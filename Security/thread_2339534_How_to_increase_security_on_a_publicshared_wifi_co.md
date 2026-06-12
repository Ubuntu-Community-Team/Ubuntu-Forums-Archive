---
title: "How to increase security on a public/shared wifi connection"
date: 2016-10-10
forum: Security
---

### Post by oygle on 2016-10-10
Kubuntu 16.04.1
All updates
UFW enabled - deny incoming

Travelling so we are using a shared wifi connection. Ran [Shields Up]("https://www.grc.com/x/ne.dll?rh1dkyd2") , and everything was marked "Stealth" except 7 ports:

Ports found to be OPEN were: 25, 143, 443, 450, 465, 803, 993

Yet everything is closed by the UFW rules. Is it showing open because it is a shared IP ?

How can I increase security on any shared wifi connection ? Have needed to do internet banking, etc, as we are travelling. Is [HTTPS Everywhere]("https://addons.mozilla.org/en-US/firefox/addon/https-everywhere/") beneficial ?

---

### Post by Drenriza on 2016-10-10
What is exactly the question.

Do you need to connect to shared WiFi connections outside in the big blue world, or do you share a hot-spot others connect to and you want to secure the guests from eachother?

---

### Post by oygle on 2016-10-10
> **Drenriza said:**
> Do you need to connect to shared WiFi connections outside in the big blue world, or do you share a hot-spot others connect to and you want to secure the guests from eachother?

Travelling, and need to connect to shared WIFI connections.

---

### Post by &amp;KyT$0P# on 2016-10-10
> **oygle said:**
> Ports found to be OPEN were: 25, 143, 443, 450, 465, 803, 993

Yet everything is closed by the UFW rules. Is it showing open because it is a shared IP ?
Well, does your NetworkManager show a [private IP address]("https://en.wikipedia.org/wiki/Private_network") for your computer?  If so, there's no way to be sure what ShieldsUp actually scanned.

Best way to check this is have someone else **on the same network as you** scan your computer from theirs with [FONT=Courier New]nmap[/FONT].  (Zenmap, the GUI frontend for nmap, makes nmap usage much easier.)

> How can I increase security on any shared wifi connection ?
Same way you secure your computer in general.  See [Ubuntu Security]("https://ubuntuforums.org/showthread.php?t=510812") and [Do I need a firewall?]("https://help.ubuntu.com/community/DoINeedAFirewall").

Also, since you're using a Mozilla-based browser, [NoScript]("https://noscript.net/").

> Is HTTPS Everywhere beneficial ?
Yes it would.

---

### Post by oygle on 2016-10-10
> **halogen2 said:**
> Well, does your NetworkManager show a [private IP address]("https://en.wikipedia.org/wiki/Private_network") for your computer?  If so, there's no way to be sure what ShieldsUp actually scanned.

Yes, it shows in the range of 10.0.0.0 - 10.255.255.255

> **halogen2 said:**
> 
Best way to check this is have someone else **on the same network as you** scan your computer from theirs with [FONT=Courier New]nmap[/FONT].  (Zenmap, the GUI frontend for nmap, makes nmap usage much easier.)

We are travelling as the OP stated. I'm not going to walk up to a total stranger and ask them to scan my computer. This **IS** a security forum.  :)

Thanks for the advice on NoScript and https everywhere.

---

