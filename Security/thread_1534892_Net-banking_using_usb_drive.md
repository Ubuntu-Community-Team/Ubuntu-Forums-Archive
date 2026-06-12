---
title: "Net-banking using usb drive"
date: 2010-07-20
forum: Security
---

### Post by realmatrix on 2010-07-20
I am new to ubuntu and haven't really made the full transition into ubuntu for everyday computing. I am primarily concerned about internet security hence I have decided to give it a try.

I use net banking very frequently. Hence I have decided to do all transactions using ubuntu 9.10 installed on dedicated usb 2gb persistant flash drive.
I have not installed any firewall or anti virus..as I was told ubuntu does not need any.

I wish to know if this is a safe and by doing so it does not leave any trace on the host system..even if it is infected by a windows virus.

---

### Post by mikewhatever on 2010-07-20
Running Ubuntu from a USB drive should be quite safe, as long as you use it for online banking. The term 'host system' is somewhat erroneous here, as, in case of running from USB, Ubuntu is not visualized, but simply loads from USB. If Windows is installed on the hdd of the same computer, it plays no role in whatever Ubuntu does.

---

### Post by ratcheer on 2010-07-20
I still think it would be safer to do your internet banking on a Live CD system.

Tim

---

### Post by C.S.Cameron on 2010-07-20
You can even encrypt the home folder on the USB drive in case it is lost.

But I would consider doing a full install to the thumb drive and maybe using a firewall.

---

### Post by bodhi.zazen on 2010-07-20
> **ratcheer said:**
> I still think it would be safer to do your internet banking on a Live CD system.

Tim

I would disagree with that sentiment.

A Live CD is not up to date in terms of security patches, so close to the initial release it does not make a difference, but over time it does.

In addition the majority of the threats to internet financial transactions and NOT on the Ubuntu computer.

The main issues are :

1. Make sure you use https for financial transactions.

2. Use strong passwords.

3. Do not store your passwords for financial institutions in your browser.

4. Make sure you are not a victim of Phishing (see #1).

5. Do not perform financial transactions on a public network (ie public wireless) or if you do, tunnel your traffic over ssh or a VPN.

So long as you do those 5 things, IMO, a live CD does not add any additional security and quite the opposite is more vulnerable due to the lack of security updates.

Linux is not Windows and just by running Ubuntu you are ahead of the curve.

---

