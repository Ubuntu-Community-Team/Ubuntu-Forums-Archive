---
title: "x11 forwarding not working in 9.10 Server"
date: 2010-01-06
forum: Server Platforms
---

### Post by firemandan9 on 2010-01-06
Pre-exsisting issue from 9.04 server, and has never worked right for me. When I try to open an X11 forwarded app on a mac using the command "ssh -X myusername@serverIP" Other linux machines have similar issues from terminal. I can login just fine and preform any actions I want that do not require X11 forwarding, like say firefox or a manager. I just get the error "Error: no display specified" when trying to do anything with X11 forwarding. I have almost no Linux experience but from tinkering and my friends tinkering wonder if I have a x authority issue. At one point I had ubuntu desktop package installed (forwarding still did not work then), did a unclean uninstall of it installed Xubuntu. Xubuntu did nothing but throw fits saying I did not have authority to preform all sorts of actions, many relating to root access. This box is meant to be a headless file, print and web server with the ability to login remotely as a convince for administration. I have given up on having a working GUI of any kind on this box. I really do not want to reinstall because of the amount of data on the main partition. What can I start trying to look into?

Thanks

---

### Post by kiranmurari on 2010-01-07
Hi,
Can you please take a look at the following thread.

[http://ubuntuforums.org/showthread.php?t=1373164](http://ubuntuforums.org/showthread.php?t=1373164)

Let me know if this helps you.

Regards,
Kiran

---

