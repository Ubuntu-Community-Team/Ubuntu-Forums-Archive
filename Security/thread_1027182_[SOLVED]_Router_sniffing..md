---
title: "[SOLVED] Router sniffing."
date: 2009-01-01
forum: Security
---

### Post by Hagablog on 2009-01-01
Before I start, just to make sure: we have a lincys router and the admin can monitor what sites I go on, the contents of those pages, the emails I send and passwords I enter to get into secure parts of websites.  What did I get wrong? 

I am pretty sure there is no spying software installed on my computer.  Is there anyway to encrypt the data so the admin (not me btw) can't read my emails.  Let's just say I know there is a sniffer of some description in use by the admin.  

FYI this is a private router and to my knowledge there is nothing wrong with not wanting the admin to read my emails.  I know this isn't specifically a Linux problem but I figured this was the best place to put it.  

As a side note:  since I'm becoming a bit of a security freak (always been the latter) are there any other security measures you would recommend to protect my data from the Admin.

---

### Post by Kinstonian on 2009-01-01
If your employer chooses to monitor their employees to detect breaches of the security policy such as breaking the acceptable use policy, or detecting attacks-- they have that right.  It's their network after all.  You obviously know you're being monitored and probably signed a document consenting, or consent when you login by agreeing to a login banner, etc., so you don't have any expectation of privacy while working.  Trying to find a way around the security measures your employer has implemented will usually get you in trouble.

---

### Post by Hagablog on 2009-01-01
It's not in an office it's at home.  I would fully accept it if that was the case it's not.  Visited sites is not my primary concern anyway, it's emails and passwords.

---

### Post by mikewhatever on 2009-01-01
How do you know you are being monitored? Who is the admin? Who is the owner of the router? Is it wired or wireless? You should really explain yourself.

---

### Post by Hagablog on 2009-01-01
I am on a wireless network and the admin is my Father who also owns the router.  I know I'm being monitored because he told me.  FYI Im not trying to hide something illeagal I just don't want him reading my emails and knowing all my passwords as I'm sure you'll understand. 

Is there actually a way that anyone knows.

---

### Post by pdtpatrick on 2009-01-01
use this for anonymity online: [http://www.torproject.org/](http://www.torproject.org/)
[http://www.gnupg.org/](http://www.gnupg.org/)   <----and this to encrypt your stuff:

---

### Post by bumanie on 2009-01-01
I can't help - but an observation. 
If you are not legally an adult, your father probably has the right to check what you are doing on the computer (at least up to a point - and that point is probably hard to define). I assume he pays for the hardware and internet etc. 
If you are an adult, you have the choice of putting up with things as they are or going to live somewhere else. I can understand you not wanting him to know everything, knowing all passwords and being able to read every email seems a bit over the top. 
How do you know there is no spying programs on the computer? What have you done to ascertain this?

---

### Post by mikewhatever on 2009-01-01
It may be wrong, but I think your father uses a packet analyzer of some kind and the router has nothing to do with it. I rather doubt there is anything you can do other then encrypt the wireless communication, which is impossible to do without having admin access to the router.
[http://en.wikipedia.org/wiki/Packet_sniffer](http://en.wikipedia.org/wiki/Packet_sniffer)
[http://www.wisegeek.com/what-is-a-packet-sniffer.htm](http://www.wisegeek.com/what-is-a-packet-sniffer.htm)

---

### Post by apoth on 2009-01-01
[https://gmail.com](https://gmail.com) ?

---

### Post by Rob_H on 2009-01-01
You can prevent local eavesdropping on email. The technique depends on whether you use some kind of web interface for your email (e.g. GMail) or a client program like Thunderbird or Evolution.

If you use a web interface, just make sure you type HTTPS in the browser window to connect to the server rather than HTTP. That will encrypt the traffic, and most web mail providers support that. If they don't, your browser will let you know.

If you use a client program like Thunderbird, then you're probably connecting to your ISP's email servers directly via POP and SMTP. The trick there is to make sure you configure your mail program to connect to those servers using SSL or TLS. The exact instructions vary by program and your ISP might not support it, so try experimenting or google for more specific instructions.

Good luck.

---

### Post by Hagablog on 2009-01-01
Wow thanks for all the advise.  In answer to a few questions:  I'm pretty sure there isn't software on my computer because I have complete control over it, plus to my knowledge he doesn't even know I'm running Linux and on the Mac side I can see everything that is installed (I have admin control over both). 
I am legally an adult (although I guess you only have my word for it).  I know it is techically his right but it still makes me uncomfortable.
It would make sense it was a package sniffer, if it is, what can I do?

Thank you so much everyone and I'll try out those things (not on aformentioned network obv.

---

### Post by Rob_H on 2009-01-01
> **Hagablog said:**
> It would make sense it was a package sniffer, if it is, what can I do?

See my earlier reply. Use of SSL/TLS/HTTPS defeats packet sniffers.

---

### Post by my_key on 2009-01-01
If you have access to computers or servers on a different network, there's lots of things you can do. E.g. [ssh dynamic port forwarding]("http://www.irongeek.com/i.php?page=videos/sshdynamicportforwarding"), use openvpn or freeswan,...

Good general advise:
Always use secure protocols like ssl. In gmail: use the setting to send all traffic over https. Learn about certificates and how people can man-in-the-middle them with cain and dsniff.

Also: show your dad who knows more about computers and [make him watch goatse or tubgirl all the time wile surfing the web]("http://www.irongeek.com/i.php?page=security/ettercapfilter"). Trust me, he will stop sniffing :D

Haha, I just found this document and it's basically all you need to know: [http://www.irongeek.com/i.php?page=security/hacker-con-handout](http://www.irongeek.com/i.php?page=security/hacker-con-handout)

Yes I know I look like I'm affiliated with that site, but I'm not. I just noticed it has lots of useful info for security newbies.

Cheers.

---

### Post by Hagablog on 2009-01-01
Thank you all so much.  Just what I wanted to know.  Problem solved in less than 24 hours that I've been battling for weeks with on my own (I know, I am a total newbie, but I'll learn).  Again, thanks

---

