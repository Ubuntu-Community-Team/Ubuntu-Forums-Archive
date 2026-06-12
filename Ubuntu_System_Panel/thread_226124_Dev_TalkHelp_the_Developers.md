---
title: "Dev Talk/Help the Developers"
date: 2006-07-30
forum: Ubuntu System Panel
---

### Post by Note360 on 2006-07-30
We are having a serious problem with the menu the gnome panel seems to want to swallow the panel whole and we cant figure out how to stop this. HELP!!!

(The problem whent like this)
Tis' just a rabbit
*chanders walks up to it*
AHHH
*rest come in
AHH
*every one runs and hides behind a rock

---

### Post by _profox on 2006-07-30
And here's an explanation that humans can understand ;)

When you open the menu (clicking on the System button) the menu is BEHIND the gnome-panel, but we want to have it completely in FRONT of it.

But we haven't figured out a way to do this yet. If we make it a Dock instead of a Menu, it will show up in front, but then we can't set the focus anywhere.

So any help is greatly appreciated :) this is something that has high priority.

---

### Post by Note360 on 2006-07-30
Lol sorry for my deaply cryptic message to the public

---

### Post by _profox on 2006-07-30
I'm facing another problem :)

Chanders, is it possible to change something about the applet button, from inside the MainWindow instance?

If I understand the code correctly, mainwin (class MainWindow) is a child of MenuWin?

Can I access variables from MenuWin inside the code of MainWindow (which is declared as mainwin in the MenuWin code block, I think?)

I should go buy myself a book of Python very soon ;) It's interesting stuff. I'm just chewing on old programming experience right now. Python is different in alot of ways. So, sorry for the dull questions ;) and Thanks

edit: I found the problem :)

---

### Post by Note360 on 2006-07-30
Try looking through the free Dive into Python book.

---

### Post by Note360 on 2006-07-31
I have a temporary solution make the distance from the panel adjustable so that for me I can have it closer (mine is completly disjointed) and others can have it father so the gnome menu doesnt over shadow it.

---

### Post by bulldog on 2006-07-31
Well this problem isn't affected to everyone I presume.
I haven't the slicest problem with the menu hiding.
The menu is located at the top-left of my panel which has 24 pixels.
Even when i set the gnome panel to 45 pixels there isn't a problem here.
It comes neatly under my panel and no hiding behind. 
I have Xgl/Compiz and maybe this make a difference between the users.

But i must say,it is a very nice application and you are all doing a great job creating it so fast.
Well done,and keep it up.

---

### Post by Note360 on 2006-07-31
Hmm odd it happened to me when I pumped up my gnome-panel on Xubuntu the top border was cut off.

---

### Post by bulldog on 2006-07-31
That's why I made my panel twice as big to see what happened.
But the menu was adapting and showed nicely under the panel and not behind.
I'm using Ubuntu and the problem doesn't exist.
Maybe take a look at howmany users have this problem and see what taste of Ubuntu they use.
The problem may not be so big as it seems.

---

### Post by Note360 on 2006-07-31
This is the problem

this is floating:
[http://www.flickr.com/photos/31943009@N00/203107219/](http://www.flickr.com/photos/31943009@N00/203107219/)

this is eating:
[http://www.flickr.com/photos/31943009@N00/203107216/](http://www.flickr.com/photos/31943009@N00/203107216/)

---

### Post by bulldog on 2006-07-31
I understand the problems and I made my panel as big as 80 pixels.
Then opened the menu and it was behind my panel.
Then closed and reopened the menu and it was nice under my 80 pixel panel.
It's adepting at the size of my panel I presume.
Made my panel 24 again and it was at the right place the first time.
So maybe I'm lucky,but the menu placement is no problem here.

---

### Post by _profox on 2006-07-31
Hey, can someone give me enough rights to assign bugs and to open/close bugs and change their priority? in launchpad

---

### Post by _simon_ on 2006-07-31
This won't really help but I've not had the problem you're talking about.

My menu is bottom left and opens just above the panel each and every time I open it.

Pic:

[[IMG]http://i17.photobucket.com/albums/b96/snewberry1980/Screenshots/th_latestusp.png[/IMG]](http://i17.photobucket.com/albums/b96/snewberry1980/Screenshots/latestusp.png)

---

### Post by _profox on 2006-07-31
chanders.

Please read this bugreport through:
[https://launchpad.net/products/usp/+bug/54695](https://launchpad.net/products/usp/+bug/54695)

I think we have to remove all "'"s in the arguments. Could this be correct? I think it is the way the terminal and the gnome menu work too. Can you let me know for sure? (the terminal seems to ignore ' but I'm not sure about the gnome menu)

edit: I solved the bug. I'll send the patch to you. I included comment code in the patch.

---

### Post by Note360 on 2006-07-31
profoX try editing the bugs. can we make a team up so we all can?

---

### Post by _profox on 2006-07-31
I don't know :) you're the one with all control over our launchpad
edit: you changed it :) thanks! :KS

---

### Post by Note360 on 2006-07-31
I made team so me u and chandler and any one else in the team can do anything.

---

### Post by _profox on 2006-07-31
> **Note360 said:**
> I made team so me u and chandler and any one else in the team can do anything.

Ok, so, how do I change status of bugs and how do I close bugs? can't seem to do that yet..

---

### Post by Note360 on 2006-07-31
click on 

usp(upstream) and a menu should pop down

---

### Post by vonpmg on 2006-08-02
I know you are going to mount a CVS but i need something to work with the changes i am doing to the code.
So i use baazar-ng at home, the same that launchpad is using, so i have a repository in launchpad for bzr (bazaar) attached to usp.
You can look at it if you click in the Branches options in the Usp project ([https://launchpad.net/products/usp/+branches](https://launchpad.net/products/usp/+branches))
I have had a problem making the branch so 2 branch exists.
One of them is named - Don't use this - :wink: , please, use the other if you want.
Actually it contains version 0.31 with my patches to language and some modifications i am trying to the glade file.

---

### Post by chanders on 2006-08-02
> **vonpmg said:**
> I know you are going to mount a CVS but i need something to work with the changes i am doing to the code.
So i use baazar-ng at home, the same that launchpad is using, so i have a repository in launchpad for bzr (bazaar) attached to usp.
You can look at it if you click in the Branches options in the Usp project ([https://launchpad.net/products/usp/+branches](https://launchpad.net/products/usp/+branches))
I have had a problem making the branch so 2 branch exists.
One of them is named - Don't use this - :wink: , please, use the other if you want.
Actually it contains version 0.31 with my patches to language and some modifications i am trying to the glade file.

Seeing that you are proactive in getting the translate done, I have the Translation features working well in UCC. maybe you can look at the code and re-use some of it. It is really simple to setup..

The users send you a translation file and as long as it is named correctly it is used...

Let me know if you want more information. That way you wouldnt have to make a separate glade file for every language..

I will look at your branch in launchpad.... thank again!

---

### Post by vonpmg on 2006-08-02
Hi.
Just now i was looking you Ucc code. You read me mind !!! :wink: 
But i don't write a different glade file for each language.
The glade file is yours, i don't touch it to translate anything.
I simply use the gettext functions.
You could use:
```

xgettext usp.glade

```
And it generates the messages.pot, we can merge with the translatable strings appearing in usp.
So translators only need to send us the messages.po
My modifications to the glade file is to fix some "problems" a user have with the searchbar.

I am going to bed now. Tomorrow i have to wake up early. I look tomorrow to your code.
Thanks

---

### Post by chanders on 2006-08-02
> **vonpmg said:**
> Hi.
Just now i was looking you Ucc code. You read me mind !!! :wink: 
But i don't write a different glade file for each language.
The glade file is yours, i don't touch it to translate anything.
I simply use the gettext functions.
You could use:
```

xgettext usp.glade

```
And it generates the messages.pot, we can merge with the translatable strings appearing in usp.
So translators only need to send us the messages.po
My modifications to the glade file is to fix some "problems" a user have with the searchbar.

I am going to bed now. Tomorrow i have to wake up early. I look tomorrow to your code.
Thanks

See ya tomorrow :)

---

### Post by Note360 on 2006-08-02
actually you know what is a good version control system. Git Linus's new project.

[http://git.or.cz/](http://git.or.cz/)

---

### Post by Note360 on 2006-08-02
actually you know what is a good version control system. Git Linus's new project.

[http://git.or.cz/](http://git.or.cz/)

---

### Post by vonpmg on 2006-08-03
I know Git. I have been playing with it in several mini projects.
It is distributed like Bazaar, but since Launchpad is using Bazaar i think is a best option to use it.
Thanks for the info anyway.

---

### Post by Note360 on 2006-08-04
You are probably right.

---

