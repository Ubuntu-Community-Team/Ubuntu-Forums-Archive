---
title: "Questions about Shared Folders VBox"
date: 2018-10-29
forum: Virtualisation
---

### Post by sonyboyj on 2018-10-29
There's a few folders i want to share in Windows with Linux (Ubuntu), So  i decided to use the shared folders feature in VBox but i need some  help. When ever i booted up Ubuntu the shared folders are mounted? to  the Desktop and i can't remove them or pin to the dock. I'd rather just  have them mounted in my Documents on Ubuntu then use file manager to get  to them. When ever i go to open one of the shared folders i'm prompted  for a password which is OK i guess but i'd rather not if possible also  all the files in the folder have a lock icon on them so i have to type  in a password again, which is annoying when you wanna listen to music or  going thru pics. I wanna in the end by able to get the music player in  Ubuntu to load the music from the shared folder labelled music which  points to the music folder on Windows.[ATTACH=CONFIG]281488[/ATTACH][ATTACH=CONFIG]281489[/ATTACH]

---

### Post by TheFu on 2018-10-30
Think of vbox shared storage as network shares.  The server (windows) shares them with the client (the VM).  Inside the client, whatever method is normally used to access network storage is needed, with the correct driver to make that access possible.

Beware that vbox shared folder are a security risk in both directions and that file locking has been a problem for years. There are many caveats with using the virtualbox implementation. Also the usually caveats about the guest addition license and keep the underlying vbox and guest additions in-sync apply.

[https://help.ubuntu.com/community/VirtualBox/SharedFolders](https://help.ubuntu.com/community/VirtualBox/SharedFolders) is the ubuntu knowledge base.
The best information about vbox is the manual: [https://www.virtualbox.org/manual/ch04.html#sharedfolders](https://www.virtualbox.org/manual/ch04.html#sharedfolders)
I'd mount the storage using the fstab myself.  Since there is zero risk of the storage not being available when the VM runs on the same physical hardware.

Mounting network storage under any userid's HOME is a bad idea for a number of reasons.  To make it "feel" that way, use symbolic links, but have the actual mount somewhere else.  I'd use /D/Music myself, but it is your system.  Most people ignore this advice and I never hear if they got burned later or not.  Also, consider making it a read-only mount to protect against accidental modification by Linux.  I use read-only mounts for Music that is shared via Plex and Nextcloud for that reason.

Just some ideas for your consideration.

---

