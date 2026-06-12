---
title: "PulseAudio 0.9.16-test5 uploaded to Karmic"
date: 2009-08-20
forum: Ubuntu Dev Link Forum
---

### Post by crimsun on 2009-08-20
Hi folks,

Subject says it all- PulseAudio 0.9.16-test5 has been uploaded to Karmic. Please see [https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-August/009227.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-August/009227.html) for more information.

Thanks.

---

### Post by rudenko_ruslan on 2009-08-20
Updated from "Ubuntu Audio Dev team PPA". Rebooted, and now my sound is enabled at startup (not muted). Great!

---

### Post by hugmenot on 2009-08-20
Daniel, am I the only one for whom paprefs is completely grayed out and insensitive?
Also, I cannot use tunnels anymore. They don&#8217;t even display in pavucontrol even though the zeroconf modules are loaded on both sides and show up in avahi-browse -ta.

---

### Post by hugmenot on 2009-08-20
Oh, and I think flat volume is mandatory. It makes PA use the analog amp a.k.a. master volume of the card,  which is a great thing.

---

### Post by crimsun on 2009-08-20
> **hugmenot said:**
> Daniel, am I the only one for whom paprefs is completely grayed out and insensitive?
Also, I cannot use tunnels anymore. They don’t even display in pavucontrol even though the zeroconf modules are loaded on both sides and show up in avahi-browse -ta.

No, but paprefs is deprecated in Karmic.

---

### Post by hugmenot on 2009-08-21
And the tunnel sinks (a.k.a. network audio)? I can handle doing without paprefs.

---

### Post by deflagmator on 2009-08-22
Sorry , can somebody tell me if we are going to be able to  use tunnels with karmic?(in the final release)

---

### Post by crimsun on 2009-08-25
> **hugmenot said:**
> And the tunnel sinks (a.k.a. network audio)? I can handle doing without paprefs.

A new paprefs has been uploaded and built; please try it.

---

### Post by crimsun on 2009-08-25
Please note that we are now running 0.9.16-test6 with git changesets from yesterday (i.e., slightly newer than 0.9.16-test6 proper).

---

### Post by hugmenot on 2009-08-25
Ok paprefs works in the sense that it isn&#8217;t grayed out anymore and I can toggle the options.

But they don&#8217;t have an effect w.r.t. tunneled sinks in PA&#8217;s own Volume Control applet. 

Could you please also pull »pavucontrol« from git and rebuild it in ~ubuntu-audio-dev PPA?

I know that pavucontrol is not in Main, etc, but for some cool advanced uses it is nice to have. Especially considering that the selling point of PA was being the »Compiz of Sound«

---

### Post by crimsun on 2009-08-25
> **hugmenot said:**
> Could you please also pull »pavucontrol« from git and rebuild it in ~ubuntu-audio-dev PPA?

pavucontrol is already sufficiently new in Karmic universe. Why do you want a rebuild in the PPA?

---

### Post by hugmenot on 2009-08-25
Because rebuilding from git worked for paprefs, so I assumed the same problem was there for pavucontrol. Maybe that was a naive conclusion.

Right now, I have Avahi-based broadcasting of sinks, I can see them in padevchooser but not in pavucontrol. I can export PULSE_SERVER and play over the network, just not using tunnels. Today I found [this FAQ]("http://pulseaudio.org/wiki/FAQ#WhydoInotseeremotesinksincontrolapplications") and it doesn&#8217;t give more clues than this.

It&#8217;s a regression in terms of functionality. This is why I keep bringing it up. Or rather, I wondered if I messed something up myself and asked here if others have this issue as well. But it seems to be a regression in fact.

---

### Post by crimsun on 2009-08-25
> **hugmenot said:**
> Because rebuilding from git worked for paprefs, so I assumed the same problem was there for pavucontrol. Maybe that was a naive conclusion.

Consulting apt-cache policy:

 *** 0.9.8+git20090701-0ubuntu2 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages

So, pavucontrol in Karmic already contains the latest commits.

---

