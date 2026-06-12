---
title: "HOWTO: Center / Re-position Windows"
date: 2006-06-04
forum: Tutorials
---

### Post by _simon_ on 2006-06-04
Have you noticed how some application windows will open with strange positioning, e.g. off to the left? Want to change that? Well now you can... 

In this example I will use Firefox (this also works for Swiftfox without changing any code)

First, install "devilspie", this is available via Synaptic.

> 
**Devilspie**
Find windows and perform actions on them
This tool will find windows as they are created and perform actions
on them, such as resizing, moving to another workspace, or pinning
them to all workspaces.


Once installed, go to your home directory and create a new hidden folder called .devilspie

In the folder you just created, create a document and call it Firefox.ds

Open up Firefox.ds with a text editor and paste the following:

```

(if
    (matches (application_name) "Firefox")
    
       (geometry "+120+0")      
)

```

The first number is the X axis (horizontal position) and the second is the Y axis (vertical position).

The figure I am using (+120) is based on a screen resolution of 1280x1024 so you may need to change this if you find it's not perfectly centered.

Now to test it!

Open up a terminal window.

Type: 

```
devilspie
```

If you already have an un-maximised/un-minimised Firefox/Swiftfox window open you should see it reposition itself. if not, just open one up and it should open in it's new position rather than to the left of the screen.

Once you are happy with the x axis position you'll want to add it to startup.

System -> Preferences -> Sessions -> Startup Programs -> Add ->> devilspie

Logout and back in to test - all should work fine.

If you want to use positioning on more than one window then simply create another .ds file for it.

There are of course more uses for devilspie, please see the wiki here:

[https://wiki.ubuntu.com/Devilspie?highlight=%28devilspie%29](https://wiki.ubuntu.com/Devilspie?highlight=%28devilspie%29)

---

### Post by NoVista on 2007-09-12
Well I realize this is an old post, but this works great!

I do have a java program that it won't work on, (the prog tries to open in the custom spot i designated, but flickers and goes back to its default).

This was on Feisty.

---

### Post by Yuzem on 2011-08-18
Ok, this post is old but just in case someone is interested, you can center the window with (I am using it with mplayer):

```
(if
    (matches (application_name) "MPlayer")
       (center)
)
```

---

