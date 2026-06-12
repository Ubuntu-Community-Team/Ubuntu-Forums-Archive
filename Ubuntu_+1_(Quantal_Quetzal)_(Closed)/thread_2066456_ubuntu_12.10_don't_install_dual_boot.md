---
title: "ubuntu 12.10 don't install dual boot"
date: 2012-10-04
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Carlos Araujo on 2012-10-04
HW: Dell Inspiron 5423 (ultrabook)
SW: Windows 7 Home Premium (64 bits)

Intel Rapid Start Manager

Problem: the installer crash, disks do not appear.

some solution?

---

### Post by dino99 on 2012-10-04
use a livecd or liveusb to boot on, then reinstall grub :

sudo grub-install /dev/sda

then reboot

---

### Post by Carlos Araujo on 2012-10-04
3 attempts using your tip. failed, grub does not work

---

### Post by cariboo on 2012-10-05
You have to chroot the patition that Ubuntu is installed on, in order to install grub. To do so boot from the Live CD and use the following commands:

[LIST=1]
[*]sudo mount /dev/sdXX /mnt
[*]sudo mount -o bind /dev /mnt/dev
[*]sudo mount -o bind /sys /mnt/proc
[*]sudo mount -o bind /proc /mnt/proc
[*]sudo chroot /mnt
[/LIST]

**Note:** /dev/sdXX = the partion where you have / installed on.

---

### Post by oldfred on 2012-10-05
The Intel Rapid systems seem to be some sort of RAID.

 Intel Smart Response Technology & Dell XPS
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Some info on re-instating 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

---

### Post by Bashing-om on 2012-10-05
Carlos Araujo; Hi !
A new machine ? 
Does it use UEFI as boot partition ?
What is the format scheme ? GPT ?
and ..are you able to boot up ubuntu in the "try ubuntu" mode ?

Further advise pending your response.

[INDENT]kind regards <==BDQ

[/INDENT]

---

### Post by Carlos Araujo on 2012-10-05
My friends, thanks for everything. All info system this here. OR, simple this

Fabricante do sistema	Dell Inc.	
Modelo do sistema	Inspiron 5423	
Tipo do sistema	x64-based PC	
Processador	Intel(R) Core(TM) i7-3517U CPU @ 1.90GHz, 1901 Mhz, 2 Núcleo(s), 4 Processador(es) Lógico(s)	
Versão/data do BIOS	Dell Inc. A03, 03/08/2012	
Versão do SMBIOS	2.7	
Pasta do Windows	C:\Windows	
Pasta do sistema	C:\Windows\system32	
Dispositivo de inicialização	\Device\HarddiskVolume2	
Localidade	Brasil	
Camada de Abstração de Hardware	Versão = "6.1.7601.17514"	
Nome de usuário	carlos-PC\carlos	
Fuso horário	Hora Padrão Brasil Central	
Memória Física (RAM) Instalada	8,00 GB	
Memória física total	7,88 GB	
Memória física disponível	6,10 GB	
Memória virtual total	15,8 GB	
Memória virtual disponível	13,5 GB	
Espaço do arquivo de paginação	7,88 GB

---

### Post by oldfred on 2012-10-05
Even though you have not installed yet, this may provide some good info on how system is configured for Booting and drive layout.

Post link to BootInfo report. 

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by Carlos Araujo on 2012-10-05
News Screens problem report, including ubiquity crash

I reported several bugs in launchpad (Ubiquitous) and grub . attachments

---

### Post by kansasnoob on 2012-10-05
I just remembered seeing you comment on one of my old bug reports here:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/727842](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/727842)

And I see you opened a new bug here:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1059245](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1059245)

According to the info apport collected in the latter report the installation media =

> LiveMediaBuild: Ubuntu 11.04 "Natty Narwhal" - Alpha i386 (20110302)

So, putting two and two together makes me think that your attempt to create a 12.10 Beta 2 live USB is failing to work properly :confused:

---

### Post by Carlos Araujo on 2012-10-05
I downloaded the version 12.10, using USB to install.See the attached files (today)

---

### Post by Carlos Araujo on 2012-10-05
> **Bashing-om said:**
> Carlos Araujo; Hi !
A new machine ? 
Does it use UEFI as boot partition ?
What is the format scheme ? GPT ?
and ..are you able to boot up ubuntu in the "try ubuntu" mode ?

Further advise pending your response.

[INDENT]kind regards <==BDQ

[/INDENT]

UEFI destroys the installation win7 ?-(

---

### Post by Carlos Araujo on 2012-10-05
Today news problems (12.10 USB ISO !!)

From: [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by Carlos Araujo on 2012-10-05
not my friend downloaded here [http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386](http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386)

---

### Post by arpanaut on 2012-10-05
> **oldfred said:**
> Even though you have not installed yet, this may provide some good info on how system is configured for Booting and drive layout.

Post link to BootInfo report. 

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
If you would please do as this post suggests and "Create Bootinfo" report with Boot Repair, see link. And provide the link to it.
Then someone may be able to offer assistance. The information you have provided is not sufficient for anyone to give good advice.

Thank You!

---

### Post by kansasnoob on 2012-10-05
I don't think boot info will help us much with an installer crash ;)

But I'm very curious where the info provided here came from:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1059245](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1059245)

Among those last screenshots you included:

[ATTACH]225130[/ATTACH]

So what happens if you click on "Continue"?

Apport should collect, and add a whole bunch of info to the **new bug report** similar to this:

[ATTACH]225131[/ATTACH]

Then we can attempt to parse that info to see what may be wrong :)

---

### Post by Rukiri on 2012-10-05
Okay, your going to want to manually install grub2 and get the latest version from github or source forge.

Follow these commands and you'll be fine.

mount /dev/sxx /mnt
mount /dev/sda1 /mnt/boot
mount --rbind /proc /mnt/proc
mount --rbind /dev /mnt/dev
mount --rbind /sys /mnt/sys
chroot /mnt

now do apt-get upgrade and make sure your repos and source list are updated. 

Since I can't find a grub2 repo just install bzr and do the following.
bzr branch [http://bzr.savannah.gnu.org/r/grub/trunk/grub](http://bzr.savannah.gnu.org/r/grub/trunk/grub)

Now it's time to install our boot loader.
grub2-mkconfig -o /boot/grub2/grub.cfg
grub2-install --boot-directory=/boot --no-floppy --recheck --debug /dev/sda

if everything went well you should receive 0 errors and you can dual boot, but be sure to edit your grub.cfg file and add any other OS you wish to boot into.

If windows is complaining "it's normal"
insert your Windows DVD and click on Repair Computer, click command line.
now.
BOOTREC.exe  (it will give you a few options, you want to use fix mbr and fix boot.)

now try and boot into windows, if successful you can boot into ubuntu as well.

Hope this helps.

---

### Post by Carlos Araujo on 2012-10-05
look this, please.

---

### Post by arpanaut on 2012-10-05
I don't believe that the OP has had the installer to complete.

From what I can see from the posted spec's he has a 500 Gig HDD and a 8 Gig SSD.
The Intel Rapid Start Manager is a raid implementation that will cause the drives to not appear as in the screenshot (unless the OP has disabled this function)

He has checked the apply updates during install and that is probably causing ubiquity to crash when the new kernel is trying to install.
I can't see how the installation is even proceeding if drives are not visible hence not able to be re-sized, partitioned et. al. 

Another impending issue is the dual video cards on this laptop.  An ongoing issue w/ Linux. I know very little about this.

I think that the OP needs to reference the information provided by oldfred in Post #5 of this thread.
If that issue is cleared up I'd be surprised if the install did not proceeded correctly.
To know the setup of the partitions, state of the system, etc. was why I suggested the results of the Bootinfo script be posted.

Hope this Helps.

---

### Post by Carlos Araujo on 2012-10-05
all the talk is useful, but, will not be possible that Linux can not support new configurations? I feel frustrated. We simply want install/use, I love free software and our community Ubuntu.

wrong in buying a new notebook? 

ps: I am just a User, not power user :-)

---

### Post by kansasnoob on 2012-10-05
Look here:

[ATTACH]225140[/ATTACH]

You must say "yes" for the crash to be properly reported.

At that point in the installation it's doubtful that you've even entered a password anyway, regardless the installation failed ;)

Almost off-topic but I'm also surprised that the full translation is not complete :confused:

I'm an old, lazy American and when I was schooled in Nebraska they didn't think foreign language was important so the best I can do is depend on google translations :(

This is surely a bug!

---

### Post by arpanaut on 2012-10-05
> **Carlos Araujo said:**
> all the talk is useful, but, will not be possible that Linux can not support new configurations? I feel frustrated. We simply want install/use, I love free software and our community Ubuntu.

wrong in buying a new notebook? 

ps: I am just a User, not power user :-)

No you were not wrong to buy new hardware, but you need to understand that it takes time for linux to catch up with new implementations concerning drivers, OEM setups, MS insisting that OEM's set up in certain ways.  
No it is not a great situation for people who want to run Linux.  Especially for newcomers to Linux.  

You have some options here:  
1. give up on Linux
2. Install using wubi and learn more about using Linux and research the issues here.
3. Take the time to research these issues concerning your hardware setup, make a plan to achieve what you want to accomplish, then with the help of the people here execute your plan to get Ubuntu installed. It's going to take some time and efort on your part.

p.s.  wubi is not a permanent solution for Ubuntu use.

I feel your pain, back in 2004 I researched and studied for over a month before I became confident enough to try an install of Ubuntu.  Back up your important data before you make major changes to your system!

Good Luck.

---

### Post by Carlos Araujo on 2012-10-05
I will not give up, using Ubuntu since the first version. it's just a stone in the road! ;)

---

