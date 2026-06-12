---
title: "CUPS print Server"
date: 2012-03-28
forum: Server Platforms
---

### Post by markosjal on 2012-03-28
I have done some testing with easy printing from Android (and probably iThingies too) but here is the missing link. I refer to this as the missing link because I have done it on CUPS in OSX 10.5 but I can not see to get it to work in Ubuntu 10.10.

I can use any Mac OS X supported printer connected to Mac OSX and via printer sharing I then simply configure most any android print client to the Mac OS CUPS server as a Postscript printer. I have tested IPP and LPR on Mac OS cups server.  

The problem I have is that when I try to do this in Ubuntu I do not get LPR support. Also I have an issue with the Postscript not quite being reformatted correctly for the printer.

What do I need to support lpr server support in CUPS? I am trying an update to Ghostscript and we will see if that helps


Fuurthermore I would like to get the Android Printershare App to see the CUPS server from Ubuntu in the same way that it sees CUPS server from the Mac OSX CUPS server 



--------update

Updating Ghostscript did not help for printing from PrintBot with Postscrfipt driver to Ubuntu CUPS server.  I get two images of the test page per page one on the left and one on the right on the Samsung ML-1675  . Each image has white lines through all of it. However the results are excellent on thE Xerox Phaser 6125N with exactly the same configuration

---

