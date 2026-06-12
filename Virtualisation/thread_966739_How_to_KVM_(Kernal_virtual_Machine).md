---
title: "How to KVM (Kernal virtual Machine)"
date: 2008-11-01
forum: Virtualisation
---

### Post by bodhi.zazen on 2008-11-01
[SIZE=6][CENTER]How to KVM[/CENTER]
[/SIZE]

[CENTER][IMG]http://kvm.qumranet.com/kvmwiki/Front_Page?action=AttachFile&do=get&target=banner_kvm_forum_2008.jpg[/IMG][/CENTER]


[SIZE=4]**Advantages of KVM**[/SIZE]

1. Open source solution, enough said.
2. Supports 64 bit hosts / guests as well as multiple CPU (I have used 8 virtual CPU without any issue). In general you want to use a max number of virtual CPU = to the number of physical CPU.
3. IMO, KVM is faster then VMWare and Virtual box, although this is obviously a subjective opinion and I kave no hard objective data to back that claim, your experience may vary.

[SIZE=4]**Disadvantages of KVM**[/SIZE]

Perhaps the biggest disadvantage is that the the GUI interface (virt-manager) is not as polished. Personally I use KVM on the command line and write a "simple" script (with all the options) to launch a machine. It takes a little more time, 

Home page : [http://virt-manager.et.redhat.com/](http://virt-manager.et.redhat.com/)

Screen shots : [http://virt-manager.et.redhat.com/screenshots.html](http://virt-manager.et.redhat.com/screenshots.html)


[SIZE=2]_FAQ_[/SIZE]

1. What is KVM ? "Kernel Based Virtual Machine".[INDENT]Home page: [http://kvm.qumranet.com/kvmwiki](http://kvm.qumranet.com/kvmwiki)[/INDENT]2. Will my hardware support KVM ?

To test this open a terminal and enter :

```
egrep --color=auto '(vmx|svm)' /proc/cpuinfo
```If you see [COLOR=red]vmx[/COLOR] or [COLOR=red]svm[/COLOR] in the output your hardware (CPU) will support KVM. If you get no output with that command you are out of luck.

[COLOR=blue]You may need to enable KVM in your BIOS.[/COLOR] I have had to do this on my hardware. Unfortunately it is not always obvious how to do this, you may need to use google, read any manual you may have, or like I did, hunt through your BIOS.


[SIZE=4]**How to install KVM**[/SIZE]

```
sudo apt-get install kvm qemu bridge-utils uml-utilities
```Alternately, you may install from source :
[COLOR=blue]~ Thanks[/COLOR] [redbrain]("http://ubuntuforums.org/member.php?u=560672")


[LIST]
[*][http://kvm.qumranet.com/kvmwiki](http://kvm.qumranet.com/kvmwiki)
[*][http://redbrain.co.uk/?page_id=35](http://redbrain.co.uk/?page_id=35)
[/LIST]


You can then either re-boot or :

```
sudo modprobe kvm
```Then add your user to the kvm group. You may either user the gui or :

```
sudo usermod -G kvm -a <user>
```where "<user>" is the user you wish to add to kvm. You will need to log out and back in for the group membership to take effect.


[SIZE=4]Quick tips[/SIZE]


[SIZE=2]_Make a virtual hard drive_[/SIZE]

use qemu-img

```
qemu-img create -f qcow2 /home/user/Ubuntu.img 5G
/sbin/mkfs.ext3 -F /home/user/Ubuntu.img
```Other options include "raw", see man qemu-img for options.


[SIZE=2]_Use a physical partition_[/SIZE]

Physical partitions are very easy in KVM. Let us assume you wish to use /dev/sda2 for example :

```
sudo chown root.kvm /dev/sda2
```Not start kvm using the physical partition:

```
kvm -hda /dev/sda2 ...
```[SIZE=2]_How to bridge your network card_[/SIZE]

First bring down your network:

```
sudo /etc/init.d/networking stop
```Next, using any editor (gksu gedit) edit /etc/network/interfaces to add a bridge. You may use either static or dhcp :

Static :

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
        address 192.168.0.10
        network 192.168.0.0
        netmask 255.255.255.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off
```DHCP:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet dhcp
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off
```_Note_:

[LIST=1]
[*]change "eth0" to your network card.
[*]This will not work with wireless.
[*]If you are using a firewall on the host, you may have problems. I find Firestarter (which is a GUI front end) will often break with complex networking.
[/LIST]


Now bring your network back up:

```
sudo /etc/init.d/networking start
```[SIZE=2]_Wrapper script for bridged network connections on KVM_[/SIZE]

Use a wrapper script to automatically bring up a tap when you start a new virtual machine.

Save this script in /usr/bin/kvm-bridge

```
#!/usr/bin/env bash
 # script to manage tap interface allocation
 # for linux kernels >= 2.6.18

 # modified by bodhi.zazen from :
 # http://calamari.reverse-dns.net:980/cgi-bin/moin.cgi/FrequentlyAskedQuestions#head-2511814cb92c14dbe1480089c04f83c281117a86
 # http://ubuntuforums.org/showthread.php?t=528046
 # http://www.howtoforge.com/using-kvm-on-ubuntu-gutsy-gibbon

 # set up a tap interface for qemu
 # USERID - uid qemu is being run under.
 USERID=`whoami`

 # generate a random mac address for the qemu nic
 # shell script borrowed from user pheldens @ qemu forum

 ranmac=$(echo -n DE:AD:BE:EF ; for i in `seq 1 2` ; \
 do echo -n `echo ":$RANDOM$RANDOM" | cut -n -c -3` ;done)

 # specify which NIC to use - see qemu.org for others
 # model=r8169
 # Set model based on this how-to
 # http://www.howtoforge.com/using-kvm-on-ubuntu-gutsy-gibbon

 model=rtl8139
 iface=`sudo tunctl -b -u $USERID`

 # start kvm with our parameters
 # echo "Bringing up interface $iface with mac address $ranmac"
 # nohup added to allow kvm to run independent of the terminal
 nohup kvm -net nic,vlan=0,macaddr=$ranmac -net tap,vlan=0,ifname=$iface $@

 # kvm has stopped - no longer using tap interface
 sudo tunctl -d $iface &> /dev/null
```Set ownership and permissions:

```
sudo chown root.kvm /usr/bn/kvm-bridge
sudo chmod 550 /usr/bin/kvm-bridge
```Usage : Use kvm-bridge in place of kvm, for example ;

```
kvm-bridge -cdrom /dev/scd0 -m 512
```[SIZE=2]_KVM console_[/SIZE]

The KVM console allow you to modify your machine as it is running. To get to the console, place your mouse in the KVM screen and hit "ctrl-alt-2".

To see your options type help. You can also use help <command>

Useful commands include :

sendkey ctrl-alt-f1 => changes to the console in the virtual machine.
sendkey ctrl-alt-f7 => changes back to the normal GUI interface in the virtual machine.

ctrl-alt-1 => returns to the KVM interface.


[SIZE=2]_Additional information_[/SIZE]

IMO at this time KVM is best run from the command line. Also, IMO the best soruce of inforation on KVM is "man qemu" (the qemu options all work with kvm).

Useful options include :

-snapshot = run kvm without making changes to your (virtual) hard disk.

-M = Allows you to select a machine (cup) to emulate.

-smp = sets number of CPU.

-m = sets amount or RAM for the virtual machine.

-hda , -hdb, -cdrom = sets hard drive and / or cdrom, you may use a physical partition, hard drive, cdrom, DVD, or a file (Ubuntu.img, ubuntu-desktop.iso) and (I assume) USB devices.

-boot = sets which device to boot from.

-soundhw = set sound card.

-win2k-hack = used with windows 2000 guests.

-std-vga = may increase the resolution of your guests, primarily used by windows guests.

-name = sets a name to your guest.

-nographic, -fullscreen = additional graphic options.

-vnc = start the built in VNC server rather then the standard display. Useful if running kvm without X.

-daemonize = kvm runs detached from your terminal.

-usb = enable usb driver.

-usbdevice = use for usb mouse / tablet etc (on the host).

-tftp , -smb = use built in ftp and samba servers.

-no-apci = Disable ACPI.

-g = set display resolution (see man qemu for details).



Other options : See [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

virsh

GUI options. use virt-manager. IMO virt-manager has come a long way, but not all options are available on the GUI interface.

virt-manager

[FONT=times][SIZE=4]*Peace be with you,*[/SIZE][/FONT][I] 
 
[IMG]http://img381.imageshack.us/img381/4226/xubuntulogo2small0lj.png[/IMG][SIZE=4] [COLOR=navy][FONT=times]bodhi.[/FONT][/COLOR][FONT=times][COLOR=darkgray]zazen[/COLOR][/FONT][/SIZE][/I]

---

### Post by bodhi.zazen on 2008-11-01
From jdong : For servers, without X, use libvirt/virsh as outlined on the Ubuntu wiki :

[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

---

### Post by finite9 on 2008-11-18
Do you know how to create the config files needed for seeing the VM in virt-manager when using pre-existing QEMU images?

I created my image 2 years ago when KVM first made it into the kernel, and I cannot figure out how to get virt-manager to see my guest.  It runs from the command line just fine.

---

### Post by JonesChr on 2008-11-18
How stable is KVM for most of you, and where should I go to get support?

I've been trying to get it working for a couple months now.  And it "works" pretty well, in that I can install and start up an ubuntu guest and use it for a while, but after a few hours or at random times, it freezes up, and the kvm process in the host goes to 100% cpu busy.

I'm not sure if this is some configuration issue, or just some bug in KVM, but I've been playing with configuration options night and day and am starting to run out of options.

I tried posting a message on the gmane kvm developer mailing list but didn't get much response.

What's the right way to get some support?
Below is the message I posted to the KVM development mailer.

Thanks,
Chris

----------------------

I've have setup a couple virtual machines and they work great... for anywhere between 2-24 hours.  But then, for no reason I can determine, they just go 100% busy and stop responding.

My basic setup is:
   Ubuntu 8.10 server running on both host and guests.
   kvm version is the one from the Ubuntu distribution (kvm-72)
   Kernel is Ubuntu 8.10 kernel (2.6.27-7-server)
  
The two VMs are both run like:
     kvm -daemonize \
     -hda Imgs/ndev_root.img \
     -m 1024 -cdrom ISOs/ubuntu-8.10-server-amd64.iso      \
     -vnc :1 -net nic,macaddr=DE:AD:BE:EF:04:04,model=e1000 \
     -net tap,ifname=tap1,script=/home/chris/kvm/qemu-ifup.sh

(With different disk imgs, vnc addresses and macaddrs)

The disk images are raw format:
    qemu-img create -f raw 80G Imgs/ndev_root.img

I've tried running with these options, and in different combos:

    -no-kvm-pit
    -no-kvm-irqchip
    -no-acpi

They don't seem to help much.  If anything, -no-kvm-irqchip seems to cause more troubles.

I tried running with -no-kvm and it won't boot at all.

I also built my own 2.6.27.4 kernel, from kernel.org, and built my own version of kvm-78, but saw the same behavior.

Anyone have any advice how I can resolve these hangs?  When the setup works, it's a beautiful setup and I love kvm.  But with the 100% busy hangs I can't really continue with it.

Thanks!
Chris

---

### Post by bodhi.zazen on 2008-11-18
To be honest KVM has been rock solid for me.

---

### Post by ajmorris on 2008-12-01
hey bodhi, 
very nice guide! :D
May i suggest adding a part for allowing opengl modes from the host, to linux guests via 'vmgl' Im sure many users will like this handy feature ;)


AJ

---

### Post by kairu0 on 2008-12-06
I am trying to enable a VNC password for my guest machines, however it seems to be ignoring the password parameter.

From [http://libvirt.org/formatdomain.html:](http://libvirt.org/formatdomain.html:)

> The password attribute provides a VNC password in clear text.

Can someone provide the proper syntax? The above page doesn't provide the syntax or a single example, so I'm kind of in a bind... :/

---

### Post by yuriz43 on 2008-12-07
I've recently switched from Xen to KVM for my Virtualization platform. Currently I have a few Win2k3-64bit guests installed on LVM partitions. No problems so far.

Honestly, I'm sad that most linux distributions have dropped Xen, but KVM looks promising.

---

### Post by Koraq on 2009-03-24
This doesn't work for me:

qemu-img create -f qcow2 /home/user/Ubuntu.img 5G
/sbin/mkfs.ext3 -F /home/user/Ubuntu.img

Since the image created will be 32k big, and mkfs can't make a fs on such a small area. Substitute "raw" for "qcow2" and it will work.

Anyone actually made it work as written?

Thanks for a very helpful HOWTO otherwise!!

---

### Post by FrankT-Qc on 2009-03-26
finite9 : Just start virt-manager, create a dummy machine (just launch a live cd with a 1k disk...) and go have a look at /etc/libvirt/ ... you'll find interesting stuff, including the xml files describing your machines. 

The format is there : [http://libvirt.org/format.html]("http://libvirt.org/format.html") , an interesting section is "capabilities"

[COLOR="Red"]----EDIT----
Sorry, the page looks empty. If you look at the left, under "XML Format" you have sections that you can click on to get the info
--END EDIT--[/COLOR]

Be aware that you have to restart quite a few services for virt-manager to notice the changes you made in there. I don't remember which, but I would have a look at /etc/init.d/kvm, /etc/init.d/libvirt* /etc/init.d/virt* ... 

Have fun,
François

---

### Post by UranUtan on 2009-04-10
Using Ubuntu Desktop 8.10 x64 (and my CPU has VT-x)

Can you please help for some novice questions

Q1. Is it OK to install KVM using Synaptic Package Manager? There is a kvm package there, how is it different compared to the "sudo apt-get ..." you listed above?

Q2. Is it OK to run KVM on Ubuntu Desktop 8.10 x64? (Just for learning purposes). If yes, after KVM is installed, does it change anything? I mean can I still continue to use Ubuntu Desktop as before?

Q3. You have listed a lot of command line instructions. Is there any GUI front end? to manage KVM server or guest VM image, etc. Similar to "Workstation" products like Virtualbox.
EDIT: I saw you mentioned virt-manager. Is it the only GUI for KVM?

Q4. Is there any utility to convert VM image from VMWare Workstation (VMDK) or from Virtualbox (VDI) into native KVM disk format?

Thanks in advance.

---

### Post by bodhi.zazen on 2009-04-10
> **UranUtan said:**
> Using Ubuntu Desktop 8.10 x64 (and my CPU has VT-x)

Can you please help for some novice questions

Q1. Is it OK to install KVM using Synaptic Package Manager? There is a kvm package there, how is it different compared to the "sudo apt-get ..." you listed above?

Yes, it is the same package. both apt-get and synaptic are front ends to apt.

> Q2. Is it OK to run KVM on Ubuntu Desktop 8.10 x64? (Just for learning purposes). If yes, after KVM is installed, does it change anything? I mean can I still continue to use Ubuntu Desktop as before?

VM will not alter your desktop functionality.

> Q3. You have listed a lot of command line instructions. Is there any GUI front end? to manage KVM server or guest VM image, etc. Similar to "Workstation" products like Virtualbox.
EDIT: I saw you mentioned virt-manager. Is it the only GUI for KVM?

virt-manager. virt manager is not as functional as the front ends for VBox/ VMWare.

do not shy away from the command line, it should not be *that* difficult, lol

> Q4. Is there any utility to convert VM image from VMWare Workstation (VMDK) or from Virtualbox (VDI) into native KVM disk format?

Thanks in advance.

yes, but they are command line tools. google will show you the tools.

---

### Post by UranUtan on 2009-04-11
Hi bodhi.zazen,

Thanks very much for your answers. Now I can start to play with KVM on my Ubuntu Desktop. Will try to learn the command lines.

---

### Post by patryk77 on 2009-07-09
> **bodhi.zazen said:**
> 

```
sudo chown root.kvm /usr/bn/kvm-bridge
sudo chmod 550 /usr/bin/kvm-bridge
```

Thanks for the tutorials. Hopefully one of them will solve my problems.

Only comment I have so far, bin is missing an "i" in "Set ownership and permissions".

---

### Post by juancarlospaco on 2009-07-09
*What's Kernal virtual Machine?*

---

### Post by patryk77 on 2009-07-09
> **juancarlospaco said:**
> *What's Kernal virtual Machine?*

>  Kernel Based Virtual Machine

KVM (for Kernel-based Virtual Machine) is a full virtualization solution for Linux on x86 hardware containing virtualization extensions (Intel VT or AMD-V). It consists of a loadable kernel module, kvm.ko, that provides the core virtualization infrastructure and a processor specific module, kvm-intel.ko or kvm-amd.ko. KVM also requires a modified QEMU although work is underway to get the required changes upstream.

Using KVM, one can run multiple virtual machines running unmodified Linux or Windows images. Each virtual machine has private virtualized hardware: a network card, disk, graphics adapter, etc.

The kernel component of KVM is included in mainline Linux, as of 2.6.20.

KVM is open source software. 

[http://www.linux-kvm.org/page/Main_Page](http://www.linux-kvm.org/page/Main_Page)

---

### Post by kebabbaro on 2009-08-12
Hello,
when I try to boot from my windows seven physical partition qemu stops at 
"booting from hard disk..."
and when i retry  I get this message on the terminal
qemu: could not open disk image /dev/sda1

why is that and how can i fix it?

FYI i give the CLI command:
kvm -hda /dev/sda1

Thank You

---

### Post by bodhi.zazen on 2009-08-13
My guess is that you do not have proper permissions on /dev/sda1

---

### Post by SnakeMedia on 2011-07-25
Hello guys, do not forget!

If you create image from /var/lib/libvirt/images

Please make sure privilege rights!
```
#sudo chmod 777 /var/lib/libvirt/images
```Than it works while you are creating hard disk images of different guest systems :)

Enjoy and happy emulating!

SnakeMedia

---

### Post by prezbedard on 2011-09-01
What is the best way to start for the host? I'm debating whether I install ubuntu server with a gui or not. My concern is how to install windows guests. I'm looking to virtualize several of our windows servers. I only have experience with virtualbox so am not sure how you go about installing a gui guest on a host with none.

Thanks.

---

### Post by bodhi.zazen on 2011-09-01
> **prezbedard said:**
> What is the best way to start for the host? I'm debating whether I install ubuntu server with a gui or not. My concern is how to install windows guests. I'm looking to virtualize several of our windows servers. I only have experience with virtualbox so am not sure how you go about installing a gui guest on a host with none.

Thanks.

You can use a web interface , such as what is offered on Proxmox, that might be your best option.

#2 would be to VNC in from another machine. KVM has a built in VNC server.

---

### Post by Harp32Wil on 2011-09-07
SB
[img]http://www.makemoneymakemoney.net/1.jpg[/img]
[img]http://www.makemoneymakemoney.net/2.jpg[/img]
[img]http://www.makemoneymakemoney.net/3.jpg[/img]

---

