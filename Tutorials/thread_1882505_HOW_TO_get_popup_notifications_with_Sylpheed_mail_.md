---
title: "HOW TO: get popup notifications with Sylpheed mail client"
date: 2011-11-17
forum: Tutorials
---

### Post by MG&amp;TL on 2011-11-17
[SIZE="4"]_How to setup Sylpheed to get mail popups_[/SIZE]

[SIZE="1"]*Note: This tutorial assumes you are using LXDE and that you have already setup sylpheed so that you can receive email. Screenshots are provided at the bottom.*[/SIZE]

[SIZE="3"]1. Install the libnotify-bin package.[/SIZE] 

To do this:

*LXMenu -> Accessories -> LXTerminal*

And type the following in the box that appears:

```
sudo apt-get install libnotify-bin
```

And press [COLOR="Red"]RETURN[/COLOR]

Enter you password(you won't be able to see it), then press [COLOR="Red"]RETURN[/COLOR] again.

Once the text has stopped scrolling, and it looks like this:

```
user@computername:~$
```

you can close the window, and are ready to move on to the next step. Congratulations, the hardest part is over. :)





[SIZE="3"]2. Make sylpheed check for mail regularly.[/SIZE]

Open sylpheed. At the top menu bar, go to:

*Configuration -> Common preferences...*

And tick the first box (*Auto-check new mail every...*). Then adjust the time (in minutes) between checking for mail to your preference. Short times will increase CPU and internet usage, longer times won't retrieve mail as regularly. Click "Apply".

Sylpheed will now check for mail on a regular basis.






[SIZE="3"]3. Make a popup appear when new mail is  received.[/SIZE]

In the same window, tick "*Execute command when new messages arrived*"

In the "command" box, copy and paste this:

```
notify-send -i /usr/share/pixmaps/sylpheed.png "New Mail"
```

*-> TIP: You may change "New Mail" to a message of your choice, as long as you keep the quotes. You can also specify the absolute path of a different icon (instead of /usr/share/pixmaps/sylpheed.png), or omit the icon entirely (in which case, remove "-i" as well).*

Now click "Apply" again, then "OK". Send an email to yourself to test it. A box (like the Unity notifications) should appear in the top-right hand corner of your screen, with the sylpheed icon and "New Mail". It will disappear after a few seconds.

I hope this tutorial helps anyone who wants more prominent mail notifications in Lubuntu or another LXDE variant.

_**Credits:**_

[http://ubuntuforums.org/showthread.php?p=7790549]("http://ubuntuforums.org/showthread.php?p=7790549") --For the libnotify hint (found on google)

Amjjawad-[[URL="https://wiki.ubuntu.com/amjjawad"]https://wiki.ubuntu.com/amjjawad]("https://wiki.ubuntu.com/amjjawad")[/URL] --For getting me into LXDE in the first place.

Thanks, people!

---

