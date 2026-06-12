---
title: "Wubi, failure to establish an account"
date: 2013-02-17
forum: Ubuntu Development Version
---

### Post by empis on 2013-02-17
Hello, I became taka very strange thing, I have installed wubi ubuntu 13.04 (if I'm not mistaken so still did not work), it would not bother me but I did not create this account, no idea what could be the root password (I tried what I contractors during the installation), I signed up as a guest but he can not quite nothing (or log on wifi) without root permissions. Grub menu does not trigger. Through wubi I tried reinstalling 3 times but still the same. It happened to you? How do I solve this? Thank you for your reply.

---

### Post by Mark Phelps on 2013-02-17
Version 13.04 is an ALPHA -- which you shouldn't even attempt using unless you are very experienced with using Ubuntu.  Early versions are known to have bugs.

You would do better using 12.10, or even then, possibly 12.04.

---

### Post by Bucky Ball on 2013-02-17
*Thread moved to **Ubuntu +1 (Raring Ringtail)**.*

+1 to what Mark Phelps has said. As a new user, don't start with 13.04. Still testing and not released until April. Not the place to jump in unless you are willing to share all bugs with the developers and are prepared for a very steep learning curve. 

Better to start with the current and stable long term support release 12.04 LTS until you know your way around.

---

### Post by kevpan815 on 2013-02-17
Empis, when posting a message about a Pre-Release Build (which is an Alpha, Beta, and/or Nightly Build from [http://ISO.QA.UBUNTU.COM/](http://ISO.QA.UBUNTU.COM/) please always post your message in the Ubuntu +1 Forum, that way you can get help from fellow Ubuntu Pre-Release Testers the Regular Ubuntu + 1 Posters who test Ubuntu + 1 Builds on a Regular Basis and you won't get Yelled at by people like Mark Phelps who don't understand that there is a Regular Crowd of people who Test Ubuntu +1 Builds and and don't even get paid to do it.

As for your problem, I have tried out the AMD 64 13.04 WUBI.EXE and am having the same problem currently, however I have also noticed that no one else has posted a Report about the Bug @ ISO.QA.UBUNTU.COM yet, so I am NOT really sure if we are supposed to post Bugs about 13.04 WUBI.EXE yet or if we need to WAIT UNTIL 13.04 HITS BETA STATUS. The main reason why I am using it is so that I can Dual Boot between Windows 8 Pro Edition (on which I am currently Testing Avast 8.0 Public Beta) and run Ubuntu 13.04 at the same time. Maybe Cariboo907 can tell us whether we should Report the Bug or wait until 13.04 hits Beta Status. In the meantime, you should be able to Login with the Guest Account. I was.

---

### Post by kevpan815 on 2013-02-17
> **Bucky Ball said:**
> *Thread moved to **Ubuntu +1 (Raring Ringtail)**.*

+1 to what Mark Phelps has said. As a new user, don't start with 13.04. Still testing and not released until April. Not the place to jump in unless you are willing to share all bugs with the developers and are prepared for a very steep learning curve. 

Better to start with the current and stable long term support release 12.04 LTS until you know your way around.

Bucky Ball, when I started out here I jumped right into Ubuntu 7.10 Pre-Release Testing. And for good reason: Ubuntu 7.04 would NOT run on the Dell Computer I had at the time. Not to mention the fact that I already had previous Pre-Release Testing Experience on Windows with Microsoft at the time. He may as well.

---

### Post by kevpan815 on 2013-02-17
> **kevpan815 said:**
> Empis, when posting a message about a Pre-Release Build (which is an Alpha, Beta, and/or Nightly Build from [http://ISO.QA.UBUNTU.COM/](http://ISO.QA.UBUNTU.COM/) please always post your message in the Ubuntu +1 Forum, that way you can get help from fellow Ubuntu Pre-Release Testers the Regular Ubuntu + 1 Posters who test Ubuntu + 1 Builds on a Regular Basis and you won't get Yelled at by people like Mark Phelps who don't understand that there is a Regular Crowd of people who Test Ubuntu +1 Builds and and don't even get paid to do it.

As for your problem, I have tried out the AMD 64 13.04 WUBI.EXE and am having the same problem currently, however I have also noticed that no one else has posted a Report about the Bug @ ISO.QA.UBUNTU.COM yet, so I am NOT really sure if we are supposed to post Bugs about 13.04 WUBI.EXE yet or if we need to WAIT UNTIL 13.04 HITS BETA STATUS. The main reason why I am using it is so that I can Dual Boot between Windows 8 Pro Edition (on which I am currently Testing Avast 8.0 Public Beta) and run Ubuntu 13.04 at the same time. Maybe Cariboo907 can tell us whether we should Report the Bug or wait until 13.04 hits Beta Status. In the meantime, you should be able to Login with the Guest Account. I was.

I forgot to mention that I was able to get the Internet to work in the Guest Account by Turning On my Apple IPhone 5's Personal Hotspot and then I Plugged the Apple IPhone 5 into the Computer using the Apple Lightning to USB Connector into the Computer's USB 2.0 Port. So unfortunately you may have to use a Wired Connection like an Ethernet Cable Internet Connection to Access the Internet in the Guest Account.

---

### Post by Bucky Ball on 2013-02-17
> **kevpan815 said:**
> Bucky Ball, when I started out here I jumped right into Ubuntu 7.10 Pre-Release Testing. And for good reason: Ubuntu 7.04 would NOT run on the Dell Computer I had at the time. Not to mention the fact that I already had previous Pre-Release Testing Experience on Windows with Microsoft at the time. He may as well.

Unsure what this has to do with OP. There are variables and here are some:

1/ Experience level;
2/ OP is using Wubi;
3/ This may not have anything to do with the fact that the stable LTS will not install, as was your case;
4/ Hardware.

For a new user, possibly without the experience you had when you plunged right in, the LTS release, which is currently known to be stable, is a good place to start.

I did mention this in my post BTW:

> Not the place to jump in unless you are willing to share all bugs with the developers and are prepared for a very steep learning curve. 

which you may have overlooked but relates directly to what you have posted.

By reading the first post it is clear that Microsoft tester/expert/guru or not, the OP is having serious trouble with their Wubi install in Linux Ubuntu 13.04, a testing release. They also say nothing about being aware 13.04 is unreleased, therefore testing is probably not the intention. Might pay to eliminate the idiosycracies of that and start with a release that is familiar and known to be stable and working on most hardware setups.

Perhaps the OP can clarify some of this but in the end it's up to them which path they take. We have made the differences between the two pretty clear at this point I'd say. Now, back on topic, 'Wubi, failure to establish an account.' ;)

PS: The OP may be 'he' or 'she'.

---

### Post by bcbc on 2013-02-18
It's more likely that the OP didn't intend to install 13.04. This seems to happen now and then, but no one has ever done the bug report and so there is no log file to prove it...

But Wubi goes after the diskimage from this address (for 12.10, assuming 32bit):
```
diskimage=http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-i386.tar.xz
```

If for whatever reason, the address is not resolved - e.g. temporary timeout or server unreachablee - it assumes that it's the dev release and then goes after this image:
```
diskimage2=http://cdimage.ubuntu.com/wubi/current/i386.tar.xz
```

Which, as you can imagine, is the 13.04 current disk image.

For 64 bit there's a similar problem except it goes for:
```
diskimage2=http://cdimage.ubuntu.com/wubi/current/amd64.tar.xz
```
Take a look and you'll see it's dated: 17-Feb-2013 07:33  550M 

Anyway - I'd guess this is what happened. It would be great to see the log file (it's in the %TEMP% directory and is called wubi-12.10-rev273.log) so this can be confirmed. Or just [create a bug report]("https://bugs.launchpad.net/wubi/+filebug") and attach the log.

---

### Post by kevpan815 on 2013-02-18
> **bcbc said:**
> It's more likely that the OP didn't intend to install 13.04. This seems to happen now and then, but no one has ever done the bug report and so there is no log file to prove it...

But Wubi goes after the diskimage from this address (for 12.10, assuming 32bit):
```
diskimage=http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-i386.tar.xz
```

If for whatever reason, the address is not resolved - e.g. temporary timeout or server unreachablee - it assumes that it's the dev release and then goes after this image:
```
diskimage2=http://cdimage.ubuntu.com/wubi/current/i386.tar.xz
```

Which, as you can imagine, is the 13.04 current disk image.

For 64 bit there's a similar problem except it goes for:
```
diskimage2=http://cdimage.ubuntu.com/wubi/current/amd64.tar.xz
```
Take a look and you'll see it's dated: 17-Feb-2013 07:33  550M 

Anyway - I'd guess this is what happened. It would be great to see the log file (it's in the %TEMP% directory and is called wubi-12.10-rev273.log) so this can be confirmed. Or just [create a bug report]("https://bugs.launchpad.net/wubi/+filebug") and attach the log.

Actually, I got the 13.04 WUBI.EXE from ISO.QA.UBUNTU.COM which has a Download Link from *.Canonical.com, Just FYI.

---

### Post by kevpan815 on 2013-02-18
> **bcbc said:**
> It's more likely that the OP didn't intend to install 13.04. This seems to happen now and then, but no one has ever done the bug report and so there is no log file to prove it...

But Wubi goes after the diskimage from this address (for 12.10, assuming 32bit):
```
diskimage=http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-i386.tar.xz
```

If for whatever reason, the address is not resolved - e.g. temporary timeout or server unreachablee - it assumes that it's the dev release and then goes after this image:
```
diskimage2=http://cdimage.ubuntu.com/wubi/current/i386.tar.xz
```

Which, as you can imagine, is the 13.04 current disk image.

For 64 bit there's a similar problem except it goes for:
```
diskimage2=http://cdimage.ubuntu.com/wubi/current/amd64.tar.xz
```
Take a look and you'll see it's dated: 17-Feb-2013 07:33  550M 

Anyway - I'd guess this is what happened. It would be great to see the log file (it's in the %TEMP% directory and is called wubi-12.10-rev273.log) so this can be confirmed. Or just [create a bug report]("https://bugs.launchpad.net/wubi/+filebug") and attach the log.

P.S. This problem that I am having (which was the exact same problem that he/she said they were having is NOT from 12.10 WUBI.EXE-REV-273, rather it is from the 13.04 WUBI.EXE-REV-275 which can be found at ISO.QA.UBUNTU.COM, just click on 13.04 Nightly Build and it will be near the bottom of the List.

---

### Post by bcbc on 2013-02-18
> **kevpan815 said:**
> Actually, I got the 13.04 WUBI.EXE from ISO.QA.UBUNTU.COM which has a Download Link from *.Canonical.com, Just FYI.

I didn't say it's not possible to test the 13.04 wubi. I do make assumptions based on where the post is made, the content of the post and a lot of reading between the lines, and if those assumption are wrong, then the OP is encouraged to clarify. But it's important that other posters know that this is a possibility and has happened in the past e.g. [http://ubuntuforums.org/showpost.php?p=12501886&postcount=4](http://ubuntuforums.org/showpost.php?p=12501886&postcount=4)

But needless to say, it wasn't addressed to you.

kevpan, I can't reply to your private message as I assume you have switched off that option. However without going into too much detail, you are welcome to explain your reasoning, or report the post.

---

### Post by mr john on 2013-03-15
I have the same issue. I was hoping to be able to nosey into 13.04 without partitioning my computer.   I've tried using a vm but its a bit laggy. If this issue cannot be resolved at the moment then I can go back to 12.10 and wait for this to be fixed.

If anyone is interested,  the output of cat /etc/password indicated that my user had never been created by the installer. I cannot connect to my wifi or do anything as user.

Wubis is part of the 13.04 ISO released for testing, so I consider it relevant.

---

### Post by bcbc on 2013-03-15
> **mr john said:**
> I have the same issue. I was hoping to be able to nosey into 13.04 without partitioning my computer.   I've tried using a vm but its a bit laggy. If this issue cannot be resolved at the moment then I can go back to 12.10 and wait for this to be fixed.

If anyone is interested,  the output of cat /etc/password indicated that my user had never been created by the installer. I cannot connect to my wifi or do anything as user.

Wubis is part of the 13.04 ISO released for testing, so I consider it relevant.
Please file a bug and attach your log file: [https://bugs.launchpad.net/wubi/+filebug](https://bugs.launchpad.net/wubi/+filebug)

---

### Post by mr john on 2013-03-15
Possible bug reported:

[https://bugs.launchpad.net/wubi/+bug/1155704](https://bugs.launchpad.net/wubi/+bug/1155704)

Could just be that Wubi 13.04 isn't ready yet for testing.

---

### Post by bcbc on 2013-03-15
> **mr john said:**
> Possible bug reported:

[https://bugs.launchpad.net/wubi/+bug/1155704](https://bugs.launchpad.net/wubi/+bug/1155704)

Could just be that Wubi 13.04 isn't ready yet for testing.
Great. And you got some developer feedback already. Must be a record...

---

### Post by mr john on 2013-03-18
That's the beauty of open source ;)

---

