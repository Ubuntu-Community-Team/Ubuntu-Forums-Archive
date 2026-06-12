---
title: "Multiple Desktop Environments"
date: 2018-08-17
forum: Ubuntu, Linux and OS Chat
---

### Post by krishnan t s on 2018-08-17
I'm posting this under Ubuntu, Linux and OS chats because i dont know under which category this falls. Please feel free to move the post to the appropriate category.

I'm presently using ubuntu 18.04(with unity desktop, because.. well... i'm not a fan of the gnome 3 desktop) alongside elementary os Juno Beta in a dual boot setup. I want to erase and merge the partition with elementary os and use ubuntu with unity as my primary driver. I can do that on my own. I also want to install elementary os Juno using the instructions provided in  [https://medium.com/@alex285/how-to-try-elementary-os-5-0-juno-on-ubuntu-18-04-4539eb346f6f](https://medium.com/@alex285/how-to-try-elementary-os-5-0-juno-on-ubuntu-18-04-4539eb346f6f)

My past experience with the above setup was a rocky one. Elementary desktop used to replace unity's window buttons with its own and also change the font type to the one used by the pantheon desktop. I want to know if there is anyway i can install Juno alongwith my existing Unity Desktop without borking the latter. Has anyone tried this setup? Any tips on how to do this? Thanks in advance for your replies

---

### Post by ajgreeny on 2018-08-17
I you were using the same /home for both OSs I am not surprised that you had some problems as the config for the desktop and many applications is included in your home files and folders.

If you want to use the same data in both OSs, and I can see the sense in wanting that, it is much less problematical to keep the home folder for each within root and either have a separate /data partition accessed by both OSs or use soft links to the data folders (Documents, Downloads, Music, etc etc) from the main OS to the second.

---

### Post by krishnan t s on 2018-08-17
I want to avoid dual booting. I want to retain the ubuntu install and erase elementary os. But, if i install elemenaty os through a PPA, it will bork my system as elemtary will replace most things in ubuntu, alongwith changing the font. I just wanted to know if there is any way to "unbork" the setup without uninstalling elementar os.. or rather how do i reset unity to default without removing elementary desktop.

---

### Post by oldos2er on 2018-08-18
If having a separate /home isn't an option, the next best thing would be to create a different user account for Elementary.

---

