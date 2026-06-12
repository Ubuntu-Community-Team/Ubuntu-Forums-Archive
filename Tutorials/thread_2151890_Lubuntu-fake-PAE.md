---
title: "Lubuntu-fake-PAE"
date: 2013-06-06
forum: Tutorials
---

### Post by sudodus on 2013-06-06
[SIZE=4]The new version 14.04 LTS 'Trusty Tahr' needs no fake-PAE. Use **forcepae** in the standard installers[/SIZE]

The new version 14.04 LTS 'Trusty Tahr', needs no fake-PAE to work with Pentium M and Celeron M CPUs. Instead you use the [boot option]("https://help.ubuntu.com/community/BootOptions") **forcepae** and boot from the standard desktop installer and alternate installer for 32-bit systems. I think Lubuntu and Xubuntu will work well in laptops with these CPUs. Xubuntu has a medium light desktop environment and Lubuntu has an ultra light desktop environment. Try both to find what is best for you.

[This is a detailed description how to use forcepae]("https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M").
[SIZE=4]
Some processors need a **non-pae** kernel[/SIZE]

The vast majority of Pentium M and Celeron M CPUs are suitable for  fakepae or forcepae and can work with PAE kernels. But some of these  processors need a [non-pae kernel]("https://help.ubuntu.com/community/9w")  also for new versions of Lubuntu. There are also other 'not too old'  CPUs that lack PAE capability: Transmeta Crusoe and VIA processors  around 1 GHz. 

[SIZE=4]**Introduction**[/SIZE]

 **PAE (Physical Address Extension)** is explained [here]("https://help.ubuntu.com/community/PAE") in details.

Lubuntu-fake-PAE  offers a method to install Lubuntu 13.10 into computers (mainly if not  only laptops) with Pentium M and Celeron M CPUs. Most if not all of  these CPUs have PAE capability, but show no PAE flag. This means that  these machines can not use any Lubuntu versions after 12.04 and  therefore, Lubuntu 12.10, 13.04 and 13.10 can not be installed and  their kernels can not be upgraded, because the software is checking for  the PAE flag. This can be fixed with fake-PAE, developed by Bernd Kreuss  [prof7bit]("https://launchpad.net/%7Eprof7bit/+archive/fake-pae") and described in the [Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=2113826&p=12504589#post12504589").  

There are many high-quality professional class laptops around with Pentium M CPUs, for example IBM Thinkpad T40, T41 and T42. 

Three  methods are described to make the new Ubuntu family 32-bit PAE kernels  available for Pentium M and Celeron M, that have PAE capability, but do  not show the PAE flag.


[LIST]
[*]Method to start from the Ubuntu 12.04 non-PAE mini-iso file described by mörgæs 
[*]'grub-n-iso' 
[*]Installed system 
[/LIST]
[HR][/HR]
[SIZE=4]**Lubuntu Fake-PAE described by sudodus**[/SIZE]

 The  idea is to make it easier for people who want to go directly into a new  version of Lubuntu. This is a good alternative for a fresh install  (instead of downloading 12.04 and upgrading twice to newer releases). 

Right now the image files to download reside on these links
 
[google drive of Nio Wiklund alias sudodus]("https://drive.google.com/folderview?id=0B46yhFQuJvfPRXRvSmJ6b0xoNE0&usp=sharing") -- link for 'all' files
[http://phillw.net/isos/lubuntu-fake-pae](http://phillw.net/isos/lubuntu-fake-pae) -- fast and stable link for the big image files, thank you [*phillw*]("http://ubuntuforums.org/member.php?u=824544")

**Test**

Thank you! 

Helpful  members of the Ubuntu and Lubuntu communities have found that fake-PAE  works with almost all Celeron M and Pentium M, and the instructions have been  improved. 


A  Celeron M 1.2 GHz is maybe one year older than a tested Pentium M with  1.6 GHz (Banias) and maybe two years older than another Pentium M  (Dothan) with 1.7 GHz. The newest Pentium M CPUs have the PAE flag, and  need no fake-PAE. We have found out and need not guess from what we find  at the internet, for example:  [here]("https://en.wikipedia.org/wiki/Pentium_M").
 

Our  test results so far for Pentium M and Celeron M CPUs suitable for  fakePAE, 'No PAE flags but 36 bit physical memory address size': 

```

         ---- CPU name ----  -- CPUID Output of 'cpuid|grep ^00000001' --
Lowest:  Celeron M 1200 Mhz  00000001 00000695 00000812 00000000 a7e9f9bf
         Celeron M 1300 MHz  00000001 00000695 00000812 00000000 a7e9f9bf
         Celeron M 1.40 GHz  00000001 00000695 00000816 00000180 a7e9f9bf
         Pentium M 1.50 GHz  00000001 000006d6 00000816 00000180 afe9f9bf
         Pentium M 1600 MHz  00000001 00000695 00000816 00000180 a7e9f9bf
         Pentium M 1.70 GHz  00000001 000006d6 00000816 00000180 afe9f9bf
         Pentium M 1.70 GHz  00000001 000006d6 00000816 00000180 afe9fbbf
Highest: Pentium M 2.10 GHz  00000001 000006d6 00000816 00000180 afe9f9bf

```

Your help and support was highly appreciated and needed.

Our test results so far for Pentium M and Celeron M CPUs **not** suitable for fakePAE, 'No PAE flags and only 32 bit physical memory address size': 

         ```

         ---- CPU name ----  -- CPUID Output of 'cpuid|grep ^00000001' --
Lowest:
         Pentium M 1200 Mhz  00000001 00000695 00000816 00000180 a7e9fbbf
Highest: 

```

Your help and support is still highly appreciated and needed. 

[LEFT][COLOR=#333333][FONT=Ubuntu]If you are a new user, you can check the PAE capability in your own computer. Running Lubuntu 12.04 with a non-pae kernel
[/FONT][/COLOR][/LEFT]
 ```

cat /proc/cpuinfo

```
reports  32 bits physical address size for a tested computer with Pentium M, but  running Lubuntu 13.10 and 14.04 LTS, it reports 36 bits physical address size. So you  need the PAE kernel running to get 36 bits. If you don't get 36 bits  with a PAE kernel, your CPU has no PAE capability. 

Details: [CPU-info & OS-info]("https://help.ubuntu.com/community/CPUinfoFakePAE") 

The  following screen shots were recorded in an IBM Thinkpad T42 and  correspond to the information in the 'CPU-info & OS-info' link 
[URL="https://help.ubuntu.com/community/Lubuntu-fake-PAE?action=AttachFile&do=view&target=installed-12.04.2-new-with-pentium-m.jpg"]
Lubuntu 12.04.2 with Pentium M[/URL] and [Lubuntu 13.04 with Pentium M]("https://help.ubuntu.com/community/Lubuntu-fake-PAE?action=AttachFile&do=view&target=installed-system-with-pentium-m.jpg") 
 
From  the feed-back so far, 'grub-n-iso' seems more popular than 'installed  system'. Unless this changes, future versions of Lubuntu-fake-PAE will  focus on 'grub-n-iso'. 
 
**Checksums and signature**

 Please use checksums to verify that the download was successful. There is a file **md5sums.txt.asc**  for each of 'grub-n-iso' and 'installed system'. It contains the  md5sums of the files to be downloaded, the instructions as well as the  compressed image files (.img.gz files). This file is signed with gpg and  you can verify it according to the following commands. 
```

gpg --keyserver hkp://pgp.mit.edu --recv-keys EB0FC2C8
gpg --verify md5sums.txt.asc

```
The  warning "This key is not certified with a trusted signature! There is  no indication that the signature belongs to the owner." means that there  is no chain of trusted keys between your computer's keyring and the  key, that was used to sign the checksums (the key of sudodus). Check  that the text here and the output, when you verify it, match. 
```

lubuntu@lubuntu:~/test/pae4pm/grub-n-iso$ [COLOR=#0000ff]gpg --keyserver hkp://pgp.mit.edu --recv-keys EB0FC2C8[/COLOR]
gpg: requesting key EB0FC2C8 from hkp server pgp.mit.edu
gpg: /home/lubuntu/.gnupg/trustdb.gpg: trustdb created
gpg: [COLOR=#008000]key EB0FC2C8: public key "Nio Sudden Wiklund (sudodus)[/COLOR] <address@mailserver.com>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
lubuntu@lubuntu:~/test/pae4pm/grub-n-iso$ [COLOR=#0000ff]gpg --verify md5sums.txt.asc[/COLOR]
gpg: Signature made Sun 02 Jun 2013 10:20:57 AM UTC using RSA key ID EB0FC2C8
gpg: [COLOR=#008000]Good signature from "Nio Sudden Wiklund (sudodus)[/COLOR] <address@mailserver.com>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 0303 EA77 E34C 52F2 2958  47C6 BD43 C742 EB0F C2C8
lubuntu@lubuntu:~/test/pae4pm/grub-n-iso$

```
Then  there is reason to trust that nobody else has written the checksums.  The date of the signature will change at updates, and the text might be  translated to your local language, but it should be clear that it is a  'Good signature from "Nio Sudden Wiklund (sudodus)"'.
[HR][/HR]
[B][SIZE=4]Method to start from the Ubuntu 12.04 non-PAE mini-iso file described by mörgæs
[/SIZE][/B]
 [https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE) 

A variant of this method is that people who have 


[LIST]
[*]more or less personalized versions of Lubuntu 12.04 running, or 
[*]already have a Lubuntu 12.04 iso file and a slow internet connection 
[/LIST]

use fake-PAE to upgrade to 12.10. 13.04 and/or 13.10.
[HR][/HR]
[SIZE=4]**'grub-n-iso'**[/SIZE]

  **Detailed description**

 You find the detailed description at [grub-n-iso]("https://help.ubuntu.com/community/grub-n-iso") 
 
**Advantages**


[LIST]
[*]Similar to normal installation (via 1GB or 2GB USB drive) 
[*]No upgrading between versions is necessary 
[*]Full flexibility, for example to make a dual boot system 
[*]The official Lubuntu i386 desktop iso file is used, and can be checked with **md5sum** 
[/LIST]

```

5e85e368b6eaf1b9f5cf88467c6570f5  lubuntu-13.10-desktop-i386.iso

```
according to [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) 
 
**Disadvantages**

 
[LIST]
[*]You do not get a complete wor&#7729;ing operating system directly 
[*]You need to install fake-pae using 7bit's ppa after the installation 
[*]It uses the desktop iso file, while the alternate iso file can install to systems with lower RAM. 
[/LIST]
 
**Warning**

 This Lubuntu Raring 'grub-n-iso&#8217; system is only intended for Pentium M and Celeron M, that have PAE capability but no PAE flag. **We take no responsibility for any damage, that this software can cause**. 

You find the detailed description at [URL="https://help.ubuntu.com/community/grub-n-iso"]grub-n-iso
[/URL][HR][/HR]
[SIZE=4]**Installed system**[/SIZE]

  **Detailed description**

 You find the detailed description at [InstalledSystemFakePAE]("https://help.ubuntu.com/community/InstalledSystemFakePAE") 
 
**Advantages**

 
[LIST]
[*]No live install CD/DVD/USB drive is used 
[*]No upgrading between versions is necessary 
[*]You get a complete wor&#7729;ing operating system directly 
[/LIST]
 
**Disadvantages**

 
[LIST]
[*]It is a different way to install a system 
[*]Lubuntu 13.04 installs into 16 GB (the first 16 GB of a drive) 
[*]Lubuntu 13.10 installs into 4 GB (the first 4 GB of a drive) 
[*]It is easier to use 'grub-n-iso' for a dual boot system 
[/LIST]
This  Lubuntu Raring 'installed system' can run with Pentium M and Celeron M  CPUs. It has been tested from a USB 3 pendrive and from a hard disk  drive. It uses the fake-PAE method of 7bit @ubuntuforums to let the  32-bit PAE kernel be updated with CPUs without a PAE flag. 

When running Lubuntu 12.04 with a non-pae kernel 

```
 cat /proc/cpuinfo
```
reports  32 bits physical address size for my Pentium M, but when running  Lubuntu 13.04 and 13.10, it reports 36 bits physical address size.

So you need the pae kernel running to get 36 bits. If you don't get 36 bits with a pae kernel, your CPU has no PAE capability. 
 
**Warning**

 This Lubuntu Raring 'installed system' is only intended for Pentium M and Celeron M, that have PAE capability but no PAE flag. **We take no responsibility for any damage, that this software can cause**.

You find the detailed description at [URL="https://help.ubuntu.com/community/InstalledSystemFakePAE"]InstalledSystemFakePAE

[IMG]https://help.ubuntu.com/community/Lubuntu-fake-PAE?action=AttachFile&do=get&target=panel-13.04.jpg[/IMG] [/URL]

---

### Post by sudodus on 2013-06-18
I installed the Saucy 32-bit daily build from a computer with PAE to a USB drive and could boot it in my IBM Thinkpad T42 with Pentium M without any problems. It runs well as it is (and if I install fake-PAE I will also be able to update the kernel). See the attached picture

---

### Post by sudodus on 2013-07-19
Two tests were added: shown in [COLOR=#0000cd]blue[/COLOR]. For the first time a Pentium M CPU was found not suitable for fakePAE.

Our  test results so far for Pentium M and Celeron M CPUs suitable for   fakePAE, 'No PAE flags but 36 bit physical memory address size': 
```

         ---- CPU name ----  -- CPUID Output of 'cpuid|grep ^00000001' --
Lowest:  Celeron M 1200 Mhz  00000001 00000695 00000812 00000000 a7e9f9bf
         [COLOR=#0000cd]Celeron M 1300 MHz  00000001 00000695 00000812 00000000 a7e9f9bf [/COLOR]
         Celeron M 1.40 GHz
         Pentium M 1.50 GHz  00000001 000006d6 00000816 00000180 afe9f9bf
         Pentium M 1600 MHz  00000001 00000695 00000816 00000180 a7e9f9bf
Highest: Pentium M 1.70 GHz  00000001 000006d6 00000816 00000180 afe9f9bf

```

Our test results so far for Pentium M and Celeron M CPUs **not** suitable for fakePAE, 'No PAE flags and only 32 bit physical memory address size': 

         ```

         ---- CPU name ----  -- CPUID Output of 'cpuid|grep ^00000001' --
Lowest:
        [COLOR=#0000cd] Pentium M 1200 Mhz  00000001 00000695 00000816 00000180 a7e9fbbf[/COLOR]
Highest: 

```
 [COLOR=#333333][FONT=Ubuntu]
[/FONT][/COLOR]

---

### Post by sudodus on 2013-07-31
Lubuntu Saucy works  quite well now. Yes, of course there are still some bugs, but the  overall experience is nice, partly due to zRAM, partly due to many  improvements under the hood. We are getting ready for the end of life of  XP in April 2014.
  [HR][/HR]
An experimental alpha-2 version of Lubuntu Saucy can be installed on a  drive with at least 4 GB. The drive is rather small, but there is  enough space to test Saucy on your computer.
  
I have made a compressed image for Lubuntu-fake-PAE Saucy Alpha-2  installed system, that can be downloaded and tested in any standard  intel/amd computer, that can run 32-bit code (including Celeron M and  Pentium M, but excluding pre Pentium 2 CPUs and UEFI systems).
  
It can be downloaded according to this wiki page
                       
             [InstalledSystemFakePAE - Community Ubuntu Documentation]("https://help.ubuntu.com/community/InstalledSystemFakePAE")

               and installed (running with superuser privileges)
  
```
zcat dd_saucy-a2-installed-system_4GB.img.gz | dd bs=4096 of=/dev/sdx
```
  
The Saucy alpha-2 version has fake-PAE and htop, and a simple  touchpad-toggle 'TT'. It is too early to get touchpad-indicator and  ubuntu-tweak. As long as there is free space, it is possible to  update/upgrade the system. It will be a rough ride until the official  release, but you can always re-install from the compressed image file.
 
  See this screenshot.

  [URL="http://ubuntu-discourse.s3.amazonaws.com/259c55ecba9e3456cb33025ef4b9070de76ef806420.jpg"][IMG]https://ubuntu-discourse.s3.amazonaws.com/259c55ecba9e3456cb33025ef4b9070de76ef806420.jpg[/IMG] dd_saucy-a2-installed-system_4GB.jpg800x600 | 50.9 KB 
[/URL]
  Please check if you have the following bugs also after update/upgrade:


[LIST=1]
[*]The standard hotkeys PrintScreen and alt+PrintScreen for screenshots do not work, but the terminal command scrot works. 
[*]Only a few of the alternatives at the top right corner of the log  in screen work. Most of them are 'dead' now (some of those worked a few  days ago). 
[/LIST]
[HR][/HR]
If you try it, let me know the result, good or bad! I'm happy to read  about good results, but I learn more from the bad ones ;-)

---

### Post by sudodus on 2013-08-16
Right now the image files to download reside on these links
 
[google drive of Nio Wiklund alias sudodus]("https://drive.google.com/folderview?id=0B46yhFQuJvfPRXRvSmJ6b0xoNE0&usp=sharing") -- link for 'all' files, thank you Big Brother ;-)
[http://phillw.net/isos/lubuntu-fake-pae](http://phillw.net/isos/lubuntu-fake-pae) -- fast and stable link for the big image files, thank you [*phillw*]("http://ubuntuforums.org/member.php?u=824544") :-)

---

### Post by sudodus on 2013-10-23
There are ***new image files*** for Lubuntu 13.10 Saucy Salamander to be downloaded.

```
Lubuntu-13.10-desktop-grub-n-iso.img.gz
Lubuntu-13.10-desktop-grub-n-iso-n-swap.img.gz
```

These images contain the Saucy i386 iso file

```
 lubuntu-13.10-desktop-i386.iso
```

See these links
[URL="https://help.ubuntu.com/community/Lubuntu-fake-PAE"]
https://help.ubuntu.com/community/Lubuntu-fake-PAE[/URL]
[https://help.ubuntu.com/community/grub-n-iso](https://help.ubuntu.com/community/grub-n-iso)

---

### Post by sudodus on 2013-10-30
There is ***new image file*** for Lubuntu 13.10 Saucy Salamander to be downloaded for the 'installed system' method.

```
dd-LubuSaucy-pae2pm-4GB.img.xz
```

See these links
[URL="https://help.ubuntu.com/community/Lubuntu-fake-PAE"]
https://help.ubuntu.com/community/Lubuntu-fake-PAE[/URL]
[https://help.ubuntu.com/community/InstalledSystemFakePAE](https://help.ubuntu.com/community/InstalledSystemFakePAE)

---

### Post by sudodus on 2013-12-16
One test was added: shown in [COLOR=#0000cd]blue[/COLOR].
```
         ---- CPU name ----  -- CPUID Output of 'cpuid|grep ^00000001' --
Lowest:  Celeron M 1200 Mhz  00000001 00000695 00000812 00000000 a7e9f9bf
         Celeron M 1300 MHz  00000001 00000695 00000812 00000000 a7e9f9bf
         Celeron M 1.40 GHz  00000001 00000695 00000816 00000180 a7e9f9bf
         Pentium M 1.50 GHz  00000001 000006d6 00000816 00000180 afe9f9bf
         Pentium M 1600 MHz  00000001 00000695 00000816 00000180 a7e9f9bf
         Pentium M 1.70 GHz  00000001 000006d6 00000816 00000180 afe9f9bf
Highest: [COLOR=#0000ff]Pentium M 2.10 GHz  00000001 000006d6 00000816 00000180 afe9f9bf[/COLOR]
```

---

### Post by sudodus on 2013-12-29
There is a new experimental tarball for the [One Button Installer, 'OBI']("http://ubuntuforums.org/showthread.php?t=2172971") of Lubuntu 13.10 with a ***non-pae kernel***. You are welcome to test it, but beware, it is an early version, and you can expect that there are some problems.

See this post [http://ubuntuforums.org/showthread.php?t=2172971&p=12885903#post12885903](http://ubuntuforums.org/showthread.php?t=2172971&p=12885903#post12885903)

---

### Post by sudodus on 2014-03-29
[SIZE=4]**News**[/SIZE]

The new version Trusty Tahr, to become 14.04 LTS, needs no fake-PAE to  work with Pentium M and Celeron M CPUs. Instead you use the [boot option]("https://help.ubuntu.com/community/BootOptions") **forcepae**  and boot from the standard desktop installer and alternate installer  for 32-bit systems.

---

### Post by sudodus on 2014-04-18
[SIZE=4][/SIZE][SIZE=4]The new version 14.04 LTS 'Trusty Tahr', needs no fake-PAE. Use forcepae in the standard installers[/SIZE]

The new version 14.04 LTS 'Trusty Tahr', needs no fake-PAE to work with Pentium M and Celeron M CPUs. Instead you use the [boot option]("https://help.ubuntu.com/community/BootOptions") **forcepae**  and boot from the standard desktop installer and alternate installer  for 32-bit systems. I think Lubuntu and Xubuntu will work well in  laptops with these CPUs. Xubuntu has a medium light desktop environment  and Lubuntu has an ultra light desktop environment. Try both to find  what is best for you.

[This is a detailed description how to use forcepae]("https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M").

---

