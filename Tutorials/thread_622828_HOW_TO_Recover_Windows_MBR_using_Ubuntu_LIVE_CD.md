---
title: "HOW TO: Recover Windows MBR using Ubuntu LIVE CD"
date: 2007-11-25
forum: Tutorials
---

### Post by inoxllor on 2007-11-25
**Tested on Ubuntu 7.04; Ubuntu 7.10 and Linux Mint 4.0 Live CDs**

If want to restore Windows Bootloader and for some reason cannot use the windows installation cd, there is a simple way to do it:

NOTE: make sure you have internet working.

1) Boot with Ubuntu Live CD or Linux Mint Live CD


2) On the terminal: 

   **sudo apt-get install ms-sys** 

then

   **ms-sys --mbr /dev/hdX **

NOTE: in my case the main windows xp system is located in hda1 so I used ms-sys --mbr /dev/hda

3) Reboot. 

This should get your windows back. :D

---

### Post by gonk on 2008-01-07
Brilliant!  Thanks for this, it worked well.

However I needed to enable the 'universe' repository (System->Administration->Software Sources) before I could install the ms-sys package.  I also needed to put "sudo" in front of the ms-sys command (e.g. "sudo ms-sys --mbr /dev/sda") otherwise I got permission denied.

---

### Post by KingdomKid on 2008-02-12
Hey guys, I recently cloned my hard drive. Every thing worked ok and still does except that I can not boot into windows anymore. I have a dual boot system (Kubuntu / Windows XP Pro).
I can boot into Kubuntu fine and all is well. Just booting into XP is messed up.

When I choose to boot into XP it just sits there with "starting up" in the top left of the screen.

I was wondering if doing the steps in this post is what I need to do?

Does anyone know what got messed up during the cloning process and how to fix it.

---

### Post by HungrySamurai on 2008-02-20
It has taken me a week to find a solution that worked -- and it worked so smoothly!  Thank you!  Now that the desktop PC is back in working order, my wife and I will not be fighting for the laptop!

---

### Post by fluteman on 2008-02-25
> **inoxllor said:**
> **Tested on Ubuntu 7.04; Ubuntu 7.10 and Linux Mint 4.0 Live CDs**

If want to restore Windows Bootloader and for some reason cannot use the windows installation cd, there is a simple way to do it:

NOTE: make sure you have internet working.

1) Boot with Ubuntu Live CD or Linux Mint Live CD


2) On the terminal: 

   **sudo apt-get install ms-sys** 

then

   **ms-sys --mbr /dev/hdX **

NOTE: in my case the main windows xp system is located in hda1 so I used ms-sys --mbr /dev/hda

3) Reboot. 

This should get your windows back. :D


Hi, I'm having the exact same problem as inoxllor and I was really excited about trying the solution you suggested.  So I loaded the Ubuntu Live CD, executed installed ms-sys and executed the commands the (I too had to set software to "universe" to install ms-sys and I also needed to use the sudo, as well as the "-f" switch when I ran ms-sys).  However, this did not resolve my problem - when I shut down my system and rebooted, GRUB is still trying to load and my system just hangs at the GRUB load error message.

Any other ideas?  I've tried everything solution I could find and none of them have worked.  Help!
fluteman:confused:

---

### Post by ajproart on 2008-04-02
:guitar: 

THANKS TO INOXLLOR & GONK THE FINAL FIX WOULD BE SOMETHING LIKE THIS:

[COLOR="Red"]HOW TO: Recover Windows MBR using Ubuntu LIVE CD
Tested on Ubuntu 7.04; Ubuntu 7.10 and Linux Mint 4.0 Live CDs[/COLOR]

If want to restore Windows Bootloader and for some reason cannot use the windows installation cd, there is a simple way to do it:

[COLOR="Red"]**NOTE: make sure you have internet working.**[/COLOR]

Before the first step:
[COLOR="Yellow"][COLOR="Red"](I needed to enable the 'universe' repository (System->Administration->Software Sources) before I could install the ms-sys package. I also needed to put "sudo" in front of the ms-sys command (e.g. "sudo ms-sys --mbr /dev/sda") otherwise I got permission denied.)[/COLOR][/COLOR]

1) Boot with Ubuntu Live CD or Linux Mint Live CD


2) On the terminal:

sudo apt-get install ms-sys

then

ms-sys --mbr /dev/hdX

NOTE: in my case the main windows xp system is located in hda1 so I used 

sudo ms-sys --mbr /dev/hda

***
ubuntu@ubuntu:~$ sudo ms-sys --mbr /dev/hda
Windows 2000/XP/2003 master boot record successfully written to /dev/hda
***

3) Reboot.:KS

This should get your windows back.
__________________
Thanks Reply With Quote

---

### Post by musico218 on 2008-05-04
Hi everyone!

I've tried to fix mbr with ubuntu live cd, but now it appears:

       Invelid partition table

Notice: I'm working on a laptop asus, with 2 partions (one recovery, and one with windows and all my dates).


Help!!!

---

### Post by tom56 on 2008-05-04
> **musico218 said:**
> Hi everyone!

I've tried to fix mbr with ubuntu live cd, but now it appears:

       Invelid partition table

Notice: I'm working on a laptop asus, with 2 partions (one recovery, and one with windows and all my dates).


Help!!!

This happened to me too. I don't think ms-sys works with Vista. Another (easier?) way is to use the Windows Recovery CD which is available for download here - [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/). Go through the various options then pick "Startup Recovery". Works a charm.

---

### Post by zorkerz on 2008-11-08
It does not appear ms-sys is in the repos for intrepid any longer.

---

### Post by Rutiio464 on 2008-11-08
Thanks! Bump!&#12288;He wiped the dust off and gently wrapped it in brown paper. Then he placed the parcel in Reuben's hands.&#12288;&#12288;Racing home, Reuben burst through the front door. His mother was scrubbing the kitchen stove. &#8220;Here, Mum! Here!&#8221;Reuben exclaimed as he ran to her side. He placed a small box in her work roughened hand.&#12288;&#12288;She unwrapped it carefully, to save the paper. A blue-velvet jewel box appeared. Dora lifted the lid, tears beginning to blur her vision.&#12288;&#12288;In gold lettering on a small, almond-shaped brooch was the word Mother.&#12288;&#12288;It was Mother's Day, 1946.&#12288;&#12288;Dora had never received such a gift; she had no finery except her wedding ring. Speechless, she smiled radiantly and gathered her son into her arms.Come and buy [age of conan gold](http://www.aocgoldweb.com), AoC Gold, AoC Power Leveling and AoC Accounts here, [aoc gold](http://www.aocgoldweb.com) the easiest and safest way to enjoy a wonderful Age of Conan life! [aoc power leveling](http://www.aocgoldweb.com/the-age-of-conan-power-leveling-aoc.asp),  [aoc power leveling](http://www.aocpowerleveling-gold.com), [age of conan power leveling](http://www.aocpowerleveling-gold.com/the-age-of-conan-power-leveling-aoc.asp)..

---

### Post by caljohnsmith on 2008-11-08
> **zorkerz said:**
> It does not appear ms-sys is in the repos for intrepid any longer.
Yes, unfortunately that is the case. You could download that package from packages.debian.org and do it that way, but there are many ways to install a Windows type MBR though, including:
```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/[COLOR="Red"]sda[/COLOR]
```
And replace sda if you want to install the MBR to a different drive. Or another method:
```
sudo apt-get install mbr
sudo install-mbr -i n -p D -t 0 /dev/[COLOR="Red"]sda[/COLOR]
```
Both the "syslinux" and "mbr" packages are available in the repositories. I should mention that all a Windows MBR does is attempt to boot whichever partition on the HDD is marked as bootable, or active, so there are many open-source boot loaders that do exactly the same thing, including the two methods given above. :)

---

### Post by Sakae on 2008-11-13
Hey guys, how`s going?

I erased the Ubuntu partition using a Partition program (can't remember what, but it doesn't matter anyway), and got a problem with "stage1" of GRUB on (my 2nd) reboot (1st one was to apply the changes made on partitions).

Now I need to recover Master Boot to load Windows XP (SDA) instead of GRUB, and was going nuts reading things about the ms-sys package (that I can't install using make/make install).

So, I tried the first code caljohnsmith wroted:

```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
```

And did not worked. Now it returns a message "PRESS A KEY TO REBOOT" instead of GRUB message.

Anyone has a idea?

---

### Post by caljohnsmith on 2008-11-13
How about first posting:
```
sudo fdisk -lu
```
Also, when you did those commands you mention, did they return any errors?

---

### Post by Sakae on 2008-11-13
fdisk -lu returns this:

```
Disco /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total de 80293248 setores
Units = setores of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Dispositivo Boot Início Fim Blocos Id Sistema
/dev/sda1   *          63    80292869    40146403+   7  HPFS ou NTFS
```

And the commands you wrote about syslinux and other (I tried the second too, it didn't worked also), haven't return any error. It says something about recording a few bytes on mbr, if I remember.

ps.: I'm typing from Live CD now, indeed.

---

### Post by caljohnsmith on 2008-11-13
So was Windows working OK on that drive before you got rid of Ubuntu? It looks like you resized the Windows partition to use the full amount of space on that drive after you deleted the Ubuntu partitions, is that true? That might be your problem. But you don't remember which partition program you used? That could be an issue if you resized the Windows partition. And was Windows originally the first partition on that HDD? 

Also, does the following command return "Missing operating system":
```
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```

---

### Post by Sakae on 2008-11-13
> So was Windows working OK on that drive before you got rid of Ubuntu? It looks like you resized the Windows partition to use the full amount of space on that drive after you deleted the Ubuntu partitions, is that true? That might be your problem. But you don't remember which partition program you used? That could be an issue if you resized the Windows partition. And was Windows originally the first partition on that HDD?

Yes, Windows was working great. I mean, I did resized the Win partition to 100% of disk, using [Partition Table Doctor](http://www.ptdd.com/download.htm) from EASEUS, and it already applied the changes. I erased the Ubuntu partition (REISERFS) and SWAP too, that's why I [s]suspect[/s] am pretty sure GRUB is dead by now.

Also, Windows wasn't the first partition on HD, but Ubuntu. Once I googled for GRUB conf to change this, but I haven't success.

> Also, does the following command return "Missing operating system":

No, it doesn't. I'm pretty sure Windows is working fine, but I can't access it...

One more thing, I found a lot of solutions for this problem, including using Windows XP CD (recover), but the *** here couldn't remember the password (if I ever setted one). I know there is one cd image that erases this pass, but the link was broken, so... I've looke for alternative solutions, and this one seems the better and faster.

---

### Post by caljohnsmith on 2008-11-13
> **Sakae said:**
> 
Also, Windows wasn't the first partition on HD, but Ubuntu. 
That's unfortunately a big problem if Windows was not physically the first partition on the drive, and now it is. So did you move the Windows partition to use the free space at the beginning of the drive that was freed up when you deleted the Ubuntu partitions, your did you resize the beginning of the Windows partition to extend over that freed space at the beginning of the drive? 

How about posting the full output of the following commands, including the commands themselves (copy/paste the terminal session):
```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```

---

### Post by Sakae on 2008-11-13
> That's unfortunately a big problem if Windows was not physically the first partition on the drive, and now it is. So did you move the Windows partition to use the free space at the beginning of the drive that was freed up when you deleted the Ubuntu partitions, your did you resize the beginning of the Windows partition to extend over that freed space at the beginning of the drive?

No, Windows is physically the first partition on the drive; I resized the end of the Win partition to the end of the drive.

It was: **Win (30gb) / Ubuntu (9gb) / Swap (few mb)**, in that order. Now it's Windows all over the disk (that sucks huh? lol).

> How about posting the full output of the following commands, including the commands themselves (copy/paste the terminal session):

Remember I'm in a Live CD now:

```
ubuntu@ubuntu:~$ sudo apt-get install syslinux
Lendo lista de pacotes... Pronto
Construindo árvore de dependências       
Lendo estado da informação... Pronto
Os pacotes extra a seguir serão instalados:
  mtools
Pacotes sugeridos:
  floppyd
Os NOVOS pacotes a seguir serão instalados:
  mtools syslinux
0 pacotes atualizados, 2 pacotes novos instalados, 0 a serem removidos e 1 não atualizados.
É preciso fazer o download de 557kB de arquivos.
Após esta operação, 1253kB adicionais de espaço em disco serão utilizados.
Quer continuar [S/n]? S
Obtendo:1 http://archive.ubuntu.com hardy/main mtools 3.9.11-0ubuntu1 [204kB]
Obtendo:2 http://archive.ubuntu.com hardy/main syslinux 2:3.53-1ubuntu2 [353kB]
Baixados 557kB em 21s (25,9kB/s)                                               
Selecionando pacote previamente não selecionado mtools.
(Lendo banco de dados ... 98423 arquivos e diretórios atualmente instalados.)
Descompactando mtools (de .../mtools_3.9.11-0ubuntu1_i386.deb) ...
Selecionando pacote previamente não selecionado syslinux.
Descompactando syslinux (de .../syslinux_2%3a3.53-1ubuntu2_i386.deb) ...
Instalando mtools (3.9.11-0ubuntu1) ...

Instalando syslinux (2:3.53-1ubuntu2) ...
```

```
ubuntu@ubuntu:~$ sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
0+1 registros entrando
0+1 registros saindo
410 byte (410 B) copiados, 0,0256682 s, 16,0 kB/s
```

```
ubuntu@ubuntu:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
Missing operating system.
```

On this third command, now it returns the error message. Praying to have a solution besides format my PC...

---

### Post by caljohnsmith on 2008-11-13
OK, that's great it returned "Missing operating system", because that means you have the Windows MBR properly installed (quite ironic, isn't it?). How about rebooting and let me know how far you get booting Windows.

---

### Post by Sakae on 2008-11-13
Cal, it shows a black page with this message: PRESS A KEY TO REBOOT

It's all.

Funny history, I was putting my snickers to go to a lan house write you back. Got error on 1st boot of Live CD, and I was all worried about (because of my deadlines); turn off the computer and start heating water to make chimarrão (don't know the translation to english). So I come back and the Live CD works.

Still stuck on Master Boot Record problem.

ps.: Do you have Messenger? I really need to get this working today, all my files are on that partition.

---

### Post by zorkerz on 2008-11-13
You should be able to use the live cd to at least access the files on the partition.

If you have a win xp cd i think that is the easiest method. boot from the cd press R to get into recovery mode and type fixmbr when you get to a command prompt. beyond that Im no help.

---

### Post by Sakae on 2008-11-13
Ok, updating my war against "bad sectors", I finally get to recovery console of Win XP, and could type FIXMBR there.

Received the warning message, proceeded and though: "Now I will access my Windows".

Nothing. Now, instead of receiving a "PRESS A KEY TO REBOOT" message, I just don't get message at all, the computer just stuck loading. Don't know what else to do.

Tried: 1 - Using the code caljohnsmith provided (apt-get install syslinux and mbr) and 2 - Using Win XP CD recovery (fixmbr and fixboot).

Is there any more ways?

---

### Post by Sakae on 2008-11-15
That kinda sucks. I let my computer on a technical assistance, and they said the HD blow up, even the data.

In other hand, my sister gave me a brand new one of 160 gb.

Best regards all

---

### Post by Scatcat on 2008-11-23
Hi, I really hope someone can help me, i'm quite a noob with computers and my windows also does not want to boot anymore. I now run Ubuntu with the Live Cd, and i want to fix the mbr. i've tried the code:

sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
But I don't know what to choose instead of 'sda'  does anyone know how i can see that?

---

### Post by caljohnsmith on 2008-11-23
> **Scatcat said:**
> Hi, I really hope someone can help me, i'm quite a noob with computers and my windows also does not want to boot anymore. I now run Ubuntu with the Live Cd, and i want to fix the mbr. i've tried the code:

sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
But I don't know what to choose instead of 'sda'  does anyone know how i can see that?
How about first posting:
```
sudo fdisk -lu
```
And when you say that Windows doesn't want to boot any more, what exactly do you mean?

---

### Post by Scatcat on 2008-11-23
Well, If I want to boot Windows it says that windows didn't start properly and aks if I want to reboot in normal or safe mode, and some other options.  But whatever I do I get the windows loading screen and then it automatically restarts and i get the same choices again. 

I tried to restore windows with the windows cd but when I want to use the recovery tool it goes right to the Dos commandscreen,but just a C: prompt (not a C:\WINDOWS prompt).  instead of asking me to log in as Admin (as it supposed to do)

So I used the Ubuntu live-Cd to get my files. But I read here that maybe I could get my windows back so that's what i'm trying to do.

---

### Post by caljohnsmith on 2008-11-23
To do a "Windows Repair", boot your Windows Install CD and choose the "install Windows" option in the first main menu; do not press "r" to go to the recovery console, because that gives you the command prompt like you got. After selecting the "install Windows" option, after that you will be given the option to do a "Windows repair" rather than install Windows. How about trying that and let me know how it goes.

---

### Post by zorkerz on 2008-11-23
If you are getting that far your windows mbr is fine. Do you see a blue screen (as in BSOD) for a second just before it restarts?

If so your computer is set to restart whenever it gets this error which has the unfortunate side effect of you not being able to see the error.

In your breif glimpses of the blue screen look for an error type it will be 0x000000**XX** (replace **XX **with your specific 2 digit letter/number combination) and occasionally there is a file name.

Im jumping the gun here a little its not clear that you have a BSOD yet.

---

### Post by Scatcat on 2008-11-24
Thanks for helping me out,
Yes i'm getting a blue screen for a second but i cannot read it since it reboots after a split second.

If I choose the the "install Windows" option on the cd it aks me to choose a partition the install windows and then says it's too full and i have to format it. Before this I see no Windows Repair option. But since i got my files, I could just format the C disk and re-install windows if there is no other option.

---

### Post by caljohnsmith on 2008-11-24
If the C drive is full, can you access your Windows partition OK from your Live CD? If so, you could go in and delete some files to make some space. If you are unsure which is your Windows partition as seen by the Live CD, how about first opening a terminal (Applications > Accessories > Terminal) and posting:
```
sudo fdisk -lu
```

---

### Post by Scatcat on 2008-11-25
Thank you!

I deleted some files. and then i was able to restore windows using the windows recover option on the cd

I can boot windows again now! Thank you!

---

### Post by zorkerz on 2008-11-25
congrats

---

### Post by geddylee on 2009-02-16
i did the same thing i deleted my linuxmint partitions and extended the end of my windows partition as far as i could and now i can't boot anymore.

I'm having the grub problem with the error 22. I downloaded the ms-sys package installed it and followed the directions, but it still didn't work, my computer still hangs at the grub loading error 22. also when i try to do sudo ms-sys -m/dev/hda(or sda) it says "unable to open -m/dev/sda(hda), no such file or directory".

im at a loss of what to do here. to make it worse, at some point while i was trying the mssys, all partitions dissapeared from my fdisk -l except for sda1 which appears to be the useless recovery partition that comes with my computer. it is set as the boot. the partition containing my windows is hda1. i don't think it's gone because it still shows up in gnome partitioner.

i know this is a really old thread but i really need my computer back and if anyone can help me i would really appreciate it. I feel like i've tried everything

---

### Post by kooljay2 on 2009-04-27
Hello all, I could use your help. I have a Windows XP laptop that won't boot. The msg is "Operating system not found". I tried the XP disc but at the repair option I get a "C" prompt. I enter "FIXMBR" but nothing happens. It just goes to the next line and another C prompt. I used Partition Table Doctor and it seemed to rebuild the partition table, but it said it could not write to the HD because the MBR was missing or corrupt. I tried beginning the XP install process but even though it saw the HD it could not access it. That's what brought me to Ubuntu. By the way, I don't have a floppy drive so I can't use a Win98 boot disk to fix the MBR.
 
I tried the fix listed here but got errors. First, I have v8.04 so I could not download ms-sys. I can go to "Computer" and see the HD, but cannot mount the image. At the error msg I do not get a "Details" option. I opened a terminal window and typed "fdisk -l" but it returned nothing. Same thing using sudo before the command. I tried to force mount it and that failed too. I got to the root ("sudo /bin/bash") and continued trying different commands but my lack of linux language is hampering me.
 
I downloaded ms-sys from sourceforge but I am not that familiar with Linux commands. I extracted it to flash drive but that's as far as I've got. I don't know which folder (bin? root?) to place it so I can access it thru Terminal. Every fix I've read online so far hasn't worked for me.
 
Help me Obi-Wan Kenobi, you're my only hope.
 
Thanks.

---

### Post by caljohnsmith on 2009-04-27
Kooljay2, in order to help troubleshoot your problem, how about downloading the **Boot Info Script** to your Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what might be going on with your HDD.

---

### Post by kooljay2 on 2009-04-27
Thanks. Here's the info:
```

============================= Boot Info Summary: ==============================
 
 => No known boot loader is installed in the MBR of /dev/hda
 => No boot loader is installed in the MBR of /dev/hdc
 
hda1: _________________________________________________________________________
 
    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
 
hda2: _________________________________________________________________________
 
    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
 
hda3: _________________________________________________________________________
 
    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
 
hda4: _________________________________________________________________________
 
    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
 
=========================== Drive/Partition Info: =============================
 
Drive: hda ___________________ _____________________________________________________
 
Partition  Boot         Start           End          Size  Id System
 
Invalid MBR Signature found
/dev/hda1     ?             0            -1                   Unknown
/dev/hda2     ?             0            -1                   Unknown
/dev/hda3     ?             0            -1                   Unknown
/dev/hda4     ?             0            -1                   Unknown
 
 
Drive: hdc ___________________ _____________________________________________________
Note: sector size is 2048 (not 512)
 
Disk /dev/hdc: 728 MB, 728221696 bytes
255 heads, 63 sectors/track, 22 cylinders, total 355577 sectors
Units = sectors of 1 * 2048 = 2048 bytes
 
Partition  Boot         Start           End          Size  Id System
 
Invalid MBR Signature found
 
 
blkid -c /dev/null: ____________________________________________________________
 
/dev/loop0: TYPE="squashfs" 
 
=============================== "mount" output: ===============================
 
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
 
=========================== Unknown MBRs/Boot Sectors/etc =======================
 
Unknown MBR on /dev/hda
 
 
Unknown BootLoader  on hda1
 
 
Unknown BootLoader  on hda2
 
 
Unknown BootLoader  on hda3
 
 
Unknown BootLoader  on hda4
 
 
 
=============================== StdErr Messages: ===============================
 
hexdump: /dev/hda1: No such file or directory
hexdump: /dev/hda1: No such file or directory
hexdump: /dev/hda2: No such file or directory
hexdump: /dev/hda2: No such file or directory
hexdump: /dev/hda3: No such file or directory
hexdump: /dev/hda3: No such file or directory
hexdump: /dev/hda4: No such file or directory
hexdump: /dev/hda4: No such file or directory
```

---

### Post by caljohnsmith on 2009-04-27
It looks like you might have some sort of hardware problem with your HDD, kooljay2, because as you mentioned in your first post and as the Boot Info Script confirmed, it doesn't look like Ubuntu can detect/read your HDD. How about posting the output of:
```
sudo lshw -C disk
```
And how big (GB) is the HDD in question?

---

### Post by kooljay2 on 2009-04-27
It's a 20G hd.
```

ubuntu@ubuntu:~$ sudo lshw -C disk
  *-disk                  
       description: ATA Disk
       product: IC25N020ATCS04-0
       vendor: Hitachi
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: CA2OA71A
       serial: CSH206D9D1LP5F
       size: 18GiB (20GB)
       capacity: 18GiB (20GB)
       capabilities: ata dma lba iordy smart security pm apm
       configuration: apm=off mode=udma5 smart=on
  *-cdrom
       description: DVD reader
       product: TOSHIBA DVD-ROM SD-R2312
       vendor: Toshiba
       physical id: 0
       bus info: ide@1.0
       logical name: /dev/hdc
       logical name: /cdrom
       version: 1905
       serial: 234K603214
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd
       configuration: mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/hdc
          logical name: /cdrom
          configuration: mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted
```

---

### Post by caljohnsmith on 2009-04-27
I can only guess what's going on with your HDD at this point, Kooljay2, because Ubuntu is able to recognize that it is present (the lshw output you posted), yet fdisk can't seem to read from it. From your first post, it sounds like that's basically what happened when you tried to install XP to that HDD, because you said XP saw the HDD but could not access it. If it is only a 20 GB HDD, I'm guessing it must be a bit old, so it may be that it is simply time to replace it. If you want you could try running a SMART HDD test on it first (assuming it has that technology) to check its self-reported health. To see if you can run a SMART test on the HDD, how about trying the following:
```
sudo apt-get install smartmontools
```
First do the following to save the current health status parameters of your HDD to a file on your desktop:
```
sudo smartctl -a /dev/hda > ~/Desktop/hda_health_before_test.txt
```
Then run:
```
sudo smartctl -t long /dev/hda
```
That command will immediately terminate while the HDD begins its self-test, and it could take quite a while. You can monitor the progress with:
```
sudo smartctl -a /dev/hda | grep -A1 -i "self-test execution status"
```
Once the above command says the test is done, then do:
```
sudo smartctl -a /dev/hda > ~/Desktop/hda_health_after_test.txt
sudo smartctl -H /dev/hda
```
And please post the contents of the two files on your desktop so I can see the results (assuming the SMART test was even able to run).

---

### Post by kooljay2 on 2009-04-27
I don't mind if it has to be replaced, but I need to get my data off it. I was hopeful the forc mounting thing would work. At this point any method fo getting the files off the drive would be a welcome solution.
 
I'll try the SMART test and post later. Thanks for your help so far.

EDIT: The SMART tests would not run

---

### Post by kooljay2 on 2009-04-27
I tried another fix. I found this Wiki thread (I know, I know...)
[http://www.wikihow.com/Recover-a-Dead-Hard-Disk](http://www.wikihow.com/Recover-a-Dead-Hard-Disk). This was the result:

```
root@ubuntu:~# mount -t ntfs /dev/hda /mnt/disk
Error reading bootsector: Input/output error
Failed to mount '/dev/hda': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.
```

---

### Post by caljohnsmith on 2009-04-27
Kooljay2, when you say the SMART test would not run, what exactly was the error it returned? It doesn't sound like anything is able to read from your HDD at this point; unless you can read from the HDD, there's not much hope of data recovery with the tools available in Linux. To try doing a low-level read from that HDD, how about posting the output of the following command (please copy and paste the output from the terminal, don't just say it didn't work):
```
sudo hexdump -C -n512 /dev/hda
```

---

### Post by kooljay2 on 2009-04-28
OK, the reason I thought SMART didn't run was because it didn't create the txt files. It went bck to the prompt so I never went the next step of running the test. This time I ran the test anyway. The test did complete according to checking the progress, but I do not have a record of the health before or after. Please review the command you asked me to type to place the text docs on the desktop and I will run the tests again. 

Thanks again for all your help.

---

### Post by caljohnsmith on 2009-04-28
OK, how about trying:
```
sudo smartctl -a /dev/hda
```
And does that produce any output/errors in the terminal? Also, please try the hexdump command I gave in my previous post and copy/paste the output.

---

### Post by kooljay2 on 2009-04-28
The hexdump command took me right back to the prompt:
```
ubuntu@ubuntu:~$ sudo hexdump -C -n512 /dev/hda
ubuntu@ubuntu:~$ sudo hexdump -C -n512 /dev/hda
ubuntu@ubuntu:~$ 
```



This is from the SMART command:

```
uhebuntu@ubuntu:~$ sudo smartctl -a /dev/hda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     IBM/Hitachi Travelstar 60GH and 40GN family
Device Model:     IC25N020ATCS04-0
Serial Number:    CSH206D9D1LP5F
Firmware Version: CA2OA71A
User Capacity:    20,003,880,960 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   5
ATA Standard is:  ATA/ATAPI-5 T13 1321D revision 3
Local Time is:    Wed Apr 29 00:11:18 2009 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:          ( 645) seconds.
Offline data collection
capabilities:              (0x1b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    No Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    No General Purpose Logging support.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  26) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   062    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   040    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0007   116   116   033    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0012   098   098   000    Old_age   Always       -       3686
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   040    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0012   076   076   000    Old_age   Always       -       10887
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   098   098   000    Old_age   Always       -       3185
191 G-Sense_Error_Rate      0x000a   098   098   000    Old_age   Always       -       131075
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       174
193 Load_Cycle_Count        0x0012   077   077   000    Old_age   Always       -       231056
194 Temperature_Celsius     0x0002   122   122   000    Old_age   Always       -       45 (Lifetime Min/Max 11/67)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       99

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     10885         -

Device does not support Selective Self Tests/Logging
ubuntu@ubuntu:~$ 
```

---

### Post by caljohnsmith on 2009-04-28
Although you are able to at least get a response from your HDD with the SMART testing software, none of the other commands so far have actually been able to read from the HDD. As I previously mentioned, there's not much hope of recovering data from that HDD until you can somehow read from it. Otherwise you would probably have to pay a professional data recovery service to try to dig the data off the HDD. So bottom line is I don't know what else to suggest, except I would open up your computer and at least reseat the HDD connector in a last ditch effort to see if that helps at all. Let me know what you decide to do, and sorry there's not much more I can suggest.

---

### Post by kooljay2 on 2009-04-28
Thanks for your help. You've been more than patient. It is genuinely appreciated.

---

### Post by kooljay2 on 2009-04-29
Do you think installing Ubuntu will give me access to the Windows folders?

---

### Post by caljohnsmith on 2009-04-29
> **kooljay2 said:**
> Do you think installing Ubuntu will give me access to the Windows folders?
I don't think you fully understand--if you can't read from the HDD, certainly you won't be able to install Ubuntu to the HDD, for the same reason you weren't able to install Win XP again. Your HDD is having serious problems, and probably your only last option at this point is a data recovery service (but that of course will most likely be really expensive). Linux data recovery tools (or any software recovery tools for that matter)will only work if your HDD is at least accessible/readable, but yours has unfortunately degraded past that point.

---

### Post by swarup on 2009-05-09
I have an HP desktop computer on which I basically have done the same thing which Sakae did (see earlier posts in this thread).

I purchased a computer which I ended up not liking and so need to return it to the store tomorrow. It came with Vista on a 500 GB HDD. I shrunk Vista to 50 GB and installed Jaunty on the space thus freed up. Now that I decided to return the computer, I booted to a Parted Magic livecd, deleted the extended partition containing Jaunty and linux swap, and re-expanded the Vista partition to its former size. So now there is nothing left of Ubuntu on the HDD. But when I try to boot up the computer it is still looking for GRUB. Here is what comes on the screen:

```
GRUB Loading stage 1.5
GRUB loading, pleast wait...
Error 22
```

In an attempt to fix the Windows MBR, I downloaded a Windows Vista Recovery Disc 64-Bit livecd iso, from [http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/](http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/) But when I booted to the livecd and ran the repair tool, it said it could not find anything wrong. I tried it several times, and it said the same thing every time. 

The computer, and HP, has a recovery partition on it. But try as I might, I could not access it.

So, having reviewed this thread carefully, I booted to a Jaunty livecd, and tried the two solutions given by caljohnsmith on page one (using the syslinux and mbr utilities). Both solutions went smoothly, but at the end of each when I tried a reboot, I got the same screen shown above, about "GRUB loading, pleast wait...Error 22".

Vista was running perfectly until I removed the linux partition, so I do not think there is anything wrong except for the MBR. I did re-expand the Vista partition, which caljohnsmith has said is not good to do. But Vista *was* the first partition on the drive meaning that when I expanded it, I expanded it from its rear end, back to the end of the drive. So hopefully, that is an encouraging point.

What should I do at this point, to re-establish the Windows MBR?

---

### Post by caljohnsmith on 2009-05-09
Swarup, in order to get a clearer picture of your setup related to your booting problem, how about booting your Ubuntu Live CD, download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next pos. The results of that script will help clarify your setup.

John

---

### Post by swarup on 2009-05-09
Hi John,
Thanks so much for writing in to help me. I actually have just now gotten the solution, and everything is fine. The solution actually came from a post on another thread which you yourself wrote. So I have to thank you profoundly for your generosity and expertise. If you are interested to see what transpired, please see this thread, where I had described everything in detail and ultimately received reference to your link which solved the problem. Here is the thread link: 

[http://ubuntuforums.org/showthread.php?t=1153560](http://ubuntuforums.org/showthread.php?t=1153560)

Someone in page 3 of the above thread gave reference to your post, which solved the problem for me. I have to apologize as well, for posting my problem in two places, for I was desperate and under time pressure to solve the problem

Thanks again for all your help! :P

---

### Post by cplx on 2009-05-29
hi guys,

I have similar problem and I thought I was going to sort it pretty easy, but somehow I cant do it.

here is the thing:

I had two hdds in my pc

sda - ntfs boot partion for windows xp
sdb - ntfs data storage

then I added third hdd and installed debian lenny on it so:

sdc - ext3 debian lenny part. , swap part. and fat32 data storage

during lenny installation installer wrote grub bootloader into sda mbr. everything was just fine, until my third (sdc) hdd stopped working. now I cannot boot windows from sda - grub error 21 (maybe 22, dont remember exactly)


I tried to restore previous win xp mbr in sda but with no succes.

I tried:

windows install cd - fixmbr, fixboot - nothing. repairing my windows installation - nothing.

from ubuntu live cd - 
```
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda1 
```[COLOR=Red][COLOR=Black]still nothing - I always get the same error - grub error 21 (22)

here is my boot_info_script output:

[/COLOR][/COLOR]```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcdbecdbe

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    39,086,144    39,086,082   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x54428459

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   320,159,384   320,159,322   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="CAD03311D03302ED" TYPE="ntfs" 
/dev/sdb1: UUID="B420CECF20CE97AE" LABEL="DATA" TYPE="ntfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /mnt/c type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute[COLOR=Red][COLOR=Black]=optin /fastdetect [/COLOR][/COLOR]
```
[COLOR=Red][COLOR=Black] 
I hope you will help me guys, thank you very much.

p.s. ssorry for english, I am czech.

[/COLOR][/COLOR]

---

### Post by Salmontarre on 2009-05-30
Hello.

I'm having quite the problem.  I am shipping this computer off to my sister, and she refuses to use Ubuntu, so I'm putting windows back on it.

It has a 320gb hard drive, split into two partitions.  Originally, it was running windows, but some time ago I nyxed windows, installed Ubuntu on the smaller partition using ext3, and kept the larger partition with all the personal data intact as a NTFS partition.

Now I want to put WinXP back on the smaller partition.

Booted from CD, deleted the small swap partition Ubuntu uses, formatted that and the Ubuntu install partition into NTFS, which should have left me with two NTFS partitions, the large, backup partition never being touched.  Install windows, blah blah.

Reboot, and nothing happens.  After the device listing, there is no GRUB errors, just a blinking cursor (can't type anything, ofc).

So I boot into this 8.10 LiveCD, and, assuming it's a MBR problem, I type in: 

```
ubuntu@ubuntu:~$ sudo apt-get install mbr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mbr is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu:~$ sudo install-mbr -i n -p D -t 0 /dev/sda
ubuntu@ubuntu:~$ 

```

Reset, same problem.

I try fixmbr from Windows recovery, which, by the way, boots me into D:/Windows... what?  It should be C:/Windows, I thought.  So I go back into LiveCD, and do:

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           16065   102398309    51191122+   f  W95 Ext'd (LBA)
/dev/sda2   *   102398373   625121279   261361453+   7  HPFS/NTFS
/dev/sda5           16128   102398309    51191091    7  HPFS/NTFS

```

This is where I get lost.  Are those Start/Ends messed up?  Shouldn't the boot be on sda5, which is the smaller partition?  I don't even know what sda1 is.

I also ran the bootinfoscript, in case it helps anyone figure this out.  Here is the output:

```
============================= Boot Info Summary: ==============================

 => Testdisk is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sda5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda5 sda5 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda5 sda5 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sda5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda5 sda5 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda5 sda5 ntfs-3g force 0 0

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda2 starts at sector 102398373.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 sda2 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 sda2 ntfs-3g force 0 0

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,065   102,398,309   102,382,245   f W95 Ext d (LBA)
/dev/sda5              16,128   102,398,309   102,382,182   7 HPFS/NTFS
/dev/sda2    *    102,398,373   625,121,279   522,722,907   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda2: UUID="9464D33964D31D34" TYPE="ntfs" 
/dev/sda5: UUID="04A03FF9A03FF032" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

```

Those mounting fail messages are what I get when I try to look at the contents of the partitions from the LiveCD GUI, as well.

Any help would be great, I'm at a total loss for how to fix this.

---

### Post by supi007 on 2009-10-28
Hello,

I'm trying to backup data from an old HDD.
I get the same message all time from Testdisk program:
"Stucture OK" && "Partition sector doesn't have the endmark 0xAA55" && 
I had made Analyzing , BackupBS ... etc, but I cannot step forward :(
I have googled many pice of advice (and I mixed them), but I still cannot solve the problem.
So If somebody has any idea pls. tell me! I need data from that HDD.

supesz

---

### Post by zonedabone on 2010-02-24
I tried running the fdisk function in the terminal. Here's what I got:

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfd478bc7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   156232124    78116031    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00055296

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   967723469   483861703+  83  Linux
/dev/sdb2       967723470   976768064     4522297+   5  Extended
/dev/sdb5       967723533   976768064     4522266   82  Linux swap / Solaris

```
What now?

---

### Post by mintybot on 2010-08-05
Thanks sooo much for this!

---

### Post by krtica on 2010-11-06
Thank you. [-o<

Works on Lucid too.

---

### Post by YannBuntu on 2011-02-17
Hi,
does anyone know the difference between ms-sys and the "mbr" package which is still in repositories ?

(see [https://answers.launchpad.net/ubuntu/+source/ms-sys/+question/28349](https://answers.launchpad.net/ubuntu/+source/ms-sys/+question/28349))

---

### Post by user1397 on 2011-03-16
The ms-sys package from dapper still works flawlessly, even in maverick (I just tested it out).

I've attached it here for convenience, but you can also easily look it up in packages.ubuntu.com

To use it under maverick, boot into the live disk, then copy the ms-sys package over using a flash drive or download it from your email (whatever works for you), install it, and then in the terminal use the original instructions provided in the first post of this thread.

aka...

**sudo ms-sys --mbr /dev/sdX** (or whatever your drive is, to find that out type **sudo fidsk -l**)

nb: Honestly now that I think about it, I have no use for either my gparted livecd or my super grub disk, i can do everything in an ubuntu live disk so why bother?

---

### Post by Cammigirl on 2011-06-30
> **inoxllor said:**
> **Tested on Ubuntu 7.04; Ubuntu 7.10 and Linux Mint 4.0 Live CDs**

If want to restore Windows Bootloader and for some reason cannot use the windows installation cd, there is a simple way to do it:

NOTE: make sure you have internet working.

1) Boot with Ubuntu Live CD or Linux Mint Live CD


2) On the terminal: 

   **sudo apt-get install ms-sys** 

then

   **ms-sys --mbr /dev/hdX **

NOTE: in my case the main windows xp system is located in hda1 so I used ms-sys --mbr /dev/hda

3) Reboot. 

This should get your windows back. :D
When I attempt to follow your instructions, I get the message below:

ubuntu@ubuntu:~$ sudo apt-get install ms-sys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ms-sys
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5        9725    78083932+   7  HPFS/NTFS
 
What am I doing wrong?

---

### Post by oldfred on 2011-06-30
You can just restore the XP boot loader with fixMBR.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Or if you cannot find XP cd, you can install lilo's boot loader which  works just like windows in looking for a boot partition and jumping to  that partition to boot.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. 
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

### Post by davedaveh on 2012-03-02
I corrupted my XP partition when experimenting with Ubuntu 11 and was able to bring XP back with these commands from live CD:

sudo apt-get install mbr
sudo install-mbr -i n -p D -t 0 /dev/sda

but after further manipulation, I screwed it up, and the fix failed --
first -i was invalid, when I removed it,
error came up 'no 0 directory'
upon removing that,
'/dev/sda no directory'

other permutations come up with error 'missing destitnation file operand...'

Have I messed it up beyond repair?

I can see the partition from Prtition Commander
but have not been able to make a bootable 'fixmbr' disk to work either.
Is XP gone now?
Also from live cd, fdisk -l has no output

---

### Post by oldfred on 2012-03-02
I prefer lilo over mbr. 

You can also run this:

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

If you cannot fix it, run the boot info script from Boot-Repair, but start a new thread with your post of the boot script link. It gets too confusing to have multiple boot scripts in one thread.

---

### Post by cacycleworks on 2012-04-18
Ouch, ubuntu 12.04 LTS final beta? There is no ms-sys in the repos. :( I even had to apt-get install aptitude... 1st time ever. BUT! If google brought you here like it did me, try this: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)  :D

---

### Post by srichakradhar on 2013-05-26
I was dual booting Windows 8 and BackTrack5 but I corrupted the mbr using easyBCD. So I tried this..

sudo apt-get install mbrsudo install-mbr -i n -p D -t 0 /dev/[COLOR=Red]sda1[/COLOR]
/dev/sda1 was the primary partition in my system which is "System Reserved" for Windows.When I rebooted my system It got stuck at the boot logo "HP" and BIOS won't show up even when I pressed the "ESC" to pause start up..What could be the reason for BIOS not showing up? Can it be fixed??

---

### Post by cacycleworks on 2013-05-26
You might want to post a new question on askubuntu.com and be sure to give as many details as possible. There or serverfault maybe.

---

### Post by srichakradhar on 2013-05-26
I've posted it here.. [http://ubuntuforums.org/showthread.php?t=2148629](http://ubuntuforums.org/showthread.php?t=2148629)

---

### Post by coffeecat on 2013-05-26
I'm closing this very old thread. Time has moved on, and the only utility described in the OP has long been unavailable from the repositories. Also, the increasing number of uefi systems will mean that this thread could be misleading to inexperienced users.

Those needing to repair the Windows bootloader in legacy BIOS systems may find this community documentation useful:

[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

If anyone needs specific help, please start a new thread in an appropriate section of the forum.

Thread closed.

---

