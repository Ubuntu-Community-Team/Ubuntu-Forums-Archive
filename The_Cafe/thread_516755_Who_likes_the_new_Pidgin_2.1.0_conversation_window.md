---
title: "Who likes the new Pidgin 2.1.0 conversation window?"
date: 2007-08-03
forum: The Cafe
---

### Post by happy-and-lost on 2007-08-03
Just upgraded to Pidgin 2.1.0 to find that my conversation windows (in MSN at least) have had a facelift.

I, personally am horrified by the new layout. Do any of you prefer it?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=39731&stc=1&d=1186171718[/IMG]

---

### Post by Nekiruhs on 2007-08-03
What did it look like before?

---

### Post by xen on 2007-08-03
Looks great to me, now all I'm after is iChat style speech bubbles!

What GTK theme is this?

---

### Post by happy-and-lost on 2007-08-03
Good question. The same as Gaim, just with Tango-style icons. Will find a screenshot...

The particular ugliness I'm referring to is the waste of space where the contact's email address and display pic now is.

(Edit, GTK is [MurrinaGraphiteGentle]("http://www.gnome-look.org/content/show.php/MurrinaGraphiteGentle?content=48237"))

---

### Post by igknighted on 2007-08-03
> **xen said:**
> Looks great to me, now all I'm after is iChat style speech bubbles!

What GTK theme is this?

Kopete does these beautifully, but I am sure there is a theme to do it in pidgin somewhere.

---

### Post by PrimoTurbo on 2007-08-03
Old one looks like this, I think newer is just cleaner?..
[img]http://img352.imageshack.us/img352/6789/screenshotjessicazg0.png[/img]

---

### Post by M$LOL on 2007-08-03
Are there .debs for Pidgin 2.1.0?

---

### Post by ftmichael on 2007-08-03
Yep.  See [http://www.getdeb.net/release.php?id=1209](http://www.getdeb.net/release.php?id=1209)

---

### Post by fct on 2007-08-03
I get the nickname at the top of the tab and then the e-mail right below it, with the same font size (not smaller to save some space). The photo is now small as hell. There are labels like "Font" right to the side of the font icon...

And it has some really weird design decisions. When you click on "Font" you get a *checkbox* for "Font style" that launches a font selection dialog! You hit the smiley icon with the "insert" label and then you get a pop-up menu to insert a smiley, an image or a link...

Plus there are no new msn or yahoo features. Actually, the changelog is laughable for a 2.0.x-2.1.0 transition:

```

        libpurple:
        * Core changes to allow UIs to use second-granularity for scheduling.
          Pidgin and Finch, which use the glib event loop, were changed to use
          g_timeout_add_seconds() on glib >= 2.14 when possible.  This allows
          glib to better group our longer timers to increase power efficiency.
          (Arjan van de Ven with Intel Corporation)
        * No longer linkifies screennames containing @ signs in join/part
          notifications in chats
        * With the HTML logger, images in conversations are now saved.
          NOTE: Saved images are not yet displayed when loading logs.
        * Added support for QIP logs to the Log Reader plugin (Michael Shkutkov)

        Pidgin:
        * Ensure only one copy of Pidgin is running with a given configuration
          directory.  The net effect of this is that trying to start Pidgin a
          second time will raise the buddy list.  (Gabriel Schulhof)
        * Undo capability in the conversation window
        * The formatting toolbar has been reorganized to be more concise.
        * A new status area has been added to the top of conversations to
          provide additional detail about the buddy, including buddy icon,
          protocol and status message.
        * Show idle times in the buddy list as days, hours, seconds

        Finch:
        * There's support for workspaces now (details in the manpage)
        * There's a new custom window manager, Irssi
        * Some improvements for tab-completion, tooltip and the password entries
        * Some bugs regarding search results fixed
        * A new DBus-script to create a docklet for finch
        * Support for showing empty groups in the buddy list (Eric Polino)

```

Still no webcam or voip support, the webpage won't show the news of the latest releases (actually the news page is broken since they migrated the webpage), the distributed version control system they use is harder to use than better alternatives like git, searches in their trac-based webpage are slowww...

I'm frankly disappointed with this release, that is still as unstable for me as 2.0.2 was. And the developers aren't making it easy to help.

So I'm still forced to use amsn to communicate with my friends using windows and I'll probably switch to telepathy when it's usable enough, cause pidgin's future doesn't look that bright right now.

---

### Post by Depressed Man on 2007-08-03
I think it's allright. I don't change my font that often and I know most of the smilies I use so I just got rid of the formating bar (you can turn it off in the  chat window). So I was just left with the username and the picture on top which is tolerable for me (not sure if it's better though).

---

### Post by PrimoTurbo on 2007-08-03
On second thought it does sound worse, I realize they added text to the menu for no reason and removed the icons?...

---

### Post by BarfBag on 2007-08-03
That picture doesn't look half bad, but it looks absolutely awful on my PC.  The text box isn't even tall enough to type.

---

### Post by daleus on 2007-08-07
Sorry to dig up a thread started a few days ago, but Does anyone know how to remove this horrible theme and re-enable the large in-chat picture?

---

### Post by loopeando on 2007-08-07
The new conversation windows is awful.

Bring back the old one!

---

### Post by jrseney on 2007-08-07
Yes, I agree, the new windows waste space, why do I need to see a screen name twice? Once in a tab, and once below? Just doesnt make sense... The relocating of the buddy icon makes the buddy icons impossibly small. The text menus and formating dropdowns take more mouse movement and clicks. Also, I can't see if im currently italic, bold or underlined while typing. Terrible terrible  update....:sad:

Despite the dependency of a web browser, Meebo is feeling like it may be a viable alternative if things with pidgin don't improve...

---

### Post by Old Pink on 2007-08-07
Old one was much nicer. 

Well, [**this**]("http://www.mbhoy.com/01-08-2007/pidgin-210/new-pidgin-210-toolbar") is an improvement. [**This** ]("http://www.mbhoy.com/01-08-2007/pidgin-210/new-pidgin-210-information-bar")is a waste of space, in MSN, but quite nice in IRC.

---

### Post by ounn on 2007-08-08
I do not agree width you. I really prefer the new interface. I think that the old avatar was a waste of space. Now it took much less space. I think the problem is on the tabs not in the new area.

---

### Post by Polygon on 2007-08-08
if they could somehow make it so that i can have the large avatar back, it would be nice. The only real thing that i dont like....

and having the name in the tab and the name in the window is only really useful for MSN or Jabber, since the name in the window is the email address.

---

### Post by smartboyathome on 2007-08-08
I am glad I did not upgrade yet! Sounds like the new version bombed.

---

### Post by Polygon on 2007-08-08
it doesnt bomb. just the UI got tweaked a bit, and even though i prefer to have a large avatar, the new message UI is perfectly usable.

there were also the usual amount of bug fixes in this version to so... yeah

---

### Post by Bou on 2007-08-08
> **jrseney said:**
> Yes, I agree, the new windows waste space, why do I need to see a screen name twice? Once in a tab, and once below?

Well, the tab is supposed to disappear when there is only one open conversation so it should look something like this:

[IMG]http://img130.imageshack.us/img130/9194/pantallazovo5.png[/IMG]

Only it will have to wait for 2.2, I think. But it's a good idea IMO.

About the new buttons, you gotta love them. They're just much cleaner this way.

---

