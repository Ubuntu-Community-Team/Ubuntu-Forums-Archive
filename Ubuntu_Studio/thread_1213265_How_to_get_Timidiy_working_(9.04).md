---
title: "How to get Timidiy working? (9.04)"
date: 2009-07-14
forum: Ubuntu Studio
---

### Post by Harrkev on 2009-07-14
I have Ubuntu 9.04 installed on my Acer Aspire One (yes, a netbook), and on a old custom-built Athon 64.  I also have Jack working on both (finally), but I am having problem getting Timidity to work (same problem on both).

First, I get Jack running.  I can see that Timidity has a MIDI-in interface.  It is installed, and appears to be there.

I can use virtual keyboard to control my external synth.  I can use my external synth to control Qsynth (fluidsynth).  I can use the virtual keyboard to control Qsynth.

I cannot get any real-time noise at all out of Timidity.

From the command line, I can feed .MID files to Timidity, and it works.

Any ideas?

---

### Post by raboofje on 2009-07-14
> **Harrkev said:**
> I also have Jack working on both (finally), but I am having problem getting Timidity to work (same problem on both).

First, I get Jack running.  I can see that Timidity has a MIDI-in interface.  It is installed, and appears to be there.

I cannot get any real-time noise at all out of Timidity.

From the command line, I can feed .MID files to Timidity, and it works

Does timidity have jack support these days? I seem to remember it was an oss/alsa-only app, so it'd need complete control over the soundcard to make noise. But that might've been a while ago :).

---

