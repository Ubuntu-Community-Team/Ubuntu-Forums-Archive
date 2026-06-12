---
title: "security surfing with ubuntu"
date: 2010-03-13
forum: Security
---

### Post by AbyssRock on 2010-03-13
hi, I've installed ubuntu intrepid ibex by two weeks, but I've alway used windows, I'm wondering if I surfing with the intrepid ibex firefox v3.0 is as safe as with windows? I ask this in case I have to surf in site that ask password, like e-mail, of credit card number. Another one question, intrepid ibex is older than koala and jacklope, so is it less safe than these other ones, obviouly I've already applied all the updates?

---

### Post by zeroseven0183 on 2010-03-13
I'm no expert in Linux security but I think--- When it comes to surfing the web, the operating system you use or the version of Ubuntu you have is irrelevant. (Although, it helps when you have the latest Firefox to minimize the  pop-ups, the malware automatically loaded to the machines, etc.) But it still depends on the user how much information are sent outside.

Never send your credit card number or e-mail to a site that you think is illegitimate. Never share your password! You might end up a victim.

The bottom line is that data security begins in the hands of the user.


P.S.
I found a good resource to secure your Ubuntu system. Check out [http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/)

---

### Post by OpSecShellshock on 2010-03-13
It would probably be better to upgrade to the current versions of Ubuntu and Firefox. It's not going to really have much effect one way or the other on the security concerns that come with web browsing and the use of sensitive information, but keeping the system updated is a good habit to form. Any site that asks for medical or financial data should use encrypted communication (in which case the address bar will say [https://)](https://)). This is true with any OS and any browser. There are fewer (if any) password stealing trojans for Linux, so in that sense there's a somewhat lower risk of automated interception of sensitive information. Just remember that there is no technological substitute for caution.

---

### Post by ja660k on 2010-03-15
okay, 
firstly nothing is private on the internet anymore BUT,

if your seriously paranoid... write down the MAC address of your router/gateway. (at home)
check it using the cmd
```
arp -a
```
if that for some reason changes at home. then chances are somebody is passively attacking you.(listening to your web traffic)

also in places like internet cafe's or anywhere with a public wireless connection its probably a good idea to VPN or SSH tunnel your web traffic
for sensitive information so that if someone is in fact listening to your traffic all they get to see is encrypted garbage.

that being said, fundamentally always look at the url. if something should be https and its not, stop.

---

### Post by Ijan on 2010-03-15
There are several threads dealing with this topic, you can find them via the search function.

---

