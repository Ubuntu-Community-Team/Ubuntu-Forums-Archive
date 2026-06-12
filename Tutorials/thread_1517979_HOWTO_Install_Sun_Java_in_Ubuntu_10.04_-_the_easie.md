---
title: "HOWTO: Install Sun Java in Ubuntu 10.04 - the easiest way"
date: 2010-06-25
forum: Tutorials
---

### Post by zerwas on 2010-06-25
[COLOR="DimGray"][SIZE="1"]Preface: There can be many reasons why you need Java on your system. You need Java in case you want to use [Wuala]("http://www.wuala.com"), the secure peer-to-peer online storage, or [Freenet]("http://www.freenetproject.org"), an anonymous and censor-resistant network. Or maybe you need just want to play a little browser game which requires Java.
There are several Java implementations, but the default Java implementation in Ubuntu does not always work with other software, that is why i created this specific tutorial for Sun's version of Java.[/SIZE][/COLOR]

[CENTER][FONT="Arial Black"][SIZE="5"]= How to install Sun Java in Ubuntu 10.04 =[/SIZE][/FONT][/CENTER]

First, we need to enable Canonical's so-called "partner" repository which includes popular non-free software like Skype, Google Earth or Sun Java. Afterwards we can install all those applications just like you are used to with every other application:

[SIZE="4"][LIST=1]
[*]Enable repository: Click [FONT="Courier New"]Applications[/FONT] -> [FONT="Courier New"]Software Centre[/FONT] -> In the Menubar, choose [FONT="Courier New"]Edit[/FONT] -> [FONT="Courier New"]Software Sources[/FONT]. Go to tab [FONT="Courier New"]Other Software[/FONT] and tick the first entry ("partner"). Close and confirm the "Reload".
[*]In Software Centre, search for "[FONT="Fixedsys"]sun java[/FONT]" and install the first package ("[FONT="Fixedsys"]Sun Java 6.0 Plugin[/FONT]"). You are done!
[/LIST]
[/SIZE]


[CENTER]I also created a short video tutorial with these instructions which you can watch by clicking on this image:

[[IMG]http://img231.imageshack.us/img231/6255/bildschirmfotolr.png[/IMG]](http://www.youtube.com/watch?v=AsYdroTnjXk)


= [SIZE="3"]Appendix[/SIZE] =
[/CENTER]

> [CENTER]== Check installation ==[/CENTER]
There are several ways to check if Sun Java is installed correctly, fire up your browser (like Firefox, Chrome, Chromium, Opera, Epiphany, ...), now:
[LIST]
[*]type into the address bar:
[FONT="Courier New"]**about:plugins**[/FONT]
You should see an entry for Sun Java on this page.
[*]You can visit the Java test page at [java.com]("http://java.com").
[*]To verify your installed Java software, see [Verify Installation]("http://www.java.com/en/download/installed.jsp") at java.com.
[*][Java Tester]("http://javatester.org") includes links to verify your Java version and whether Java is enabled.
[/LIST]
For Firefox-specific help, see the [Mozilla Knowledgebase]("http://support.mozilla.com/en-US/kb/Using%20the%20Java%20plugin%20with%20Firefox").


> [CENTER]== Problems ==[/CENTER]

If you face any problems, see if other Java implementations are installed. To check this, remove those packages:
[LIST]
[*]icedtea6-plugin
[*]openjdk-6-jre-lib
[/LIST]

For Firefox-specific problems related with Java you can also consult the [Mozilla Knowledgebase]("http://support.mozilla.com/en-US/kb/Java-related%20issues").


> [CENTER]== Multiple Java installations ==

[/CENTER]If you have a parallel OpenJDK Java installed and want to keep it but would like to set Sun Java to be the default, execute this command:
```
sudo update-alternatives --set java /usr/lib/jvm/java-6-sun/jre/bin/java
```

[CENTER]=== Manually choose Java version ===[/CENTER]
It is also possible to manually choose which Java version you want to let the system use:
```
sudo update-alternatives --config java
```
To specify the Java version *for your browser plugin* manually, execute```
sudo update-alternatives --config mozilla-javaplugin.so
```
> [CENTER]== The expert way ==

[/CENTER]If you are a command line freak, you might like this method instead:```
sudo add-apt-repository "deb http://archive.canonical.com/ubuntu $(lsb_release -s -c) partner"
sudo apt-get update && sudo apt-get install sun-java6-plugin
```

---

### Post by soldier1st on 2010-07-03
why would you want sun java when you get OpenJDK?are there any advantages of using sun java instead of OpenJDK?i have java apps and they work fine with OpenJDK.

---

### Post by zerwas on 2010-07-03
> **soldier1st said:**
> why would you want sun java when you get OpenJDK?Thanks for your question, soldier1st. First, there are several applications that have problems with OpenJDK (or the other way round) like Freenet, Wuala, Sparnord and others but work fine with Sun JRE. A [Google search]("https://encrypted.google.com/search?&q=%22does+not+work+with+openjdk%22") reveals many applications and issues. Also see [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/openjdk-6") for issues with OpenJDK, if you are interested. So if you want to use one of these applications you have to use Sun Java.

> are there any advantages of using sun java instead of OpenJDK?Azureus for example works faster with Sun Java than with OpenJDK.

> i have java apps and they work fine with OpenJDK.Then there is no need to switch over to Sun Java of course. Open source should always be the first choice if it fits all your needs.

---

### Post by wonderingwhy on 2010-07-04
Thanks so much Zerwas this worked a treat, am much obliged:D

---

### Post by Npl on 2010-07-04
> **soldier1st said:**
> why would you want sun java when you get OpenJDK?are there any advantages of using sun java instead of OpenJDK?i have java apps and they work fine with OpenJDK.One popular problem is the icedtea-plugin which is dependend on firefox libraries and only works on this browser (atleast in 10.04, hope they fix this mess in the next version).

---

### Post by Theft42 on 2010-07-04
This is greatly appreciated zerwas..

Thank you so very much :D

---

### Post by bogaczew on 2010-07-07
> if you have a parallel OpenJDK Java installed and want to keep it but would like to set Sun Java to be the default, execute this command:

```
sudo update-alternatives --set java /usr/lib/jvm/java-6-sun/jre/bin/java
```

why not simple

```
sudo update-alternative --config java
```



> If you face any problems, see if other Java implementations are installed. To check this, remove those packages:

    * icedtea6-plugin
    * openjdk-6-jre

it's a clear bug to me. there should be two plugins available in firefox, and one should choose which one he wants to use. i just don't know where should i report it. mozilla? ubuntu? oracle?

---

### Post by zerwas on 2010-07-07
> **bogaczew said:**
> why not simple

```
sudo update-alternative --config java
```Because with your command you have to choose on your own, which Java implementation you want to enable as default. There is less that can go wrong if you just copy and paste my command into the terminal.

> It's a clear bug to me. there should be two plugins available in firefox, and one should choose which one he wants to use.
That's already possible through the Add-ons window in Firefox (you need to disable the other java plugin). See my posting:

> For Firefox-specific help, see the [Mozilla Knowledgebase]("http://support.mozilla.com/en-US/kb/Using+the+Java+plugin+with+Firefox").


---

### Post by bogaczew on 2010-07-08
> Because with your command you have to choose on your own, which Java implementation you want to enable as default. There is less that can go wrong if you just copy and paste my command into the terminal.

OK. I see Your point. 

> That's already possible through the Add-ons window in Firefox (you need to disable the other java plugin).

in my ubuntu 10.06 64b, with firefox from repo, there is only one java plugin in add-ons window. either icedtea or sun-javaplugin. you have to uninstall icedtea to use sun-java plugin.

so i will report it to mozilla.

[https://bugzilla.mozilla.org/show_bug.cgi?id=577670](https://bugzilla.mozilla.org/show_bug.cgi?id=577670)

---

### Post by zerwas on 2010-07-08
> **bogaczew said:**
> in my ubuntu 10.06 64b, with firefox from repo, there is only one java plugin in add-ons window. either icedtea or sun-javaplugin. you have to uninstall icedtea to use sun-java plugin.
You are right. But while Firefox changed to OpenJDK after installing icedtea plugin and didn't change back even when i did update-alternatives, Chromium always used Sun Java.

It would be nice if you could give us the URL to your bug report. :)

---

### Post by bogaczew on 2010-07-14
if you have similiar error (onlu one plugin in firefox, icedtea or sun-java) please, add comment to my bug. to show mozilla that i'm not the only one.

---

### Post by soldier1st on 2010-07-15
so having both sun java and openjdk would not cause any problems?

---

### Post by thahir1986 on 2010-07-15
thanks a lot:p

---

### Post by zerwas on 2010-07-15
> **thahir1986 said:**
> thanks a lot:pThanks! :-)
> **soldier1st said:**
> so having both sun java and openjdk would not cause any problems?No, usually everything should work fine with several Java implementations installed parallel.> **bogaczew said:**
> if you have similiar error (onlu one plugin in firefox, icedtea or sun-java) please, add comment to my bug. to show mozilla that i'm not the only one.I think your bug report will be marked as WONTFIX because the operating system is processing this. The most elegant way to secify which Java plugin browsers should use is (to select the version manually):
```
sudo update-alternatives --config mozilla-javaplugin.so
```

To tell Ubuntu to use OpenJDK *for your browser* by default, execute ```
sudo update-alternatives --set mozilla-javaplugin.so /usr/lib/jvm/java-6-openjdk/jre/lib/$(dpkg --print-architecture)/IcedTeaPlugin.so
```I added this to the tutorial.

---

### Post by coilwinder on 2010-07-15
@zerwas:

Thank you!!

I was turning crazy, trying lots of things and following long lists of instructions, to no avail. I was about to give java up. Then I discovered your 2-point list :)

But, on my ubuntu 10.04 64-bit, it seems to partialy work? I'm not sure, according to the sun java test it works. But I can't use my internet bank, which uses java, so I dont know for sure what the issue is. It seems to work except for that. Maybe it's got to do with the fact that Ubuntu 10.05 64-bit got java 6 update 18, while ubuntu 9.10 32-bit got java 6 update 20?

In addition your instructions also worked perfectly on my ubuntu 9.10 32-bit :)

---

### Post by bogaczew on 2010-07-15
> **zerwas said:**
> .I think your bug report will be marked as WONTFIX because the operating system is processing this. The most elegant way to secify which Java plugin browsers should use is (to select the version manually):
```
sudo update-alternatives --config mozilla-javaplugin.so
```



yes, I just figurd it out, and added in comment to my bug. think it will be closed now.

---

### Post by zerwas on 2010-07-16
> **coilwinder said:**
> @zerwas:Thank you for your nice words. :)

Regarding your bank issues, i would need more information in order to be able to get down to the cause of your problem.

That is: What exactly does it mean that you "can't use" it? Is there any error message while loading the website? If not, what do you get instead? A gray empty field? Did it work with Ubuntu 9.10? Does it still work with other browsers? Depending on your browser, did you have a look into the Java error console and Java log respectively? (but before you start to answer all those questions, have a look at the command at the bottom of this posting)

Maybe you should better start a new thread to describe this problem exactly if it is urgent.

> Maybe it's got to do with the fact that Ubuntu 10.05 64-bit got java 6 update 18, while ubuntu 9.10 32-bit got java 6 update 20?That's possible. But: In Ubuntu 10.04 you should also get the latest version, which is "update 20" at the moment. Maybe you already have an old version of Java installed on this system by following other (outdated) tutorials.

You should check the output of this command in the terminal and see if the correct Java version is set:
```
sudo update-alternative --config java
```

---

### Post by Searock on 2010-07-16
Thanks a lot for the tutorial.

---

### Post by edmondt on 2010-07-19
Checked out you video on youtube... was that text to speech or was it your voice? Sorry I just thought that 99.9% of ubuntu users are male...

Very helpful post, thanks!

---

### Post by zerwas on 2010-07-19
Thanks for your feedback, Searock and edmondt :)

> **edmondt said:**
> Checked out you video on youtube... was that text to speech or was it your voice? Sorry I just thought that 99.9% of ubuntu users are male...

I already used text-to-speech for other videos but it didn't turn out so well. But in this video it's a real woman ;). It was a german IRC friend of mine who did it for me (ubuntu philosophy at its best). I think there was a time where you would be right with your guess of 99.9% male ubuntu users ;) ... like in 2004. But as Ubuntu becomes more popular (and more beautiful), more and more women are using it, too. One good example is [Nixie Pixel]("http://www.youtube.com/user/NixiePixel?blend=2&ob=1#p/c/C57C60F699A5C44D/0/2qR591lh5Ow").

---

### Post by pascar on 2010-08-27
Thanks for your tutorial that works fine for 1.6.0_20 release that is the Lucid repositories, but I need to install 1.6.0_07 because my Oracle eBS application server *needs* clients to connect with exactly that release...

Any idea how I can force installation through repositories of a specific version of the JRE and plugins?

THANKS!

---

### Post by Linuxforall on 2010-08-27
> **pascar said:**
> Thanks for your tutorial that works fine for 1.6.0_20 release that is the Lucid repositories, but I need to install 1.6.0_07 because my Oracle eBS application server *needs* clients to connect with exactly that release...

Any idea how I can force installation through repositories of a specific version of the JRE and plugins?

THANKS!

In that case you have to install it manually via the bin file, the methods are outlined here on the forum.

---

### Post by pedlazcar on 2010-08-31
Hi, zerwas and everyone else. I'm having trouble in step1.

When I click and confirm "Reload", Ubuntu can't install files from 19 until the last one. It seems it's trying to get files from "http://br.archive.ubuntu.com lucid", problably because I'm from Brazil. What should I do?

---

### Post by zerwas on 2010-08-31
Greetings to Brazil,

> **pedlazcar said:**
> It seems it's trying to get files from "http://br.archive.ubuntu.com lucid", problably because I'm from Brazil

It looks like the brazilian Ubuntu mirror is down right now. One option for you is to wait for the server to come back. Or you can switch to another server

[LIST=1]
[*]by going to [FONT="Courier New"]System -> Administration -> Software Sources[/FONT].
[*]In the tab "[FONT="Courier New"]Ubuntu Software[/FONT]" you can see a dropbown menu "[FONT="Courier New"]Download from: Server for Brazil[/FONT]". Click on it, choose "other", click on "[FONT="Courier New"]Select Best Server[/FONT]" and wait a minute for it to test all servers.
[*]Now just click "[FONT="Courier New"]Choose Server[/FONT]", close the window and you will be asked if you want to reload again.
[/LIST]

---

### Post by pedlazcar on 2010-08-31
> Greetings to Brazil, Hallo, Deutschland! (no google translator, hehe)

> It looks like the brazilian Ubuntu mirror is down right now. One option  for you is to wait for the server to come back. Or you can switch to  another server

[LIST=1]
[*]by going to [FONT=Courier New]System -> Administration -> Software Sources[/FONT].
[*]In the tab "[FONT=Courier New]Ubuntu Software[/FONT]" you can see a dropbown menu "[FONT=Courier New]Download from: Server for Brazil[/FONT]". Click on it, choose "other", click on "[FONT=Courier New]Select Best Server[/FONT]" and wait a minute for it to test all servers.
[*]Now just click "[FONT=Courier New]Choose Server[/FONT]", close the window and you will be asked if you want to reload again.
[/LIST]
 zerwas, it worked fine. With a little help from Argentina (the best server at the moment), I managed to install JavaSun and Frostwire (which was the reason I was looking for a tutorial like yours). Anyway, many thanks!

---

### Post by Newark_Wilder on 2010-09-05
This isn't working for me.  When I click on Sun Java 6.0 Plugin in the Software Center it gives me the following message:

To show information about this item, the software catalog needs updating.

Canonical does not provide updates for Sun Java 6.0 Plugin.  Some updates may be provided by the Ubuntu community.

---

### Post by zerwas on 2010-09-05
> **Newark_Wilder said:**
> This isn't working for me.  When I click on Sun Java 6.0 Plugin in the Software Center it gives me the following message:

It should also give you a button "Update now" which you should click. If you don't see that button, could you show us a screenshot?

You can also try to execute this command in Terminal (and have a look if it finishes without errors):

```
sudo apt-get update
```

---

### Post by Newark_Wilder on 2010-09-05
it doesn't give me an "update now" button.  I used that command line in terminal and it seemed to work meaning there were no error messages or anything but when i tried to run the software center again i got the same results with sun java 6.0.

i'm attaching a screenshot.[IMG]http://img819.imageshack.us/img819/2975/screenshotts.png[/IMG]

[IMG]file:///tmp/moz-screenshot.png[/IMG]

---

### Post by zerwas on 2010-09-06
Thank you very much for your reply. Are you sure the partner repository is activated (step 1 in my tutorial)?
When you do the command sudo apt-get update, you should also see a line that has the word "partner" in it.

It sounds just like [this]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/542892") launchpad entry.

---

### Post by Newark_Wilder on 2010-09-07
yeah i followed step 1 in the tutorial. when i run that command in terminal the partner line does show up as well. here's another screen shot of my "software sources" dialog box:

[IMG]http://img844.imageshack.us/img844/9105/screenshot1cf.png[/IMG]

---

### Post by zerwas on 2010-09-08
You are using Ubuntu 9.10 Karmic Koala, where Sun Java is part of the multiverse repository. In the tab "Ubuntu Software" you need to click on the "multiverse" entry. Then you can install the package sun-java6-plugin.

---

### Post by bearcy on 2010-10-02
> **soldier1st said:**
> why would you want sun java when you get   OpenJDK?are there any advantages of using sun java instead of OpenJDK?i   have java apps and they work fine with OpenJDK.

All the Internet banks in Norway depend upon running Sun Java. Without   it, you're stuck when you've installed the new ubuntu, and can't access   your bank. Neither can you pay with credit cards, nor Paypal or  similar,  because they re-direct you to your Internet bank which depend  upon Sun Java to be default, in order for the user to input  a number  from a code-generator, issued by the banks.

And I know for a fact that far from just Norwegian Internet banks use  Sun Java as their default virtual machine! It just denies to work with  openjdk.

If you've never emigrated from Windows, I can understand why this type of obvious ignorance exists in the linux-community.

But ubuntu boasts of being the best distribution in the linux family for   windows users who want to emigrate. Then selecting out Sun Java --   which also is free, by the way -- with any other open source well-made   java-version is devestating.

I know a lot of people in Norway who gave up ubuntu when 10.04 came,   because they're Windows-users who want something better and easier. Not   more complicated and therefore worse.

So this manual is a life saver to people like me, who wants to promote   ubuntu among my friends. But it does, however, make it necessary for me  to help them each and everyone  manually, and cannot expect them to do  any of this by themselves,  unfortunately.

So I strongly appeal to who-ever has the responsibility of making the  ubuntu distribution, to insert Sun Java as its default virtual machine.

Also make it easier for non-geeks (I'm one of the few pc-geeks I know!)   to install Windows-necessities like Adobe Flash and codecs for   multimedia, that are restricted.

I remember I found it relieving when copy-and-paste became integrated  into Linux, and didn't anymore have to be downloaded and installed  seperately, and started manually each time I wanted to use it; so you've  come a long way -- it's just a little bit more that needs to be done,  before you can save the poor Windows users!

A great idea might be to make an install-box appear the first times you   start ubuntu, and confirm each and every installation and preferance;  also with mime included, but so that even  my mother can do it! (She's  75 and dependent upon her Internet bank;  which is what she mainly uses  Internet for.)

If you want to save the wretched windows-users over on your side, please   make things easier to install and use! Not more   geek-dependent-difficult than necessary. Rather not at all, if possible.

But you don't have to let go of any of the geek-stuff, because you also  make  a graphic user's interface, that will do the same job. And which  will prudently ask for a  root-password whenever the command-line it  feeds into asks for it. Just make a gui that writes all those  difficult  commands that you otherwise would have to type in manually.

Windows-applications like Tweak-this-and-that (I myself use Tune-Up  Utilities) which writes directly to Windows System Registry and make  changes to how Windows behave, could be used as a role-model for  ubuntu-writers who needs inspiration. With VirutalBox, it is easy to  install a downloaded crack from thepiratebay.org or similar places of a  current version of Windows to test it in; in order to make something  looking similar for ubuntu. Not for the file defragmentation or other  os-maintenance-stuff necessarily, but at least scandisk and the  installations and tweaks that will make ubuntu as easy to use as  Windows. In order to surpass it and thus make it uninteresting to the  private market.

For people without any dos- or linux pc-experience, things like this  seem like a nightmare to even have to relate to. Since I bought my first  pc in 1985, I had to learn dos. And therefore Gnome terminal doesn't  seem so scary to me.

After trying for years to emigrate to Linux ubuntu, I must say that I   stick with it and learn more, more because of pride than anything.

But if you're not really interested in harvesting frustrated pc-users   from Windows' failure, please keep on in ignorant bliss! I won't try to   dictate anyone. Just plea!

---

### Post by Linuxforall on 2010-10-03
Absolutely correct, many banks, interactive sites all depend on Sun Java, Azureus runs better on Sun Java, so does Jdownloader etc. For now Open JDK is not the way to go.

---

### Post by goog64 on 2010-12-02
Thank you zerwas for this great thread.
I have done all that you said, but I still get the following message window when I try to log on to my stock trading site:
[B]This application requires java to be installed/upgraded.
 Installation will start now[/B]

If I click on it, it takes me to the sun java website to download java for Linux.
I have Ubuntu 10.04. I have checked my Sun Java installation as you said in your first post. Everything is installed correctly. 
I have verified it at the link you posted. I have also checked in Firefox plugins to see that it is enabled and it is the latest update.
I have no other alternatives installed like the "iced tea" or the JDK packages.
Do you know what I can try next?
Thank you for your help.

---

### Post by zerwas on 2010-12-05
Thank you for your detailed description of the problem. Is the website you experience the problems with publicly available, i.e. could you give me a link to it? (maybe as personal message if you don't want to post it here)

If your Sun Java installation works with other webpages it looks like a site-specific issue. Did you try another browser to rule out a browser problem?

---

### Post by coilwinder on 2010-12-28
@zervas:

Sorry for replying so late. I figured I could post this anyway, since I got it to work now. In the meantime I resolved to using my internet bank from my Ubuntu 9.10 32-bit OS.

However today I looked a little more closely (again) at getting the newest Sun Java (1.6.0_23) installed, since another application complained (it still worked, though). I found another list of things-to-type-in-terminal to install it manually. Just downloading "jre-6u23-linux-x64.bin" from Sun java and executing that (with sudo), didn't help (as before).

Anyway, now I have resolved it on my 64-bit Ubuntu 10.04, using a long-ish list. I found the solution on a norwegian forum here (description is copy-pasted from english, unfortunately the poster didn't have the original URL): [http://www.ubuntu.no/node/2674#comment-11203](http://www.ubuntu.no/node/2674#comment-11203) 

Except that it was for 32-bit (also 64-bit, but that part was left out), but I managed to modify it for 64-bit anyway. Which wasn't that different, basically only for the Mozilla firefox plugin activation. E.G. instead of

> For Firefox 3.6 and newer, type (copy/paste):
ln -s /opt/java/32/jre1.6.0_18/lib/i386/libnpjp2.so ~/.mozilla/plugins/I used:
> ln -s /opt/java/64/jre1.6.0_23/lib/amd64/libnpjp2.so ~/.mozilla/plugins/
As well as having a folder named 64 instead of 32, and the newest java atm.


My internet bank log-in still takes quite some time before showing the log-in applet window, and also requires some clicking in the java applet window to get it to react (also does this on the ubuntu 9.10 32-bit, for Windows I don't remember atm). But it works :)


As for your questions (I didn't spot them before - sorry!):
> What exactly does it mean that you "can't use" it? Is there any error  message while loading the website? If not, what do you get instead? A  gray empty field? Did it work with Ubuntu 9.10? Does it still work with  other browsers? Depending on your browser, did you have a look into the  Java error console and Java log respectively?What I ment before, that I couldn't use it on my internet bank, was that I actually could - seemingly - log in, but then I immediately got an error message on the internet bank webpage, stating I should close the browser and log in again (which didn't help of course).

And yes, it did work with Ubuntu 9.10 (32-bit OS on another AMD64 I got). Which browser didn't matter. Probably there was some differences, but none worked anyway. I tried chromium, firefox and Opera. - Usually I use firefox on this machine, and haven't tried the others yet after installing java manually.

And I have no idea where the Java error console or log is, so no, I haven't looked at that.


Before I  installed the new java, I had the "1.6.0_22" installed, which the netbank didn't work with. I also have the OpenJDK java installed, just not as default atm.

---

### Post by michel. on 2012-07-04
Since Aug 2011 there is no longer any Sun/Oracle Java available from Ubuntu. Also not from the partner repo.
You get the following message: 
```
Package sun-java6-jdk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jdk has no installation candidate
```

If you need Sun Java, install it manually or use the duinsoft repo. Both methods are clearly explained at [http://www.duinsoft.nl](http://www.duinsoft.nl)

---

### Post by Elfy on 2012-07-04
Old thread closed.

---

