---
title: "Uninstal ubuntu-desktop from server"
date: 2007-07-10
forum: Server Platforms
---

### Post by mfdc1969 on 2007-07-10
Howdy,

Being a newb I found it easier to deal with my "server" install of Edgy by adding the ubuntu-desktop ... so now, the silly question of the day is:

When I uninstall ubuntu-desktop will it have any negative affects on my server - other than me being forced to use the command line? 

I'm most concerned about any issues with Samba as I have set up a file share for my wife to manage shared photos etc... 

Any issues that you can warn me about before I hit the enter key would be greatly appreciated!!

Thanks,
Michael

---

### Post by HermanAB on 2007-07-10
The Linux scheduler and memory manager are very good.  Programs that are not used do not consume resources.  Therefore, it doesn't matter that you have installed a desktop system on your server.  If something needs the RAM and your desktop schtuff is not used, then it will be swapped out.

If you really wish to free up every last byte of RAM forcefully, then simply run the server in level 3 (without X):
# sudo init 3

Though again, as I said, it doesn't really matter, it is just a hold over from the bad old days (and some security paranoia) to not install unneeded stuff on a server.  If I were you, just keep doing what you are doing.

---

### Post by mfdc1969 on 2007-07-10
Thanks for the reply - without X sounds simple enough. A concern I had is that the machine only has 512 MB RAM and a video card with 64 MB ... I thought without X might free up resources for other processes.

So, I opened a terminal typed # sudo init 3 and then restarted ... the same ol' Gnome popped up again ... did I miss something? 

Please forgive my ignorance ... :-)

Michael

---

