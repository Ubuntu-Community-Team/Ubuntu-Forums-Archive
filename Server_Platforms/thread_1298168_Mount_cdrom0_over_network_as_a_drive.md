---
title: "Mount cdrom0 over network as a drive"
date: 2009-10-22
forum: Server Platforms
---

### Post by Viper1987 on 2009-10-22
i'll try to make this as short as possible so i don't make you read for 8 days about what i did... my final goal is to use my ps3 bd drive to decrypt, rip, and convert to mp4 (for streaming to ps3 xmb) with minimal quality loss... space is not an issue, as i have TONS of HDD space

(i'm somewhat of an experienced linux user as i have been using it as my main OS for ~3 years)

here's what i have done/tried thus far:

1. i tried using the "dd" command to rip the blu ray disk to an external hdd, taking the hdd to my ubuntu laptop and using "makemkv"... this didn't work because the blu-ray had to be decrypted first...

2. finding an easy way to decrypt a blu ray is damn near impossible on linux, as i have googled so many times i can't type anymore "o"s.... i tried using virtualbox and hesitantly installing xp (i HATE windows and their corporate greed... i'd also like to mention i got a virus after about two seconds of surfing the web)... virtualbox wasn't a good option because if i'm ripping bddvds, i want the maximum amount of resources possible, so i set it up to dual boot (even partitioning didn't go right for me at first!!!) and most of the programs didn't work in Wine

3. after finally getting a working xp and an iso on the external hdd with the "dd" command, i took it to the xp and tried using anydvdhd... i, then had to find a way to either a)mount the iso to the xp (which anydvd didn't like and wouldn't work) or b)mount the cdrom drive over the network (if possible)???? either /media/cdrom0 or /dev/scd0 (it won't let me share scd0 using samba and with cdrom0, it lets me see the files, but not as a cdrom drive)

ANY HELP?!?!?!? i've wasted the entirity of my two off days trying to solve this!!!! i've looked at every forum and guide on google!!! how is this done?!?!!?!

ps3 has xubuntu 9.10, laptop has ubuntu 9.04, media server has ubuntu 9.04

---

### Post by Viper1987 on 2009-10-22
NOTE: makemkv didn't work on xubuntu ppc

---

### Post by Viper1987 on 2009-10-27
if this is not possible, just let me know... ANYBODY?!

---

