[![mouse](http://labs.gurron.com/trove/react-with-mouse.png)](https://github.com/ulpmori/react-with-mouse/)
=====


# React with mouse

Event-driven, non-blocking I/O with the mouse framework.

This is still at a very experimental stage and should not be used for production 
in any way.

## What is it?

mouse is a web development framework designed to be lightweight, simple to use 
and provide a cleaner codebase. Routing has a structures system with the ability 
of mapping custom urls. Whiskers.json app information that simplifies packaging 
and app control. Its base is in PHP with an option of using templating 
for a narrow cleaner coding syntax. It also includes jquery and bootstrap and 
could support further front-end libraries.

React is a low-level library for event-driven programming in PHP. At its core
is an event loop, on top of which it  provides low-level utilities, such as:
Streams abstraction, async dns resolver, network client/server, http
client/server, interaction with processes. Third-party libraries can use these
components to create async network clients/servers and more.

The event loop is based on the reactor pattern (hence the name) and strongly
inspired by libraries such as EventMachine (Ruby), Twisted (Python) and
Node.js (V8).

## Usage

### Example

The example below is for a simple HTTP server with react alone, quickstarts and 
tutorials will be provided soon.

Here is an example of a simple HTTP server listening on port 1337:
```php
<?php

$i = 0;

$app = function ($request, $response) use (&$i) {
    $i++;

    $text = "This is request number $i.\n";
    $headers = array('Content-Type' => 'text/plain');

    $response->writeHead(200, $headers);
    $response->end($text);
};

$loop = React\EventLoop\Factory::create();
$socket = new React\Socket\Server($loop);
$http = new React\Http\Server($socket);

$http->on('request', $app);

$socket->listen(1337);
$loop->run();
```

## Tests

To run the test suite, you need PHPUnit.

    $ phpunit

## License

MIT, see LICENSE.
