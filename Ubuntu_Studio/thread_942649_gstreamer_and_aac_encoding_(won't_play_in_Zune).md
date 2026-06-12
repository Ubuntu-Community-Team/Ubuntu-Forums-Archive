---
title: "gstreamer and aac encoding (won't play in Zune)"
date: 2008-10-09
forum: Ubuntu Studio
---

### Post by rosyatrandom on 2008-10-09
Hi people,

I'm running Ubuntu Hardy, and since I have a Zune am also dual-booting with Windows (current flavour Vista, just for the hell of it).

Now, Zune's should support aac/m4a files, but I produced a batch with Sound Juicer and the Zune software doesn't recognise the format.

Looking a little closer, the Zune wants m4a's that have been encoded using AAC-LC, and I'm guessing this isn't what gstreamer's been using. The file info indicates it's using Lavf1d.51.10.0... which seems to be the libavformat version.

So, my questions, assuming I have the right of this:

* Can gstreamer be updated to use a compatible codec?
* Can the files I've created be easily modified to be compatible?
* Can the Zune software (this is probably not the place but what the hell) be modified to accept these files as they stand?

---

### Post by eye208 on 2008-10-11
> **rosyatrandom said:**
> Looking a little closer, the Zune wants m4a's that have been encoded using AAC-LC, and I'm guessing this isn't what gstreamer's been using.
The gstreamer faac plugin uses the "Main" encoding profile by default. To make it use the "Low Complexity" (LC) profile instead, add "profile=2" to "faac" in the gstreamer pipeline string.

For more info about faac plugin properties, enter "gst-inspect faac" in a terminal window.

---

