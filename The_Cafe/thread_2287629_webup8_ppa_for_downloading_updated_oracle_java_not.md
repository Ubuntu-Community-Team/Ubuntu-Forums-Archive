---
title: "webup8 ppa for downloading updated oracle java not maintained?"
date: 2015-07-21
forum: The Cafe
---

### Post by claracc on 2015-07-21
Hello,

I don't know if this is the proper subforum to ask this question, if no, please feel free to move to the adecuate one.

Someone knows if the webup8 ppas for downloading updated oracle java 8 or 7 are not longer mantained?, I have the ppa corresponding to oracle java 7 but I remains with oracle java 1.7.0.80 which is marked as unupdated by firefox and I don't receive any security update from the forementioned ppa.

Thanks in advance

---

### Post by Bucky Ball on 2015-07-21
*Thread moved to **The Cafe**.*

As Webup8 has nothing to do with Canonical or Ubuntu directly and this is not a Ubuntu support request, best here. You might try posting on a Webup8 forum or emailing them directly (or emailing directly the maintainer of whatever PPA you are talking about).

---

### Post by QIII on 2015-07-21
I'll try to get in touch with Andrew again and see if he is maintaining it any longer.

Edit:  I emailed Andrew.  We'll see what he has to say.  All that stuff on webupd8?  Maintained by one guy.  He may just be taking a well-deserved break.

If you are hard pressed for an immediate solution and must have Oracle Java, then I suggest [this]("https://sites.google.com/site/easylinuxtipsproject/java"), which is what I used to use to get the JRE and browser plugin.  But it doesn't install the JDK.

You may also uninstall Oracle Java 7/8 from the PPA and install OpenJDK.

OpenJDK is the open source reference implementation of Oracle Java -- which is to say that Oracle has decreed that all things Java, including Oracle Java, must conform to OpenJDK as the standard (although they haven't exactly held to that.)

---

### Post by monkeybrain20122 on 2015-07-21
> **QIII said:**
> I'll try to get in touch with Andrew again and see if he is maintaining it any longer.

+1. Log in to launchpad and you can find his contact info. Just send him an email.

---

### Post by vasa1 on 2015-07-21
> **claracc said:**
> ...

Someone knows if the webup8 ppas for downloading updated oracle java 8 or 7 are not longer mantained?, I have the ppa corresponding to oracle java 7 but I remains with oracle java 1.7.0.80 which is marked as unupdated by firefox and I don't receive any security update from the forementioned ppa.
...
I asked about java here: [Which Java for LibreOffice Base?]("http://ubuntuforums.org/showthread.php?t=2274594") and was pointed to [http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html](http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html). So I went ahead and installed it as the link directed.

Now, when I open LibreOffice Calc Tools > Options > Advanced, I see Oracle Corporation version 1.8.0_45. But I too haven't noticed any updates (and I do make a point of knowing what updates arrive).

```
11:37 AM ~ $ java -version
java version "1.8.0_45"
Java(TM) SE Runtime Environment (build 1.8.0_45-b14)
Java HotSpot(TM) 64-Bit Server VM (build 25.45-b02, mixed mode)
11:46 AM ~ $ 

```But the webupd8 link has this:> As a reminder, the WebUpd8 Oracle Java PPA doesn't include any Java binaries, just a script that automatically downloads and install Oracle Java 8. Everything is done automatically so you'll get updates through the update manager for JDK8 which includes JRE8 and the Java browser plugin.

---

### Post by QIII on 2015-07-21
It's currently at Update 51 from Oracle, so webupd8 is getting a little old.

Again:  I emailed Andrew.  Please don't flood him.  I'll get back to this with an update when I hear something.

---

### Post by QIII on 2015-07-21
> **monkeybrain20122 said:**
> +1. Log in to launchpad and you can find his contact info. Just send him an email.

He's already in my personal address book.  :)

---

### Post by Pilot6 on 2015-07-26
I made a script to install and automatically update java.

[http://askubuntu.com/a/652901/167850](http://askubuntu.com/a/652901/167850)

[https://github.com/hanipouspilot/oracle-java8](https://github.com/hanipouspilot/oracle-java8)

---

### Post by nargaroth_reg on 2015-07-27
Thanks Pilot6, your script worked very well for me. I updated from 8u45 to 8u51 amd64 without issues.

---

### Post by QIII on 2015-08-03
If you hadn't heard, the webupd8 PPA has been updated.

Two of my Ubuntu machines updated just fine.  With the third, I had to use ppa-purge to purge the PPA, reinstall the PPA and then install oracle-java8-installer again.

---

### Post by claracc on 2015-08-04
Thankyou for the information.

I uninstalled the ppa and installed icedtea java plugin. For now I think it is enough for me, since I am not a 
developer and only want to see animations or applets in web.

Regards

---

### Post by nargaroth_reg on 2015-08-05
Great, the update was only delayed a few days. Unfortunately Oracle doesn't seem to provide fixed urls (like [https://ftp.mozilla.org/pub/firefox/releases/latest/linux-x86_64/](https://ftp.mozilla.org/pub/firefox/releases/latest/linux-x86_64/) for instance), which would imo make it easier to update via script.

---

### Post by QIII on 2015-08-05
Remember that webupd8.org is at present a one man show.  I'm amazed he keeps up as well as he does.

---

### Post by SantaFe on 2015-08-05
Great, I just manually updated Java to the current one, now I've upgraded from 51 to 51! ;)

---

### Post by monkeybrain20122 on 2015-08-06
Except for a few  Oracle applications like Netbeans I am not sure about the need or advantage of installing Oracle Java. Openjkd8 is in Ubuntu 15.04, for Trusty there is [https://launchpad.net/~openjdk-r/+archive/ubuntu/ppa/+index?field.series_filter=trusty](https://launchpad.net/~openjdk-r/+archive/ubuntu/ppa/+index?field.series_filter=trusty)

---

### Post by nargaroth_reg on 2015-08-12
> **monkeybrain20122 said:**
> Except for a few  Oracle applications like Netbeans I am not sure about the need or advantage of installing Oracle Java. Openjkd8 is in Ubuntu 15.04, for Trusty there is [https://launchpad.net/~openjdk-r/+archive/ubuntu/ppa/+index?field.series_filter=trusty](https://launchpad.net/~openjdk-r/+archive/ubuntu/ppa/+index?field.series_filter=trusty)
Hmm as of today that ppa seems to be outdated.

---

### Post by QIII on 2015-08-12
[webupd8]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html") has Oracle Java 8 Update 51, which is the newest version according to [this]("http://www.java.com/en/download/installed.jsp").

---

### Post by nargaroth_reg on 2015-08-12
> **QIII said:**
> [webupd8]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html") has Oracle Java 8 Update 51, which is the newest version according to [this]("http://www.java.com/en/download/installed.jsp").
Yeah, I was referring to the ppa monkeybrain20122 suggested, which has openjdk8 for ubuntu 14.04, but its version is still 8u45.

---

### Post by monkeybrain20122 on 2015-08-12
> **nargaroth_reg said:**
> Yeah, I was referring to the ppa monkeybrain20122 suggested, which has openjdk8 for ubuntu 14.04, but its version is still 8u45.

Well here is another one with 8u66. [https://launchpad.net/~jonathonf/+archive/ubuntu/openjdk](https://launchpad.net/~jonathonf/+archive/ubuntu/openjdk)

But I don't really know what the difference is as long as it is openjdk8 and you get timely security updates. There are things that run on openjdk8 but not openjdk7, but to my knowledge nothing requires a particular sub version or build of openjdk8

---

