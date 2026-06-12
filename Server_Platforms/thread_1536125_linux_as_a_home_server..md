---
title: "linux as a home server."
date: 2010-07-21
forum: Server Platforms
---

### Post by wigg on 2010-07-21
I'm looking for some suggestions.  I have used ubuntu and debian before it to operate as a server in my house.  I'm currently running 10.04 headless for media tomb for media hosting, LAMP, torrent flux, samba share, and squid to strip the headers of packets on my ps3.  I also have xming on my XP box so that I can SSH programs when rather than use a remote desktop.  I was wondering if anyone had fancy suggestions so that I can make even more use out of this incredibly powerful os.  I love *nix OSes and wish they where more viable as a desktop.  I love gaming and electronic music sequencers and Linux doesn't do that well enough.  So to be clear, I'm looking for some inventive suggestions on taking full advantage of linux as a personal server.

---

### Post by lisati on 2010-07-21
Moved to "[Server Platforms]("http://ubuntuforums.org/forumdisplay.php?f=339")"

I use my main desktop machine as a basic server system which hosts a web site or two and hosts an email server. 

One of the main advantages I've found with running my own email server is that there are more options available for safely dealing with spam than are commonly available with regular email clients such as Evolution and Thunderbird. For example, a spam comes in and I decide to fire off a "nastygram" or some such message saying "go away!" With an email client, we need to do our homework before clicking on "reply": to put it simply, we can't trust the "From" or "Reply to" information contained in an email. Blindly replying to a message could result in an innocent third party being extremely annoyed about your message sent in response to something they didn't send. However, with an email server, one of the options is to arrange for the message to be checked while it's arriving, and, if certain criteria are met, your server can say, in effect, "Go away, I'm not accepting that rubbish!", and you are freed from having to deal with it.

---

### Post by Iowan on 2010-07-21
I run DNSMasq as DHCP/DNS server. 
Check the [Server Guide]("https://help.ubuntu.com/10.04/serverguide/C/index.html") for some more ideas.

---

### Post by CharlesA on 2010-07-21
I'm just running Samba, SMTP and SSH on my server for the moment.

DHCP/DNS are handled by the router.

---

### Post by wigg on 2010-07-21
> **Iowan said:**
> I run DNSMasq as DHCP/DNS server. 
Check the [Server Guide]("https://help.ubuntu.com/10.04/serverguide/C/index.html") for some more ideas.

I have a question about DNSMasq.

Does it allow you to DNS a dynamic IP from a cable company?  I'm thinking of the no-ip program from no-ip.com.  Because that would actually be really nifty to get register a domain.

---

### Post by CharlesA on 2010-07-21
> **wigg said:**
> I have a question about DNSMasq.

Does it allow you to DNS a dynamic IP from a cable company?  I'm thinking of the no-ip program from no-ip.com.  Because that would actually be really nifty to get register a domain.

You'd have to do that separately as far as I know. DNSMasq only does lookups.

There is **ddclient** in the repos that you can install.

---

### Post by Sporkman on 2010-07-22
You could look into:

[Subsonic]("http://www.subsonic.org/pages/index.jsp") for music streaming,

[Gallery]("http://gallery.menalto.com/") for photo & video hosting,

Automated backups,

Virtual machine hosting,

etc.

---

### Post by Iowan on 2010-07-22
> **wigg said:**
> I have a question about DNSMasq. DNSMasq is more a local DNS - at least the way I use it. I can ping other DHCP client machines by name (if they've used **send hostname** in */etc/dhcp3/dhclient.conf*).

---

### Post by drdos2006 on 2010-07-22
I found this how-to very informative....
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

### Post by TwiceOver on 2010-07-23
If you have a couple systems in your house, check out BackupPC also.

---

### Post by johnycage on 2010-07-24
Question: if you use headless server, there's no need of GUI, which OS you've installed on that server? Home edition or server edition?

btw, You can add backup utility & schedule backups at regular intervals.

---

### Post by metalf8801 on 2010-07-24
> **Sporkman said:**
> You could look into:

[Subsonic]("http://www.subsonic.org/pages/index.jsp") for music streaming,

[Gallery]("http://gallery.menalto.com/") for photo & video hosting,

Automated backups,

Virtual machine hosting,

etc.

What software are you using for Automated backups?

---

### Post by CharlesA on 2010-07-24
> **metalf8801 said:**
> What software are you using for Automated backups?
I use an rsync script running in a cronjob that syncs data to an external drive.

There are probably easier ways of doing it, but that's what works for me. :)

---

### Post by Sporkman on 2010-07-24
> **metalf8801 said:**
> What software are you using for Automated backups?

I have a script that does it via rsync, though I invoke in manually, not as a cron job.

---

### Post by arrrghhh on 2010-07-24
If you want a piece of software to help with backups, Bacula I've heard is good... The others are slipping me currently.

---

### Post by Skadork on 2011-01-10
> **TwiceOver said:**
> If you have a couple systems in your house, check out BackupPC also.


I'll second this.  BackupPC is a very powerful piece of software. I currently have it backup up 7 different computers.  2 computers are backed up over a OpenVPN with roughly 20 GB of data from my parent's office to my server in my basement.  Gotta love a local utility owned Fiber network :D  A single hop from my home to their network and 15+Mbit speeds both ways!  ...never even touches the Internet!

to the OP: you could also check out trying to set up DropBox on your server so you could sync/back up all your files.


Also, I use one ubuntu box as a "hop" box.  Meaning, from the internet, I can't hit any other computer on my network unless I first go through this box.

---

