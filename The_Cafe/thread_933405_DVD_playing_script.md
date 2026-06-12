---
title: "DVD playing script"
date: 2008-09-29
forum: The Cafe
---

### Post by bruce89 on 2008-09-29
I got bored of Totem not being able to play DVDs, so I wrote a script (barely executes one command) to do it. It requires GStreamer.

```
#!/bin/sh
# This plays a title from a DVD

# Parameters
TITLE=$1

# Check for input
if [ -z "$1" ]; then
	echo "Needs a title number" >&2
	exit 1
else
	gst-launch-0.10 dvdreadsrc title=$TITLE ! decodebin name=decode decode. ! queue ! audioconvert ! audioresample ! pulsesink decode. ! deinterlace ! xvimagesink force-aspect-ratio=true
fi
```

It needs one parameter, the title you want to play.
Of course, you can't do anything except just play it right through. (apart from pausing with suspend)

---

