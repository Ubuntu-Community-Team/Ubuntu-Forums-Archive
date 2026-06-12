---
title: "Sun JDK in Extras"
date: 2005-04-10
forum: Ubuntu Backports
---

### Post by jdong on 2005-04-10
Just would like to tell everyone that Sun's JDK (Java Development Kit) is available under Hoary Extras / Restricted [STAGING].

---

### Post by gbusse on 2005-04-11
Thank you!!!

---

### Post by alexp on 2005-04-12
jdong,

maybe it would be good to coordinate efforts with [email="cpinto@ubuntujava.yimports.com"]this guy (girl?)[/email], who provides Ubuntu java packages (JRE/SDK) for both 1.4 and 1.5 versions.

Regards,
Alexander

---

### Post by jdong on 2005-04-12
Umm, is there any decent reason why one'd like Java 1.4? I can arrange for that!

---

### Post by alexp on 2005-04-13
jdong,

yes -- for a) java [developers]("http://westcoast1.us.mirrors.ninjas.org/echo23/domopers_hi.mov") and b) users of commercial software. I need both SDKs, mostly for testing purposes and because the --target=1,4 switch doesn't produce 100% compatible code in all cases (especially when the users run it on non-standard JVMs). Furthermore I need both JREs: besides the aforementioned testing purposes, Poseidon for UML (and Together Designer and...) do not run on the 1.5 platform (heck, they even refuse to install). I think this applies to most commercial products -- and this almost certainly won't change in the near (6 months to 1 year) future.

However, the installation itself shouldn't pose much of a problem; the maintainer mentioned above installs them to /usr/lib/sun-j2{re|sdk}-<version> and creates symlinks to the newer one. This isn't a perfect solution (a debconf tool to switch between them would be nice), but it seems to work.

I'd be glad to help (especially with the debconf stuff), but I have no idea how it works. If one could point me to some docs, I'd have a look at it. But I don't think this dpkg-reconfigure switching of the active JVM is blocker; merely nice to have and with low priority.

Thanks in advance.

Regards,
Alexander

---

### Post by jdong on 2005-04-13
ok, I'll get them packaged :)

It's a trivial task.

---

### Post by asimon on 2005-04-13
Cool and thanks!

---

### Post by gbusse on 2005-04-13
John,

Thanks again for packaging up the Sun-JDK. I finally got around to testing it on a fresh install of Hoary and have noticed the following issues with some symbolic links created during the install:

/etc/alternatives/firefox-javaplugin.so
/etc/alternatives/mozilla-javaplugin.so

both point to:

/usr/lib/j2sdk1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so

and are broken as the file "libjavaplugin_oji.so" actually exists at:

/usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

also:

/etc/alternatives/netscape-javaplugin.so

points to:

/usr/lib/j2sdk1.5-sun/plugin/i386/ns4/libjavaplugin.so

as far as I can tell this file does not exist at all.

It is easy enough for me to fix the firefox-javaplugin.so symbolic link after the install, I just thought you would like to know.

Thanks again for all your work on the backports and extras.

Gord

---

### Post by jdong on 2005-04-14
Ok, that would be an upstream bug in the "java-package" program, which automatically created these Java package backports... Funny thing how my JRE works fine. Is it just the JDK that's affected?


BTW, Java 1.4 has been assigned this task: [https://sourceforge.net/pm/task.php?func=detailtask&project_task_id=114393&group_id=125877&group_project_id=42440](https://sourceforge.net/pm/task.php?func=detailtask&project_task_id=114393&group_id=125877&group_project_id=42440)

---

### Post by gbusse on 2005-04-15
John,

Not sure if only the JDK is affected or not as I have not tried the JRE. I will see if I can test out the JRE as soon as I find a free moment.

Gord

---

### Post by RastaMahata on 2005-04-20
thankyou thankyou thankyou thankyou thankyou thankyou.

---

### Post by mrbass on 2005-04-20
this isn't related to this guys ubuntu java is it? I'm guessing not.
[http://ubuntujava.yimports.com/](http://ubuntujava.yimports.com/)

---

### Post by jdong on 2005-04-20
No; we're not related :)

---

### Post by RastaMahata on 2005-04-20
does the sun-j2sdk package add plugins to firefox?

---

### Post by jdong on 2005-04-20
Well, uhh, it was meant to be that way.


However, apparently there's a bug (see a few posts above) with a bad symlink.


In short: install the JRE with the JDK.

---

### Post by RastaMahata on 2005-04-20
aight, Just finished installing jdk (I can compile again! goodby blackdown or whatever it was called)...

I'll install jre now. I'll report as soon as I can. ;)

Rasta out

---

### Post by Mlehliw on 2005-04-20
For some reason I can't find the sun jdk package. I've found the sun-j2re1.5 package just fine. I'm almost absolutely sure I have all the backports sections included in my sources file, so I don't think that's the problem (well everything except for bleeding that is). Is anyone else not finding this or am I missing something obvious?

---

### Post by RastaMahata on 2005-04-21
Well, they didnt add themselves automagically, so I just had to do these 2 steps:
```
cd /usr/lib/mozilla-firefox/plugins
sudo ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so
```That simple... 
I hope that you can do something about it, so users dont have to do this :P

Thanks!

---

### Post by Tomcat_ on 2005-04-21
Can anybody of you please help me with the installation of this? I don't really know what's wrong... I have

```
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted
```

in my sources.list (and apt-get update'd) but I can't seem to find the package. The only one concerning Java I see is sun-j2re1.5 which I already installed through the hoary after-install helper.

Where exactly is the JDK? Another repository?

Thanks in advance.

---

### Post by blyzzz on 2005-04-21
its in the staging-area i think

```
deb http://backports.ubuntuforums.org/backports/ hoary-extras-staging main restricted universe multiverse
```

---

### Post by thund3rman on 2005-04-21
When to the promotion from staging to stable backports?

Sorry for the anoyance, but I'm pretty thrilled with sun jdk being avalailable in a repository... ;)

And above all... Thanks for the good work! ;)

---

### Post by Tomcat_ on 2005-04-21
Thanks! Worked with hoary-extras-staging.

If you could also package the j2sdk 1.4 that would be amazing. I need it for a bigger uni assignment. But it's also low priority for you, I can also use the installer from Sun. :)

---

### Post by nanaban on 2005-04-26
[QUOTE=jdong]In short: install the JRE with the JDK.[/QUOTE]

What does that mean? I installed jre using ubuntu-geek's auto script for the noobs. What do I need to look out for when I install j2sdk? Should I uninstall the jre first?

---

### Post by RastaMahata on 2005-04-28
Hey, jdong, when will jsdk be out of the staging area? :S

[ joda]Confused I am[/joda]

---

### Post by cpinto on 2005-04-30
Hi,

I'm the maintainer of the UbuntuJava project and I was a little bit amazed when I found out that you guys are also providing the packages.

I remember a few months ago proposing these packages to be included in the Backports project and you dismissed the request stating that the licence strictly prohibited it.

If you're serious about distributing the JDK, etc. for the forseeable future, please bear in mind that in no way you will ever be able to distribute any competing product (gcj, kaffe and the GNU Classpath come into mind).

Anyway, if you're really interested I'd still like to propose a merge of these projects since I have a lot of stuff planned for it I just haven't found the free time necessary to go through all that stuff (for example, building complete packages for Eclipse, JBoss, a Java enabled version of OpenOffice.org 2.0, etc.) and it'd be really nice to have someone else to help/discuss these ideas.


Cheers,
Celso

PS: I'm a guy :P

---

### Post by jdong on 2005-05-01
I'm just distributing it for now, because after 4 or so reinstalls on my desktop, I'm ticked that I have to do so much MANUAL after-install configuration.


Whether Java on Backports is long-term, I'll have to think about it. Most likely, this'll be the case, and I'll make a "java" section to hold it :)

---

### Post by gbusse on 2005-05-01
[QUOTE=cpinto]
Anyway, if you're really interested I'd still like to propose a merge of these projects since I have a lot of stuff planned for it I just haven't found the free time necessary to go through all that stuff (for example, building complete packages for Eclipse, JBoss, a Java enabled version of OpenOffice.org 2.0, etc.) and it'd be really nice to have someone else to help/discuss these ideas.
[/QUOTE]

I, for one, would like to put my vote in for a merge. I think Celso has some great ideas and being able to install all of this Java stuff using an easy apt-get command would definitely make my life a lot easier.

Gord

---

### Post by gregorian21 on 2005-05-07
Hi Guys,
A n00b question for you.

I installed the JRE ( 1.5.0_01-b08 ) as described in the UbuntuGuide when I upgraded my system to Hoary. I am planning on installing the J2SDK from the backports reporsitory.


[list=1]
[*]Is it necessary that I 'uninstall ' my previously installed JRE before I install the J2SK (I'm assuming the J2SDK package includes a JRE). If so could someone point me to the procedure?
[*]If not, will there be any problems running two versions of the JRE on a single system.
[/list]Thanks

---

### Post by jdong on 2005-05-07
You don't need to reinstall -- the Guide's method is pretty solid, and won't conflict with UBP's JDK.

---

### Post by RastaMahata on 2005-05-07
[QUOTE=jdong]You don't need to reinstall -- the Guide's method is pretty solid, and won't conflict with UBP's JDK.[/QUOTE]
 Hey jdong, I still had to ```
sudo ln -sf /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /etc/alternatives/firefox-javaplugin.so
```To get the firefox plugin running :/

---

### Post by jdong on 2005-05-07
The UBP **JRE** automagically configures Firefox plugins. There was a bug in the Java packager that caused **JDK** to have an invalid plugin path, as described in this thread.

---

### Post by RastaMahata on 2005-05-07
im sorry to be such a PITA, but is this going to be fixed in the future? :(

---

### Post by jdong on 2005-05-07
Eventually I'll use an updated java packager to build Java packages, but currently there's simply no motivation / strong reason to do so :)

---

### Post by XDevHald on 2005-05-11
[QUOTE=jdong]Just would like to tell everyone that Sun's JDK (Java Development Kit) is available under Hoary Extras / Restricted [STAGING].[/QUOTE]

I'm not exactly sure why I'm not able to get the staging, but could you or someone post the deb for the sources list?

Thanks :)

**Edit$ ~** Ok, got it :)

---

### Post by mohaham on 2005-05-11
Thanks for the good work..

---

### Post by crazeinc on 2005-05-19
Hello, I added the staging area to my sources.list and did apt-get update, but I can't find the jdk in Synaptic. Is there something I've missed?

Thanks.

---

### Post by jdong on 2005-05-19
It's called **sun-j2sdk1.5**

Sorry about the weird naming scheme -- Debian chose it (?!?)

---

### Post by crazeinc on 2005-05-20
[QUOTE=jdong]It's called **sun-j2sdk1.5**

Sorry about the weird naming scheme -- Debian chose it (?!?)[/QUOTE]
 Thanks :)

---

### Post by wasabi on 2005-07-12
Can somebody explain to me how you can legally distribute this? Or are you distributing it against the terms of the license?

---

### Post by nestorgm on 2005-08-27
I think this is the right place to ask for help, Im confused. I'd like to install java sdk 5 on my ubuntu box. I found someting as java-packages, so i have /usr/share/java-package/sun-j2re1.5 path with install and remove scripts, beside some others. Further more I found your sun-j2sdk1.5 package and the installer jdk-1_5_0_04-linux-i586.bin from sun repository. 

What I dont know is if the package from sun does not work on ubuntu, if java-package  needs more work to install after apt-get, if sun-j2sdk1.5 needs something more after install ... 

Please enlight me about

Thanks in advance

---

### Post by jdong on 2005-08-27
[QUOTE=wasabi]Can somebody explain to me how you can legally distribute this? Or are you distributing it against the terms of the license?[/QUOTE]

It's permitted, as long as you don't distribute a competing Java implementation. And since Backports (which has GNU Java 4.0) and Extras are two separate projects, only sharing the same server and developers, it's fine.

---

### Post by incinerator on 2005-08-27
[https://wiki.ubuntu.com/JavaPackageBuildNewVersions](https://wiki.ubuntu.com/JavaPackageBuildNewVersions)

[QUOTE=nestorgm]I think this is the right place to ask for help, Im confused. I'd like to install java sdk 5 on my ubuntu box. I found someting as java-packages, so i have /usr/share/java-package/sun-j2re1.5 path with install and remove scripts, beside some others. Further more I found your sun-j2sdk1.5 package and the installer jdk-1_5_0_04-linux-i586.bin from sun repository. 

What I dont know is if the package from sun does not work on ubuntu, if java-package  needs more work to install after apt-get, if sun-j2sdk1.5 needs something more after install ... 

Please enlight me about

Thanks in advance[/QUOTE]

---

### Post by zacman on 2005-08-28
I installed with apt-get but i don't have the java command in my path... what should I do?

---

### Post by incinerator on 2005-08-28
That is very odd, as the java binaries are installed in /usr/bin/
A guess would be that you have installed sun-j2sdk but not sun-j2re.

---

### Post by zacman on 2005-08-28
I definitely have both packages installed.  I even have the firefox plugin working, but no java command.  Any ideas?

---

### Post by zacman on 2005-08-28
Never mind, got it working

Thanks

---

