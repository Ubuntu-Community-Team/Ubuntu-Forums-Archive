---
title: "VLC, how come it wouldnt work right in 12.10?"
date: 2012-08-22
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by chrissy.millichamp on 2012-08-22
Every time I play something with VLC, and I try to go in the playlist tab it wouldn’t work. And it eventually crashes and leads all my window tops to disappear. What can I do to fix these issues?

---

### Post by mc4man on 2012-08-22
See here for link to bug & how to fix opening vlc from Dash, launcher or a menu. -  as in edit it's .desktop, pick option 1 or 2
[http://ubuntuforums.org/showthread.php?t=1988663](http://ubuntuforums.org/showthread.php?t=1988663)

**After editing the .desktop you must** >
Open home folder, find .local/vlc & delete this file
"vlc-qt-interface.conf"

---

### Post by mc4man on 2012-08-22
**Additionally** to above - 
To 'fix' using vlc from a terminal - 
Open home folder, create a file named this 

```
.bash_aliases
```
Inside place this line
```
alias vlc='export LIBOVERLAY_SCROLLBAR=0 && vlc'
```

or to fix & remove global menu 

```
alias vlc='export QT_X11_NO_NATIVE_MENUBAR=1 LIBOVERLAY_SCROLLBAR=0 && vlc'
```

Remember to delete that .conf file before restarting vlc after fixing...

---

### Post by chrissy.millichamp on 2012-08-22
It wont work.... I even tried to reinstall it...

---

### Post by chrissy.millichamp on 2012-08-22
Why is there such a problem with vlc's playlist?

---

### Post by effenberg0x0 on 2012-08-22
> **chrissy.millichamp said:**
> Why is there such a problem with vlc's playlist?

You mean, programmatically? As in "- What are the specific block/lines of code in VLC's source code that cause a crash in the Window Manager and should then be patched"?

If so, I don't think anyone took the time to find it yet. But you can search Ubuntu wiki for "apport-retrace" or "debugging with gdb". Once you install the debugging symbols package, you can set breakpoints in VLC, step the program up to the break and then associate the crash output to specific functions in VLC's source. With that info in hands you can post a detailed bug report and even suggest a possible patch.

Regards,
Effenberg

---

### Post by chrissy.millichamp on 2012-08-23
Ive studied what u were mentioning, and there’s no message saying like Sorry the application closed unexpectedly that comes up when vlc crashes, which is weird? I couldve sent the report detailing why and so on....Is there a way that a message as such could occur somehow?

---

### Post by cariboo on 2012-08-24
> **chrissy.millichamp said:**
> Ive studied what u were mentioning, and there’s no message saying like Sorry the application closed unexpectedly that comes up when vlc crashes, which is weird? I couldve sent the report detailing why and so on....Is there a way that a message as such could occur somehow?

Start vlc in a terminal, you should see some sort of error message, Copy and paste the error in your next post.

---

### Post by chrissy.millichamp on 2012-08-24
> **cariboo907 said:**
> Start vlc in a terminal, you should see some sort of error message, Copy and paste the error in your next post.
How do I start vlc in a terminal?

---

### Post by cariboo on 2012-08-24
> **chrissy.millichamp said:**
> How do I start vlc in a terminal?

Open a terminal Ctrl-Alt-t, and type:

```
vlc
```

---

### Post by chrissy.millichamp on 2012-08-24
```

Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
^AX Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0

```

---

### Post by cariboo on 2012-08-24
Have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1988663](http://ubuntuforums.org/showthread.php?t=1988663)

It deals with the same problem you are running into.

---

### Post by chrissy.millichamp on 2012-08-24
Could u tell me in your own words step by step that how I could resolve these Issues concerning from what my problem is. Because it seems that even though if  I read those threads youve suggested and such, I think matter of the fact is, if I am asking you that its because I am an Linux Ubuntu lover,not a geek, u get the picture? lol :)

---

### Post by effenberg0x0 on 2012-08-24
> **chrissy.millichamp said:**
> Could u tell me in your own words step by step that how I could resolve these Issues concerning from what my problem is. Because it seems that even though if  I read those threads youve suggested and such, I think matter of the fact is, if I am asking you that its because I am an Linux Ubuntu lover,not a geek, u get the picture? lol :)

Hi chrissy.millichamp, 

Ubuntu+1 is the area of UbuntuForums where contributors test upcoming releases of Ubuntu and report bugs to developers. It is now focused on the the next Ubuntu (Quantal Quetzal), to be released in October. 

I believe you are more likely to receive fast and thorough support for VLC if you post a support request in the "General Help" section of UbuntuForums. Not only they have much more contributors providing support to end-users, they also know a lot more about specific applications like VLC.

Regards,
Effenberg

EDIT: I forgot to mention: Installing a development release is expected to cause breakage in many applications. It's not a finished product. If you need a working OS, I believe running a development release is not the best option, as it can cause you a lot of problems.

---

### Post by cariboo on 2012-08-24
> **chrissy.millichamp said:**
> Could u tell me in your own words step by step that how I could resolve these Issues concerning from what my problem is. Because it seems that even though if  I read those threads youve suggested and such, I think matter of the fact is, if I am asking you that its because I am an Linux Ubuntu lover,not a geek, u get the picture? lol :)

There are a couple of things to try to solve the problem:

First, press Alt-F2 and type:

```
gksu gedit /usr/share/applications/vlc.desktop
```

This will open the vlc launcher file in a text editor. Click Search->Find and type:

```
Exec
```

the line you are looking for should look like this:

```
Exec=/usr/bin/vlc %U
```

Edit the line, so that it looks like this:

```
Exec=env LIBOVERLAY_SCROLLBAR=0 /usr/bin/vlc %U
```

then save the file and close the text editor.

What the above line does is disable the overlay scrollbar, and should solve the problem.

Another thing that mc4man suggest is to delete the vlc QT configuration file in your home directory. To do this, open Nautilus, and press Ctrl-h, this will reveal the hidden files and directories in your home directory, double-click ,config, then vlc, you should see two files:

[LIST]
[*]vlc-qt-interface.conf
[*]vlcrc
[/LIST]

You need to delete ***vlc-qt-interface.conf***. then close nautilus.

Hopefully this hould solve your problem.

---

