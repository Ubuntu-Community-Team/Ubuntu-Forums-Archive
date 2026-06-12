---
title: "Xbox connection through router ubuntu security question"
date: 2009-02-22
forum: Security
---

### Post by bruce64 on 2009-02-22
Good afternoon - I just hooked up my son's xbox to a router that shares a connection with my computer using a Linksys 4 port router.  What security measures should I be taking?  More importantly if the xbox gets hit with a virus, what are the chances of it infecting my machine?  I know that .exes won't run automatically on ubuntu I'm not worried about that. I am asking because I do not know what I should be doing to make my system as locked down as possible.  I know that xbox users have the ability to download games through the console (not even sure the method is even locked down but thats for another thread).  Any help would be greatly appreciated.  Take care.

---

### Post by whoop on 2009-02-22
You should be fine. Chances your ubuntu will be infected via the xbox are non existent atm. 
If you want to take measures anyway, make sure you haven't got services running on your ubuntu (default ubuntu desktop runs 0 services) and make sure your router's firewall is configured properly <-- all ports for all lan ip's closed except for specified xbox ports (probably, I don't have xbox).
Also keep you ubuntu updated.
That's it.

---

### Post by bruce64 on 2009-02-22
Thanks for the heads up!

---

### Post by bodhi.zazen on 2009-02-22
I do not see how the XBox changes security measures on Ubuntu.

Start with the sticky on these forums.

---

### Post by bruce64 on 2009-02-22
The reason for the initial post was because I know very little about gaming consoles period, however the post was because as far as I'm concerned I am not aware of any firewall feature on an xbox nor was I aware of how to lock one down through the router.  My concern is that the xbox would be used as sort of a backdoor into my linux machine because both are connected to a wired router.  Maybe its a little paranoid but that is why this ended up being posted here.  Lastly looking at previous posts for xbox through wired turned up little that was useful.  I appreciate your post though.

Take care

---

### Post by bodhi.zazen on 2009-02-22
Well security is only as good as the weakest link in the chain, so start by securing the XBox as much as possible.

Otherwise your configuration does not change Ubuntu much, it is no different then connecting to the internet in general (lots of bad stuff on the internet).

You can always configure your xbox with a static IP and then use iptables or ufw to deny all traffic from your xbox ip address if you wish, would be simple to do.

---

### Post by bruce64 on 2009-02-22
This is really helpful, many thanks for your time!  Again, it may be a little over the top paranoid but better safe than Windows.

Take care!

---

### Post by bodhi.zazen on 2009-02-22
You are most welcome. I should have been more clear but I did not understand what you were wanting.

---

### Post by sinclair86 on 2009-02-24
Make sure ICMP is disable on the router although you may not be able to get viruses I play a lot of gears of war 2 and you have to worry about people DDOS'ing you if you are host which happens time to time when you play online games.... Dont know what you use the your home computers for but DDOS is no joke espically if you talked a lot of trash during the game and you pissed someone off and they run ddos on you for a day or two... lol

---

### Post by phones604 on 2009-02-25
[chinese cell phones](http://www.chinese-cell-phones.com) [img]http://www.chinese-cell-phones.com/uploadfile/UploadFileimages/2009177364091959b.jpg[/img]

---

