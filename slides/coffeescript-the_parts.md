!SLIDE bullets incremental

#CoffeeScript#
* The Parts

!SLIDE

#Possible points of contention#
##clearly the best way to convince people o_O##

!SLIDE

##Whitespace Delimited Blocks##

!SLIDE code

    function close() {
      for (var i = 0; i < arguments.length; i++) {
        arguments[i].fadeOut(opts.duration);
      }
    }

!SLIDE

##becomes...##

!SLIDE code

    close = -> for argument in arguments
      argument.fadeOut(opts.duration)

!SLIDE code

    addMarker: function(options, layer) {
      var settings = $.extend({
        id: '',
        lat: 0,
        lng: 0,
        icon: {
          path: '/images/markers/headend_low_severity.png',
          width: 10,
          height: 10,
          severity: 'low'
        },
        info_bubble: ""
      }, options);

!SLIDE

##becomes...##

!SLIDE code

    addMarker: (options, layer) ->
      settings = $.extend(
        id: ''
        lat: 0
        lng: 0
        icon: 
          path: '/images/markers/headend_low_severity.png'
          width: 10
          height: 10
          severity: 'low'
        info_bubble: ""
     , options)

!SLIDE code

    if (happy && knowsIt) {
      clapsHands();
      chaChaCha();
    } else {
      showIt();
    }

!SLIDE

##becomes...##

!SLIDE code

    if happy and knows_it
      clapHands()
      chaChaCha()
    else
      showIt()

!SLIDE

#Compilation Phase#

!SLIDE bullets incremental
* Unlike your javascript, it requires a preparser. Sorry.
* Theoretically more difficult to debug.           Like Sass, or Haml.
* but in practice, it hasn't been much of an issue.           Like Sass, or Haml.
* Tooling will make it all alright :D

!SLIDE bullets incremental

* BistroCar - serve CS from Rails 2
* Barista - serve CS from Rails 3
* RackCoffee - serve CS from Rack-based applications
* Node.js - Native support, woot

!SLIDE

# I'm not sure what else you could complain about, tbh * #
#### * but haters gonna hate ###

!SLIDE

# Why should u <3 it? #

!SLIDE

## Everything is an expression ##
### See conditionals, for loops, etc... ##

!SLIDE code

# List Comprehensions! #

    cat.meow() for cat in cats

    all_kittens = cat.kittens() for cat in cats

!SLIDE code

# Existential Operator! #

    cat.meow() if cat?

    kittens ?= cat.kittens()

!SLIDE code

# Sane Class Constructors! #

    class Animal
      constructor: (@name) ->

      move: (meters) ->
        alert @name + " moved " + meters + "m."

    class Cat extends Animal
      move: ->
        alert "Meow!"
        super 10

!SLIDE

# becomes... #

!SLIDE code

	var Animal, Cat;
	var __extends = function(child, parent) {
	    var ctor = function(){};
	    ctor.prototype = parent.prototype;
	    child.prototype = new ctor();
	    child.prototype.constructor = child;
	    if (typeof parent.extended === "function") parent.extended(child);
	    child.__superClass__ = parent.prototype;
	  };
	Animal = function(_a) {
	  this.name = _a;
	  return this;
	};
	Animal.prototype.move = function(meters) {
	  return alert(this.name + " moved " + meters + "m.");
	};
	Cat = function() {
	  return Animal.apply(this, arguments);
	};
	__extends(Cat, Animal);
	Cat.prototype.move = function() {
	  alert("Slithering...");
	  return Cat.__superClass__.move.call(this, 5);
	};

!SLIDE

## fuck ##

!SLIDE code

# Destructuring #

    weatherIn = (location) ->
      # some ajax bs

      [
        location, 85, "Partially Cloudy",
        "Double Rainbow", "All", "the", "Way"
      ]

    [city, temp, forecast, misc...] = weatherIn "Jacksonville, FL"
    city == [ "Double Rainbow", "All", "the", "Way" ]

!SLIDE code

# String Interpolation #
### alone worth the price of admission, imo ###

    name = cat.name()

    "The cat's name is #name"

    "The cat's name is #{cat.name()}"

!SLIDE
#Other goodies#

!SLIDE bullets incremental

* Function binding (useful for scoping issues in callbacks)
* unless keyword
* splats!
* array slicing via ranges.  kittens[3..6]
* passthrough assignment (everything is an expression)

!SLIDE bullets incremental

* REPL (read eval print loop, ala irb, or ipython)
* no more semicolons
* no more var
* == behaves sanely, using === under the covers
* is( == ), isnt ( !== ), and( && ), or( || )

!SLIDE bullets

# And much more #
* visit www.coffeescript.com
* try coffeescript, watch it compile on the fly, neat
* etc...

!SLIDE bullets

## Thanks ##

* email: robert@hashrocket.com
* (twitter|github): rbxbx
* slides: coffeescript-theparts.heroku.com
