---
title: "Microsoft continues to make life difficult for Linux"
date: 2012-11-22
forum: The Cafe
---

### Post by slickymaster on 2012-11-22
Because of the fact that all versions of 64-bit PCs with Windows Certification Program, certified by Windows, use UEFI instead of BIOS, Microsoft intended to impose a way that hardware manufacturers have the Secure Boot functionality active and Microsoft keys installed, what somehow can restrict which installed operating systems computers may have.

Several Linux projects, as is the case with Fedora or Suse, decided to acquire these keys and implement them in their distros, and according to James Bottomley, of the Technical Council of the Linux Foundation, the acquisition of a key is a simple and inexpensive (only $ 99) process.
However, the bureaucracy imposed  by Microsoft, after the acquisition of the key is unfortunate, because a contract is required for its use making it a complete nightmare.

See [Adventures in Microsoft UEFI Signing]("http://blog.hansenpartnership.com/adventures-in-microsoft-uefi-signing/") post at his blog and [Microsoft Holding Keys To Linux Foundation's Secure Boot Solution]("http://www.muktware.com/4855/microsoft-holding-keys-linux-foundations-secure-boot-solution#.UK4HJ-Rg-ik") article.

---

### Post by Lars Noodén on 2012-11-22
Secure Boot closes off one almost completely irrelevant vector for malware.  These games with the keys simply confirm that it is more about creating barriers to those who would want to casually try Linux.  The best solution would be to get the OEMs to abandon 'secure' boot, but all the Linux vendors combined would still have little pull.  

This greatly hinders dual boot, too.  And I guess this may be the end of live CDs/DVDs, too, if the optical media cannot boot.

---

### Post by slickymaster on 2012-11-22
Couldn't agree more with you. But it is a shame that still remains the corporate will and not the individual will who gets to decide what we can choose.

---

### Post by Paqman on 2012-11-22
I think any hassles it generates for desktop Linux on x86 are just collateral damage. Microsoft's intended target for Secure Boot was the ARM devices, where they were worried about getting slaughtered by Android and Ios. They knew the only way they could compete was to force the OEMs to lock the competition out completely. 

If they were really that worried about desktop Linux on x86 they would have insisted on the same restrictions they did on ARM.

---

### Post by grahammechanical on 2012-11-22
Have any of you seen this statement?

> In what is largely an accident of release timing, from what I can tell (and please correct me if I'm wrong), this actually makes Ubuntu 12.10 the first general release of any OS to support Secure Boot.

in this blog:

[http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/]("http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/")

---

### Post by sffvba[e0rt on 2012-11-22
> **grahammechanical said:**
> Have any of you seen this statement?



in this blog:

[http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/]("http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/")

Yup, read that before... all to do with timing.  Fedora would have been second if F17 hadn't slipped.


404

---

### Post by swoll1980 on 2012-11-22
Somebody will crack it. Not worried...

---

### Post by stalkingwolf on 2012-11-23
perhaps if the vendors dont have the horsepower , we as "the people " should make our position known to vendors .  in the form of reduced revenue.
if we quit buying their products they will either listen or go broke.

And yes it would require a re assesment of what actually are needs and what are wants.

what are each of us willing to give up or put off to gain the desired goal?

---

### Post by Gone fishing on 2012-11-23
Never put down to maliciousness what can be put down to stupidity; Obviously this is both! It is a transparent attempt to protect Microsoft's  monopoly under the guise of increasing security – I can't remember the last time I saw a boot virus 1998 perhaps? 

Obviously it will be cracked or the keys obtained by male-ware writers. Although I am not too sure of the technology it seems that MS may be creating new vectors for attack, presumably male-ware will now only need to modify the Windows boot process slightly, to render the system un-bootable, creating opportunities for extortion and presumably when male-ware writers get the key making it more difficult to to remove the rootkit.

> Somebody will crack it. Not worried... 

I am - we shouldn't need to crack things to use our own boxes, not only that, in some areas it will be illegal to use that crack and MS will undoubtedly feign moral indignation when this happens, probably equating the distros that use it to male-ware.

---

### Post by KiwiNZ on 2012-11-23
I have a Laptop running Win 8 it has secure boot, it also runs Kubuntu. Storm in a tea cup, there is nor MSFT conspiracy.

---

### Post by Dr. C on 2012-11-23
I will only be convinced that there is no Microsoft conspiracy when a version of GNU/Linux that:

1) Includes code licensed under the GPL v3 
2) Modification of the GPL v3 code, in the operating system, requires root

is installed on an ARM, Windows 8 **RT**, computer without having to crack the bootloader. 

PS: 1 and 2 are met by current versions of Ubuntu and many popular GNU/Linux distribution namely Debian, Fedora, CentOS etc.

---

### Post by alexfish on 2012-11-23
> **Dr. C said:**
> I will only be convinced that there is no Microsoft conspiracy when a version of GNU/Linux that:

1) Includes code licensed under the GPL v3 
2) Modification of the GPL v3 code, in the operating system, requires root

is installed on an ARM, Windows 8 **RT**, computer without having to crack the bootloader. 

PS: 1 and 2 are met by current versions of Ubuntu and many popular GNU/Linux distribution namely Debian, Fedora, CentOS etc.
I can remember a similar converse , about  UFEI  , as in secure boot, on this forum some time ago, I spelt the dangers of signing up to the present agreement, as in the MIke Garetett agreement with Microsoft . Microsoft will always look for the weakest link,
Perhaps Ubuntu has the stronger as in  Security Relationship in  regards Protecting Your Rights. UEFI Is Paramount to the success of modern day security , If you read how it can work  to the benefit of the end user , and also is most important to Business , Then perhaps you will realise How important , as any in statement "Microsoft has a Commitment To make This Work" , Give it Time, Linux Is secure in the Knowledge , which had already been achieved at it, concept, give it key , What F***'ing key,

That delay will not surprise the real I am.
Happy days....
Elude GNU as per say Is wrong , Invite Secure Applications Is correct,

Debian Does this By a matter of course.

BR

Alex

---

### Post by MadmanRB on 2012-11-24
> **KiwiNZ said:**
> I have a Laptop running Win 8 it has secure boot, it also runs Kubuntu. Storm in a tea cup, there is nor MSFT conspiracy.

Yes but you will probably need another laptop in the future, secure boot might be more restrictive, thats why we need to stop it.

---

### Post by KiwiNZ on 2012-11-24
> **MadmanRB said:**
> Yes but you will probably need another laptop in the future, secure boot might be more restrictive, thats why we need to stop it.

Then we buy the key, simple.

---

### Post by monkeybrain2012 on 2012-11-24
> **KiwiNZ said:**
> Then we buy the key, simple.

Why do we have pay them in the first place? If some scamer uses a malware to lock up your machine and demands a payment to unlock it would you say "just pay the fee and stop making a fuss"? (That happened in Russia before)

This is a similar situation. MS Windows is like a malware on your machine because it limits the way that you can use it by purposefully restricting the hardware's capability (by definition a malware). They say it is for "security" but it is really a malware itself if you don't control the key signing.

---

### Post by KiwiNZ on 2012-11-24
As I said earlier I am using a Secure boot machine with a Ubuntu on it. I have no issue with this initiative or any initiative to make devices more secure. It is easily worked with, again, storm in a tea cup.

---

### Post by kurt18947 on 2012-11-24
> **KiwiNZ said:**
> Then we buy the key, simple.

And if it becomes necessary for each user to buy a key?  It sure could get expensive to use linux, could it not?  I know that's not the case today but in the future?  That's how Microsoft has always screwed their competition, $$$$.  The people/companies being screwed could pursue a legal option but even if they win, it'll likely take any judgement, after dragged out appeals, years to come and the plaintiffs will be long bankrupt or the issue will have been rendered moot.  This is not unprecedented, unfortunately.

---

### Post by KiwiNZ on 2012-11-24
> **kurt18947 said:**
> And if it becomes necessary for each user to buy a key?  It sure could get expensive to use linux, could it not?  I know that's not the case today but in the future?  That's how Microsoft has always screwed their competition, $$$$.  The people/companies being screwed could pursue a legal option but even if they win, it'll likely take any judgement, after dragged out appeals, years to come and the plaintiffs will be long bankrupt or the issue will have been rendered moot.  This is not unprecedented, unfortunately.

Yep MSFT wants to make a fortune from this, that's why it got $90 from Red hat, they even opened a new bank account or the stack of cash.

---

### Post by MadmanRB on 2012-11-24
You are encouraging Microsoft though, thatsd why secureboot is terrible as we are paying dirty money to a dirty company.
Why cant you see that?

---

### Post by Paqman on 2012-11-24
> **kurt18947 said:**
> And if it becomes necessary for each user to buy a key?

Don't be silly.

I agree with KiwiNZ, on x86 it's a non-issue. The distro coughs up a small one-time fee (which doesn't go to Microsoft, btw) and the whole problem goes away.

Microsoft has not implemented secure boot to hurt desktop Linux on x86. They've done it to hurt Android on ARM. Desktop Linux is no threat to them, Android is.

---

### Post by KiwiNZ on 2012-11-24
> **MadmanRB said:**
> You are encouraging Microsoft though, thatsd why secureboot is terrible as we are paying dirty money to a dirty company.
Why cant you see that?

One cannot see that which does not exist.

---

### Post by MadmanRB on 2012-11-24
Yes but some people like the 64bit versions of linux

---

### Post by KiwiNZ on 2012-11-24
Refer my previous posts.

---

### Post by arvevans on 2012-11-24
Interesting discussion, but may have missed one interesting point.  Linux on the Desktop does not have enough clout to affect manufacturer's application of secure boot, but Linux on servers does have significant impact on sale of machines for use as servers.  It might be interesting if those purchasing server hardware were to complain to the manufacturers about secure boot and it's potential effect of the purchase of new server hardware.

---

### Post by KiwiNZ on 2012-11-24
Not an issue for servers

---

### Post by weasel fierce on 2012-11-24
> **Paqman said:**
> Don't be silly.

I agree with KiwiNZ, on x86 it's a non-issue. The distro coughs up a small one-time fee (which doesn't go to Microsoft, btw) and the whole problem goes away.

Microsoft has not implemented secure boot to hurt desktop Linux on x86. They've done it to hurt Android on ARM. Desktop Linux is no threat to them, Android is.

That's not exactly something we should encourage in any event.

---

### Post by mythic97 on 2012-11-24
Something just makes me think that Microsoft are scared that Linux will one day overtake them and with Ubuntu for android and Ubuntu phone OS windows 8 cross platform aint going to work they are already going in a closed platform direction it seems. 
But this is Linux and we will find a way!

---

### Post by Gone fishing on 2012-11-24
> Then we buy the key, simple.

I believe the point of the original post is even when you have bought the key it isn't simple. Obviously it is doable and will be done. However,  this is still malicious, this is still an attempt by MS to exert it's monopolistic influence and make things more difficult. Will it make x86 Windows more secure and safe I very much doubt it will.

---

### Post by kurt18947 on 2012-11-24
> **KiwiNZ said:**
> Yep MSFT wants to make a fortune from this, that's why it got $90 from Red hat, they even opened a new bank account or the stack of cash.

It wouldn't be about making piles of cash, they probably have more of that than they'll ever spend.  It'd be about killing perceived competition.  I can see the benefit of secure boot but I and I suspect others would prefer that someone with a more ethical business reputation were in charge of its administration.

---

### Post by KiwiNZ on 2012-11-24
> **Gone fishing said:**
> .

I believe the point of the original post is even when you have bought the key it isn't simple. Obviously it is doable and will be done. However,  this is still malicious, this is still an attempt by MS to exert it's monopolistic influence and make things more difficult. Will it make x86 Windows more secure and safe I very much doubt it will.

There is nothing malicious at all with this but I guess believing the opposite is more colourful.

---

### Post by KiwiNZ on 2012-11-24
> **kurt18947 said:**
> It wouldn't be about making piles of cash, they probably have more of that than they'll ever spend.  It'd be about killing perceived competition.  I can see the benefit of secure boot but I and I suspect others would prefer that someone with a more ethical business reputation were in charge of its administration.

You don't trust any of the OEM'S or Redhat?

This is not new has been around for along time on Servers and the sky did not fall.

---

### Post by Bandit on 2012-11-24
> **KiwiNZ said:**
> I have a Laptop running Win 8 it has secure boot, it also runs Kubuntu. Storm in a tea cup, there is nor MSFT conspiracy.

QFT, I been off the forums for a few months and this still hasn't died down..  Thought for sure everyone would have moved on to something else to conspire on by now.. LOL :)

---

### Post by weasel fierce on 2012-11-24
I think the point is more that this is a company that has proven to be very willing to extinguish competition by any means possible, that has been sued over and over for anti-trust violations and that has been extremely willing to lie and deceive.

This is like trusting your alcoholic friend to not throw up on your carpet this time. Honestly, he swears.

---

### Post by Bandit on 2012-11-24
> **weasel fierce said:**
> I think the point is more that this is a company that has proven to be very willing to extinguish competition ......

Sadly that sounds like every company out there these days...

---

### Post by weasel fierce on 2012-11-24
> **Bandit said:**
> Sadly that sounds like every company out there these days...

The worship of "Success at all cost" is a social cancer, but if we start down that conversation, we'll get the thread locked :)

---

### Post by Bandit on 2012-11-24
> **weasel fierce said:**
> The worship of "Success at all cost" is a social cancer, but if we start down that conversation, we'll get the thread locked :)

LOL Indeed..  :popcorn:

---

### Post by Gone fishing on 2012-11-24
> You don't trust any of the OEM'S or Redhat?

I think kurt18947 point is that the keys are ultimately in Microsofts hands and possibly MS is not as fair even-handed  as they could be (it is after-all a convicted monopolist). I note that de Raadt (OpenBSD) doesn't trust Red Hat or Canonical

In my first post I wrote > Never put down to maliciousness what can be put down to stupidity and as restricted boot is a solution looking for a problem perhaps you are right and this is just stupidity - it seems that Linus would agree.


> "The real problem, I feel, is that clever hackers will bypass the whole key issue either by getting a key of their own (how many of those private keys have stayed really private again? Oh, that's right, pretty much none of them) or they'll just take advantage of security bugs in signed software to bypass it without a key at all."

Torvalds concluded, "Signing is a tool in the tool-box, but it's not solving all the security problems, and while I think some people are a bit too concerned about it, it's true that it can be mis-used." 

I am more inclined to believe the restricted boot on ARM is a desire to copy the locked in model of Apple and its inclusion on x86 is a small mean maliciousness - but perhaps you are right and it is simply stupidity.

---

### Post by Paqman on 2012-11-25
> **KiwiNZ said:**
> There is nothing malicious at all with this but I guess believing the opposite is more colourful.

Hmm, I wouldn't go that far. Secure Boot on ARM is clearly an attempt to leverage their sranglehold on the PC OEMs to force their way into a new market that they'd otherwise get stomped in. That's probably not illegal, but it is playing dirty.

I don't think there's any malice on their part towards desktop Linux on x86 though. I think they probably consider desktop Linux pretty irrelevant. I can't imagine they feel they have to do anything in particular to defend against it.

---

### Post by Paqman on 2012-11-25
> **Bandit said:**
> Sadly that sounds like every company out there these days...

Not just companies. We used to have a saying in the military: "If you have to cheat to win then...win!".

Although in their defence the stakes they play for are somewhat highly than those in business. And coming second hurts more.

---

### Post by Bandit on 2012-11-25
> **Paqman said:**
> Not just companies. We used to have a saying in the military: "If you have to cheat to win then...win!".

Although in their defence the stakes they play for are somewhat highly than those in business. And coming second hurts more.

I agree.

---

### Post by kurt18947 on 2012-11-25
> **weasel fierce said:**
> I think the point is more that this is a company that has proven to be very willing to extinguish competition by any means possible, that has been sued over and over for anti-trust violations and that has been extremely willing to lie and deceive.

This is like trusting your alcoholic friend to not throw up on your carpet this time. Honestly, he swears.


Precisely!!!

---

### Post by mythic97 on 2012-11-25
Yeah windows is trying to brush Linux under the rug before everyone knows about it just look at there store like the guys at steam said and so did notch windows is heading down the dark path of a closed source closed platform OS yet no one notices apart from none windows user? and have you seen how <censored> the desktop looks even the gnome and unity user who hate the other's GUI can't help but laugh at windows 8s thing, what's it called? windows is heading for oblivion I think and the going out in a horrible blue screen of chaos.

---

### Post by D_E_H0987 on 2012-11-26
I can't believe no one thought of the real reason for changing from BIOS to UEFI, and that is to force people to upgrade software.   

Now what they will tell you this is for is for "security" but in realality it is because newer versions add certain "features" so they can spam you with advertising, and in Microsoft's case they also spy on everything you do.  Google spys on you too, but at least they tell you about most of it.

The simple fact is security is better if everyone uses something different, as one bug can't infect all the differing software packages.

Right now lots of people are using old machines with old software, what they want is for you to throw out the old PC, software and all, and buy a new one.  
Microsoft has been playing this game for a while now with requiring computer sellers to put the COA on the machine rather than giving it to you with the software disks.  And all the later games with authenticating windows, and them forcing you to reauthenticate windows everytime you look at the machine cockeyed.

They want everyone to have the same "features' available, so everyone sees the new craptastic advertising.

As others have said Linux isn't big enough on home PC's for them to worry too much about.

You notice every time you turn around there is a new browser version and you will also notice each of these new browser versions even in Firefox these days, breaks APP's like Adblock.

You will also notice web sites try to force you to update flash all the time, and java all the time and ....

And what happens each time?  Yep, some new advertising crap gets threw your AD blocking software.

I wouldn't have the AD block software if the AD's were not insane, popups popdowns, popovers, ..........   Its nuts.  I never minded a side bar, or a header, or footer AD, but when the crap came out I started finding APP's to remove the crap.

I can also guarantee if Google wants to put Android on a PC of any type even with UEFI they will have no problem doing it.

Now there is also some of the big computer company's who don't like people buying $3 dollar cards when they try to sell you a card with the same chips on it for $50, and these guys may try to add the "feature" to mother boards that only authorized cards will work.  They would get sued, but it takes big bucks to win, and many times even if you win, you really have lost anyhow, as it costs so much.

---

