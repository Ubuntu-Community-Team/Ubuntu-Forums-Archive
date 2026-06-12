---
title: "Google's relationship to Chromium?"
date: 2011-06-27
forum: The Cafe
---

### Post by bonfire89 on 2011-06-27
Hello there,

What exactly is Google's relationship to Chromium? I know Chrome bases itself on Chromium but does Google own Chromium? Does Google benefit from me using Chromium? Is Chromium made with typical FLOSS philosophies free of things that spy on you etc.?


Thanks!

---

### Post by BCingyou on 2011-06-27
As far as I know, Chromium is a completely open-source project.  Google takes Chromium and adds a few non-free elements, most notably bundling Flash Player into Chrome.  

Chromium does **not** have the usage tracking of Chrome, which is why me and I'm sure a lot of other linux users have adopted Chromium as our default browser.  

I'm not really clear if there is any financial relationship between Chrome and Chromium, can anyone clear that up?  E.g. does google fund the development of chromium at all?

---

### Post by sanderd17 on 2011-06-27
This is what I have read:

Google devs and some volunteers develop Chromium
The chromium project releases a full FLOSS version of the browser they made
But google also takes the source and builds it's own Google chrome (with some features added like "call home" things).

---

### Post by sanderd17 on 2011-06-27
Oh, and google benefits from you because you create a more open web. As you know, having as much information accessible on the web is the main target for google. Using a fast browser like Chrome (or other browsers that become faster due to competition) helps with that process.

If people would still use ie6, the cloud would not be so developed and html5 would have had no chance.

---

### Post by juancarlospaco on 2011-06-27
> **BCingyou said:**
> 
Chromium does **not** have the usage tracking of Chrome

Not necessarily always a bad thing..., 
random example: Ubuntu, Debian, etc got usage tracking (.deb packages),

Internet is a public thing, everything that is not encrypted can be, and is tracked,
you only need to know how, and you can track someones else data.

---

### Post by Paqman on 2011-06-27
> **BCingyou said:**
> 
Chromium does **not** have the usage tracking of Chrome

Even Chrome doesn't have usage tracking if you don't want it to. It's opt-in.

---

### Post by BCingyou on 2011-06-27
I'm not really making a value judgment, just pointing out the differences.  

I believe Chrome also reads PDFs "out of the box" while chromium requires some configuration?  Can't remember the exact details.  

Honestly I use chromium mostly because it's the fastest and because they've fixed the Flash bugs that seemed to plague in version 12.  Also it has a nice unity integration which not all browsers have (yet).

---

### Post by Nyromith on 2011-06-27
Chromium is the source code of Chrome, a project that is founded and owned by Google. Google works on most of the source code of Chrome with Chromium's community, and offers its own branded compilation as Chrome (which is synchronized with Chromium releases). Chrome is a closed-source browser that is based on the open-source Chrome, with some additions from Google, such as a flash player, pdf reader, and possibly a spyware.

---

### Post by Mr. Picklesworth on 2011-06-27
The relationship of Chromium to Chrome is pretty simple: Chrome is Chromium with some proprietary bits, and with an official release schedule. (The beta/stable Chromium PPAs follow along with what Chrome does, as far as I know). As for Google, they own and run the Chromium project. Everything that goes into Chrome, except stuff that must be proprietary like Flash and the PDF plugin, is developed in open in the Chromium project. Google effectively makes Chromium; all of its core developers are Google employees. From what I have seen on their bug tracker, they do a really good job working with outside contributors (unlike a certain other high profile open source project of theirs), which also tells me they don't implement features in the dark. They have a good number of patches coming from outside Google :)

---

