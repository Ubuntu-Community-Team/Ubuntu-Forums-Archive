---
title: "AMZGet, download music from Amazon"
date: 2009-03-03
forum: Ubuntu Dev Link Forum
---

### Post by MrWizard on 2009-03-03
Hi everybody.  I'm pretty new to Python - I've tinkered around with it and used it for a couple of little tiny projects.  Anyway, I thought I'd share my latest tinkering and hopefully get a little feedback.

You may be familiar with clamz, an alternative downloader for music purchased from Amazon.com.  My project was intended to pretty much be a Python clone of this application.  The primary reason I wanted to do this was portability.  Since it is written in Python, it can be moved from computer to computer without having to worry about recompiling due to dependencies or the host architecture.  It should hopefully be easier for inexperienced users to use, for similar reasons.

I would like to know how portable this code is - for example, would this run, unmodified, without issue in a Windows or other *nix environment?  I'm not sure about some of the console stuff, particularly with the download meter.  Also, please let me know if you find any bugs or potential problems.

Currently the program is hard-coded to debug mode.  This means that it will do all the work processing and parsing the AMZ file that you get from Amazon, but when it comes time to download the tracks, it will just download a 10 MB test file each time, instead.  I have successfully downloaded music that I purchased from Amazon with this, so you can change this in the default settings section.

Feel free to do with this what you will, but I would of course appreciate feedback and suggestions.  As I said, I'm new to Python and would love to learn from some more experienced coders.

[amzget.py]("http://dl.getdropbox.com/u/106811/amzget.py")

Edit:  Oh, I know squat about DES encryption, so I took that code from pyDes (which is in the public domain).  I plan to clean it up a bit, as there is probably some code that is not needed for the purposes of this program.

---

### Post by CFBauer on 2009-05-12
Just posting to say thanks! I'm not a programmer, so I can't offer anything in the way of actual help. It is clear though that a good alternative to Amazon's downloader would be worthwhile.

---

