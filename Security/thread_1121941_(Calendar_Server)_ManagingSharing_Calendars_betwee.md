---
title: "(Calendar Server) Managing/Sharing Calendars between iCal and Outlook...?"
date: 2009-04-10
forum: Security
---

### Post by michwill on 2009-04-10
Hi All,

I'm looking to set up a reasonably straightforward calendar server on an Intrepid 8.10 server.  My requirements are as follows:

1) Be able to manage content from both iCal and Outlook (mobile would be nice but not required)

2) Be able to control subscriptions/invites via the server.

3) Support multiple calendars per user.

I approached my client about using a combination of Google Apps and whatnot, but they want something 100% in-house.  That said, I'm tasked with coming up with a quality solution.  Would a simple WebDAV setup work for publishing and managing users?  What's the best way to go about it?  Any ideas -- turnkey or otherwise? 

Thanks.

---

### Post by HermanAB on 2009-04-11
Citadel with the Bynari Connector for Outlook:
[http://www.citadel.org](http://www.citadel.org)

[http://aeronetworks.ca/citadel-howto.html](http://aeronetworks.ca/citadel-howto.html)
[http://aeronetworks.ca/citadel-clients.html](http://aeronetworks.ca/citadel-clients.html)

---

### Post by michwill on 2009-04-12
Thanks for that post.  I'm actually going with WebCalendar (unless Citadel simply provides easier access to the things I need).  I took a look at Citadel as well, and it seems a bit oversimplified while not providing obvious access to multiple calendars or access control.

If you have any info regarding Citadel's implementation I'm all ears.  One issue I'm having across the board is the ability to cooperatively manage calendars from clients (i.e. iCal and Outlook can either subscribe to or Publish a calendar, but not both).  Perhaps this is simply a software limitation, and I can understand the paradigm for "security" purposes etc, but I still want to do it.  Any thoughts?

---

### Post by HermanAB on 2009-04-12
Yes, Citadel can do multiple calendars, shared calendars, private email, shared email, access control, mailing lists...

It has been around since about 1980, so *everything* you can think of it does already.

Subscribe to the uncensored.citadel.org BBS and ask your questions there in the Citadel support room.

---

### Post by michwill on 2009-04-13
Thanks for that.  I'm still having trouble understanding how to use Citadel.  I see a lot of documentation telling me that I can do stuff without telling me how to go about it.  On the other hand I see information on items that I'd never care to use. So...

Fyi, I've joined the list and posted a few questions.  I guess it's time to hurry up and wait. ;)


Thanks again.

---

### Post by HermanAB on 2009-04-13
Well, Citadel is a groupware server with a database back end.  The front end can be anything you want.  The default front end is Webcit and it is the most convenient way to administer the system.  However, you can use other programs with it: Thunderbird, Sunbird, Lightning, Outlook, chat clients, Roundcube, Squirrel mail, whatever.

What do you need to configure?

---

### Post by michwill on 2009-04-13
Well, this is the list of my requirements:

1) Manage bi-directional content from the desktop (preferably iCal and Outlook...but willing to use Sunbird...mobile would be nice but not required)

2) Control subscriptions/invites via the web interface at the very least, and if possible, the client as well.

3) Support multiple calendars per user.

4) Email (and phone) notifications for all invites...I saw Citadel has PUSH notification, but it the documentation is abysmal and all the web references seem circular.


Email notifications could be handled by the user's default email address, however I can't seem to figure out how to get Citadel to send a simple email when someone is invited to an event.

Those are basically my requirements.  If you could put me in the know regarding the configuration of any of these items, it would be most appreciated.

Best,
Michael

---

### Post by HermanAB on 2009-04-13
Howdy,

1) Using Citadel iCal with Sunbird is described here: [http://aeronetworks.ca/citadel-clients.html](http://aeronetworks.ca/citadel-clients.html)

"For Citadel calendars, install Sunbird, then click File, Subscribe to Remote Calendar, On the network, Next, iCalendar (ICS), Location: [http://mail.example.com/groupdav/Calendar](http://mail.example.com/groupdav/Calendar), Next, Name: whoever, Next, Finish. If all went well, a username and password dialogue will pop up - enter your data and tell Sunbird to remember it.

To get the calendar from Citadel, click File, Reload remote calendars and to push the changes back to Citadel, click File, Publish calendar."

Outlook requires the Bynari Connector, and will then work exactly as with MS Exchange.

2) Meeting invites: Select your Calendar room, click the Date and click Add New Event.

3) Click Advanced, Add New Room, and select type Calendar and make it Private (default), Public or invite a list of users.

4) Citadel won't phone anyone, but the meeting invites will be sent to all attendees.

Just install the thing, start using it and you'll have it figured out in no time flat.  It only takes about 20 minutes to run Easy Install, or you can download a pre-installed VM for use on a Windows host.

---

### Post by michwill on 2009-04-14
Thanks for that.  I'll check that link out shortly.

> **HermanAB said:**
> 
3) Click Advanced, Add New Room, and select type Calendar and make it Private (default), Public or invite a list of users.


Well, that's what I can't figure out.  I've got Citadel installed on Intrepid 8.10 running it's own web server (not that that matters), but it it never sends out emails to any of the invitees.

When I go to the "Internet Mail" section, it doesn't seem to have anything useful for setting up the sending of mail.  What items do I need to manually configure so that it will send email to all invitees?

Also (and perhaps I'll come across it in the Sunbird doc) is there any way to control invites from the desktop clients themselves?  I suppose I would need to sync it with the online contacts, huh?  Any input/documentation regarding this would be very helpful.

Thanks again.

---

### Post by HermanAB on 2009-04-14
Hmm, Citadel will not send mail if your network and DNS are not configured properly.  The machine should have a fully qualified hostname and the DNS must resolve with A, MX and PTR records.  You could also configure Citadel to forward mail to a smart host (your ISP mail server).

Test your DNS with nslookup and dig.

---

### Post by michwill on 2009-04-14
First of all, Herman, I absolutely appreciate you taking the time out to assist with this issue.  I've played around and around and looked through the docs, but still can't find what I need.

Is any of this possible via WebCit or must I use the command line?  I've read ([http://www.citadel.org/doku.php/documentation:system_administration_manual#basic.site.configuration](http://www.citadel.org/doku.php/documentation:system_administration_manual#basic.site.configuration)), and I see nothing regarding setting up Citadel to send email via another SMTP server.  Can't I just do some kind of generic "sendmail" thing?  I see all kinds of information on setting it up to join neighbor nodes and all kinds of complex items I have no need for, but the "simple" stuff seems to be missing.

As for DNS, is a local DNS sufficient, or are you suggesting I get the office set up with a resolvable internet host name?  I don't currently have a DNS set up in the test area and don't really care to unless it's absolutely necessary.  Also, I've worked with A, MX, PTR records and whatnot on only a few occasions in the past -- frankly I find the whole issue a bit confusing.  So if you have any pointers (pun intended) on dealing with these, I'll take whatever you care to offer.  Until then I'll keep reading away.

Best.

---

### Post by HermanAB on 2009-04-14
Note that to run ANY mail server, the network must be configured right, else it won't work. The Easy Install script will set Citadel up properly for you provided that the network is configured right before your start. The script will try to figure things out but "garbage in, garbage out" applies.

Your mail server must have a FQDN.  I'm not sure where Ubuntu sets that, on Redhat-ish systems, it is in /etc/sysconfig/network.  If you don't run a DNS, then the server won't receive mail directly since it needs a MX record.  If the server doesn't have a hostname and IP address in a DNS, then you can define it in /etc/hosts and then it will be able to send mail. 

Assuming that you don't want to run a DNS and want to use Citadel to act as a slave and fetch mail from your ISP mail server and deliver mail to your ISP mail server, check the following things:

/etc/sysconfig/network (may be different for Ubuntu):
HOSTNAME=mail.example.com

/etc/hosts:
127.0.0.1 localhost.localdomain localhost
192.168.1.2 mail.example.com

You can configure all Citadel features using Webcit: 
In Internet Configuration, set the Local Host Aliases to example.com. 
In Internet Configuration, set Masqueradable Domains to example.com
In Internet Configuration, set Smart Hosts to mail.yourisp.net
In Site Configuration, set Node Name to mail
In Site Configuration, set Fully Qualified Domain Name to example.com
In Site Configuraton Network Services, set Server IP Address to 0.0.0.0

Now restart networking and restart Citadel and hopefully it will be able to send mail to your ISP mail server.  

You then need to go into your private mailbox and configure it to fetch mail from your ISP:
Click Mail, Advanced, Remote Retrieval and configure it to fetch mail from your ISP mail server.

Hope that helps!

---

### Post by michwill on 2009-04-15
Wow.  Ok, I'm sure I'll get to that soon enough, but I think that may have been a bit much.  Basically all I need to accomplish right now is to get out notifications to those that receive invites.  If I create a new event I want all invitees to get an email, or SMS message, or carrier pigeon letting them know they have a new event to accept or decline.

I'm not interested in the "mail server" capabilities of Citadel outside sending notifications.  I'm interested in the "calendaring server" aspects.  I don't need them to be able to receive mail from their email accounts -- they can continue to use Mail.app or Outlook, etc. for that.  I'm simply looking for a quality scheduling/invite system to use.

Not to bring up WebCalendar again, but WebCalendar simply uses PHP Mail to send notifications to invitees.  Just to confirm, this isn't possible with Citadel, correct?

Are there any 3rd party plugins, etc you'd recommend for *simple* notification if Citadel isn't capable of this?

Thanks again.

---

### Post by HermanAB on 2009-04-15
Hmm, you say that you are not interested in the mail capabilities, yet you say that you want to send mail notifications - you got to make up your mind, sorry.

Citadel is a complete solution.  If you want a Lego solution, install Apache, Postfix, Dovecot and Webcal, but that will take you much longer to get to work.

As I said, first get your network settings right, then fix the mail send function and lastly the mail receive function.  If you don't configure the network properly, then Postfix, Exim, Qmail or whatever won't work either.  It is a house of cards, so every layer depends on the one beneath it.

---

### Post by michwill on 2009-04-16
> **HermanAB said:**
> Hmm, you say that you are not interested in the mail capabilities, yet you say that you want to send mail notifications - you got to make up your mind, sorry.

Haha, well I do apologize for the confusion.  But, in all fairness, sending/receiving/managing are not joined at the hip.  I should absolutely be able to output mail without needing to manage it (a la sendmail/PHPmail)

> 
Citadel is a complete solution.  If you want a Lego solution, install Apache, Postfix, Dovecot and Webcal, but that will take you much longer to get to work.

As I said, first get your network settings right, then fix the mail send function and lastly the mail receive function.  If you don't configure the network properly, then Postfix, Exim, Qmail or whatever won't work either.  It is a house of cards, so every layer depends on the one beneath it.


I can appreciate what you're saying, but to infer that the current paradigm is necessary/desired is a bit misleading...no?  I suppose I'll keep reading to see if there is a "hidden" value (or plugin) somewhere that I can add or adjust in order to achieve my goal.

If it weren't for Citadel's future potential and scalability, I might very well use WebCalendar.  But, as it stands, Citadel has seemingly very useful (albeit poorly documented) features that may prove useful.


Thanks again for your help

---

### Post by HermanAB on 2009-04-16
What you seem to miss is that Citadel uses its mail server to send calender invitations.  In Citadel, everything is joined at the hip and configuring it is very easy, provided that you do it right.  

All you need to do is configure your hostname properly and run the Easy Install script again, or fix those few configuration items I showed you.

---

### Post by michwill on 2009-04-19
Alright, you win.  ;)  I've scoured the documentation, and it's not helpful.  Granted, part of it is my lack of familiarity with quality DNS/Mail Server setup, but the other part is the lack of direct answers on the part of the documentation.

That said, from my limited POR, I have no idea what the options available under the "Domain names and Internet mail configuration" even correlate to.  Shouldn't I need to enter a username and password for logging into the mail server, etc?  Where is this information entered/stored?  How do you determine which server is for which group of users?

...so many unanswered questions.

Anyway, before I forget, thank you again for taking the time...I am once again all ears (or eyes as the case may be)


EDIT:  I'm beginning to think that more of my troubles are due to the way WEBCIT presents information -- not with Citadel itself.  It's neither here nor there, but although I'm liking the available features in Citadel more and more, I'm not sure I agree with WEBCIT's presentation and access.

---

### Post by HermanAB on 2009-04-19
If you do 'ps -e' then you'll see that the mail server is called 'citserver' and the web server is called 'webserver'.  Citadel stores all user data (username, password hash, email, attachments, chat, instant messages, calendars, notes...) in an Oracle BerkeleyDB database.  This database can hold up to 256 terabytes of schtuff.

Each user must have a unique user account on Citadel.  You cannot have two users by name of john.doe for example.  User accounts are defined in:
Administration, User Account Management

The domains that Citadel will receive mail for are listed in:
Internet Configuration, Local host aliases

The domains that Citadel will send mail for are listed in:
Internet Configuration, Masqueradable domains.

Just install the thing and start playing, you'll figure it out.

---

### Post by michwill on 2009-04-19
Believe it or not, I've installed it 7 times now.  Five times via the package manager, and twice via the "Easy Installer" -- mostly in an effort to re-attain a clean state (which in and of itself is an exercise in madness).  Something still isn't clicking.  I attempted your suggestion of manually editing the /etc/hosts file in order to set up a "domain name" , but that didn't provide any results.  

This application will be set up in an office environment.  We have no DNS to speak of, and the mail server is the same as our web server -- all hosted externally.  You keep saying "play around", and I have been.  I don't believe I'm a complete idiot, but this endeavor is beginning to prove otherwise.  I'm not sure where to go from here.  I understand what you're saying about Citadel being a complete solution, but it seems to have many features that wouldn't/shouldn't require DNS, etc.  I'm not sure why it can't send/receive mail my simply pretending to be a mail client -- no different than Thunderbird, Mail.app, etc.

There's either something you're assuming I understand that you're not saying, or something you've said a million times that I'm simply not getting.  Either way, I'm gonna take a break from this for a few hours and see if I can't figure something out later.

I apologize for my frustrated tone.  It's absolutely not directed at you.  You've been nothing but helpful, and I appreciate it.  But this install might be the death of me.  ;)


Best.

---

### Post by michwill on 2009-04-19
Ok, I've got it checking mail (although I'm not really concerned about that).  I believe the assumption was that I wanted to use this very box as the email server -- I don't.  One thing about the mail though is that it appears to have no rhyme or reason to its order, and the timestamps are CITADEL's, not the timestamp of the remote mail server.  Besides that, receiving appears to work.

I'm still having trouble with the whole sending thing.  Frankly, I don't really care to send emails atm.  In all honesty, I was just under the impression that sending an email is/was the best way to notify someone of a calendar event.  That's all I really want at this point -- notifications.

---

### Post by HermanAB on 2009-04-20
Well, it all revolves around the mail server.  Citadel consists of a BerkeleyDB back end that stores everything, email, attachments, calendars whatever and similarly all the message passing is done by the MTA.  The only part that you can remove is the web server, but it is nice to keep that one around for administration even if the users don't actually use it and even if you installed Roundcube or Squirrel.  

As soon as you got the DNS and hostname configured right, the whole thing will magically start to work.  Citadel has sanity checks to prevent the system from being abused as a spam relay, so it will only send mail (and notifications!) if it is configured correctly.

Resistance is futile, you will be assimilated.

---

