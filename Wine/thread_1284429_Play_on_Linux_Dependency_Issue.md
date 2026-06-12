---
title: "Play on Linux Dependency Issue"
date: 2009-10-06
forum: Wine
---

### Post by ngrieb on 2009-10-06
I am trying to install Play On Linux using Intrepid (8.10), but I am having an odd dependency issue. POL needs python-wxgt2.8, which does show up in the repos and in synaptic, but when I mark for install it says I need python < 2.5, and says something about a dependency on python2.5.2-1ubuntu1, which does not show up in synaptic. 

How do I get this package?

 I have python-wxgt2.4 as well as 2.6 installed (does the above python <2.5 simply mean less than 2.5 like I assumed?...then it should have worked...:confused:)

---

### Post by ErikEhlert on 2009-10-06
if you have 2.6 installed won't it just upgrade over 2.4? I think when it looks for your version of python it automatically just finds 2.6, regardless if there's a lower version availible.

Well, the quick fix is to uninstall 2.6, but thats no fun, unless your really desperate.

---

### Post by ngrieb on 2009-10-06
Damn...well that means Phatch has to go :(, which sucks since I do a lot of art and design...
And I just tried it and it still did not work...still complains...same thing. Maybe if I reinstall 2.4 too???

python-wxgtk2.8:
  Depends: python (<2.5) but 2.5.2-1ubuntu1 is to be installed

---

### Post by ngrieb on 2009-10-07
Ok, so it appears that everything and it's mother depends on python 2.5-2ubuntu1 including banshee, blender, compiz-fusion, ...everything!!! Who the hell would make a program that depends on < 2.5 then? Argggg ...any solutions...please? Is there any way to clean up broken packages?

---

