---
title: "Can't see Linux box"
date: 2006-04-26
forum: Server Platforms
---

### Post by Coruba67 on 2006-04-26
Hi guys,

Ok, am having some trouble seeing my Linux box from my windows one.  I have installed samba on the Ubuntu box, created the folder /Shares and shared it.... setup a samba username and password...  also started the smb service.

the IP of this linux box is 192.168.0.100

From windows when I go into windows explorer and type \\192.168.0.100 I get nothing...  It just can't even see the linux box... any idea's why?

cheers in advance.

---

### Post by alamba on 2006-04-26
Can you ping your .100 machine? Do you have a firewall running? Can you run 'nmap localhost' and check if the ports are being listened on?

A

---

### Post by Coruba67 on 2006-04-26
ok... yes can ping the box.  hmmmmm... I am an idiot don't mind me... thanks for that didn't open the port up on the firewall....

Thanks heaps for your help!!  :)

---

### Post by alamba on 2006-04-26
You're welcome....cheers!

A

---

