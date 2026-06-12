---
title: "First Theme direct for USP."
date: 2007-02-09
forum: Ubuntu System Panel
---

### Post by roberTO on 2007-02-09
[COLOR="Orange"]**UPDATED!**[/COLOR]

Hi All USP Fan!

I use USP2-svn version, and the preferences panel i see "USP Theme" choice...
Write in the section "Clearlooks" and WOW USP look Clearlooks...
Very good option!

And now make my first theme DIRECT for USP.
USP-solidWHITE
This theme is simple GTK-2.0 theme but skinned only the USP elements (buttons, tabs, options, menus, scrollbars, and Button for Panel...)
DO NOT USE for GTK!!! Look horryble!!!

To install theme:
1 - GoTo System/Preferences/Themes and press install theme button.
2 - In the USP Preferences/Main tab/"USP Theme" input box put theme name USP-solidWHITE.
3 - In the "USP Button Text" inputbox, put spaces after the text while not looks good.

And enjoy :)

Files:
[USP-solidWHITE-1.1 theme]("http://www.roberto-studios.hu/Files/USP/USP-solidWHITE-1.1.tar.gz")


Other: question to chanders: Hi, Any solution to remove colorized backgrounds in applets?
example: My tabs is gradient colour, and i add applet, bg not gradient more...
Other programs example: gnome-theme-manager, gftp preferences panel and many-many more not used solid color in tabs.
picture:

[IMG]http://www.roberto-studios.hu/Files/USP/ColourProblem.png[/IMG]





[COLOR="Orange"]**UPDATES...**[/COLOR]


[IMG]http://www.roberto-studios.hu/Files/USP/USP-1.1-Preview.png[/IMG]



(Sorry my BAD english...)

[IMG]http://www.roberto-studios.hu/Files/USP/USP-4.png[/IMG]

---

### Post by chanders on 2007-02-09
First post!

First of all I would like to welcome you! You are also the very first person who has designed a theme just for use with USP. Thank you so much!! 
Your theme is kick *** \\:D/, and I am looking froward for the rest of you artistic types to give it a try!!

EDIT: I am a big fan of your themes! Anyone want to know more see [here]("http://topstyles.net/interview-with-roberto/")

---

### Post by nico1038 on 2007-02-09
Congratulations. I always find the look&feel of USP a little bit unfinished but with that theme it just looks great! 

Nico

---

### Post by roberTO on 2007-02-09
Thank you ALL!!

I continue work with USP themes, next theme is DARK i think, matched to dark GTK themes.
Canders and Malac  and all USP Developer keep up GREAT work!

---

### Post by delfick on 2007-02-09
so that's what full theming support means...

Thankyou roberTO :D :D 

(though where on your site can i find it ??)

> **roberTO said:**
> Thank you ALL!!

I continue work with USP themes, next theme is DARK i think, matched to dark GTK themes.
Canders and Malac  and all USP Developer keep up GREAT work!

looking forward to them :D

---

### Post by Malac on 2007-02-10
USP2 in the SVN can use _any_ gtk2 theme in your theme folder. It will use the current theme if the field in uspconfig is left blank but if you put in an existing theme name it will use that instead. Some look better than others, in my experiments.
If you find one that isn't quite right save it under a different name and then remove the elements that aren't used by USP(not really necessary) and change the png's or theme file to the values that look best for you.

Excellent Work roberTO and welcome to the fray. :)

---

### Post by roberTO on 2007-02-10
Sorry all i not enough time for update my site...
Theme direct linked again!

Bye...

---

### Post by Malac on 2007-02-10
[ATTACH]24973[/ATTACH]
Very Nice roberTO.

---

### Post by delfick on 2007-02-10
> **roberTO said:**
> Sorry all i not enough time for update my site...
Theme direct linked again!

Bye...

hehe, thnx :D

---

### Post by roberTO on 2007-02-14
[COLOR="Orange"]**UPDATES available in first page...**[/COLOR] :KS

---

### Post by delfick on 2007-02-14
> **roberTO said:**
> [COLOR="Orange"]**UPDATES available in first page...**[/COLOR] :KS

awsome :D

thnx :D
[SIZE="1"]
(i'll test it when i fix my computer, which would probably not happen till after work (I updated the kernel, now linux won't boot))[/SIZE]

edit :: hmm, that was easy to fix :D

here have a screenshot :D

---

### Post by roberTO on 2007-02-15
> **delfick said:**
> awsome :D

thnx :D
[SIZE="1"]
(i'll test it when i fix my computer, which would probably not happen till after work (I updated the kernel, now linux won't boot))[/SIZE]

edit :: hmm, that was easy to fix :D

here have a screenshot :D

Hi!

How to make the USP border 0px ???
Also: I working a dark menu theme :)
Upload soon...

---

### Post by delfick on 2007-02-15
> **roberTO said:**
> How to make the USP border 0px ???

in uspconfig, set the "set border" option to 1 :D (which is as low as it goes, screenshot attached).... 

> Also: I working a dark menu theme :)
Upload soon...

YAY!!! :D

---

### Post by Malac on 2007-02-15
> **roberTO said:**
> How to make the USP border 0px ???.
Due to the SetGconf error check returning 0 if something isn't set you can't set border width to 0 using the SetGconf function.
If it really bothers you, edit the /usr/bin/usp file and replace this line (number 80 in the latest SVN)
```
        self.borderwidth = SetGconf( self.client, "int", "/apps/usp/border_width", 8 )
```with:
```
        self.borderwidth = 0
```You will have to do this whenever you update.
Hope this helps.

---

### Post by roberTO on 2007-02-15
> **Malac said:**
> Due to the SetGconf error check returning 0 if something isn't set you can't set border width to 0 using the SetGconf function.
If it really bothers you, edit the /usr/bin/usp file and replace this line (number 80 in the latest SVN)
```
        self.borderwidth = SetGconf( self.client, "int", "/apps/usp/border_width", 8 )
```with:
```
        self.borderwidth = 0
```You will have to do this whenever you update.
Hope this helps.

Wow!

Thank you answers! :lolflag: 

roberTO

---

### Post by hanzomon4 on 2007-02-18
I don't see a "usp-theme" in my svn usp usp-preferences

EDIT: forget about it, I got it.  
I forgot ./usp_update [color=red]install[/color]

---

### Post by hanzomon4 on 2007-02-18
I can't get my tabs to look like the ones in the first post nor can I set a boarder

---

### Post by hanzomon4 on 2007-02-18
> **Malac said:**
> Due to the SetGconf error check returning 0 if something isn't set you can't set border width to 0 using the SetGconf function.
If it really bothers you, edit the /usr/bin/usp file and replace this line (number 80 in the latest SVN)
```
        self.borderwidth = SetGconf( self.client, "int", "/apps/usp/border_width", 8 )
```with:
```
        self.borderwidth = 0
```You will have to do this whenever you update.
Hope this helps.

Can't believe I missed this post, I changed the 0 to 5 to manually set the boarder. For some reason it just won't set in the usp preferences .

By the way good work folks this is coming along nice. Deflick you've introduced me  to screenlets usp kiba-dock and other cool stuff, you should be on the payroll if people actually got paid.

EDIT: I removed the number and uncommented this line *SetGconf( self.client, "int", "/apps/usp/border_width", 8 )*to set the boarder in usp preferences

---

### Post by delfick on 2007-02-18
> **hanzomon4 said:**
> Delfick you've introduced me  to screenlets usp kiba-dock and other cool stuff, you should be on the payroll if people actually got paid.

hehehehe :D

---

### Post by MetalMusicAddict on 2007-02-18
roberTO. I just wanted to say hi to a old face from Aqua-Soft. ;)

Nice theme here.

---

### Post by hanzomon4 on 2007-02-20
Aqua-soft is what got me started in what eventually lead to linux, I would still love to see a linux version of avedesk although screenlets seem to be filling that niche.

---

### Post by MetalMusicAddict on 2007-02-22
> **hanzomon4 said:**
> Aqua-soft is what got me started in what eventually lead to linux, I would still love to see a linux version of avedesk although screenlets seem to be filling that niche.

I thought I knew your name as well! :) I think Ive seen about 5-6 of us over here.

Oh, I so miss Avedesk. We had some cool stuff from A-S didnt we. :) I look at A-S every once in a while for walls and how much Ubuntu is mentioned.

---

### Post by s_spiff on 2008-05-20
> **delfick said:**
> awsome :D

thnx :D
[SIZE=1]
(i'll test it when i fix my computer, which would probably not happen till after work (I updated the kernel, now linux won't boot))[/SIZE]

edit :: hmm, that was easy to fix :D

here have a screenshot :D

Sweet! Can you please tell me how do I get something like that? esp. the terminal in the menu part!!! Including the tabs on the top etc...

---

### Post by Malac on 2008-05-21
> **s_spiff said:**
> Sweet! Can you please tell me how do I get something like that? esp. the terminal in the menu part!!! Including the tabs on the top etc...
See [http://code.google.com/p/ubuntu-system-panel/w/list](http://code.google.com/p/ubuntu-system-panel/w/list) for instructions on install, extra plugins and setup of tabs etc.
 
Hope this helps

---

### Post by BilliShere on 2008-08-22
> **hanzomon4 said:**
> Aqua-soft is what got me started in what eventually lead to linux, I would still love to see a linux version of avedesk although screenlets seem to be filling that niche.
I would absolutely LOVE to see one of those avedesk tab things like on the sides of the desktop. The ones that slide out to reveal a bunch of program icons. That is what i miss most from windows.. it was an essential part of my desktop.

---

### Post by Rayaz on 2009-08-09
Link for the download doesn't work anymore. Anywhere else I can download the theme?
Thanks.

---

