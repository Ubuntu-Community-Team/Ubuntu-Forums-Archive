---
title: "Travel Techniques with Ubuntu Laptops?"
date: 2016-09-22
forum: Ubuntu, Linux and OS Chat
---

### Post by TheFu on 2016-09-22
As I travel more and more, I've built up a few techniques to deal with issues while on the road.  I'd love to learn from others.

How do you deal with computer issues on the road for 3 weeks?

Issues like:
* stolen laptop in airport security lines
* corrupted OS
* broken screens
* Security people who want to "look around" on the computer

Backups, remote access, encryption ...  any tips?

Some articles for consideration: 
* [https://www.schneier.com/blog/archives/2012/06/israel_demandin.html](https://www.schneier.com/blog/archives/2012/06/israel_demandin.html)
* [https://www.eff.org/wp/defending-privacy-us-border-guide-travelers-carrying-digital-devices](https://www.eff.org/wp/defending-privacy-us-border-guide-travelers-carrying-digital-devices)
* [https://www.schneier.com/blog/archives/2009/07/laptop_security.html](https://www.schneier.com/blog/archives/2009/07/laptop_security.html)

---

### Post by ian-weisser on 2016-09-22
My tip: Don't travel with an ivory-tipped violin bow. Or an ivory-inlaid laptop. You are sure to lose both forever.
(Elephant ivory is proscribed, Mammoth ivory is not...but do you really expect a Customs inspector to recognize the difference?)

---

### Post by coldraven on 2016-09-22
From what I've read in the comments on TheRegister, always assume that a device has been compromised at the airport (especially USA) and re-flash or or destroy it at the end of the trip.

---

### Post by TheFu on 2016-09-22
> **ian-weisser said:**
> My tip: Don't travel with an ivory-tipped violin bow. Or an ivory-inlaid laptop. You are sure to lose both forever.
(Elephant ivory is proscribed, Mammoth ivory is not...but do you really expect a Customs inspector to recognize the difference?)

I sat next to a customs inspector for a recent 7 hr flight. It was an interesting conversation.  Pork. Don't bring pork. ;) Pretty much anything in a manufactured tin or package is ok, except pork.  Any sort of cheese is fine (except some really odd ones that would be very hard to get anyway).  He was sent to specialized training for a few months with mandatory refresher classes annually.  His background was as a botanist.  His wife worked for RSA - didn't have much to say. She was a Unix nerd. 

[QUOTE=coldraven]From what I've read in the comments on TheRegister, always assume that a device has been compromised at the airport (especially USA) and re-flash or or destroy at the end of the trip.[/QUOTE]
Odd. I assume the same thing when entering Canada or China if a device is ever outside my control.  Entering the USA, only once has my laptop/netbook been out of my sight - it was stolen at the security line (completely encrypted, so just a HW loss).  My company had a device swap policy for traveling to China - They had cheap phones we could take and cheap, empty laptops for the trip.  Evil maid attacks was the concern.  We'd be debriefed on return - sorta like after meeting a foreign national when I worked in a DoD clearance job.  I don't worry about US customs seeing stuff on my machines much.  I've never heard of the USA providing corporate information from knowledge gained during these searches to US companies. I have heard of the Indian and French governments and many smaller governments feeding local companies information, however.  Whether any of this is true or not is hard to prove.  Then again the NSA are masters at getting data that isn't shared elsewhere: [https://wikileaks.org/nsa-france/](https://wikileaks.org/nsa-france/)

Now I don't know what to think. ;(

How do you travel securely with a computer?

---

### Post by Geoffrey_Arndt on 2016-09-23
I guess all that can be done is to reduce the risks. 

>  As you've already written . . full disk encryption,
>  Remove Bookmarks and Disable ALL syncing,
>  Disable ALL auto logins on browsers especially for webmail/pop3 mail mail access,
>  Setup a white list filter via apps/plugins such as ublock and/or iptables,
>  Disable usb port access/boot via the firmware

Another variation of above - only have a portable OS via a fully installed Ubuntu on usbv3 SSD (not LIVE OS) like the SanDisk Extreme 500 which you can carry on your person at all times.

IF I still travelled a lot like I used two, I would do a customization of all the above, especially using the SSD.   I think it can be set up to be reasonably easy to use and safer than many other options.

---

### Post by TheFu on 2016-09-23
I avoid using cloud stuff. No cloud storage. No email (for important things), no social networks. This place is about as social as I get. ;) 
The only sync I do is via rsync between systems I control.  

Don't really use bookmarks. Doubt anyone cares that I read Krebs, Friday Squid blog, or my own blog.

Never used auto-login stuff in browsers or to login to any Unix system. Browsers aren't to be trusted, especially google-chrome, but as they've become more complicated, they've been unable to be secure. Dillo is a nice, simple, browser - don't trust it for SSL stuff. Opera has been adding interesting features, but those tend to bite them in the **** a year later when issues are found.  I don't plan to ever use the opera VPN.

If we disable USB ports, then we can't use external storage for boot.  Plus, I don't have access to any BIOS on the chromebook, so that really isn't an option.

My systems all have a huge, blocking /etc/hosts file.  About 12K sites last time I counted.  Updates happen centrally through ansible - that is consistently good or consistently bad.  I suppose removing DNS and only putting in white-listed internet domains would be possible. Probably too much work with all the included, included, included files.  I do run certificate patrol and really watch reported changes when on travel.  Unfortunately, big sites change their certs daily.

I use different browsers for different tasks and often run inside firejails with different settings. Usually using the --private option so nothing, zero, nada, is written to disk.  This way the "private window" bugs that have been common in all the major browsers don't impact me.  I find it refreshing to login to my bank's website with a fresh browser every time.

Sadly, my chromebook will not boot from USB3.  Also, sadly, if any storage device is connected to the USB3 port, it won't boot at all. So using a USB2 drive with /boot to access the USB3 storage with the encrypted OS/data won't work either.  I have a 128G [m2.SSD inside a USB3 enclosure]("https://www.amazon.com/M-2-NGFF-SATA-SSD-Enclosure/dp/B0146DD6KM/") ... for that purpose. Too bad it doesn't work.  It is encrypted with dm-crypt and requires a yubikey to enter the 2nd half of the decryption passphrase (something i have + something I know) - or is the the first half?  I always forget.

I love my chromebook except for that aspect.  Core i3, 8+ hrs of real use on battery, 1080p screen, less than 3 lbs. It really is amazing. They sell a fast Celeron version for $100 less which would have been absolutely fine for my needs.  Really, I just need an x2go client from the chromebook. All other uses can be handled via chromeOS and encrypted crouton install accessed as guest login.  The encryption used by crouton is better than nothing, but not strong enough for border crossing, IMHO.

Good stuff in this discuss.  Had a similar discussion a few years ago inside my defcon group.  Most of them had decided that traveling without any computing devices was the best solution and buying something cheap on arrival the best method internationally.  Get your cell phone in China and expect all use to be recorded was their stance.  Guess I should assume the same inside the USA.

---

### Post by Geoffrey_Arndt on 2016-09-23
Interesting . . but . . "avoid using Cloud stuff" . . . . and then running a Chromebook?  

I had an Acer c720 Chromebook . . with Celeron and small 16 gig ssd.   Ran great, but I grew frustrated with ChromeOS  apps.   Got rid of it although I should have tried crouton.   Linux kind of spoils you.

So,  no Windows at all any more for me (I'm retired) . . . but I love dual-booting via usb stick and usb ssd.    Full update/security support provides the incentive for running off an installed external mini ssd.

---

### Post by DuckHook on 2016-09-23
@The Fu

It's a shame you didn't post this under the security sub forum. While it is admittedly something of a free-form discussion, it touches upon very practical and useful issues for the road-warrior. Your measures already taken are especially useful (though guru-ish in the extreme).

Like Geoffrey_Arndt, I've also been retired for years. If a bad guy steals and gets into my laptop, s/he is free to rifle through my innocuous pictures, old '60's rock songs and mind-numbingly boring emails. Irrespective, I still encrypt all data on a separate partition with a very strong key that makes it hardly worth their while. As a purveyor of ancient equipment, I only take really old and beat up laptops travelling. Since the old beater will likely fetch only a few dozen bucks on the market, the incentive to steal it is also greatly diminished.

But for road warriors who must carry around powerful laptops as an indispensable work tool, I can definitely see how my strategy won't work. So, full disk encryption is important. However, it may interest all posters to read the following:

[https://twopointfouristan.wordpress.com/2011/04/17/pwning-past-whole-disk-encryption/](https://twopointfouristan.wordpress.com/2011/04/17/pwning-past-whole-disk-encryption/)

The author is ingenious in how he cracks even properly formed full disk encryption. So, for the really paranoid, or those who handle super-sensitive information, make sure your /boot resides on a separate USB key (or perhaps 2 separate ones for backup). The Fu already does this. I thought it might be useful to post a link as to why.

---

### Post by TheFu on 2016-09-24
For me, the chromebook was about cheap hardware.  Never logged in on it using a gmail account. Always guest. Don't really use google stuff all that much - tried to find a use for their storage and always felt "dirty" using it even with 200G free (came with the chromebook).  

That means I couldn't load any chrome-apps.  Yes, privacy means THAT much to me. My current chromebook ran crouton for about 3 months before I became too frustrated not having access to kernel modules (NFS especially) and wiped chromeOS for a lite Ubuntu (no DE).   I had an Acer C720 too. Great first-time chromebook that ran Ubuntu nicely.  The keyboard eventually became useless and my attempts to fix it cheaply failed. It is a paperweight now. I miss the 1440p screen my cheap Dell laptop had in 2006.  All the "HD" and "F-HD" marketing screwed over laptop users all this time with terrible resolutions.

I'm mostly retired too (20 yrs too young to claim full retirement), but take a few odd jobs and stay active in both the Linux and Security communities. 

Good point about booting off portable devices when using whole drive encryption.  I know they are working on a verified, validated /boot. Think they have it for other distros, but like a boot sector virus, if we don't control that, even with encryption, we've lost the beachhead and can't trust anything on the system - look up "evil maid attack" if you'd care to understand more. In short, a keylogger can be added to the boot process while we shower, even on an encrypted setup.

Today, I think that ChromeOS running on a chromebook is probably the most secure network OS available. The setup is really impressive, only issue with it is ... er ... google. They sign the OS, mount it read-only, sign updates and the BIOS validates the signatures. User storage on chromebooks is encrypted too.  Hopefully, they didn't make the same mistake with the encryption on ChromeOS as they did on Android (which can be broken according to reports).  The experience using the guest login is really excellent. I can see how people using it with a gmail login could love the devices. Everything works as it should, within the limitations of chromeOS. I think chromeOS is the reason Logitech decided to make their webcam's work with Linux too. ;)  Previously, my C920 webcam was very flakey, but since chromeOS became mainstream, it has been working with regular Linux installs perfectly.

I didn't post in the security section because I expected not to have 100% facts and wanted some wild-crazy ideas shared.

People don't realize how important an email account is to their online lives.  If a bad person gets control of your main email account, they can reset passwords for your bank, brokerage, online shopping, and other online accounts.  If the stolen laptop has access to the email account used to authenticate your bank .... game over.  Folks need to lie about those extra security questions. Never use the correct answers - pet, high school, grandparents names ... all these things can be discovered with just a little searching online. Lie, lie, lie - and use a password manager to store those lies securely - different lies for each account too.

We haven't mentioned that using a VPN or ssh-tunnel is always required when on networks we don't trust/control. Don't use DNS to resolve hosts when away either - use IPs for the VPN access point and force all DNS queries down the VPN channel to avoid nasty DNS side-attacks.

Being secure on a computer and online and on travel is hard. Nobody said this would be easy.

---

### Post by DuckHook on 2016-09-24
> **TheFu said:**
> &#8230;People don't realize how important an email account is to their online lives.  If a bad person gets control of your main email account, they can reset passwords for your bank, brokerage, online shopping, and other online accounts.  If the stolen laptop has access to the email account used to authenticate your bank .... game over.&#8230;which also gives the lie to my statement about how "innocuous" my e-mail is. Sobering consideration and food for thought.> Folks need to lie about those extra security questions. Never use the correct answers - pet, high school, grandparents names ... all these things can be discovered with just a little searching online. Lie, lie, lie - and use a password manager to store those lies securely - different lies for each account too&#8230;I learn something new from you with impressive frequency. I've never really thought about this one, but when you put it the way that you just did, it makes lots of sense.

A curiosity question: many people will say that all of these measures may be *theoretically* useful, but in the same way that a howitzer will effectively kill a fly. That is to say, it's gross overkill that protects against insignificant risk at the cost of major inconvenience, system brittleness (what happens if I lose the USB key?), and not a little hubris (why would sophisticated crime rings, to say nothing of shadowy three-letter organizations, be interested in a boring retired grandpa?). I mean, as much as evil maid attacks may be theoretically possible, they aren't very plausible for the average Joe. So why go to the trouble of taking such&#8213;by any measure&#8213;extraordinary precautions?

---

### Post by TheFu on 2016-09-24
> **DuckHook said:**
> …which also gives the lie to my statement about how "innocuous" my e-mail is. Sobering consideration and food for thought.I learn something new from you with impressive frequency. I've never really thought about this one, but when you put it the way that you just did, it makes lots of sense.

I can't take credit for anything. Learned it all from much smarter folks. Every few years I ask questions about this to get more ideas.

> **DuckHook said:**
> A curiosity question: many people will say that all of these measures may be *theoretically* useful, but in the same way that a howitzer will effectively kill a fly. That is to say, it's gross overkill that protects against insignificant risk at the cost of major inconvenience, system brittleness (what happens if I lose the USB key?), and not a little hubris (why would sophisticated crime rings, to say nothing of shadowy three-letter organizations, be interested in a boring retired grandpa?). I mean, as much as evil maid attacks may be theoretically possible, they aren't very plausible for the average Joe. So why go to the trouble of taking such&#8213;by any measure&#8213;extraordinary precautions?

[https://en.wikipedia.org/wiki/Nothing_to_hide_argument](https://en.wikipedia.org/wiki/Nothing_to_hide_argument)  - there are people who DO have things to hide and we all need to help them out by demanding our privacy whether we have something to hide or not.  
Use TOR, even if you don't need it.  
Use a VPN, even if you don't need it. 
Use gpg encrypted email, even if you don't need it.  
Someone you know probably DOES NEED that added privacy. Think about people with unpopular ideals anywhere in the world.  Like women should be allowed to drive cars or almost anything religious or about gay people and their rights or anything negative about any nation/state.

---

### Post by simonsaysthis on 2016-09-25
Interesting discussion. Will read up a bit more of this as I certainly don't fear somebody looking at my music and family pictures.

---

### Post by mastablasta on 2016-09-26
laptop gone at airport security? it's supposed ot be one of the safes places in the building. :shock:

and our company notebooks have win 10, non encrypted and there is no backup done at work. got myself a small USB key and i am now doing backups at regular intervals. in case it get stolen i will demand all data be returned to me from "company's backup solution".  :-) 

if really stolen among others you would get access to most drawings, plans (at least basic ones), prices, top secret contracts, various sales conditions...

---

