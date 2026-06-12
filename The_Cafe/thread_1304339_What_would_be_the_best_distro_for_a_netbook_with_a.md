---
title: "What would be the best distro for a netbook with an extremly slow ssd?"
date: 2009-10-29
forum: The Cafe
---

### Post by Borjs85 on 2009-10-29
Hi guys,

My mother owns an Acer Aspire One (I think it's the first one, with an awful 8GB SSD). She is using Windows XP and it's a nightmare: seems that everything's going  in slow motion. I'm going to change her OS. Before installing  Ubuntu or other distro I'd like to ask you what would be the best distro (user friendly) for a netbook with this big limitation (SSD)

Thanks a lot (and if I have kicked english dictionary, sorry, I'm from Spain and I am not very good at english)

---

### Post by PorkyPie on 2009-10-29
Have you checked out ubuntu netbook remix? [http://www.ubuntu.com/GetUbuntu/download-netbook](http://www.ubuntu.com/GetUbuntu/download-netbook)

---

### Post by karimruan on 2009-10-29
> **Borjs85 said:**
> Hi guys,

My mother owns an Acer Aspire One (I think it's the first one, with an awful 8GB SSD). She is using Windows XP and it's a nightmare: seems that everything's going  in slow motion. I'm going to change her OS. Before installing  Ubuntu or other distro I'd like to ask you what would be the best distro (user friendly) for a netbook with this big limitation (SSD)

Thanks a lot (and if I have kicked english dictionary, sorry, I'm from Spain and I am not very good at english)

Well, you could always try Xubuntu, it is designed for machines with low specs such as your mothers netbook. If you want, you can try Damn Small Linux or Puppy Linux (Puppy has at least 50 different versions all over the net, even ones that look like mac osx). The problem with Puppy is that it has very little hardware support, especially for wireless (at least when I used it). DSL (Damn Small Linux) is debian based, so you can add as many .debs as you want, and turn it into a full blown desktop OS if you want. DSL is like 60 MB to download, so it is fast as he!!. 

I would recommend trying Xubuntu first.

---

### Post by karimruan on 2009-10-29
> **PorkyPie said:**
> Have you checked out ubuntu netbook remix? [http://www.ubuntu.com/GetUbuntu/download-netbook](http://www.ubuntu.com/GetUbuntu/download-netbook)

Would netbook remix be okay on an 8GB partition? I mean, that is pretty small!

---

### Post by PorkyPie on 2009-10-29
> **karimruan said:**
> Would netbook remix be okay on an 8GB partition? I mean, that is pretty small!

It should be fine.

---

### Post by Borjs85 on 2009-10-29
Ubuntu netbook remix is better than Ubuntu? 
I've always thought UNR was ubuntu whith less default apps and some extra packages, like window-picker-applet or netbook-launcher.

Xubuntu is an option... but will give a better performance than Ubuntu? I'm running in an eepc 901 Kubuntu without problems: it has the same cpu and graphic card. The SSD is its curse

---

### Post by karimruan on 2009-10-29
The good thing about xubuntu is you could always run sudo apt-get install kde, and get the kde DE, or even do it with gnome. Then, you get the great look with less of the resource heavy apps.

---

### Post by bailout on 2009-10-29
XP is probably your best bet tbh. Ubuntu has poor battery life compared to XP or Linpus (which was the linux distro that came with the aao). XP needs some tweaks to work well on the ssd version though iirc. Try looking on the aao forums for tips.

[http://www.aspireoneuser.com/forum/](http://www.aspireoneuser.com/forum/)

---

### Post by kasrawis on 2009-10-29
i recommend to install Xubuntu it will be pretty good

---

### Post by gnomeuser on 2009-10-29
A friend of mine runs Fedora 12 on one of those with btrfs mounted in the ssd mode. He claims this provides decent performance on that hardware. Remember there are other tweaks you can do, such as entirely disabling swap.

---

### Post by Hallvor on 2009-10-29
Easy Peasy? 

[http://www.geteasypeasy.com/](http://www.geteasypeasy.com/)

---

### Post by NoaHall on 2009-10-29
Don't install Xubuntu. Install Ubuntu from the minimal iso and then install xfce.

---

### Post by benj1 on 2009-10-29
most of the speed loss with SSD is down to crappy firmware not handling writes very well, writes are the main bottleneck in SSDs so its best to minimise them, so turn off access times for files in the file system (google atime/noatime for you partcular file system), 
if you have the ram mount /tmp in ram, also perhaps /var/log aswell 
if you have the internet bandwidth, point your web browser cache to use /tmp too

then choose a distro that you dont need to dip in to swap with, that should speed it up, and make your hard drive last longer too

---

### Post by benj1 on 2009-10-29
for anyone interested here is a pretty good indepth look at SSDs
[http://www.anandtech.com/storage/showdoc.aspx?i=3531&p=1]("http://www.anandtech.com/storage/showdoc.aspx?i=3531&p=1")

this page in particular explains the slowdown issue
[http://www.anandtech.com/storage/showdoc.aspx?i=3531&p=8]("http://www.anandtech.com/storage/showdoc.aspx?i=3531&p=8")

---

### Post by snowpine on 2009-10-29
Smaller distros (Puppy, DSL, SliTaz, even AntiX) have the ability to load completely into RAM at boot time, then run without ever accessing the drive (unless you are saving a document for example). Highly recommended in this instance. Also, don't create a swap partition (no matter which distro you choose).

---

### Post by *g!t5^_)*(H on 2009-10-29
I'm using 'standard' Karmic on Acer Aspire One with 8GB SSD. The disk is very (very) slow and it doesn't matter if you use Gnome, Xubuntu or Puppy, if firefox or update manager are writing into SSD all the system will stop for some seconds.

I solved it installing the system into an SDHC card running at the 'storage expansion' slot. If you try it be careful, the card has to be as fast as possible (I'm using an 8GB card with 30M/s of read AND WRITE, I bought it for 50&#8364; some months ago and I'm sure there are cheaper cards now, but I don't recommend you tu use a slower card). 

This way, the system works VERY WELL !!!!!!!!!!

If you want to proceed as I did:

> A. Install Ubuntu using a USB 'live unit' with :

148 MB partition on SSD (internal disk) as /boot
The rest of SSD as /media/extra (I use the SSD as extra storage)

750 MB partition on SDHC card as <swap>
The rest of SDHC card as /

B. When Ubuntu installation is done DON'T RESTART. From the live USB open a terminal (Applications>Accessories>Terminal) and:

1. Type: sudo gedit /etc/initramfs-tools/modules
2. Add the following lines at the end of the file:

mmc_core
mmc_block
sdhci
sdhci-pci

3. Save the file.

4. Type: sudo /usr/sbin/update-initramfs.distrib -u

5. Mount the SSD (boot) unit clicking at Places>148 MB Filesystem

6. Copy the file into de boot folder from SSD:

sudo cp /boot/initrd.img-* /media/X (X is the SSD folder, can be a very long name like: ad73823737a-3923f98-k09sd8f798sd)

7. Umount the SSD

8. Mount SD HC unit clicking at Places>(Unit size, in my case 7.4 GB Filesystem)

9. Add the following lines at the end of the file (/etc/initramfs-tools/modules) from the SD HC card:

sudo gedit /media/Y/etc/initramfs-tools/modules (Y is the SD HC folder, can be a very long name like: daba2355f-3454...)

mmc_core
mmc_block
sdhci
sdhci-pci

10. Save the file.

10. Restart ubuntu, and remove the USB live Ubuntu (In my case there's a message error at GRUB2, but it still works after some seconds)

11. When Ubuntu is running from SD HC type into a terminal: "sudo chmod 777 /media/extra" in order to allow Read and Write from the 'extra' space of SSD.

*"I don't know if it's necessary, but when Ubuntu is running again (its first run from SD HC) you can run: sudo /sbin/update-initramfs.distrib -u"*

Espero que te ayude, se trata de la única forma decente que he encontrado para 'salvar' esta máquina y transformala en 'funcional'. :)

---

### Post by gn2 on 2009-10-29
You could fix it permanently by fitting a mechanical hard drive....?

---

### Post by Johnsie on 2009-10-29
Puppy Linux

---

### Post by drawkcab on 2009-10-29
> **snowpine said:**
> Smaller distros (Puppy, DSL, SliTaz, even AntiX) have the ability to load completely into RAM at boot time, then run without ever accessing the drive (unless you are saving a document for example). Highly recommended in this instance. Also, don't create a swap partition (no matter which distro you choose).

^^^This is a good idea but I'm not sure how mom will react to a distro like puppy.

---

### Post by wilee-nilee on 2009-10-29
Go to the acer site and make sure the bios is up to date, before you do anything.

---

