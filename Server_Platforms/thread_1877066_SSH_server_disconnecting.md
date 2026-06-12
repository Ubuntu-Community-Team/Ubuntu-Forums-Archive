---
title: "SSH server disconnecting"
date: 2011-11-07
forum: Server Platforms
---

### Post by stormthirst on 2011-11-07
I've recently installed v11.10 as a fresh install on an old PC. It's working and everything seems to be functioning properly. Originally I had it set up with a dhcp address. I've changed that to a static address, and now the SSH server keeps dropping my connection after what feels like less than a minute of inactivity. This is obviously suboptimal. Worse, when I try and re-connect it usually takes a minute or so before I can log back in via ssh. I temporarily changed it back to a dhcp address and everything returns to normal.

I've added:

LogLevel DEBUG

to the /etc/ssh/ssh_config file, but there's nothing relevant in the syslog.

I've looked through the man pages, and checked this forum and googled for a solution, but nothing seems relevant.

How can I get more information to try and work out where the problem lies?

---

### Post by papibe on 2011-11-07
Hi stormthirst.

When you changed to a static IP, Did you restart your server? (because if you don't the dhcp client process was probably still running and trying to change your IP).

Also, Does your router supports DHCP reservation? I find myself easier to set an static IP on the router and leave the default configuration just as it is.

Regards.

---

### Post by stormthirst on 2011-11-07
I rebooted the PC when I changed the IP address.

My router does support reservations - and for the most part I do use them. However, the server will soon be handling local DNS queries, and DHCP itself rather than the router, so it needs to go over to a static address.

---

### Post by papibe on 2011-11-07
Interesting.

An idea: May be it is a DNS problem?

I would try this: set your server to a static IP, and then in the client add an entry to /etc/hosts for the server. Something like:
```
192.168.1.10         your_server
```
That way the client  won't have a doubt which one is the server's IP.

Also, I would try connecting using the zero configuration style:
```
ssh your_user@your_server.local
```

Just some thoughts,
Regards.

---

### Post by stormthirst on 2011-11-07
Doh! I've found the problem: IP address conflict!

I'd pinged the new address before changing it over to make sure, but hadn't turned on the media streaming device which was on the address. Neither the PC nor the media device told me there was a conflict.

*sigh*

Thanks for your help anyway!

---

### Post by papibe on 2011-11-07
:D Glad you solved it.

Kind Regards.

---

