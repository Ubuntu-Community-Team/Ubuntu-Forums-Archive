---
title: "HOWTO: Add a &quot;Search Folder&quot; option to Nautilus's right-click/context menu."
date: 2010-01-09
forum: Tutorials
---

### Post by rCXer on 2010-01-09
While Nautilus's built-in search (accessed by the "Search" button or Ctrl-F) can find files by name or extension, I often need something a little more advanced.  For example, searching for files based on their dates, size, and content.  The gnome-search-tool, accessed by Places->Search for Files, can do this but I have to browse to the folder of interest everytime I use it.  This problem can be solved by adding the gnome-search-tool to the right-click/context menu using the "Nautilus Actions Configuration".

[list]
[*] Install it by entering...
```

sudo apt-get install nautilus-actions

```
...into the terminal.  

[*] Start the program by going to System->Preferences->Nautilus Actions Configuration.
[/list]
[SIZE="5"]Ubuntu 11.04 and later[/SIZE]

Haven't figured it out yet.  All suggestions are welcome.

[SIZE="5"]Ubuntu 10.04 and 10.10[/SIZE]
[list]
[*] File->"New action"
[*] On the "Actions" tab, type...
```
Advanced Search...
```
...for the **Context Label** and make sure **Display item in selection context menu** is checked.
[*] On the "Command" tab, type...
```
gnome-search-tool
```
...for **Path** and...
```
--path %d/%f
```
...for **Parameters**. (For a detailed description of the parameters, click the Legend button.)
[*] Now we have to tell Nautilus to display this option only when a folder is selected.  On the **Conditions** tab, accept the defaults. Under "*Appears if selection contains*", Select **Only folders** and make sure "*Appears if selection has multiple files or folders*" is **unchecked**.
[*] File->Save and close the program.
[/list]

[SIZE="5"]Ubuntu 9.10 and earlier[/SIZE]
[list]
[*] Click the **Add** button.  Type...
```
Advanced Search...
```
...for the **Label**.

[*] In the Profiles box, select **Main** and and click the **Edit** button on the right.

[*] Next we have to tell the gnome-search-tool to start the search at the selected folder.  On the **Action** tab, enter...
```
gnome-search-tool
```
...for **Path** and...
```
--path %d/%f
```
...for **Parameters**.  (For a detailed description of the parameters, click the Legend button.)

[*] Now we have to tell Nautilus to display this option only when a folder is selected.  On the **Conditions** tab, accept the defaults. Under "*Appears if selection contains*", Select **Only folders** and make sure "*Appears if selection has multiple files or folders*" is **unchecked**. Click **OK**, **OK**, and **Close**.
[/list]

Restart Nautilus by logging out and logging back in. To test it, and right click on any folder choose "**Advanced Search...**" near the bottom of the context menu.  The folder you chose should appear by "*Look in Folder*".  Advanced options can be displayed by by clicking on "*Select More Options*" and choosing one from the dropdown menu before clicking **Add**. Finally, to search click the **Find** button.

That's it! :popcorn: 
For a graphical explanation (but dated) of how to use the *Nautilus Actions Configuration* look [here](http://www.foogazi.com/2007/11/05/adding-shortcuts-to-the-right-click-menu-in-ubuntu/).  If you want to edit or remove your "Advanced Search..." item from the menu, run the "Nautilus Actions Configuration", select it and click Edit Or Delete.  "Nautilus Actions Configuration" can be uninstalled by...
```
sudo apt-get remove nautilus-actions
```

---

### Post by Interruptor on 2010-01-27
> * Restart Ubuntu.
quite confusing :?
What about
```
$ nautilus-actions-check-actions-change
```?
What is it for?
There is no information about it neither in 
```
$ man nautilus-actions-check-actions-change
```
neither in
```
http://www.google.com.ua/search?q=%2Bnautilus-actions-check-actions-change
```

---

### Post by rCXer on 2010-01-27
> **Interruptor said:**
> quite confusing :?
I changed it to "Restart the computer"

> 
What about
```
$ nautilus-actions-check-actions-change
```?
What is it for?


I have no idea what "nautilus-actions-check-actions-change" does.  I always use the gui :P

---

### Post by Interruptor on 2010-01-27
> **rCXer said:**
> I changed it to "Restart the computer"
:)
It was not about formulation, but about meaning.
I'm used to restart Ubuntu (equals "my computer") only if I've changed something in grub's menu.lst or installed new kernel version. And this setting is so insignificant to restart Ubuntu. Weird :)

---

### Post by rCXer on 2010-01-28
Hmm, on my machine, items added sometimes don't appear until I restart nautilus or Ubuntu.  I'll leave "Restart the computer" there just in case.

---

### Post by Interruptor on 2010-03-20
```
nautilus -q
```
working without system restart :)

---

### Post by airtonix on 2010-03-20
Restarting the computer is quite unnecessary.

A simple restarting of nautilus will do.

1. alt + f2
2. gksudo killall nautilus && nautilus

Or just logout and back in again.

---

### Post by Interruptor on 2010-04-25
Also, adding different options can be very useful. For example, I modified parameters string like this:
```
--path %d/%f --hidden --contains=""
```

---

### Post by rCXer on 2010-07-13
I have updated this tutorial for Lucid.

---

### Post by Ashrael on 2011-06-10
Hello!

I tried this in Natty and found out that Nautilus Action Configuration has been upgraded to v 3.0.5, so your howto is not up to date anymore. Especially in Natty/Unity it's vital to be able to search from context menu. 

GRTZ!

---

### Post by mc4man on 2011-06-10
> **Ashrael said:**
> Hello!

I tried this in Natty and found out that Nautilus Action Configuration has been upgraded to v 3.0.5, so your howto is not up to date anymore. Especially in Natty/Unity it's vital to be able to search from context menu. 

GRTZ!
Am on 11.10, but same diff. - see screens, should get you going
(when entering a Mimetype or Basename, after typing press enter on keyboard to set, no mouse

---

### Post by rCXer on 2011-06-15
Ashrael, thanks for the PM.  I don't have Natty yet (sorry) but I'll try my best to help out.

mc4man did you get it to work?  If so could you write out detailed instructions on how you did it.  I'll add your instructions to the first post.

---

### Post by mc4man on 2011-06-16
> mc4man did you get it to work?

Sure - works fine on natty (NA 3.0.5) and on O (11.10) where I'm using a built NA 3.1.4 because there is no current repo package that works. 

I know many have complained about how 'complicated' the 3.X.X Na's are but they're not really once you get the idea. (though I did like the simplicity of the earlier versions

The 2 screens above show how I did your "Search Folder" action, as noted for mimetype - after entering I've found you need to press enter to set, not use mouse to 'click out'

The mimetype and basename work well, some of the others ones not at all, (or I've yet to understand them),  and i haven't yet seen if multiple mimetypes can be allowed per action (like for various audio files, ect.

Also exporting between 3.X and 2.x versions doesn't completely work the few times I've tried, sometimes close but not exactly correct
(and in 11.10 exporting is quite hit or miss at the moment

---

### Post by vanadium on 2011-06-30
I do not get it to work. With the parameters as indicated in your screenshot, gnome-search-tool always opens in Documents for me.

- edit - and it suddenly worked after I added the --hidden option and changed the Profile Label back to "Default profile" (to mach the screenshot exactly) ...

---

### Post by startling on 2012-01-25
I apologise in advance if this seems a silly response but I assure you it's meant to be helpful. While I like some things about Ubuntu and Unity it seems to me to be a bit immature in its development.

On Windows, Agent Ransack is a superb search utility that integrates into the right-click context menu of Explorer and it's fast too. I've tried other search options in Ubuntu but none of the ones I've tried work as well or as simply as Agent Ransack. Recently using Ubuntu's search it didn't find the file at all, but the same search in Agent Ransack found several files in seconds.

So my solution to this problem is to run Windows XP in a VirtualBox virtual machine and use Agent Ransack to search folders. I know this might seem crazy but I haven't found an alternative method in Ubuntu 11.10 with Unity - if anyone can tell me otherwise I'd be delighted.

---

### Post by Ashrael on 2013-04-26
@startling: I have completely removed Zeitgeist etc, because it slows my machine down too much. I use gnome-do to do all searches. Don't know if it beats your w*nd*ws alternative.

Still it would be nice to have a contect menu entry in 12.04.

---

### Post by startling on 2013-04-26
> **Ashrael said:**
> @startling: I have completely removed Zeitgeist etc, because it slows my machine down too much.

@Ashrael: I have removed Ubuntu because it slows my machine down too much! ;-) 

I've moved to Debian with XFCE and the speed increase is noticeable. Resources and CPU used is a lot lower. I'm really enjoying Debian/XFCE and I wish I had migrated away sooner. I'll always be grateful to Ubuntu and its developers but I think it's a shame the way Ubuntu seems to be heading. There seems to be a lot of non-optional bloat. What eventually made me make the move was that Ubuntu kept crashing (it was like using Win98 all over again!). I know there's Xubuntu, but my experience of Ubuntu changing so much over the last few years made me worry that something might happen there too, so I made the decision to abandon *buntu altogether.

---

### Post by startling on 2013-04-27
@Ashrael: 

P.S. I have heard that the developers of Zeitgeist warn users not to uninstall it. I guess because it's so tightly integrated into Ubuntu (just like the way a certain Redmond-based company does with its products!) that it might be a bad idea. I don't know if the crashes I kept getting on a daily basis were due to my removing Zeitgeist, but anyway that's when I thought, time to move and Debian looks the best fit. 

Have you noticed any system instability since removing Zeitgeist?

---

