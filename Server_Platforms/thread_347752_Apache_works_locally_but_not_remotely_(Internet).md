---
title: "Apache works locally but not remotely (Internet)"
date: 2007-01-27
forum: Server Platforms
---

### Post by proxima estacion on 2007-01-27
Hi,

I hope this is the appropriate forum to post this topic. I'm sure Im not the first to have this problem but couldn't find an appropriate thread.

I got Apache running nicely when I type in localhost in my browser i get a list of the contents of /var/www

I have a domain registered when i enter [www.mydomain.com](www.mydomain.com) I get the same list of the contents of /var/www

when I ask a friend outside of my network to goto [www.mydomain.com](www.mydomain.com) or enter [http://82.xx.xx.xx](http://82.xx.xx.xx) (my IP according to whatisyourIP.com) they get a message along the lines of "forbidden, you do not have access"

oh and I dont have a router I am connected directly to a cable modem.

Any ideas or pointers? Thanks

---

### Post by oldmanstan on 2007-01-27
you said it shows the contents? a common security practice is to not allow listings of directory contents.  try putting a file called index.htm in the /var/www directory and see if your friend can view that

---

### Post by proxima estacion on 2007-01-27
okay added /var/www/index.htm 

This is what I get when I type various things in:

[http://82.xx.x.xxx/index.htm](http://82.xx.x.xxx/index.htm)   - The test index page
[http://localhost/index.htm](http://localhost/index.htm)      - as above
[http://82.xx.x.xxx](http://82.xx.x.xxx)                  - contens of /var/www
[http://localhost](http://localhost)                     - contents of /var/www

When my friend enters the same links:


[http://82.xx.x.xxx/index.htm](http://82.xx.x.xxx/index.htm)  - The website for the people I bought the domain from
[http://localhost/index.htm](http://localhost/index.htm)     - N/A
[http://82.xx.x.xxx](http://82.xx.x.xxx)                 -  "Internet Explorer cannot display this Page"
[http://localhost](http://localhost)                    - N/A

Do these results offer any clues? Any further ideas or pointers? What should the access permissions to /var/www be so the world can view my web pages? 777  - Thanks

---

### Post by thornomad on 2007-01-27
Who is hosting your DNS ?  Same place you bought the web site from ?

---

### Post by proxima estacion on 2007-01-27
My limited subject knowledge is going to show up here...

I got [www.mydomain.com](www.mydomain.com) from a company and bought nothing but the domain name. I want to host the website on my own machine (using apache) and set it so people type mydomain.com and get to my site.

I set web forwarding from mydomain.com to my machine and which resulted in the problem described in the first thread.

I just did the CHANGE A record www to 82.xx.x.xxx  to see if that works

> **thornomad said:**
> Who is hosting your DNS ?  Same place you bought the web site from ?

The company I got the domain from I assume will host the DNS  and I didnt buy any web/server space from them

Does this make sense? either way Apache works in my network fine, but as it stands you guys wont be able to enjoy my holiday pictures...yet

Any pointers or good websites dealing with this?? - Thanks all

---

### Post by chrisfay on 2007-01-27
> When my friend enters the same links:

[http://82.xx.x.xxx/index.htm](http://82.xx.x.xxx/index.htm) - The website for the people I bought the domain from

How long ago did you purchase the domain? Sometimes it takes a day or so for the new DNS records to propogate.

If its been a couple days since you bought it, you should run a dns report from [http://dnsstuff.com](http://dnsstuff.com) and see if everything checks out ok and that your A record is correctly pointed to your server's IP.

If that's all good, you may be blocked on port 80, the default for web traffic. You can try changing Apache's listen port to 8080 or whatever other port you like and test it via [http://hostname.tld:8080](http://hostname.tld:8080). If you can connect on the non-standard port, you're ISP is probably filtering standard server ports.

---

### Post by proxima estacion on 2007-01-27
> **chrisfay said:**
> How long ago did you purchase the domain?
a few days ago, when I got the domain I set web fowarding to bbc.co.uk i could type in mydomain.com and it went to BBC no probs.

> ...run a dns report from [http://dnsstuff.com](http://dnsstuff.com) 
The following failed; Open DNS Servers; Missing Stealth name servers; Stealth NS record leackege; Acceptance of Postmaster address (postmaster@mydomain.com) - everything else passed

> your A record is correctly pointed to your server's IP.
Only just changed this, But I managed to forward to BBC.co.uk as a test so I don't think this is it

> you may be blocked on port 80, 
port 80 is defiantly open and all good.

Perhaps I shall wait to see if having changed the A record does it. What should the file permissions of my /var/www be?

Thanks for the guidance

---

### Post by chrisfay on 2007-01-27
> port 80 is defiantly open and all good.

How are you sure its open? Have you ran services on this port on your own server perviously? 

> Perhaps I shall wait to see if having changed the A record does it.
Generally, A record changes don't take more than a few minutes to update once the main routing to your domain's DNS server has already propogated throughout the root servers. Since thats done, any records you edit on your DNS server should be effective almost immediately.

> What should the file permissions of my /var/www be?

You could always chmod -R 777 your /var/www folder for testing purposes. Then get more restrictive once everything's functional. 

> [http://82.xx.x.xxx/index.htm](http://82.xx.x.xxx/index.htm) - The website for the people I bought the domain from

This still confuses me, usually you get the registrar's web site if you either haven't routed the domain somewhere or if you purchased hosting with them and haven't had your site configured yet. For it to be producing the domain registrar's home page when attempting your site is strange...Especially considering you're using their DNS servers and supposedly have configured an A record. 

What was the A record listed when you ran the dnsstuff report? Was it correctly listed as your server's IP?

---

### Post by crabhunter on 2007-01-28
Hi,
I'm having very similar problems except I always get my page up from inside my network and never the contents of /var/www.
I have got a file in there index.html just like you.
Follow some of the portforwarding advice in my thread here.
[http://www.ubuntuforums.org/showthread.php?t=346269](http://www.ubuntuforums.org/showthread.php?t=346269)
and my new thead here.
[http://www.ubuntuforums.org/showthread.php?t=347929](http://www.ubuntuforums.org/showthread.php?t=347929)
I'm glad I'm not the only one having this problem.
Mike

---

### Post by proxima estacion on 2007-01-28
hmmm...i dont really know how to say this so here I go it was my firewall all along. I completely forgot I had a Linux firewall. It was only after setting apache up in XP disabling the firewall in that I thought hang on a moment...


anyway I have taken the liberty of defrosting a kipper and will slap myself round the face just as soon as it has thawed out a bit.

Thank you all for your advice its so good to know the support is out there:guitar:

---

### Post by chrisfay on 2007-01-28
Glad to hear it!

---

### Post by crabhunter on 2007-01-28
Where oh where do I find firewall settings in Ubunto 6.10
It is probably my problem as well but as I thought I didn't have a firewall installed it wasn't that.
Thanks.
Mike

---

### Post by proxima estacion on 2007-01-28
As far as I am aware (this is by no means a fact) Ubuntu 6.10 doesnt have a firewall installed by default. I had 'Firestarter' installed accessible through System->Administration->Firestarter and it was right there. I uninstalled it with Synaptic Manager. and Apache worked a treat.


Have you used [URL="http://www.canyouseeme.org/"] to see if the Internet can see you on port 80? 

I am new to this forum but I think this thread is now dead. You should start you own thread (I think you did this though...hmm)

good luck

---

