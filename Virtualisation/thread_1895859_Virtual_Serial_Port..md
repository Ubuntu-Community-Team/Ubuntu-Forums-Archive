---
title: "Virtual Serial Port."
date: 2011-12-15
forum: Virtualisation
---

### Post by alan2796 on 2011-12-15
I apologize if this is in the wrong forum but i was unsure of where to post this.

I am trying to write an application in C# in Ubuntu using the .NET Framework. and mono.

it's a serial communication application and I was writing a client/ server design for testing to emulate responses from the controller. 

so using this code I created a virtual Serial Port.

**sudo socat PTY,link=/dev/ttyS3 PTY,link=/dev/ttyS4**

The problem is .NET dosen't recognise /dev/ttyS3 as a valid COM 

first i get a permission denied error, then if i chmod the tty file i get a invalid argument error... 

anyone got any ideas ?

---

