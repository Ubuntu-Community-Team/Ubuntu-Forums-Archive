---
title: "data security for travel with laptop"
date: 2013-05-12
forum: Security
---

### Post by teacherjeff on 2013-05-12
I'm going to be doing some backpacker-style travel, using public transportation, staying in budget lodgings, using public wifi networks, etc. For the first time, I'm going to have to bring along a netbook (Windows 7 / Ubuntu 13.04 dual boot) for work.

I'm actually more worried about the data than I am about the hardware. Let me emphasize that the data on my computer isn't anything really high-value: I don't feel the need to make my computer NSA-proof or even determined-and-knowledgeable-hacker-proof.

I will store the data I'm concerned about in the home directory on the Ubuntu partition. 

I use Dropbox to sync the data in the Dropbox directory (which is, of course, also in the Ubuntu home directory).

I just want to be reasonably confident that if somebody should steal my computer, they won't be able to access the data without some serious effort, and thus would probably reformat the drive and reinstall the OS before selling it or whatever.

So here's what I've done:

1. Set a HDD pasword in the BIOS.
2. Turned on encryption of the home directory when I installed Ubuntu.
3. Set a login password.
3. Chose strong (and different) passwords for all these things.

Will this give me a reasonable level of protection?

---

### Post by tubbygweilo on 2013-05-12
teacherjeff,
Should do unless you forget anyone of them due to excitement of travel. So, will you be carrying plain / clear text versions of these passwords / phrases with you?

---

### Post by HermanAB on 2013-05-13
Use full disk encryption with a long password (>12 chars).

---

### Post by D7Gd on 2013-05-13
[QUOTE=teacherjeff]I use Dropbox to sync the data in the Dropbox directory (which is, of course, also in the Ubuntu home directory).[/QUOTE]

Others might disagree, but in my opinion this is an incredibly bad idea.

[http://money.cnn.com/2011/06/22/technology/dropbox_passwords/index.htm](http://money.cnn.com/2011/06/22/technology/dropbox_passwords/index.htm)

**"For _four hours_ on Sunday, a site glitch let visitors use any password to log in to customers' accounts."**


[QUOTE=teacherjeff]I just want to be reasonably confident that if somebody should steal my computer, they won't be able to access the data without some serious effort, and thus would probably reformat the drive and reinstall the OS before selling it or whatever.[/QUOTE]

Remember not to leave your laptop in the sleep/suspend state when you are not around! The [cold boot attack]("https://en.wikipedia.org/wiki/Cold_boot_attack") can render most of the encryption methods useless. In general, don't leave it where someone can gain physical access to it for a long period of time, if you can avoid it.

Also something to keep in mind:
[https://www.schneier.com/blog/archives/2009/10/evil_maid_attac.html](https://www.schneier.com/blog/archives/2009/10/evil_maid_attac.html)

---

### Post by sudodus on 2013-05-13
> **tubbygweilo said:**
> teacherjeff,
Should do unless you forget anyone of them due to excitement of travel. So, will you be carrying plain / clear text versions of these passwords / phrases with you?
+1

---

### Post by sudodus on 2013-05-13
> **HermanAB said:**
> Use full disk encryption with a long password (>12 chars).

This will give you a higher level of security, but I think your original plan will do, according to what you described in the opening post.

---

### Post by Soul-Sing on 2013-05-13
> **HermanAB said:**
> Use full disk encryption with a long password (>12 chars).

yep, consider it as a usb stick with private information.

---

### Post by tubbygweilo on 2013-05-14
teacherjeff,
You mentioned a machine for work and I wondered if you may be travelling in or out of the US? If so then eff.org has a few pointers 
[https://www.eff.org/wp/defending-privacy-us-border-guide-travelers-carrying-digital-devices](https://www.eff.org/wp/defending-privacy-us-border-guide-travelers-carrying-digital-devices). I feel these points should also be considered when crossing into countries if your kit is holding sensitive work or sensitive social data.

---

