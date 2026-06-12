---
title: "[lubuntu] Indicators applet width workaround"
date: 2014-04-15
forum: Tutorials
---

### Post by doctorjellyface on 2014-04-15
Hi all.

First post, and I'll like to post something nice as a greeting.

**Note:** this post is meant for use in Lubuntu and was tested only in Lubuntu 12.04 (actually it was Ubuntu with lubuntu-desktop installed). I am not aware if it can be used in other distors.

If you use the indicators applet in Lubuntu on LXPanel, and have a small screen, you may have found out that the applets are WAY to far away from each other.

I searched quite a lot for a solution. Many people even said that it hasn't got a solution. But I found one.

It looks like it's a problem with the theme you're using (probably, not sure, but looks like it).

**SOLUTION** (/workaround)**:**

1: Create a file in your home folder called [B].gtkrc-2.0
[/B]2: Check that the path to the file is **./.gtkrc-2.0** (just for safety, in case you misunderstood me)

If there already is a file called **.gtkrc-2.0**, proceed to step **6**.

3: Open the file in your favourite text editor (gedit, leafpad)
4: Copy+paste this text into it:

```
style "mythin"
{
 xthickness = 0
 GtkMenuItem::horizontal-padding = 2
}
 widget "*fast-user-switch*"       style "mythin"


```

5: Restart LXPanel by typing

```
lxpanelctl restart
```

into the terminal, and if that doesn't work, log out and back in, AND IF THAT doesn't work, restart your system.
If it still doesn't work, I have no idea what's wrong. Try going back to step 1 and read more carefully.

You may want to play with the numbers to achieve better results. Post your configuration here if you got something better.


**Step number 6:**

If you already have a .gtkrc-2.0 file there, and it's empty, don't fret and go back to step 3.

**If it is not empty**, you've got a problem. The file wasn't on my system when I tried this workaround, so I didn't have a problem.
But you might want to just copy+paste the code there, without deleting what is there already, and see what happens. Please post if something interesting happens :)


And that's all! Enjoy the new, slick and **thin** indicators applet!

Credits to [eros2]("https://launchpad.net/~eros2") for the comment [#92]("https://bugs.launchpad.net/indicator-applet/+bug/527267/comments/92") on [Bug #527297]("https://bugs.launchpad.net/indicator-applet/+bug/527267") on the [indicator-applet Launchpad page]("https://launchpad.net/indicator-applet") for the solution. It was quite hard to find so I put it here.

Enjoy!

PS: Maybe, if you use the indicators applet, you don't have it very long and it isn't using much space. You may be missing packages with all the indicators (clock, session menu, messages, etc.) In that case you may want to install these packages that are missing:

```
sudo apt-get install indicator-application-gtk2 indicator-datetime-gtk2 indicator-messages-gtk2 indicator-session-gtk2 indicator-sound-gtk2
```

And then, tick everything in the indicators applet settings menu (right click on it, you'll find it).

Source: [http://namakutux.blogspot.com/2012/07/how-to-use-install-indicator-applet-on.html]("http://namakutux.blogspot.sk/2012/07/how-to-use-install-indicator-applet-on.html")

---

