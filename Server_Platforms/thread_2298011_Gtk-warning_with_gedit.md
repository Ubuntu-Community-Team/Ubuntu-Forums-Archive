---
title: "Gtk-warning with gedit"
date: 2015-10-08
forum: Server Platforms
---

### Post by c_xy on 2015-10-08
Hello,


We currently have Ubuntu 14.04 LTS server installed. Running it with an Lxde destkop environment.

We've run into this GTK warning whenever we are using gedit.

If we start typing in a gedit window, or save it, this output appears on the screen:

> (gedit:84652): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error: org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files




Is this simply a harmless bug or does this indicate a bigger problem? If it is just a big, is there a simple workround where this Gtk-warning can be suppressed? 

Any help is greatly appreciated.

Thanks,

c.

---

### Post by tgalati4 on 2015-10-08
I don't see it running MATE, which is based on Gnome2 when I run *pluma*, the *gedit* fork using MATE libraries.  I presume that since you are running lxde that you do not have all of the Gnome2/3 frameworks.  You can install the missing ones, or run an editor that was designed for lxde.

To supress it, you can send the error to the bit bucket:

```
gedit > /dev/null
gedit 2>/dev/null
gedit > /dev/null 2>$1
gedit 2>$1
```

Or some variation of that.  At least one of the above should hide the error messages.  I'm not running *lxde* or *gedit* so I can't test it directly.

---

### Post by c_xy on 2015-10-08
Thank you for your response.

I also have Ubuntu-mate installed as an alternative Desktop environment.


When I run gedit, type or try to save file in Ubuntu-mate, I get the same output:

> (gedit:89564): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files


Also, based on your suggestion

> [COLOR=#000000][FONT=Ubuntu Mono]gedit > /dev/null
[/FONT][/COLOR]gedit 2>/dev/null
gedit > /dev/null 2>$1 
[COLOR=#000000][FONT=Ubuntu Mono]gedit 2>$1[/FONT][/COLOR]

Is there a way to configure it (possibly in .bashrc or something else) where you don't have to add   "> /dev/null"   every time you call gedit?

Thanks,

c

---

### Post by vasa1 on 2015-10-08
Yes, you can make a small script to do so. I've done something similar to cut down on errors/messages/warnings for some programs that get posted in ~/.xsession-errors.

---

### Post by c_xy on 2015-10-08
vasa1,

Thank you for your response.

If you don't mind me asking, could you post an example of your script to where I could suppress the gedit warnings?

c

---

### Post by vasa1 on 2015-10-08
```
#!/bin/bash
mousepad 2>/dev/null
```

BTW, why did you go with gedit? If you weren't careful, you'd have pulled in quite a few GNOME "recommends".

---

### Post by tgalati4 on 2015-10-08
If you are running MATE, do you get the same messages when running *pluma*?  I'm not familiar with the error, so I can't recommend a specific library or service to add that will fix it.

---

### Post by c_xy on 2015-10-09
Thanks guys for  your suggestions.

If I try this:

> [COLOR=#000000]*gedit >/dev/null*[/COLOR]


In my .bashrc file, it automatically opens a gedit text window if I open a new terminal or source the .bashrc file.

Preferably, we just want to suppress the output wihtout having a window pop-up everytime or typing > /dev/null when ever using gedit.

I found the following link:


[http://askubuntu.com/questions/505594/how-to-stop-gedit-and-other-programs-from-outputting-gtk-warnings-and-the-like](http://askubuntu.com/questions/505594/how-to-stop-gedit-and-other-programs-from-outputting-gtk-warnings-and-the-like)

I used the second recommendation, and placed it in my .bashrc file:

> 

_supress() {

  eval "$1() { \$(which $1) \"\$@\" 2>&1 | tr -d '\r' | grep -v \"$2\"; }"
}

_supress gedit          "Gtk-WARNING\|connect to accessibility bus"



The above seems to help , although every time I close the gedit window, a few lines white space are produced. It is as if the above command/function suppresses any text printed out, but not the line space it would take up if printed.

We wanted to use gedit since we've used it with Ubuntu 10.04. I tried pluma a few times, but we prefer the code coloring, style, and setup of gedit better.

c

---

### Post by vasa1 on 2015-10-09
I mess with .bashrc as little as possible.

The code I gave was saved as a script in ~/bin and not added in .bashrc.

Since you mentioned server and LXDE I got the impression you were going for a light system. For most purposes, Geany (fewer dependencies) can do what Gedit does.

---

### Post by c_xy on 2015-10-11
still trying some things.

so far, the suppress code is the closest thing to normal usage without error output.


if I want to use pluma as an alternative, is there a way to comment multiple lines of code in pluma? There used to be a comment code plugin in gedit. But I don't see it in pluma. How does one comment multiple lines in pluma?

c

---

### Post by tgalati4 on 2015-10-11
Are you looking for tags such as this?

> <comment>This is some random text that I want to comment.</comment>

There is a tag plug-in that needs to be activated and then accessed through the sidebar, bottom tab.  You highlight a block of text and select comment tag.

---

### Post by c_xy on 2015-10-11
Thanks for the feedback.

I tried what you suggested.

I essentially want to do this:

Here is some code:


```
 

Example Code
Line Two
Line Three



```

Instead of typing a comment symbol (# sign for example) at the beginning of each line,

I want to have the ability to highlight the 3 lines above, and then comment out all three lines at the same time.

Once Commented it would look like this.

```
 

[COLOR=#0000ff]#Example Code
#Line Two
#Line Three[/COLOR]



```

This really helps when you have long lines of code.

In gedit, I would go to Edit and click Comment Code (or type Cntrl + M). And it would use the appropriate command symbol for specific language (bash, R, matlab, etc.)

Is this possible to do with pluma?

Thanks,

c

---

### Post by tgalati4 on 2015-10-12
No, *pluma* 1.8.1 (as found in Linux Mint MATE 17, based on Ubuntu 14.04) does not have native code comment (Control-M) capability.  However, there are some plug-ins to look at:

[http://wiki.mate-desktop.org/plugins](http://wiki.mate-desktop.org/plugins)

Specifically:  [https://github.com/yselkowitz/pluma-plugins/tree/master/plugins/codecomment](https://github.com/yselkowitz/pluma-plugins/tree/master/plugins/codecomment)

Haven't installed these or used these in *pluma*, so I don't know if they work the same way as in *gedit*.

---

