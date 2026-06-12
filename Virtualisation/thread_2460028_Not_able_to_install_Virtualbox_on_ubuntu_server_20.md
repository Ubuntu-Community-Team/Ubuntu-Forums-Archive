---
title: "Not able to install Virtualbox on ubuntu server 20.04"
date: 2021-03-31
forum: Virtualisation
---

### Post by ghezzi-alex on 2021-03-31
[COLOR=#333333][FONT=&amp]Good evening everybody[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]I'm trying to launch a new virtual machine on Ubuntu server to run free NAS.[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]I'm quite sure I miss something but I'm not sure what.[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]this is the error :[/FONT][/COLOR]
```
[COLOR=#2E8B57][FONT=Monaco]Failed to open a session for the virtual machine FreeNAS.[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]The virtual machine 'FreeNAS' has terminated unexpectedly during startup with exit code 1 (0x1).[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]Result Code: NS_ERROR_FAILURE (0x80004005)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Component: MachineWrap[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Interface: IMachine {85632c68-b5bb-4316-a900-5eb28d3413df}[/FONT][/COLOR]
```
The virtual machine 'FreeNAS' has terminated unexpectedly during startup with exit code 1 (0x1).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: MachineWrap
Interface: IMachine {85632c68-b5bb-4316-a900-5eb28d3413df}

[COLOR=#333333][FONT=&amp]The screenshot attached is the error I see just few second after the VM launch. When I click OK the error I posted appear.[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Can you help me to fix the problem?[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]thanks in advance[/FONT][/COLOR][COLOR=#333333][FONT=&amp]
[/FONT][/COLOR]

---

### Post by TheFu on 2021-03-31
Well - freenas was based on BSD last time I checked, not Linux.  Did that change?  Just for clarity, BSD and Linux are completely different OSes. They are not compatible.
Isn't the freeNAS project dead?  

What this means is that virtualbox needs to be using a BSD VM setup, not Linux.

Didn't everyone move to TrueNAS?  [https://www.servethehome.com/freenas-is-dead-long-live-truenas-core/](https://www.servethehome.com/freenas-is-dead-long-live-truenas-core/)

I've not used either. Much prefer rolling my own NAS with Ubuntu Server for 1,000,000x more flexibility, but that does require intermediate-level Linux admin skills.  People who need point-n-click, should probably find some NAS-storage distro or buy a commercial NAS.

---

### Post by ghezzi-alex on 2021-04-01
Thanks for the answer TheFu.
Just to understand better: When I create the VM it asked me which OS I was going to install on the VM. Since I know Free NAS is based on BSD I choose "Other OS" option.
I'm not sure but looks like I missed something during the VirtualBOX installation, or maybe I should install something more...
Maybe you already understood I'm a newby in ubuntu server and I'm close to zero in admin skills :D. I'm trying to get my hands dirty and would like to create my home NAS... Do you think following the right instructions I can roll it out without any third distro?

---

### Post by TheFu on 2021-04-01
> **ghezzi-alex said:**
> Thanks for the answer TheFu.
Just to understand better: When I create the VM it asked me which OS I was going to install on the VM. Since I know Free NAS is based on BSD I choose "Other OS" option.
I'm not sure but looks like I missed something during the VirtualBOX installation, or maybe I should install something more...
Maybe you already understood I'm a newby in ubuntu server and I'm close to zero in admin skills :D. I'm trying to get my hands dirty and would like to create my home NAS... Do you think following the right instructions I can roll it out without any third distro?

I haven't used virtualbox in many years.
I've never used it on a Linux hostOS.

I wrote:
> Much prefer rolling my own NAS with Ubuntu Server for 1,000,000x more flexibility, but that does require intermediate-level Linux admin skills. People who need point-n-click, should probably find some NAS-storage distro or buy a commercial NAS. 

Does that sound like you?  Only you know if it does.  Anyone can accomplish anything they want, if they are dedicated. You can do it, if you want and have purpose.

Rolling your own doesn't have 1 set of instructions and 5 steps.  It is hundreds of choices and if those choices aren't so great, then you'll have to constantly tinker to fix prior mistakes and perhaps correct issues that lost data.  My NAS doesn't have a pretty webGUI. It is maintained mostly through custom, automatic, scripts I've written over decades.  In the last 12 months, 2 HDDs have failed. I lost just a few files which hadn't been backed up since the automatic overnight backup.

Do you know that Ubuntu Server doesn't have a GUI and that for NAS stuff, there isn't any GUI even on Ubuntu Desktop releases? There aren't any GUIs for storage setup or management through RAID or LVM or ZFS.  All those are handled using CLI/shell commands.

You can do whatever you want, regardless of what others say. Background in Unix systems will greatly enhance the chances of success. Windows background isn't really relevant. Things are very different in the Unix world.  Storage management is different across almost all Unixes and almost nothing like Windows.

---

### Post by ghezzi-alex on 2021-04-01
OK,
Sounds really hard...
I'm not ready. I would prefer to use a ready to use distro.
Do someone know what I'm doing wrong with the VM installation?

---

### Post by CelticWarrior on 2021-04-01
You're probably doing nothing wrong. The error is unrelated to the actual VM, it's a problem with Virtualbox itself.

Let's eliminate the usual culprit first: Disable Secure Boot in UEFI. It prevents loading the (unsigned) virtual drivers.
If this isn't the problem then probably you need to reinstall Virtualbox.

---

### Post by ghezzi-alex on 2021-04-02
> **CelticWarrior said:**
> You're probably doing nothing wrong. The error is unrelated to the actual VM, it's a problem with Virtualbox itself.

Let's eliminate the usual culprit first: Disable Secure Boot in UEFI. It prevents loading the (unsigned) virtual drivers.
If this isn't the problem then probably you need to reinstall Virtualbox.
Thanks CelticWarrior
To restart everything I tried to reinstall Virtualbox...
First I tried to remove the old Virtualbox with this command:
```
sudo apt-get purge virtualbox
```
Then starting from the downloaded folder I gave the command:
```
sudo dpkg -i virtualbox*.deb
```
but now it gave me back this error:
```
(Reading database ... 132156 files and directories currently installed.)
Preparing to unpack virtualbox-6.1_6.1.18-142142_Ubuntu_eoan_amd64.deb ...
Unpacking virtualbox-6.1 (6.1.18-142142~Ubuntu~eoan) over (6.1.18-142142~Ubuntu~eoan) ...
dpkg: dependency problems prevent configuration of virtualbox-6.1:
 virtualbox-6.1 depends on python (<< 2.8); however:
  Package python is not installed.
 virtualbox-6.1 depends on python (>= 2.7); however:
  Package python is not installed.
 virtualbox-6.1 depends on python:any (>= 2.6.6-7~); however:


dpkg: error processing package virtualbox-6.1 (--install):
 dependency problems - leaving unconfigured
Processing triggers for systemd (246.6-1ubuntu1) ...
Processing triggers for desktop-file-utils (0.24-1ubuntu4) ...
Processing triggers for mime-support (3.64ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for shared-mime-info (2.0-1) ...
Errors were encountered while processing:
 virtualbox-6.1

```
do you have any suggestion to try to reinstall it?

---

### Post by TheFu on 2021-04-02
There is a choice in the version of virtualbox you install.  One from the Canonical Repos and one from an Oracle PPA.  My understanding is that the Oracle PPA version is better.

So ... you need to completely remove all the Canonical virtualbox stuff first and any left over dependencies.  Get the package names using
```
dpkg -l 'vbox*'
```
and
```
dpkg -l 'virtualbox*'
```
Remove those using 
```
sudo apt purge {insert list of package names from both commands above}
```
Next, get completely updated/patched.
```
sudo apt update
sudo apt full-upgrade
```
Finally, clean up dependencies.
```
sudo apt autoremove
sudo apt autoclean
```
You may need to reboot here.  Check if "/var/run/reboot-needed" exists.  If so, reboot.

Ok, assuming that all went well, it is time to follow the Oracle install instructions.
[https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions) has instructions for adding the PPA to your system. You'll need to CAREFULLY follow those instructions, since they are different for different versions of VirtualBox and different versions of Ubuntu. I don't think you need to download the .deb file. In fact, that is something to avoid.

[https://ubuntuforums.org/showthread.php?t=2458475](https://ubuntuforums.org/showthread.php?t=2458475) is another thread about doing the vbox install.

---

### Post by ghezzi-alex on 2021-04-03
Hi TheFu,
thanks for the suggestion.
Some issue:
When I enter:
```
[COLOR=#000000][FONT=&amp]dpkg -l 'virtualbox*'[/FONT][/COLOR]
```
it shows me:
```

Desired=Unknown/Install/Remove/Purge/Hold| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                           Version                       Architecture Description
+++-==============================-=============================-============-============================================================
rc  virtualbox                     6.1.16-dfsg-6~ubuntu1.20.10.1 amd64        x86 virtualization solution - base binaries
un  virtualbox-2.0                 <none>                        <none>       (no description available)
un  virtualbox-2.1                 <none>                        <none>       (no description available)
un  virtualbox-2.2                 <none>                        <none>       (no description available)
un  virtualbox-3.0                 <none>                        <none>       (no description available)
un  virtualbox-3.1                 <none>                        <none>       (no description available)
un  virtualbox-3.2                 <none>                        <none>       (no description available)
un  virtualbox-4.0                 <none>                        <none>       (no description available)
un  virtualbox-4.1                 <none>                        <none>       (no description available)
un  virtualbox-4.2                 <none>                        <none>       (no description available)
un  virtualbox-4.3                 <none>                        <none>       (no description available)
un  virtualbox-5.0                 <none>                        <none>       (no description available)
un  virtualbox-5.1                 <none>                        <none>       (no description available)
un  virtualbox-5.2                 <none>                        <none>       (no description available)
un  virtualbox-6.0                 <none>                        <none>       (no description available)
iU  virtualbox-6.1                 6.1.18-142142~Ubuntu~eoan     amd64        Oracle VM VirtualBox
ii  virtualbox-dkms                6.1.16-dfsg-6~ubuntu1.20.10.1 amd64        x86 virtualization solution - kernel module sources for dkms
un  virtualbox-guest-additions-iso <none>                        <none>       (no description available)
un  virtualbox-guest-modules       <none>                        <none>       (no description available)
un  virtualbox-modules             <none>                        <none>       (no description available)
un  virtualbox-ose                 <none>                        <none>       (no description available)
rc  virtualbox-qt                  6.1.16-dfsg-6~ubuntu1.20.10.1 amd64        x86 virtualization solution - Qt based user interface
un  virtualbox-source              <none>                        <none>       (no description available)
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
lines 1-28/28 (END)
```
Starting a never ending loop (I left it all night long) without any result.
If I try to close the Terminal windows it show me the attached warning.

Whats going wrong?

---

### Post by TheFu on 2021-04-03
<cntl>-c

---

### Post by ghezzi-alex on 2021-04-03
HI again,
what does it means?
Is this a command to do what?

---

### Post by TheFu on 2021-04-03
> **ghezzi-alex said:**
> HI again,
what does it means?
Is this a command to do what?

Did you try it?  It is one of the most standard key-chords used in a terminal.
[https://en.wikipedia.org/wiki/Control-C](https://en.wikipedia.org/wiki/Control-C)

---

### Post by ghezzi-alex on 2021-04-03
Hi Again,
Ok, I know is a way to copy. But what have I to copy?
And also, where should I past after copy it?
Sorry but really I don't understand...

---

### Post by TheFu on 2021-04-03
Sorry the link wasn't exactly to the command line part that matters.  [https://en.wikipedia.org/wiki/Control-C#In_command-line_environments](https://en.wikipedia.org/wiki/Control-C#In_command-line_environments)  - read further.   It isn't about copy.  It has been around on nearly every computer since the 1970s.  MS-DOS, Windows, Unix, Linux, BSD, all use cntl-c to terminate processes.

---

### Post by ghezzi-alex on 2021-04-03
OK, thanks. But my problem is still to install virtualbox. What have I to do after having terminate the process with cntl-c?

---

### Post by TheFu on 2021-04-03
> **ghezzi-alex said:**
> OK, thanks. But my problem is still to install virtualbox. What have I to do after having terminate the process with cntl-c?

You got side-tracked.  Re-read post #8 above.

---

### Post by ghezzi-alex on 2021-04-04
> [COLOR=#000000]Remove those using[/COLOR]
[COLOR=#000000]Code:
sudo apt purge {insert list of package names from both commands above}[/COLOR]

OK, reading back I stopped at this point for 2 reasons:
1- the command before this, started the never ending loop where I used cntl-c to stop it. But anyway it gives me an output...
2- what should I wrote exactly and with which sintax between the braces? I mean I get all this code with the command before:
```
[COLOR=#000000][FONT=&amp]Desired=Unknown/Install/Remove/Purge/Hold| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend[/FONT][/COLOR]|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                           Version                       Architecture Description
+++-==============================-=============================-============-============================================================
rc  virtualbox                     6.1.16-dfsg-6~ubuntu1.20.10.1 amd64        x86 virtualization solution - base binaries
un  virtualbox-2.0                 <none>                        <none>       (no description available)
un  virtualbox-2.1                 <none>                        <none>       (no description available)
un  virtualbox-2.2                 <none>                        <none>       (no description available)
un  virtualbox-3.0                 <none>                        <none>       (no description available)
un  virtualbox-3.1                 <none>                        <none>       (no description available)
un  virtualbox-3.2                 <none>                        <none>       (no description available)
un  virtualbox-4.0                 <none>                        <none>       (no description available)
un  virtualbox-4.1                 <none>                        <none>       (no description available)
un  virtualbox-4.2                 <none>                        <none>       (no description available)
un  virtualbox-4.3                 <none>                        <none>       (no description available)
un  virtualbox-5.0                 <none>                        <none>       (no description available)
un  virtualbox-5.1                 <none>                        <none>       (no description available)
un  virtualbox-5.2                 <none>                        <none>       (no description available)
un  virtualbox-6.0                 <none>                        <none>       (no description available)
iU  virtualbox-6.1                 6.1.18-142142~Ubuntu~eoan     amd64        Oracle VM VirtualBox
ii  virtualbox-dkms                6.1.16-dfsg-6~ubuntu1.20.10.1 amd64        x86 virtualization solution - kernel module sources for dkms
un  virtualbox-guest-additions-iso <none>                        <none>       (no description available)
un  virtualbox-guest-modules       <none>                        <none>       (no description available)
un  virtualbox-modules             <none>                        <none>       (no description available)
un  virtualbox-ose                 <none>                        <none>       (no description available)
rc  virtualbox-qt                  6.1.16-dfsg-6~ubuntu1.20.10.1 amd64        x86 virtualization solution - Qt based user interface [COLOR=#000000][FONT=&amp]un  virtualbox-source              <none>                        <none>       (no description available)[/FONT][/COLOR]
```
Should I copy and past all? or should I select just some row? or should I "read" something in the middle of the output and wrote it between the braces?

As I told you I'm really new with ubuntu server :(

---

### Post by TheFu on 2021-04-04
I forgot how hard this stuff was when just starting out. We've all been there.  The cntl-c is something that every terminal user "just knows" ... unless they've never watched someone else for a few minutes.  Watching an expert on their computer working in a shell will open your eyes about how powerful the shell can be.  It just takes time. You'll get there, with practice.

It is important to know that just because a command CAN do things, that doesn't mean it is the best tool for the job.  dpkg is great for pulling information, it is a low-level tool for interfacing with the packaging system, but really shouldn't be used for modifying/adding/removing packages.  For that, we use **apt** or **apt-get**.  The APT tools handle some details that dpkg does not.

If you are really new to Ubuntu Server, perhaps running an Ubuntu Desktop flavor (Lubuntu/Xubuntu) would be better to start?  It has a GUI for package management which is more like what you seem to need at this stage of skill.

In the posted output, the first column says whether a package is installed, uninstalled or removed.  Need to uninstall/remove all the packages that are installed or partially installed.

If you do decide to keep using Ubuntu Server, then you'll want to learn about manpages.  Every command has a manpage. These are installed on the system.  The output from dpkg is explained in the dpkg manpage - run **man dpkg** to view it. To understand how manpages are organized - read the manpage on manpages - **man man**.  There is a method to the way the data is presented which is hard for beginners, but becomes extremely useful when we just need a memory tickler to remind us about a specific option.  Manpages try to be organized like a newspaper article.  Summary first, more details as we go deeper.

Back to post #8  ... at this point, it says
> Remove those using
```
sudo apt purge {insert list of package names from both commands above}
```
So the intent is to remove any packages that look like virtualbox-* and vbox* using the **apt purge** command
From the output you've posted, it looks like _virtualbox-6.1 virtualbox-dkms_ are the packages to be purged. The EXACT COMMAND:
```
sudo apt purge virtualbox-6.1 virtualbox-dkms
```
If that goes well, then move back to post #8 and pick up at the next step.

---

### Post by ghezzi-alex on 2021-04-05
Thanks again for all the detailed instructions, now worked perfectly and I think I cleaned up everithig.
Just a question before trying to follow the [COLOR=#000000]Oracle install instructions:
[/COLOR]You wrote:
> **TheFu said:**
> 
You may need to reboot here.  Check if "/var/run/reboot-needed" exists.  If so, reboot.

How can I check if it exist?

---

### Post by TheFu on 2021-04-05
> **ghezzi-alex said:**
> Thanks again for all the detailed instructions, now worked perfectly and I think I cleaned up everithig.
Just a question before trying to follow the [COLOR=#000000]Oracle install instructions:
[/COLOR]You wrote:

How can I check if it exist?

How would you check if a file was in your HOME directory?  Do that, just for the other location. 
There are 500 different ways.

---

### Post by slickymaster on 2021-04-05
Thread moved to **Virtualisation** for a better fit

---

### Post by ghezzi-alex on 2021-04-05
> **TheFu said:**
> How would you check if a file was in your HOME directory?  Do that, just for the other location. 
There are 500 different ways.
I'm sorry but I don't know any of the 500 ways to check...:confused:

---

### Post by TheFu on 2021-04-05
> **ghezzi-alex said:**
> I'm sorry but I don't know any of the 500 ways to check...:confused:

It wasn't a trick question.  Do you have a file manager?  Click on the directories until you are in /var/run/ .  Is there a file inside there named "reboot-needed"?  That's 1 method.  All you are trying to determine is whether that file in that directory exists. Nothing more. It won't have anything inside it.  If there isn't a file with that name - then you don't need to reboot. Simple. Elegant.

So ... there are 500 different ways to figure out if a file exists or not.  Ok - perhaps there are 5 easy ways and all the other ways are less easy, less good. But who am I to tell you how to accomplish something so simple?  I'm not into the GUI thing. I'd just use **ls** and know the answer in 3 seconds, but everyone is different.

Unix systems are built around files. Different files mean specific things and have specific purposes.  There is a Standards document for what files belong where in every Linux system. It if very stable and has been for 20+ yrs.  Google "File System Hierarchy Standards" .... the wikipedia article is more than sufficient 99.9% of the time, but the real document was last updated in 2015 if you need more details. This document doesn't say anything about the "reboot-needed" file, but it does say something about /var/run/ directory and the types of files that should be located there.

You could have just rebooted by now, right?  Generally, rebooting isn't something I do, unless it is needed.  Some people shutdown every night, so if you ran the commands yesterday and shutdown overnight - that the same result.

---

### Post by ghezzi-alex on 2021-04-05
Sorry TheFu, I was thinking about a command line instead of looking in the directory... Now I do, and there were no file called reboot-needed. But Anyway I rebooted it because I had to change the server place.
Now Istarted to follow the Oracle install instructions but after just one step I find a problem:
After I added the
```
[COLOR=#000000]deb [arch=amd64] https://download.virtualbox.org/virtualbox/debian <[/COLOR][COLOR=#000000][FONT=monospace]xenial[/FONT][/COLOR][COLOR=#000000]> contrib[/COLOR]
``` (I replaced 'mydist' with 'xenial' assuming this is the right one for my ubuntu server installation)
but, as the attached screenshot shows, I realize there are 2 line with the same dowload...
Is that normal?

---

### Post by TheFu on 2021-04-05
Duplicate lines aren't good, but I don't think they are terrible.  Only 1 line is needed.

---

### Post by ghezzi-alex on 2021-04-06
OK, I'll try to remove one...
But now I faced another issue.
I'm connecting to the server through Anydesk since is not connected to a monitor. Since yesterday everything was working perfectly and I managed all the suggestion you gave me, from a laptop with Anydesk.
Now, after few minutes of work, the server froze itself without any possibility to intervene.
See attached a screenshot of what I see from the laptop... I tried to close the windows, to open the menù, to close forcing but nothing happened.
The only way to do something, I think, is to shutdown the PC with the power button...
I hope to had explained what's going on.

---

### Post by TheFu on 2021-04-06
I use **ssh** to manage servers and have for 25 yrs.
ssh is how all Unix-like OSes are managed remotely. There are thousands and thousands of how-to guides.  For all the trouble, perhaps just buy a NAS that can do what you want?

Oh, and I really, really, hope you aren't using xenial.  That's 16.04 and suppost ends in a few weeks.  You should start with 20.04 today. That's an LTS, supported until April 2025. Don't use anything newer - until the next LTS is released in April 2022 (next year).

---

### Post by ghezzi-alex on 2021-04-06
> **TheFu said:**
> 
perhaps just buy a NAS that can do what you want?

And were is the fan &#128514;&#128514;&#128514;?
> **TheFu said:**
> 
Oh, and I really, really, hope you aren't using xenial.

If xenial is a GUI no. As suggested in an Italian forum, I installed Tasksel. Is it ok?
Anyway to avoid the frozen problem above, what should I do?

---

### Post by TheFu on 2021-04-06
> **ghezzi-alex said:**
>  
If xenial is a GUI no. As suggested in an Italian forum, I installed Tasksel. Is it ok?
Anyway to avoid the frozen problem above, what should I do?

Xenial --> 16.04.  Nothing more. It doesn't say which flavor of Ubuntu (xubuntu, lubuntu, kubuntu, .... or ubuntu server) it is.  16.04 support ends in a few weeks.  Run 
```
$ lsb_release -a
```
to see which release.

---

### Post by ghezzi-alex on 2021-04-06
This is the output of the command
```

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.10
Release:    20.10
Codename:    groovy

```
looks like is the 20.10 release...
Anyway I restarted the server in the brutal mode &#128561;&#128561;&#128561;, in order to operate in it..
Looking at this link: [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)
I'm not sure which distro I should indicate in the command line
```
[COLOR=#000000]deb [arch=amd64] https://download.virtualbox.org/virtualbox/debian <mydist> contrib[/COLOR]
```
Is it mine [COLOR=#000000][FONT=Verdana]'[/FONT][/COLOR]eoan[COLOR=#000000][FONT=Verdana]', '[/FONT][/COLOR]bionic[COLOR=#000000][FONT=Verdana]', '[/FONT][/COLOR]xenial[COLOR=#000000][FONT=Verdana]', '[/FONT][/COLOR]buster[COLOR=#000000][FONT=Verdana]', '[/FONT][/COLOR]stretch[COLOR=#000000][FONT=Verdana]', or '[/FONT][/COLOR]jessie[COLOR=#000000][FONT=Verdana]' ?
thanks again for your patience [/FONT][/COLOR]

---

### Post by TheFu on 2021-04-06
Your output says "groovy". That doesn't appear to be an available download.

If you are new to linux, running a non-LTS release like 2020.10 is not a great idea. It has support only until July.  Do you plan to install a new OS every 6 months?  If not, run back to 20.04.  LTS releases happen in April of even years. No other time.  They get 5 yrs of support.  All other Ubuntu releases get 6-9 months of support, which means you have to upgrade/migrate to the next release every 6 months, no exceptions.  Not all non-LTS releases are upgrades. They often get shipped with broken stuff - alpha stuff.  17.10 set Wayland as the default display server. That broke all sorts of other tools, badly.  It was ugly.  Since that mistake, Wayland was shipped, but not as the default.  People who want it can choose it, but for people like me where it breaks our workflows, we aren't forced into it.

People who want stability should only run LTS releases.  
```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.2 LTS
Release:        20.04
Codename:       focal
```
If you put in the wrong code-name, you'll get the wrong, incompatible, packages. That will break all sorts of things.

If you point your browser at: [https://download.virtualbox.org/virtualbox/debian/dists/](https://download.virtualbox.org/virtualbox/debian/dists/), then you can see which distros are available.  focal is the latest.

---

### Post by ghezzi-alex on 2021-04-06
I thought my version was the last one. 
So, How can I run back to the 20.04 version?
Do I have to completely reinstall the OS from the begin?
Or i can go back with a command line?
Anyway I still have the problem that the system froze itself...

---

### Post by TheFu on 2021-04-06
Backup any data or settings you can't lose before. **Reinstall.** Wipe everything.  The methods to fall back are quite advanced and require taking steps BEFORE doing an upgrade.  Is there a fall back from Windows10 to WinXP that doesn't lose data?  Nope.  Linux development moves much faster.  What MSFT does in 10 yrs, Linux does annually.

Probably should read [https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle) - this is an overview and short. It has commands to check support status, but really the understanding will prevent making poor choices.

The only time I run non-LTS releases is when my hardware is nearly bleeding edge (less than 1 yr old) and only the last release has the support for that hardware included. Getting 2-yr old hardware is usually the best compromise in price, performance and support.  For laptops, I try to get 2-yr old.  For desktops, I've been custom building after getting burned in the 1990s.  I've wanted to build a new Ryzen system about 18 months. The prices never got where I'd happily pay.  Last fall, I felt the CPU prices would drop in the spring - they haven't.  CPU availability has been tight the entire time, so even the 2 yr old CPUs aren't available at good prices.

---

### Post by ghezzi-alex on 2021-04-07
I've nothing to backup since I've just began to play with Ubuntu Server. So I will reinstall asap

---

### Post by ghezzi-alex on 2021-04-08
I reinstalled the 20.04 version of the server... I also installed the GUI in order to simplify the startup at least.
During the installation I also installed the openSSH server in order to manage remotely the server.
Can you help me to understand how to connect with it remotely from a macbook?
What should I check in order to reach the server from the terminal app?

---

### Post by TheFu on 2021-04-08
> **ghezzi-alex said:**
>  Can you help me to understand how to connect with it remotely from a macbook?

I know very little about macbooks, so no.  Had a Mac for a few weeks about 10 yrs ago. Found it completely frustrating. Best to ask a new question in the Apple-users forum, I'd guess.

---

### Post by ghezzi-alex on 2021-04-08
I don't think you should know macbook to tell me what to write in a terminal in order to reach the server. isn't it? Which parameters should I insert in the client ssh in order to reach the ssh server?

---

### Post by ghezzi-alex on 2021-04-09
Anyway! Now I had reinstalled everything, I tried to follow the instructions here: [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)
After the first step where I added in [COLOR=#000000][FONT=monospace]/etc/apt/sources.list [/FONT][/COLOR]the following line, where i substitute <mydist> with <focal> 
```
[COLOR=#000000]deb [arch=amd64] https://download.virtualbox.org/virtualbox/debian <mydist> contrib[/COLOR]
```

And after downloading and registering as suggested with this command:
```
[COLOR=#000000]wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -[/COLOR]
```

I tryed to launch this command:
```
[COLOR=#000000]sudo apt-get update[/COLOR]
```
But I get this result:
```
Hit:1 http://it.archive.ubuntu.com/ubuntu focal InReleaseHit:2 http://it.archive.ubuntu.com/ubuntu focal-updates InRelease
Hit:3 http://it.archive.ubuntu.com/ubuntu focal-backports InRelease
Hit:4 http://it.archive.ubuntu.com/ubuntu focal-security InRelease
Ign:5 https://download.virtualbox.org/virtualbox/debian <focal> InRelease
Err:6 https://download.virtualbox.org/virtualbox/debian <focal> Release
  404  Not Found [IP: 2.17.140.90 443]
Reading package lists... Done
E: The repository 'https://download.virtualbox.org/virtualbox/debian <focal> Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```
Looks like the release for focal does not exist, isn't it?
How can I solve it?

---

### Post by CelticWarrior on 2021-04-09
Remove the repos, download and install the .deb file according to the instructions for Ubuntu, not Debian.
That will install and add the correct repo.

---

### Post by ghezzi-alex on 2021-04-09
Thanks for the suggestions.
got it but still look like there were an issue:
```
Selecting previously unselected package virtualbox-6.1.(Reading database ... 122361 files and directories currently installed.)
Preparing to unpack virtualbox-6.1_6.1.18-142142_Ubuntu_eoan_amd64 (1).deb ...
Unpacking virtualbox-6.1 (6.1.18-142142~Ubuntu~eoan) ...
Preparing to unpack virtualbox-6.1_6.1.18-142142_Ubuntu_eoan_amd64.deb ...
Unpacking virtualbox-6.1 (6.1.18-142142~Ubuntu~eoan) over (6.1.18-142142~Ubuntu~eoan) ...
More than one copy of package virtualbox-6.1 has been unpacked
 in this run !  Only configuring it once.
dpkg: dependency problems prevent configuration of virtualbox-6.1:
 virtualbox-6.1 depends on libqt5core5a (>= 5.12.2); however:
  Package libqt5core5a is not installed.
 virtualbox-6.1 depends on libqt5gui5 (>= 5.4.0) | libqt5gui5-gles (>= 5.4.0); however:
  Package libqt5gui5 is not installed.
  Package libqt5gui5-gles is not installed.
 virtualbox-6.1 depends on libqt5opengl5 (>= 5.0.2); however:
  Package libqt5opengl5 is not installed.
 virtualbox-6.1 depends on libqt5printsupport5 (>= 5.0.2); however:
  Package libqt5printsupport5 is not installed.
 virtualbox-6.1 depends on libqt5widgets5 (>= 5.12.2); however:
  Package libqt5widgets5 is not installed.
 virtualbox-6.1 depends on libqt5x11extras5 (>= 5.6.0); however:
  Package libqt5x11extras5 is not installed.
 virtualbox-6.1 depends on libsdl1.2debian (>= 1.2.11); however:
  Package libsdl1.2debian is not installed.
 virtualbox-6.1 depends on python (<< 2.8); however:
  Package python is not installed.
 virtualbox-6.1 depends on python (>= 2.7); however:
  Package python is not installed.
 virtualbox-6.1 depends on python:any (>= 2.6.6-7~); however:


dpkg: error processing package virtualbox-6.1 (--install):
 dependency problems - leaving unconfigured
Processing triggers for systemd (245.4-4ubuntu3.6) ...
Processing triggers for desktop-file-utils (0.24-1ubuntu3) ...
Processing triggers for mime-support (3.64ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for shared-mime-info (1.15-1) ...
Errors were encountered while processing:
 virtualbox-6.1

```
Looks like it is not installed...

---

### Post by CelticWarrior on 2021-04-09
Do you have all the normal repos enabled? Please check that first.
And have you been messing with python? The error messages are worrisome, they suggest you have a very broken system.

---

### Post by TheFu on 2021-04-09
```
Ign:5 [https://download.virtualbox.org/virtualbox/debian](https://download.virtualbox.org/virtualbox/debian) <focal> InRelease
Err:6 [https://download.virtualbox.org/virtualbox/debian](https://download.virtualbox.org/virtualbox/debian) <focal> Release
```

I suspect the OP is entering "<focal>", not "focal" for the PPA stuff.

Whenever there is {something} or <something> in some instructions, the intent is that we will not include the {} or <> in our entry.

---

### Post by ghezzi-alex on 2021-04-09
HI All,
I think I'll give up...
Now the system start again to freeze itself without having the opportunity to do anything. The only way is to reboot it in the "brutal" mode... (i.e. push the power button for some second)...
I'll try to install ubuntu desktop, maybe for my basic experience is better...
I'll let you know

---

### Post by CelticWarrior on 2021-04-09
It's quite obvious that you have deeper issues than installing Virtualbox.
Yes, please reinstall and avoid messing with things you don't understand enough of yet. When in doubt ask first here, we're happy to help.

---

### Post by ghezzi-alex on 2021-04-10
Thanks... I'll ask for sure :)

---

### Post by ghezzi-alex on 2021-04-11
Hi Again Guys,
As you know I decided to go back to ubuntu desktop because I think it's easier for me.
Everything went very well since I installed the OS, then Anydesk in order to control it remotely and finally VirtualBOX, because I would like to enjoy myself playing with some different operatin system (FreeNAS above all).
The problem is that I went back to the first post of this thread:
Once I try to start the virtual machine it gives me back an error like I had no installed kernel driver. The exact error is: Kernel driver not installed (rc=-1908). See attached.
Does anybody know how to install those drivers?
Thanks again for the support you are giving to me...

---

### Post by CelticWarrior on 2021-04-11
I would suggest you double-check the Secure Boot status and disable it if enabled.
If it doesn't solve the problem then please run and post back the error messages resulting from the command suggested in your screenshot.

---

### Post by ghezzi-alex on 2021-04-12
Hi CelticWarrior,
as always precious suggestion ;).
Now the VM is working.
Just another question: can I enable again the secure boot? Or should I leave it disable?
And also another small issue I think derived from some screen setting: When I disconnect the screen from the pc where ubuntu is installed, I can't reach it from remote control (anydesk). But if I re-connect the screen it starts to work again without any problem. I hope to have explained the problem. Do you have any suggestion?

---

### Post by CelticWarrior on 2021-04-12
Leave Secure Boot off or alternatively manually sign all the Virtualbox modules/drivers. Considering the latter is not for newbies, it's time consuming and for no tangible benefit, better disable it (Secure Boot is a UEFI feature, absent during the 40 years reign of BIOS).

Regarding Anydesk (or Teamviewer or anything else similar) I'm afraid that's exactly how it rolls: The remote access software needs a display server running in the remote machine and if the remote machine doesn't detect a video output it won't run the display server. There are workarounds, both software and hardware. Hardware, a "dummy dongle", is by far the easiest but it costs money and there isn't that much offer. By software the idea is to create a "dummy output" that can be used by the remote access software.

---

### Post by TheFu on 2021-04-12
use **ssh** or **x2go** for access to headless systems.  ssh is much preferred and is required for x2go to work.

---

### Post by ghezzi-alex on 2021-04-13
> **CelticWarrior said:**
> Leave Secure Boot off or alternatively manually sign all the Virtualbox modules/drivers. Considering the latter is not for newbies, it's time consuming and for no tangible benefit, better disable it (Secure Boot is a UEFI feature, absent during the 40 years reign of BIOS).
Great I'll let it disable.
> **CelticWarrior said:**
> By software the idea is to create a "dummy output" that can be used by the remote access software.
Sounds interesting... I would like to try! Is it hard? where can I find something in order to start to study?

---

