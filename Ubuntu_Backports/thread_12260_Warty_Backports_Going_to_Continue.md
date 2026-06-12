---
title: "Warty Backports Going to Continue"
date: 2005-01-23
forum: Ubuntu Backports
---

### Post by jdong on 2005-01-23
Since the new backports system was easier to set up than previously anticipated, I will continue to develop Warty backports on the new system. Hang tight as I proceed with migration.

---

### Post by Quest-Master on 2005-01-23
Yes. <3

---

### Post by jdong on 2005-01-23
Note that this continuation of the Warty Backports tree is still gonna be a kind-of experiment to see if our bandwidth donor will be able to handle the typical load.

---

### Post by Skid on 2005-01-23
[QUOTE=jdong]Note that this continuation of the Warty Backports tree is still gonna be a kind-of experiment to see if our bandwidth donor will be able to handle the typical load.[/QUOTE]
 What amount of bandwidth do you typically push through on a monthly figure (if you have that data, and are willing to release it)?

Cheers.

---

### Post by jdong on 2005-01-23
[QUOTE=Skid]What amount of bandwidth do you typically push through on a monthly figure (if you have that data, and are willing to release it)?

Cheers.[/QUOTE]

I do not have that figure -- SF doesn't give me that kind of output. But on average, 200 files are requested daily, via SF.net publicly accessible project stats. Most of the time, I project, it's gonna be either 

1. Search engine indexing front page
2. apt-get update'ing, pulling the tiny Packages.gz files.

---

### Post by jdong on 2005-01-24
Ok, 400MB worth of repository stuff uploaded and sync'ed, ready to go for backporting again.

First off, I saw that Hoary now has readahead. I'll first play with that.

---

### Post by oracledarren on 2005-01-25
Could you let me have the addresses to put in my apt.sources please so I can start using the Warty backport?

Thanks

Darren

---

### Post by jdong on 2005-01-25
[http://ubuntuforums.org/showthread.php?t=8486](http://ubuntuforums.org/showthread.php?t=8486)

I updated the Welcome thread with the new addresses. Note also that there are "main restricted universe multiverse" sections for every distribution -- that changed from last time!

---

### Post by oracledarren on 2005-01-25
Thanks I will do that now :)

Darren

---

### Post by xpt on 2005-01-25
[QUOTE=jdongI will continue to develop Warty backports on the new system. Hang tight as I proceed with migration.[/QUOTE]

Is the deb source at:

deb [http://ubuntu-bp.sourceforge.net/ubuntu](http://ubuntu-bp.sourceforge.net/ubuntu) ?

If so, could you add AMD64 architecture please? I think SF have that architecture for you to compile. 

Thanks a lot!

---

### Post by jdong on 2005-01-26
```

deb [http://cloud9.somniumcomputing.com:81/ubuntu/backports](http://cloud9.somniumcomputing.com:81/ubuntu/backports) warty-backports main restricted universe multiverse

deb [http://cloud9.somniumcomputing.com:81/ubuntu/backports](http://cloud9.somniumcomputing.com:81/ubuntu/backports) warty-extras main restricted universe multiverse


```

Even though SF.net has AMD64 and PPC systems that I can compile on, they will **NOT** let me take over my 5.0GB Warty chroot environments. This pretty much makes them useless.

---

### Post by ember on 2005-01-26
First of all, great work. The backports project at last made it possible for me to switch more or less completely to linux with much lesser effort than I expected.

Yet at the moment, Thunderbird locales are missing - I've tested the new locale-de-package from hoary here on my computer and it seems to work. So maybe that could be of interesert for other people.

---

### Post by jdong on 2005-01-26
[QUOTE=ember]Yet at the moment, Thunderbird locales are missing - I've tested the new locale-de-package from hoary here on my computer and it seems to work. So maybe that could be of interesert for other people.[/QUOTE]

I will build ALL thunderbird 1.0 locales this week!

---

### Post by akurashy on 2005-01-26
[QUOTE=jdong]```

deb [http://cloud9.somniumcomputing.com:81/ubuntu/backports](http://cloud9.somniumcomputing.com:81/ubuntu/backports) warty-backports main restricted universe multiverse

deb [http://cloud9.somniumcomputing.com:81/ubuntu/backports](http://cloud9.somniumcomputing.com:81/ubuntu/backports) warty-extras main restricted universe multiverse


```

Even though SF.net has AMD64 and PPC systems that I can compile on, they will **NOT** let me take over my 5.0GB Warty chroot environments. This pretty much makes them useless.[/QUOTE]

when i reload with the repository there a lot of failing on the list O_o
i think is the host or soemting O_o

---

### Post by jdong on 2005-01-26
More info please? There may be "Ign" messages, which means that Release files are missing, or a certain branch is empty.

---

### Post by Suzan on 2005-01-26
Thank you for the great work! :-)

It's brilliant to have actual software in the stable Ubuntu release.

---

### Post by xpt on 2005-01-26
[QUOTE=jdong]More info please? [/QUOTE]

They might just be timeouts. I clicked on that url in my browser. Now it is 1.5 minutes later, and it still says "loading". I remember trying it yesterday and it failed at the end also. 

Could you mirror your repository in SF please? 

thanks

---

### Post by jdong on 2005-01-26
[QUOTE=xpt]They might just be timeouts. I clicked on that url in my browser. Now it is 1.5 minutes later, and it still says "loading". I remember trying it yesterday and it failed at the end also. 

Could you mirror your repository in SF please? 

thanks[/QUOTE]

Ok, if you browse it by hand, you need a trailing "/" on the URL -- it's standard procedure with apache2 and any WebDAV extension.

Well, I can't really mirror it in Sourceforge. The repository is about 1GB right now, well over the SF.net Project Services limit. My request for sandboxing has gone unresolved for well over a month now. Plus, they do not support atomicity, so during the mirror syncing process, you're more than likely to get corrupt downloads.


SF.net has been pretty awful for me in this project.


I've spoke with ubuntu-geek today, and am hoping  to be able to use our forum's server to host the SVN repository, provided that he can get us SVN support!

---

### Post by xpt on 2005-01-26
[QUOTE=xpt] Now it is 1.5 minutes later, and it still says "loading". I remember trying it yesterday and it failed at the end also. [/QUOTE]

Just FYI, 15 minutes passed, I finially get a untitled blank page.

---

### Post by jdong on 2005-01-26
You must refer to it as:
[http://cloud9.homelinux.net:81/ubuntu/backports/](http://cloud9.homelinux.net:81/ubuntu/backports/)

not just
[http://cloud9.homelinux.net:81/ubuntu/backports](http://cloud9.homelinux.net:81/ubuntu/backports)


Gentoo Apache2 is very anal about trailing slashes with DAV.

---

### Post by joede on 2005-01-27
[QUOTE=jdong]You must refer to it as:
[http://cloud9.homelinux.net:81/ubuntu/backports/](http://cloud9.homelinux.net:81/ubuntu/backports/)
[/QUOTE]

Doesn't work here too. I don't get a connect for three days now.

---

### Post by fng on 2005-01-27
```
Get:19 [http://cloud9.somniumcomputing.com](http://cloud9.somniumcomputing.com) warty-backports/main Release [93B]
Get:20 [http://cloud9.somniumcomputing.com](http://cloud9.somniumcomputing.com) warty-backports/restricted Packages [20B]
Get:21 [http://cloud9.somniumcomputing.com](http://cloud9.somniumcomputing.com) warty-backports/restricted Release [99B]
Get:22 [http://cloud9.somniumcomputing.com](http://cloud9.somniumcomputing.com) warty-backports/universe Packages [29.2kB]
Get:23 [http://cloud9.somniumcomputing.com](http://cloud9.somniumcomputing.com) warty-backports/universe Release [97B]
Get:24 [http://cloud9.somniumcomputing.com](http://cloud9.somniumcomputing.com) warty-backports/multiverse Packages [20B]
Get:25 [http://cloud9.somniumcomputing.com](http://cloud9.somniumcomputing.com) warty-backports/multiverse Release [99B]
``` 
works fine here

How is your /etc/apt/sources.list file?
I'll post here my section about backports :

```
##############Ubuntu Warty Backports################
deb http://cloud9.somniumcomputing.com:81/ubuntu/backports warty-backports main
deb http://cloud9.somniumcomputing.com:81/ubuntu/backports warty-backports restricted
deb http://cloud9.somniumcomputing.com:81/ubuntu/backports warty-backports universe
deb http://cloud9.somniumcomputing.com:81/ubuntu/backports warty-backports multiverse
```

---

### Post by jdong on 2005-01-27
Yeah, I'm transferring the entire repository from cloud9 to the Ubuntu forums, so the upload pipe on cloud9 is completely FILLED! 90% done as of now.

---

### Post by emperor on 2005-02-12
Looking for backports link this morning (4:50 am CST US) and it dead; even forum link. When will the repo be live again? I would like to upgrade kernel to 2.6.10 to fix shutdown problem and maybe Firefox to 1.0.

---

### Post by jdong on 2005-02-12
Hmm, we're up now. Don't know what happened.

---

### Post by emperor on 2005-02-12
I can see this now: [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/) but can not browse the repo.

---

### Post by jdong on 2005-02-12
Yeah working on that. Mod_ssl caused quite a bit of destruction.

---

