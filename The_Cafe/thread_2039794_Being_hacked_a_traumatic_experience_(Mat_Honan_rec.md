---
title: "Being hacked a traumatic experience (Mat Honan recounts)"
date: 2012-08-09
forum: The Cafe
---

### Post by nrundy on 2012-08-09
video: [http://www.wired.com/gadgetlab/2012/08/mat-honan-video/](http://www.wired.com/gadgetlab/2012/08/mat-honan-video/)

Articles available at Wired. Definitely motivates one to invest in security.

My heart goes out to Honan. And a big thank you as well for sharing his story so we can all learn from it.

---

### Post by Bachstelze on 2012-08-09
> And worst of all, my AppleID account was broken into, and my hackers used it to remotely erase all of the data on my iPhone, iPad, and MacBook. 

So he signed up on a thing where anyone can remotely erase all his data? Methinks he had it coming.

*EDIT:* Also:
> 
I&#8217;m a technology journalist &#8212; I&#8217;ve been a technology journalist since the &#8217;90s

Sums up what I think about "technology journalists".

---

### Post by KiwiNZ on 2012-08-09
it sums up our sick society

---

### Post by Primefalcon on 2012-08-09
Another couple of reason why I'd never touch Apple.....

1. Apple has access to all your *snip* stuff
2. Anyone who looks at amazon has as well...

You know... even MS users would kick a stink at that kinda access to your data....

---

### Post by ZarathustraDK on 2012-08-09
> **Bachstelze said:**
> So he signed up on a thing where anyone can remotely erase all his data? Methinks he had it coming.

^ This

Sucks to be the guy, and you can't help feeling bad for him, but doing above is truly stupid. It's also the reason why I avoid using the same password and "keychaining" it on sites that could severely mess up my life IRL if hacked.

---

### Post by sffvba[e0rt on 2012-08-09
Google has made it uber convenient for me to have what I have on my desktop on my laptop on my phone on the web etc... Problem is that it is also prone to the same issue faced by this guy.

So I can't have this engineered convenience because someone is off doing no good?!

With that kind of mentality I should just not switch on a computing device and then I really won't have anything to worry about.


404

---

### Post by johnathansmith on 2012-08-09
Feel sorry for the guy, specially when they erase his family photos. But you know what they say "There's a weak link in every chain. And it's just a matter of time before this one snaps".

Call me paranoid but always backup my data!

---

### Post by Primefalcon on 2012-08-09
Having any kind of 3rd party having access to your local files is ridiculous IMO....

---

### Post by KiwiNZ on 2012-08-09
> **Primefalcon said:**
> Having any kind of 3rd party having access to your local files is ridiculous IMO....

That depends on the purpose and the level of access, a blanket NO is wrong if one is to be able to communicate on this planet and to properly maintain equipment and software.

One has to be aware of the risks and mitigate the risk in a way which is appropriate to them.

---

### Post by Primefalcon on 2012-08-09
> **KiwiNZ said:**
> That depends on the purpose and the level of access, a blanket NO is wrong if one is to be able to communicate on this planet and to properly maintain equipment and software.

One has to be aware of the risks and mitigate the risk in a way which is appropriate to them.
the only way I'd have remote access which I do use even is to use keybased ssh logins.....

Even my dropbox is encrypted with ENCFS which I have the keyfile to access it on a usb.... which without that... even the password is useless...

Even files on this machine which I deem important are inside an EncFS volume which is separate from the encrypted home partition....

People really need to learn security and stop inherently trusting 3rd party access.... 

If they need to grant 3rd party access for any reason whatsoever to make sure they cannot access anything that don't **NEED** access to.

This being a tech journalist should of known better.

---

### Post by KiwiNZ on 2012-08-09
the knee jerk reaction is to have so much security that it becomes impossible to operate effectively and efficiently. I have seen more security on home networks etc that I have seen on sensitive institutions mainly as a result of misinformed hysteria generated in the media and, said with caution, Forums.

---

### Post by Primefalcon on 2012-08-09
> **KiwiNZ said:**
> the knee jerk reaction is to have so much security that it becomes impossible to operate effectively and efficiently. I have seen more security on home networks etc that I have seen on sensitive institutions mainly as a result of misinformed hysteria generated in the media and, said with caution, Forums.
The thing is though if more people had this attitude, were would not be anywhere near the the number of intrusions as there are now.....

And people like this guy lost a lot of stuff due to not considering security enough of an issue. Frankly IMO Operating systems (in this case I mean Windows, Macs, and yes Linux) should come with an introduction to keeping your computer secure.

And lets face it.... it only takes a couple of seconds to plug in a usb and type a password, and with the ENCFS dropbox I have the password stored in my seahorse... so it decrypts on computer boot... seamlessly... so it really does not impede my workflow....

---

### Post by vexorian on 2012-08-09
> **Primefalcon said:**
> the only way I'd have remote access which I do use even is to use keybased ssh logins.....

Even my dropbox is encrypted with ENCFS which I have the keyfile to access it on a usb.... which without that... even the password is useless...

Even files on this machine which I deem important are inside an EncFS volume which is separate from the encrypted home partition....

People really need to learn security and stop inherently trusting 3rd party access.... 

If they need to grant 3rd party access for any reason whatsoever to make sure they cannot access anything that don't **NEED** access to.

This being a tech journalist should of known better.
Suggesting ssh for remote access misses the point a little. The journalist's data was not stolen due to the hacker intercepting the transmissions of files or a password or anything. The hackers did not even need to bruteforce a password. All they needed was access to an apple mail account which was granted to them because Apple security trusts too much the privacy of the last 4 digits of your credit card.

I think the real mistake was not in giving access to apps. The journalist really did take advantage of iCloud to share between his computers and phone. So, he was giving access to an application that he used and trusted. Encrypting the files would have worked well *to prevent* the hackers from reading the files, but I am not sure it would have done much to stop them from accessing them. 

The real mistake was in leaving an unusued email account at a poorly secured email service as the backup email address. Backup email addresses are very dangerous it seems. If your gmail account is linked to a backup address, then it does not matter how much SSH you use to access the account, the backup account can be the weak link.

Backup accounts are just a side effect of passwords being terrible for security. The good thing is that google now allows two-factor verification. I hope services like amazon, dropbox, ubuntu-one and iCloud begin using it.


> the knee jerk reaction is to have so much security that it becomes impossible to operate effectively and efficiently. All he needed was to use two-factor verification in google and to back up periodically.

I think everyone with a computer with internet access probably also has a cell phone, so two-factor seems not like a big killer of usability or efficiency. Life might be a lot easier when you don't back up periodically, but really, it is the least thing every user of computers should do.

---

### Post by Primefalcon on 2012-08-09
It would also be inherently better if 3rd parties like dropbox and whatnot.. required keybased logins rather than simple passwords and then encrypted said data with the password and not store the password....

And remove the entire I forgot my password feature which would be impossible with the above anyhow

The mistake he made was allowing a 3rd party with he access to wipe all of his data from all of his local computers and devices.... not to mention giving an I forgot my password thing on his gmail..... hell he probably had the easy question for a reset as well such as what town was I born in.....

---

### Post by JDShu on 2012-08-09
GMail users should use 2 factor authentication. It's actually less hassle than it sounds.

---

### Post by Primefalcon on 2012-08-09
> **JDShu said:**
> GMail users should use 2 factor authentication. It's actually less hassle than it sounds.
Yes I agree that is better, but its also a lot less convenient for people who don't have a mobile phone...

What  lot of people need to do though whether or not you have 2 factor auth, is to have a good password at least 20 digits alphanumeric, upper/lowercase, symbols password **and not have a reset account or reset questions**....

---

### Post by vexorian on 2012-08-09
Numbers in passwords are severely overrated. Use passphrases.

2 factor verification works with non-mobile phones. It is a bad idea not to have a recovery account if you are not using two-factor.

---

### Post by Primefalcon on 2012-08-09
> **vexorian said:**
> Numbers in passwords are severely overrated. Use passphrases.

2 factor verification works with non-mobile phones. It is a bad idea not to have a recovery account if you are not using two-factor.
you mean in case the account is compromised? recovery accounts give too much of an opening to be worth it IMO, as was proven the case in this incident. The Gmail account was compromised from having the .me account compromised... which was then used to reset the password

---

### Post by vexorian on 2012-08-10
The problem was not in using a recovery account, but in using a recovery account hosted at a poor service. And not even knowing that the recovery account was in use. Also, using your same nickname in the recovery account. If it was not for that, the hackers would have had no idea what account to hack.

---

### Post by ZarathustraDK on 2012-08-10
> **not found said:**
> Google has made it uber convenient for me to have what I have on my desktop on my laptop on my phone on the web etc... Problem is that it is also prone to the same issue faced by this guy.

So I can't have this engineered convenience because someone is off doing no good?!

With that kind of mentality I should just not switch on a computing device and then I really won't have anything to worry about.


404

That's like being bugged about having to put a lock on the front door when the door is much easier to use without one.

---

### Post by vexorian on 2012-08-10
In the case of a physical lock, maybe life is really better without them. Because physical locks don't really stop anyone from entering your house, you know.

---

### Post by Primefalcon on 2012-08-10
> **vexorian said:**
> In the case of a physical lock, maybe life is really better without them. Because physical locks don't really stop anyone from entering your house, you know.
its a disincentive, because to enter they'll typically need to make noise which could raise an alarm.... so yes it does stop most...

about 2 months ago My wife and I came back from shopping and the actual handle on our backdoor was busted, someone had I think hit it with a hammer to force entry.... luckily we had a second dead lock which held so all we had to replace was a door handle......

Sure they could of probably broken the window... but they probably resisted doing that because of noise.... however 2 nights later,... 2 houses down from us had a home invasion and.... a robbery and a killing..... and guess what same style, handle broken... difference they didn't have a dead lock...

So don't tell me locks do nothing.....

---

### Post by vexorian on 2012-08-10
Locks, do something, but the something they do is more of the kind of security theater and making you feel secure rather than making you secure. [http://www.schneier.com/blog/archives/2009/08/lockpicking_and.html](http://www.schneier.com/blog/archives/2009/08/lockpicking_and.html)

---

### Post by Primefalcon on 2012-08-10
> **vexorian said:**
> Locks, do something, but the something they do is more of the kind of security theater and making you feel secure rather than making you secure. [http://www.schneier.com/blog/archives/2009/08/lockpicking_and.html](http://www.schneier.com/blog/archives/2009/08/lockpicking_and.html)
lets face it though how many people know how to properly lock pick though? most just go for the quick break and entry, and if the target will make a noise or whatever they'll just move on to the next house...

So it makes you a lot less tempting target...

We live in the city and the area around here is rather high crime zone.... 2nd worst in Milwaukee... and the house on both sides of us as well as over the road have all had break ins.... 

We have dead locks on all the doors and reinforced storm windows as well as a German Shepherd (which is more of a pet that a gaurd dog... but she has a loud bark)....

As I stated above we've had to replace the door handle/lock as well as had a couple of items stolen that we've left outside such a snow shovel from our backyard... but guess what... no actual forces entries... where nearly everyone else has....

Those dead locks are a lot harder if not impossible to pick than a normal lock..... so don't fool yourself.... it makes a difference

---

### Post by sffvba[e0rt on 2012-08-10
> **ZarathustraDK said:**
> That's like being bugged about having to put a lock on the front door when the door is much easier to use without one.

With the lengths that some would have everyone take to secure themselves it is more like not having any doors and breaking down a wall to get it and then bricking it up again... And as has been stated in the thread a lock on a door only keeps an honest man out.


404

---

### Post by Porcini M. on 2012-08-10
I agree with Primefalcon. Locks are a good idea - they won't necessarily stop a determined intruder, but they'll slow them down & increase their risk. And it will be a physical record of a break-in.

Security: Layers, hurdles/obstacles, records.

---

### Post by nrundy on 2012-08-23
I think most of the blame lies in Gmail and Amazon and Apple.

Gmail should allow users to NOT have a recovery email. They should offer NO password recovery option. Perhaps have password recovery options exist but allow users the option of disabling this feature and take full responsibility for remembering their password. Same goes for Amazon & Apple.

As long as email is made a part of password recovery, accounts will never be secure.

Why banks don't digitally sign their emails (PGP/MIME signatures) is still beyond me.

There's just no security hardly anywhere in the whole consumer infrastructure. Even SSL/TLS isn't up to date and it not being up to date is causing security vulnerabilities like BEAST.

---

### Post by vexorian on 2012-08-23
Most locks do not stop criminals, not for even a second. And most of the time, they can be locked back without leaving trace of intrusion. 

Not saying "don't use locks". But they have become more of a social convention than a security layer. And if you really want to be safe because of a physical lock, get a *very good* physical lock. The common place locks found everywhere are terrible.

> Gmail should allow users to NOT have a recovery email. They do:/

---

### Post by sdowney717 on 2012-08-23
My gmail and hotmail were both hacked from someone in Japan.
Gmail locked it down because why would I be in Japan? Hotmail had no clue.

I kept using the same password and was posting on at least 10 different forums. I figure that someone hacked some type of password folder off one of those forums and then matched it up to the email registered on that forum.

Nothing was done except for them sending out all sorts of spam to my contacts. But you know they could really make it bad for you if they started sending 'bad pictures' or threatened the president etc...

I suppose you could be setup by a malicious enemy and who knows if the real truth would be discovered by law enforcement or if they would believe you were innocent.

---

### Post by t0p on 2012-08-23
You ever joined a forum or something that says you gotta set a password of 8-10 alphanumeric characters only?

I haven't. 

And Honan lost his family photos?!  Holy chao!!  I *love* photography, and I've got all my digital images backed up and stored all over the place.  Same with most data, where practicable.  I've lost trivial stuff before, and that taught me: back back back up.  I back up lots.

As for *physical* security: I once locked myself out of my flat, and I was able to break in, silently, by forcing a built-in window lock.  That scared me.  So I made sure I got *good* locks for my windows, double locks on outside doors and, for layering, I have a big, barky dog.  I didn't buy her as a security device, she's just a pet, and really friendly generally.  But everyone who lives anywhere near me will have seen me walking what *looks* like a savage beast, will have heard her bark... friends who have rung my doorbell when the dog's been home alone report that the sound is blood-curdling... and she's friendly but she's also a bitch, therefore very territorial and protective, and I don't think she'd be too happy if a stranger broke in.

---

### Post by aysiu on 2012-08-23
> **vexorian said:**
> Most locks do not stop criminals, not for even a second. And most of the time, they can be locked back without leaving trace of intrusion. Locks aren't to stop criminals--they're to slow down criminals. They also do stop some potential but not determined criminals. If you have a car with an unlocked door and leave a really expensive laptop in there in plain view, random people who don't consider themselves career-professional criminals *will* open the door and steal the laptop. It's very different from someone who is deliberately trying to steal and brings equipment with her.

Even then, it makes sense for criminals to go for the lowest-hanging fruit. If a car is locked and another car is unlocked, why bother even trying to break the lock when you can just open the door on the other car?

---

### Post by GeoffreyBernardo on 2012-08-23
I would not be surprised if the whole thing was a hoax.

---

