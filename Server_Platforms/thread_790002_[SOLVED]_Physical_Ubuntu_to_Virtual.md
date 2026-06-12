---
title: "[SOLVED] Physical Ubuntu to Virtual"
date: 2008-05-11
forum: Server Platforms
---

### Post by cikic on 2008-05-11
Hello

I have two small Ubuntu (7.10) server machines both running on old hardware. Now I have bought a "BigThing" and I would like to migrate the physical Ubuntu Servers to Virtual Servers. The virtualisation solution is not important to me. If I could do this with VBox I will use VBox otherweise I will use VM-Ware or whatever.

Question is: How to convert a physical Ubuntu to a Virtual one?

Thanks
Chris

---

### Post by windependence on 2008-05-11
With Vmware you could use VMware converter.

-Tim

---

### Post by cikic on 2008-05-11
Sorry, VMWare Converter converts only windows machines. Any other Ideas?

---

### Post by windependence on 2008-05-11
Create the VM on your box and then dd or rsync the other machine to the new VM.

-Tim

---

### Post by cikic on 2008-05-12
I have allready tired this. But it is not working (not out of the box) due to hardware differences and other problems copying directories like /proc.

Finally I have found a tutorial - maybe sometimes somebody will script this:

[http://tinyurl.com/yr39om](http://tinyurl.com/yr39om)

Chris

---

