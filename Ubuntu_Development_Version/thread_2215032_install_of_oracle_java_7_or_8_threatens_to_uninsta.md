---
title: "install of oracle java 7 or 8 threatens to uninstall apt?"
date: 2014-04-04
forum: Ubuntu Development Version
---

### Post by zeke2135 on 2014-04-04
As part of the latest updates this morning, open jdk7 was installed and oracle jdk7 was uninstalled by the system. Since I have jars that prefer oracle java (according to the developers), I uninstalled openjdk7 and attempted to reinstall oracle jdk7 from the webupd8team ppa (the package is oracle-jdk7-installer). However, apt was telling me that it and a bunch of other really essential components would be uninstalled. Obviously I can't install oracle java w/ these conditions. Has anyone encountered this issue?

---

### Post by QIII on 2014-04-04
Hello!

What version of Ubuntu are you using?  I get OpenJDK updates all the time, but Oracle Java 7 is never uninstalled.

Could you post the entire output from the terminal when you see this?  Please remember to use code tags, since that output may be rather long.

---

### Post by zika on 2014-04-04
You can keep these openjdk packages for peace sake and install Oracle Java manually, make it default and be happy... No new package will be in position to uunistall it and every package will be in position to use it.
An old post of mine [http://forum.ubuntu-rs.org/Thread-64-bit-java-flash-i-script-za-brisanje-prethodnih-install-acija-flash-a?pid=222001#pid222001](http://forum.ubuntu-rs.org/Thread-64-bit-java-flash-i-script-za-brisanje-prethodnih-install-acija-flash-a?pid=222001#pid222001) and I'm sure there is one mine similar to that here...

---

### Post by zeke2135 on 2014-04-04
@QIII, I am using the 14.04 development version. I'm not sure how to get what you are asking, as the update process is already completed. I simply did apt-get update; apt-get dist-upgrade and watched while oracle jdk7 was uninstalled and openjdk7 was installed (I did not have openjdk7 installed beforehand). There were no errors that I saw.

Now, if I try to install oracle 7 or 8 (whether openjdk7 is installed or not), I get an indication that the oracle-jdk7-installer is broken if I use synaptic. If I use apt-get install, I get the warning that like 20 packages, including apt, apturl, and many others, will be uninstalled. I can get the output of that command when I have a chance, but it seems basically "normal", just warning me emphatically that I shouldn't do what I've asked to do.

---

### Post by zika on 2014-04-04
Where comes this epidemic of dist-upgrades from...?
Apart from the fact that now even apt has Java as dependency?
Which I simply refuse to believe to put it mildly... ;)

---

### Post by cromat on 2014-04-04
I have the same issue using the webupd8team/java ppa, I'm just going to write my own script from now on...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gsfonts-x11 java-common
Suggested packages:
  default-jre equivs binfmt-support visualvm ttf-baekmuk ttf-unfonts
  ttf-unfonts-core ttf-kochi-gothic ttf-sazanami-gothic ttf-kochi-mincho
  ttf-sazanami-mincho ttf-arphic-uming
The following packages will be REMOVED:
  apt apturl nautilus-share python3-software-properties software-center
  software-properties-common software-properties-gtk ubuntu-desktop
  ubuntu-extras-keyring ubuntu-minimal unattended-upgrades
The following NEW packages will be installed:
  gsfonts-x11 java-common oracle-java8-installer
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt
0 upgraded, 3 newly installed, 11 to remove and 0 not upgraded.
Need to get 158 kB of archives.
After this operation, 7,481 kB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?]

---

### Post by macozz on 2014-04-04
I am having the same problem.
Yesterday I installed oracle-java-8 installer without any problem, but in the last upgrade few hours ago it was removed because incompatibilities and open-jdk installed.
The problems is that my internet banking require oracle java!t to do
What to do???

Thanks

---

### Post by zika on 2014-04-04
> **cromat said:**
> I have the same issue using the **webupd8team/java ppa**, I'm just going to write my own script from now on...Now we know where the trouble comes from... ;)
Simply DL Oracle Java tar, de-compress it, update alternatives and enjoy using Java... Do not rely on ppa's that would take Your system apart... And do not use dist-upgrade if You're not sure what is going to happen... Especially in U+1...

---

### Post by cromat on 2014-04-04
Here is the script for anyone who needs it, you will need to keep your jdk up to date however...the ppa was convient.

<code>
#!/bin/sh

tar -xvf jdk-8*
sudo mkdir /usr/lib/jvm
sudo mv ./jdk1.8* /usr/lib/jvm/jdk1.8.0
sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jdk1.8.0/bin/java" 1
sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/lib/jvm/jdk1.8.0/bin/javac" 1
sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/lib/jvm/jdk1.8.0/bin/javaws" 1
sudo chmod a+x /usr/bin/java
sudo chmod a+x /usr/bin/javac
sudo chmod a+x /usr/bin/javaws
</code>

---

### Post by zika on 2014-04-04
> **cromat said:**
> Here is the script for anyone who needs it, you will need to keep your jdk up to date however...the ppa was convient.

<code>
#!/bin/sh

tar -xvf jdk-8*
sudo mkdir /usr/lib/jvm
sudo mv ./jdk1.8* /usr/lib/jvm/jdk1.8.0
sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jdk1.8.0/bin/java" 1
sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/lib/jvm/jdk1.8.0/bin/javac" 1
sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/lib/jvm/jdk1.8.0/bin/javaws" 1
sudo chmod a+x /usr/bin/java
sudo chmod a+x /usr/bin/javac
sudo chmod a+x /usr/bin/javaws
</code>As I wrote in [http://ubuntuforums.org/showthread.php?t=2215032&p=12977078#post12977078](http://ubuntuforums.org/showthread.php?t=2215032&p=12977078#post12977078)...
There are caveats in the way You propose, and it is easier not to put it where You've proposed it to be put, especially if that is one user machine, but not a big deal... You've missed one major thing: java-plugin...
Take a peek at my post, mentioned in [http://ubuntuforums.org/showthread.php?t=2215032&p=12977078#post12977078](http://ubuntuforums.org/showthread.php?t=2215032&p=12977078#post12977078) to resolve that matter also...
Chmods are also superfluous I think...

---

### Post by zeke2135 on 2014-04-04
Manually installing oracle java seems like it's treating the symptom not the disease. I've used the webupd8 ppa for a while w/o problems. It's hard to believe that yesterday the installer worked fine, then upgrades happen, then the installer is saying it's incompatible with crucial parts of the whole system. I'm definitely no expert here, but it just seems more likely that something in the upgrades somehow flagged oracle java as being incompatible w/ those components (and maybe it is - I have no clue).

---

### Post by zika on 2014-04-04
> **zeke2135 said:**
> Manually installing oracle java seems like it's treating the symptom not the disease. I've used the webupd8 ppa for a while w/o problems. It's hard to believe that yesterday the installer worked fine, then upgrades happen, then the installer is saying it's incompatible with crucial parts of the whole system. I'm definitely no expert here, but it just seems more likely that something in the upgrades somehow flagged oracle java as being incompatible w/ those components (and maybe it is - I have no clue).Did You read my post: [http://ubuntuforums.org/showthread.php?t=2215032&p=12977166#post12977166](http://ubuntuforums.org/showthread.php?t=2215032&p=12977166#post12977166) ? If You do You will find my a(p)titude (pun intended) about that upgrade... ;) But PPA does not help much if it is not up-to-date enough to withstand changes and that is known to happen in U+1 often... Ergo, my conclusion about using PPAs in U+1 and especially dist-upgrade which is being lustrated to much times to easily... ;)

---

### Post by QIII on 2014-04-04
I suspect that this is simply a case of an anecdotal problem or there was an error in the webupd8 script which has been corrected now.  Remember that the webupd8 installer does nothing more, nor less, than some of the scripts offered.  webupd8.org maintains no binaries because Oracle no longer authorizes that.  The script downloads the binary for you, uninstalls your old version, reinstalls the current version and handles the browser plugin -- and does it automatically again when Oracle releases new versions.

My opinion is this:  the webupd8 route is simply the easiest method for installing Oracle Java and it has the added benefit of automatic updates when Oracle issues them.  There is no need to stay on top of Oracle's updates.  If you take a look at the Java link in my signature, you will see that I have put this method as the first suggestion under command line methods. 

With regard to PPAs, it is a good idea to avoid them.  However, webupd8.org has an excellent reputation and is one of the organizations one may trust.  They make mistakes as all humans do.  So do those at Canonical who maintain packages.  So do those who offer scripts to do exactly what webupd8's installer does.

webupd8.org is one of the three organizations from whom I will use PPAs.

Best not to throw the baby out with the bath water here.

---

### Post by zika on 2014-04-04
If You caught even a glimpse of my even a slightest condemnation of WebUPD8 either You're wrongly interpreting me or I might made some typing error... ;)
Simply put, I do not recommend using scripts especially in U+1 for reasons of having real control of happenings... Not for inexperienced users especially...
That is not a mantra, life is much better proof of my stand... ;)
Java 9 (Oracle) Ante Portas... ;)

---

### Post by QIII on 2014-04-04
I hope I have not come across as argumentative.

There is wisdom in what you say.  I don't think that I was arguing with you about this, rather making sure the OP was not dissuaded from using a resource if they can.
 
I don't think the inexperienced should be fiddling with a development version anyway, so I hope that these sorts of things are not anything they would encounter.

With regard to using a PPA or a script in a development version, I consider that part of testing.  I want to see that the things that I would normally do work correctly.  If they don't, I can go back and see why.  So I test the drivers and apps I would normally use, the PPAs, the scripts, conky, etc.

If I'm running the dev version on a non-production machine and I break it utterly beyond repair -- meh.  Gives me a chance to dig a bit and learn something.  With my level of experience that's not a problem.  Besides, I can fix things in most cases without nuking and reinstalling.

With regard to Oracle Java 7 installed this way, this is the first time I have encountered anyone having trouble -- especially something odd like this, and I refer often to the Java wiki in my sig.  (By the way, I know that Eugene San's PPA is a wreck and I have included instructions for cleaning up if someone tries to use it.)  I'm an early adopter and have been using Kubuntu Trusty as my daily driver and Ubuntu Trusty on the side to play with.  I haven't had any problem with updating Java just as I normally would, so this question is intriguing.

I guess I am just agreeing with the user who suggested that said that this seemed like treating the symptom.  It would be nice to know why webupd8's installer didn't work so we can discuss it with webupd8.org or find out if it is something indicative of an introduced oddity in Ubuntu.

Cheers -- and no argument. Unfortunately, tone of voice does not translate well to written communication on a forum.   Just a discussion.

---

### Post by gifford on 2014-04-04
Having the problem here...running update manager it says partial update.
The issue is apt...will not install without removing oracle java 8.
Will wait to see if this gets fixed before doing anything.

---

### Post by zeke2135 on 2014-04-04
> **QIII said:**
> I suspect that this is simply a case of an anecdotal problem...

I would be willing to think that there was something highly unusual about my system, or about what I did, but @cromat in post#6 and @macozz in post #7 described exactly what happened in my case. And @macozz mentioned that he used the oracle installer successfully just before the recent upgrades that uninstalled oracle java. I'm pretty curious about how this might happen. I have very little understanding about how package management is actually done, and how conflicts are flagged, but it just seems like the upgrade process must have flagged oracle java as incompatible and not the other way around. In other words it seems like the upgrade process was flawed somehow and not the webupd8 script (I don't have access to the machine where this issue occurred, but is the script cached somewhere?). Does it seem like a stretch that a change to a popular script to download some files and install them could suddenly introduce a flaw that accidentally marks some crucial system components as incompatible and removable??

---

### Post by zika on 2014-04-04
> **zeke2135 said:**
> I would be willing to think that there was something highly unusual about my system, or about what I did, but @cromat in post#6 and @macozz in post #7 described exactly what happened in my case. And @macozz mentioned that he used the oracle installer successfully just before the recent upgrades that uninstalled oracle java. I'm pretty curious about how this might happen. I have very little understanding about how package management is actually done, and how conflicts are flagged, but it just seems like the upgrade process must have flagged oracle java as incompatible and not the other way around. In other words it seems like the upgrade process was flawed somehow and not the webupd8 script (I don't have access to the machine where this issue occurred, but is the script cached somewhere?). Does it seem like a stretch that a change to a popular script to download some files and install them could suddenly introduce a flaw that accidentally marks some crucial system components as incompatible and removable??You're missing the point that You're testing pre-production version of SW. I've made the same mistake quite a few times and recognized my mistake each and every time... New apt is in store and while bringing great imporvement and primising even lot more in 1.0, it brings also troubles... ;)
As i said, a bit different approach in applying Java tar could save all from such inconveniences... Read^...

---

### Post by zeke2135 on 2014-04-04
> **zika said:**
> You're missing the point that You're testing pre-production version of SW. 
Why exactly do you conclude that I'm missing this point? As far as I can see, the point of testing pre-production software is to find out what doesn't work and figure out why, if you're capable, or report your experiences to others who might be, so it can be fixed. I'm pretty sure a lot of users install oracle java from the webupd8 ppa, and I can see that others are already also reporting a similar issue, so it would seem to be a good idea to solve the problem, not work around it by manually installing.

---

### Post by orj-gmail on 2014-04-04
> **gifford said:**
> Having the problem here...running update manager it says partial update.
The issue is apt...will not install without removing oracle java 8.
Will wait to see if this gets fixed before doing anything.

same here.

---

### Post by QIII on 2014-04-04
I have reported this as a bug, as I encountered it when I got home tonight.  Please add yourself to the "Affects me" list, but don't add simple comments such as "This affects me too!" as that gets in the way of making sense of the bug report.  

[URL="https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1302923"]https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1302923

[/URL]

---

### Post by mc4man on 2014-04-04
The ppa owner probably needs to adjust the control file, maybe related to Provides: .... default-jre, ( maybe also  - default-jre-headless,
I made a couple of small changes to control (removed above, added java-common ) & the ppa packages installed/ran fine (one is transitional, not really needed.
So it probably will be squared away shortly.

Ex. new 14.04 install - 
> ........
The following NEW packages will be installed:
  java-common
0 upgraded, 1 newly installed, 0 to remove and 14 not upgraded.
Need to get 130 kB of archives.
After this operation, 299 kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main java-common all 0.51 [130 kB]
Fetched 130 kB in 0s (279 kB/s)     
Selecting previously unselected package java-common.
(Reading database ... 361742 files and directories currently installed.)
Preparing to unpack .../java-common_0.51_all.deb ...
Unpacking java-common (0.51) ...
Processing triggers for man-db (2.6.6-1) ...
Processing triggers for doc-base (0.10.5) ...
Processing 2 added doc-base files...
Registering documents with scrollkeeper...
Setting up java-common (0.51) ...
Setting up oracle-java7-installer (7u51-0~webupd8~4) ...
Downloading Oracle Java 7...
--2014-04-04 23:46:14--  [http://download.oracle.com/otn-pub/java/jdk/7u51-b13/jdk-7u51-linux-x64.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u51-b13/jdk-7u51-linux-x64.tar.gz)
Resolving download.oracle.com (download.oracle.com)... 23.0.160.198, 23.0.160.200
Connecting to download.oracle.com (download.oracle.com)|23.0.160.198|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://edelivery.oracle.com/otn-pub/java/jdk/7u51-b13/jdk-7u51-linux-x64.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u51-b13/jdk-7u51-linux-x64.tar.gz) [following]
--2014-04-04 23:46:14--  [https://edelivery.oracle.com/otn-pub/java/jdk/7u51-b13/jdk-7u51-linux-x64.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u51-b13/jdk-7u51-linux-x64.tar.gz)
Resolving edelivery.oracle.com (edelivery.oracle.com)... 23.193.198.140
Connecting to edelivery.oracle.com (edelivery.oracle.com)|23.193.198.140|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://download.oracle.com/otn-pub/java/jdk/7u51-b13/jdk-7u51-linux-x64.tar.gz?AuthParam=1396669693_010d9a556161c4a132e6030fb635ad63](http://download.oracle.com/otn-pub/java/jdk/7u51-b13/jdk-7u51-linux-x64.tar.gz?AuthParam=1396669693_010d9a556161c4a132e6030fb635ad63) [following]
--2014-04-04 23:46:14--  [http://download.oracle.com/otn-pub/java/jdk/7u51-b13/jdk-7u51-linux-x64.tar.gz?AuthParam=1396669693_010d9a556161c4a132e6030fb635ad63](http://download.oracle.com/otn-pub/java/jdk/7u51-b13/jdk-7u51-linux-x64.tar.gz?AuthParam=1396669693_010d9a556161c4a132e6030fb635ad63)
Connecting to download.oracle.com (download.oracle.com)|23.0.160.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 138199690 (132M) [application/x-gzip]
Saving to: &#8216;jdk-7u51-linux-x64.tar.gz&#8217;

     0K ........ ........ ........ ........ ........ ........  2% 6.49M 20s
  3072K ........ ........ ........ ........ ........ ........  4% 6.91M 19s
  6144K ........ ........ ........ ........ ........ ........  6% 6.90M 18s
  9216K ........ ........ ........ ........ ........ ........  9% 6.90M 18s
 12288K ........ ........ ........ ........ ........ ........ 11% 6.90M 17s
 15360K ........ ........ ........ ........ ........ ........ 13% 6.90M 17s
 18432K ........ ........ ........ ........ ........ ........ 15% 6.90M 16s
 21504K ........ ........ ........ ........ ........ ........ 18% 6.90M 16s
 24576K ........ ........ ........ ........ ........ ........ 20% 6.91M 15s
 27648K ........ ........ ........ ........ ........ ........ 22% 6.90M 15s
 30720K ........ ........ ........ ........ ........ ........ 25% 6.90M 14s
 33792K ........ ........ ........ ........ ........ ........ 27% 6.90M 14s
 36864K ........ ........ ........ ........ ........ ........ 29% 6.91M 14s
 39936K ........ ........ ........ ........ ........ ........ 31% 6.90M 13s
 43008K ........ ........ ........ ........ ........ ........ 34% 6.91M 13s
 46080K ........ ........ ........ ........ ........ ........ 36% 6.90M 12s
 49152K ........ ........ ........ ........ ........ ........ 38% 6.91M 12s
 52224K ........ ........ ........ ........ ........ ........ 40% 6.89M 11s
 55296K ........ ........ ........ ........ ........ ........ 43% 6.91M 11s
 58368K ........ ........ ........ ........ ........ ........ 45% 6.89M 10s
 61440K ........ ........ ........ ........ ........ ........ 47% 6.91M 10s
 64512K ........ ........ ........ ........ ........ ........ 50% 6.89M 10s
 67584K ........ ........ ........ ........ ........ ........ 52% 6.92M 9s
 70656K ........ ........ ........ ........ ........ ........ 54% 6.89M 9s
 73728K ........ ........ ........ ........ ........ ........ 56% 6.91M 8s
 76800K ........ ........ ........ ........ ........ ........ 59% 6.89M 8s
 79872K ........ ........ ........ ........ ........ ........ 61% 6.91M 7s
 82944K ........ ........ ........ ........ ........ ........ 63% 6.89M 7s
 86016K ........ ........ ........ ........ ........ ........ 66% 6.91M 7s
 89088K ........ ........ ........ ........ ........ ........ 68% 6.90M 6s
 92160K ........ ........ ........ ........ ........ ........ 70% 6.91M 6s
 95232K ........ ........ ........ ........ ........ ........ 72% 6.89M 5s
 98304K ........ ........ ........ ........ ........ ........ 75% 6.91M 5s
101376K ........ ........ ........ ........ ........ ........ 77% 6.89M 4s
104448K ........ ........ ........ ........ ........ ........ 79% 6.91M 4s
107520K ........ ........ ........ ........ ........ ........ 81% 6.90M 3s
110592K ........ ........ ........ ........ ........ ........ 84% 6.90M 3s
113664K ........ ........ ........ ........ ........ ........ 86% 6.90M 3s
116736K ........ ........ ........ ........ ........ ........ 88% 6.91M 2s
119808K ........ ........ ........ ........ ........ ........ 91% 6.90M 2s
122880K ........ ........ ........ ........ ........ ........ 93% 6.90M 1s
125952K ........ ........ ........ ........ ........ ........ 95% 6.90M 1s
129024K ........ ........ ........ ........ ........ ........ 97% 6.90M 0s
132096K ........ ........ ........ ........ ........ ....    100% 6.91M=19s

2014-04-04 23:46:33 (6.89 MB/s) - &#8216;jdk-7u51-linux-x64.tar.gz&#8217; saved [138199690/138199690]

Download done.
Removing outdated cached downloads...
update-alternatives: error: no alternatives for java
update-alternatives: using /usr/lib/jvm/java-7-oracle/jre/bin/ControlPanel to provide /usr/bin/ControlPanel (ControlPanel) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/jre/bin/java to provide /usr/bin/java (java) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/jre/bin/java_vm to provide /usr/bin/java_vm (java_vm) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/jre/bin/javaws to provide /usr/bin/javaws (javaws) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/jre/bin/jcontrol to provide /usr/bin/jcontrol (jcontrol) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/jre/bin/keytool to provide /usr/bin/keytool (keytool) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/jre/bin/orbd to provide /usr/bin/orbd (orbd) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/jre/bin/pack200 to provide /usr/bin/pack200 (pack200) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/jre/bin/policytool to provide /usr/bin/policytool (policytool) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/jre/bin/rmid to provide /usr/bin/rmid (rmid) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/jre/bin/rmiregistry to provide /usr/bin/rmiregistry (rmiregistry) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/jre/bin/servertool to provide /usr/bin/servertool (servertool) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/jre/bin/tnameserv to provide /usr/bin/tnameserv (tnameserv) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/jre/bin/unpack200 to provide /usr/bin/unpack200 (unpack200) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/jre/lib/jexec to provide /usr/bin/jexec (jexec) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/appletviewer to provide /usr/bin/appletviewer (appletviewer) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/extcheck to provide /usr/bin/extcheck (extcheck) in auto mode
update-alternatives: warning: not replacing /usr/share/man/man1/extcheck.1.gz with a link
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/idlj to provide /usr/bin/idlj (idlj) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/jar to provide /usr/bin/jar (jar) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/jarsigner to provide /usr/bin/jarsigner (jarsigner) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/javac to provide /usr/bin/javac (javac) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/javadoc to provide /usr/bin/javadoc (javadoc) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/javafxpackager to provide /usr/bin/javafxpackager (javafxpackager) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/javah to provide /usr/bin/javah (javah) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/javap to provide /usr/bin/javap (javap) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/jcmd to provide /usr/bin/jcmd (jcmd) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/jconsole to provide /usr/bin/jconsole (jconsole) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/jdb to provide /usr/bin/jdb (jdb) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/jhat to provide /usr/bin/jhat (jhat) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/jinfo to provide /usr/bin/jinfo (jinfo) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/jmap to provide /usr/bin/jmap (jmap) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/jmc to provide /usr/bin/jmc (jmc) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/jps to provide /usr/bin/jps (jps) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/jrunscript to provide /usr/bin/jrunscript (jrunscript) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/jsadebugd to provide /usr/bin/jsadebugd (jsadebugd) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/jstack to provide /usr/bin/jstack (jstack) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/jstat to provide /usr/bin/jstat (jstat) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/jstatd to provide /usr/bin/jstatd (jstatd) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/jvisualvm to provide /usr/bin/jvisualvm (jvisualvm) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/native2ascii to provide /usr/bin/native2ascii (native2ascii) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/rmic to provide /usr/bin/rmic (rmic) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/schemagen to provide /usr/bin/schemagen (schemagen) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/serialver to provide /usr/bin/serialver (serialver) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/wsgen to provide /usr/bin/wsgen (wsgen) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/wsimport to provide /usr/bin/wsimport (wsimport) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-oracle/bin/xjc to provide /usr/bin/xjc (xjc) in auto mode
Oracle JDK 7 installed
update-alternatives: using /usr/lib/jvm/java-7-oracle/jre/lib/amd64/libnpjp2.so to provide /usr/lib/mozilla/plugins/libjavaplugin.so (mozilla-javaplugin.so) in auto mode
Oracle JRE 7 browser plugin installed
Setting up oracle-java7-set-default (7u51-0~webupd8~4) ...
Setting up oracle-jdk7-installer (7u51-0~webupd8~4) ...


Though it's quite simple to manually install  as in links..

---

### Post by zika on 2014-04-05
> **zeke2135 said:**
> Why exactly do you conclude that I'm missing this point? As far as I can see, the point of testing pre-production software is to find out what doesn't work and figure out why, if you're capable, or report your experiences to others who might be, so it can be fixed. I'm pretty sure a lot of users install oracle java from the webupd8 ppa, and I can see that others are already also reporting a similar issue, so it would seem to be a good idea to solve the problem, not work around it by manually installing.In my book using PPA is workaround and manual install is direct approach. That difference is answer to Your first question pointed to me, I presume.
Not to forget tomention crucial thing here: Ubuntu (read Canonical) made a decision of what Java to embrace and all this is a kind of workaround... ;)

---

### Post by gifford on 2014-04-07
Web UPD8 has posted they now have a work around installation: [http://www.webupd8.org/2014/04/oracle-java-installer-conflicting-with.html](http://www.webupd8.org/2014/04/oracle-java-installer-conflicting-with.html)
I will give it a try.

---

### Post by orj-gmail on 2014-04-07
> **gifford said:**
> Web UPD8 has posted they now have a work around installation: [http://www.webupd8.org/2014/04/oracle-java-installer-conflicting-with.html](http://www.webupd8.org/2014/04/oracle-java-installer-conflicting-with.html)
I will give it a try.

tried it and worked.

---

### Post by gifford on 2014-04-07
Also worked for me.

---

