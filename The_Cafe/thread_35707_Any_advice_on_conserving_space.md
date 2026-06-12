---
title: "Any advice on conserving space?"
date: 2005-05-19
forum: The Cafe
---

### Post by 1337sithlord on 2005-05-19
Okay being the fool that I am, i only allotted 2.2gb for ubuntu.  Well it was supposed to be more but u know how file tables work :(.  Anyway, I doubt partition editors are a wise choice and im using online storage for most of my files, but what programs and system tools, do you ppl think i should prioritize, with my 300mb or so of free space?

By that I mean: do i need codecs?  like what file types cannot run without them?  If i can play mp3s, wavs, avis and mpegs without them, then thats what il do, but if i need to get them, how big are they?  

Also, how big is limewire?  id like to get that but yeah.  And is the azuerus file on the guide, the bit torrent meta file that it asks for?  That might be nice too, but is it a large file?  

And then theres a bunch of updates.  They have stuff like patches for gaim and openoffice but its 67mb.  Do they take up 67mb until u replace the old versions and then it takes up the same ammount of space again, pretty much?  And if i dont invest space in them, are they absolutely necessary, and how often do they come out?  Cause il do this once if its a good idea, but if it costs me 100s of mb overtime, i might be a bit apprehensive. 

Theres also mozilla thunderbird.  Is it compatible with basically any account, like hotmail and gmail?  Those are the two that I use... well i hardly ever use them but the name sounds damn cool lol.  Ppl have also recommended adding repositories in myself for even more programs, but do those take up much space?  Il do that if it just adds lines of codes to ubuntu, decreasing space by mere kb.

Ok well, those are the programs on which i have my eye set, and im probably forgetting some.  Essentially, how big are they and if i cant get them all, which should i get?  Thanks sry for being such a /\/00|3.

---

### Post by HungSquirrel on 2005-05-19
Well, you could remove ubuntu-desktop and some packages that come by default that you don't really need.  diveintopython comes to mind.  ubuntu-desktop is a metapackage that tells apt what packages are needed for the default system.  Removing it won't cause any problems.  However, if you mess something up when you're removing other packages, you can always re-install ubuntu-desktop and be back to where you were.

There is a program that helps you trim the fat from Debian distros by removig "orphaned" packages.  Someone want to help the man out?

---

### Post by jerome bettis on 2005-05-20
/var/log can get huge and is a total waste if you never look at it.

---

### Post by 1337sithlord on 2005-05-20
Hmm id rather not remove programs that come with ubuntu, but maybe il have to... how much space would that free up?  I trust it wont interfere with installing stuff with the sudo apt-get type codes.

---

### Post by jonrkc on 2005-05-20
[QUOTE=1337sithlord]Hmm id rather not remove programs that come with ubuntu, but maybe il have to... how much space would that free up?  I trust it wont interfere with installing stuff with the sudo apt-get type codes.[/QUOTE]
 One way to free up some space is to browse (using your favorite file manager) through all the directories and sub-directories and remove stuff that you KNOW you don't need, or shuttle some of it to a different hard drive (which however doesn't seem to be an option in your case).  

One example that comes readily to mind: documentation that you'll never read, especially in languages other than your own--often indicated by suffixes such as .de, .fr, .es, etc.  Individually the files may be not very large, but in sum they do add up to take precious space.  

If you're not running a server, you don't need any of the server-specific software, but I'm not adept enough to tell you what that might be.  However you could use synaptic and read descriptions of all the packages installed on your system, and if you know a package is useless to you, you could just remove it then and there.  If you ever needed it in the future, you could always go back and get it again.

Those are two ways I can think of to gain some space.

---

### Post by Stormy Eyes on 2005-05-20
Set up cron jobs that clean out /var/log and /tmp every 24 hours. Lots of cruft builds up there. Also, use **apt-get clean** to get rid of deb packages stored on disk.

---

### Post by 1337sithlord on 2005-05-20
Ok apt-get clean worked well.  Only deleted unnecessary deb packages :).  Im a major noob, so do u mind telling me why i cant clear out /var/log?  Everything in there is locked so i cant delete it. I could bypass the permissions of the comp to delete, but is that what you have to do?  Its prolly not a good idea.  Im guessing there just hasnt been any buildup there yet, so only necessary files remain?  Or maybe i have to go into each file and just delete the text...

Well the tmp files can pretty much all be deleted, but is it the /tmp folder, or the /var/tmp folder that I should clear?  Some contain root folders, but is the rest just cookies and stuff?

---

### Post by jonrkc on 2005-05-21
[QUOTE=1337sithlord]Ok apt-get clean worked well.  Only deleted unnecessary deb packages :).  Im a major noob, so do u mind telling me why i cant clear out /var/log?  Everything in there is locked so i cant delete it. I could bypass the permissions of the comp to delete, but is that what you have to do?  Its prolly not a good idea.  Im guessing there just hasnt been any buildup there yet, so only necessary files remain?  Or maybe i have to go into each file and just delete the text...

Well the tmp files can pretty much all be deleted, but is it the /tmp folder, or the /var/tmp folder that I should clear?  Some contain root folders, but is the rest just cookies and stuff?[/QUOTE]
 When I'm in doubt if I can safely delete a file, I rename it (use the mv command) and see how things run for a while.  If I can do my normal operation for a few days, I know I can do without that file.  Most log files can be done away with safely, but personally I would keep the newer ones around and just delete the older ones, in case I had to try to do some troubleshooting.  I believe you should be able to delete any of them as root but it's unlikely a "normal" user could delete any, for security reasons.

---

### Post by fng on 2005-05-21
[QUOTE=1337sithlord]Im a major noob, so do u mind telling me why i cant clear out /var/log?  Everything in there is locked so i cant delete it. I could bypass the permissions of the comp to delete, but is that what you have to do?  Its prolly not a good idea.[/QUOTE]

The owner off those files is the root-account.  Thta's why you dont have permission to delete/modify/... them.

But there is a solution by using the sudo command
If it asks for a password, just use your normal user password

```
cd /var/log
sudo rm *
```

---

