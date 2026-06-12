---
title: "How to.."
date: 2006-07-28
forum: Ubuntu System Panel
---

### Post by chanders on 2006-07-28
How to add items

Method 1
1. Press the pin button (top left) 
2. Drag items from the old gnome menu into USP
3. Un-press the pin button

Method 2 (Applications only)
1. Click on 'All Applications'
2. Right click and choose 'Add to favourites'

Thats it!

---

### Post by chanders on 2006-07-28
How to get your resolution to show up (if it doesnt) 

Most users reported that this works
1. Click the resolution button then apply
2. Restart the applet

USP gets this data from
/desktop/gnome/screen/default/0/resolution
/desktop/gnome/screen/default/0/rate

---

### Post by gruvsyco on 2006-07-30
Hot to set your menu opacity:

Quote Chanders from Compiz.net:

Elegant:
Open gconf-editor go to "state" plugin in compiz and write in "opacity"
w:Menu:90

Brute-Force:
place your mouse over USP and - hold down alt - and - scroll the mouse wheel down

---

### Post by chanders on 2006-08-06
HowTo set colors:

Here is a link with a list of colors you can choose from (or you can just install gcolor and get the values from there)

[Color List]("http://www.webmonkey.com/webmonkey/reference/color_codes/")

[[IMG]http://img330.imageshack.us/img330/6327/colorhexem1.th.gif[/IMG]]("http://img330.imageshack.us/img330/6327/colorhexem1.gif")

---

### Post by Mathiasdm on 2006-09-17
**How to move your menu**
While the menu is open, press 'ALT' and drag the menu.
Bug: this is not remembered by the USP :(

---

### Post by airtonix on 2006-10-03
I think you have to either move it, then unpin then re-pin it....then possibly restart gnome-panel 

```

 sudo killall gnome-panel

```

---

### Post by andresmoschini on 2006-10-08
USP is the better menu for my use, but... I dont know how asign a hotkey].
The keyboard support of the UPS menu seems bad, but i can wait for new versions...
thanks (sorry for my bad english)

---

### Post by BitTorrentBuddha on 2006-10-10
The ability to map it to a hotkey would be much appreciated by many I'm sure.

---

### Post by kobewan on 2007-02-14
[LEFT]     **How to rearrange the panes**

Open gconf-editor. Unfold the tree which say apps->Select usp

Scroll down to a field called plugins_list and double click on it.

Rearrange the values the way you want. The highest in the list will come first. The default stacking order is from top to bottom, all in a row. You can change this with a value of 'newpane'. 

'newpane' causes the value after it to open next to the pane of the value above it, instead of in the same pane.

EDIT: Still can't figure out how to permanently move the menu. It's a little annoying, because there is about a 2px gap between my menu and my panel.
[/LEFT]

---

### Post by Malac on 2007-02-15
> **kobewan said:**
> Still can't figure out how to permanently move the menu. It's a little annoying, because there is about a 2px gap between my menu and my panel.Have you tried altering the panel_size key.

---

### Post by kobewan on 2007-02-16
> **Malac said:**
> Have you tried altering the panel_size key.

Yes, I have, but it doesn't seem to do anything. It defaults at 24 (my panel size), but changing it either upwards or downwards seems to have no effect. I've tried changing it and closing gconf-editor, killing python, killing gnome-panel and even sudo killall gnome-panel. No effect :(

---

### Post by chanders on 2007-02-16
Try setting it to 1, then removing the applet and adding back. This was sorted in USP2. You should try it out from SVN ;-)

---

### Post by kobewan on 2007-02-16
Didn't work.

How stable is the SVN? I just discovered this program about a day ago, and its already become invaluable. I can't imagine living without it. If the SVN crashes often, I'll probably pass. On the other hand, if you need more testers or something, I'd be happy to...

---

### Post by delfick on 2007-02-16
> **kobewan said:**
> Didn't work.

How stable is the SVN? I just discovered this program about a day ago, and its already become invaluable. I can't imagine living without it. If the SVN crashes often, I'll probably pass. On the other hand, if you need more testers or something, I'd be happy to...

svn is stable :D

(and fantastic :D).....

hmm, a crashing menu...that sounds funny :D :p
(has that ever happened to the usp chanders ??)

---

### Post by kobewan on 2007-02-19
Alright, my guide is finally done:
[URL="http://ubuntuforums.org/showthread.php?t=365147"]
http://ubuntuforums.org/showthread.php?t=365147[/URL]

---

### Post by delfick on 2007-02-19
> **kobewan said:**
> Alright, my guide is finally done:
[URL="http://ubuntuforums.org/showthread.php?t=365147"]
http://ubuntuforums.org/showthread.php?t=365147[/URL]

well done :D

i like it a lot :D

it should be made sticky :D

---

### Post by Zyphrexi on 2007-03-09
I second the sticky. It's annoying when clicks open up a new firefox window though.

---

### Post by stalker145 on 2007-03-11
> **Zyphrexi said:**
> I second the sticky. It's annoying when clicks open up a new firefox window though.

<ctrl> click and open it in a new tab instead...

---

### Post by Zyphrexi on 2007-03-14
well it'd be nicer if it just jumped to the location of the post the link refers to. But this is no longer an issue now that the wiki is up.

---

### Post by kobewan on 2007-03-15
Actually, I wanted there to be a wiki for this very same reason! I couldn't figure out how to do it in the forums, or if it is even possible. Sorry that I didn't know it auto opened in a new window; I pretty much always middle-click links and open them in new tabs, so I don't know what's supposed to open there and whats not.

Glad to see that the wiki is up as well --- I've been meaning to do it for a while, but kept putting it off. I've become a lot more busy than I expected to be, and was trying to figure out proper formatting of wiki pages to set up all the fancy internal linking and stuff. Glad that somebody else put it up, and I apologize that I couldn't help more :redface:

---

### Post by Malac on 2007-03-15
> **kobewan said:**
> Actually, I wanted there to be a wiki for this very same reason! I couldn't figure out how to do it in the forums, or if it is even possible. Sorry that I didn't know it auto opened in a new window; I pretty much always middle-click links and open them in new tabs, so I don't know what's supposed to open there and whats not.

Glad to see that the wiki is up as well --- I've been meaning to do it for a while, but kept putting it off. I've become a lot more busy than I expected to be, and was trying to figure out proper formatting of wiki pages to set up all the fancy internal linking and stuff. Glad that somebody else put it up, and I apologize that I couldn't help more :redface:
No Probs, you've helped loads kobewan :)
You did all the work, I just copied/pasted it into the wiki with very minor alterations.

---

### Post by kobewan on 2007-03-15
Thanks for that though, now I might actually get around to updating it.

I've been playing around with the latest SVN, but havn't noticed any major changes. Am I missing anything that needs to be documented, or is there anything else in the documentation that isn't clear enough?

---

### Post by Malac on 2007-03-16
> **kobewan said:**
> Thanks for that though, now I might actually get around to updating it.

I've been playing around with the latest SVN, but havn't noticed any major changes. Am I missing anything that needs to be documented, or is there anything else in the documentation that isn't clear enough?

No major changes recently, just some debug alterations to hopefully give us more info if there is a problem. And I've been trying to shave the code down to reduce cpu and ram requirements, stuff like that.

Hopefully we are just down to slight tweaks and error corrections ready for Beta, then Final release.

---

### Post by eagletip on 2007-10-13
Good day
For some reason I cannot adjust the display settings anymore. All my icons are way too big and Icant fix.. Here isthe error code I get::

an error occured during your last kde upgrade leaving an orphaned control module.
you have old third party modules lying around

And I have no clue what this means.
Can you help??

Regards

Larry

---

### Post by stan theman on 2008-11-22
when i first installed i had a wifi icon beside the date on top right of panel. Through a right-clicking mishap its now gone. How do i get it back? thanks

it also used to show minimized running programs like the windows system try?

---

