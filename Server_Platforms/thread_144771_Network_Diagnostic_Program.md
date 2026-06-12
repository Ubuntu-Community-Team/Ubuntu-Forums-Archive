---
title: "Network Diagnostic Program"
date: 2006-03-15
forum: Server Platforms
---

### Post by Tux_Phoenix on 2006-03-15
Ok I need some help I have my server up and running and everything seem sot be good but when I type in my static IP I get a time out error usaly but some times an access denyied error.  I am looking for some sort of network Diagnostic program to help me see where my inbound packets are ending up, and also to see if my router/modem are sending packets out properly.  Not sure what to search for here so a point in the right direction would be great.  Thanks

---

### Post by Koybe on 2006-03-15
You can use simple commands such as ping and traceroute for a beginning. In most of the case it's sufficient to determine where is your packet lost and what to do. Go step by step :
- ping your router's ip
- ping an internal name
- ping an external ip
- ping an external name
- traceroute your router (should be short)
- traceroute an external ip

Old tools are still usefull ;)

---

### Post by Tux_Phoenix on 2006-03-15
I have tryed all of those and I get the normal readings.  That or I just do know what I am reading.  From the looks of it I have everything set up right but it doesn't work.  So I need some where to start and I have no idea where that might be.

---

### Post by Glut on 2006-03-15
ethereal is a good way to go. It's quite powerful and 'understands' a good many protocols.

---

### Post by spectre_25gt on 2006-03-16
It would be helpful to know what your end goal is. At the moment, it sounds to me like you have a port forwarding issue, but I really don't have enough to go on.

---

