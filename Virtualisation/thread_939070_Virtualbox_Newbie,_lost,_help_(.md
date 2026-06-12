---
title: "Virtualbox Newbie, lost, help :("
date: 2008-10-05
forum: Virtualisation
---

### Post by Tex786 on 2008-10-05
So, I have installed Ubuntu as a guest, but it's a very small screen. The solution is guest additions, but I can't install it!
Terminalwindow says: No administrator privileges to run this. Aborted

Can someone explain in detail what I need to do to get this solved?

Thanks

---

### Post by Meow27 on 2008-10-05
ok when you click the button(install guest additions), guest additions should appear to be a cd rom[on the desktop]. so open it, then copy LINUX binary with the respective architecture (32 bit or 64 bit OS) to the Desktop (VBoxLinuxAdditions-x86.run or VBoxLinuxAdditions-amd64.run)

then open up the terminal and type
```
cd Desktop
sudo sh VBoxLinuxAdditions-x86.run (or VBoxLinuxAdditions-amd64.run depending on OS architecture)
```

i would copy the 32 bit folder to the desktop just in case :P

this has worked for me 3 times already. so i expect the same should happen with you

have fun :)

---

