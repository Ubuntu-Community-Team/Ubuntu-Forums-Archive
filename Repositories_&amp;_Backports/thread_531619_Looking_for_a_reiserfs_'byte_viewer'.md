---
title: "Looking for a reiserfs 'byte viewer'"
date: 2007-08-21
forum: Repositories &amp; Backports
---

### Post by TravMan63 on 2007-08-21
I'm looking for 'something' that can examine a reiserfs ...

(unless someone has another idea on this...)

I chose the incorrect option on a gvim file and 'deleted' (a big) part of my file... I'm guessing it still exists on that partition 'somewhere'...  

Are there any tools that will allow examining the reiserfs byte by byte?

TM

---

### Post by kidders on 2007-08-22
Hi there,

In general, flat text files are quite difficult to recover. If, however, you deleted something with structure (eg an XML document), you'll find that a *whole* lot easier, because recovery applications can identify the file's original boundaries.

Unfortunately, it's quite likely that the only way examining the raw filesystem would be of much use is if you already knew approximately where your file was stored ... which is unlikely, to say the least! In theory however, there is no particular reason why you can't open /dev/sda1 (for example) in a hex editor, or any other application, and take a look around ... provided you make *absolutely no modifications* of any kind. Even the slightest alteration could destroy the whole filesystem.

Anyhow, there's a wealth of forensic data recovery utilities available that are at least *capable* of doing the job for you ... your problem is likely to be identifying which of the thousands (millions?) of things these tools may recover is the one file you're interested in.

Recently, a friend of mine deleted a very important PDF. Since PDFs, like XML, are another example of "structured" data, all I had to do was plug his laptop into my firewire port, run a utility called foremost to recover *all* PDFs, and select the right one based on their preview icons. If it had been C source though, things would've been much more difficult.

Three suggestions:[LIST]
[*]If possible, alter your /etc/fstab to mount the affected filesystem in read only mode until your recovery is complete. In the interim, the more you write to the filesystem containing the data you want to recover, the less likely it becomes that you'll succeed.
[*]ReiserFS uses some unusual techniques (that you are presumably already aware of) to store small files (ie the sort of thing you might be working on in a text editor). This *may* impact data recovery ... I'm not sure. If you've been using your filesystem without the "notail" mount option, you might want to double-check, just on the off-chance it makes any difference.
[*]Naturally, any reply to your post *has* to mention backups at some point. Sorry for doing it. I do want to suggest that you at least consider implementing some sort of automated replication procedure though ... perhaps something that could take 5-minute snapshots of vitally important files, that would then allow you to edit them more freely, without fear of losing anything.[/LIST]I hope this post helps a little.

---

### Post by TravMan63 on 2007-08-23
Thank you for your comments and insight...

I do know it can be a daunting task to locate exactly where the data is stored (I have successfully used editors on other file systems - in windows - FAT/NTFS (and I think way back in my c-64 'daze')

I do understand the risks of writing/modifying data in this way.
My intent is to read only.

This pc has 2 OS's - the data is in the home folder/partition of the OS I would NOT boot to... I would use the other (Ubuntu) - to do the 'recovery attempt'.

I'm not sure how 'structured' a gvim file is - so I'm not sure about these 'boundaries'.  However, I would guess that there would be 'sector links' - that any file would use (to know where the next section of data is).

I understand that Reiserfs does 'something different' to work with small files well ... this is my 1st use of Reiser - so I'm definitely 'green' at knowing the details about that.  My usual thinking would be 'smaller cluster sizes'.

Yes - backups are very important... the only way I can back this system up is via a remote machine (I use winscp on windows machine... with ssh) (no local storage device - although a floppy could simply suffice for small files).  As far as the idea of '5 minute snapshots' - I would guess you are suggesting a cron job that would simply copy the desired files/ directories to an alternate location?  I would guess tar could be used as well?

I've heard of the 'notail' mount option; but as I previously stated - I'm pretty 'green' (very new to) this file system (and fairly new to Linux as well).

Very good ideas and points have been made here; however, to begin this 'adventure' does require a tool capable of the job.  Any suggestions here?

I'm not sure how gvim behaved when I 'recovered ' the file - did it simply truncate it - or did it actually write data over the existing data?  I would think it is the 1st, as the file size is reported as smaller.

Thanks again

TM

---

### Post by kidders on 2007-08-23
Hey again,

> **TravMan63 said:**
> I'm not sure how 'structured' a gvim file isThat will depend on exactly what you were editing, really.

FYI, the "notail" option prevents ReiserFS from writing small files directly into its tree ... a peculiar trick it likes to use for disk usage & access time efficiencies. I suspect (perhaps with no good reason) that this may confuse some recovery tools.

> **TravMan63 said:**
> As far as the idea of '5 minute snapshots' - I would guess you are suggesting a cron job that would simply copy the desired files/ directories to an alternate location?Well, imagine you created a ~/bin/gvim that did something like this...```
~/bin/snapshot $1 &>/dev/null &
/usr/bin/gvim $@
```You could arrange it so launching an editor also triggered an additional process, that could monitor the file you were editing for changes, and create backups.

You've more or less made it already, but the distinction between a deleted file and a truncated one is important. Consequently, off the top of my head, I can't name a utility that would *definitely* be able to help you. I would suggest doing a few "apt-cache search"-es, and trying out one or two apps. There are also lots and lots of threads here that deal with data recovery ... perhaps some of them mention applications that aren't in Ubuntu's repos that would be worth a shot. Also, does opening the raw filesystem in a hex editor get you anywhere?

---

### Post by TravMan63 on 2007-09-02
I have attempted to view /dev/hda12
with:
elvis
nano
vim
gedit

none will open it.

lde - linux disk editor - doesn't support reiser...

I also looked at foremost, but it doesn't appear to do what I'm looking for... (but appears to be a good tool)...

like you observed - it's a truncated file...  and who knows - maybe gvim overwrote it...

TM

---

### Post by kidders on 2007-09-02
> **TravMan63 said:**
> I have attempted to view /dev/hda12
with:
elvis
nano
vim
geditThis isn't really a terribly useful observation, I suppose, but I wouldn't expect you to have great success with these ... they're just text editors. A hex editor might be more productive, imo.

---

### Post by TravMan63 on 2007-09-04
winhex - 

[http://www.winhex.com/](http://www.winhex.com/)

runs under wine... but unfortunately I can't get it to open a disk (dev/hdx) due to path problems... 

it's the same tool I've used in windows...

---

### Post by kidders on 2007-09-04
Hehe... I imagine trying to open something in /dev would make a Windows app terribly confused. How about something in "apt-cache search hex editor"?

I'm still not convinced you'll be able to successfully recover much this way, but if your stuff is important enough, anything is worth a shot, I suppose.

---

### Post by TravMan63 on 2007-09-09
kidders,

Thanks for your time and input.  I do appreciate it.

Actually - 'elvis' came from a search in synaptic (also appears with the apt-cache search)....

I did download another prog called 'git' - I"m having the same issue - as with winhex and elvis --- they can't open the (any) of the /dev/hdxx files .... perhaps I need to chmod or chown?

Those files/icons do have the 'red x' in nautilus- owner of root (rw), group of disk (rw) - I ran winhex (wine) as root.... I can view files (in standard directories as a user with git....

--
edit
Maybe I didn't try elvis as root ---- but git as root - and I"m in the filesystem :)  - now the search....

what kinda person enjoys looking at this kinda data anyway :) ?

thanks for your comments and direction

TM

---

### Post by MadMan2k on 2007-09-11
as for hex editors; theres ghex.

---

