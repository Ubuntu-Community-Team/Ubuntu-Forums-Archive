---
title: "HTML 5 &lt;video&gt; buffer size"
date: 2009-12-16
forum: Server Platforms
---

### Post by pi.boy.travis on 2009-12-16
Hi!  I have been experimenting with the html 5 video spec, and it seems that on larger videos the autobuffer stops at about 50% until the play button is pressed.  Buffering only resumes when the video "catches up."  Is there a way to control the buffer size, like the bufferSize parameter used in Cortado?  

Thanks!

---

### Post by Skidbladniir on 2009-12-16
Try digging through [http://w3.org/](http://w3.org/) documentation.

---

### Post by Skidbladniir on 2009-12-16
Errwoops!

Try digging through the [http://whatwg.org/](http://whatwg.org/) documentation.  X_X

---

### Post by pi.boy.travis on 2009-12-16
> The autobuffer  attribute is a boolean attribute. Its presence hints to the user agent that the author believes that the media element will likely be used, even though the element does not have an autoplay  attribute. (The attribute has no effect if used in conjunction with the autoplay attribute, though including both is not an error.) This attribute may be ignored altogether. The attribute must be ignored if the autoplay attribute is present.

The autobuffer IDL attribute must reflect the content attribute of the same name.

media . buffered

    Returns a TimeRanges object that represents the ranges of the media resource that the user agent has buffered.

The buffered attribute must return a new static normalized TimeRanges object that represents the ranges of the media resource, if any, that the user agent has buffered, at the time the attribute is evaluated. Users agents must accurately determine the ranges available, even for media streams where this can only be determined by tedious inspection.

I think the media.buffered tag is what I am looking for, but I can't find a sample implementation. . .  Any ideas?

---

### Post by Skidbladniir on 2009-12-16
If whatwg hasn't implemented it, it would be a browser only tag, which would de-validate your HTML and cause issues.  You could try to create a flash version, but that's the only other (apparent) way to do this.

---

### Post by pi.boy.travis on 2009-12-16
Ah well, guess I'll have to stick with Cordato for now. . .

---

