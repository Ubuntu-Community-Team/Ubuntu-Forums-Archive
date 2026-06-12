---
title: "Setting up my server"
date: 2006-09-04
forum: Server Platforms
---

### Post by CameronCalver on 2006-09-04
Hello i have an old computer which i would like to set up for proxy server using squid file server using samba and ssh and i installed server ubuntu but i am unsure of how to do things
I no how to set up all of these in gui but in cli i have not got a clue how to i get into a file editing program like gedit and i want to buy a wireless 802.11b card for it and i would like to be able to set it up.
So can someone tell me how to edit config files in cli only or should i install gnome-desktop then uninstall it when everything is upand running.
Also i need a wireless card pci or usb i dont care i just need it fairly fast more thrn 60mps because i am using this for a file server which one do you recomend

---

### Post by Titus A Duxass on 2006-09-04
use an editor like pico, nano or Vim.
Simply sudo pico file.name and off you go.

I would do the old desktop install/remove trick myself.

---

### Post by bunnynuts on 2006-09-05
I'm partial to vi myself. [Here]("http://www.eng.hawaii.edu/Tutor/vi.html") is a quick tutorial on the editor. To use it as an editor you must assume root priveleges first thus using the following command: ```
sudo vi /home/bunnynuts/*filename*
``` or make yourself root...but be careful, you can jack stuff up if you're not careful!

---

