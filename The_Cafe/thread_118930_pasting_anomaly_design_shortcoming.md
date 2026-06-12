---
title: "pasting anomaly/ design shortcoming?"
date: 2006-01-18
forum: The Cafe
---

### Post by borisattva on 2006-01-18
i opened up google and found a command.
not to type it all out i just selected it with a mouse, right lick, 'Copy'
i closed the window immediately, and opened up terminal.

neither Ctrl+V, not Shift+Ins, did anything. right click Paste was grayed out too.
i did it 2 more times to make sure i wasnt letting go of the keys.

then i did it again without closing firefox and only then the copy / paste worked.

isnt clipboard system wide? why did closing the source application clear it out?
from what i understand in window it actually makes a copy of the data in the clipboard, is there any reason that it doesnt do that in linux?

---

### Post by 23meg on 2006-01-18
In X when you close an app, the data you copy from it is erased from the clipboard. To remedy this you can use gnome-clipboard-daemon. I thought this was made default in Gnome 2.12 but it somehow doesn't seem to be.

---

### Post by benplaut on 2006-01-18
[QUOTE=23meg]In X when you close an app, the data you copy from it is erased from the clipboard. To remedy this you can use gnome-clipboard-daemon. I thought this was made default in Gnome 2.12 but it somehow doesn't seem to be.[/QUOTE]

i think they left it out at the last minute... It's a shame, 'cause gnome is really in need of one

<<edit>>

even worse, i don't even see the daemon in the repos!!

---

### Post by 23meg on 2006-01-18
There's a binary [here]("http://members.chello.nl/~h.lai/gnome-clipboard-daemon/"). [These instructions]("http://www.ubuntuguide.org/#clipboard-daemon") for setting it up are for Hoary but should work in Breezy.

---

### Post by borisattva on 2006-01-18
thanks alot 32meg,

i will try this after i fully reinstall my system next time
looks like nothing i do fixes my Fonts and Nautilus FTP problems,
and ive installed too much to figure out what broke what..

---

### Post by ardchoille on 2006-01-18
[QUOTE=borisattva]i opened up google and found a command.
not to type it all out i just selected it with a mouse, right lick, 'Copy'
i closed the window immediately, and opened up terminal.

neither Ctrl+V, not Shift+Ins, did anything. right click Paste was grayed out too.
i did it 2 more times to make sure i wasnt letting go of the keys.

then i did it again without closing firefox and only then the copy / paste worked.

isnt clipboard system wide? why did closing the source application clear it out?
from what i understand in window it actually makes a copy of the data in the clipboard, is there any reason that it doesnt do that in linux?[/QUOTE]
You must be using an old version of gnome because this was fixed in gnome 2.12 (according to gnome.org) and works fine here. The text that is copied to the clipboard in gnome 2.12 is no longer erased when you exit the app, it is retained.

---

### Post by borisattva on 2006-01-18
[QUOTE=ardchoille]You must be using an old version of gnome because this was fixed in gnome 2.12 (according to gnome.org) and works fine here. The text that is copied to the clipboard in gnome 2.12 is no longer erased when you exit the app, it is retained.[/QUOTE]
i'm using the what ever gnome that comes with breezy 5.10 dvd fully patched up..

---

### Post by prizrak on 2006-01-18
It still does it this way here, it's quite possible that it was a security decision since it's not a good idea to keep data in the clipboard until it is overwritten.

---

### Post by borisattva on 2007-11-24
2 years later its still missing from a default installation.

copy and paste something from a window or a prompt; close that window/prompt and the copy buffer is gone.

is this really sacrificing THAT much from 'security' on a personal computer to justify loss of convenience?

---

### Post by Polygon on 2007-11-24
i think its a security thing actually.

cause think of it, if you have a password manager and you need to look up a password for some obscure website, and you copy/paste the password as its pretty long and complicated, and then you close the password manager but dont copy anything, then your password is in your clipboard....a potential security risk

---

### Post by borisattva on 2007-11-24
i agree with that point, however its the same security risk as leaving the pc unattended, with who ever uses it to have access to my documents folders etc and so on. by design an unattended computer is a 'security risk.' if you dont wnat anyone having access to clip board, you wouldnt want them having access to your pc with everything else it has 'open' in the first place.

even with this in mind, the security risk is only annulated if the user explicitly closes the application.

the obscure protection/inconvenience ratio seems to tip towards the latter.

it really feels more like a design shortcoming than a conscious/effective security feature.

$0.02

---

