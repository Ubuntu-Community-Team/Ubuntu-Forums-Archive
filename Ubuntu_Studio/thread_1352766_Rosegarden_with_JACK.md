---
title: "Rosegarden with JACK"
date: 2009-12-12
forum: Ubuntu Studio
---

### Post by kmac on 2009-12-12
I've been trying to read other people's testimonies first before becoming a poster myself, but I seem to be stuck. I may be missing something altogether, but please enlighten me.

I first run JACK as root, as that seems to be the only way to get it starting properly.

```
$ sudo qjackctl -s
```

Then I run rosegarden. Then I  run vkeybd to simulate my USB keyboard which I'll worry about later,

```
$ vkeybd&
```

When I go to the connect tab in JACK, I have no problem routing the output of vkeybd to rosegarden under the ALSA tab. However, under the AUDIO tab, I only have entries on either side labeled "system", none mentioning rosegarden. So essentially, I end up being able to record from vkeybd to rosegarden but I roegarden plays no sound. Any help would be appreciated. Let me know if you need kernel version or lspci. 

Thanks a bunch

--Kyle

---

### Post by rafalcieslak on 2009-12-13
JACK is one of the stranges pieces of software I ever met. You shouldn't need to run it as root... but if you did so, rosegarden must been run as root too, in order to connect these applications together. (I found it using trials/errors way, could someone wise explain me why it must be run as root?)

---

### Post by kmac on 2009-12-15
I tried signing in to both as root. Still same problem. Any ideas?

---

### Post by kmac on 2009-12-15
After some monkeying around, I got it so that I can patch my audio through, but only for a few seconds before the connection disappers. Any reason as to why this might happen? Here are the most recent messages in the log, though I'm not entirely familiar with them:

```
03:33:40.143 JACK connection change.
subgraph starting at qjackctl timed out (subgraph_wait_fd=23, status = 0, state = Running, pollret = 0 revents = 0x0)
03:33:52.541 JACK connection graph change.
**** alsa_pcm: xrun of at least 1.748 msecs
03:33:52.569 XRUN callback (7).
**** alsa_pcm: xrun of at least 1.660 msecs
03:34:20.141 XRUN callback (8).
```

---

### Post by kayosiii on 2009-12-15
You should not start jack as root...
The setup for jack from jack control is broken out of the box current and recent versions of Ubuntu.

Jack works considerably better if it can run at a higher priority than is normally allowed. In order to allow it to run this way you have to make some changes to Ubuntu's security policies to allow this. 

There are plenty of references in this forum on how to do this (It seems that I answer this question at least once a week).
This looks to be a fairly good answer
[http://ubuntuforums.org/showthread.php?t=806730&highlight=/etc/security/limits](http://ubuntuforums.org/showthread.php?t=806730&highlight=/etc/security/limits)

You can also disable real-time privileges for jack in jack control (qjackctl) look for the real-time option in settings.

---

### Post by TickOfAgnos on 2010-02-17
Rosegarden works just fine on my computer *without* the JACK server running (although it gives the error message), whereas *with* JACK the program is mute. Any ideas why? It seems Rosegarden connects to timidity-ports for producing sounds - could the problem lie in some kind of software conflict?

---

