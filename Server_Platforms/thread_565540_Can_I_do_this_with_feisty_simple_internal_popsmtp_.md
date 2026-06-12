---
title: "Can I do this with feisty: simple internal pop/smtp server with string based box sort"
date: 2007-10-02
forum: Server Platforms
---

### Post by ofm on 2007-10-02
First off, apologies if this is in the wrong forum, I looked at the "before you post thread", and this doesn't really seem like a HOWTO, nor did I see another sub-forum that looked more fitting.

Also, I have searched around and seen some stuff for how to set up mail servers in general, but not matching what I want.  I'm fairly new to linux, but familiar with computers in general & pretty familiar with Windows junk in specific.

Here's my problem:

I need a mail server separate from our current one to do two simple  (to describe at least) things:

1. Receive emails sent from a simple Windows based SMTP program (CSSMTP), and store ALL messages with the string *gwrfaxapi* in the TO: line in the same mailbox (all other messages can be trashed).  The TO: line will be in a format similar to this: **gwrfaxapi.{8001234567/John Smith}**

2. Allow POP access to the aforementioned mailbox, and extraction of the messages with the TO: line unmodified.

I've tried a number of free/shareware mail solutions for Windows, but couldn't get #1 to work (not saying they wouldn't work, I just couldn't get them to work)  - they all seemed to an individual email address created for each user.  This won't be possible, because it's a specially formatted string for a fax application (don't ask why the app can't just be it's own SMTP server...would be much easier that way) to use as a fax to address. 

So, I need something that can do some pre-processing on emails before it tries to sort them, and that won't reject an email message just because an address doesn't match an existing user.

Also, I don't/won't/can't have a domain registered and set up for this server - we don't want it accessible from the outside world anyway, so this would all have to work via IP addresses. 

Thanks for taking the time to read, and if anyone knows how/if this can be done with Feisty (or an older distro), please let me know.

---

### Post by kidders on 2007-10-03
Hi there,

My instinct would be to use Postfix & Procmail. They're both highly scalable, and are a pretty standard combination, so you should have no difficulty finding documentation & howtos ... which is pretty important.

Whether an SMTP server only accepts mails destined for local users is down to how you configure it ... any decent server will give you complete control over what gets rejected. For example, you will presumably want to reject all mail that doesn't come from your Windows box. Strictly speaking, I imagine Postfix could handle the functionality you've described on its own, without any help from Procmail. Exactly what apps you'll want to use depends on the specifics of how you go about setting up your server. Procmail is useful for post-processing mail.

POP isn't something I use very often, so I have limited knowledge of what apps are better than others.  I imagine most people will go with what they know ... I would probably choose Courier these days, but more out of a sense of familiarity than a belief that it's any better than the alternatives.

Anyhow, I hope that's of some help.

One additional option, I suppose, would be to write an SMTP-style server of your own. SMTP servers are complicated animals, and it sounds as though all you'd want yours to do is accept mail and dump it, unmodified, into a directory for later retrieval over POP. Depending on the size of your operation, a short script may be a perfectly sufficient substitute for a bulky & complex set of server apps.

---

### Post by ofm on 2007-10-03
Thanks kidders.  After much digging yesterday I was sort of suspecting some of the solution lay in postfix.  I

I've found a few howtos, mostly merging postfix, courier & other stuff I may or may not need.  I keep trying to get a Feisty VM set up (inside feisty!) so I  can test without messing anything up horribly.  Amazing how one project always requires another.

Off to find something on procmail!

---

### Post by kidders on 2007-10-03
> **ofm said:**
> I keep trying to get a Feisty VM set up (inside feisty!) so I  can test without messing anything up horribly.If you've decided to go with Postfix, there's no need to be too bothered about messing up. Its configuration files, which are the only things you should play with, live in /etc, as you would expect. Provided your local network is trusted, there's only so much damage you can do with a misbehaving SMTP server!

Some (possibly obvious) Postfix-specific advice ...
[LIST]
[*]Don't bind it to an externally accessible network interface.
[*]Try to keep main.cf as small as possible ... it can easily get very bloated! Removing unnecessary comments and restatements of default behaviour can make things way easier to follow.
[*]Avoid so-called "permanent failure" conditions, until you're reasonably sure your server is behaving itself. If a misconfiguration causes your server to reject mail it should be accepting, it's generally better if the reject condition is in the 400s, rather than the 500s.
[*]When tinkering with Postfix, I very often leave a **tail -n0 -f /var/log/mail.log** running in a terminal window, so I can keep an eye on what it's doing. Postfix's logs are very helpful.[/LIST]As you mention, Postfix & Courier is a well-trusted combination. Incidentally, is your local network trustworthy?

---

### Post by ofm on 2007-10-04
I was/am more concerned with just messing the machine itself up (not the network) and having to redo the machine from scratch.  I wound up not being able to get the graphic ubuntu (gnome) workstation version working in vmare, so I gave up and got Debian etch running instead...was messing with that for a while, then decided it was easier to use the VNC built into ubuntu than cludge around with getting it working in Etch (although I did, mostly).

SO, now I'm back in Ubuntu, have got postfix installed, and am just mucking around trying to get stuff figured out.  I like how I have to dig around to find the main.cf file, that was fun ;).

I've found many postfix howtos, but so far they all involve postfix+something else, often sql, webmail, etc. I'm working through some of them, trying to avoid all that other stuff, and it's definitely challenging.

If anyone knows of a simple postfix by itself (yes I checked postfix.org) or postfix + procmail on Ubuntu howto floating around, I'd appreciate it.

I'd say our network is trustworthy - it's a medium sized business network, and we haven't had a single virus/trojan/spyware infection/etc. in the last 2 years at least (not bad for a primarily Windows based office).

The nic/ip is definitely not accessible from an outside source, only the local subnets. 

Thanks for the help so far :).

---

### Post by kidders on 2007-10-04
> **ofm said:**
> I'd say our network is trustworthy - it's a medium sized business network, and we haven't had a single virus/trojan/spyware infection/etc. in the last 2 years at least (not bad for a primarily Windows based office).

The nic/ip is definitely not accessible from an outside source, only the local subnets. 

Thanks for the help so far.No worries. :-) I was more concerned about whether it's a good idea to be sending data to/from your mail server unencrypted. Depending on what's in the mails, who uses your network, and whether wireless access is available, for example, there could be privacy issues.

Anyhow, Postfix per se doesn't need much configuration. It works (in some fashion at least!) out of the box, so all you should need to do is take a look at the documentation for main.cf, to learn about some of the configuration options. I find this a useful resource ... [http://www.postfix.org/postconf.5.html](http://www.postfix.org/postconf.5.html)

---

### Post by ofm on 2007-10-04
I think I've got postfix setup ok (I can echo "Hello world" | mail -s subject <emailadd>@<domain> and it works), but I can't seem to get pop working.

I tried Dovecot at first, and eventually gave up (I got it working for checking mail, but it wouldn't send, and kept kicking out an error that I couldn't track down).  Currently I'm working on Courier, which seems simpler, but stuck getting on the following error (from /var/log/mail.log).

>  courierpop3login: chdir MailDir: No such file or directory.

I try to log in with a simple telnet, it accepts the username then either tells me the password is wrong, or kicks me after I put in the correct password.

I tried > postconf -e 'home_mailbox = Maildir/' as I saw suggested in some of the howtos, then restarted, but it didn't seem to affect anything.

Currently I'm trying to find the right syntax to tell courier that instead of "MAILDIRPATH=Maildir" I want it to access whatever procmail is using.  There is no "home_mailbox" line in my main.cf, and my mailbox_command line is > mailbox_command = procmail -a "$EXTENSION"

It's kind of funny - 99% of the howtos I find are for hardcore postfix+ssl+dovecot/courier+spam filtering+virtual users+blah blah stuff, but I haven't found a single thing for just simple, basic postfix + pop3.  I suspect this has something to do with how google/etc. index pages these days  - it's harder and harder to find "old" web pages via a search engine.

---

### Post by kidders on 2007-10-05
> **ofm said:**
> It's kind of funny - 99% of the howtos I find are for hardcore postfix+ssl+dovecot/courier+spam filtering+virtual users+blah blah stuff, but I haven't found a single thing for just simple, basic postfix + pop3. I suspect this has something to do with how google/etc. index pages these days - it's harder and harder to find "old" web pages via a search engine.Yeah, Google can be irritating! I'd have thought you'd be able to find *one* howto that's reasonably close to what you want. How frustrating. :-(

Here's roughly what I would do ...

[B]- I -
[/B]Configure Postfix & Courier-POP any way I could, so they at least do *something* ... which might as well be per-user mailboxes, based on your local accounts. Most mail software will naturally "want" to work that way.

[B]- II -
[/B]There are loads of possible roads to go down from here. One option would be to take a look at a howto that mentions "virtual mailboxes". These are normally meant to be used to host multiple mail domains & thousands (or millions) of users, none of whom have local user accounts on your box.

Virtual mailboxes are stored in a central location (ie not in users' home directories), and all have the same permissions ... which would be perfect for you ... except you'll only want one of them.

[B]- III -
[/B] Then, I would work on limiting what Postfix can & can't accept. To start with, you might want to set up an appropriate smtpd_client_restrictions directive, so your server will reject mail outright if it doesn't come from the computer running your relay application. You may also want to reject mail with a "To" address that doesn't conform to the pattern you mentioned in your o/p. How does "/gwrfaxapi\.\{\d{4,}\/.+\}/" grab you?

[B]- IV -
[/B]What I'm working towards is a mail server on which all users have exactly the same mailbox. At least to start with, you'll only need one user though ... and it should be a virtual user ... ie allowing him to check his mail should not involve creating a unix account for him.

An alternative way of doing things would be to retain your per-user mailboxes for future use, and force Postfix to disregard "To" addresses that look like your gwrfaxapi pattern & deliver matching mail to a particular user.

[B]- V -
[/B] Next, since this is for use in a commercial setting, I would give serious consideration to encrypting all the connections. Were some sort of privacy-related incident to arise, it would look bad (to say the least!) if all your messages & passwords were bouncing around your network in plain text, for everyone to see.

The only problem is likely to be whether your relay application can handle secure SMTP. I suspect it may not know how, in which case, you'd need to set up a secure tunnel to your SMTP server, like this...[LIST=1]
[*]Configure your relay app to send mail to itself (ie "localhost") on whatever port you designate.
[*]Use SSH to forward that port to port 25 (or again, whatever you've chosen) on your Postfix server.
[*]Reconfigure Postfix to accept mail only from itself, ie not from your relay application.
[*]Restart all services you altered.[/LIST]Presumably, anyone who wants to check the mailbox can use secure POP, so there won't be a problem there.


> **ofm said:**
> courierpop3login: chdir MailDir: No such file or directory.Looks like your Postfix & Courier aren't on the same wavelength. They're each expecting your user mailboxes to be in different places. Postfix can create missing maildirs, but Courier doesn't like to, which is the reason for the error. There is no way to tell Courier to use "whatever something else is using", if you know what I mean. The simplest thing to do is to set Postfix (or Procmail) and Courier up independently ... your maildir locations will never really need to be changed, anyway.

---

### Post by ofm on 2007-10-08
Thanks so much for all that info, I'm going to give that a try again tomorrow & will post back after I see how far I can make it.

Spent the last few days getting a vm image working as per [this]("http://www.howtoforge.com/perfect_setup_ubuntu704") tutorial, and then getting ISPConfig working over that, which would supposedly make all this easy to setup ;).

Not, now I'm even more paranoid about messing with stuff in the command line...so off to archives goes that image for later use & back to the basics as you suggested.

Luckily,there's nothing confidential in the messages being sent, nor are any passwords required (doesn't take a real user name or password to use SMTP/relay I guess), so I'm not too worried.  Anyone already inside our network is going to find much more interesting things than my fax traffic.

[edit: 

OK, I'm getting closer. I've got postfix working, routed, and receiving emails from other machines.
Now I'm trying to get the re-routing working.
I think I found the first step, by using ```
local_recipient_maps = 
``` in main.cf, I have disabled outright rejections for "bad" addresses.
I've tried using both ```
virtual_alias_maps = regexp:/etc/postfix/<FILENAME>
``` and ```
header_checks = regexp:/etc/postfix/header_checks
``` with lines in both that are pretty basic regexps: ```
/.*fax=.*/ fax[code]  and it IS re-routing (*header_checks doesn't work, virtual_alias_maps does*)  The problem is that it replaces the to field with **"undisclosed-recipients:;"** and I need that To: to remain untouched.

Once I get that fixed, onward to POP (again)!
[/edit]
[edit2:
...header_checks doesn't work at least partially because I didn't understand it :). - a proper line would have been like [code]/.*fax=.*/ REDIRECT fax
``` where "fax" is the target username.  This does work with a "WARN whatever text" instead of a REDIRECT, but REDIRECT still fails.  I'm guessing it gets processed after the actual address checking.
[/endedit2]
[edit3:]
I've now also tried smtpd_client_restrictions = check_client_access regexp:/etc/postfix/access with the following in access ```
/.*fax=.*/ REDIRECT fax
```.  That doesn't appear to be doing anything, so I must be missing something.  Oh well, enough for today, maybe fresh eyes tomorrow will help
[/endedit3]
[edit4:10/11/07]
OK, I've narrowed the problem down to procmail.
It is somehow stripping the To: header and replacing it with "undisclosed recipients:;"
[/endedit4]

---

