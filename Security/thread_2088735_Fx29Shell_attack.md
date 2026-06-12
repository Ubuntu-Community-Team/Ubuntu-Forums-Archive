---
title: "Fx29Shell attack"
date: 2012-11-27
forum: Security
---

### Post by cj13579 on 2012-11-27
Hi All, 

Just wanted to ask you all for some advice about what to do about something that I noticed this morning. When checking my emails this morning I noticed that I had 20 or so permanent delivery failures to mails from myself as www-data to another email address saying:

> Boss, there was an injected target on cj13579.dyndns-server.com/blog/wp-admin/css/xml.php?x=ls&d=/var/www/blog/wp-admin/css/.ccs/&sort=0a by 186.73.255.87

I went on my server and looked at this xml.php because i didn't recognise it and saw that it's ownership was different from the other file ownership within this folder. I also noticed that the permissions were much more open than I hoped. xml.php actually turned out to be a binary file and a quick google search shows that Fx29Shell is backdoor shell program for getting entry into systems. From what I can read, it seems as though they wanted to use my box for mail spamming.

My checks to see if they had succeeded were pretty rudenmentary. My server can send mails via the mail command and I use my gmail stuff as the gateway thing. A check of my sent mails showed all of the mails that had delivery folders. I *think* i might has escaped...

I have deleted the xml.php file and closed the permissions on these folders and others in my webserver directory. I also saw that I was running a relatively old version of Apache so I have upgraded this in case they exploited a vunerability in that to get in.

Additionally, I have updated ClamAV and have done a clamscan on the webserver idrectory which came back with no infected files. I am currently running a  scan on the rest of the box to confirm that nothing else is elsewhere.

Apart from these things, I would be interested to get peoples opinions on what else I could do to tighten up security and/or ensure that nothing else on my system is infected. 

I would also be interested to hear if anyone else has come across this issue.

Thanks in advance.

---

### Post by spynappels on 2012-11-27
The box has been owned, I would suggest getting any data off it and re-installing with the most recent versions of Apache etc.

---

### Post by SlugSlug on 2012-11-27
what do you use for the alerts?

---

### Post by cj13579 on 2012-11-27
> **spynappels said:**
> The box has been owned, I would suggest getting any data off it and re-installing with the most recent versions of Apache etc.

Oh, that's rubbish. I was hoping that wasn't going to come. A bit of an update, the full scan finished and only found 1 infected file which was some dodgey .exe that I was keeping in a backup folder for a old Windows box.

> **SlugSlug said:**
> what do you use for the alerts?

I'm not using anything. The message that I posted was the body of an email that was trying to go from my server (as www-data) to another gmail account via mine. I only noticed because I got a load of permanent delivery failures to that address. It doesn't seem to have tried to send anything anywhere else.

---

### Post by CharlesA on 2012-11-27
The general rule when a machine is owned is to wipe it and restore from backups.

You can run all the scans you want, but you still cannot trust that machine completely.

---

### Post by spynappels on 2012-11-27
> **cj13579 said:**
> Oh, that's rubbish. I was hoping that wasn't going to come. A bit of an update, the full scan finished and only found 1 infected file which was some dodgey .exe that I was keeping in a backup folder for a old Windows box.

You did ask for advice, sorry you didn't like it....

As CharlesA said, this is standard practice when a box has been owned, but it's your box, you can do what you like with it.

---

### Post by mr-woof on 2012-11-27
I agree with what has been said above, wipe the server, Have you got any backups?

---

### Post by LiamOS on 2012-11-27
Wipe it clean. It's the only way to be sure.

---

### Post by OpSecShellshock on 2012-11-27
Re-install, make sure that Apache, PHP, and Wordpress are patched and up to date, and reset all passwords.

---

### Post by unspawn on 2012-12-02
- Deleting foreign objects without first saving details (process, open files, network connections, time stamps, ownership, access permissions) is the *best* way to thwart any investigation.
- Given how web stack exploits work a compromise of (usually) the UID the web server runs as *does not automagically make it to a full-blown root compromise*.
- Suggesting a (full-blown root) compromise without actually investigation it is inefficient to say the least (I'll leave the expletives out).
- Restoring from backup without checking contents first or re-installation without investigating first may easily expose the same loophole all over again.

---

### Post by cj13579 on 2012-12-03
> **unspawn said:**
> - Deleting foreign objects without first saving details (process, open files, network connections, time stamps, ownership, access permissions) is the *best* way to thwart any investigation.
Agree with this, and kind of regretted it as soon as I did it. I was just a bit panicked and was being rash. I knew that it would limit what I was able to do and how much help I was able to retreive from others.

> **unspawn said:**
> - Given how web stack exploits work a compromise of (usually) the UID the web server runs as *does not automagically make it to a full-blown root compromise*.
Agree. I have have tightened up the permissions on the webserver directory and only made folders writeable where they need to be. I don't have anything "sensetive" on the server and I am confident that my data is OK.

> **unspawn said:**
> - Suggesting a (full-blown root) compromise without actually investigation it is inefficient to say the least (I'll leave the expletives out).
I don't think I did this. Perhaps I should have put more detail about the entry point. Apologies for any confusion.

> **unspawn said:**
> - Restoring from backup without checking contents first or re-installation without investigating first may easily expose the same loophole all over again.
I agree. I have not yet rebuilt the box (mainly because I don't have the time at the moment) but I have made sure that there are no unknown or dubious looking connections to the box (there was 1) and have patched up Wordpress to latest version (I was running 2.8.4). I will monitor the sitiation for now but so far I have not seen any more of the emails and no unknown connections.

Many thanks to all for all your comment on this. Much appreciated. I will try and make sure that I stay more up-to-date in future!!

---

