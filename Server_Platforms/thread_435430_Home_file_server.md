---
title: "Home file server"
date: 2007-05-06
forum: Server Platforms
---

### Post by CreativeName5 on 2007-05-06
I recently aquired an old HP computer that I would like to use as a file server for my home. I have seen many tutorials that show me how to do this with SSH and samba or FTP but none of them have successfully worked for me.

So basically, my question is, does anyone know of some sort of tutorial that will allow me to set this computer up as a home file server that i can access from Mac OS X, Windows, and my other Ubuntu box?

Thanks in advance,
Sean

I hope this is in the right catagory, if not, please tell me....

---

### Post by dmizer on 2007-05-06
to set up your server, use the tutorial in the first link in my sig.
to connect to your server from ubuntu, use the second link in my sig.

to use the mac, you will need one of two things:
1) a windows computer must be on while accessing the share with your mac.
or
2) you will need to configure your network with static ip and make the linux server also act as a wins server.

either way, you will need to do some editing of /etc/smb.conf on your mac is configured correctly for the windows workgroup like so:
> Make sure that the following are included in your Mac's /etc/smb.conf [global] section:

encrypt passwords = yes
os level = 8
workgroup = your_workgroup_name #insert the workgroup name you choose earlier
wins server = xxx.xxx.xxx.xxx #insert IP address of windows box or linux box (if your linux box is configured as your wins server) here
above taken from this thread: [here](http://www.macworld.com/forums/ubbthreads/showflat.php?Cat=&Board=UBB12&Number=351250&page=0&view=collapsed&sb=5&o=&fpart=1) [macworld.com]

if you have any questions or problems ... please post.

---

### Post by CreativeName5 on 2007-05-07
Ok so before i go and cahnge all my computers to have static ip adresses, i have a question, see my mac recognizes my windows network and i am able to log onto other windows boxes without mine being on so basically my question is, since my mac recognizes my windows network do i *have* to do this?

Thanks,
Sean

---

### Post by dmizer on 2007-05-07
it would seem so.  i don't have a mac for direct testing this situation so i can't verify directly.  but i did run through the trouble of trying to configure a friends local file sharing network with a windows, mac, and ubuntu box where the ubuntu box was the file server.  the mac could not see the ubuntu box as a result of wins.

alternative to static ip, most routers are capable of assigning an ip based on mac addressing.  this will allow you to have your machines remain configured for dhcp, while allowing your local network configuration to have a reliable addressing structure.

---

