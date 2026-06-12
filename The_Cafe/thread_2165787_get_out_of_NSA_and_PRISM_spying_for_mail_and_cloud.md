---
title: "get out of NSA and PRISM spying for mail and cloud services"
date: 2013-08-06
forum: The Cafe
---

### Post by oleanj on 2013-08-06
Hi. Just read in some articles about spying from NSA and the PRISM program [http://www.theguardian.com/world/2013/jun/06/us-tech-giants-nsa-data](http://www.theguardian.com/world/2013/jun/06/us-tech-giants-nsa-data)

SO, I'm playing with the idea to ditch some of the services from the tech giants (like google email, google calendar, dropbox).

I have to switch from google mail - And the best thing would (maybe) to host my own email server.
Then get rid of dropbox to sync pictures, personal files, and so on from multiple PCs, android phones and iphones  to my local cloud - And the best would be to host my own personal cloud service.

I do have a ReadyNAS Ultra 6 for storage (the newer ReadynNAS has build in cloud solutions for home users).

If I buy a cheap server, for example a HP ProLiant MicroServer [https://ssl.www8.hp.com/us/en/products/proliant-servers/product-detail.html?oid=5336619#!tab=features](https://ssl.www8.hp.com/us/en/products/proliant-servers/product-detail.html?oid=5336619#!tab=features)
and install Ubuntu Server then setup the build-in email server from Ubuntu, and install a cloud solution from Ubuntu. There is a opensource solution from [http://owncloud.com](http://owncloud.com)  but it has no support sync clients for mobile devices.
And I don't know if it a simple process installing my own home cloud solution from Ubuntu, that supports sync clients from windows, mac, iphone and androide phones?

The best solution is of cause to buy a physical box that has cloud, email, http (and so on) prebuild, and use some wizards to set it up, but I can not find such a box.

Any idea how to create my own personal cloud, email and http server?

---

### Post by Hylas de Niall on 2013-08-06
Seems like an awful lot of effort to hide from the NSA/Prism.
Are you doing stuff you shouldn't online? :)

I really don't think it's that big of a deal (though i hate the 'big brother' angle to it), what do i care if the NSA can see my emails and family photos?

Ta.

---

### Post by donovan1983 on 2013-08-06
Just for the heck of it I tried setting up a "personal cloud" over the weekend. I wasn't planning to actually use it since I like Google's, Dropbox's, and Evernote's solutions quite a lot, but I figured it'd be educational and it certainly was. I did get ownCloud installed as well as Postfix, Dovecot, and RoundCubeMail for email. It worked fine even though using a self-signed SSL certificate is not ideal. It didn't work nearly as well as the hosted solutions I already used, though, and dealing with a secure backup of that data was anything but trivial. It also was undoubtedly less secure than hosted solutions (one machine doing too many functions and no dedicated firewall machine). Reduced functionality with reduced security and vastly increased chances of data loss are not good trade offs for an increase in perceived privacy, in my opinion.

Google may mine your data to serve you ads, but they have entire teams dedicated to keeping your data secure. After all, if they had a reputation for not keeping your data safe they'd lose market share pretty quickly. I highly doubt that these companies have some secret government backdoor since that'd be a huge security risk for them. However, I have absolutely no doubt that they are also complying with all legal requests for users' data and may even have a streamlined process for it. You are not immune to legal requests for your data if you run your own personal cloud or even if you bow out of the whole cloud thing and keep your data on your own personal computers. I'm no fan of the idea that multiple governments are trying to spy on internet activity. I'm just far less worried about that than the idea of hackers (script-kiddies, really) or identity thieves gaining access to my personal information.

---

### Post by buzzingrobot on 2013-08-06
The net is a public space, so everything on it is, one way or another, available if someone wants to go to the trouble of chasing it down. That includes standing up your own physical server, buying the bandwidth, registering domains, administering the thing, and keeping up with security fixes.

Do you have the time, money, knowledge and skill?

For me, I'm not interested in being a sys admin unless someone pays me.

You *can* resort to encryption techniques with a closed circle of other users who also use it, assuming you all are trustworthy and know what you're doing.

The smartest thing to do is use common sense and avoid publishing on the net anything you would not print out, sign, and staple to a public bulletin board. ("Publishing" is the right word.  It's not point-to-point communication.)

You didn't mention cellphones, but... They're little radios, you know, transmitting on the public airwaves. How private can that really be?

---

### Post by Paqman on 2013-08-06
> **donovan1983 said:**
> Reduced functionality with reduced security and vastly increased chances of data loss are not good trade offs for an increase in perceived privacy, in my opinion.


This, plus the maintenance burden. How much is your time worth? If you've not run a server before you've got a huge amount of reading, learning, configuring and tweaking to do. It'd be worth doing for the sake of an educational exercise, or if you have plenty of free time and can afford to sink it all into the project, but in order to do it just for privacy you'd have to put an *extremely* high premium on your privacy.

As always the cost/benefit equation will break down differently for everyone, but it's good to be aware of it at the start.

---

### Post by slw210 on 2013-08-06
So what was the purpose of driving around tapping into personal information through wireless connections (Google Street View)?

But, I agree with it being too much trouble just to avoid the NSA, etc., there are other more secure/private cloud services.

---

### Post by pqwoerituytrueiwoq on 2013-08-06
ever consider using UbuntuOne for cloud storage?
mega.co.nz claims to be really secure

If you use your own email server they run through your ISP, also last I tried doing that there was a 15min delay getting it to my gmail account
i was using PHP's mail feature

---

### Post by grahammechanical on 2013-08-06
> [COLOR=#000000]that supports sync clients from windows, mac, iphone and androide phones?[/COLOR]

And you still want to use that stuff? Extraordinary! Ditch mobile devices and wireless connections. Run your own landlines. Wrap everything in aluminium foil.

---

### Post by QIII on 2013-08-06
Just a friendly reminder:

We have been more lenient with discussion of political matters as they affect technology/privacy issues and the open source community.  These are important matters that bear some discussion.

However, I have just closed another thread that wandered too far into the purely political.

This thread doesn't look like it has gone that direction and is more a discussion of security.  Let's keep it that way.

If it starts to get into rights afforded by different countries under their laws, the relative merits of those laws, the motivations of various governments, etc, the line will have been crossed.

For my fellow Americans:  The US Constitution applies only where the legal authority of the US extends and not to the countries where many forum members reside.  Therefore, discussions of rights guaranteed by the US Constitution are inappropriate political discussion on the Forums.

---

### Post by ssam on 2013-08-06
mailpile looks like it could be a very nice solution to email part.
[http://boingboing.net/2013/08/04/mailpile-crowdfunding-a-secur.html](http://boingboing.net/2013/08/04/mailpile-crowdfunding-a-secur.html)
[http://www.indiegogo.com/projects/mailpile-taking-e-mail-back](http://www.indiegogo.com/projects/mailpile-taking-e-mail-back)

you might also like to look at freedombox [https://www.freedomboxfoundation.org/](https://www.freedomboxfoundation.org/)

---

### Post by CharlesA on 2013-08-06
> **Paqman said:**
> This, plus the maintenance burden. How much is your time worth? If you've not run a server before you've got a huge amount of reading, learning, configuring and tweaking to do. It'd be worth doing for the sake of an educational exercise, or if you have plenty of free time and can afford to sink it all into the project, but in order to do it just for privacy you'd have to put an *extremely* high premium on your privacy.

As always the cost/benefit equation will break down differently for everyone, but it's good to be aware of it at the start.

Pretty much this.

I have my own server setup in a VPS, and have most of those services running on it, but I still use gmail for my main email. It's easier for me to manage it there.

---

