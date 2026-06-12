---
title: "update-manager -d from 14.04 upgrades directly to 16.04"
date: 2015-10-30
forum: Ubuntu Development Version
---

### Post by mikio on 2015-10-30
what is going on? i decided to go ahead not realizing that it was actually 16.04 and not 15.04 -  i am now worried what will be broken and what not - any comments? it is in the middle of installing everything, so i believe it is too late to stop it.

just now i have a could not install sysv-rc - i am getting worried that i will have broken my system :( lets see

and now Could not install '/var/cache/apt/archives/systemd-sysv_227-2ubuntu1_amd64.deb'

and now Could not install 'systemd-sysv'

The upgrade will continue but the 'systemd-sysv' package may not be in a working state. Please consider submitting a bug report about it.

this seems to be turning into a nightmare

---

### Post by grahammechanical on 2015-10-30
It will. Won't it? It is the -d switch. -d = development version. You told the OS to upgrade to the next available development version. See Upgrading to development releases.

[https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades)

Edit: One of the big differences between 14.04 and 15.04 is the replacement of upstart as the init system with systemd. What you are in the process of getting is 15.10 with some updates that have been made to the 16.04 development version (xenial). 

You should also get another option in the Advance Options for Ubuntu sub-menu of the grub boot menu. If you find that the OS is broken because of the systemd files then boot with the upstart option in the Advanced options sub-menu. That option may still be available.

Regards.

---

### Post by mikio on 2015-10-30
you are right, of course - i should have known better .. i use linux exclusively since 12 years :) funny that his can happen to me - just one moment of not being careful - and i was actually keeping 14.04 for such a long time because it is my production machine and all was working smooth.

but after some upgraded where after i did not reboot my network/skype indicators disappeared and i - while chatting with people from work on skype / decided to go for my not so wise update-manager -d 

i can laugh about it - but now i have to save my data - i can not boot anymore - on the current and the older kernels, in normal or recovery mode - kernel panic .. not too bad, i save it - any recipes of how to rescue such a broken system? i will find them online, just in case you could point me to some help - i would appreciate your support.

love ubuntu - serves me well since years! thank you all!

---

### Post by grahammechanical on 2015-10-30
Is there an upstart option in Advanced options for Ubuntu of the Grub boot menu?

---

### Post by mikio on 2015-10-30
just checked - no, just the various previously used kernels - and the recovery mode for each - all panic ..

---

### Post by mikio on 2015-10-30
i am download 15.10 and creating a loadable usb. i will then rescue my data in my home directory and maybe try some rescue operations .. but i feel i should just install a clean 15.10 and simply use a couple of hours to get all running again - it has been 1.5 years now - why not ..
all good - i am sure i did not loose my data ..

---

### Post by mikio on 2015-10-30
can you help me - is there a way i can use chroot to try to fix the partial/failed upgrade???

---

### Post by Mateusz Stachowski on 2015-10-30
> **mikio said:**
> can you help me - is there a way i can use chroot to try to fix the partial/failed upgrade???

Yes there is. When I have such problems I refer to wiki about reinstalling GRUB 2. There is a section describing use of chroot.

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

> [COLOR=#333333][FONT=Ubuntu]via ChRoot
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]This method of installation uses the [/FONT][/COLOR][COLOR=#333333][FONT=inherit]chroot[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] command to gain access to the broken system's files. Once the chroot command is issued, the LiveCD treats the broken system's / as its own. Commands run in a chroot environment will affect the broken systems filesystems and not those of the LiveCD.[/FONT][/COLOR]

---

### Post by mikio on 2015-10-31
thank you

---

