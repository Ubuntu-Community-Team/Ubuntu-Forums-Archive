---
title: "Opera removed from 9.04 repos?"
date: 2009-07-30
forum: The Cafe
---

### Post by magmon on 2009-07-30
I checked the add/remove for opera when firefox started acting up, and it seems to be gone. Is there a reason for it's removal? Is it incompatible or simply unpopular?

---

### Post by ghindo on 2009-07-30
I don't believe that Opera has ever been in the repositories.

---

### Post by magmon on 2009-07-30
Maybe my terminology is wrong then, but I know I could download it from the add/remove menu in 8.10.

---

### Post by Majorix on 2009-07-30
Opera has its own .deb repo, I installed Opera from there.

---

### Post by seteshf on 2009-07-30
Installing Opera from the standalone rpm/deb package will add their repository, it's how they implement their auto-upgrade on Linux.

---

### Post by dmizer on 2009-07-30
> **ghindo said:**
> I don't believe that Opera has ever been in the repositories.

It hasn't. Since Opera is not OSS it can't be built by Ubuntu packagers for Ubuntu.

---

### Post by Colonel Kilkenny on 2009-07-30
> **dmizer said:**
> It hasn't. Since Opera is not OSS it can't be built by Ubuntu packagers for Ubuntu.

Opera has been in Ubuntu 3rd party commercial (or whatever it was) repository.

---

### Post by seteshf on 2009-07-30
> **Colonel Kilkenny said:**
> Opera has been in Ubuntu 3rd party commercial (or whatever it was) repository.

Yeah, they never let you install it on x86-64 systems though which sucked because you had to override dpkg to get the standalone DEB to work.

That's what I never understood about Debian packaging. x86-64 is just a superset of x86, not some completely foreign architecture. RPM  doesn't _care_ if the user installs a x86 package, why exactly does Dpkg?

Thankfully Opera has an x86-64 native package now, and Ubuntu shouldn't really be packaging Opera anyway when Opera can do a better job managing their own repo.

---

### Post by kostkon on 2009-07-30
According to [the ubuntu documentation page for Opera]("https://help.ubuntu.com/community/OperaBrowser"), you need to add the following line to your software sources list:
```
deb http://deb.opera.com/opera/ stable non-free
```
and to add the key, give the following in a terminal:
```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
```

---

### Post by jamest09 on 2009-07-30
Never used Opera and never intend to

---

### Post by coldReactive on 2009-07-30
> **jamest09 said:**
> never intend to

Ever since I used it once, I removed it, and now this applies to me too.

---

### Post by Arup on 2009-07-30
Wish there was a way to remove Firefox, never worked for me in Windows or Ubuntu and I feel its unethical to bundle any browser, let the user decide. Opera's lawsuit against MS should be extended to Linux distros as well, those bundling brosers, free or non free. The fact that apt gets integrated in FF is another facet that really irks me.

---

### Post by Viva on 2009-07-30
> **Arup said:**
> Wish there was a way to remove Firefox, never worked for me in Windows or Ubuntu and I feel its unethical to bundle any browser, let the user decide. Opera's lawsuit against MS should be extended to Linux distros as well, those bundling brosers, free or non free. The fact that apt gets integrated in FF is another facet that really irks me.

Both windows and IE are products of microsoft and they have a monopoly in desktop market with windows. Ubuntu neither has a monopoly nor is Firefox a canonical product. Besides, Microsoft's biggest crime was to blackmail OEMs into installing IE and forcing them not to include an alternate browser.

---

### Post by dmizer on 2009-07-30
Let's stay on topic.

Just as a reminder, the topic is why Opera is no longer a part of the repos, not "is $browser good/bad/evil/appropriate" etc.

---

### Post by bodhi.zazen on 2009-07-30
> **dmizer said:**
> let's stay on topic.

Just as a reminder, the topic is why opera is no longer a part of the repos, not "is $browser good/bad/evil/appropriate" etc.

+1

---

### Post by Arup on 2009-07-30
The sad part is Opera is not even included in medibuntu repos when rmpfusion includes it in Fedora, so do many other distros, hardcore and others, Medibuntu has all other so called non free stuff so why leave Opera out and give it step motherly treatment. I just have a strong suspicion that team Firefox has some real stranglehold on Canonical regarding this matter.

---

### Post by 23meg on 2009-07-30
[QUOTE=Arup]Medibuntu has all other so called non free stuff so why leave Opera out and give it step motherly treatment. I just have a strong suspicion that team Firefox has some real stranglehold on Canonical regarding this matter.[/QUOTE]

Canonical has nothing to do with Medibuntu.

---

### Post by Cenotaph on 2009-07-30
Opera used to be in the canonical's partner repository but it got outdated fast and it wasn't available there already in 8.10. In fact, i think the reference to the package was removed from previous versions of ubuntu as well.

---

### Post by earrame on 2009-07-30
Good topic. When I switched from Mepis to Ubuntu last Summer I retrieved the .deb from the Opera site to install. I noticed over the months that it never appeared on the updates. I've been thinking I need to get around to checking my sources and see if I can add Opera.

---

### Post by magmon on 2009-07-30
I do see why it isn't there anymore though. The interface is extremely outdated in the linux version. It even changes your mouse, and the whole thing reminds me of windows 2000. Im extremely disappointed to say the least. (Sudo apt-get remove opera)

---

### Post by doorknob60 on 2009-07-30
> **magmon said:**
> I do see why it isn't there anymore though. The interface is extremely outdated in the linux version. It even changes your mouse, and the whole thing reminds me of windows 2000. Im extremely disappointed to say the least. (Sudo apt-get remove opera)

10.0 beta **finally** has a native qt interface that looks decent and uses your theme. And a 64 bit native build for it too, finally.

---

### Post by magmon on 2009-07-30
> **doorknob60 said:**
> 10.0 beta **finally** has a native qt interface that looks decent and uses your theme. And a 64 bit native build for it too, finally.

That is excellent news. I may try it again after 10.0 is released as a stable build.

---

