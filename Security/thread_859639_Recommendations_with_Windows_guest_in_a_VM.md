---
title: "Recommendations with Windows guest in a VM"
date: 2008-07-14
forum: Security
---

### Post by calibre97 on 2008-07-14
I've just discovered that ZoneAlarm Pro won't work on an XP guest (mine happens to be in VMWare Server 1.06). I would like to know what people have had success with regarding firewalls and AV (and anti-whatever including spyware, phishing etc.)

I'm looking at Online Armor Firewall and ESET Nod32 v2.7 (because I intend to try to create a lean, clean, new Win2K Pro VM for my occasional Windows apps needs). Can people pipe in with their experiences and recommendations? I hope to skip "Don't use BLAH because it SUCKS!" wars;I'm interested in real-world experience. You're using something because it works so I'd like to know what that is. If you can provide interesting information on why you DIDN'T chose something, that'd be pretty useful, too.

For example, ZoneAlarm Pro is out because of incompatibility (unless you can detail what you had to do to get it to work. Saying "well, it just works for me" won't help because it WON'T work for me so no deal). I'm also not interested in anything McAfee or Symantec/Norton.

Free is naturally preferred but NOT a deal-breaker.

---

### Post by rickyjones on 2008-07-15
> **calibre97 said:**
> I've just discovered that ZoneAlarm Pro won't work on an XP guest (mine happens to be in VMWare Server 1.06). I would like to know what people have had success with regarding firewalls and AV (and anti-whatever including spyware, phishing etc.)

I'm looking at Online Armor Firewall and ESET Nod32 v2.7 (because I intend to try to create a lean, clean, new Win2K Pro VM for my occasional Windows apps needs). Can people pipe in with their experiences and recommendations? I hope to skip "Don't use BLAH because it SUCKS!" wars;I'm interested in real-world experience. You're using something because it works so I'd like to know what that is. If you can provide interesting information on why you DIDN'T chose something, that'd be pretty useful, too.

For example, ZoneAlarm Pro is out because of incompatibility (unless you can detail what you had to do to get it to work. Saying "well, it just works for me" won't help because it WON'T work for me so no deal). I'm also not interested in anything McAfee or Symantec/Norton.

Free is naturally preferred but NOT a deal-breaker.

I personally use AVG Free antivirus. 

For firewalls I do not use third party software. I am always behind a hardware NAT firewall and just leave the XP firewall enabled. Works just fine for me.

Sincerely,
Richard

---

### Post by hyper_ch on 2008-07-15
zonealarm (free) works in the VM... as antivirus I normally use antivir. both free.

---

### Post by calibre97 on 2008-07-15
Following up:
That's interesting that the free version of ZoneAlarm works. I finally got the new XP install done in a new VM and I'm trying out, like I said in the original post, Armor Online and ESET Nod32.

---

### Post by NetworkGuy on 2008-07-15
A patch was released by ZoneAlarm to fix the problem caused by the patch installed by Microsoft to fix the problem with DNS.   :whew:

---

### Post by Shazaam on 2008-07-15
> **NetworkGuy said:**
> A patch was released by ZoneAlarm to fix the problem caused by the patch installed by Microsoft to fix the problem with DNS.   :whew:

+1 this is probably your Zone Alarm problem if you recently installed and updated Windows.
I say Windows is Windows. I use the same security setup whether it's a native install or a vm when both have internet access. Antivirus, firewall, and anti-spyware/malware apps.

---

### Post by calibre97 on 2008-07-16
The thing about that patch is ZoneAlarm wasn't a problem when I booted directly into Windows before I VM'd it. The ZoneAlarm forum had several posts stating what I discovered and that was that ZA don't play nice in a VM.

I have to admit, I'm liking Online Armor and ESET AV so I may wind up keeping them.

---

