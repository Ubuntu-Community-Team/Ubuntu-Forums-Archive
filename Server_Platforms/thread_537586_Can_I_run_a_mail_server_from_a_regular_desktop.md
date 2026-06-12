---
title: "Can I run a mail server from a regular desktop?"
date: 2007-08-29
forum: Server Platforms
---

### Post by Gen2ly on 2007-08-29
I been thinking lately that it would be nice if I could get my own server to do my mail and be able to run it from a desktop install.  My requirements aren't much - 2,3 users don't think virus and spam and anything to be concerned about.  But will a regular desktop (coreduo-2GB) still work alright with it daemonized?  Or would this really require a separate machine?

---

### Post by Gen2ly on 2007-08-29
Good to know.  I've always heard of them in server capacity.  The reason I ask is that I don't want my box to slow to a crawl.  Like I said I won't be getting a lot of mail but I know these run as a daemon.  So I guess I was thinking what kind of overhead are we talking about?

---

### Post by Yizi on 2007-08-29
can anyone name a mail program?! open source if not paid one.

---

### Post by googlah on 2007-08-29
Hi,

Yes, I would suggest you look into "postfix" which can be fetched from a apt-get source. That was the first app I came in touch with and it was sure an easy install.

Then you just need something in pop3/imap-way.

---

### Post by KCPokes on 2007-08-29
I recommend Zimba, which is an all-in-one solution, but it does have some high overhead and really should be ran on a dedicated machine.  

For a shared machine, as was stated, I'd recommend running Postfix.  I'd also recommend, though, that you look into possible using SpamAssassin as well.  If you are going through the trouble of setting up your mail server, might as well integrate something that will make your life easier down the road.  

One other thing of note, before you start, is to verify that your ISP allows port 25 traffic.  A lot of providers have blocked this port, due to spamming.

---

### Post by Yizi on 2007-08-29
what about if i install Cpanel / WHM does the mail service comes with it?

---

### Post by KCPokes on 2007-08-29
Unless it has changed, cPanel carries a substantial licensing fee.  But, even with cPanel, you will still need to install and configure the mail server.  cPanel just provides you a graphical interface for using the service(s).

---

### Post by Yizi on 2007-08-29
OK, thank you for the information, it hepled a lot.

---

### Post by googlah on 2007-08-29
Instead of cPanel, there is also zPanel which is based on open-source. I have not tried it myself, but I guess it should be pretty good. As stated in the messages over this one, Postfix need port 25 to be open from your ISP if you want to handle outgoing mail yourself, but many providers block this feature due to spam.

Instead, which was not stated, you can choose to use your ISP's SMTP-server for outgoing mail, which often is offered to the customers.
That is set in the Postfix configuration at the line which says "Relay_host". I've put mine to smtp.bredband.net for instance.

---

### Post by reckless2k2 on 2007-08-29
zimbra is great but it does hog some resources especially if you are using this as a regular desktop machine. postfix with squirrel mail will do great even though it's not so pretty. you could just yank it down to thunderbird or evolution if you don't want a web interface with squirrelmail from other computers. keep in mind though that you now have to keep that machine running at all times though. some people forget that a server needs to run all the time. haha

---

### Post by Yizi on 2007-08-29
I think i should give Cpanel a try.

---

### Post by Yizi on 2007-08-29
Anyone knows where i can get the Zpanel in .tar format? :-s

---

### Post by Gen2ly on 2007-08-29
Thanks appreciate this ideas.   I still have to decide what imap client to use and how much over head this will all cost.  The thought on spam is a good idea as I hadn't thought of that previously.  I'll let you guys know  how it all turns out.

---

### Post by freebeer on 2007-08-29
I run a mail server on my 6.06 box.  (Sendmail, in my case) and the overhead is basically zilch if that's anything to go by.  I don't have much traffic, of course - mostly outgoing, but it hasn't hampered performance a bit.

---

### Post by reckless2k2 on 2007-08-30
well i have a domain name and DDNS along with running zimbra and i get a decent amount of spam. there are some tweaks i can do but haven't done so as of yet. if you are not going to get a FQDN and DDNS, you probably will have a very small spam issue. FQDN and DDNS through no-ip.com was not too much money a year.

obviously the mail server was free if you sue zimbra, postifx, ...etc..etc.

---

### Post by Gen2ly on 2007-09-02
Do I have to pay for domain name? or can I just register one?  All the information I've looked up is mostly advertising.  Seems to me though that you can inform a DNS and pass the domain on??

I should also mention that I have a static-ip.

---

### Post by reckless2k2 on 2007-09-02
well if your isp gives you a static ip you don't necessarily need ddns. as long as you know your addy, you just plug the ip in the address bar and you will be fine for accessing webmail or even if using a mail client just point to the ip just the same. 

as far as if you want a domain name, no-ip (the service i use) provides free domain names with a ddns service i'm pretty sure. i don't know. dyndns has something like that too. hhhmmmm...i think they both have free domain names and ddns. i know the free names those are part of their domains so it's not like you can pick [www.domain.com](www.domain.com). it has to be something usually like [www.domain.no-ip.com](www.domain.no-ip.com). check out their sites if interested. if you have a static ip from your isp though, not really a need for ddns.

---

