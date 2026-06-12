---
title: "Ubuntu 42 Screenshot CLI?"
date: 2023-04-08
forum: Ubuntu Application Development
---

### Post by j630-io on 2023-04-08
edit: Ubuntu 22.04.  Gnome Screenshot 42 is presumably what this is that runs?  What is the background process?

How can I launch screenshot exactly like this but from command line?  In the finder when I type "screenshot" I get two results.  Screenshot (gnome-screenshot) and "Take a Screenshot" which does what I want.

How can I launch "Take a Screenshot" from the command line?  I basically want it to start exactly like this with no extra clicks.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292059&stc=1[/IMG]

before it is suggested: gnome-screenshot --interactive does not open up the tool in this way

Thanks

---

### Post by TheFu on 2023-04-08
I'd look at **import -geometry [geometry]** - that's a tool in the ImageMagick suite. It can resize/rotate the captured image too.

---

### Post by j630-io on 2023-04-08
Hey thanks trying it out.  It does not do what I want out of the gate but maybe with some tweaks.  

Was thinking it should be easy to emulate.  Using XDO to send the PrtScr key in background did not work either.

---

