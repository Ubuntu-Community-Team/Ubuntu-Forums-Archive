---
title: "Windows client to see vnc?"
date: 2009-05-19
forum: Server Platforms
---

### Post by Vegan on 2009-05-19
Right now I manage my server with a VT102 compatible terminal program, no problem.

I am aware of vnc to provide x-windows remote access. What terminal would I need to use it.

My current terminal client supports: VT100, VT102, VT282, VT320 & VT382.

---

### Post by justatemptest on 2009-05-19
[http://www.lmgtfy.com/?q=free+vnc+client+for+windows](http://www.lmgtfy.com/?q=free+vnc+client+for+windows)
[http://www.lmgtfy.com/?q=how+to+setup+vnc+server+ubuntu](http://www.lmgtfy.com/?q=how+to+setup+vnc+server+ubuntu)

---

### Post by windependence on 2009-05-19
You really shouldn't use VNC IMHO. Use ssh and forward your X applications OR use FreeNX or something else that encrypts your connection unless you are only using the machines on a LAN. Even then, I am not impressed with how often VNC gets hacked. You don't need any terminal emulation for GUI access. Terminal emulation is just that - emulating a terminal. It has nothing to do with remote access to a GUI. You best option is to bear down and learn your CLI.

-Tim

---

### Post by smeerbartje on 2009-05-19
> **windependence said:**
> You really shouldn't use VNC IMHO. Use ssh and forward your X applications OR use FreeNX or something else that encrypts your connection unless you are only using the machines on a LAN. Even then, I am not impressed with how often VNC gets hacked. You don't need any terminal emulation for GUI access. Terminal emulation is just that - emulating a terminal. It has nothing to do with remote access to a GUI. You best option is to bear down and learn your CLI.

-Tim

Hi, can you please provide a short explanation how to forward X applications? Now I'm using FreeNX, but I would like to understand the other solutions as well.

---

### Post by Vegan on 2009-05-19
I am competent with the bash CLI, its simply convenient to load a GUI for some tasks.

---

### Post by windependence on 2009-05-20
> **smeerbartje said:**
> Hi, can you please provide a short explanation how to forward X applications? Now I'm using FreeNX, but I would like to understand the other solutions as well.

It's pretty simple really:

```
ssh -X /path/to/application
```

You must have an X server running on your client machine though. There are some X servers for Windoze, and MacOS has one already built in as well as Linux if you installed X.

-Tim

---

