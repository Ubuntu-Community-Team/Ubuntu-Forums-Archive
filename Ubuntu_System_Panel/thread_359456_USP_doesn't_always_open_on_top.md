---
title: "USP doesn't always open on top"
date: 2007-02-12
forum: Ubuntu System Panel
---

### Post by groggyboy on 2007-02-12
When I have a window open and I try to open USP, it appears behind the window.  I either have to click in the USP panel or reopen the menu to bring it to the front.  This behaviour is quite consistent.  Is it a bug or a "feature"?  If it is a feature, how can I make it stop doing that?  It's *very* annoying.  I've attached a picture to show what I mean.  I'm not sure if it's related, but when I do have USP in front, and I click on a window behind it, USP doesn't disappear like I expect it to.

Two other questions: 1.) How do I use the shortcuts panel?  It's blank, and there are no options to configure it in the preferences.  2.) How do I make themes?  [roberTO's theme]("http://www.ubuntuforums.org/showthread.php?t=357368") is quite inspiring.=D>

---

### Post by Malac on 2007-02-12
> **groggyboy said:**
> When I have a window open and I try to open USP, it appears behind the window.  I either have to click in the USP panel or reopen the menu to bring it to the front.  This behaviour is quite consistent.  Is it a bug or a "feature"?  If it is a feature, how can I make it stop doing that?  It's *very* annoying.  I've attached a picture to show what I mean.  I'm not sure if it's related, but when I do have USP in front, and I click on a window behind it, USP doesn't disappear like I expect it to.

Two other questions: 1.) How do I use the shortcuts panel?  It's blank, and there are no options to configure it in the preferences.  2.) How do I make themes?  [roberTO's theme]("http://www.ubuntuforums.org/showthread.php?t=357368") is quite inspiring.=D>

1.) Click the Pin Menu Button(top left of the sidepane) Then drag shortcuts onto the shortcut plugin from your desktop or other menu. The first one is a bit tricky as you have to aim for just below the "Shortcut" title button until you see a black line. Then release.
2.) USP themes are just normal gtk themes you can create them with a variety of tools. Do a search on the forums or through Google. You could also download some from [www.gnome-look.org]("http://www.gnome-look.org") and then just alter the png files and/or the gtkrc file.

The menu focus thing is a bit of a problem as Metacity and Beryl seem to approach focus events in a different way and so coding for both Window Managers is proving more of a problem than it should. :)
Are you using Beryl, if so, how have you got focus stealing set?

EDIT: Just noticed you are running Kubuntu. So I'll need to install a copy to test with KDE.

---

### Post by chanders on 2007-02-12
Also, to solve the focus stealing problem, set it to none in beryl-manager ;-)

---

### Post by groggyboy on 2007-02-12
> **Malac said:**
> The menu focus thing is a bit of a problem as Metacity and Beryl seem to approach focus events in a different way and so coding for both Window Managers is proving more of a problem than it should. :)
Are you using Beryl, if so, how have you got focus stealing set?

EDIT: Just noticed you are running Kubuntu. So I'll need to install a copy to test with KDE.

Beryl's focus stealing prevention was set to normal.  Chander's tip to set it to none fixed the problem.  What does that affect anyways?  And as for KDE, I don't actually use USP in KDE.  - I use USP in gnome and [Kickoff]("http://www.kde-look.org/content/show.php?content=50240") in KDE - if you ever use KDE, i recommend it.  Some good ideas there.  I did, however, use USP in Xfce for a little while (via the xfapplet plugin).

thanks for the tips re: themes and shortcuts pane!
:guitar:

---

### Post by chanders on 2007-02-12
As both a KDE user and Gnone user, what do you like in Kickoff that you would like to see in USP?

---

### Post by delfick on 2007-02-12
> **chanders said:**
> As both a KDE user and Gnone user, what do you like in Kickoff that you would like to see in USP?

didn't you once saying you were making a kickoff plugin or something ??

---

### Post by chanders on 2007-02-12
> **delfick said:**
> didn't you once saying you were making a kickoff plugin or something ??
 
Thats why I asked that question ;-)

---

### Post by delfick on 2007-02-12
> **chanders said:**
> Thats why I asked that question ;-)

hehe, in that case....

tabs with pictures look nice :D


:D
(usp rules :D)

---

### Post by groggyboy on 2007-02-13
> **delfick said:**
> tabs with pictures look nice

agreed.  in general, i find the large tabs/icons to be quite nice.  also, i like that i just have to mouseover a tab to select it (although this isn't for everyone - my roommate hates kickoff for that reason - his motor skills aren't fine enough :roll: - it's kinda funny watching him mouse over the wrong tab and get all flustered).  i also like the search bar in kickoff.  it is *really* nice - it behaves kinda like deskbar.

in general, i think that kickoff has quite a logical layout.  each important thing has its own tab (ie: favourites, recent, places, applications & "quit").  it isn't customizable though - USP has got kickoff beat hands down on that one.  i guess if i wanted, i could set up USP's tabs in more or less the same way.  go figure, something in KDE is *less* configurable than it's gnome counterpart!

the two are different, each good for their own reasons.  some things from kickoff that i would *love* to see in USP: a deskbar-like search field, the ability to have large icons in favourites, and separate favourites/applications plugins (although i can survive without this last one).  i remember being able to set the icons as large as 4 (24x24) in USP 0.41, but that option doesn't seem to work in the newer version.

all in all, i think USP is great.  thanks for the awesome menu, guys!

---

### Post by chanders on 2007-02-13
> **groggyboy said:**
> i remember being able to set the icons as large as 4 (24x24) in USP 0.41, but that option doesn't seem to work in the newer version.

Try changing in gconf editor /apps/usp/plugins/applications/icon_size to 4 ;-)

---

### Post by groggyboy on 2007-02-13
thanks!
 :oops:

---

### Post by Malac on 2007-02-13
> **chanders said:**
> Try changing in gconf editor /apps/usp/plugins/applications/icon_size to 4 ;-)
Sorry groggyboy my bad. A key name got changed and I missed it.
I've updated the uspconfig section of applications.py and committed it. I'm so glad I converted uspconfig to a plugin version too.  :)

---

