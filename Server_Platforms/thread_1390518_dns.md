---
title: "dns"
date: 2010-01-25
forum: Server Platforms
---

### Post by trentscott4 on 2010-01-25
I setup a webhosting server with ISPConfig and have some questions.  I use Comcast and have ddclient set to update ZoneEdit with my current external IP.  If I want to offer web hosting, what is the point of running my own DNS servers in house?  Couldn't I just have my domain xxxx.com direct to my external IP and forward thru the router to my server box and use virtual hosts thru apache?

---

### Post by noway2 on 2010-01-25
Yes, you can.  You don't need DNS to host a web page.  An internal DNS will allow you to communicate amongst the devices on your LAN with name and address resolution.  You can even combine it to co-ordinate with your DHCP.

---

### Post by trentscott4 on 2010-01-25
Any real advantages to doing so if I only want to run a web/mail server?

---

