---
title: "Netatalk 2.1 Packages for Ubuntu | Any other ideas?"
date: 2010-05-11
forum: Server Platforms
---

### Post by Denmaru on 2010-05-11
First off all, I'm quite irate over the lack of netatalk 2.1 packages for Ubuntu. I mean, seriously - it's one of the major LAN-protocols, 2.1 finally gives us extended attributes support, and it's been out for quite some time.

Yet, it isn't even considered for... maverik? Why isn't there a package already?

So, with that out of the way - I had to install netatalk 2.1 ASAP. I searched for a *.deb, but only found one for Debian (guys... even Debian gets it faster? Really?!)


But after installing the Debian-Package, it won't let me login. On the Mac-Client, it merely says that the login is incorrect (when in fact, it is), and I get a

```
11.05.10 10:20:01	kernel	ASP_TCP do_thread_read: no reqInfo found for reqID 1
```

on MacOS X's console.

I also did a 
```
find -H / -name .AppleD* -exec rm -rf {} \;
```
to eliminate all the .AppleDB files.

Everything is fine with Ubuntu's 2.0.5 package, though.

Installing using the dh_make simply doesn't work. It merely creates a deb with a few kilobytes that installs the documentation.

So, I resorted to rpms. Luckily, I found a SRPM at [Link]("http://www003.upp.so-net.ne.jp/hat/netatalk/rpm.html").

I installed it using alien, and ... nothing. It wont even let me log in anymore.

So, back to 2.0.5 for the while being. But do you have any other ideas, instead of

*) "Just use Samba" - no, because it's slow and I want to use TimeMachine without hacks.

---

### Post by windependence on 2010-05-11
Since Time Machine is nothing more than a fancy GUI for rsync, isn't there a way you could adapt? I mean, I thought netatalk? how old a Mac does this guy have? ....and yes, I'm typing this on a unibody Macbook Pro.

-Tim

---

### Post by Denmaru on 2010-05-11
Erm, thanks for the reply, but: No. My clients (and me) simply want to use TimeMachine, and nothing else for their backup, and the RAID-5 on this server for storage.

---

### Post by Denmaru on 2010-05-11
Wait, what? There is a 2.1.1 package for... Maverick in development? And it's only been 42 hours since the upload? Nice.

But how do I get this package? >.<

---

### Post by jd65pl on 2010-05-11
I believe 2.1 has only been out of beta for 2 weeks. This would have conflicted with the ubuntu release cycle. There are currently no binary packages for [netatalk 2.1]("https://launchpad.net/ubuntu/maverick/+source/netatalk")

Yes extended attributes are useful, if you are that desperate for this functionality why not compile from source rather than trying to hash the rpm? Failing that go get the deb from debian sid and use that.

---

### Post by ReturnPrivacy on 2010-08-31
Hi all,
I have to agree. A lot of us are new to Ubuntu, and have no idea what "repository, depository, compile, hairballs, binaries, dependencys etc." all mean. I am using 8.04, and trying to find Netatalk to install and have AFP, so I can have Time Machine backup from my iMac to my Ubuntu computer. This should be simple, right? I went to Add/Remove, and there is no Netatalk at all. I found it on sourceforge, and downloaded it, but it is a .tar.bz2 file. I clicked, and it is there, but nothing happens. I hit "extract" and it just gives a new box, showing folders and files? I found a file names "install.sh", so I clicked on that, and nothing happened. I don't understand why you make it so hard to install a program in Ubuntu? Can somebody make this "netatalk" thing install so I have AFP working?:confused:

---

