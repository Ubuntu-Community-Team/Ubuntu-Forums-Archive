---
title: "CJK text input candidate list not showing"
date: 2013-10-02
forum: Ubuntu Development Version
---

### Post by Jeffrey04 on 2013-10-02
I have recently upgraded from 13.04 to 13.10 development branch via update-manager. While most of the things run well, but apparently the text-input system is changed in this coming release. It actually worked quite well at first, but I just screwed up the system and decided to start with a new user account, then the input system went broken. Before this I used iBus to input chinese (ibus-pinyin), however in 13.10, after entering the pinyin the candidates failed to show up.

I tried running ibus-setup but apparently that wouldn't work anymore. Just out of curiousity, has Ubuntu changed the input method framework or something? Because there seem to be no way at the moment to change the settings besides the (new?) "Region & Language" applet (there's nothing much to change anyway). I even tried playing with the settings in ibus-setup utility but doesn't seem to have any effect. And is the Language support applet being deprecated?

---

### Post by tora201 on 2013-10-02
same problem here - actually got it going last night somebody, but can't replicate though...

---

### Post by grahammechanical on 2013-10-02
Have you tried going to Language Support? That has a label that says: Keyboard Input Support. Read the mouse-over text that appears when the mouse is held over the drop down menu which has as options Default, Ibus, None,

Regards.

---

### Post by Jeffrey04 on 2013-10-02
played with it, doesn't seem to work :/

looks like if i can't get this working properly i would have to log a bug report :/

---

### Post by ping-wu on 2013-10-02
I also had a lot of problems with ibus in 13.10.  For Chinese language users, my advice is to use UbuntuKylin instead, which is a flavor of Ubuntu developed specifically for this purpose.

It seems that you have already installed Ubuntu 13.10. You can "switch" to UbuntuKylin simply by installing the following package:

apt-get install ubuntukylin-default-settings

Prior to that, you may want to remove ibus, at least to save some harddrive space.

---

### Post by Jeffrey04 on 2013-10-02
not too interested in switching to kylin :/
i only need to input chinese characters occasionally though, guess I can live with just google chrome input tools for now

---

### Post by ping-wu on 2013-10-03
> **Jeffrey04 said:**
> not too interested in switching to kylin :/
i only need to input chinese characters occasionally though, guess I can live with just google chrome input tools for now

At the present time, it is not so much as "switching" to UbuntuKylin, but simply installing a package.  Personally, like you, all I need from Ubuntu is a tool to input Chinese characters--only if life can be so simple.  Before its total collapse in 13.10, IBus also has other problems, such as it doesn't work with Dash, one of the mainstays of the next generation Ubuntu.  Stability, or more specifically the lack thereof, is also one of its major problems.

Short of installing the UbuntyKylin package, you may want to explore the fcitx input method, which, for me, was the main reason for "switching" to Kylin.

---

### Post by Jeffrey04 on 2013-10-05
not sure, apparently the "Region & Language" panel is dropped after an upgrade earlier today, and the chinese input works properly again (miraculously)...
it works for dash too

P/S: tried ibus-setup again, and it still has no effect to the apparently new input framework/stack/whatever it is called

---

### Post by ping-wu on 2013-10-05
Actually I am OK with ibus in 12.04LTS (& upto 13.04).  Based on my past experience, I believe the problems that I experienced in 13.10 will be solved before the official release--if no so already.

The main reason I am thinking about ditching ibus (even in 12.04 LTS), is the sogou-pinyin (&#25628;&#29399;&#25340;&#38899;) input method.  It is far superior to any (simplified) Chinese pinyin method I have ever used.  At the present time, sogou-pinyin only works with fcitx, but not with ibus.

---

### Post by Jeffrey04 on 2013-10-08
> **ping-wu said:**
> Actually I am OK with ibus in 12.04LTS (& upto 13.04).  Based on my past experience, I believe the problems that I experienced in 13.10 will be solved before the official release--if no so already.

The main reason I am thinking about ditching ibus (even in 12.04 LTS), is the sogou-pinyin (&#25628;&#29399;&#25340;&#38899;) input method.  It is far superior to any (simplified) Chinese pinyin method I have ever used.  At the present time, sogou-pinyin only works with fcitx, but not with ibus.

the candidate box is now showing, however I can't access the preferences of the input method. I don't care what input method it is as long as it is pinyin-based, and i can change the final output to trad chinese lololololol

---

### Post by ping-wu on 2013-10-08
Exactly my sentiment.  I don't really give it a da*n about what input method I use as long as I can type in Chinese character (both simplified and traditional), and it is PINYIN-based.  For all I'm concerned, it can be totally generic.  The key issue is that it must work, and must be consistently working.

However, in real life, the more popular the input method, the more developers will be attracted to its maintenance, and it will have a less chance of having devastating regression.

In our machines, we typically have both ibus and fcitx installed.  To add fcitx-sogoupinyin to your system, enter the following commands:

sudo add-apt-repository ppa:fcitx-team/nightly

sudo apt-get install fcitx-sogoupinyin

Then go to the language support to select fcitx as your input method.

You can also install other input engines (e.g., google pinyin, etc).  I also like Google pinyin a lot.  However, with ibus, I can't change Google pinyin's preference.  I understand your frustrations!

---

### Post by Jeffrey04 on 2013-10-11
just found workaround to the preference problem

13.10 is still using ibus indeed. The problem with that is that the ibus-setup utility is not quite compatible to the updated ibus stack. Therefore, certain settings won't work. For instance adding a new input method (but a new IM can be added through the Text Entry applet in Settings application).

Therefore, to access the preference setup for a specific input method, just add the input method via the utility anyway. Then just change the settings for the particular input method as desired. (you may want to remove the input method from list after changing the settings)

Then in terminal, execute "ibus restart", and the new settings should be applied now

---

### Post by gmarcotte on 2014-03-10
I could not get ibus to work. I installed , SCIM anthy and use the settings | language support  select input method "Scim anthy" then find the Scim anthy input method configuration tool ( on my system I installed nome-session-fallback (because unity sucks) so its on the menu "system tools | preferences | SCIM input method").  after loging out and back in again the trigger function was working. the little anthy screen pops up when active, space bar works for selecting kanji, F7 convert the hirokana to katakana. its all good.

the EN or Ja  icons (top right) --> text entry setting seems to only change a keyboard layout (remapping the keys) for example the + key gets mapped to ~ when Ja is active. There also a Japanese Kana layout that gives you the old style Japanese keyboard (not useful unless you have stickers for the keys or have the layout etched into your brain). the Ubuntu 12.10 everything still works, 13.10 they managed to break ibus totally.

---

