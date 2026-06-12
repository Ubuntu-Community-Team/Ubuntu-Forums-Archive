---
title: "Stolen laptop recovery ideas"
date: 2009-06-01
forum: Security
---

### Post by N1c0_ds on 2009-06-01
Since I'm going to college next year, I will need to carry my laptop around and I'm not too comfortable with it. I heard of all the recovery services, but I'm looking for a more direct approach that could help me recover my laptop quickly. I started brainstorming the idea, trying to find the best way to locate the laptop and the thief without any costs.

**1-Webcam+script+cronjob**
Since most laptops have a webcam, all we would need is a webcam application that can run transparently from the command line. The script would take and email a photo of the user once a week along with its IP address and other information.

All we need is a capture software that can run from the command line :S

**2-Firefox saved passwords+script+cronjob**
Since there are so many ways to synchronise passwords with Firefox, a simple plugin could sync all the passwords with a server. Someone who steals a laptop will invariably use the 'net and eventually enter its own username on a few website. From then, all there is left to do is to follow the idiot and track his ***.
[B]
3-Fake link to script[/B]
This one is a bit more abstract considering a lot of people use Firefox, but it could still work with those who never used linux. I'd put shortcuts on the desktop that look like Internet Explorer and MSN icons, but those would instead open a script that sends all the information necessary to me by email before launching Firefox and Emesene.



I'm truely open to any efficient way to recover a Linux laptop, since most utilities are only available for a fee or for Windows.

---

### Post by benj1 on 2009-06-01
theres a program adeona that does what you want, the problem is login, unless you login automatically they won't be able to login and so reinstall something else. you would probably be better locking the bios to prevent booting from cd or usb so atleast they have to replace the hard drive.

---

### Post by aysiu on 2009-06-01
Doesn't this all assume the thief isn't just going to install a new operating system on it right away before selling it as "used"?

You'd have to be extremely lucky for your IP-webcam thing to work... lucky like this woman:
[http://www.smh.com.au/news/technology/mac-thief-caught-on-webcam/2008/05/12/1210444306538.html](http://www.smh.com.au/news/technology/mac-thief-caught-on-webcam/2008/05/12/1210444306538.html)

---

### Post by DGortze380 on 2009-06-02
A frequent DynDNS Update would help you gain access as soon as it's connected to the internet.

---

### Post by scorp123 on 2009-06-04
> **N1c0_ds said:**
> Since I'm going to college next year, I will need to carry my laptop around and I'm not too comfortable with it. ...  I'm looking for a more direct approach that could help me recover my laptop quickly.  Not very likely. Out of experience I can tell you that a thief will most likely wipe your OS or even take out the harddisk and then try and sell your laptop as "used" e.g. on eBay. They are not going to bother to mess with your OS installaton ... costs way too much time and offers little gain for a normal thief. So once your laptop is "gone" it's highly unlikely to ever go online again (unless you maybe used Windows + auto-login + no password??) so all the methods you might try to implement are in vain.

What should worry you is your privacy. If your laptop contains pictures, documents, login info, credit card numbers, private messages, etc. then you should consider using harddisk encryption. That way a thief at least won't be able to snoop around in your life. Harddisk encryption won't give you your laptop back ... but at least it might help you to keep private things private.

Best recipe against laptop theft is this: Always keep your eyes and a firm grip on it. Always. Never ever leave it anywhere, not even for a second. And make sure you write down serial numbers and product ID's ... This may help to report your laptop as stolen if this should ever be necessary. You might be lucky and your vendor's repair centers might by chance get their hands on that laptop again, especially if the thief (or the person the thief sold the laptop to ...) is so daft to send it in for repairs. It's hard to believe but this stuff happens sometimes.

I know one case from my time at HP (2000-2007) where some moron stole a HP laptop. The owner called HP's repair center and some other PC repair places and reported the laptop as stolen. And sure enough the thief was so daft to go to a HP repair center because he wanted the harddisk "repaired" (thanks to the harddisk encryption the owner had installed the thief was unable to boot the laptop ... but stupid as he was he assumed that HP would "repair" that ...). They got him via the laptop's serial number. When the HP repair guys checked the serial number the ticketing system reported the laptop as having been stolen recently ... And the thief was so stupid and left his real name and real address so HP could send him the "repaired" laptop. Instead of a "new" laptop he got to try out the brand-new handcuffs the cops had with them.

So maybe you can be lucky and your laptop gets stolen by a really really stupid thief ... but you can't count on it. So better encrypt the harddisk and thus make sure that he at least can't gain any private info on you.

Because identity-theft is the part that sucks most when a laptop gets stolen.

---

### Post by N1c0_ds on 2009-06-06
Heheheh. What an idiot.

Anyway, I'm all about shaving off seconds at boot time so anything related to passwords is out of the question. However there is a little, easy move I will absolutely do and it will be to engrave information on a few parts of the laptop, something that will make its identification easy if it's found, but won't stop me from reselling it. I used to do that with my bikes, so I can differentiate my own stolen bike from a legit one.

---

### Post by munky99999 on 2009-06-06
Highrisk theft items like laptops for example. 

Password the bios.
Disable booting from anything BUT the hardrives.
Disable changes to the mbr
Password welcome screen.

Which at this point. Anything besides openning the laptop up and replacing the hard drive; and/or killing the power to the bios such that it loses all this. This laptop wouldnt be accessible.

And ofcoarse the best idea.
[Uglify the laptop.]("http://blog.jimmieprodgers.com/2009/05/my-ugly-camera.html")

While you are uglifying the laptop you can attach devices to the laptop. GPS tracking sort of things can be glued onto it. Usually operating by GSM-phone deal. They let you track where the laptop is after.

---

### Post by scorp123 on 2009-06-07
> **N1c0_ds said:**
> I'm all about shaving off seconds at boot time so anything related to passwords is out of the question. Why? With the exception of a quick password prompt at the beginning of the boot process you should not notice any speed differences on a reasonably modern laptop.

My laptops use LUKS full-disk encryption (aka "Encrypted LVM", installed via Ubuntu's "Alternate Install CD"). And even if you don't want all of the disk encrypted, you could at least encrypt your Home directory (that's another option independent of the first one that you can activate too). That latter option uses a mechanism called "ecryptfs", and that mechanism requires you to login with your username and password to unlock your /home ... So if you were not intending to use auto-login (now that would be kinda risky on a laptop anyway ...) and use the usual way of authenticating yourself at the login screen then you won't even know the difference: You type in username and password into the login screen, your settings get loaded ... and in the background "ecryptfs" is decrypting your home directory. From the outside it will look the same to you as if there was no such mechanism.

I use both mechanisms :D  (Yes, I am paranoid but that's OK .... ) :D

---

### Post by soltanis on 2009-06-07
Use LUKS to encrypt your filesystem (prevents booting/reading sensitive data).

Password protect your BIOS settings, and boot from Hard Disk only. This will make wiping your computer pretty damn difficult for your average thief. At this point, he'll probably dump the computer; it's not worth the effort.

If you were THAT paranoid/rich and had a little GPS tracky thingy glued to your laptop, you could probably find it, but chances are if your 'top is stolen, you won't get it back.

Best defense is not getting it stolen.

---

### Post by N1c0_ds on 2009-06-07
> **scorp123 said:**
> Why? With the exception of a quick password prompt at the beginning of the boot process you should not notice any speed differences on a reasonably modern laptop.

My laptops use LUKS full-disk encryption (aka "Encrypted LVM", installed via Ubuntu's "Alternate Install CD"). And even if you don't want all of the disk encrypted, you could at least encrypt your Home directory (that's another option independent of the first one that you can activate too). That latter option uses a mechanism called "ecryptfs", and that mechanism requires you to login with your username and password to unlock your /home ... So if you were not intending to use auto-login (now that would be kinda risky on a laptop anyway ...) and use the usual way of authenticating yourself at the login screen then you won't even know the difference: You type in username and password into the login screen, your settings get loaded ... and in the background "ecryptfs" is decrypting your home directory. From the outside it will look the same to you as if there was no such mechanism.

I use both mechanisms :D  (Yes, I am paranoid but that's OK .... ) :D

It's not a laptop speed thing, it's a human speed thing. I usually boot my computer while I'm doing something else so I decided not to put any BIOS password this time.

---

### Post by Sir Jasper on 2009-06-08
Hi,

I read that thieves often try to extract personal details before installing a new Operating System or wiping everything.

There is a program called "prey"  [http://bootlog.org/prey#download](http://bootlog.org/prey#download)  which works on all Operating Systems including Linux.

Rick Maybury says today:
QUOTE
Tip of the Day -

Laptop Locator

What would happen if your laptop went missing or was stolen? In all likelihood that would be the last you’d ever see or hear of it again, but maybe not. If a freeware application called Prey was installed there’s a fair chance that it might be able to call home, possibly to let you know where it was, or maybe send you a photograph of the thief. Prey is a simple program that runs silently in the background. It builds up a detailed picture of its whereabouts, the status of the computer, running programs and connections plus information about the network it is connected to. It also takes a snapshot of the desktop, and if it has a built-in webcam, it records and image of whoever is using it. The first time it is is able it connects to an network or wi-fi hotspot and sends this data back to a website or email address that you specify.  Needless to say, one of the first things a thief will do is format the drive, but there’s a chance that before they do they will have a poke around to see if there’s any valuable personal data on the machine, and that could give Prey enough time to send back the evidence that might help you to recover your property. It's available for WIndows, Mac and Linux, unfortunately the Windows version hasn't been translated into English yet, but it's all pretty obvious.

08/06/09 
UNQUOTE

My regards

I have copied the above because it will only be shewn for a few days under
[http://www.rickmaybury.com/](http://www.rickmaybury.com/)

---

### Post by glotz on 2009-06-08
I have a dead man's switch and a some semtex.

Bad for recovery but good for preventing repeat offenders.

---

### Post by pedja_portugalac on 2009-06-08
> **scorp123 said:**
> What should worry you is your privacy. If your laptop contains pictures, documents, login info, credit card numbers, private messages, etc. then you should consider using harddisk encryption. That way a thief at least won't be able to snoop around in your life. Harddisk encryption won't give you your laptop back ... but at least it might help you to keep private things private.

Best recipe against laptop theft is this: Always keep your eyes and a firm grip on it. Always. Never ever leave it anywhere, not even for a second.

I completely agree.

---

### Post by aysiu on 2009-06-08
I don't get it. If a criminal is smart (and they aren't all smart, of course), wouldn't they just "extract" data from the drive with a live CD?

---

### Post by pedja_portugalac on 2009-06-08
> **aysiu said:**
> I don't get it. If a criminal is smart (and they aren't all smart, of course), wouldn't they just "extract" data from the drive with a live CD?

Is it possible when disk is fully encrypted? I don't think so, but I'll check it on my laptop.

---

### Post by aysiu on 2009-06-08
> **pedja_portugalac said:**
> Is it possible when disk is fully encrypted? I don't think so, but I'll check it on my laptop.
I was responding to > I read that thieves often try to extract personal details before installing a new Operating System or wiping everything. I didn't get the *try* part of it. If it's unencrypted, there is no *try*. You just boot up a live CD and that's it. If it's encrypted... do you "try" to brute-force the password? I don't get what this *try* thing is.

---

### Post by Sir Jasper on 2009-06-08
Hi,

Presumably, some thieves try to extract personal information (sometimes they fail) other thieves do not even bother to try.

The post was intended to try to be helpful for those with a serious interest.

I have a desktop and I don't follow why "prey" wouldn't work on that; but no matter, as I didn't try it.

My regards

---

### Post by cariboo on 2009-06-08
I have to agree with aysiu, most of you are giving the common thief to much credit. I have a friend that has been a court reporter for 30 years, and he says if a thief were smart, he wouldn't turn to thievery in the first place. From my experience all the thief is looking for is a quick buck, they try to get rid of whatever they have stolen as fast as possible.

---

### Post by Sir Jasper on 2009-06-08
Hi,

Usually the owner or user will want to recover a lost or stolen laptop (even with "new for old" insurance cover). Also, usually that same owner or user will be concerned about prospective fraud, blackmail, or other unsociable acts.

The recommendation to avoid leaving a laptop unattended is obviously good advice though, for many users, it will not always be practicable.

It seems to me that using "prey", if and when a laptop has already been lost or stolen, could only lead to a win in terms of prosecution and/or recovery.  However, I'll be most interested in any logical explanation that claims otherwise.

My regards

---

### Post by aysiu on 2009-06-08
Undoubtedly, there is a *slim* (not "fair," as what you quoted above would assert) chance that Prey might help. After all, something similar worked for a woman whose Macbook was stolen:
[Thieves caught on stolen MacBook webcam](http://www.geek.com/articles/apple/thieves-caught-on-stolen-macbook-webcam-20080513/)

But the chances are very slim, and that should be acknowledged. It is far, far better to keep physical watch over your laptop and, if you're worried about sensitive materials, encrypt your drive.

Yes, the thieves could be stupid, and in that case maybe Prey might come in handy. But if the thieves don't immediately wipe the hard drive with a clean reinstall, they will probably just sell the laptop as "used" to someone else, and that would be the poor sap "caught" by Prey.

---

### Post by yaroto98 on 2009-06-08
Help out and track aliens with your laptop when you're not doing anything

[http://www.boingboing.net/2007/02/22/stolen-laptop-recove.html](http://www.boingboing.net/2007/02/22/stolen-laptop-recove.html)

Some girl had her laptop stolen, and luckaly the girl's husband had installed SETI. The laptop kept communicating with their servers after the theft. By tracking the IP address the police got it back.

See? SETI does find things!

---

### Post by Sir Jasper on 2009-06-08
Hi,

Indubitably you did not read at [http://bootlog.org/prey#download:](http://bootlog.org/prey#download:)

QUOTE
You may be thinking “but what’s the point of this program if the guy will probably just format the thing right away?” and you’re completely right. However, experience shows that thieves tend to look in stolen computers for valuable information, so there’s actually a chance you can catch the guy (and there’s even some succes[s]ful cases!).
UNQUOTE

Further, where did I remotely suggest that encryption and physical care were not additional sensible precautions.

Rick Maybury may have used "fair" rather than "slim" inadvisedly but you have now agreed that a slim chance is better than no chance.

However, both words are subjective and neither you, nor I, can attribute any absolute value to their meaning.

As for the poor sap who paid a low price for the laptop; whose decision was that? Its recovery may be unfortunate but it is unarguably justice.

My regards

---

### Post by aysiu on 2009-06-08
I see where you're coming from, but I worry that if this becomes a trend, people will begin to rely too heavily on programs that have a slim chance of helping instead of just preventing the theft in the first place by physically securing their laptops.

It's a bit the way a lot of Windows users think "I have antivirus, so my computer's protected" and then they proceed to do stupid things and get infected with malware.

If people keep a perspective about it and realize it's about 1% out of the total security you could have, I fully agree with you. From what I've seen, people have a tendency to easily lose that perspective, and I'd rather people put their focus into theft prevention than into theft recovery.

---

### Post by H2SO_four on 2009-06-08
An ounce of prevention is worth a pound of cure...

Full encryption and don't let the thing out of your sight.  Pretty simple really.

---

### Post by Sir Jasper on 2009-06-08
Hi again,

The thread starter wants to maximise protection on going to college. 

There are many reasons why a constant physical guard may not be possible.

However, you are right in that many who suffer are lazy, careless or unthinking.

My regards

---

### Post by aysiu on 2009-06-08
Sir Jasper, I appreciate your suggestion, and the OP may as well. It's always good to know what options are out there (especially ones that are open source and cross-platform).

I still agree with H2SO_four, though.

---

### Post by H2SO_four on 2009-06-08
Thanks Aysiu :)   

I survived college and even took some valuables along for the ride, including but not limited to cell phones, playstation, computer etc.  The key is just knowing where your stuff is.  Don't loan it out.  Don't leave it unattended in public areas.  If you are cautious you will not need to worry about longshot laptop recovery programs.  Although it is a really cool idea, I would rather try to prevent the event from occuring in the first place altogether.

Best of luck in school mate!

---

### Post by scorp123 on 2009-06-08
> **Sir Jasper said:**
>  The recommendation to avoid leaving a laptop unattended is obviously good advice though, for many users, it will not always be practicable. Maybe, but then you should at least get a laptop with a "Kensington" security slot and the right metal cord with padlock that fits into it. If you have to leave your laptop somewhere (e.g. a class room? lab? library? ..) then at least make use of the lock and the cord and tie your laptop to something heavy (desks, heating radiators) or something the thief won't be able to carry away or get close to without drawing too much attention (angry pitbulls, gooey Alien eggs, Sigourney Weaver armed with a flamethrower ...). 

This probably won't keep the really motivated criminals away but it would at least cause most thieves to look for easier targets first.

---

### Post by scorp123 on 2009-06-08
> **H2SO_four said:**
> Full encryption and don't let the thing out of your sight. Exactly.

---

### Post by HermanAB on 2009-06-09
Use encryption to protect your data at rest and a program called 'motion' to save a snapshot to a web server when the thief steals your machine.

---

