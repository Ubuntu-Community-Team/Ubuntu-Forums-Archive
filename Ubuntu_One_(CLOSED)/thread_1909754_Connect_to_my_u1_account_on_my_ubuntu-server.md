---
title: "Connect to my u1 account on my ubuntu-server?"
date: 2012-01-15
forum: Ubuntu One (CLOSED)
---

### Post by yanom on 2012-01-15
I have a server running ubuntu server 11.10 ... is there any way to get my ubuntu one cloud file storage service hooked up on that? I was hoping the server could drop it's backups and logs in there and i could read them on my PC. currently i have to use scp to grab everything manually and it's a chore.

---

### Post by yanom on 2012-01-16
bump

---

### Post by yanom on 2012-01-17
bumpity.

---

### Post by yanom on 2012-02-12
anyone?

---

### Post by CivilizationII on 2012-02-17
Maybe fill a bug for 11.10 release, it is working with 10.04 server.

---

### Post by thnewguy on 2012-02-19
I don't think he's reporting a bug, but asking how to get it to work. I'm curious about this too. The ability to sync Ubuntu Server with the One service has been brought up a couple of times, but I haven't seen a definitive answer on the topic. How does one set up One to sync on Ubuntu Server?

---

### Post by Holdolin on 2012-02-21
A Google search turned up this tutorial.  I have yet to verify that this works, but as I found this thread with the same question, I intend to try it on a VM.  Hope it  helps some.  

[http://joysofprogramming.com/u1sdtool-ubuntu-one-command-line-tutorial/]("http://joysofprogramming.com/u1sdtool-ubuntu-one-command-line-tutorial/")

---

### Post by thnewguy on 2012-02-22
That tutorial is for Ubuntu Desktop systems where the user wants to sometimes use the command line. It assumes authentication and setup is being done through the GUI.

---

### Post by Holdolin on 2012-02-28
Ya, I got some time to test it on a vm, and it kicked errors relating to the (lack of) desktop environment.  I should have done that before I even linked the tutorial.  My apologies.  Its a shame really, U1 would be a great place to store off-site backups :)

---

### Post by thnewguy on 2012-02-29
Agreed, I was hoping to present One as an off-site backup solution to a small business recently until I found out U1 wouldn't work from a headless server environment. I hope that changes soon, U1 has a reasonable cost:storage ratio and some home and small business offices would benefit from having automated backups from Ubuntu Server.

---

### Post by Holdolin on 2012-03-16
If you're willing to look outsude U1, there are cloud storage services that will run in a CLI only environment.  Was talking to a friend of mine and got some suggestions.  Now with the ones i've looked at, you will need a GUI-based platform to set up your account, but once that's done you can sync your server to the clouds with a simple command.  :)

---

