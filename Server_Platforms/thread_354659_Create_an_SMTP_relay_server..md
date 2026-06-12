---
title: "Create an SMTP relay server."
date: 2007-02-06
forum: Server Platforms
---

### Post by aberry5555 on 2007-02-06
Hi, I have a problem that I want to be able to fix with Ubuntu.

Our ISP provides us with an SMTP server but, recently, it keeps on going wrong and our clients are starting to get upset with having email on two or three days a week :S. Our current work-around is to use our Windows 2003 exchange server to relay SMTP connections for our clients, but this server is over-loaded enough and we want to be able to restart our internal systems without doing anything to our clients. 

I use Ubuntu for a few different things, we use BIND on two and I'm in the process of setting up a LAMP server with it on another, but I have a spare old machine and I want to be able to set it up as a simple, stand-alone SMTP relay machine, for fail-safe purposes.

Does anyone know what sort of program I should use for this? I have read a couple of threads but, since I know very little about Linux E-mail servers it's a bit confusing trying to figure out which program does what :S. All I need to be able to do is to add certain domain names to an accepted list and pass them through with some simple security, and maybe use it later on to host POP3 accounts and such but I will ignore that for the minute as it isn't important.

Can anyone point me in the right direction, remember I'm fairly new to the concept of how these things work precisely?

Thanks

---

### Post by kidders on 2007-02-06
Hi there,

Personally, I would opt for postfix ... although it's by no means your only option.

Postfix is well trusted, flexible and well capable of handling mail on an industrial scale. Plugging virus scanners, spam filters, etc. into it is also quite easy, and *extremely* well documented on the web.

My recommendation is just one person's opinion though ... you should definitely take a look around, and see how some other alternatives compare to Postfix, in terms of your own specific requirements.

Once you're set up (and you've tested your mail gateway _thoughrally_), you can update your DNS to include an MX record for it.

---

### Post by MJN on 2007-02-06
I agree that Postfix would handle the job nicely.

However, to avoid further confusion, no MX records would be required - after all this MTA would not be hosting any e-mail domains at all but merely allowing clients to connect to send mail.

Needless to say, some form of authentication would be essential given the potential for it to be abused my spammers (so-called open relay).

However, given you're presumably paying for your ISP's service can you not get them to sort their problem out? Keeping an outgoing mail server up 24/7 is really not that difficult (certainly relative to the rest of the services they provide).

Mathew

---

### Post by tturrisi on 2007-02-06
For such a system I would just install Debian Sarge minimal base system and Exim4 + dependencies, no need for anything else.  Rock solid, boot it up, make your configs and never have to touch the box again for at least a year or more.

---

### Post by aberry5555 on 2007-02-07
we have our own mail server and our clients have their own servers, too, however it's the relay betweent their email clients and the server that's the problem :S . and, on trying to get them to fix it, believe me I've tried, I've asked them three times a day for the past week or two and the best they can come up with is "we're looking in to it but you should have had a backup" :mad: ! I will definately try postfix then, does anyone know of a good site with a walk-through on installing it, maybe on the forum somewhere? I'll look myself, obviously, but I may overlook it :p

---

