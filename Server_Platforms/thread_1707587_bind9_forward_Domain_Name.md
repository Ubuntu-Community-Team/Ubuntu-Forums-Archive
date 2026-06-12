---
title: "bind9 forward Domain Name"
date: 2011-03-15
forum: Server Platforms
---

### Post by wiggly81 on 2011-03-15
hi..
im about to purchase a VPS server I wish to forward my domain name to this server using bind I have come across many help files but it never seems quite clear to me, I would like to know is there a simple set-up for using my domain name setting up name servers etc. I can configure Apache fine and mysql php etc. it just seems to be bind that is catching me out, the VPS will be running ubuntu 10.04 if that is of any help my computer is running 10.10 so I will be running test set-up locally first if I can get some help on what I need to do to go forward from here.

thank you in advance

---

### Post by jmacgowan on 2011-03-15
Who did you register your domain with?
 
If you need to run your own nameservers, you will usually need two IP addresses for the VPS, but depending on which registrar you used we may not need to go down that road.

---

### Post by wiggly81 on 2011-03-15
yes I own many domain names I have just released 1 from its former name server so I can use it for testing my own set-up (I know its 24-48 hours) the domain is registered through simply names and I have control over name servers etc. I just need to know how to configure bind to use my domain name(s) so for now i have web server set up on my machine apache / MySQL / PHP using no-ip domain i have installed bind9.

---

### Post by jmacgowan on 2011-03-15
It looks like simplynames has it's own DNS utility, so why not just use that to point to the IP of your VPS? That's really all you should have to do and any requests at [http://example.com](http://example.com) should end up pointing to your webserver.
 
If you -really- want to run your own nameservers, you'll probably need two IPs as most registrars require two nameserver records. Then you'll just need to create a zone file for your domain in /etc/bind/ and configure it for your domain. I would recommend starting with the db.local file and copying it to db.example.net (where example.net is your domain) then changing the entries from there. Suggestions for setting up a zone file correctly can be found here:
[https://help.ubuntu.com/10.04/serverguide/C/dns-configuration.html](https://help.ubuntu.com/10.04/serverguide/C/dns-configuration.html)
 
Be sure to update named.conf accordingly as well.
 
Don't forget to restart BIND after you make changes, and post your zone file here if you can't seem to get it working.
 
edit: changed link to 10.04 instead of 10.10, even though it's probably exactly the same.

---

### Post by wiggly81 on 2011-03-15
> It looks like simplynames has it's own DNS utility, so why not just use that to point to the IP of your VPS? That's really all you should have to do and any requests at [http://example.com](http://example.com) should end up pointing to your webserver.

I could do this but it does not work so well, I cant have the URL display correct doing this and also eventually I will need all my domain names on 1 server but and this is where im going to complicate things further I need it like this for example..
[www.domain1.com](www.domain1.com) > would go to a folder called doamin1 on the web server
[www.domain2.com](www.domain2.com) > would go to a folder called doamin2 on the server etc.

i know it is possible somehow as the current web hosting plan I have has it set-up this way, I need to change to a VPS so I have greater control so I need to learn all these things I have taken for granted in the past lol

i will take a read through that link that was posted and hope to get somewhere with it, i learn fast (usually) so should be fine

any further thoughts on this matter are welcomed and appreciated.

---

### Post by jmacgowan on 2011-03-15
Now we're talking about two different things, so let me see if I can explain this right.

What will have to happen is that you will have to set up DNS records for domain1 and domain2 to point to the IP address of your VPS.  You're working on that part, so we'll leave it alone for now.

Let's try not to get to ahead of ourselves, but changing the folder that domain1 and domain2 point to will be done in apache2.

Basically:
By default, apache2 is configured to answer any request to it on port 80 using files in /var/www/

What you'll have to do is make two new "sites" within apache so it will answer requests for domain1 using /var/www/domain1 and requests for domain2 using /var/www/domain2

Documentation for the proper way to do this in apache2 can be found:
[https://help.ubuntu.com/10.04/serverguide/C/httpd.html](https://help.ubuntu.com/10.04/serverguide/C/httpd.html)
With much more information in apache2's documentation (you probably wont need this, but if you want more details about config options):
[http://httpd.apache.org/docs/2.2/](http://httpd.apache.org/docs/2.2/)

---

