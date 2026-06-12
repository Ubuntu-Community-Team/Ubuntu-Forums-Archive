---
title: "Virtualization Ubuntu 9.04"
date: 2009-04-08
forum: Virtualisation
---

### Post by bodhi.zazen on 2009-04-08
This is a brief thread at this point :twisted:

**[SIZE=4]Ubuntu 9.04 Host[/SIZE]**


[LIST=1]
[*]KVM - Works out of the box for me :twisted: .
[*]Virtualbox - On the [Sun site]("http://www.virtualbox.org/wiki/Linux_Downloads") {PUEL edition} , Virtualbox 2.2.0 is available for Ubuntu 9.04. Works fine :twisted: .
[*]Vmware Server 1.0.9 - As usual VMWare takes a little effort :(

Basically follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=966070") .

Extract the vmware archive. This will extract to a directory "vmware-server-distrib"

**DO NOT** run the install script (vmware-install.pl) ... yet 

First download the patch for the 2.6.27 kernel (works on the 2.6.28 kernel as well) from [here]("http://www.insecure.ws/warehouse/vmware-update-2.6.27-5.5.7-2.tar.gz"). Extract the archive (vmware-update-2.6.27-5.5.7-2) and save it inside the "vmware-server-distrib" directoy.

Now (assuming all this is in your home directory)

```
cd ~/vmware-server-distrib/vmware-update-2.6.27-5.5.7-2
```and run the "runme.pl" as root.

```
sudo ./runme.pl
```the "runme.pl" will call the installer and from there continue with the installation, including entering a serial number and configuring your keyboard. :twisted:
[/LIST]
**VMWare mouse thread** [http://ubuntuforums.org/showthread.php?t=1126696](http://ubuntuforums.org/showthread.php?t=1126696)


**[SIZE=4]Ubuntu 9.04 Guest[/SIZE]**


[LIST=1]
[*]KVM - No problems. I have been running 9.04 as a guest in KVM since Alpha 2.
[*]VirtualBox - Installing the VirtualBox Additions is a bit tricky. You have to manually extract the installer scripts and manually modify them. Once you do that they work fine. For instructions see [this blog]("http://www.ubuntu-inside.me/2009/03/howto-fix-virtualbox-guest-additions.html") for installation instructions. Otherwise I have also been running 9.04 as a guest in VirtualBox since the first Alpha.[URL="http://this%20thread"]
[/URL]
[*]VMWare - I have not yet tried installing the VMWare Toolbox on a 9.04 guest.
[/LIST]


Enjoy - I will try to give more detailed instructions after the final release ;)

---

### Post by rcdeacon on 2009-04-10
I am having trouble getting usb to work in 9.04. I did some searching but have not come up with the answer. My usb devices ARE seen in virtualbox but are grayed out. I'm sure this is a simple problem but I if someone can steer me in the right direction I would sincerely appreciate it.

---

### Post by rcdeacon on 2009-04-10
The problem is SOLVED. In the process of installing other programs I had to do a reboot and upon reboot all is well. Sorry for the false alarm.

---

### Post by juancarlospaco on 2009-04-10
Whats Virutalization ...?

---

### Post by bodhi.zazen on 2009-04-10
> **juancarlospaco said:**
> Whats Virutalization ...?

VMware, virtualbox, kvm, qemu, etc

see the other sticky ;)

---

### Post by -Rick- on 2009-04-11
> **juancarlospaco said:**
> Whats Virutalization ...?
A typo for Virtualization ;)

---

### Post by sabi on 2009-04-13
I have tried numerous times to install vmware tools in jaunty 9.04, latest daily build (guest in vmware workstation, 6.5.2, on 8.10 host). The install produces errors in one section as follows:

/tmp/vmware-config0/vmhgfs-only/page.c:867: error: implicit declaration of function ‘__grab_cache_page’
/tmp/vmware-config0/vmhgfs-only/page.c:867: warning: assignment makes pointer from integer without a cast
make[2]: *** [/tmp/vmware-config0/vmhgfs-only/page.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmhgfs-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [vmhgfs.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmhgfs-only'
Unable to build the vmhgfs module.

All other modules build correctly.

End result is the mouse cursor is trapped inside the guest window (only manual release using ctrl+alt). Also, after the install, must run vmware-user for other options such as copy/paste to work correctly.

Anyone have a fix/workaround for the trapped mouse cursor?

Thanks,
sabi

---

### Post by CloudFX on 2009-04-14
The link for VirtualBox doesn't have any Jaunty downloads, are the Intrepid ones supposed to work fine?

EDIT: Ah, didn't read the second part after Intrepid.

---

### Post by TJet1.8 on 2009-04-16
> **sabi said:**
> Anyone have a fix/workaround for the trapped mouse cursor?


They just release a fix for the cursor today.
Run an Update and all should be good.
Worked for me

---

### Post by RealG187 on 2009-04-23
Can anyone go and change the theme, last time I tried using appearance in a VMWare VM the system would go really slow! But that was on 8.04 or 8.10, can someone try in 9.04?

---

### Post by axel206 on 2009-04-24
I had a little problem with Ubuntu 9.04 guest on ArchLinux host. Mouse pointer integration wasn't working altough I had installed Guest Additions. Here is the solution.

[How to fix mouse pointer integration in Ubuntu 9.04 installed on VirtualBox](http://www.my-guides.net/en/content/view/157/26/)

---

### Post by BryanPearson on 2009-04-24
> **sabi said:**
> 
make: Leaving directory `/tmp/vmware-config0/vmhgfs-only'
Unable to build the vmhgfs module.

All other modules build correctly.

End result is the mouse cursor is trapped inside the guest window (only manual release using ctrl+alt). Also, after the install, must run vmware-user for other options such as copy/paste to work correctly.

Anyone have a fix/workaround for the trapped mouse cursor?

Thanks,
sabi

The vmhgfs module is only responsible for shared folders.  I quote from the config script itself, "The filesystem driver (vmhgfs module) is used only for the shared folder feature.  the rest of the software provided by VMware tools is designed to work independently of this feature."

 I always say no to building it, and UNTIL NOW I have gotten mouse support.  I too have captive mouse cursor issues with this Ubuntu release and version 6.5.2 build-156735 of VMware Workstation.

  Oddly enough, cut and paste works, and drag and drop works as well.  Just this odd inability to move the mouse outside the bounds of the VM window without hitting Ctrl+Alt.

---

### Post by axel206 on 2009-04-24
BryanPearson and sabi

Why don't you try the guide I posted above? Although it mentions VirtualBox it could work for VMWare as well. All you have to do is add some lines in xorg.conf. Make a post here if it works. Here is the link again.

[How to fix mouse pointer integration in Ubuntu 9.04 installed on VirtualBox](http://www.my-guides.net/en/content/view/157/26/)

---

### Post by bodhi.zazen on 2009-04-24
The short answer is there is no "vboxmouse" in vmware. you get that driver when you install the vbox additions :lolflag:

The longer answer is VMWare uses a VMWare Toolbox and not VBoxAdditions.

---

### Post by BryanPearson on 2009-04-24
I tried your guide, and it didn't work for me with VMware.  I did find a fix from sabi, though:

[http://ubuntuforums.org/showpost.php?p=7088527&postcount=19](http://ubuntuforums.org/showpost.php?p=7088527&postcount=19)

---

### Post by Hatfield on 2009-04-24
Can we still install the VirtualBox 2.1.4 PUEL version in Jaunty using this HowTo(for Intrepid)?
[http://ubuntuforums.org/showthread.php?t=1074160](http://ubuntuforums.org/showthread.php?t=1074160)

Seems so since Sun has Intrepid and Jaunty using the same download on their Linux Downloads page.
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Or do we have to replace "intrepid" with "jaunty" in the Software Sources APT line?

---

### Post by Schorschi on 2009-04-24
Any one compile KVM-85?  Get it working?  On 9.04?

---

### Post by starfry on 2009-04-25
What about openvz ?

just tried to install linux-openvz but it isn't in the Jaunty repos. I'm going back to hardy for now.

---

### Post by bodhi.zazen on 2009-04-25
> **starfry said:**
> What about openvz ?

just tried to install linux-openvz but it isn't in the Jaunty repos. I'm going back to hardy for now.

The openvz kernel patch is again kernel dependent. Right now Ubuntu supports openvz only on LTS, which means 8.04 . This is true in all distors (there is lag with openvz in Fedora, Centos, and Debian).

The other option is to compile your own kernel, you would need to get instructions on the openvz site.

---

### Post by starfry on 2009-04-25
I suspected that was the answer. I was actually planning on running Hardy but I could not get it to install on this new system of mine because it is 100% SATA and the Hardy installers can't cope with it. That's the only reason I installed Jaunty.

Either I find a way to install Hardy or I compile the kernel (I've done it loads of times). I looked at [http://wiki.openvz.org/Download/kernel](http://wiki.openvz.org/Download/kernel) but I can't see a 2.8.28 kernel there.

---

### Post by she11c0de on 2009-04-26
> **Schorschi said:**
> Any one compile KVM-85?  Get it working?  On 9.04?
Yes, i get is work with linux distro, but my previous installed WindowsXP can't work, whatever KVM-85 or ubuntu default KVM-84

---

### Post by coldReactive on 2009-04-27
I just would like a deb on getdeb of qemu for Ubuntu 9.04 amd64, since there is one for Intrepid of 0.10, but the repos for Ubuntu only have qemu 0.5

---

### Post by CloudFX on 2009-04-27
I receive the following error when trying to install VirtualBox in Jaunty from the provided link:

```
VirtualBox will not start until this problem is fixed. Please consult /var/log/vbox-install.log to find out why the kernel module does not compile. Most probably the kernel sources were not found. Install them (the package name is probably linux-headers-<version> whereby <version> can be determined by 'uname -r') and execute

  /etc/init.d/vboxdrv setup

as root.
```

uname -r shows 2.6.27-7-generic, but linux-headers-2.6.27-7-generic does not exist in Jaunty.

What do I do to fix this?

---

### Post by tchoklat on 2009-04-27
Having trouble with mouse integration .Tried Sabi's fix, still nothing. Any one got a new way to release the mouse? (9.04 inside PCLOS)

Tony

---

### Post by Suncoaster on 2009-04-28
Having problems with USB and file sharing.  I can see the USB devices but they are greyed out so I cannot select them.  The same for shared folders if I select 'Devices" on the menu and then "Shared Folders" the share is visible, but it is not available from Windows Explorer.

I have this all working in 8.04 but not in 9.04.  The only configuration suggestion in all the Howtos I have not implemented is the modification to **/etc/init.d/mountdevsubfs.sh** as there is no commented code block in the 9.04 version.

Do I need to insert this code block or is there something else I can do.

I hope someone out there can help me.

---

### Post by Suncoaster on 2009-04-28
**OOPS**, sorry guys the problem has disappeared.  I rebooted several times while trying to solve this issue, then, when I turned my computer on this morning everything worked.

I think my computer hates me!!!

Sorry for bothering you guys.

---

### Post by sunnyliu2005 on 2009-05-01
I think that it is solved by this post:
[http://bbs.archlinux.org/viewtopic.php?pid=485477#p485477]("http://bbs.archlinux.org/viewtopic.php?pid=485477#p485477")

**Its message are here:**
open-vm-tools-2009.01.21-142982.patch :
Code:

diff -aur open-vm-tools-2009.01.21-142982.pristine/modules/linux/vmhgfs/page.c open-vm-tools-2009.01.21-142982.new/modules/linux/vmhgfs/page.c
--- open-vm-tools-2009.01.21-142982.pristine/modules/linux/vmhgfs/page.c    2009-01-21 00:03:01.000000000 -0800
+++ open-vm-tools-2009.01.21-142982.new/modules/linux/vmhgfs/page.c    2009-01-22 06:51:20.000000000 -0800
@@ -864,7 +864,9 @@
    unsigned pageTo = pos + len;
    struct page *page;
 
-   page = __grab_cache_page(mapping, index);
+//   change this, because of problems with 2.6.28 linux kernel
+//   page = __grab_cache_page(mapping, index);
+   page = grab_cache_page_write_begin(mapping, index, flags);
    if (page == NULL) {
       return -ENOMEM;
    }

---

### Post by sudhanshu_goswami on 2009-05-06
Mouse started working seamlessly between the host and the guest after I installed this in the guest:

> sudo apt-get install xserver-xorg-input-vmmouse

and rebooted the guest. Copy/Paste started working after I ran this:

> vmware-user

- Sudhanshu

---

### Post by juancarlospaco on 2009-05-07
Any have been installed enomalism2 on Jaunty sucessfully ...?
[I]
if yes, post how to thanks...[/I]

---

### Post by juancarlospaco on 2009-05-08
*so... anyone ?*

---

### Post by tkoco on 2009-05-16
[quote=bodhi.zazen;7039466]This is a brief thread at this point :twisted:

**[SIZE=4]Ubuntu 9.04 Host[/SIZE]**


[LIST=1]
[*]KVM - Works out of the box for me :twisted: .
[*]Virtualbox - On the [Sun site]("http://www.virtualbox.org/wiki/Linux_Downloads") {PUEL edition} , Virtualbox 2.2.0 is available for Ubuntu 9.04. Works fine :twisted: .
[/LIST]
....
....

I agree. VirtualBox works fine. I'm currently running Jaunty (guest) on top of Jaunty (host). The host is the 64 bit version and the guest is the 32 bit version. Just one quirk with this setup. VirtualBox will get extremely sluggish if the host machine is not running PulseAudio. 

Read here for more infomation [http://ubuntuforums.org/showthread.php?t=1162742](http://ubuntuforums.org/showthread.php?t=1162742)


Hopefully, this information will help someone fix a sluggish issue with VirtualBox.

---

### Post by coldReactive on 2009-05-16
I have a sluggish virtual box in comparison to OSE, but I can't use what you mentioned due to the fact that the guest is Windows.

---

### Post by tkoco on 2009-05-16
> **tkoco said:**
> [quote=bodhi.zazen;7039466]This is a brief thread at this point :twisted:

**[SIZE=4]Ubuntu 9.04 Host[/SIZE]**


[LIST=1]
[*]KVM - Works out of the box for me :twisted: .
[*]Virtualbox - On the [Sun site]("http://www.virtualbox.org/wiki/Linux_Downloads") {PUEL edition} , Virtualbox 2.2.0 is available for Ubuntu 9.04. Works fine :twisted: .
[/LIST]
....
....

I agree. VirtualBox works fine. I'm currently running Jaunty (guest) on top of Jaunty (host). The host is the ......

If you do not need audio, an alternative fix is to leave the audio option turned off for the guest machine.

---

### Post by bodhi.zazen on 2009-05-16
Thanks for the tip. Personally I do not use audio in the guests.

---

### Post by tkoco on 2009-05-16
> **coldReactive said:**
> I have a sluggish virtual box in comparison to OSE, but I can't use what you mentioned due to the fact that the guest is Windows.

Try maxing out the video memory for the guest machine. During my investigations of the audio issue, I found that the amount of video memory can cause the sluggishness as well if the value is too low.

---

### Post by coldReactive on 2009-05-16
I figured that was the case, because adding more regular RAM didn't do the trick.

---

### Post by Michael85233 on 2009-05-19
Dumb question. Running VMware Workstation 6.5 on a Ubuntu 9.04 desktop. I have a VM that needs promiscuous on /dev/vmnet0. Well workstation installs as root so /dev/vmnet0 is owned by root with a group of root. I can do a sudo chown and fix that and it all works until the next time I restart Ubunto. It goes back to root then. Any ideas?

---

### Post by codywohlers on 2009-05-21
> **sudhanshu_goswami said:**
> Mouse started working seamlessly between the host and the guest after I installed this in the guest:

> sudo apt-get install xserver-xorg-input-vmmouse
- Sudhanshu

Thanks alot!  I was wondering why the mouse wouldn't work fully upon a fresh install of 9.04-desktop-amd64 with vm-workstation 6.5.2

---

### Post by RealG187 on 2009-05-22
i am having major issues in vmware, for starters as you may notice shift doesn't work so i cannot make capital letters
[http://ubuntuforums.org/showthread.php?t=1167432](http://ubuntuforums.org/showthread.php?t=1167432)

---

### Post by bodhi.zazen on 2009-05-23
> **RealG187 said:**
> i am having major issues in vmware, for starters as you may notice shift doesn't work so i cannot make capital letters
[http://ubuntuforums.org/showthread.php?t=1167432](http://ubuntuforums.org/showthread.php?t=1167432)

Yes, moving forward, for me, vmware is more hassle then it is worth.

Don't get me wrong, 1.x is an awesome product, not as happy with 2.x.

KVM and virtualbox are both easier to install and maintain.

If you need to file share, learn a network protocol (ssh (scp) , samba, ftp, nfs, http) or use a flash drive.

---

### Post by protargol on 2009-05-23
I'm having trouble getting VMware to work properly in Jaunty.  I (mostly) followed the instructions from the [first post]("http://ubuntuforums.org/showpost.php?p=7039466&postcount=1"), aside from running the vmware-install.pl before I found out that there'd be a problem...  

I got it to open up and run, but as soon as I try to power on my first virtual machine, it gives my my first error as a gui:

```
Version mismatch with vmmon module: expecting 168.0, got 161.0.
You have an incorrect version of the `vmmon' kernel module.
Try reinstalling VMware Workstation.
```

I'm lost as to how to fix this.  I'm (trying to) run VMware 6.0.4 Workstation.

As another aside, I have serial number through work for 6.0.4.  Will that number activate 6.5 or whatever the version is that people have working on Jaunty?  

Thanks a bunch

---

### Post by RealG187 on 2009-05-24
> **bodhi.zazen said:**
> Yes, moving forward, for me, vmware is more hassle then it is worth.

Don't get me wrong, 1.x is an awesome product, not as happy with 2.x.

KVM and virtualbox are both easier to install and maintain.

If you need to file share, learn a network protocol (ssh (scp) , samba, ftp, nfs, http) or use a flash drive.

VMware was a dream in 8.04 and I can't leave it, my VM's are already in VMware format, I tried converting one to vortual box but it hangs on boot...

---

### Post by lunatiko on 2009-06-04
hi everyone this my first post.

im using ubuntu 9.04 and im trying to install vmware esx 3.1 i download the patch, and run the installer; but always i got the same error:

What is the location of the directory of C header files that match your running 
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.28-11/arch/x86/include

The path "/usr/src/linux-headers-2.6.28-11/arch/x86/include" is an existing 
directory, but it does not contain at least one of these directories "linux", 
"asm", "net" as expected.

i already google and always the same, plz help ill appriciate.


now i got
The path "/lib/modules/2.6.28-11-generic/build/include" is a kernel header file 
directory, but it does not contain the file "asm/page.h" as expected.

What is the location of the directory of C header files that match your running 
kernel? [/usr/src/linux/include] 

google ...



thx:D

---

### Post by techfanboy81 on 2009-06-06
I have just download the patch and ready to install hopefully works fine for me.

---

### Post by RealG187 on 2009-06-07
[http://ubuntuforums.org/showthread.php?p=7414378#post7414378](http://ubuntuforums.org/showthread.php?p=7414378#post7414378)

> Okay I have decided to stick with VMWare. Virtualbox opened up more problems which I don't need.

I just need to get a bridged network working again on VMware and stop to SOB from stealing my modifier keys. Once I get VMWare working on 9.04 I will never update again. I had 8.10 and everything was perfect, updating to 9.04 was the biggest mistake of my life!

Can someone help me with my VMWare woe's please?

---

### Post by bodhi.zazen on 2009-06-07
> **RealG187 said:**
> []("http://ubuntuforums.org/showthread.php?p=7414378#post7414378")Can someone help me with my VMWare woe's please?

You basically have two problems :

1. VMWare does not support Ubuntu 9.04. So I suggest you downgrade to 8.04, which is a LTS release, or a supported OS.

2. You are asking an extremely technical question about a third party application that appears to be beyond the kowledge of this community.

Personally VMWare runs for me on 9.04 with essentially the same instructions as 8.10. It does  not run well and while guests are booting my computer makes a long high pitched very irritating beep. Once the guest is done booting it all seems to be working normally, although I have not extensivly tested my guests.

Personally, at this piont, I have no need to run VMWare, KVM and Virtualbox both better integrate into Ubuntu and both seem to work better (for me) then VMWare.

Personally, I do not like the direction VMWar Server 2.0 is moving, 1.x is for me a much better product.

Becasue of those issues I am guessing community members are slowy moving away from VMWare, although I sure there are some very knowledgable people using VMWare.

Your other option is to post on the VMWare Forums :

[http://communities.vmware.com/community/vmtn/server?view=discussions](http://communities.vmware.com/community/vmtn/server?view=discussions)

---

### Post by RealG187 on 2009-06-07
I just finished reinstalling Ubuntu to 9.04. I'll go insane if I have to reinstall again. I have even more problems with Virtualbox than VMWare.

---

### Post by zuerston on 2009-06-11
all I did was type **apt-get install virtualbox** and it works great. also upgraded it with **apt-get upgrade virtualbox**.
good stuff! :popcorn:

---

### Post by drooze on 2009-06-12
I got ubuntu 9.04 (guest) working perfectly with guest additions on Vista (host) with VirtualBox.

Will probably upgrade to Karmic next week.

---

### Post by ducksun43 on 2009-06-14
imho OpenVZ [http://sunoano.name/ws/public_xhtml/openvz.html](http://sunoano.name/ws/public_xhtml/openvz.html) should be mentioned since it is exremly fast and easy to setup because, for Debian and Ubuntu, there are .debs available

---

### Post by bodhi.zazen on 2009-06-14
I use OpenVZ and it runs guests at native speed.

It is a little off the beaten path at it takes some effort to install. Support is kernel dependent and I am not sure there are .deb available for 9.04.

Usually you need to run an older kernel and / or path your own.

Openvz does not support BSD or Windows guests, and I bet most people here want to run Windows.

My advice if you want Openvz is to use Proxmox :

[http://pve.proxmox.com/wiki/Main_Page](http://pve.proxmox.com/wiki/Main_Page)

Here is a review :

[https://www.montanalinux.org/proxmox-ve-review.html](https://www.montanalinux.org/proxmox-ve-review.html)

---

### Post by juancarlospaco on 2009-06-15
i come here to say...
[B]
[COLOR="Red"]Just try OpenQRM 4.x installed on Ubuntu Server[/COLOR][/B]

All-in-one enterprise grade web based Multi-Virtualization-Technology managment console

[B]OpenSource, Xen, KVM, VMWare ESXi, Citrix XenServer, Linux Vserver,
VMWare Server, VMWare Server2, i-SCSI, P2V, V2P, V2V, 
Drag&Drop Live Migration, Cloud Computing Ready, DHCP-In-Cloud, DNS-In-Cloud, 
Enterprise High Avaliability, Ready to deploy Image collection, 
Support for Local Servers&Storage, LVM2, Nagios2/3 Autoconfig, CloudApp ready,
NFS remote Storage, SSH, TFTPd, ...and large ETC.[/B]

---

### Post by ysNoi on 2009-07-20
Is there a way how to access both files on Host and Guest OS..? How to copy files from Host to Guest OS or vice versa...?

---

### Post by bodhi.zazen on 2009-07-20
> **ysNoi said:**
> Is there a way how to access both files on Host and Guest OS..? How to copy files from Host to Guest OS or vice versa...?

You can use almost any network protocol. ssh (scp), samba, nfs, ftp, http (one way), rsync.

scp and samba are probably most popular, nfs probably #3 .

---

### Post by RealG187 on 2009-07-20
What's scp?

---

### Post by bodhi.zazen on 2009-07-20
> **RealG187 said:**
> What's scp?

scp = secure copy.

If you have a ssh server running you can transfer files over the ssh protocol via scp.

If you like you can mount them locally, on Linux, with sshfs and use nautilus as a gui interface.

On windows you can use an application "winscp" which will again use a gui interface.

Thus , if you have ssh server installed anyways, might as well use it rather then ftp, nfs, samba, etc.

scp foo [email]bodhi@secret_server.com[/email]:/home/bodhi/foo

scp is nice over the internet as it encrypts the data :twisted:

---

### Post by RealG187 on 2009-07-21
Doesn't nautilus mount FTP and Samba as local too? (Well not for my [Yahoo! Hosting...]("http://ubuntuforums.org/showthread.php?t=1011474"))

Anyways, I am need a way to send files over the internet...:
[http://ubuntuforums.org/showthread.php?p=7181074](http://ubuntuforums.org/showthread.php?p=7181074)

---

### Post by maryfrank58 on 2009-08-12
I just got virtualbox working on 9.04.  Thought I had check the groups and EHCI, didn't but did and now usb works.  I now can't use right CTRL to get out of box.  Checked preferences under vb file and Right-ctrl is checked.  Help!
mary

---

### Post by bodhi.zazen on 2009-08-13
There are two control keys on most key boards. Try the one on the right side of the keyboard.

---

### Post by maryfrank58 on 2009-08-13
Thanks for the reply, but I tried that.  Everything worked (except no USB)before I reclicked on merged group[ and EHCI.  Now the USB works but not the right ctrl or even the left ctrl.

---

### Post by bodhi.zazen on 2009-08-13
Ouch. Try re-defining your host button in Virtualbox.

File -P preferences -> Input tab (on the left).

---

### Post by The Bright Side on 2009-08-14
Hey, hope you guys can help me out here. Using VirtualBox 3.0.4, I just created a VM with Jaunty 64 on a Jaunty 64 host system (I need it so I can try new software etc. w/o screwing up my system).

Two things I noticed:
1 - It runs slow, esp. the desktop graphics, you can watch windows get built step by step on the screen
2 - I have no network or internet access. I installed the Guest Additions, but I cannot used a shared folder or access the WWW from within the guest.

My Network configuration for that VM is:
- Adapter 1 enabled
- Adapter Type: Intel PRO/1000 MT Desktop (85240EM)
- Attached to: NAT

Do you have some advice? Thanks! :-)

---

### Post by techfanboy81 on 2009-08-14
Virtualization its like an imagination.  You may think its a real box but its not, its just a virtual machine that executes programs, like a real machine.

---

### Post by running_rabbit07 on 2009-08-15
Is there a tutorial anywhere on how to use KVM? I have installed it and there is no start button for it in the main menu. Does it only start via Terminal?

---

### Post by bodhi.zazen on 2009-08-15
> **running_rabbit07 said:**
> Is there a tutorial anywhere on how to use KVM? I have installed it and there is no start button for it in the main menu. Does it only start via Terminal?

yes, KVM is command line only. There are several graphical interfaces for KVM , see virt-manager.

In addition there are several web based interfaces, I personally use Proxmox.

From the command line kvm is easy, but it takes some time. See man kvm and man qemu.

basic usage:

kvm -m 512 -cdrom /home/you/ubuntu.iso -hda /home/you/ubuntu.qcow -usbdevice tablet &

I have several kvm tutorials on my blog if you wish.

[http://blog.bodhizazen.net/category/linux/](http://blog.bodhizazen.net/category/linux/)

---

### Post by running_rabbit07 on 2009-08-16
Sweet, Thanks!

---

### Post by bodhi.zazen on 2009-08-17
You are most welcome.

---

### Post by pdtpatrick on 2009-08-17
Yup KVM on ubuntu is pretty sweet. I like the way virt-manager looks just like vmware ESX server  .. pretty cool. 

Not to mention, X11 forward and then you can fire up virt-manager from anywhere - makes working remote very handy. 

Gotta try proxmox

---

### Post by der_flo on 2009-08-27
> **pdtpatrick said:**
> Yup KVM on ubuntu is pretty sweet.
If it works, yes.

But see our issue:
[http://ubuntuforums.org/showthread.php?p=7822865#post7822865](http://ubuntuforums.org/showthread.php?p=7822865#post7822865)
[http://serverfault.com/questions/51427/apt-get-and-aptitude-not-working-in-ubuntu-9-04-kvm-environment](http://serverfault.com/questions/51427/apt-get-and-aptitude-not-working-in-ubuntu-9-04-kvm-environment)

Perhaps somebody can help. Thanks!

der Flo

---

### Post by prrajend on 2009-09-04
Hi,

I am new to Ubuntu..I was trying to install VMware server1.0.6 on Ubuntu 9.04 and i got the following error.

usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config0/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:71:
/tmp/vmware-config0/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config0/vmmon-only/linux/driver.c:146: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config0/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c:150: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config0/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1670: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

Please advise

---

### Post by bodhi.zazen on 2009-09-04
First, vmware server 1.0.6 is very old, server is currently in 2.0.x

Second, 9.04 is a relatively new kernel so you are likely to have problems.

I have become disinterested in supporting VMWare on Ubuntu as it has always been difficult.

If you wish to run VMWare I suggest you use one of the supported platforms listed on the VMWare site. If you wish to use 1.0.6 you *may* have to use Ubuntu 8.04.

Take a look at the so called any-any patch and see if that helps.

[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

As an alternate to VMWare you might consider KVM or VirtualBox. Of the two VirtualBox is the easier to use.

---

### Post by cwmoser on 2009-09-04
I'm ready to switch over to KVM.
VMware's Player is slow - especially when Compiz is running.

Can my vmware VM's be converted to run under KVM virtualization????

Carl

---

### Post by bodhi.zazen on 2009-09-04
> **cwmoser said:**
> I'm ready to switch over to KVM.
VMware's Player is slow - especially when Compiz is running.

Can my vmware VM's be converted to run under KVM virtualization????

Carl

Yes, I have a number of how-to's for KVM on my blog.

[http://blog.bodhizazen.net/linux/convert-vmware-vmdk-to-kvm-qcow2-or-virtualbox-vdi/](http://blog.bodhizazen.net/linux/convert-vmware-vmdk-to-kvm-qcow2-or-virtualbox-vdi/)

It is not 100 % but it is fairly easy to do.

Personally I run KVM from the command line with a few scripts, again easy to do. There are a number of options for KVM that are not available via virt-manager or virsh.

Again I have a number of how-to's on my blog, they will come up on a google search as well.

---

### Post by theZoid on 2009-09-05
> **bodhi.zazen said:**
> Yes, I have a number of how-to's for KVM on my blog.

[http://blog.bodhizazen.net/linux/convert-vmware-vmdk-to-kvm-qcow2-or-virtualbox-vdi/](http://blog.bodhizazen.net/linux/convert-vmware-vmdk-to-kvm-qcow2-or-virtualbox-vdi/)

It is not 100 % but it is fairly easy to do.

Personally I run KVM from the command line with a few scripts, again easy to do. There are a number of options for KVM that are not available via virt-manager or virsh.

Again I have a number of how-to's on my blog, they will come up on a google search as well.

If I am using VirtualBox non-free edition for Windows XP with USB support, is there any advantage for me to use KVM?  thanks as I'm not familiar with KVM.  Also, does KVM support usb and 3d acceleration?

---

### Post by bodhi.zazen on 2009-09-05
kvm supports usb devices. graphics are better in VBox and VMWare.

---

### Post by theZoid on 2009-09-06
> **bodhi.zazen said:**
> kvm supports usb devices. graphics are better in VBox and VMWare.

Thanks...I'm right where I want to be with VB then...wanted to make sure I wasn't missing out on something :)

---

### Post by bengtner on 2009-10-11
I've installed 9.04 in a virtual machine (VirtualBox 3.0) on a Windows 7 (64bit) host. Initially I had problems with to enable higher screen resolution than 800x600, but after installation of Vboxadditions this problem was gone, and I can adjust the screen resolution to whatever I want. 

However, after I installed Vboxadditions, the system became very sluggish. For instance, when I type text, the characters pop up with a significant delay. 

I don´t know if this is the right forum to bring up this subject, but I' make a try.

BR

---

### Post by thelastquincy on 2009-10-23
> **bengtner said:**
> I've installed 9.04 in a virtual machine (VirtualBox 3.0) on a Windows 7 (64bit) host. Initially I had problems with to enable higher screen resolution than 800x600, but after installation of Vboxadditions this problem was gone, and I can adjust the screen resolution to whatever I want. 

However, after I installed Vboxadditions, the system became very sluggish. For instance, when I type text, the characters pop up with a significant delay. 

I don´t know if this is the right forum to bring up this subject, but I' make a try.

BR

 Hey I wanted to do the opposite of what this guy has...9.04 host with 64 bit windows 7 in vbox will this work on my vaio vgn-nr460? thanks  -Quincy

---

### Post by rliegh on 2009-10-24
> **bengtner said:**
> I've installed 9.04 in a virtual machine (VirtualBox 3.0) on a Windows 7 (64bit) host. Initially I had problems with to enable higher screen resolution than 800x600, but after installation of Vboxadditions this problem was gone, and I can adjust the screen resolution to whatever I want. 

However, after I installed Vboxadditions, the system became very sluggish. For instance, when I type text, the characters pop up with a significant delay. 

I don´t know if this is the right forum to bring up this subject, but I' make a try.

BR

Try turning off compiz in your Ubuntu guest ( system->preferences->appearance preferences->visual effects, select 'none' and then log out and then back in -better yet, restart the VM), that should improve things.

---

### Post by linuxkingpin on 2009-10-26
Ive got ubuntu 9.04 running floorlessly with additions and i did additions without moding although i cant get compiz to work

---

### Post by Bob63 on 2009-10-27
Okay, noob question for the virtualization gurus:

I'm running a fresh install of Jaunty with all updates, kernel 28-16. I recently upgraded my videocard to a 9500GT. I have not yet installed the NVidia restricted drivers. I am running the current build of VirtualBox v3.0.8 r53138. I have installed WinXP SP3 on the virtual machine for gaming. So far, everything is working.

My question is this:
Does VirtualBox (or any of the virtualization environments) actually expose the hardware to the guest machine? Specifically, is there any way for my Windows guest to see and use the 9500GT?

I'm not opposed to a little tinkering, but if I can't get what I want, I guess I'll change my setup so that I have a Windows partition.

Apologize if this has been covered or not the proper place to ask; I didn't see anything in this thread.

---

### Post by bodhi.zazen on 2009-10-27
> **Bob63 said:**
> My question is this:
Does VirtualBox (or any of the virtualization environments) actually expose the hardware to the guest machine? Specifically, is there any way for my Windows guest to see and use the 9500GT?

No, not yet.

---

### Post by corsakh on 2009-10-30
> **bodhi.zazen said:**
> kvm supports usb devices. graphics are better in VBox and VMWare.
Which one of those two would you pick for better and mainly faster desktop graphics?

---

### Post by bodhi.zazen on 2009-10-30
> **corsakh said:**
> Which one of those two would you pick for better and mainly faster desktop graphics?

If you want graphics, IMO either VirtualBox or VMWare (workstation). Both are nice.

Personally KVM is sufficient for my needs so I have not compared the two recently.

---

### Post by Nightstrike2009 on 2010-01-20
> By RCDeacon:
I am having trouble getting usb to work in 9.04. I did some searching but have not come up with the answer. My usb devices ARE seen in virtualbox but are grayed out. I'm sure this is a simple problem but I if someone can steer me in the right direction I would sincerely appreciate it.

> By RCDeacon:The problem is SOLVED. In the process of installing other programs I had to do a reboot and upon reboot all is well. Sorry for the false alarm.

How did you get this to work as I have the same problem?

---

### Post by Nightstrike2009 on 2010-01-20
I have fixed this problem now after a few searches on the internet it seemed to be a problem with usergroup setups anyhow here is my guide so new people don't have to suffer this annoying problem.

> BY Nightstrike2009:
FIXING USB SUPPORT IN UBUNTU VIRTUAL BOX

1)On Ubuntu 9.04 go to Administration>Users & Groups
2)Click &#8220;Unlock&#8221; button and type in root password on request.
3)Click &#8220;Manage Groups&#8221; button after your password has been accepted.
4)On the &#8220;Groups Settings&#8221; Screen, Scroll down and highlight &#8220;vboxusers&#8221;, double click on its name & Check the box in front of your username, then click &#8220;OK&#8221;.
5)Close &#8220;Vboxusers group properties&#8221; window, by clicking &#8220;OK&#8221;, then close &#8220;Groups Settings&#8221; and &#8220;User Settings&#8221; windows by clicking &#8220;Close&#8221; button.
6)Either log out and log back into Ubuntu 9.04 or reboot it, you should now be able to use your USB devices.

ADDING & DISABLING USB DEVICES IN VIRTUAL BOX

1)On Ubuntu select Applications>System Tools Sun Virtual Box.
2)In right pane (Information) scroll down to until you see a small USB icon with &#8220;USB&#8221; in blue text at its side, click the blue &#8220;USB&#8221; text.
3)Check both boxes for &#8220;Enable USB Controller&#8221; and &#8220;Enable USB 2.0 (EHCI) Controller&#8221;.
4)At the right side of &#8220;USB device filters&#8221; there is a little usb icon with a green add sign (this adds new usb devices).
5)After you have finished adding usb devices, check the boxes at the left side of all usb devices you wish to use.
6)NOTE: I had to disable the USB/PS2 mouse driver on my pc as it wasn't letting me use the mouse.

And that's it it works :-)

---

### Post by nirmalsudan on 2010-02-01
Hello,
 
I have successfully Put Sun Virtuabox on Ubuntu 9.10.
Only drawback is it allows only one vm at a time.
 
I shall be trying to put VMWARE Workstation or Server soon as I need mulitple VM's running.
Let me know if you have soon comments on this area

---

### Post by bodhi.zazen on 2010-02-01
> **nirmalsudan said:**
> I have successfully Put Sun Virtuabox on Ubuntu 9.10.
Only drawback is it allows only one vm at a time.

What give you that impression ? 

Last time I looked at VirtualBox you could run as many guests as allowed by your hardware.

---

### Post by davarse on 2010-03-01
hey guys im running tiny windows 7 on my ubuntu jaunty using virtual box so i get itunes for my ipod nano 5th gen. and i dont really know how to transfer my songs and/or data from my ubuntu to windows...
really appreciate the help

peace

---

### Post by Bob63 on 2010-03-01
Well, I've had success transferring files between my Ubuntu 9.04 host and my XP VM using the shared folders.

When I set up my VM, I put my home directory's Public folder as the shared directory. Then after installing Guest Additions inside the VM, I enabled file sharing, and pointed at the folder I named during the setup.

Host folder: /home/bob63/Public
VM setting: VMPublic (assign this name in the VM's Settings>Shared Folders)

I don't have Win 7 virtualized, but for XP once the Guest Additions were installed, I was able to find the folder in My Network Places (I think I may have had to look for a new network location, can't remember exactly). It shows up in My Computer as a Network drive on XP.

Once the network finds the shared folder, any file you put in it on the host will become available on the guest, (and vice versa) as far as I know. 

Hope this helps.

---

### Post by bodhi.zazen on 2010-03-01
> **davarse said:**
> hey guys im running tiny windows 7 on my ubuntu jaunty using virtual box so i get itunes for my ipod nano 5th gen. and i dont really know how to transfer my songs and/or data from my ubuntu to windows...
really appreciate the help

peace

you may use any network protocol to share files -

samba, ftp , ssh (scp) ,

---

### Post by davarse on 2010-03-02
> **bodhi.zazen said:**
> you may use any network protocol to share files -

samba, ftp , ssh (scp) ,

i installed samba host OS (ubuntu jaunty). do i need samba installed as well in the tiny windows 7?
and how do i access the file from the host OS?
thanks

---

### Post by RealG187 on 2010-03-02
Tiny Windows 7?

---

### Post by bodhi.zazen on 2010-03-02
> **davarse said:**
> i installed samba host OS (ubuntu jaunty). do i need samba installed as well in the tiny windows 7?
and how do i access the file from the host OS?
thanks

[http://www.ideaexcursion.com/2009/01/15/windows-7-in-virtualbox-shared-folders-workaround/](http://www.ideaexcursion.com/2009/01/15/windows-7-in-virtualbox-shared-folders-workaround/)

---

### Post by juancarlospaco on 2010-03-02
*Where the LXC comments go...?*

---

### Post by davarse on 2010-03-02
yea just the basic of windows 7

---

### Post by RealG187 on 2010-03-02
> **davarse said:**
> yea just the basic of windows 7Did you make it your self from an ISO of retail Windows 7?

---

### Post by bodhi.zazen on 2010-03-02
> **juancarlospaco said:**
> *Where the LXC comments go...?*

What about LXC ?

---

### Post by juancarlospaco on 2010-03-03
> **bodhi.zazen said:**
> What about LXC ?

Anything..., 
i think the most flakky part of these contextualization technology is the DOCs

*Last time i checked the documentation is not so nice to finishing a production ready setup*
:)

---

### Post by bodhi.zazen on 2010-03-03
> **juancarlospaco said:**
> Anything..., 
i think the most flakky part of these contextualization technology is the DOCs

*Last time i checked the documentation is not so nice to finishing a production ready setup*
:)

I agree completely !!!

[https://bugs.launchpad.net/ubuntu/+source/lxc/+bug/514379](https://bugs.launchpad.net/ubuntu/+source/lxc/+bug/514379)

[https://bugs.launchpad.net/ubuntu/+source/lxc](https://bugs.launchpad.net/ubuntu/+source/lxc)

See :

    [http://blog.bodhizazen.net/linux/lxc-linux-containers/](http://blog.bodhizazen.net/linux/lxc-linux-containers/)
    [http://blog.bodhizazen.net/linux/lxc-configure-fedora-containers/](http://blog.bodhizazen.net/linux/lxc-configure-fedora-containers/)
    [http://blog.bodhizazen.net/linux/lxc-configure-ubuntu-lucid-containers/](http://blog.bodhizazen.net/linux/lxc-configure-ubuntu-lucid-containers/)
    [http://blog.bodhizazen.net/linux/lxc-configure-ubuntu-karmic-containers/](http://blog.bodhizazen.net/linux/lxc-configure-ubuntu-karmic-containers/)
    [http://blog.bodhizazen.net/linux/lxc-configure-debian-lenny-containers/](http://blog.bodhizazen.net/linux/lxc-configure-debian-lenny-containers/)

---

### Post by davarse on 2010-03-11
it's solved
thanks

---

### Post by marenmar on 2010-09-20
hi, it may be a simple problem for you guys,
 
during installation of my Ubuntu 9.10 VM on Windows7 hosts, my installation stopped at 97%
then my hosts hanged up, I used the issued CD during this installation.
Then I downloaded a iso version on the site and used it as the installer. Same problem had occured. I am using the Sun VirtualBox by the way.
 
Hope you can help my problem, thanks.

---

### Post by thelastquincy on 2010-09-20
Have you checked the iso file for validity? Doing a quick check sum will see if the file is corrupted or not. All of Ubuntu files use some sort of md5 check sum. i think.

---

### Post by marenmar on 2010-09-20
Actually, I have just used the iso file last month and no problems occured. It only surfaced when I installed it the other day. >_<

---

### Post by thelastquincy on 2010-09-20
Did you still check the file? Even though you can use it, it might not be fully valid you know what I mean?

---

### Post by marenmar on 2010-09-20
I'll check it for sure.
 
Thanks, I hope this solves my problem.

---

### Post by Darth Penguin on 2010-11-02
Lubuntu is the best host for any other OS. Matter of fact I don't think there is a Ubuntu distro better than it for virtualization.

---

### Post by bodhi.zazen on 2010-11-02
> **Darth Penguin said:**
> Lubuntu is the best host for any other OS. Matter of fact I don't think there is a Ubuntu distro better than it for virtualization.

Depends on what you want to do exactly for "Virtualization". There are many options from KVM to VBox to VMWare to LXC to Openvz.

Honestly I do not think Lubuntu is "best" , it is simply a Window manager (openbox + LXDE).

If you are going to run X , use the DE of your choice.

If you are using your box as a (server) host, do a minimal install and do not install X at all.

---

### Post by stlsaint on 2010-11-04
> **Darth Penguin said:**
> Lubuntu is the best host for any other OS. Matter of fact I don't think there is a Ubuntu distro better than it for virtualization.

That is a stretch to say it is the best for virtualization and im a lubuntu user myself! If your simply using vbox, ubuntu itself is great just as any other main distro would be! (ie: fedora, debian, mint, etc)

---

### Post by bontimelenggang on 2010-11-05
i have install ubuntu 9 via v.box under windows but i can't remote it,,,:(
i have change port access and check allow to remote acces but still not word?:confused:
can any one help me step by step?

---

### Post by JoeBnKY on 2011-12-02
I am using VMware Players on my 5 Quad core Win 7 boxes I built.  I had been using Ubuntu 9.04/10.10 as an OS for them.  When I updated to v 11.04 my network adapters quit working in both VMware Players on 1 of my boxes.  I checked the adapter settings against those on another box that is still working and they are all the same.  What can/must I do to get them working again?  I am using the adapters in the Nat. config. setting.
 :confused: I cant up or download anything on or to the VMware Players until I get a connection within them again.:confused:

---

### Post by JoeBnKY on 2011-12-06
MSG below my 1st post,  "Please click one of the Quick Reply icons in the posts above to activate Quick Reply".

If I knew what a quick reply was or what the icons looked like I could do that. But as this is my 2nd post to the forums I have no idea what  quick reply icons you are talking about.

---

### Post by Bob63 on 2011-12-06
> **JoeBnKY said:**
> If I knew what a quick reply was or what the icons looked like I could do that. But as this is my 2nd post to the forums I have no idea what  quick reply icons you are talking about.
@JoeBnKY,
In the lower right hand corner of each post are three icons: ***Quote***, ***Multi-Quote This Message*** and ***Quick Reply***. If you hover your mouse over the icons the names will appear.

Good Luck.

---

### Post by JoeBnKY on 2011-12-06
That icon says, "Quick reply to this msg". not Activate Quick Replys.  Why would I reply to my own question, I wouldn't post a question if I already had the answer.

---

### Post by JoeBnKY on 2011-12-06
> **JoeBnKY said:**
> I am using VMware Players on my 5 Quad core Win 7 boxes I built.  I had been using Ubuntu 9.04/10.10 as an OS for them.  When I updated to v 11.04 my network adapters quit working in both VMware Players on 1 of my boxes.  I checked the adapter settings against those on another box that is still working and they are all the same.  What can/must I do to get them working again?  I am using the adapters in the Nat. config. setting.
 :confused: I cant up or download anything on or to the VMware Players until I get a connection within them again.:confused:

I'll wait until 6PM Thur night, 12-8,  for somebody to answer then I guess I'll just delete those players and start from scratch.

---

### Post by zahidpak on 2012-02-02
Dear the link for blog which you have given is not open!

---

### Post by AndrewS1967 on 2012-03-25
Thank you or your question.Could you please describe me a little more about user-mode kernel virtualization?I suppose that file / registry virtualization is enough, but we really would like to improve boxedapp, so it would be great to understand more what does user-mode kernel virtualization provide.Thank you.

---

### Post by kevinyoukilis264 on 2012-06-26
[IMG]http://ihavejustbeenpaid.info/upload/158/smiler.gif[/IMG]


Ubuntu Server is an extremely popular platform for virtualising data centres. Ubuntu Server provides [KVM]("http://www.linux-kvm.org/page/Main_Page")  as the core option for both host and guest virtualisation. A wide  variety of open-source and proprietary technologies are also used in  conjunction with Ubuntu Server.
  
 **Open-source virtualisation**

 With each release Ubuntu Server offers more options for building and *managing*  a virtualised environment. Open-source technologies are at the  forefront of the modern virtualised environment, and the licence-free  model of Ubuntu is ideally suited to the dynamic expansion and reduction  of physical and virtual machines that are typical in these  environments.
   
 **A low footprint operating system**

 Ubuntu Server can  also be configured with a low footprint, creating the ideal base on  which to build virtual machines. Ubuntu includes a [Virtual Machine Builder ]("https://launchpad.net/vmbuilder")  which makes this process simple and replicable allowing multiple  pre-configured machines to be deployed instantly. Users of Canonical's [ Landscape ]("http://www.canonical.com/enterprise-services/landscape")  management tool will also find it an easy environment to manage as it  makes no distinction between virtual and physical machines, allowing  them to be managed through the same interface and in the same manner.
  
 **Ubuntu Server: ready for virtualisation**

 Our built-in hypervisor [ KVM]("https://help.ubuntu.com/community/KVM"), [libvirt ]("https://help.ubuntu.com/9.10/serverguide/C/libvirt.html")  and our virtual host profile can get you ready to virtualise x86  workloads. To simplify hardware maintenance and to enable dynamic  capacity balancing, live migration of guests between servers only  requires that they share a common storage system. Memory aggregation can  maximise the number of virtual machines when hosting the same operating  systems and applications on the same server.
  
 **Improve performance with VirtIO drivers**

 VirtIO  drivers provide virtual machines direct access to hardware which speeds  performance and eases maintenance. If you need more throughput, you can  dedicate specific hardware to virtual machines. The libvirt interface  is becoming an open-source standard and part of the core Linux kernel  with multiple third-party interfaces available.
  
 **The best guest OS**

 Ubuntu  Server runs smoothly as a guest operating system on popular  virtualisation technologies including Amazon EC2, VMware, Xen,  Parallels, LXC, VirtualBox, and KVM. With one of the smallest footprints  as a minimal install, you can easily base your virtual machines on  Ubuntu Server and only add what you really need. We even provide you  with tools to automate the build process of virtual machines that can be  created, or recreated, in a matter of minutes.

---

### Post by hovrashko on 2012-07-13
Virtual Box one of the best vitalization platforms that i had to work. VMWare quite unstable.:)

---

### Post by heiko_s on 2013-01-19
I had been fed up with dual-booting and was looking for a suitable virtualization solution for a long time. It turned out that Xen provides by far the best solution*:

1. VGA passthrough to the (Windows 7/8) guest - full video hardware acceleration under Windows 7/8 VM.
2. Excellent disk I/O performance when using GPLPV drivers in Windows VM - about as good as running Windows directly on the hardware.
3. Efficient CPU scheduling - CPU resources are assigned dynamically between host (Linux dom0) and guest VM.
4. Wide range of disk/storage options, incl. LVM (physical), file-based, or SATA controller passthru for direct AHCI access to the disk.
5. Best documentation after VirtualBox - there is still a gap between the two, but then VirtualBox doesn't get anywhere close to the performance of Xen.
6. Advanced server and cloud computing features - hot migration, etc.

I seriously don't know why Xen has been undervalued as it seems. I nearly passed on it myself, but luckily gave it a try.

If you want to run a virtual machine that offers near-native performance, or want to get rid of dual-booting, Xen is the best option. A typical example would be a gaming VM running a Windows guest for graphics intensive (3d) games.

P.S.: I myself am doing CPU and GPU intensive photo/graphics work in a Windows 7 virtual machine running on Xen/Linux Mint.

* EDIT: kvm seems to be picking up quickly. Those who aren't afraid going bleeding edge (=experimental) may want to give kvm a try. I'm specifically referring to VGA passthrough under kvm.

---

