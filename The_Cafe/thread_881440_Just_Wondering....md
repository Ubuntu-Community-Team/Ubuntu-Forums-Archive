---
title: "Just Wondering..."
date: 2008-08-06
forum: The Cafe
---

### Post by dreamscaper on 2008-08-06
Why is there no alsaconf in ubuntu? It is such a useful utility that I cannot understand why the developers would go through all that trouble to take it out. I ended up going through hours of troubleshooting that ate a very large portion of my time over the past couple days. I ended up having to compile alsa-utils from source and find all the pre-requisites on my own. No one from the actual Ubuntu forums could figure out my problem. It took Debian users telling me to run alsaconf over and over and me telling them "I don't have it, there is no alsaconf in ubuntu" to finally make me throw my hands up and decide to reinstall alsa-utils from source. It was quite a pain. 

If I did not like the interface and all my other hardware hadn't worked so beautifully out of the box I would've just moved to another distro. I love Ubuntu, but I really think the powers that be ought to consider putting alsaconf back in. It would save some newbies a whole lot of time and energy.

---

### Post by FuturePilot on 2008-08-06
I remember hearing something about this before. I think this is it
[https://bugs.launchpad.net/alsa-utils/+bug/29597]("https://bugs.launchpad.net/alsa-utils/+bug/29597")
Specifically this
[https://bugs.launchpad.net/alsa-utils/+bug/29597/comments/3]("https://bugs.launchpad.net/alsa-utils/+bug/29597/comments/3")

---

### Post by dreamscaper on 2008-08-06
> **FuturePilot said:**
> I remember hearing something about this before. I think this is it
[https://bugs.launchpad.net/alsa-utils/+bug/29597]("https://bugs.launchpad.net/alsa-utils/+bug/29597")
Specifically this
[https://bugs.launchpad.net/alsa-utils/+bug/29597/comments/3]("https://bugs.launchpad.net/alsa-utils/+bug/29597/comments/3")

That makes some sense but the only problem I have with that is that it assumes that your sound card will run well out of the box with no bugs. If it is a pain on the developing side, then fine leave it out. But why not make a package that will install it for you in case you need it instead of making it incredibly difficult to use for those who need it? Let me tell you I tried EVERYTHING to get the card to work, and alsaconf was the only thing that got it done. My other option would have been compiling my own driver...

---

