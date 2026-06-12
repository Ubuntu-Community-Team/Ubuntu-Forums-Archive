---
title: "Ubuntu Server on old Celeron Computer"
date: 2012-06-15
forum: Server Platforms
---

### Post by Wiking on 2012-06-15
Can I run an Ubuntu server on a computer with a Celeron processor from early 2001? Max 512mb of RAM.

What other options?

---

### Post by rubylaser on 2012-06-15
Personally, I'd run Debian 32bit server, and you're well within the [minimum specs]("http://www.debian.org/releases/stable/i386/ch03s04.html.en") with no GUI. Ubuntu server will [work great]("https://help.ubuntu.com/community/Installation/SystemRequirements#Ubuntu_Server_.28CLI.29_Installation") too. What do you hope to do with this server?

---

### Post by volkswagner on 2012-06-15
Yes you can.  What type of content would you like to host?

With 512MB RAM you could do a lot with a server install.  There are many folks running home servers on similar hardware.

---

### Post by Wiking on 2012-06-15
I'd like to host media possibly audio and video. It only has a 20 GB hard drive so it would be limited.

I also was thinking of maybe a mail server for my LAN, to play around.

I'm not really quite sure what I want to do with it, I want to try different configurations and play around with the firewall. It's more for experimentation to get to know ubuntu server. If I get a bigger HD I might make it a permanent media server.

Can I access the server console from my main computer? Is it accessable if I'm using W7?

---

### Post by papibe on 2012-06-15
> **Wiking said:**
> I'd like to host media possibly audio and video. It only has a 20 GB hard drive so it would be limited.

I also was thinking of maybe a mail server for my LAN, to play around.
Good stuff. As long as you set it up as a file server (sharing data) instead of streaming, I think it'll be fine.

> **Wiking said:**
> Can I access the server console from my main computer? Is it accessable if I'm using W7?
Sure. Take a look at [Putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/").

Regards.

---

### Post by Wiking on 2012-06-15
Doesn't telnet have weak security?

---

### Post by papibe on 2012-06-16
> **Wiking said:**
> Doesn't telnet have weak security?

Indeed.

The common practice is to use its SSH functionality. I'd recommend installing openssh-server on the server, and using Putty as an ssh client :D

Regards.

---

### Post by Wiking on 2012-06-16
I went ahead and installed ubuntu server on a 500mhz pc.

How would I login from boot if the pc(server) has no keyboard or monitor? Through my main computer using putty? Or do I have to log into the server before any other client can connect? But how can I without keyboard or screen?

So If I wanted to host media I'd install zamba, and share the files using openssh. 

How fast is this setup compared to the windows simple file sharing?

thanks,

---

### Post by lisati on 2012-06-16
As an aside, a couple of years back I managed to get a basic Ubuntu-based webserver working on a 100MHz machine with 64Mb RAM and a 3Gb hard drive, but I wouldn't recommend it.

---

### Post by papibe on 2012-06-16
> **Wiking said:**
> How would I login from boot if the pc(server) has no keyboard or monitor? Through my main computer using putty? Or do I have to log into the server before any other client can connect? But how can I without keyboard or screen?

Login into the computer console using a keyboard and a monitor is not requisite for any service to run, including sharing services or allowing remote ssh connections.

You want to make sure your computer boots properly without a keyboard and a monitor. Sometimes you need to adjust some BIOS parametres. In some rare occasions (unfortunately) you have to have a keyboard connected.

> **Wiking said:**
> So If I wanted to host media I'd install zamba, and share the files using openssh. 

How fast is this setup compared to the windows simple file sharing
Installing ssh-server couldn't be simpler:
```
sudo apt-get install openssh-server
```

As for samba, it requires a few more steps. This is mainly because the lack of GUI, since in Ubuntu Desktop it is as easy as Windows. Here's a very useful [guide]("https://help.ubuntu.com/community/Samba") to setup **[COLOR="Red"]s[/COLOR]**amba (take special attention to the section 'Configuring Samba Servers').

Regards.

---

### Post by bubylou on 2012-06-19
Dont forget to set a static ip for your server so you dont have to guess what it is when trying to remote in over ssh. Also to clear up any confusion. 

Samba - share files
Open SSH - handles ssh connections

---

### Post by Wiking on 2012-06-20
I'm still having to use a keyboard to press ENTER which takes me to the login screen where I type in my credentials. Then after logging I can use patty to see the terminal from a W7 machine. I timed the boot time that way I don't have to use a monitor. 

I was able to setup a samba server and even created and moved some files to the server in windows by accessing \\server\wiking, that was pretty neat.
I then installed smbtree and was able to see workgroups and machines. Is there any way I can see specific folders and files through the terminal?

Can a server have dual purposes such as samba server and a mail server or dedicated only? 

I shut off the server using the terminal, however the HD is unmounts and it doesn't shut off unless I hold the power button.

Thanks,

---

### Post by papibe on 2012-06-20
> **Wiking said:**
> I'm still having to use a keyboard to press ENTER which takes me to the login screen where I type in my credentials. Then after logging I can use patty to see the terminal from a W7 machine. I timed the boot time that way I don't have to use a monitor.

If I understand correctly you are not able to connect remotely using Putty unless you physically log into the server?

> **Wiking said:**
> Can a server have dual purposes such as samba server and a mail server or dedicated only?
You can set up several services, there's no software limitations, only the things that you hardware allow you to run with reasonable performance.

> **Wiking said:**
> I shut off the server using the terminal, however the HD is unmounts and it doesn't shut off unless I hold the power button.
Which command are you using to shutdown the server? Have you try this?
```
sudo poweroff
```
Regards.

---

### Post by Wiking on 2012-06-20
> If I understand correctly you are not able to connect remotely using Putty unless you physically log into the server?

Yes that is correct.

> Which command are you using to shutdown the server? Have you try this?

I tried

sudo shutdown -h now

&

$ sudo shutdown -h 0

and the one you just gave me, same result. Unmounted HD but machine still running.

thanks,

---

### Post by spynappels on 2012-06-20
> **Wiking said:**
> Yes that is correct.



I tried

sudo shutdown -h now

&

$ sudo shutdown -h 0

and the one you just gave me, same result. Unmounted HD but machine still running.

thanks,

Try ```
sudo shutdown -P now 
```

---

### Post by Wiking on 2012-06-20
same thing for that command as well.

---

### Post by papibe on 2012-06-20
By any change you have to press ENTER on the grub menu? Something like [this]("http://2.bp.blogspot.com/-dXMQSfEqj5c/T08jZPAMRhI/AAAAAAAAAKs/zN91GVavd0o/s1600/ubuntu_11.04-grub2.png") picture?

If so, it is not necessary to press enter. If you look closer next time you boot, you should see a count down just below the rectangle. If you wait a few seconds, the computer should boot normally and get you in the login screen. You should be able to connect using Putty without login into the server console.

That countdown can be reduce to zero so you don't have to wait any second more than necessary to boot your server.

Tell us if you need help with reducing that countdown.

Regards.

---

### Post by volkswagner on 2012-06-21
Check dmesg log for BIOS warning.  If your BIOS predates year 2000 you may need to boot grub with force acpi option (acpi=force).

This may help shutdown issue.

---

### Post by Vegan on 2012-06-21
It would pay for itself in no time at all to use a more modern machine. Old machines tend to be very inefficient compared with my modern server.

The 35W sempron I have drops down to << 10W when the load is low. The corporate board I use was expensive but its feature rich.

I have even considered my netbook for a web appliance. The Atom CPU is very attractive for power consumption.

:guitar:

---

### Post by Wiking on 2012-06-24
> 
By any change you have to press ENTER on the grub menu? Something like this picture?

That countdown can be reduce to zero so you don't have to wait any second more than necessary to boot your server.


I was able to reduce it to zero and can now login without keyboard or monitor, great stuff!


> Check dmesg log for BIOS warning. If your BIOS predates year 2000 you may need to boot grub with force acpi option (acpi=force).

This may help shutdown issue.

I looked at the file didn't see anything that said "WARNING" but I really don't know what to look for. Here's the first bit from the dmesg:

 ```
0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000016ff0000 (usable)
[    0.000000]  BIOS-e820: 0000000016ff0000 - 0000000016ff8000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000016ff8000 - 0000000017000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffef0000 - 00000000fff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.3 present.
[    0.000000] DMI: PCCHIPS                          M756LMRT                        /M756LMRT                        , BIOS 062710                           07/15/9
7
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x16ff0 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CBFFF write-protect
[    0.000000]   CC000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FF0000000 write-back
[    0.000000]   1 base 010000000 mask FFC000000 write-back
[    0.000000]   2 base 014000000 mask FFE000000 write-back
[    0.000000]   3 base 016000000 mask FFF000000 write-back
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 base 0F4000000 mask FFC000000 write-combining
[    0.000000] PAT not supported by CPU.
[    0.000000] initial memory mapped : 0 - 02000000
```

I think it says BIOS is from 1997?


And here's what the server prints out during shutdown, I assume this is normal?


```
* Asking all remaining processes to terminate....
* All processes ended within 1 seconds...
* Deconfiguring network interfaces....
* Deactivating swap....
* Unmounting local filesystems...
* Stopping remaining crypto disks....
* Stopiing early crypto disks...
* Will now halt

[1172.549579] System halted.
```

---

### Post by volkswagner on 2012-06-24
To get the machine to power off you likely need to modify your grub boot parameter.

To better search dmesg use less, then search for BIOS, use the "n" key to go to the "next" instance of the searched term.  To search using less start by typing a forward slash.  Your commands will look like the following:

```
less /var/log/dmesg
```

then type:

```
/BIOS
```

use the "n" key to jump to the next occurrence.

```
n
```
```
n
```

Once you reach the end of the document type "q" to quit.

```
q
```

Here is an example of my grub line.

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi=force"
```

---

### Post by Wiking on 2012-06-25
Couldn't find anything that specifically mentioned GRUB, but I found this line.


```
[    0.000000] ACPI: BIOS age (1997) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support

```

---

### Post by volkswagner on 2012-06-25
> **Wiking said:**
> Couldn't find anything that specifically mentioned GRUB, but I found this line.


```
[    0.000000] ACPI: BIOS age (1997) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support

```


The search was for BIOS.  You did great.

Now you will need to modify your grub boot parameter as mentioned above.

Backup your current grub.
```
sudo cp /etc/default/grub /etc/default/grub.bak
```

Edit grub for acpi force:
```
sudo nano /etc/default/grub
```

Change the following line:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
```

Note your line may be slightly different if you have already modified....

Change it by adding the acpi=force inside the quotes.

Like:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi=force"
```

Write changes to file and save:  <ctrl>+O then <ctrl>+X

Now you update grub2:
```
sudo update-grub2
```

Look for any errors, if none then reboot.  If you have errors, post them here.  You can restore your backup then update grub2 if you have errors.

```
sudo reboot
```

Test your shutdown after boot.

---

### Post by Wiking on 2012-06-25
Thanks, everything works flawlessly now.

Thanks to everyone as well for helping out with the other problems.

---

