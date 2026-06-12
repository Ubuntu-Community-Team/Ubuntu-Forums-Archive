---
title: "question from a newbie"
date: 2006-03-24
forum: Server Platforms
---

### Post by bionnaki on 2006-03-24
I currently have a website that I primarily use for email & hosting images and random files for friends. my one year host contract is up in 2 weeks and I'd like to see what my options are. I see it is possible to host your own website/email server. can I do this with only my desktop computer running ubuntu? or do I need another computer for this? my connection is fast enough for my purposes and I dont think I'd need a fast connection to serve my files (little traffic).

just wondering if this is possible or not - thanks!

---

### Post by gerbman on 2006-03-24
[QUOTE=bionnaki]I currently have a website that I primarily use for email & hosting images and random files for friends. my one year host contract is up in 2 weeks and I'd like to see what my options are. I see it is possible to host your own website/email server. can I do this with only my desktop computer running ubuntu? or do I need another computer for this? my connection is fast enough for my purposes and I dont think I'd need a fast connection to serve my files (little traffic).

just wondering if this is possible or not - thanks![/QUOTE]
It is pretty easy to set up an Apache web-server in Ubuntu. I've never set up an e-mail server, but I doubt it's any harder. The only trouble I've had is that I don't have a static IP address through my ISP, but that's not an Ubuntu problem and isn't much of an inconvenience anyway. Go for it.

---

### Post by kennethb on 2006-03-24
I'm going to follow this thread for a bit as I'm wanting to do something similar. My ISP (Comcast) does not offer static IP addresses. I can get a few dynamic IP address, but I have learned that I would need to use somehting like 'no-ip' to manage/sync the dynamic IP address provided by my ISP with the IP address on my Ubuntu box.

---

### Post by gerbman on 2006-03-24
[QUOTE=kennethb]I'm going to follow this thread for a bit as I'm wanting to do something similar. My ISP (Comcast) does not offer static IP addresses. I can get a few dynamic IP address, but I have learned that I would need to use somehting like 'no-ip' to manage/sync the dynamic IP address provided by my ISP with the IP address on my Ubuntu box.[/QUOTE]

I don't think you should need anything extra to get Apache up and running on a dynamic IP address. Comcast is my ISP, too, and the only "problems" I have had have been when my IP address changes, but it hasn't done that in a few months. I am behind a Linksys router and simply set up port-forwarding to direct incoming http connections to my PC. I would give it a shot.

---

### Post by wsanders on 2006-03-24
You can set up Dynamic DNS ([www.dyndns.org](www.dyndns.org)) to have a permanent link to your IP, which updates whenever your IP changes. Setting up a web server (apache) is very easy, though setting up a mail server takes a bit more work. Also, your ISP may not allow you to run a web site, check your subscriber agreement to be sure.

---

### Post by bionnaki on 2006-03-24
ok thanks for the replies.

I have comcast as well and I see they offer static ips for an extra dollar or so per month. perhaps this is only a regional option..?

so, all I really need to host my site via my desktop computer is apache. now, how resource-intensive is this? I wouldnt have much traffic at all. I have a pent4 with 1 gig of memory and a pretty fast connection - would I notice the difference?

I'll check the comcast TOS to see if they say anything about hosting personal websites, but if any finds out, post it.

---

### Post by bionnaki on 2006-03-24
is there a how-to that explains the steps to set this up?

---

### Post by wsanders on 2006-03-24
apache is simple enough and not resource intensive 
[https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

---

### Post by gerbman on 2006-03-24
[QUOTE=bionnaki]ok thanks for the replies.

I have comcast as well and I see they offer static ips for an extra dollar or so per month. perhaps this is only a regional option..?

so, all I really need to host my site via my desktop computer is apache. now, how resource-intensive is this? I wouldnt have much traffic at all. I have a pent4 with 1 gig of memory and a pretty fast connection - would I notice the difference?

I'll check the comcast TOS to see if they say anything about hosting personal websites, but if any finds out, post it.[/QUOTE]
You'll never notice :-)

---

### Post by bionnaki on 2006-03-24
thanks. this looks a bit over my head right now. I got to the part where it says

> After installing MySQL, you really ought to read [WWW] 2.9.3. Securing the Initial MySQL Accounts from the [WWW] MySQL Reference Manual. The basedir is /usr so:

cd /usr
sudo ./bin/mysql_install_db --user=mysql


but im not sure how to configure this...

guess I need to read more about what exactly all this stuff is.

---

### Post by kmi on 2006-03-25
[QUOTE=bionnaki]thanks. this looks a bit over my head right now. I got to the part where it says



but im not sure how to configure this...

guess I need to read more about what exactly all this stuff is.[/QUOTE]

The how-to appears a little bit too complicated in my opinion. :p 
Simply do :
```
sudo mysql_secure_installation
```
It will ask for root password, just type 'Enter', then type (2 times...) your new root password... You're done.

After that you might install phpmyadmin:
```
sudo apt-get install phpmyadmin
```
and then manage all MySQL related questions through phpmyadmin's webGUI.
Let me please know if it fits with your needs :)

---

### Post by kennethb on 2006-03-25
[QUOTE=gerbman]I don't think you should need anything extra to get Apache up and running on a dynamic IP address. Comcast is my ISP, too, and the only "problems" I have had have been when my IP address changes, but it hasn't done that in a few months. I am behind a Linksys router and simply set up port-forwarding to direct incoming http connections to my PC. I would give it a shot.[/QUOTE]

Thanks for the suggestion. I'm behind an Apple Airport Base Station. So I'll need to figure out how to direct incomming http connections to my Ubuntu box.

---

### Post by kennethb on 2006-03-25
[QUOTE=gerbman]I don't think you should need anything extra to get Apache up and running on a dynamic IP address. Comcast is my ISP, too, and the only "problems" I have had have been when my IP address changes, but it hasn't done that in a few months. I am behind a Linksys router and simply set up port-forwarding to direct incoming http connections to my PC. I would give it a shot.[/QUOTE]

Thanks for the suggestion. I'm behind an Apple Airport Base Station. So I'll need to figure out how to direct incomming http connections to my Ubuntu box.

---

