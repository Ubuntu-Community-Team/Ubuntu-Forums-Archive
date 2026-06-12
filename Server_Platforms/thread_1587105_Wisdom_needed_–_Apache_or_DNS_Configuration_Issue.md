---
title: "Wisdom needed – Apache or DNS Configuration Issue"
date: 2010-10-03
forum: Server Platforms
---

### Post by Donut5000 on 2010-10-03
I managed to host my webpage via my 10.04 LTS home server, however after I enter the address (i.e. *[www.mysite.com]("http://www.mysite.com")*) in the address bar, the address changes to the IP address and port number.  The webpage comes up, not problem, but I want the domain name to remain.  Would I accomplish this by configuring DNS (BIND) or Apache?  Here’s how I arrived at this point.
   
  1)      Registered the domain name from godaddy.  No hosting.
  2)      In godaddy’s domain manager, selected domain forwarding to my servers public IP address and port number.  Configured my routers firewall to accept requests.
  3)      Configure /etc/apache2/sites-availible/default:
  <VirtualHost www.mysite.com:port#>
  DocumentRoot /var/www/mysite.com/
  <Directory /var/www/mysite.com/
   
              Symbolic link to /etc/apache2/site-available/mysite.com (file now named mysite.com in lieu of default)
   
  Please help.  Helpful tips and guidance much appreciated.

---

### Post by HermanAB on 2010-10-03
That is an Apache configuration problem in the vhost stanza.

---

### Post by Ryan Dwyer on 2010-10-03
> **HermanAB said:**
> That is an Apache configuration problem in the vhost stanza.

No it isn't.

You need to remove the forwarding from GoDaddy and set up an A/HOST record to point to your IP address.

---

### Post by lisati on 2010-10-03
Did you remember to set up port forwarding to your server for port 80 as well as accepting incoming requests?

---

### Post by Donut5000 on 2010-10-03
I have a 2wire router from At&t u-verse and I created a special firewall exception for a server on port 80.  Other than that, I don’t see any other options as far as the router is concerned.
   
  I wish I [FONT=&quot]was knowledgeable enough to forget something during configuration.[/FONT] Aside from the Apache configuration I mentioned above, I haven’t made any other modifications to Apache or BIND9.  Perhaps Ryan’s godaddy reconfiguration is a good place to start.  Thoughts?  Is setting up an A/Host record the same as providing the nameservers?

---

### Post by BkkBonanza on 2010-10-03
The domain redirect allows you to use a non-standard port# but it seems when it does that it loses the name. If you add an A record to point to your IP then it won't lose the name but you will have to specify any non-standard port# as part of your address. 

An A record is not the same as providing nameservers (which isn't going to help you either). An A record is simply the base "address" record that you enter into GoDaddy's name servers. They will have a section for DNS records where you can add it in with a simple form. You should likely add a CNAME record for the **www** subdomain while you're at it.

I don't use GoDaddy so I'm a bit surprised the redirect doesn't work better. Usually these are done using a "frame" redirect which means that GoDaddy hosts a frame page that your redirected page shows up inside. It's transparent to the user and usually the address stays fixed (more than you want sometimes!). You may want to see if they have a couple choices for type of redirect and if one is called "frame" or maybe "cloaked" redirect and it's not what you already chose then it may work better.

---

