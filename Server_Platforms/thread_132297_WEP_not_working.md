---
title: "WEP not working?"
date: 2006-02-18
forum: Server Platforms
---

### Post by biotope on 2006-02-18
I'm not sure if this is the right place to ask this.. but... 

The situation is this, i'm running ubuntu linux 5.1 on my acer notebook, and i did a quick scan using ethereal(the one included in the distro) and i'm suprised that all my packets turn up unencrypted, despite WEP being enabled. 

Not sure if there's something wrong with my WEP or isit just ethereal being too good at its job, can someone tell me if there is any other way i can check to see if my packets are indeed encrypted?

---

### Post by robert_pectol on 2006-02-18
WEP encrypts/decrypts data between the hardware devices.  Once your system gets the data, it's already been decrypted.  You were probably just monitoring that.  You'd need to monitor a wireless interface that isn't sync'd to your wireless network (does NOT have your access point or router's WEP key loaded) in order to see the encrypted packets.  Kismet and airsnort are a couple of utilities that come to mind (I like kismet).

---

### Post by biotope on 2006-02-18
i dun quite get it...

does it mean that if there are multiple computers connected to the one router/access point, the data packets flying around are encrypted, but would appear unencrypted to any of these computers that are monitoring the packets?

---

### Post by robert_pectol on 2006-02-18
Yes!  That is what WEP is designed to do; secure wireless networks so that "outsiders" cannot participate on your WEP enabled wireless network.  They have to know the key in order to exchange network data with any of the wireless devices on your network.  Since each of the local machines are connected and their wireless interfaces have the appropriate keys loaded, it's no different than a normal wired network from the PCs' point of view.  They don't even have to know that the data has been encrypted and then decrypted during its journey from one PC to the other.  Again, the data is only encrypted for transit over the wireless link and then decrypted once received at the other end.  This all takes place within the wireless devices themselves.  Now, if you are looking to encrypt local network traffic as well, then you might look into the various VPN solutions available.

As a side note, WPA is better than WEP so if your hardware supports it, that's what I'd use.  If not, WEP is much better than nothing.  :)

---

### Post by biotope on 2006-02-18
i see... thks man, solved a mystery for me ;) 

jus like to know though, is there any way i can capture the packets in its encrypted form? Other than using another machine not connected to my own network? would using another program such as kismet or airsnort help? cos i was trying to highlight the pros of encryption over no encryption in an assignment of mine and if i could actually produce a result, (ie. i send an email twice, first time before i implement WEP, 2nd time after i implement WEP, and i can only see the contents the 1st time) and would really appreciate it if anyone can help me out here.... :-k

---

