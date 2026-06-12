---
title: "are wireless network safe?"
date: 2008-07-03
forum: Security
---

### Post by dapim on 2008-07-03
i have wireless network , is it safe, even with wpa2-tkip?

well i saw so many tutorials to teach people how to break it?
so is it secure to use?

---

### Post by walkerk on 2008-07-03
wpa2 is pretty secure. i guess it all comes down to what youre protecting. national/corporation secrets probably not... home use, sure.

i wouldn't use tkip... instead aes-ccmp

---

### Post by dapim on 2008-07-03
why u don't use it?

---

### Post by pmlxuser on 2008-07-03
i would say for my computer i use the default security setting that are used by ubuntu when you install it. so far no problems I just make sure that my username and password are very secure for starters. But of course the level of security will also depend on the level of information you want to protect.
I have used wireless for 1 & half years no problem (break in so far on my computer)

---

### Post by kevdog on 2008-07-03
This is kind of a silly question -- yes they are safe -- WPA has not been shown to have been cracked currently.

---

### Post by dapim on 2008-07-03
i only know silly answers, not silly question,

read the tutorials

---

### Post by milosz.galazka on 2008-07-03
I am using wpa2 (aes) in somewhat crowded area so I can suggest changing key from time to time.

---

### Post by brian_p on 2008-07-03
> **milosz.galazka said:**
> I am using wpa2 (aes) in somewhat crowded area so I can suggest changing key from time to time.

Do you do the same for your front door keys too?

---

### Post by milosz.galazka on 2008-07-03
> **brian_p said:**
> Do you do the same for your front door keys too?

Only if I lost one.

I am not too paranoid ;p

---

### Post by update_manager on 2008-07-03
> **dapim said:**
> i have wireless network , is it safe, even with wpa2-tkip?

well i saw so many tutorials to teach people how to break it?
so is it secure to use?

That depends on what you mean by "safe".

If you are using WPA (even older versions of WPA) for access control, I'd be pretty confident that only people with the passphrase (assuming its the appropriate length) will be able to successfully associate with your access point and access your network. 

What it won't protect you from:

- Anyone within 802.11 range from sending you control or data frames (see [here]("http://www.wi-fiplanet.com/tutorials/article.php/1447501") for more details). This means anyone close by can DoS your wireless network by sending deauth frames.

- Anyone sending you crazy malformed packets in an attempt attack your wireless drivers.

- Any of the other common threats, like buffer overflows, XSS, phishing, viruses, etc.


If you are really concerned about security you can use VPNs or SSH tunnels to encrypt your traffic, but this requires buying a service or setting up a server/firewall. If you are going to set up a server you can use an authentication proxy like Squid to restrict web access.

---

### Post by kevdog on 2008-07-03
> Any of the other common threats, like buffer overflows, XSS, phishing, viruses, etc.


What do these threats have to do specifically with wireless networks?

---

### Post by dje on 2008-07-03
For extra security i set my router to restrict access to my wireless network by mac address

---

### Post by hyper_ch on 2008-07-04
> **dje said:**
> For extra security i set my router to restrict access to my wireless network by mac address

You can give your nic a fake mac address very simply by setting it up with "hwaddress"

---

### Post by update_manager on 2008-07-04
> **kevdog said:**
> What do these threats have to do specifically with wireless networks?

Nothing.

Which means that an encrypted wireless network is no more "safe" than an unencrypted one for those things.

---

### Post by dje on 2008-07-04
> **hyper_ch said:**
> You can give your nic a fake mac address very simply by setting it up with "hwaddress"

Yes but they would have to find out the allowed mac address which they could also do, but it's just an extra layer of security ;)

---

### Post by hyper_ch on 2008-07-04
kismet --> shows nicely who is connected to what with which IP... it's not security... rather it's obscurity (IMHO)

I mean if someone is able to crack WPA2 then I don't think such a trivial feature like mac address filtering will hinder them...

---

### Post by Kevbert on 2008-07-04
If you're connected to a wireless router you should change the default password on the router.  Many routers use the default userid as 'admin' and password as 'password'.

---

### Post by hyper_ch on 2008-07-04
or "admin/admin" or "admin/1234" ;)

---

### Post by wirelesswall on 2008-08-10
There is no single security measure, but there are solutions that can secure wireless more thoroughly than others. See [http://snifferproof.blogspot.com/](http://snifferproof.blogspot.com/)

---

### Post by jerome1232 on 2008-08-10
From my understanding a 63 character passphrase is, within reasonable time, uncrackable (A Good processor will take like a year of chewing on your passphrase to crack it).

Unless your neighbor has 10 clustered supercomputers that can chew on cracking your passphrase, wpa2 with a long passphrase is plenty secure.

---

