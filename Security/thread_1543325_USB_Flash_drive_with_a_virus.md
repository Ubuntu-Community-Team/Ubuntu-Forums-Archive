---
title: "USB Flash drive with a virus"
date: 2010-07-31
forum: Security
---

### Post by Mduke on 2010-07-31
Hi, this may belong to the "beginner talk" section as this is probably a very ridiculous and noobish question, but I'd like some closure on this.

A while back I had been using ubuntu on a live cd after my windows partition had been taken over by a virus, which at the time I thought had been removed by my anti virus (and then took out winlogon) and I did a system repair instead of a complete reformat because I didn't want to lose all of my files. After repairing, I noticed some things like what looked like fake "this page has been blocked based on your security preferences" on major sites like youtube, myspace and facebook. I ran another virus scan with a different AV and strangely it detected a behavioural software keylogger, which after looking it up seemed to be something that could only be installed with physical access to the system, which confused me. Anyway, this is when I started to use the live CD to copy some of my music, videos, pictures etc. onto my flash drive. From what I can remember, I used this USB on my main computer without problems, but the last time I used it (few months ago) I ran a virus scan afterwards, just to feel safe and it came up with a couple java exploit trojans. This was probably just coincidence and I hadn't ran a scan in a day or two, possibly even a false positive as I noticed no decrease to system performance or any odd happenings.


So, my questions are: Is it even possible for a virus from a windows partition to copy itself to a USB flash drive on an ubuntu live cd; and is it possible (if the virus was even capable of this) if I insert the flash drive into my ubuntu computer, it could do anything like transfer across my WLAN to my windows computer, or even copy its files onto ubuntu but be unable to do anything? Which brings me to another question: if I visit a website that may contain drive-by malware or a virus of any type, is it capable of acting at all, such as even trying to transfer itself into my home folder, or does it not even recognize ubuntu at all and do nothing?

Sorry if any of this of plain dumb, but I'm very tired and paranoid and want to use my flash drive again to retrieve some files off of it.

 Thanks.

---

### Post by FuturePilot on 2010-07-31
> Is it even possible for a virus from a windows partition to copy itself to a USB flash drive on an ubuntu live cd

No. Windows would have to be running to do that and you can't run 2 OSes at once.

> and is it possible (if the virus was even capable of this) if I insert the flash drive into my ubuntu computer, it could do anything like transfer across my WLAN to my windows computer, or even copy its files onto ubuntu but be unable to do anything?

No. A Windows virus will only run on Windows.

> Which brings me to another question: if I visit a website that may contain drive-by malware or a virus of any type, is it capable of acting at all, such as even trying to transfer itself into my home folder, or does it not even recognize ubuntu at all and do nothing?


Once again, if it's targeted at Windows it will only run on Windows.

---

### Post by Mduke on 2010-07-31
> **FuturePilot said:**
> No. Windows would have to be running to do that and you can't run 2 OSes at once.



No. A Windows virus will only run on Windows.



Once again, if it's targeted at Windows it will only run on Windows.

Thanks, this makes me feel a bit better. I know ubuntu is immune to windows viruses, but I guess I was mainly just worried it would somehow send itself over the wireless network when I plug it into my ubuntu computer, SOMEHOW make its way past my windows computers firewall and AV/anti spyware, and infect the computer (absolutely ridiculous, even I know that) but I get strangely hung up on ridiculous things like this, and despite knowing it likely isn't even possible, I can't stop myself from worrying. Probably need a psychiatrist.

Anyway, I guess despite all of this one last question would be: is it even at all common for viruses to be able to send themselves through a WLAN with file sharing turned off and no ports forwarded? I know this would be a windows only situation ( I really hate windows). I know conficker was known to do this, but everytime I look this up, everyone acts like basically EVERY virus tries to do this, so it causes me to be paranoid.

---

