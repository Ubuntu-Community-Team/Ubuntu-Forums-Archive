---
title: "Ubuntu can read teh secret iPhone data!"
date: 2010-05-27
forum: The Cafe
---

### Post by ssj6akshat on 2010-05-27
[http://marienfeldt.wordpress.com/2010/03/22/iphone-business-security-framework/](http://marienfeldt.wordpress.com/2010/03/22/iphone-business-security-framework/)

OMG! Loonix is so 1337 Hax0r.

Now lets see Apple improves its security or blocks linux users.

Standard Chartered must be facepalm.

[http://www.itbusinessedge.com/cm/community/news/mt/blog/standard-chartered-switches-from-blackberry-to-iphone/?cs=41229](http://www.itbusinessedge.com/cm/community/news/mt/blog/standard-chartered-switches-from-blackberry-to-iphone/?cs=41229)

---

### Post by ssj6akshat on 2010-05-27
Can anyone test encryption with Android?

---

### Post by mihai.ile on 2010-05-27
as far as I know android does not use the SD card for sms/email storage so it does not matter as the internal memory is never accessible when connected to the pc...
On android you have complete access to the SD card and everything on it, heck if you want you can just take it out and put it directly in your pc through an micro/sd adapter.

---

### Post by tgalati4 on 2010-05-27
So what you are saying is Ubuntu's Lucid Lynx is a security risk for iPhones?  Then Apple should take appropriate steps and block Ubuntu's proliferation.

---

### Post by juancarlospaco on 2010-05-27
*Security?, Apple?*

---

### Post by ssj6akshat on 2010-05-27
> **tgalati4 said:**
> So what you are saying is Ubuntu's Lucid Lynx is a security risk for iPhones?  Then Apple should take appropriate steps and block Ubuntu's proliferation.

No.This clearly shows that Apple's security is trash,as far as I know them they will block linux access in their next update instead  of improving security.

---

### Post by donkyhotay on 2010-05-27
> **ssj6akshat said:**
> No.This clearly shows that Apple's security is trash,as far as I know them they will block linux access in their next update instead  of improving security.

It worked for sony! Oh, wait...

---

### Post by Sealbhach on 2010-05-27
> **tgalati4 said:**
> So what you are saying is Ubuntu's Lucid Lynx is a security risk for iPhones?  Then Apple should take appropriate steps and block Ubuntu's proliferation.

This guy thinks so:  [http://twitter.com/louis6321/status/14831563279](http://twitter.com/louis6321/status/14831563279)

.

---

### Post by ssj6akshat on 2010-05-27
> **Sealbhach said:**
> This guy thinks so:  [http://twitter.com/louis6321/status/14831563279](http://twitter.com/louis6321/status/14831563279)

.

I can see this guy's intelligence from his avatar

---

### Post by mihai.ile on 2010-05-27
We all should except a cease and desist letter from apple any time now :D

---

### Post by jrothwell97 on 2010-05-27
So what you're saying is that if you plug in a soft-encrypted external storage device into a computer, you can read its contents?

God forbid!

---

### Post by blur xc on 2010-05-27
> **ssj6akshat said:**
> I can see this guy's intelligence from his avatar

Yeah, the guy look like a genius- but why is that Linux's fault?  And my heart sank, even if just a little bit, when I read that headline this morning.  All it will mean is that my need for iTunes will return once again, soon...  I better good make use of this time while I can... :(

BM

---

### Post by aysiu on 2010-05-27
The only reference I've seen to this in Google News so far is [Ubuntu Lucid Lynx 10.04 can read your iPhone's secrets](http://www.zdnet.com/blog/hardware/ubuntu-lucid-lynx-1004-can-read-your-iphones-secrets/8424)

ZDNet blogger Adrian Kingsley-Hughes says [quote=emphasis mine]This, quite honestly, is a staggering flaw. It basically allows **anyone capable of driving a Linux PC** to copy data off of an iPhone without the owner of the phone having any idea whatsoever that this has happened.[/quote] It doesn't really take that much to "driv[e] a Linux PC." Anyone can get a free live CD and just boot it on their computer. Maybe they don't know how to troubleshoot a Broadcom wireless card or even how to use Synaptic Package Manager. They don't have to. Just boot up the CD and plug the iPhone in. That's it. It just appears in the file browser. Nothing to drive.

The comments are quite silly, though. A lot of people spout the half-truth that physical access is compromised security by definition. What they're missing out on is that in [iPhone in Business Security Overview](http://images.apple.com/iphone/business/docs/iPhone_Security_Overview.pdf), Apple says > iPhone 3GS offers hardware-based encryption. iPhone 3GS hardware encryption uses AES 256 bit encoding to protect all data on the device. Encryption is always enabled, and cannot be disabled by users. If you can just plug in a device by USB and immediately read all of its contents, it is **not** encrypted... or the encryption is not implemented properly.

---

### Post by mihai.ile on 2010-05-27
maybe they created a folder/file called "data" which uses the feature and so they can put the above sentence.

---

### Post by pwnst*r on 2010-05-27
> **mihai007 said:**
> maybe they created a folder/file called "data" which uses the feature and so they can put the above sentence.

How much wishful thinking can a zealot have?

---

### Post by ssj6akshat on 2010-05-28
Now I can understand,the protection wasn't bypassed,there wasn't any to start with.That is why apple forces iDevices to sync only with iTunes.

---

### Post by Furcifer on 2010-05-28
> **aysiu said:**
> The only reference I've seen to this in Google News so far is [Ubuntu Lucid Lynx 10.04 can read your iPhone's secrets]("http://www.zdnet.com/blog/hardware/ubuntu-lucid-lynx-1004-can-read-your-iphones-secrets/8424")

ZDNet blogger Adrian Kingsley-Hughes says  It doesn't really take that much to "driv[e] a Linux PC." Anyone can get a free live CD and just boot it on their computer. Maybe they don't know how to troubleshoot a Broadcom wireless card or even how to use Synaptic Package Manager. They don't have to. Just boot up the CD and plug the iPhone in. That's it. It just appears in the file browser. Nothing to drive.

The comments are quite silly, though. A lot of people spout the half-truth that physical access is compromised security by definition. What they're missing out on is that in [iPhone in Business Security Overview]("http://images.apple.com/iphone/business/docs/iPhone_Security_Overview.pdf"), Apple says  If you can just plug in a device by USB and immediately read all of its contents, it is **not** encrypted... or the encryption is not implemented properly.

+1 for "not implemented properly".  The iPhone actually does the decryption and presents the data in the clear to the mount request.  At the same time, I can attest that AppBox Pro does not present its "Secure Wallet" data in the clear from the filesystem, pinlocked phone or not.  In fact, I can't even figure out where it's stored just yet...  Not a lot of info out there on how or what AppBox Pro uses for the Secure Wallet encryption, where the app files are stored, etc.

---

