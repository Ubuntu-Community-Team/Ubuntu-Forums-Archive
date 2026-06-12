---
title: "Firefox sometimes uses 95% of cpu on my Starling"
date: 2010-12-14
forum: System76 Support
---

### Post by tc101 on 2010-12-14
Sometimes when typing into firefox, the keyboard input freezes up for a second or two.  Actually it just happened as I typed this.  I opened system monitor to watch and see exactly what is happening.   10-16% of cpu is being used by the system monitor, and all the frest is firefox-bin.  At times it goes all the way up to 100%.  What is happening?

---

### Post by jpv on 2010-12-15
1. Are you leaving any tabs containing Flash content open?
2. How often do you restart Firefox?
3. What plugins are you using?

It's probably Flash, which is awful, awful, awful, and even if you don't think you have any tabs with it, lots of site use it unnecessarily.  Flash will kill you dead, use No-Script, or Flashblock or something.

Firefox and/or Firefox plugins are still full of memory leaks, especially when left open for weeks or months (as I do).  FF needs to be restarted every once in a while (welcome back to Windows) or it goes crazy.  That usually has more to do with RAM than CPU use, but sometimes...

---

### Post by tc101 on 2010-12-25
> Flash will kill you dead, use No-Script, or Flashblock or something.

Which is better, or should I use both?  Do I lose anything by using these?

---

### Post by tc101 on 2010-12-25
Well I just got an answer to my last question at this site

[http://kb.mozillazine.org/Problematic_extensions](http://kb.mozillazine.org/Problematic_extensions)

It says 

NoScript blocks JavaScript, which is required by FlashBlock 	Do not use both FlashBlock and NoScript together (NoScript includes Flash-blocking functionality) 

So I guess the best on to use is NoScript.

---

### Post by jpv on 2011-01-03
Sorry, I should have been more clear.  Use NoScript to add *ton*s of security at a cost of many sites not working as expected.  Use FlashBlock just to block Flash.

I use NoScript because I understand what it's doing and why it breaks a *lot* of sites, but I leave it off my wife & kid's machines.  It's really appalling how many sites are a) very poorly written, b) very hostile to privacy & security, c) use Flash inappropriately/unnecessarily, d) all of the above.

---

### Post by Flyers2391 on 2011-01-05
> **jpv said:**
> Sorry, I should have been more clear.  Use NoScript to add *ton*s of security at a cost of many sites not working as expected.  Use FlashBlock just to block Flash.

I use NoScript because I understand what it's doing and why it breaks a *lot* of sites, but I leave it off my wife & kid's machines.  It's really appalling how many sites are a) very poorly written, b) very hostile to privacy & security, c) use Flash inappropriately/unnecessarily, d) all of the above.

Yeah, NoScript has really given me insight into some web pages out there ... it is pretty scary to see a dozen web sites or so load javascript on a single web page.  You are exactly right, as long as you are aware of NoScript, it's great.  I have to turn it off sometimes at work when browsing test machines and when I go back to web browsing without turning it back on, it's like I'm on a different Internet.

---

### Post by gamerchick02 on 2011-01-05
I don't know if you want to use a different browser, but I recommend Chromium.  I've found it uses fewer resources than Firefox.

Amy

---

### Post by rdelfin on 2011-01-06
I've always criticized Apple (S.Jobs) for not supporting Flash for their smaller i-Products, but there is truth and validity in their reasoning for not wanting Flash since it can (and does) bring a system to its knees, and in that sense, their claim is valid.

---

### Post by tlroche on 2011-01-07
> **gamerchick02 said:**
> if you want to use a different browser, [...] I've found [Chromium] uses fewer resources than Firefox.

Gotta second that, except I use Chrome, and I'm specifically discussing FF3 (dunno about FF4). I prefer FF's interface (esp with Tab Mix Plus) and extensions, but I'm also a tab slob. Most of the time my desktop is a couple of emacs and a lotta browser windows containing many tabs. On my panp5 with browser == FF3, performance tanks. With browser == google-chrome, no problems.

---

