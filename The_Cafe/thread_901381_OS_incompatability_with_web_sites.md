---
title: "OS incompatability with web sites?"
date: 2008-08-26
forum: The Cafe
---

### Post by ARhere on 2008-08-26
Someone please educate my ignorance.

[This article on /.]("http://news.slashdot.org/news/08/08/25/229210.shtml") talks about how a web site will not play its video if you are not using an approved operating system and browser combo.

The web site supports Firefox, and the video plays well on Firefox under Windows, but not if you are running Firefox on Linux.

My question is, what the hell does the OS have to do with browser software decoding and playing streaming video?  What does the web server care what is running underneath the browser software?  Do I need to get my tin foil hat???

-AR

---

### Post by qstraza on 2008-08-26
it could be done on purpose with php:p

---

### Post by klange on 2008-08-26
> **qstraza said:**
> it could be done on purpose with php:p
It can only be done on purpose in situations like this. If it works in Firefox *it works in Firefox*.
This is also why we have the user agent switcher.

---

### Post by Joeb454 on 2008-08-26
Javascript can also check for the OS. The point, I don't know, but it can be checked :)

---

### Post by qstraza on 2008-08-26
Evil bastards ;)

---

### Post by xravexheavenx on 2008-08-26
Lol.  I smell AdWare!  :P

Only reason I can think of why they would run a JS on a page t only allow WinBlows users.  

My guess is there is a FireFox exploit for WinBlows users and they are taking advantage of it.

---

### Post by Yes on 2008-08-26
It needs Silverlight and the Move Network player, I don't believe there's a Linux client for either of them.  They just check the OS because they know there aren't clients for Linux.

---

### Post by ghostandmachine on 2008-08-26
I've actually been on an IT job search web site that includes those who are certified in Linux but the site refuses to run in Firefox under linux[LEFT][/LEFT]

---

### Post by y@w on 2008-08-26
You have to keep in mind that Firefox doesn't render some things natively. It has to use third party applications to play videos, etc.. If Mozilla would build all the tools into the browser, besides violating some copyright laws.. we'd all complain about how bloated it had become. At the end of the day, the OS is what handles displaying the video and playing the sounds.. The only valid reason I can see to not allow the page to load certain components is to just not show things that won't work in Linux. The last thing you want to do from a usability perspective is to just let it display but not do anything.

---

### Post by Orlsend on 2008-08-26
Yeah some sites Like Apple and the TOEFL test sites wont work or will keep asking you to switch to aanother OS to View the content

---

### Post by klange on 2008-08-26
> **Yes said:**
> It needs Silverlight and the Move Network player, I don't believe there's a Linux client for either of them.  They just check the OS because they know there aren't clients for Linux.

You're very much wrong about the first one (we have Moonlight, and despite the controversy, it is there and available and open-source), and I've never heard of the second.

---

### Post by Yes on 2008-08-26
> **WindowsSucks said:**
> You're very much wrong about the first one (we have Moonlight, and despite the controversy, it is there and available and open-source), and I've never heard of the second.

Oh, has Moonlight been released?  I thought it was still in development.  I Googled the second one and apparently they're supposed to be releasing a Linux client sometime in Q2 of this year (or has that passed already?).

---

### Post by Dragonbite on 2008-08-26
I would trust Moonlight before I trust Microsoft's Silverlight for Linux.  

Not out of any paranoia, but the fact Miguel and team has done a good job with Mono and they "get" Linux while Microsoft is not experienced.

---

### Post by clinux on 2008-08-26
> **Joeb454 said:**
> Javascript can also check for the OS. The point, I don't know, but it can be checked :)

```

<script type="text/javascript">
var info = navigator;
document.write("You are using:" + info.platform);
</script>

```

---

