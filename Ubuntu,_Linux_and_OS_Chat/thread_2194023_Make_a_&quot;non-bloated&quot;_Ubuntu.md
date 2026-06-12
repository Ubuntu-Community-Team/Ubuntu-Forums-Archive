---
title: "Make a &quot;non-bloated&quot; Ubuntu"
date: 2013-12-16
forum: Ubuntu, Linux and OS Chat
---

### Post by Tristan_Williams on 2013-12-16
A lot of people, such as myself, feel that Ubuntu has way too much extra stuff, a.k.a. "Bloat". Personally, I hate bloat, because it gets in my way. I hate seeing those extra applications that I've never even clicked on or even know what they are for. I hate having Kernel support for amatuer radio, when I don't even know what amateur radio is.

So, to overcome this issue, I decided to use Ubuntu Minimal Installer. This handy "mini.iso" Live system lets you start from the absolute minimum. It gives you the option to only install what is required by ubuntu to boot, run a command line, and use package management.

For this tutorial, we will be using Ubuntu 13.10 mini.iso, you can download it from the following page:
[https://help.ubuntu.com/community/Installation/MinimalCD#A32-bit_PC_.28x86.29](https://help.ubuntu.com/community/Installation/MinimalCD#A32-bit_PC_.28x86.29)

Next, using your favorite live cd creator (I reccomend Unetbootin), write the mini.iso image to your Prefered media. I personally use a 8 GB USB stick.

Once the iso is installed, reboot your system, and boot from your installation media.

If you are confortable using advanced options, go to advanced options --> expert command line install

For this tutorial, we will be using the normal command line install, so just select command line install (don't go to advanced options)

Follow the instructions provided and pick whichever options suit you best.
I will give you a hint. If you leave your flash drive in through the entire process, you wont ever be able to remove it, because it is /dev/sda... grub gets installed on /dev/sda, so you wont be able to boot without it.

Instead, once you reach the part where you pick a username, remove the installation media.

Once the process is done, you will reboot your computer and boot into the newly installed system. 

You are good to go now. Just install the packages you want via the command line and configure things the way you want.

I will post another tutorial, as a comment, on how to make the necessary backups to recover from a broken system (I break things quite often)

---

### Post by QIII on 2013-12-16
*Moved to *[I][B]Ubuntu, Linux and OS Chat.


[/B][/I]Thank you for your effort and willingness to help.  Unfortunately, this did not meet the guidelines for inclusion in the tutorials section.  Please review [this]("http://ubuntuforums.org/showthread.php?t=2143602") and feel free to post again in the Tutorials subforum after preparing a suitable guide.

Thanks.

---

### Post by Tristan_Williams on 2013-12-16
For this part, we will be creating the necessary backups for when you break something (trust me, you will, just like me)

First, we need to make a directory to store our backups.
```

cd /
mkdir /pref
cd /pref

```

Now, lets make a backup of the current installed packages.
```

sudo dpkg --get-selections > pkgs-backup.txt

```

Now we will ad a few directories
```

sudo mkdir /pref/etc /pref/home /pref/other

```

Now, we will create a few aliases. 
```

sudo nano /etc/bash.bashrc

```

Now, add the following lines to the end of the file.
```

alias depend='sudo apt-get install -f'
alias update='sudo apt-get update'
alias upgrade='sudo apt-get upgrade'
alias clean='sudo apt-get autoclean'
alias autorm='sudo apt-get autoremove'
alias filebackup='sudo cp /etc/bash.bashrc /pref/etc/ && sudo cp /etc/profice /pref/etc/profile'
alias backup ='filebackup &&  sudo cp -R /home /etc/home && sudo dpkg --get-selections > /pref/backup.txt'
alias maintain='update && depend && upgrade && clean && autorm && backup'

```

Note: in order for this to take effect, you must restart bash (simply type "bash" in the command line.

From now on, instead of "sudo apt-get update" you need to type "maintain"

This "maintain" command will automatically update, upgrade all packages as needed, clean up any unneeded files or packages, and create backups of everything you need.

-----------------------------------------------------------------------

Now for the good part. 

Lets assume that you have just done something and your system is broken somehow.

You need to make a copy of the entire /pref directory, and place it on a CD or USB drive for later use. 

Next, install the system using the same method explained in the first tutorial.

Setup your user and copy everything from the backup "home" directory into the new users "home" directory.

Now, replace the /etc/bash.bashrc with the one in the the /pref/etc/ directory.

Do the same thing for the /etc/profile file.

Now, restart bash, and type "maintain" and press enter.

your system should now be back to normal.



Please note that this solution USUALLY works. I have had occasions where the only solution was a clean install, or only parts of this recovery technique worked, but others did not.

All feedback is appreciated. Thank you :)

---

### Post by Tristan_Williams on 2013-12-16
Thank you for informing me that this tutorial isn't up to par. I'm not quite sure as to what i'm missing in it though. Could you please help me with making a better tutorial? I know all of the steps are correct but I'm sure there are things i need to explain in more detail or change.

Thank you.

---

### Post by deadflowr on 2013-12-16
I think that at some point in your toot, you will need to discuss networking issues.
Since the mini install is basically a netinstall.
And a network connection is paramount for using it.

---

### Post by rrnbtter on 2013-12-18
Greetings,
At least a few of the "lot of people, such as yourself" may want enough bloat to get a bluetooth mouse working. You may want to include information on how to install the BT dongle firmware and get a BT stack running such that it will support a mouse. Also I agree the amateur radio operators are on their own or else use the bloated system. :)

---

