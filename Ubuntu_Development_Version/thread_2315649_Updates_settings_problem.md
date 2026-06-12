---
title: "Updates settings problem"
date: 2016-03-01
forum: Ubuntu Development Version
---

### Post by aljosa2 on 2016-03-01
Hi all,
inside updates settings, options within "when there are security updates" are grayed out - see the attached image.
Any idea?

---

### Post by dino99 on 2016-03-01
purge then reinstall synaptic

---

### Post by v3.xx on 2016-03-01
Try doing a update and dist-upgrade in terminal, then go back and look at it.

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by aljosa2 on 2016-03-01
Thanks for advice,
I performed *'apt-get update', 'apt-get upgrade', 'apt-get dist-upgrade', 'apt-get check'* and *'apt-get -f install'* but problem is still here.

---

### Post by MikeMecanic on 2016-03-01
> **aljosa2 said:**
> Thanks for advice,
I performed *'apt-get update', 'apt-get upgrade', 'apt-get dist-upgrade', 'apt-get check'* and *'apt-get -f install'* but problem is still here.

Same here, plus removing Synaptic didn't help.  Isn't it always set that way?

---

### Post by aljosa2 on 2016-03-01
> **MikeMecanic said:**
> Isn't it always set that way?

No.

---

### Post by MikeMecanic on 2016-03-01
> **aljosa2 said:**
> No.

Never seen it enable in the Xenial cycle

---

### Post by v3.xx on 2016-03-01
Odd

[ATTACH=CONFIG]267593[/ATTACH]

---

### Post by deadflowr on 2016-03-01
Perhaps try reinstalling the package : software-properties-gtk, and/or the update-manager package.

---

### Post by Frogs Hair on 2016-03-01
Strange , mine is different than both images. Prereleased updates are displayed under the developer options.

---

### Post by MikeMecanic on 2016-03-01
> **deadflowr said:**
> Perhaps try reinstalling the package : software-properties-gtk, and/or the update-manager package.

It didn&#8217;t help for software-properties-gtk and was able to reinstall it.


I&#8217;m not able to re-install python 3.x module for update-manager. 


In Broken Dependencies and/or not install (residualconfig) I have this message:  **Fix broken packages first???**


Synaptic History:


[PHP]Commit Log for TueMar  1 22:33:06 2016

Completely removed the following packages:
python3-update-manager

Removed the following packages:
apturl-common
python3-distupgrade
ubuntu-release-upgrader-core
ubuntu-release-upgrader-gtk
update-manager
update-manager-core
update-notifier
[/PHP]

Fix broken dependencies first???

The update of Software updater didn't help also.

---

### Post by MikeMecanic on 2016-03-01
I forgot to close and re-open Synaptic to proceed.  Still have the same issue.  Thanks for help!
There must be something that I always do on post-installation that cause this then. Will try something else now...


[PHP]Commit Log for Tue Mar  1 23:18:20 2016


Installed the following packages:
python3-distupgrade(1:16.04.7)
python3-update-manager(1:15.10.3)


Commit Log for Tue Mar  1 23:19:17 2016


Installed the following packages:
apturl-common(0.5.2ubuntu11)


Commit Log for Tue Mar  1 23:19:54 2016


Installed the following packages:
ubuntu-release-upgrader-core(1:16.04.7)
ubuntu-release-upgrader-gtk(1:16.04.7)
update-manager(1:15.10.3)
update-manager-core(1:15.10.3)
update-notifier(3.166)
[/PHP]

---

### Post by MikeMecanic on 2016-03-02
I thought that Vino and/or Remmina (removing them) were responsible for the problem but this is not the case. To tell you the truth, I think the bug (it is not really one) is there as soon as I have completed the installation and before I do anything on post-installation.

P.S.:  Thanks for the update and 1000 thanks for taking good care of my machine since 17 weeks now.

---

### Post by aljosa2 on 2016-03-03
Maybe the problem lies here: *'System settings/software&updates'* and *'Gnome software center/software sources'* are currently one and the same thing.

---

### Post by MikeMecanic on 2016-03-03
This feature remains disable (gray) here after a fresh install of Ubuntu 20160303.  I said that I never seen it enable in the entire Xenial cycle, well let say in 2016.
  It is true for all flavors, except Studio and Mythe that I didn't try yet.  

Special thanks to  [COLOR=#000000][FONT=Ubuntubeta]aljosa2 [/FONT][/COLOR]for this observation.

---

### Post by aljosa2 on 2016-03-03
Hi MikeMecanic,
some 20-25 days ago I installed Xenial on 3 notebooks, just 2 or 3 days before 'Gnome software center' replaced 'Ubuntu software center'. Everything was ok with these settings.
In order to update BIOS in this notebook (Lenovo Y700-17ISK), few days ago I had to delete Xenial, install Windows 10 evaluation enterprise, then delete Windows 10 and install Xenial again.
Unfortunately I am circa 500-600 km far away from other 2 notebooks at the moment, so can't tell you what is the current situation.

---

### Post by MikeMecanic on 2016-03-03
> **aljosa2 said:**
> Hi MikeMecanic,
some 20-25 days ago I installed Xenial on 3 notebooks, just 2 or 3 days before 'Gnome software center' replaced 'Ubuntu software center'. Everything was ok with these settings.
In order to update BIOS in this notebook (Lenovo Y700-17ISK), few days ago I had to delete Xenial, install Windows 10 evaluation enterprise, then delete Windows 10 and install Xenial again.
Unfortunately I am circa 500-600 km far away from other 2 notebooks at the moment, so can't tell you what is the current situation.

You should dual boot instead and choose the option alongside Windows 10.  If you still have the bug mention in the Kernel 4.5 thread, then try a fresh install in Legacy Mode.

The bug is not in Trusty Daily ISO.  Will try Gnome now...

---

### Post by Cavsfan on 2016-03-03
Oddly, I don't have this problem but noticed something new in Xubuntu 16.04.

My Pre-Released updates are in a new tab all it's own - Developer Options:

[ATTACH=CONFIG]267628[/ATTACH][ATTACH=CONFIG]267629[/ATTACH]

---

### Post by MikeMecanic on 2016-03-03
The bug is also in Gnome.

---

### Post by DougieFresh4U on 2016-03-03
> **Frogs Hair said:**
> Strange , mine is different than both images. Prereleased updates are displayed under the developer options.

I have the same as you and nothing
'grayed' out.
Using up to date Xenial

---

### Post by mc4man on 2016-03-04
I believe it may come & go. On one laptop wasn't there, showed up the other day, now gone.
On this laptop I'm on it's there, screen 1. The file that controls  & default setting would be on the line highlighted in screen 2, maybe check what's there ...

If changed for example as in screen 3 then both line 2 & 4 would be altered as in scr. 4

---

### Post by MikeMecanic on 2016-03-04
```
gksu gedit /etc/apt/apt.conf.d/10periodic

```

Changing line 2 to <<1>> seems to be the solution.  I don't have line 4 and I didn't disable Xenial-backports.  The bug was not in and out here, it was permanent since many, many weeks.  

This is the modification I made to line 2:

[PHP]APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "1";
APT::Periodic::AutocleanInterval "0";[/PHP]

Thanks for the tip! I pay the beer Friday.

---

### Post by v3.xx on 2016-03-04
> **MikeMecanic said:**
> ```
gksu gedit /etc/apt/apt.conf.d/10periodic

```

Changing line 2 to <<1>> seems to be the solution.  I don't have line 4 and I didn't disable Xenial-backports.  The bug was not in and out here, it was permanent since many, many weeks.  

This is the modification I made to line 2:

[PHP]APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "1";
APT::Periodic::AutocleanInterval "0";[/PHP]

Thanks for the tip! I pay the beer Friday.

Here is what it did for me.

[ATTACH=CONFIG]267646[/ATTACH]

---

### Post by ventrical on 2016-03-04
I used the beta1 release and it chose restricted by default.

..but no issues..

---

### Post by MikeMecanic on 2016-03-04
> **ventrical said:**
> I used the beta1 release and it chose restricted by default.

..but no issues..

I enable it on post-installation.  I just try to disable it and put line 2 back to zero but the bug comes back.
@Ve3.xx Well, I  guess that you don't have the bug...  Developers will have to take a look at it now.  Let see if Aljosa2 can fix the bug?

---

### Post by mc4man on 2016-03-04
The 4th line is from the option of 'Download & Install ..' it being the the Install part of that option, ie., Unattended-Upgrade
(- the 2nd line is the Download.. part

Now on the other machine where the option was greyed out (it's currently unavailable to me until tonight)  I know there was a 2nd file in that folder that seemed to mirror 10periodic, maybe see  if that file exists & if so get rid of if the option is not becoming 'un-greyed out' in Software & updates.

---

### Post by MikeMecanic on 2016-03-04
> **ventrical said:**
> I used the beta1 release and it chose restricted by default.

..but no issues..

Forgot to mention something that may not be related but I keep canonical and canonical source disable.  On Feb 3rd, the Gnome team disable them permanently and since then I don't enable them anymore.  I was getting a message saying Failed to download repository, check you Internet connection.  After the 3rd, this message was gone.

---

### Post by MikeMecanic on 2016-03-04
> **mc4man said:**
>  I know there was a 2nd file in that folder that seemed to mirror 10periodic, maybe see  if that file exists & if so get rid of if the option is not becoming 'un-greyed out' in Software & updates.

There are lots of files there but I don't see one that looks like the mirror of 10periodic?  If you want I can do a screenshot of them...

---

### Post by mc4man on 2016-03-04
> **MikeMecanic said:**
> There are lots of files there but I don't see one that looks like the mirror of 10periodic?  If you want I can do a screenshot of them...
I'll ck. tonight. Probably nothing to do with the option being greyed out the cause of which remains unknown?

---

### Post by mc4man on 2016-03-04
> **mc4man said:**
> I'll ck. tonight. Probably nothing to do with the option being greyed out the cause of which remains unknown?

here's the file, not on my other install

---

### Post by MikeMecanic on 2016-03-04
I'M on Xubuntu now and the bug is still there.  I have a second bug, gksu does not work in Xubuntu.  When I enter my password nothing happen for the same command line of post 22.  Here's the content of 20upgrade

EDIT:  Got it now it is not gedit here but mousepad. ** So you want me to set the first line to 2? ** BTW, Made a perfect fresh install of X with Proposed + Kernel4.5-rc6 + removing 4.4.0.10 +4.4.0.9.  A+ all the way and no slow reboot.
EDIT2: Setting line 1 at 2 did not change anything.  Plus I did not change 10periodic yet.  Will reboot to see if the change occurs.

EDIT3: DId not work, so I set back to << 1 >>.

---

### Post by mc4man on 2016-03-04
> **MikeMecanic said:**
> I'M on Xubuntu now and the bug is still there.  I have a second bug, gksu does not work in Xubuntu.  When I enter my password nothing happen for the same command line of post 22.  Here's the content of 20upgrade
well getting rid of 20 didn't matter here on the affected laptop but simply editing line 2 (10) enabled the option again. 
As an aside  you're set to check daily daily & download automatically. If wanting to also install those downloaded packages automatically that's where line 4 is needed.  (the APT::Periodic::Unattended-Upgrade "1";  line
 it that scenario line 2 stays the same, ie. 1

---

### Post by MikeMecanic on 2016-03-04
> **mc4man said:**
> well getting rid of 20 didn't matter here on the affected laptop but simply editing line 2 (10) enabled the option again. 
As an aside  you're set to check daily daily & download automatically. If wanting to also install those downloaded packages automatically that's where line 4 is needed.  (the APT::Periodic::Unattended-Upgrade "1";  line
 it that scenario line 2 stays the same, ie. 1

I set line 2 in 10periodic to << 1 >> and it's okay now:  Same as in Gnome.  I only have 2 lines in 20auto-upgrades.  Do I keep it the way it is or should I also put line 2 in 20auto-upgrade at 10? Not sure where is the 10?

```
gksu mousepad /etc/apt/apt.conf.d/10periodic

```

---

### Post by sammiev on 2016-03-04
I updated Xubuntu first and made the changes in 10 on line 2 to << 1 >>. Open Software and updates to see whats above on the other post.

Did a fresh update in Terminal and seen it checked for Security updates.

No updates were available.

---

### Post by mc4man on 2016-03-04
> **MikeMecanic said:**
> I set line 2 in 10periodic to << 1 >> and it's okay now:  Same as in Gnome.  I only have 2 lines in 20auto-upgrades.  Do I keep it the way it is or should I also put line 2 in 20auto-upgrade at 10? Not sure where is the 10?

```
gksu mousepad /etc/apt/apt.conf.d/10periodic

```
Once it comes back in the gui then no need to edit the file(s) anymore. 
If the option disappears again the an edit seems to return it. 10periodic seems to be the file of note, as said  my good install didn't even have it & this install doesn't care if it's gone. If you happen to  have it (the 20 file) I'd just leave it.

---

### Post by MikeMecanic on 2016-03-04
> **mc4man said:**
> Once it comes back in the gui then no need to edit the file(s) anymore. 
If the option disappears again the an edit seems to return it. 10periodic seems to be the file of note, as said  my good install didn't even have it & this install doesn't care if it's gone. If you happen to  have it (the 20 file) I'd just leave it.

Thanks a lot then.  I'll show up with a few Heineken Friday.

EDIT:  Feel good to see that it also work for you Sammiev

---

### Post by Cavsfan on 2016-03-06
I guess I'm not with the rest of you as this being a concern. I do not want any update to be downloaded and installed automatically. I get all updates via CLI commands.
Or maybe I'm not understanding the problem correctly.
When and if update manager opens I just close it. Occasionally, I'll see the "dpkg is busy" error and open update manager and close it and the error goes away.

Arch Linux does not even have an update manager or whatever. I like it that way.

---

### Post by unflavored on 2016-03-17
This has been a bug in Ubuntu for many years for some people.  [I found this thread from 2012.](http://ubuntuforums.org/showthread.php?t=2005415&page=2&p=12070400#post12070400)  I made a fresh install of 16.04 from the big 1.5GB daily build, not the mini.iso, and I have this bug too.  From that 2012 thread, this is the workaround that worked for me: ```
sudo rm /etc/apt/apt.conf.d/20auto-upgrades
```  Edit: PaulW2U points out [there is a bug report now.](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1554099)

---

### Post by MikeMecanic on 2016-03-22
Bug fixed with today's update: Software-common-properties 0.96.20.  The content of 10periodic and 20auto-upgrades (4 lines each) are all set to zero now.

---

### Post by unflavored on 2016-03-23
> **MikeMecanic said:**
> Bug fixed with today's update: Software-common-properties 0.96.20.  The content of 10periodic and 20auto-upgrades (4 lines each) are all set to zero now.  It's fixed for me in today's daily .iso, but my files are different from yours.   10periodic  ```
APT::Periodic::Update-Package-Lists "1"; APT::Periodic::Download-Upgradeable-Packages "0"; APT::Periodic::AutocleanInterval "0";
```  20auto-upgrades  ```
APT::Periodic::Update-Package-Lists "1"; APT::Periodic::Unattended-Upgrade "1";
``` I don't know what any of it means, though.

---

