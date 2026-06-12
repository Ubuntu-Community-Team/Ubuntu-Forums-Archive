---
title: "Site blocked by google"
date: 2009-12-13
forum: The Cafe
---

### Post by BandD on 2009-12-13
Anybody come across this before?

trying going to this site:
[URL="http://www.autooneofsantacruz.com/"]
http://www.autooneofsantacruz.com[/URL]

and googling autoone of santa cruz.

You get slightly different warning pages.  Interesting nonetheless.

Same messages in firefox and epiphany (mozilla based).  Also same on Safari.  Interestingly enough, it didn't come up when trying to view the page with my father-in-law's AOL browser.

Is it a google DNS thing or what?

It's kinda scary how much control over the internet they seem to have.

---

### Post by Techsnap on 2009-12-13
I don't have GoogleDNS, but that does happen if I go on it from the search engine link, otherwise the URL does work. Just contact them and ask for it to be removed, they done it quite quick when I told them about a site once which wasn't meant to be blocked.

---

### Post by pwnst*r on 2009-12-13
> **BandD said:**
> 

It's kinda scary how much control over the internet they seem to have.

control over the internet?  you're using THEIR search engine.  the only reason that warning page comes up is because you're using their search engine link.  i use googleDNS and i can open it just fine in FF using the standard link and also in IE and Konquerer.  

don't sensationalize something that's not there. kthx.

---

### Post by Marvin666 on 2009-12-13
Is there a way to remove that "attack site" system from firefox? I don't trust google, and don't really see a warning from them as having any power.

---

### Post by LinuxFanBoi on 2009-12-13
> **Marvin666 said:**
> Is there a way to remove that "attack site" system from firefox? I don't trust google, and don't really see a warning from them as having any power.

If there are shenanigans going on within a website I would rather Firefox err on the side of caution.

---

### Post by pwnst*r on 2009-12-13
in FF : tools>options>security> uncheck "block reported attack sites"

good luck with that if you're not using *nix.

---

### Post by Marvin666 on 2009-12-13
At the moment no, but even if it had a virus, I wouldn't go on google's word of it.

---

### Post by jpeddicord on 2009-12-13
Not sure if anyone saw this:

[http://safebrowsing.clients.google.com/safebrowsing/diagnostic?site=http://www.autooneofsantacruz.com/&client=chromium&hl=en-US](http://safebrowsing.clients.google.com/safebrowsing/diagnostic?site=http://www.autooneofsantacruz.com/&client=chromium&hl=en-US)

---

### Post by pwnst*r on 2009-12-13
> **jpeddicord said:**
> Not sure if anyone saw this:

[http://safebrowsing.clients.google.com/safebrowsing/diagnostic?site=http://www.autooneofsantacruz.com/&client=chromium&hl=en-US](http://safebrowsing.clients.google.com/safebrowsing/diagnostic?site=http://www.autooneofsantacruz.com/&client=chromium&hl=en-US)

nice info!  

lol @ naysayers.

---

### Post by NCLI on 2009-12-13
> **Marvin666 said:**
> At the moment no, but even if it had a virus, I wouldn't go on google's word of it.

Why?

---

### Post by CharlesA on 2009-12-13
> **NCLI said:**
> Why?

Cuz it's (onoez!!) google, apparently.

Hurray for sites infected with malware.

---

### Post by LinuxFanBoi on 2009-12-13
> **Marvin666 said:**
> At the moment no, but even if it had a virus, I wouldn't go on google's word of it.

As I said err on the side of caution.  There is enough information available to convince me that the site is not safe.

---

### Post by lukjad on 2009-12-13
> **BandD said:**
> Anybody come across this before?

trying going to this site:
[URL="http://www.autooneofsantacruz.com/"]
http://www.autooneofsantacruz.com[/URL]

and googling autoone of santa cruz.

You get slightly different warning pages.  Interesting nonetheless.

Same messages in firefox and epiphany (mozilla based).  Also same on Safari.  Interestingly enough, it didn't come up when trying to view the page with my father-in-law's AOL browser.

Is it a google DNS thing or what?

It's kinda scary how much control over the internet they seem to have.
So, a spam/malware site has a warning page put in front of it on google. So?

---

### Post by BandD on 2009-12-13
It happens to me when I try to access the url directly. NOT through google's search engine.

---

### Post by jpeddicord on 2009-12-13
> **BandD said:**
> It happens to me when I try to access the url directly. NOT through google's search engine.

Google search, Firefox, and Chromium all use the same malware database, so that makes sense.

---

### Post by Crunchy the Headcrab on 2009-12-13
> **jpeddicord said:**
> Not sure if anyone saw this:

[http://safebrowsing.clients.google.com/safebrowsing/diagnostic?site=http://www.autooneofsantacruz.com/&client=chromium&hl=en-US](http://safebrowsing.clients.google.com/safebrowsing/diagnostic?site=http://www.autooneofsantacruz.com/&client=chromium&hl=en-US)
Interesting.  So third party malware?  Malware is malware.

---

### Post by t0p on 2009-12-13
When I try that url, I get this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=139740&stc=1&d=1260742392[/IMG]
There's a link called "Ignore this warning" down to the bottom right corner.  Click on that and I'm through to the evil site.

---

### Post by The Real Dave on 2009-12-13
Chromium gives a nice big malware warning. Firefox does the same. Usually like to trust their opinion, and click out :)

---

### Post by sdowney717 on 2009-12-13
i wonder how they know its malware. did someone complain or is the site scanned and that is how they know.

---

### Post by jpeddicord on 2009-12-13
> **sdowney717 said:**
> i wonder how they know its malware. did someone complain or is the site scanned and that is how they know.

They check the Safe Browsing database. The [link I posted]("http://safebrowsing.clients.google.com/safebrowsing/diagnostic?site=http://www.autooneofsantacruz.com/&client=chromium&hl=en-US") had information on how they scanned that site; seems to be mostly automated.

[http://code.google.com/apis/safebrowsing/](http://code.google.com/apis/safebrowsing/) has a little bit of developer info.

---

### Post by Yes on 2009-12-13
[http://www.stopbadware.org/](http://www.stopbadware.org/) seems to be the organization which finds "attack" websites and blacklists them.  Any program which subscribes to their list will give you a warning before they let you go on to a site listed as an attack site.

Google has nothing to do with deciding what site is bad, and when you try going to the website directly in a browser like Firefox it's Firefox that blocks you, not Google.

---

### Post by sdowney717 on 2009-12-13
chrome also blocks you
big red message banner
says get me out of here

---

### Post by hobo14 on 2009-12-13
> **Marvin666 said:**
> Is there a way to remove that "attack site" system from firefox? I don't trust google, and don't really see a warning from them as having any power.

The warning you see is not from Google.

---

