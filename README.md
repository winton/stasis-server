Stasis::Server
==============

Redis-backed queue for Stasis render jobs

[![Build Status](https://secure.travis-ci.org/winton/stasis-server.png)](http://travis-ci.org/winton/stasis-server)

Install
-------

Install via [RubyGems](http://rubygems.org/pages/download):

<!-- language:console -->

    $ gem install stasis-server

Server Mode
-----------

Stasis can run as a server that uses [redis](http://redis.io) to wait for render jobs.

Stasis server that uses redis on port 6379:

    $ stasis -r localhost:6379/0

Push to the server (in Ruby):

    Stasis::Server.push(
      # Paths to render
      :paths => [ "index.html.haml", "subdirectory" ],

      # Made available to views as `params`
      :params => {},

      # Redis address
      :redis => "localhost:6379/0",

      # Return rendered templates (false by default)
      :return => false,

      # Block until templates generate (false by default)
      :wait => false,

      # Write to the filesystem (true by default)
      :write => true,

      # Cache ttl for returned templates (nil by default)
      :ttl => nil,

      # Force write even if cached (false by default)
      :force => false
    )