---
title: "How to create custom thumbnailers"
date: 2014-01-30
forum: Ubuntu Application Development
---

### Post by dannyboytward on 2014-01-30
I've been trying to create thumbnailers for custom file types for a while now, and I can't quite get things working.

There was a nice tutorial here: [https://developer.gnome.org/integration-guide/stable/thumbnailer.html.en](https://developer.gnome.org/integration-guide/stable/thumbnailer.html.en) , which explains nicely how to create icons for your application, create custom file types to open with your application, and build a thumbnailer for these file types.  The thumbnailer section (using gconftool) doesn't seem to work though.  Instead, a thumbnailer entry needs to be placed in /usr/share/thumbnailers/ , like this one

[Thumbnailer Entry]
TryExec=gnome-thumbnail-font
Exec=gnome-thumbnail-font %u %o
MimeType=application/x-font-ttf;application/x-font-pcf;application/x-font-type1;
application/x-font-otf;

So now comes my questions.  

1. Is it possible to install thumbnailer entries on a per user basis (just putting them in ~/.local/share/thumbnailers doesn't seem to work)?  I'd like to do this at work where I don't have root access.

2. How can you create custom thumbnailers in KDE?  I can't seem to find any info about this.

Thanks for your help!

---

