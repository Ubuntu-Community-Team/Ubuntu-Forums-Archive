---
title: "Hylafax on hardy 8.04 server"
date: 2009-09-08
forum: Server Platforms
---

### Post by minerbog on 2009-09-08
Hi Guys,

Any help would be great :)

I have installed hylafax on hardy server 8.04. All installed fine (as far as I know!!) and runs like a treat!. I can recieve faxs no problem but all it does is store them in recvq folder as a tiff.

I have set the FaxDispatch file to pdf and sendto to my email address but the log still shows it is storing them as a tiff in the recvq folder.

I have searched high and low on the net about this but can not seem to find an answer that works!

I have conviced my boos to use linux for our lamp and file server but if I can not get the fax working I feel he may force my back to windoz!! ARRRRGH please helpif you can.

Thanks

---

### Post by i.r.id10t on 2009-09-08
Do all incoming faxes get sent to the same email address?

If so a trivial script run via cron should do it.

---

### Post by minerbog on 2009-09-09
> **i.r.id10t said:**
> Do all incoming faxes get sent to the same email address?

Yes all faxes get sent to the same mail address.  However I have fiddled some more by running faxrcvd from command line.  It does convert to PDF but then just seems to disapear.  I have found a mail in /var/spool/hylafax/mail to FaxMaster. When I nano  the file it says the mailing has fail because remote domains are not supported?

Any Idea what that means?

---

### Post by kustomjs on 2009-09-09
are you using a internal modem or external modem?  its best to use external modem.

to see if your modem is online type in faxstat in the command line.

---

### Post by minerbog on 2009-09-10
The modem is an external and it is working fine.

It receives faxs lovely and sends faxes lovely.

I just cannot get it to forward the faxes to an email address.

---

### Post by minerbog on 2010-01-15
I had to install mail server to handle local emails.

Opps

---

