---
title: "Failed downloads in upgrade from 8.10"
date: 2011-06-03
forum: Server Platforms
---

### Post by sipickles on 2011-06-03
Hi,

I have a fileserver happily chugging away on 8.10, but I notice this version is no longer supported. 

I want to upgrade (no, please don't suggest a clean install) to the latest, understanding it has to be done version by version.

Here's the problem:
```
simon@sciproj-server:~$ sudo do-release-upgrade
Checking for a new ubuntu release
Failed Upgrade tool signature
Failed Upgrade tool
Done downloading
extracting 'jaunty.tar.gz'
Failed to extract
Extracting the upgrade failed. There may be a problem with the network or with the server.
```

I have checked /var/lib/update-manager/meta-release and have this entry for Jaunty 9.04:
```
Dist: jaunty
Name: Jaunty Jackalope
Version: 9.04
Date: Thu, 23 Apr 2009 12:00:00 UTC
Supported: 0
Description: This is the 9.04 release
Release-File: http://archive.ubuntu.com/ubuntu/dists/jaunty/Release
ReleaseNotes: http://changelogs.ubuntu.com/EOLReleaseAnnouncement
UpgradeTool: http://archive.ubuntu.com/ubuntu/dists/jaunty-proposed/main/dist-upgrader-all/0.111.8/jaunty.tar.gz
UpgradeToolSignature: http://archive.ubuntu.com/ubuntu/dists/jaunty-proposed/main/dist-upgrader-all/0.111.8/jaunty.tar.gz.gpg

```

I think the problem is caused by the Upgrade tool and UpgradeToolSignature no longer residing at archive.ubuntu.com. Instead they are at old-releases.ubuntu.com. I have checked this location and I can download them manually using wget.

I tried editing /var/lib/update-manager/meta-release by hand but it seems to be overwritten back the the old values of archive.ubuntu.com.

Can anyone suggest how I point the upgrade at the right URL?

Thanks

Simon

---

### Post by jaywhoopee on 2011-06-04
> **sipickles said:**
>  I tried editing /var/lib/update-manager/meta-release by hand but it seems to be overwritten back the the old values of archive.ubuntu.com. 
 I've been following the guide at [http://help.ubuntu.com/community/EOLUpgrades/Intrepid](http://help.ubuntu.com/community/EOLUpgrades/Intrepid) and got stuck at this stage too. 

 Having found your post I edited the /var/lib/update-manager/meta-release file and replaced all 40 or so occurrences of "archive" with "old-releases" which has worked for me. 

  Thanks for your help and sorry if this doesn't help you :)

---

### Post by sipickles on 2011-06-06
I tried your approach and changed ALL occurances of 'archive. with 'old-releases'. No better.

I find linux very odd at times and this problem is no different. It is entirely irrational to render old versions un-upgradable by 'turning off' their ability to find the necessary upgrade files!

I mean, even M$ aren't that lame.

Please, do correct me if I am wrong and help me stop drifting away from Linux...

---

### Post by Bucky Ball on 2011-06-06
Servers should be running on an LTS release, currently 10.04 LTS. I would try heading there, personally. Not sure if you can get from where you are to there easily without a clean install but I know you can get from one LTS to the next in a couple of clicks (12.04 LTS should be the next one but the current server version of 10.04 is supported until 2015 by which time you'll be ready for 14.04 LTS). ;)

---

### Post by sipickles on 2011-06-06
I am trying to perform the upgrade to the latest LTS...


Reluctant to do a full clean install (yet)

---

### Post by Bucky Ball on 2011-06-06
Got ya. Disregard my last post then! ;)

---

### Post by sipickles on 2011-06-06
All I need to do (I think) is point the sudo do-release-upgrade to the correct URI: 

```
old-releases.ubuntu.com
```

not

```
archive.ubuntu.com
```

I think the URI info is being loaded from [http://changelogs.ubuntu.com/meta-release](http://changelogs.ubuntu.com/meta-release) (as specified in /etc/update-manager/meta-release) each time I run do-release-upgrade, which prevents me modifying /var/lib/update-manager/meta-release by hand.

Just need a workaround for this!

---

### Post by sipickles on 2011-06-06
Holy cow!

I think I may have solved a problem on my own ;)

Here's what I did.

Replace archive with old-releases while copying file:

```
sed -i ‘s/archive/old-releases/g’ /var/lib/update-manager/meta-release > /home/simon/meta-release
```

Point upgrade manager to the modified file:

```
sudo nano /etc/update-manager/meta-release
# Comment out URI line and add new:
URI = file:/home/simon/meta-release
```

Re-run update-manager

```
sudo do-release-upgrade
```

Hey presto, its downloading Jaunty! I'll report back if it is all successful.

I guess I'll need to restore the default meta-releases when I'm back into 'supported' territory.

Still think its totally :confused: (thats the polite way of putting it!)

---

### Post by JumpinJimminy on 2011-06-30
Thank you **sipickles**, gave you credit for referring me to this site. I have been on a long mission to get this from 8.10 to 10.04.2. 

Your command line to create and copy meta-release file did not work for me. I had to just create another at /home/HOMENAME/ called meta-release and copy and paste info from old to new. 

Then I had to swap "archives" for "old-releases". I made this easier by using ctrl+F to highlight all occurrences of "archive" up to and including 9.10. I was then able to run sudo do-release-upgrade and move up to 9.04. 

Once at 9.04 Update Manager showed 10.04 LTS (Lucid Linux) available. When I tried to upgrade I got the error "Can not upgrade.  An upgrade from 'jaunty' to 'lucid' is not supported with this tool"

To go from 9.04 to 9.10 you have to edit a line in the /home/HOMENAME/meta-release file from the 9.10 details. The line is:

Supported: 0

should be:

Supported: 1

After doing that Update Manager showed 9.10 instead of 10.04 LTS (Lucid Linux) and I got the failed to fetch error again:

Checking for a new ubuntu release
Failed Upgrade tool signature
Failed Upgrade tool
Done downloading            
Failed to fetch
Fetching the upgrade failed. There may be a network problem. 

I'll update when I find the answer to this one......

---

### Post by JumpinJimminy on 2011-06-30
Bingo! Leave the Release-File, ReleaseNotes, UpgradeTool and UpgradeToolSignature address in the meta-release file pointed to "archive" in 9.10. Do not switch to "old-releases" as needed in previous versions details prior to 9.10.

---

### Post by arrrghhh on 2011-06-30
> **sipickles said:**
> Still think its totally :confused: (thats the polite way of putting it!)

Yea, it is kinda dumb...

But honestly, who has a server on 8.10?  I'd say you're an extreme minority - and honestly Ubuntu provided plenty of opportunity to upgrade.

Ironically, if you were on the older version (8.04 LTS) you would've been able to go straight to 10.04 LTS.  I would recommend this in the future, on server platforms staying with LTS releases, unless you want to upgrade every 6 months - which it seems like you do not want considering you were still on 8.10 :p.

This is the "recommended" method.  Either stick to LTS and upgrade every 2 years, or if you want to stay on regular releases, make sure you upgrade every 6 months or so.  Otherwise, you'll fall behind and run into another issue like this.

Microsoft doesn't have to keep up repo's like Ubuntu does, and I understand why Ubuntu does it the way that they do - they can't possibly support all the newer versions, and all the older versions, there's just too many.  You just got caught out, like I said stick to LTS and make sure you upgrade before support has expired!

---

### Post by JumpinJimminy on 2011-06-30
After 9.10 was done installing I was able to upgrade to 10.04 LTS w/out issue. 

I apologise for not using correct forum etiquette, lingo, post formatting or any other such things. I am new to linux and new to this forum. With both, I will get better with familiarity. Thanks for being patient with a newbie.

---

### Post by arrrghhh on 2011-06-30
> **JumpinJimminy said:**
> After 9.10 was done installing I was able to upgrade to 10.04 LTS w/out issue. 

I apologise for not using correct forum etiquette, lingo, post formatting or any other such things. I am new to linux and new to this forum. With both, I will get better with familiarity. Thanks for being patient with a newbie.

Oh puh, you did just fine.  Don't feel like you did something wrong...

Glad you got it working.  Keep it on that LTS release, and then (before support expires!) get it on 12.04.  You can go from LTS to LTS without issue (in theory ;))

---

### Post by JumpinJimminy on 2011-06-30
I'll keep up on it from here for sure, this sucked! I decided to switch from M$ and had a disk that had 8.10 on it. Installed it on my desktop and have been going from there. Now I gotta figure out how to tweak it to the way I want it once 10.04 is done installing. That and whether it is better to stick with LTS's or newer releases.

---

### Post by arrrghhh on 2011-06-30
> **JumpinJimminy said:**
> I'll keep up on it from here for sure, this sucked! I decided to switch from M$ and had a disk that had 8.10 on it. Installed it on my desktop and have been going from there. Now I gotta figure out how to tweak it to the way I want it once 10.04 is done installing. That and whether it is better to stick with LTS's or newer releases.

Here's my rule of thumb - server platforms, LTS.  Desktops, newest release.

Unless there's something you absolutely need, LTS is usually fine for server.  I don't really like upgrading my server more than I have to, mainly because it "just works".  Hell, I know Linux servers that are just left and never really get updated.  Usually these are servers that are not connected to the internet tho ;).

That's just my .02.  There's no reason you can't upgrade a server to a non-LTS release obviously, it's just that those revisions are not supported with patches etc for as long as LTS releases.  With the added benefit of jumping directly between LTS releases, and they're *typically* more stable, I don't see any downside to sticking with LTS IMHO.

As always, do what works best for you ;).

---

### Post by Bucky Ball on 2011-06-30
10.04 LTS supported until late April 2013, after the next LTS release comes out in 2012, so you have plenty of time. You also have a year for 12.04 LTS to get stable before upgrading to that (which you will be able to do in a couple of clicks as LTS versions upgrade easily to the next LTS version).

As well advised already; stick with LTS releases for servers. They're made for that. ;)

---

### Post by hardkaare on 2011-09-01
I had the same problem going from 8.10 to a newer version.

I managed to do it by cheating do-release-upgrade with

vi /etc/lsb-release

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04

This is not a safe way, but it seem to work.

---

### Post by anotheranne on 2011-10-11
> **jaywhoopee said:**
> I've been following the guide at [http://help.ubuntu.com/community/EOLUpgrades/Intrepid](http://help.ubuntu.com/community/EOLUpgrades/Intrepid) and got stuck at this stage too. 

 Having found your post I edited the /var/lib/update-manager/meta-release file and replaced all 40 or so occurrences of "archive" with "old-releases" which has worked for me. 

  Thanks for your help and sorry if this doesn't help you :)

[FONT=Courier New]$ sudo do-release-upgrade
Checking for a new ubuntu release
Failed Upgrade tool signature
Failed Upgrade tool
Done downloading            
extracting 'jaunty.tar.gz'
Failed to extract
Extracting the upgrade failed. There may be a problem with the network or with the server.[/FONT]

I had same problem (Intrepid 8.10 server to Jaunty 9.04) and I found that this was the definitive solution for me. I can progress to the next upgrade just now :)

Anne

---

### Post by sferrell615 on 2013-04-15
i had the same problem and this worked for me too.  i thought that we only had to update sources.list... apparently meta-release is important too!  
thanks!!

---

### Post by overdrank on 2013-04-15
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

