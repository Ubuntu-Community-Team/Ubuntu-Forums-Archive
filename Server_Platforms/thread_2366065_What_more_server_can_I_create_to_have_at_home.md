---
title: "What more server can I create to have at home"
date: 2017-07-13
forum: Server Platforms
---

### Post by cazz on 2017-07-13
Hi
Right now I have at least four linuxserver running at home.
webserver with PHP and MySQL,
VPN server with OpenVPN,
Game server with CSGO server,
System server with Observium and
Cloud server with Nextcloud.

I wonder what more server fun I can create at home that I also can use, I mean is not fun to create a server and not use it :)

I'm not into email server, I have already a good place for my mail so what more can I create?

---

### Post by TheFu on 2017-07-14
You didn't mention a backup server or NAS for the network or clustered VM server.  Guess it depends on what you want to learn.

plex server - nice to stream my video content and audio files from anywhere in the world. No need to have any plex userid.  Just use a socks proxy to access the content from anywhere in the world ... or your vpn should work.

IRC bouncer?

Read-it-later clone - wallabag?  I like to dump a few sites into an epub and have them on my disconnected tablet for reading in waiting rooms or on airplanes.

Calibre - PDF/epub/eBook server.  Handy to convert from X --> epub formats.

Centralized news reader - I use a nextcloud addon, NEWS.  Same view of my RSS feeds regardless of client device is very nice.

Pi-hole - block 99% of all ads.

For some other ideas: "sovereign self hosting" is the search. Must be 100 other interesting things.

---

### Post by cazz on 2017-07-14
ohh thanks for the replay

Well to tell the truth I have a Plex server, also a backup server but they are not in Linux.

The other idea is intresting and thanks for the idea to search for "sovereign self hosting"

---

### Post by TheFu on 2017-07-14
> **cazz said:**
> ohh thanks for the replay

Well to tell the truth I have a Plex server, also a backup server but they are not in Linux.

The other idea is intresting and thanks for the idea to search for "sovereign self hosting"

Clearly you should Upgrayedd those to Linux ASAP - for a "double-dose of pimpin".

Also, having a local email cache is very handy.  If you care about privacy ... oh ... you run that other OS, sorry. I'll go away now. ;)

---

### Post by cazz on 2017-07-14
lol well yes I can use Linux to Plex and also to backup but I like to be good in more then one OS.
And why change when something that working.

But I have help a friend to run Plex and Backup in Linux :)

I have think a little about email but to tell the truth, I'm afraid that I do something mistake or forgot something so someone take control of the linux and use it to send spam and that.
It just feel that people that do that just looking for a homemade mailserver to take control over.

---

### Post by Michael_McKenney on 2017-07-14
Backup server that was offsite in case of disaster.

---

### Post by cazz on 2017-07-14
I have two duplicate server that both have same information in RAID.
One server is at my house, the other one is in another building with another Powersource and UPS
Every night it run a backup to clone everything from one server to another and I get log everyday if it is ok or something is wrong.

---

### Post by Habitual on 2017-07-14
[Kibana]("https://www.digitalocean.com/community/tutorials/how-to-install-elasticsearch-logstash-and-kibana-elk-stack-on-ubuntu-14-04")?

---

### Post by TheFu on 2017-07-14
A clone of a server isn't the same a having versioned backups.

Cloning corrupted data from RAID to RAID can mean having 4 corrupted copies. I've seen it.  The issue taught me the vast difference between having a mirror and having versioned backups.

RAID solves 3 problems.

Versioned backups solve 1001+ problems, including corrupted RAID.

BTW, I'm really good in many OSes; mostly Unix related. Each has slight differences that don't matter much to end-users, but make them vastly different to an admin.  Plus they pay better which is always a bonus.

I wasn't suggesting that you run a mailserver. 
Just suggesting that running a caching mail system could be nice to have, only available via VPN.
OTOH, I care about privacy more than most. Some might call me crazy. ;)  We each have a line and those shift over time for everyone.

---

### Post by cazz on 2017-07-14
Kibana did look fun but not sure if I going need to use it.


Ahh well is not a clone system I have, just a backup system that read the file and if the file is not there it going to copy to the backup server (it never go from server 2 to server 1, only server 1 to server 2)
So when I notice I have some error in my files in server 1 I remove them.
I like to know what I have on my servers (10 servers on two Hyper-V core)


ohh sorry I have never hear about caching mail server but have just read a little and it look very interesting and I think I going to read a little more about it.
What I understand it send the mail I got from my mail provider to my own mail caching system.
I can make it more secure if I do not make it access from internet and I have go true my openVPN

---

### Post by cazz on 2017-07-14
A little update.
Is maybe have to create a new thread but I ask here first.

Is a webmail more secure if I make it so I only can receive mail and never send mail??

Was thinking if I create a mailsystem home that only can receive then it make it easy to send attached to me to save.
Maybe even send log to this mail instead of gmail that I do now if something is wrong with my system.

---

### Post by TheFu on 2017-07-14
Most home connections can't be used as full email servers. Between ISPs and every email server admin blocking residential IP ranges, it doesn't work.  If you aren't on a residential subnet, then we can talk further.

As for a caching email server ... use **fetchmail** to pull the email.

---

### Post by cazz on 2017-07-15
well is ok with my ISP but the fetchmail does looks very intresting.

---

### Post by TheFu on 2017-07-15
> **cazz said:**
> well is ok with my ISP but the fetchmail does looks very intresting.

Your ISP is 5% is the issue. The rest of the world is the other part.  If your static IP is in a blocklist, forgetaboutit. There are email blocklist checkers all over the web.

If you don't have a static IP, it isn't impossible, but if the IP changes more than weekly, it would be difficult to host an email server regardless.

But none of that matters if you are just running a caching server and using fetchmail to retrieve emails.  In that situation, you don't need a DNS MX record or even any DNS records. Your client IP can move all over the place. Of course, with a VPN used to access the email system, it would be less useful.

There are other methods to run an email setup - like with a gateway at a VPS and the main email server at home. All traffic in and out go through the VPS, but data doesn't sit there long at all. If the home connection goes down, it sits on the gateway until it is back up and gets flushed down.  If you care about privacy, this is the way to go instead of using 4th party email or (cough, cough) gmail/ymail/hotmail or any huge email provider.  The issue with VPS IPs being in block lists is still there, so before accepting any static IP from a VPS, check that.

---

### Post by cazz on 2017-07-15
Thanks for that information.

Well I don't care so much my privacy when we talk about email.
My idea is like this.
create a email address and then use fetchmail to get all the mail that goes there to my own server, leave no mail left.
That mean I don't have to worried if I get to much mail or to much file attached to me.
I have ask my mail provider if that is any limit of how big the mail can be and they say they have no limit.
So if I send 20mb files to the email address then I want fetchmail to get it and save it on my local server.

But what I have read (It is maybe wrong) that I also need MTA like Postfix or Sendmail.

My idea if that is possible is use a webmail on my local server like SquirrelMail so when I want to see if I get something or look true old mail from fetchmail I only need to login on the local webmail and read.
And if I'm not at home I go true my openVPN.

---

### Post by TheFu on 2017-07-15
I've been using postfix for over 20 years.  It was designed to replace sendmail for 99% of the needs that sendmail has due to sendmail having a history of being hacked.  Security was the main goal for postfix when it was written.  My advice is to avoid sendmail unless you absolutely know what you need can only be done with it.  I've run corporate email systems all this time. Not once would sendmail be needed.

The goal of the MTA is to place files into the correct place for users.  How they arrive isn't nearly that important.  The "correct place" can be numerous locations. All that matters is that the MTA and any helpers and any clients respect that location.  MTAs are for receiving email and sending email. They can also do some address re-writing. 

Viewing email is a different thing. You can use any client you like.  I ran squirrelmail for a few years.  Compared to other options, it is a toy.

As for how squirrelmail gets access to the email, that is via a pop3 or imap server.  This is needed for any client that isn't running ON THE SERVER.  Dovecot is popular.  Most of the other imap clients have died off for assorted reasons.

If you really want a full communications system, check out Zimbra.  However, Zimbra's installation is very picky about stupid things.  It demands an MX DNS record be correctly set PRIOR to the install. The trick is to make your Zimbra install a 3rd or 4th priority for your normal MX server.  Also, Zimbra hates /etc/hosts files that have more than 3 lines.  Post install, you can put back whatever you want, but during the install, it cares.  Zimbra is like MS-Exchange 10x, but it is hard to properly secure.  The web-GUI is amazing, if that is your desire.  I only use it to setup filters and rules.  For everything else I use thick clients.  Zimbra can access user accounts from an outside LDAP server, or it can be the primary LDAP server for all application and user logins on your network.  Not quite SSO, but single userid/password.  I wouldn't let Zimbra be the primary LDAP for a network.  I did for 5 yrs and zimbra upgrades were always a terrible hassle. Had to remove the POSIX extension before, do whatever upgrades were needed, then put them back .. using whatever new method they'd imagined.  End users loved it.  Change your email password and that immediately impacts all other systems.  

And Zimbra can pull email from all your other email accounts, so you don't need a separate fetchmail.  There are many addons for Zimbra - SIP calling, CRM connectors, lite-document management, enterprise calendaring with resources and delegation, Contacts, tagging, distribution lists, aliases, spoofing and the search is like google for all your email, contacts, attachments, tags, calendar, whatever.  Virtual folders can be created based on keywords, times, or TO/FROM addresses ... anything in an email.  I have about 15 different calendars, overlaid on the same view. Handy.

Zimbra is a beast. It is a mix of 15 F/LOSS projects and each is tightly coupled. In theory, each one can be swapped/upgraded as you like. In practice, it is impossible.  When I started with Zimbra, before Sun owned it, it would run in a 768MB VM with 1 CPU.  Then Sun bought them and added lots and lots of Java, which bloated it to needing 2G of RAM and 2 cores.  The last update I did wouldn't work with 2G, so I upped that to 2.5G.  

Probably more than you want to know.  Zimbra mostly runs itself, but every upgrade and I have to relearn stuff.  It is time to do a Zimbra upgrade, I'm fairly certain.  They broke some things last time I tried, so put it off 6 months.  Did I mention that my Zimbra system isn't directly available on the internet for security reasons?  

I'm completely addicted to Zimbra's capabilities.  I've tried other calendaring and email systems. None come close. None.

Sorry for going on.

---

### Post by cazz on 2017-07-15
Wow I got headache reading all this technical terms in english, just happy is soon time to eat pizza. :)

Yes I have hear and even read about Zimbra sometime ago but I think this is a overkill for me.
At first I was just curious what kind of linux server I can use at home, after I while I got curious about mail caching server.
Next you gave me a idea of fetchmail
and one of the guide I find was this
[https://www.howtoforge.com/debian_etch_fetchmail](https://www.howtoforge.com/debian_etch_fetchmail)
I also find this
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-postfix-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-postfix-on-ubuntu-16-04)

My goal is to make so every mail from [email]file@domain.se[/email] go to my local mail server that have 100GB space.
I guess I need some kind of client to make it easy for me to read the mail I got.
I use Thunderbird on my workstation but does not like to have it on when I'm away just to read some mail that why I need somekind of webmail GUI.

I'm very happy that you give me so much information, this forum is fantastic and the people too.

---

### Post by TheFu on 2017-07-15
I use K-9 mail on my tablets and smartphones.  Webmail is just too painful.  Plus, any email that isn't ASCII is a security issue.  Definitely don't allow HTML email anywhere, that is an attack vector.

Fetchmail is pretty easy.  Go to {THERE}, get my email, using the provided login creds.  Drop it in my ~/.mail/ directory in mbox format.  Pretty simple.

---

### Post by cazz on 2017-07-15
ohh ok
Not sure if I'm right but is that something like this

Fetchmail - Get mail from POP3/IMAP from a email to the local mail server
Postfix - Make so I can connect the client to my local mail server.

What I understand I have to first config Postfix and after that install Fetchmail to get it to work

---

### Post by TheFu on 2017-07-15
Clients only connect to postfix to SEND email. Not for reading it.

---

### Post by Michael_McKenney on 2017-07-15
If you want to do an email server, you need to setup a Godaddy account and get an A and MX record for your server.   A record of Domain.Com and MX record of Mail.Domain.Com.   Without an MX record, no mail server will talk to you.

---

### Post by TheFu on 2017-07-15
And if using fetchmail, he doesn't need a domain or MX or any other DNS records at all.

---

### Post by cazz on 2017-07-15
ok so it mean I do not need postfix, just fetchmail.
ok
now I have so much info that I going to try :)

---

### Post by cazz on 2017-07-15
it looks like i have to install postfix just to get the SMTP to save mail in the home folder.

/Update
Have install postfix and run is as local only

Have try with both mail and mutt and both works fine.
Have not yet find out how to do with attached files

Have also not have time to look if that is any web GUI that is easy to use that can read local maildir so I can easy access the mail and the attached files.

---

### Post by TheFu on 2017-07-15
I don't know if fetchmail requires an MTA or not.  I have used it for years to poll ISP email addresses and similar never-use email addresses that I'm forced to have occasionally.

Every one of my systems runs postfix as a satellite node.  They only accept local mail and forward it to the main mail server.  That is part of my systems management - logwatch and other alarming systems for example.  Plus it is nice when cron has a place to send job results.

I don't know of **any** webguis that can read mbox files.  I hope they cannot. That security would suck greatly.  Think about how webapps work - you don't want them having any access to general files just anywhere on the machine.  You'll want an imap of pop server, probably.

---

### Post by cazz on 2017-07-15
mm right now I just try different idea.
Like maybe install XFCE desktop and see if any client there can read the folder.

But I have also notice mpack and have a script that extract attached files so I can use that too.
Have made a backup of the ubuntu server so when I'm done I just restore it :)

But have notice is some file size limit in fetchmail or postfix. a mail with attached file is about 6 mb is ok but if is 25 mb it can't download the mail from my mail provider.

---

### Post by TheFu on 2017-07-15
postfix (and all MTAs) have a maximum size that can be configured.

---

### Post by cazz on 2017-07-15
Thanks alot.
Now I have change a little and that and now everything works very good.
I going to change so one of my mail log go to the new email address so I'm curious how it going to works :D

---

### Post by jamapii on 2017-08-04
A smart home server, I think should be run at home if possible. Within a few years, home automation will be widespread.

There are a lot of smart home systems that depend on some cloud server outside the home. What if it goes down? And think p r 1 v a 6 y.

A few years ago, one of them even has shut down all devices with an update.

---

### Post by cazz on 2017-08-04
Hmm not sure what you mean but I have a smartserver (not in Linux) that take care of my lights in the house and even the temp.
I use Tellstick

---

