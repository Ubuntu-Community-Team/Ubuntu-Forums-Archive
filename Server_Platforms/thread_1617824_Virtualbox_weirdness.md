---
title: "Virtualbox weirdness"
date: 2010-11-09
forum: Server Platforms
---

### Post by maino82 on 2010-11-09
I wasn't sure where to post this, so I appologize up front if it's in the wrong spot. I also wasn't even sure if this was an Ubuntu issue, so if it belongs on another message board, I will gladly hang my head in shame and head off into the sunset.

I have an Ubuntu host (10.04) running an Ubuntu virtual machine (also 10.04, but the server addition) under Virtualbox (3.2.8). I use VNC (vino-server) to get access to the host sometimes to tweak stuff in the virtual machine, but I also have SSH set up directly into the virtual machine. When I use VNC (real vnc from a Windows box) to try and control the VM directly and try to type something into it I get a bracket "[" in front of everything that I type, including backspace or delete. When I try and type in the host, I get none of these shenanigans. When I pull out a keyboard and mouse and hook it up to the host, and type inside the guest that way I get no brackets. Also, when I SSH into the guest I get no brackets. By process of elimination I have to think it's something with VNC.

Here's the kicker, though. When I VNC into the host to set up a new virtual machine and boot it up into a LiveCD or directly into an install environment (like with the server install), none of the brackets come up when I type! It's only after the install when I boot into the new VM that the problem occurs. I didn't believe it myself, so I've installed two more VMs over the VNC connection just to confirm that it's the case.

Ideas, thoughts and conspiracy theories are welcome. Any help anyone could offer would be greatly appreciated, even if it's just to direct me to another message board that might be better suited to this question.

---

### Post by wilee-nilee on 2010-11-09
I will go conspiracy I think its the mother ship controlling the VNC.;)

---

### Post by maino82 on 2010-11-10
> **wilee-nilee said:**
> I will go conspiracy I think its the mother ship controlling the VNC.;)

Haha, at this point I'd have to tend to agree.

---

