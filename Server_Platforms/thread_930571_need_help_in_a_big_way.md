---
title: "need help in a big way"
date: 2008-09-26
forum: Server Platforms
---

### Post by focus_uk on 2008-09-26
I want to make the move from windows server over to ubuntu.but i just dont understand all the right things to start me off.i have read the how to?? there talk about settin up headless but surely you need to be workin on the server box to set it up headless.i have an website runnin on windows server with apache.but now the time to make the move over,when i read the how too pages i get confuse as to what to install and what to install on a remote computer.any help would be great this is what i want to do,

1 setup server box with apache and perl.
2 setup some way of remote so i can make changes to server over network but not internet,as an when needed.i do have an firewall with router,

what i would like is to see an easy understandin how to setup
Thanks

---

### Post by lian1238 on 2008-09-26
You just need to do it one step at a time. Install apache2 and apache-perl first. Then for remote access, I think you can use openssh-server. (I've never done any remotely.) The server directory is '/var/www/'.

** Edit:** install just apache2. For perl, you need mod_perl.

---

### Post by focus_uk on 2008-09-26
Tx for the reply,yes i know that what i will need to do.Right now i have an box all ready to install ubuntu server on.like i say am very very new to linux and lookin for the right way to go about doin this right.

---

### Post by kamaji792 on 2008-09-26
Try this link [Ubuntu 8.04 Lts Server set-up](https://help.ubuntu.com/8.04/serverguide/C/index.html)

I must admit when I am creating a server I start with a monitor and keyboard connected.
I do a base server install, from CD, with no services.
Get the network up and running.
Get the Internet connection to work.
Do an update of the system - 'sudo apt-get update' 'sudo apt-get upgrade'
Then I install OpenSSH so I can connect remotely.
Test the remote connection.
Turn off the server, remove the monitor and keyboard if required.
Install the services I require remotely.

I use **putty** from a WinXP box.

All the best.

---

### Post by lian1238 on 2008-09-26
Ubuntu Server comes with apache and all the scripting modules installed, no?

---

### Post by kamaji792 on 2008-09-26
> **focus_uk said:**
> like i say am very very new to linux and lookin for the right way to go about doin this right.

Make sure you have take all the data off the box you are about to install the server on.  Put the install CD in and re-boot.

As for worrying about getting it right.  I favor the suck-it-and-see approach.

For your first install stick to the simple default option but don't install any services (well you could install OpenSSH).

Get the network up and running, internet connection, remote connection.

If you have any major problem you can always start a new install.  It does not take long if you don't specify any services.

All the best

---

### Post by kamaji792 on 2008-09-26
> **lian1238 said:**
> Ubuntu Server comes with apache and all the scripting modules installed, no?

You have to specify PHP or install it separately from Apache.

---

### Post by focus_uk on 2008-09-26
Tx guys.am taken all what you say on board,i guess 15+ years with windows as made me thick.click and go,other thing is when members say just install putty or webadmin on an xp box so can do remote,well again sury its more then just installin the software on an remote box,there must be some kind of setup on the server box to connect right.see its all this which am not to sure about aswell.would you guys say its all about try and error. then if thats the case how would i know it all right and all sceure.

---

### Post by kamaji792 on 2008-09-26
> **focus_uk said:**
> how would i know it all right and all sceure.

It has been said before.  One step at a time.

If you are setting up a local network behind a router you should be pretty safe.

When you have a base setup running as you want.  Then worry about security.  Ubuntu is pretty secure to start with.

---

### Post by freebeer on 2008-09-26
> **kamaji792 said:**
> 
Turn off the server, remove the monitor and keyboard if required.
Install the services I require remotely.


Wouldn't you have to turn the server on at some point?  :)

---

