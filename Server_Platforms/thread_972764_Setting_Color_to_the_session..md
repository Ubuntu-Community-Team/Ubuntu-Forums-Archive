---
title: "Setting Color to the session."
date: 2008-11-06
forum: Server Platforms
---

### Post by satyendra on 2008-11-06
Hello,

I have about 1000 AIX boxes to be maintained and I want to set the terminal color schemes when I login thru PUTTY or SECURE SHELL LOGIN utilities to differentiate between Production and Pre-Production Servers.

I know I can do it for individual sessions in PUTTY but there are about 100 more users who will be using these servers and  I am not keen on asking users to change the settings.

Can anyone help me out and let me know that is it possible to change the colors on AIX box itself to use the colors other than traditional black and white. 

I tried googling but got confused and tried couple of solution and it dint work.

Thanks in advance for the help Guys.

-- Satyendra

---

### Post by FakeOutdoorsman on 2008-11-06
This is a good start:
[Color Bash Prompt]("http://wiki.archlinux.org/index.php/Color_Bash_Prompt") [Arch Linux Wiki]

I think there is a way to apply this system-wide, but I'm not sure which file it is.  Unfortunately, this would require you to add this to all remote machines.  I suppose you would need to be using bash as your shell as well.  I'm not really sure.

---

