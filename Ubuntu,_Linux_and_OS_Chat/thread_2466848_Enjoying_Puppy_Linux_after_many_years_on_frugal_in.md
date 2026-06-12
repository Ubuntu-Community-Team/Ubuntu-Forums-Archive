---
title: "Enjoying Puppy Linux after many years on frugal install of Fossapup64 9.5"
date: 2021-09-08
forum: Ubuntu, Linux and OS Chat
---

### Post by kagashe on 2021-09-08
Last time I used Puppy Linux was in Jan 2008 (Puppy 4.0). Afterwards Puppy Linux was being built in many flavours one of them built software repos from Ubuntu for apps. Then came UEFI and I thought Puppy Linux could not be used on UEFI machines.

Recenly I downloaded Fossapup64 9.5 iso, copied vmlinuz, initrd.gz and the four .sfs files on Fossapup directory on Ubuntu 20.04 partition, added following lines to /etc/grub.d/40_custom:
```
menuentry 'Fossapup64 9.5' {
search --no-floppy --fs-uuid --set 1e364a7e-9e6d-468a-99a2-404936a14d59
linux /Fossapup/vmlinuz pfix=nocopy pmedia=atahd psubdir=Fossapup 
initrd /Fossapup/initrd.gz 
}
```
updated grub and booted into Fossapup Desktop.

I appended pfix=nocopy to linux command because I wanted to add Gnucash and Libreoffice to frugal installation.

I was surprised to find flatpak in the Puppy Package Manager. I installed flatpak and Gnucash 4.6 in it. I could open my .gnucash file on Ubuntu partition which was already mounted for using Fossapup folder. It worked nicely with Stocks/MFs getting updated with Finance:Quote.

For Libreoffice I found the menu item Menu/Document/Get_Libreoffice_download_and_install_Libreoffice and installed Libreoffice 7.2.

I installed Firefox from quickpet and I could update it to Firefox 92 through Help/About_Firefox.

I could make the Sound work through Alsa_Sound_Wizard/Soundcard_wizard.

As I use Hindi/Marathi typing I added India Keyboard and installed fonts-indic and fbxkb (Keyboard Indicator) from Puppy Package Manager. 

I could adjust backlight through Menu/Desktop/Redshift.

I installed Aisleriot and Mahjongg games.

In fact every thing I could set to my liking in the JWM Desktop.

Fantastic progress by Puppy Linux.

Kamalakar

---

### Post by zebra2 on 2021-09-10
yep! I first started using linux with Carolina Puppy and others about the same time.  Fossapup looks really polished.  I especially like the fact that my wireless mouse worked which was hard to come by back in those days. I haven't done much more than get it running but will install some of my programs this weekend and see what happens. 

```

40_custom
menuentry "foss"{
set root='(hd0,2)'
linux (hd0,2)/foss/vmlinuz psubdir=/foss
initrd (hd0,2)/foss/initrd.gz
```

---

### Post by kagashe on 2021-09-10
> **zebra2 said:**
> yep! I first started using linux with Carolina Puppy and others about the same time.  Fossapup looks really polished.  I especially like the fact that my wireless mouse worked which was hard to come by back in those days. I haven't done much more than get it running but will install some of my programs this weekend and see what happens. 

```

40_custom
menuentry "foss"{
set root='(hd0,2)'
linux (hd0,2)/foss/vmlinuz psubdir=/foss
initrd (hd0,2)/foss/initrd.gz
```

By default Puppy Linux runs in RAM. Remember to append pfix=nocopy to linux command if you plan to add big programs like I wanted gnucash & libreoffice. Initially I tried Ubuntu default gnucash 3.8 but it failed to fetch Finance Quotes. Then I installed flatpak and the latest stable gnucash worked nicely.

In addition the frugal install with pfix=nocopy option saves the session automatically without any prompt.

Kamalakar

---

### Post by zebra2 on 2021-09-12
I know Puppy runs in RAM, which means it has come of age, since today RAM is cheap and plentiful and I have RAM that has never been used.  Regarding frugal, I prefer to use a save file that allows me to take the Puppy to any computer in the house or elsewhere. I really don't see Puppy getting close to the max of my systems. But really it is just a toy. I need a full featured heavy desktop system like Ubuntu Impish and Gnome 40.2. But it is still nice to have something I can carry in my pocket so thanks for the thread. Fossa is a really nice edition of puppy with quite a bit of advancements.

---

### Post by sudodus on 2021-09-12
I never used Puppy regularly, but I have tested several versions, and I agree with you that it is a nice Linux distro. Barry Cauler has continued with [Easy OS](https://easyos.org/). Have a look at it if you didn't already.

---

### Post by zebra2 on 2021-09-12
EasyOS installs to a boot partition.  I don't think it will boot from a directory which is normal for puppy. Normally frugal install just means that the directory that contains the puppy also contains all of the data.  A non-frugal install has its data in a 'save" file. One may even accumulate multiple save files that are dated. This makes Puppy Linux very convenient especially if one is traveling and doesn't want to expose the system OS.  Since EasyOS installs to a partition it has to support EFI if the partition is part of a EFI enabled system, which it does. Normally a Puppy doesn't need EFI support because it loads from a directory.  What all this means is ........Not for me!  But thanks for the post. Interesting!

---

