---
title: "Xnest, GDM, X, SSH, remote login"
date: 2009-07-11
forum: Server Platforms
---

### Post by Cocoabean on 2009-07-11
I've been searching all over. I have Jaunty Jackalope server with X and GDM installed. I used chkconfig to disable x11-common and gdm at startup. What I want to do is be able to SSH to the machine and forward X, but I want to get a GDM login without leaving GDM running all the time (if someone logs onto the console they must do a startx type setup). I've been messing around with Xnest but X always confuses me. gdmXnest looks promising but I am not sure if it is what I want:
-SSH to machine.
-Run command.
-Get GDM.
-Have GDM shutdown when I close the session.

Thanks.

---

### Post by wojox on 2009-07-11
Ok 

ssh to machine

```
sudo /etc/init.d/gdm start
```

Then when you leave

```
sudo /etc/init.d/gdm stop
```

---

