---
title: "running multiple instances of a program"
date: 2010-03-11
forum: Server Platforms
---

### Post by hotpancakes on 2010-03-11
Hi,

Does anybody know how to run multiple instances of a command line app from the terminal? Thanks a bunch!

---

### Post by viralmeme on 2010-03-11
> **hotpancakes said:**
> Hi,

Does anybody know how to run multiple instances of a command line app from the terminal? Thanks a bunch!
I googled on multiple + commands + bash and got these ..

[http://www.hypexr.org/bash_tutorial.php#multiple](http://www.hypexr.org/bash_tutorial.php#multiple)
[http://stackoverflow.com/questions/161252/bash-start-multiple-chained-commands-in-background](http://stackoverflow.com/questions/161252/bash-start-multiple-chained-commands-in-background)

---

### Post by Seq on 2010-03-11
Concurrently or consecutively? Do you care about the output at all?

Consecutively, you can chain commands, as ymitchell found.

Concurrently, if you care about output, you would need multiple terminals. You can do this either by opening another terminal, or using a multiplexer like GNU Screen.

Concurrently without caring about input or output, you can suffix your command with a single ampersand. This causes the command to be forked off, and you are returned to your console to run more commands. You will still get output, but if you're running multiple commands this way it will all be jumbled together.

A variation of the last example would be to redirect output to a file for each command.

So it all depends on the behaviour you want.

---

