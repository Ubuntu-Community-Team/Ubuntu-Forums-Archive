---
title: "HOW TO: Reinstall (Almost) All Packages At Once Without Re-Installation"
date: 2010-02-14
forum: Tutorials
---

### Post by ALIENDUDE5300 on 2010-02-14
[SIZE="5"][COLOR="Olive"]Introduction[/COLOR][/SIZE]

First of all, I want to start by saying that most of this is taken from [this great post here by Lumenary]("http://ubuntuforums.org/showthread.php?t=735693"). I simply took his bash script source code and greatly improved it by making it reinstall all the packages at once instead of one at a time. If you don't know what this script does, or why it would be needed, I suggest reading Lumenary's post, which does a great job explaining this script's purpose. By reinstalling all the packages at once, the process is incredibly faster. It also makes the process possible on a wireless connection. When reinstalling the packages one at a time over a wireless connection, it is possible, but not very likely for some of the packages to disconnect you from the internet, at least temporarily, causing the rest of the process to fail. However, because all the packages are sent to aptitude at once, it downloads all the files needed before it even starts reinstalling packages. Therefore, even if you do lose internet connectivity partway through the process, you shouldn't experience any problems as all the necessary files are already retrieved and cached locally. In addition to that, I also added the apt-get clean command before reinstalling the packages to clear the local package cache, and force apt-get to retrieve any package files again (instead of manually running the command before running the script). In addition to that, I added apt-get update to check for new versions of packages from the repositories and I added the -m flag to the apt-get command so that if there are any packages that can not be retrieved, apt-get will still reinstall all other packages, ignoring the missing packages. This didn't matte much in Lumenary's script because it reinstalled each package one by one, but because this script tries to reinstall all the packages at once, this option could prevent the script from not working at all. In order to run this script you will *need* to be connected to a working internet connection. I have tested this script on my own computer, and it worked perfectly without causing any problems at all, however, I can NOT guarantee that you will experience the same result. Therefore, even though I tried to make this script work flawlessly without causing any problems, you are running this script at your own risk. 

[SIZE="5"][COLOR="Olive"]Let's Get Started[/COLOR][/SIZE]

Since you've made it this far, I'm going to assume that you realize the risks of re-installing all the packages on your system and want to continue anyways. Even though this script is relatively safe and should cause no problems, I suggest that you backup all of your important data. For most people, simply copying your /home folder and all the files in it should be all you need to do, but you may also want to backup any custom configuration files and any other changes you've made to your system. Because of how this script handles re-installation, steps 1 and 2 of Lumenary's post are unnecessary, and will actually not help at all since this script will end up removing the locally cached files and then retrieving them again. In this tutorial, I'm going to attempt to guide you step by step in setting up this script and running it. If you simply want to get this done as fast as possible, simply copy and paste the following code into a terminal window (Applications > Accessories > Terminal). Sorry for the complicated code, but it's mostly to avoid having to add sudo in front of every line, in addition to informing the user what's going on and saving everything to a log file.

[SIZE="5"][COLOR="Olive"]The Terminal Command[/COLOR][/SIZE]

Sorry for the complicated code, but it's mostly to avoid having to add sudo in front of every line, in addition to informing the user what's going on and saving everything to a log file. This is the code that you should copy and paste into your terminal. There is no need to manually create the bash file or set executable permissions, this command handles everything for you. This is in a quote box to make it easier to copy.

> 

sudo su root -c "echo apt-get clean && apt-get update --fix-broken && echo -e '#\x21/bin/bash\\n\\nfor pkg in \x60dpkg --get-selections | egrep -v deinstall | awk \x27{print \$1}\x27 | egrep -v \x27(x11-common|libc|libss2|libstdc|libpam|libgcc|liblaunchpad|libtext-wrap|lsb-base|passwd|upstart|dpkg|debconf|perl-base|python|apt|initscripts|sysv|coreutils|bash|mysql|virtuoso|mythtv|anjuta|dash|diff)\x27\x60 ; do pkgs=\"\$pkgs \$pkg\"; done\\necho \"The Following Apt-Get Command Was Run:\\\n--------------------------------------\\\n\\\napt-get -y -m --force-yes install --reinstall\$pkgs\\\n\\\nCommand Output Log:\\\n-------------------\\\n\" > reinstallationlog.txt\\napt-get -y -m --force-yes install --reinstall\$pkgs | tee -a reinstallationlog.txt' > reinstall.sh && clear && echo -e \"\\nSetting Script Permissions...\\\n------------------------------\" && chown -v root:root reinstall.sh && chmod +x -v reinstall.sh && echo -e \"\\nStarting Package Re-Installation Process...\\n-------------------------------------------\" && sh reinstall.sh && echo -e \"\\nThe re-installation process is complete. A log of the process can be found in the file called 'reinstallationlog.txt'.\""



[SIZE="5"][COLOR="Olive"]The Bash File Source Code[/COLOR][/SIZE]

You don't have to pay any attention to this section, as the code above handles everything including becoming root, setting permissions on the bash file, and running it while saving output to a log file in case something goes wrong. The only reason this is here is in case anybody wonders what the actual bash file looks like before the code above is run (you can always just open the file after running the code), and there are lots of good reasons to wonder what code you are running on your system, especially when you are running it as root.

```


#!/bin/bash

for pkg in `dpkg --get-selections | egrep -v deinstall | awk '{print $1}' | egrep -v '(x11-common|libc|libss2|libstdc|libpam|libgcc|liblaunchpad|libtext-wrap|lsb-base|passwd|upstart|dpkg|debconf|perl-base|python|apt|initscripts|sysv|coreutils|bash|mysql|virtuoso|mythtv|anjuta|dash|diff)'` ; do pkgs="$pkgs $pkg"; done
echo "The Following Apt-Get Command Was Run:\n--------------------------------------\n\napt-get -y -m --force-yes install --reinstall$pkgs\n\nCommand Output Log:\n-------------------\n" > reinstallationlog.txt
apt-get -y -m --force-yes install --reinstall$pkgs | tee -a reinstallationlog.txt


```

[SIZE="5"][COLOR="Olive"]For Absolute Beginners -- How to Run the Code[/COLOR][/SIZE]

Experienced users can probably safely skip this part: If you are an absolute Linux beginner (don't worry -- we all were at some point!), unless you are absolutely sure that you need to run this script, you should definitely make sure that you know what you are doing. I've had a few people ask how to copy and paste things into the terminal before, so I'm going to briefly explain this here to avoid confusion (and to prevent people from actually trying to *type* this monstrosity into a terminal window. To copy the text, simple select it with the mouse and either right click it with the mouse and then click "Copy", or press Ctrl+C. I like to use keyboard shortcuts whenever possible as they save a lot of time. Now to paste it in the terminal: Assuming that you already have your terminal window open, make sure that there is nothing already on the line except for the prompt which looks something like this: "user@computer:~$ ". Of course, user would be replaced with your username, computer would be replaced with your computer's hostname, and ~ would be replaced with the folder you are currently in (~ by default is your home folder). However, there should be no other text after the dollar sign ($). If you press the up and down arrow keys, you may accidentally cause commands you entered previously to appear on the line. Simply hold in backspace until the line is blank. Now then, in the terminal window, either right click and choose paste or press Shift+Insert. Once the code is on the line, press the Enter key. Because you are running a command as root (in order to make system changes), you will need to enter your password.  You will not see your password on the screen as you type it. This is perfectly normal, simply press enter when you are done typing it. If your account is not in the admin group (the account you created when you installed the system automatically is), this will not work, as you do not have permission to run sudo. If you only have only one account on your system, chances are you have administrative permissions and you don't need to worry about this, however if it's not your computer, such as a public computer or someone else's PC, you probably shouldn't be running this command anyways.

[SIZE="5"][COLOR="Olive"]Encountering Any Problems?[/COLOR][/SIZE]
If you run this script and receive any errors, post them here and I will attempt to modify the script to prevent these errors from occurring. This script is not perfect, however I will try to help you with any trouble you have.

**EDIT:** This post has been recently updated to work with some new changes in Lucid Lynx.

---

### Post by DGRE6133 on 2012-05-08
Hi im a newbie to ubuntu. Is there a way to use this script to isolate and reinstall broken packages?

---

