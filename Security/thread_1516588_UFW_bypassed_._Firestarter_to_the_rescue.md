---
title: "UFW bypassed . Firestarter to the rescue"
date: 2010-06-23
forum: Security
---

### Post by TheBrainWave on 2010-06-23
Hi there. I've been using UFW and FS on my lucid box with no problem.FW load first then I start FS.Recently Firefox (on blank page) was connecting to a certain IP address on start up. Was able to replicate the situation many times. FS was able to let me know the situation with just a click while ufw was just blindsided and bypassed by some offending software.Finally with FS's help I was able to quickly discover this intrusion and make some correction using about:config and delete the offending files from my system after a quick search.Problem solved.:p .Don't count Firestarter out.):P.It saved me a lot of pain.
Sorry for the long post.I had to share this.:KS

---

### Post by MechaMechanism on 2010-06-23
You do know that UFW and Firestarter are merely front-ends to IPtables. If UFW was bypassed then Firestarter was also bypassed.  Firestarter is an obsolete piece of software and has been for quite some time.  Frankly your post makes very little sense and I had trouble digesting the meaning.  I am curious about the change you made to Firefox.

---

### Post by TheBrainWave on 2010-06-24
I repeat Firestarter let me know with a click what was happening to my system.If it wasn't for that piece of software I wouldn't be able to quickly solve that problem.
I am not using as a firewall.

---

### Post by Rubi1200 on 2010-06-24
From the security sticky by bodhi.zazen:

> A source of confusion sometimes occurs when users feel the need to be running firestarter/Guarddog for their firewall to be active. **This is untrue !** Keep in mind that these applications are not firewalls, but rather configuration tools for ip tables. These applications should be run *only to configure your firewall*. Once configured, IP tables (the actual firewall) is active (at boot) *without having to run firestarter/guarddog*._ firestarter will monitor traffic, but it runs as root and there are better monitoring programs, so configure you firewall, shut down firestarter/grauddog, and let IP tables do the rest_ (my underlining)
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by yeleek on 2010-06-24
> **Rubi1200 said:**
> From the security sticky by bodhi.zazen:

(my underlining)
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Hear Hear.  I'm gonna get this tatoo'd on my head soon, just so people stop asking the same question.

---

### Post by Rubi1200 on 2010-06-24
Ouch! Wouldn't that hurt?

:-)

---

### Post by yeleek on 2010-06-24
Well yes I suppose it would ;-)  But perhaps worth it :)

---

### Post by cariboo on 2010-06-24
Just an aside, if someone doesn't step up to the plate and do something about firestarter, it won't be usable in maverick, due to csd (client side decoration) being used.

So firestarter questions may be moot once Maverick Meerkat is released.

---

### Post by OpSecShellshock on 2010-06-24
> **cariboo907 said:**
> Just an aside, if someone doesn't step up to the plate and do something about firestarter, it won't be usable in maverick, due to csd (client side decoration) being used.

So firestarter questions may be moot once Maverick Meerkat is released.

Not sure that would be such a bad thing.

---

### Post by kevdog on 2010-06-24
There are definitely problems with FS as it runs as root -- and its old -- and not maintained -- but the very fact a similar type GUI hasn't been developed in several years is pitiful.  GUFW -- nice try.  But I digress.

---

### Post by gjw0 on 2010-07-05
GUFW would be "better", if it had some of Firestarter's features(e.g., Events, active connections).

---

### Post by bodhi.zazen on 2010-07-05
> **gjw0 said:**
> GUFW would be "better", if it had some of Firestarter's features(e.g., Events, active connections).

Linux is modular. Use wireshark to monitor network traffic.

---

### Post by -humanaut- on 2010-07-05
Firestarter is deprecated I'd stick with UFW I just use it from the command line but you can grab the GUI if you need to.

---

