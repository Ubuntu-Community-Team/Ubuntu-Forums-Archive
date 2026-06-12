---
title: "in search of knowledge"
date: 2022-03-16
forum: Ubuntu, Linux and OS Chat
---

### Post by coley9225 on 2022-03-16
Hello all. I am always looking for a way to learn more about the workings of linux systems. I'm posting here because I don't have a problem, just looking for a better way, and some info on a couple of things. I am, by nature, a lazy individual. In keeping with the linux way of tthings, I recently wrote a bash script to GREATLY reduce my typing for updates/upgrades, script shown below.I wrote the script, and made a keyboard shortcut to run it. <super>+<u> will execute 'qterminal -e sudo ./updates.sh'. Major time saver, as I run all my upgrade through terminal. I have a couple questions on the script itself, and also questions on the output of the commands.
my update script:
```
#! /bin/bash

# A short script to simplify my updates.
# Must be run as root with sudo.


apt update &&
apt list --upgradable | tee ./upgradable_list.txt
echo "exit status $?"
echo "Do you want to upgrade now? y/n"
    read answer
        answer=${answer^^} # convert answer to uppercase
        answer=${answer:0:1} #reads first letter only
if [ ${answer} = 'Y' ] ;
    then apt upgrade -y
    echo "exit status $?"
    sleep 5


elif [ ${answer} = 'N' ] ;
    then echo "We will postpone upgrades for now."
    sleep 5


else
    echo "Invalid selection. Please run upgrade manually.
    Exiting script now."
    sleep 5
fi


exit

```
The questions on the script;
  1) lines 11 and 12 convert to upper case and strip all but first letter. Is there an easier way to do this? My searchs find a lot of sed or awk methods, but much more typing, and a little confusing.
 2) I have the upgradable list piped to tee, and saved to a file. I don't know what most of that is, but saving to a file affords me a chance to research them. I know libreoffice, firefox, google-chrome, etc, but the lib### and others I can check into some other time. My question is can I do pipe and tee with the update and upgrade commands,, and how to do that without truncating the file on each command.
  3) Is there a way to have the script tell if a reboot is needed.
That covers the script(for now). mMy other questions are on the output of the apt update command. I had an issue with the script, which I was able to solve, but I copied the output to a text file.

```
charles:$ sudo ./updates.sh[sudo] password for charles: 
Hit:1 http://us.archive.ubuntu.com/ubuntu focal InRelease
Hit:2 https://dl.google.com/linux/chrome/deb stable InRelease               
Get:3 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]   
Get:4 http://us.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]  
Hit:5 http://archive.canonical.com/ubuntu focal InRelease                   
Hit:6 http://ppa.launchpad.net/dupeguru/ppa/ubuntu focal InRelease          
Get:7 http://us.archive.ubuntu.com/ubuntu focal-backports InRelease [108 kB]
Get:8 https://esm.ubuntu.com/infra/ubuntu focal-infra-security InRelease [7,426 B]
Get:9 https://esm.ubuntu.com/infra/ubuntu focal-infra-updates InRelease [7,425 B]
Get:10 http://security.ubuntu.com/ubuntu focal-security/main amd64 DEP-11 Metadata [40.7 kB]
Get:11 http://security.ubuntu.com/ubuntu focal-security/universe amd64 DEP-11 Metadata [66.2 kB]
Get:12 http://security.ubuntu.com/ubuntu focal-security/multiverse amd64 DEP-11 Metadata [2,464 B]
Get:13 http://us.archive.ubuntu.com/ubuntu focal-updates/main i386 Packages [616 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [1,641 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 DEP-11 Metadata [277 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu focal-updates/universe i386 Packages [673 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [909 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu focal-updates/universe amd64 DEP-11 Metadata [391 kB]                                                          
Get:19 http://us.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 DEP-11 Metadata [940 B]                                                         
Get:20 http://us.archive.ubuntu.com/ubuntu focal-backports/main amd64 DEP-11 Metadata [7,992 B]
Get:21 http://us.archive.ubuntu.com/ubuntu focal-backports/universe amd64 DEP-11 Metadata [30.8 kB]
Fetched 5,007 kB in 3s (1,539 kB/s)                            
Reading package lists... Done
Building dependency tree       
Reading state information... Done
5 packages can be upgraded. Run 'apt list --upgradable' to see them.
Listing... Done
alsa-ucm-conf/focal-updates,focal-updates 1.2.2-1ubuntu0.12 all [upgradable from: 1.2.2-1ubuntu0.11]
fwupd-signed/focal-updates 1.27.1ubuntu7+1.2-2~20.04.1 amd64 [upgradable from: 1.27.1ubuntu5+1.5.11-0ubuntu1~20.04.2]
fwupd/focal-updates 1.7.5-3~20.04.1 amd64 [upgradable from: 1.5.11-0ubuntu1~20.04.2]
libfwupd2/focal-updates 1.7.5-3~20.04.1 amd64 [upgradable from: 1.5.11-0ubuntu1~20.04.2]
libjcat1/focal-updates 0.1.4-0ubuntu0.20.04.1 amd64 [upgradable from: 0.1.3-2~ubuntu20.04.1]
Do you want to upgrade now?
y
./updates.sh: line 20: syntax error: unexpected end of file

```

Disregard the error message. When doing the updates, it comes up with get:1 or hit:5, etc. Sometimes it lists 8 or 10, sometime 40+. Questions;
1) Difference between get:# and hit:#.
2) Why such a varied amount of each on each update.

Again, not having an issue at this point, just trying to gain a little knowledge.
Thanks

---

### Post by GhX6GZMB on 2022-03-16
Why so complicated? A script file containing this will do the job:
```
#! /bin/bash
sudo apt update && sudo apt upgrade && sudo apt autoremove
```
And yes, it will ask you if you want to proceed.

I have it stored in /usr/local/sbin/upgrade
I just run
```
sudo upgrade
```
That's it. You can leave out the"autoremove" part if you like that better.

---

### Post by grahammechanical on 2022-03-16
As regards the "Hit" and "Get" part of the question, here is my guess.

Hit = established two way communication with the stated internet address.

Get = downloading files from sub directories at the stated internet address.

I am also guessing that certain repositories such as PPAs and Google do not have sub directories and so there are no "Get" for those internet addresses. 

Regards

---

### Post by coley9225 on 2022-03-17
Thanks for the responses. ml9104, I considered a 1 liner like the 1 you suggest, and putting it in root cron to run nightly,(would have to add the -y flag so as to not need my input). I opted for this script because I can see what is going on, again in the search for a better understanding of how things work, and to catch any errors that may occur. I ran my script this morning and 1 of the upgradable pkgs is firefox. I am postponing the upgrade until later, because I have to close and relaunch 3 instances of the browser.
grahammechanical, that's kind of what I thought. I did a little more research, and from what I can tell is the update compares the package file in your system with the ones in the repository. If your install packages are up-to-date, it returns hit:#, and nothing is downloaded. If your packages are old, then returns get:#, indicating that it is 'getting' the new files. If a package is not found in the repository, retuns ign, meaning it will ignore that 1, without a fatal error. I'm still trying to figure out why sometimes the hit or get is 8 or 10, and sometimes as much as 45. Is the update not running through all the repositories on some updates? The quest for knowledge continues.

---

### Post by CharlesA on 2022-03-17
This doesn't really help you with your original script/update philosophy (as you want logs), but I've been running updates via Ansible for quite a while now and it's been fine for me.

I set it up that way, since I have a handful of different machines running and I didn't feel like I wanted to update everything manually.

This is my playbook, which effectively runs: ***sudo apt update && sudo apt dist-upgrade && sudo apt autoremove***

```

---
- hosts: debian
  remote_user: username
  become: yes
  become_method: sudo
  tasks:
    - name: Update Package Index
      apt:
        update_cache: yes
    - name: Update Packages
      apt:
        upgrade: dist

    - name: Remove Unneeded Packages
      apt:
        autoremove: yes

    - name: Check if reboot is needed
      stat: path=/var/run/reboot-required
      register: reboot_required

    - name: Reboot Required
      command: cat /var/run/reboot-required
      when: reboot_required.stat.exists


```

---

### Post by GhX6GZMB on 2022-03-17
Why not just redirect the output of my "1 liner" into a text file? Then you'll see what happened in the night during your cron job. All that's needed is >

---

### Post by TheFu on 2022-03-17
First there are 500+ different solutions to almost any problem. Which to use is a matter of taste, skill and understanding the repercussions.

1) yes, there are easier ways. Below handles the default and upper/lower case:
```
  read -p "PWD is $(pwd).  Continue? (Y/n) :" yesno
      case $yesno in
          "" | [yY]* ) 
                echo "Continuing ..."
             ;;
          [nN]* ) exit 0;
             ;;
      esac
```

2) 
```
$ some command 2>&1 | tee /tmp/log
```
Learn more about redirection from "The Art of the Command Linux" - a github repo.

3) Is there a way to have the script tell if a reboot is needed.
On Ubuntu systems, a file is created in* /var/run/reboot-needed.* If that file exists, then a reboot is needed. That's basically when libc or a new kernel is installed.

I would warn against 100% automatic patching. I've been burned a few times by broken systems and systems that won't boot post-patching.  OTOH, it is your box. Do what you feel is best.

APT has a history/log in /var/lib/apt/  ... so what is installed, removed, purged are logged there.

I have a script that patches my systems. I manually run it once a week while doing other things.  It waits for my input for each system/apt command. I log everything to the same file each week - this makes seeing what happened should anything bad come to light following the patch much easier. About 2x a year, the log is useful.  The file is part of my backup data too, so I have at least 90 days to review it, but often 180 days.

I would be concerned about trusting the PATH in a script like this. A best practice for all production scripts is to never trust the PATH and to spell out the location of all commands to be run.
apt is wrong.
/usr/bin/apt is correct, for example.

---

### Post by coley9225 on 2022-03-21
Thanks everyone. CharlesA, I've never used ansible, but looks like something I should check out. I glanced at a couple of things, and looks a little out of my range, for now. Thefu, thanks for the pointers. I have studied case a little more, and have rewritten the script to use that method. My next step is to work on a way to have the script check if reboot is needed, and to list the packages that require a reboot to fully upgrade. I have found the files the info is in, just need to incorporate that into the script. Any further advise is always appreciated, not only one this project, but further reading on scripting, methods, etc. Thanks again for the help.

---

### Post by TheFu on 2022-03-21
If you have 5+ systems, learning a little ansible is very useful.  I've found that the library of roles I find online are extremely limited. They usually make a service work, but not really secure enough.  Still, if I need to run a command across 20 systems, ansible is pretty easy.

For for 5 or fewer system, a simple loop over hostnames with some ssh commands can do wonders.  I use this method in my patch script with 'heredocs' to send the commands to be run over the ssh connection.  I do something similar in my backup script too - for the pre/post backup commands on the remote client systems.  Looping over stuff is a very standard practice in scripts.

But again, there are 500+ solutions for these sorts of things.

---

### Post by CharlesA on 2022-03-22
> **coley9225 said:**
> Thanks everyone. CharlesA, I've never used ansible, but looks like something I should check out. I glanced at a couple of things, and looks a little out of my range, for now. Thefu, thanks for the pointers. I have studied case a little more, and have rewritten the script to use that method. My next step is to work on a way to have the script check if reboot is needed, and to list the packages that require a reboot to fully upgrade. I have found the files the info is in, just need to incorporate that into the script. Any further advise is always appreciated, not only one this project, but further reading on scripting, methods, etc. Thanks again for the help.

Sure thing. I've had it handling my updates for 8-10 systems for a while now. I started learning about it from an ebook I found online, but there's plenty of stuff on youtube about it.

> **TheFu said:**
> If you have 5+ systems, learning a little ansible is very useful.  I've found that the library of roles I find online are extremely limited. They usually make a service work, but not really secure enough.  Still, if I need to run a command across 20 systems, ansible is pretty easy.

For for 5 or fewer system, a simple loop over hostnames with some ssh commands can do wonders.  I use this method in my patch script with 'heredocs' to send the commands to be run over the ssh connection.  I do something similar in my backup script too - for the pre/post backup commands on the remote client systems.  Looping over stuff is a very standard practice in scripts.

But again, there are 500+ solutions for these sorts of things.

That's my thing... I've looked at some of the ansible libraries and I end up usually rolling my own thing, but I know that's not something everyone would do.

---

### Post by coley9225 on 2022-03-27
Hello all. I would like to say again how much I appreciate all the help. This is exactly why I use linux exclusively. The community. You folks are always will to give your time to share you knowledge with others. I have taken some of what I learned in this thread, researched other things(arrays, seq, etc.) and improved some of my other scripts. I do have one more question related to updates/upgrades though. I run my script, and it shows all packages are up to date. Same with synaptic, shows no packages to upgrade. However, if I run discover(thee default software manager in lubuntu), it shows some packages upgradable. Why. If the terminal commands don't see anything to upgrade, why is discover finding them. I can't express enough how helpfull you folks are, and how grateful I am for that. With your help, I have learned tons of things, and I have many times that yet to learn, thus the quest for knowledge will be never ending. Thanks so much, again.

---

### Post by CharlesA on 2022-03-27
What updates does it say are pending?

---

### Post by TheFu on 2022-03-27
> **coley9225 said:**
> Hello all. I would like to say again how much I appreciate all the help. This is exactly why I use linux exclusively. The community. You folks are always will to give your time to share you knowledge with others. I have taken some of what I learned in this thread, researched other things(arrays, seq, etc.) and improved some of my other scripts. I do have one more question related to updates/upgrades though. I run my script, and it shows all packages are up to date. Same with synaptic, shows no packages to upgrade. However, if I run discover(thee default software manager in lubuntu), it shows some packages upgradable. Why. If the terminal commands don't see anything to upgrade, why is discover finding them. I can't express enough how helpfull you folks are, and how grateful I am for that. With your help, I have learned tons of things, and I have many times that yet to learn, thus the quest for knowledge will be never ending. Thanks so much, again.

I can only guess it is the difference between APT and other package management systems - like flatpak or snaps?  But I don't know. I don't use GUIs for system management.

Or it could be the difference between a 'full-upgrade' and an 'upgrade' option.  The manpage for apt-get explains those differences.

---

### Post by coley9225 on 2022-03-27
Thanks CharlesA and TheFu. The packages that show upgradable in discover are:
DXVK, Mesa, 4 that start with org.freedesktop.Platform.<and more>.
TheFu is right, they have to do with flatpak packages, in this case, bottles. I had forgotten I install any flatpaks and that apt doesn't upgrade those. Again, google was a big help.

---

