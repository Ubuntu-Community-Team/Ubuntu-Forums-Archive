---
title: "How does my security model sound?"
date: 2012-11-18
forum: Security
---

### Post by MrIceBlock on 2012-11-18
Hi, I was just wondering if you all could give me some feedback about my security model on my laptop. 

I work for a company where I handle clients personal information, and I travel a lot. I need Windows to run some software that I need on the job, and it does not run in Wine. I also have to connect to public Wi-Fi's a lot so I like to use Ubuntu for that. 

Here is how my laptop is setup:

1) On the Hard Drive I have dual booted Windows Vista and Ubuntu 12.04

2) I use Lubuntu on a flash drive to handle clients data, email others, and handle some online banking 

I was wondering if that sounds secure to you? 

I am not really worried about someone stealing the flash drive because I always unplug it and keep it in my pocket when I am not using it. :)

I also had some questions, I never boot into Windows or Ubuntu with the flash drive plugged in, but I do insert the flash drive when the computer is turned off, is there a possibility that a Windows virus could some how steal data off of it while the laptop is turned off or booting?

And I have heard about AppArmour and Firewalls for Linux, I don't have any of that installed (unless it comes by default), should I worry about it?

Thank you for your feedback!

P.S I am not very good with computers so keep it simple! :)

---

### Post by Lars Noodén on 2012-11-18
Better to run the legacy system from a virtual machine such as Virtualbox.  That way every time you start it up, you can begin from a known clean snapshot.

---

### Post by MrIceBlock on 2012-11-18
> **Lars Noodén said:**
> Better to run the legacy system from a virtual machine such as Virtualbox.  That way every time you start it up, you can begin from a known clean snapshot.
I don't use Virtual Box.

---

### Post by Lars Noodén on 2012-11-18
Right.  But it would be time to start using a VM.  There are other options besides Virtualbox.  One is qemu, but VB is better.  Your dual boot system will gather cruft and suffer from the infamous "bitrot" that goes along with that brand of OS.  If you make a clean install with all the patches, then you can take a [snapshot](http://www.virtualbox.org/manual/ch01.html#snapshots) which will permanently save that fresh state.  Then every time you start up from that snapshot, you are starting from that clean image.  It's an arrangement that's hard to beat.

---

### Post by MrIceBlock on 2012-11-18
> **Lars Noodén said:**
> Right.  But it would be time to start using a VM.  There are other options besides Virtualbox.  One is qemu, but VB is better.  Your dual boot system will gather cruft and suffer from the infamous "bitrot" that goes along with that brand of OS.  If you make a clean install with all the patches, then you can take a [snapshot](http://www.virtualbox.org/manual/ch01.html#snapshots) which will permanently save that fresh state.  Then every time you start up from that snapshot, you are starting from that clean image.  It's an arrangement that's hard to beat.
I tried Virtual Box before and I didn't like it, it was pretty slow and jerky so I like dual boot better. My whole setup works fine to be honest, I don't really want to change it. But I was just wondering if it was secure. Mainly I wanted to have an answer to this question:

> I never boot into Windows or Ubuntu with the flash drive plugged in, but I do insert the flash drive when the computer is turned off, is there a possibility that a Windows virus could some how steal data off of it while the laptop is turned off or booting?

---

### Post by OpSecShellshock on 2012-11-18
Windows malware won't run if Windows isn't running. If the system is powered off then nothing will be running at all, including the USB drivers that would tell the system that a USB device is plugged in.

If there is personal/sensitive info on the USB stick you may want to consider encrypting it.

---

### Post by snowpine on 2012-11-18
Is Lubuntu installed to the USB with all security upgrades up-to-date, or is it a "Live" USB?

---

### Post by Ms. Daisy on 2012-11-18
Read the [Basic Security Wiki]("https://wiki.ubuntu.com/BasicSecurity").  IMO it has reasonable security measures for someone such as yourself that apply specifically to Ubuntu, but a lot of it can also apply to Windows.

I would expand on OpSecShellshock's advice and say encrypting the entire drive would be a good idea if you're handling clients' sensitive data.

---

### Post by snowpine on 2012-11-18
+1; dropped/lost/stolen/found/planted USB flash drives are an actual real-world major vector of cybershennanigans.

---

### Post by DuckHook on 2012-11-19
You are asking a complex question where the answer is not definitive but spans a continuum of possibilities depending on how sensitive your data is and how paranoid you are.

My own security setup (for my travelling laptop) is as follows:

1. I encrypt a Private directory within my /home partition using a strong 128 bit random passphrase. All of my sensitive stuff is then placed there with only links pointing back to the locations where various apps expect to find them. This includes all of my keys, mail, browser history, etc. including the mail program itself after I discovered that it stashes mail backup files within its own directory structure rather than the mail database where you might expect them to reside. Many people choose to encrypt their entire /home partition, but I refrain from doing this because I want certain nonsensitive scripts to be able to run on a virgin system install prior to the system even being configured for decryption.
2. I encrypt my swap partition.
3. I connect in public wifi hotspots, hotels, etc. only through a certificate-based VPN (I use openVPN) back to my home VPN server. IPsec has holes and PPTP is a worse than no security at all because it gives the illusion of security while delivering none.
4. I have a firewall with strong rules: all incoming ports denied and only specifically needed outgoing ports allowed.
5. I have apparmor configured for my most at-risk apps. I have found that it's just too much work to configure it for every app I have, but I configure it for two of my three browsers, my mail client, cloud clients, etc. In short, for all apps that communicate or access resources outside of my computer.
6. Cloud data is all totally non-sensitive stuff that I wouldn't give two hoots for the whole world to see.
7. I use links2 for 90% of my surfing. It's missing practically all of the eye-candy, bells and whistles and other bloat that are now a given in mainstream browsers, but it can't accept cookies, and isn't capable of running any sort of script, whether java, flash or anything else. Its upside is that it's lightning-fast and super secure.
8. My other two browsers are locked tight with Adblock, noscript, cookies disabled by default and privacy guard. I surf through openDNS which blocks the worst sites and I use Web of Trust. Notwithstanding all this, I am mindful of the fact that my biggest security exposure remains the browser.
9. I will not install any program that does not come from the Ubuntu repository, and I don't attach any PPAs.
10. Most of all, I refuse to use Windows on my travel laptop. It is installed only at home where I have the time and resources to deal with its inherent security flaws, bloat and crud.
11. I understand and use very strong passwords for my most important sites/accounts that are impervious to a straight dictionary attack.
12. I disable password login for all services such as ssh and only use preshared keys.
13. Despite all these precautions, I harbour no illusions about the fact that a truly dedicated cracker could access all of my data with only moderate effort. Therefore, I refrain from doing or storing truly critical tasks/data on my travelling laptop.

My spouse, children and friends think I am absurdly paranoid. For my part, I think them absurdly naive. It remains a matter of good-natured ribbing, but the consequences can be quite serious especially if you are dealing with client data. For what it's worth, your practice of storing your personal and client records on a USB drive gives me the willies. Don't DO things like that. But, hey, I'm absurdly paranoid, I'm told.

BTW, all flavours of Ubuntu come with a firewall and apparmor already installed. However, they are disabled by default--you have to turn them on and/or configure them. Most users don't, which also gives me the willies.

It's your choice how far you want to go with security. That's the nice thing about Linux: you have choices and the tools are already there and don't cost anything, except perhaps, some time and a sometimes steep learning curve. I'm a big proponent of tight security, but even I must admit that Linux is awfully secure right out of the box. Insanely better than Windows anyway.

---

### Post by Hungry Man on 2012-11-19
I would suggest that you set up an AppArmor profile for whichever browser you're using. If you're doing online banking you should configure Firefox to use NoScript and only whitelist the websites you use. 

A combination of Firefox with NoScript and AppArmor is likely the best defense for online banking.

If you us Google Chrome make sure you go to Content Settings and disable Javascript - only enable it for websites you use. Also disable plugins, set all plugins to Click To Play.

Make sure you keep your operating system and your browser up to date. There is no level of security that can protect you from an unpatched system.

If the system is off it can't read info from the USB.

I suggest installing TrueCrypt and using it to store any and all information that's sensitive/ confidential. Create a strong password of at least 12 characters and possibly store a key file on the USB drive as well (useful if an attacker pulls the encrypted info, but not the key file, or if the encrypted info is on the USB put the keyfile on the disk).

Depending how crazy you want to get into it you can start to create your own AppArmor profiles for any other programs you've got installed. You can also look into patching your Lubuntu with GRSecurity/ PaX but this is somewhat tedious, you have to weigh the cost and rewards yourself, I don't know how secret your system needs to stay.


For Windows:
Make sure you stay up to date. Check your OS for updates daily, and every second Tuesday of the month there's a large set of patches. Make sure you keep your browser, plugins, PDF reader, document viewer, etc all up to date.

Disable any services (go to services.msc) that you don't use (be careful here, always look up what a services does before disabling it). For example: if you don't print you can disable the spoolsrv service, which handles printing and has been exploited.

Make sure that you're running EMET ([here is a guide I've written to set EMET up ]("https://insanitybit.wordpress.com/2012/05/30/emet-v3-0-whats-new-and-how-to-set-it-up/")) and that you protect all internet facing profiles. Follow the guide and you should stay secure. Potentially turn DEP, SEHOP, and ASLR to Always On to ensure your system makes use of security mitigations.

If you can move to Windows 8, and you don't mind the interface, I recommend doing so. It's more secure than Vista/ 7. If you're still on XP you should understand that trying to protect your system against a determined attacker is virtually futile without completely overbearing policy etc. It's outdated and can't be secured easily, move to at least Windows 7.

I can't think of much else.

---

### Post by MrIceBlock on 2012-11-20
Thank you all for your replies.

> Windows malware won't run if Windows isn't running. If the system is powered off then nothing will be running at all, including the USB drivers that would tell the system that a USB device is plugged in.
I assume the same applies when booting?

---

### Post by OpSecShellshock on 2012-11-21
Yeah, if you don't boot to Windows then anything that only runs in Windows won't run.

---

### Post by MrIceBlock on 2012-11-22
> **OpSecShellshock said:**
> Yeah, if you don't boot to Windows then anything that only runs in Windows won't run.
Great, because the only reason I asked is because when I removed the hdd to install Lubuntu on my flash drive, the boot screen said "hard drive not found" and then proceeded to boot from the cd-rom, so I just wanted to make sure it never activated windows during that period.

---

### Post by MrIceBlock on 2012-11-23
bump

---

### Post by OpSecShellshock on 2012-11-23
If the hard drive that was removed is where Windows was, then it couldn't have booted. As for the CD ROM drive being used for boot rather than the USB stick, that's most likely because of the way the boot order is set up in the BIOS. You can generally go in and specify which disk you want it to use first, and that will default to a CD most of the time.

---

### Post by MrIceBlock on 2012-11-26
> **OpSecShellshock said:**
> If the hard drive that was removed is where Windows was, then it couldn't have booted. As for the CD ROM drive being used for boot rather than the USB stick, that's most likely because of the way the boot order is set up in the BIOS. You can generally go in and specify which disk you want it to use first, and that will default to a CD most of the time.
So basically if the USB drive is set at a higher position in the BIOS boot order there is no way that a theoretical Windows malware could read what is on the flash drive when booting?

Thanks.

---

### Post by Ms. Daisy on 2012-11-26
I think you're confused about how operating systems work.  The first thing that boots on a computer is the BIOS, which is the hardware initializing.  Once that is complete then the computer looks for an operating system. The BIOS hands control over to the operating system once it finds it.  

If you have told the computer to boot to a flash drive, then all of the other operating systems on your computer remain dormant and essentially turned off.  Whatever operating system is on the flash drive is the only one that will wake up.  

If you have malware on the windows operating system of your computer but you always boot to a linux operating system on a flash drive, then the windows malware will remain turned off.  There are ways to move files from a sleeping windows drive into a running linux operating system (by using 'mount') but you would have to purposely do that- I don't know how you would accidentally do it.

---

### Post by MrIceBlock on 2012-11-26
> **Ms. Daisy said:**
> I think you're confused about how operating systems work.  The first thing that boots on a computer is the BIOS, which is the hardware initializing.  Once that is complete then the computer looks for an operating system. The BIOS hands control over to the operating system once it finds it.  

If you have told the computer to boot to a flash drive, then all of the other operating systems on your computer remain dormant and essentially turned off.  Whatever operating system is on the flash drive is the only one that will wake up.  

If you have malware on the windows operating system of your computer but you always boot to a linux operating system on a flash drive, then the windows malware will remain turned off.  There are ways to move files from a sleeping windows drive into a running linux operating system (by using 'mount') but you would have to purposely do that- I don't know how you would accidentally do it.
Now I see, thanks for the info! :)

---

