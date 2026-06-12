---
title: "Security Strategy for Laptops"
date: 2023-03-09
forum: Security
---

### Post by makitso on 2023-03-09
I am trying to create a security strategy for two laptops, mine and my wifes.  Ideally, I want increased security when our laptops are away from our home.  

I have a mounted NAS device that is in a secure location.  So, if the laptop is say stolen, the NAS device would not mount and browser password would not be enabled.  

I use Bitwarden on laptop, with a Brave plugin.  I tried the AppImage version of Bitwarden but it has no browser integration on linux.

My wife uses Firefox.  I tried to use the master password for her but she complains.

Strategies?

---

### Post by TheFu on 2023-03-09
Security isn't a product, it is a process.
What are you trying to protect against?  
From whom?  
Are you a target of a nation, a business competitor, professional thieves or just opportunistic theft?  
Are nations trying to "get you"?
Security and privacy aren't the same. How much compromise are you willing to have for each?
Do you work for an NGO?
Do you travel across international boundaries?
What sort of data is being protected?

So, when I worked for a govt agency and traveled internationally, I'd not take any electronic devices with me, not even a cell phone. This was long ago.
In more recent times, when I travel for business internationally, the company would provide a clean laptop and loaner cell phone for the trips. I was told not to take any business data with me and only bring software tools necessary to complete the work for the specific client.  I'd use a VPN to access the business network from the hotel, as our clients didn't allow VPN access from their network.

Some countries, even those with protected freedom of speech, have rules at their borders which may require you do provide access to encrypted storage as part of their border checks.  As a citizen of the country, you may have added rights, but perhaps not.  France and the UK have laws that require encrypted passphrases be turned over on request. You can look up the specifics.  It comes down to how much inconvenience you are willing to undergo to protect encrypted data.

BTW, all portable devices should be fully encrypted, period.  Ensure they are powered off whenever moving beyond a 5 minute walk.  Encryption only works when the data is fully at rest. That means no standby, no hibernation.

Yes, you should use a password manager.  I don't have any browser integration in my setup, mainly because I don't trust browsers. They are far too complex to be trusted and history has proven they are full of thousands of bugs, waiting to be abused. Use a simple browser, one that doesn't support javascript at all, for most web use.

I know people who travel with a laptop that doesn't have any internal storage. They have a tiny USB3 flash drive that they use to boot which has some small area for permanent file storage.  They keep the storage with the OS in different bags than the laptop when going through airports, so if their laptop walks off (gets stolen), it is just hardware and a slight inconvenience.

For a few years, I traveled with a chromebook.  It is probably the most secure portable computer that is also internet connected today, but there's zero privacy with chromeOS.  Tradeoff.

To you use wifi or bluetooth?  Hint: stop doing that, especially bluetooth and only use wifi with a full VPN, even inside your home.

Those are just a few thoughts.

---

### Post by DuckHook on 2023-03-10
> **makitso said:**
> Strategies?
You, my friend, are blessed with a non&#8209;techie spouse who refuses to take security seriously. Join our very large club.

This limits your options. If she insists on taking her laptop travelling, then just make sure that it contains nothing of substance. Often, non&#8209;techie users have the saving grace of not using their laptops for much other than surfing and retrieving e&#8209;mail. The way I handle that is to delete the e-mail client along with the database and tell Mrs DH that she can only retrieve e&#8209;mail using my whole disk encrypted laptop, which she is free to use anytime. When we get home, I will reinstall the e&#8209;mail client and it's usually a minor enough inconvenience to her that she won't be too hard on me.

She can surf all she wants on her own laptop because I've disabled the password manager, history memory and all autofills on her browser. I also set her FF to "strict" privacy and "delete cookies on close". That's about all I can do without risking her wrath and my coming to an untimely end.

In the final analysis, I've just had to resign myself to the fact that our collective security is only as strong as its weakest link: in my case, the Mrs. If she doesn't take it as seriously as I do, then there's nothing that I can do about it.

---

### Post by makitso on 2023-03-10
Thanks for the comments guys.

My primary concern is theft;  either someone breaking into our home and stealing our laptops. After that, loosing a laptop while away from our home.
Both laptops run Ubuntu Budgie 22.04, have a separate home partition and no encryption of the file system.

I have all of our critical data on the NAS device hidden away.  So, if the laptops leave our house, the mount fails, etc.

The area I am trying to focus on is browser passwords.  On my laptop I use bitwarden and it works pretty well.  I don't save passwords in the Brave browser.

My wife's laptop is really the issue here.  Bitwarden integration with her Brave/Chrome/Firefox browser is not 100% perfect.  By that I mean that some sites do not auto-fill correctly and she complains.  So, I dropped bitwarden and instead use the Firefox password manager for her.  However, again, I get complaints about the need for a master password being required.

Ideally, I would like her laptop to be completely open at home but if stolen have no browser passwords available.

Things I have thought about:

Encryption of the home partition but, from what I have read, its not 100% reliable.  
Firefox profile stored on the NAS device.

---

### Post by TheFu on 2023-03-10
Portable devices need to be fully encrypted, not just the HOME directories.  Ubuntu deprecated HOME directory encryption for very good reasons.
I'd never use the built-in browser password system for many reasons.  Better off carrying a piece of paper around with 50% of the passwords written down and 50% memorized.  Just make the written down part unique and 10+ characters.

If you want to limit ease of use to be only when at home, use NFS mounts for your HOME directories off the NAS device. That way, when away  from home, nothing in the HOME directory would be available.  [https://ubuntu.com/server/docs/service-nfs](https://ubuntu.com/server/docs/service-nfs)  Just use the nfs-client-configuration instructions.

Not all NAS devices are equal. Beware.

---

### Post by DuckHook on 2023-03-10
If you are concerned about your laptop being stolen at home, then TheFu's suggestion is good. You wouldn't even need to have all of /home transferred to the NAS, just the important data folders. It's a more involved process finding and symlinking those folders, but the advantage is that your laptop is still functional even if the NAS goes down.

What I don't understand is your focusing your concern on the laptops while the NAS is presumably just as vulnerable. B&E artists these days will go for the NAS before they go for your laptops. It's for this reason that I don't worry too much about laptop security at home. If someone physically breaks in to my home, the game is over.

But we may be overthinking this. If Mrs DH is anything to go by, it's all about the least possible friction. She does not object to security. What she objects to is the friction that security invariably creates. Examples: she hates dealing with passwords, so, if left to herself, will reuse insecure ones. Therefore, secure passwords means the use of a password manager. But this creates its own friction if that password manager is not "easy" to use. This means absolutely no muss or fuss. I understand your rationale for resorting to FF's network password service. As insecure at it is, it's better than nothing and certainly better than her projected frustrations.

To solve that problem, consider keepassxc and its browser extension. It works transparently and is almost always successful with Mrs DH. TheFu will rightly warn you that browser extensions are suspect, etc, but we are dealing with more than just security here—we are trying to maintain marital bliss and this requires compromise.

Perhaps one solution is to replace the SSD in her laptop when travelling. This is what I do. My travel SSD is fully whole disk encrypted. It also contains just a small subset of the apps and data that is on my home SSD. That way, if it is lost or stolen, it simply doesn't have much sensitive stuff on it.

For example, it has no e-mail client. When travelling, I check e&#8209;mail through the web interfaces of my various providers. This is a pain, but it eliminates the e&#8209;mail exposure. Passwords are not stored while travelling. I'm suitably apologetic to Mrs DH, but she understands the security risks and is willing to forego that convenience while on the road. After all, 99% of her web usage is searching for hotels, eateries, places of interest, etc. We aren't about to do our banking or our taxes while travelling, so there is no need for access to the sensitive stuff.

When you get home, just replace the SSD and you are back to a more complete laptop.

---

### Post by makitso on 2023-03-11
All good suggestions.  Clearly, the first thing I should do is to encrypt the SSDs on my three laptops.  

All three are dual boot system, two with UEFI  and one old system with BIOS.  Any issues with encrypting the older system with BIOS that I should know about?

---

### Post by TheFu on 2023-03-11
I know of no easy way to have good encryption and dual boot.  Setting up Ubuntu with whole drive encryption is 1 checkbox during installation, but that will overwrite the entire storage device and any other OSes.  I suppose people have done it manually, but it it non-trivial.

The solution to having multiple OSes on the same hardware is to use virtual machines, not dual booting.

---

### Post by mIk3_08 on 2023-03-11
> **makitso said:**
> All good suggestions.  Clearly, the first thing I should do is to encrypt the SSDs on my three laptops.  
All three are dual boot system, two with UEFI  and one old system with BIOS.  Any issues with encrypting the older system with BIOS that I should know about?
Yeah, this will also help. Use all the BIOS/UEFI security, HDD/SSD security. all that. That will help you a little. Also the best Idea is to store important files on your home NAS or on Cloud. Regards and cheers.

---

