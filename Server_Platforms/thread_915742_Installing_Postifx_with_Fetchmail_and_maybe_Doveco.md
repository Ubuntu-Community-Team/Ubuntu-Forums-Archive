---
title: "Installing Postifx with Fetchmail and maybe Dovecot?!?!?"
date: 2008-09-10
forum: Server Platforms
---

### Post by scurlaruntings on 2008-09-10
Hopefully one of you guys can help me. Im trying to set up a mail server that can POP email from 1and1 inject that into postfix and then allow a MUA to recieve and send mail from that server. Do i require Dovecot to use IMAP/POP3 as i cant see anything natively within Postfix to configure IMAP/POP3 access for clients. Also im using fetchmail to retrieve the emails from 1and1 how do i then configure this to inject the email into Postfix? Is this setup possible i guess may be the right question. Please note i am a windows exchange admin so the world of Linux is pretty new to me.:(

Please note in addition im using webmin to configure it as im not to ofay with all the commands to configure the .cf files.:guitar:

---

### Post by beaker15 on 2008-09-10
postfix should automatically setup your mailboxes for the users you have. The webmin module for Fetchmail is quite self explanatory, you choose a user to setup fetchmail for and just enter your settings for 1and1 and it fetches the mail and puts it in that users maibox, its very straightforward. And yes you will need Dovecot for your clients to get their email from postfix to their MUA

good luck!

---

### Post by scurlaruntings on 2008-09-10
Are there any decent user guides for configuring postfix with webmin? Do i require BIND to be installed on the same box?

---

### Post by scurlaruntings on 2008-09-10
Bumpety Bump! C`mon guys i thought you Unix/Linux admins were in the know!!!

---

### Post by scurlaruntings on 2008-09-10
Ok 20 views and no one here can point me in the right direction? Hmm may be il just stick to Exchange.

---

### Post by schettj on 2008-09-10
Google... use it. I mean, I can google the answer for you, but you really could find this answer yourself just as fast as I can. 

I mean, this is now a webmin question. Asking a webmin question on an ubuntu server board is a bit of a reach.

Teach a man to fish and all that...

---

### Post by scurlaruntings on 2008-09-11
> **schettj said:**
> Google... use it. I mean, I can google the answer for you, but you really could find this answer yourself just as fast as I can. 

I mean, this is now a webmin question. Asking a webmin question on an ubuntu server board is a bit of a reach.

Teach a man to fish and all that...What kind of stupid answer is that? I came here because iv trawled google and couldnt find the answers i need!!! I even purchased O`reillys book on Postfix but unfortunately its too vague for linux noobies like myself. Bearing in mind the plethora of linux distro`s and disimilar compliations i thought id ask the socalled experts seeing as im trying to get 3 applications to work together. If was using Exchange i wouldnt have this problem. But i thought id be open minded and try the world of linux and all you can tell me is google search!?!?!?  And how on earth is it a bit of a reach when i elected to use a simpler tool for administration of postfix as im not entirely ofay with the UNIX commands? Havent i already said im a linux noob or consider myself such? Seriously if you have nothing of any merit to post dont waste your time. Note to self find another distro and dont waste my time with salty boards like this.

---

### Post by windependence on 2008-09-11
Note that you will find the same joy in whatever "other" distro you find also because these packages are configured the same way throughout.

That being said, if you can swallow your pride for a sec I'll give you some suggestions to make your life easier.

There are two packages that combine all these things into one so you don't have to devil yourself with assembling three pieces of your e-mail server.

I prefer Zimbra Collaboration Suite, [www.zimbra.com](www.zimbra.com)

Here is a tutorial to get you going:

[http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu](http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu)

[http://www.howtoforge.com/zimbra-integration-with-samba-on-ubuntu](http://www.howtoforge.com/zimbra-integration-with-samba-on-ubuntu)


The other option is Citadel. There is a member by the name of HermannAB here who is an expert on Citadel setup. I'm sure he will chime in on this thread soon.

-Tim

---

### Post by scurlaruntings on 2008-09-11
> **windependence said:**
> Note that you will find the same joy in whatever "other" distro you find also because these packages are configured the same way throughout.

That being said, if you can swallow your pride for a sec I'll give you some suggestions to make your life easier.

There are two packages that combine all these things into one so you don't have to devil yourself with assembling three pieces of your e-mail server.

I prefer Zimbra Collaboration Suite, [www.zimbra.com](www.zimbra.com)

Here is a tutorial to get you going:

[http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu](http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu)

[http://www.howtoforge.com/zimbra-integration-with-samba-on-ubuntu](http://www.howtoforge.com/zimbra-integration-with-samba-on-ubuntu)


The other option is Citadel. There is a member by the name of HermannAB here who is an expert on Citadel setup. I'm sure he will chime in on this thread soon.

-Tim
I have a Vmware instance of Citadel already built on CentOS. I do need to explore it further but i couldnt see any feature within it that allowed me to POP mail from an external source. Plus Postfix gives me a bit more control. Zimbra iv heard of but iv never used it.

And for the record dude there is absolutely no pride here whatsoever. Linux is a steep learning curve which im more than willing to explore and have done for the past 3 years. But i certainly consider myself a newbie and and more than willing to learn and ask. Those that see fit to add there 2 pennys worth with asinine comments are not appreciated by me in the slightest.

---

### Post by schettj on 2008-09-11
> **scurlaruntings said:**
> 
 Those that see fit to add there 2 pennys worth with asinine comments are not appreciated by me in the slightest.
Yeah, see, this gets my gander up.

You want to use free software, you're going to have to do some work. I'm not getting paid to support you, or anyone else - neither is anyone else here.

You're asking generic Linux admin questions, nothing specific to ubnutu server. 

Installing postfix is "sudo apt-get postfix" 

Then you google for ubuntu howto postfix, and you follow the recipe. 

If you have webmin issues with postfix, you should ask on a webmin board - webmin isn't ubuntu...

What you're doing is the equivalent of walking into a laundromat, and asking about how to cuff a pair of paints. Sure, that has something to do with clothing, but other then that, it's totally unrelated.

Then you get pissed when no one answers. Then you get more pissed when someone does point out that the tailor shop is right next door.

Shrug.

---

### Post by scurlaruntings on 2008-09-11
> **schettj said:**
> Yeah, see, this gets my gander up.

You want to use free software, you're going to have to do some work. I'm not getting paid to support you, or anyone else - neither is anyone else here.

You're asking generic Linux admin questions, nothing specific to ubnutu server. 

Installing postfix is "sudo apt-get postfix" 

Then you google for ubuntu howto postfix, and you follow the recipe. 

If you have webmin issues with postfix, you should ask on a webmin board - webmin isn't ubuntu...

What you're doing is the equivalent of walking into a laundromat, and asking about how to cuff a pair of paints. Sure, that has something to do with clothing, but other then that, it's totally unrelated.

Then you get pissed when no one answers. Then you get more pissed when someone does point out that the tailor shop is right next door.

Shrug.I didnt personally ask for your support did i? This is a server support forum isnt it? YOUR the one that chose to reply with a facetious and useless answer. If you had taken the time to read my post you would have noticed that i have ALREADY installed Postfix and am in the process of trying to get Dovecot and Fetchmail to work with it. No thanks to yourself of course i have already done this.Im using webmin as that allows me to administer it remotely aswell as configure all 3 applications. Surely your aware of that? May be not.. Either way you`ve made no attempt to answer the question and instead are wasting web space with a pointless post meandering with useless analogies that have zero relavence to the case in point. "webmin isnt ubuntu".. Neither is Postfix or fetchmail or dovecot.. see how stupid you sound.

---

