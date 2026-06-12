---
title: "Installing PHP5 with JSON on Hardy?"
date: 2009-08-29
forum: Server Platforms
---

### Post by Dizzley on 2009-08-29
I must be hard of thinking.

I'm finally getting to grips with customising my Ubuntu Hardy Heron server, but I'm hazy on installing PHP5 with JSON compiled in.

Running a file with JSON gets me:
[FONT=Courier New]Failed opening required 'JSON.php'[/FONT]

And if I remove the require "JSON.php" I get:
[FONT=Courier New]**Fatal error**:  Class 'JSON' not found in **/var/www/examples/example.php** on line **54**[/FONT]

[FONT=Verdana]A bit of Googling leads me to think that I don't have JSON compiled in to the PHP5 I have installed.

How do I fix that? :confused:
[/FONT]

---

### Post by Dizzley on 2009-08-29
OK, I've bitten the bullet and I'm compiling PHP 5.2.10. I'll let you know how it goes. I can always revert...

---

### Post by Dizzley on 2009-08-29
Well, maybe a bit nearer...

I did:
[LIST]
[*]I downloaded PHP 5.2.10 from php.net.
[*]./configure --enable-json
[*]make
[*]sudo make install
[*]php -v (to check version)
[*]Still get error "Class 'JSON' not found" at command line. :(
[/LIST]
Is there anything else I have to do to get json working?
](*,)

I can feel mod_perl calling me...

---

### Post by Dizzley on 2009-08-29
Looks like I'm talking to myself here but -

Does compiling JSON into PHP 5.2  create an extension library, or is it in the core of PHP? I don't see any .so files at all.

I see the build makes a json.lo but I don't know what happens to it?

Still confused. :confused: Anyone?

---

### Post by Dizzley on 2009-08-29
[SIZE=5]FIXED[/SIZE]

Here's the explanation to save anyone else falling into the same trap.

There is no problem with my installation of PHP 5.2 with JSON. To check you have JSON enabled, simply make a call to phpinfo() and view your page in a browser.

[php]<?php
phpinfo();
?>[/php]You should see a JSON section which will show if json support is enabled.
There is no need to plug in any libraries or include any PHP libraries from 5.2 onwards.

And here is a simple example of calling one of the built-in routines from PHP 5.2. JSON support is now as simple as the two routines: json_encode and json_decode().

[php]<?php
$json = '{"a":1,"b":2,"c":3,"d":4,"e":5}';

var_dump(json_decode($json));
var_dump(json_decode($json, true));

?>[/php]The JSON support allso has a set of predefined constants. See the [PHP 5.2 JSON documentation]("http://php.net/manual/en/book.json.php") page.

If you see code examples like [http://www.phpclasses.org/browse/file/20929.html](http://www.phpclasses.org/browse/file/20929.html), they are built for older PHP versions pre-5.2 which require external JSON extension support. That particular one caused ne about 3 hours of worry until I finally worked it all out.

---

