---
title: "maintaining configurations, settings"
date: 2012-10-05
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by unibroker on 2012-10-05
When I boot from a live cd am I able to introduce my setup from 12.04 or is that only possible once I install Quantal to my hard drive?  When I use the live cd I start with a completely new Home folder however I can see the contents of 12.04 under Devices.  I was doing a test run with Quantal and everything works (internet connection, resolution, sound) but I would like to be able to test the settings I had under 12.04 before I go all in.

---

### Post by grahammechanical on 2012-10-06
If you are thinking of upgrading 12.04 to 12.10 then wait until it is officially released at the end of October. There is still much work being done on it.

If you are thinking of installing 12.10 into a separate partition and dual or triple booting into it, then go ahead. But keep in mind that you will then be a tester of Ubuntu Quantal. Expect the issues that testers expect.

I think that it is good practice to install the latest release of Ubuntu into a 10 to 15 GB partition to see if you can set it up the way you like, with the applications you like before you upgrade the existing Ubuntu install. I would say that this is especially true for those using 12.04 as it is an LTS release.

This has been my practice for some time.

Regards.

---

### Post by unibroker on 2012-10-06
> **grahammechanical said:**
> 
I think that it is good practice to install the latest release of Ubuntu into a 10 to 15 GB partition to see if you can set it up the way you like, with the applications you like before you upgrade the existing Ubuntu install. I would say that this is especially true for those using 12.04 as it is an LTS release.

This has been my practice for some time.

Regards.

I came over from Windows to Ubuntu about a year ago.  I was and am dual boot with WinXP.  Soon after I started Ubuntu I read an article that Precise booted very fast and so upgraded.  This was in November so Precise was still in the testing phase.  I actually enjoyed getting the updates and seeing things improve along the way.  It wasn't until later that I read, besides the issues of a testing phase, of all the problems people were have doing an upgrade as opposed to a clean install.

My question is if I upgrade is there away to access my setting, files and configuration that I currently utilize in Precise?  It is a rudimentary question but upon booting into a live cd I see them when I go into nautilus but not real clear how to have them automatically implemented when using Quantal.  Thanks for the response.

---

### Post by cariboo on 2012-10-06
You can use your settings using the Live CD, but unless you have set up a persistent area on your usb device, the changes will go away, when you shut the system down. 

As far as using your 12.04 settings and configurations in Quantal, What most of us do is backup the home directory, before doing an upgrade/fresh install, then the settings are available in your backup. I selectively copy the settings that rarely change from my backup to my new home directory.

Most of the settings and configurations are in hidden directories, so depending on how you plan to copy the configuration files to your new home directory, you may have to use Ctrl-h in nautilus to see them.

---

### Post by funicorn on 2012-10-06
```
mount /dev/sda_home /mnt
mount -B /mnt /home
```
solves your problem

---

### Post by stinkeye on 2012-10-06
> **cariboo907 said:**
> You can use your settings using the Live CD, but unless you have set up a persistent area on your usb device, the changes will go away, when you shut the system down. 

As far as using your 12.04 settings and configurations in Quantal, What most of us do is backup the home directory, before doing an upgrade/fresh install, then the settings are available in your backup. I selectively copy the settings that rarely change from my backup to my new home directory.

Most of the settings and configurations are in hidden directories, so depending on how you plan to copy the configuration files to your new home directory, you may have to use Ctrl-h in nautilus to see them.
I agree with this.
I always do fresh installs and then copy over settings/configs from a home 
backup for some programs like easystroke, gnote, opera, bash aliases etc.
Not that upgrades don't work but this way, if you encounter problems you know it's not caused by your old configs.

---

### Post by unibroker on 2012-10-06
Thanks for the responses.  One last thing; can I copy the entire contents of my Precise Home folder into the Quantal Home folder at one time?  In the meantime heading on over to Tutorials & Tips forum to read about Backup and Restore.  Can you believe I have root privileges!:shock:

**Update:** I was able to copy the backup (Duplicity) of my Home folder to the home folder of Quantal.  However when I tried to 'Extract Here' with Archive Manager it failed.  I did file an apport with Launchpad.

---

