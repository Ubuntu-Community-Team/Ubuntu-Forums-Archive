---
title: "File managers and keyboard operation"
date: 2010-04-08
forum: Testimonials &amp; Experiences
---

### Post by tupfzom on 2010-04-08
Hi all,

do you know this feeling?  There is this brick that you're constantly stumbling over and, despite all the Linux power ;-), you can't get it out of your way?  No?  Well, this is my brick:

I'm somewhat dissatisfied with the file managers I am using.  On my desktop, I've installed Gnome and am mainly using Nautilus.  On my Laptop, an older machine, I'm using Thunar.

Well, Nautilus isn't bad, but it's a bit sluggish.  I'm almost exclusively using the keyboard for navigating around my files.  Say I want to reach the file ~/photos/holidays/2009-winter/snowman.jpg.  I type "pho", which selects the "photos" folder, I press enter, I go on typing "hol" because I know this will select the "holidays" folder inside, and press enter.  No problem with Thunar, but Nautilus is too slow.  I pressed enter the second time before it even opened the "photos" folder, so the "holidays" folder isn't selected.  Nautilus constantly thwarts me and makes me stumble.

Well, Nautilus, you could take a leaf out of Thunar's book.  You say Thunar is faster because it lacks much of your functionality?  No excuses!  Look at Dolphin, it's feature rich and still snappy when I type!  You can count yourself lucky that Dolphin has one major deficiency that keeps me from abandoning you:  The only way to reach the open with dialog is with the right mouse button!  (Unless I'm missing something - please tell me I do!)  Your "open with" functionality is already horrible to use with the keyboard (did you hear my arrow keys aching?), but Dolphin doesn't even have File => Open (with)!  (It looks similar with Konqueror.)  I can't live without "open with", and no, I won't be reaching for the mouse!  (This would thwart me even more severely.)  If I'm e.g. working with SVG files, I might want to open them in a text editor, an XML editor, Inkscape or a handful of web browsers.  For me, there is no default app for such files.

Well, then I should probably go with Thunar?  Honestly, it's a bit spartan.  Midnight Commander?  I must admit I didn't try.  I may seem a bit geeky to some, but I'm enough artistically inclined (sounds better than "spoiled", doesn't it?) that I feel much more comfortable with nicely themed GUIs.

I hate to say it, it seems to me that Windows Explorer might be the fastest GUI file manager for keyboard operation!?  Nautilus, Thunar, Dolphin, Konqueror, Rox and all you folks out there, I appeal to your honor!  It can't be true that Linux users have become worse mouse pushers than Windows users!

Devastated,
Thomas W.

---

### Post by julianb on 2010-04-08
I don't use file managers in Ubuntu all that much. I often find them less convenient than the command line. Windows explorer isn't too bad when I'm in Windows, but my preference in Windows is to use Google Desktop in its place whenever possible. (I use Google desktop to type in file-path locations sometimes). 

Maybe I should install Google Desktop in Linux too, because Beagle seems buggy. 

Like you, I am annoyed when stuff that I would do with keyboard shortcuts in windows requires me to pick up the mouse in Ubuntu. Oh well.

---

### Post by cariboo on 2010-04-08
Do you have to use a gui file manager? Give mc a try, it's in the repositories.

---

### Post by WinterRain on 2010-04-08
You can use thunar in gnome ubuntu also.
```
sudo apt-get install thunar
```

---

### Post by mastablasta on 2010-04-09
In windows i never used windows explorer (i guess i used it at first when it was still called file manager). I used norton and later total commander. 
 
Ther eis no total commander for linux but there are plenty alternatives. Such as for example Krusader. I think these kind of managers are much more capable and are made for keyboard use. in fact you can move faster in them using keyboard than mouse.
 
Only thing is in Gnome Krusader gives me some errors. Haven't really got time to troubleshoot them. Might be that i am just missing some dependant programmes.

---

### Post by tupfzom on 2010-04-09
> **julianb said:**
> Like you, I am annoyed when stuff that I would do with keyboard shortcuts in windows requires me to pick up the mouse in Ubuntu. Oh well.

Good to hear I'm not the only one who feel like this.

> **cariboo907 said:**
> Do you have to use a gui file manager? Give mc a try, it's in the repositories.

Well, I am picky here!  (For my (lame?) justification for rejecting mc see my first post.)  My motivation for this thread was to express my disappointment that GUI programs in fact *can* be operated efficiently with the keyboard, but for some reasons they often totally neglect this.  File managers are a prominent example.

> **WinterRain said:**
> You can use thunar in gnome ubuntu also.

Of course, and I have it installed.  It's nice and fast, but it lacks some features, you know (I don't complain, it's meant to be like that).

> **mastablasta said:**
> Ther eis no total commander for linux but there are plenty alternatives. Such as for example Krusader.

Oh, I almost forgot about Krusader.  It's been quite a while since I've had a look at it.  But still no "open with" without right mouse button AFAIKS?

But there is an interesting thing I found out:  There is this editable menu shortcut feature of Gnome, that I find great but deactivated it because I all to easily change shortcuts involuntarily.  (This could be fixed easily, but there doesn't seem to be any interest[1].  This is what I mean.  Keyboard efficiency is totally neglected.)  Anyway, I found I could assign Ctrl+O to File => Open with => Other application in Nautilus and Thunar.  Now I can Press Ctrl+O and type the first letters of the app.  That's in fact a lot better than any open with submenu!  Thunar is even a bit better here because it lists the preferred apps first (potentially less letters to type).  Maybe I really should relinquish Nautilus' additional features and go with Thunar...

[1] [http://mail.gnome.org/archives/gnome-list/2010-January/msg00007.html](http://mail.gnome.org/archives/gnome-list/2010-January/msg00007.html)

---

### Post by mastablasta on 2010-04-09
to tell you the truth i haven't tried this function. at the moment i am on win.
 
in total commander you need to hold down the right mouse button to get open with in menu. maybe in Krusader is the same?

---

### Post by tupfzom on 2011-03-24
It's been some times since I expressed my frustration here.  I've since switched to nice and fast Thunar as my file manager and am now using pcmanfm because of its tabs.

Pcmanfm lacks an "open with" keyboard solution, but I've worked out an alternative that I'm pretty happy with.  Using autokey and pyGtk I've worked out a dialogue similar to the good old application launch dialogue (the Alt+F2 one) that opens any selected file, filename or URL in any program of your choice that it can get hold of by copying it to the clipboard with Ctrl+C.  It also has MIME type sensitive autocompletion (I find that so cool!).

In case someone wants to try it, here it is.  It's basically the first reasonable thing I've done with Python, so I'm happy to learn what can be done better.  There are also some TODOs and questions left open, but up to now I'm reasonably happy with it.

```

import time
import pygtk
import os
import gio

def key_press(widget,event):
  if event.keyval == gtk.keysyms.Return:
    os.system(entry.get_text().strip() + " " + filename.replace(" ","\\ ") + " &")
    window.destroy()
  elif event.keyval == gtk.keysyms.Escape:
    window.destroy()

# Get filename by <Ctrl>+C
try:
  old_clipboard = clipboard.get_clipboard()
except:
  old_clipboard = ""
clipboard.fill_clipboard("")
keyboard.send_keys("<ctrl>+c")

# We create and show GUI elements now so the user can type immediately
# As copying to the clipboard takes some time, it makes sense to do something
# else in the meanwhile (allocating all kinds of objects)
entry = gtk.Entry()
entry.add_events(gtk.gdk.KEY_PRESS_MASK)
entry.connect("key_press_event",key_press)

window = gtk.Window()
window.add(entry)
window.set_default_size(400,-1)
window.set_position(gtk.WIN_POS_CENTER)

window.show_all()

commandlist = gtk.ListStore(str)
completion = gtk.EntryCompletion()
completion.set_inline_completion(True)
completion.set_text_column(0)

entry.set_completion(completion)

# It's not sure that the selection has already reached the clipboard
# so try until it has.
filename = ""
while filename == "":
  try:
    filename = clipboard.get_clipboard().strip()
  except:
    pass

clipboard.fill_clipboard(old_clipboard)

# If the launcher copies the path from the address bar of a web browser,
# remove/replace the special URI parts.
if filename.startswith("file:///"):
  filename = filename[7:]
if filename.startswith("file://localhost/"):
  filename = filename[16:]
filename = filename.replace("%20"," ")

window.set_title('open "' + filename + '" with:')

# Detect what applications are listed to open this mimetype
try:
  mimetype = gio.File(filename).query_info('standard::content-type').get_content_type()
except:
# If it's not a local file (otherwise gio would succeed), as a fallback assume it's a remote
# html page so it opens in the web browser.
  mimetype = "text/html"

# Store all applications for this mimetype in a list
# TODO: Replace get_executable with get_commandline and process exec variables correctly
# http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-0.9.4.html#exec-variables
paths = os.environ['PATH'].split(":")
for fileInfo in gio.app_info_get_all_for_type(mimetype):
  executable = fileInfo.get_executable()
  # Sometimes the whole path is returned by get_executable.
  # If the path environment variable has this path anyway, remove it from executable
  for path in paths:
    if executable.startswith(path):
      executable = executable[len(path)+1:len(executable)]
      break
  # We prepend a space to all executable names because later we'll send a space
  # keystroke that will trigger the dropdown list for associated file types
  commandlist.append([" " + executable])
  
completion.set_model(commandlist)

# Enter a space so that the autocompletion dropdown is triggered
# If the entry field has already been modified, we need to insert the space
# and adjust the cursor position accordingly
if entry.get_text() == "":
  keyboard.send_keys(" ")
else:
  position = entry.get_position()
  entry.set_text(" " + entry.get_text())
  entry.set_position(position + 1)
```

If anyone wants to give it a try, install autokey, open the configuration window, create a new script (Shift+Ctrl+N), paste the code and assign a keyboard combination of your choice.

Thomas W.

---

### Post by mips on 2011-03-24
```
sudo apt-get install worker

```

[http://www.boomerangsworld.de/worker/](http://www.boomerangsworld.de/worker/)
[http://sourceforge.net/projects/workerfm/](http://sourceforge.net/projects/workerfm/)
[http://www.ubuntugeek.com/worker-highly-configurable-two-paned-file-manager-for-x.html](http://www.ubuntugeek.com/worker-highly-configurable-two-paned-file-manager-for-x.html)

---

### Post by mastablasta on 2011-03-24
hmm then again... keyboard... such an old input device since the age of typewriters. nowadays things are moving to touch screen (various tabs and phones) and then to hand movements (e.g kinnect) and voice commands, so is keyboard really the future that should be heavily invested in?

---

### Post by tupfzom on 2011-03-24
> **mastablasta said:**
> hmm then again... keyboard... such an old input device since the age of typewriters. nowadays things are moving to touch screen (various tabs and phones) and then to hand movements (e.g kinnect) and voice commands, so is keyboard really the future that should be heavily invested in?

I'm not a Spartan.  I usually prefer a nice, clean, consistent GUI over a command line or text user interface.  Yes, for things like web browsing touch navigation is certainly nice.  And I can imagine doing audio recording and editing using a touch interface for my amateurish uses.  But writing text/code?  Every technology has its uses.  I think the keyboard is still the fastest input device (although it might be the least intuitive), not only for text.

And it's not a "heavy investment".  I was surprised how few lines of code it takes to create a feature that I always wanted to be in the file manager.  (Thanks gtk/gio/python.)  It's not perfect, but I thought I'd post it here in case anyone was looking for a similar thing.

---

### Post by mastablasta on 2011-03-24
well i on th eother hand would liek to see a good voice recognition programme to whome i could dictate large volumes of text while cooking or something...
 
think of it as star trek computer. you command and it does the job. :-)
 
yah coding (at least at the moment) might be a bit difficult with voice command. but again just like you can play chess on imaginary set made in your brains so you can code. maybe we are not there yet, but some day...

---

### Post by tupfzom on 2011-03-24
Right!  Sometimes I too wish that while cooking, cleaning, washing the dishes or folding the laundry I could do something else besides.  But when writing text, I'm often re-reading and reformulating, so simply dictating is not my cup of tea.  That's simpler to do with the keyboard and when you see the text.

And I wouldn't want the computer to read out XML code or something similar to me!  When reading you can easily skip parts, detect repeating or deviating patterns, move back and forth.  You can't reasonably when you're listening.

So I'm sticking to a good radio program that doesn't bore my brain when doing household work!

---

