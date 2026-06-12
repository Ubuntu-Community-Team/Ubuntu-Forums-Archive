---
title: "How to create a Dynamic DNS server?"
date: 2010-06-17
forum: Server Platforms
---

### Post by pepsifx357 on 2010-06-17
I was told that it was possible to setup a dynamic dns server on linux.  How would you do it?

---

### Post by iponeverything on 2010-06-17
[http://www.google.com/search?hl=en&q=Dynamic+DNS+server+linux](http://www.google.com/search?hl=en&q=Dynamic+DNS+server+linux)

---

### Post by pepsifx357 on 2010-06-23
Maybe I need to be more specific.  I've been running linux for about 2 years, so I'm still learning.

When you want to create a web server at home, usually you have to setup a dynamic DNS through your router with something like DynDNS.com so that you can link up your domain name.  Mine which I got through godaddy is: [www.bencookemusic.com](www.bencookemusic.com)

I'm sitting behind a router here, however DynDNS.com doesn't really work.  I have to keep going to the website and update my IP address manually.

Someone told me that I could set up a Dynamic DNS server that would work better and it would be on my server, instead of using a 3rd party service.

I would like for my internet/public IP address to be updated with [www.bencookemusic.com](www.bencookemusic.com) without using a service like DynDNS.com

The only reason I am being more specific and asking for the answer here, is because It's hard to find exactly what your looking for on the Internet when you're not as knowledgeable about the subject as many of you are here.  Sometimes you think you've found the answer and the website you read is not even close.

---

### Post by koenn on 2010-06-23
setting up your own DNS server, "dynamic" or not, is not  going to help here, because you have no control over your ip address, your ISP does. That's why you need ssomething like dyndns

to avoid the manual updates, you can run somthing like ddclient on your server. It will manage the updates for you

[http://www.dyndns.com/support/kb/using_ddclient_with_dyndns_services.html](http://www.dyndns.com/support/kb/using_ddclient_with_dyndns_services.html)

---

### Post by arrrghhh on 2010-06-23
Well... maybe you're not quite understanding how this is supposed to work.

Your friend is partially correct.  There is a couple of clients for linux (inadyn and ddclient - I prefer the latter) that will update your DDNS service for you.  So you're not really running a DDNS service on your machine, you're just running a DDNS client that updates your DDNS service... make sense?

---

### Post by pepsifx357 on 2010-06-23
So there's no way around having to use a service like DynDNS.com?  Unless I get a static IP of course.

---

### Post by koenn on 2010-06-24
correct

edit:
or maybe ...
you could mimic DynDNS by setting up a DNS server yourself, make it authoritive for your domain, then monitor changes in the IP address your ISP assigns to you, and modify the A and/or CNAME records in your DNS when needed, either manually or with an automated solution of some sort.

---

### Post by pepsifx357 on 2010-06-24
I'll have to do some research on this.

---

### Post by arrrghhh on 2010-06-24
> **pepsifx357 said:**
> I'll have to do some research on this.

What's wrong with dyndns?  I've used their service for years for free, I love it.  Very simple to setup, and does exactly what I need it to do - update my domain if my IP changes.

---

### Post by Vegan on 2010-06-24
I am lucky up here in Canada, we have static addresses that stay the same year after year.

I log into my domain registrar, not for IP changes, but to look at the logs.

---

### Post by EmanresuusernamE on 2010-06-24
The free services only allows you to manage a subdomain of one of their domains.  He has his own top level domain that he needs to update.  DynDNS has a service for that though:
[http://www.dyndns.com/services/dns/custom/](http://www.dyndns.com/services/dns/custom/)

It's $30 per year though.

---

### Post by arrrghhh on 2010-06-24
Ah, I did not realize that.  It does make sense however...

Well your options then would be to pony up the $30/year for dyndns, or pony up for a static IP.  The other method of doing a custom script to update your DNS records would work, but wouldn't be easy to implement.

---

### Post by pepsifx357 on 2010-06-25
> **arrrghhh said:**
> What's wrong with dyndns?  I've used their service for years for free, I love it.  Very simple to setup, and does exactly what I need it to do - update my domain if my IP changes.



I could never get it to work.  It would always reassign the IP to 12.0.0.1 or somthing not even close.  I would have to go to IPchicken and copy/paste my IP to update it.

---

### Post by arrrghhh on 2010-06-25
> **pepsifx357 said:**
> I could never get it to work.  It would always reassign the IP to 12.0.0.1 or somthing not even close.  I would have to go to IPchicken and copy/paste my IP to update it.

Works flawlessly for me.  I've used it for years.  Something in your config must've been wrong.  If you want some help setting it up, let us know.

---

### Post by pepsifx357 on 2010-06-26
trying to set it up now...

[http://www.uluga.ubuntuforums.org/showthread.php?p=9515726#post9515726](http://www.uluga.ubuntuforums.org/showthread.php?p=9515726#post9515726)

---

### Post by pepsifx357 on 2010-06-27
> **arrrghhh said:**
> Works flawlessly for me.  I've used it for years.  Something in your config must've been wrong.  If you want some help setting it up, let us know.

Please help me set it up, I've hit a brick wall again.  I've gotten the public IP to go to my web page, but dyndns.com won't forward the name.

---

### Post by SecretLegend on 2010-06-27
Hey Man Im guessing you are trying to link your domain name to your server. Its really simple and easy to do if you are trying to accomplish this:

So what I think your trying to do is: Server IP ( Servers Content Like in the www folder)= Yourdomain.com

If you are trying to do that you need to set up an A address and Get the name server to your godaddy account.

Here are the steps to accomplish this:

1. Go to namecheap.com and set up a freeDNS hosting account, and set that up with your domain name at godaddy. I am hoping you know how to add the name servers to your godaddy domain name.

2. Create an A adress in namecheap under you freeDNS account. If you don't know how to do this google it or use the live chat support at namecheap.com and they will guide you through the process.

3. Remember your value for the A address will be you IP which you can find out on cmyip.com, just use a computer thats on you network to accomplish this as they all will have the same IP.

4. Now you need to open port 80 on you router so that when people go to your domain it connects to your servers IP. You need to forward the port. If you don't know how to open port 80 you should google it.

5. When you open port 80 you need to enter the servers IP address which you can find out by issuing this code in your command line: ifconfig Now you need to look for the inet adress which is the last number at the end of init addr which should fit in the box in your routers port 80 forwarding box.

6. Now when you go to yourdomain.com it should connect to your server and display the site located in /var/www/ on your server.

7. Hope It works. this is how I configured my server to point to my domain. If you have any questions just ask me in this thread or Private Message me.

---

### Post by EmanresuusernamE on 2010-06-28
Have you tried one of their tutorials?
[http://www.dyndns.com/support/clients/unix.html](http://www.dyndns.com/support/clients/unix.html)

Also, is there a router between your server and the internet?  A good amount of routers, and now that I think of it, modems as well, come with the ability to update services such as DynDNS.  Look at your modems firmware first, then go for your router if you can't get it to work.

---

