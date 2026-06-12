---
title: "Rosegarden window disappears"
date: 2011-10-21
forum: Ubuntu Studio
---

### Post by tobician on 2011-10-21
Hi there,

I ve been using ubuntu studio and rosegarden to record for the last two years and everything has always been working properly. 

Since today however, when I open Rosegarden something goes wrong, I cannot see the Rosegarden window although i am sure it s open and works correctly. Indeed, the rose icon appears in the launch bar and I can connect Rose to the midi keyboard and synth and start playing. I  Moreover, by hanging about with the mouse on the desktop i see that there something open as the name of the icons of rosegarden appear. With a clic on the  launch bar icon I can quit the program, after deciding to save or not. But... I just see my desktop

I already tried to remove and reinstall but nothing changes... 


anybody having an idea about what could be wrong?

---

### Post by jejeman on 2011-10-21
Run it from teminal, maybe it will give more info.

---

### Post by tobician on 2011-10-22
This is what i get by trying to load it from the terminal

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-feta-design20.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-design20.pfa" " to Qt font database 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-feta-nummer-design10.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-feta-nummer-design10.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-nummer-design10.pfa" " to Qt font database 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-parmesan-design20.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-parmesan-design20.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-parmesan-design20.pfa" " to Qt font database 

[generic]  RosegardenMainWindow::slotTestStartupTester 

SystemFont::loadSystemFont[Qt]: wanted family steinberg notation at size 12, got family DejaVu Sans (exactMatch 0)
[notation]  SystemFont::loadSystemFont[Qt]: Wrong family returned, failing 

Warning: Unable to load any of the fonts in "steinberg notation"
[notation]  SystemFont::loadSystemFont: name is  "georgia" , size  12 

[notation]  Found font files:  ("/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-design20.pfa", "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-nummer-design10.pfa", "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-parmesan-design20.pfa", ":/fonts/LilyPond-feta-design20.pfa", ":/fonts/LilyPond-feta-nummer-design10.pfa", ":/fonts/LilyPond-parmesan-design20.pfa") 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-design20.pfa" " to Qt font database 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-nummer-design10.pfa" " to Qt font database 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-parmesan-design20.pfa" " to Qt font database 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-feta-design20.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-feta-design20.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-design20.pfa" " to Qt font database 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-feta-nummer-design10.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-feta-nummer-design10.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-nummer-design10.pfa" " to Qt font database 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-parmesan-design20.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-parmesan-design20.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-parmesan-design20.pfa" " to Qt font database 

[notation]  SystemFont::loadSystemFont: name is  "times new roman" , size  12 

[notation]  Found font files:  ("/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-design20.pfa", "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-nummer-design10.pfa", "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-parmesan-design20.pfa", ":/fonts/LilyPond-feta-design20.pfa", ":/fonts/LilyPond-feta-nummer-design10.pfa", ":/fonts/LilyPond-parmesan-design20.pfa") 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-design20.pfa" " to Qt font database 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-nummer-design10.pfa" " to Qt font database 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-parmesan-design20.pfa" " to Qt font database 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-feta-design20.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-feta-design20.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-design20.pfa" " to Qt font database 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-feta-nummer-design10.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-feta-nummer-design10.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-nummer-design10.pfa" " to Qt font database 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-parmesan-design20.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-parmesan-design20.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-parmesan-design20.pfa" " to Qt font database 

[notation]  SystemFont::loadSystemFont: name is  "times" , size  12 

[notation]  Found font files:  ("/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-design20.pfa", "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-nummer-design10.pfa", "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-parmesan-design20.pfa", ":/fonts/LilyPond-feta-design20.pfa", ":/fonts/LilyPond-feta-nummer-design10.pfa", ":/fonts/LilyPond-parmesan-design20.pfa") 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-design20.pfa" " to Qt font database 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-nummer-design10.pfa" " to Qt font database 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-parmesan-design20.pfa" " to Qt font database 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-feta-design20.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-feta-design20.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-design20.pfa" " to Qt font database 

[generic]  RosegardenMainWindow::slotTestStartupTester 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-feta-nummer-design10.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-feta-nummer-design10.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-nummer-design10.pfa" " to Qt font database 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-parmesan-design20.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-parmesan-design20.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-parmesan-design20.pfa" " to Qt font database 

[notation]  SystemFont::loadSystemFont: name is  "DEFAULT" , size  12 

[generic]  ResourceFinder::getResourcePath: Looking up file " "xinfonia.xml" " for category " "/fonts/mappings" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  ResourceFinder::getResourcePath: Looking up file " "xinfonia.xml" " for category " "/fonts/mappings" " in prefix " "/usr/local/share/rosegarden" " 

[generic]  ResourceFinder::getResourcePath: Looking up file " "xinfonia.xml" " for category " "/fonts/mappings" " in prefix " "/usr/share/rosegarden" " 

[generic]  ResourceFinder::getResourcePath: Looking up file " "xinfonia.xml" " for category " "/fonts/mappings" " in prefix " ":" " 

[generic]  Found it! 

[notation]  SystemFont::loadSystemFont: name is  "xinfonia" , size  12 

[notation]  Found font files:  ("/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-design20.pfa", "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-nummer-design10.pfa", "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-parmesan-design20.pfa", ":/fonts/LilyPond-feta-design20.pfa", ":/fonts/LilyPond-feta-nummer-design10.pfa", ":/fonts/LilyPond-parmesan-design20.pfa") 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-design20.pfa" " to Qt font database 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-nummer-design10.pfa" " to Qt font database 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-parmesan-design20.pfa" " to Qt font database 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-feta-design20.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-feta-design20.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-design20.pfa" " to Qt font database 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-feta-nummer-design10.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-feta-nummer-design10.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-nummer-design10.pfa" " to Qt font database 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-parmesan-design20.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-parmesan-design20.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-parmesan-design20.pfa" " to Qt font database 

SystemFont::loadSystemFont[Qt]: wanted family xinfonia at size 12, got family DejaVu Sans (exactMatch 0)
[notation]  SystemFont::loadSystemFont[Qt]: Wrong family returned, failing 

Warning: Unable to load any of the fonts in "xinfonia"
[notation]  SystemFont::loadSystemFont: name is  "georgia" , size  12 

[notation]  Found font files:  ("/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-design20.pfa", "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-nummer-design10.pfa", "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-parmesan-design20.pfa", ":/fonts/LilyPond-feta-design20.pfa", ":/fonts/LilyPond-feta-nummer-design10.pfa", ":/fonts/LilyPond-parmesan-design20.pfa") 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-design20.pfa" " to Qt font database 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-nummer-design10.pfa" " to Qt font database 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-parmesan-design20.pfa" " to Qt font database 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-feta-design20.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-feta-design20.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-design20.pfa" " to Qt font database 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-feta-nummer-design10.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-feta-nummer-design10.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-nummer-design10.pfa" " to Qt font database 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-parmesan-design20.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-parmesan-design20.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-parmesan-design20.pfa" " to Qt font database 

[notation]  SystemFont::loadSystemFont: name is  "times new roman" , size  12 

[notation]  Found font files:  ("/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-design20.pfa", "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-nummer-design10.pfa", "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-parmesan-design20.pfa", ":/fonts/LilyPond-feta-design20.pfa", ":/fonts/LilyPond-feta-nummer-design10.pfa", ":/fonts/LilyPond-parmesan-design20.pfa") 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-design20.pfa" " to Qt font database 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-nummer-design10.pfa" " to Qt font database 

[generic]  RosegardenMainWindow::slotTestStartupTester 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-parmesan-design20.pfa" " to Qt font database 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-feta-design20.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-feta-design20.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-design20.pfa" " to Qt font database 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-feta-nummer-design10.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-feta-nummer-design10.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-nummer-design10.pfa" " to Qt font database 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-parmesan-design20.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-parmesan-design20.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-parmesan-design20.pfa" " to Qt font database 

[notation]  SystemFont::loadSystemFont: name is  "times" , size  12 

[notation]  Found font files:  ("/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-design20.pfa", "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-nummer-design10.pfa", "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-parmesan-design20.pfa", ":/fonts/LilyPond-feta-design20.pfa", ":/fonts/LilyPond-feta-nummer-design10.pfa", ":/fonts/LilyPond-parmesan-design20.pfa") 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-design20.pfa" " to Qt font database 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-nummer-design10.pfa" " to Qt font database 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-parmesan-design20.pfa" " to Qt font database 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-feta-design20.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-feta-design20.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-design20.pfa" " to Qt font database 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-feta-nummer-design10.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-feta-nummer-design10.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-feta-nummer-design10.pfa" " to Qt font database 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-parmesan-design20.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[generic]  ResourceFinder::getResourcePath: Looking up file " "LilyPond-parmesan-design20.pfa" " for category " "/fonts" " in prefix " "/home/tinoladino/.local/share/rosegarden" " 

[generic]  Found it! 

[notation]  Added font file " "/home/tinoladino/.local/share/rosegarden/fonts/LilyPond-parmesan-design20.pfa" " to Qt font database 

[notation]  SystemFont::loadSystemFont: name is  "DEFAULT" , size  12 

[generic]  RosegardenMainWindow::slotTestStartupTester 

:-k

---

### Post by tobician on 2011-10-24
well... decided to re install ubuntu studio 11.04 and everything works fine again..

---

