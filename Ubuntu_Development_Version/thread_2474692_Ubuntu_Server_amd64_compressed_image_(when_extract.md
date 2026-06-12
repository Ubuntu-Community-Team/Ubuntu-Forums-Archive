---
title: "Ubuntu Server amd64 compressed image (when extracted) boots in UEFI and BIOS mode"
date: 2022-05-05
forum: Ubuntu Development Version
---

### Post by sudodus on 2022-05-05
[SIZE=4]Official Ubuntu Server compressed image file (when extracted and flashed to a drive) boots in UEFI and BIOS mode[/SIZE]

In Kinetic Kudu, to be released as 22.10, **Ubuntu Server is distributed as a compressed image file**. When extracted to a drive, it is an **installed system that can boot PC computers both in UEFI mode and BIOS mode**.

This is great, because it makes it very easy to make portable servers as well as desktops with Ubuntu Desktop, Ubuntu community flavours and of course Ubuntu systems with lightweight desktop environments or window managers.

[hr][/hr]
You can get the Ubuntu Server compressed image via

[kinetic-preinstalled-server-amd64.img.xz](http://cdimage.ubuntu.com/ubuntu-server/daily-preinstalled/pending/kinetic-preinstalled-server-amd64.img.xz)

or
```

zsync http://cdimage.ubuntu.com/ubuntu-server/daily-preinstalled/pending/kinetic-preinstalled-server-amd64.img.xz.zsync

```
When downloaded (and checked with sha256sum) you can flash it to an internal or external drive with [mkusb-dus](https://help.ubuntu.com/community/mkusb)
```

dus kinetic-preinstalled-server-amd64.img.xz

```
[hr][/hr]
User: ubuntu
Password: ubuntu (and you are prompted to change it directly after the first login)

---

### Post by sudodus on 2022-05-18
There is also the discussion with Ubuntu developers at [this link](https://discourse.ubuntu.com/t/official-ubuntu-server-tarball-for-amd64/28336/)

---

### Post by sudodus on 2022-05-21
**I played with the Ubuntu Server amd64 compressed image from yesterday**
```

-rw------- 1 sudodus sudodus 863993716 maj 20 03:24 kinetic-preinstalled-server-amd64.img.xz

```
extracted it to a USB pendrive, booted into it, let the root partition expand with some margin to fill a 32 GB drive

logged in with the default

user name: **[COLOR="#0000CD"]ubuntu[/COLOR]**
original password: **[COLOR="#0000CD"]ubuntu[/COLOR]** (for the preinstalled server image)
and changed to
new password: **[COLOR="#0000CD"]changeme[/COLOR]** (for the 'Lubuntized' image)

This Ubuntu Server runs in text mode as usual, and ssh is activated by default.

**Then I made 'Lubuntu',**
```

sudo apt update
sudo apt full-upgrade
sudo apt install lubuntu-desktop

```
Lubuntu made like this works both in UEFI mode and BIOS mode, just like the original Ubuntu Server. The boot structure seems stable. I made a new compressed image
```

-rw-r--r-- 1 root root 1705181816 maj 21 07:12 dd_unb_lubuntu-kinetic_31GB_22-05-21.img.xz

```
As you notice, the size is twice that of the compressed server image, but smaller than the corresponding Lubuntu iso file
```

-rw------- 1 sudodus sudodus 2646388736 maj 20 17:21 kinetic-desktop-amd64.iso

```

See the attached screenshot.

If you think it is a good idea, I can upload the 'Lubuntized' compressed image file and make it available publicly. But I think most people will prefer to download the official Ubuntu Server amd64 compressed image and tweak the system themselves.

If you want to use the whole drive (typical case with an external high-end USB pendrive or {SSD + adapter to USB}) for a portable installed system, this is easier and more likely to succeed compared to installing from an iso file.

---

### Post by sudodus on 2022-06-12
Today I found a **Jammy preinstalled server** too (so not only Kinetic). You can find it in the following directory

[cdimage.ubuntu.com/ubuntu-server/jammy/daily-preinstalled/current/](http://cdimage.ubuntu.com/ubuntu-server/jammy/daily-preinstalled/current/)

where there is also a SHASUM for it.

This might be a *real alternative* for people who have problems with the subiquity installer and/or are missing the Ubuntu **[FONT=Courier New]mini.iso[/FONT]** *but it grabs the whole drive* (there is no 'install alongside').

Enjoy :-)

[HR][/HR]
This preinstalled image of an established LTS version is rather stable, but it is provided for testing purposes. Sometimes the **proposed repositories will contain code for testing**, in other words, code that is not tested yet, so it may cause problems.

*If you want to use such a system made from the Jammy preinstalled server image regularly (not only for testing), you should **inactivate** the proposed repositories* (delete the line(s) or put # at the left end of the line to make it/them a comment).

```

deb http://archive.ubuntu.com/ubuntu/ jammy-proposed main restricted
--->
**#** deb http://archive.ubuntu.com/ubuntu/ jammy-proposed main restricted

```
in the file **[FONT=Courier New] /etc/apt/sources.list.d/proposed.list[/FONT]**

You can check for all proposed repositories with the following commands
```

ubuntu@ubuntu:~$ [COLOR="#0000cc"]find /etc/apt/ -type f -path '*source*' -exec grep --color -H proposed {} \;[/COLOR]
[COLOR="#800080"]/etc/apt/sources.list.d/proposed.list:[/COLOR]deb http://archive.ubuntu.com/ubuntu/ jammy-[COLOR="#FF0000"]proposed[/COLOR] main restricted

ubuntu@ubuntu:~$ [COLOR="#0000cc"]cat /etc/apt/sources.list.d/proposed.list [/COLOR]
deb http://archive.ubuntu.com/ubuntu/ jammy-proposed main restricted
ubuntu@ubuntu:~$ 

```

In this case we find only one file with one line (pointing to two proposed repositories: main and restricted).

---

### Post by #&amp;thj^% on 2022-06-12
> **sudodus said:**
> Today I found a Jammy preinstalled server too (so not only Kinetic). You can find it in the following directory

[cdimage.ubuntu.com/ubuntu-server/jammy/daily-preinstalled/current/](http://cdimage.ubuntu.com/ubuntu-server/jammy/daily-preinstalled/current/)

where there is also a SHASUM for it.

This might be a *real alternative* for people who have problems with the subiquity installer and/or are missing the Ubuntu **[FONT=Courier New]mini.iso[/FONT]** *but it grabs the whole drive* (there is no 'install alongside').

Enjoy :-)

Nice find sudodus, thanks for the heads up on " grabs the whole drive" i would think anyone installing a server only would have already built  a partition for the install, and again maybe not.;)

---

### Post by grahammechanical on 2022-06-12
My question is this:

Once this server image is put on a drive is it the installed OS or does it come with an installer to be used to put Ubuntu server on another drive?

I am trying to understand the point of this image. I suspect it is another of the software experiments that Canonical has played with over the years. In the past I experimented with personal_X86.img (Snappy Ubuntu Desktop Next) and amd64-all-snap.image.xz. Both were attempts to produce an immutable Ubuntu desktop based on snap packages and using Mir and Unity 8. They worked after a fashion. All they needed were some snap applications to install. 

Regards

---

### Post by sudodus on 2022-06-13
@ grahammechanical,

Once this server image is put on a drive it is the installed OS. There is no installer involved, only extraction from the compressed image file to the device, **[FONT=Courier New]/dev/sdx[/FONT]** (some tools, for example mkusb, can do it 'directly', otherwise you extract to a file in step one and clone from the file in step two. This is like installing an operating system into a Raspberry Pi.

A developer writes that it is provided because the group of developers want it. Obviously it makes the development and testing easier. It is there, and some users like us might find it useful too, because it is very easy to create a working system from this kind of compressed image file.

---

### Post by C.S.Cameron on 2022-06-14
This sounds similar to: [https://askubuntu.com/questions/1300454/easy-full-install-usb-that-boots-both-bios-and-uefi](https://askubuntu.com/questions/1300454/easy-full-install-usb-that-boots-both-bios-and-uefi)
Installing with image files sounds like the future to me.

---

### Post by sudodus on 2022-06-14
@C.S.Cameron,

Yes, I think so too. It should be a standard case to let the system install to the whole drive.

Installing alongside on one drive will probably be a special case. It should be good enough with modern computers to use virtual machines, where a whole virtual drive can be used, or machines with more than one drive (for example a fast USB 3 SSD).

---

### Post by C.S.Cameron on 2022-06-15
I see several sites that provide VBox images of Ubuntu.
I have converted Full installed Ubuntu Image files, (.img), to VBox, (.vdi), and it worked OK.
.vdi to .img also works.

---

### Post by sudodus on 2022-11-18
There is a compressed image of Lunar now:

[Ubuntu Lunar Preinstalled Server](http://cdimage.ubuntu.com/ubuntu-server/daily-preinstalled/current/)

Its amd64 version works for me, when extracted and cloned to a USB drive.

---

### Post by sudodus on 2023-04-24
[SIZE=3]You can install Ubuntu Server this way directly using data transfer with **[FONT=Courier New]nc[/FONT]** (netcat)[/SIZE]

This makes it easier to install into a virtual machine with a single virtual internal drive (with a bridged network):

- Boot into a live system via a virtual optical disk. (I tested by connecting to a Lubuntu 22.04 LTS iso file.)

- In the virtual machine:

     Check with **[FONT=Courier New]ip a[/FONT]** the own IP address (192.168.0.32 assumed here)

     Start by using **[FONT=Courier New]nc[/FONT]** to listen on a specific port,
     with output captured into a file:
```

     sudo bash -c 'nc -l 1234 > /dev/sdx'  # double-check the target drive

```

- In the host machine or some other machine that is connected via a network:

Connect to the listening **[FONT=Courier New]nc[/FONT]** process, feeding it the file which is to be transferred:
```

     xzcat -c ubuntu-preinstalled-server-amd64_23.04.img.xz  | nc -N 192.168.0.32 1234

```

- In the virtual machine, when the transfer has finished, flush the buffers.
```

     sync

```

- Reboot into the virtual machine's virtual internal drive /dev/sdx, and you are running Ubuntu Server.


You can find more details at **[FONT=Courier New]man nc[/FONT]**

[HR][/HR]
It probably also works to extract the compressed image file and convert the extracted file to a vdi file (or some other format for virtual drive storage), but I have not done that.

---

### Post by tea for one on 2023-04-24
> **sudodus said:**
> There is a compressed image of Lunar now:
[Ubuntu Lunar Preinstalled Server](http://cdimage.ubuntu.com/ubuntu-server/daily-preinstalled/current/)
Its amd64 version works for me, when extracted and cloned to a USB drive.
An interesting project - I decided to have a closer look.
Using the Lunar compressed image and adding lubuntu-desktop, I found that Firefox is missing (probably because it is a snap package now)
Another step needed to be comparable to an official Lubuntu ISO.

---

### Post by sudodus on 2023-04-24
Thanks for the heads up @tea for one,

I will look into it and see if I can add a suitable command to install Firefox.

(It seems to be a bug, that Firefox would come with the meta package.)

[hr][/hr]
Edit: After installing Lubuntu and rebooting
```

sudo apt install lubuntu-desktop
# or if you want to reduce the size
sudo apt install --no-install-recommends lubuntu-desktop

```

I think the following command line brings an installation of Firefox similar to that of a normally installed Lubuntu.
```

sudo snap install firefox

```

It can be maintained via the following command.
```

sudo snap refresh

```

---

### Post by sudodus on 2023-04-24
[SIZE=3]Extract and convert to a vdi file with the following commands (if VirtualBox)[/SIZE]

```

# extract
xzcat ubuntu-preinstalled-server-amd64_23.04.img.xz | pv > ubuntu-preinstalled-server-amd64_23.04.img

# convert
VBoxManage convertdd ubuntu-preinstalled-server-amd64_23.04.img ubuntu-preinst-server.vdi

# increase size from approx 3.5 GiB to approx 10 GiB
VBoxManage modifymedium disk ubuntu-preinst-server.vdi --resize 10240

# convert from dynamic to fixed size (optional)
VBoxManage clonemedium disk ubuntu-preinst-server.vdi ubuntu-preinst-server-fixed.vdi --variant fixed

# Check the result
VBoxManage showmediuminfo disk ubuntu-preinst-server.vdi
VBoxManage showmediuminfo disk ubuntu-preinst-server-fixed.vdi

```

Now you can start VirtualBox and import/attach your virtual drive into the virtual machine.

See more details in

[how-to-convert-img-file-to-vdi-file-using-oracle-virtualbox](https://ostechnix.com/how-to-convert-img-file-to-vdi-file-using-oracle-virtualbox/)

[how-to-enlarge-a-virtual-machines-disk-in-virtualbox-or-vmware](https://www.howtogeek.com/124622/how-to-enlarge-a-virtual-machines-disk-in-virtualbox-or-vmware/)

[how-to-convert-between-fixed-and-dynamic-disks-in-virtualbox](https://www.howtogeek.com/312456/how-to-convert-between-fixed-and-dynamic-disks-in-virtualbox/)

---

