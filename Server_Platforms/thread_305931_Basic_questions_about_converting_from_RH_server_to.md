---
title: "Basic questions about converting from RH server to Ubuntu based"
date: 2006-11-24
forum: Server Platforms
---

### Post by EmmAytch on 2006-11-24
I almost feel like putting this in the newbie section, but I am struggling with setting up an Ubuntu mail / web server.

Funny thing is I've been doing Red Hat based stuff for so long that I am too comfortable at just getting on and doing it. I use Ubuntu on the desktop all the time and have set up an Ubuntu LAMP (pre Ubuntu server disks) which works fine.

BUT, I am really strugling due to the differences between RH and Ubuntu. I want to move all the servers I am responsible for to 6.06 LTS, but am not making much headway.

In RH I use:
sendmail
squid
imapd
fetchmail
plus all other nec tools

I want to have a similar system with some antispam (spamassassin) type features.

Squid and fetchmail are OK, but no imapd and lots of MTA's, not just sendmail. I can see uw-imapd which is the debundled imapd (I think).

What do people suggest?

I want the shortest learning curve possible, but am happy to change MTA and imap daemon. As long as spamassassin can do server-wide rules so that identified spam gets sent to a global mailbox - rather than each individual's account.

Lot's of questions here, but how do you turn on services? In RH I have a services tool. In Ubuntu, there's a tool but it only shows fetchmail - none of the others.  I am using a full  x/gnome install rather than console based server install.

Been banging my head all day on this one and was about to go to CentOS or something RH based, but thought I'd keep trying.  I posted this on linuxquestions Ubuntu forum, but it seems a little quiet!

---

### Post by MJN on 2006-11-24
Do keep trying - I did the very same move a year or so ago and have not looked back!
 
To start to address your specific queries, I would recommend postfix for your MTA and Dovecot for IMAP. I had Postfix and uw-imap running on Red Hat and was never particularly happy/comfortable with uw-imap... Difficult to configure and, above, all, used the mbox method/format of storing messages as opposed to the much safe/simpler/better (IMHO) maildir supported by Dovecot. Note that this move required converting everybody's mailbox - the thought of which scared the pants off me but it was actually very easy... I have a few scripts here that can handle it.
 
With regards to starting/stopping services, most can be controlled with /etc/init.d/<service> start|stop|restart etc - I thought RH did something similar (but can't remember and I was nowhere near as much 'into it' as I am now).
 
Is your server in a live production environment? Or is it more for your own use? I'm just asking because a transition like this will inevitable involved some downtime/troubleshooting and the last thing you want is the pressure of other people/requirements on your back. In my case, it was somewhere inbetween - I host various websites and mailboxes for friends/family so whilst they were applying no pressure at all I still felt an obligation to keep things quick and smooth.
 
Mathew

---

### Post by EmmAytch on 2006-11-24
Thanks for the reply.  It is a production server, and I am on it as I type this, but the old RH server is still in operation.  I was hoping to swap it over on Wednesday evening, giving me 3 working days to sort things out.

I am quite happy to tell evey user to clear their imap boxes and store emails locally, which would make the transfer better.

Did you implement any spam filter or antivirus features?

As for the /etc/init.d - yes RH more or less follows the same thing but the have (or had) a really good gui for setting it all up.  There's probably something in Ubuntu if I knew what it was called!

I will now go and read up on dovecote.  I take it the difference is that I do not need to create user accounts on the server for mail.  That would make me happier!

Thanks again - expect a few more questions to come!

Maz

---

### Post by MJN on 2006-11-24
If other's are relying on you (and your server) then I'd suggest getting to grips with the new server apps (Postfix, Dovecot etc) on a different machine rather than fighting the inevitable difficulties in real time!
 
For anti-spam I am currently just using the Postgrey greylisting tool and a number of RBLs - it's working very well stopping several hundred a day and allowing perhaps 1 or 2 through. I intend to implement Spamassassin someday but the 'problem' isn't big enough at the moment to increase this as a priority.
 
I personally do have a system account for all my users as most of them need one anyway. To implement mail accounts is certainly possible however you'd need to read the relevent documentation etc to sort this out.
 
Mathew

---

### Post by EmmAytch on 2006-11-24
Hi

The "new" server is not connected to the LAN, so I can keep going at my own pace thankfully.

I have now installed postfix and dovecot.  Am following the docs

---

### Post by EmmAytch on 2006-11-24
Just answered a silly question so removed it from the above post!

---

### Post by EmmAytch on 2006-11-24
Where did you set your imap mailboxes.  By default it looks like they are in /home/username, but in RH they used to reside on /var/mail (or /var/spool/mail).  

Not sure which is best.

---

### Post by MJN on 2006-11-24
I set mine in ~/Maildir/ as you say, however that's fine in my case because all users have a system account.
 
You can put them whereever you like - you just need to ensure Postfix drops the mail in the right place and Dovecot can pick it up again.
 
I'm quite happy where they are as it maintains the 'all user data is in /home' concept (all websites are served from here too as opposed to the 'default' /var/www) thus simplifying backups etc. I don't think it really matters at the end of the day.
 
Mathew

---

### Post by EmmAytch on 2006-11-24
Thanks again.  I now have squid up and running and serving pages OK.  One major step complete.  All my acl rules work, so I'm happy with that.

I'm curious as to why yours are in a sub directory in the user's home - and more to the point, how easy is it to get potfix and dovecot to look elsewhere?

I think I know what I'll be doing over the weekend!!!  Thanks for the help and encouragement.  I want the long term support aspect of 6.06 and I am really happy with it on the desktop and have been since hoary.

---

### Post by MJN on 2006-11-24
They're in a sub-directory because I wanted them there! I believe it also may be convention to use Maildir/ too.. (and it does make sense - then only the one parent folder to shift around if need be)

As for telling Postfix and Dovecot where the mail is, this is done with the directives **home_mailbox** (see [http://www.postfix.org/postconf.5.html#home_mailbox](http://www.postfix.org/postconf.5.html#home_mailbox)) and **default_mail_env** (superced by the use of **mail_location** according to [http://wiki.dovecot.org/MailLocation)]("http://wiki.dovecot.org/MailLocation%29").

Reading that last URL it's clear now why it's the convention to use the users' home directory (so it can have multiple mailboxes which IMAP supports, unlike POP) and a sub-directory of it (because mbox format would otherwise list all the users' files/directories as messages/folders).

Mathew

---

### Post by EmmAytch on 2006-11-26
Well, what a polava!

Thank you for your help but after an entire weekend working well into the early hours, I have given up.  Shame as I REALLY do like Ubuntu and have "spread the word" about it since I first started using it with hoary.

But, IMO  as a server it is just too tricky and in my (little) experience flaky. I could not get postfix to work, so removed it and tried both sendmail and exim.  They were worse - even though I am used to sendmail.  Finally I went back to postfix, got it working and then got amavis-new with spamassassin and clamav working.  Except it didn't!  I have managed to filter either a spam or virus, but not both.  clamd flips out and then it just fails to do much.  

As for dovecot, it didn't either!  Got rid of that and went for ipopd (this server needed pop not imap) - but that didn't work either.  So, two different PC's, both fresh installs of 6.06 and both by far the hardest setting up I have ever done.

On a better note, I did get squid and dansguardian working!

Perhaps my skills are not as good as I thought.  Baring in mind the first server I set up was a RH5.1 - that was hard but it got much easier with 7.1 onwards.  I couldn't get a stable ubuntu server working  and my skills were not sufficient to establish the causes of why things were not working or only working intermitantly.

I still think Ubuntu on the desktop is the right choice - that's all I use (with the occasional Puppy Linux for those non-linux PC moments).

I did see a post with someone suggesting meta packages - a bit like easyubuntu - for web, mail and server type installations.

That would be a great idea.  Just get easymailserver (or whatever) and off you go, all you need to do is set up your local variables.

Until that day, I am back on RH - albeit CentOS.  I didn't want to but I simply haven't got unlimited time to make it work when something else will work almost out of the box.

Finally, after my tale of woe, I just wanted to thank you for your help.  I was encouraged by it, but I simply couldn't crack this one.

---

### Post by MJN on 2006-11-26
What a shame!

I've found Ubuntu to be the easiest distribution ever to set up, although granted to a greater or lesser extent that's comparing a newer distro with older ones.

I'm surprised Dovecot didn't cut it for you - it usually runs straight out of the box for most people... indeed I don't think I've changed the config file from the original.

Choice of distribution aside, I would well advise you to tackle one issue at a time - attempted to build Rome in a day will never work. As for installing meta-packages with 'everything you've ever wanted' installed I think don't agree that's a good idea - it's like the HowTo's covering every-topic-and-then-some -  if you follow them blindly you learn nothing... Which is fine until something goes wrong then you're up sh1t creek without a canoe, nevermind a paddle. This approach may suffice for dabbling at home but it'd be unacceptable in a professional capacity (I'm assuming that's where you're coming from given the mention of 'users').

Can we not tempt you back? Remember, Ubuntu is the future... ;)

Mathew

---

### Post by EmmAytch on 2006-11-26
I will be back - but time is my big enemy now.  I won't move from ubuntu on the desktop (unless something much better comes along) but I just need to get things kind of future-proofed quickly - and that means replacing some of the servers I built a while ago.  One of them is RH7.3 - which works fine but along with other RH9 servers, all the critical updates are coming to an end in December.

I have to admit, I couldn't work out what the hell was going on with the flakey setup.  If I had time I would get to the bottom of it and fathom out the problem - God knows I've had to do that enough in the past, but now I just need something that works.  I am a (reasonable) techy - but I also run a small business so I don't have the time to get too dirty any more.  This is a shame because I enjoy it and find it challenging - but then I have to eat and pay wages!

I think the meta package issue is fair comment - but that would have really helped me if it would have been available.  Sometimes quick and working is what is needed - and also I worry that we can put off new users if we make it an arcane art to build a server.  If the NT or Server 2003 admin decided to try linux and couldn't easily get it working, would they persist?   Whereas if it worked almost out of the box would they start to look under the bonnet?  

Thanks again for the help - and yes, I will be trying again at some point in the near future! (and as you said, ubuntu is the future!)

---

