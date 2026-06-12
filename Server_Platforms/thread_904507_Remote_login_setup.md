---
title: "Remote login setup"
date: 2008-08-29
forum: Server Platforms
---

### Post by Yaspoon on 2008-08-29
Im messing round with a ubuntu server setup and was wondering how to setup a remote login like in a windows system there is the server and the desktop the windows desktop logs in via information on the server like you see at work normally :) is there anyway to do this in linux? pointers towards guides would be sweet 
thanks

---

### Post by cdenley on 2008-08-29
Well, if you want remote login on a server
```

sudo apt-get install openssh-server

```

If you want remote login for a desktop
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by timcredible on 2008-08-29
you can remotely access your normal login with the already-installed xdm protocol.  it's similar to windows' remote desktop.  click on the link in my signature and click on the remote login with xdm link on my website for a complete how-to.

---

### Post by Yaspoon on 2008-08-30
Thanks for the help much appreciated :)

---

### Post by CaptSaltyJack on 2008-08-30
I have to vote against VNC and XDM for remote access.

[http://ubuntuforums.org/showthread.php?t=905200](http://ubuntuforums.org/showthread.php?t=905200)

---

### Post by mellowd on 2008-08-30
For server I'd stick solely with ssh

---

### Post by CaptSaltyJack on 2008-08-30
Yes, what mellowd said.  ssh is preferred, but if you need remote access to the window manager (Gnome, KDE, what have you), can't go wrong with NX (especially since it operates over SSH and is way faster than VNC).

---

### Post by windependence on 2008-08-31
> **CaptSaltyJack said:**
> I have to vote against VNC and XDM for remote access.

[http://ubuntuforums.org/showthread.php?t=905200](http://ubuntuforums.org/showthread.php?t=905200)

I have to agree here especially if security is a concern.

I haven't checked out NX but it sounds ineteresting for accessing my desktops. I don't use GUI on my servers.

Thanks Capt.

-Tim

---

