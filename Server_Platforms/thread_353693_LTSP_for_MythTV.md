---
title: "LTSP for MythTV?"
date: 2007-02-05
forum: Server Platforms
---

### Post by Beta-Glitch on 2007-02-05
Hello All!

I have this big headache that I'm trying to get my head around with regards to creating a media centre system.

Background:
My father-in-law is buying a Bed-and-Breakfast style accommodation that they may use for occasional "retreat"-style weekends, etc.

He told me he was wanting to build an entertainment system into each room (5-6 in total), including the ability to watch DVD's, Play CD's, browse the internet, and Maybe host a central repository of video files to watch over the network. He was also interested is TV on this entertainment system, but that was more of a "if we could do it"

He was also worried about being able to protect the machines from "unwanted" content on the web, and it needed to be easy to administer so he doesn't have to call me up everytime it goes wrong (I'll be about 2 hours away).

My problem:
I'm not what I would call an experienced Linux user. I messed in it here and there, but always with general purpose distros, nothing on the scale of customised needs as above.

I was thinking a LTSP on edubuntu could potentially work, but I don't know the ins and out. Would MythTV work over an SSH tunnel into the server, or would that be too slow? also, can you customise the root filesystem that is booted, purhaps chroot into it and edit it like any other system, to allow customisation? Am I way of here or is there another easy way of setting it up?

Also, as you can probably guess, is the support for MythTV in ubuntu good too?

Hardware wise, I was thinking along the lines of maybe a Via-based system, because it's small and you can get fanless configurations, for noise. is ubuntu's support for these type of systems very good?

Thanks for any info you can give.

---

### Post by Beta-Glitch on 2007-02-11
Well, I kinda answered my own question, but brought about more.

So LTSP wouldn't really work, because it uses the server for processing everthing, which is not my intention

so I'm back to diskless booting over NFS.

[https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)

Looking at above wiki page, I can see this is what I want, but it does assume a certain amount of knowledge about how NFS, PXE, and linux in general works, which I lack. 

So, my challenge: Can someone tell me how to do the following, based on above steps

I have 1 server, running vanilla ubuntu 6.10, 1 network card configure to 192.168.10.11
I have NO DHCP running
and I have 1 intel iMac, running windows + VMware Server set to have no HD and use PXE booting.

How can I use the vanilla ubuntu install to be the source of my booted clients, and also be the server for them, obviously requiring to copy the entire contents of server into another folder. Then, test the setupwith my iMac.

I hope this question get at least SOME response, I'd rather hear a 'No' or 'you're an idiot' to nothing at all.

Regards

---

### Post by Beta-Glitch on 2007-02-13
OK, well thanks for the great help again :roll: 

I've hacked away until I've got it to work (I don't know how I'm gonna recreate it), except it hangs on the following line:

eth0: link up

I'm guessing it drops the NFS connection when it brings up the ethernet. I've commented out the 'auto eth0' from /etc/network/interfaces, but it still does it, any one have any ideas how to get over this final hurdle?

I await your replies

---

### Post by Beta-Glitch on 2007-02-17
I can hear tumble weed ....

---

### Post by afljafa on 2007-02-18
Hi - Im about to do the same thing. SMEServer backend (running Mythtv) pxe booting an Ubuntu diskless frontend.

I shall help where I can.

---

### Post by afljafa on 2007-02-21
> **Beta-Glitch said:**
> OK, well thanks for the great help again :roll: 

I've hacked away until I've got it to work (I don't know how I'm gonna recreate it), except it hangs on the following line:

eth0: link up

I'm guessing it drops the NFS connection when it brings up the ethernet. I've commented out the 'auto eth0' from /etc/network/interfaces, but it still does it, any one have any ideas how to get over this final hurdle?

I await your replies

Take a look at the last portion of [this page]("http://developer.novell.com/wiki/index.php/HOWTO:_Convert_Ubuntu_to_Diskless").

I have this working in a virtual machine at the moment.

---

### Post by superm1 on 2007-02-21
> **afljafa said:**
> Take a look at the last portion of [this page]("http://developer.novell.com/wiki/index.php/HOWTO:_Convert_Ubuntu_to_Diskless").

I have this working in a virtual machine at the moment.
I've currently got a diskless frontend setup that is functional by setting up something between those two guides approx 2 months ago.  Works wonderfully :)

I've got OpenWRT installed on my WRT54G router, and it hands out information about where to PXE boot to.  I have an ubuntu 6.06 backend running tftpd and sharing via nfs root.  I installed via debootstrap into a directory and then modified the initrd to allow for network booting.  Followed the information in the guides about updating /etc/fstab, and haven't had any troubles.

I wish I documented the entire procedure, because I'm sure I came across some problems but knew how to handle them.  Post any questions you have to this thread, and I can try to help.

---

### Post by Beta-Glitch on 2007-02-22
> **afljafa said:**
> Take a look at the last portion of [this page]("http://developer.novell.com/wiki/index.php/HOWTO:_Convert_Ubuntu_to_Diskless").

I have this working in a virtual machine at the moment.

Which version of ubuntu are you using? as I said I have already commented it out of the interfaces file and it still does the same thing.

Anything I'm missing?

---

### Post by afljafa on 2007-02-22
I am using the base install on the alternate 6.10 cd. I also changed "MODULES=netboot" in /etc/mkinitramfs/initramfs.conf as per [this]("http://alkemio.org/diskless-edgy.html") page.

---

### Post by afljafa on 2007-02-24
> **superm1 said:**
> I've currently got a diskless frontend setup that is functional by setting up something between those two guides approx 2 months ago.  Works wonderfully :)



Well - I have just finished. Did a mythtv frontend install using your guide - however I ommited GDM in favour of an autologin method. Weighs in at around 800 meg.

If anyone is interested - I am slowly working thru a SMEServer install [here]("http://mythtv.goldtel.com.au"). It makes for a great backend as well as a good pxe/nfs server for the frontend.

---

### Post by superm1 on 2007-02-24
> **afljafa said:**
> Well - I have just finished. Did a mythtv frontend install using your guide - however I ommited GDM in favour of an autologin method. Weighs in at around 800 meg.

If anyone is interested - I am slowly working thru a SMEServer install [here]("http://mythtv.goldtel.com.au"). It makes for a great backend as well as a good pxe/nfs server for the frontend.
Out of curiousity, what autologin method are you using instead of a gdm autologin?

---

### Post by superm1 on 2007-02-24
err is this it [http://mythtv.goldtel.com.au/startx?v=231](http://mythtv.goldtel.com.au/startx?v=231)

---

### Post by afljafa on 2007-02-24
> **superm1 said:**
> err is this it [http://mythtv.goldtel.com.au/startx?v=231](http://mythtv.goldtel.com.au/startx?v=231)

Similar - but not quite. I compiled the little auto login script found floating around the web and created an executable .xinitrc with the openbox and mythfrontend stuff in it.

I also found this method that might work. [linky]("http://www.mythtv.org/wiki/index.php/Frontend_Auto_Login#Note_on_Ubuntu_.286.10.29")

---

### Post by Beta-Glitch on 2007-02-26
I'm still getting stuck. I've even started from scratch to see if I did something wrong.

The few lines I get before it hangs are as follows:

Begin: Running /scripts/nfs-top ...
[171795.74.160000] pcnet32.c:v1.32 18.Mar.2006 [email]tsbogend@alpha.franken.de[/email]
[171795.74.160000] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 18 (level, low) -> IRQ 169
[171795.74.160000] pcnet32: PCnet/PCI II 79C970A at 0x1400, 00 0c 29 05 40 cd assigned IRQ 169.
[171795.74.160000] eth0: registered as PCnet/PC II 79C970A
[171795.74.160000] pcnet32: 1 cards_found.
Done.
[171795.74.172000] NET: Registered protocol family 17
IP-Config: eth0 hardware address 00:0c:29:05:40:cd mtu 1500 DHCP RARP
[171795.74.172000] eth0: link up


It sounds to me like it still bringin up the ethernet. I've redone my initrd.img based on the website afljafa posted. I've also taken out the lines from my pxe boot config to reflet what it says on that page. I'll also reconfirm that I have commented every line out of /etc/network/interfaces, except for 'auto lo' and 'iface lo ....'.

Any one have any idea why this is happening?

---

### Post by afljafa on 2007-02-26
This is how my /tftpboot/pxelinux.cfg/default reads. Not sure it will help.


```
LABEL linux
KERNEL vmlinuz-2.6.17-10-386
APPEND root=/dev/nfs initrd=initrd.img-2.6.17-10-386 nfsroot=10.0.0.5:/nfsroot rw quiet splash
```

Other than that - I really can`t think of any other reason for this not working. It certainly seems that you are almost there.

It is the /etc/network/interfaces on the nfs server you have modified and not the physical build?

---

### Post by superm1 on 2007-02-26
For sanity's sake, here is my tftp default line too:

label linux
        kernel netboot/vmlinuz
        append root=/dev/nfs initrd=netboot/initrd.img nfsroot=192.168.6.52:/media/netboot/netboot ip=dhcp quiet splash

I keep everything in a directory called netboot, this allows me to use normal sudo kernel updates automatically.

The only big change for me to get the initrd properly netbooting was to modify a line in /etc/initramfs-tools/initramfs.conf.
Just changed BOOT to be:
```
BOOT=nfs
```

My frontend's /etc/network/interfaces is this:
```
mythtv@mythtv:~$ cat /etc/network/interfaces 
# Used by ifup(8) and ifdown(8). See the interfaces(5) manpage or
# /usr/share/doc/ifupdown/examples for more information.
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

I'm not sure where you are even seeing that script run.  I don't see notes of it in dmesg or /var/log/messages even.

---

### Post by afljafa on 2007-02-26
> **superm1 said:**
> 
My frontend's /etc/network/interfaces is this:
```
mythtv@mythtv:~$ cat /etc/network/interfaces 
# Used by ifup(8) and ifdown(8). See the interfaces(5) manpage or
# /usr/share/doc/ifupdown/examples for more information.
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

Lol - That should throw a spanner into the works. If I don`t hash out **auto eth0** and 
**iface eth0 inet dhcp** my frontend will not get past trying to bring eth0 up.

---

### Post by superm1 on 2007-02-26
> **afljafa said:**
> Lol - That should throw a spanner into the works. If I don`t hash out **auto eth0** and 
**iface eth0 inet dhcp** my frontend will not get past trying to bring eth0 up.
Yea that will be mighty confusing.  I wonder why it works fine for me then?
DHCP is supposed to occur duing the initrd anyhow,.

---

### Post by Beta-Glitch on 2007-03-09
well if no one has any other ideas, I might try it with an earlier version, 6.06 maybe?

---

### Post by Beta-Glitch on 2007-03-11
OK, so foloowed the instuctions using 6.06 as server and client.

got pretty mucht he same thing (i think):

last line of startup:

IP-Config: eth0 hardware address: xx:xx:xx:xx:xx:xx mtu 1500 DHCP RARP


again I have checked /nfsroot/etc/network/interfaces and commented out all references to eth0

Why is this so difficult for me only?

---

### Post by afljafa on 2007-03-12
It might be hardware. I have just tried my same diskless client on another machine (quite a new Nvidia jobby) and it bombs out with a kernel panic around the time it deals with the networking.

Switch back to the older machine and it works fine.

You could grab a copy of vmware workstation and try network booting from it to test your work. Thats how I built my machines.

---

### Post by Beta-Glitch on 2007-03-12
I've done the whole thing in vmware server (the free one), should basically be the same.

thats what's odd.

---

