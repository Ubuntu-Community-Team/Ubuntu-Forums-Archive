---
title: "editing of application menu in ubuntu studio/xfce sort of nightmarish"
date: 2014-07-16
forum: Ubuntu Studio
---

### Post by a-you on 2014-07-16
I recently installed ubuntu studio trusty 64 bit from scratch, overwriting the install of quantal I had been using.

Before I installed  trusty I deleted many .desktop files. I did that because editing the "Applications Menu" with alacarte had gotten to be a very slow and labor intensive process, mostly because over the last couple of years I had added and/or removed menu entries and so there were *many* that were by now simply disabled but taking up space in the alacarte editor. Yes, I'm sure I could have deleted those launchers in alacarte, but at the time(s) it was unclear what could be deleted without trashing some other part of the menus, so instead I always just unchecked the items that I didn't want displayed.

Unfortunately now I  forget from where I deleted those .desktop files!

I had the foolish notion that I'd  start from scratch. But editing with alacarte can be painfully sluggish.

Meanwhile menulibre worked one time, then crashed the  next time I tried to use  it, now it refuses to even launch. If I try to  launch it by typing  menulibre into the terminal window then these error  messages return:
```
** (menulibre:4630): WARNING **: Couldn't connect to accessibility  bus: Failed to connect to socket /tmp/dbus-Hnd6kiixZm: Connection  refused
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 14: reading  configurations from ~/.fonts.conf is deprecated. please move it to  /home/<my_user_name>/.config/fontconfig/fonts.conf manually **
ERROR:/build/buildd/gnome-menus-3.10.1/./libmenu/gmenu-tree.c:4022:preprocess_layout_info:  assertion failed: (!directory->preprocessed) Aborted (core  dumped)
```
Restarting does no good, neither does purging and then reinstalling  menulibre. Not only that but menulibre rearranged the menus in a way  that they're clearly screwed up (to try to describe how would take too  long and isn't too relevant I don't think anyway). It's clear that it  was the test I made of trying menulibre the first time that rearranged  the menus too.

[update:] I tried removing ~/.config/menus/xfce-applications.menu and  that allowed both alacarte and menulibre to launch, also alacarte's  button to restore the stock menus seems to have worked after removing  that. But it seems that making any sort of change using  menulibre  causes a new ~/.config/menus/xfce-applications.menu to be  created and  at the same time causes menulibre not to run next time one  tries to  launch it.

Learning to comprehend the whole menus-and-.desktop specification (with the thought of editing menus with a text editor) looks like a career move (ie way too much to get into).

Look, I don't mean to sound ungrateful. I adore ubuntu studio when it's finally up and running and totally configured. Honestly too I don't think this is in any way an ubuntu studio problem specifically. I think it's at least broad enough that it affects anybody that's using xfce to say the least. Maybe it's broader than that---and that's why I'm ranting. Because in that case it seems to me that shouldn't people that are paid employees of Canonical be dealing with a very basic question like menu editing?? Or am I wrong? Since I've not used unity I have no way to comment on that; maybe it's totally solved so long as one uses unity. But at the moment I'm finding this last(???) step in the install of trusty to be frustratingly hard.

There's gotta be some relatively simple way to edit menus!! Has anybody out there somehow solved this? Many thanks in advance if so!!

[update:] I added the PPA for menulibre and upgraded that but still the same issues.

I'm wondering if it may be at least in part because I've somehow got a mix of gnome and xfce when it comes to menus? It might be so, because /home has gone through versions of ubuntu studio from lucid to natty to quantal to now trusty, and it may well be that parts of the desktop are still based on gnome?? This is sheer speculation on my part here. And even if so I would not want to get into starting from scratch with that.

If this thread is coming across as just a rant then I'll gladly delete it, with apologies. But too it's hard to believe that I'm the only one with this particular issue...

---

### Post by jejeman on 2014-07-16
For 14.04 I've edited menus with provided Menu application. My guess its alacarte. No toruble at all.
Desktop files are located in ~/.local/share/applications/ if you need to add some.

---

### Post by a-you on 2014-07-16
Yes that's alacarte.

I'm guessing that you were not making major changes. Or that unfortunately I'm am ;-). Because at the moment I'm seeing many items in the most bizarre locations. In fact there are 3 menus called "Unused Menu," all 3 full of lots of items. It's totally wacky.

And re ~/.local/share/applications/, here's for example one small part of this odd puzzle: if I create a new menu item with alacarte no desktop file appears in that location. And I'm certainly not running the editor as root and they're not appearing in /usr/share/applications either (I even checked just to be sure). So I wonder where those items are being created.

...oh, I think I just answered that. Maybe this information is useful to somebody else dealing with this: it creates files called eg "alacarte-made-12.desktop"

Anyway thanks a lot for commenting

---

### Post by jejeman on 2014-07-16
> I'm guessing that you were not making major changes.
> it creates files called eg "alacarte-made-12.desktop"Exactly.

---

### Post by a-you on 2014-07-17
Btw do you happen to know what other files are involved in menus?? I mean, in addition to the .desktop files? I see that there's ~/.config/menus/xfce-applications.menu but are there any others that I should be aware of? (Thanks)

---

### Post by autumnus- on 2015-04-05
**update:** it turns out once you survive the first bug, more of them show up, like everything that goes out of a menu folder and then back into the folder will vanish from menu altogether etc... 
looks like our best bet is still sticking with the default menu editor. :(

------

you can use menulibre. it will just involve some text editing after the edit. :) 

1) do your menu editing.
2) open ~/.config/menus/xfce-applications.menu in your favorite file editor
3) go to the end of the file. last 2 lines will be like this: 
     ```

    </Layout>
</Menu>
```

4) add the DefaultMergeDirs tag like this:

    ```

    </Layout>
    <DefaultMergeDirs />
</Menu>
```

5) save the file. You will have to do this modification every time after editing the menu with menulibre unfortunately. 

Somebody already filed a bug report with menu libre about this so it will probably get fixed at some point. [https://bugs.launchpad.net/menulibre/+bug/1430571](https://bugs.launchpad.net/menulibre/+bug/1430571)

I hope this helps.

---

### Post by a-you on 2015-04-15
Thanks [**[COLOR=#000000]autumnus-[/COLOR]**]("http://ubuntuforums.org/member.php?u=1977645") :-). I had ultimately just gone back to using alacarte and now that I have the menus like I want them the occasional mod is not a big deal. But it's nice that you post that because I do think that if one wants to make large changes it's hard to do with alacarte.

---

