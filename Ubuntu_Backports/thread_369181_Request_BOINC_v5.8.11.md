---
title: "Request: BOINC v5.8.11"
date: 2007-02-24
forum: Ubuntu Backports
---

### Post by Talon2 on 2007-02-24
Running Edgy here.

The current version of BOINC in the repositories is v5.4.  There are some very important updates in v5.8.11.

[http://boinc.berkeley.edu/download.php](http://boinc.berkeley.edu/download.php)

Thanks.

---

### Post by zenrox on 2007-02-24
file a bug for fiesty in lauchbad for it to be upgraded

---

### Post by zenrox on 2007-02-25
bug filed
[https://bugs.launchpad.net/ubuntu/+source/boinc/+bug/87853](https://bugs.launchpad.net/ubuntu/+source/boinc/+bug/87853)

---

### Post by Talon2 on 2007-02-25
> **zenrox said:**
> bug filed
[https://bugs.launchpad.net/ubuntu/+source/boinc/+bug/87853](https://bugs.launchpad.net/ubuntu/+source/boinc/+bug/87853)

zenrox, thanks for the help.

I'm still somewhat new to the community and it can be difficult to sort out the good info from the bad.  There are messages floating around that say to put requests here then there is the sticky here that says use launchpad but I can't see in launchpad how to identify a bug as specific to version or category.  This process is a little confusing.

Thanks again.

---

### Post by zenrox on 2007-02-25
ya it can be confusing 
all i can offer is start reading up on how to do something before you do it
pop some :popcorn:  and start reading

---

### Post by sleepyenglish on 2007-04-02
So does this mean 5.8 will be available in the feisty repositories?

Thanks

---

### Post by harrisony on 2007-04-05
> **sleepyenglish said:**
> So does this mean 5.8 will be available in the feisty repositories?

Thanks
Not yet son but watch
[http://packages.ubuntu.com/feisty/net/boinc-client](http://packages.ubuntu.com/feisty/net/boinc-client)
[http://packages.ubuntu.com/feisty/x11/boinc-manager](http://packages.ubuntu.com/feisty/x11/boinc-manager)
and hope for the best

---

### Post by Feenix3k on 2007-04-07
I have tryed downloading the most current version of Boinc and I can't do anything with the download. How can I install the new vision myself?

---

### Post by sleepyenglish on 2007-04-08
> **harrisony said:**
> Not yet son but watch
[http://packages.ubuntu.com/feisty/net/boinc-client](http://packages.ubuntu.com/feisty/net/boinc-client)
[http://packages.ubuntu.com/feisty/x11/boinc-manager](http://packages.ubuntu.com/feisty/x11/boinc-manager)
and hope for the best

Thanks

[-o<

---

### Post by Lucifiel on 2007-04-14
> **harrisony said:**
> Not yet son but watch
[http://packages.ubuntu.com/feisty/net/boinc-client](http://packages.ubuntu.com/feisty/net/boinc-client)
[http://packages.ubuntu.com/feisty/x11/boinc-manager](http://packages.ubuntu.com/feisty/x11/boinc-manager)
and hope for the best

Thank you, dude! :D

That's because I tried to install the latest version myself but after getting more errors again, I decided to revert back to the version in Synaptic. :p

---

### Post by sleepyenglish on 2007-04-25
It didn't make it :sad:, is going to be updated?

---

### Post by sleepyenglish on 2007-05-19
The kind people at [http://www.getdeb.net/](http://www.getdeb.net/) have created a .deb for BOINC 5.8.17 which works great on feisty.

[http://www.getdeb.net/app.php?name=Boinc](http://www.getdeb.net/app.php?name=Boinc)

---

### Post by Feenix3k on 2007-05-19
I got a libc6 error, like my version is missing something.

---

### Post by sleepyenglish on 2007-05-20
Did you install both  boinc-manager & boinc-client? If so try leaving a comment on the Boinc getdeb page informing them of the problem.

---

### Post by Feenix3k on 2007-05-20
I try to load the boinc-client, got the libc6 error, tried loading the manager got same error.

---

### Post by Cappy on 2007-05-23
> **Feenix3k said:**
> I try to load the boinc-client, got the libc6 error, tried loading the manager got same error.

```
sudo apt-get install libc6 
```

BOINC only detects one CPU =( I'm on Feisty 64-bit and running the 64-bit client. If CPU1 is being used at 90% then CPU0 will be being used at 10%. Basically, CPU0 + CPU1 = 100%? I'm not sure if this is normal or not.

---

### Post by Feenix3k on 2007-05-24
[QUOTE=Cappy;2710346]```
sudo apt-get install libc6 
```

The above command showed I have the most current version of libc6, but still says I have dependency problems when I try to install Boinc from the links in previous posts

---

### Post by Cappy on 2007-05-24
I'm using the packages from:
[http://www.getdeb.net/app.php?name=Boinc](http://www.getdeb.net/app.php?name=Boinc)

You need to give the error and "the links in previous posts" doesn't say which package you are using. Try the ones in the link above if they aren't the ones you are already using.

---

### Post by Feenix3k on 2007-05-25
When I try loading from the link in last post I get from my system:

Error: Dependency is not satisfiable: libc6.

My libc6 is 2.3.6-Oubuntu20.4

---

### Post by Cappy on 2007-05-25
It requires a newer version of libc6 so your version is too old because you are running dapper.
Unfortunately, your 2.3.6 is the only one available for dapper.
You can run
```
sudo apt-get install boinc-manager boinc-client
```
and that will install the older version that doesn't need the newer libc6.
You could force install the newer lib6 but I don't know anything about doing something like that and it may hose the system or something. 
You could use 5.8.16 but it isn't a deb:
[http://boinc.berkeley.edu/dl/boinc_5.8.16_i686-pc-linux-gnu.sh](http://boinc.berkeley.edu/dl/boinc_5.8.16_i686-pc-linux-gnu.sh)

---

