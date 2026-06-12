---
title: "How to reset all settings their original state?"
date: 2016-05-15
forum: Ubuntu Studio
---

### Post by javierdl on 2016-05-15
I know, silly me, I didn't make a backup of the original state the moment I installed US.
Then I naively played with the Main menu using the Menu Editor, and now I can't orbit around objects in Blender using Alt as before. Not to mention that it screwed with the directories I originally had.

Thanks guys,

JDL

---

### Post by javierdl on 2016-05-15
Serg from [AskUbuntu]("http://askubuntu.com/questions/588351/how-do-i-reset-ubuntu") advised to Reset the Desktop for [COLOR=#111111][FONT=Ubuntu]Ubuntu 14.04.2 LTS[/FONT][/COLOR]:

[COLOR=#111111][FONT=Ubuntu]**1) Reinstall ubuntu desktop**[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Execute in terminal or tty: sudo apt-get install --reinstall ubuntu-desktop[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]**2) Reset compiz **[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]dconf reset -f /org/compiz/ (Source: [ubuntu handbook]("http://ubuntuhandbook.org/index.php/2014/04/reset-unity-and-compiz-settings-in-ubuntu-14-04/"))[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]**3) Reset Unity **[/FONT][/COLOR]
Would this work in US 16.04?

---

### Post by QIII on 2016-05-15
What do you mean by "US"?

---

### Post by javierdl on 2016-05-15
QIII, 
Ubuntu Studio

---

### Post by QIII on 2016-05-15
Thanks.

Bear in mind that not everyone will interpret or understand acronyms the way you intend.  Best to call it "Ubuntu Studio".

Cheers!

---

### Post by javierdl on 2016-05-18
Well, I just ended up reinstalling...

---

