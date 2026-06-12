---
title: "Please help test the bug-fix for 'Install/reinstall wipes out all/other partitions'"
date: 2015-01-01
forum: Ubuntu Development Version
---

### Post by sudodus on 2015-01-01
Hi everybody,

We must hurry to test the bug-fix for this very bad bug. In particular, it is important to test it in a real computer running in UEFI mode. So *please*, if you have the opportunity: time, hardware and a good backup ;-)

See the following links (and the final comment by Bruno Nova)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192/](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192/)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192/comments/111](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192/comments/111)

[URL="https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192/comments/122"]https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192/comments/122

[/URL]

---

### Post by ventrical on 2015-01-01
Can we try this using vivid daily or do we have to roll back to trusty.iso?

Regards..

---

### Post by ventrical on 2015-01-01
@sudodus

 I do not totally understand what Bruno is saying. Does he want us to hard test 14.04.1 (proprosed) only or can I use vivid 15.04?

 I am going ahead with 15.04 spin.

Do you have some add on pointers ?

---

### Post by ventrical on 2015-01-01
Ok... got this far (see video). I ran out of memory space on my Nokia. As you can see Ubiquity will not let me resize partition. It recognizes ntfs partitons but not Windows 8 OS. Does it matter? 

 I will abort install and try 14.04.1 Unity live with proposed.

Please do not mind video quality. It has been long day in polar vortex :)lol

[https://www.youtube.com/watch?v=kRWnz__3CL4&feature=youtu.be](https://www.youtube.com/watch?v=kRWnz__3CL4&feature=youtu.be)

---

### Post by ventrical on 2015-01-02
Trusty iso.live

[s] ```

ubuntu@ubuntu:~$ sudo apt-get install ubiquity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  consolekit docbook-xml docbook-xsl icoutils kate-data katepart kde-runtime
  kde-runtime-data kde-style-oxygen kde-window-manager
  kde-window-manager-common kdelibs-bin kdelibs5-data kdelibs5-plugins
  kdoctools kubuntu-debug-installer libattica0.4 libbaloocore4 libbaloofiles4
  libbalooxapian4 libck-connector0 libdebian-installer4 libdlrestrictions1
  libencode-locale-perl libepub0 libfile-listing-perl libfont-afm-perl libgif4
  libhtml-form-perl libhtml-format-perl libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl
  libhttp-daemon-perl libhttp-date-perl libhttp-message-perl
  libhttp-negotiate-perl libilmbase6 libio-html-perl libkactivities-bin
  libkactivities-models1 libkactivities6 libkatepartinterfaces4 libkcmutils4
  libkde3support4 libkdeclarative5 libkdecorations4abi1 libkdecore5 libkdesu5
  libkdeui5 libkdewebkit5 libkdnssd4 libkemoticons4 libkfile4 libkhtml5
  libkidletime4 libkio5 libkjsapi4 libkjsembed4 libkmediaplayer4
  libknewstuff3-4 libknotifyconfig4 libkntlm4 libkparts4 libkpty4
  libkrosscore4 libktexteditor4 libkubuntu0 libkwineffects1abi4
  libkwinglesutils1 libkwinglutils1abi3 libkworkspace4abi2 libkxmlrpcclient4
  liblwp-mediatypes-perl liblwp-protocol-https-perl libnepomuk4
  libnepomukcleaner4 libnepomukcore4abi1 libnepomukquery4a libnepomukutils4
  libnet-http-perl libntrack-qt4-1 libntrack0 libopenexr6 libpam-ck-connector
  libphonon4 libplasma3 libpolkit-qt-1-1 libpoppler-qt4-4 libqapt2
  libqapt2-runtime libqca2 libqjson0 libqmobipocket1 libqt4-qt3support
  libsolid4 libsoprano4 libstreamanalyzer0 libstreams0 libthreadweaver4
  libvirtodbc0 libwww-perl libwww-robotrules-perl libxcb-composite0
  libxcb-damage0 libxcb-keysyms1 libxcb-xtest0 libxml2-utils libzip2
  nepomuk-core-data nepomuk-core-runtime ntrack-module-libnl-0 odbcinst
  odbcinst1debian2 oxygen-icon-theme phonon phonon-backend-gstreamer
  phonon-backend-gstreamer-common phonon-backend-gstreamer1.0
  plasma-scriptengine-javascript python3-dbus.mainloop.qt python3-pyqt4
  python3-sip qapt-batch sgml-data shared-desktop-ontologies soprano-daemon
  ttf-dejavu-core ubiquity-frontend-gtk ubiquity-frontend-kde
  ubiquity-ubuntu-artwork virtuoso-minimal virtuoso-opensource-6.1-bin
  virtuoso-opensource-6.1-common
Suggested packages:
  docbook docbook-dsssl docbook-defguide dbtoepub docbook-xsl-doc-html
  docbook-xsl-doc-pdf docbook-xsl-doc-text docbook-xsl-doc docbook-xsl-saxon
  fop libsaxon-java libxalan2-java libxslthl-java xalan
  libterm-readline-gnu-perl libterm-readline-perl-perl djvulibre-bin finger
  weston libdata-dump-perl hspell libcrypt-ssleay-perl
  libqca2-plugin-cyrus-sasl libqca2-plugin-gnupg libqca2-plugin-ossl
  libauthen-ntlm-perl phonon-backend-vlc gstreamer1.0-plugins-ugly
  phonon4qt5-backend-gstreamer python3-pyqt4-dbg perlsgml w3-recs opensp
  gnome-control-center feh
The following NEW packages will be installed:
  consolekit docbook-xml docbook-xsl icoutils kate-data katepart kde-runtime
  kde-runtime-data kde-style-oxygen kde-window-manager
  kde-window-manager-common kdelibs-bin kdelibs5-data kdelibs5-plugins
  kdoctools kubuntu-debug-installer libattica0.4 libbaloocore4 libbaloofiles4
  libbalooxapian4 libck-connector0 libdlrestrictions1 libencode-locale-perl
  libepub0 libfile-listing-perl libfont-afm-perl libgif4 libhtml-form-perl
  libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl
  libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl
  libhttp-message-perl libhttp-negotiate-perl libilmbase6 libio-html-perl
  libkactivities-bin libkactivities-models1 libkactivities6
  libkatepartinterfaces4 libkcmutils4 libkde3support4 libkdeclarative5
  libkdecorations4abi1 libkdecore5 libkdesu5 libkdeui5 libkdewebkit5
  libkdnssd4 libkemoticons4 libkfile4 libkhtml5 libkidletime4 libkio5
  libkjsapi4 libkjsembed4 libkmediaplayer4 libknewstuff3-4 libknotifyconfig4
  libkntlm4 libkparts4 libkpty4 libkrosscore4 libktexteditor4 libkubuntu0
  libkwineffects1abi4 libkwinglesutils1 libkwinglutils1abi3 libkworkspace4abi2
  libkxmlrpcclient4 liblwp-mediatypes-perl liblwp-protocol-https-perl
  libnepomuk4 libnepomukcleaner4 libnepomukcore4abi1 libnepomukquery4a
  libnepomukutils4 libnet-http-perl libntrack-qt4-1 libntrack0 libopenexr6
  libpam-ck-connector libphonon4 libplasma3 libpolkit-qt-1-1 libpoppler-qt4-4
  libqapt2 libqapt2-runtime libqca2 libqjson0 libqmobipocket1
  libqt4-qt3support libsolid4 libsoprano4 libstreamanalyzer0 libstreams0
  libthreadweaver4 libvirtodbc0 libwww-perl libwww-robotrules-perl
  libxcb-composite0 libxcb-damage0 libxcb-keysyms1 libxcb-xtest0 libxml2-utils
  libzip2 nepomuk-core-data nepomuk-core-runtime ntrack-module-libnl-0
  odbcinst odbcinst1debian2 oxygen-icon-theme phonon phonon-backend-gstreamer
  phonon-backend-gstreamer-common phonon-backend-gstreamer1.0
  plasma-scriptengine-javascript python3-dbus.mainloop.qt python3-pyqt4
  python3-sip qapt-batch sgml-data shared-desktop-ontologies soprano-daemon
  ttf-dejavu-core ubiquity-frontend-kde virtuoso-minimal
  virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common
The following packages will be upgraded:
  libdebian-installer4 ubiquity ubiquity-frontend-gtk ubiquity-ubuntu-artwork
4 upgraded, 132 newly installed, 0 to remove and 492 not upgraded.
Need to get 78.9 MB of archives.
After this operation, 213 MB of additional disk space will be used.
Do you want to continue? [Y/n] y


``` [/s]

ok... this locked up my Pc .. my bad...

New:

```

ubuntu@ubuntu:~$ sudo apt-get install ubiquity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  aptitude aptitude-common bogl-bterm libboost-iostreams1.54.0 libcwidget3
  libdebian-installer4 libept1.4.12 ncurses-term tasksel tasksel-data
  ubiquity-frontend-debconf ubiquity-frontend-gtk ubiquity-ubuntu-artwork
Suggested packages:
  aptitude-doc-en aptitude-doc debtags libcwidget-dev gnome-control-center feh
The following NEW packages will be installed:
  aptitude aptitude-common bogl-bterm libboost-iostreams1.54.0 libcwidget3
  libept1.4.12 ncurses-term tasksel tasksel-data ubiquity-frontend-debconf
The following packages will be upgraded:
  libdebian-installer4 ubiquity ubiquity-frontend-gtk ubiquity-ubuntu-artwork
4 upgraded, 10 newly installed, 0 to remove and 492 not upgraded.
Need to get 9,117 kB of archives.
After this operation, 16.1 MB of additional disk space will be used.
Do you want to continue? [Y/n] 

```

Ok... I used gparted to resize windows8 and create new partition. i am just putting screenshots up so i do no tloose them live:

..and..

---

### Post by ventrical on 2015-01-02
Reviewing Bruno's test case,  I did not follow his method to a tee because most PCs come with Windows 8 installed at the factory - so I did all other suggestions he advised.  I installed a full version of Windows 8 though using the whole disk. Trusty and 15.04 xubuntu ubiquity (with proposed enabled and the required files updated) would still NOT recognize Windows 8 operating system in UEFI mode on hard install.   I consider this a complete fail. This is really bad news... and we have to fix this thing.! Ubuntu trusty is still installing on resized partiton. I'll get back on this.

Ok.. Install complete..

```

ventrical@ventrical-desktop:~$ sudo update-grub
[sudo] password for ventrical: 
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 8 (loader) on /dev/sda1
done
ventrical@ventrical-desktop:~$ 


```


so it detected Windows 8 bootloader.  so time now to reboot and see what happens , eh?  :)

---

### Post by ventrical on 2015-01-02
Success!

 *note* I had to do this without using the updates that Bruno recommended I used trusty.iso without proposed enabled. Those patches are buggy on hard install.

  The trick is in resizing the windows8 partion with gparted then confirming and formatting the new (freespace) to ext4 and confirming again. gparted seems a difficult read about confirming operations to be completed and may confuse some people. After a swapspace is created using standard trusty current ubiquity it will install seamlessly but must:
```

sudo update-grub

```

It is really very simple operation .. not comlicated like many have wrote about .. making special partitons .. etc.. Trusty knew exactly how to install itself and then grab windows8 Bootloader in hard UEFI mode.

regards.

---

### Post by sudodus on 2015-01-02
> **ventrical said:**
> @sudodus

 I do not totally understand what Bruno is saying. Does he want us to hard test 14.04.1 (proprosed) only or can I use vivid 15.04?

 I am going ahead with 15.04 spin.

Do you have some add on pointers ?

Neither do I, but I guess Ubiquity will be the same version, (backported to 14.04.[COLOR=#ff0000]2[/COLOR]).

---

### Post by sudodus on 2015-01-02
> **ventrical said:**
> Reviewing Bruno's test case,  I did not follow his method to a tee because most PCs come with Windows 8 installed at the factory - so I did all other suggestions he advised.  I installed a full version of Windows 8 though using the whole disk. Trusty and 15.04 xubuntu ubiquity (with proposed enabled and the required files updated) would still NOT recognize Windows 8 operating system in UEFI mode on hard install.   I consider this a complete fail. This is really bad news... and we have to fix this thing.! Ubuntu trusty is still installing on resized partition. I'll get back on this.

> **ventrical said:**
> Ok.. Install complete..

```

ventrical@ventrical-desktop:~$ sudo update-grub
[sudo] password for ventrical: 
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 8 (loader) on /dev/sda1
done
ventrical@ventrical-desktop:~$ 


```


so it detected Windows 8 bootloader.  so time now to reboot and see what happens , eh?  :)

> **ventrical said:**
> Success!

 *note* I had to do this without using the updates that Bruno recommended I used trusty.iso without proposed enabled. Those patches are buggy on hard install.

  The trick is in resizing the windows8 partition with gparted then confirming and formatting the new (freespace) to ext4 and confirming again. gparted seems a difficult read about confirming operations to be completed and may confuse some people. After a swapspace is created using standard trusty current ubiquity it will install seamlessly but must:
```

sudo update-grub

```

It is really very simple operation .. not complicated like many have wrote about .. making special partitions .. etc.. Trusty knew exactly how to install itself and then grab windows8 Bootloader in hard UEFI mode.

regards.

Great work, and with a very short notice :KS

Please write a summary (with a reference to this thread) in the [bug-report]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192/"), because I don't think the developers will read our thread here.

(I can write a reference to our thread, but I might misunderstand and write a bad summary.)

---

### Post by ventrical on 2015-01-02
Ahhh... I re-read the bug blog and see the many different problems there with what ubiquity is  and is not reporting .. etc.. so I can see now that UEFI  is the culprit and not windows 8 detect. I am assuming that UEFI hardware is somehow stealthing the windows 8 operating at the beggining of the detection process (and then subsequently detected by GRuB) so this is very interesting scenario.  I think it is simple line of code or script which runs ubiquity or perhaps other.

  I will not post this assumption on current bug report until i can see it or prove it.

regards..

---

### Post by ventrical on 2015-01-02
Ok.. even though I got correct bootup I think I am not booting from UEFI mode but, rather , BIOS mode. Thats all fine and everything and the system is not busted but I had thought I would be in UEFI mode.

---

### Post by brunonova on 2015-01-02
Thanks for all the testing!

The installer indeed has/had problems detecting Windows 8 on UEFI (which I can't test).
But I think the major bug here is/was that the installer would format the entire disk even when reinstalling or upgrading Ubuntu! The automatic partitioning was misleading. I think this is what you should mainly test.
The bug description refers what to test (I didn't write that).

The tests should be for Trusty (the fix was released for Utopic and Vivid already).
But of course, your tests in Vivid and about Windows 8 detection could be very useful information later (maybe in a new bug report).
All the tests I have done were inside Virtualbox with EFI disabled (I didn't install Windows to the entire disk, and left some free space for Ubuntu).

---

### Post by ventrical on 2015-01-02
I had done some installs earlier last year with UEFI, Windows 8 and Ubuntu.  There are a few partitions that have to be created.  It is a real labyrinth of extra work. I was of the opinion that this had been streamlined somewhat (so - of course is a different bug). For the most part , the method I used  rolled back UEFI to BIOS mode but did not wipe Windows*. I see now where the test case you have presented is testing another aspect of Ubiquity so my apologies for the confusion.

Regards..

---

### Post by ventrical on 2015-01-02
A possible reason why Windows 8 is hidden from partitoner.

Please notice jpgs taken from my camera.

See where it states in Windows 8 bootloader:

```

parttool ${root} hidden-

```

so perhaps editing out '-hidden' may make the Windows OS visible to Ubiquity.?

---

### Post by grahammechanical on 2015-01-02
@ventrical

I am glad to see you getting stuck in. This is exactly the kind of testing that we wanted the U+1 team to be doing. Right? It also shows the importance of direct communication between the developer and the tester.

Regards.

---

### Post by ventrical on 2015-01-02
@graham

Agreed. We have to keep building bridges whether it's UDV or qa. More minds, better quality assurance. :) So olive leaves and bamboo sticks .. whatever it takes to build these bridges :)

---

### Post by ventrical on 2015-01-02
> **ventrical said:**
> A possible reason why Windows 8 is hidden from partitoner.

Please notice jpgs taken from my camera.

See where it states in Windows 8 bootloader:

```

parttool ${root} hidden-

```

so perhaps editing out '-hidden' may make the Windows OS visible to Ubiquity.?

In my pics from GRuB there are 2 UUID numbers:

```

UUID=DA74EE4374EE224D
UUID=BC06F0CA06F08724

```

and when I attempted to try and assign new numbers it gave me a warning that changing these numbers would affect WPA, Microsoft Windows Product Activation. shimmy I call it ;)

  Oh .. and here is the other part of the dog's breakfast :)

[https://wiki.ubuntu.com/SecurityTeam/SecureBoot](https://wiki.ubuntu.com/SecurityTeam/SecureBoot)

---

### Post by sudodus on 2015-01-02
I think those short partition numbers belong to Windows, and should be left alone. At least they belong to Windows file systems, FAT or NTFS.

Linux would not be happy if Windows would be changing the UUIDs of linux ext and swap partitions. (We know that it is possible to change them, and to change at the same time the content of certain system files in linux.)

Why do you want to change those UUID numbers? And was there any Windows installed when you tried to change them? Or only UEFI?

---

### Post by ventrical on 2015-01-02
> **sudodus said:**
> I think those short partition numbers belong to Windows, and should be left alone. At least they belong to Windows file systems, FAT or NTFS.

Yes.. that is exactly my point.

> 

Linux would not be happy if Windows would be changing the UUIDs of linux ext and swap partitions. (We know that it is possible to change them, and to change at the same time the content of certain system files in linux.)


Of course .. but that was not my point.

> 
Why do you want to change those UUID numbers? And was there any Windows installed when you tried to change them? Or only UEFI?

 Yes.. I had installed Windows 8 orignially in UEFI mode. I used the whole disk and just let the install happen. I then studied Bruno's contribution and tried to employ that. I can boot trusty.iso in UEFI mode from USB but it will not *hard* install (as I mentioned previously) in UEFI mode. So with my method  it rolled back to legacy BIOS (which can be a good thing - but not what I wanted to accomplish. The reason I brought up the UUID nos from Windows was that I thought I could get Ubuntu USB iso to somehow detect Windows 8.

  I had researched another method using a variable:

```

$WINOSDATA=true ubiquity

```

Which did not work. It was supposed to direct os-prober to detect Windows 8  from Ubiquity installer. If you type:

```

$WINOSDATA=true os-prober

```

You should get a report - Windows 8, chained.

-----------

  Back to Win8 UUIDs .. I had assumed that I could get a clue there  to be able to unstealth in a more expedient fashion a way to detect Windows 8 OS.  If Ubuntu was installed as the first OS then there would not be so much problem but I am trying to attack the problem of persons who buy PCs with Windows 8 pre-installed in UEFI mode.  I am well aware of all the KBs out there on this subject .. but I thought I would like to take an honest hack at it and see if I could find a way to slip by UEFI (or trick it into giving up  Win 8 OS.)  to Ubuntu install.

It is not a complete fail as proved out that  both Ubuntu and Windows 8 will roll back to legacy BIOS mode and no data gets wiped.

Regards..

---

### Post by sudodus on 2015-01-02
I see. You did more advanced things than I could imagine :-P

Do you think we must use a two step procedure?

1. Boot Ubuntu and write a list of the detected operating system somewhere (which will work only with a read-write file system)

2. Reboot (which might be automatic after the detecting stage) into the regular install stage

In this case 'Install alongside' should be allowed only from USB (with a read-write file system, for example created with the Startup Disk Creator or Unetbootin, maybe not necessarily a persistent live system, the FAT32 partition should do).

-o-

> It is not a complete fail as proved out that  both Ubuntu and Windows 8  will roll back to legacy BIOS mode and no data gets wiped.

Do you mean that the Windows installation was transformed from UEFI to BIOS and still worked? Or was the data available, but Windows did not work?

---

### Post by ventrical on 2015-01-02
> **sudodus said:**
> I see. You did more advanced things than I could imagine :-P

Do you think we must use a two step procedure?


In some ways, yes.  What I think is happening is that there is a TRAFFIC COP when using UEFI.  When Windows 8 is being installed FIRST it creates a MAP or TABLE specific for UEFI - so- when computer FIRST boots it passes control over to UEFI and UEFI <grabs> the maps and tables that are in some area of the boot record . Now .. it is designed so that when Ubuntu attempts to install from USB it looks for other operating systems but either something in the Ubuntu USB boot process is dumping a _map_ or table from UEFI and taking control of UEFI <or> it cannot <get> the data table as it could be possible that  UEFI is grabbing the map&table FIRST from the boot sector of the hdd!!

  The reason why I say this is that  the Ubuntu USB flash drive still boots in true UEFI mode, otherwise it would default to Plymouth - so I am assuming that the Ubuntu USB boot proceedure is somehow not able to handle the way the Windows 8 UEFI maps and tables are formatted. IF this is really the case then the bug fix should not be that difficult.

So here is step by step synopsis.

1. Install Windows 8 in UEFI mode. <full install - no manual partitions>
2. Windows 8 runs  in UEFI mode.
3. Prepare to install Ubuntu 14.04 alongside Windows 8
4. Ubuntu boots into UEFI mode but Ubiquity cannot find Windows 8 OS
5. <Something Else> shows us the NTFS file partitions
6. We go <back> to live mode, enable proposed repositories and install proposed ubiquity.
7. Use the partitioner again and still no Windows 8 detected.
8. Go <back> to live and open gparted and resize ntfs file to create free space
9.Format free space as ext4.
10. Confirm operations in gparted.
11. Proceed again to Ubiquity partitioner.
12. Choose <something else>.
13 Create ext4 partition <rooted> and swap space.
14. Proceed to install Ubuntu.
15. sudo update-grub
16. Voila' Windows 8 Bootloader and Ubuntu detected but no UEFI.

Observations/results:- Process of Installing Ubuntu has annuled UEFI and rolled back to legacy MODE. Since this is taking place in GRuB then it is somewhat safe to assume that UEFI got bumped or routed_by during the Ubuntu installation process.

> 
1. Boot Ubuntu and write a list of the detected operating system somewhere (which will work only with a read-write file system) 

This would be the logical next step because we can't see whats going on under the hood.

> 

2. Reboot (which might be automatic after the detecting stage) into the regular install stage


As you know the Windows install process does just this. It will suspend and reboot while not actually rebooting the CD and continue it's install.

> 

In this case 'Install alongside' should be allowed only from USB (with a read-write file system, for example created with the Startup Disk Creator or Unetbootin, maybe not necessarily a persistent live system, the FAT32 partition should do).

-o-


 But that's just the thing. If ubuntu is live and running,  Windows 8 system will not allow read/write. It is in some sort of protected mode (which I guess is the whole purpose of UEFI). Now the thing is, is that even though Windows 8 OS is not being detected the partitions in the Ubiquity partitioner still show the ntfs boot <System Reserved> and the ntfs <filesystem> so Ubiquity is not using expert_system to assume that  those two <unknown> systems are actually Windows 8. We should be able to create an experimental test case to prove this. That is another reason why I was looking at the UUIDs  .. in effect to be able to create a new pointer  that Ubiquity could understand - so it would be like <fake_windows_8_OS> on sda(n) but I can see now that those UUIDs are of no use in proceeding with the process I am proposing.

Regards..



> 
Do you mean that the Windows installation was transformed from UEFI to BIOS and still worked? Or was the data available, but Windows did not work?

Yes .. everything *still* works .. even now. Windows 8 UEFI was transformed to BIOS !!! I am going to use another drive and try again, later.

---

### Post by grahammechanical on 2015-01-02
@ventrical

You have made some points in this last post that fit some of the problems people have been posting about in the other sections of the forum. Such as not being offered an Install Alongside option: The partitioner not detecting Windows and offering Erase Disk option.

And then there are the posts where Boot Repair has been run and it reports that Grub is not installed in the MBR and the repair puts the require EFI Ubuntu boot files in the boot partition but the problem is not fixed. Look at this thread and check out the Boot Repair report. The machine only has Ubuntu on it. So, why is the install failing and also boot repair failing? Note my next to useless advice. I am starting think "conspiracy! Bill Gates, come out, come out, wherever you are." :)

[http://ubuntuforums.org/showthread.php?t=2259055&page=3](http://ubuntuforums.org/showthread.php?t=2259055&page=3)

Regards.

---

### Post by ventrical on 2015-01-03
> **grahammechanical said:**
> @ventrical

You have made some points in this last post that fit some of the problems people have been posting about in the other sections of the forum. Such as not being offered an Install Alongside option: The partitioner not detecting Windows and offering Erase Disk option.

And then there are the posts where Boot Repair has been run and it reports that Grub is not installed in the MBR and the repair puts the require EFI Ubuntu boot files in the boot partition but the problem is not fixed. Look at this thread and check out the Boot Repair report. The machine only has Ubuntu on it. So, why is the install failing and also boot repair failing? Note my next to useless advice. I am starting think "conspiracy! Bill Gates, come out, come out, wherever you are." :)

[http://ubuntuforums.org/showthread.php?t=2259055&page=3](http://ubuntuforums.org/showthread.php?t=2259055&page=3)

Regards.

@graham

Your link brings us back to here :)

It is  a conspiracy of sorts. That can be proven with gparted. The Windows 8 UUID codes are actual WPA keys (Windows Product Activation). and gparted will warn you that  changing the keys could invalidate the WPA!!! gparted, however, provides a way to use half-keys so that the old keys can be restored so those devs have been through the loop already it seems.

  I also know you have been following UEFI and GRuB problems very closely and that we have debated this item in the past in detail.. but it rears it's head once again!

  I am still experimenting (some might say hacking) :) lol .. but I am not trying to Bust Bill's Bonanza at all.. I am just looking for an easy hack so UEFI can be shared in a fair way  being that MS does not own the entire space on the harddrive.

So i am of the thinking that  if I install Windows 8 on hdd in UEFI mode THEN shut down and remove the drive THEN stick in USB trusty.iso and boot to live session in UEFI mode (which works) and then hotplug the Windows 8 drive back into the system and try an install or see what happens.  This way it will prove the UEFI is not grabbing the maps and tables off the hdd and that ubuntu installer is the problem. There are also a lot of hardware BIOS bugs that Ubuntu will refuse to deal with and just dump them. It's a real cornundrum ...:)

Regards..

edit*

  It just occured to me that  once UEFI is enabled and then Windows 8 is installed that the Windows 8 UEFI maps and tables are still in the UEFI even after the machine is turned off .. sort of like the BIOS battery .. so after I install I will disabled UEFI and then re-enable it and see if that flushes whatever buffered data it is holding (if it is holding data)...so then Ubuntu install does not flush the UEFI buffers ... or to that affect is my assumption..  why .. I haven't got a clue :) lol

*edit* hehehehe .. Ok.. I tried my proceedure and now it hard boots into Windows 8 only. USB will not boot up with Windows hdd drive installed and will not recognize hot-plug Windows 8 UEFI drive. So Technically that hdd belongs to Bill now :) ahehehe

---

### Post by ventrical on 2015-01-03
> **ventrical said:**
> @graham

Your link brings us back to here :)

It is  a conspiracy of sorts. That can be proven with gparted. The Windows 8 UUID codes are actual WPA keys (Windows Product Activation). and gparted will warn you that  changing the keys could invalidate the WPA!!! gparted, however, provides a way to use half-keys so that the old keys can be restored so those devs have been through the loop already it seems.

  I also know you have been following UEFI and GRuB problems very closely and that we have debated this item in the past in detail.. but it rears it's head once again!

  I am still experimenting (some might say hacking) :) lol .. but I am not trying to Bust Bill's Bonanza at all.. I am just looking for an easy hack so UEFI can be shared in a fair way  being that MS does not own the entire space on the harddrive.

So i am of the thinking that  if I install Windows 8 on hdd in UEFI mode THEN shut down and remove the drive THEN stick in USB trusty.iso and boot to live session in UEFI mode (which works) and then hotplug the Windows 8 drive back into the system and try an install or see what happens.  This way it will prove the UEFI is not grabbing the maps and tables off the hdd and that ubuntu installer is the problem. There are also a lot of hardware BIOS bugs that Ubuntu will refuse to deal with and just dump them. It's a real cornundrum ...:)

Regards..

edit*

  It just occured to me that  once UEFI is enabled and then Windows 8 is installed that the Windows 8 UEFI maps and tables are still in the UEFI even after the machine is turned off .. sort of like the BIOS battery .. so after I install I will disabled UEFI and then re-enable it and see if that flushes whatever buffered data it is holding (if it is holding data)...so then Ubuntu install does not flush the UEFI buffers ... or to that affect is my assumption..  why .. I haven't got a clue :) lol

*edit* hehehehe .. Ok.. I tried my proceedure and now it hard boots into Windows 8 only. USB will not boot up with Windows hdd drive installed and will not recognize hot-plug Windows 8 UEFI drive. So Technically that hdd belongs to Bill now :) ahehehe

hdd does not belong to Bill any longer. :) I opened a new thread on this. I was successful  in detecting Windows bootloader and partioning 'alongside' with xubuntu 15.04. Both OSes are working fine in UEFI mode. The thing is I am not sure what happened .... whether disabling UEFI then shutdown, restart , re-enable had flushed a buffer or if using the F10 option. I think it was a combination of both. Nonetheless... it's the first time Iv'e seen this work with Windows 8 bootloader without irreversible repair work. I'll try to document this a little more comphrehensively after some rest. All you U+1 testers .. thanks for encouragement , input and help.! :)

Regards..


whew ...

---

### Post by sudodus on 2015-01-03
Very interesting description and results :-)

( in post [#21-]("http://ubuntuforums.org/showthread.php?t=2259055&page=2&p=13199638#post13199638") )

---

### Post by sudodus on 2015-01-03
> **ventrical said:**
> hdd does not belong to Bill any longer. :) I opened a new thread on this. I was successful  in detecting Windows bootloader and partioning 'alongside' with xubuntu 15.04. Both OSes are working fine in UEFI mode. The thing is I am not sure what happened .... whether disabling UEFI then shutdown, restart , re-enable had flushed a buffer or if using the F10 option. I think it was a combination of both. Nonetheless... it's the first time Iv'e seen this work with Windows 8 bootloader without irreversible repair work. I'll try to document this a little more comphrehensively after some rest. All you U+1 testers .. thanks for encouragement , input and help.! :)

Regards..


whew ...

Just helping others find your new interesting thread[URL="http://ubuntuforums.org/showthread.php?t=2259219"]

Detecting Windows Bootloader in Ubiquity[/URL]

---

### Post by grahammechanical on 2015-01-03
I have just come on the forum and I found this thread. See, the user's comments in the 6th post.

> [COLOR=#000000]the problem now lies with the windows itself. Ok when i saw the boot menu shows me the 2 options 1 windows 2 usb ubuntu well I made 1 ubuntu and 2 windows. REstart and goes into a black window asking if i was to try ubuntu or install ubuntu. I tried for instaling ubuntu. Well it runs but the problem is when it says what do you want to do because it only says i can either choose to install ubuntu which will delete my hard drive because apparently there is no other operatign system it recognizes or do somethign else which sys do parton and soemthing. I went into the somethgn else make artition and wow I ran out of there i dont even know what i was lookign at. So yea is where i stand now either eraze my hard drive or do a partition which made me worry.[/COLOR]

[http://ubuntuforums.org/showthread.php?t=2259201&p=13199900#post13199900](http://ubuntuforums.org/showthread.php?t=2259201&p=13199900#post13199900)

It looks to me that the re-install Ubuntu = erase the disk and the absence of an install alongside option are related. Fixing the re-install Ubuntu = erase disk is not enough unless it also fixes the missing Install Alongside option.

Regards.

---

### Post by ventrical on 2015-01-03
@graham and sudodus

 From that same thread:

> 

 Sudodus wrote:


The start the installer and at the partitioning page select ***Something else***.  This time you need not create anything. Only select the partition, that  you made for a root partition, mark that you want it as **/** (symbol for root partition), and format it with the **ext4** file system. The swap partition will be selected automatically.



  The swap partition will NOT be selectd automatically. You have to create it from the fee space left over and mark it as Primary/Swap. I know.. it sounds quirky but that's what I had to do.

---

### Post by sudodus on 2015-01-03
> **ventrical said:**
> @graham and sudodus

 From that same thread:



  The swap partition will NOT be selectd automatically. You have to create it from the fee space left over and mark it as Primary/Swap. I know.. it sounds quirky but that's what I had to do.

Yes, you have to create the swap partition (or let the installer find an already existing partition). In this particular case, the OP was adviced to use gparted to create it (and also create a partition for the root file system). The according to my experience, swap will be selected automatically.

- at least in BIOS mode

- I have too little experience of UEFI to be sure if the automatic selection of swap works

---

### Post by ventrical on 2015-01-03
> **sudodus said:**
> Yes, you have to create the swap partition (or let the installer find an already existing partition). In this particular case, the OP was adviced to use gparted to create it (and also create a partition for the root file system). The according to my experience, swap will be selected automatically.

- at least in BIOS mode

- I have too little experience of UEFI to be sure if the automatic selection of swap works

My misread.

:)

---

### Post by grahammechanical on 2015-01-03
My point would be that Install Alongside is better for would be new users than expecting them to get involved with Something Else. Likewise, with reinstalling Ubuntu from the same menu without wiping everything on the disk.

My first install of Ubuntu (7.04) was on a blank disk and I let the installer take the automatic route. I could not have worked my way through the "guided" method even though there was no risk of messing up an existing OS.

Regards.

---

### Post by ventrical on 2015-01-03
It's working great with 'alongside' with xubuntu .

Yeah .. +1 I agree with graham.

Regards..

---

### Post by sudodus on 2015-01-04
> **grahammechanical said:**
> My point would be that Install Alongside is better for would be new users than expecting them to get involved with Something Else. Likewise, with reinstalling Ubuntu from the same menu without wiping everything on the disk.

My first install of Ubuntu (7.04) was on a blank disk and I let the installer take the automatic route. I could not have worked my way through the "guided" method even though there was no risk of messing up an existing OS.

Regards.

In the perfect world, yes, I agree 100%. But with these bugs, new users are tricked into wiping their Windows and their personal data. So as long as these bugs are not completely squashed, 'Install alongside' is way too dangerous to be offered as a menu option.

I'm really looking forward to the improved situation, that *ventrical* is finding in vivid, that Windows is detected, and that 'Install alongside' is giving correct information of what is going to happen.

---

### Post by kansasnoob on 2015-01-04
I have no UEFI hardware to test on so I've so far stayed out of this since I know almost less than nothing about the process but this comment made me think:

> I'm really looking forward to the improved situation, that ventrical is finding in vivid, that Windows is detected, and that 'Install alongside' is giving correct information of what is going to happen. 

I think ventrical has been testing Trusty using 14.04.1 images + boot to live DE + enable proposed + apt-get update + apt-get install ubiquity, eh?

If so it might be interesting to verify the failings/bugs using a Trusty daily image:

[http://cdimage.ubuntu.com/trusty/daily-live/20150104/](http://cdimage.ubuntu.com/trusty/daily-live/20150104/)

The Trusty daily images are also available here (that makes it a bit easier to find the flavors):

[http://iso.qa.ubuntu.com/qatracker/milestones/308/builds](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds)

If in fact the Trusty daily images are failing, but the Vivid images are not, it might also be interesting to know whether the Utopic images work properly or not.

@ventrical, thanks for doing all the heavy lifting, it's much appreciated :D

I am going to try some tests on a standard BIOS system within the next few days as time allows. I've just been AFK with some weather sensitive issues that can't wait.

---

### Post by grahammechanical on 2015-01-04
> [COLOR=#333333][FONT=monospace]It would be great if someone else also tested this. Better yet if the tests could be done on a real UEFI testing machine.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]But note that, according to [/FONT][/COLOR][https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule](https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule)[COLOR=#333333][FONT=monospace], 14.04.2 will be released on February 5th. The new version of ubiquity should be tested and "approved" before then.[/FONT][/COLOR]

I assume that this new version of Ubiquity is already in Vivid Vervet? Is it not true that the LTS point releases bring in to the LTS certain improvements made during the development cycle of the standard release? I do not have UEFI. So, I cannot test. It would indeed be good to know that these bugs are now fixed and that there is some kind of documented work around that can be used with 14.04.1 until 14.04.2 is released.

We are in the situation that those with the confidence that comes with experience do not have the latest hardware and those with the latest hardware do not have the knowledge that comes with experience. This is life. I know that, but people expect a free to download and install OS to just work. I consider that to be an unreasonable expectation. I never expected 07.04 to just work but it did and in part it was down to my researching the components to buy for my self-build machine.

Ah, how to test with 14.04.1

> [COLOR=#333333][FONT=monospace]Every time before running the installer, I enabled trusty-proposed and upgraded 3 packages: ubiquity, ubiquity-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]frontend-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]gtk, ubiquity-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]ubuntu-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]artwork (I wrote these names from memory).[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]I also wanted to see if ubiquity would detect an hibernated Windows 8 partition, but I couldn't find the option to enable it in Windows 8 (maybe it's not supported inside Virtualbox).[/FONT][/COLOR]

Regards.

---

### Post by ventrical on 2015-01-04
> **kansasnoob said:**
> I have no UEFI hardware to test on so I've so far stayed out of this since I know almost less than nothing about the process but this comment made me think:



I think ventrical has been testing Trusty using 14.04.1 images + boot to live DE + enable proposed + apt-get update + apt-get install ubiquity, eh?

If so it might be interesting to verify the failings/bugs using a Trusty daily image:



  All my trusty attempts using 14.04.1 + other addons  will fail. Will not detect Windows 8 Bootloader, will not offer 'alongside' install ... however  as per Bruno's and Sudodus original request method it will successfully install trusty in BIOS mode, which procedure thereof is just way too difficult for new users to catch onto.

 
> 
[http://cdimage.ubuntu.com/trusty/daily-live/20150104/](http://cdimage.ubuntu.com/trusty/daily-live/20150104/)

The Trusty daily images are also available here (that makes it a bit easier to find the flavors):

[http://iso.qa.ubuntu.com/qatracker/milestones/308/builds](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds)

If in fact the Trusty daily images are failing, but the Vivid images are not, it might also be interesting to know whether the Utopic images work properly or not.

@ventrical, thanks for doing all the heavy lifting, it's much appreciated :D

I am going to try some tests on a standard BIOS system within the next few days as time allows. I've just been AFK with some weather sensitive issues that can't wait.

 I had mentioned that I will try this later .. but might as well zsync sooner:)  

Weather?? .. hehehe yeah .. we got it really rolling now up on the Great Lakes .

@kansasnoob

Thanks for kind comments.. :)

edit:

Ok .. here goes with trusty daily...UEFI

---

### Post by ventrical on 2015-01-04
Trusty daily-live now detects Windows Boot Loader but does not offer 'alongside' most likely because I have vivdi-vervet installed. So I am going to choose 'erase ubuntu vivid-vervet and reinstall'.

Please note that:

1. This is not a fresh Windows 8 install but a previous install (yesterday) with an 'alongside' of xubuntu vivid vervet in UEFI mode.
2. This is daily-live ubuntu unity session.
3. I did not use efibootmgr to flush the old list so this is an experiment to se if Trusty will append to the list.

...continuing with install...

---

### Post by ventrical on 2015-01-04
This next step reports totally wrong information. It should only warn of:

The following partitions are going to be formatted:
partition#5 of SCSI1 (0,0,0) sda as ext4
partition#6 of SCSI1 (0,0,0) sda as swap

...here goes .. continue...

---

### Post by ventrical on 2015-01-04
@kansasnoob,all

Absolute seamless success! :) Another canonical/dev/shuttleworth/qatracker/ubuntuforums/development-version masterpiece :)

 The screenshot in my previous post is mostly an f/p and they just have to fix the wording in the way the warning is presented. So if you want to pass it on that the trusty-daily-live has the right fix for detecting Windows Bootloader and will not wipe Windows when installing over 'other previous ubuntu'.

 One note of caution. When installing from trusty live session make sure you boot it with the UEFI shell which is usually F10 just before bootup is in full POST.

Regards..

---

### Post by kansasnoob on 2015-01-04
> **ventrical said:**
> @kansasnoob,all

Absolute seamless success! :) Another canonical/dev/shuttleworth/qatracker/ubuntuforums/development-version masterpiece :)

 The screenshot in my previous post is mostly an f/p and they just have to fix the wording in the way the warning is presented. So if you want to pass it on that the trusty-daily-live has the right fix for detecting Windows Bootloader and will not wipe Windows when installing over 'other previous ubuntu'.

 One note of caution. When installing from trusty live session make sure you boot it with the UEFI shell which is usually F10 just before bootup is in full POST.

Regards..

Thanks ventrical. I think the first two paragraphs/sentences in that warning are boiler plate statements designed as a "one size fits all" warning to give anyone with even the slightest doubt what they are doing one last chance to abort and ask some questions before proceeding.

In a perfect world I'd prefer that ubiquity displayed a boiler plate warning before displaying any other screens such as "Any installation, re-installation, or repartitioning presents some inherent risk of data and/or existing operating system loss so we recommend creating a full backup before proceeding. For more information and individualized guidance please ask here or here." with links to ask ubuntu and the forums, but such things have been suggested in the past many times to no avail.

---

### Post by sudodus on 2015-01-04
> **kansasnoob said:**
> thanks ventrical. I think the first two paragraphs/sentences in that warning are boiler plate statements designed as a "one size fits all" warning to give anyone with even the slightest doubt what they are doing one last chance to abort and ask some questions before proceeding.

In a perfect world i'd prefer that ubiquity displayed a boiler plate warning before displaying any other screens such as "any installation, re-installation, or repartitioning presents some inherent risk of data and/or existing operating system loss so we recommend creating a full backup before proceeding. For more information and individualized guidance please ask here or here." with links to ask ubuntu and the forums, but such things have been suggested in the past many times to no avail.

+1 ;)

---

### Post by ventrical on 2015-01-05
> **grahammechanical said:**
> I assume that this new version of Ubiquity is already in Vivid Vervet? Is it not true that the LTS point releases bring in to the LTS certain improvements made during the development cycle of the standard release? I do not have UEFI. So, I cannot test. It would indeed be good to know that these bugs are now fixed and that there is some kind of documented work around that can be used with 14.04.1 until 14.04.2 is released.

It appears from one install I have done with trusty-daily-live zsync that this 'bug' is fixed. Note however that I am booting in UEFI mode and that my Windows 8 was installed in UEFI mode <enabled> and that I subsequently reinstalled trusty-daily.iso over 15.04 install in the UEFI USB SHELL mode. Trusty daily-live -ubiquity was able to correctly detect Windows boot loader and then overwrite 15.04 with 14.04. I have 4 UEFI machines current but only have so much time to test various cases (of which there are many).  

I am about to try a test from booting Windows 8 with the GRuB bootloader.  Remember what happened the last time ? :)

> 
We are in the situation that those with the confidence that comes with experience do not have the latest hardware and those with the latest hardware do not have the knowledge that comes with experience. This is life. I know that, but people expect a free to download and install OS to just work. I consider that to be an unreasonable expectation. I never expected 07.04 to just work but it did and in part it was down to my researching the components to buy for my self-build machine.

Ah, how to test with 14.04.1



Regards.

 True ... there is some experience required of how to set the BIOS correctly and how to boot from the bootable options menu which is provided by any given particular manufacturer. ie ; Intel/Phoenix.  Expecting GRuB to defeat  the platform option provided on any given form factor is unrealistic. It does in fact overshoot the tool provided on the hardware platform and it is no wonder that there are currently cornundrums of bugs.  I just read the links and then try the test case. If I get a fail I try again, something different, and try to document it as best as I can. In the last 48 hours  I have come close as I think possible to a 100% success rate with trusty current and 15.04.  Of course this may change after I try booting Windows Bootloader from Grub menu within UEFI shell ubuntu.

---

### Post by ventrical on 2015-01-05
To any interested; that was a pass for Windows 8 while booting Windows Boot Loader from the Grub menu so there has been quite a few advancements with the trusty daily and 15.04 development version.

Regards..

---

### Post by ventrical on 2015-01-05
> **kansasnoob said:**
> Thanks ventrical. I think the first two paragraphs/sentences in that warning are boiler plate statements designed as a "one size fits all" warning to give anyone with even the slightest doubt what they are doing one last chance to abort and ask some questions before proceeding.

In a perfect world I'd prefer that ubiquity displayed a boiler plate warning before displaying any other screens such as "Any installation, re-installation, or repartitioning presents some inherent risk of data and/or existing operating system loss so we recommend creating a full backup before proceeding. For more information and individualized guidance please ask here or here." with links to ask ubuntu and the forums, but such things have been suggested in the past many times to no avail.

I see that now .. my statement was just sort of a knee jerk reaction. Actually , after reading the warning again, it is factually correct.

Regards..

---

### Post by sudodus on 2015-01-05
The attached files are my [mkusb]("https://help.ubuntu.com/community/mkusb")'s and [OBI]("https://help.ubuntu.com/community/OBI")'s versions of a perfect world: a displayed boiler plate warning before displaying any other screens

---

### Post by sudodus on 2015-01-06
I've been thinking ...

When 14.04.2 arrives, I hope ***install alongside*** will be reasonably  safe.

But maybe there will still be problems recognizing  Windows, if it is not shut down completely. What happens when Windows is  hibernated or semi-hibernated with fast boot? Can Ubuntu read the Windows file system? Will that be a trap where  people can go ahead and wipe Windows even in the future?

---

### Post by ventrical on 2015-01-06
I might try to take a look at that a little later today. I have also been experiementing with LVM and encrypted  installs , but not in UEFI mode.. so may try that also and see what happens,

---

### Post by sudodus on 2015-01-06
I've iso-tested the Lubuntu encrypted install, and it eats the whole drive. I think it does in Ubuntu too (unless you go the ***Something else*** route).

---

### Post by ventrical on 2015-01-06
Here we go with Ubuntu reinstall in UEFI with Win8 in hibernation mode.

---

### Post by ventrical on 2015-01-06
> **sudodus said:**
> I've iso-tested the Lubuntu encrypted install, and it eats the whole drive. I think it does in Ubuntu too (unless you go the ***Something else*** route).


  I wanted it to encrypt the whole drive It made two 250GB hdds on an old 200GB seagate Sata. It is virtually impossible to crack /home directory without passphrase :) Haven' tried UEFI. I may do today. We have polar vortex - so might have time.

---

### Post by sudodus on 2015-01-06
> **ventrical said:**
> Here we go with Ubuntu reinstall in UEFI with Win8 in hibernation mode.

Does this (see the picture) mean that it cannot see Windows, so it does not report it? The install alongside says it will erase Ubuntu, which is true. But an understatement, because it will erase Windows too.

If this interpretation is correct, there is still a trap for beginners :-(

---

### Post by ventrical on 2015-01-06
There were no wipes or ill effects of doing a reinstall of trusty (unity) daily alongside of Windows 8 in hibernation mode. However , on a dual boot machine one has to specify certain parameters and has to use F10 Boot Up Options from the UEFI shell. This is a Windows problem, not an Ubuntu problem and of course there are always limitations presented unless one is willing to do some serious homework on the subject.

Hibernate Mode in Win 8 is not installed by default .. and for a very good reason.

[http://www.pcworld.com/article/2016932/how-to-enable-hibernate-mode-in-windows-8.html](http://www.pcworld.com/article/2016932/how-to-enable-hibernate-mode-in-windows-8.html)

Regards...

Also LVM/encrypted will not work as the option is not presented in Ubiquity.. This is a quality assurance boiler plate to save noobs from bricking their systems. If any want to go ahead and use gparted to fanaggle around this one then be my guest ... but IMHO .. it is not Ubuntu bug.

Regards..

---

### Post by ventrical on 2015-01-06
> **sudodus said:**
> Does this (see the picture) mean that it cannot see Windows, so it does not report it? The install alongside says it will erase Ubuntu, which is true. But an understatement, because it will erase Windows too.

If this interpretation is correct, there is still a trap for beginners :-(

The screenshot I sent up from the live install mode states very clear that the Windows Boot Manager is detetcted (see top line of screenshot) and that only 14.04.1 will be erased and re-installed.  As I had commented earlier .. it is in the language of how the boiler plates are presented, what is included and (in this case) what is not included. But it is factually correct and just because Windows 8 is not mentioned in the final step before commit does not mean that it is going to be wiped. So the developers have to 'tweak the english'. Perhaps they think it more conservative not to include extra info on Windows 8. We are still early in dev.. and perhaps there is still time to get correct english report inserted into Ubiquity before 14.04.2 release.

---

### Post by sudodus on 2015-01-06
> **ventrical said:**
> There were no wipes or ill effects of doing a reinstall of trusty (unity) daily alongside of Windows 8 in hibernation mode ...

This is good :-)

Would you say that we can start to trust ***Install alongside*** again from the next point version 14.04.2 LTS and the next short version 15.04?

---

### Post by sudodus on 2015-01-06
> **ventrical said:**
> The screenshot I sent up from the live install mode states very clear that the Windows Boot Manager is detetcted (see top line of screenshot) and that only 14.04.1 will be erased and re-installed.  As I had commented earlier .. it is in the language of how the boiler plates are presented, what is included and (in this case) what is not included. But it is factually correct and just because Windows 8 is not mentioned in the final step before commit does not mean that it is going to be wiped. So the developers have to 'tweak the english'. Perhaps they think it more conservative not to include extra info on Windows 8. We are still early in dev.. and perhaps there is still time to get correct english report inserted into Ubiquity before 14.04.2 release.

Bad reading by me :oops:

You are right about making things clear with good English statements (and translated to other locales later on).

---

### Post by ventrical on 2015-01-06
This Computer currently has Windows Boot Manager and Ubuntu 14.04.1 LTS on it. What would you like to do?

*Erase Ubuntu 14.04.1LTS and reinstall
  Warning: This will delete all your Ubuntu 14.04.1LTS programs. documents,photos,music and any other files.

OErase disk and Install Ubuntu
Warning: This will delete all your Ubuntu 14.04.1LTS programs. documents,photos,music and any other files.

 The other options are not germane at this time to the topic at hand.

 Therefore the first option could inlcude "Your Windows Boot Manager and files will not be affected" but this courtesy card is not really necessary because it does exactly what it says it is going to do.

---

### Post by grahammechanical on 2015-01-06
Regarding that screen shot and reasoning from the point of view of a simple user (which I am), if I had a dual boot with Windows and Ubuntu and I was running the Ubuntu installer again I would be doing it to reinstall Ubuntu or to Install ubuntu and replace both Windows and the existing Ubuntu install. If I wanted another install of Ubuntu them I would use the Something Else option. I see no need for an Install Alongside option in this situation. But that is what we get at present. Whenever I put in an install I get offered Install Alongside, which I ignore. I always go to the Something Else option. So, I think that there is an improvement here.

Regards.

---

### Post by ventrical on 2015-01-06
> **grahammechanical said:**
> Regarding that screen shot and reasoning from the point of view of a simple user (which I am), if I had a dual boot with Windows and Ubuntu and I was running the Ubuntu installer again I would be doing it to reinstall Ubuntu or to Install ubuntu and replace both Windows and the existing Ubuntu install. If I wanted another install of Ubuntu them I would use the Something Else option. I see no need for an Install Alongside option in this situation. But that is what we get at present. Whenever I put in an install I get offered Install Alongside, which I ignore. I always go to the Something Else option. So, I think that there is an improvement here.

Regards.

"I see no need for an Install Alongside option in this situation. But that is what we get at present."

  But I have been working exclusivley in UEFI mode and I have not been presented with that option with the exception of when I attempt an install on a fully loaded Windows 8 system in UEFI mode.  Otherwise .. I have to agree with you, strictly speaking , from BIOS mode. 

Regards..

---

### Post by kansasnoob on 2015-01-06
> **sudodus said:**
> This is good :-)

Would you say that we can start to trust ***Install alongside*** again from the next point version 14.04.2 LTS and the next short version 15.04?

Install alongside has two problems "baked in" by design:

(1) There is no longer a separate "Use largest continuous free space". It's now just "baked into" the alongside option. When you select "Install alongside" if the button in the lower right hand corner changes from Continue to Install now then the installer has made up it's own mind to use whatever adequate free space it thinks appropriate. That can result in Ubuntu being installed somewhere you didn't want it to be - like a USB drive with adequate free space, or the wrong drive altogether.

(2) If more than one drive exists you're not offered the choice of which drive to resize so the installer will just assume it knows best. You can however jump to advanced partitioning from that screen if the incorrect drive is presented for resizing.

---

### Post by ventrical on 2015-01-06
> **kansasnoob said:**
> Install alongside has two problems "baked in" by design:

(1) There is no longer a separate "Use largest continuous free space". It's now just "baked into" the alongside option. When you select "Install alongside" if the button in the lower right hand corner changes from Continue to Install now then the installer has made up it's own mind to use whatever adequate free space it thinks appropriate. That can result in Ubuntu being installed somewhere you didn't want it to be - like a USB drive with adequate free space, or the wrong drive altogether.

(2) If more than one drive exists you're not offered the choice of which drive to resize so the installer will just assume it knows best. You can however jump to advanced partitioning from that screen if the incorrect drive is presented for resizing.

@kansasnoob
"There is no longer a separate "Use largest continuous free space". It's now just "baked into" the alongside option. "

 But that's a horse of a different colour (as they would say in Kansas) :)  When installing Ubuntu 14.04.1 daily onto a hdd that was OEMed in the factory (or as which we are trying to emulate here in our tests) then there is  NO "largest contiguous free space". The Ubuquity installer has to CALL on scripts to resize the partiton. A logical offer is presented but the ability to use the <slider> is still there. I know this does not answer your question because I assume you are talking  of a system that has other partitions that have been wiped or created by gparted .. etc..

  Now .. I can create a scenario where I take a 200GB hdd and when installing Windows 8 it gives me the option to create partitions before install. I can create 1 partiton 100GBs and leave the other as "free space". So you are saying that  <alongside> will present a 'baked' option? Thi sis interesting because I thought that is why we use <something else> in the case you are presnting .. either that or I do not full understand you.

---

### Post by ventrical on 2015-01-06
> **sudodus said:**
> This is good :-)

Would you say that we can start to trust ***Install alongside*** again from the next point version 14.04.2 LTS and the next short version 15.04?

 Well .. with what kansasnoob has presented I am not so sure on multiple drives. I'll have to try it.  Another thing also is if using Bitlocker - then the operator would have to manually disable the bitlocker security so that the hdd can be auto-resized  by Ubiquity. This is where we are talking apples and oranges, meaning that certain proceedures have to be followed in the preparation cycle to configurate Windows 8 *properly *.  It is  somewhat beyond the pale to expect Ubiquity to be the cure all  for  Windows 8 framework settings/maps/templates etc...  as I pointed out  in tweaking the Windows 8 hibernate mode .. it is very well hidden away  . Once it is enabled , then you choose hibernate, then restart and choose UEFI shell boot USB and Install Ubuntu while the hibernate is WAITING will cause you to loose hibernated session. So this is a product limitation of UEFI and can only be worked around manually.

---

### Post by ventrical on 2015-01-06
I will take 200GB hdd that has LVM encrypted Ubuntu 14.04.1 daily and install it  on one of my UEFI systems and then boot the live USB and see what options are presented.

edit:

That not what I wanted. I will install Windows 8 on 200GB hdd but create a 100GB patition and one with free space in UEFI mode and see if I can duplicate kansasnoobs scenario.

---

### Post by ventrical on 2015-01-06
Ok .. I wiped 200GB hdd
Installed it on UEFI compliant  Intel MoBo that has existing drive.
Wiped windows 8 on exisitng drive.
Partitioned 200GB drive. One for Windows 8 , one for free space.
Fresh installed windows 8 on second drive of new partition. 
Booted fine.

 Then , when I went to install Ubuntu 14.04.1 daily from live-daily UEFi USB shell it did not present me with install 'alongside' option but can be manipulated manually with something else.

 I call this a pass.

I will not complete this install but will now try Ubuntu 15.04 USB UEFI.

---

### Post by ventrical on 2015-01-06
15.04 correctly warns that all other operating system will be erased. But does not identify other hdd .. only with <somthing else>

 I will create ext4 out of free space and then reboot with USb 15.04

---

### Post by ventrical on 2015-01-07
> **kansasnoob said:**
> Install alongside has two problems "baked in" by design:

(1) There is no longer a separate "Use largest continuous free space". It's now just "baked into" the alongside option. When you select "Install alongside" if the button in the lower right hand corner changes from Continue to Install now then the installer has made up it's own mind to use whatever adequate free space it thinks appropriate. That can result in Ubuntu being installed somewhere you didn't want it to be - like a USB drive with adequate free space, or the wrong drive altogether.

(2) If more than one drive exists you're not offered the choice of which drive to resize so the installer will just assume it knows best. You can however jump to advanced partitioning from that screen if the incorrect drive is presented for resizing.

At this stage of the game , from my observations , with two drives, it's a complete fail in UEFI mode. That goes for Win 8 hibernate too. Unless you are willing to spend a few hours at terminal ...  

Alongside option appears to be a "one shot deal" on an hdd that has had Windows 8 previously installed.

Regards..

---

### Post by ventrical on 2015-01-07
> **sudodus said:**
> This is good :-)

Would you say that we can start to trust ***Install alongside*** again from the next point version 14.04.2 LTS and the next short version 15.04?

Standard basic .. yes. Any customization .. do at your own risk . Ubiquity is not an expert system.

Regards..

---

### Post by sudodus on 2015-01-07
> **ventrical said:**
> Standard basic .. yes. Any customization .. do at your own risk . Ubiquity is not an expert system.

Regards..

And the beginners may not know if their system is standard basic or customized - so 'do at your own risk' is still a valid warning.

---

### Post by ventrical on 2015-01-07
> **sudodus said:**
> And the beginners may not know if their system is standard basic or customized - so 'do at your own risk' is still a valid warning.

Absolutely .. unless some fix comes in before Feb 4th.

---

### Post by grahammechanical on 2015-01-07
I just downloaded the trusty daily 20150107. Standard BIOS motherboard. 2 HD. Lots of partitions with lots of Ubuntus + Windows 8 preview. I wanted to see what Ubiquity offered. And it was

Install Alongside, Erase Disk, LVM, Encrypted Home and Something Else.

No option to upgrade and existing install. At least it did not tempt me to use the upgrade option with the possible result of wiping all the partitions on that disk. Is this particular bug only affecting UEFI systems or does it affect BIOS systems as well? Or perhaps it is as Ventrical said - Ubiquity is not smart. Too many OS for it to smartly offer to upgrade them.

Or, perhaps it is too soon after the holiday period for bug fixes to get into the daily image. I will wait until 14.04.2 comes up on the iso.qa.tracker.

Regards.

EDIT: @ventrical. I have just seen those screenshots from your post four posts back. Am I correct in thinking that the Vivid Xubuntu disk is offering to upgrade Ubuntu Vivid to Xubuntu Vivid? That would be a neat trick. People sometimes ask about changing from one flavour to another and we always say "A fresh install" is the only way.

---

### Post by kansasnoob on 2015-01-07
> No option to upgrade and existing install. At least it did not tempt me to use the upgrade option with the possible result of wiping all the partitions on that disk. Is this particular bug only affecting UEFI systems or does it affect BIOS systems as well? Or perhaps it is as Ventrical said - Ubiquity is not smart. Too may OS for it to smartly offer to upgrade them.

If more than one Ubuntu (or Ubuntu derivative) exists ubiquity doesn't offer the upgrade/replace option.

---

### Post by kansasnoob on 2015-01-07
> Am I correct in thinking that the Vivid Xubuntu disk is offering to upgrade Ubuntu Vivid to Xubuntu Vivid? That would be a neat trick. People sometimes ask about changing from one flavour to another and we always say "A fresh install" is the only way. 

It "sort of" works but things don't install as cleanly as a true fresh install. It's really sort of an odd bird in that if you use the replace/upgrade option it uses 'apt-clone' so it attempts to reinstall any and all packages that it detects as having been previously installed. Then if there are packages that it can't find it displays a warning at the end of re-installation saying that it couldn't restore all packages, but it's always just a boiler plate type of message.

If you ever perform an upgrade/replace via live media you'll be surprised to find that there is no var/log/installer but rather a ubiquity-apt-clone like this:

[ATTACH=CONFIG]259076[/ATTACH]

Here's [a link to a thread]("http://ubuntuforums.org/showthread.php?t=2242056") where I encountered a slight bit of leftover cruft from that upgrade/replace operation.

---

### Post by ventrical on 2015-01-07
> **grahammechanical said:**
> I just downloaded the trusty daily 20150107. Standard BIOS motherboard. 2 HD. Lots of partitions with lots of Ubuntus + Windows 8 preview. I wanted to see what Ubiquity offered. And it was

Install Alongside, Erase Disk, LVM, Encrypted Home and Something Else.

No option to upgrade and existing install. At least it did not tempt me to use the upgrade option with the possible result of wiping all the partitions on that disk. Is this particular bug only affecting UEFI systems or does it affect BIOS systems as well? Or perhaps it is as Ventrical said - Ubiquity is not smart. Too many OS for it to smartly offer to upgrade them.

Or, perhaps it is too soon after the holiday period for bug fixes to get into the daily image. I will wait until 14.04.2 comes up on the iso.qa.tracker.

Regards.

EDIT: @ventrical. I have just seen those screenshots from your post four posts back. Am I correct in thinking that the Vivid Xubuntu disk is offering to upgrade Ubuntu Vivid to Xubuntu Vivid? That would be a neat trick. People sometimes ask about changing from one flavour to another and we always say "A fresh install" is the only way.

I am assuming that when Ubiquity script searches for partitions (during the installation process) it is looking at the boot sector map and it is looking for the First Primary (Ubuntu and/or/both Windows Bootloader) Partition(s).  So , that would mean that even though there are *other* Primary partitions  in the mapping of BootSector/and/or GRuB_include, it (it meaning the Ubiquity script) is not going to report all the listed Primary *Ubuntu* partitions. *That* is why we have the expert_custom option of <something-else>.  Most of the expert_custom_options can be performed with <something-else>. I firmly believe that 90% of the  wishlist which we have seen here in this forum  can be performed with that tool. 

 However , as for UEFI and Hibernate, then we have to go and read some of OldFred's , Super Moderator, links on Grub and UEFI - not exactly a place where noobs can catch on in , say , a half an hour or so. We can weave patches  here in development version but it is a mountain to be able to present those translations to end_users who don't even know what a hard drive looks like or have never opened the back-side of their boxes.

Regards..

---

### Post by ventrical on 2015-01-07
> **grahammechanical said:**
> 

EDIT: @ventrical. I have just seen those screenshots from your post four posts back. Am I correct in thinking that the Vivid Xubuntu disk is offering to upgrade Ubuntu Vivid to Xubuntu Vivid? That would be a neat trick. People sometimes ask about changing from one flavour to another and we always say "A fresh install" is the only way.

Honestly I haven't tried that yet. Kansasnoob looks to have put up an accurate review on it. Perhaps you should try and dupe that and report results here please.

Regards..

---

### Post by kansasnoob on 2015-01-09
Just finally following up with non-UEFI hardware to check for any additional improvements or regressions and I see this buggy behavior still exists:

[Ubiquity offers to erase existing OS rather than use entire disc even when more than one disc exists]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1361914")

But that really is a variation of this long standing bug:

[Side-by-Side option only chooses one disk]("https://bugs.launchpad.net/ubuntu/+source/partman-auto/+bug/351473")

I wouldn't hold my breath waiting for that to be fixed since it's been a known issue since Jaunty.

---

### Post by sudodus on 2015-01-09
That's bad kansasnoob, but what about the bug discussed [earlier] in this thread:

[Install/reinstall wipes out all/other partitions]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192/")

Would you consider at least this bug wiped, or would you say they all are part of a poorly managed 'Install alongside' option?

---

### Post by kansasnoob on 2015-01-09
> **sudodus said:**
> That's bad kansasnoob, but what about the bug discussed [earlier] in this thread:

[Install/reinstall wipes out all/other partitions]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192/")

Would you consider at least this bug wiped, or would you say they all are part of a poorly managed 'Install alongside' option?

It should not result in wiping any existing OS or data, so IMHO we're OK. These changes are a definite improvement. But there are scenarios (such as having multiple drives or adequate free space available) where some knowledge is required. I don't think it's possible to make ubiquity altogether idiot-proof.

---

### Post by ventrical on 2015-01-09
> **sudodus said:**
> That's bad kansasnoob, but what about the bug discussed [earlier] in this thread:

[Install/reinstall wipes out all/other partitions]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192/")

Would you consider at least this bug wiped, or would you say they all are part of a poorly managed 'Install alongside' option?

  I know the question is not directed towards me but I think some of the things we would like Ubiquity to do  falls along the area known as 'wish-list'.  I would have liked to have tested the multiple-disk options a little more in depth. (I still may be able to do so if someone else hasn't already). I think the greater part of some of these problems/bugs (especially with mutiple -disks) have to do with .

1. How the BIOS is set up?
2. Are both disks MASTER, one MASTER, one SLAVE?
3. Are both disks SATA or is one SATA , one IDE or both IDE?
4. If both disks are SATA is an IDE DVD ROM connected?
5.. Will muti-disk work if IDE DVD/ROM  is removed?
6. Is USB hdd (not USB flash disk) connected during boot ?
7. Should I even mention RAID drives and how they are detected and configurated?
8. How about SCSI Adaptec PCI Card with RAID config?
  So there are a lot of factors to consider .

The STANDARD basic system that Ubiquity is designed for is a single disk system, Most OEM desktops come out of the factory with ONE (1) hdd installed. Anything more is considered 'custom' , hence <something else>. Just my view.

Regards..

---

### Post by sudodus on 2015-01-10
Yes, I agree with both of you.

Beyond the programming problems (program logic, detection of hardware and installed systems) there should be a good balance between ***encouraging*** the beginner to dare install an Ubuntu flavour OS, and ***warning*** that it might destroy the current content in the connected drive(s).

***Install alongside*** looks and is more convenient than ***Something else*** (I'd prefer ***Manual partitioning***), so it is encouraging the beginner, but I think they often do not realize the risks. Maybe people are too lazy to start by backing up the current system or at least the personal files, at least if the warning is not LOUD enough ;-)

---

### Post by kansasnoob on 2015-01-10
> **sudodus said:**
> Yes, I agree with both of you.

Beyond the programming problems (program logic, detection of hardware and installed systems) there should be a good balance between ***encouraging*** the beginner to dare install an Ubuntu flavour OS, and ***warning*** that it might destroy the current content in the connected drive(s).

***Install alongside*** looks and is more convenient than ***Something else*** (I'd prefer ***Manual partitioning***), so it is encouraging the beginner, but I think they often do not realize the risks. Maybe people are too lazy to start by backing up the current system or at least the personal files, at least if the warning is not LOUD enough ;-)

+1! In real life I always use "something else" because I like to be 100% in control, but I continue to test the other options offered to look for bugs.

---

### Post by grahammechanical on 2015-01-10
Something Else used to be called Guided. I was reminded of that the other day when I decided to test end of life release upgrades and I installed 9.10. The expression "Guided" really confused me because I was expecting to be given guidence and not be the one to give the guidence. Thankfully we can still back out at this point.

I think the ability to re-install or upgrade from the live session without using Something Else is a good thing to have. I am talking from the point view of the uneducated user.  We are trying to find out if it does it simply and accurately. And is there a difference between BIOS and UEFI boot systems. It does seem as if there is some progress in this matter.

Regards

---

### Post by ventrical on 2015-01-10
> **sudodus said:**
> Yes, I agree with both of you.

Beyond the programming problems (program logic, detection of hardware and installed systems) there should be a good balance between ***encouraging*** the beginner to dare install an Ubuntu flavour OS, and ***warning*** that it might destroy the current content in the connected drive(s).

***Install alongside*** looks and is more convenient than ***Something else*** (I'd prefer ***Manual partitioning***), so it is encouraging the beginner, but I think they often do not realize the risks. Maybe people are too lazy to start by backing up the current system or at least the personal files, at least if the warning is not LOUD enough ;-)

Windows8 is the same thing. Will not install unless ext4 partions are removed . It offers first Express (standard), then custom. So Ubuntu is not only one with multi-drive detect prob.

Regards..

---

### Post by ventrical on 2015-01-10
> **grahammechanical said:**
> Something Else used to be called Guided. I was reminded of that the other day when I decided to test end of life release upgrades and I installed 9.10. The expression "Guided" really confused me because I was expecting to be given guidence and not be the one to give the guidence. Thankfully we can still back out at this point.

I think the ability to re-install or upgrade from the live session without using Something Else is a good thing to have. I am talking from the point view of the uneducated user.  We are trying to find out if it does it simply and accurately. And is there a difference between BIOS and UEFI boot systems. It does seem as if there is some progress in this matter.

Regards

When I first started using Ubuntu  Hardy Heron version  it just worked:)lol .. and it kept getting better. By the time 10.10 came along I was just baffled at what the Ubiquity Installer could do. It saved me a lot of downtime. And it's no real sweat here because I like the challenge of working with customized systems and <something else> gives me that ways and means. Of course the forums have always provided help most always in less than 24 hours.

+1 ... and I have to hand it to the maintainers and devs who work to  make it better.

Regards..

---

### Post by ventrical on 2015-01-15
I think I have discovered what Ubiquity is doing when detecting more than one drive. It is choosing the logical largest partition to install alongside. In this case it was the Seagate 250GB hdd which largest partition with Ubuntu laready installed (140GBs) offered me up the "install alongside' option. This now makes all the sense in the world .. but please note that I used the 15.04 xubuntu daily iso. I also launched ubiquity --only from terminal.

```

ubiquity --only

```


will try now with 14.04.1

---

### Post by ventrical on 2015-01-15
Thats it .. thats whats happeneing..

---

### Post by ventrical on 2015-01-15
That's it .. that's what happening.

edit;

Notice for both xubuntu 15.04 and ubuntu 14.04.1 it no longer says windows Boot Loader but, rather, 'mutiple operating systems' and correctly chooses largest partiton.

regards..

---

### Post by ventrical on 2015-02-06
New 3TB SATA hdd is now purchased.

Does anybody have any suggested test cases?

Regards...

---

### Post by sudodus on 2015-02-06
A couple of suggestions:

1. Try if the problem of this thread will be fixed also in 14.04.2, LTS which is rescheduled to be released two weeks late (February 19).

2. Since the drive size > 2 GB you can check how the automatic installation to the whole drive works with a blank HDD (without any partition table) in BIOS/CSM mode. Will there be an MSDOS or a GUID partition table? Or must a partition table be created before installing?

---

### Post by ventrical on 2015-02-06
> **sudodus said:**
> A couple of suggestions:

1. Try if the problem of this thread will be fixed also in 14.04.2, LTS which is rescheduled to be released two weeks late (February 19).

2. Since the drive size > 2 GB you can check how the automatic installation to the whole drive works with a blank HDD (without any partition table) in BIOS/CSM mode. Will there be an MSDOS or a GUID partition table? Or must a partition table be created before installing?

Ok.. I'll try that.

  But here are specs and this hdd is designed to work with legacy specs and overcome other backward compatible errors.

[http://www.storagereview.com/seagate_barracuda_3tb_review_1tb_platters_st3000dm001](http://www.storagereview.com/seagate_barracuda_3tb_review_1tb_platters_st3000dm001)

I'll have to take current ssd out of one of my main EUFI desktops, install 3TBhdd and then boot into trusty or xubuntu 15.04 and report whatever the disk utility shows up.

Regards..

---

### Post by sudodus on 2015-02-06
Sounds good :-)

---

### Post by ventrical on 2015-02-06
Here is first screenshot. So it is clean drive.. no partiton from factory it appears.

---

### Post by ventrical on 2015-02-06
Next.. I will choose <erase and install>.

---

### Post by ventrical on 2015-02-06
Here is the next ..

---

### Post by ventrical on 2015-02-06
Ok... after installing trusty.iso here is the results: No wwill reboot into install.

---

### Post by sudodus on 2015-02-06
It seems to me that is works well - selects GPT and uses the whole drive.

One question: Is there reason to use 17 GB swap? How much RAM is there (16 GiB)?

---

### Post by ventrical on 2015-02-06
> **sudodus said:**
> It seems to me that is works well - selects GPT and uses the whole drive.

One question: Is there reason to use 17 GB swap? How much RAM is there (16 GiB)?

Yes. There is 16GB DDR3. It automatically chose that 17GB value.  Interesting?

---

### Post by ventrical on 2015-02-06
Next I will wipe and install in uEFI mode.

---

### Post by ventrical on 2015-02-06
UEFI success.

Now wipe and Windows 8 Install in UEFI mode.

---

### Post by sudodus on 2015-02-06
> **ventrical said:**
> Yes. There is 16GB DDR3. It automatically chose that 17GB value.  Interesting?

If you want hibernation, there should be at least

1024*1024*1024*16 bytes = 17179869184 bytes = approx 17.2 GB (and maybe there is, if you look closely).

---

### Post by sudodus on 2015-02-06
> **ventrical said:**
> UEFI success.
That's good, but no longer a surprise :-)> 
Now wipe and Windows 8 Install in UEFI mode.

---

### Post by ventrical on 2015-02-06
I installed Windows 10 tech-preview. I then proceeded to install 14.04 directly but Ubiquity could not find any other operating system.

 I am in live mode now - screenshot below. It only used 2.2TBs and left almost 800GBs as free space. I am going to try and install from live session / then / 15.04 if no success.

---

### Post by ventrical on 2015-02-06
Ok.. I ran gparted and ran into new problem. have not seen this one before. I did remove all partions before I installed Windows 10.

Any ideas?  I'm standing by.

---

### Post by sudodus on 2015-02-06
I recognize this problem. *Oldfred* has helped several people with the same problem. Maybe it will be solved with a fresh GUID partition table (not a blank drive, when you start installing Windows).

---

### Post by ventrical on 2015-02-06
Ok... sounds about right. I am going to abort this install and try 15.04 and see what happens and then try OldFreds method later.

---

### Post by sudodus on 2015-02-06
I don't know where the UEFI backup is stored, and it does not feel like a good idea to wipe the whole drive. Of course you can try to wipe the first and/or last megabyte and gigabyte but not terabytes :-P

---

### Post by ventrical on 2015-02-06
Xubuntu 15.04 comes up with an error 'starting sector number (n)exceeds the msdos partition -table imposed maximum sectors(n) and it does not recognize windows boot loader.

So my questions is.

1. I am , say , ie; an OEM installing Windows 10 on a blank drive. (I was able to do this successfully) You have mentioned to start out with GUID. Do they do this at the factory?

2. Can I create a GUID partition using the Windows 10 installer?

3. Any how to's that are not extremely verbose?

---

### Post by ventrical on 2015-02-06
xubuntu 15.04 screenshot

---

### Post by ventrical on 2015-02-06
Wiped 10, installed win 8 and now have gparted working in xubuntu 15.04

---

### Post by kansasnoob on 2015-02-06
I got far enough with that "new" mobo to see that the reinstall options at least look better in the 14.04.2 candidates as compared to the 14.04.1 images, but I didn't actually pull the trigger on a reinstall as I'm dealing with an off-topic issue:

[http://ubuntuforums.org/showthread.php?t=2264348](http://ubuntuforums.org/showthread.php?t=2264348)

That just comes down to a learning curve for me ;)

---

### Post by sudodus on 2015-02-07
> **ventrical said:**
> Xubuntu 15.04 comes up with an error 'starting sector number (n)exceeds the msdos partition -table imposed maximum sectors(n) and it does not recognize windows boot loader.

So my questions is.

1. I am , say , ie; an OEM installing Windows 10 on a blank drive. (I was able to do this successfully) You have mentioned to start out with GUID. Do they do this at the factory?

I think they make a master installation and clone it (OEM install). They tweak that master installation (and add bloatware), and Windows 8 and 8.1 are delivered with UEFI.
> 
2. Can I create a GUID partition using the Windows 10 installer?

I don't know in BIOS/CSM mode. It should be the default in UEFI mode.
> 
3. Any how to's that are not extremely verbose?

---

### Post by sudodus on 2015-02-07
> **ventrical said:**
> xubuntu 15.04 screenshot

> **ventrical said:**
> Wiped 10, installed win 8 and now have gparted working in xubuntu 15.04

What partition tables did you use in these cases?

It seems there are things to improve with Windows Technical Preview '10' (which can be understood).

---

### Post by ventrical on 2015-02-07
I could not get gparted to create an actual partition. It wanted to send some details to the developer, but , there were no details.

  Ubuntu correctly identifies, formats and installs the systems on the new, cutting edge hdd in BIOS and UEFI mode. Windows 10 and Windows 8 Tech Preview seem to have a problem with the geometry of the drive but are still able to install in UEFI mode.

gparted has a problem also with the new drive.  I am going to switch the drive to an older UEFI system and see if it works there. It could also be a setting I have set wrong in the BIOS of my newer MSi Mother board.

 Thanks for your suggest and info research. I am looking into all this still.

Regards..

---

### Post by sudodus on 2015-02-07
> **ventrical said:**
> ...
  Ubuntu correctly identifies, formats and installs the systems on the new, cutting edge hdd in BIOS and UEFI mode. Windows 10 and Windows 8 Tech Preview seem to have a problem with the geometry of the drive but are still able to install in UEFI mode.

gparted has a problem also with the new drive ...

It seems Ubuntu is faster than Windows and gparted to manage your new, cutting edge hdd :-

Did you look for the newest possible version of gparted?

---

### Post by ventrical on 2015-02-08
> **sudodus said:**
> It seems Ubuntu is faster than Windows and gparted to manage your new, cutting edge hdd :-

Did you look for the newest possible version of gparted?

Seems that this could be a possible fix.  I have to take  small break as my service provider notified me and told me I was way over my b/w limit for this month.  :)

Regards..

---

### Post by ventrical on 2015-02-08
I just wanted to document this here.

 I softbricked the hdd to the point where my newer UEFI system would not boot until I removed the new hdd. I then put it in another, older Intel UEFI system and I have it running up once again. I used gparted to resize the Windows partiton. All went well until I tried to create a swap drive.  I think then also it overwrote a file on the live USB drive of xubuntu - so i will have to re-burn that.. so this new technology is real fun :)

As you can see the information reported in gparted is not the same as reported in ubiquity <something else>.

Since I have now crashed the live xubuntu system I will burn the daily and try an install with that.

---

### Post by sudodus on 2015-02-09
How did you create the USB boot drive? If you flash the iso to USB with mkusb, it will be a read-only ISO9660 file system, and should not be allowed to be overwritten.

---

### Post by ventrical on 2015-02-09
SDC on 10.10 , discard on shutdown.  I think that the Windows 10 OS fired something at the USB stick. I have the drive installed now on older UEFI system .. but it completely locked up my new system.

  I will be testing this later :)

---

### Post by ventrical on 2015-02-09
I had found out that the problem is that I was NOT using the 'extend' option in the Windows 10  Installer. Windows Installer is not intuitive, such as is xubuntu (daily-live/current 15.04). So now it appears that I cn hard install and resize the partition, however, the Windows 10 Installer warned me that it could not be changed. Let's see what happens :)

---

### Post by ventrical on 2015-02-09
Keeping it simple :)

edit:

Just making a note that this was a success after using 'extend' from windows installer. If you do not use extend then Ubuntu cannot use the free extra space left over.

---

