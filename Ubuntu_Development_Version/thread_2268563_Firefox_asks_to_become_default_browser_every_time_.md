---
title: "Firefox asks to become default browser every time I open it"
date: 2015-03-09
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2015-03-09
Since I installed Vivid Mate beta1 every time I open Firefox or nearly every time it asks to become the default browser.
I check the box not to ask me again and click yes to the question.

Yet it does this over and over.
I searched the internetz and could not find any compelling answer as to a fix.

Any one have any good ideas?

---

### Post by mc4man on 2015-03-09
Really not clue as I don't use mate or even 15.04 but happened to notice - 
For whatever reason it appears that Firefox uses gconf for this & when setting as default writes to ~/.gconf/desktop/gnome/url-handlers/*
Maybe see if that directory/files is used in mate

Otherwise maybe just tell FF to stop bothering you about this...

---

### Post by buzzingrobot on 2015-03-09
Not using Mate now, but I recall dconf-editor included Mate entries.  Perhaps there's a way to set the default browser there. 

Might also just be a bug in the beta.

---

### Post by pqwoerituytrueiwoq on 2015-03-09
under xubuntu 14.04 i have this issue using the developer edition of firefox

---

### Post by mc4man on 2015-03-09
From live session:
There are settings all over the place regarding  though the one that seems to matter is in "Preferred Applications" 
(- firefox writes this as mentioned to ~/.gconf/blah, blah but mate ignores that
There is a mate dconf setting for 'browser' but it also doesn't seem to matter

So try opening "Preferred Applications"  & set to Firefox there
What would be interesting is to know where are Preferred Applications settings stored?
(edit: maybe the same as where individual mimetype associations are stored,  which isn't in ~/.local/share/applications/mimeapps.list

---

### Post by Cavsfan on 2015-03-10
Thanks for the replies!
I just got it again when I opened Firefox and each time I check don't ask me again and set Firefox to default. 
But that has not had any effect. It will do it again.

After looking in the places you have mentioned one would think it would not be doing this.

There is really nothing in ~/.gconf/desktop/gnome/url-handlers/ that says Firefox. 
Although I don't know why chrome would be in there as I don't have it installed. Maybe that's the problem?

[ATTACH=CONFIG]260548[/ATTACH]

I'm using the default Firefox that came installed although I think it was updated recently but I had the problem before that too.
It was just an update from 36 to 36 so no real upgrade.

[ATTACH=CONFIG]260549[/ATTACH]

Firefox appears to be set as the default in dconf as you said mc4man it apparently doesn't matter.

[ATTACH=CONFIG]260550[/ATTACH]

It's been set to Firefox in my preferred applications since it was installed. I think it came that way.

[ATTACH=CONFIG]260551[/ATTACH]

```
cavsfan@cavsfan-MS-7529:~$ cat ~/.local/share/applications/mimeapps.list 
[Default Applications]
x-scheme-handler/http=firefox.desktop
x-scheme-handler/https=firefox.desktop
x-scheme-handler/about=firefox.desktop
x-scheme-handler/mailto=thunderbird.desktop
application/x-extension-eml=thunderbird.desktop
message/rfc822=thunderbird.desktop
inode/directory=caja-folder-handler.desktop
text/plain=pluma.desktop
audio/mpeg=rhythmbox.desktop
audio/x-mpegurl=rhythmbox.desktop
audio/x-scpls=rhythmbox.desktop
audio/x-vorbis+ogg=rhythmbox.desktop
audio/x-wav=rhythmbox.desktop
video/mp4=vlc.desktop
video/mpeg=vlc.desktop
video/mp2t=vlc.desktop
video/msvideo=vlc.desktop
video/quicktime=vlc.desktop
video/webm=vlc.desktop
video/x-avi=vlc.desktop
video/x-flv=vlc.desktop
video/x-matroska=vlc.desktop
video/x-mpeg=vlc.desktop
video/x-ogm+ogg=vlc.desktop
image/bmp=eom.desktop
image/gif=eom.desktop
image/jpeg=eom.desktop
image/png=eom.desktop
image/tiff=eom.desktop
application/pdf=atril.desktop

```

---

### Post by Cavsfan on 2015-03-10
It did it when I first opened Firefox after I booted into Vivid Mate. But it hasn't done it the last two times I've closed Firefox and opened it again.

It's sort of a hit or miss thing; random. But, I'm fairly sure it'll happen again.

---

### Post by SeijiSensei on 2015-03-10
Do you have a $HOME/.mozilla directory?  It, and all the files in the directory, should be owned by you.  Are they?

---

### Post by Cavsfan on 2015-03-11
> **SeijiSensei said:**
> Do you have a $HOME/.mozilla directory?  It, and all the files in the directory, should be owned by you.  Are they?

Yes. I always back that folder up before I do a clean install
```
cavsfan@cavsfan-MS-7529:~/.mozilla$ ls -l
total 16
drwx------ 2 cavsfan cavsfan 4096 May 19  2014 extensions
drwx------ 5 cavsfan cavsfan 4096 Jun 22  2014 firefox
-rw------- 1 cavsfan cavsfan    3 Mar 22  2013 firefox.last-version
drwx------ 2 cavsfan cavsfan 4096 Mar 25  2014 plugins

```

It did it today when I first booted into Vivid. It seems like it's about a once a day thing - the first boot. 
I have booted a 2nd time after reinstalling nvidia-340 and nvidia-340-uvm when it got the never ending error after the 3.19.0-8-generic was installed and when I opened Firefox I did not get this message.

I just changed the file permissions to this:
```
cavsfan@cavsfan-MS-7529:~/.mozilla$ ls -l
total 16
drwxrwx--- 2 cavsfan cavsfan 4096 May 19  2014 extensions
drwxrwx--- 5 cavsfan cavsfan 4096 Jun 22  2014 firefox
-rw-rw---- 1 cavsfan cavsfan    3 Mar 22  2013 firefox.last-version
drwxrwx--- 2 cavsfan cavsfan 4096 Mar 25  2014 plugins

```

Maybe that will do it.

---

### Post by SeijiSensei on 2015-03-11
Adding group privileges won't help, I'm afraid.  The permissions granted to you as a user should suffice.

---

### Post by Cavsfan on 2015-03-11
> **SeijiSensei said:**
> Adding group privileges won't help, I'm afraid.  The permissions granted to you as a user should suffice.

Thanks! It just did it to me again. I opened Firefox and the box appeared without a check in the box. I once again put a check in the box and told it to be default.

So I guess it just randomly does this. A few times per day.

---

### Post by Cavsfan on 2015-03-12
It did not happen to me today when I first opened Firefox. I think that is the first time that has happened.

So, maybe it's good to go. Only time will tell.

---

