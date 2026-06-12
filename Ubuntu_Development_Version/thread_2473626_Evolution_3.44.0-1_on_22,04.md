---
title: "Evolution 3.44.0-1 on 22,04"
date: 2022-04-08
forum: Ubuntu Development Version
---

### Post by cigtoxdoc on 2022-04-08
Evolution will not show text of messages and allow text to be added to new messages until Evolution is started with:

 $ WEBKIT_DISABLE_COMPOSITING_MODE=1 evolution

This workaround came from Milan on [email]evolution-list@gnome.org[/email]

John

---

### Post by DuckHook on 2022-04-08
We seem to have posted regarding the same issue.

For a more general explanation/approach, please see my thread: [https://ubuntuforums.org/showthread.php?t=2473639](https://ubuntuforums.org/showthread.php?t=2473639)

---

### Post by cigtoxdoc on 2022-04-08
Thank you.  My understanding of the comments on Launchpad is that the problem with webkit is not going to be fixed in the near future.  What would be really helpful is a "program" (script?) that could be assigned an icon that one could click and get evolution w/o use of terminal.  Once you play with terminal after evolution is lauched, it makes the problem with evolution reappear.

---

### Post by DuckHook on 2022-04-08
As I read it, it will be fixed, but in a roundabout way. It is possible that they will revert the changes that were the cause of the problem, or they will wait for the upstream mesa devs to address the problem at their end.

However, I don't think the devs will just leave the problem unfixed. Flagging the bug as "high" means that they are taking it very seriously. Moreover, when apps like Evolution, Epiphany and even Yelp are broken because of this problem, it clearly has to be fixed. These are major apps and the devs will not release a LTS that breaks such apps.

We just have to be patient while they put their heads together and find a solution.

In the meantime, we can use workarounds. You can create a simple script that will launch Evolution with the proper preset (please note that I don't use Evolution, so you might need to adjust the following to Evolution's proper filename):
```
#!/bin/bash

# Starts Evolution with webkit compositing off.
WEBKIT_DISABLE_COMPOSITING_MODE=1 evolution
```
Save the file under a made&#8209;up name like&#8212;ohh&#8212;*revolution* (I hope that's not too cute), and place it in your local ~/bin directory so that it can be found on your local path (it's where I keep all of my local scripts). Remember to make it executable.

Now you can invoke the script with <Alt> <F2> &#8594; revolution

For further convenience, [create a .desktop file for it]("https://www.howtogeek.com/445303/how-to-create-desktop-shortcuts-on-ubuntu/"), place this file in ~/.local/share/applications and you can add the resulting "app" icon to whichever launcher you use. If vanilla Ubuntu, you would be using Gnome's. Just remember to call the new "app" revolution (instead of evolution, which would confuse the OS), and you are up and running again.

BTW, it is possible to free up your Terminal session by running evolution in the background:
```
WEBKIT_DISABLE_COMPOSITING_MODE=1 evolution >/dev/null 2>&1 &
```&#8230;which will launch Evolution, send all terminal output/error messages to /dev/null and then push it to the background, thus freeing up your terminal. This has the major drawback that exiting your terminal will kill Evolution.

Over the years, I've found that the script + <Alt> <F2> method is best.

EDIT: Further thought:

Webkit *will* get fixed. When it does, Evolution will work again. When that happens, it's a good idea to delete all of the above workarounds just for purposes of good computing hygiene. Not a good idea to keep dead scripts laying around. Over the years, we forget what they are for and they serve as unnecessary cruft that increases attack surface.

---

