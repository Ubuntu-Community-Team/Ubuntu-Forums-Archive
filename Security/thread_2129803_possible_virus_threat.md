---
title: "possible virus threat"
date: 2013-03-27
forum: Security
---

### Post by laopaishpe on 2013-03-27
scanning with AVIRA boot CD, I got a first warning about it not being able to read /lib/firmware/vxge/X3fw.ncf and .../vxge/X3fw_pxe.ncf.

My question is what do these files usually do ? I understand that the legit vxge directory is for flashing firmware via ethtool. Now, the good news, is I don't have ethtools (at least synaptic did not find it); the bad is why are these files encrypted ? and why are they symlinked somewhere else ? (a "ls -l" shows two entries for each one !)

On anoter note, in /lib/firmware there are two files: TDA7706_OM_v2.5.1_boot.txt and .._v3.0.2_boot.txt that when opened in leafpad show a bunch of hex numbers, addresses and asm istructions I would guess, definitely not a "text" file.  Did not check to see permissions on these, but again the question again is are these legit files? 

My system is Ubuntu 11.10, and was "updated" from 10.4 when I had another virus scare some months ago, when I wiped ouut all partitions and installed "clean". So my money would be on a "boot" type of virus, if any !  

The symptom: there is a sllight jerking of the mouse pointer, when for ex. trying to work in a file manager, or to open files in gimp, that I do not have on the other linux machine.

Any comments/inputs really appreciated.

---

### Post by Stonecold1995 on 2013-05-04
I don't think you have to worry.  If I remember, I've seen other people complain about that exact thing.  It seems like ClamAV has a lot of false positives.  Plus, it's not designed to scan for the few Linux viruses out there, it is designed for Windows and Macintosh malware.

Upload the files to virustotal.org if you want something like 40 different scanners checking the file (I love that site).

---

### Post by epicoder on 2013-05-05
Stonecold1995 is right about ClamAV. I only use it because a lot of my mail ends up at windows clients...

Also, [http://virustotal.com](http://virustotal.com) (not .org)

---

### Post by gsnoorky on 2013-05-07
This is the first time I've looked into this: I'm running xubuntu 12.10 AMD64, and now I get 100s (235 today) of false positives from ClamAV--this given a sys also with grub2-dual booting with Win7 HP 64-bit. Another sys with grub2-dual-booting WinXP SP3 and the same distro comes up clean--zero malware--apparently no false positives. I also have System Suite 14 on both systems--it seems to run correctly (of course, it can't get into EXT4 files). Sometimes, that comes up with something.  Clamav runs really slowly on my 7 system. 


What I've done until now is to parse those messages--I tend to avoid hacking away the files involved with Windows 7--I run SS for those. It has helped for me to use Blkviper's site to keep many programs (such as netlogon) from running automatically in Windows: Associated files no longer pop up.

Thanks for your recommended site:  I wonder if some setting, etc., that I'm missing in clamav that will cut down the false positives. Long ago, I did kill those files (once)--naturally, I had to re-install Win 7. It seems that the problem popped up after I started using 7. (For Windows, I use NTFS solely and for Xubuntu, EXT4 (and SWP, of course).) I just wonder why others haven't noted this great number of valid files being "fingered" by clamav given 7.... Duh, I've noted that my 7 is 64-bit--XP is 32-bit and well-known/well-seasoned.

I intend to upgrade to xubuntu 13+ soon. It seems to me that such errors are somewhat unacceptable--I know that clamav is far from perfect--especially given that it's intended to weed-out Win and Mac malware--it appears to be doing a poor job, here, given my  sys contexts. I don't want to fool with other programs, but I'll have to look into that, I suppose. I don't mind burning and booting from a CD/DVD, though--that likely would speed up things and give a more accurate picture of reality....

Clamav just now finished after several hours in this 7 sys: All sort of files fingered in the Windows directory--not just from MS--also ATi catalyst and many others. I'll get into 7 and run SS now. (I'd like to get virtual sys going someday--a step forward.) lastpass.js from open source always is fingered: I think that's wrong.

---

### Post by maglinu on 2013-05-07
> **gsnoorky said:**
> This is the first time I've looked into this: I'm running xubuntu 12.10 AMD64, and now I get 100s (235 today) of false positives from ClamAV--this given a sys also with grub2-dual booting with Win7 HP 64-bit. Another sys with grub2-dual-booting WinXP SP3 and the same distro comes up clean--zero malware--apparently no false positives. I also have System Suite 14 on both systems--it seems to run correctly (of course, it can't get into EXT4 files). Sometimes, that comes up with something.  Clamav runs really slowly on my 7 system. 


What I've done until now is to parse those messages--I tend to avoid hacking away the files involved with Windows 7--I run SS for those. It has helped for me to use Blkviper's site to keep many programs (such as netlogon) from running automatically in Windows: Associated files no longer pop up.

Thanks for your recommended site:  I wonder if some setting, etc., that I'm missing in clamav that will cut down the false positives. Long ago, I did kill those files (once)--naturally, I had to re-install Win 7. It seems that the problem popped up after I started using 7. (For Windows, I use NTFS solely and for Xubuntu, EXT4 (and SWP, of course).) I just wonder why others haven't noted this great number of valid files being "fingered" by clamav given 7.... Duh, I've noted that my 7 is 64-bit--XP is 32-bit and well-known/well-seasoned.

I intend to upgrade to xubuntu 13+ soon. It seems to me that such errors are somewhat unacceptable--I know that clamav is far from perfect--especially given that it's intended to weed-out Win and Mac malware--it appears to be doing a poor job, here, given my  sys contexts. I don't want to fool with other programs, but I'll have to look into that, I suppose. I don't mind burning and booting from a CD/DVD, though--that likely would speed up things and give a more accurate picture of reality....

Clamav just now finished after several hours in this 7 sys: All sort of files fingered in the Windows directory--not just from MS--also ATi catalyst and many others. I'll get into 7 and run SS now. (I'd like to get virtual sys going someday--a step forward.) lastpass.js from open source always is fingered: I think that's wrong.

Are you using clamav (terminal) or clamtk (gui)?

Clamtk has PUP/PUA enabled by default. Clamav default scan setting doesn't.

---

