---
title: "New Linux app requires JRE"
date: 2009-09-24
forum: System76 Support
---

### Post by ShowMeGrrl on 2009-09-24
I have a Starling netbook and tonight downloaded the AptanaStudio application for Linux. Though my preference is always to install applications using Synaptic, unfortunately, AptanaStudio was not listed in Synaptic.

So I downloaded a zip file and extracted it to the recommended directory (/usr/local/aptana). But when I tried to launch the AptanaStudio application, I got a message saying a java runtime environment (jre) must be available to run AptanaStudio. The program apparently looked for it in the /usr/local/aptana/jre/bin/java 

Synaptic shows that there is a "headless" jre installed somewhere on my machine as part of Ubuntu. Is this version of the jre sufficient for AptanaStudio? And if so, how do I find out where it lives and how do I point AptanaStudio to it?

Or should I download the jre1.6 that Aptana recommends? And if I do download it using Synaptic, will it go to the right place and will Aptana know where it is? Will it slow down my Starling to have this jre installed? Should I just give up on Aptana?

Sorry, I'm kind of a newbie.

---

### Post by mustafa-linux on 2009-09-24
you can find your jre by runing
```

which java
java -version

```
the last command should indicate your java version and I think it should be the java from sun which is the standard in java world.

---

### Post by ShowMeGrrl on 2009-09-24
> **mustafa-linux said:**
> you can find your jre by runing
```

which java
java -version

```
the last command should indicate your java version and I think it should be the java from sun which is the standard in java world.
This is what I got:
<code>
mylogon@system76-netbook:~$ java -version
The program 'java' can be found in the following packages:
 * gij-4.3
 * java-gcj-compat-headless
 * openjdk-6-jre-headless
 * cacao
 * gij-4.2
 * jamvm
 * kaffe
Try: sudo apt-get install <selected package>
bash: java: command not found
</code>

Does it mean these packages are installed on my machine? If so, why does it suggest I do "sudo-apt-get install <selected package>?

---

### Post by jdb on 2009-09-24
> **ShowMeGrrl said:**
> This is what I got:
<code>
mylogon@system76-netbook:~$ java -version
The program 'java' can be found in the following packages:
 * gij-4.3
 * java-gcj-compat-headless
 * openjdk-6-jre-headless
 * cacao
 * gij-4.2
 * jamvm
 * kaffe
Try: sudo apt-get install <selected package>
bash: java: command not found
</code>

Does it mean these packages are installed on my machine? If so, why does it suggest I do "sudo-apt-get install <selected package>?

It's telling you that you can get java by installing one of those packages which implies that none of them are installed.

It suggests using apt-get but the graphical interface synaptic works just as well.

I don't know which is best to install but I'm sure that you'll be getting more replies with advice :)

jdb

---

### Post by jerrrys on 2009-09-24
im thinking that **jre **is part of the restricted extra package.  do you have this installed?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by ShowMeGrrl on 2009-09-24
> **jerrrys said:**
> im thinking that **jre **is part of the restricted extra package.  do you have this installed?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
I think I do have the restricted extra package installed but I don't think it includes jre, because now that I understand Synaptic better*, I see that none of the jre's or jdk's seem to be installed.

Now the questions are: 1) which package to install
2) when a jre package is installed, will Aptana know it and be able to use it?

*I mistakenly thought that a Ubuntu logo next to the empty box meant it was installed. I now understand that if the box isn't filled in, it isn't installed.

---

### Post by jerrrys on 2009-09-24
heres what i have installed, should work for you.  and while your there, check to be sure that ubuntu restricted extras is installed...

[ATTACH]129624[/ATTACH]

also do you know that you can narrow your search by clicking on any program and then type in the first three letters of the program your looking for

---

### Post by thomasaaron on 2009-09-24
I would install Sun's JKD (which includes the JRE). The open jre that's in the system has issues.

sudo apt-get install sun-java6-jkd

Then run...

sudo udpate-alternatives --config java

...and select sun's java as your primary.

---

### Post by jerrrys on 2009-09-24
interesting thomasaaron.  it doesn't happen often, but from time to time i cannot get a java site to display and wondering if this may be a fix for me.  so being my lazy self and not wanting to dig thru launchpad i was wondering if you had any links to this...tia...and i promise to never go off subject again :)

---

### Post by thomasaaron on 2009-09-24
Probably, Ubuntu typically comes with the icedtea plugin for firefox (which is the open java plugin). Unfortunately, it sometimes doesn't work that well.

If you install the sun-java6-plugin, which I believe is installed automatically with the above commands, those sites might run better.

---

### Post by ShowMeGrrl on 2009-09-24
> **thomasaaron said:**
> I would install Sun's JKD (which includes the JRE). The open jre that's in the system has issues.

sudo apt-get install sun-java6-jkd

Then run...

sudo udpate-alternatives --config java

...and select sun's java as your primary.


Synaptic shows that I could install sun-java6-jdk using Synaptic. Is there a reason to use the above code in the terminal rather than using Synaptic?

---

### Post by jdb on 2009-09-24
> **ShowMeGrrl said:**
> Synaptic shows that I could install sun-java6-jdk using Synaptic. Is there a reason to use the above code in the terminal rather than using Synaptic?

I don't think it makes any difference if you use apt-get or synaptic.

This is from the man page for synaptic:

Description
Synaptic is a frontend for the apt package managent system.
It allows you to perform all actions of the command line tool apt-get in a graphical environemnt.
This includes installing, upgrading, downgrading and removing of single packages or even upgrading your whole system.

jdb

---

### Post by ShowMeGrrl on 2009-09-25
I am happy to say that I used Synaptic to install the Sun Java6 JDK and my Aptana application is now working as it should. So thanks for the help everybody. :)

---

