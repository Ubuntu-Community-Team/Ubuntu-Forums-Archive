---
title: "Server or Desktop? I want both!"
date: 2006-06-12
forum: Server Platforms
---

### Post by weiqi on 2006-06-12
I am a .deb and Ubuntu newbie (but not new to Linux or UNIX).  I want to install Ubuntu to use both as a server (apache, php, mysql, dns, sshd, sftpd, smtp) as well as a desktop.  It looks like I could install Server or Desktop and then add to it.  Would I be better off starting with Desktop?  Any opinions?

---

### Post by mrcowcow on 2006-06-12
I would reccomend starting with the Ubuntu server install cd, if you have an internet connection, doing the lamp installation, and then doing a sudo apt-get install ubuntu-desktop once it is installed. That gives you a lamp server, and a desktop. From there you can add whatever other servers/programs you need.

---

### Post by weiqi on 2006-06-12
I do have an internet connection and it sounds like **sudo apt-get install ubuntu-desktop** may work about as nicely or identically as a Desktop install.  Does apt-get install ubuntu-desktop essentially get everything?  Maybe this is a question for another forum....

---

### Post by mrcowcow on 2006-06-12
It looks like it installs everything that is installed in a regular desktop install. You can find a list of all the packages included at [http://packages.ubuntu.com/dapper/base/ubuntu-desktop]("http://packages.ubuntu.com/dapper/base/ubuntu-desktop"). It should be identical to a desktop install, although you might have to do a little more configuring to get everything to work.

---

### Post by weiqi on 2006-06-12
Thanks, Mr. Cow -- as you suggeted I first installed Server and then did apt-get install ubuntu-desktop on top of it.  I got some error messages, especially relating to font configuration files, but overall, it looks very good.  I am writing this from the new combined server-desktop.  Thanks!

---

### Post by sleestak on 2006-06-27
I ran through this as well with the same errors, have you noticed any issues?

---

### Post by weiqi on 2006-06-27
The errors went by quickly and mostly concerned being unable to write font configuration files.  I have't done much with fonts yet, so haven't seen those problems.  Also, as I have not used Desktop I can't tell when something does not "work" if would in a regular install.

After doing the install with Server first and then adding Desktop, I thought it might be better to do it the other way around since so much more comes with Desktop than server.

I'd be interested in hearing about other approaches or experiences people have had installing Server and Desktop togother.  Also, can anyone point me to where I can learn more about **apt-get install** such as where the error messages are logged?

---

### Post by houstonbofh on 2006-06-29
I did several installs on a server.  (other issues, then a HD dies...  Sigh)  Right now there are desktop tags, but no LAMP tag.  So it is MUCH easier to install a LAMP server then *apt-get install ubuntu-desktop* or *apt-get install xbuntu-desktop* or *...kbuntu-desktop* on top.  the *buntu-desktop packages are empty packages with dependencies.  This means removing them will **not** remove the desktop.  Use aptitude if you think you will have second thoughts.  Or, apt-get, and then remove unneeded components. (like APIC and sound)

---

### Post by houstonbofh on 2006-06-29
[QUOTE=sleestak]I ran through this as well with the same errors, have you noticed any issues?[/QUOTE]
I forgot...  Those errors are normal for a first run of X.  It is just hidden from the user in a desktop install.

---

### Post by happysinger on 2006-09-28
Hello, everyone!

Thanks to everyone who's posted in this thread: it's answered a lot of my questions: but not all... :-(

I have the same agenda: combining the desktop install with LAMP so I can do my graphics in the Gimp, scripting in gedit, stick my content in PHPMyAdmin and test the whole thing in Firefox, before I send it all to my host.

In contrast, however, I DON'T have a home internet connection. I could perhaps get a friend to download the server ISO, and ShipIt have sent me the desktop CD.

My questions: A) could I install the server and use apt-get or some other method to install the desktop on top, using the desktop install CD as the source?
              B) Is there a better way to do it? :-)

Thank you ever so much to anyone who takes the time to answer.

Sorry for not posting this in a newbie forum, but I guessed it would be more on-topic here.

Cheers then,

Dave

---

### Post by genesis[OFT] on 2006-09-28
I imagine you could...

You'd have to remove all instances of websites or external locations in your /etc/apt/sources.list file though, so JUST the ubuntu CD is listed.

Make a backup of the file first though :D

---

### Post by happysinger on 2006-09-30
Hi there!

Thanks for the answer! I will try as soon as I can find a mate who can download me the ISO (I can hardly do it from work... :-) )

---

### Post by PanzerMKZ on 2006-09-30
see that makes me wonder if it would be possible to run server install and just change the sources file to the desktop dvd.  Should not have to commit out the internet sources as it would not be able to connect to them anyway.  The local source is first on the list anyway.


Panzer

---

### Post by Blue Backbite on 2007-12-12
Anyone happen to know how to install it from the Ubuntu Desktop CD? (in the server Terminal)

---

### Post by rsambuca on 2007-12-12
Do you realize this thread is over a year old?

Anyways, the Desktop Cd can only be used to install the Desktop edition.

---

### Post by HermanAB on 2007-12-12
Well, since it is Yule Tide, you should have plenty of time on your hands, so get an external 56kbps modem and dial up to your friend's ISP for the downloads.

Cheers,

H.

---

### Post by jvonmitchell on 2007-12-27
when I do the sudo apt-get install ubuntu-desktop, apt-get tells me that ubuntu-desktop is a non-existent package.  I've done a sudo apt-get update, is there any other way to expand my software sources.

---

