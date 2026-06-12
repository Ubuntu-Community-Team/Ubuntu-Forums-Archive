---
title: "VNC Server Howto ???"
date: 2006-06-23
forum: Server Platforms
---

### Post by JKoder on 2006-06-23
Hello!
I know that there are some post wit this title but those does not helped me at all.
So what i need is to setup a VNC server on Ubuntu 6. I managet to setup my VNC server, i can connect to it but i get a annoying gray screen with a cross for mouse, the X server with no desktop manager.
Can anyone help me on this ?
Thank you !

---

### Post by x64Jimbo on 2006-06-23
You're running into a very common problem with VNC and it's pretty hard to get around with the standard VNC server package. However, there is a solution that makes the Linux version of VNC server behave just like the Windows version. It's called x11vnc. Check it out here:
[http://www.karlrunge.com/x11vnc/](http://www.karlrunge.com/x11vnc/)
There's a lot of information there about configuring it for startup too.

---

### Post by JKoder on 2006-06-23
[QUOTE=x64Jimbo]You're running into a very common problem with VNC and it's pretty hard to get around with the standard VNC server package. However, there is a solution that makes the Linux version of VNC server behave just like the Windows version. It's called x11vnc. Check it out here:
[http://www.karlrunge.com/x11vnc/](http://www.karlrunge.com/x11vnc/)
There's a lot of information there about configuring it for startup too.[/QUOTE]
Thank you !!! i will try it !!!!!!

---

### Post by hagen00 on 2006-06-23
I also had a problem with a grey screen...

Check out this HowTo I made...[http://ubuntuforums.org/showthread.php?t=151703]("http://ubuntuforums.org/showthread.php?t=151703")

---

