---
title: "Email Server Question"
date: 2008-05-15
forum: Server Platforms
---

### Post by kroenecker on 2008-05-15
If I purchase my own domain name, can I assume that emails directed towards the domain will be forwarded to my ip address?  

Or do I have to purchase some sort of email option in order to set up my own email server?

Finally, if I have a free "domain" like "myname.no-ip.org", will emails sent there be forwarded to my ip address?

I'm pretty confused about how this works so any advice is greatly appreciated!

---

### Post by bluefrog on 2008-05-21
you will need to change settings in your registrar configuration page. BUT you'd better not change things as you appear not to know what to do.

---

### Post by windependence on 2008-05-21
It's a bit more complicated than that. You have to point your mx records to your server's IP address and then you have to be running a mailserver. 

If you want to jump into that without having to build everything from scratch, check out Zimbra. [http://www.zimbra.com/community/downloads.html](http://www.zimbra.com/community/downloads.html)

That page is a link to their community edition which is open source and free.

Otherwise if you just want e-mail from your domain to where you can check your mail, most domain registrars will forward the mail to you for a small fee or even free if you buy your domain name from them.

-Tim

---

### Post by hyper_ch on 2008-05-21
and if you want to send email through your server then you'll need a dedicated IP address... otherwise you might be blocked.

---

### Post by windependence on 2008-05-21
> **hyper_ch said:**
> and if you want to send email through your server then you'll need a dedicated IP address... otherwise you might be blocked.

True, he will need to have reverse DNS set up for outgoing mail.

-Tim

---

### Post by hyper_ch on 2008-05-21
hmmm, I just read he uses no-ip... they offer mx-entries... so it might be they also provide dynmic reverse dns?

---

### Post by windependence on 2008-05-21
> **hyper_ch said:**
> hmmm, I just read he uses no-ip... they offer mx-entries... so it might be they also provide dynmic reverse dns?

Yes, I believe they do. I used to have an acct with them myself. I like them much better than dyndns.

-Tim

---

### Post by MJN on 2008-05-21
> **hyper_ch said:**
> hmmm, I just read he uses no-ip... they offer mx-entries... so it might be they also provide dynmic reverse dns?
 
They can't do, because they don't control the reverse zone delegation for the IP address that his ISP assigns to him. They are unlikely to delegate the authority for it to a 3rd party too (certainly not for a standard resedential account).
 
That aside, reverse delegation or not the OP will likely find that it's the recognised dynamic IP allocation that will cause the troubles and hence require relaying through his ISP's mail server as one solution.
 
Mathew

---

### Post by windependence on 2008-05-21
You are correct on this, and I usually don't recommend trying to run an email server without a static IP, however, they advertise that they can somehow set this up for you. I do not know what exactly they are doing to make it work.

-Tim

---

