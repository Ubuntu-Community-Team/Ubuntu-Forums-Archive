---
title: "[SOLVED] Problem with Headers while Executing a Perl Script"
date: 2007-06-27
forum: Server Platforms
---

### Post by briealeida on 2007-06-27
I have found quite a few people who have been having this issue but their fixes don't work for me.

I'm using a fresh install of Ubuntu 6.06 Server. I installed ubuntu-desktop because what I'm doing is just easier that way. :-(.

So, I downloaded the .tar.gz of vmplayer and tarred it and I'm executing the perl script called vmware-install.pl

Everything was going fine until the script asked me if I had 'make'.
I installed it using apt-get. I then was prompted to do the same thing with 'gcc'.
The trouble started when I was asked to:
What is the location of the directory of C header files that match your running kernel? [/usr/src/linux/include] I hit enter and was told "The path "/usr/src/linux/include" is not an existing directory.

I googled this and found some fixes that I thought would work.
I created the directories and was told "The path "/usr/src/linux/include" is an existing directory, but it does not contain a linux subdirectory as expected. Using apt-get I installed linux-headers-2.6.15-26-server successfully. The headers were not placed into the directory that the perl script was expecting. So I created the linux directory and within it the include directory and manually copied 'linux-headers-2.6.15-26' and 'linux-headers-2.6.15-26-server' to the include directory.

Now when I hit enter when asked for the C headers I get an even worse error: "The path "/usr/src" is a kernel header file directory, but it does not contain the file "linux/version.h" as expected. this can happen if the kernel has never been built, or if you have invoked the "make mrproper" command in your kernel directory. In any case, you may want to rebuild your kernel."

I have not invoked that command and would really like to avoid rebuilding my kernel. Any thoughts or help?

---

### Post by Maxtorm on 2007-06-27
Try installing build-essential rather than each of the required packages individually.  That is,
```
sudo apt-get install build-essential
```
and then re-run the VMWare installer.

---

### Post by briealeida on 2007-06-27
I did issue that command. I did not restart the VMplayer installer. I feel waaayy new for asking this question, but, should just killing the execution of the perl script be OK? It won't create any issues? 

Thanks a million for the response, though! I'm going to go do that now.

---

### Post by Maxtorm on 2007-06-27
Ctrl-C out of the install script should be OK.  As far as I recall, the installer doesn't start any of the "real" work until after you've answered all the "what goes where" questions.

---

### Post by briealeida on 2007-06-27
This is why 'should' is a four letter word.
I am doing what you suggested and being told that a previous installation of VMPlayer is detected. It's attempting to keep the tar4 installer database format and is now uninstalling the tar installation of VMPlayer.

The uninstall completed and I invoked the command again and got the exact same error in the same place:
What is the location of the directory of C header files that match your running kernel [/usr/src/linux/include]

Error:

The path "/usr/src/linux" is an existing directory, but it does not contain a "linux" subdirectory as expected.

---

### Post by Maxtorm on 2007-06-27
I know you said you have already been poking around the forums for solutions, so you've probably already tried this, but if you create a symbolic link as per [http://ubuntuforums.org/showthread.php?t=381984](http://ubuntuforums.org/showthread.php?t=381984) does that fix it?

---

### Post by briealeida on 2007-06-28
Testing that out now. Can't wait to mark this thread as 'Solved'.

---

### Post by briealeida on 2007-06-29
I have another machine that I put Fedora 7 on and attempted a fresh install of VMWare Server and I am having the same issue. Going to try that suggested fix on both machines.

Thanks a bunch!

---

### Post by briealeida on 2007-07-02
So, I've been hearing a lot about Automatix. I had been having this same issue on my home machine and installed Automatix. I got Java, VMPlayer and VMware Server sans issue! I'm installing it on this server now. 
It's listed as a GNOME app and I converted my machine to Kubuntu. Nooo issues. 

Thanks for the help. I'm going to put this to bed and not sweat the Fedora 7 install because I have another machine with F7 that works just fine.

---

### Post by jedispy on 2008-07-07
I'm sorry for posting to an old/dead/solved thread, but I'm having this exact issue, and I followed the information herein.  However I'm getting an additional message saying:> None of the pre-built vmhgfs modules for VMware Tools is suitable for your running kernel.  Do you want this program to try to build the vmhgfs module for your system (you need to have a C compiler installed on your system)? So it's putting back to square one.  Any other thoughts?

Jedispy

**EDIT:** I'd like to state that I'm brand new to Ubuntu, so thank you for your patience.

---

### Post by Maxtorm on 2008-07-07
I assume you answered "yes" to that question and it still bombed on you?

If so, does this help: [http://ubuntuforums.org/showthread.php?p=4091869](http://ubuntuforums.org/showthread.php?p=4091869)  ?

---

