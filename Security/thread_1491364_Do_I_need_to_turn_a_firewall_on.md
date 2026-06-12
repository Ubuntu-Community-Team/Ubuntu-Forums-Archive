---
title: "Do I need to turn a firewall on?"
date: 2010-05-23
forum: Security
---

### Post by FinalShot on 2010-05-23
Will I need to actiavte the firewall that comes with Ubuntu since I'm using Transmission?

---

### Post by wojox on 2010-05-23
Do you have a router? Then no. Just port forward the port that Transmission will be using.

---

### Post by FinalShot on 2010-05-23
Weird, I just cleared all my forwarded ports in my router, turned of dmz, and Transmision is still connecting fine...

---

### Post by wojox on 2010-05-23
> **FinalShot said:**
> Weird, I just cleared all my forwarded ports in my router, turned of dmz, and Transmision is still connecting fine...

It's using UPnP. Which is easier but less secure than manual forwarding.

---

### Post by FinalShot on 2010-05-23
> **wojox said:**
> It's using UPnP. Which is easier but less secure than manual forwarding.
Oh yeah, I have a Xbox 360, I think the best would be to manually forward ports for my pc, and turn on dmz for the xbox. Or is there a better solution?

---

### Post by wojox on 2010-05-23
> **FinalShot said:**
> Oh yeah, I have a Xbox 360, I think the best would be to manually forward ports for my pc, and turn on dmz for the xbox. Or is there a better solution?

I would manually forward the ports to the PC. Go to the Network tab in Transmission and select your port you want to use and untick Use UPnP or NAT-PMP.

Remember to log back into your router and configure Port Forwarding.

---

### Post by jerome1232 on 2010-05-23
If it's a concern to you you should probably turn off UPnP in the router too.

---

### Post by FinalShot on 2010-05-23
I turned UPnP off in my router, manually forwarded my ports. I honestly can't remember why I turned UPnP on for the 360.

---

### Post by The Cog on 2010-05-24
I turned UPnP on long enough to find out which ports the xbox wanted forwarding, then turned it off again and forwarded that port manually. It seems the only port it needs is UDP port 3074.

---

### Post by FinalShot on 2010-05-25
Thanks I'll add that.

---

