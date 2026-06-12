---
title: "Putting &quot;Ubuntu&quot; into my browser's user agent string"
date: 2011-11-23
forum: The Cafe
---

### Post by vasa1 on 2011-11-23
I use both Firefox and Chrome.
While I do have the updated Firefox that comes with the 11.10 install, I also have Aurora which I picked up directly from Mozilla.

With version 8 of Firefox, **Ubuntu** is now part of the user agent string. I suppose this is to help identify Firefox that has been downloaded from Canonical's repos.

**Ubuntu** is obviously missing in the user agent string of versions downloaded direct from Mozilla. There's just the generic **Linux**.

In case one wants to incorporate Ubuntu in the string, the method is described in [this]("http://johnbokma.com/mexit/2004/04/24/changinguseragent.html") old but still valid link.
So now my new string look like this:
Mozilla/5.0 (**Ubuntu**; X11; Linux i686; rv:10.0a2) Gecko/20111113 Firefox/10.0a2

I want to do the same for Chrome which I got (and update) from [http://dl.google.com/linux/chrome/deb/stable](http://dl.google.com/linux/chrome/deb/stable).

Running```
google-chrome --user-agent="Mozilla/5.0 (X11; Linux i686) AppleWebKit/535.2 (KHTML, like Gecko) Ubuntu/11.10 Chrome/15.0.874.121 Safari/535.2"
``` from the terminal works. But could someone help me make a "launcher" so I don't have to go the terminal route?

---

### Post by Elfy on 2011-11-23
Thread moved to The Community Cafe.

---

### Post by Copper Bezel on 2011-11-23
It probably won't do any good, because nothing is going to respond to that string. It's just going to be treated as Chrome / Linux.

You can, however, copy google-chrome.desktop from /usr/share/applications to ~/.local/share/applications, then open it with gedit and add the user agent switch to the exec line. This is a useful method for any switches you want to apply to applications by default on launch (and will apply to any GUI method of launching them.)

"Ubuntu" is probably included in the Firefox user agent string for internal reasons, such as to gauge Ubuntu usage. I can't imagine many other uses (such as rendering compatibility, which wouldn't be affected, or to distinguish Debian from other package managing systems to provide the correct software downloads, which sites generally already do somehow, except when they are terrible, like Adobe's or IBM's. But that's another issue entirely. = D)

---

### Post by ice60 on 2011-11-23
i've never used chrome so i don't know about this extension. maybe it will work.
[http://spoofer-extension.appspot.com/](http://spoofer-extension.appspot.com/)

user agent strings can be used for tracking, but that doesn't seem to bother most people.
[http://panopticlick.eff.org/self-defense.php](http://panopticlick.eff.org/self-defense.php)

you can use http proxies like privoxy to change/hide your user agent too.

---

### Post by vasa1 on 2011-11-23
> **Copper Bezel said:**
> It probably won't do any good, because nothing is going to respond to that string. It's just going to be treated as Chrome / Linux.
That's okay. The point you mentioned later is the relevant one.

> You can, however, copy google-chrome.desktop from /usr/share/applications to ~/.local/share/applications, then open it with gedit and add the user agent switch to the exec line. This is a useful method for any switches you want to apply to applications by default on launch (and will apply to any GUI method of launching them.)

Thanks! I'll take a look at it.

> "Ubuntu" is probably included in the Firefox user agent string for **internal reasons, such as to gauge Ubuntu usage**...
That's exactly my point. I didn't want my browser to be without **Ubuntu** in the string just because I got it "direct" and not from the Ubuntu Software Center.

---

### Post by vasa1 on 2011-11-24
> **Copper Bezel said:**
> ...
You can, however, copy google-chrome.desktop from /usr/share/applications to ~/.local/share/applications, then open it with gedit and add the user agent switch to the exec line. This is a useful method for any switches you want to apply to applications by default on launch (and will apply to any GUI method of launching them.)
...

I couldn't get that ^^^ to work but I guess it's not a big deal. If Canonical would like all Ubuntu users to have the option of including "Ubuntu" in their browsers' user agent strings, irrespective of where the browser comes from, they may come up with something.

---

### Post by vasa1 on 2011-11-27
Couple of mentions of the user agent string over here:
[http://www.omgubuntu.co.uk/2011/11/dare-to-be-different-ubuntus-popularity-is-not-declining/](http://www.omgubuntu.co.uk/2011/11/dare-to-be-different-ubuntus-popularity-is-not-declining/)

---

### Post by Copper Bezel on 2011-11-27
Yes, good point. It's odd that it didn't work for you, though. I just made the addition to the .desktop, like so:

```
Exec=/opt/google/chrome/google-chrome %U --new-window --user-agent="Mozilla/5.0 (X11; Linux i686) AppleWebKit/535.2 (KHTML, like Gecko) Ubuntu/11.10 Chrome/15.0.874.121 Safari/535.2"
```

And _[What's My User Agent]("http://whatsmyuseragent.com/")_ reports

> Your User Agent: Mozilla/5.0 (X11; Linux i686) AppleWebKit/535.2 (KHTML, like Gecko) Ubuntu/11.10 Chrome/15.0.874.121 Safari/535.2

as expected. (Thanks, by the way.)

---

### Post by vasa1 on 2011-11-27
> **Copper Bezel said:**
> ... It's odd that it didn't work for you, though. ...

```
Exec=/opt/google/chrome/google-chrome %U --new-window --user-agent="Mozilla/5.0 (X11; Linux i686) AppleWebKit/535.2 (KHTML, like Gecko) Ubuntu/11.10 Chrome/15.0.874.121 Safari/535.2"
```
...

I'm afraid I'm going to need serious hand-holding here :( 

1. What permissions should google-chrome.desktop have in its new location (.local/share/applications)? Is [FONT="Courier New"]-rw-r--r--[/FONT] okay?
2. I could open this copied file using:
```
gksudo gedit .local/share/applications/google-chrome.desktop
```
But where do I stick your code?
My file has 222 lines, including comments.
There are **three** occurrences of lines starting with **Exec=** 
line 108: Exec=/opt/google/chrome/google-chrome %U
line 168: Exec=/opt/google/chrome/google-chrome
line 221: Exec=/opt/google/chrome/google-chrome --incognito

Did you change all three or just the first one?

Edit: I changed just the first one. Now, I have:
```
Your User Agent: Mozilla/5.0 (X11; Linux i686) AppleWebKit/535.2 (KHTML, like Gecko) Ubuntu/11.10 Chrome/15.0.874.121 Safari/535.2
```

So Thank You :)

---

### Post by Copper Bezel on 2011-11-27
Yeah, sorry, I suck. = ) I'm glad it worked, though! = ) 

To belatedly answer your questions: 

.desktops in .local should be owned by you and don't need to be marked executable. I just drag and drop them as myself in Nautilus.

The exec line on line 108 is the ordinary launch. The other two are Ayatana shortcuts for the right-click menu of the Unity Launcher, New Window and New Incognito Window. (Nice of the Chromium folks to think of us Ubunteros.) However, note that the user agent is set for the browser session, not the individual window. Thus, using the quicklist items for a new or incognito window will retain the correct user agent string.

---

### Post by vasa1 on 2011-11-27
> **Copper Bezel said:**
> ...
```
Exec=/opt/google/chrome/google-chrome %U **--new-window** --user-agent="Mozilla/5.0 (X11; Linux i686) AppleWebKit/535.2 (KHTML, like Gecko) Ubuntu/11.10 Chrome/15.0.874.121 Safari/535.2"
```
...

I've marked the thread "Solved" but I'd like to know about why you (and I) included the --new-window switch.

Edit: I'm digesting your last post :)

---

### Post by Copper Bezel on 2011-11-27
Oh, sorry about that - I wasn't thinking and just dropped the whole line in unedited. You can remove it. I use a lot of workspaces, and I occasionally use the Gnome Shell search for Wikipedia and Google searches, as well as Chrome as my default .pdf viewer, all of which adds up to adding --new-window to my exec line for Google Chrome. = )

---

### Post by vasa1 on 2011-11-27
> **Copper Bezel said:**
> ...
.desktops in .local should be owned by you and don't need to be marked executable. I just drag and drop them as myself in Nautilus.

Hmmm... I've still to get used to Control+[drag-and-drop] in Nautilus in order to copy files.
> 
The exec line on line 108 is the ordinary launch. The other two are Ayatana shortcuts for the right-click menu of the Unity Launcher, New Window and New Incognito Window. (Nice of the Chromium folks to think of us Ubunteros.) However, note that the user agent is set for the browser session, not the individual window. Thus, using the quicklist items for a new or incognito window will retain the correct user agent string.

So I guess we're all good until the next Chrome update! :D

---

### Post by vasa1 on 2011-11-27
> **Copper Bezel said:**
> Oh, sorry about that - I wasn't thinking and just dropped the whole line in unedited. You can remove it. I use a lot of workspaces, and I occasionally use the Gnome Shell search for Wikipedia and Google searches, as well as Chrome as my default .pdf viewer, all of which adds up to adding --new-window to my exec line for Google Chrome. = )

Okay, I'll remove it as my usage is pretty simple. Thanks!

---

### Post by vasa1 on 2011-11-27
This maybe quite ironic but there's been an oldish report of a Google site refusing to recognize a Chromium browser from Ubuntu!
[http://code.google.com/p/chromium/issues/detail?id=67332](http://code.google.com/p/chromium/issues/detail?id=67332)

Something to keep in mind!

---

### Post by vasa1 on 2011-11-28
More mention: [http://randall.executiv.es/perceptionisreality](http://randall.executiv.es/perceptionisreality)

---

### Post by Copper Bezel on 2011-11-29
Good point. = ) Seriously, anything to kill this Mint silliness (assuming that they don't just use Ubuntu's Firefox wholesale, including the modified user agent string.)

> So I guess we're all good until the next Chrome update! :D
Damn, I hadn't thought of that. = P I guess it's not *that* much an inconvenience.

---

### Post by vasa1 on 2011-11-29
> **Copper Bezel said:**
> ...
Damn, I hadn't thought of that. = P I guess it's not *that* much an inconvenience.

Not at all, now that I know what to tweak :)

But ... is the stuff below an easier way?

If one has alacarte (Main Menu) installed,
[list][*]click on Internet in the left panel
[*]click on Chrome in the middle panel
[*]click on properties in the right panel
[*]edit the command line in the pop-up window to make it look like what we want[/list]

I haven't tried it and would like your opinion first!

---

### Post by Copper Bezel on 2011-11-29
Yeah, you're right, that is more convenient. I have the habit of editing .desktop files manually for some reason, but Alacarte seems the better option.

---

