---
title: "Scanning with just a command line"
date: 2009-07-30
forum: Ubuntu Studio
---

### Post by sdenel on 2009-07-30
Hello everybody!
Well, xsane, it's great, but what if you want to scan a lot of documents?
It would be better to have just a shortcut and HOP, it scans and put the file into your desktop!

But to do that, you need to have a program like xscan where you can put parameters like output directory, format, resolution, as arguments.

And here is my question: which program can I use?

Thanks for your help!
Simon.

---

### Post by rylleman on 2009-07-31
XSane is a GUI for the scanner software Sane. There is also a CLI frontend called scanimage which should be what you're looking for. 

Run "man scanimage" in your terminal for a guide on how to use it. Run "scanimage -h" for all available options.

---

### Post by sdenel on 2009-07-31
Thank you rylleman, this is what I was looking for.
Here is an help to use this shell prompt program:
[http://www.cyberciti.biz/faq/linux-scan-image-commands/](http://www.cyberciti.biz/faq/linux-scan-image-commands/)
seeing: How do I scan an image from a shell prompt?

---

