---
title: "video converter server"
date: 2009-08-18
forum: Server Platforms
---

### Post by Willn21 on 2009-08-18
How can I convert videos on an Ubuntu server.  I want to be able to go in through putty and type in a command to start the conversion. 

Example:
I have an mp4 on the server and I want to convert it to wmv.

---

### Post by hessiess on 2009-08-18
> **Willn21 said:**
> How can I convert videos on an Ubuntu server.  I want to be able to go in through putty and type in a command to start the conversion. 

Example:
I have an mp4 on the server and I want to convert it to wmv.

ffmpeg.

---

### Post by Willn21 on 2009-08-18
> **hessiess said:**
> ffmpeg.

Is that the best converter?  Is the output quality identical to the original.  can i activate it with a php script?

---

### Post by hessiess on 2009-08-18
> **Willn21 said:**
> Is that the best converter?  Is the output quality identical to the original.  can i activate it with a php script?

As far as I know, yes, a lot of the `play anything' media players use ffmpeg under the hood.

Encoding between lossy formats(most video formats) will always degrade the quality, there is no way around this, you can use a higher bitrate to reduce the quality loss (ffmpeg -b and -ab flags).

Yes, its a CLI app, call it with exec() or shell_exec()

---

### Post by Willn21 on 2009-08-18
Ok thanks.  Keep checking on this thread I might have another question.  Good luck with dyslexia

---

