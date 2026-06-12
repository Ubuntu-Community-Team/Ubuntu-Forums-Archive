---
title: "ANN: Pymazon 0.1beta released."
date: 2009-12-29
forum: The Cafe
---

### Post by sccolbert on 2009-12-29
I'm happy to announce the first beta release of Pymazon: a Python implemented alternative to the Amazon mp3 downloader. 

Pymazon was created specifically to alleviate the issues surrounding the Linux version of the Amazon mp3 downloader (though it should run just fine in Windows too). 

Pymazon can be used from the command line, or a gui interface if PyQt4 is installed. 

You can get Pymazon from the cheeseshop using pip (easy_install is not supported as it breaks the bin script):

$ pip install pymazon

You can read more about Pymazon (screenshots, installation, usage, source code) at [http://code.google.com/p/pymazon/](http://code.google.com/p/pymazon/)

Cheers!

Chris

---

### Post by marym on 2010-01-03
I am a true novice user of ubuntu so I am very wary of downloading stuff from sites I am not sure of - and my son just gives me so much earache when things go topsy turvey.

I have a netbook and a desktop.  Some time ago I downloaded the Amazon downloader onto the netbook and it works fine.

I cannot make the same downloader work on the desktop (running Karmic). Getting fed up of moving .amz files from one computer to another, so would like something that actually worked without putting my installation at risk.

There is little feedback on the forum about this Pymazon - has anyone actually used it?

---

### Post by isaacj87 on 2010-01-03
> **marym said:**
> I am a true novice user of ubuntu so I am very wary of downloading stuff from sites I am not sure of - and my son just gives me so much earache when things go topsy turvey.

I have a netbook and a desktop.  Some time ago I downloaded the Amazon downloader onto the netbook and it works fine.

I cannot make the same downloader work on the desktop (running Karmic). Getting fed up of moving .amz files from one computer to another, so would like something that actually worked without putting my installation at risk.

There is little feedback on the forum about this Pymazon - has anyone actually used it?

I've used Linux for a couple years now and I too am wary of projects that aren't well known. I took the liberty of peeking at the source code and while I haven't actually used the program, I didn't see anything suspicious (please take no offense, sccolbert). Unfortunately, I only have a basic understanding of python, but the beauty of opensource, anyone can pry it open and take a look inside. I look forward to trying this project out.

On a side note, I may be able to help you get the Amazon downloader to work on Karmic as I have it working on my installation.

---

### Post by oldos2er on 2010-01-03
Looks interesting. I've been using clamz for quite awhile, since Amazon's mp3 downloader doesn't work in 64-bit Ubuntu.

---

### Post by juancarlospaco on 2010-01-03
Nice name...!   :)

---

### Post by sccolbert on 2010-01-07
With regards to the skepticism of Pymazon's "intentions".

I completely 100% understand your hesitation with trying out unknown projects and I have no ill will against you for feeling that way. 

That said, I can assure you 100% that Pymazon is not malicious in any way. I have contributed to some other well-known projects in the Python-Scipy community (I wrote the OpenCV bindings for the scikits.image project for example [http://github.com/stefanv/scikits.image/tree/master/scikits/image/opencv/](http://github.com/stefanv/scikits.image/tree/master/scikits/image/opencv/) see the license file there) and am very active on the scipy, numpy, and enthought-dev mailing lists. These are things that can be easily verified via google. 

Also, it's possible to install Pymazon without using sudo if you are using Python >= 2.6 (since these versions support a user specific site-packages directory). Simply do "$ python setup.py install --user" or if using pip "$ pip install --install-option='--user' pymazon" 

And like other's have said, Pymazon is fully open source so you can see exactly what is going on. It's only ~600 lines of code. There have been over 200 downloads so far, and no negative feedback (barring bug reports :))

If you have any trouble or still have any other questions, post back or send me a pm.

Cheers!

Chris

---

