---
title: "Is this specific to System76 on Lexmark Drivers"
date: 2010-11-30
forum: System76 Support
---

### Post by RedRat on 2010-11-30
**I posted this over in "General Help" but got no takers. _*{Please see my last post on pg 2]*_**
                                                                Could this be something that is peculiar to a conflict with the Lexmark installation and the System76 drivers. I have a Serval Pro running 10.04LTS. 

I just  downloaded the 64bit Lexmark print driver for the Pro905 platinum  printer for installation on my 10.04 laptop. It is the legacy printer  driver (I don't know exactly what that means plus it is the only 64bit  driver there). When I follow the directions and click on the icon for  the shell script, then tell it to run in terminal I get the following  error: 
Lua error detected: While parsing install.lua: install.lua:118: Overflow detected: Not enough space for widget.

What is going on and what does it mean????

I note that this particular driver is for a system without the JRE (Java  runtime environment), mine has the JRE installed. could this be botching  the install??? I note that this is called a legacy driver by Lexmark.

---

### Post by HotShotDJ on 2010-11-30
I suspect you may be attempting to install a Windows driver, which wouldn't work in Linux. Lexmark printers are notorious for poor Linux support.  Most of them won't work at all Linux.  Perhaps you're lucky and have one of the exceptions.

In any case, please provide a link to the driver that you downloaded and I'll be able to give you more information.

NEVERMIND -- I did some searching for you, and I've found that Lexmark IS now providing Linux drivers.  What a great development!  The file you should have is called: lexmark-inkjet-legacy-1.0-1.amd64.deb.sh.tar.gz.  You want the one WITHOUT Java, since you should have Java installed through regular Ubuntu repositories.

I'll look at it further.  Stand by. :)

Ok... I've got it.  Make sure that the extracted file (lexmark-inkjet-legacy-1.0-1.amd64.deb.sh) is in your home directory -- it really can be anywhere that you have read/write permission as long as you know how to navigate to the directory in your terminal.  Open a terminal and type```
sh lexmark-inkjet-legacy-1.0-1.amd64.deb.sh
```Now just follow the instructions.

---

### Post by RedRat on 2010-11-30
> **HotShotDJ said:**
> I suspect you may be attempting to install a Windows driver, which wouldn't work in Linux. Lexmark printers are notorious for poor Linux support.  Most of them won't work at all Linux.  Perhaps you're lucky and have one of the exceptions.

In any case, please provide a link to the driver that you downloaded and I'll be able to give you more information.

NEVERMIND -- I did some searching for you, and I've found that Lexmark IS now providing Linux drivers.  What a great development!  The file you should have is called: lexmark-inkjet-legacy-1.0-1.amd64.deb.sh.tar.gz.  You want the one WITHOUT Java, since you should have Java installed through regular Ubuntu repositories.

I'll look at it further.  Stand by. :)

Ok... I've got it.  Make sure that the extracted file (lexmark-inkjet-legacy-1.0-1.amd64.deb.sh) is in your home directory -- it really can be anywhere that you have read/write permission as long as you know how to navigate to the directory in your terminal.  Open a terminal and type```
sh lexmark-inkjet-legacy-1.0-1.amd64.deb.sh
```Now just follow the instructions.
No go. Seems to start ok then I get this error message:
Lua error detected: While parsing install.lua: install.lua:118: Overflow detected: Not enough space for widget.

That is the driver I downloaded.

Any more ideas??? I appreciate the help.

---

### Post by HotShotDJ on 2010-11-30
> **RedRat said:**
> No go. Seems to start ok then I get this error message:
Lua error detected: While parsing install.lua: install.lua:118: Overflow detected: Not enough space for widget.

That is the driver I downloaded.

Any more ideas??? I appreciate the help.Exactly how far do you get in the installation process before you get the error?  So far, I'm able accept the license agreement and get a root authentication prompt.  I cancel at that point since I really don't want to install the software on my computer.  But if you're getting the error before that point, then I'm not able to replicate your problem and will have to look into it further.

---

### Post by RedRat on 2010-11-30
> **HotShotDJ said:**
> Exactly how far do you get in the installation process before you get the error?  So far, I'm able accept the license agreement and get a root authentication prompt.  I cancel at that point since I really don't want to install the software on my computer.  But if you're getting the error before that point, then I'm not able to replicate your problem and will have to look into it further.
Sorry not even close to you. This error comes up almost immediately, perhaps two or three steps. I get nothing. I tried running it with sudo command too. No go. Same error. I had no problem installing this driver on my 8.04 machine, it went very well.

---

### Post by HotShotDJ on 2010-11-30
> **RedRat said:**
> Sorry not even close to you. This error comes up almost immediately, perhaps two or three steps. I get nothing. I tried running it with sudo command too. No go. Same error. I had no problem installing this driver on my 8.04 machine, it went very well.
Ok.  I SUSPECT the problem is with the Java version. Please open System -> Administration -> Synaptic Package Manager.  You may have IcedTea / OpenJava installed.  While this works for many Java applications, it also causes problems for many others.  If it is not installed, install sun-java6-plugin (this will pull in everything else that it needs).  Then REMOVE everything installed related to IcedTea and OpenJava.

Now, try installing the printer driver again.  You do NOT need to run the installer as root.  It will request root privileges at the appropriate point.

---

### Post by RedRat on 2010-11-30
> **HotShotDJ said:**
> Ok.  I SUSPECT the problem is with the Java version. Please open System -> Administration -> Synaptic Package Manager.  You may have IcedTea / OpenJava installed.  While this works for many Java applications, it also causes problems for many others.  If it is not installed, install sun-java6-plugin (this will pull in everything else that it needs).  Then REMOVE everything installed related to IcedTea and OpenJava.

Now, try installing the printer driver again.  You do NOT need to run the installer as root.  It will request root privileges at the appropriate point.
Now I have real problems. I followed your directions and after the install of got the sun java plugin going. Then I remvoed IcedTea and the OpenJava stuff. When i tried to run the install of the driver, got the same error message. So I went to restart the machine and got a black screen with a blinking cursor in the upper left corner that is not responsive to anything. Did not get the customary Ubuntu or login. Turned the machine off and restarted it, same thing. What now?????

---

### Post by HotShotDJ on 2010-11-30
> **RedRat said:**
> So I went to restart the machine and got a black screen with a blinking cursor in the upper left corner that is not responsive to anything. Did not get the customary Ubuntu or login. Turned the machine off and restarted it, same thing. What now?????WHAT??  That makes no sense.  Java has nothing to do with starting up your system. I fear that you may have inadvertently removed something more than just Icedtea and OpenJava.  Can you remember anything about what you removed that might help me identify what it might have been?

I've removed those things on 4 different systems without a problem.

---

### Post by RedRat on 2010-11-30
> **HotShotDJ said:**
> WHAT??  That makes no sense.  Java has nothing to do with starting up your system. I fear that you may have inadvertently removed something more than just Icedtea and OpenJava.  Can you remember anything about what you removed that might help me identify what it might have been?

I've removed those things on 4 different systems without a problem.
I must agree with you. It appears that it is not even getting to GRUB. I am not getting any of the normal boot stuff that you see. I checked the BIOS and the boot is still the hard drive. Don't see how that could happen.

I looked at the list of stuff to be removed and it was only the OpenJava and IceTea. Something else more fundamental must have been touched in some way. I don't understand this either. Got any suggestions to get the system back?

---

### Post by HotShotDJ on 2010-11-30
> **RedRat said:**
> I must agree with you. It appears that it is not even getting to GRUB. I am not getting any of the normal boot stuff that you see. I checked the BIOS and the boot is still the hard drive. Don't see how that could happen.Hmmmm... Maybe something happened to grub or its configuration files.  But I just don't see HOW.  But let's try something first. Using your Ubuntu 10.04 LTS install CD, try to boot into a LiveCD session.  If that works, then we can reasonably rule out a hardware problem that just happened to hit at the same time we were working on the Lexmark driver issue.  While you are in the LiveCD session, try recovering GRUB -- you'll use the same method that one would use if a Windows installation trashed GRUB -- using these instructions: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Hopefully this will sort things out... If not, you may need to consider a complete reinstall of Ubuntu -- either 10.04 LTS or 10.10.  In either case, I need to go to bed soon, but I'll check back tomorrow after work to pick up where we left off.  BTW... I've created a fresh 10.04 LTS VM so that I can test some things out for you... but one thing at a time.

I'll talk to you again tomorrow evening!

---

### Post by RedRat on 2010-12-01
OK it was a loss of GRUB, I was in contact with System76 and received help there very quickly through an email. Very quick and good response from the guys at System76--I call this great support. Kudos.

---

### Post by HotShotDJ on 2010-12-01
> **RedRat said:**
> OK it was a loss of GRUB, I was in contact with System76 and received help there very quickly through an email. Very quick and good response from the guys at System76--I call this great support. Kudos.Excellent!  I'm glad that got sorted.  Were you able to get the Lexmark driver installed?

---

### Post by RedRat on 2010-12-01
> **HotShotDJ said:**
> Excellent!  I'm glad that got sorted.  Were you able to get the Lexmark driver installed?

The support guy gave me some new instructions about updating the repos. Here they are:
sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
sudo update-alternatives --config java

You'll want to select the one that's labeled as "/usr/lib/jvm/java-6-sun/jre/bin/java", not "/usr/lib/jvm/java-6-openjdk/jre/bin/java".

Then, finish up with these:

mkdir .mozilla/plugins
ln -s /usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so ~/.mozilla/plugins/libnpjp2.so

Then try the installer again. That ought to get it working.

However, the very first command returns an error, saying it needs a repository for an argument. Hmm. I have emailed him for a clarification and am waiting for a reply before I go ahead. I don't think I actually need to do this since this particular repo is already in my list. But before I do anything I want to get some reassurance from him. I am kinda gun shy now. Basically, i think all of that ought to be there but I want to be sure. I still don't know what caused GRUB to go away, but still there may be some other problems within the system. Just being conservative here, I have another printer that I can use in my system so I don't need the Lexmark right now.

---

### Post by RedRat on 2010-12-02
Ok went ahead and ran the other commands because that particular repo is in my sources list. However, even after getting the .so file into the .mozilla/plugins folder, the Lexmark Installer still does not install. Still get that same error I reported.

---

### Post by RedRat on 2010-12-10
OK after much tomfoolery, I got a "solution" to installing the Lexmark driver from the folks at Lexmark. You can try this.

For the sake of simplicity, move the file lexmark-inkjet-legacy-1.0-1.amd64.deb.sh to the Desktop. Now do the following:

1. Open the TERMINAL type in "cd Desktop" and enter command: ```
sudo sh lexmark-inkjet-legacy-1.0-1.amd64.deb.sh --noexec --target temp
```

2. Then key in "cd temp" and "temp ls" commands

3. Then enter command "```
sudo tar xvvf instarchive_all --lzma
```

4. Then enter the "```
sudo dpkg -i lexmark-legacy-wsu-1.0-1.amd64.deb
```" 

5. Then enter the ```
sudo dpkg -i lexmark-inkjet-legacy-1.0-1.amd64.deb
```

6. The installer should run and just follow thru whats on the installation window

Comment: When I did this, there was no installation window opening as per #6 above, whether this is my machine and its particular configuration I don't know. However, the drivers seem to be in place. You can then go to System>Administration>Printing and then "Add Printer". You choose Network Printer. It takes a few minutes to find the printer via the wireless, but it does find it and correctly identifies the printer. Then you have it look for the drivers, it should find them correctly and you should be able to print a test page via CUPS. I do have problems running the installed Lexmark Printing Toolbox, this "runs" but hangs. I clearly do not have all the utilities that I would like, e.g., ink level etc. but it does print and works.  If you have any questions you can contact the Lexmark Linux guy at Linux Phone Support through 1-800-834-7814, Mondays to Fridays, 8 am - 11 pm EST.

I hope that this might help others who might have run into this problem.

---

