---
title: "Virtualbox Guest Additions fail"
date: 2013-08-26
forum: Virtualisation
---

### Post by unibroker on 2013-08-26
I have had no success with Guest Additions in Ubuntu 12.04.  Last night I decided to go through Software Center and just follow the prompts.  When I try to run the script VBoxLinuxAdditions.run the terminal returns:  ```
[COLOR=#000000][FONT=Arial]Verifying archive integrity... All good.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Uncompressing VirtualBox 4.1.12 Guest Additions for Linux.........[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]VirtualBox Guest Additions installer[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Removing installed version 4.2.16 of VirtualBox Guest Additions...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Removing existing VirtualBox DKMS kernel modules ...done.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Removing existing VirtualBox non-DKMS kernel modules ...done.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Building the VirtualBox Guest Additions kernel modules ...done.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Doing non-kernel setup of the Guest Additions ...done.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Starting the VirtualBox Guest Additions ...fail![/FONT][/COLOR]
[COLOR=#000000][FONT=Arial](modprobe vboxguest failed)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Installing the Window System drivers[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Installing X.Org Server 1.11 modules ...done.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Setting up the Window System to use the Guest Additions ...done.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]You may need to restart the hal service and the Window System (or just restart[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]the guest system) to enable the Guest Additions.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial][/FONT][/COLOR][COLOR=#000000][FONT=Arial]Installing graphics libraries and desktop services components ...done.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

```

I understand from searching that it suggests a problem with the linux kernel headers not matching between host and guest.  I have tried uninstalling and installing linux-headers as well as dkms but still come up with the above failure.  Any ideas would be appreciated.

---

### Post by TheFu on 2013-08-26
Isn't there an install log file?  I seem to remember that. It has the errors.

There is another alternative these days - run KVM and use Spice for the remote desktop if you need a desktop at all. No guest additions needed and you'll be away from Oracle.

---

### Post by unibroker on 2013-08-26
> **TheFu said:**
> Isn't there an install log file?  I seem to remember that. It has the errors.

There is another alternative these days - run KVM and use Spice for the remote desktop if you need a desktop at all. No guest additions needed and you'll be away from Oracle.

Thanks for the response.  The script I ran was packaged with a lot of other executables for various platforms (Windows & Mac).  The only other files contained in that iso that are not platform-specific are runasroot.sh and autorun.sh.  VBox was recommended by a developer that I've had good experience with who I emailed as well.  If all else fails however it's nice to have a fall-back so thanks for the suggestion.

---

### Post by ibjsb4 on 2013-08-26
I have better luck with downloading the latest version from the VirtualBox site.

---

### Post by TheFu on 2013-08-26
> **unibroker said:**
> Thanks for the response.  The script I ran was packaged with a lot of other executables for various platforms (Windows & Mac).  The only other files contained in that iso that are not platform-specific are runasroot.sh and autorun.sh.  VBox was recommended by a developer that I've had good experience with who I emailed as well.  If all else fails however it's nice to have a fall-back so thanks for the suggestion.

That script that you ran created a log file of the installation AND of the failures somewhere in /var/log/....   When I've installed the guest additions, if there were any issues, the location of the log file was displayed in the terminal so I would be able to see what the issue was.  Running the script over will cause the log file location to be displayed again ... assuming it fails.  The errors in that file will tell us the issue, so it can be resolved.

---

### Post by unibroker on 2013-08-26
> **ibjsb4 said:**
> I have better luck with downloading the latest version from the VirtualBox site.

I originally did that but tried the Software Center because I received that error in going direct.

---

### Post by unibroker on 2013-08-26
> **TheFu said:**
> That script that you ran created a log file of the installation AND of the failures somewhere in /var/log/....   When I've installed the guest additions, if there were any issues, the location of the log file was displayed in the terminal so I would be able to see what the issue was.  Running the script over will cause the log file location to be displayed again ... assuming it fails.  The errors in that file will tell us the issue, so it can be resolved.

I ran that as well but didn't include it in the OP because it didn't tell anything additional.

```
[COLOR=#000000][FONT=Arial]cat /var/log/VBoxGuestAdditions.log[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial][/FONT][/COLOR][COLOR=#000000][FONT=Arial]Starting the VirtualBox Guest Additions ...fail![/FONT][/COLOR]
[COLOR=#000000][FONT=Arial](modprobe vboxguest failed)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Starting VirtualBox Guest Addition service VirtualBox Additions module not loaded![/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

```

---

### Post by JKyleOKC on 2013-08-28
What version of VirtualBox are you running? The one in the Ubuntu repositories/Software Center is usually out of date. Your first post indicates that a copy of the Guest Additions for version 4.2 was removed, to be replaced by one for the older version 4.1. It's essential that the version of Guest Additions match the version of VirtualBox itself, and it's usually best to obtain both from the Oracle web site rather than from the Ubuntu repositories, to be sure of getting the current version. Ubuntu freezes the versions of software in the repositories at each version release, and does not update them except when required for security purposes.

You can check /var/log/vbox-install.log to determine what is going wrong in attempting to create the needed kernel modules.

---

### Post by unibroker on 2013-08-28
Thanks for clearing that up for me.  I was under the impression that the kernel for the host OS had to match the kernel for the guest OS.  In any event I have removed all traces of VBox and will start over getting everything from the Oracle website.

---

### Post by JKyleOKC on 2013-08-28
No, there's no relation between the guest version(s) and the host version. I run Xubuntu 12.04 as a guest on one of my Xubuntu 12.04 systems, and Debian 6 as a guest on another. What's important is that all parts of vbox on the same system be at the same revision level, and all copies of Guest Additions in the guests match the vbox version on the host. I've run older Guest Additions installations (by accident) at times, with no ill effects, but it's not advised.

---

### Post by TheFu on 2013-08-29
> **JKyleOKC said:**
> What version of VirtualBox are you running? The one in the Ubuntu repositories/Software Center is usually out of date. Your first post indicates that a copy of the Guest Additions for version 4.2 was removed, to be replaced by one for the older version 4.1. It's essential that the version of Guest Additions match the version of VirtualBox itself, and it's usually best to obtain both from the Oracle web site rather than from the Ubuntu repositories, to be sure of getting the current version. Ubuntu freezes the versions of software in the repositories at each version release, and does not update them except when required for security purposes.

You can check /var/log/vbox-install.log to determine what is going wrong in attempting to create the needed kernel modules.

Running any non-repository software means taking ownership of management, packing, updating that software from not until the machine dies.  For me, **being able to use trusted repositories is the main reason that I use Linux over other OSes.**  

Newer isn't always better.

There are times when we don’t have any choice except to run code from source or binary installers or "someone's" PPA, but those should be avoided as much as possible.

Package safety is a serious issue now that there are targeted attacks against Linux desktops.

---

### Post by JKyleOKC on 2013-08-29
> **TheFu said:**
> Running any non-repository software means taking ownership of management, packing, updating that software from not until the machine dies.  For me, **being able to use trusted repositories is the main reason that I use Linux over other OSes.**  

Newer isn't always better.As a general rule I'm in full agreement with this. However, the vbox repository maintained by Oracle provides a PPA that integrates it into the Ubuntu update system just like the PPAs located at Launchpad, so that it retains all the advantages of the repository system. IMO, the Oracle-run PPA **is** a trusted repository.

And for anything that integrates into the kernel as closely as does a virtualization package, staying with a version that's three years, one major revision, and two minor ones out of date is a huge reliability risk -- and that was the case for those of us who only run LTS versions of *buntu, in the last days of Lucid, were we staying with the official repository versions. It wouldn't matter with most applications, but version 3 of vbox had a few serious problems. The current 4.2 isn't perfect (there's a problem with USB 3.0 support; see their forum for details) but it's much better.

---

