---
title: "GRUB died on external HDD or smthn idk"
date: 2022-10-28
forum: Ubuntu, Linux and OS Chat
---

### Post by viction2 on 2022-10-28
So I have an external HDD with ALL of my logins running windows and one day while i was running it it just started to slow down alot (games i run at like 100fps were getting all choppy and stuff) so i decided to restart my computer because that would normally help but it didnt the HDD just became unusable it just doesnt boot (shows black screen with cursor that i can use but thats it)i wasnt to worried about it for like a month until i accidentaly wiped my backup drive (yes i know im stupid) and i lost my phone so i cant login to anything even if i could remember the 80 char passwords because well my phone had 2fa on it. but this HDD has all my logins in it so if i can boot it up i fix everything hopefully so i asked one of my long time linux using friends whos pretty good with computers yk better than me atleast and he told me GRUB prolly messed up and i should reinstall it so i look up a few tutorials and none of them work for me because i get error messages ALWAYS. i used 2 tutorials mainly the first one was the archwiki article for grub installations on uefi the other was some old youtube video but the arckwiki article said to do this cmd 
grub-install --target=x86_64-efi --efi-directory=*esp* --bootloader-id=GRUB

so i ran it but i either get "could find canonical path for /udev" or "could find canonical path for /cow"
depending what i put for esp in the cmd.
which im prolly gonna look rly stupid here but arent you supposed to do "mount (the hdd you wanna put grub on) /mnt/boot?"
and then id either but /dev/sdc1 for esp or /boot 
(is that right??) i just rly need help with this i spent 6 hours yesterday tryna figure this out

and on the ytb tutorial i found i had no problems until i had to do chroot and then chroot couldnt find /bin/bash and idk how to direct chroot to it PLEASE HELP.

---

