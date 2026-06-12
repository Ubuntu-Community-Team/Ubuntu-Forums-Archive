---
title: "Firefox 27?"
date: 2014-02-09
forum: Ubuntu, Linux and OS Chat
---

### Post by monkeybrain20122 on 2014-02-09
Firefox 27 has been released for 5 days. It was updated in Fedora several days ago (usually it is not upated as fast) But it is still not updated in Ubuntu (not even in proposed updates) What is the deal?

---

### Post by waynefoutz2 on 2014-02-09
Well. I'm glad I'm not alone. My girlfriend's Windows 7 machine got the update 4 days ago. I'm still waiting.....

---

### Post by vasa1 on 2014-02-09
> **monkeybrain20122 said:**
> Firefox 27 has been released for 5 days. It was updated in Fedora several days ago (usually it is not upated as fast) But it is still not updated in Ubuntu (not even in proposed updates) What is the deal?
Purely speculative but it's possible that some Canonical-specific hacks are not playing ball with the new version and so some more time is needed? That shouldn't really be the case because the Mozilla Team is tracking precursor versions pretty closely and should have known at least when Fx 27 was in beta (= virtually a feature freeze).

The other time I remember a *Canonical*cified Firefox took a while was when Mozilla told the team that there was going to be a "chemspill" fix and so there was no point in releasing immediately.

Another reason could just be human ;) The Mozilla team isn't that big and maybe someone is indisposed (or unavoidably detained)? 

Anyway, I don't use Canonical Firefox. I use Firefox beta and Aurora straight from source.

(I don't know what policy Fedora follows in terms of trying to "integrate" software. Maybe that's why they're quicker?)

---

### Post by monkeybrain20122 on 2014-02-09
> **vasa1 said:**
> 

(I don't know what policy Fedora follows in terms of trying to "integrate" software. Maybe that's why they're quicker?)

Usually it is slower than Ubuntu for Firefox. That's why I am curious. I think they do their special build as well, for example, in Fedora 19 FF gstreamer option was missing from about:config and they said it was because the Fedora version was compiled without gstreamer support (in Ubuntu the option existed even though before FF25/26 you needed to enable it manually)

---

### Post by vasa1 on 2014-02-09
> **monkeybrain20122 said:**
> Usually it is slower than Ubuntu for Firefox. That's why I am curious. I think they do their special build as well, for example, in Fedora 19 FF gstreamer option was missing from about:config and they said it was because the Fedora version was compiled without gstreamer support (in Ubuntu the option existed even though before FF25/26 you needed to enable it manually)
Okay! I tried poking around in Launchpad to get clues but found nothing. Maybe looking in all the wrong places.

Some devs mention things on their blogs or in "tweets" or whatever.

---

### Post by vasa1 on 2014-02-10
Chris Coulson seems to be travelling. Maybe that has something to do with the delay.

---

### Post by hoopia on 2014-02-10
If you don't want to wait, you can get it from the PPA directly (just add it via apt-get):
 [http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu](http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu)

Then do a update && dist-upgrade and it should update to 27.

---

### Post by vasa1 on 2014-02-10
> **rushi4687 said:**
> If you don't want to wait, you can get it from the PPA directly (just add it via apt-get):
 [http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu](http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu)
...
That changes a user from the "stable" channel to the "beta" channel.

---

### Post by monkeybrain20122 on 2014-02-10
Just got the update. I thought some new UI has landed on FF27, but it still looks the same as before. Do I need to change some preferences??

---

### Post by mbott on 2014-02-10
I don't think you will see much change at all:  [http://www.ghacks.net/2014/02/04/firefox-27-find-new/]("http://www.ghacks.net/2014/02/04/firefox-27-find-new/")

-- 
Mike

---

### Post by vasa1 on 2014-02-10
> **monkeybrain20122 said:**
> Just got the update. I thought some new UI has landed on FF27, but it still looks the same as before. Do I need to change some preferences??
If you mean the *Australis* effect, that would be the current Aurora channel (= Fx29). I'm using both Fx28 and Fx29 (with different profiles).

---

### Post by monkeybrain20122 on 2014-02-10
> **vasa1 said:**
> If you mean the *Australis* effect, that would be the current Aurora channel (= Fx29). I'm using both Fx28 and Fx29 (with different profiles).

I see. I am just curious, but I can wait. :)

---

