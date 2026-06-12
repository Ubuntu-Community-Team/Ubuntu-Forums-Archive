---
title: "VMWare Workstation Crashes Often"
date: 2007-12-20
forum: Virtualisation
---

### Post by davinci0212 on 2007-12-20
Hello All,

Let me start off by saying I am a very appreciative noob. Searching through this forum has answered a great deal of my questions. 

I am running Gutsy Gibbon and VMWare Workstation 6.0.2 on a ThinkPad T43p. I have a Windows Server 2003 VM team that I use to study for the MCSE. I also have a Windows XP VM that I use when needed (i.e. as a last resort).  


The host OS seems to be fine as long as I only do one or two things (e.g. Firefox & Thunderbird). I feel like I'm working on eggshells here :)


My problem is that when I am multitasking on the host OS and guest OS, the GUI crashes and restarts (like a Ctrl+Alt+Backspace). I log back into GNOME, but I don't see VMWare running as a process. Furthermore, all of my guest OSes have had "the power plug pulled out". 


Can someone help me troubleshoot? I believe that I may find clues to the answer by looking at logs, but I am not sure where the relevant logs are located. 

Many thanks!

---

### Post by Delvien on 2007-12-20
> **davinci0212 said:**
> Hello All,

Let me start off by saying I am a very appreciative noob. Searching through this forum has answered a great deal of my questions. 

I am running Gutsy Gibbon and VMWare Workstation 6.0.2 on a ThinkPad T43p. I have a Windows Server 2003 VM team that I use to study for the MCSE. I also have a Windows XP VM that I use when needed (i.e. as a last resort).  


The host OS seems to be fine as long as I only do one or two things (e.g. Firefox & Thunderbird). I feel like I'm working on eggshells here :)


My problem is that when I am multitasking on the host OS and guest OS, the GUI crashes and restarts (like a Ctrl+Alt+Backspace). I log back into GNOME, but I don't see VMWare running as a process. Furthermore, all of my guest OSes have had "the power plug pulled out". 


Can someone help me troubleshoot? I believe that I may find clues to the answer by looking at logs, but I am not sure where the relevant logs are located. 

Many thanks!


Wouldnt happen to be running hardy would you? 

Also if the above is not true, try running your vmware-config.pl script again, make sure you reset all the settings in there. If there are any errors , post them here. Otherwise I would run check /var/log for errors.

---

### Post by davinci0212 on 2007-12-20
Thanks for the quick response Delvien! I am running Gutsy, as I am not brave enough to work with alpha distros ](*,)

I will rerun vmware-config.pl tonight. Do you know where in /var/log VMWare install details go?

---

### Post by davinci0212 on 2007-12-20
> Also if the above is not true, try running your vmware-config.pl script again, make sure you reset all the settings in there. If there are any errors , post them here. Otherwise I would run check /var/log for errors. 

I re-ran vmware-config.pl without any errors (i.e. that I saw). I can post the script if you'd like. 

I had the crash happen to me again after reinstalling. It happened when I opened a Guest OS and launched full screen. gdm restarted and the vmware process was not running. 

I also experience this error whenever running a guest OS: 

**Unable to query the valid mode lines from your X server; will not try to change host resolution when entering fullscreen mode**. 

Note that this error occured before and after I ran the vmware-config.pl script. 

Anything else I can look at?

---

### Post by davinci0212 on 2007-12-20
> I re-ran vmware-config.pl without any errors (i.e. that I saw). I can post the script if you'd like.

I had the crash happen to me again after reinstalling. It happened when I opened a Guest OS and launched full screen. gdm restarted and the vmware process was not running.

I also experience this error whenever running a guest OS:

Unable to query the valid mode lines from your X server; will not try to change host resolution when entering fullscreen mode.

Note that this error occured before and after I ran the vmware-config.pl script.

Anything else I can look at?

I wasn't able to reproduce the crash in VM, but when I went in and out of full screen on the guest OS, the screen resolution on my host OS went from 1400x1050 to 1280x1024. 

I also had the crash happen once when I went to System | Administration | Screens and Graphics.....maybe this is not related to vmware at all.

---

### Post by HDave on 2008-01-03
I am experiencing this exact same problem on a DELL XPS M1210 laptop running Gutsy.

I can run VMWare (an XP guest) for about an hour or two and then BAM...its EXACTLY like I hit ctrl-alt-backspace.

Didn't think about searching the log files for errors.  Will try again and report back.

---

### Post by Kyairan on 2008-02-11
Me too, VMWare 6.0.2 on Gutsy and it just randomly appears to kill gnome and reloads... Anyone have any ideas?

---

### Post by asif_is_me on 2009-07-02
Hi,
 
Has anyone solved this problem? I am experiencing the same issue on Ubuntu 9.04 and Vmware 6.5. Its very frustrating!

---

### Post by asif_is_me on 2009-07-06
Does anyone have PAE enabled? Could that be a problem?

---

### Post by asif_is_me on 2009-07-08
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/311076](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/311076)

Looks like I have to wait for xorg 1.6.1 to be release :(

---

