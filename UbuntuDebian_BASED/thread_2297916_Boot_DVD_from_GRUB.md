---
title: "Boot DVD from GRUB"
date: 2015-10-07
forum: Ubuntu/Debian BASED
---

### Post by Gabriel_Appugliese on 2015-10-07
I would like to boot a dvd from GRUB.
i have a MacBookPro11,5 with rEFInd installed and working but i can't boot the Kali dvd on it because it has no efi support, well atleast on my machine it doesnt.
so i have installed ubuntu on here for now, boots up and can be used im happy with it for now.

i had booted the kali graphical installation from a usb by following this [guide]("https://community.spiceworks.com/how_to/66948-uefi-kali-linux-live-usb-on-surface-pro"), but i couldn't boot the live part because it cant mount from a usb3.0 ("error couldnt find a live medium" or something along the lines of that) i need to boot to live to partition because im following a guide on their site
 and after the install i need to boot into live again todo some last changes to sync the drives and convert it to hybrid and shtuff.

so i burned the Kali image to a dvd and need to find a way to add the cdrom entry to the grub menu
is this possible, if this is a repost sorry i did do a bit of research but only thing that showed up was suggestions to boot it with BIOS, i dont have one so they're useless, ive been looking up crap for 5 days trying to make rEFInd boot a legacy loader with no luck at all, im just tired of searching and reading at this point

if you can make rEFInd boot a legacy loader than i will gladly do that instead but for now this is my only option

---

