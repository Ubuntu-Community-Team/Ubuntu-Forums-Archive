---
title: "Home Server Risks"
date: 2008-08-09
forum: Security
---

### Post by frmdstryr on 2008-08-09
Hi, I recently was trying to decide whether or not to set up a apache2 home server. I was talking to a buddy of mine who says that I will get hacked if my server is not secure (by people with programs that scan for unprotected servers).  What are the risks of running a home server?  What can I do to set up some kind of protection if I do in  fact set up a webserver?  Thanks.

---

### Post by powderhound99 on 2008-08-09
Good question I want to know the same more specifically for a media server I want to be able to access my media anywhere I can get a network connection at home and a wan any were else... Also I'm aware it's fairly new and am just barely beginning to comprehend it but how much consideration should be given to the new dns bug?

---

### Post by brian_p on 2008-08-09
> **frmdstryr said:**
> 

What are the risks of running a home server?  What can I do to set up some kind of protection if I do in  fact set up a webserver?  

By 'home server' do you mean a server which will only be available to other machines on your network? If so, set up apache to listen only on your network. The risk of being hacked is zero.

---

### Post by brian_p on 2008-08-09
> **powderhound99 said:**
> Good question I want to know the same more specifically for a media server I want to be able to access my media anywhere I can get a network connection at home and a wan any were else... 

Select a media server to use. Read all its documentation thoroughly. Investigate its security track record. Install if satisfied. Enjoy.

> Also I'm aware it's fairly new and am just barely beginning to comprehend it but how much consideration should be given to the new dns bug?

Not a lot for what you want to do.

---

### Post by frmdstryr on 2008-08-09
by home server I mean my own free web hosting preferably local and over the interent. (im cheap & not ready to purchase yet)

I set up an apache2 server (on ubuntu desktop) and changed the ports.conf to listen 127.0.0.1:80.  If I put it on the internet what are the chances of being hacked like my friend is saying?  Also is a wrt54gl with tomato with default settings good enough protection to keep out unwanted visitors?

For web hosting I've heard you need to enable DMZ, what exactly is DMZ?

Thanks.

---

### Post by jerome1232 on 2008-08-09
DMZ is just a mode on routers that tell them to forward all traffic to the specified computer. It basically takes them out of the firewall. You can have only one computer in DMZ mode.

You don't need DMZ, in fact I would just forward the ports you need to the webserver. That way your router is still acting as a firewall for it.

---

### Post by frmdstryr on 2008-08-10
Well would I be likely to get hacked?  (I find it hard to believe, they probably have more important things to do)

---

### Post by HermanAB on 2008-08-10
Apache is very secure.  There are millions of them running on the web.  Most security issues come from badly coded PHP programs and idiot users using 4 character passwords.

So if you run Apache and don't do anything special with it, then it won't get hacked.  Before you run something strange like a BBS/Forum program, first read up on its security issues and always use looooong passwords for everything - 16 character semi-pronounceable passwords are good.

So, relax and enjoy your server!

Cheers,

Herman

---

### Post by Dr Small on 2008-08-10
> **HermanAB said:**
> Apache is very secure.  There are millions of them running on the web.  Most security issues come from badly coded PHP programs and idiot users using 4 character passwords.

So if you run Apache and don't do anything special with it, then it won't get hacked.  Before you run something strange like a BBS/Forum program, first read up on its security issues and always use looooong passwords for everything - 16 character semi-pronounceable passwords are good.

So, relax and enjoy your server!

Cheers,

Herman
Apache is secure right now. But who's to say it will stay that way if Microsoft lends a helping hand? :D

---

### Post by Joeb454 on 2008-08-10
I run a home server w/ apache, samba & ssh/sftp access.

So far so good :) (it has a flash game on it, I'll warn you now).

[http://www.joeb454.com](http://www.joeb454.com)

---

### Post by atoponce on 2008-08-10
Will you get hacked?  Not likely.  Then again, what data are you hosting that an attacker would want?  Consider the practicalities before considering the theoretical.  Think of it this way: if you have a proper firewall in place, the data you're hosting is not personal, and you're not stupid, then what are you worried about?  The likelihood of an attacker singling your box out for your data, is like taking a trip to Africa, singling out a specific ant hill, and squishing ants.

---

### Post by frmdstryr on 2008-08-10
I'm just trying to host a site that can give pricing for a small business my brother is running, nothing personal or anything that would really matter if it was taken.  I thought my friend was exaggerating. Thanks, I'm going to put it back on the interent now...hopefully I can figure out how to host on my dynamic ip.

---

### Post by daleus on 2008-08-11
> **frmdstryr said:**
> hopefully I can figure out how to host on my dynamic ip.

Look up "Dynamic DNS"

My router has a feature to update my dynamic home IP to my dyndns account (that's free btw), then I have a CNAME entry for my domain that points to that dyndns URL, so home.my-domain-name.com always resolves to my home IP address.

but if you don't have a domain, you can have a dyndns name like

frmdstryr.no-ip.com, depending on which domain you choose and what name you want to give it.

---

### Post by HermanAB on 2008-08-11
DynDNS is typically not worth the trouble.  For about $50 a month more your ISP can give you a server account with 2 or more fixed IP addresses and a lot more bandwidth.

Cheers,

Herman

---

