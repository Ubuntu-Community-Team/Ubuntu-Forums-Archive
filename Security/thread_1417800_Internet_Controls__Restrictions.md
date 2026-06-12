---
title: "Internet Controls / Restrictions"
date: 2010-02-27
forum: Security
---

### Post by Scotty-B on 2010-02-27
Hello-

I am looking for some advice on restricting access to the internet to certain times and days. Here's what i have in mind:

I have 3 computers (2 Win XP and my Ubuntu Server 9.1 box) and 2 iPod touches on the network, all access the internet via a wireless router/switch.

I currently use the Ubuntu server as a personal ftp and web server.
I would guess that I could also slap another network card into it and use it as a router. 

Assuming I get the Uuntu box to route for me, I would like to limit my kid's access to the internet to certain times on certain days. Doing this on a per mac addresses or static ip's basis makes sense to me.

Can anyone suggest some software to do this? And if said software can be configured via Webmin, all the better, tho I'm not hellbent on avoiding command lines or hand configuring .conf files if I can get good docs to guide me.

---

### Post by joberly on 2010-02-27
What kind of router do you have? Some stock firmware will allow you to do this right in the router config. You can alternatively flash the firmware with DD-WRT or Tomato, and get the desired results. (Not sure if they support scheduling, it's been a while since I've played with it)

Otherwise, in order to restrict access via your Ubuntu box, you can create firewall rules to REJECT or DROP all packets coming from the boxes you specify. Then use cron jobs to start/stop the rules in place. Of course you need to make sure the computers are being routed through the Ubuntu machine where the firewall is.

You could even configure it to simply reject WWW traffic, and allow the boxes to continue to operate on the network and share resources, if you want.

Someone may have an easier setup using some other software, but it can be accomplished with iptables and some learning!

---

### Post by Scotty-B on 2010-02-28
Thanks for the reply joberly. THe router is a Belikin, and so far i have had no luck w/ the DD-WRT firmware. 

I hadn't thought of using cron to put the rules into place. Seems like a great solution.

Now.... off to google to learn me some iptables!

Thanks again.

---

### Post by karthick87 on 2010-03-01
You can do it by using squid proxy..

---

