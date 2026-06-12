---
title: "Evince menu problems"
date: 2013-06-05
forum: Ubuntu Development Version
---

### Post by cariboo on 2013-06-05
I just opened that latest issue of [Full Circle Magazine]("http://fullcirclemagazine.org/") in the default pdf viewer (Evince) and noticed the only menu Selection I have is Document Viewer, and the only drop-down that shows is Help. Is anyone else seeing the same thing?

---

### Post by dino99 on 2013-06-05
that link is opened normaly and cant see a pdf there.

---

### Post by zika on 2013-06-05
> **dino99 said:**
> that link is opened normaly and cant see a pdf there.
[http://dl.fullcirclemagazine.org/issue73_en.pdf](http://dl.fullcirclemagazine.org/issue73_en.pdf)
It opened with warning in FF, although without any problems and it opened in Evince OK with all the stuff in all the menues...

---

### Post by dino99 on 2013-06-05
> **zika said:**
> [http://dl.fullcirclemagazine.org/issue73_en.pdf](http://dl.fullcirclemagazine.org/issue73_en.pdf)
It opened with warning in FF, although without any problems and it opened in Evince OK with all the stuff in all the menues...

That link open the pdf, but its delayed by 3/5 seconds; everything seems normal.

---

### Post by slickymaster on 2013-06-05
Same here. Everything normal, with all the stuff in all the menus

---

### Post by cariboo on 2013-06-05
Well is seems my problem is solved, I was looking for a global-menu, instead of just clicking on the gear icon in the upper right. It just goes to show you that I should have at least 2 cups of coffee first thing in the morning, before trying to do anything even remotely important. I'll mark this thread as Solved. :-D

---

### Post by skierpage on 2013-11-01
> **cariboo907 said:**
> Well is seems my problem is solved, I was looking for a global-menu, instead of just clicking on the gear icon in the upper right. :-D

Don't blame yourself, it's still misleading and non-intuitive.
[LIST]
[*]There's no print button on the toolbar ( [LP bug 746160]("https://bugs.launchpad.net/ubuntu/+source/evince/+bug/746160") ) 
[*]The HUD doesn't work, so press Alt and look for a Print command and nothing matches ( [LP bug 1088778]("https://bugs.launchpad.net/ubuntu/+source/indicator-appmenu/+bug/1088778") ) 
[*]Press F1 for help, the Evince Document Viewer help window pops up, and its "Printing a Document" says very specifically 
[*]Click [COLOR=#6C6C6C][COLOR=#6C6C6C]File[/COLOR] &#9656; [COLOR=#6C6C6C]Print[/COLOR][/COLOR]
which doesn't work ( [LP bug 1247317]("https://bugs.launchpad.net/ubuntu/+source/evince/+bug/1247317") ) 
[/LIST]
When you try to print from many online systems (Google docs, airline boarding passes, shipping documents, etc.) their "Print" button results in a PDF download that the browser offers to open in Document Viewer. And then... good luck finding Print.

So one of the main use cases for the Document Viewer is, while not technically "broken", quite unpolished.

---

### Post by cariboo on 2013-11-01
> **skierpage said:**
> Don't blame yourself, it's still misleading and non-intuitive.
[LIST]
[*]There's no print button on the toolbar ( [LP bug 746160]("https://bugs.launchpad.net/ubuntu/+source/evince/+bug/746160") ) 
[*]The HUD doesn't work, so press Alt and look for a Print command and nothing matches ( [LP bug 1088778]("https://bugs.launchpad.net/ubuntu/+source/indicator-appmenu/+bug/1088778") ) 
[*]Press F1 for help, the Evince Document Viewer help window pops up, and its "Printing a Document" says very specifically 
[*]Click [COLOR=#6C6C6C][COLOR=#6C6C6C]File[/COLOR] &#9656; [COLOR=#6C6C6C]Print[/COLOR][/COLOR]
which doesn't work ( [LP bug 1247317]("https://bugs.launchpad.net/ubuntu/+source/evince/+bug/1247317") ) 
[/LIST]
When you try to print from many online systems (Google docs, airline boarding passes, shipping documents, etc.) their "Print" button results in a PDF download that the browser offers to open in Document Viewer. And then... good luck finding Print.

So one of the main use cases for the Document Viewer is, while not technically "broken", quite unpolished.

After my initial problem, of not paying attention, the print command is quite easy to find. Just click the gear icon to see the full menu. I had to setup my printer, as I hadn't done it since upgrading to Trusty, once that was done I can print what I want whether to a printer, or file.

---

### Post by QDR06VV9 on 2013-11-02
> **cariboo907 said:**
> Well is seems my problem is solved, I was looking for a global-menu, instead of just clicking on the gear icon in the upper right. It just goes to show you that I should have at least 2 cups of coffee first thing in the morning, before trying to do anything even remotely important. I'll mark this thread as Solved. :-D

Off topic I know butt...
Oh I can so relate to that!!:D

---

### Post by David Oxland on 2014-07-06
I don't have a gear icon at the top. Only a blank menu bar only way to escape is CTRL + W and kill  Evince completely.
 I've tried to file a bug and the issue has been marked as resolved a couple of times. lots a talk on the bug site  about Gnome having the right or obligation to do this.
If it's a simple choice of global set up(I don't know what that is) I don't find documentation to show me how.
For me the problem is definitely not solved. Evince opens with no menu bar or gear icon and it seems that now CTRL + P  will not work any more either so I can't print a bill or invoice.
Ubuntu 14.04 LTS now

---

### Post by cariboo on 2014-07-07
This thread is two years old, and the last post has nothing to do with Utopic, closed.

---

