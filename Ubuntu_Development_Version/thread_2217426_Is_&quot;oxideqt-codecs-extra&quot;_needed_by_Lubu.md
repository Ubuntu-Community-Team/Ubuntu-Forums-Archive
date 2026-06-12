---
title: "Is &quot;oxideqt-codecs-extra&quot; needed by Lubuntu 14.04?"
date: 2014-04-17
forum: Ubuntu Development Version
---

### Post by vasa1 on 2014-04-17
Part of the output of *apt-cache show oxideqt-codecs-extra* is
> Description-en: Web browser engine library for Qt (codecs)
 Oxide is a web browser engine library based on Google Chromium, [B]that makes
 it easy to embed web content in your Qt application[/B]
 .
 This package provides some media codecs needed for the HTML5 <audio> and
 <video> tags. Included are the Theora, Vorbis, Opus, VP8, VP9, MP3, AAC
 and H.264 codecs

Does that mean it's something for "developers" and not really necessary for "end-users" who use Firefox as their browser?

---

### Post by mc4man on 2014-04-17
I believe it's generally for webapps & webbrowser-app, why you have it on Lubuntu no idea (doesn't seem to be inc. on current image

---

### Post by vasa1 on 2014-04-17
> **mc4man said:**
> I believe it's generally for webapps & webbrowser-app, why you have it on Lubuntu no idea (doesn't seem to be inc. on current image
Thanks! I downloaded a "daily" the day before yesterday. Looks like there's been a clean-up if you don't see it now.
I've purged it for now and nothing's exploded so far.

---

### Post by frank18 on 2014-04-17
> **vasa1 said:**
> Part of the output of *apt-cache show oxideqt-codecs-extra* is

Does that mean it's something for "developers" and not really necessary for "end-users" who use Firefox as their browser?



Hi vasa1; i had a notification  when i installed Ubuntu restricted-extras  that i should remove (oxideqt-codecs) and i did remove 
oxideqt-codecs, do i need those installed and  if i installed them will i have conflict as it suggested by Ubuntu restricted extras installer?

---

### Post by vasa1 on 2014-04-17
> **frank18 said:**
> Hi vasa1; i had a notification  when i installed Ubuntu restricted-extras  that i should remove (oxideqt-codecs) and i did remove 
oxideqt-codecs, do i need those installed and  if i installed them will i have conflict as it suggested by Ubuntu restricted extras installer?
@Frank18, all this oxide stuff is new to me! All I know is that it concerns the browser Canonical is developing to work with Unity and this webapp business. Which is why I was puzzled to see it appear in Lubuntu (from a build a couple of days old).

As mc4man pointed out, it isn't present in the latest Lubuntu build he looked at.

I suggest you open a new thread about what you have seen and mention whether you're on Unity or Xubuntu or Lubuntu, etc.

---

