---
title: "Beryl question"
date: 2007-02-18
forum: Ubuntu Customization Guide
---

### Post by roadman555 on 2007-02-18
Is there a way to reset beryl back to the default settings without having to reinstall it?

---

### Post by Waappu on 2007-02-18
Hi

Type in terminal```
mv ~/.beryl ~/beryl-old
```and restart beryl.
If you want restore your old settings you can find those in ~/beryl-old folder

---

### Post by roadman555 on 2007-02-18
I did as instructed and it says no such file or director,any other thoughts??

---

### Post by booe on 2007-03-04
Try these commands:

> 
cd ~
ls -a


Do you see a folder called ".beryl" ??

Otherwise, if you're using an old version of beryl/compiz, you will find the settings by typing "gconf-editor" as a command. A new GUI window pops up where you can manually change settings for Beryl/Gnome/etc.

---

### Post by FuturePilot on 2007-03-05
Can't you just open Beryl Manager and in the bottom left hand corner there's a thing that says something like restore defaults?

---

### Post by macpointman on 2007-03-30
I lost my Cube function after messing around with the settings in various parts of Beryl.  There are A LOT of them and sometimes it is hard to remember which one you changed.  Anyhow the command that Waappu posted got mine working and back to normal.

> **Waappu said:**
> Hi

Type in terminal```
mv ~/.beryl ~/beryl-old
```and restart beryl.
If you want restore your old settings you can find those in ~/beryl-old folder

Thanks Waappu.

I have been tinkering around with Linux for a couple of years now.  Just decided on Ubuntu and made the switch Deleted Windows completely from my hard drive and dove right in.  It seems to be the best supported distro out there.  Thats not to say that there aren't better distros out there.  But Beryl is just one of the very many reasons that Linux Owns Windows.

Thanks to all those who know A whole lot more about Linux and Ubuntu for sharing their knowledge with the rest of Us.

MacPointMan

---

### Post by wingnuts on 2007-04-10
Im a 3 day newbie to linux, and im extremely happy that im not the only one thats pushed too many buttons in ubuntu beryl settings.  ill try the above command to reset beryl to default tonight and see if it works for me.. Theres too many changes that can be made,  you start off thinking this is cool,, this is cooler ,, this is urm not cool, Dam what did I press. I find it awesome that ppl are happy to answer questions for newies, thanks

---

### Post by Geekkit on 2007-04-14
> **wingnuts said:**
> Im a 3 day newbie to linux, and im extremely happy that im not the only one thats pushed too many buttons in ubuntu beryl settings.  ill try the above command to reset beryl to default tonight and see if it works for me.. Theres too many changes that can be made,  you start off thinking this is cool,, this is cooler ,, this is urm not cool, Dam what did I press. I find it awesome that ppl are happy to answer questions for newies, thanks

:D 

Hahah ... this^ I swear I did the exact same thing here.

"Oooo. Cool .... Wow, trippy! ... wait .... where did my icons go? Uhhh ...."

Actually if you know you don't want your old settings back just go to Nautilus and delete the beryl directory. That just sets it back to defaults. And yes, this forum is a far far cry from the days I remember of constant statements of "RTFM" even after you had poured over 50 pages of little details that may or may not apply to your situation. This Ubuntu community shows incredible amounts of support, tolerance, and encouragement. It's put the fun back into Linux I think.

---

### Post by Brackish_zygote on 2007-05-22
If you can view the Beryl Settings Manager window, then there is a way to change back to default settings without using the terminal. Just go to General Options in the Settings, Profiles and Desktop integration section under the profiles tab there is a default profile. If you haven't changed that profile, you should be able to load it and restore the default settings. 

Hope this helps.

---

