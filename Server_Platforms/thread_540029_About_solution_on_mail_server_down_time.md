---
title: "About solution on mail server down time"
date: 2007-09-01
forum: Server Platforms
---

### Post by satimis on 2007-09-01
Hi folks,


Re: Solution on mail server down time.

A mail server may be out of work under 2 situations,

1) The server is broken down
2) ISP connection is out of service

For 1) I can build a replicate server or just a box for mail queueing avoiding bouncing of mails
For 2) It is out of my control

I'm venturing to find a solution whether I can make use of the parking service on Registrar's server. Let the mails queneing there to be download back to the mail server later. OR are there any other suggestions? TIA


B.R.
satimis


P.S. the mail server only serves <15 users w/o heavy traffic

---

### Post by southernman on 2007-09-01
OR
3- Being dos'ed *boo hiss*

Seriously,

Just fire off a support ticket to your registrar to find out if/how they could handle this for you... (read - if it's doable or not)

Question - Are you serving this from your house/business, rented server, or a colo?

If your serving from home/business, and the emails are mission critical you may want to look into coloing a tower somewhere relatively close by if at all possible. Then use the colo as primary and home/business as the backup.

---

### Post by GigaVolt on 2007-09-01
For "2" I have such configuration:
1) I use two ISP
Example:
ifconfig eth0 127.0.0.11 up
ifconfig eth0:1 10.10.10.12 up
Lay stress on script change GW!
2) In domein name zone add dwo MX record
Example:
* MX      10 mail.domein.tld
* MX       20 backupmail.domein.tld

---

### Post by satimis on 2007-09-01
Hi folks,


Tks for your advice.

Registrar can solve point-2 of the problem which is my most concern.  I use one ISP.  I'm now searching doc on how to config MX.  Pointers would be appreciated.  TIA.


B.R.
satimis

---

### Post by southernman on 2007-09-01
[http://bobcares.com/article3.html]("http://bobcares.com/article3.html")HTH's

---

### Post by HermanAB on 2007-09-01
Note that a mail server doesn't *have* to be online all the time!

The SMTP protocol will retry delivery when a mail server goes down, or is very busy.  This retry time varies between 30 minutes and 2 hours, but the users will typically only get a warning message after 4 hours and a non-delivery message after 4 days.

So, when a machine fails, you have at least 3 days to fix a mail server, without suffering any loss of mail.  Shitty service yes, but no loss of mail.

Cheers,

H.

---

### Post by GigaVolt on 2007-09-02
Give notice to one BIG problem. Little mail servers use priority in MX record. Example, backup mail server get mail until mail server work

---

### Post by HermanAB on 2007-09-02
Yes, the MX record priority settings are also useful when you need to move to a new server.  Define the MX record with the new server as lower priority, that allows you to test the new server for a few days and gives the DNS change time to propagate.  Then eventually you just turn the old server off and all mail will then go to the lower priority server, which is the new one.  Then you you go back and change the MX records again to remove the old server.

---

### Post by GigaVolt on 2007-09-02
And don't forget change SPF record. 
More info: [http://www.openspf.org/Introduction](http://www.openspf.org/Introduction)

---

### Post by satimis on 2007-09-03
> **HermanAB said:**
> Yes, the MX record priority settings are also useful when you need to move to a new server.  Define the MX record with the new server as lower priority, that allows you to test the new server for a few days and gives the DNS change time to propagate.  Then eventually you just turn the old server off and all mail will then go to the lower priority server, which is the new one.  Then you you go back and change the MX records again to remove the old server.
Hi,

Tks for your advice.

MX on registrar's site will help me.  Any pointer about its setup and testing after setup.  TIA


B.R.
satimis

---

### Post by satimis on 2007-09-03
> **GigaVolt said:**
> And don't forget change SPF record. 
More info: [http://www.openspf.org/Introduction](http://www.openspf.org/Introduction)
Tks for your link.


B.R.
satimis

---

### Post by Mr. C. on 2007-09-03
Backup MX servers, outside your control, become enormous spam targets.  Spambots disregard MX priorities, and deliver to any accepting MX.  Unless you can perform the same level of anit-spam measures on the backup MX, you're better off not using one.  Otherwise, be prepared for your anti-spam measures being defeated.

Internet connections today are much more reliable than they were when SMTP was created.

MrC

---

