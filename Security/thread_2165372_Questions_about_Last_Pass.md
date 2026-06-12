---
title: "Questions about Last Pass"
date: 2013-08-04
forum: Security
---

### Post by wbee on 2013-08-04
Hello,

I did change all my passwords as a precaution after the issue that affected this site.

A week or two previous,my credit card company cancelled my old number and issued me a new card because somebody had compromised their data.

*******

My Google Chrome browser has an extension for Last Pass. Should I install and use it? Will my computer be more secure having done so? Are there any drawbacks of installing and using it?

------

Thank you.

---

### Post by bapoumba on 2013-08-05
I personally use KeePassX and store the db on Dropbox. Has versions for all platforms (I've tested it and use it on Linux, MacOS and mobile devices). I use several machines. Works great. The db is encrypted, and you can ask for both a password and a specific file to be present on the device to be able to open it.

When I decided to use it, I also checked on LastPass. I do not recall exactly what I did not like about it :)

[https://www.keepassx.org/](https://www.keepassx.org/)

---

### Post by aze555666 on 2013-08-05
I've been using lastpass for a 2 months now (since password databases get hacked one after another these days : ubuntu, fb/twitter, OVH, musicbrainz, and some others I don't recall).
I use it for any new account by creating a unique new strong password, and I'm in the process of changing all my old passwords (priority : those which were identical to the one I had here and those which were identical to the one I was using on OVH)

I think it's a great tool and I'm happy with it. I can only encourage you to use it too, so you can use strong&unique password everywhere and not have to worry next time some site loses its database.

---

### Post by bapoumba on 2013-08-06
Thanks aze555666 :)

---

### Post by wbee on 2013-08-19
Thank you.:-)

---

### Post by Welly Wu on 2013-08-20
As an iconoclast, I deleted my LastPass Premium account a few days ago. LastPass had a security breach on May 3rd, 2011 which may seem eons ago, but they were never 100% forthcoming or transparent about the incident and they paid for a third-party security audit, but they never published the findings. LastPass is secure if you pay for Premium service for 12 months and you use two-factor authentication especially if you purchase a pair of Yubico Yubikeys which I have done so. Your e-mail address and your LastPass master password generate a unique encrypted hash with a nonce and it uses PKBDF2 with a SHA-256 hash algorithm and AES CBC 256 bit cipher that is stored locally on each PC and web browser that you have installed it on. However, your encrypted credentials and secure notes are stored in the cloud on their servers. They don't publish any reports on how many times they have been scanned by intruders and they don't report whether they have hired an independent security company to audit their systems either on a regular basis. LastPass is for the average Joe who is tired of managing multiple complex passwords and for someone who prefers convenience over security. That's the bottom line with them.

I switched to KeePassX and KeePass 2. I use GRC's password haystacks, Microsoft's password strength analyzer, and passfault to determine if I generated secure yet memorable master passwords for my data. Then, I use KeePass 2 to analyze the strength of my master password. I also use a key file for second factor authentication. KeePass 2 is not easy to configure to work with both Mozilla Firefox and Google Chromium using the KeeFox and ChromeIPass plug-ins as the instructions do vary depending upon the sources that document the installation guides. However, KeePassX and KeePass 2 are free, libre, open source and they are well trusted and used worldwide. They are also free of charge to use with plenty of documentation, plug-ins, extensions, and other resources for KeePass 2.

Do what works for you. I switched to KeePassX and KeePass 2 because I prefer FLOSS software and I trust them. I don't trust LastPass and their customer service and technical support are deliberately closed mouth when customers ask them questions about their security setup and configuration for obvious reasons. They want to keep making money.

It comes down to whom you trust. Do you trust a small privately owned company with all of your secrets? Or, do you trust yourself to stay secure? I trust myself. I make multiple backups of my encrypted data and I upload them to CrashPlan+ and Ubuntu One.

---

### Post by bapoumba on 2013-08-20
Thanks Welly Wu. 2011 rings a bell, but I'm not sure. I honestly cannot remember what I did not like too much when I had a look at LastPass. It also had something to do with Xmarks that I was using at the time and do not use any more either. Something related to the application passwords, or the way one  app bought the other, I should have taken notes :/

---

### Post by Traxster on 2013-08-21
> **Welly Wu said:**
> As an iconoclast, I deleted my LastPass Premium account a few days ago. LastPass had a security breach on May 3rd, 2011 which may seem eons ago, but they were never 100% forthcoming or transparent about the incident and they paid for a third-party security audit, but they never published the findings. LastPass is secure if you pay for Premium service for 12 months and you use two-factor authentication especially if you purchase a pair of Yubico Yubikeys which I have done so. Your e-mail address and your LastPass master password generate a unique encrypted hash with a nonce and it uses PKBDF2 with a SHA-256 hash algorithm and AES CBC 256 bit cipher that is stored locally on each PC and web browser that you have installed it on. However, your encrypted credentials and secure notes are stored in the cloud on their servers. They don't publish any reports on how many times they have been scanned by intruders and they don't report whether they have hired an independent security company to audit their systems either on a regular basis. LastPass is for the average Joe who is tired of managing multiple complex passwords and for someone who prefers convenience over security. That's the bottom line with them.

I switched to KeePassX and KeePass 2. I use GRC's password haystacks, Microsoft's password strength analyzer, and passfault to determine if I generated secure yet memorable master passwords for my data. Then, I use KeePass 2 to analyze the strength of my master password. I also use a key file for second factor authentication. KeePass 2 is not easy to configure to work with both Mozilla Firefox and Google Chromium using the KeeFox and ChromeIPass plug-ins as the instructions do vary depending upon the sources that document the installation guides. However, KeePassX and KeePass 2 are free, libre, open source and they are well trusted and used worldwide. They are also free of charge to use with plenty of documentation, plug-ins, extensions, and other resources for KeePass 2.

Do what works for you. I switched to KeePassX and KeePass 2 because I prefer FLOSS software and I trust them. I don't trust LastPass and their customer service and technical support are deliberately closed mouth when customers ask them questions about their security setup and configuration for obvious reasons. They want to keep making money.

It comes down to whom you trust. Do you trust a small privately owned company with all of your secrets? Or, do you trust yourself to stay secure? I trust myself. I make multiple backups of my encrypted data and I upload them to CrashPlan+ and Ubuntu One.

 
     I think it is noteworthy to point out however, that if any user credentials were ever stolen from the lastpass server, they would be useless without the passwords to decrypt them which are not stored on their servers.  I think it all comes down to proper key and/or passphrase management. Any security expert would probably recommend changing your passphrase frequently as well. I personally do, and choose passphrases that have upper and lower case letters, numbers and symbols mixed in...If you want to take extra precautions you can also use a virtual keyboard to input in you passphrase and purchase a yubi key.


traxster

---

### Post by Buntu Bunny on 2013-08-23
> **Welly Wu said:**
> LastPass is secure if you pay for Premium service for 12 months and you use two-factor authentication especially if you purchase a pair of Yubico Yubikeys ...<snip>... However, KeePassX and KeePass 2 are free, libre, open source and they are well trusted and used worldwide. They are also free of charge to use with plenty of documentation, plug-ins, extensions, and other resources for KeePass 2.

Thanks Welly Wu, those are the bits that sometimes get left out in users' discussions about these.

---

### Post by Welly Wu on 2013-08-23
I'd rather go through the installation and set up once to get KeePassX or KeePass 2 and KeeFox or ChromeIPass rather than rely on LastPass or some other third-party company for my credentials and security. It's not terribly difficult to do and it only needs to be done once. If I can figure it out, then anyone can and I don't consider myself to be a special GNU/Linux user.

You got to understand that without coming clean about serious security breaches, it's hard to trust a third-party vendor for something as important as your credentials and secure notes. LastPass failed to inform their users about their past security breaches and they hardly published anything about it. It's all secret and without that crucial information, you can't verify their claims that the problems are solved. LastPass users are blindly trusting the company to keep their word and their customer's confidential data protected.

You'll find that it's not difficult to breach LastPass accounts if two-factor authentication is not purchased. Most people come up with bad passwords using single factor authentication and that's the problem. It's a security breach waiting to happen and you can't blame LastPass for not purchasing their 12 month premium service for two-factor authentication. They warn their customers about this in their terms of service and their security notes about their freemium product and service.

KeePassX and KeePass 2 make it next to impossible for someone else to hack into your encrypted database so long as you keep your key file and encrypted database offline. This is what I have chosen to do to enhance my security. I don't upload my KeePassX or KeePass 2 key files and encrypted database to any remote server or to the cloud. It's inconvenient because I have to use my sole PC to access my encrypted database, but I know nobody else can access it either.

Putting your stuff in the cloud is sometimes risky if you're dealing with third-party companies looking to do business with you. They have an incentive to sell you their products and services monthly or annually and they don't have the expertise, technical infrastructure, or the resources to survive a well-funded and sophisticated advanced persistent threat or attack. They don't even cover their customers in case of such a security breach hoping that it will never happen to one of their customers data.

I'm not saying that you should ditch LastPass if that's your preferred option, but realize that the company is in no condition to notify you if you're being targeted in an investigation and the government or a law firm has a court order to the company to hand over your data to them. Attacking the individual PCs that contain your encrypted, hashed, and nonce LastPass master password is as simple as a search warrant and seizure of property.

This is why it is important to encrypt your full disk and to encrypt your /home partition with a separate password for added security. In case of a search warrant or seizure, you don't have to comply with providing the passwords needed to decrypt your data and you can hire attorneys to fight them in court. You may not win in court, but you'll have your day in court.

Ubuntu's LUKS and ecryptfs are particularly effective against forensic analysis techniques because they aren't widely popular and even cold boot attacks won't work without the encryption keys. Storing your data offline like your credentials or your secure notes is easy to do and it is very safe and secure. Just don't upload it to your favorite cloud storage provider and you'll be good. You can fight the good fight in court if necessary.

LastPass doesn't divulge how many times they have had a court order or national security letter issued to them about a particular customer and the federal government doesn't divulge how many times they have successfully accessed your LastPass or other cloud based credentials using your master passwords. It's murky and this is why it's not safe to do upload that kind of data to the cloud.

---

### Post by Welly Wu on 2013-09-02
You can increase the key transformations for PKBDF2 in KeePassX and KeePass 2 to increase it to a much higher number. I increased both of my encrypted databases to 512,000.00 iterations. I also switched from AES to TwoFish cipher because AES is partially broken and TwoFish is not broken yet. TrueCrypt and KeePassX and KeePass 2 support AES-NI for hardware accelerated encryption and decryption. TwoFish is an AES finalist and it is nearly as fast as AES, but TwoFish is unbroken.

---

### Post by Welly Wu on 2013-09-02
[http://www.differencebetween.net/technology/difference-between-aes-and-twofish/](http://www.differencebetween.net/technology/difference-between-aes-and-twofish/)

---

