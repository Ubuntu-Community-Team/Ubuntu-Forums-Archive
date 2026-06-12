---
title: "jabberd2 starts before mysql does"
date: 2013-03-08
forum: Server Platforms
---

### Post by thany on 2013-03-08
I've set up a jabberd2 server pretty much the default way, afaik. I connects to mysql for storings its... things. All is cool, everything works... Until the server needs a reboot.

In the logs, I get things like this:
```
Fri Mar  8 10:01:21 2013 [info] loading 'mysql' authreg module
Fri Mar  8 10:01:21 2013 [error] mysql: connection to database failed: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
Fri Mar  8 10:01:21 2013 [error] failed to initialize auth module 'mysql'
```
When I retry starting jabberd2, it works beautifully. This leads me to believe that everything is in fact working perfectly fine, except that jabberd2 is trying to start itself before mysql has started.

So mysqld needs to be running and fully operational before jabberd2 can start.
Is there a way to add this kind of dependency?

---

### Post by SeijiSensei on 2013-03-08
Are you starting the jabber server manually or via the /etc/init.d scripts?  If the latter, look in /etc/rc2.d which is a collection of symlinks to the various init.d scripts.  The number following "S" determines the order in which they are started at boot.  Just make sure it's larger than the value for mysqld.

Worst case scenario is to remove the init.d script and start the jabber server by a command in /etc/rc.local which is run after everything else has been started.

---

### Post by thany on 2013-03-11
Not to be rude, but in my point of view I don't see why on earth I would start jabberd2 (or any daemon) manually after each and every reboot. So yes, it is started automatically (or tries to anyway ;))

I think I basically understand how this works now, except for the fact that mysqld is not in rc2.d... But it is definately started automatically.
Mind you, I have never touched these scripts, not once. So reasons dictates that it must be standard. Whyever mysql is not there, must be a standard thing. Can you tell me what to do in order to get jabberd2 to start after mysql, even if mysql is not to be found in /etc/rc.2?

---

### Post by thany on 2013-03-21
Any help please? I didn't get to resolve this issue yet...

---

