---
title: "My own custom server: how?"
date: 2009-10-13
forum: Server Platforms
---

### Post by erupter on 2009-10-13
Hallo.
I am fairly new to linux, just used some ?ubuntu (jolly char) distros for writing my thesis. But i have a decent knowledge of computers, programming, networks.
Just it's in the windows world.
Now my project.
I want to build a home server, and i could go windows but i'd really like to be able to do a couple things. And i don't know windows softwares that do them.

Essential server functions
-NAS
-RAID (mirroring, so chipset drivers needed: what chipsets do have linux drivers?)
-DLNA
-advanced mail server

(other functions i already know i can do: ftp, torrent client, webserver and so on)

Now what i mean by "advanced mail server"?
Essentially i want something that gives me access from every computer in my house (or over the internet via secure VLAN) to my emails (with authorization obviously). Mails must be stored on the server and be aggregated from various different mail addresses according to rules. Also i want to decide a folder structure for my global inbox. Essentially a remote Thunderbird (which i currently use).


Ages ago my father used to have such a setup on his notebook when he worked for a big organization: he could dial up the intranet from everywhere and the ancient Outlook (can't remember what version, we are talking mid 1990) would load the folder structure as it was saved on the server with every email in their place. No local storing.
I don't know what kind of technology was that. Is it replicable?

Was it microsoft proprietary?

I am open to suggestions of any kind.

---

### Post by Lars Noodén on 2009-10-14
> **erupter said:**
> 
-NAS

Samba or WebDAV+SSL or FUSE+SSHfs are going to be your easiest options.  

> **erupter said:**
> 
-RAID 


mdadm supports many different RAID levels.  Put the drives in, assign RAID partions, assemble the partitions into a RAID array, optionally repeat for RAID 10 or 50 or 5x5, create regular file system.  Here is one example:
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

> **erupter said:**
> 
-DLNA


??  Streaming?
> **erupter said:**
> 
-advanced mail server ...


Your longer description is met by basically any IMAP client.  Thunderbird does that.  So does mulberry.  If you want webmail, then there is roundcube.

---

### Post by erupter on 2009-10-14
> **Lars Noodén said:**
>  Your longer description is met by basically any IMAP client.  Thunderbird does that.  So does mulberry.  If you want webmail, then there is roundcube.

 Ok but i need the server side. As i said i want to be able to access all the emails from every computer. As of now i have my personal computer with Thunderbird that manually checks every email account. No automatic save. I want my server to automatically download all the emails, check them, and make the whole folder tree available from every computer. As i've seen it i think it's possibile, but i don't know the server app to do it. It has to be some kind of email aggregator.

---

### Post by Lars Noodén on 2009-10-14
> **erupter said:**
> Ok but i need the server side. As i said i want to be able to access all the emails from every computer. As of now i have my personal computer with Thunderbird that manually checks every email account. No automatic save. I want my server to automatically download all the emails, check them, and make the whole folder tree available from every computer. As i've seen it i think it's possibile, but i don't know the server app to do it. It has to be some kind of email aggregator.


What do you mean by 'automatic save' and how should the server (as opposed to you) 'check' the mails?  

By aggregation, do you mean all mail from separate accounts funneled into a single mailbox / account?  Fetchmail is sometimes used to aggregate mail, but I prefer to leave things in the various accounts and access them seamlessly via an IMAP client.

---

### Post by erupter on 2009-10-14
> **Lars Noodén said:**
> What do you mean by 'automatic save' and how should the server (as opposed to you) 'check' the mails?  

By aggregation, do you mean all mail from separate accounts funneled into a single mailbox / account?  Fetchmail is sometimes used to aggregate mail, but I prefer to leave things in the various accounts and access them seamlessly via an IMAP client.

 The server should do it the same way i do but on schedule. Just like thunderbird, if left open, can do an auto check every n minutes. The fact you have your preferences that are different from mine is not essential right now :P I currently already put mails from different addresses in one big account, differentiated with various rules. The main point is that all these emails, once downloaded, are not accessible anymore from the web. And even if they are (and that would mean no mail cancellation from servers), they are spanned on a number of different servers, with different logins, all requiring a manual visit to a different webmail. So for me it would be best to have something that does what i said. Is it possible?

---

### Post by undecim on 2009-10-14
Could you elaborate on what you mean by DLNA? I'm not familiar with that acronym.

For your mail server, you should start by looking at the Ubuntu Server Guide on email services: [https://help.ubuntu.com/9.04/serverguide/C/email-services.html](https://help.ubuntu.com/9.04/serverguide/C/email-services.html)

What you are looking for may be documented there.

---

### Post by erupter on 2009-10-14
> **undecim said:**
> Could you elaborate on what you mean by DLNA? I'm not familiar with that acronym.


 A search on google yelds this result [http://en.wikipedia.org/wiki/Digital_Living_Network_Alliance](http://en.wikipedia.org/wiki/Digital_Living_Network_Alliance) In simple terms it's a(nother) streaming standard. Made for consumer appliances like dvd players/recorders, bluray players, home theaters, home stereo, etc. PS3 as well as Xbox360 are both DLNA compatible. If you have a DLNA server on your network, every DLNA client can (thoretically) stream content from that server without manual setup. Differentiating between media type, accessing libraries, and so on.

---

### Post by undecim on 2009-10-15
Well, I've never used it myself, but you should take a look at elisa (which is already in the Ubuntu repositories). It claims it interfaces with DNLA devices, but I'm not sure which DNLA category it falls under.

Wikipedia also lists TVMOBiLi as a cross-platform DMS, so take a look at that: [http://www.tvmobili.com/](http://www.tvmobili.com/)

---

### Post by kpholmes on 2009-10-15
i dont have much advice for you, other then getting a ubuntu server book, which i picked up at my local microcenter for around 40 bucks, has almost about everything you need to know in there, and most importantly keeping you server safe. but look at my sig, its the home server super thread!

also with the DNLA, what do you want to stream to?

---

### Post by Lars Noodén on 2009-10-15
> **erupter said:**
> ...they are spanned on a number of different servers, with different logins, all requiring a manual visit to a different webmail. So for me it would be best to have something that does what i said. Is it possible?

Use an IMAP client. 

Thunderbird, for example, will check your mail automatically at intervals you set, and leave it all on the server if you so wish.  Just like any other IMAP mail client.  

If you are hell-bent on having a server aggregate for you, then you could cobble something together with the MTA of your choice (e.g. postfix), and maybe fetchmail or procmail.

---

### Post by Despot on 2009-10-16
For serving DLNA content, the best option seems to be Coherence: [http://coherence.beebits.net/](http://coherence.beebits.net/)

For playback on Linux, there's Elisa (now called Moovida, I believe)

---

### Post by erupter on 2009-10-16
> **Lars Noodén said:**
> Use an IMAP client. 

Thunderbird, for example, will check your mail automatically at intervals you set, and leave it all on the server if you so wish.  Just like any other IMAP mail client.  


 Many accounts i can access by webmail only, or http tunneling addons. (like freepops or webmail extension for thunderbird). As far as i know this does not allow IMAP. 
So i'm stuck with my proposal. Mail aggregation with IMAP server running locally.
I'm reading fecthmail, procmail and postfix docs. This is what i gathered
postfix is a sender, an smtp local server?
fetchmail is a retriever... some kind of "no-gui-mail-agent"?
procmail is a... what? looks like it's some kind of filtering software that acts upon mails stored as files on a file system.
Is this right?

---

### Post by Lars Noodén on 2009-10-18
> **erupter said:**
> 
fetchmail is a retriever... 
procmail is a... what? 

Fetchmail
[LIST]
[*][fetchmail(1)](http://linux.die.net/man/1/fetchmail)
[*][Fetchmail web site](http://fetchmail.berlios.de/)
[/LIST]

Procmail
[LIST]
[*][procmail(1)](http://linux.die.net/man/1/procmail)
[*][Procmail web site](http://www.procmail.org/)
[/LIST]

Look around also for other types of 'milter'
If you know what kind of defective software the mail hosting sites are running, you might find screen scrapers for them.

---

