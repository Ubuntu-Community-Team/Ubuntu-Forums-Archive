---
title: "Avast Antivirus GUI."
date: 2012-02-13
forum: Security
---

### Post by ayenack on 2012-02-13
Hello all

I installed Avast Antivirus Home Edition on my friends openbox laptop so he can scan NAS mounts easily (he shares files with Windows comps).

What I'm wondering is does anyone know how to start the Avast Home Edition GUI from the command line?

Reason I ask is that I can then add Avast to his openbox menu so he can use it easily rather than having to use the command line.

Thanks for any help.

ayenack.

---

### Post by winh8r on 2012-02-13
Try using

```
avastgui
```

think that might work

---

### Post by ayenack on 2012-02-13
100% correct. LOL.

Thanks for that.

---

### Post by ayenack on 2012-02-13
I got an avast engine error after updating avast.

To fix it I did this.

Open terminal then:-

```
Sudo su
```

And then this:-

```
ysctl -w kernel.shmmax=128000000
```

I've also added this to /etc/init.d/rcS so it should be set at boot. I'll report back on  if it does or not.

---

### Post by oklokl on 2012-02-14
[http://www.howtogeek.com/howto/14434/scan-a-windows-pc-for-viruses-from-a-ubuntu-live-cd/](http://www.howtogeek.com/howto/14434/scan-a-windows-pc-for-viruses-from-a-ubuntu-live-cd/)

[http://www.avast.com/linux-home-edition](http://www.avast.com/linux-home-edition).
 
sudo dpkg -i *deb

sudo apt-get install ia32-libs  
 sudo echo "kernel.shmmax=128000000" >> /etc/sysctl.conf

##  [http://forum.avast.com/index.php?topic=53107.0](http://forum.avast.com/index.php?topic=53107.0)


[http://dcthirteen.blogspot.com/2011_10_01_archive.html](http://dcthirteen.blogspot.com/2011_10_01_archive.html)

---

