---
title: "64 bit ubuntu wired &amp; wireless connection problem."
date: 2017-10-13
forum: Ubuntu/Debian BASED
---

### Post by mangleworsel on 2017-10-13
I really need your help! I am trying to use Ubuntu Astronomy  64 but it won't connect to the net. Ubuntu 32 connects with no problem, as do mint and other 32 bit versions of Debian.
The only 64 bit version  I have been able to connect with so far is PC Linux, Full Monty.
I need to set this up so that we can the computer up and running for the local school club.

The computer specification is as follows:-

Motherboard  Gigabyte  GA 970 DS3

Processor AMD Phenom 2, 6 cores.

Memory 64 Meg.

Thank in advance.

Mangleworsel

---

### Post by praseodym on 2017-10-13
Please show these terminal outputs. C/P them into a txt file.
```

uname -a
lspci -nnk
lsusb
lsmod
rfkill list
dpkg -l linux-image-* | grep ii
ifconfig -a
iwconfig
```

---

### Post by mangleworsel on 2017-10-13
I am sorry but I don't understand what you are asking for. I am quite thick when it comes to this sort of thing.

---

### Post by oldos2er on 2017-10-13
That's not an official "flavor" of Ubuntu; thread moved to Other OS, Ubuntu/Debian BASED.

You may want to seek support from [https://sourceforge.net/projects/ubuntu-astronomy-16-04/support?source=navbar](https://sourceforge.net/projects/ubuntu-astronomy-16-04/support?source=navbar)

praseodym is asking you to copy and paste those commands into a terminal, then copy and paste their output into a post here.

---

### Post by mangleworsel on 2017-10-13
> **oldos2er said:**
> That's not an official "flavor" of Ubuntu; thread moved to Other OS, Ubuntu/Debian BASED.

You may want to seek support from [https://sourceforge.net/projects/ubuntu-astronomy-16-04/support?source=navbar](https://sourceforge.net/projects/ubuntu-astronomy-16-04/support?source=navbar)

praseodym is asking you to copy and paste those commands into a terminal, then copy and paste their output into a post here.



Thank you for your help, I have managed to copy the items. sorry if I posted in the wrong place but the distro does say Ubuntu Astronomy 64, so I thought you friendly guys would be able to help, particularly as the same problem happens to all versions of Ubuntu 64 on my system as I mentioned in my cry for help.
Best Regards
Mangleworsel :(

---

### Post by mangleworsel on 2017-10-13
> **praseodym said:**
> Please show these terminal outputs. C/P them into a txt file.
```

uname -a
lspci -nnk
lsusb
lsmod
rfkill list
dpkg -l linux-image-* | grep ii
ifconfig -a
iwconfig
```

Thanks ***[COLOR=#000000][I]praseodym *[/COLOR]**[/I][COLOR=#000000][I]I think I have done it.

Please let me know if I need to supply anything else.

Thanks again
Mangleworsel [/I][/COLOR]

---

### Post by mangleworsel on 2017-10-13
[COLOR=#000000]I really need your help! I am trying to use Ubuntu 64 but it won't connect to the net. Ubuntu 32 connects with no problem, as do mint and other 32 bit versions of Debian.
[/COLOR]
[COLOR=#000000]The only 64 bit version I have been able to connect with so far is PC Linux, Full Monty.
[/COLOR]
[COLOR=#000000]I need to set this up so that we can get the computer up and running for the local school club and let us do some image processing[/COLOR]

[COLOR=#000000]The computer specification is as follows:-[/COLOR]

[COLOR=#000000]Motherboard Gigabyte GA 970 DS3[/COLOR]

[COLOR=#000000]Processor AMD Phenom 2, 6 cores.[/COLOR]

[COLOR=#000000]Memory 64 Meg.[/COLOR]

[COLOR=#000000]Thank in advance.[/COLOR]

[COLOR=#000000]Mangleworsel[/COLOR]

---

### Post by oldos2er on 2017-10-13
Please be patient. It takes time for all our forum members to see your question. "Bumping" your post once or twice a day for visibility is acceptable.

---

### Post by mangleworsel on 2017-10-13
> **oldos2er said:**
> Please be patient. It takes time for all our forum members to see your question. "Bumping" your post once or twice a day for visibility is acceptable.


I was't trying to BUMP my post, I was trying to comply with your last comment and make sure it only referred to the official version of Ubuntu as the problem is the same whichever version of the 64 bit I try but doesn't happen on any version of the 32 bit.

Best Regards
Mangleworsel

---

### Post by praseodym on 2017-10-13
First: You have 2 LAN NICs, drivers are loaded and an IP address is given. Tried both?

Second: Obviously, no WLAN chip is shown. Please show these outputs, too:
```

usb-devices
pccardctl info
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
```

---

### Post by mangleworsel on 2017-10-14
> **praseodym said:**
> First: You have 2 LAN NICs, drivers are loaded and an IP address is given. Tried both? 

Second: Obviously, no WLAN chip is shown. Please show these outputs, too:
```

usb-devices
pccardctl info
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
```

Hi Praseodym,  Yes I have tried both, one of those might be from when I tried to get it working by using a WiFi dongle, (failed)

If it helps I am not worried if the WiFi side doesn't work as it's a desktop and lives about 3 feet from the router.

I have attached the results in text format.

Sorry for the delay in getting back to you but had to go to bed.

Thanks again for your help.
Mangleworsel

---

### Post by praseodym on 2017-10-14
Two NICs with one driver. It is possible to manage both NICs individually by two drivers. Download these files and save them in "Downloads":

[http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.043.02-1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.043.02-1_all.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5.14.04.9_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5.14.04.9_all.deb)

Installation:
```

sudo dpkg -i ~/Downloads/*.deb
```
Blacklist both drivers
```

echo -e "blacklist r8168\nblacklist r8169" | sudo tee /etc/modprobe.d/blacklist-LAN.conf
```
Now load them one by another:
```

gksudo gedit /etc/rc.local
```
and add these lines before "exit 0":
```

modprobe r8168
sleep 5
modprobe r8169
```
Save, close the editor and remove all profiles in the network manager. Reboot and show
```

ifconfig -a
lsmod
```

---

### Post by mangleworsel on 2017-10-14
Hi P[COLOR=#000000]raseodym,[/COLOR]

[COLOR=#000000]Have done the commands as you sent, but I think I might have done something incorrectly.

Not sure how to remove the profiles.

i have attached the print out from the last 2 commands.

Thanks for your patience.

[/COLOR]

---

### Post by praseodym on 2017-10-14
Only one driver is loaded, lets try
```

sudo modprobe -rfv r8169
sudo modprobe -v r8168
sudo modprobe -v r8169
```
Please show the outputs

---

### Post by mangleworsel on 2017-10-14
Hi P[COLOR=#000000]raseodym,[/COLOR]

[COLOR=#000000]Here are the results.[/COLOR]
[COLOR=#000000]Interestingly it now says I am connected, but when I try Firefox it says cannot connect.

Would it be useful to do a clean installation, as there is no valuable data on it (because it can't connect to the net).

I have to go out to the shops so I might take a while to get back to you.

Thanks again
Mangleworsel[/COLOR]

---

### Post by praseodym on 2017-10-15
> ```
modprobe: FATAL: Module r8168 not found in directory /lib/modules/4.4.0-78-generic
```
Obviously, the driver was not installed?!

---

### Post by mangleworsel on 2017-10-15
> **praseodym said:**
> Obviously, the driver was not installed?!

Obviously I must do it all again.

The thing that really surprises me, is this this problem with Reatek has been going on for years, but no one at Ubuntu has done nothing about it.

As I see it :-

1)  All 32 bit versions work well.

2) Up until 2005 the 64 bit version worked well.

3) Other 64 bit Linux distro's that are not based 
     on Debian eg. Fedora and PC Linux don't
      suffer from this problem.

So it seems that there was a change made in the networking part of of the 64 bit of Debian but not in the 32 bit version.

Is it therefore possible to delete the networking part of the 64 bit system and replace it with the 32 bit version.

I know this is way beyond my capabilities but I thought someone with your capabilities might be able to accomplish this.
Or am I talking rubbish? &#128552;

Mangleworsel  &#128301;

---

### Post by praseodym on 2017-10-15
Please show the output of the installation command, just re-run it

---

### Post by mangleworsel on 2017-10-15
Will do.

---

### Post by mangleworsel on 2017-10-15
> **praseodym said:**
> Please show the output of the installation command, just re-run it

Have done and put some extra dialogue bits as well.

---

### Post by praseodym on 2017-10-15
This package is missing:

[https://packages.ubuntu.com/trusty/module-init-tools](https://packages.ubuntu.com/trusty/module-init-tools)

Re-run again

---

### Post by mangleworsel on 2017-10-17
Hi Praseodyn,
I have tried running the commands that you have sent and nothing has changed, still no internet connection.
I really don't understand why! 
The 32 bit version of Ubuntu has no problem and connects from the Live disk.

I t seems to me that this problem has been going on for years and nobody at the helm of Ubuntu has taken it seriously and looked into the problem.

I have found an official Astronomical Distro by Fedora that runs in 64 bit and so am changing to that.

I have loved Ubuntu and used it along with other forks.

Thanks for all your help.

Mangleworsel

---

### Post by praseodym on 2017-10-17
Error messages?
```

dmesg >> dmesg.txt
```
Please upload the file

---

