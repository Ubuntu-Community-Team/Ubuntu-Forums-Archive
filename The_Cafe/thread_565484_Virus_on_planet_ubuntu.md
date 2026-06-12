---
title: "Virus on planet ubuntu ?"
date: 2007-10-02
forum: The Cafe
---

### Post by chatainsim on 2007-10-02
Hi all,
i try to connect to [http://planet.ubuntulinux.org](http://planet.ubuntulinux.org)
and my antivirus avast say Warning there is a virus Worm ELF:SucKIT-rootkit on this website.
(i'm @ work that's why i'm under windows)
anybody have this warning ?
[[IMG]http://images6.pictiger.com/thumbs/4d/4b0ba6a651dd8d728e8eb939c288184d.th.png[/IMG]](http://server6.pictiger.com/img/689229/computers-and-electronic-gadgets/virus-ubuntu-.php)

---

### Post by Sunflower1970 on 2007-10-02
No, I don't think so...But there's a blog about a SucKIT-rootkit maybe it's picking up the wording...?

---

### Post by ssam on 2007-10-02
see [http://blog.knightlust.com/?p=18](http://blog.knightlust.com/?p=18)

---

### Post by M$LOL on 2007-10-02
I get a virus alert from that page.

---

### Post by swj on 2007-10-03
Confirmed.  I just tested from a windows xp laptop, running avast 4.7 home. 

ELF:SucKIT-rootkit

virus/worm

---

### Post by reyfer on 2007-10-03
There is no virus or rootkit on that page!!!! AVAST is picking the wording of the blog about the SuckIt rootkit, and it reports it as a virus. I'm sure if you copy and paste the blog entry here, and then try to check the page with AVAST on, it will report the same thing.

---

### Post by FuturePilot on 2007-10-03
How can an antivirus app read your webpages?:-s
That's like saying Geyes is watching you :o

---

### Post by reyfer on 2007-10-03
> **FuturePilot said:**
> How can an antivirus app read your webpages?:-s
That's like saying Geyes is watching you :o

Well, then explain to me how AVAST talks about a virus/rootkit on a page that only  reports about that said virus?(and I checked with Clamav, AVG, and on windows with Norton, McAfee, Kaspersky, and nothing came up)

---

### Post by FuturePilot on 2007-10-03
> **reyfer said:**
> Well, then explain to me how AVAST talks about a virus/rootkit on a page that only  reports about that said virus?(and I checked with Clamav, AVG, and on windows with Norton, McAfee, Kaspersky, and nothing came up)

Hm, that's odd. I've just never heard of antivirus programs being able to read webpages.

---

### Post by Samhain13 on 2007-10-03
> Well, then explain to me how AVAST talks about a virus/rootkit on a page that only reports about that said virus?

Could it have read the expression from the browser-cached file? But then again...

---

### Post by jouka on 2007-10-04
Real time scanning type of scanners work like this:

1. You get some file on your computer
2. You start opening it, program that should open it sends a request to open that file
3. In between is scanner engine which works as a 'gatekeeper' for file activities
4. It hijacks the file and scans it.
5. If the file has malicious code in it, request to open that file is denied and alert generated. If the file is clean, no action taken. File will get clear passage and scanner engine is sad. Job for nothing :(

Browsers do not display web pages at protocol level. First that page must be downloaded to browsers cache. Ever seen that 'GET' command? ;)

Shitty AV product I say.

---

### Post by skymera on 2007-10-04
so this isnt a virus?

if it is, can it affect ubuntu?

---

### Post by jouka on 2007-10-04
> **skymera said:**
> so this isnt a virus?

if it is, can it affect ubuntu?

No. You can only get 'virus' to your ubuntu system if you go and install one. Installing programs from repos is secure.

---

### Post by skymera on 2007-10-04
whats the chances of that?

---

### Post by 23meg on 2007-10-04
> **skymera said:**
> whats the chances of that?

Practically zero if you stick to the trusted sources.

---

### Post by skymera on 2007-10-04
well i have that Trevino list.
perghaps i should scrap that and use the list from the ubuntu source generator..

---

### Post by n3tfury on 2007-10-04
avast sucks apparently.  and reyfer, give me a break.  it's not scannign for verbage on websites.

---

### Post by handy on 2007-10-04
The info' in the following link is old, but still very valid, its great for new linux user's to get an understanding of the differences between linux & windows, with regards to security:

***_[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)_***

---

### Post by macogw on 2007-10-04
> **skymera said:**
> well i have that Trevino list.
perghaps i should scrap that and use the list from the ubuntu source generator..
The source generator isn't all necessarily secure repos.  It pretty much just lists all the Ubuntu repos it knows of.  The repos to definitely trust are the official ubuntu.com ones.  You're on your own for whether or not to trust 3rd party repos.  There are some, like Trevino's, that are widely trusted by Ubuntu users, and are probably just fine to use.  Random repos you find that you don't know where they're coming from are the ones to worry a bit about because if very few people are using them, they've likely not been looked into very well to see if the packages really are OK.  By adding a signing key from a repository, you are verifying that you trust the *person* who packaged it.  If your friend has a repo, and you know you can trust them, go ahead and use it.  If a stranger says "hey try my repo," maybe not.

---

