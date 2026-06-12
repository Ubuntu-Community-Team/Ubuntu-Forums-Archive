---
title: "Planned: Windows 11 won't install without an internet connection"
date: 2022-02-20
forum: The Cafe
---

### Post by Paddy Landau on 2022-02-20
Microsoft is planning an important change to Windows 11. It plans to make it that Windows 11 (and presumably future versions) won't install without an internet connection.


[LIST]
[*][Windows 11 will soon be closed off to anyone without internet]("https://www.techradar.com/uk/news/upcoming-windows-11-pro-update-will-force-you-to-have-an-internet-connection")
[*][You’ll need a Microsoft account to set up Windows 11 Pro]("https://arstechnica.com/gadgets/2022/02/new-preview-build-adds-microsoft-account-requirement-to-windows-11-pro/")
[/LIST]

This will be seriously bad news for people dependent on air gapped Windows computers. It potentially will also be a problem for some very poor people, although they probably already use Linux or a pirated version of Windows.

It will be interesting to see the response from IT departments.

---

### Post by TheFu on 2022-02-20
> **Paddy Landau said:**
> ...
It will be interesting to see the response from IT departments.

The enterprise versions have a non-Internet method. Just need to have an AD central server to get away from this mandate.  I foresee lots of new AD-Samba setups.

---

### Post by Paddy Landau on 2022-02-20
> **TheFu said:**
> The enterprise versions have a non-Internet method.
They're removing it from Pro, so I wonder if it's just a matter of time before they remove it from the enterprise versions?
 > **TheFu said:**
> Just need to have an AD central server to get away from this mandate.  I foresee lots of new AD-Samba setups.
Will that work? The installation enforces the use of a Microsoft account, so it'll still need internet access. Perhaps it'll work if you restrict internet access to just [https://microsoft.com](https://microsoft.com) for the duration of the installation. Though, if MS gets its way, it might tighten it further by allowing updates only when logged in, which won't work on an air gapped machine.

---

### Post by TheFu on 2022-02-20
Right now, it appears that pressing alt-F4 when the prompt to sign in using a MSFT account is all that is needed.
> When Windows 11 Home prompts users to connect to a network, a simple &#8216;Alt + F4&#8217; shortcut closes the prompt, and the screen proceeds directly to the local account creation page &#8211; something that is never offered to users in the usual process.
Ref: [https://www.neowin.net/news/windows-11-home-requires-internet-to-complete-setup-but-there039s-a-workaround/](https://www.neowin.net/news/windows-11-home-requires-internet-to-complete-setup-but-there039s-a-workaround/)

There will be workarounds.

Of course, people shouldn't be forced into doing what they don't want to do. There are lots of alternatives.  However, Canonical has tried to force people using Ubuntu Core into using their SSO accounts. [https://ubuntu.com/download/raspberry-pi-core](https://ubuntu.com/download/raspberry-pi-core) See *Step 1. Set up an Ubuntu SSO account *

We have choices.  Businesses will push back. The smaller businesses that basically treat their computers like a home network will be stuff, probably.

---

### Post by Shibblet on 2022-02-22
> **Paddy Landau said:**
> Microsoft is planning an important change to Windows 11. It plans to make it that Windows 11 (and presumably future versions) won't install without an internet connection.


[LIST]
[*][Windows 11 will soon be closed off to anyone without internet]("https://www.techradar.com/uk/news/upcoming-windows-11-pro-update-will-force-you-to-have-an-internet-connection")
[*][You’ll need a Microsoft account to set up Windows 11 Pro]("https://arstechnica.com/gadgets/2022/02/new-preview-build-adds-microsoft-account-requirement-to-windows-11-pro/")
[/LIST]

This will be seriously bad news for people dependent on air gapped Windows computers. It potentially will also be a problem for some very poor people, although they probably already use Linux or a pirated version of Windows.

It will be interesting to see the response from IT departments.

Aside from the "TPM 2.0", "8th Generation Intel", "2nd Gen Ryzen", "Windows 10 Expiration of 2025" requirements, it's a wonder more people haven't jumped over to Linux.

Unfortunately, Microsoft drives this industry.  People may think they have an option with Apple, but it's a 2nd rate alternative option at best.

There are a lot of seats on the bus, giving us all the illusion of choice.  Ultimately, no matter where you sit on this bus, it's all being driven by Microsoft.

---

### Post by Paddy Landau on 2022-02-22
> **Shibblet said:**
> People may think they have an option with Apple, but it's a 2nd rate alternative option at best.
I think that Apple-lovers will disagree vehemently on that. In my experience, everyone who migrates from Windows to Mac stays with Mac, whereas the reverse isn't true. Unless it's about gaming, which for commercial reasons appear to be always Windows-supported, not always other platforms.

I personally don't like Apple products, but it does have the advantage that all Apple products seem to work seamlessly with each other. I'd rather have Apple than Windows, but Linux is my favourite.

---

### Post by Shibblet on 2022-02-22
> **Paddy Landau said:**
> I think that Apple-lovers will disagree vehemently on that.
Buyer's remorse?  Have to try and justify a bad purchase somehow, right?  ](*,)

> **Paddy Landau said:**
> In my experience, everyone who migrates from Windows to Mac stays with Mac, whereas the reverse isn't true. Unless it's about gaming, which for commercial reasons appear to be always Windows-supported, not always other platforms.
Valve has put a huge dent in Windows Gaming.  Not quite broken through yet... we'll see when the Steam Deck officially launches.  ;-)

> **Paddy Landau said:**
> I personally don't like Apple products, but it does have the advantage that all Apple products seem to work seamlessly with each other. I'd rather have Apple than Windows, but Linux is my favourite.
Personally, I think Apple products are incredible.  Great hardware!  Bad OS though...  Not much different than Windows underneath the DE.

---

### Post by Paddy Landau on 2022-02-22
> **Shibblet said:**
> Buyer's remorse?  Have to try and justify a bad purchase somehow, right?  ](*,)
Ha ha! No, Apple lovers genuinely love the product. It does seem to be aimed very much at non-technical people who want things to "just work". I also want things to "just work", but I strongly dislike the lock-in that comes with Apple, as well the lack of flexibility. Plus, I dislike being overcharged, and Apple definitely has that down to a fine art.
> **Shibblet said:**
> Valve has put a huge dent in Windows Gaming.  Not quite broken through yet... we'll see when the Steam Deck officially launches.  ;-)
The key point will be whether or not Steam puts sufficient effort into marketing. Windows won the desktop thanks to marketing, despite being at the time an awful OS.
> **Shibblet said:**
> Not much different than Windows underneath the DE.
Um… I beg to differ. MacOS and iOS are based on Unix, the older sister of Linux. Much of the innards are very similar, even to the extent of using the same commands.

---

### Post by Shibblet on 2022-02-22
> **Paddy Landau said:**
> Ha ha! No, Apple lovers genuinely love the product. It does seem to be aimed very much at non-technical people who want things to "just work". I also want things to "just work", but I strongly dislike the lock-in that comes with Apple, as well the lack of flexibility. Plus, I dislike being overcharged, and Apple definitely has that down to a fine art.
Fair enough.

You're right about the "lock-in" though.  It's hard to let-go after you've been in so long.  Red from "The Shawshank Redemption" called it "institutionalized."

> **Paddy Landau said:**
> The key point will be whether or not Steam puts sufficient effort into marketing. Windows won the desktop thanks to marketing, despite being at the time an awful OS.
It was "touch and go" (pun intended) with Windows 8 for a while.  Microsoft didn't seem like they were sure they wanted to keep doing Desktop OS's.

> **Paddy Landau said:**
> Um… I beg to differ. MacOS and iOS are based on Unix, the older sister of Linux. Much of the innards are very similar, even to the extent of using the same commands.
Doesn't Windows 10 and 11 both utilize a BSD based Bootloader?  I could be wrong on that... either way...
Windows, at this point, is attempting to utilize a Linux kernel, presumably to offer Windows users access to Linux programs.  However, due to the popularity of Linux over Windows, I'd assume that's not the reason.  I would venture to say, they are heavily leaning toward changing their kernel to, shall we say... another kind...

---

### Post by Paddy Landau on 2022-02-22
> **Shibblet said:**
> It was "touch and go" (pun intended) with Windows 8 for a while.  Microsoft didn't seem like they were sure they wanted to keep doing Desktop OS's.
Ha ha! Windows 8 was horrific. Microsoft was trying to compete with Android and iOS, but they were too late to the party and their attempt was, well, we all know about that.

Since Gates and Ballmer left Microsoft, Windows has improved dramatically. Windows 10 is almost a decent OS now. I don't know about Windows 11, because it's not yet possible to install it on VirtualBox.
> **Shibblet said:**
> Doesn't Windows 10 and 11 both utilize a BSD based Bootloader?
I don't know. But that's just the bootloader.
> **Shibblet said:**
> Windows, at this point, is attempting to utilize a Linux kernel…
Yes, I don't know what Microsoft has planned. It's a bit mysterious. I know that they like to absorb and neuter, and maybe there's a long-term plan to neuter Linux?

---

### Post by TheFu on 2022-02-22
> **Shibblet said:**
>  
Doesn't Windows 10 and 11 both utilize a BSD based Bootloader?  I could be wrong on that... either way...
Windows, at this point, is attempting to utilize a Linux kernel, presumably to offer Windows users access to Linux programs.  However, due to the popularity of Linux over Windows, I'd assume that's not the reason.  I would venture to say, they are heavily leaning toward changing their kernel to, shall we say... another kind...

Bootloader?  How does 0.00001 seconds matter?  We were booting MS-Windows using LILO in the 1990s.  Before MS-Bloat had a full EFI partition (they didn't have room in the boot sector to waste.  It has only taken them 10 yrs to bloat it out.  My few EFI booting systems use 9MB, which is just crazy when we consider that they've been less than 1M the last 40 yrs. A new install suggested 900MB on Sunday as the size.  I couldn't believe it!   The first computer I owned with a HDD had 40MB of disk and the boot software might not fit in that anymore?  That's the definition of bloat.

Windows use of Linux is inside a VM - a well hidden VM, but still a VM.

MSFT will not be changing their kernel.  They just won't. That rumor has been floating around since the WinNT days when it was BSD they were migrating to use.  At the time, there was clear proof, since they'd "borrowed" the BSD network stack (and got caught).  As soon as that got out, Bill-n-Steve quickly rewrote it in-house.  Until 2010, MSFT had a buy-it, steal-it or invent it here mentality. The last few years, under new day-to-day management, it has been steal-it or buy-it so others can't use it mentality.  They are better at public relations now that the world runs mostly Unix-like OSes.  

They've spent $billions to kill Unix things. $Billions. They've gone so far as to get a MS SVP to take a job at a competing, highly regarded company that was migrating from that company's proprietary mobile OS onto Debian-based mobile OS, and kill the company. The former MSFT-SVP caused the corporate value to drop ... and a sale to MSFT was planned. Of course, there's no proof, but that's what happened.  That company nearly failed after losing most of it's market value.

The big "recent" purchases that come to mind were all about gaining intelligence on the competition.  They bought LinkedIn and Github and Skype.  They know WHO is working where and with Github, they know exactly WHAT they are working on. With Skype, they get which companies are working together. Does anyone really think they aren't going through all the project code for interesting stuff? When MSFT buys a company, I close my account there.  I've had accounts at each of those places. The day MSFT bought them - closed.  I've seen too many evil, but legal-enough, outcomes from that company.

Has anyone actually read the entire EULA for running Windows 8+?  I have.  No - Freakin - Way. I won't agree to those terms. Lawyers gone crazy and most of the world is letting them have a completely 1-sided contract.  Just say no.

---

### Post by Paddy Landau on 2022-02-23
> **TheFu said:**
> That's the definition of bloat.
Your post was interesting, although I'm not sure that increasing size is the definition of bloat. Remember that EFI has to contain much more functionality, including security, than previous incarnations.

I remember when DOS (yes, I'm even older than that) increased its memory abilities to 640 Mb. At the time, we all thought, "What, 640 Mb? No one could ever use that amount of memory! What would you possibly want so much RAM for?"

Now, even Ubuntu wants at least 8 Gb if it's to run well with modern apps.

So, I think that sizes will continue to increase across the board far into the future.

I'm curious about which company you were referring to. I know that MS has some aggressive attitudes towards market share, which is unfortunate, because it has held back innovation through reduced competition. (Before Microsoft, it was IBM that managed that trick.)

---

### Post by TheFu on 2022-02-23
> "What, 640 Mb? 
It was 640Kb, not Mb.

---

### Post by Paddy Landau on 2022-02-23
> **TheFu said:**
> It was 640Kb, not Mb.
… And you are right!

It's crazy how much has changed.

---

### Post by Shibblet on 2022-02-23
> **TheFu said:**
> Has anyone actually read the entire EULA for running Windows 8+?  I have.  No - Freakin - Way. I won't agree to those terms. Lawyers gone crazy and most of the world is letting them have a completely 1-sided contract.  Just say no.

The fact that these "agreements" have to be hidden within a legal document akin to the size of "War and Peace," is telling in and of itself.

---

### Post by Paddy Landau on 2022-02-23
> **TheFu said:**
> Has anyone actually read the entire EULA for running Windows 8+?
> **Shibblet said:**
> The fact that these "agreements" have to be hidden within a legal document akin to the size of "War and Peace," is telling in and of itself.
I think that these documents need a *tl;dr* addendum!

Once upon a time, there was a drive to reduce legalese, in order to make those documents readable. Perhaps making the documents stupidly long is their way to keep them unreadable!

---

### Post by poorguy on 2022-02-26
> **Shibblet said:**
> Aside from the "TPM 2.0", "8th Generation Intel", "2nd Gen Ryzen", "Windows 10 Expiration of 2025" requirements, it's a wonder more people haven't jumped over to Linux.

Unfortunately, Microsoft drives this industry.  People may think they have an option with Apple, but it's a 2nd rate alternative option at best.

There are a lot of seats on the bus, giving us all the illusion of choice.  Ultimately, no matter where you sit on this bus, it's all being driven by Microsoft.

Everyone I know who left Windows went over to Apple and they have no complaints and according to them it does what they want without complaints.

My daughter uses Apple and the times I've used her Apple desktop it worked great and was easy to navigate.

My complaint with Apple is it's way more than I want to pay for a desktop computer so I'll just stay with Linux.

---

### Post by jihth on 2022-03-01
I think this is the worst decision ever made by Microsoft.

---

### Post by Shibblet on 2022-03-01
> **jihth said:**
> I think this is the worst decision ever made by Microsoft.

This is how you become aware of a Monopoly.

People don't want this change, and they're going to do it anyway, and there's not a gorram (thanks Firefly) thing that can be done about it.

Microsoft does what they want, and their users have no choice but to follow.  They're going to make Microsoft Accounts mandatory, and that all comes into play after 2025, when Windows 10 is no longer supported.

We should all be aware of how this works.  The first thing they do, is give you an End-User License Agreement.  If you don't agree to this, you can't use the Operating System.  And if you don't use Windows, you can't use Office, or play the games in your Steam library...  (This is the common understanding, Linux users know different) 

It's literally (as in written down), forced extortion.

---

### Post by DuckHook on 2022-03-02
> **poorguy said:**
> Everyone I know who left Windows went over to Apple and they have no complaints and according to them it does what they want without complaints.
My first smartphone was an iPhone. It wasn't long before I hated it. Vendor lock-in, forced silo, lack of power and flexibility, couldn't hack or tinker, planned obsolescence—a technological and economic dead end. All it had going for it was slick looks and a cool image. Neither made up for its shortcomings.

Lest I be accused of having an axe to grind, I've worked with Apple graphical products going back to the Newton and the Lisa. Most youngsters haven't the foggiest what those products are. I've owned a succession of Macs and their various offspring: LCs, Quadras, Performas—must be at least half a dozen. Back in the day, if one wanted to do graphics, there was no other choice. All suffered from the same issue as that iPhone: they have an initial *Wow* factor that quickly fades when the various chains, locks, anvils and millstones become evident.

Not everyone who left Windows and went to Apple are happy with their choice. Here's one who wasn't.

---

### Post by mastablasta on 2022-03-03
> **Paddy Landau said:**
> 
Once upon a time, there was a drive to reduce legalese, in order to make those documents readable. Perhaps making the documents stupidly long is their way to keep them unreadable!

EULA can not be enforced if it is against the local law. the issue is you need to fight it (at court) later on (maybe). they just put the standard legal stuff in there.

is android available without google account? i mean it is available but when you buy a preinstalled phone you setup google account to access all features, right? and you probably sell your soul and some other stuff at the same time. :)

then you see Epic and Bungie coplain about linux and supposed cheater increase. while in reality they can't harvest your data and they have MS behind them. i mean why would there be any more cheater than there already are in those MP games. it is not about the OS or anticheat it is about their defence being client based. it's like you would try to protect a web server from hack by installing specific client to users in order to access the site.

---

### Post by Paddy Landau on 2022-03-03
> **mastablasta said:**
> EULA can not be enforced if it is against the local law.
This is correct. I'm sure that their expensive lawyers make the EULAs fully compliant with the law.
 > **mastablasta said:**
> is android available without google account?
Yes, you can set up your phone without one, but some apps won't work well. Obviously, any app that needs access to Google's services, e.g. Docs, Sheets, Photos, etc. Most importantly, Google Play Store won't allow installations unless you sign in. It doesn't affect me, because I use Google's services extensively, and so I'm always signed in.
> **mastablasta said:**
> … you probably sell your soul and some other stuff at the same time. :)
Nope. All that you're selling is the opportunity for Google to sell to the advertisers the chance to advertise to you. You can even opt out, if you want, though I don't, because why would I want adverts that are useless to me? The same applies to, say, Google Maps, because it makes it so much easier. I pay the price of feeding Google's thirst for statistics in return for a life of massive convenience.

---

