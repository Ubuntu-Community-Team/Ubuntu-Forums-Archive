---
title: "anti-tampering of boot sector, software,  software anti-evil maid, TPM 2.0"
date: 2024-01-29
forum: Security
---

### Post by catacombs2468 on 2024-01-29
I am looking at being able to verify if computer boot sector, software, firmware has been tampered with.  I am aware of Heads, which is limited to a few computers, and requires taking apart computer, using an external hardware flasher.  Perhaps get at accomplished the first two.  verify boot sector, software has not been tampered with.  Similar to anti-evil maid, trench boot??   I see software tripwire.  that the later versions of Ubuntu will have such a program to integrate to TPM 2.x.   Possibly one could use the proxy TPM for testing?

---

### Post by TheFu on 2024-01-31
I think the only sure way is to boot from flash storage that contains all the boot files (/boot/ and /boot/efi/) along with all the LUKS decryption stuff to access the rest of the OS.

If you don't encrypt everything possible, all bets are off, but parts of the boot cannot be encrypted, so those need to NOT be ever out of your control.  Shower with your flash drive or sdhc boot storage.  Keep it on you, always.  Put it in a belt for border crossings or use a microSD coin holder. [https://shomer-tec.com/products/covert-coin-1](https://shomer-tec.com/products/covert-coin-1)   Or if you want to overpay [https://www.amazon.com/US-Mint-Quarter-Covert-Compartment/dp/B0036VJHXG](https://www.amazon.com/US-Mint-Quarter-Covert-Compartment/dp/B0036VJHXG)

Eventually, some flaw with the TPM --> OS connection will be found and exploited.  That's how security works. Nothing is perfect and there will eventually be a flaw, probably where two different parts connect, that will be exploited.

TrenchBoot on a microSD is probably the belt and suspender's solution for today.

When I travel to places known for not respecting privacy, I take a cheap laptop or chromebook (never connected to google) and boot with a full OS off the microSD. A 64G microSD is more than I typically need anyway and in a country like that, I'll just use an NX remote desktop to remote back to my home office to do everything.  Important stuff never enters those types of countries.

---

### Post by catacombs2468 on 2024-02-01
Thank you for replying.  Your answer sounds spot on.  I actually am usually on the Qubes forum.  There the gold standard to verify the trustworthiness of a computer, security is to use Heads, which is only available on a limited number of computers.  

Problem with that, and AEM (Anti-Evil Maid) is that they require an external hardware flasher, Taking computer apart, and flashing.  

In my personal situation right now.  I am using a Lenovo T480, 8th generation Intel, Which I have added 64 GB RAM.  This is not one of the laptops which Heads has been fitted to.  

Also, my hope, is to find a less expensive way for a Journalist or Human Rights Defender can create a secure means to get online, while living in, never leaving the kind of country you describe.  Authoritarian, a danger to those who write of the truth.  Hardware Flashing for amateurs seems to raise the bar a bit much.   

I had hoped to discover the method (verify software) Ubuntu uses, and, at least for myself, implement it on my T-480.  Which still leaves out, Verification of hardware.  mitigation of the negative features of Intel Management Engine.  ME.  Plus, in the case of the T480, disabling the white list of components (and I am not sure that applies - the techie types who I read about the T-480 from, do flashing with an external flasher)   I have gorked a Lenovo X-230 trying to flash it.  I am not anxious to spend more hours, more money on flashing.   And, It would not apply to what I hope is an eventual target audience.  Journalists, Human Rights defenders.   Actually, in some ways, the reporting of wrong doing by power groups seems to be done by individuals, rather than reporters.   I have heard the prisons in China have many individuals who 'reported" what they have witnessed on Social Media.  

I once tried Chrome Book, with an external drive, with several different live Linux systems.  Guessing the Chrome book was a bit too slow, only occasionally starting up.   Seems like a valid idea.   One of the other live Linux OS's was Easy OS, which has some security features built in.   However, it only has one developer (Barry Kauler -developer of Puppy Linux), and not an organized group of testers.   More recent Chrome Books, maxed memory, are more expensive than I can afford.  Like a lot, hoping for a RISC/V.

I would hope, in my thoughts of a Journalists/Human Rights worker is to have a Qube (kept offline) with an app for "I talk, I types."  which I understand Ubuntu has, and hopefully, a lot of different languages.  First I need for someone to create the Qube for Ubuntu,   I would prefer, for Journalists/Human Rights types to have a group of Qubes, with third party software already installed.    Providing the tool kit of Qubes for inexperienced technical people is not my first choice of how to proceed.  (disclaimer, Yes, I know, adding any third party software to Qubes increases the attack surface. Plus making available ready to download extra Qubes with third party software has risk in trusting -whoever put it together.)

 My line of what I --think I need, from a verify software, that can be installed by an ordinary user, without opening computer case.

Cheers

---

### Post by TheFu on 2024-02-01
When you can't trust standard delivery or local sales of hardware not to be unmolested, then you are left with what a visitor could bring in.  That means some sort of compute stick they can carry-on and a method to provide updates every quarter or so.   If you are a target by the govt in a "free" country, you can only hope to randomly buy hardware, in-person, at a store, and play the odds of it not being modified.  I've done this a few times.  Walked in to a store that I'd never been to previously, grabbed a sales associate, walked to the locked area with the laptops and pointed at the 3rd box with the model I wanted.  The salesman thought I was crazy, since they were all the same.  I've paid cash a few times too, but only for $300 or less chromebooks.

I cannot think of a way that I'd risk my life trusting to use computers that I didn't bring myself into authoritarian countries.  And like I said, I'd have anything important external, so the internal device would only be a remote terminal.  I've thought about this for about 2 decades.  There are even some "friendly" nations with laws that I disagree over with laws that mandate unlocking storage on request.  It is for those countries too.  My home country is pretty good about privacy, but they have a border exception. There have been cases where someone with jobs similar to mine were forced by the border control people to unlock files on a laptop in violation of other US laws (not border related).  That traveler reported the incident to his site security manager immediately and was told he did what was necessary. He wasn't prosecuted, thankfully.  Fortunately, case law changed the requirement to unlock your data at any border crossing in the last few years.  It won't protect against detainment and all the problems that brings, however.

As paranoid as I am, I've never been asked to give up my laptop or tablet at any border.  Once, I was trying to have the laptop inside my luggage and was forced to pull it out and carry it with me.  I didn't like that, since I'd planned (2) 23 hour layovers on the return trip home and wanted to leave my main luggage with the airlines.  It isn't any fun trying to do an overlay visit stuck carrying even a 2lb laptop, much less 3-5 lb versions.  On that trip, I sorta hoped someone would steal the laptop from my luggage. I was looking for a good excuse to replace it. ;)  There was nothing on it and it was going to be wiped when I got home anyway.  I wipe my laptops before and after any trip. It is habit.  Once that screwed me and I got hacked thought a default BT setting in Ubuntu less than 24 hrs after a freshly patched and updated load.

I've never touched Qubes and think they are over selling the security claims.  There's no silver bullet for security. It is a process with thousands of decisions along the way.

Puppy Linux was non-secure by default, so beware. There's almost always a trade off between usability and security.  I know of only 1 exception to that.

---

### Post by catacombs2468 on 2024-02-01
I admire your knowledge that comes from experience.  I surely do not have such experience.  I don't think I want it.  Someone has to do certain kinds of work.  Thanks for that.

From what I read.  Those looking to create a Secure Computer, someone chose an Lenovo X-230, which is only a third generation intel processor.  One of the goals was to choose hardware which could be reasonably purchased used inside most countries around the world.   Also like a random purchase.  It is solidly built, much is known of it.   A techie could do the hardware flash, change some internal hardware, like a better more trusted WiFi adapter, a randomly purchased SSD, max out RAM memory.  Then install Heads, to be verified with Nitrokey or equal.  then the first stage of having a trustworthy laptop is met.  Likely also, if trained properly, border security might recognize the device (Lenovo X-230), and provide additional, special scrutiny for the person carrying it.  

Bruce  Schneier says much of what is being done for computer security for agencies, (US Homeland Security) is 'Security Theatre."  Only likely to catch someone who is not at all knowledgeable.  Don't bring in anything computer at all.  Just memorize a way to get a website name, a password.  After arrival, buy a computer. Connect  through a tunnel, and download all the things that would make Homeland Security interested, very unhappy.  other stuff.  [https://www.schneier.com/](https://www.schneier.com/)

I notice Reporter, who was Russian went home to see their sick mother in Russia.  Russian Security seized her Graphene phone, although she gave them the password to inspect it.  and gave them Passwords to her computer, which they let her keep.  I now hear someone with a description like that was arrested by Russian Security Services.  

Gee,  I guess I am mentioning things you already know.  

Easy OS has applications chosen to be more useful for a Security laptop.  A very simplistic browser (Yes you can install the other browsers).  Containers.  Claws Mail.  Ability to close the computer without saving anything from the session.  Encryption software.  OpSec  being a big consideration to using this securely.  

I would agree, that your doing what you have already, used,  given long consideration to "how to", is the best solution.

---

### Post by TheFu on 2024-02-01
I wouldn't get stuck on any specific model.  If you can hack it to do what you need, then someone else can too.  Of course, we all have experiences, good and bad, with specific computers.  I used to carry IBM laptops for work, then Lenovo after that part of the business was sold.  When I was working all the time in Asia, I soon found a way to stop taking any laptop with me and just used the client's workstations instead.  They didn't want my laptop on their network anyway.  I was traveling with a non-networked PDA only for taking notes.

I do watch many security related blogs and news sites.  Schneier is on my daily feed list. Some weeks, his tidbits about squids are the best news. ;(

EasyOS sounds like a newer TinyCore.  I've used TinyCore with X11 and a browser for corporate banking, when I had that role. It was very fast and only got used for 1 website. Not bad for a 50MB distro.

Don't buy into the Linux Container hype as the solution for security.  Many containers are setup in a way that make them worse for system security than running an app natively installed on the system.  Details for how every container was created matter.  Of course, without looking at every container and how it was built, I can't say anything good or bad.  "It depends" is the only answer.

Good luck finding or creating a solution that fits your needs.

---

