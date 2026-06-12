---
title: "web based email breached?"
date: 2012-10-06
forum: Security
---

### Post by alvinmoneypit on 2012-10-06
Hi,

I'm running Ubuntu 10.10 using Firefox 9.0.1.  My Yahoo email was compromised the other day.  Yahoo service says an IP address in Mexico corresponded with the attack.  They got my contacts and spammed them - not just my address book, but everyone I ever contacted , which puzzles me as I use Yahoo classic mail, and the contacts are hidden I'm not sure how I can access them.  

Anyway, I was wondering if this was a vulnerability on my computer or was Yahoo compromised or perhaps my DNS server?  I changed the password on my Yahoo account (which I've had for probably near 15 years).  
I don't see any damage to my system or files, perhaps they were just using me to spam.  My computer hasn't been slowing down, however it refused to 'sleep' or hibernate until I rebooted, now it works as before.

Is this anything I need to change besides the action I've already done (changing my password)?  I run Clam TK and have configured the firewall well before this breach.  Sorry I don't know more about security and counter measures.

Below is the header of one of the emails:

```
X-Apparently-To: 		[email]me@yahoo.com[/email] via 98.138.85.242; Thu, 04 Oct 2012 11:53:47 -0700
Return-Path: 		<me@yahoo.com>
Received-SPF: 		none (domain of yahoo.com does not designate permitted sender hosts) aW5zL2FkZC1mcm9tLXNlcnZlci9pbmZvLnBocD9hdHRhY2hlZDI2MS5qcGcg ATABAQEBA3RleHQvcGxhaW4DAzACA3RleHQvaHRtbAMDMQ--
X-YMailISG: 		upabsv8WLDuP_W0fOHF2.B9WkwobM8JRzutq6rgLnwBEx.NN 3sNQnt5h1noZYVuC25mAsGc.aYo8jVoMve3nQ8fnRnaUGusMenXLMZYVVKYO oMxDkgp_sMAkssQW4MGmfGMna58uhLvs7Av3cYxo8vXx1UlWDR6HwmxxzzR8 _CLTuqvkaLdvOZ5hjIAKlGffsa6fjdyEsfP1wSCpLPMgXCP7nbnYeCtncBFC DnE.G69z68xIhjrqV2WkBzH23PXLrkdt0YPVP6RldWA0paBhESfhuiCxFklc .4HHLfDv4Xk9eq.Ol9HXbq_2A..frkktWuzdu1mesVvaPegcSfr3cBD1qOmf avq.SLb2b88_wJWrc2Qt8nJLnDCyxPlc6w5Sr1wWX98KQizdK3WdJcfaKpnR .9iL7lJIWiuNQ8FcM9H7dPuKZ_QCBua5V55I9BQf.9j_aT4rY.pRVwyHVysz oEy4imvWk8hDFX57nc3thxFDMl3cl5_AgJl37xxmj4SBnY9yXh4ffi0RDRsn MiQY1IQVf6F.nkE6pApPZQDX7HvcV5qYXn513m91ahy8U_Y8bVizLI3v952J q5VKxvUYXyg_lcvGmPgmlZBa6TdEYFNHKyFIrLpasP4lDOtOJVNeYN5W7_78 6M1ujSDiUgUalSYgtLm5L6OVAlCe17jPkxYL2MeJEaa.AoOOD_F.GYZDDT7l TG3B5U4jssUFBcum0QLyINe3Xkub35zhltIg38IydkVQfZhHpLMAc4XRiDC7 pGrddW9Oj2pIkY.sJRdh_FEe5mw8kL47xyJhL.jT222uwFr8Km3mOjhQYIUX bW7gruNXP2kBQp31M.Cyhcq3e0.NXuVdOjyeYk6JZKZ8mELHXFJmNhpHsuQI 2bvcwQdJFD7Z5zmwUFGz9o8pi_bADUZ27kwWRMEat4U5B68lqF11HXZmvg3G iW.kvlb8YHU1vJgEAwSKdxdzTSbpUt8FJ9C9a65LZ.pYA93tE89EOd8RVO9X n8Nms1CRElm__6kyFuAFv7OuLNQOrp7H9o4bknGViwzuCdtuaHIXnIMe9A7x 1EsoAYnxFiG6bV4L1PNzTX0Kbmmc4dxZsu1Xh41F6l4-
X-Originating-IP: 		[98.138.90.78]
Authentication-Results: 		mta1354.mail.bf1.yahoo.com from=yahoo.com; domainkeys=pass (ok); from=yahoo.com; dkim=pass (ok)
Received: 		from 127.0.0.1 (HELO nm15.bullet.mail.ne1.yahoo.com) (98.138.90.78) by mta1354.mail.bf1.yahoo.com with SMTP; Thu, 04 Oct 2012 11:53:46 -0700
Received: 		from [98.138.90.54] by nm15.bullet.mail.ne1.yahoo.com with NNFMP; 04 Oct 2012 18:53:45 -0000
Received: 		from [98.138.89.174] by tm7.bullet.mail.ne1.yahoo.com with NNFMP; 04 Oct 2012 18:53:45 -0000
Received: 		from [127.0.0.1] by omp1030.mail.ne1.yahoo.com with NNFMP; 04 Oct 2012 18:53:45 -0000
X-Yahoo-Newman-Property: 		ymail-3
X-Yahoo-Newman-Id: 		[email]636703.67324.bm@omp1030.mail.ne1.yahoo.com[/email]
Received: 		(qmail 2855 invoked by uid 60001); 4 Oct 2012 18:53:45 -0000
DKIM-Signature: 		v=1; a=rsa-sha256; c=relaxed/relaxed; d=yahoo.com; s=s1024; t=1349376825; bh=Xy8SnXya7pjJ4CV80+IYC08v3p4NouVtmXVzi8yIaYY=; h=X-YMail-OSG:Received:X-Mailer:Message-ID:Date:From:Reply-To:To:MIME-Version:Content-Type; b=mUlwKlsCt/ejkbobulrN25Rs7k1u4b8PU8AV7lUxtMZM28AzxQu6l0dzUY1uvlOLRiXV16dsInGlCRkd6bborAvJHEWVCDhhj8xi0hPz/zdhTJwGqr8iLIeDWHMUX/5kqZXMWvRm6oPh7HWVE7GQIgBrqq3egW+WxoNTBiCeOPQ=
DomainKey-Signature: 		a=rsa-sha1; q=dns; c=nofws; s=s1024; d=yahoo.com; h=X-YMail-OSG:Received:X-Mailer:Message-ID:Date:From:Reply-To:To:MIME-Version:Content-Type; b=xqjMmb+itrTAIKERjUwIPEqPd5lpzBu9NdxHT3LXbAHM28qUx6VwBXdxtqMrDkU/T4N0JcL8F/V076JzdVVp2JZLH8FlihXQK86jsYzc6BEpgCZR9wl+dkFCxxrRFzo99iwUql1fjgjqurPMDtntmL/npq82/6R/abXZ+qeIk6I=;
X-YMail-OSG: 		ZD0HixsVM1mF8Q59fsOHEkt7EAOfsMK11Ijt2zH4UcwD0fZ LaSb2hfNGO7wC0hbZNVA0wJ5Cy6V_PpAc0IDNaHVp8_jx.1dTJw7QjdNLUsk EF_D8k4IDNktWLFu5YfUqSwEKnHfUUjNLg2EuSY0CXvh6MtkVJYbQi1EquiL fuPS1RRAOF8xBHISKafPOdAaaya.KAPrCIB4xK_QWO6b8JLhu.NA08HTsyD3 fZJldyWFrQv56QeYtzpuUpIvvU4ix0_dezt6swjR3K5x8WgSOSWcEqlqaAfI u.N8MMtyUzJm.iuMREhQH6Midgm1LvMRRI9uYacPRlroCyAB7L4vaFS5Yrvf Uv7.CfI5E3ARM.KTsZC.1WKf2Eq3NIsuizMbMN1zb6ZqL72ai5AIWEj_1JVt 56OJPXatnVKeNp1qZcWtAFryALhaUNcQpjOEXmmtHsZiMkBaGuxMaCn.znza 4UL_u5GMHC1foFJ201BV2bSJO2qbzcIk7m2K17PCDILysjzpdSVICtD5_1Z. UIU.ITXUfPeIlbZmTlGCC29Qsm1_f_5AgNh1usb1y5hq7X5BAPh.KAaSk6Tl FUwTY6Awa2UYDtiUwrqaTr3SxhPh8jSEl9ZnMQiqFf.J26ld.Bhvu3Ebxr90 -
Received: 		from [189.175.200.16] by web120505.mail.ne1.yahoo.com via HTTP; Thu, 04 Oct 2012 11:53:45 PDT
X-Mailer: 		YahooMailWebService/0.8.122.442
Message-ID: 		<1349376825.86122.YahooMailNeo@web120505.mail.ne1.yahoo.com>
Date: 		Thu, 4 Oct 2012 11:53:45 -0700 (PDT)
From: 		This sender is DomainKeys verified
"me@yahoo.com" <me@yahoo.com>  
View contact details
Reply-To: 		"me@yahoo.com" <alvinmoneypit@yahoo.com>
To: 		[email]nels.lippert@wilmerhale.com[/email], [email]me@yahoo.com[/email], 
MIME-Version: 		1.0
Content-Type: 		multipart/alternative; boundary="1874583742-1497240135-1349376825=:86122"
Content-Length: 		639
```

---

### Post by alvinmoneypit on 2012-10-06
Sorry about the icons in my header quote, the shortcuts must be in the original and I don't know how to prevent them from appearing.

---

### Post by lisati on 2012-10-07
> **alvinmoneypit said:**
> Sorry about the icons in my header quote, the shortcuts must be in the original and I don't know how to prevent them from appearing.

"fixed" that for you by adding "code" tags. 

Change your email password a.s.a.p.!!!!!!!

If the X-mailer header was something other than a fairly standard Yahoo webmail header, I'd suggest running the headers through a tool such as [http://whatismyipaddress.com/trace-email](http://whatismyipaddress.com/trace-email) or [Spamcop]("http://spamcop.net")'s reporting service to help you track down the sender.

---

### Post by Cheesemill on 2012-10-07
It may be possible that your machine has been compromised in some way.

Ubuntu 10.10 reached end-of-life 6 months ago and as such hasn't received any support or security updates for all of this time. Your browser and OS will have been unprotected from any newly discovered exploits and security vulnerabilities.

---

### Post by bra|10n on 2012-10-07
If you've been a long time user of Yahoo email then you would have also noticed the sudden rise of spam in your inbox over the last 12 months, 
including the almost monthly 'user survey' from Yahoo asking you to "tell them how they're doing".
Let me tell you, there's nobody home at Yahoo. 
The lights may be on but Yahoo has become nothing more than a clearing house for CEO's. Is it 5 now in 6 years?

Many people have concerns about sharing their personal data with Google.
On the other hand, Yahoo via incompetence shares your data with everyone.

Find yourself a new web-mail account :KS.

---

### Post by tubbygweilo on 2012-10-07
alvinmoneypit, A change may well be in order, If your data is backed up then would you consider at least a fresh 12.04 install with all that accrues from the security updates?   As for your email you may well wish to consider moving to Gmail [(Privacy T&C)]("https://mail.google.com/mail/help/intl/en/terms.html"), Gmail offers import tools that allow you to load an address from you last email provider. I would also ask you to consider Mozilla Thunderbird (+Enigmail) on you nice new system as I have found that the spam catching powers of Gmail and Thunderbird work rather well together. 

When using Gmail I have only the Gmail service open, I do not allow Google to connect email accounts, products and services  together and upon ending a Gmail session I close or flush the browser and open again for other business. Google do read you mail but it is done in the chance or matching keywords with advertisers, just learn to ignore the few adverts that do appear. If you wish to be secure than conduct all email exchange via Thunderbird Enigmail (gnupg encryption).

Remember, Google look at your key words for advertising revenue but security people look at un encrypted headers to see who you are in contact with and this is common to most if not all email systems.

All the best with you new secure & spam free system.

PS Be sure to use a long, strong password. Longer & stronger the better.

---

### Post by OpSecShellshock on 2012-10-07
Going by the activity you mentioned it seems most likely that someone else accessed your account rather than hijacking one of your existing sessions, but it's really hard to say for sure since we don't know a lot of the contextual circumstances around it (i.e. have you also accessed the same account from other computers/devices/networks, have you logged in from open wifi anywhere, etc.).

Sent items are usually stored by webmail services, so it would be easy to get a spam message out to anyone you'd sent an email to if someone else logged in as you. However, I don't think a simple brute force would work well for the simple reason that Yahoo seems to limit failed attempts from unexpected sources, and will lock the account if there are too many of them. The fact that the spammer succeeded strongly suggests that they did so within the available number of attempts.

So here's how these things usually go: you use your email address as your username on some other web-based service, and that service gets compromised and its data gets leaked, resulting in someone having a list of user names and passwords where the user names are also email addresses. Statistically, a large number of those users will re-use the same password for multiple services, including email, and the passwords will either be dumped in plain text or in an easily-cracked hash format. Then it's just a matter of trying the leaked passwords on the email accounts that match the user names and seeing what happens.

There are two fairly easy things you can do to counter such a thing: use a different password for every service and select passwords that are at least 16 characters long (the number of characters should be expected to increase over time, because technological developments make automated password cracking easier and faster).

---

### Post by alvinmoneypit on 2012-10-07
Thanks for all the replies.

1) I rarely access this account from outside my home computer or laptop.  I do access it travelling with my laptop.  I don't access it with phones or other devices, I might have used a work computer once or twice a very long time ago to check this email account.  

2) this was an easy password to figure out and I use the same one on bland technical forums such as this one.  It is 6 non capital characters and number mix which many could figure out w/o and artificial cracking means.  Frankly, I'm surprised that it survived this long.  

3) I changed my password within the hour as I was currently using the computer at the time it was compromised,  I leave the browser open always with a tab on this logged in email account until the sleep function kicks in which is set to 2 hours.

4)  The offending spam sent from my account never showed in my 'sent' folder.  That's why I wonder about yahoo system problems, etc.

5)  I've had no discernible attacks or compromises since the 2 emails sent.  It looks like the attacker gained access to my account and sent his/her spam within seconds and left. The spam was 2 separate emails with containing single url's with no text sales pitch.

6)  It bothers me a little that my computer wouldn't sleep despite a long period of inactivity - it always sleeps or the monitor becomes inoperative after the set time expires.  Rebooting appears to return the computer to its normal operating condition.  Should I be concerned with implants that may have been left like password harvesters, keyloggers, etc?  How do I find them on this system if I need to look?

7) I've been looking at sites trying to learn how to read the headers and isolate the offending IP, and isolate the sender if possible.


8.  OpSecShellShocked-  Thanks for your analysis.  I recognize this as a vulnerability, so I rarely use my email address as a user name in other places, however I admit that I'm sure it has occurred accidently because of carelessness or the default nature of some websites.  I don't use that password for such cases, I use another password which I try to apply to all such instances.  As mentioned earlier, I did use this password on unrelated sites, but haven't used it for years on the sites I've since signed up to.

9.  I don't want to upgrade- only as last resort.  It may sound childish, but every upgrade or security update, whether Ubuntu or windows frequently caused problems with computer freezes, loss of function of some programs or reduced function.  The old and cheap character of my components are an admitted likely cause IMO.  Yet my system always seems to work so smoothly when I don't accept updates or security fixes, so I haven't used them for years.   

I think I can still get around 183 MB of updates for this system, I'd rather upgrade.  Upgrading usually takes a week or two to get all the hardware functioning properly again.  As I'm not a geek, or proficient in this OS, I spend upgrade hours perusing these forums or googling or posting questions as I've done here to get the upgrade working.  I'd rather spend these last few days of mild Ohio fall weather preparing my home for the colder season. I don't bank online or pay bills online so I'm not concerned with being financially ruined due to breach, but I don't like strangers in the house, and am enraged a goon got in and used my account to spam friends and acquaintances.

---

