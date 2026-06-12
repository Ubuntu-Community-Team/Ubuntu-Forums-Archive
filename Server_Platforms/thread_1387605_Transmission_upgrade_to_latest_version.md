---
title: "Transmission upgrade to latest version"
date: 2010-01-22
forum: Server Platforms
---

### Post by smeerbartje on 2010-01-22
Now that there is a new version of [Transmission]("http://www.transmissionbt.com/index.php") available, I was wondering if it is possible to install the latest version on my server, running 9.04 (Jaunty). According to [this page]("http://packages.ubuntu.com/search?keywords=transmission&searchon=names&suite=all&section=all") the latest Transmission is not available for Jaunty, right? So that's it? Not possible to use latest version?

---

### Post by yogesh.girikumar on 2010-01-22
Hi,

> **smeerbartje said:**
> Now that there is a new version of [Transmission]("http://www.transmissionbt.com/index.php") available, I was wondering if it is possible to install the latest version on my server, running 9.04 (Jaunty). 

Yes, the latest version of transmission is indeed available for Jaunty. You'll have to do an update of the package list and then do an fresh install. 

```
$ sudo apt-get update && apt-get install transmission
```This command will do a fresh installation. If you already have an older version of transmission installed, it will do an upgrade.

> **smeerbartje said:**
> According to [this page]("http://packages.ubuntu.com/search?keywords=transmission&searchon=names&suite=all&section=all") the latest Transmission is not available for Jaunty, right? So that's it? Not possible to use latest version?

Applications are updated/upgraded frequently and these upgrades are available for download most of the time. All you might have to do is to just update your repository database which holds information about packages and keeps track of their versions as updates are released. Then you simply do an upgrade in your system.
 HTH

---

### Post by duncan503 on 2010-01-23
Hello Ubuntu did upgrade then my Transmission upgraded too I restarted the pc and transmission doesn't do is job, just froze, now what?

---

### Post by smeerbartje on 2010-01-24
> **yogesh.girikumar said:**
> Hi,



Yes, the latest version of transmission is indeed available for Jaunty. You'll have to do an update of the package list and then do an fresh install. 

```
$ sudo apt-get update && apt-get install transmission
```This command will do a fresh installation. If you already have an older version of transmission installed, it will do an upgrade.



Applications are updated/upgraded frequently and these upgrades are available for download most of the time. All you might have to do is to just update your repository database which holds information about packages and keeps track of their versions as updates are released. Then you simply do an upgrade in your system.
 HTH

Sorry to bother you, but I did a fresh installation like you mentioned above, but APT did not install the latest version. Should I change something in the sources file?

---

### Post by ICEB3AR on 2010-01-24
What about the source-code:

./configure 
make
make install 
?

---

### Post by yogesh.girikumar on 2010-01-25
Hi,


       Transmission is present in the universe repository. You may have to enable the universe repository by editing the "/etc/apt/sources.list" file.


       Before doing anything, it's a good idea to backup the sources.list file just to be safe.
   ```
$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```      Then edit the original /etc/apt/sources.list file.
   ```
$ sudo vim /etc/apt/sources.list
```      or
   ```
$ sudo nano /etc/apt/sources.list
``` Then make sure the following lines are present in the file. If they are commented out, please remove the # symbol from the start of each line. 
```
deb http://in.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://in.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://in.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://in.archive.ubuntu.com/ubuntu/ jaunty-updates universe
```After this, save and close the file, and try updating and upgrading once again.  ```
$ sudo apt-get update && apt-get install transmission
```      P.S. If you would like to know how to manipulate repositories from the command line, please refer this link: [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

To add to this,


       When you update the packages in your system, Ubuntu's update release policy makes sure that you have the most stable version of every application installed in your system. That is, you get to have all the security and bug fixes applied as and when they are released. But this does not mean you have the most current/recent version of your app. This is because any non critical updates or bug fixes are usually included **only** in the next release of Ubuntu OS itself. These releases are termed as **Stable Release Updates** (SRU). This is done to keep the OS as stable as possible.
       Read more about it here: [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)
[URL="https://wiki.ubuntu.com/StableReleaseUpdates"]
[/URL]
       So when you need to install the bleeding edge version of your favorite applications, you might have to enable **"Ubuntu Backports"**. Enabling backport repositories enable you to download the latest version of applications as they are released. But installing them is usually done for testing purposes. They "may be" more prone to application crashes as they are not fully tested. Most of the time, the stable releases should be enough to do what we want them to do.


       Here is a very useful and informative link that you might find interesting: [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)
[URL="https://help.ubuntu.com/community/UbuntuBackports"]
[/URL]
       If you still want to enable backports, follow the procedures below. You've been warned ;-)
       Backup /etc/apt/sources.list file


```
$ sudo cp /etc/apt/sources.list /etc/apt/sources_original.list
     
```edit the original sources.list file. Open it with vim or nano   ```
$ sudo vim /etc/apt/sources.list
```      or
   ```
$ sudo nano /etc/apt/sources.list
```  Find the lines that say something like below.
```
# Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
```      Uncomment the last two lines, i.e., remove the # from the start of the lines.
    ```
deb http://in.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
 deb-src http://in.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
```      Save and close the sources.list file. Then
   ```
$ sudo apt-get update && apt-get install transmission
```Alternatively, You can also add the following lines to the sources.list repository and try which gave me Version 1.76. Earlier, it was version 1.75. Which could mean that the latest version of Transmission shipped by Ubuntu is 1.76.
   ```
deb http://ppa.launchpad.net/transmissionbt/ubuntu jaunty main
deb-src http://ppa.launchpad.net/transmissionbt/ubuntu jaunty main
deb http://ppa.launchpad.net/transmissionbt-nightly/ubuntu jaunty main
deb-src http://ppa.launchpad.net/transmissionbt-nightly/ubuntu jaunty main
deb http://ppa.launchpad.net/transmissionbt-beta/ubuntu jaunty main
deb-src http://ppa.launchpad.net/transmissionbt-beta/ubuntu jaunty main
```For some reason if you still need the bleeding edge version, which is 1.82, you may have to download the source code and compile it  and build the application.

HTH

---

### Post by Charles Kerr on 2010-01-25
I'm one of the Transmission developers and want to request that if you want to upgrade to 1.8 right now, if you encounter any problems please give helpful feedback in #transmission on freenode, or in transmissionbt.com's forums or bug tracker.

The diffs from the 1.7x and 1.8x branches are probably the largest we've ever had,  closing about 140 tickets (feature requests, speed improvements, bug reports, etc).  Even though we had five betas, there's now a new wave of bug reports because the official release increases the number of testers by several orders of magnitude...  there are known bugs in 1.81 and 1.82 that are already fixed in the nightly tarballs @ [http://build.transmissionbt.com/job/trunk-linux/](http://build.transmissionbt.com/job/trunk-linux/) .

Things will calm down soon, but for the time being, if you want to use 1.8 *please* give useful feedback if you encounter problems.  Thanks!

(Hint: saying "hurr durr, didn't work, switched to $other_bittorrent_client" is not useful feedback. ;)

---

### Post by andrew.46 on 2010-01-27
Hi,

I have written a guide to building the latest Transmission under Karmic and posted in 'Tutorials and Tips'. It should appear in a day or so (after moderation) and should prove useful to those who would like to try out the latest version. I look forward to some feedback from this small guide, especially as a Transmission developer is here :).

Andrew

---

### Post by grimeywelsh on 2010-01-27
Hey, can you pm me that guide?  I am building a vm torrent server for a friend and would like to try out the new version.  I need to get it to him tomorrow though:)

---

### Post by andrew.46 on 2010-01-28
Hi grimeywelsh,

> **grimeywelsh said:**
> Hey, can you pm me that guide?  I am building a vm torrent server for a friend and would like to try out the new version.  I need to get it to him tomorrow though:)

Should be released very shortly, sometimes moderation takes a little while as the Forum staff have life in the real world :).

Andrew

---

### Post by bartlomiejp on 2010-01-28
yogesh.girikumar, I do not think Transmission is present in Universe repo,
it did not work for me, but make install worked, build it from sources,
like I did and you will have it. Takes 5 minutes!!!

---

### Post by andrew.46 on 2010-01-29
Hi,

So for those who are interested:

Howto: Build the BitTorrent client Transmission under Karmic Koala
[http://ubuntuforums.org/showthread.php?t=1391718](http://ubuntuforums.org/showthread.php?t=1391718)

Love some feedback, criticisms, advice etc...

Andrew

---

### Post by andrew.46 on 2010-01-29
Hi Charles,

> **Charles Kerr said:**
> Things will calm down soon, but for the time being, if you want to use 1.8 *please* give useful feedback if you encounter problems.

I have corrected the smallest of bugs with this patch:

[http://trac.transmissionbt.com/attachment/ticket/2836/cli.diff](http://trac.transmissionbt.com/attachment/ticket/2836/cli.diff)

where the command:

```
transmissioncli --help
```

gives incorrect syntax for usage. It would be nice if my very small change was incorporated :).

Andrew

---

