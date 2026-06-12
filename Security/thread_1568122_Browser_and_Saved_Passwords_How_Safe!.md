---
title: "Browser and Saved Passwords: How Safe?!"
date: 2010-09-04
forum: Security
---

### Post by Kixtosh on 2010-09-04
I'm about to do a new install of some flavour of Ubuntu on a laptop that I intend to use for online banking and other sensitive stuff (even e-mails are "private" often enough).

I'd like to know: how safe is it to use the "Save Password" feature that a browser like Chromium offers?

What about a fingerprint reader? Is using one of these more for convenience than security, or does it add a better level of security than a browser for saving passwords?

---

### Post by uRock on 2010-09-04
I know in firefox, you can save the passwords, then have the browser ask you for a master password.

---

### Post by FuturePilot on 2010-09-04
In Firefox if you set a master password the database of passwords gets encrypted. Chrome/Chromium stores them in plain text no matter what (Bad!). Of course a workaround for that would be to just encrypted your entire home directory.

---

### Post by uRock on 2010-09-04
> **FuturePilot said:**
> In Firefox if you set a master password the database of passwords gets encrypted. Chrome/Chromium stores them in plain text no matter what (Bad!). Of course a workaround for that would be to just encrypted your entire home directory.
Encrypting the home is a great idea.

If you have already installed, then you can create another account for doing your private stuff and tell the Users & Groups application to encrypt the home folder for the new account.

---

### Post by FuturePilot on 2010-09-04
> **uRock said:**
> Encrypting the home is a great idea.

If you have already installed, then you can create another account for doing your private stuff and tell the Users & Groups application to encrypt the home folder for the new account.

There is also the ecryptfs-migrate-home script. No need to make a new user.

---

### Post by Kixtosh on 2010-09-04
> **FuturePilot said:**
> In Firefox if you set a master password the database of passwords gets encrypted. Chrome/Chromium stores them in plain text no matter what (Bad!). Of course a workaround for that would be to just encrypted your entire home directory.What a pity Chromium doesn't encrypt them by default, and yes: that does sound like a very bad idea. Perhaps the fingerprint reader might solve that issue? I'm not sure if it's as convenient to use a fingerprint reader for opening websites with passwords as it is the way I've been used to doing it with WinXP: if you navigate to a website with a saved fingerprint password, the reader is automatically activated and ready to access the account after a finger swipe.

I prefer to use Chromium, if possible, because it seems a lot faster on slower processors, and this being an ultra-light, it only has a 1.2 GHz CPU (and is also limited to 1.2GB of RAM), but that's another topic!

As for encrypting the home directory: does that slow anything down in terms of performance, or not at all? Are there any convenience factor considerations involved?

---

### Post by jeight on 2010-09-04
Use firefox and yes your passwords are safe. Much safer than you would ever get using windows. Encrypting your /home is only good if you are nervous about your laptop ever getting stolen.

---

### Post by BkkBonanza on 2010-09-04
Fingerprint readers have been demonstrated to be insecure. Just think how many of your fingerprints are all over your keyboard and computer.

Personally I don't store important passwords in browsers. The reason people do this is to save time typing them in but then anyone with passing access to your computer saves the same time too. It's even more silly on a laptop where someone can steal it. 

If this system is meant to be for online sensitive work then don't do anything that obviously reduces your security. Install Certificate Patrol add-on in Firefox to keep a watch over certificates from sites you use. 

If you use the laptop with wifi then make sure you use WPA2 encryption. Don't enable VNC/Remote Desktop. Use a ssh proxy if on public links.

Definitely use an encrypted home on a laptop. If you are really trying to make a secure system configure it for two-factor authentication. Also, make sure the suspend/hibernate/screensaver functions are password protected otherwise someone can suspend the laptop, grab it and run.

Encrypted home slows disk access by about 1%. Are trying to make a secure system or a fast system, a convenient system? Decide on your priorities first.

---

### Post by Kixtosh on 2010-09-04
Wow! Lots of interesting points, BkkBonaza.

This is a laptop, but when I travel with it, I enable the BIOS password (which shows up within one second of pressing the power button, even before the BIOS splash screen). Of course, that wouldn't protect the information on the hard drive if it were removed from the laptop. 

Otherwise, that's a good point about the browser being able to automatically log in to sensitive sites, with saved user and password information ... In case of theft, or even a potential burglar in the house taking the time "off work" to have a peek, it sounds like a very valid concern that I hadn't thought of (I'm using a fingerprint reader to log in for the moment, so I don't currently use browser memorized profiles).

Of course, everything comes down to compromise at some point. I like the convenience of a fingerprint reader, but I understand it may not be foolproof. Encrypting the Home directory sounds like it's easy to do, without many negative factors to consider (if any at all). The convenience of passwords saved in a browser application sounds almost reckless on a laptop, I suppose. Having to type eight or ten character passwords in security conscious gibberish every five minutes sounds like a nuisance, but maybe it's also a necessary evil after all.

---

### Post by BkkBonanza on 2010-09-04
I do use it to remember passwords for many sites like this forum. But not for my money accounts and things like ebay.

Regarding hard drive - everything on your system is on the hard drive, so removing it is really removing your system. They can plug it into another PC and get full access unless you have an encrypted home. The BIOS password can be reset with access to the internals - not sure where on laptops but there has to be a "reset" like on desktop systems. These vulnerabilities have primarily to do with theft. 

No one expects their laptop to be stolen. The real question is "what is the downside when it is stolen?". An encrypted home cancels out almost all that downside assuming you have a good strong password.

With encrypted home two factor auth you move the "key file" onto a usb flash stick. Then you need to know the password and have the flash stick to get in. This is one step further than just a password but entails a bit more hassle (and you need to have a backup of the key elsewhere or you can lose the flash stick and be locked out, and the flash stick needs to be config'd to mount during boot).

I do use a password safe program for storing all my hundreds of passwords but I never leave it active when I'm not immediately using it. I've just found in the past that I will some random day forget a password. This reduces it to one master password to remember. KeepassX is in the repos. The main thing here is that it's not automatically always active when the browser is open. It does allow copy/paste which makes it easier to use stronger passwords.

---

### Post by wacky_sung on 2010-09-05
Yeah storing password in browser inregarding of the encryption level is still crackable.My personal advise is to store those non crucial password in browser only and the best password storage is still on your head. :)

---

### Post by bodhi.zazen on 2010-09-05
> **Kixtosh said:**
> I'm about to do a new install of some flavour of Ubuntu on a laptop that I intend to use for online banking and other sensitive stuff (even e-mails are "private" often enough).

I'd like to know: how safe is it to use the "Save Password" feature that a browser like Chromium offers?

What about a fingerprint reader? Is using one of these more for convenience than security, or does it add a better level of security than a browser for saving passwords?

Personally, I store passwords of any significance (banking for example) on keepassx.

keepassx is cross platform and runs off a flash drive.

[http://www.keepassx.org/](http://www.keepassx.org/)

---

### Post by d3v1150m471c on 2010-09-05
"stupid passwords", like crap you use to say woogitaboogitta to your friends on facebook i'd say save them on firefox. for serious things like banking and paypal i wouldn't. that way vip passwords, even if encrypted, are not stored on your system for someone to crack.

---

### Post by Kixtosh on 2010-09-05
Well, well, well. So here is what I intend to do:

1) Install Ubuntu, and figure out how the fingerprint reader operates compared to Win XP currently in use. If it works in the same way, then there would be no need to use the browser password save feature, so I'll just disable it altogether.

2) Figure out how to encrypt the /home directory, and see how that works. It seems like a good idea no matter what else I do.

3) Try out KeePassX, and see how that works. This also seems like a good idea and not very difficult to implement.

The whole point here is to have an easy to use laptop (or even a nettop) that is mostly used for sensitive stuff. Something that I can pop out and hook up on my desk on a whim within minutes. It doesn't need to be a speed demon, by any means, but I don't want to be waiting five minutes for boot times either (or ten seconds for every new browser tab).

The laptop I'm thinking about is three years old now, and would only fetch about $200 on eBay, so it doesn't seem worth selling. It's in good condition, has a fingerprint reader that seems to work with a Live CD, and weighs just 2.7 lbs (1.22 Kg.). It's very slow to boot with Windows, but I have high expectations that it'll work very well with some of the lighter Ubuntu distros (that I've already tried with a much older laptop with good results). It also has a Trusted Platform Module (TPM) Embedded Security Chip, but I don't see how that would be used. 

This way, it seems to me that it could serve a very useful purpose.

---

### Post by uRock on 2010-09-05
> **Kixtosh said:**
> As for encrypting the home directory: does that slow anything down in terms of performance, or not at all? Are there any convenience factor considerations involved?
I use the encrypted private folder for some of my stuff and it doesn't seem to slow the system down. 

Most physical PC thieves run straight to the pawn show, so I am not very worried about someone stting there for days trying to crack my encryption, when the passphrase looks like this; 
```
a5dde4b48675309rdacf7e842ab4fa5df11
```

No this isn't the passphrase to my current system and yes I still shuffled the numbers and letters around.

---

### Post by Kixtosh on 2010-09-05
> **uRock said:**
> ... Most physical PC thieves run straight to the pawn show, so I am not very worried about someone stting there for days trying to crack my encryption, when the passphrase looks like this; 
```
a5dde4b48675309rdacf7e842ab4fa5df11
``` ...He he he!

---

### Post by Agent ME on 2010-09-05
To the people mentioning fingerprint readers - as far as I know, those can't be used for actual encryption. You can't use them to encrypt your passwords. They're only used for authentication on a running system. They don't stop someone with physical access to your machine from looking at your hard drive.

---

### Post by Kixtosh on 2010-09-05
> **Agent ME said:**
> To the people mentioning fingerprint readers - as far as I know, those can't be used for actual encryption. You can't use them to encrypt your passwords. They're only used for authentication on a running system. They don't stop someone with physical access to your machine from looking at your hard drive.I'm not sure what you mean, but as far as I know, I can currently use the fingerprint reader in Windows to encrypt files, folders, drives and passwords. It's probably enabled by the software used. In fact, it even comes with a warning that you must backup your profile before any new installation, and import it again after installation, or encrypted files will be lost forever.

OmniPass, from Softex Inc. 

[http://www.softexinc.com/product.asp?product=omnipass3](http://www.softexinc.com/product.asp?product=omnipass3)

> Secure Single Sign-On and Enterprise Class Password Management including support for Internet Explorer and Mozilla Browsers (Firefox)

Multi-device and Multi-factor Authentication

Biometrics

Smart Cards

TPM Support

Hardware Tokens

File and folder encryption

Encrypted file sharing

Secure E-mail, VPN and certificate access

> ... OmniPass creates and maintains an encrypted &#8220;vault&#8221; for your passwords. ...

---

