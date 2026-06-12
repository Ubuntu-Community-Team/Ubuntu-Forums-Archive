---
title: "Headless Server Upgrade from 12.04 - 14.04"
date: 2014-07-31
forum: Server Platforms
---

### Post by Joshua on 2014-07-31
I can't get the normal
```
sudo do-release-upgrade
```
command to work as expected.

Some options do appear to work, but I don't want to use them unless I can tell exactly what the differences are.

My /etc/update-manager/release-upgrades file says Prompt=lts, but when I run the normal command, I get 
```
Checking for a new Ubuntu release
No new release found

```

If I run with the -d or -p options, it seems to work properly, but I cancel the upgrade after it gets started since I don't know exactly what the difference is.

Also, if I change to "Prompt=normal" and run the command (with no options) I get:
```
Checking for a new Ubuntu release
Err Upgrade tool signature                                                     
  404  Not Found [IP: 91.189.92.201 80]                                        
Err Upgrade tool                                                               
  404  Not Found [IP: 91.189.92.201 80]                                        
Fetched 0 B in 0s (0 B/s)                                                      
WARNING:root:file 'quantal.tar.gz.gpg' missing
Failed to fetch
Fetching the upgrade failed. There may be a network problem. 
```

Something that might be related - the server was running 11.10 until a couple days ago.  I used the command to successfully upgrade to 12.04.4 successfully.  Now, it won't go to the next LTS release.

Anyone know how the do-release-upgrade tool works in detail?

---

### Post by tgalati4 on 2014-07-31
When you canceled the upgrade-in-progress, there is probably a pre-installation script the runs (and quickly) to create environment variables, make directories, copy configuration files needed, etc.  So now when you try to run it again, you get errors.  This is a Use Case that was probably not considered when writing the upgrade-in-place script.

Your chance of breakage in this situation is directly proportional to how difficult it is to reach your headless server.

I would back up critical data, wipe and perform a clean install.  Your system is now in an indeteriminate state, and will remain that way until a clean install is performed.  In order of risk of breakage:

1.  In-place upgrade
2.  In-place upgrade on a headless server
3.  In-place upgrade on a headless server after immediately canceling upgrade

That would be called a hat-trick, a triple-play, or a triple-double, depending on your sport of choice.

If you are determined to fix your system, as is, then look for that pre-installation script and manually unroll those changes.  You can also try removing *update-manager-core* with the purge switch, then reinstalling *update-manager-core* to try to get back to a determinate state.  I would strongly recommend a wipe and clean install.

---

### Post by Joshua on 2014-07-31
Thanks for the feedback, but I should expand on some stuff I said in my first post.

The only things I've run since I started upgrading from 11.10 are:
```
sudo apt-get update
sudo apt-get upgrade
sudo do-release-upgrade
exit
```

Then on 12.04:
```
uname -mrs
lsb_release -a
cat /etc/update-manager/release-upgrades
sudo apt-get update
sudo apt-get upgrade
sudo do-release-upgrade
do-release-upgrade
```

This is where things aren't working properly and where I start experimenting.
```
man do-release-upgrade
sudo nano /etc/update-manager/release-upgrades
sudo apt-get update
sudo apt-get upgrade
sudo do-release-upgrade
sudo apt-get dist-upgrade
sudo nano /etc/update-manager/release-upgrades
sudo do-release-upgrade
sudo do-release-upgrade -d
sudo do-release-upgrade -p
```

So I was having problems with the ugprade before ever "cancelling" anything at the last lines where I ran with the -d and -p options.  Also, by "cancelling" I mean that I hit N when it asked if I would like to continue since I was attempting to do the upgrade remotely over SSH.  I should also note that when I first log in to the box via SSH, I get the default status screen and it says:
```
New release '12.10' available.
Run 'do-release-upgrade' to upgrade to it.

```

Of course, that would be the next normal release rather than the next LTS release.

You had two other thoughts that I'm gonna work on, though.  First, does anyone know where the scripts are for the do-release-upgrade tool?  Probably more important, any configuration files for it?

Also, I think I'll try to purge the tool and reinstall.  If that works, at least I'll know that apt-get is working normally.

I have not restarted the computer since it was requested during the last upgrade.  So I'll probably do that, too - just hate doing so.

---

### Post by CharlesA on 2014-07-31
Back your stuff up before you do anything else.

So you upgraded from 11.10 to 12.04, right? Sounds like it's still set for regular releases, not lts to lts.

Check this out:
[https://help.ubuntu.com/14.04/serverguide/installing-upgrading.html](https://help.ubuntu.com/14.04/serverguide/installing-upgrading.html)

I just tried it on my 12.04.4 box and it stated: 

```
sudo do-release-upgrade
Checking for a new Ubuntu release
No new release found
```

I had to use 
```
sudo do-release-upgrade -d
```

To get to 14.04. Note: This box was a clean install of 12.04, not an upgrade.

---

### Post by Joshua on 2014-07-31
This is strange.  The status screen says 12.10 is available, but I definitely have Prompt=lts in the config file.  Is there another place for settings that would force lts-lts upgrades?

If I understand the -d option, it's intended to force an upgrade to a developmental version.

I actually did this same thing on a backup server last week that had a clean install of 12.04 that has been running since 2012.  I got the same messages and the -d option seemed like it would bypass the issues until a week ago (last Friday) after the 14.04.1 update was released.  At that time I could do the normal:
```
sudo do-release-upgrade
```
and it worked perfectly.  Just doesn't seem to work on this box.

Also, the backup server is still working properly and completed a backup of the server I'm working on now last night.  So I should be good in the data backup area.

---

### Post by CharlesA on 2014-07-31
I haven't done updates on the box I tested in about a week, so it looks like that was why I had to use -d. Running it normally prompted to upgrade to 14.04.1.

---

### Post by Joshua on 2014-07-31
I think I've got some hints about where the problem is.  I tried to:

```
sudo apt-get remove --purge update-manager-core
```
and I got some warnings:
```
dpkg: warning: while removing update-manager-core, directory '/var/lib/update-notifier' not empty so not removed.
dpkg: warning: while removing update-manager-core, directory '/var/lib/update-manager' not empty so not removed.
dpkg: warning: while removing update-manager-core, directory '/var/log/dist-upgrade' not empty so not removed.
```
The first directory contains the text file release-upgrade-available and it says
```
New release '12.10' available.
Run 'do-release-upgrade' to upgrade to it.
```
Maybe that's where the status screen gets it's message on ssh login?
The last directory is logs that I haven't really looked at yet, but the second directory contains:
```
$ ls /var/lib/update-manager/
meta-release      meta-release-lts-development
meta-release-lts  meta-release-lts-proposed
```
Each one of those files has a list of versions of Ubuntu with some details about them. Notably, the files meta-release, *-development, and *-proposed all contain an entry for 14.04, but meta-release-lts does not.  Where do these files get their info?

---

### Post by CharlesA on 2014-07-31
```
sudo rm -r /var/lib/update-notifier /var/lib/update-manager /var/log/dist-upgrade
sudo apt-get install update-manager-core
```

Good luck.

---

### Post by tgalati4 on 2014-08-01
Just to clarify:

Case 1.  In-place upgrade:  This entails a certain amount of risk whether going from 12.04 to 12.10 or 12.04 to 14.04.  Newer kernels, newer frameworks, newer configuration scripts--the complexity is sure to cause some issues.  If you are lucky, the upgrade will work as it is supposed to.

Case 2.  In-place upgrade on a headless server:  Well, you do have to reboot at some point.  Many of the post-installation scripts require the newer code to be running in order to execute properly.  If you reboot and you have a kernel or network card problem, then you are effectively locked out of your system.

Case 3.  Not applicable in this case since you didn't start the upgrade process, you just didn't let the script continue.  However, without rebooting and fixing the intermediate issues, your system will still be in an indeterminate state.

In-place upgrades are a nice feature in linux, but not without risk and certainly not intended for production servers.

Good luck with your troubleshooting.

---

### Post by Joshua on 2014-08-01
Removing the files and then reinstalling the update-manager-core package doesn't seem to have changed anything.  I'm starting to wonder if there was something different about the last upgrade I did (other than physical location).  Anyway, I went ahead and used the -d option, and everything seems to have gone very well.  So far, the only reconfiguration I needed was for Apache options that have been changed since the last version.  Thanks for the help!

---

