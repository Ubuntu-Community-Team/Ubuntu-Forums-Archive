---
title: "Changing computer name?"
date: 2009-01-12
forum: System76 Support
---

### Post by BlazinNightSkye on 2009-01-12
When i got my laptop it didnt give me the option of setting a computer name, I dont want it to stay as 'Ubuntu', is there a way i can change it?

---

### Post by Lee_Machine on 2009-01-12
Install network admin GUI. Why the hell its not by default I dont know....keep users away?

sudo apt-get install gnome-network-admin

Then go to System >> Admin >> Network

Click on the general tab to change the name


hope this helps.

---

### Post by Lee_Machine on 2009-01-12
Anyone know why this was taken away in Ibex as to it was in Hardy?

The only other way I know of is to change your hostname config file in etc/hostname. It's not hard but users shouldn't have to do that.

I'll have to do some reading to see if this will be fixed in Jaunty.

---

### Post by BlazinNightSkye on 2009-01-12
WIll that program work under kubuntu?

---

### Post by Lee_Machine on 2009-01-12
ah, my mistake. Kubuntu.

go to KMenu >> System Settings >> Network Settings

then click on hostname

---

### Post by BlazinNightSkye on 2009-01-13
It doesnt give me an option to change the host name.

---

### Post by Lee_Machine on 2009-01-13
ok, I'll try and find the GUI way for you. Until then type

sudo kate /etc/hostname a text box will show up with just one name and that will be your computer name, change it to what you what you want an' then save.

Reboot and the changes will take effect.

---

### Post by Lee_Machine on 2009-01-14
I apologize BlazinNightSkye none of my Linux computers have KDE on them any more. So i cannot simply change DEs to test this out, but here is a good how to networking page I found.

[http://kudos.berlios.de/kf/kisimlar/network.html](http://kudos.berlios.de/kf/kisimlar/network.html)

This is a feature that was taken out of 8.10 to prevent normal end users from changing it. From what I read it will be put back in the next version.

for now just use the above CL way to do it. 

Yeah, the dreaded CL :lolflag:

---

### Post by BlazinNightSkye on 2009-01-15
Thanks

---

### Post by cmnorton on 2009-01-15
> **Lee_Machine said:**
> Install network admin GUI. Why the hell its not by default I dont know....keep users away?

sudo apt-get install gnome-network-admin

Then go to System >> Admin >> Network

Click on the general tab to change the name


hope this helps.

Thank you. This answer was helpful. 

I too received a new computer -- today as a matter of fact -- and network admin was not installed. I tried changing the network name in /etc/hosts, which caused cannot find "ubuntu" errors to take place when I entered sudo commands.

Once I changed in the Network Admin, all was well.

---

