---
title: "How to set up Shorewall in Ubuntu Server 9.10"
date: 2010-05-04
forum: Server Platforms
---

### Post by TomDaBomb2u on 2010-05-04
Hello all:

I'm about at about an intermediate level with Ubuntu, but completely new to servers. I followed [this tutorial]("http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/") to set up Ubuntu Server 9.10 on my Lenovo R61i. All went well up until the installation of the firewall. 

I can't seem to install Shorewall. I typed

```
sudo aptitude install shorewall
```

and it seems to have installed fine, but when I try to backup the configuration file: 

```
sudo cp /usr/share/doc/shorewall-common/examples/one-interface/* /etc/shorewall/
``` I get ```
cp: cannot stat `/usr/share/doc/shorewall-common/examples/one-interface/*': No such file or directory
``` 

I can't find any evidence that Shorewall is even installed. What am I missing?? I googled the problem, and haven't seen anyone else with this issue.

Please help! Let me know if any more info is required.

Thanks!
Thomas

---

### Post by bab1 on 2010-05-04
> **TomDaBomb2u said:**
> ...

I can't seem to install Shorewall. I typed

```
sudo aptitude install shorewall
```

and it seems to have installed fine, but when I try to backup the configuration file: 

```
sudo cp /usr/share/doc/shorewall-common/examples/one-interface/* /etc/shorewall/
``` I get ```
cp: cannot stat `/usr/share/doc/shorewall-common/examples/one-interface/*': No such file or directory
``` 

I can't find any evidence that Shorewall is even installed. What am I missing?? I googled the problem, and haven't seen anyone else with this issue.

Please help! Let me know if any more info is required.

Thanks!
Thomas

So what have you done to try and locate the shorewall files?  Have you tried ```
sudo locate shorewall
```

---

### Post by TomDaBomb2u on 2010-05-04
> **bab1 said:**
> So what have you done to try and locate the shorewall files?  Have you tried ```
sudo locate shorewall
```

Thanks for the quick reply. Yes, I tried that, but got nothing.

Thomas

---

### Post by bab1 on 2010-05-04
> **TomDaBomb2u said:**
> Thanks for the quick reply. Yes, I tried that, but got nothing.

Thomas

Did you update the locate database since you just did the install?

Did you check Shorwall's site for updated information?

Did you check ```
man shorewall
```

---

### Post by TomDaBomb2u on 2010-05-04
Neither. Will do when I get back home. I'll post results.  Thanks!

---

### Post by TomDaBomb2u on 2010-05-04
Well, that was kinda embarrassing lol. . . I looked on the website (but not very well at first) and completely missed the package repo. I added it and installed. ```
sudo locate shorewall
``` still doesn't do anything but I'm looking at the manual now. 

Thanks! I still may have questions though lol.

---

### Post by redmk2 on 2010-05-04
> **TomDaBomb2u said:**
> Well, that was kinda embarrassing lol. . . I looked on the website (but not very well at first) and completely missed the package repo. I added it and installed. ```
sudo locate shorewall
``` still doesn't do anything but I'm looking at the manual now. 

Thanks! I still may have questions though lol.
You have to populate the database.

Try this```
sudo updatedb
```

See [**_here_**]("http://ubuntuforums.org/showthread.php?t=912965").

Edit: For a complete config of *locate *see section 8 of this [**_manual_**]("http://www.nsrc.org/helpdesk/ubuntu/post-install-exercises.pdf").

---

### Post by ne0h184 on 2012-10-06
Hey, this might be completely off, but if your installation came up successful try looking in /usr/share/doc/shorewall/... (instead of shoreall-common). That's were I found my examples.  -Frank

---

### Post by overdrank on 2012-10-06
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

