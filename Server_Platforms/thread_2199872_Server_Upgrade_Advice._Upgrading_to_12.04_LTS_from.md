---
title: "Server Upgrade Advice. Upgrading to 12.04 LTS from 10.10 Maverick Meerkat."
date: 2014-01-16
forum: Server Platforms
---

### Post by jeremy4 on 2014-01-16
I need some advice on my server upgrade plan.  I am running a server with Ubuntu Server 10.10 "Maverick Meerkat" currently.  I am basically using the server as a NAS storage device for a media share, but am also running a Subsonic Music server and a Gallery picture library.  When I set up the server Maverick was the latest version available and at the time I  did not know about LTS in regards to server editions of Ubuntu (for some reason at the time assumed all server versions were LTS).  The 10.10 installation is up-to-date and prompting me to do a  a release upgrade to Natty.

The server is running the following:

mdadm - RAID5 6 TB array for media storage
SMB - samba for the network share off of the RAID array
Subsonic music server
Gallery
Webmin

The 10.10 installation is actually running off of an older IDE hard drive.  After I got everything up and running I took a Clonezilla image of the drive.  

My upgrade plan is to do the following.  Please let me know if anybody sees any flaws:

1.)  Use clonezilla to clone the current 10.10 installation to a new hard disk (this will actually be another IDE HDD :)).

2.)  Disconnect the HDD with my original installation from the server.  

3.) Verify the system boots and is working properly with the newly cloned HDD.

4.) Do a release upgrade to 11.04 Natty Narwhal. 

5.)  Apply all available updates.

6.) Do a release upgrade to 11.10 Oneiric Ocelot

7.) Apply all available updates.

8.) Do a final release upgrade to 12.04 Precise Pangolin.

9.) Apply all updates.

The end goal is to get the server updated to the latest LTS release.  

My assumption is that by doing it via this method, if something goes wrong with the upgrades, I can just put the HDD with my original 10.10 installation back in the server and it will be like nothing changed.

All of the data is on the untouched RAID 5 array (4 x 2TB SATA drives), so I don't see the attempted upgrade having any affect on this.  I do have about 80% of the data on the Array backed up elsewhere, but backing up the entire media share is not possible.

Does my method described above seem like a low-risk option for getting my server up-to-date?  In regards to the data on the array?

I would prefer to do this via an in-place upgrade rather than a fresh install of 12.04 on a new disk and then assembling the array in mdadm on the new installation, due to some previous configurations I have done on this server some time ago. (mdadm email notifications, Webmin install, etc.)  Thanks for any input or suggestions on this process.

-hogfan

---

### Post by rubylaser on 2014-01-16
I would backup your boot drive as you plan to do (verify that it works).  Next, I would just upgrade from 10.10 -> 12.04 directly. You can follow these [directions]("https://library.linode.com/upgrading/upgrade-to-ubuntu-12.04-precise") to do that.  Your array will be fine. Each disk in mdadm carries the necessary date to re-create your mdadm.conf file even if you lost your OS drive.  The only thing that may be affected during the upgrade is Webmin, but I don't use it, so I'm not sure about that.

---

### Post by jeremy4 on 2014-01-16
Thanks for the link.  That is what I will do.  I'm now worried about Webmin too much.  I can always purge and re-install it if necessary.  Good to know I can go straight up to 12.04.....wasn't sure  due to dependencies, etc.  Thanks for the ip.

-hogfan

---

### Post by jeremy4 on 2014-01-16
Well, I am running into some problems here since my version is EOL.........I've followed this guide here:

[http://askubuntu.com/questions/81647/upgrading-server-9-10](http://askubuntu.com/questions/81647/upgrading-server-9-10)

replacing Karmic in their example with Maverick, and I able to get all the way to the do-release upgrade step, but then I just get "no new release found"

-hogfan

---

### Post by CharlesA on 2014-01-16
Read this: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Or this: [http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release](http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release)

You will have to go from 10.10 > 11.04 > 11.10 > 12.04, so be sure to back up your working configuration.

Personally, I would backup any config files and install 12.04 clean because upgrades aren't always foolproof.

---

### Post by jeremy4 on 2014-01-17
Ok, I ended up going through the upgrade process  from 10.10 --> 11.04 --> 11.10 --> 12.04.  Everything appears to be working fine after the upgrade.  Only errors I saw were on the sendmail.cf  config file about some sections being out of order or something (kept my existing config).  I'll backup that config and reconfigure sendmail and I should be good.  I'm only using it for mdadm email notifications anyway.


There is one last thing I'd like to get sorted out though.

My [COLOR=black] /etc/update-manager/release-upgrades  files  is set to "Prompt=lts".
[/COLOR]
However, now that I am up-to-date (LTS release) on Precise Pangolin, it is notifying me of new release 12.10.  What steps do I need to take to get rid of this prompt. As I understand it, [COLOR=#000000] /etc/update-manager/release-upgrades  file set to "Prompt=lts" should only notify me of an upgrade if it's an LTS release.
[/COLOR]
Thanks for any assistance with this, and thank you both for all of the good info on the upgrade process.  

-hogfan

---

### Post by CharlesA on 2014-01-17
Check to see what "Notify me of new Ubuntu versions" is set to in the Update Manager settings.

---

### Post by jeremy4 on 2014-01-17
No update manager here. Not using any GUI.  I thought that is what the **[COLOR=#000000]/etc/update-manager/release-upgrades [/COLOR]**[COLOR=#000000]config[/COLOR]**[COLOR=#000000] [/COLOR]**[COLOR=#000000]file is for.  I have it set to:

Prompt = lts

Here's what my release-upgrades config file looks like.
```
[/COLOR]# Default behavior for the release upgrader.

[DEFAULT]
# Default prompting behavior, valid options:
#
#  never  - Never check for a new release.
#  normal - Check to see if a new release is available.  If more than one new
#           release is found, the release upgrader will attempt to upgrade to
#           the release that immediately succeeds the currently-running
#           release.
#  lts    - Check to see if a new LTS release is available.  The upgrader
#           will attempt to upgrade to the first LTS release available after
#           the currently-running one.  Note that this option should not be
#           used if the currently-running release is not itself an LTS
#           release, since in that case the upgrader won't be able to
#           determine if a newer release is available.

Prompt=lts


[COLOR=#000000]
```
[/COLOR]

---

### Post by CharlesA on 2014-01-17
What does the prompt look like, I wonder if it is just landscape telling you there is a new release.

Try running this and see if it shows you the same message:

```
landscape-sysinfo
```

---

### Post by jeremy4 on 2014-01-17
FYI -


If anybody else runs into this it appears the issue is:


The release available stamp file hangs around incorrectly. The following fixes this issue:


On 12.04+: 


sudo rm /var/lib/update-notifier/release-upgrade-available


Below 12.04:


sudo rm /var/lib/ubuntu-release-upgrader/release-upgrade-available




Once I removed that file, I am no longer prompted for the next release.


This file is safe to remove as it will be regenerated next time the motd script runs if appropriate.

---

