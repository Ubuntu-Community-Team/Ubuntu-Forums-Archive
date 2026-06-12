---
title: "SPAM solutions for qmail"
date: 2008-05-19
forum: Server Platforms
---

### Post by leewilson78 on 2008-05-19
Hi all, 

I have a dedicated server, for some reason, the hosting company won't install SpamAssassin. So I was wondering what other spam filtering software I can use that can be configured with qmail?

Appreciate any help.

Thanks

---

### Post by HermanAB on 2008-05-19
Assp

---

### Post by windependence on 2008-05-19
Check out Zimbra. Maybe they will let you install a package like that, that has everything you need in one. It works great and has an open source version.

-Tim

---

### Post by leewilson78 on 2008-05-19
> Assp

I did ask them to install Assp, my host seems to be very picky, they say that there doesn't seem to be instructions for configuring Assp with qmail.

> Check out Zimbra. Maybe they will let you install a package like that, that has everything you need in one. It works great and has an open source version.

I will try this.

Thanks

p.s. if anyone has any detailed instructions for installing Assp with qmail I would be very happy.

Lee

---

### Post by windependence on 2008-05-19
> **leewilson78 said:**
> I did ask them to install Assp, my host seems to be very picky, they say that there doesn't seem to be instructions for configuring Assp with qmail.



I will try this.

Thanks

p.s. if anyone has any detailed instructions for installing Assp with qmail I would be very happy.

Lee

If you decide to try Zimbra, you should be able to install it yourself remotely from the command line. The installer is menu driven and quite easy, you just have to make sure the hostname is correct. When it asks you if you want to change the hostname say no, even though it looks like you want to change it. Good luck!

-Tim

---

### Post by leewilson78 on 2008-05-19
> If you decide to try Zimbra, you should be able to install it yourself remotely from the command line. The installer is menu driven and quite easy, you just have to make sure the hostname is correct. When it asks you if you want to change the hostname say no, even though it looks like you want to change it. Good luck!

-Tim 

That sounde perfect, I will give it a try.

Thanks

---

### Post by leewilson78 on 2008-05-19
couldn't find any configuration guideline for configuring Zimbra with qmail. Are there people hear who have done this?

My hosts don't seem to be willing to try anything without instructions.

Thanks
Lee

---

### Post by windependence on 2008-05-19
> **leewilson78 said:**
> couldn't find any configuration guideline for configuring Zimbra with qmail. Are there people hear who have done this?

My hosts don't seem to be willing to try anything without instructions.

Thanks
Lee

Ack, I'm sorry, I was actually suggesting using Zimbra in place of qmail. Qmail is a great product, but Zimbra is all in one package, runs on linux and has the spam, anti-virus and stuff built in. It's really a nice product. I had built my own mail server from scratch like you and found Zimbra on a client's machine. I was so impressed, I wiped my server and installed it for myself. There were quite a few features I didn't have and admin was wayyyy easier. And no I don't work for them. ;-)

Here is the link:

[http://www.zimbra.com/community/downloads.html](http://www.zimbra.com/community/downloads.html)

And here is the documentation:

[http://www.zimbra.com/community/documentation.html](http://www.zimbra.com/community/documentation.html)

-Tim

---

### Post by leewilson78 on 2008-05-19
I did post over Zimbra and they were very prompt with their reply, confirming what you have said.

I think Zimbra is the best solution for me, If I can get my host to disable qmail and use zimbra.... it might save me bunch of time.

If my hosting company aren't willing to install Zimbra, they seem to be quite happy for me to install myself, I am not too confident with this, windependence, would you be willing to install for me, if I wiped the server clean? For a fee of course, perhaps you could quote me for this.

If not, no problems.

Thanks
Lee

---

### Post by windependence on 2008-05-19
> **leewilson78 said:**
> I did post over Zimbra and they were very prompt with their reply, confirming what you have said.

I think Zimbra is the best solution for me, If I can get my host to disable qmail and use zimbra.... it might save me bunch of time.

If my hosting company aren't willing to install Zimbra, they seem to be quite happy for me to install myself, I am not too confident with this, windependence, would you be willing to install for me, if I wiped the server clean? For a fee of course, perhaps you could quote me for this.

If not, no problems.

Thanks
Lee

Sure, let me work you something up. You can reach me here or at [email]tim@linuxsystems4you.com[/email]

-Tim

---

