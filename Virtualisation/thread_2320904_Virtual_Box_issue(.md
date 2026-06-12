---
title: "Virtual Box issue("
date: 2016-04-18
forum: Virtualisation
---

### Post by Brent_Thurber on 2016-04-18
I wasn't sure where to post this but i am getting the following issue from virtualbox
Kernal driver not installed (rc=-1908)

It tells me to run /sbin/rcvboxdrv setup as root
when i run the command it tells me to i get the following error
Starting VirtualBox kernal modules ...failed!
 (modprobe vboxdrv failed. Please use 'dmesg' to find out why)
When I do that I get alot of stuff and I can't type it all out.

Help me I'm sorry if I broke formatting rules I'm new

Running ubuntu trusty in a chroot built on an Acer c710 chromebook

---

### Post by howefield on 2016-04-18
"*Virtualisation*" forum would be the best bet..

Thread moved and welcome to the forums.

---

### Post by MAFoElffen on 2016-04-18
What subversionb version of Ubuntu Desktop 14.04.0x LTS (The x in the previous) are you chrooted into?
What version of VirtualBox?
> 
Kernal driver not installed (rc=-1908)

Then you said the error was
> 
Starting VirtualBox kernal modules ...failed!
(modprobe vboxdrv failed. Please use 'dmesg' to find out why)

You already knew that by your first statement right?

To fix
```

sudo apt-get install --reinstall virtualbox-dkms

```

---

### Post by Brent_Thurber on 2016-04-19
1. I am using Unity with VirtualBox 5.0(the most recent)
2. What do you mean by [code]?
3. Also would it be easier if i used an older version?([https://github.com/divx118/crouton-packages](https://github.com/divx118/crouton-packages)...that is a tutorial i tried along with other...i think it will work fine if i get an older version)
4. And i ran the sudo apt-get install --reinstall virtuaqlbox-dkms and it said it didnt exist...Assuming that that is a typo, i did the other command and got some errors
vboxpci.ko:
Running module version sanity check.
Error! Module version 4.3.36_Ubuntu for vboxpci.ko
is not newer than what is already found in kernel 3.8.11 (5.0.16).
You may override by specifying --force.

also

runlevel:/var/run/utmp: No such file or directory

and

invoke-rc.d: policy-rc.d denied execution of restart.

Needless to say, it didnt work

---

### Post by MAFoElffen on 2016-04-19
Previous post edited...

Since it did not exist, then that confirmed that the kernel module was never installed, so in a terminal run:
```

sudo apt-get install virtualbox-dkms

```
to install it.

---

### Post by Brent_Thurber on 2016-04-19
All i got was
Code:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
virtualbox-dkms is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Still doesnt work

---

### Post by bapoumba on 2016-04-19
It is virtualbox-dkms which is in the multiverse repositories.
Edit : nija'd :)

---

### Post by Brent_Thurber on 2016-04-19
I'm not that good with linux, what does that mean and what do i do?

---

### Post by MAFoElffen on 2016-04-19
I am as confused as your machine is.

(1) Your error said that vboxdrv is not installed. That is a kernel module (driver) provided via package virtualbox-dkms.
(2) You tried to reinstall the package, but it said it was not installed (not present), so could not reinstall it.
(3) You tried to install fresh, but it said it was installed and at the current version.

*** Somewhere in that logic is a contradiction of terms.

Since the "last" said it was installed, lets try again to reinstall it:

Check that the multi-verse repo is selected in your software sources (find in Ubuntu Software Center Settings, or Search in Dash for "Software", which finds the "Software  Sources" Ap, which both methods look at the file at /etc/apt/sources.list) then:
```

sudo apt-get install --reinstall virtualbox-dkms

```

---

### Post by Brent_Thurber on 2016-04-19
there is no software sources app or software center settings? however i did gedit /etc/apt/sources.list and this was in there...deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) trusty contrib

also rerunning the command changed nothing BUT i did see this under a bunch of things
vboxnetflt.ko:
Running module version sanity check.
Error! Module version 4.3.36_Ubuntu for vboxnetflt.ko
is not newer than what is already found in kernel 3.8.11 (5.0.16).
You may override by specifying --force.


vboxpci.ko:
Running module version sanity check.
Error! Module version 4.3.36_Ubuntu for vboxpci.ko
is not newer than what is already found in kernel 3.8.11 (5.0.16).
You may override by specifying --force.

---

### Post by Brent_Thurber on 2016-04-19
OK so i was also talking to my bro about this issue and he said that since i updated my ChromeOS, the script to make it work wouldnt work anymore. So i have to wait for someone to make a new script or update the old one. Thanks for the help though!

---

### Post by MAFoElffen on 2016-04-19
Open a terminal seesion. 
```

sudo gedit /etc/apt/sources.list

```
Look in that file for these 2 lines. If they are not there, paste them into that file and save
```

deb http://[COLOR=#ff0000]01[/COLOR].archive.ubuntu.com/ubuntu/ trusty multiverse 
deb-src http://[COLOR=#ff0000]01[/COLOR].archive.ubuntu.com/ubuntu/ trusty multiverse 

```
If the sections in [COLOR=#ff0000]RED,[/COLOR] between "http://" and ".archive.ubuntu.com/" are different in your sources list, then modify that section in the new lines to reflect that. That section of the address just points to "your" local repository, based from where you originally installed from, in the world... Then save that file and close gedit. Get back to the terminal session

Run this commands to ensure you have the correct keyring for Oracles non-free software (free of cost, but some pieces of the code are closed source):
```

wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add - 
deb http://download.virtualbox.org/virtualbox/debian trusty contrib

```
This will remove the old module and install the newer:
```

sudo apt-get remove --purge virtualbox-dkms && sudo apt-get install virtualbox-dkms

```
What those errors tell me is that you (or someone) upgraded Virtualbox to a newer version, without first uninstallling the old version. That is the procedure that Oracle recommends when doing an upgrade of VirtualBox. So, VirtualBox was at version 4.3.36, got upgraded (without the old removed) to version 5.0.16 (current as of yesterday morning) or 5.0.18 (current as of this morning) ... but the virtualbox-dmks package said it was current, which it is, but with the old 4.3.36 version's kernel module... which will crash when you try to use version 5.0.x VB. Odd that it usually throws a different error for that, but no matters.

The above should get you going again. If the sources lines are good, just skip those. If it says that you already have a good key, so be it, go on. The other commands will remove the old module and install the correct newer module.

---

### Post by MAFoElffen on 2016-04-20
LOL... Good luck with that, but, please read on:

Upgrading ChromeBook... the OS, might affect the script in how your chroot starts. (Did sound like it did chroot and into the root of your image.) But if it does chroot, then that script is working. Not much changes in a chroot (command-wise). If it worked before and works now... One way to check is, after the chroot, check for differences in list directory... and try to execute a command. This is a virtualization section... and a chroot is a type of virtualization.

Like I said ... that error was different than it usually is with that, so there is a slight possibility that it is the chroot, buut other things point to, that you "are" chroot'ed into the image. ... That exception is this--, It recognized that there was a VirtualBox version mismatch. I'm thinkng if you had VirtualBox installed on Chromebook ... that we wouldn't be talking about having to chroot into an image, right?

By this error:
> 
[COLOR=#000000]Error! Module version 4.3.36_Ubuntu for vboxnetflt.ko [/COLOR][COLOR=#000000]is not newer than what is already found in kernel 3.8.11 (5.0.16)[/COLOR]

Changing anything in your script will not change that mismatch in your VirtualBox program version and the vbox kernel module version. Even if, for some reason there was a problem with that, you would still neeed to correct this problem. You will need to eventually correct this by what I posted, or by removing VirtualBox and reinstalling it... 

If, it still had problems after doing that, then it might be easier just to remove VirtualBox, and reinstall. That would ensure that there are no other mismatched "pieces" present.

---

### Post by Brent_Thurber on 2016-04-20
So it didn't work, and now im just really confused. I have no clue how to completely uninstall with everything i have done and it probably won't work anyway. Thanks for your help though!

---

### Post by MAFoElffen on 2016-04-20
Did you install via the ubuntu repo or did uou install from Oracle's website?

---

### Post by Brent_Thurber on 2016-04-20
Oracles website

---

### Post by Brent_Thurber on 2016-04-21
Never mind crouton is broke and im not reinstalling linux for the third time so im trying to go to windows only now thanks for your help

---

### Post by Brent_Thurber on 2016-04-21
I think something you had me do might have broken it

---

### Post by Brent_Thurber on 2016-04-21
Nevermind i dont want to brick my chromebook screw this

---

### Post by MAFoElffen on 2016-04-21
Just got home.

Wait one...

Crouton? What Chromebook version?

---

### Post by Brent_Thurber on 2016-04-22
its an acer c710

---

### Post by MAFoElffen on 2016-04-22
So you are not doing a traditional chroot on an image file, as you described early in this thread...

Did you follow the "crouton" recommendations of a backup? (Just seeing where you are at and how you system is laid out...)

---

### Post by Brent_Thurber on 2016-04-22
Traditional chroot? Apparently not.
I did not use a backup because I didn't know how and did not think my system would just go out...I'm reinstalling trusty and unity again this afternoon

---

### Post by MAFoElffen on 2016-04-24
And how did that go?

---

### Post by Brent_Thurber on 2016-04-25
I have it installed and running...haven't tried virtual box and am not going to unless i have a step by step tutorial so i dont screw up again

---

### Post by MAFoElffen on 2016-04-26
Will PM you when I get home... I might be able to IM, or IRC you through that, if you document what worked back into this thread... Would that work okay for you?

---

### Post by Brent_Thurber on 2016-04-26
I don't know what that means but sure...I wont be home tonight though

---

