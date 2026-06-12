---
title: "PHP tools"
date: 2009-03-26
forum: Server Platforms
---

### Post by quikone8 on 2009-03-26
I am running a web server and would like to be able to test some of my php scripts remotely.  Are there any tools that will work with firefox or terminal  to accomplish debug?

---

### Post by Bachstelze on 2009-03-26
You can run PHP scripts from the command-line or run the PHP interpreter:

```
firas@hatchin ~ % cat test.php
<?php

$foo = "bar";
var_dump($foo);

firas@hatchin ~ % php test.php
string(3) "bar"
firas@hatchin ~ % php -a
Interactive shell

php > $foo = "bar";
php > var_dump($foo);
string(3) "bar"
php >

```

---

### Post by quikone8 on 2009-03-26
> **HymnToLife said:**
> You can run PHP scripts from the command-line or run the PHP interpreter:

```
firas@hatchin ~ % cat test.php
<?php

$foo = "bar";
var_dump($foo);

firas@hatchin ~ % php test.php
string(3) "bar"
firas@hatchin ~ % php -a
Interactive shell

php > $foo = "bar";
php > var_dump($foo);
string(3) "bar"
php >

```

I don't mean to be thick, but is this an example or is this a script that would start command line testing?

---

### Post by Bachstelze on 2009-03-26
> **quikone8 said:**
> I don't mean to be thick, but is this an example or is this a script that would start command line testing?

It was just an example, to illustrate how to run a PHP script from the command-line. ;)

Basically, [font="monospace"]php myscript.php[/font] executes a script, and [font="monospace"]php -a[/font] starts the interactive interpeter.

---

### Post by hyper_ch on 2009-03-27
you need to have php5-cli package installed to run scripts from the terminal.

---

### Post by quikone8 on 2009-03-27
> **hyper_ch said:**
> you need to have php5-cli package installed to run scripts from the terminal.

Okay, I have got that downloaded and installed on the server.  I have a php script in ubercart that has a very slight error.  Is there a way to debug remotely, if so, how?  Do I need to right anything to make it work?  Thanks for the help.

---

### Post by ddoom on 2009-03-28
By the sound of it you need knowledge of PHP.

---

### Post by hyper_ch on 2009-03-28
well, php5-cli is only needed if you want to run php script on the cli (e.g. a cron job).

What error do you get? By default the php.ini will display errors and line and then youhae to troubleshoot yourself...

---

### Post by quikone8 on 2009-03-29
> **hyper_ch said:**
> well, php5-cli is only needed if you want to run php script on the cli (e.g. a cron job).

What error do you get? By default the php.ini will display errors and line and then youhae to troubleshoot yourself...

No error, the code is showing up in the field instead of the desired data.  I am sure that I have it coded incorrectly.  Is there a good place to figure out what I am doing wrong?

---

### Post by hyper_ch on 2009-03-29
try```
sudo a2enmod php5
```

---

### Post by gregor171 on 2009-03-29
You might be missing open and close tag in script:

[PHP]<?php
// your code
?>[/PHP]

Or you dont have php or php-cli installed. It should run without apache.

---

