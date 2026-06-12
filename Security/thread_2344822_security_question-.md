---
title: "security question-"
date: 2016-11-28
forum: Security
---

### Post by Amelia_Hayner on 2016-11-28
I just got a notice from Panda security that we needed to update our security. I cancelled it. Was that the right thing to do? I am understanding that Ubuntu is generally free from virus/bugs?
also, my husband loves to look at MSN and 2x lately, when he has clicked on a story, not the main page- the computer has been taken over by this loud beeping, and says your computers hard drive will be permanently deleted if you don't call some  number within 5 min. and give them your password.
we just shut the computer down, and went back later, and it was gone. is there anything we should do about this?
thank you.

---

### Post by slickymaster on 2016-11-28
*Thread moved to **Security**.*

---

### Post by Frogs Hair on 2016-11-28
There are Firefox add-ons that will block this kind of malicious popup . Ghostery and NoScript are well known  and there are others as well. Though malware/viruses that target Windows won't execute on Linux they can be passed to Windows machines. Web browser exploits are often cross platform and can cause different types of problems. See the security link in my signature.

---

### Post by Amelia_Hayner on 2016-11-29
thank you, will do so.

---

### Post by SeijiSensei on 2016-11-29
I recommend Ghostery.  Last I tried Noscript it needed too much manual tuning.  

Some sites will require turning Ghostery off, or editing its blocklist, to see their content, especially if they have proprietary video players.  MSNBC is one example.

---

### Post by &amp;KyT$0P# on 2016-11-29
> **SeijiSensei said:**
> I recommend Ghostery.  Last I tried Noscript it needed too much manual tuning.  
Let's not conflate privacy and security here.  Ghostery is for privacy, NoScript is for security.  Two totally different things.

This OP wants security and blocking of popups.  Therefore, I would recommend to use NoScript and uBlock Origin.

If the manual tuning of NoScript becomes annoying, there is [sort of a way around it]("https://forums.informaction.com/viewtopic.php?f=7&t=22243#p84726").

---

### Post by SeijiSensei on 2016-11-30
I use uBlock Origin and Ghostery.  I never see unwanted popups.

---

### Post by &amp;KyT$0P# on 2016-11-30
> **SeijiSensei said:**
> I use uBlock Origin and Ghostery.  I never see unwanted popups.
Yes, because you use uBlock Origin. :) That's why I mentioned it.

Isn't Ghostery redundant with uBlock Origin?

---

### Post by SeijiSensei on 2016-11-30
> **halogen2 said:**
> Yes, because you use uBlock Origin. :) That's why I mentioned it.

Isn't Ghostery redundant with uBlock Origin?

It doesn't seem to be.  I get different lists of blocked objects from the two add-ons.  Ghostery seems better at identifying tracking cookies and similar kinds of audience measurement.

---

### Post by &amp;KyT$0P# on 2016-11-30
> **SeijiSensei said:**
> Ghostery seems better at identifying tracking cookies 
Ah, I wasn't aware that Ghostery did more than filtering requests by URL.  Thanks.

---

### Post by KenUBF on 2017-04-09
>  the computer has been taken over by this loud beeping, and says your computers hard drive will be permanently deleted if you don't call some  number within 5 min. and give them your password.
we just shut the computer down, and went back later, and it was gone. is there anything we should do about this?
thank you.

Amilia, I agree with the other posters that uBlockOrigin will help to stop this, though be aware that it may not stop all of them. NoScript can also help stop some pop ups that uBlockOrigin misses. 

This is a very common kind of scam where groups put up fake security notices/pop ups to scare novice computer users into calling their tech support. Once you call them they ask if they can remotely connect to your computer to "diagnose" and fix the "problem," charging you hundreds of dollars in support fees for extended "support." You can read more about tech support scams here: [https://en.wikipedia.org/wiki/Technical_support_scam](https://en.wikipedia.org/wiki/Technical_support_scam)

You did the right thing. So far as I know these alerts are mere webpages that do no harm to your computer. It's just theatrics to scare you into calling them. Just closing out the page will make it go away.

---

### Post by TheFu on 2017-04-11
Something not mentioned so far is using a different browser + userid for different activities.
When I'm blindly surfing, I use dillo. It is small, lite, fast and simply doesn't support many of the nasty things out on the internet.  It isn't secure, since it doesn't validate HTTPS certs, which may or may not be important.  Nothing will replace a human brain.

For sites like this one, firefox with all the anti-javascript/privacy addons listed above is used. If a specific page doesn't work and I really want to see it, I'll use chromium-browser inside a **firejail** container with --private mode so nothing is written to the disk to view only that page without any blocking. No need for the "private browsing mode."

For banking and brokerage online, I'm a little lazy and just use a virtual machine that boots a tiny Linux OS and runs chromium-browser. It doesn't do much more. Really, I should completely reboot into a liveCD on a physical machine, not just a VM.  Why Chromium?  U2F support and I won't have a google browser on my systems. Privacy means more than that to me.  Other browsers aren't supported correctly with u2f yet. Sure firefox has an addon, but many sites only check for a chrome/chromium browser in the user-agent to decide if u2f will be used or not.

Plus, any emergency popup for security would get me thinking whether I need to wipe my system and start over.  If I'm not certain, I would do that.  Versioned backups are a great thing and my #1 security tool. Knowing I can restore a backup from last night or yesterday or last month, if needed, in about 45 min is really nice. Having 60 days of versioned backups isn't THAT hard. I sleep very well.

---

