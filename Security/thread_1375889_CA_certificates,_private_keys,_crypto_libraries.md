---
title: "CA certificates, private keys, crypto libraries???"
date: 2010-01-08
forum: Security
---

### Post by riksaga on 2010-01-08
Hello,

 I have used Linux/Ubuntu/Debian/Suse for quite awhile and, as always, am looking to switch completely. My situation, 10 months ago, is as follows:

 To access special bank services I need to generate a keys & certificates from the banks site.  I call up and get a time limited login and they say only IE will work.  The keys are generated w/ non-export so I cannot copy them over.

 On winXP IE Keys & Certs are generated with MS crypto libraries.

 On Ubuntu 8.04 w/ FF the site hangs.

 On Ubuntu 8.04 w/ IE4Linux the keys are not generated (no crypto).

 On Ubuntu 8.04 w/ WINE and IE 5.5 the keys are not generated (no crypto).

I currently use an XP notebook w/ IE for this bank functionality.

  I am looking at getting a new laptop (dell??) for the newest Ubuntu.  I am willing to install IE4Linux or wine+IE, but do not relish the thought of hunting down MS crypto libraries and hacking them into my new machine.

  What is the likely hood that I can get my keys & certs generated on a new laptop using a standard install( ideally with FF, but if necessary w/ IE)?

---

### Post by ajgreeny on 2010-01-08
Judging by your previous comments, I should think the only way to do this is either in a separate install of windows or a VM install in, for example, VirtualBox direct from Sun.

---

### Post by BkkBonanza on 2010-01-09
I have a bank account that doesn't work in Linux FF either. I use a VirtualBox install of XP to run Windows FF and it works fine. Also IE works fine. Most likely if you install VirtualBox (free) and then Windows as a guest in VBox you'll be set to go. 

I like this better than Wine because you have a real Windows and so far everything I've tried has worked perfectly. Also with VBox it has an integrated desktop mode where you can run Linux and Win apps on the same desktop. It's an awesome product worth checking out and it's free (as in beer) too.

PS. They also have a VirtualBox Open Source Edition which is free as in freedom, but it lacks a few advanced guest features.

---

