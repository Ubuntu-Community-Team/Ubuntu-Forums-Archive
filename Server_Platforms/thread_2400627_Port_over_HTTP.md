---
title: "Port over HTTP?"
date: 2018-09-07
forum: Server Platforms
---

### Post by warmango on 2018-09-07
So im trying to get a port to work over the webbrowser, im trying to use Webminal over on MYDOMAIN.COM/SHELL, or any port like that, or even my laptop on /lap/foo/bar

---

### Post by TheFu on 2018-09-08
You've lost me.  "Port over HTTP" doesn't really say much as to what you really want to do.  You'll need to either use the correct terminology or explain more clearly.
When you say "port" related to computing, we think about the 64K ports every IP gets which might have a listener.  If you setup a web-server, then by default that is a listener on port 80/tcp with a specific set of available commands. Because 80 is less than 1024, it is a "privileged port" and the service/listener must started by the root account.  If you don't want to use an existing webserver, then it is much easier to have a listener on a higher port. Any userid can do that.

A directory or file is NOT a port, though you can connect them, if you like using redirection.

If you will describe what you hope to accomplish rather than HOW you hope to do 1 part of it, maybe someone could be more helpful?

If your goal is to gain a remote shell connection, then ssh is the normal method for that on Unix systems.  ssh is the normal way for Unix systems to be managed around the world.  Running remote programs over ssh is also extremely common.  On Ubuntu, the standard ssh-server is in the openssh-server package. Install that.  Then from any client, use ssh {IP-of-server} to create a simple remote connection using the same userid.  If you need to change userids between the client and the server, there are options.

---

### Post by warmango on 2018-09-08
Apologies, was tired and half asleep when i wrote that,

I recall once on a server i hosted at my school, forwarding "mydomain.com:4422" to a better URL like "my-domain.com/shell" because that was the port i had ShellInABox set to, 

I recall modifying my Apache Config with a <Location> setting, but i don't recall how I did it.  An example of what i want it to do, is like what [http://webminal.org/](http://webminal.org/) have done, they use ShellInaBox on the server which one logs into. I am trying to use ShellInABox because School has been getting stricter on what plugins we are allowed to use (They have blocked a rather useful Offline DOCUMENT editor that lets me keep my files on my USB) and insist on using only WEBSITES for everything, and its making it a lot more complicated for me to access, and im worried they will block the SSH plugin for Chromebooks,

So how i want it to work is allowing me to go to "mydomain.com/sh" and be able to access my Server's shell when i need to, like per say, needing to make a file on my server because I don't like the school having access to EVERYTHING i use.

---

### Post by wildmanne39 on 2018-09-09
From the CoC:
> We do not support circumventing TOS, EULA, etc here. Such threads will be closed and offending users will be penalised with infractions and warnings. Given that our forums could be used by people at work and school we want to ensure they will not encounter material that will cause them problems or cause their access to our site to be limited, so all content should be safe for both.
We do not support trying to circumvent security measures/protocols put in place by schools, employer's, etc.

For a complete list of the rules:

[https://ubuntuforums.org/misc.php?do=showrules](https://ubuntuforums.org/misc.php?do=showrules)

Thread closed!

---

