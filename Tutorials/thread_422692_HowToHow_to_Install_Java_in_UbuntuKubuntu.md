---
title: "HowTo:How to Install Java in Ubuntu/Kubuntu"
date: 2007-04-25
forum: Tutorials
---

### Post by Gmaster1440 on 2007-04-25
This tut will allow you to install a java environment that will allow you to run apps on your firefox/konqueror.

We will now install the following Java packages
sun-java6-bin - Contains the binaries
sun-java6-demo - Contains demos and examples
sun-java6-doc - Contains the documentation
sun-java6-fonts - Contains the Lucida TrueType fonts from the JRE
sun-java6-jdk - Contains the metapackage for the JDK
sun-java6-jre - Contains the metapackage for the JRE
sun-java6-plugin - Contains the plug-in for Mozilla-based browsers
sun-java6-source - Contains source files for the JDK

**Installing the Java Runtime Environment**

1) In terminal, enter the following command:```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

2) Once it downloads the packages and begins the installation, you&#8217;ll get a screen that contains the Sun Operating System Distributor License for Java and hit Enter to continue. You&#8217;ll see a dialog that asks you if you agree with the DLJ license terms. Select Yes, and hit Enter; the JRE will finish installing.

[B]
Aftermath:[/B]

First, check that the JRE is properly installed by running the following command from a terminal.
java -version
You should get similar output
java version &#8220;1.6.0&#8243;
 Java(TM) SE Runtime Environment (build 1.6.0-b105)
 Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

**Making sure java works on Firefox:**

Open Firefox and type ```
about:plugins
``` in the address bar and check for java plugin.

**Making sure Java works on Konqueror**

Go to any website that uses a java applet and see if it runs. If it doesn't run, click ```
Tools
``` 
in the Konqueror top bar, go to ```
HTML Settings
```
and make sure the "Java" option is ticked.


Feel free to post any questions.

---

### Post by stevenrushing on 2007-04-26
This is my output:

[INDENT]steven@steven-desktop:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
steven@steven-desktop:~$ [/INDENT]

But when i try to apt-get the new one, it says I have the most recent version.

Any ideas?  =)

Steven Rushing

---

### Post by gg234 on 2007-04-26
here is the original article [http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html)

> **Gmaster1440 said:**
> This tut will allow you to install a java environment that will allow you to run apps on your firefox/konqueror.

We will now install the following Java packages
sun-java6-bin - Contains the binaries
sun-java6-demo - Contains demos and examples
sun-java6-doc - Contains the documentation
sun-java6-fonts - Contains the Lucida TrueType fonts from the JRE
sun-java6-jdk - Contains the metapackage for the JDK
sun-java6-jre - Contains the metapackage for the JRE
sun-java6-plugin - Contains the plug-in for Mozilla-based browsers
sun-java6-source - Contains source files for the JDK

**Installing the Java Runtime Environment**

1) In terminal, enter the following command:```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

2) Once it downloads the packages and begins the installation, you’ll get a screen that contains the Sun Operating System Distributor License for Java and hit Enter to continue. You’ll see a dialog that asks you if you agree with the DLJ license terms. Select Yes, and hit Enter; the JRE will finish installing.

[B]
Aftermath:[/B]

First, check that the JRE is properly installed by running the following command from a terminal.
java -version
You should get similar output
java version “1.6.0&#8243;
 Java(TM) SE Runtime Environment (build 1.6.0-b105)
 Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

**Making sure java works on Firefox:**

Open Firefox and type ```
about:plugins
``` in the address bar and check for java plugin.

**Making sure Java works on Konqueror**

Go to any website that uses a java applet and see if it runs. If it doesn't run, click ```
Tools
``` 
in the Konqueror top bar, go to ```
HTML Settings
```
and make sure the "Java" option is ticked.


Feel free to post any questions.

---

### Post by naughtywill on 2007-04-26
I have looked and looked and I have not seen an post regarding my following question, so please forgive me if I overlooked something. When I try to install java it always come up to this right here....>    The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] dpkg: error processing sun-java6-doc (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Errors were encountered while processing:
 sun-java6-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)

 What is this and how do I get past this ?

---

### Post by jespdj on 2007-04-27
> **stevenrushing said:**
> This is my output:

[INDENT]steven@steven-desktop:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
steven@steven-desktop:~$ [/INDENT]

But when i try to apt-get the new one, it says I have the most recent version.

Any ideas?  =)

Steven Rushing

You might need to make Sun Java the default by running the following command:
```
sudo update-alternatives --config java
```
and selecting Sun Java.

---

### Post by Compyx on 2007-04-27
> **naughtywill said:**
> I have looked and looked and I have not seen an post regarding my following question, so please forgive me if I overlooked something. When I try to install java it always come up to this right here....
 What is this and how do I get past this ?

Somehow the quoting got mangled a bit, but these are the messages/instructions mentioned:
```

Selecting previously deselected package sun-java6-doc.
(Reading database ... 134351 files and directories currently installed.)
Unpacking sun-java6-doc (from .../sun-java6-doc_6-00-2ubuntu2_all.deb) ...
Setting up sun-java6-doc (6-00-2ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

```

So you should do what it says:

Go to [http://java.sun.com/javase/downloads/]("http://java.sun.com/javase/downloads/") and click on the "Download" button next to "Java SE 6 Documentation".

In the new page, click on the 'Accept License Agreement' radio button.

Now click on the package you want (English or Japanese) and save it somewhere in your home directory or on your Desktop.

Open a new terminal emulator and (assuming you've downloaded the package to your Desktop), do:
```

sudo cp Desktop/jdk-6-doc.zip /tmp

```

You can then continue with the installation (by pressing enter in the terminal emulator with apt-get/aptitude running, or Synaptic): the installer doesn't give a lot of feedback, but you should see something similar to this:
```

/tmp/jdk-6-doc.zip has been unpacked and installed.
You can now delete it, if you wish.

```

Which means everthing went well. You don't have to remove the package from /tmp yourself, it'll get deleted on your next boot anyway.

---

### Post by amadeov on 2007-04-30
I installed all of the packages that you suggested and I still can't get Java working.  I'm running Feisty and Firefox 2.0.0.3 (I believe).

When I run "java -version" I get back: 
```
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)
```

So, I know that Java 1.6.0 is installed... and when I run "sudo update-alternatives --config java", it is set to the following: ```
*         1    /usr/lib/jvm/java-6-sun/jre/bin/java.
```

So, Java should be configured properly.  However, java will NOT work in firefox.  When I look in "about:plugins", NOTHING is listed.

Any ideas?

---

### Post by Yggdrasill on 2007-05-07
What is the install path for Java 1.6 in Gnome?  I need to know in order to initiate initiate Java in Konqueror.

---

### Post by ant_999 on 2007-05-10
after installing the java-doc, where can I access it? where is index.html in the doc dir?


> **Compyx said:**
> Somehow the quoting got mangled a bit, but these are the messages/instructions mentioned:
```

Selecting previously deselected package sun-java6-doc.
(Reading database ... 134351 files and directories currently installed.)
Unpacking sun-java6-doc (from .../sun-java6-doc_6-00-2ubuntu2_all.deb) ...
Setting up sun-java6-doc (6-00-2ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

```

So you should do what it says:

Go to [http://java.sun.com/javase/downloads/]("http://java.sun.com/javase/downloads/") and click on the "Download" button next to "Java SE 6 Documentation".

In the new page, click on the 'Accept License Agreement' radio button.

Now click on the package you want (English or Japanese) and save it somewhere in your home directory or on your Desktop.

Open a new terminal emulator and (assuming you've downloaded the package to your Desktop), do:
```

sudo cp Desktop/jdk-6-doc.zip /tmp

```

You can then continue with the installation (by pressing enter in the terminal emulator with apt-get/aptitude running, or Synaptic): the installer doesn't give a lot of feedback, but you should see something similar to this:
```

/tmp/jdk-6-doc.zip has been unpacked and installed.
You can now delete it, if you wish.

```

Which means everthing went well. You don't have to remove the package from /tmp yourself, it'll get deleted on your next boot anyway.

---

### Post by haloedrain on 2007-05-20
I installed the sun-java6-jre and -jdk packages, but when I type java -version I get
> The program 'java' can be found in the following packages:
 * j2re1.4
 * gij-4.1
 * kaffe
 * jamvm
 * java-gcj-compat
 * cacao
 * sablevm
Try: sudo apt-get install <selected package>
Make sure you have the 'universe' component enabled
bash: java: command not found


I also tried the update-alternatives thing, it didn't help.

The javac command seems to work just fine, though.


**Edit:**  the following command fixed it:
> update-java-alternatives --set java-6-sun

I found that in /usr/share/doc/sun-java6-bin/README.alternatives

---

### Post by approaching on 2007-06-02
i went through those steps trying to get the java-6-doc.zip to get through the install, but instead of the unpacked install complete goodness that you got for output, this came out.

Setting up sun-java6-doc (6-00-2ubuntu2) ...
[/tmp/jdk-6-doc.zip]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of /tmp/jdk-6-doc.zip or
        /tmp/jdk-6-doc.zip.zip, and cannot find /tmp/jdk-6-doc.zip.ZIP, period.
dpkg: error processing sun-java6-doc (--configure):
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
 sun-java6-doc

is this saying something to the effect that i need the install cd? this was downloaded of the net, and there aren't more volumes available of this file.

---

### Post by zeroc on 2007-06-03
The installation went OK:
-------------------------------------------------------------------------------------------
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0-b105, mixed mode)
-------------------------------------------------------------------------------------------
There is also a symlink "docs" in /usr/lib/jvm/java-6-sun-1.6.0.00 to Javadocs,
but it doesn't show up in Eclipse:
-------------------------------------------------------------------------------------------
Note: This element neither has attached source nor attached Javadoc and 
 hence no information could be found.
-------------------------------------------------------------------------------------------
I am able to access Javadoc in Browser, so it's there. Any ideas/hints on that?

Thanks in advance!

---

### Post by approaching on 2007-06-09
ok, so i think i got it, i was actually wasn't downloading that file from the website, just wasn't paying much attention to it. it's actually a pretty big file, and seemingly requires the download manager that it wants to use. so just click on the checkbox, and let it open it with whatever program that it wants to use. just make sure that you download to somewhere you know. then follow what the rest of these guys have said.

---

### Post by davidma777 on 2007-06-10
These instructions don't seem to work when I do the install for sun-java6-jdk:

"2) Once it downloads the packages and begins the installation, you’ll get a screen that contains the Sun Operating System Distributor License for Java and hit Enter to continue. You’ll see a dialog that asks you if you agree with the DLJ license terms. Select Yes, and hit Enter; the JRE will finish installing."

What happens is the confirmation screen comes up and nothing I do is accepted. <Enter> does nothing, clicking on the OK at the bottom of the screen does nothing, forward slash <Enter> does not respond. How do I get the confirmation screen accepted? There is no "Yes" visible to select. Where is it hidden?

Dave A.

---

### Post by zeroc on 2007-06-12
> **zeroc said:**
> The installation went OK:
-------------------------------------------------------------------------------------------
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0-b105, mixed mode)
-------------------------------------------------------------------------------------------
There is also a symlink "docs" in /usr/lib/jvm/java-6-sun-1.6.0.00 to Javadocs,
but it doesn't show up in Eclipse:
-------------------------------------------------------------------------------------------
Note: This element neither has attached source nor attached Javadoc and 
 hence no information could be found.
-------------------------------------------------------------------------------------------
I am able to access Javadoc in Browser, so it's there. Any ideas/hints on that?

Thanks in advance!

Normally, when we are coding java in Eclipse, we do not see any javadoc help when we hover over a keyword. This is because by default, eclipse is not configured to use javadoc. This is how you can enable javadoc in eclipse.

1. In the package explorer select the JRE System LIbrary -> rt.jar and go to it's properties.

2. In the Javadoc Location provide the javadoc URL. This may be eiher a URL like "http://java.sun.com/javase/6/docs/api/" or a local path like mine "file:/usr/lib/jvm/java-6-sun/docs/api/" (if you have javadoc installed locally, which is recommended)

3. Now when you mouse-hover on a java method or something, you shall see its associated javadoc. If its lengthy and you can't see all of it, press F2.

[http://zaher14.blogspot.com/2007/05/using-javadoc-with-eclipse.html]("http://zaher14.blogspot.com/2007/05/using-javadoc-with-eclipse.html")

---

### Post by Gouz on 2007-09-27
Do you have any idea why I get this message?

Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

---

### Post by ZenWarrior on 2007-10-06
Attempting to install Java, but without success. :(

Followed the directions above, Java downloaded, but then I saw a screen which isn't in the instructions (I think). And quite frankly, I've forgotten exactly what it said, but there was an <OK>. However, hitting enter did nothing. In fact, there seemed no way to respond to it. The window was informational and there was no prompt, just the <OK> which did nothing.

I also did not see the following on the first try that left me with the seemingly nonfunctioning <OK> dialog :

> ...a screen that contains the Sun Operating System Distributor License for Java and hit Enter to continue. You’ll see a dialog that asks you if you agree with the DLJ license terms. Select Yes, and hit Enter; the JRE will finish installing.

So, I then shut down Terminal and began the process again. That delivered a message about something still being open and it continued no further. I only knew to quit Ubuntu to close whatever files were open and did so. 

I restarted Ubuntu and Terminal. Again I attempted to follow the Java installation instructions, but now I get the following:

```
jimmy@ubuntu:~$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
jimmy@ubuntu:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
jimmy@ubuntu:~$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
jimmy@ubuntu:~$ 
```

Help, please?

Also, why is it that Terminal reports an older version of Java being installed, but Firefox doesn't see it? About : plugins entered into Firefox does not list the older version of Java that Terminal says is there.

```
jimmy@ubuntu:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)
```

Oh, and I'm a complete noob so please bear with me. I'm finding I am oblivious to the obvious when it comes to Ubuntu and Linux.

---

### Post by ZenWarrior on 2007-10-06
> **davidma777 said:**
> These instructions don't seem to work when I do the install for sun-java6-jdk:

"2) Once it downloads the packages and begins the installation, you’ll get a screen that contains the Sun Operating System Distributor License for Java and hit Enter to continue. You’ll see a dialog that asks you if you agree with the DLJ license terms. Select Yes, and hit Enter; the JRE will finish installing."

What happens is the confirmation screen comes up and nothing I do is accepted. <Enter> does nothing, clicking on the OK at the bottom of the screen does nothing, forward slash <Enter> does not respond. How do I get the confirmation screen accepted? There is no "Yes" visible to select. Where is it hidden?

Sorry I didn't catch this before, but this appears to be the very same problem I mention just above. 

Thanks [IA] for some very much needed help.

---

### Post by ZenWarrior on 2007-10-08
Although it is not at all my intention, this posting may step on a few toes here.

I heard tons of good stuff about Ubuntu, and thus decided to give it a try. However, it is still light-years away from prime-time or coming the least bit close to taking over the world--regardless of what its supporters say.

Why is that? Well, I just read this somewhere else online and must agree--that is, community support of Ubuntu leaves much to be desired. (Please, this is meant as constructive criticism. I want Ubuntu/Linux to be everywhere just as much as any true Linux geek.) Yes, many questions get answered in these forums, but I have also noticed that many (far too many?) go unanswered--sometimes for days, weeks, or are never answered.

Take this thread and my question as an example. Obviously, I am having the same problem trying to follow this tutorial someone else is having. They have not received a response of any kind and neither have I. I know this may be difficult for some to understand, but if I'm to use Ubuntu it has to work. But without Java, a "modern" OS/browser combo just doesn't cut it. Java is needed to both play and work on the net. No Java means no functionality too many times.

An exception to what I've seen is **ago** over in the Wubi forum. Questions there at least get an, "I don't know." That serves to let a user know someone is at least paying attention--and might even care. However, I do not see the same prevalence of that at many other places in these forums. If you want to take over the world with Ubuntu, the very people you seek to convert (noobs) *must* be able to find some sort of support in a timely manner. And although life is casual for many, that means within 24 hours. More than that and life has been put on hold b/c of the problem.

For example, I cannot use Ubuntu at present simply because something which is as easy as pie with both Windows and Mac, installing and using Java, just isn't happening with Ubuntu. Posting here by me and someone else has not brought us help, but only continued frustration.

So although I *really* want to use Ubuntu, it's coming off my computer today--and likely for a very long time. It's useless if it doesn't work and the community doesn't help. Again, this is meant as constructive criticism that I hope someone recognizes as illuminating a real problem, and not as something unimportant, bogus, or trollish. 

However, feel free to flame away.  But as you do, please keep in mind that I would much rather be using Ubuntu to post this instead of Windows. Unfortunately, the next sites I'll be visiting require Java--but Ubuntu [apparently] hasn't placed very much importance on making Java happen for people who wish to adopt Ubuntu. In sum, no Java means no Ubuntu. And, a tutorial which doesn't work isn't a tutorial--it's wasted bytes and time.

That said, I do hope to check my mail sometime today and see a message that leads me back here to at least find someone *trying* to help, even if not offering a procedure which does. And again, I am not the only one saying this about Ubuntu's forums. Others see they aren't helped and turn away, too. That certainly isn't good for either Ubuntu or a "free" computing environment. It only rewards the de facto monopoly (i.e., Microsoft) we all would prefer to have less control over us and our computers.

---

### Post by Haruhara on 2007-10-21
When I type the command 

sudo apt-get install sun-java6-jre 

it returns

E: Couldn't find package sun-java6-jre

I do have the multiverse repository enabled as per [this website]("https://help.ubuntu.com/community/Java"). I also tried manually downloading it from Sun Java's website, and following their instructions listed [over here]("http://www.java.com/en/download/help/5000010500.xml#selfextracting"). Chmod claimed it couldn't find the file I had just downloaded. 

Any help would be appreciated.

---

### Post by Haruhara on 2007-10-21
Found the answer (to my own problem)!

It was listed [over here]("http://ubuntuforums.org/showthread.php?t=431116"). Google search helped me more than Ubuntu forums search, sorry for the unnecessary post.

---

### Post by jeffemmert on 2008-05-06
I tried step one by opening a terminal and typing: sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts. Everything seemed to be downloading. Eventually, there was a sun license agreement with an <ok> at the bottom, a graphic within the terminal that had no way of clicking the ok or saying yes or any other way of continuing the installation. It's the BSOD of Sun Java. Now what?

---

### Post by vvvladut on 2008-05-08
> **ZenWarrior said:**
> Although it is not at all my intention, this posting may step on a few toes here.

I heard tons of good stuff about Ubuntu, and thus decided to give it a try. However, it is still light-years away from prime-time or coming the least bit close to taking over the world--regardless of what its supporters say.

Why is that? Well, I just read this somewhere else online and must agree--that is, community support of Ubuntu leaves much to be desired. (Please, this is meant as constructive criticism. I want Ubuntu/Linux to be everywhere just as much as any true Linux geek.) Yes, many questions get answered in these forums, but I have also noticed that many (far too many?) go unanswered--sometimes for days, weeks, or are never answered.

Take this thread and my question as an example. Obviously, I am having the same problem trying to follow this tutorial someone else is having. They have not received a response of any kind and neither have I. I know this may be difficult for some to understand, but if I'm to use Ubuntu it has to work. But without Java, a "modern" OS/browser combo just doesn't cut it. Java is needed to both play and work on the net. No Java means no functionality too many times.

An exception to what I've seen is **ago** over in the Wubi forum. Questions there at least get an, "I don't know." That serves to let a user know someone is at least paying attention--and might even care. However, I do not see the same prevalence of that at many other places in these forums. If you want to take over the world with Ubuntu, the very people you seek to convert (noobs) *must* be able to find some sort of support in a timely manner. And although life is casual for many, that means within 24 hours. More than that and life has been put on hold b/c of the problem.

For example, I cannot use Ubuntu at present simply because something which is as easy as pie with both Windows and Mac, installing and using Java, just isn't happening with Ubuntu. Posting here by me and someone else has not brought us help, but only continued frustration.

So although I *really* want to use Ubuntu, it's coming off my computer today--and likely for a very long time. It's useless if it doesn't work and the community doesn't help. Again, this is meant as constructive criticism that I hope someone recognizes as illuminating a real problem, and not as something unimportant, bogus, or trollish. 

However, feel free to flame away.  But as you do, please keep in mind that I would much rather be using Ubuntu to post this instead of Windows. Unfortunately, the next sites I'll be visiting require Java--but Ubuntu [apparently] hasn't placed very much importance on making Java happen for people who wish to adopt Ubuntu. In sum, no Java means no Ubuntu. And, a tutorial which doesn't work isn't a tutorial--it's wasted bytes and time.

That said, I do hope to check my mail sometime today and see a message that leads me back here to at least find someone *trying* to help, even if not offering a procedure which does. And again, I am not the only one saying this about Ubuntu's forums. Others see they aren't helped and turn away, too. That certainly isn't good for either Ubuntu or a "free" computing environment. It only rewards the de facto monopoly (i.e., Microsoft) we all would prefer to have less control over us and our computers.

It's been more than 6 months...I can't believe that nobody has answered to this...at least to say that they empathize with you, or any sign or recognition at all...

You're absolutely right, the "great community support" that the Ubuntu advertises is far from being so great. I've been on this forum for a few months, with mixed results; some people have been very helpful, but I wouldn't call mixed results "great".

Anyway, your problem doesn't even seem so complicated after all: I think that the OK button would have become active if you tabbed your way through it, until it was highlighted, and then press enter. I know this has worked for me before. And when something asks for "superuser privileges" it means that you have to type "sudo" before the respective command. It will probably ask you for your password, and then it will run.

But that is not the point...the point is that someone should have bothered to reply. It's that simple. Anything. Just 3 words.

Ubuntu is still so close, yet so very far from its ambitions...

---

### Post by roadworrier on 2009-09-23
So, installing java 1.6 from apt-get in an sshed command-line window, and I got the same screen as others above "Do you agree with the DLJ license terms" <Yes> <No>

There's no indication of making a selection, no indication how to make a selection or continue or whatever. Through trial and error it appears that you make a selection with the TAB key, and then you confirm it with ENTER. Since you can't see what you're selecting, you may need to do what I did... Count the number of times you hit tab followed by enter. If that doesn't work, do one less, or one more the next time you try. Trial and error, but hitting tab and enter are your tools.

---

### Post by dhd1956 on 2009-09-24
I recently installed ubuntu.

I then installed java 6 and eclipse. I am able to use java in eclipse.

My latest installation is oracle-xe, which I haven't been able to configure.

When I try to use the apt-get command to install libaio1, it gets stuck on what it considers unfinished java installation.

The code is as follows:

dave@dave-desktop:~$ sudo apt-get install libaio1
[sudo] password for dave:
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
dave@dave-desktop:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of oracle-xe-universal:
 oracle-xe-universal depends on libaio (>= 0.3.96) | libaio1 (>= 0.3.96); however:
  Package libaio is not installed.
  Package libaio1 is not installed.
dpkg: error processing oracle-xe-universal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 oracle-xe-universal
dave@dave-desktop:~$ sudo apt-get install libaio1
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  sun-java6-bin sun-java6-jre
Suggested packages:
  sun-java6-plugin ia32-sun-java6-plugin sun-java6-fonts
Recommended packages:
  gsfonts-x11
The following NEW packages will be installed:
  libaio1
The following packages will be upgraded:
  sun-java6-bin sun-java6-jre
2 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
3 not fully installed or removed.
Need to get 0B/35.5MB of archives.
After this operation, 101MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ...
dpkg: serious warning: files list file for package `sun-java6-jre' missing, assuming package has no files currently installed.

//ending with...

Package configuration

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring sun-java6-jre &#9500;&#9472;&#9472;

a java screen follows with the terms and conditions ending with <Ok>. I cannot find a way of getting beyond this and have to restart the computer in order to be able to enter apt-get commands once more.

Any suggestions?

---

### Post by dhd1956 on 2009-09-24
> **jeffemmert said:**
> I tried step one by opening a terminal and typing: sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts. Everything seemed to be downloading. Eventually, there was a sun license agreement with an <ok> at the bottom, a graphic within the terminal that had no way of clicking the ok or saying yes or any other way of continuing the installation. It's the BSOD of Sun Java. Now what?

I get the same thing as indicated in my previous reply... I think finding a way to exit this BSOD will allow it to complete gracefully, but any key I hit has no effect on this.

---

### Post by closetmonsterrr on 2009-09-26
ok i installed everything and made it to the licensing, but since im a noob n couldnt figure out how to select the <OK> at the end, i closed the page n java doenst work...
how can i bring up the licensing/user agreement so i can ok it again?

---

### Post by closetmonsterrr on 2009-09-26
this is wat it says when i try to do:
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts


and then i get this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

how do i fix this?.. :O

---

### Post by pax5055 on 2009-09-27
still figuring out how to get it to work in firefox corectly when install, but in the license agreement to get to the bottom hit the TAB key to highlight it then hit enter.

---

### Post by alienclone on 2009-09-27
> **closetmonsterrr said:**
> this is wat it says when i try to do:
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts


and then i get this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

how do i fix this?.. :O


do what the error says to do, open terminal and type

```
dpkg --configure -a
```

---

### Post by m.nowak on 2009-10-30
This tutorial worked really good.

I am using Kubuntu 9.10 and Firefox 3.5 and this tutorial solved my Java-problems.

//Mattias

---

### Post by guriinii on 2009-11-04
java version "1.6.0_15"
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
Java HotSpot(TM) Client VM (build 14.1-b02, mixed mode, sharing)

Thanks worked a treat.

---

### Post by andor1970 on 2009-12-01
> **ZenWarrior said:**
> Attempting to install Java, but without success. :(

Followed the directions above, Java downloaded, but then I saw a screen which isn't in the instructions (I think). And quite frankly, I've forgotten exactly what it said, but there was an <OK>. However, hitting enter did nothing. In fact, there seemed no way to respond to it. The window was informational and there was no prompt, just the <OK> which did nothing.

I also did not see the following on the first try that left me with the seemingly nonfunctioning <OK> dialog :



So, I then shut down Terminal and began the process again. That delivered a message about something still being open and it continued no further. I only knew to quit Ubuntu to close whatever files were open and did so. 

I restarted Ubuntu and Terminal. Again I attempted to follow the Java installation instructions, but now I get the following:

```
jimmy@ubuntu:~$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
jimmy@ubuntu:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
jimmy@ubuntu:~$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
jimmy@ubuntu:~$ 
```Help, please?

Also, why is it that Terminal reports an older version of Java being installed, but Firefox doesn't see it? About : plugins entered into Firefox does not list the older version of Java that Terminal says is there.

```
jimmy@ubuntu:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)
```Oh, and I'm a complete noob so please bear with me. I'm finding I am oblivious to the obvious when it comes to Ubuntu and Linux.

After restarting ubuntu just follow the instructions in the terminal. So type
```
andor@KubuntuReserve:-$ sudo dpkg --configure -a
Setting up java-common (0.30 Ubuntu5) ...

Processing triggers for man-db ...
andor@KubuntuReserve:~$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
Reading package lists... Done                                                              
Building dependency tree                                                                   
Reading state information... Done                                                          
You might want to run `apt-get -f install' to correct these:                               
The following packages have unmet dependencies:                                            
  sun-java6-jre: Depends: sun-java6-bin (= 6-15-1) but it is not going to be installed or  
                          ia32-sun-java6-bin (= 6-15-1) but it is not installable          
                 Recommends: gsfonts-x11 but it is not going to be installed               
  sun-java6-plugin: Depends: sun-java6-bin (= 6-15-1) but it is not going to be installed  
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).  
andor@KubuntuReserve:~$ sudo apt-get -f install
Reading package lists... Done                  
Building dependency tree                       
Reading state information... Done              
Correcting dependencies... Done
```

Then in the Dialog screen hit the TAB button and "ok" will be selected. Hit Enter and you're off!

---

### Post by andor1970 on 2009-12-01
I know this question has been asked before, but no answer was being given. After my installation of java with the procedure above, no java plugin could be found in Firefox. Although if I entered "java -version" in the terminal I get"

```

andor@KubuntuReserve:~$ java -version                                                          
java version "1.6.0_15"                                                                        
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)                                           
Java HotSpot(TM) Client VM (build 14.1-b02, mixed mode, sharing) 
```

So it seems to be installed correctly. Does anyone know what could be wrong?

---

### Post by johnhdsi on 2009-12-02
Gmaster1440 all I can say is THANK YOU...I have done the java install by following the install directions off the java site every time and it is nothing less than confusing and frustrating...I followed your tut to the letter and BAM installed and working freakin great!  Much much thanks for making my life (and I'm sure alot of other peoples lives) easier.

John

---

### Post by mikey12561 on 2009-12-09
> **closetmonsterrr said:**
> ok i installed everything and made it to the licensing, but since im a noob n couldnt figure out how to select the <OK> at the end, i closed the page n java doenst work...
how can i bring up the licensing/user agreement so i can ok it again?

For those that are having an issue trying to select the Okay Button in the License agreement.

All you simply need to do it hit the tab button once. The okay will highlight in red and hit the enter key. Then it goes to the screen saying you must agree to the terms. Make sure you hit okay by moving the left arrow key. I believe it highlights no as the default. After that it will finish the installation without a single problem.

I do know one thing is it will not work in Konqueror after it is installed. The reason being is Java actually hasn't given support for Konqueror and there is a special thing that someone did that you have to get to get it to work. I will let you know now that konqueror sucks and you should stay with mozilla.

---

### Post by cornholder on 2009-12-22
(Running 9.04 here) I also had the problem with not being able to push the button in the Sun agreement dialog. What worked for me there was pushing the left and right keys, which highlighted the <ok> button. Of course, I closed the terminal at first when I couldn't click ok, which caused the same problem ZenWarrior had (post #17) but I got through that ok. Running java version in the terminal would not work however; it said it couldn't find a bunch of things. I closed that terminal window and can't find any logs of it, so unfortunately I can't paste in exactly what it said. I fixed this through Synaptic: type "java" in the search field, and maybe 12-15 entries down is the java 6 plugin, which was not checked. I just checked the box to install it, and now I can play all the other yahoo games besides chess!

---

### Post by TroyStachnik on 2010-06-04
when i try to install this is what i get:

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate

what should i do?

---

### Post by six^letters^digits on 2010-09-15
[java.com : How do I download and install Java for my Linux computer ?]("http://www.java.com/en/download/help/linux_install.xml")


[java.com : Download Java software for Linux]("http://www.java.com/en/download/linux_manual.jsp")

---

### Post by verevie on 2010-09-25
> **TroyStachnik said:**
> when i try to install this is what i get:

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate

what should i do?

Go to Software Sources in System>Administration and under the Other Software tab make sure that [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner is check. That's what fixed it for me.

---

### Post by xlinop on 2010-10-03
> **verevie said:**
> Go to Software Sources in System>Administration and under the Other Software tab make sure that [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner is check. That's what fixed it for me.

I did this but I'm still getting the error D:

---

### Post by corevalue on 2011-01-11
Three years on, and still this atrociously bad piece of software is killing would-be users. Installing Java shouldn't be easy, it should be trivial. 

Whoever thought accepting a license with an odd combination of Tab and enter was a good idea?

---

### Post by RedComputer on 2011-07-13
For me gives me a error
```
alexhr2000@alexhr2000-Satellite-Pro-A200:~$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
[sudo] password for alexhr2000: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package sun-java6-fonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'sun-java6-jre' has no installation candidate
E: Package 'sun-java6-plugin' has no installation candidate
E: Package 'sun-java6-fonts' has no installation candidate
alexhr2000@alexhr2000-Satellite-Pro-A200:~$ 

```

What i do?

I Use Kubuntu 11.4

---

### Post by rec9140 on 2011-08-18
> **RedComputer said:**
> For me gives me a error
```
alexhr2000@alexhr2000-Satellite-Pro-A200:~$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
[
E: Package 'sun-java6-jre' has no installation candidate
E: Package 'sun-java6-plugin' has no installation candidate
E: Package 'sun-java6-fonts' has no installation candidate
alexhr2000@alexhr2000-Satellite-Pro-A200:~$ 

```

What i do?

I Use Kubuntu 11.4

Sun Java is no longer packaged in the repos for easy install.

You will have to download it via the Sun Site and follow their instructions to insall.

Be sure to uninstall the useless openJDK stuff via Synaptic or apt-get

---

### Post by jdjenkins on 2011-09-10
This is what I used  to get Java working:

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner" 

sudo apt-get update

and then as posted earlier:

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

I used the Tab key to select the correct items in the Java license.

---

### Post by linux_nub on 2011-09-16
This is my output.:KS Can anyone say what the problem might be here ?

[COLOR=Blue]madiarasias@madiarasias-VPCEB15FG:~$ sudo apt-get install sun- java6- jre sun- java6- plugin sun- java6- fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Unable to locate package sun
E: Unable to locate package java6
E: Package 'jre' has no installation candidate
E: Unable to locate package sun
E: Unable to locate package java6
E: Unable to locate package plugin
E: Unable to locate package sun
E: Unable to locate package java6
E: Unable to locate package fonts
madiarasias@madiarasias-VPCEB15FG:~$ [/COLOR]

Thank you:D:D

---

### Post by linux_nub on 2011-09-16
> **rec9140 said:**
> Sun Java is no longer packaged in the repos for easy install.

You will have to download it via the Sun Site and follow their instructions to insall.

Be sure to uninstall the useless openJDK stuff via Synaptic or apt-get

On the sun site where it links you to the instructions for ubuntu,, the link they give you gives me this errore message : 
'firefox does nto know how to open this addresss because the protocol apt isnt associeated with any program"
  
:)

---

### Post by jimwill on 2011-09-16
Actually I'm running trinity maverick upgraded to natty. 
What I did was use either the Adept manager or the Synaptic Package Manager (I forget which it was) and had a graphical question to select yes/no on.

My problem was with getting Firefox to use the sun java instead of icetea! 
Finally resolved with the 
sudo update-java-alternatives --set java-6-sun 
given earlier. (had to use sudo which wasn't specified before)

Now Firefox is using the Sun Java and I'm able to use my webmin again!!!!

---

### Post by jdjenkins on 2011-09-17
Try what I used - in the Terminal:

sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"

and then this:

sudo apt-get update

and then repeat the command you were using before

JJ


> **linux_nub said:**
> On the sun site where it links you to the instructions for ubuntu,, the link they give you gives me this errore message : 
'firefox does nto know how to open this addresss because the protocol apt isnt associeated with any program"
  
:)

---

### Post by PayPaul on 2011-10-03
> **jdjenkins said:**
> Try what I used - in the Terminal:

sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"

and then this:

sudo apt-get update

and then repeat the command you were using before

JJ

I've tried the same thing as you suggested above. I also used synaptic to download and install what I believed to be the JRE Sun 6 applets. When I attempted the code to use alternatives for Firefox I got the following error messages:

```
update-alternatives: error: no alternatives for appletviewer.
update-alternatives: error: no alternatives for apt.
update-alternatives: error: no alternatives for extcheck.
update-alternatives: error: no alternatives for HtmlConverter.
update-alternatives: error: no alternatives for idlj.
update-alternatives: error: no alternatives for jar.
update-alternatives: error: no alternatives for jarsigner.
update-alternatives: error: no alternatives for javac.
update-alternatives: error: no alternatives for javadoc.
update-alternatives: error: no alternatives for javah.
update-alternatives: error: no alternatives for javap.
update-alternatives: error: no alternatives for java-rmi.cgi.
update-alternatives: error: no alternatives for jconsole.
update-alternatives: error: no alternatives for jdb.
update-alternatives: error: no alternatives for jhat.
update-alternatives: error: no alternatives for jinfo.
update-alternatives: error: no alternatives for jmap.
update-alternatives: error: no alternatives for jps.
update-alternatives: error: no alternatives for jrunscript.
update-alternatives: error: no alternatives for jsadebugd.
update-alternatives: error: no alternatives for jstack.
update-alternatives: error: no alternatives for jstat.
update-alternatives: error: no alternatives for jstatd.
update-alternatives: error: no alternatives for mozilla-javaplugin.so.
update-alternatives: error: no alternatives for native2ascii.
update-alternatives: error: no alternatives for rmic.
update-alternatives: error: no alternatives for schemagen.
update-alternatives: error: no alternatives for serialver.
update-alternatives: error: no alternatives for wsgen.
update-alternatives: error: no alternatives for wsimport.
update-alternatives: error: no alternatives for xjc.
update-alternatives: error: no alternatives for xulrunner-1.9-javaplugin.so.
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/appletviewer
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/apt
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/extcheck
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/HtmlConverter
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/idlj
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jarsigner
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jar
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javac
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javadoc
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javah
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jconsole
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jdb
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jhat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jinfo
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jmap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jps
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jrunscript
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jsadebugd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstack
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstatd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/native2ascii
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/rmic
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/schemagen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/serialver
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsgen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsimport
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/xjc
update-alternatives: error: no alternatives for mozilla-javaplugin.so.
update-alternatives: error: no alternatives for xulrunner-1.9-javaplugin.so.
paulw@ubuntu:~$ sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
paulw@ubuntu:~$ sudo apt-get update
Ign http://us.archive.ubuntu.com natty InRelease                               
Ign http://us.archive.ubuntu.com natty-updates InRelease                       
Hit http://us.archive.ubuntu.com natty Release.gpg                             
Hit http://us.archive.ubuntu.com natty-updates Release.gpg                     
Hit http://us.archive.ubuntu.com natty Release                                 
Hit http://us.archive.ubuntu.com natty-updates Release                         
Hit http://us.archive.ubuntu.com natty/main Sources                            
Hit http://us.archive.ubuntu.com natty/restricted Sources                      
Hit http://us.archive.ubuntu.com natty/universe Sources                        
Hit http://us.archive.ubuntu.com natty/multiverse Sources                      
Hit http://us.archive.ubuntu.com natty/main amd64 Packages                     
Hit http://us.archive.ubuntu.com natty/restricted amd64 Packages               
Hit http://us.archive.ubuntu.com natty/universe amd64 Packages                 
Hit http://us.archive.ubuntu.com natty/multiverse amd64 Packages               
Ign http://us.archive.ubuntu.com natty/main TranslationIndex                   
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex             
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex             
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex               
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Hit http://us.archive.ubuntu.com natty-updates/main Sources                    
Hit http://us.archive.ubuntu.com natty-updates/restricted Sources              
Hit http://us.archive.ubuntu.com natty-updates/universe Sources                
Hit http://us.archive.ubuntu.com natty-updates/multiverse Sources              
Hit http://us.archive.ubuntu.com natty-updates/main amd64 Packages             
Hit http://us.archive.ubuntu.com natty-updates/restricted amd64 Packages       
Hit http://us.archive.ubuntu.com natty-updates/universe amd64 Packages         
Hit http://us.archive.ubuntu.com natty-updates/multiverse amd64 Packages       
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex           
Hit http://ppa.launchpad.net natty Release.gpg                                 
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex       
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main amd64 Packages                         
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main amd64 Packages                         
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main amd64 Packages                         
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://us.archive.ubuntu.com natty/main Translation-en_US                  
Ign http://us.archive.ubuntu.com natty/main Translation-en                     
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US            
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en               
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com natty/restricted Translation-en               
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US              
Ign http://us.archive.ubuntu.com natty/universe Translation-en                 
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en             
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US    
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en       
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en       
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://extras.ubuntu.com natty InRelease                                   
Ign http://archive.canonical.com natty InRelease                               
Ign http://archive.canonical.com lucid InRelease
Ign http://security.ubuntu.com natty-security InRelease
Hit http://extras.ubuntu.com natty Release.gpg 
Hit http://archive.canonical.com natty Release.gpg
Hit http://security.ubuntu.com natty-security Release.gpg
Hit http://extras.ubuntu.com natty Release     
Get:1 http://archive.canonical.com lucid Release.gpg [198 B]          
Hit http://security.ubuntu.com natty-security Release
Hit http://extras.ubuntu.com natty/main Sources                       
Hit http://archive.canonical.com natty Release 
Hit http://security.ubuntu.com natty-security/main Sources                     
Hit http://extras.ubuntu.com natty/main amd64 Packages               
Ign http://extras.ubuntu.com natty/main TranslationIndex             
Get:2 http://archive.canonical.com lucid Release [8,215 B]           
Hit http://security.ubuntu.com natty-security/restricted Sources               
Hit http://security.ubuntu.com natty-security/universe Sources                 
Hit http://security.ubuntu.com natty-security/multiverse Sources               
Hit http://security.ubuntu.com natty-security/main amd64 Packages              
Hit http://security.ubuntu.com natty-security/restricted amd64 Packages        
Hit http://security.ubuntu.com natty-security/universe amd64 Packages          
Hit http://security.ubuntu.com natty-security/multiverse amd64 Packages
Ign http://security.ubuntu.com natty-security/main TranslationIndex
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex
Ign http://security.ubuntu.com natty-security/universe TranslationIndex
Hit http://archive.canonical.com natty/partner Sources               
Hit http://archive.canonical.com natty/partner amd64 Packages        
Ign http://archive.canonical.com natty/partner TranslationIndex      
Get:3 http://archive.canonical.com lucid/partner Sources [6,836 B]   
Get:4 http://archive.canonical.com lucid/partner amd64 Packages [13.8 kB]      
Ign http://archive.canonical.com lucid/partner TranslationIndex                
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Ign http://extras.ubuntu.com natty/main Translation-en                         
Ign http://security.ubuntu.com natty-security/main Translation-en_US           
Ign http://security.ubuntu.com natty-security/main Translation-en              
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US     
Ign http://security.ubuntu.com natty-security/multiverse Translation-en        
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US     
Ign http://security.ubuntu.com natty-security/restricted Translation-en        
Ign http://security.ubuntu.com natty-security/universe Translation-en_US       
Ign http://security.ubuntu.com natty-security/universe Translation-en          
Ign http://archive.canonical.com natty/partner Translation-en_US               
Ign http://archive.canonical.com natty/partner Translation-en                  
Ign http://archive.canonical.com lucid/partner Translation-en_US               
Ign http://archive.canonical.com lucid/partner Translation-en                  
Fetched 29.0 kB in 6s (4,146 B/s)                                              
Reading package lists... Done
paulw@ubuntu:~$ sudo update-java-alternatives --set java-6-sun 
update-alternatives: error: no alternatives for appletviewer.
update-alternatives: error: no alternatives for apt.
update-alternatives: error: no alternatives for extcheck.
update-alternatives: error: no alternatives for HtmlConverter.
update-alternatives: error: no alternatives for idlj.
update-alternatives: error: no alternatives for jar.
update-alternatives: error: no alternatives for jarsigner.
update-alternatives: error: no alternatives for javac.
update-alternatives: error: no alternatives for javadoc.
update-alternatives: error: no alternatives for javah.
update-alternatives: error: no alternatives for javap.
update-alternatives: error: no alternatives for java-rmi.cgi.
update-alternatives: error: no alternatives for jconsole.
update-alternatives: error: no alternatives for jdb.
update-alternatives: error: no alternatives for jhat.
update-alternatives: error: no alternatives for jinfo.
update-alternatives: error: no alternatives for jmap.
update-alternatives: error: no alternatives for jps.
update-alternatives: error: no alternatives for jrunscript.
update-alternatives: error: no alternatives for jsadebugd.
update-alternatives: error: no alternatives for jstack.
update-alternatives: error: no alternatives for jstat.
update-alternatives: error: no alternatives for jstatd.
update-alternatives: error: no alternatives for mozilla-javaplugin.so.
update-alternatives: error: no alternatives for native2ascii.
update-alternatives: error: no alternatives for rmic.
update-alternatives: error: no alternatives for schemagen.
update-alternatives: error: no alternatives for serialver.
update-alternatives: error: no alternatives for wsgen.
update-alternatives: error: no alternatives for wsimport.
update-alternatives: error: no alternatives for xjc.
update-alternatives: error: no alternatives for xulrunner-1.9-javaplugin.so.
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/appletviewer
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/apt
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/extcheck
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/HtmlConverter
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/idlj
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jarsigner
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jar
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javac
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javadoc
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javah
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jconsole
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jdb
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jhat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jinfo
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jmap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jps
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jrunscript
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jsadebugd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstack
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstatd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/native2ascii
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/rmic
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/schemagen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/serialver
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsgen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsimport
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/xjc
update-alternatives: error: no alternatives for mozilla-javaplugin.so.
update-alternatives: error: no alternatives for xulrunner-1.9-javaplugin.so.

```

Java seems to be really messed up for Linux and perhaps even for windows. With Oracle taking over for Sun the process of installation seems to be much more complicated. On the Oracle site I saw a number of tar.gz files as well another type of file called an "rpm". My recent experience with tar files and source files hasn't been good with too many errors and too much hacking involved with the source codes of certain programs to make that pursuit worth it. The programs I was trying source code installation on unfortunately were also old and support from the developers seems to have ceased.:(

To be honest Java or no Java really doesn't effect me too much. My quest for it only started when I got a program yesterday for molecular modeling and the website for downloading parameter files for manipulation in that program required Java to be enabled in Firefox. Apparently the Linux version of FF doesn't enable it or add it by default. Maybe that's because of all the messed up programming or installations of it. Should I even bother with it? If it's not fixable within a reasonable amount of time I can't see the point.

---

### Post by PayPaul on 2011-10-03
> **jdjenkins said:**
> This is what I used  to get Java working:

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)



Thanks for the link to this thread. I was able to download and install via the Software Center, the plugin for firefox. It works now and I was able to download those molecule PDB files from the site. I wonder if there's any place here I could upload them to for display purposes. It's a cool program. It's called Pymol.

---

### Post by ratcheer on 2011-12-02
Here is a clear set of instructions I found to install Oracle Java 7. I am going to try them. I'll report back as to whether it works.

[http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html)

Tim

---

### Post by ratcheer on 2011-12-02
> **ratcheer said:**
> Here is a clear set of instructions I found to install Oracle Java 7. I am going to try them. I'll report back as to whether it works.

[http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html)


***This worked perfectly.***

```
tim@tim-oneiric:~/Downloads/oracle-jdk-7$ java -version
java version "1.7.0"
Java(TM) SE Runtime Environment (build 1.7.0-b147)
Java HotSpot(TM) 64-Bit Server VM (build 21.0-b17, mixed mode)
tim@tim-oneiric:~/Downloads/oracle-jdk-7$ javac -version
javac 1.7.0
```

And the Java 1.7.0 plugin is installed and working in my web browser.

Tim

---

### Post by Linforcer on 2011-12-17
This does not work in Kubuntu as the last step requires gksudo, which of course is not present in Kubuntu (is also not in repositories by default. On top of all this, it installs gtk and some other stuff, when this could probably be done in a console.

Meanwhile I'm still struggling to get it to work in Kubuntu

---

