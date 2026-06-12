---
title: "Need Help With Apache!"
date: 2012-06-23
forum: Server Platforms
---

### Post by Manhi40 on 2012-06-23
I am trying to run a website from my ubuntu machine (11.10) but I can only log into the server with my internal and external ip. I want to be able to log into it with [www.erykcraft.com](www.erykcraft.com) but it wont let me. I'm running it with apache2 also my server's ip is <snip>
Thanks in advance!

---

### Post by lisati on 2012-06-23
*Thread moved to **Server Platforms**.*

I've removed your IP address from your post to help avoid possible security issues.

Have you arranged registration with a DNS provider yet? If so, your website name might not be fully propagated through the DNS system. 

If you are on a dynamic IP address ([www.whatismyipaddress.com](www.whatismyipaddress.com) seems to think you are) you will also need to arrange for your details to be automatically updated with your DNS provider: if you're in luck, there will be a setting you can use in your router.

Does your ISP block port 80? Do you have port forwarding configured on your router? I tried browsing your website using your IP address but the connection timed out.

---

### Post by phaed on 2012-06-23
What do you mean "log into it", over ssh?

Also, are you saying you want the server to host the domain erykcraft.com? If so, you need to add an A record in the DNS with the IP address of your server, but that domain isn't registered.

---

### Post by Manhi40 on 2012-06-23
im not very familiar with dns, i haven't setup dns, can you explain what dns is, and is it free? thanks! and sorry for bad spelling/grammor, im om my phome

---

### Post by gregor171 on 2012-06-23
First you have to REGISTER or BUY this domain (I use godaddy.com since it has good pricing for .com) and registrars do provide you with DNS server with DNS manager that allready have default values in it.

What DNS does is pointing a human readable web address  yourdomain.com to it's computer readable directions or IP address! There many records that are in a DNS and for pointing to a web server you need to change A record or CNAME. 

You need at least one A record that points to IP address!

Sample fot A record:
Host: @ Points to  xxx.xxx.xxx.xx
results:
yourdomain.com to an IP

Sample for CNAME:
Host: www Points to  @
results:
[www.yourdomain.com](www.yourdomain.com) to yourdomain.com

That would be a quick introduction in to DNS services!

PS: If you do not have static IP, this will work until your IP is changed! In this case you need a dynamic DNS service!

---

### Post by Manhi40 on 2012-06-23
ok,  now i understand! but is dns a one time fee? also i found a  google dns thing that is free will that work? 
thanks again!

---

