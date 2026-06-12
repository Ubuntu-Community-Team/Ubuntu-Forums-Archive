---
title: "Ubuntu 11.04"
date: 2011-05-14
forum: The Cafe
---

### Post by LolxD on 2011-05-14
I didn't get good idea for title, but there should be an Ubuntu 11.04 Human-theme Edition or something like that for Human theme likers, like me, because i dont like the new theme in 10.04, 10.10 and 11.04. So is someone made an Ubuntu 11.04 with Human Theme, and if not, is it possible to get the Human theme for 11.04. This is not an problem, it's just an suggestion/question. =)

---

### Post by JRV on 2011-05-14
That is what I wanted too, Here is what I did:
```
sudo apt-get install human-theme

```
 
---------------------------------------------------------------------------------
  
To disable the global menus remove the indicator-appmenu package. 
Install the indicator-appmenu package to re-install them.

---------------------------------------------------------------------------------

To remove the Applications, and Files icons from the bottom of the launcher bar:

   gksudo gedit /usr/share/unity/places/*.place

Add the following line to the bottom of the "[Entry:Files]" in both files:
  
  ShowEntry=false

---------------------------------------------------------------------------------

To disable the overlay scrollbars:
```

   sudo apt-get remove overlay-scrollbar
   sudo su
   echo "export LIBOVERLAY_SCROLLBAR=0" > /etc/X11/Xsession.d/80overlayscrollbars

```
to re-install the overlay scrollbars:
```

   sudo apt-get install overlay-scrollbar
   sudo rm /etc/X11/Xsession.d/80overlayscrollbars

```
---------------------------------------------------------------------------------

To stop a window from maximizing when dragged to the top of the screen:

   Open CompizConfig Settings Manager
   Uncheck the "Grid" in the "Window Management" category

---------------------------------------------------------------------------------

to remove me-menu:
```

   sudo apt-get remove indicator-me

```

[IMG]http://scc.net/~jrv/natty.png[/IMG]

---

### Post by RJ12 on 2011-05-14
Wow! Nice!!

---

### Post by madjr on 2011-05-14
why not just use the radiance theme?

is very similar to the old human theme, but is better integrated.

also many new themes coming out soon.

---

### Post by Oxwivi on 2011-05-14
My eyes burn! THEY BURN!

---

