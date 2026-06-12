---
title: "Apache only showing 1 VirtualHost"
date: 2008-08-18
forum: Server Platforms
---

### Post by andyd34 on 2008-08-18
I have been having this trouble now for a couple of weeks, so much so I have now subscribed to a second provider so my server is not networked to my Windows computers.

I have several domain names registered with differant companies and all forwarded to my server external IP provided by my service propvider. This goes to a router and my server connects to that router.

My PC's are connected to a wireless router which gets its IP from a totally seperate provider now.

I have installed lamp on my server and set it up as per numerous googled sites.

in the apache2.conf I have added

ServerName localhost

My sites-available folder is as follows

**File: [www.combiman.co.uk](www.combiman.co.uk)**

> <VirtualHost *:80>


ServerName [www.combiman.co.uk](www.combiman.co.uk)

ServerAlias combiman.co.uk *.combiman.co.uk

DocumentRoot /media/disk/home/combiman/www/


<Directory /media/disk/home/combiman/www/>
Options FollowSymLinks
AllowOverride None
</Directory>

ErrorLog /media/disk/home/combiman/log/error_log

TransferLog /media/disk/home/combiman/log/access_log


</VirtualHost>


**File: [www.diyholidaylets.co.uk](www.diyholidaylets.co.uk)**
> 
<VirtualHost *:80>


ServerName [www.diyholidaylets.co.uk](www.diyholidaylets.co.uk)

ServerAlias diyholidaylets.co.uk *.diyholidaylets.co.uk

DocumentRoot /media/disk/home/diyholid/www/


<Directory /media/disk/home/diyholid/www/>
Options FollowSymLinks
AllowOverride None
</Directory>

ErrorLog /media/disk/home/diyholid/log/error_log

TransferLog /media/disk/home/diyholid/log/access_log

</VirtualHost>


**File: [www.theukhub.co.uk](www.theukhub.co.uk)**
> 
NameVirtualHost *:80

<VirtualHost *:80>

ServerName [www.theukhub.co.uk](www.theukhub.co.uk)
ServerAlias theukhub.co.uk *.theukhub.co.uk
DocumentRoot /media/disk/home/theukhub/www/

<Directory /media/disk/home/theukhub/www/>
Options FollowSymLinks
AllowOverride None
</Directory>

ErrorLog /media/disk/home/theukhub/log/error_log
TransferLog /media/disk/home/theukhub/log/access_log
</VirtualHost>

From the terminal window I have done the following

sudo a2dissite default
sudo rm /etc/apache2/sites-available/default
sudo a2ensite [www.theukhub.co.uk](www.theukhub.co.uk)
sudo a2ensite [www.combiman.co.uk](www.combiman.co.uk)
sudo a2ensite [www.diyholidaylets.co.uk](www.diyholidaylets.co.uk)

All site are now showing in /etc/apache2/sites-enabled/

When I type **[http://www.combiman.co.uk](http://www.combiman.co.uk) **
I get the enabled site **[www.combiman.co.uk](www.combiman.co.uk)**

When I type **[http://www.theukhub.co.uk](http://www.theukhub.co.uk) **
I get the enabled site **[www.combiman.co.uk](www.combiman.co.uk)**

When I type **[http://www.theukhub.co.uk](http://www.theukhub.co.uk) **
I get the enabled site **[www.combiman.co.uk](www.combiman.co.uk)**

With the companies I have my domains registered with I have pointed them to my external ip
[B]
 ***.***.***.*** [/B]

but I know with one of the hosting companies I have been using when I point to there server I have to forward to 

*****.***.***.***/~username** 
I can only guess the /~username is the site-enabled name

I have tried this in the browser address bar *****.***.***.***/~[www.theukhub.co.uk](www.theukhub.co.uk)** but I get a 404 error


Can someone please shed some light on what I have done wrong.

---

### Post by MJN on 2008-08-18
> **andyd34 said:**
> I have several domain names registered with differant companies and all forwarded to my server external IP provided by my service propvider.
 
No you have not. As we covered in your other thread your DNS is all over the place.
 
[www.combiman.co.uk]("http://www.combiman.co.uk") points to 86.16.254.80
[www.theukhub.co.uk]("http://www.theukhub.co.uk") points to 194.154.164.82
[www.diyholidaylets.co.uk]("http://www.diyholidaylets.co.uk") doesn't point anywhere (given that it is delegated to ns1.theukhub.co.uk which does not exist)
 
You really do need to sort out your broken DNS otherwise you don't have a chance in hell of fixing your Apache config in any methodical manner.
 
You say:
 
> With the companies I have my domains registered with I have pointed them to my external ip
 
but then also:
 
> but I know with one of the hosting companies I have been using when I point to there server I have to forward to 
 
*****.***.***.*****/~username
 
What do you mean by this? **You** are your 'hosting company' are you not? Or are you talking about your DNS providers? In which case anything after the / is not their realm (i.e. nothing to do with DNS).
 
> Can someone please shed some light on what I have done wrong.
 
Yes, ignored the advice previously given to you! Fix your DNS then you know where you traffic is going!
 
Mathew

---

### Post by andyd34 on 2008-08-18
But 194.154.164.82 is the DNS IP for 123-reg

---

### Post by MJN on 2008-08-18
What do you mean?

---

### Post by andyd34 on 2008-08-18
I have put my external IP as the forwarding address but 194.154.164.82 is the address of 123-reg.co.uk DNS

---

### Post by MJN on 2008-08-18
You're really playing around with this DNS aren't you? Are you're wondering why it doesn't work?! :confused:

Anyway, let's look at what we've got now...

[www.combiman.co.uk]("http://www.combiman.co.uk") points to 86.16.254.80 (same as before)
[www.theukhub.co.uk]("http://www.theukhub.co.uk") points to 86.5.18.96 (that's changed from earlier - it was pointing to a 123-Reg (Pipex) machine, now it points to NTL (presumably your ISP WAN address))
[www.diyholidaylets.co.uk]("http://www.diyholidaylets.co.uk") is still broken (as its NS is ns1.theukhub.co.uk which doesn't exist)

So, leaving [www.diyholidaylets.co.uk]("http://www.diyholidaylets.co.uk") aside, what exactly is your current problem?

Mathew

P.S. Presumably you have removed the entries from your local hosts file that we put in the other day? If not, it's no wonder you are blissfully unaware of the mess your externally-facing DNS is in.

---

### Post by andyd34 on 2008-08-18
I haven't touched the DNS its preset. I have opened a support ticket with 123-reg about the domains they must be working on them. 86.5.18.96 is my external IP

---

### Post by MJN on 2008-08-18
Can this thread be closed now then?

---

### Post by andyd34 on 2008-08-18
Yes

---

