---
title: "having trouble connecting remotely using vmware"
date: 2008-11-27
forum: Virtualisation
---

### Post by buster65 on 2008-11-27
I am having trouble connecting remotely to a virtual machine. I have 8.10 installed on a desktop with vmware server 2.0 running and after typing [Https://192.168.1.100:8333](Https://192.168.1.100:8333) from a remote computer it seems to connect but does not give the login screen. it works fine from the desktop but not remotely. does anyone have any ideas?
Thanks in advance
Buster

---

### Post by bodhi.zazen on 2008-11-27
IMO server 2.0 is a bit quirky, to say the least.

1. Firwall ?

2. Are you trying to connect over the internet ? If so did you forward all the ports ?

3. Do you have java installed on the client ? Are you blocking java (NoScript) ?

4. Try port 8333 ([https://ip_address:8333](https://ip_address:8333)).  

5. If all else fails, reload the web page (sometimes the first few attempts fail).

6. Re-start vmware.

---

### Post by buster65 on 2008-11-27
I am connecting over home network through a router. i did manage to get to the login screen and then to the admin screen but i come up with "server not responding i think it has something to do with the desktop as i cannot get some websites to come up on it but i can with my laptop. if there is a firewall it would be set to whatever default is under ubuntu 8.10. i have tried rebooting both machines and logging in from another and i get the same thing. I am fairly new to linux and i am trying to get away from windows but the are a few things i have to do under windows for the time being that is why i am trying to get this to work.
thanks for the response
buster

---

### Post by bodhi.zazen on 2008-11-27
I understand. The web interface seems to be the "Weak link" in Server 2.0 (to me it seems slow and at times unreliable). You might consider 1.0.8 (you can get a web interface with that version as well) or possibly Virtualbox (Virtualbox is also freely available, although I do not think there is a web interface),

HTH,.

---

### Post by buster65 on 2008-11-28
I have tried virtual box and I like it but I could find any usb support. does it support usb and if so how can i get it to work.

---

### Post by bodhi.zazen on 2008-11-28
> **buster65 said:**
> I have tried virtual box and I like it but I could find any usb support. does it support usb and if so how can i get it to work.

Yes it does, and it works quite well.

You need to make a single edit to /etc/fstab, the instructions are in the virtualization mega thread at the top of these forums.

---

