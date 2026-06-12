---
title: "What email accounts do you use?"
date: 2015-07-03
forum: The Cafe
---

### Post by cwblanch on 2015-07-03
Hey,

So I'm curious as to what email accounts people use. Yahoo, Google, Microsoft, Juno (that may be an old one) etc.
Also what do/don't you like about the one you use?

I'm curious because I use both Yahoo and Gmail but I don't really like how they both work. 
I'd like an email account that I can organize my stuff into folders, but will actually automatically do it!
I have both set with filters and to move the emails automatically but it NEVER does it. 
Actually I think Yahoo is the only one with "folders", Gmail calls them "Bundles" now.

So if someone could recommend to me an email provider that has that functionality I would love it!
It really bugs me that NONE of my emails are organized how I want them to be.

---

### Post by TheFu on 2015-07-03
My own.  It isn't like we can't have our own email servers for $0-$4/month (or free if your ISP doesn't mind).  A micro-instance on Amazon can easily handle email for 20 people.

No need to give up all your privacy for the government snoops by using a large-scale email provider. That seems just crazy to me and defeats the purpose of a federated internet.  Centralized = BAD.

If you want a full-scale communications server that does shared folders, shared addressbooks, shared calendaring and/or delegation, there are F/LOSS solutions for that - but running those is a little more involved and requires a stronger server.  

**I'm completely addicted to Zimbra.**  It provides server-side filters and server-side tags, so all that time spent organizing email is basically gone.  I get 200-400 emails daily and almost all are automatically organized thanks to tagging and virtual folders.  It is hard to explain - but it changed my life.  Use to use Outlook - I'll NEVER, EVER go back.  Zimbra is a hog (java always is), but it has a  pretty GUI and is standards compliant for other client program connections.  Our zimbra server isn't directly on the internet due to security considerations. Best to have a tiny front-end email gateway that can be completely patched and fully maintained that forwards emails to the zimbra instances AFTER all the spam, AV, and other improper emails are filtered.
Did I mention the calendaring is amazing?

Oh - and when you run your own server, you have unlimited aliases, unlimited email accounts, and complete control over what can be forwarded or not.  Also, you can setup automation like IfTTT with procmail. Been doing that sort of stuff since around 1990.  Need to have some job run on another server - send an email - done.

There are so many things that having a Unix-based server/email system can that folks never considered or just never were exposed to thanks to being stuck in *desktop think mode.*  If you have a Linux system - it is a powerful server - why not use it to make life more convenient?

---

### Post by night_sky2 on 2015-07-04
Deleted.

---

### Post by portalhavoc on 2015-07-04
I have 2 Gmail Accounts. (1 from 2004 (From when Gmail was in beta. :O) and the other from 2012.) 

I've been using them for everything. Including Ubuntu. ;)

---

### Post by jeff127 on 2015-07-04
> **TheFu said:**
> My own.  It isn't like we can't have our own email servers for $0-$4/month (or free if your ISP doesn't mind).  A micro-instance on Amazon can easily handle email for 20 people.

No need to give up all your privacy for the government snoops by using a large-scale email provider. That seems just crazy to me and defeats the purpose of a federated internet.  Centralized = BAD.

I partly use Yahoo but mainly my own service. Evolution Mail for GNOME is a pleasure to use. The free services change all the time, I hate that. When Yahoo Mail was upgraded all sorts of weird things happened with people not able to access contacts and such.

---

### Post by rewyllys on 2015-07-05
> **TheFu said:**
> My own.  It isn't like we can't have our own email servers for $0-$4/month (or free if your ISP doesn't mind).  A micro-instance on Amazon can easily handle email for 20 people.

No need to give up all your privacy for the government snoops by using a large-scale email provider. That seems just crazy to me and defeats the purpose of a federated internet.  Centralized = BAD.
I'm not familiar with the Amazon email service that you mention.  Could you please expand a bit on how one can have one's own email server?  

Thanks.

---

### Post by TheFu on 2015-07-05
> **rewyllys said:**
> I'm not familiar with the Amazon email service that you mention.  Could you please expand a bit on how one can have one's own email server?  

Thanks.

Amazon provides a VPS. You install and configure an email service like postfix and dovecot.
Search "postfix dovecot server" for how-to guides.

Or for more security, just use the amazon VPS as an email gateway and forward all inbound email to your house MTA (postfix) so messages aren't left on someone elses' storage more than a few seconds.  The micro-server will easily handle either of these needs.

---

### Post by buzzingrobot on 2015-07-05
At the moment, I use a paid Fastmail account with my own domain ($40 per year).  It's an excellent product and I recommend anyone with serious email needs take a look at it.

But, almost all of my mail is self-inflicted spam that I delete on reading, so I don't need that kind of capability. When I get around to it, I'll let the domain expire and switch to one of the freebies. 

(As someone who did the homebrew mail server thing years ago, the uninitiated should be aware of what they're getting themselves in to.)

---

### Post by rewyllys on 2015-07-05
@TheFu
Interesting reading. I've learned a lot.  Thanks very much.

---

### Post by monkeybrain20122 on 2015-07-05
2 gmail accounts. An outlook account basically for accessing random websites that require email, such as UF. I don't really use it for anything, only log in occasionally to keep it active and to remove spams. :)

---

### Post by TheFu on 2015-07-05
In case there's any confusion. I have multiple email accounts - some on public services and hundreds of aliases on my servers. After all, you cannot use an android phone without at least 1 gmail account - I don't use it, don't give it out and the only emails there were app purchases.  Each of my android devices has a new gmail account. I like to keep things separate and disconnected.  I do NOT use google apps on any of those devices - prefer to use k-9 mail instead.

Part of my privacy efforts expands to social networks. Those are blocked at the network layer to prevent the "like" following from all those companies. If they aren't paying me, they don't deserve access to my private data.  BTW, you can replace most of those social networks and "cloud services" by running them on your own server - how hard it is depends on your skill level.  Here's 1 example: [https://github.com/sovereign/sovereign](https://github.com/sovereign/sovereign)

Each of us has to decide how much we care about our privacy. The EFF tries to help: 
[https://www.eff.org/deeplinks/2013/07/technology-protect-against-mass-surveillance-part-1](https://www.eff.org/deeplinks/2013/07/technology-protect-against-mass-surveillance-part-1)

Oh - and internet privacy is REALLY, REALLY, hard. It is not as easy at installing TOR and going. The devil is in the details. The more we share on public services online, the harder it is.  After having a stalker, I took some drastic steps to reduce and change my online persona.  Be careful out there folks. Please.

---

### Post by pfeiffep on 2015-07-05
> **cwblanch said:**
> Hey,

So I'm curious as to what email accounts people use. Yahoo, Google, Microsoft, Juno (that may be an old one) etc.
Also what do/don't you like about the one you use?

I'm curious because I use both Yahoo and Gmail but I don't really like how they both work. 
I'd like an email account that I can organize my stuff into folders, but will actually automatically do it!
I have both set with filters and to move the emails automatically but it NEVER does it. 
Actually I think Yahoo is the only one with "folders", Gmail calls them "Bundles" now.

So if someone could recommend to me an email provider that has that functionality I would love it!
It really bugs me that NONE of my emails are organized how I want them to be.I have three email accounts (yahoo, verizon, gmail) and I've never liked using webmail as my regular client. I use gmail to consolidate the other 2 accounts, then I can use Thunderbird to read my email using imap. This method provides me the flexibility of readin my email form any internet connected device.

---

### Post by mips on 2015-07-05
Been a gmail user since their beta days.

---

### Post by night_sky2 on 2015-07-05
> **jeff127 said:**
> I partly use Yahoo but mainly my own service. Evolution Mail for GNOME is a pleasure to use. The free services change all the time, I hate that. When Yahoo Mail was upgraded all sorts of weird things happened with people not able to access contacts and such.

I think Yahoo has a really nice mailbox but a compagny that now absolutely requires a mobile phone number in order to subscribe automatically gets on my blacklist.

---

### Post by Kpenguin on 2015-07-06
My main one is my college account (ends in .edu) but I also have a gmail only because it's required for a Google account, I never use it.

---

### Post by Dragonbite on 2015-07-06
I use both Gmail and Outlook.

Important for me is not only the email systems because they almost work as well as each other with a few differences, but their integration with the online storage and document editing capabilities.  This way at work I can edit and work on files through the browser and not have to install anything, and at home I can continue my work.

When I received the original Chromebook (cr48) as part of the pilot program I realized I had to move some of my "life" into the "cloud" but things have come a long way since then.

I split these two accounts this way:

**Gmail **is used for my "personal" life and such. 

[LIST]
[*]The interface is alright, and it has the benefit of saving attachments into Google Drive (and selecting the folder it resides in) which has become more important after hearing that Google deletes attachments after about 5 years of sitting in you Gmail account.


[*]I think GMail's tagging is a little easier than Outlooks, plus it includes multiple levels so I can set up "My" for my personal categories and "Go" for something else and have them further divided (e.g. "My/Friends", "My/Family", "My/School", "Go/Camping", "Go/Church", "Go/Church/Choir", etc.)


[*]At one point you could set up your own domain and Google Apps for only the cost of the domain (~ $10/year).  I jumped on this and set up email accounts for my kids where I was able to manage / control to some degree as opposed to leaving them in Google's (or others') hands and having not ability to manage things.  Now, unfortunately, it costs monthly per user (like $5/user/month) which sucks.
[/LIST]
Meanwhile....

I use **Outlook **for my "professional" and organizations I volunteer with purposes.  It started because I use ASP.NET at work so it seemed logical to use a Microsoft email system for resumes and the like.  It has also been useful for Azure and Visual Studio connectivity.

[LIST]
[*]Something Outlook provides over Gmail is aliases.  I have multiple aliases and use those instead of my account name and split them up between what I use it for (though it all goes into one email box).  I use "Live" for organizations and "Outlook" for resume-related materials.  I like how you could easily set it up so the alias has its own folder and automatically moves the email to the corresponding folder.  

So if I sign up for a newsletter but don't want it intermingling with my other accounts I can set it up to go into its own folder.  


[*]There is also "Sweep" which says "delete any emails from this person, or in this folder, older than 10 days." So if I have a newsletter folder and I don't get to reading a newsletter for 10 days it could automatically delete it because really, what are the chances I'll read it a week and a half later?


[*]One thing I prefer with OneDrive over Google Drive is that the files need not be converted to their format to be editable online.  Meaning I can work on a file at home using LibreOffice, synchronize and then open the file in the browser using Office Online. 

Even better, I can set OneDrive to automatically save files in ODT format, rather than MS Office format.  Plus if you have a text file such as PHP script, Office Online (or OneDrive itself) can open the file AND provide syntax coloring! 


[*]Plus you can open Office files in Dropbox using Office Online, but it only works with Word, Excel & PowerPoint.
[/LIST]
So ....

I use both because they both have benefits for me, either for sorting out their general purpose or providing integration with their "desktops" : Google -> Chromebooks, Outlook -> Windows 8+ (or coming 10 in my case)

---

### Post by Vikingberry on 2015-07-08
I use Gmail for things like forums and sites to gather information/learn/talk but I'm currently working on making my own email in my homelab for business related things.

---

### Post by alan62 on 2015-07-08
I have a gmail account and a yahoo one, although I haven't been using the yahoo email for about 2 years, still login occasionally to laugh at all the spam I get.

---

### Post by Wadim_Korneev on 2015-07-11
I have a ZohoMail accounts. Zoho Mail is a solid email service with ample storage, POP and Imap Access, some integration with instant messaging and online office suites.

---

### Post by leclerc65 on 2015-07-11
I use Gamil, plus a Hotmail as a recoverable mail box.
But I add the following in my /etc/hosts
```

# [Google Inc]
127.0.0.1 adwords.google.com
127.0.0.1 pagead.googlesyndication.com
127.0.0.1 pagead2.googlesyndication.com
127.0.0.1 adservices.google.com
127.0.0.1 imageads.googleadservices.com
127.0.0.1 imageads1.googleadservices.com
127.0.0.1 www.googleadservices.com
127.0.0.1 apps5.oingo.com
127.0.0.1 www.google-analytics.com
127.0.0.1 kona.kontera.com
127.0.0.1 infolinks.com
127.0.0.1 online-oas.affinitygroup.com
127.0.0.1 ad.doubleclick.net

```

---

### Post by user1397 on 2015-07-12
I have a main gmail and a secondary that I use for anything I have to sign up for that I deem sketchy or not completely trustworthy.

---

### Post by Skaperen on 2015-07-12
> **TheFu said:**
> Amazon provides a VPS. You install and configure an email service like postfix and dovecot.
Search "postfix dovecot server" for how-to guides.

Or for more security, just use the amazon VPS as an email gateway and forward all inbound email to your house MTA (postfix) so messages aren't left on someone elses' storage more than a few seconds.  The micro-server will easily handle either of these needs.

yes, Amazon ([AWS]("http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html")) [Free Tier]("https://aws.amazon.com/free/") can do this (_BTDT_).  but i went with a traditional VPS at [CloudVPS]("http://www.cloudvps.com/virtual-private-server") to get a full _IPv6_/64 and isolation from USA access.  _AWS_ does *not* support _IPv6_, yet, and *i am into it*.

i might try out [Zimbra]("https://en.wikipedia.org/wiki/Zimbra") here and see how well it does on _IPv6_.
i have *not* received any spam over _IPv6_, yet.

---

### Post by night_sky2 on 2015-07-12
Gmail is pretty hard to beat and with all the other nice services synced with a Google account (Drive, Youtube, Maps ect) it's a a winner.
But I remain a Firefox user, and Chrome is one of the few things I am not using from Google.

---

### Post by mikodo on 2015-07-13
I'm trying out Tutanota again. It suits me. It came out of beta this spring. It uses encrypted servers, that no one but the user can access.
It provides for encrypted email transfer with public and private keys or, non encrypted emails.

It can not be used with IMAP/POP3 though. To do that, they would have to clear text access to the emails. Maybe someone will, create an extension for Thunderbird, etc. that parses what is on the server and displays it in a decrypted form. Paraphrase from Colin Arnott, here:  [URL="https://tutanota.uservoice.com/forums/237921-general/suggestions/6895110-external-imap-pop3-connection"]https://tutanota.uservoice.com/forums/237921-general/suggestions/6895110-external-imap-pop3-connection
[/URL]

---

### Post by Wild_Duck66 on 2015-07-14
I have gmail, virgin and ntlworld addresses that I use with Thunderbird, I also have a hotmail one that doesn't get used anymore.

---

### Post by sammiev on 2015-07-14
Been using gmail with no issues what so ever but also been playing with Tutanota with no issues.

---

### Post by khade_putra on 2015-07-16
I like gmail, bcoz its free :p and simple to use

---

### Post by bashiergui on 2015-07-19
> My own. It isn't like we can't have our own email servers for $0-$4/month (or free if your ISP doesn't mind). A micro-instance on Amazon can easily handle email for 20 people.All you need is ssl and gpg and no one can snoop.

---

### Post by NeoGreen on 2015-07-20
I use gmail and outlook.com, but planning on setting up my own email server soon.

---

### Post by mystics on 2015-07-20
I use GMail. Signed up for it when I first got an Android, and it has mostly worked. The only real issue I had was trying to get it set up with Thunderbird, as Google didn't want to play nice with it. But it was nothing a few minutes of changing settings couldn't fix. (Admittedly, though, I've held that against Google far more than is probably healthy.) Well, I guess I also don't like Google's stance on privacy, but I just haven't jumped over to another service (yet).

However, I recently had to set up an email server for someone and the process got me interested in setting up one for myself, especially since there were a lot of things I wanted to do with their server that they didn't want me to do. I'm sure it will happen eventually. I just need to stop being a poor college student.

---

### Post by anakai on 2015-07-21
Gmail and Gmail, one for personal use and one for registrations everywhere.

---

### Post by hunterkasy on 2015-07-21
I use gmail,yahoo, and I am slowly switching over to protonmail.  protonmail is a zero knowledge full encryption based in Switzerland

---

### Post by yannis2 on 2015-07-27
i use gmail mostly

---

### Post by NathanRodriguez on 2015-07-28
I'm on Yahoo mail for some time and seems pretty reliable.

---

### Post by night_sky2 on 2015-08-14
Outlook/Hotmail is the best email service available. Fast, secure, reliable, customizable and comes with a calendar, 15GB of cloud storage, Office Web apps and Skype intergration.

 I am surprised it's not mentionned more often. Ah, I forgot, it's from MS...

---

### Post by Dragonbite on 2015-08-14
> **night_sky2 said:**
> Outlook/Hotmail is the best email service available. Fast, secure, reliable, customizable and comes with a calendar, 15GB of cloud storage, Office Web apps and Skype intergration.

 I am surprised it's not mentionned more often. Ah, I forgot, it's from MS...

There are times I prefer Outlook... and there are times I prefer Gmail.

I wasn't quite impressed with Office365, but that was a couple years ago so it may be improved.

---

### Post by SantaFe on 2015-08-14
> **Dragonbite said:**
> There are times I prefer Outlook... and there are times I prefer Gmail.

I wasn't quite impressed with Office365, but that was a couple years ago so it may be improved.
Let's hope those two e-mail providers don't merge and become Goutlook!  :D

---

### Post by Dragonbite on 2015-08-14
> **SantaFe said:**
> Let's hope those two e-mail providers don't merge and become Goutlook!  :D

Could be "glook" or "gout"

---

### Post by rebusgadfly on 2015-08-24
I have used gmail since it went beta. I also use outlook. I think the best advice I can give is use what you find most comfortable. Most people have at least two accounts. One account for everyday use and business. (that's my gmail) Use a second account as a junk account when a website or op system requires an email account.(my outlook). Gmail is beta testing a new web based interface that is just amazing. It is so nice to use and very intuitive.

---

### Post by mikodo on 2015-08-24
> **TheFu said:**
> Snippet [https://github.com/sovereign/sovereign](https://github.com/sovereign/sovereign)Thanks for .. ahh, sharing that!

I think I may have found a starting place, that provides for what my journey into this technology, has the potential for. As of late, I have wondered why.  I now have guides/leads/ideas/images to play with, in my retirement. I was wanting a project that provides these capabilities. There is more there, to utilize than I am aware of now. And ... it works with TarSnap. Is this FreeBSD based I wonder, given the dev/maintainer's history. 

If, I don't have the firing neurons left to do it then, I have someone who will do it for me. I'm rushing into my second divorce.  Xwives cost a lot of money, and I may have to work until I drop. Back to work.

Have a nice day!

:)

---

### Post by montag dp on 2015-08-24
I also use Outlook.  I've had it for probably about 12-15 years since my parents have used MSN mail and created accounts for all of us back in the day.  I don't like Gmail, so even though it seems to be all the rage I have avoided switching to that (plus it's a hassle switching your primary email address).  I recently discovered that Evolution works quite flawlessly with my MSN email, so I no longer have to go onto the outlook.com website, which I really disliked anyway.  (I never had much luck getting Thunderbird to work reliably with my MSN email.) It's also nice getting notifications on my computer when I get a new email.

---

### Post by night_sky2 on 2015-08-24
> **montag dp said:**
> I also use Outlook.  I've had it for probably about 12-15 years since my parents have used MSN mail and created accounts for all of us back in the day.  I don't like Gmail, so even though it seems to be all the rage I have avoided switching to that (plus it's a hassle switching your primary email address).  I recently discovered that Evolution works quite flawlessly with my MSN email, so I no longer have to go onto the outlook.com website, which I really disliked anyway.  (I never had much luck getting Thunderbird to work reliably with my MSN email.) It's also nice getting notifications on my computer when I get a new email.
So you have a msn.com email? That's legacy. There are very few of those left in circulation nowadays. I've had an hotmail.com address for years now but never could get a MSN one back in the days. I think you had to pay for an MSN premium feature or something.

I personally never liked to manage my emails locally. It has become somewhat of an habbit to bookmark the Hotmail/Outlook web app and access it first thing in the morning. Now I can also sync with Onedrive, open documents with Office Web app and have a quick chat with my Skype contacts straight from the mail box. To be honest, I can't really see myself reverting to an email client.

---

### Post by montag dp on 2015-08-25
> **night_sky2 said:**
> So you have a msn.com email? That's legacy. There are very few of those left in circulation nowadays. I've had an hotmail.com address for years now but never could get a MSN one back in the days. I think you had to pay for an MSN premium feature or something.

I personally never liked to manage my emails locally. It has become somewhat of an habbit to bookmark the Hotmail/Outlook web app and access it first thing in the morning. Now I can also sync with Onedrive, open documents with Office Web app and have a quick chat with my Skype contacts straight from the mail box. To be honest, I can't really see myself reverting to an email client.Yes, it's an msn.com account.  I didn't know they were so rare, lol.  I'm guessing now it's no different than a hotmail.com account, except for maybe sounding a little more official.  I never use the Office Web app or Skype, but I can see why you'd rather use outlook.com instead of a client if you did.  For my purposes, I'd rather not use the website.  It makes Firefox constantly use CPU (I think it's the ads that do it), and in my experience sometimes the site just sits there thinking for awhile when I'm clicking through messages quickly, which is annoying.

---

### Post by yoshii on 2015-08-25
[http://FastMail.fm](http://FastMail.fm) is a good service and seems to have the folder functionality you need.  
They have 30-day free trials, and paid accounts start at about 10 dollars per year.

---

### Post by sonicwind on 2015-11-08
I'm a long time Yahoo Mail user. It's not perfect but I've never been so unhappy with it to make a switch to anything else. I think it does a good job containing spam to the spam folder.

---

### Post by night_sky2 on 2015-11-10
> **yoshi2 said:**
> [http://FastMail.fm](http://FastMail.fm) is a good service and seems to have the folder functionality you need.  
They have 30-day free trials, and paid accounts start at about 10 dollars per year.
I wouldn't pay for an email account when there are plenty of good, free options.

I really like the new Outlook box, it's basically now an ad-supported version of Office 365 Exchange Online. Pretty hard to beat.

---

### Post by Habitual on 2015-11-10
You had me at EHLO

---

### Post by Dragonbite on 2015-11-10
> **night_sky2 said:**
> I wouldn't pay for an email account when there are plenty of good, free options.

I really like the new Outlook box, it's basically now an ad-supported version of Office 365 Exchange Online. Pretty hard to beat.

You mean the browser version?  Try Adblock Plus... I don't see any advertisements, but it sometimes still shows a blank column instead.

---

### Post by night_sky2 on 2015-11-10
> **Dragonbite said:**
> You mean the browser version?  Try Adblock Plus... I don't see any advertisements, but it sometimes still shows a blank column instead.
Yeah I know but I don't use Adblock Plus (too heavy) I prefer BluHell Firewall on Firefox.

I meant to say that the new Outlook.com release is now pretty much Office 365 Exchange, it has the exact same features, but with an ad (that can be blocked..).

[http://www.theverge.com/2015/5/21/8634979/microsoft-outlook-email-service-new-features-user-interface](http://www.theverge.com/2015/5/21/8634979/microsoft-outlook-email-service-new-features-user-interface)

---

### Post by at35z on 2015-11-10
I use Yahoo, but well, I don't have many requirements. It's just kind of "needed".

---

### Post by QDR06VV9 on 2015-11-10
> **mikodo said:**
> I'm trying out Tutanota again. It suits me. It came out of beta this spring. It uses encrypted servers, that no one but the user can access.
It provides for encrypted email transfer with public and private keys or, non encrypted emails.

It can not be used with IMAP/POP3 though. To do that, they would have to clear text access to the emails. Maybe someone will, create an extension for Thunderbird, etc. that parses what is on the server and displays it in a decrypted form. Paraphrase from Colin Arnott, here:  [URL="https://tutanota.uservoice.com/forums/237921-general/suggestions/6895110-external-imap-pop3-connection"]https://tutanota.uservoice.com/forums/237921-general/suggestions/6895110-external-imap-pop3-connection
[/URL]
+1    I really like them.

---

### Post by robboguy on 2015-11-12
Gmail all the way, however I'm getting more and more into Tutanota.

---

### Post by mikodo on 2015-11-13
I'm liking ProtonMail more than I do Tutanota now. I still use Tutanota. I plan to keep both. Protonmail is evolving very quickly.

---

### Post by bruakerche on 2015-11-13
Yahoo and domain specific email account. Gmail is great but blocked here.

---

### Post by smtp on 2015-11-17
Domain specific email account.

---

### Post by Dragonbite on 2015-11-17
My wife actually has an email account through her website hosting company but it is set to forward to her Gmail account so that Gmail will archive and handle all the nitty-gritties and if she changes web host, the new one will just need to be able to forward it and she otherwise doesn't have to change a thing.

---

### Post by shantiq on 2015-11-17
a few times i have wanted to run away from gmail
but no one offers 25MB attachment and 15GB of space and googledrive-type upload capacity

so all these encrypted providers look tremendous but i remain with the NSA-friendly gmail :]  a bit like camping in a train station with the doors open in the middle of winter with free access to the buffet :)
but hey i am not planning world domination in any of my messages i do not think ... 

[https://protonmail.com/invite](https://protonmail.com/invite)
[https://www.hushmail.com](https://www.hushmail.com)
[https://tutanota.com](https://tutanota.com)

---

### Post by kurt18947 on 2015-11-17
I'm pretty happy with gmx.com and Thunderbird IMAP. For sites that insist in an email address for no legitimate reason, I use a temporary email address.

---

### Post by night_sky2 on 2015-11-18
> **kurt18947 said:**
> I'm pretty happy with gmx.com and Thunderbird IMAP. For sites that insist in an email address for no legitimate reason, I use a temporary email address.
I liked GMX until it shut me out of my account for no reason when I logged in on 2 different computers in the same day.

Couldn't get it back as their tech support is very poor and apparently doesn't reply back.

---

### Post by lisati on 2015-11-18
> **night_sky2 said:**
> I liked GMX until it shut me out of my account for no reason when I logged in on 2 different computers in the same day.

Couldn't get it back as their tech support is very poor and apparently doesn't reply back.

I went off GMX after they shut me out of my account too. The best I could manage to get from them was that there was some kind of security problem, with nothing useful that could have helped me figure out what on earth they were talking about.

---

### Post by kurt18947 on 2015-11-18
That's good to know about GMX mail. It might be wise to not become TOO dependent on them, it sounds like.

---

### Post by night_sky2 on 2015-11-18
> **kurt18947 said:**
> That's good to know about GMX mail. It might be wise to not become TOO dependent on them, it sounds like.
There are many complaints against them locking accounts out of the blue:

[http://www.sitejabber.com/reviews/www.gmx.com](http://www.sitejabber.com/reviews/www.gmx.com)

They seem to have some system in place to detect ''irregular activity'' which is _***way ***_too restrictive. Logging in with two different IP adresses in the same day can trigger it.

---

### Post by rocco6 on 2015-11-21
Personally, 1 Gmail account from 2008 to 2012 (deleted) and another Gmail account from 2013. I love Inbox and Gmail.

---

