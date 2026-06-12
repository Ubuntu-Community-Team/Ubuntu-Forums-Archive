---
title: "get lucid login info into a hardy server"
date: 2010-06-05
forum: Server Platforms
---

### Post by inphektion on 2010-06-05
I have a new lucid server.  When I login to it via ssh it shows:
```

Linux syn 2.6.32-22-server #36-Ubuntu SMP Thu Jun 3 20:38:33 UTC 2010 x86_64 GNU/Linux
Ubuntu 10.04 LTS

Welcome to the Ubuntu Server!
 * Documentation:  http://www.ubuntu.com/server/doc

  System information as of Sat Jun  5 09:57:55 EDT 2010

  System load: 0.0               Memory usage: 14%   Processes:       81
  Usage of /:  3.8% of 56.37GB   Swap usage:   0%    Users logged in: 0

  Graph this data and manage this system at https://landscape.canonical.com/

Last login: Sat Jun  5 09:47:30 2010 from 10.9.8.98

```

How do i get this type of info into a hardy server?  I find it useful esp the part where it will tell me if a system restart is required.  

I checked .bashrc and various profile files and ssh config files.... I don't see it anywhere...

---

### Post by inphektion on 2010-06-05
ok i see it is written to /etc/motd.  but that is static.  so some other script is writting its output there....
searching...

---

### Post by benderisgreat on 2010-06-05
```
sudo apt-get install landscape-common
```

---

### Post by inphektion on 2010-06-05
thanks.  found this too [http://ubuntuforums.org/showthread.php?t=1470011](http://ubuntuforums.org/showthread.php?t=1470011)

has all the rest of the info I need as i want to remove some of the info it shows.

---

