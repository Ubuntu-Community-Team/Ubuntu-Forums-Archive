---
title: "index.html --&gt; .avi"
date: 2008-05-29
forum: Ubuntu Studio
---

### Post by xigen on 2008-05-29
Hello,

I got married !!! .. it's awesome. 

I could use some help, please.  

The file:
[http://www.tylersipe.com/source/multimedia/wilsonwedding/index.html](http://www.tylersipe.com/source/multimedia/wilsonwedding/index.html)
... looks terrific in a browser, however my parents would like to see it on their dvd player.

How do I convert the above into .avi or some format which can be burned to a dvd?

* if the sourcefile is required:
[www.mediafire.com/?3s1x6bevnkk](www.mediafire.com/?3s1x6bevnkk)

Check out the video/side show - it is terrific.

All the best,

Mario
:popcorn:

---

### Post by Stochastic on 2008-05-29
Well you'll either want to do a screen capture of that webpage using gtk-recordmydesktop, or you can convert the source file swf into an mpg (this is a bit more techy to get done, but results in much higher quality results)
I found this: > Hi all,

To get a conversion happening with sound i needed to:

add the -V (video) switch in edit.py
$ edit.py -o out.mpg -V input.swf

and upgrade to latest flash player
$ sudo aptitude update && sudo aptitude install flashplugin-nonfree
(with edgy backports repo enabled)

also note that edit.py to mpeg requires PyMedia ([http://pymedia.org/](http://pymedia.org/))
whereas SWF -> FLV -> AVI doesn't.

So much nicer than the nasty (and expensive) programs under windows
that just do a screen capture of a playing swf....

So here's all the links in one spot:
vnc2swf (edit.py): [http://www.unixuser.org/~euske/vnc2swf/](http://www.unixuser.org/~euske/vnc2swf/)
PyMedia (Python MPEG): [http://pymedia.org/](http://pymedia.org/)
Flash9 Install Howto: [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)
Seveas Packages (for Lame3.97):
[http://ubuntu-tutorials.com/2006/10/21/seveas-ubuntu-packages/](http://ubuntu-tutorials.com/2006/10/21/seveas-ubuntu-packages/)

cheers,
wulf solter 
near the bottom of this page: [http://help.lockergnome.com/linux/convert-SWF-AVI-format-ftopict396093.html](http://help.lockergnome.com/linux/convert-SWF-AVI-format-ftopict396093.html) but I have never needed to do this myself, so I can't truly vouch for or give any troubleshooting advice beyond this.

---

### Post by Creative2 on 2008-05-29
i have opened with opera then i went to cache and i have found your photos :) but i think with recordmydesktop it will be easier

---

