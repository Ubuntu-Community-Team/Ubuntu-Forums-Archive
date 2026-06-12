---
title: "HUD not working in LibreOffice"
date: 2012-02-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by xedi on 2012-02-18
I updated the 12.04 Alpha and now have the HUD to play around with. However, it does not seem to be working in LibreOffice. HUD works fine with gedit, but in LibreOffice I only get information about other packages.

So e.g.: When I type new, instead of the new in LibreOffice the suggestion to create a new wireless network pops. When I type in Manual Break, nothing happens.

Before filing a bug, I wanted to ask whether I am making some mistake or whether LibreOffice is simply not supported yet.

Furthermore, I find it a bit annoying that if I hit the first letter of my search term too fast after hitting alt it is not registered. Where would be the appropriate way to give feedback concerning that be?

---

### Post by grahammechanical on 2012-02-18
It is not a bug. Unless you want to complain to Libreoffice about it.

what you are experiencing is the main issue with this Heads Up Display feature - it needs programs that cooperate with it. At present Libreoffice does not work with HUD. Or is it the other way around?

Do you not think that it is too much to expect everything to be working perfectly in a pre-release version? The Ubuntu developers have a lot to do over the next few weeks. And now they have to adjust other people's programs to work with HUD. It will take a while for all the programs on offer in even a default install (let alone in the Software Centre) to be integrated into the workings of HUD.

At the moment I am just pleased that a tap on the alt key will raise the HUD. when it first came out I found it very hard to make it appear.

The other day I stayed up in to the early morning running a test program on Unity that included the functioning of the HUD. There were 171 individual tests of Unity to be run. The report had to be in by 08:00 of that day. A lot is being done to make sure that things work as they should before release day.

Regards.

---

### Post by xedi on 2012-02-18
Thank you for your response.

I did not want to come across as expecting everything to work properly. Quite the contrary, I installed 12.04 on a second computer so I can help finding bugs and so on. And that was the purpose of this thread, I was not sure whether it is a missing feature, a general bug, a bug that only applies to me or whether I did some mistake.

---

### Post by EgoGratis on 2012-02-18
I might be wrong but i think applications that don't support "global menu" don't work with HUD. If i am wrong somebody can correct me but there is "global menu" support being developed for LibreOffice too is just not production ready yet!

---

### Post by daniel_w93 on 2012-04-06
You can enable the global menu for libre office (and with that, HUD functionality) by installing the package 'lo-menubar' (sudo apt-get install lo-menubar) it isn't included by default yet because of a few bugs.

---

### Post by Baldrick_NZ on 2012-04-06
> **daniel_w93 said:**
> you can enable the global menu for libre office (and with that, hud functionality) by installing the package 'lo-menubar' (sudo apt-get install lo-menubar) it isn't included by default yet because of a few bugs.

+1

---

### Post by ubuntu27 on 2012-04-06
If you finds a bug in LibreOffice, you can report it [here]("https://bugs.launchpad.net/ubuntu/+source/libreoffice") and [here]("https://www.libreoffice.org/get-help/bug/").

[How to Report Bugs in LibreOffice]("http://wiki.documentfoundation.org/BugReport")


If you find a bug in LibreOffice's **Global Menu** (a.k.a Menu Bar), then it should be reported [here]("https://bugs.launchpad.net/ubuntu/+source/lo-menubar").


Go Bug Hunters! :guitar:

---

### Post by syntr on 2012-04-08
The HUD still doesn't work for me in LO with the package lo-menubar installed, I don't think that the two are related...

---

### Post by keithpeter on 2012-04-08
> **syntr said:**
> The HUD still doesn't work for me in LO with the package lo-menubar installed, I don't think that the two are related...

What happens when you press the ALT key to bring HUD up?

I've installed lo-menubar on my netbook as I find the space saving useful.

I just loaded LibreOffice writer, and then with LibreOffice writer as the focussed window, I tapped Alt to bring up the HUD and typed 'format'. HUD showed the items in the 'Format' menu. I pressed Esc to clear the search results, then ESC to close the HUD so I could see the LibreOffice window.

Then I tapped the ALT key again and typed 'autocorrect' to see if HUD would find the autocorrect options dialogue. It did, so the HUD searching of the deeper menu items does work and lets people find functions they can't see.

I think HUD is neat: you have the text of the menus available in a central place because of the global app menu needing them. So then you add a search function.... brilliant whoever came up with that

---

### Post by ubuntu27 on 2012-04-08
> **syntr said:**
> The HUD still doesn't work for me in LO with the package lo-menubar installed, I don't think that the two are related...

What desktop environment and shell are you using?

Are you using Unity 3D, Unity 2D, or Gnome Classic? Or even perhaps Xfce, KDE...

---

### Post by syntr on 2012-04-09
> **ubuntu27 said:**
> What desktop environment and shell are you using?

Are you using Unity 3D, Unity 2D, or Gnome Classic? Or even perhaps Xfce, KDE...

Unity 3D.

---

### Post by keithpeter on 2012-04-09
> **syntr said:**
> Unity 3D.

Ok syntr

When you have libre office writer (say) loaded and as the active window, what happens when you tap the ALT key?

Assuming the HUD search box appears, what happens when you type (say) 'autocorrect' into the HUD search box?

---

### Post by Cenko on 2012-04-18
> You can enable the global menu for libre office (and with that, HUD functionality) by installing the package 'lo-menubar' (sudo apt-get install lo-menubar) it isn't included by default yet because of a few bugs.

I was editing something in Microsoft Office and couldn't find how to change cases easily, got angry and thought "If it had HUD like my ubuntu, I could just press alt and type 'case'!". Then out of curiosity I opened my ubuntu 12.04 pc and tested hud on libreoffice, and disappointed to see that it doesn't work. 

Then found out this thread and I'm happy to say that your suggestion works for me (at least for changing case).

Ubuntu 12.04, Unity2D

---

