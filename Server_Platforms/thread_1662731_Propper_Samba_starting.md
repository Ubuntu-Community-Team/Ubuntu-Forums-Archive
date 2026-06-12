---
title: "Propper Samba starting"
date: 2011-01-08
forum: Server Platforms
---

### Post by p2ranger on 2011-01-08
After upgrading from 9.04 to 10.04, I've discovered the Upstart issue with getting Samba shares to work right. I can get my Samba share to show up if I do the following commands after rebooting my server:

```
sudo service nmbd start
sudo service smbd restart

```

I've been looking around to find out how to fix this and I've seen lots of posts and what not about getting it to work, but I haven't been able to find a way to get this to work on its own so I don't have to issue the commands.  I'm sure someone has found a solution to this and I am hoping they could please share it with me.

Thanks

Jason

---

### Post by rgulia on 2011-01-08
Do you have a start/stop script configured for smbd and nmbd? 

ls /etc/rc*.d/*mbd* should provide a list of them. Check in which order  they come up for the run level which applies to your system. 

 More info on 

man update-rc.d

---

### Post by p2ranger on 2011-01-09
I doubt that I have a script. I don't know how to write a script. When I entered that ls command I got

```

ls: cannot access /etc/rc*.d/*mbd*: No such file or directory
```

Jason

---

