---
title: "problems with recent documents plugin"
date: 2006-10-12
forum: Ubuntu System Panel
---

### Post by burlap on 2006-10-12
With recent documents plugin I was finally able to start using USP - it's a great app!

However, recent documents suffer from the same obscure bug as gnome panel: they are not always visible (and appear only after opening a document). 

There are several bugs on this:
Ubuntu (two of many):
[https://launchpad.net/distros/ubuntu/+source/meta-gnome2/+bug/43251](https://launchpad.net/distros/ubuntu/+source/meta-gnome2/+bug/43251)
[https://launchpad.net/distros/ubuntu/+source/gnome-panel/+bug/44940](https://launchpad.net/distros/ubuntu/+source/gnome-panel/+bug/44940)
Upstream (Gnome)
[http://bugzilla.gnome.org/show_bug.cgi?id=316813](http://bugzilla.gnome.org/show_bug.cgi?id=316813)

Do you think the fact that this bug concerns both gnome-panel and USP plugin is somehow relevant? Should I comment on these bugs?

---

### Post by Malac on 2006-10-12
This seems to be a strange Gnome bug but as USPrecent doesn't use any Gnome process to access the recent list it seems weird that USPrecent is doing the same.
USPrecent uses the same file, .recently-used, but that is about it.
It doesn't "hook" any processes, it just reads the file once every second to see if something has been added.
My only thought is that it is some sort of file access issue, i.e. if two processes are trying to access the file at the same time. And it is not being opened in "share" mode.
I'm sorry I can't offer anymore help.

---

### Post by chanders on 2006-10-12
> **burlap said:**
> With recent documents plugin I was finally able to start using USP - it's a great app!

However, recent documents suffer from the same obscure bug as gnome panel: they are not always visible (and appear only after opening a document). 

There are several bugs on this:
Ubuntu (two of many):
[https://launchpad.net/distros/ubuntu/+source/meta-gnome2/+bug/43251](https://launchpad.net/distros/ubuntu/+source/meta-gnome2/+bug/43251)
[https://launchpad.net/distros/ubuntu/+source/gnome-panel/+bug/44940](https://launchpad.net/distros/ubuntu/+source/gnome-panel/+bug/44940)
Upstream (Gnome)
[http://bugzilla.gnome.org/show_bug.cgi?id=316813](http://bugzilla.gnome.org/show_bug.cgi?id=316813)

Do you think the fact that this bug concerns both gnome-panel and USP plugin is somehow relevant? Should I comment on these bugs?

USPrecent taps into Gnome's recently used file just to show the data. It doesnt modify the file in any way (only if you click clear ;-)

This looks like the gnome bug being propogated down to the plugin. Unless it's resolved it wil continue to manifest itself in USPrecent..

---

### Post by burlap on 2006-10-12
[Quote=Malac]My only thought is that it is some sort of file access issue, i.e. if two processes are trying to access the file at the same time.[/Quote]
This was my first thought as I used gnome-panel menu bar and USP simultaneously. But for the last few days I've used USP exclusively and the problem was the same - after login no recent documents until I open some file (but not always). Of course, bug comments (especially from Gnome bugzilla) suggest this issue is strange and difficult to track.
[Quote=Malac]It doesn't "hook" any processes, it just reads the file once every second to see if something has been added.[/quote]
Hmm. Is it the reason that USP with recent documents plugin constatly eats 5-8% of the CPU? I was trying to investigate why my computer started to run its fan more often (it's a laptop) and I've noticed this. 
[quote=chanders]This looks like the gnome bug being propogated down to the plugin.[/quote]
I'll follow the bug reports then.

---

### Post by Malac on 2006-10-12
> **burlap said:**
> 
Hmm. Is it the reason that USP with recent documents plugin constatly eats 5-8% of the CPU? I was trying to investigate why my computer started to run its fan more often (it's a laptop) and I've noticed this. 
I haven't profiled USP with USPrecent but if you want you can change the poll interval.
Find this line, around line 58 in USPrecent.py:
```
gobject.timeout_add(1000, self.DoRecent)
```and change the 1000(= 1second) to a larger number e.g. 60000=1minute.

Hope this helps.

---

### Post by M7S on 2006-10-24
I think I found out why USPrecent is empty sometimes. Sometimes the .recently_used seams to loose the spaces in the begining of the rows (this is the gnome bug, right?). USPrecent only search for lines that begins with ```
"    <URI>"
``` and misses the line when it's just ```
"<URI>"
``` with no spaces in the begining of the row.

Hope you understand what I mean.
Regards,
M7S

EDIT: Just tested myselft. After line 149 in USPrecent.py I added

```
			if FileLine[0:5]=="<URI>":
				EndPoint=FileLine.find("</URI>")
				FileString.append(FileLine[12:EndPoint])
				ItemCount+=1
``` 
In the situation where it didn't work before it works now. :)

By the way, I don't know any python. It must be a great language when that doesn't stop you from finding and fixing workarounds for bugs. ;)

---

### Post by chanders on 2006-10-24
^^ Exactly. Python is very user friendly, not to mention easy to read and understand...

---

### Post by Malac on 2006-10-25
Hi thanks for the fix but I have changed it slightly to allow for the occassions when there are spaces there.
If you replace between the line 146 "else:" and line 153 "in_file.close()" with this :
```
                URITextLen=len('<URI>')
                StartPoint=FileLine.find('<URI>')
                if StartPoint != -1:
                    EndPoint=FileLine.find("</URI>")
                    FileString.append(FileLine[StartPoint+URITextLen:EndPoint])
                    ItemCount+=1
```It should handle both situations.

I'll change the plugins page entry so you can download it if you like.

I've also changed to edgy and discovered this plugin doesn't work for that as they have changed the filename and layout for edgy. So I will code one for edgy too.

---

### Post by Malac on 2006-10-25
New USPrecent for Edgy. It no longer polls at all so should be zero (nearly) impact on cpu.
If you have Dapper and want to try it as I can't (on Edgy now), please let me know if it works via pm.
Thanks.

---

### Post by SlugO on 2006-11-07
I've got some problems with this plugin too (Dapper version). I extracted both files to plugins directory and the tab for its configuration showed up in USPconfig. But when I added it it only gave that Not found error in USP. And yes, it was spelled correctly.

I thought I'd remove the .pyc file, maybe it'd recompile it. Not a good idea :) The settings tab remained in USPconfig but now in addition to not getting it to show up I don't have a compiled file anymore since it won't compile it again once the .pyc is deleted.

Any ideas how to make it work?

---

### Post by Malac on 2006-11-07
> **SlugO said:**
> I've got some problems with this plugin too (Dapper version). I extracted both files to plugins directory and the tab for its configuration showed up in USPconfig. But when I added it it only gave that Not found error in USP. And yes, it was spelled correctly.

I thought I'd remove the .pyc file, maybe it'd recompile it. Not a good idea :) The settings tab remained in USPconfig but now in addition to not getting it to show up I don't have a compiled file anymore since it won't compile it again once the .pyc is deleted.

Any ideas how to make it work?
Hi SlugO,
First try removing USP then adding it back again.
(I don't know why this works but sometimes it does.)
Next open a terminal and cd to ~/.usp/plugins and type :
```
python USPrecent.py
```This should report any errors in the file, if it does try moving both files to the /usr/lib/python2.4/site-packages/usp/plugins folder and run that code again in a terminal in that folder.
Lastly try running ```
usp run-in-window
```in a home terminal and see what it says.
Post any errors here and I'll try to sort it.

---

### Post by SlugO on 2006-11-07
Thanks for the suggestions. When I ran it in ~/.usp/plugins I got```
Traceback (most recent call last):
  File "USPrecent.py", line 12, in ?
    from execute import Execute
ImportError: No module named execute
```Once I moved it to that /usr dir it didn't give any errors (or anything else) but I still can't see a .pyc file. I tried adding it to USP but I'm still getting the not found error. Window mode printed this:```
usp run-in-window
Warning! - Icon for item not found!
Warning! - Icon for item not found!
Warning! - Icon for item not found!
Warning! - Icon for item not found!
Warning! - Icon for item not found!
Warning! - Icon for item not found!
Warning! - Icon for item not found!
Dir exist
Dir exist
Dir exist
Application added - /home/janne/.usp/applications/firefox.desktop
Application added - /home/janne/.usp/applications/gedit.desktop
Application added - /home/janne/.usp/applications/gnome-terminal.desktop
Application added - /home/janne/.usp/applications/gaim.desktop
Application added - /home/janne/.usp/applications/totem.desktop
Application added - /home/janne/.usp/applications/gimp.desktop
Application added - /home/janne/.usp/applications/amarok.desktop
Place added - /home/janne/.usp/places/nautilus-home.desktop
Place added - /home/janne/.usp/places/-media-d-Games.desktop
Place added - /home/janne/.usp/places/-home-janne-Download.desktop
Place added - /home/janne/.usp/places/-home-janne-Kuvat.desktop
Place added - /home/janne/.usp/places/-media-d-Valokuvat.desktop
New Pane
```

---

### Post by Malac on 2006-11-08
Okay that says to me that there is nothing wrong with the plugin code as such.
Can you just check if you have a .recently-used hidden file in your home directory.
If it doesn't find that it would error too.
Can you post a screenshot of USP with the not found error showing please?

---

