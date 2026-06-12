---
title: "OpenOffice.org and Inkscape on a Server Setup for Web apps?"
date: 2006-12-07
forum: Server Platforms
---

### Post by OneSeventeen on 2006-12-07
I have installed Ubuntu 6.06 LTS Server using the LAMP option from the boot menu, and I would like to create a web application that takes advantage of the command-line features of Inkscape and OpenOffice.org

(Primarily I want to be able to have Inkscape render SVG's and print them to files so I can then convert them to PDF using ps2pdf, and the same for OpenOffice.org.)

Is there any way of doing this without installing a GUI?

---

### Post by OneSeventeen on 2006-12-07
Okay, reading up on it, it appears to be possible only through using an X server on another machine or something like that, which I am not comfortable with.

It looks like I'll be installing X :(

I'm shocked that with all of the push towards ODF they haven't made a command-line conversion tool from ODF to PDF, or even easy-to-use programming API's for us newbie script kiddies.

---

### Post by technodigifreak on 2006-12-07
> **OneSeventeen said:**
> Okay, reading up on it, it appears to be possible only through using an X server on another machine or something like that, which I am not comfortable with.

It looks like I'll be installing X :(

I'm shocked that with all of the push towards ODF they haven't made a command-line conversion tool from ODF to PDF, or even easy-to-use programming API's for us newbie script kiddies.

Haven't tried it, but I don't see a reason why printing to a CUPS-PDF printer wouldn't work?  Should be just like printing to any other printer from the application standpoint...

Dunno, just a thought.

---

### Post by fnjordy on 2006-12-08
SVG2PDF?

[http://www.freshports.org/graphics/svg2pdf](http://www.freshports.org/graphics/svg2pdf)

OOo can run on the command line too, various article on google:

[http://www.xml.com/pub/a/2006/01/11/from-microsoft-to-openoffice.html](http://www.xml.com/pub/a/2006/01/11/from-microsoft-to-openoffice.html)
[http://www.oooforum.org/forum/viewtopic.phtml?t=46347](http://www.oooforum.org/forum/viewtopic.phtml?t=46347)

You don't have to run a real X11 server anyway, just like Java has needed an X11 server for a very long time you can redirect the display to [xvfb](http://en.wikipedia.org/wiki/Xvfb)

---

### Post by mjwok on 2007-01-16
Hi,

I am developing an application in which I would also like to use capacity of Openoffice - in my case to generate and convert reports dynamically. 

I have found you can execute OpenOffice using these command line options "-headless" or "-invisible". There is also a "-server" option however I need to find some documentation on how to best configure this. 

The headless and server options (as far as I can tell) do not have a UI, reducing the applications memory footprint.  However with invisible you can open elements through code you submit - I don't know if this is the same for headless (I will have to test). 

Have you had any luck? 

Michael

---

