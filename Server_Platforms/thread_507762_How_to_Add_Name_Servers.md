---
title: "How to Add Name Servers?"
date: 2007-07-23
forum: Server Platforms
---

### Post by tocleora on 2007-07-23
I used to have a Red Hat server with Rackspace.com.  In that setup, i had my primary domain ([www.domain.com](www.domain.com)) and then I had two name server domains (ns.domain.com and ns2.domain.com).  I have an ubuntu server at work where we want to point a domain to it, but it's been so long I don't remember exactly how to do it.  This is what I do remember:

1. Rackspace gave me two ip addresses for the two name server domains.
2. I remember going to the domain registrar and registering these ip's with those name server domains.  this part I think I can figure out on my own.
3. I remember them some how associating those ip's to my network card?  They did this part so any assistance on how to do this would be greatly appreciated.
4. I remember adding these name servers in bind through webmin.  I might be able to figure this part out but if there are clear cut instructions somewhere I'd love them.  I do remember that bind was on my primary server, and I set up both ip addresses (well all 3 actually, the primary domain ip and both dns ip's) in there.

So I have two ip addresses, I need to set them up on the server per #3 and then associate them with bind per #4.  Then I need to go to the domain registrar and associate those ip's with those name server domains.  Am I forgetting something?  Are there instructions anywhere that go through this process clearly from beginning to end?  Or is there an alternative way I should do it instead?

Thanks in advance for any assistance!

---

### Post by murraymca on 2007-07-23
[QUOTE=tocleora;3067252]I used to have a Red Hat server with Rackspace.com.  In that setup, i had my primary domain ([www.domain.com](www.domain.com)) and then I had two name server domains (ns.domain.com and ns2.domain.com).  I have an ubuntu server at work where we want to point a domain to it

Hi, I'm not really clear on what that part means.  Maybe it would be best to just give Rackspace a call? 

.
4. I remember adding these name servers in bind through webmin.

As far as I know, you can just edit your zone file an place say:
@ IN NS ns.domain.com.

If the nameserver is in your domain, you will also need an A record for it:

ns IN A ip_address

I reckon giving Rackspace a call would be the quickest and most helpful ;)

---

