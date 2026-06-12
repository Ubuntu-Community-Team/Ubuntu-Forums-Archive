---
title: "Running GUI app from php?"
date: 2009-03-21
forum: Server Platforms
---

### Post by linuxisevolution on 2009-03-21
Not sure where to ask, so I asked here.

I want to integrate DOSBOX into a web page to execute dos commands. First I thought I'd test it by launching something simple first like xcalc. I copied the xcalc binary to the directory of the php file on the server and chmod'ed it to 777. I then put this in a dos.php file:
```

<?php


$command = "xcalc";
shell_exec($command);

?>

```
Am I doing something wrong? How would I go about putting dosbox ***_in_*** the web page, like a flash applet?


EDIT: link is [here.]("http://98.219.177.90/apache2-default/linforum/forum/forum/nes/dos.php")

---

### Post by Dr Small on 2009-03-21
[php]<?php
$cmd = `export DISPLAY=:0; xcalc`;
shell_exec($cmd);
?>[/php]

xcalc just can't execute to nowhere. You've got to tell it where to display.

---

### Post by linuxisevolution on 2009-03-21
> **Dr Small said:**
> [php]<?php
$cmd = `export DISPLAY=:0; xcalc`;
shell_exec($cmd);
?>[/php]

xcalc just can't execute to nowhere. You've got to tell it where to display.

I put this in the php file, no errors but nothing happens.

Thanks for the help though, I'm in the right direction.

---

### Post by Dr Small on 2009-03-21
I've never actually used shell_exec(). I've just used exec() or backtics (same as shell_exec()).
[http://us.php.net/manual/en/function.exec.php](http://us.php.net/manual/en/function.exec.php)

But, I know it's possible, as I've done it before. I just don't have a webserver on my local machine to try it, anymore.

---

### Post by linuxisevolution on 2009-03-21
> **Dr Small said:**
> I've never actually used shell_exec(). I've just used exec() or backtics (same as shell_exec()).
[http://us.php.net/manual/en/function.exec.php](http://us.php.net/manual/en/function.exec.php)

But, I know it's possible, as I've done it before. I just don't have a webserver on my local machine to try it, anymore.

I know it's possible too. Going to sleep now, talk to you in the morning.

---

### Post by init1 on 2009-03-22
> **linuxisevolution said:**
> Not sure where to ask, so I asked here.

I want to integrate DOSBOX into a web page to execute dos commands. First I thought I'd test it by launching something simple first like xcalc. I copied the xcalc binary to the directory of the php file on the server and chmod'ed it to 777. I then put this in a dos.php file:
```

<?php


$command = "xcalc";
shell_exec($command);

?>

```
Am I doing something wrong? How would I go about putting dosbox ***_in_*** the web page, like a flash applet?


EDIT: link is [here.]("http://98.219.177.90/apache2-default/linforum/forum/forum/nes/dos.php")

> **Dr Small said:**
> [php]<?php
$cmd = `export DISPLAY=:0; xcalc`;
shell_exec($cmd);
?>[/php]

xcalc just can't execute to nowhere. You've got to tell it where to display.
I think Apache executes php commands using a separate and limited user, which is not able to access the X server. I've tried to make a web interface for launching apps using php, but it didn't work. I was able to run commands like 'ls' and 'free' and put their output into the page, but nothing graphical worked. As for putting dosbox into a web page, there's something like that for Java. 
[http://www-jpc.physics.ox.ac.uk/Demo.html](http://www-jpc.physics.ox.ac.uk/Demo.html)

---

### Post by binbash on 2009-03-23
Yes, you have to set up apache for that.Default and most cases/distros the commands run as nobody.

---

### Post by bodhi.zazen on 2009-03-23
Moved to server platforms.

---

### Post by Joeb454 on 2009-03-23
Moved to the non-archived version! :p

---

### Post by Dr Small on 2009-03-23
> **Joeb454 said:**
> Moved to the non-archived version! :p
That's probably helpful, incase someone would wish to reply :)

---

### Post by Mehall on 2009-03-23
> **Dr Small said:**
> That's probably helpful, incase someone would wish to reply :)

One would imagine!

---

