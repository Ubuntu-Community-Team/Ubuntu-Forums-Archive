---
title: "Not sure how I did what I did...."
date: 2008-06-01
forum: Testimonials &amp; Experiences
---

### Post by SneakyWho_am_i on 2008-06-01
There comes a time when you say something like this:
```
mv ~/.* ~/old_config
```
That's when you realise that your problems were with corrupted packages. You fix the problems, try to move back the files (chat logs, whatever) etc that you had set aside and.... ooops. Must have forgotten a slash somewhere, or something. My settings are all mincemeat.

It's my own fault. It was a pretty serious command, and I should have had backups of that sort of thing anyway.

Well, the good news for me is, I've set aside copies of some of the important stuff (in /root *for some strange reason*, don't ask). Can you see what's coming here? I really can't be bothered sorting out the stuff in /root so how about I just kludge it?
I open Konqueror and try to copy everything to my own folder. Of course, it fails, I don't have permission to see into most of those folders, and Konqueror will abort a 1000 file transfer if one file fails.

So:
```
cd /root
sudo chown -R sneaky:sneaky *
```

Hey, that seemed to turn out OK. So in Konqueror I try to copy it again (just because I happen to have it open. Honestly!)

It fails. Something didn't move across, lol, what's this?
So I look in some auth log somewhere and lo and behold:
```
Jun  2 03:17:40 ubuntu sudo:   sneaky : TTY=pts/4 ; PWD=/root ; USER=root ; COMMAND=/bin/chown -R sneaky:sneaky Desktop Documents imvulog.txt imvu.txt InstallIMVU_393.0_full.exe Music Pictures Public sdfgsdfg Templates Videos workspace
```
OHHH of course! The .something files never got chowned

so ok how about this? (still from /root)

```
sudo chown -R sneaky:sneaky .*
```
A a dot, followed by anything. Right? Right.

I would like to say **ls -la** to check the permissions, but I can't because for some reason the operation is taking forever.

I try to copy the stuff in Konqueror anyway. Ho hum. What's really odd is that it actually works, and it only takes a few seconds :) :) ... But sudo chown is still running. And running. And running.
Eventually I get bored and kill it with CTRL+C.
**ls -la** shows that everything is as it should be.

Ten minutes later I am warned that sudo needs uid root.
I fixed that (or so I thought) by moving into the recovery console and chowning it to root:root (because it had mysteriously become sneaky:sneaky)
Ahh, good, I can use sudo again. For five short minutes.

mlocate, mysql, a bunch of other stuff. Not working. Permissions all wrong in /usr, lib, /etc. What the?? I never set permissions/ownership in any of those places??
So now I can't use sudo but I'm effectively root.
I don't know how this happened. The auth log doesn't know how it happened either:

```
Jun  2 03:18:06 ubuntu sudo:   sneaky : TTY=pts/4 ; PWD=/root ; USER=root ; COMMAND=/bin/chown -R sneaky:sneaky . .. .adobe .aptitude .bash_history .bashrc .cache .config .cvspass .dbus .eclipse .esd_auth .gconf .gconfd .gcvs .gimp-2.4 .gnome2 .gnome2_private .gnupg .gstreamer-0.10 .gtk-bookmarks .gvfs .ICEauthority .kde .kde4 .local .macromedia .mcop .mcoprc .mozilla .mysqlgui .nautilus .netrc .profile .pulse .pulse-cookie .pureadminrc .purple .qt .recently-used.xbel .Skype .ssh .subversion .synaptic .thumbnails .wapi .wine .wireshark .Xauthority .xsession-errors
```

Does one of those files/folders contain a link to / ??
Was **.*** parsed like a regular expression instead of a file/directory name?

I don't know and don't think I really care at this point. Today has not been a good week for me really.

So, a bad experience for sure. Probably my fault of course, but still bad.
Will I move to another OS? No way! By system is hurting quite badly, but it's not bricked. At least this thing only happens *every few hundred hours*, and not *every few hours* like in Windows.
At least it always breaks as a result of something I've done, and not just randomly when I'm, say, writing a letter in Notepad or something.
Thank you Ubuntu for all the fun. Looking forward to much more in the future ;)

EDIT: Yeah, I'm not even done yet and already I'm editing it. I've just realised why it changed the permission of everything under **/**
Have you?
**.*** matched **.** AND **..** - as shown in the log. /root/../ is /
Oh man, that really sucks, lol... Why is **..** caught by **.*** and not by ***** ?? Shouldn't it count as both? Blimey.

---

