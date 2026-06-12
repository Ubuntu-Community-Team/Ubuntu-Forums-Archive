---
title: "Samba performance and tcpdump"
date: 2006-10-06
forum: Server Platforms
---

### Post by bd_dali on 2006-10-06
I have performance problems with Samba on Ubuntu 6.06, fully updated. I get < 10 Mbit/sec over a GBit LAN, transferring files from Windows Server 2003 to Samba shares. The Ubuntu server is running on a P4 3.6 GHz with 2 GB RAM, the Win2k3 is running in a virtual machine on VMWare ESX 3.0.1.

I've done some tests and this is what it looks like:

W2k3 Explorer/cmd -> Ubuntu Samba (write) = < 10 Mbit/sec.
Ubuntu Samba (read) -> W2k3 Explorer = ~ 200 Mbit/sec.
Win2k3 FileZilla FTP -> Ubuntu glftpd (write) = ~ 350 Mbit/sec.
Ubuntu glftpd (read) -> Win2k3 FileZilla FTP = ~ 350 Mbit/sec.

As far as I can tell, Samba write performance is the bottleneck. I've set performance options (TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192 IPTOS_LOWDELAY) but without any noticeable difference.

I found a tip about running tcpdump to see where the bottleneck is, but instead a strange thing happened: when I start tcpdump, Samba performance instantly jumps to ~ 200 Mbit/sec! If I stop tcpdump all goes back to "normal", i e < 10 Mbit/sec. It doesn't matter if tcpdump uses promiscuous mode (default) or not (-p). The performance jump is instant, even during an ongoing transfer.

One (really ugly) workaround would be to start tcpdump in the background and redirect output to /dev/null ... :D

The same thing happens if I run tethereal. 

Can anyone explain this?

---

### Post by bd_dali on 2006-11-29
This issue has been resolved! It was a driver problem, I have a Netgear GA311 card (RealTek 8169) and the r8169 driver was the problem. Using the r1000 driver I get 200 Mbit/sec both ways. This applies to Ubuntu 6.10 (and probably 6.06, had the same problem).

In my case all I had to do was to blacklist r8169. I checked to see what r-modules were loaded:

```
lsmod | egrep -i  r[0-9]{4}
```

If both r8169 and r1000 are listed, check to see which one is actually used by the NIC:

```
dmesg | egrep -i  r[0-9]{4}
```

If it's the r8169 module, blacklist it:

```
sudo vi /etc/modprobe.d/blacklist-network
```

Add the following lines:

```
# Prevent r8169.ko from loading and allow r1000.ko to load
blacklist r8169
```

Reboot.

CREDIT: Thanks to Noah Markon for finding the solution to this problem.

---

### Post by bd_dali on 2007-05-31
Updated version for Ubuntu 7.04, which no longer includes a r1000 driver.

First, download headers for the running kernel and create/update link ...

```
sudo apt-get install linux-headers-`uname -r`
cd /usr/src; sudo rm -f linux; sudo ln -s linux-headers-`uname -r` linux
```

Download source code for version 1.05 of RealTek's driver (see attached file below) and place it in /tmp.

Unpack it ...
```
cd /tmp; bunzip2 r1000_v1.05.tar.bz2
```
... and untar the resulting file:
```
tar xvf r1000_v1.05.tar
```

The result should be a directory named r1000_v1.05 with this structure:

r1000_v1.05/
r1000_v1.05/release_note.txt
r1000_v1.05/Makefile
r1000_v1.05/src/
r1000_v1.05/src/r1000.h
r1000_v1.05/src/Makefile
r1000_v1.05/src/Makefile_linux24x
r1000_v1.05/src/r1000_ioctl.c
r1000_v1.05/src/r1000_n.c
r1000_v1.05/README

If you are running Ubuntu 6.10 or older, do this ...
```
cp -p /lib/modules/`uname -r`/kernel/drivers/net/r1000.ko ~
```
A backup copy of the original r1000.ko is placed in your home directory.

Then do this ...
```
cd /tmp/r1000_v1.05
sudo make
```

The kernel module is compiled and installed. To make the added r1000 module usable in Ubuntu 7.04 you have to run this command:
```
sudo depmod -a
```

The next step is to blacklist the r8169.ko module (se previous post) and reboot. It worked for me, Samba performance is restored to the 200-350 Mbit/sec range, instead of low 10's.

Note that the original file was named r1000_v1.05.tgz, but I had to repack it with bunzip because of filename restrictions for attachments to Ubunutforums posts. The content is the same as the original.

Realtek also has a r8169 driver (version 6.001.00) but that's just as slow as the one Ubuntu supplies. I have tried version 1.06 of the r1000 driver, but it won't compile.

---

### Post by robertpolson on 2007-06-03
I did as you said:

# Prevent r8169.ko from loading and allow r1000.ko to load
blacklist r8169


But r8169 still loads and is used as a primary network driver.

Are you sure about what you wrote as I did exactly step by step.

I did restart.

---

### Post by bd_dali on 2007-06-04
Strange. What version of Ubuntu are you using?

---

### Post by robertpolson on 2007-06-04
Ubuntu Feisty 7.04

When I enter this :

> sudo vi /etc/modprobe.d/blacklist-network


I get this:


> E325: ATTENTION
Found a swap file by the name "/etc/modprobe.d/.blacklist-network.swp"
          owned by: root   dated: Sat Jun  2 22:08:20 2007
         file name: /etc/modprobe.d/blacklist-network
          modified: YES
         user name: root   host name: laptopishe
        process ID: 7410
While opening file "/etc/modprobe.d/blacklist-network"

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /etc/modprobe.d/blacklist-net
work"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/etc/modprobe.d/.blacklist-ne
twork.swp"
    to avoid this message.

"/etc/modprobe.d/blacklist-network" [New File]
Press ENTER or type command to continue



the "vi" thing is that a text editor ? Can it be done via gedit or nano text editor ?

---

### Post by bd_dali on 2007-06-04
Yes, vi is a text editor. It looks like you have two sessions of vi editing the same file. Make sure you end all vi sessions and then use whatever text editor you like to make the changes to blacklist-network.

If you don't know how to end all vi sessions, just reboot the computer and remove /etc/modprobe.d/.blacklist-network.swp when the computer has started.

---

### Post by robertpolson on 2007-06-04
I am having some trouble with that vi editor.

Once I start it, do I just paste in 

> # Prevent r8169.ko from loading and allow r1000.ko to load
blacklist r8169

?

After that, how do I save and exit ? 

I know hot to use nano and gedit, but vi is giving me a headache.

---

### Post by bd_dali on 2007-06-04
Try nano instead of vi if you feel more comfortable with that. It doesn't matter what you use as long as it is a text editor.

---

### Post by robertpolson on 2007-06-04
So basically, I should have a text file in the > /etc/modprobe.d/

Named > blacklist-network

Containing: > # Prevent r8169.ko from loading and allow r1000.ko to load
blacklist r8169

Exactly like so ?



So far I have:

For > lsmod | egrep -i  r[0-9]{4} I get: r> 1000                  20492  0 
r8169                  32392  0 

And for: > dmesg | egrep -i  r[0-9]{4}

I get:>  [    4.636000] r8169 Gigabit Ethernet driver 2.2LK loaded
[   30.764000] r8169: eth0: link up
[   30.764000] r8169: eth0: link up

---

### Post by bd_dali on 2007-06-04
Yes, that looks about right.

---

### Post by robertpolson on 2007-06-04
I did all that and what I get is slow booting time instead, you know when ubuntu is booting it says: Loading, please wait. It takes like 40 seconds there for further stuff to continue loading.

And when I boot,

dmesg | egrep -i r[0-9]{4}

> [    3.948000] r8169 Gigabit Ethernet driver 2.2LK loaded
[   85.060000] r8169: eth0: link up
[   85.060000] r8169: eth0: link u

So, it does not get blacklisted.

I have a fresh install of Ubuntu Feisty 7.04

---

### Post by bd_dali on 2007-06-04
Hmmm, that's weird. A blacklisted driver shouldn't load ... can't help you any more, my experience with modprobe is very limited ... :(

---

### Post by robertpolson on 2007-06-04
Shame that I can't get it to work as I highly depend on my network as I have a MediaGate player attached to my computer.

Can you help me to uninstall r1000 completely just to keep the system clean ?

---

### Post by bd_dali on 2007-06-05
Sure, just run these commands:
```
sudo rmmod -f r1000
sudo rm -f /lib/modules/`uname -r`/kernel/drivers/net/r1000.ko
```

That should take care of it. If rmmod complains, run the other command and then reboot the machine.

---

### Post by robertpolson on 2007-06-06
Thank you. It looks like it worked.

---

### Post by sartic on 2007-06-06
I am interested in command line options u used width tcpdump. I have unstable transfer width my lan card few systems width feisty. thx

---

### Post by mathewfer on 2007-06-12
Hi robertpolson,


I am trying to get the Wake-on LAN enabled for your source code.

Do you know how to apply the attached 2 patch files to this source file (r1000_v1.05) and compile the module with WOL enabled on R1000.ko?

It seems it should work according to the below forum;



Thanks for the reply.

mathew

---

### Post by bd_dali on 2007-09-13
I had to reinstall my machine and after installing a vanilla 7.04 all of a sudden I have the same problem; blacklist-network just does not work. I previously had a 6.x install dist-upgraded to 7.04.

I found a workaround here: [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/114171](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/114171)

In short, here's what has to be done to get rid of r8169 (after r1000 has been compiled as described in my earlier posts in this thread):

sudo mv /lib/modules/`uname -r`/kernel/drivers/net/r8169.ko ~/
sudo depmod -a
sudo mv /boot/initrd.img-`uname -r` /boot/initrd.img-`uname -r`.ubuntu
sudo mkinitramfs -o /boot/initrd.img-`uname -r` `uname -r`

sudo gedit /etc/modules
Add "r1000" (without the quotes) at the end of the file.
Reboot.

Not sure what will happen the next time the kernel (and initrd) is updated, the above commands may have to be repeated for every kernel update in the future.

---

### Post by Devilotx on 2007-11-29
Is this working for Gutsy?

I'm getting the same crap speeds as before but the r1000 driver isn't in gutsy anymore.

> **bd_dali said:**
> Updated version for Ubuntu 7.04, which no longer includes a r1000 driver.

First, download headers for the running kernel and create/update link ...

```
sudo apt-get install linux-headers-`uname -r`
cd /usr/src; sudo rm -f linux; sudo ln -s linux-headers-`uname -r` linux
```

Download source code for version 1.05 of RealTek's driver (see attached file below) and place it in /tmp.

Unpack it ...
```
cd /tmp; bunzip2 r1000_v1.05.tar.bz2
```
... and untar the resulting file:
```
tar xvf r1000_v1.05.tar
```

The result should be a directory named r1000_v1.05 with this structure:

r1000_v1.05/
r1000_v1.05/release_note.txt
r1000_v1.05/Makefile
r1000_v1.05/src/
r1000_v1.05/src/r1000.h
r1000_v1.05/src/Makefile
r1000_v1.05/src/Makefile_linux24x
r1000_v1.05/src/r1000_ioctl.c
r1000_v1.05/src/r1000_n.c
r1000_v1.05/README

If you are running Ubuntu 6.10 or older, do this ...
```
cp -p /lib/modules/`uname -r`/kernel/drivers/net/r1000.ko ~
```
A backup copy of the original r1000.ko is placed in your home directory.

Then do this ...
```
cd /tmp/r1000_v1.05
sudo make
```

The kernel module is compiled and installed. To make the added r1000 module usable in Ubuntu 7.04 you have to run this command:
```
sudo depmod -a
```

The next step is to blacklist the r8169.ko module (se previous post) and reboot. It worked for me, Samba performance is restored to the 200-350 Mbit/sec range, instead of low 10's.

Note that the original file was named r1000_v1.05.tgz, but I had to repack it with bunzip because of filename restrictions for attachments to Ubunutforums posts. The content is the same as the original.

Realtek also has a r8169 driver (version 6.001.00) but that's just as slow as the one Ubuntu supplies. I have tried version 1.06 of the r1000 driver, but it won't compile.

---

### Post by bd_dali on 2007-11-30
> **Devilotx said:**
> Is this working for Gutsy?

Don't know, have you tried it?

---

### Post by Devilotx on 2007-11-30
After I posted, I did try it, and it did not work, the system would not pick up the r1000 driver.

I tried the latest driver from Realtek and got nothing better then what I had, even tcpdump didn't speed the transfers, but apt-get update && upgrade did, but only if it actually downloads anything.

I can't have such horrible speeds on my server, the hardware is too new for Dapper, so I'm burning Fedora 8 to give that a go.

I'd rather use ubuntu, but I need my fileserver up, and fast.

---

### Post by bd_dali on 2007-11-30
OK, I actually use CentOS 5 now on my file server so I can't test the r1000 driver on Gutsy. 

No problems with performance on vanilla CentOS though, Fedora should be the same.

---

### Post by greylock on 2007-12-20
Hello
I managed to break my FreeBSD fileserver a few days ago, and decided, while i was spending time fixing it, to switch to a new os, so I installed Ubuntu 7.10, however im experiencing the same problems you guys have with my R8169 PCI nic. (samba=slow, ftp=fast, iperf=fastest).

I first installed new realtek drivers (r8169) from realtek page (6.004.00). same slow speeds.

I then tried to install the older r1000 1.05 driver from this thread, and got as far as compile ok, but the module wouldnt install. If i try to modprobe it it complains about unknown symbol or parameter (dmesg says this unknown symbol is pci_module_init).
I have also tried r1000 v1.07 (from realtek webpage),  (fail to compile)
and r1000 v1.02 (supplied with the nic), (also failed to compile)

So, i would be very helpful if someone could help me install r1000 v1.05 so i could see if this actually helps on my system. 

Regards 
Espen

---

### Post by Gweniviere on 2007-12-27
> **greylock said:**
> Hello
I first installed new realtek drivers (r8169) from realtek page (6.004.00). same slow speeds.

I then tried to install the older r1000 1.05 driver from this thread, and got as far as compile ok, but the module wouldnt install. If i try to modprobe it it complains about unknown symbol or parameter (dmesg says this unknown symbol is pci_module_init).
I have also tried r1000 v1.07 (from realtek webpage),  (fail to compile)
and r1000 v1.02 (supplied with the nic), (also failed to compile)

So, i would be very helpful if someone could help me install r1000 v1.05 so i could see if this actually helps on my system. 

Regards 
Espen

I'm having the same issue. Did you manage to get it to work?

Thanks in advance
Gwen

---

### Post by greylock on 2007-12-28
> **Gweniviere said:**
> I'm having the same issue. Did you manage to get it to work?

Thanks in advance
Gwen

No, I went out looking for another NIC that wasnt realtek based, but I didnt do enough checking, and ended up with another two NIC's thats Realtek based. So eventually I ended up dumping ubuntu for ClarkConnect.

I have better transfer rates there, even still much worse than i do in FTP
(ftp about 25 MBytes/sec and samba about 12MBytes/sec.)
On ubuntu i had 1.5 - 4 MBytes/sec in samba and 35-40MBytes/sec in ftp

It is strange though, because ClarkConnect uses the exact same driver according to lsmod. 
However i think im going to try to get ahold of a  Intel NIC, as they use different chip/driver.

---

### Post by spicyflana on 2008-01-11
i had the same problem, but finally solved it.:

here is how you get your RTL 8169 card to work with decent speeds with gusty (enable r1000 1.05):

AS ROOT (or sudo):

* install sources:
apt-get install linux-source-2.6.22
apt-get install linux-headers-2.6.22-14-server

* get the file r1000_v1.05.tgz, untar it 

* in file src/r1000_n.c edit the line 
[FONT="Courier New"]return pci_module_init (&r1000_pci_driver);   // pci_register_driver [/FONT](drv)
to
[FONT="Courier New"]return pci_register_driver (&r1000_pci_driver);[/FONT]

* make clean modules 

* make install

* depmod -a

* test it: modprobe r1000

****** remove r8169 from booting  *********
as mentioned create file /etc/modprobe.d/blacklist-network
with text:
[FONT="Courier New"]# Prevent r8169.ko from loading and allow r1000.ko to load
blacklist r8169[/FONT]

* make it permanent:
[FONT="Courier New"]update-initramfs -u
[/FONT]

* reboot.

---

### Post by moonlightcheese on 2008-02-15
[http://www.hep.ucl.ac.uk/~ytl/tcpip/linux/txqueuelen/datatag-tcp/](http://www.hep.ucl.ac.uk/~ytl/tcpip/linux/txqueuelen/datatag-tcp/)

---

### Post by greylock on 2008-03-03
> **spicyflana said:**
> i had the same problem, but finally solved it.:

here is how you get your RTL 8169 card to work with decent speeds with gusty (enable r1000 1.05):

AS ROOT (or sudo):

* install sources:
apt-get install linux-source-2.6.22
apt-get install linux-headers-2.6.22-14-server

* get the file r1000_v1.05.tgz, untar it 

* in file src/r1000_n.c edit the line 
[FONT="Courier New"]return pci_module_init (&r1000_pci_driver);   // pci_register_driver [/FONT](drv)
to
[FONT="Courier New"]return pci_register_driver (&r1000_pci_driver);[/FONT]

* make clean modules 

* make install

* depmod -a

* test it: modprobe r1000

****** remove r8169 from booting  *********
as mentioned create file /etc/modprobe.d/blacklist-network
with text:
[FONT="Courier New"]# Prevent r8169.ko from loading and allow r1000.ko to load
blacklist r8169[/FONT]

* make it permanent:
[FONT="Courier New"]update-initramfs -u
[/FONT]

* reboot.

Hi again.
Thanks for the procedure to compile the r1000 driver.

I reinstalled Ubuntu yesterday to check if installation of the r1000 driver helped on the issue.

I was able to compile the r1000 driver using the procedure from spicyflana, however the NIC never used this driver (lsmod shows the mod, modprobe reports no errors, but when i blacklist r8169, the nic is simply not working, networking restart reports the nic as missing.)

I removed the blacklisting of r8169, and did a quick test of samba performance again.
This time i approach 21000 kB/sec (approx 160mbps) wich is better than i have ever gotten in samba. I am now running the supplied r8169 driver from ubuntu.

However this time i am running ubuntu server (before it was desktop), and i did apt-get update, apt-get upgrade before testing. Not sure if i did this last time. So maybe there has been a change in Samba, or in the driver?

---

