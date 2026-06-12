---
title: "No Java in Firefox 3.6 via Ubuntuzilla?"
date: 2010-01-21
forum: Ubuntuzilla
---

### Post by dmaxel on 2010-01-21
Hi there. I am very happy that I found this so I could update to the newest Firefox (I'm paranoid like that). However, I found out that it doesn't want to find Java (worked fine in the Ubuntu-provided 3.5.7). I tried installing Java over the "Install Missing Plugin" button, but it said that it was already installed. I even tried the alternative (something called IceTea apparently?), installed that, then restarted Firefox with no effect. I even looked in this forum and followed the "provide manual link" suggestion, but that didn't work either. Any help on this?

---

### Post by nanotube on 2010-01-22
> **dmaxel said:**
> Hi there. I am very happy that I found this so I could update to the newest Firefox (I'm paranoid like that). However, I found out that it doesn't want to find Java (worked fine in the Ubuntu-provided 3.5.7). I tried installing Java over the "Install Missing Plugin" button, but it said that it was already installed. I even tried the alternative (something called IceTea apparently?), installed that, then restarted Firefox with no effect. I even looked in this forum and followed the "provide manual link" suggestion, but that didn't work either. Any help on this?

hi
this is due to a bug in the sun-java6-plugin package in karmic:
[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/509727](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/509727)

also described in the ubuntuzilla faq:
[https://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Java_plugin_not_showing_up_.28on_Ubuntu_Karmic.29](https://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Java_plugin_not_showing_up_.28on_Ubuntu_Karmic.29)

use the provided workaround command, and everything will be fixed. :)

---

### Post by dmaxel on 2010-01-22
The one in the Wiki for Karmic? I tried that too, still didn't work. :(

---

### Post by peakshysteria on 2010-01-22
Stalemate hear as well. No Java :( 

java version gives me:

> java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.6.1) (6b16-1.6.1-3ubuntu1)
OpenJDK Client VM (build 14.0-b16, mixed mode, sharing)

about:config shows no java either.

[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/509727](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/509727) did not help.

---

### Post by modean987 on 2010-01-22
The libjavaplugin_oji.so no longer works.

In your firefox plugins directory add a symbolic link to the NEW plugin.

ln -s /usr/local/java/jre1.6.0_18/lib/i386/libnpjp2.so libnpjp2.so 

Change your path accordingly.

Disclaimer: This works with a mozilla 3.6 tarball.

Info: [http://java.sun.com/javase/6/webnotes/install/jre/manual-plugin-install-linux.html](http://java.sun.com/javase/6/webnotes/install/jre/manual-plugin-install-linux.html)

The above link assumes you're using Sun's latest JRE installed in /usr/local. For those of you using Ubuntu's Sun packages, the appropriate symbolic link would be:

ln -s /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so libnpjp2.so

---

### Post by nanotube on 2010-01-22
did you follow the steps precisely? execute the command:
```
sudo update-alternatives --install /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so 50
```

then restart your browser?

does a libjavaplugin.so show up in /usr/lib/mozilla/plugins?

---

### Post by peakshysteria on 2010-01-22
I'm sorry man. No cigar. I don't understand this at all. I think I have to Java plugins installed. And I must say I don't understand this symbolic link thing at all either. Terminal stuff ain't my strong side.

Any simple solutions for us Java-novices?

nanotube: yes libjavaplugin.so shows up in /usr/lib/mozilla/plugins

---

### Post by modean987 on 2010-01-22
> **peakshysteria said:**
> 
Any simple solutions for us Java-novices?

nanotube: yes libjavaplugin.so shows up in /usr/lib/mozilla/plugins

Terminal mode isn't hard to use... just a pain to type in. Copy-n-paste is your friend. As I mentioned before, libjavaplugin.so does NOT work any more starting with firefox 3.6. It's obsolete. It's kaput, gone by the wayside, pushing up daisies, etc. You need to start using libnpjp2.so

So, shut down firefox, pull up a terminal window, and type this:

cd /usr/lib/mozilla/plugins

Then type this if you're using Ubuntu's Java JRE (copy and paste it into the terminal window):

sudo ln -s /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so libnpjp2.so

Then start firefox. Java should now work.

---

### Post by nanotube on 2010-01-22
> **peakshysteria said:**
> I'm sorry man. No cigar. I don't understand this at all. I think I have to Java plugins installed. And I must say I don't understand this symbolic link thing at all either. Terminal stuff ain't my strong side.

Any simple solutions for us Java-novices?

nanotube: yes libjavaplugin.so shows up in /usr/lib/mozilla/plugins

is package sun-java6-plugin installed?

---

### Post by nanotube on 2010-01-22
> **modean987 said:**
> Terminal mode isn't hard to use... just a pain to type in. Copy-n-paste is your friend. As I mentioned before, libjavaplugin.so does NOT work any more starting with firefox 3.6. It's obsolete. It's kaput, gone by the wayside, pushing up daisies, etc. You need to start using libnpjp2.so

So, shut down firefox, pull up a terminal window, and type this:

cd /usr/lib/mozilla/plugins

Then type this if you're using Ubuntu's Java JRE (copy and paste it into the terminal window):

sudo ln -s /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so libnpjp2.so

Then start firefox. Java should now work.

modean987: your link command does exactly the same thing functionally as the update-alternatives command, except it doesn't register the link with the alternatives system. use it if you want, it's just fine - but update-alternatives is the more 'proper' way.

---

### Post by peakshysteria on 2010-01-22
I seem to remember for some time ago exactly the same problem. Right now I think I have both IcedTea and the official Java installed. Copy/paste is easy for me as well, as you guys point out. But it doesn't work at all. I just get prompted for my password. After typing that and hitting enter all seems good. But it ain't. All is the same. about:plugins shows no java.

---

### Post by nanotube on 2010-01-22
> **peakshysteria said:**
> I seem to remember for some time ago exactly the same problem. Right now I think I have both IcedTea and the official Java installed. Copy/paste is easy for me as well, as you guys point out. But it doesn't work at all. I just get prompted for my password. After typing that and hitting enter all seems good. But it ain't. All is the same. about:plugins shows no java.

did you completely restart your browser? is package 'sun-java6-plugin' installed?

---

### Post by modean987 on 2010-01-22
> **nanotube said:**
> modean987: your link command does exactly the same thing functionally as the update-alternatives command, except it doesn't register the link with the alternatives system. use it if you want, it's just fine - but update-alternatives is the more 'proper' way.

Ack! You're right. I always forget that... I run a hybrid system, downloading the mozilla.com tarball directly. Sorry... I'll bow out of the discussion to avoid further confusion.

---

### Post by nanotube on 2010-01-22
> **modean987 said:**
> Ack! You're right. I always forget that... I run a hybrid system, downloading the mozilla.com tarball directly. Sorry... I'll bow out of the discussion to avoid further confusion.

hey no problem - just pointing it out. :)

---

### Post by dmaxel on 2010-01-22
Well, I did do the alternatives install command, yes I do have the sun-java-6 package installed, and I do find the sym link to be there, but Firefox is stubborn.

---

### Post by charonn0 on 2010-01-23
Just my $0.02 here:

I had done the old symlink to the /plugins dir before and it had worked. Now with 3.6, the command from the Ubuntuzilla wiki made everything work for me:

```
sudo update-alternatives --install /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so 50
```

---

### Post by peakshysteria on 2010-01-23
> **charonn0 said:**
> Just my $0.02 here:

I had done the old symlink to the /plugins dir before and it had worked. Now with 3.6, the command from the Ubuntuzilla wiki made everything work for me:

```
sudo update-alternatives --install /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so 50
```

Does not work in my end. Still no Java.

---

### Post by nanotube on 2010-01-23
well, all i can say is to make sure sun-java6-plugin is installed, get the symlink in there with update-alternatives, and restart the browser. this is what has worked for me, and i don't know of any reason it wouldn't work for you.

note that this is for ubuntu karmic only - earlier versions should have that symlink by default, if sun-java6-plugins is installed. you should not need to run the update-alternatives command, all you would need is to install sun-java6-plugin.

---

### Post by peakshysteria on 2010-01-24
No Java working.When going to the Java site I get prompted by the Plugin manager to Install Missing plugins. Clicking that gives me a prompt to install either one of IcedTea or sun-java6-plugin. I choose sun-java6-plugin but then I get prompted that it is allready installed. Going to the Menu --> Tools --> Addons --> Plugins it does not show. about:plugins gives me the same. No Java.

Going to the Java site they explain how to use the Java Control Panel:

> SOLUTION

To see whether your browser is configured to use Java or not, first open Windows Control Panel. From the Start menu button, select Settings, then Control Panel to open the Control Panel. You should see Java Coffee Cup logo icon in the Control Panel.

6.0

   1. Double-click the icon to open Java Control Panel.
   2. In Java Control Panel, click the Advanced tab.
   3. Click on + icon next to Default Java for browsers.
   4. Make sure the box next to Internet Explorer, Netscape, or Mozilla is checked.
   5. If it is not checked, click the checkbox to enable Java for your Web browser.
   6. Click Apply. 



In Ubuntu the Control Panel says: Command to launch default browser. And then you can put the filepath to the browser of your choice. Mine says: /usr/bin/firefox. Not sure if this is the right file path for FF 3.6 or not? Under Applications --> Internet I can see two entries of firefox (Firefox Web browser and Mozilla Build of Firefox).

```
java -version
```gives me:

> java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.6.1) (6b16-1.6.1-3ubuntu1)
OpenJDK Client VM (build 14.0-b16, mixed mode, sharing)

---

### Post by nanotube on 2010-01-24
peakshysteria:

ok, so first, post output of ```
ls -al /usr/lib/mozilla/firefox
```

second, post output of ```
ls -al /etc/alternatives/mozilla-javaplugin.so
```

third: post output of ```
ls -al /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so
```

fourth: which version of ubuntu are you using?  on my karmic install, with sun-java6-plugin out of the repos, "java -version" shows:
```
java version "1.6.0_15"
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
Java HotSpot(TM) Client VM (build 14.1-b02, mixed mode, sharing)
```
which is different from yours...
aha wait, yours is 'openjdk' rather than the plugin from java. probably that's the issue? well post the output of the other commands anyway.

also, /usr/bin/firefox should be right, if you have installed the ubuntuzilla package.

---

### Post by peakshysteria on 2010-01-24
Thanks for helping nanotube. I'm currently with Ubuntu 9.10 Karmic Koala. This is the output of your above mentioned commands:

> peaks@peaks-desktop:~$ ls -al /usr/lib/mozilla/firefox
ls: cannot access /usr/lib/mozilla/firefox: No such file or directory
peaks@peaks-desktop:~$ ls -al /etc/alternatives/mozilla-javaplugin.so
lrwxrwxrwx 1 root root 57 2010-01-22 19:01 [COLOR="DeepSkyBlue"][COLOR="MediumTurquoise"]/etc/alternatives/mozilla-javaplugin.so[/COLOR][/COLOR] -> /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so
peaks@peaks-desktop:~$ ls -al /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so
-rw-r--r-- 1 root root 72908 2009-07-31 15:46 /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so
peaks@peaks-desktop:~$ 


---

### Post by nanotube on 2010-01-24
> **peakshysteria said:**
> Thanks for helping nanotube. I'm currently with Ubuntu 9.10 Karmic Koala. This is the output of your above mentioned commands:

hey, sorry about it, first one was supposed to be
```
ls -al /usr/lib/mozilla/plugins
```
please give me that one

that said... looks like you're set to use the openjdk icedtea plugin. 

would you be averse to trying to use the sun-java6 plugin instead?
if not, then run
```
sudo update-alternatives --config mozilla-javaplugin.so
```
and from the list provided select the "/usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so" option.

then restart the browser and see if it shows up in about:plugins :)

---

### Post by peakshysteria on 2010-01-24
peaks@peaks-desktop:~$ ls -al /usr/lib/mozilla/plugins
total 380
drwxr-xr-x 2 root root   4096 2010-01-22 19:01 .
drwxr-xr-x 4 root root   4096 2008-07-02 12:21 ..
lrwxrwxrwx 1 root root     37 2009-10-08 00:06 [COLOR="MediumTurquoise"]flashplugin-alternative.so[/COLOR] -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root     39 2010-01-22 19:01 [COLOR="MediumTurquoise"]libjavaplugin.so[/COLOR] -> /etc/alternatives/mozilla-javaplugin.so
-rw-r--r-- 1 root root   5400 2009-12-13 13:08 librhythmbox-itms-detection-plugin.so
-rw-r--r-- 1 root root  96200 2009-11-11 10:09 libtotem-cone-plugin.so
-rw-r--r-- 1 root root 104768 2009-11-11 10:09 libtotem-gmp-plugin.so
-rw-r--r-- 1 root root  71612 2009-11-11 10:09 libtotem-mully-plugin.so
-rw-r--r-- 1 root root  75904 2009-11-11 10:09 libtotem-narrowspace-plugin.so
peaks@peaks-desktop:~$ 

sudo update-alternatives --config mozilla-javaplugin.so seemed to work nicely. I love you man. Trying to log into my bank loads the applet. But it takes between two and four minutes to get in. Nevermind that. Now I only use about 10% CPU. Earlier I used about 98%  Going to the Java site to test it tells me I now have Your Java version is Version 6 Update 16. And they recommend me to install Your Java version is Version 6 Update 18. Anyways, I'm content. Thanks a million man.

---

### Post by nanotube on 2010-01-24
> **peakshysteria said:**
> peaks@peaks-desktop:~$ ls -al /usr/lib/mozilla/plugins
total 380
drwxr-xr-x 2 root root   4096 2010-01-22 19:01 .
drwxr-xr-x 4 root root   4096 2008-07-02 12:21 ..
lrwxrwxrwx 1 root root     37 2009-10-08 00:06 [COLOR="MediumTurquoise"]flashplugin-alternative.so[/COLOR] -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root     39 2010-01-22 19:01 [COLOR="MediumTurquoise"]libjavaplugin.so[/COLOR] -> /etc/alternatives/mozilla-javaplugin.so
-rw-r--r-- 1 root root   5400 2009-12-13 13:08 librhythmbox-itms-detection-plugin.so
-rw-r--r-- 1 root root  96200 2009-11-11 10:09 libtotem-cone-plugin.so
-rw-r--r-- 1 root root 104768 2009-11-11 10:09 libtotem-gmp-plugin.so
-rw-r--r-- 1 root root  71612 2009-11-11 10:09 libtotem-mully-plugin.so
-rw-r--r-- 1 root root  75904 2009-11-11 10:09 libtotem-narrowspace-plugin.so
peaks@peaks-desktop:~$ 

sudo update-alternatives --config mozilla-javaplugin.so seemed to work nicely. I love you man. Trying to log into my bank loads the applet. But it takes between two and four minutes to get in. Nevermind that. Now I only use about 10% CPU. Earlier I used about 98%  Going to the Java site to test it tells me I now have Your Java version is Version 6 Update 16. And they recommend me to install Your Java version is Version 6 Update 18. Anyways, I'm content. Thanks a million man.

awesome! and you're quite welcome :)

so the culprit was the icedtea plugin from openjdk... i'll know to point people to this thread if they have similar problems. :)

---

### Post by _atle_ on 2010-01-25
I want to thank you for this fix. Though, for 64bit systems the command line should be:> sudo update-alternatives --install /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so /usr/lib64/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so 50
And not: > sudo update-alternatives --install /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so 50

Once again, thanks.

atlef.

---

### Post by nanotube on 2010-01-25
> **_atle_ said:**
> I want to thank you for this fix. Though, for 64bit systems the command line should be:
And not: 

Once again, thanks.

atlef.

thanks for the tip!

---

### Post by mlissner on 2010-02-03
> **nanotube said:**
> 
```
sudo update-alternatives --config mozilla-javaplugin.so
```and from the list provided select the "/usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so" option.

then restart the browser and see if it shows up in about:plugins

This worked for me, thanks.

---

### Post by Tomrac on 2010-02-18
Hello 

I' m new here and in Ubuntu and I have the same problem like the author of this thread. 
I' m using Ubuntu 9.04 x64 version and I updated Firefox to 3.6 and no Java now working :< In Chrome Java works fine but not in firefox :<
I tryed some help from Poland Ubuntu forum but nothing works. 

This is what sudo update-alternatives --config mozilla-javaplugin.sogive : 
         ```
1    /usr/java/jre1.6.0_18/lib/i386/libnpjp2.so
*+        2    /usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so
          3    /usr/lib64/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so
```
None of them fix the issue. 
 

Some help ? :<

---

### Post by ismaelito on 2010-02-18
This code has fixed java in Firefox 3.6, Thanks :D

```
sudo update-alternatives --config mozilla-javaplugin.so
```

---

### Post by nanotube on 2010-02-18
> **Tomrac said:**
> Hello 

I' m new here and in Ubuntu and I have the same problem like the author of this thread. 
I' m using Ubuntu 9.04 x64 version and I updated Firefox to 3.6 and no Java now working :< In Chrome Java works fine but not in firefox :<
I tryed some help from Poland Ubuntu forum but nothing works. 

This is what sudo update-alternatives --config mozilla-javaplugin.sogive : 
         ```
1    /usr/java/jre1.6.0_18/lib/i386/libnpjp2.so
*+        2    /usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so
          3    /usr/lib64/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so
```
None of them fix the issue. 
 

Some help ? :<

if you're running 32bit firefox (which you are if you are getting the official mozilla build), then you should be using a 32bit java plugin, not a 64bit java plugin. (this would be option 1 in your list - assuming that file actually exists - check).

---

### Post by Tomrac on 2010-02-18
My version of FF (I upgrade it by using ubuntuzilla )```
Mozilla/5.0 (X11; U; Linux i686 (x86_64); pl; rv:1.9.2) Gecko/20100115 Firefox/3.6
```The first option didn t fix the problem :<

Edit : When the first option is on in FF in plugins I have Java but it is not working while using FF (YouTube says that i don t hava Java but in Chrome it works fine). When the second and the last option is on FF don t have Java in plugins and it is not working.

---

### Post by nanotube on 2010-02-18
> **Tomrac said:**
> My version of FF (I upgrade it by using ubuntuzilla )```
Mozilla/5.0 (X11; U; Linux i686 (x86_64); pl; rv:1.9.2) Gecko/20100115 Firefox/3.6
```The first option didn t fix the problem :<

Edit : When the first option is on in FF in plugins I have Java but it is not working while using FF (YouTube says that i don t hava Java but in Chrome it works fine). When the second and the last option is on FF don t have Java in plugins and it is not working.

Hi
is it possible that you're talking about flash, not java? because youtube doesn't use java, it uses flash...

---

### Post by Tomrac on 2010-02-18
No no no maybe a gived a bad example :) 

When I am trying to watch something on YT i get : You JavaScript is off or you are using old version of Adobe Flash Player (I translated it from Polish). 

And when I am on sites for example : [http://www.ubucentrum.net/](http://www.ubucentrum.net/)
I get a information on the top that I need a aditional plugins to show all the page so i click to install the plugin and FF say that I need Adobe Flash Player and I need to get it manualy. 

This is what Java -version command give back :
```

java version "1.6.0_16"
Java(TM) SE Runtime Environment (build 1.6.0_16-b01)
Java HotSpot(TM) 64-Bit Server VM (build 14.2-b01, mixed mode)
```

Like I said before FF show that Java Plugin is on : 
[IMG]http://img35.imageshack.us/img35/2781/javae.png[/IMG]

---

### Post by nanotube on 2010-02-18
> **Tomrac said:**
> No no no maybe a gived a bad example :) 

When I am trying to watch something on YT i get : You JavaScript is off or you are using old version of Adobe Flash Player (I translated it from Polish). 

And when I am on sites for example : [http://www.ubucentrum.net/](http://www.ubucentrum.net/)
I get a information on the top that I need a aditional plugins to show all the page so i click to install the plugin and FF say that I need Adobe Flash Player and I need to get it manualy. 

This is what Java -version command give back :
```

java version "1.6.0_16"
Java(TM) SE Runtime Environment (build 1.6.0_16-b01)
Java HotSpot(TM) 64-Bit Server VM (build 14.2-b01, mixed mode)
```

Like I said before FF show that Java Plugin is on : 
[IMG]http://img35.imageshack.us/img35/2781/javae.png[/IMG]

well, hate to break it to you ;), but java and javascript are /completely/ different things!

the "your javascript is off" message has nothing to do with the java plugin. 

if you haven't turned off javascript (or installed an addon such as noscript) then your problem is an old (or missing) flash plugin. in your screenshot above, your plugins list only includes java - so it looks like flash is missing... but still let's test your javascript just in case.

so, first, test if your javascript is on: go to this page:
[http://liblearn.osu.edu/tutor/jscript.html](http://liblearn.osu.edu/tutor/jscript.html)
and if an alert box comes up saying "you can use javascript" with an ok button, then your javascript is on. if it doesn't then it's turned off.

if javascript is on, then what you need to do is grab the latest flash player. best way to do it: install package "flashplugin-installer" from the ubuntu repos, ```
sudo apt-get install flashplugin-installer
```
restart firefox, then check to see that in your firefox plugins list flashplayer 10.0.45 shows up.

---

### Post by Tomrac on 2010-02-18
The page shows that I can use javascript :< 

In synaptic I get that it is installed : 
[IMG]http://img705.imageshack.us/img705/5076/synaptic.png[/IMG]

But not in the version that FF shows :< 

In Chrome flash runs fine :<

---

### Post by nanotube on 2010-02-18
> **Tomrac said:**
> The page shows that I can use javascript :< 

In synaptic I get that it is installed : 
[IMG]http://img705.imageshack.us/img705/5076/synaptic.png[/IMG]

But not in the version that FF shows :< 

In Chrome flash runs fine :<

ah, well, of course - you're on 64bit, and so the flashplugin-installer coming from the repos will install 64bit flash plugin. 

but since you're running 32bit firefox, you need a 32bit flash plugin to go with it.

follow these step by step instructions to manually install a 32bit flash plugin:
[https://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#Flash](https://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#Flash)

---

### Post by Tomrac on 2010-02-18
It' s alive :) :) :) 

Man thanks  :) and sorry for me being so noob :p

---

### Post by nanotube on 2010-02-18
> **Tomrac said:**
> It' s alive :) :) :) 

Man thanks  :) and sorry for me being so noob :p

hey no prob - we all have to start somewhere. :)

---

### Post by Agent.Logic_ on 2010-03-23
Switching to the non-repository Firefox has been a real nightmare. First, it took me a while to try and fix the flash plugin problem. Now that it was fixed, the java plugin gave me  headache.

From what I understand, **using Ubuntuzilla installs the 32-bit version of Firefox**. So, anyone running a 64-bit OS and is having trouble with the solutions in this topic, you'll have to install the **ia32-sun-java6-bin** package from the repository. You might also want to check if the **libnpjp.so** file is in your ~/.mozilla directory before restarting firefox to check if the plugin is installed properly. If not, the **libnpjp2.so** file can be found in:

```
/usr/lib/jvm/ia32-java-6-sun-1.6.x.x/jre/lib
```

Just add a symlink to this file in the ~/.mozilla folder. It took me a bit of googling to figure out that I needed the 32-bit version of Java for this. Just saving some headaches for those who don't go through the user manual @ the Ubuntuzilla site from top to bottom. :P

---

### Post by roton on 2010-03-24
> **_atle_ said:**
> I want to thank you for this fix. Though, for 64bit systems the command line should be:
And not: 

Once again, thanks.

atlef.


Just wanted to say thanks Atlef. It was indeed the path I was getting wrong. It seems obvious now I look at it but with everyone listing the i386 path I forgot to check that it was actually correct.

---

### Post by Yleeyas on 2010-03-28
Hi there.

I installed FF3.6.2 using the Ubuntuzilla process, via repos, and I'm afraid I've got the missing Java problem.

I've gone through this thread a couple of times and I think I've just confused myself, so I'll give you my details and hope a fresh set of eyes will sort things out for me :)

I'm running Hardy LTS (fully uptodate, 32bit) and have sun-java6-plugin installed. (Actually re-installed it as per one of the prior replies).

I also executed the 'aternatives' line, but I'm not so sure I needed that?

I entered all those ls commands as per one of nanotubes reqs and here are the results:

```
yleeyas@katrina:~$ ls -al /usr/lib/mozilla/plugins
total 464
drwxr-xr-x 2 root root  4096 2010-02-16 09:12 .
drwxr-xr-x 4 root root  4096 2008-09-23 14:28 ..
lrwxrwxrwx 1 root root    37 2010-02-16 09:12 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
-rw-r--r-- 1 root root 81776 2008-05-27 11:25 gecko-mediaplayer-dvx.so
-rw-r--r-- 1 root root  1339 2008-05-27 11:25 gecko-mediaplayer-dvx.xpt
-rw-r--r-- 1 root root 81932 2008-05-27 11:25 gecko-mediaplayer-qt.so
-rw-r--r-- 1 root root  1339 2008-05-27 11:25 gecko-mediaplayer-qt.xpt
-rw-r--r-- 1 root root 81964 2008-05-27 11:25 gecko-mediaplayer-rm.so
-rw-r--r-- 1 root root  1339 2008-05-27 11:25 gecko-mediaplayer-rm.xpt
-rw-r--r-- 1 root root 82792 2008-05-27 11:25 gecko-mediaplayer.so
-rw-r--r-- 1 root root 82352 2008-05-27 11:25 gecko-mediaplayer-wmp.so
-rw-r--r-- 1 root root  1339 2008-05-27 11:25 gecko-mediaplayer-wmp.xpt
-rw-r--r-- 1 root root  1339 2008-05-27 11:25 gecko-mediaplayer.xpt
lrwxrwxrwx 1 root root    39 2008-10-13 09:48 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
yleeyas@katrina:~$ 
yleeyas@katrina:~$ ls -al /etc/alternatives/mozilla-javaplugin.so
lrwxrwxrwx 1 root root 64 2010-03-28 20:27 /etc/alternatives/mozilla-javaplugin.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
yleeyas@katrina:~$ 
yleeyas@katrina:~$ ls -al /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so
-rw-r--r-- 1 root root 72908 2009-10-11 04:43 /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so
yleeyas@katrina:~$ 
yleeyas@katrina:~$ java -version
java version "1.6.0_17"
Java(TM) SE Runtime Environment (build 1.6.0_17-b04)
Java HotSpot(TM) Client VM (build 14.3-b01, mixed mode, sharing)
yleeyas@katrina:~$ 
```

I'm gonna try and manually follow all the links around again, while waiting for your help.

TIA

Nevermind :oops:
I tried the other 'update-alternatives --config' command, and THAT fixed it. Sorry to bother you ... I'll go stand in the corner now

---

### Post by nomnex on 2010-06-24
FIY,

Installed today: ubuntuzilla FF3.6.4 recognized Java(TM) Plug-in 1.6.0_20 out of the box. Can we considere this thread as solved?

---

