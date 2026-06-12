---
title: "How To: Use USAA Deposit@Home on 10.04 Lucid"
date: 2010-04-15
forum: Tutorials
---

### Post by wbar2 on 2010-04-15
For those who bank with USAA and use the Deposit@Home feature, you probably have realized that you cannot use it on Linux machines. This tutorial will show you how to make it work on Ubuntu 10.04 and 10.10.

[SIZE="4"]**[COLOR="Sienna"]1. Uninstall IcedTea Plugin[/COLOR]**[/SIZE]

First you need to remove the IcedTea plugin if it is installed. In Synaptic Package Manager (System - Administration - Synaptic Package Manager) type "icedtea6-plugin" in the Quick Search box. If it is installed the box will be green. If that's the case, click the box and select "Mark for Complete Removal." Then click the Apply button.

[IMG]http://dl.dropbox.com/u/3050866/usaa%20headercontrol/usaa1.png[/IMG]

*[COLOR="DarkSlateBlue"]Alternatively[/COLOR]* you can simply go to the Terminal (Applications - Accessories - Terminal) and type:
```
sudo apt-get remove icedtea6-plugin
```

[SIZE="4"]**[COLOR="Sienna"]2. Enable Partner Repository[/COLOR]**[/SIZE]

In order to install Sun Java, make sure the [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) repository is enabled. You can do this in the Synaptic Package Manager by going to the Settings menu and clicking Repositories. Click the Other Software Tab. Make sure there is a checkmark next to "http://archive.canonical.com/ubuntu lucid partner". Then close the window.

[IMG]http://dl.dropbox.com/u/3050866/usaa%20headercontrol/usaa2.png[/IMG]

*[COLOR="DarkSlateBlue"]Alternatively[/COLOR]* you can go to the Terminal and type the following which enables all repositories in your list:
```
sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
```

[SIZE="4"]**[COLOR="Sienna"]3. Install Sun Java[/COLOR]**[/SIZE]

You can install Sun Java in Synaptic Package Manager by doing a quick search for "sun-java6". You should see the four following packages among the list: sun-java6-jre, sun-java6-bin, sun-java6-plugin, and sun-java6-fonts. Click the box next to each one and select "Mark for Installation." After doing this for all four packages click the Apply button.

[IMG]http://dl.dropbox.com/u/3050866/usaa%20headercontrol/usaa5.png[/IMG]

[COLOR="Navy"]*Alternatively*[/COLOR] you can go to the Terminal and type:
```
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin sun-java6-fonts
```

[COLOR="DarkSlateBlue"]*Or*[/COLOR], you can simply **_[click here]("apt:sun-java6-jre,sun-java6-bin,sun-java6-plugin,sun-java6-fonts")_** to install them.

[SIZE="4"]**[COLOR="Sienna"]4. Verify Sun Java Installation[/COLOR]**[/SIZE]

Restart Firefox. In the location bar in Firefox (not the Terminal) type:
```
about:plugins
```

You should see Java installed! It should say "Java(TM) Plug-in 1.6.0_20."

[IMG]http://dl.dropbox.com/u/3050866/usaa%20headercontrol/usaa6.png[/IMG]

**[SIZE="4"][COLOR="Sienna"]5. Install HeaderControl to Firefox.[/COLOR][/SIZE]**

Go to [https://addons.mozilla.org/en-US/firefox/addon/11327](https://addons.mozilla.org/en-US/firefox/addon/11327) and add the HeaderControl add-on for Firefox.

Restart Firefox. In Firefox go to Tools - Addons. Go to HeaderControl and select the Preferences button. Click the Add button. Type in usaa.com for the Suffix. Click the Useragent tab. Check Mangle HTTP 'UserAgent.' In the dropdown menu select Custom Useragent. In the box below it type the following:

```
Mozilla/5.0 (Macintosh; U; PPC Mac OS X Mach-O; en-US; rv:1.8.0.3) Gecko/20060426 Firefox/1.5.0.3
```

[IMG]http://dl.dropbox.com/u/3050866/usaa%20headercontrol/usaa4.png[/IMG]

Click OK. Click OK again.

**[SIZE="4"][COLOR="Sienna"]6. Scan in Checks[/COLOR][/SIZE]**

You're finished! Now you should be able to go the USAA website and use Deposit@Home. Just follow the instructions there. You will need to scan your checks in first, then upload them to the site.

**Option A: Scan with XSane**

First, install Xsane Image Scanner. You can use the Synaptic Package Manager as described above or simply _[click here.]("apt:xsane")_

Then go to Applications - Graphics - XSane Image Scanner. Select the appropriate scanner if asked. You should see several windows. The only windows you are concerned with are the main window and the standard options window.

In the main window you will see a dropdown menu that says 75. This is the dpi. Change it to 200.

[IMG]http://dl.dropbox.com/u/3050866/usaa%20headercontrol/usaa7.png[/IMG]

In the standard options window you will see a Color Depth dropdown menu. It will say 24-bit Color. Change this to 8-bit Grayscale.

[IMG]http://dl.dropbox.com/u/3050866/usaa%20headercontrol/usaa8.png[/IMG]

In the main window now click the scan button.

[IMG]http://dl.dropbox.com/u/3050866/usaa%20headercontrol/usaa9.png[/IMG]

Save the image to your desktop as a jpeg. Do this for the front and the back of the check, following the instructions on the USAA website. You should now be able to upload your checks on the USAA website. Make sure to follow their instructions!

**Option B: Use a script to automate check scanning**

Thanks to isotherm for [_his post_]("http://ubuntuforums.org/showpost.php?p=9552746&postcount=21") about a script he wrote to automate the process! You can _[download the script here]("http://ubuntuforums.org/attachment.php?attachmentid=162593&d=1278420975")_. Check his post for more details.

---

### Post by lkbrow1 on 2010-04-20
I have been doing it the hard way with XP running in a Virtual Box.  Thanks for the info.

Larry

---

### Post by gbear14275 on 2010-04-20
Hey guys,

Might not have to do this crap for much longer.

[http://www.linuxinsider.com/story/The-Bank-the-Linux-User-and-the-9-Month-Call-for-Help-69811.html](http://www.linuxinsider.com/story/The-Bank-the-Linux-User-and-the-9-Month-Call-for-Help-69811.html)

If you want to show support, the bank rep currently making progress is Mark Voelkel if you want to write to him and levy his support.

---

### Post by LewRockwell on 2010-04-20
> **gbear14275 said:**
> Hey guys,

Might not have to do this crap for much longer.

[http://www.linuxinsider.com/story/The-Bank-the-Linux-User-and-the-9-Month-Call-for-Help-69811.html](http://www.linuxinsider.com/story/The-Bank-the-Linux-User-and-the-9-Month-Call-for-Help-69811.html)

If you want to show support, the bank rep currently making progress is Mark Voelkel if you want to write to him and levy his support.

What is Mark Voelkel's contact and mailing information?

Perhaps he would like to do an interview?

.

---

### Post by gbear14275 on 2010-04-22
lew,

if you are a usaa member just write him per the message center.

if not you'll probably have to go through their pa shop.

---

### Post by arrrghhh on 2010-04-24
So I tried to follow this guide, and java failed.  So I installed it from the sun version from the partner repo.  So now the java applet works up until I hit submit.  It goes to the "Deposit is processing" screen just like normal, but does not ever move past it.

I guess for now I will continue to use XP w/VirtualBox :(

---

### Post by wbar2 on 2010-04-26
> **arrrghhh said:**
> So I tried to follow this guide, and java failed.  So I installed it from the sun version from the partner repo.  So now the java applet works up until I hit submit.  It goes to the "Deposit is processing" screen just like normal, but does not ever move past it.

I guess for now I will continue to use XP w/VirtualBox :(

What version of Java are you using?

---

### Post by wbar2 on 2010-05-06
I just went through the tutorial again after a clean install, and there was an error, but it has been corrected.

---

### Post by T-Keith on 2010-05-06
Does this only work in 32 bit?   I am running 64bit Kubuntu and I swear I got it to work just before upgrading to 10.04.  Now it says I don't meet minimum system requirements.  I just installed Java through the software management utility, do I need to do all these steps?  My about:plugins says the Java plugin is 1.6 could that be the problem?

thanks,
-Keith

---

### Post by wbar2 on 2010-05-07
> **T-Keith said:**
> Does this only work in 32 bit?   I am running 64bit Kubuntu and I swear I got it to work just before upgrading to 10.04.  Now it says I don't meet minimum system requirements.  I just installed Java through the software management utility, do I need to do all these steps?  My about:plugins says the Java plugin is 1.6 could that be the problem?

thanks,
-Keith

The 32-bit plugin should work for the 64-bit machine, but specific instructions can be found here for installing the 64-bit version: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java).

I'm not exactly sure how the version numbering works for Java. I think the platform has a version number and the plugin has a version number (the 1.6 you mentioned). The repositories in Synaptic may contain a slightly older version of Sun Java. The newest version is Version 6 Update 20, which I have tested to work on USAA.

---

### Post by T-Keith on 2010-05-07
I followed those instructions and I get as far as the java applet.

I get this error:

Java Plug-in 1.6.0_20
Using JRE version 1.6.0_20-b02 Java HotSpot(TM) 64-Bit Server VM
User home directory = /home/keith
----------------------------------------------------
c:   clear console window
f:   finalize objects on finalization queue
g:   garbage collect
h:   display this help message
l:   dump classloader list
m:   print memory usage
o:   trigger logging
q:   hide console
r:   reload policy configuration
s:   dump system and deployment properties
t:   dump thread list
v:   dump thread stack
x:   clear classloader cache
0-5: set trace level to <n>
----------------------------------------------------


load: class com.usaa.bank.homedeposit.applet.ScanApplet.class not found.
java.lang.ClassNotFoundException: com.usaa.bank.homedeposit.applet.ScanApplet.class
	at sun.plugin2.applet.Applet2ClassLoader.findClass(Unknown Source)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at sun.plugin2.applet.Plugin2ClassLoader.loadCode(Unknown Source)
	at sun.plugin2.applet.Plugin2Manager.createApplet(Unknown Source)
	at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Unknown Source)
	at java.lang.Thread.run(Unknown Source)
Caused by: java.io.IOException: open HTTP connection failed:[https://www.usaa.com/inet/bank_deposit/applet/com/usaa/bank/homedeposit/applet/ScanApplet/class.class](https://www.usaa.com/inet/bank_deposit/applet/com/usaa/bank/homedeposit/applet/ScanApplet/class.class)
	at sun.plugin2.applet.Applet2ClassLoader.getBytes(Unknown Source)
	at sun.plugin2.applet.Applet2ClassLoader.access$000(Unknown Source)
	at sun.plugin2.applet.Applet2ClassLoader$1.run(Unknown Source)
	at java.security.AccessController.doPrivileged(Native Method)
	... 7 more
Exception: java.lang.ClassNotFoundException: com.usaa.bank.homedeposit.applet.ScanApplet.class

---

### Post by wbar2 on 2010-05-10
> **T-Keith said:**
> I followed those instructions and I get as far as the java applet.

I get this error:

Java Plug-in 1.6.0_20
Using JRE version 1.6.0_20-b02 Java HotSpot(TM) 64-Bit Server VM
User home directory = /home/keith
----------------------------------------------------
c:   clear console window
f:   finalize objects on finalization queue
g:   garbage collect
h:   display this help message
l:   dump classloader list
m:   print memory usage
o:   trigger logging
q:   hide console
r:   reload policy configuration
s:   dump system and deployment properties
t:   dump thread list
v:   dump thread stack
x:   clear classloader cache
0-5: set trace level to <n>
----------------------------------------------------


load: class com.usaa.bank.homedeposit.applet.ScanApplet.class not found.
java.lang.ClassNotFoundException: com.usaa.bank.homedeposit.applet.ScanApplet.class
	at sun.plugin2.applet.Applet2ClassLoader.findClass(Unknown Source)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at sun.plugin2.applet.Plugin2ClassLoader.loadCode(Unknown Source)
	at sun.plugin2.applet.Plugin2Manager.createApplet(Unknown Source)
	at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Unknown Source)
	at java.lang.Thread.run(Unknown Source)
Caused by: java.io.IOException: open HTTP connection failed:[https://www.usaa.com/inet/bank_deposit/applet/com/usaa/bank/homedeposit/applet/ScanApplet/class.class](https://www.usaa.com/inet/bank_deposit/applet/com/usaa/bank/homedeposit/applet/ScanApplet/class.class)
	at sun.plugin2.applet.Applet2ClassLoader.getBytes(Unknown Source)
	at sun.plugin2.applet.Applet2ClassLoader.access$000(Unknown Source)
	at sun.plugin2.applet.Applet2ClassLoader$1.run(Unknown Source)
	at java.security.AccessController.doPrivileged(Native Method)
	... 7 more
Exception: java.lang.ClassNotFoundException: com.usaa.bank.homedeposit.applet.ScanApplet.class

So you're saying that you have the plugin installed (you see it in about:plugins in firefox), but when you go to the USAA website you get that error?

---

### Post by T-Keith on 2010-05-14
There is an error where the form would be, you have to click on it and view log or something like that.  Now when I try it I can't get past the minimum requirements.  Anyone have any ideas?  Why do they make it so difficult?

---

### Post by wbar2 on 2010-05-18
> **T-Keith said:**
> There is an error where the form would be, you have to click on it and view log or something like that.  Now when I try it I can't get past the minimum requirements.  Anyone have any ideas?  Why do they make it so difficult?

I believe I had this issue as well. Are you still using the Java from the repos? If so, you may need to upgrade to the latest one which is update 20. Go to "about:plugins" in firefox and see what version you have.

Mine says: "Java(TM) Plug-in 1.6.0_20"

What does yours say?

---

### Post by Sarastro on 2010-05-19
This process worked well for me.  Leaving Windows is a slow process, now quickly accelerated by the ability to scan my deposits.

Thanks for taking the time to post this information

---

### Post by wbar2 on 2010-05-20
> **T-Keith said:**
> Does this only work in 32 bit?   I am running 64bit Kubuntu and I swear I got it to work just before upgrading to 10.04.  Now it says I don't meet minimum system requirements.  I just installed Java through the software management utility, do I need to do all these steps?  My about:plugins says the Java plugin is 1.6 could that be the problem?

thanks,
-Keith

I have redone the tutorial using the Sun Java from the repos. It works on 64-bit. You will need to remove the old Sun Java you install first using the instructions here: [http://sites.google.com/site/easylinuxtipsproject/java#TOC-Removal](http://sites.google.com/site/easylinuxtipsproject/java#TOC-Removal)

---

### Post by T-Keith on 2010-05-24
Thanks, I will give it a shot when I get a chance.  It's less of a priority now that Verizon pushed 2.1 to my phone so I can use their android app instead.

---

### Post by Objekt on 2010-06-12
I want to get around USAA's stupid "system requirements" too, and not run a virtual XP machine just for one lousy website.  I run Ubuntu 9.10 64-bit, not 10.04, but the method for 10.04 should also work for 9.10, shouldn't it?  Won't, so far.

> **wbar2 said:**
> I have redone the tutorial using the Sun Java from the repos. It works on 64-bit. You will need to remove the old Sun Java you install first using the instructions here: [http://sites.google.com/site/easylinuxtipsproject/java#TOC-Removal](http://sites.google.com/site/easylinuxtipsproject/java#TOC-Removal)

That didn't work for me.  I followed the entire procedure, but there is NO Java anything listed in Firefox's about : plugins page.  There are only 2 plugins: 
```
Shockwave Flash

    File: libflashplayer.so
    Version: 
    Shockwave Flash 10.0 r42

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Default Plugin

    File: libnullplugin.so
    Version: 1.0.0.15
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No
```

No idea what that second one is.

Also, when I go to Oracle's "verify your Java version" page ([http://java.com/en/download/installed.jsp]("http://java.com/en/download/installed.jsp")) in Firefox, it doesn't work.  The "detecting Java on your computer" animations sits there for a while, then I get "Something is wrong.  Java is not working."

I also get a bar at the top of the tab telling me "Additional plugins are required to display all the media on this page," but if I click to "Install missing plugins...," that doesn't work either.  The only two choices given are "The Iced Tea Web Browser Plugin," and "The Java (TM) Plugin, Java SE 6."  Obviously I don't want Iced Tea.  Clicking the second one just gives me the unsurprising message:
```
Package 'sun-java6-plugin' is already installed
```

(No kidding, I just finished installing it, before restarting Firefox.)

Meanwhile, the Java version test works fine in other browsers, Chrome for example.  In Chrome, I get the expected result:
```
You have the recommended Java installed (Version 6 Update 20).
```

USAA isn't the only website I've visited where Java stuff doesn't work properly.  I did everything necessary to install the Java JRE plugin for Firefox.  What is Firefox's problem?

---

### Post by wbar2 on 2010-06-20
> **Objekt said:**
> I want to get around USAA's stupid "system requirements" too, and not run a virtual XP machine just for one lousy website.  I run Ubuntu 9.10 64-bit, not 10.04, but the method for 10.04 should also work for 9.10, shouldn't it?  Won't, so far.



That didn't work for me.  I followed the entire procedure, but there is NO Java anything listed in Firefox's about : plugins page.  There are only 2 plugins: 
```
Shockwave Flash

    File: libflashplayer.so
    Version: 
    Shockwave Flash 10.0 r42

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Default Plugin

    File: libnullplugin.so
    Version: 1.0.0.15
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No
```

No idea what that second one is.

Also, when I go to Oracle's "verify your Java version" page ([http://java.com/en/download/installed.jsp]("http://java.com/en/download/installed.jsp")) in Firefox, it doesn't work.  The "detecting Java on your computer" animations sits there for a while, then I get "Something is wrong.  Java is not working."

I also get a bar at the top of the tab telling me "Additional plugins are required to display all the media on this page," but if I click to "Install missing plugins...," that doesn't work either.  The only two choices given are "The Iced Tea Web Browser Plugin," and "The Java (TM) Plugin, Java SE 6."  Obviously I don't want Iced Tea.  Clicking the second one just gives me the unsurprising message:
```
Package 'sun-java6-plugin' is already installed
```

(No kidding, I just finished installing it, before restarting Firefox.)

Meanwhile, the Java version test works fine in other browsers, Chrome for example.  In Chrome, I get the expected result:
```
You have the recommended Java installed (Version 6 Update 20).
```

USAA isn't the only website I've visited where Java stuff doesn't work properly.  I did everything necessary to install the Java JRE plugin for Firefox.  What is Firefox's problem?

Hey, I really don't know what that problem could be. Although there shouldn't be too much of a difference between 9.10 and 10.04 concerning this, there very well might be.

---

### Post by Objekt on 2010-06-23
FWIW, there is a bit about a missing Java plugin in Firefox at the Ubuntuzilla project page:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Java_plugin_not_showing_up_.28on_Ubuntu_Karmic.29]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Java_plugin_not_showing_up_.28on_Ubuntu_Karmic.29")

I don't know whether you use Ubuntuzilla, but I do, and these instructions do *not* fix the problem.

I seem to have a general plugins problem.  In the other two browsers I've tried, Google Chrome and Opera, I get a lot of plugins listed when I go to about:plugins.  In Firefox, everything except Flash is missing.  No idea what's going on here, as no one else seems to have this problem.

I'm sick and tired of tearing my hair out over Firefox not doing simple stuff it should do.  I would have abandoned it long ago, if there were any other browser with its tons of extensions and add-ons.

---

### Post by isotherm on 2010-07-05
Attached is a script I wrote to automate the check scanning. After downloading, be sure you have permissions ot execute it. Also be sure the "imagemagick" package is installed, and of course SANE.

The images are saved to in the /tmp folder as usaa_check_FRONT.jpg and usaa_check_BACK.jpg

---

### Post by sgosnell on 2010-07-05
No attachment.

---

### Post by isotherm on 2010-07-06
Sorry, it must've been removed when I edited the first time. Fixed.

---

### Post by wbar2 on 2010-07-09
> **isotherm said:**
> Attached is a script I wrote to automate the check scanning. After downloading, be sure you have permissions ot execute it. Also be sure the "imagemagick" package is installed, and of course SANE.

The images are saved to in the /tmp folder as usaa_check_FRONT.jpg and usaa_check_BACK.jpg

Works great! The only thing is that the zenity progress bar does not work properly.

---

### Post by isotherm on 2010-08-08
Thanks for the feedback. Unfortunately, scanimage outputs its progress using carriage returns (\r) rather than line feeds (\n), which means the buffer is never flushed, so zenity never gets the progress. I fixed it on my end by changing scanimage. :???: Not sure of any other solution, unless someone knows a way to force a certain program to use unbuffered I/O.

---

### Post by tony_clifton on 2010-08-24
Huge thanks to wbar2 for this tutorial.  Pure awesome.

---

### Post by tony_clifton on 2010-08-25
> Now when I try it I can't get past the minimum requirements.

Based on my experience with this issue, that sounds like you're not using a user agent switcher. The user agent has to be changed to spoof a Mac before you go to the USAA website.

---

### Post by torstenaf on 2010-09-07
D@H was working for a long time. I installed Lucid 10.4 on my new laptop, followed this tutorial, and now I keep getting this error:

> 
   Error occurred while uploading. Please click "Submit" to try again. If you continue to have difficulty, please call 1-800-XXX-XXXX for assistance.

  Note: If you are using a modem or satellite to connect to the internet, this application may not work for you.

   For information review our Troubleshooting Tips.
Reference Id: 38320639


Any suggestions?

---

### Post by tony_clifton on 2010-10-16
> **torstenaf said:**
> D@H was working for a long time. I installed Lucid 10.4 on my new laptop, followed this tutorial, and now I keep getting this error:

Any suggestions?

This has begun happening to me as well.  I tried both Ubuntu 10.04 and 10.10 with the same results. 

As a test, I installed User Agent Switcher into Firefox on Windows XP (this is the add-on I use to spoof Mac) and spoofed a Mac via Windows XP.  Everything worked fine, no errors, check was deposited.

What this means for me is that the problem is not my internet connection, as suggested in the error text, nor is it the scanned images or the check itself.

The possibilities I'm currently looking at are something inherent to Linux itself or something with the browser (same browser version all three systems, however add-ons used on Linux vs.  Windows are not exactly the same).  Also a possibility, however seemingly unlikely, is Java.  Java on Linux is currently 6-21 while XP already has 6-22.

---

### Post by Objekt on 2010-10-26
> **torstenaf said:**
> D@H was working for a long time. I installed Lucid 10.4 on my new laptop, followed this tutorial, and now I keep getting this error:



Any suggestions?

Same here, I just tried a deposit 4 times in a row and it didn't work.

That message was replaced by a "The system is currently unavailable.
 Reference Id: 40592123" error message, almost before I had a chance to read the first error message.

Perhaps it's a genuine system outage?  I'll have to try again later to be sure.

Also, I note that XSANE is STILL very broken, as it was under Ubuntu 9.10.  XSANE no longer even pretends to start working.  I see the "scanning for devices" window briefly, then brief flashes of the XSANE GUI, then it disappears completely.  I guess it's time to start another thread. :P

At least Skanlite still works.  In fact, it works pretty darn well, and I like it.

---

### Post by sgosnell on 2010-10-26
XSane works fine for me.  Usually the problem you describe is caused buy XSane not finding the scanner.  Make sure the scanner is actually working, and is correctly configured.  If XSane doesn't find a scanner, it just quits, and will never load.

---

### Post by Objekt on 2010-10-27
The problem must be with Xsane.  Other software has no trouble finding the scanner.  I just used it to scan my check through Skanlite.  Gscan2pdf works as well, although it's not useful in the current discussion.

I noticed a big difference between doing Deposit@Home in Windows XP vs. Ubuntu.  When I do it in Ubuntu, I get a button labeled "Select" that lets me choose & upload prescanned images for the front & back of the check.  When I do Deposit in Windows, I don't get that option.  It forces me to pick my scanner & scan the check "live."  Which is really inconvenient, since I already scanned the check yesterday in Ubuntu.  

Perhaps the Java USAA is using tries to detect my scanner automagically, but is unable to do so because it assumes it is operating in a Windows OS.  Maybe that's why I get the "Select" button when running Ubuntu.

---

### Post by sgosnell on 2010-10-27
I've always had the select button, using the Mac spoof in Agent Switcher.

What kind of scanner do you have?  You may need to load some drivers to have XSane use it.  For a Brother, I've had to load some additional drivers.  HP seems to work pretty easily.

---

### Post by Objekt on 2010-10-27
Brother MFC-7440N.  I have the drivers to print & scan installed, or at least those things work with other software.  I am not aware of any other drivers for the MFC-7440N.

---

### Post by sgosnell on 2010-10-28
I had to install the brscan and brscan-skey drivers to get scanning to work.  If you have these already installed, then it appears that xsane is not detecting the Brother for some reason.  I don't have much else to suggest.

---

### Post by dennis1200 on 2010-11-02
I am also experiencing the "error occurred while uploading" message, but I am fairly sure it is not XSane related. I have tried XSane/Simple Scan as well as photos, as is and edited in GIMP (always grayscale, 200dpi), and the message is still there.

And I'm using Java 1.6.0_22, not 21.

---

### Post by Objekt on 2010-11-02
No, I don't think the error message has anything to do with how you scan.  It's a BS error message that USAA's code is throwing up because it has some stupid dependency on a Windows environment.

That said, I haven't tried it in another browser, like Chromium or Opera.  Might be worth a try.

---

### Post by DMJ on 2011-04-17
> **isotherm said:**
> Attached is a script I wrote to automate the check scanning. After downloading, be sure you have permissions ot execute it. Also be sure the "imagemagick" package is installed, and of course SANE.

The images are saved to in the /tmp folder as usaa_check_FRONT.jpg and usaa_check_BACK.jpg

I modified the script a bit to scan multiple checks at a time. I hope you don't mind. It appends today's date and the check number to each image. If it's alright with you I'll post a link to it. 

Has there been any progress with the bank? I have firefox 3 and 4 installed, because headercontrol doesn't work with ff4.

---

### Post by DMJ on 2011-04-25
There's another add-on called UAControl that does the same thing and it works in FF4.

I've attached the script for scanning multiple checks, as described in my last post. It's not quite bulletproof yet, so I can't guarantee what will happen if you hit the cancel button while scanning, etc. It can easily be modified to save the images to any directory by changing the check_path variable. Enjoy.

---

### Post by gbear14275 on 2011-06-29
[http://www.miscfits.com/2009/04/usaa-deposit-at-home-on-linux.html](http://www.miscfits.com/2009/04/usaa-deposit-at-home-on-linux.html)

USAA has commited to releasing a fix for this issue which, barring unforseen issues, should be released September 1st.

---

### Post by gbear14275 on 2011-09-16
Hey guys!  Great news I have just been able to preview an update to USAA's deposit at home feature which will allow for unsupported systems (including ours) to be used without a bunch of spoofing.  The update will roll out on September 23rd and should be available the following day.  I haven't been able to test a check yet but the below screenshot's show what the initial interface looks like.

I am using the official 64 bit java plugin so don't know how icedtea compatibility is but hopefully there shouldn't be any issues.  If there are please post them after the 24th and I'll pass them along.

Hope everyone likes this as much as me.

Garrett

---

### Post by gbear14275 on 2011-09-16
> **LewRockwell said:**
> What is Mark Voelkel's contact and mailing information?

Perhaps he would like to do an interview?

.

P.S.  I finally got in touch with someone who made it happen.  Let me know if you want to talk with them.

Garrett

---

### Post by marklila on 2012-12-03
Thanks isotherm and DMJ for the scripts.  They are great.

A while back USAA changed the site so it no longer requires the images to be cropped on the web site while processing the check.  I then got an error unless I manually cropped the check prior to uploading the image.  I tried to "-trim" the image's whitespace with the script but it isn't white enough whitespace because it doesn't "-trim".  I made a hard-coded change to the script to "-x 152 -y 69" to get around the error for typical standard sized checks only.  I otherwise crop with GIMP as follows:
> Right click file and open with GIMP
> Press Shift+C to enable the Crop Tool
> Select object
> Press enter to crop
> Press Ctrl+Shift+E to export
> Click Export
> Click Replace
> Click Export
> Press Ctrl+Q to close GIMP
> Click Discard Changes

Has anybody else seen this issue or have a better solution?

---

