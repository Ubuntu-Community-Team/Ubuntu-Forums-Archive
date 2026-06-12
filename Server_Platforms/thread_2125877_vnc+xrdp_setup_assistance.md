---
title: "vnc+xrdp setup assistance"
date: 2013-03-15
forum: Server Platforms
---

### Post by MakOwner on 2013-03-15
I had this setup once before - it's a little slow, but for the little amount of time that it's used it worked just fine for us - and it's better than using a closed source package.

I set this up and as I recall it really painless, but I didn't write anything down of course and the VM where it was setup got wiped.

Googling results in a lot of "just install and the connect" , but that isn't working.

I did an apt-get install for xdrdp and that included vino and vnc4 packages and I see the xrdp service is enabled at startup.

What am I missing?


This is on LinuxMint Maya - the MATE desktop.

```

 # dpkg -l | grep vnc
ii  libvncserver0                          0.9.8.2-2ubuntu1                        API to write one's own vnc server
ii  vnc4server                             4.1.1+xorg4.3.0-37ubuntu4               Virtual network computing server software
 # dpkg -l | grep vino
ii  vino                                   3.4.2-0ubuntu1.2                        VNC server for GNOME
 # dpkg -l | grep xrdp
ii  xrdp                                   0.5.0-2                                 Remote Desktop Protocol (RDP) server


```

---

### Post by steeldriver on 2013-03-15
so... what exactly isn't working? what error(s) do you get / what behavior do you see when you try to connect?

---

### Post by MakOwner on 2013-03-15
I'm using a windows 7 RDP client, and I just get a generic "can't connect" message as if the service isn't available.
I rebooted it after the install just to make sure, looks like the xrdp service is tagged to start on boot up and no firewalls between the boxes.

---

