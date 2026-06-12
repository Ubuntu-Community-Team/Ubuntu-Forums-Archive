---
title: "How do you backup .config or .gconf via cli?"
date: 2011-11-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kansasnoob on 2011-11-10
I guess I'm having one of those dunce-cap moments :(

I generally know very well how to back-up or rename system files, but I've always used the UI for stuff in /home.

Now I'd like to learn how to "cp" .gconf, .config, etc. Something like "cp .gconf .gconf_OLD".

I'd think since I'm in /home there'd be no need to use "sudo" or "cd" to any different directory.

Somehow I'm stumped. I can right-click any of those files and select rename or copy, but I'll be dogged if I can create a backup using "cp".

I'm sure I'll laugh at the simplicity of the answer, but I'm stumped ATM :(

---

### Post by seeker5528 on 2011-11-10
```
cp -a .config some_destination_directory
```

If you copy to a location (ntfs/fat) that can't save the linux FS permissions you will probably get a complaint, but it should still do it, the destination directory has to exist.

In the case of ntfs/fat I would create an archive of .config then copy the archive to your ntfs/fat partition.

If you don't care about permissions ```
cp -r some_directory some_destination_directory
```

Later, Seeker

---

### Post by kansasnoob on 2011-11-10
> **seeker5528 said:**
> ```
cp -a .config some_destination_directory
```

If you copy to a location (ntfs/fat) that can't save the linux FS permissions you will probably get a complaint, but it should still do it, the destination directory has to exist.

In the case of ntfs/fat I would create an archive of .config then copy the archive to your ntfs/fat partition.

If you don't care about permissions ```
cp -r some_directory some_destination_directory
```

Later, Seeker

So the "-a" must be there just as if I were using "ls", eg: 

```
ls -a
```

to show the contents of /home:

```
lance@lance-desktop:~$ ls -a
.              Desktop           .gvfs             Public
..             .dmrc             .ICEauthority     .pulse
.adobe         Documents         .local            .pulse-cookie
.bash_history  Downloads         .macromedia       .sudo_as_admin_successful
.bash_logout   .esd_auth         .mission-control  Templates
.bashrc        examples.desktop  .mozilla          .thumbnails
.cache         .gconf            Music             Videos
.compiz        .gnome2           .opera            .Xauthority
.config        .gstreamer-0.10   Pictures          .xsession-errors
.dbus          .gtk-bookmarks    .profile

```

Why didn't I think of that :confused:

Many, many thanks :)

---

### Post by kansasnoob on 2011-11-10
Just out of curiosity, does .config act like .gconf as far as totally blowing it away to get a default configuration back?

---

### Post by xebian on 2011-11-10
> **kansasnoob said:**
> Just out of curiosity, does .config act like .gconf as far as totally blowing it away to get a default configuration back?

The -a option in cp means archive preserve all attributes and recursively copies everything especially if it's a directory.

In GUI file manager, turn on 'show hidden file' ( ctl+h) and then you can see them so you can then do your copy or move right+click

If these files are missing they will be recreated from default once you login.

---

### Post by MacUntu on 2011-11-11
> **kansasnoob said:**
> So the "-a" must be there just as if I were using "ls", eg:

Nope, has nothing to do with 'ls' at all.

```
man cp
``` should help. Easy to remember: 'a' for archive. ;)

---

### Post by kansasnoob on 2011-11-11
This was all very helpful. What I'm doing is trying to come up with a basic "single command" to convert either a Oneiric or Precise DE to "classic w/o effects", and I was concerned about providing instructions for editing the panel afterwards.

What I've found is that there is no real need to back up either .config or .gconf, unless you have them customized and desire to have a backup (I'll keep a copy on a flash drive for my own use), because you can still "rm -r" both of those and on reboot (or even just logout/login) the desktop settings are restored just as they were in gnome 2.3* :)

Many thanks to all.

---

### Post by effenberg0x0 on 2011-11-11
I backup using cp -axR cp -axR .something /media/other_devices/backup

But, as you are doing heavy customization on the machine, and it's good to play safe, you might wanna store important settings elsewhere. While cp -axR .something .something.else is ok, you might also wanna consider putting rsync on cron to backup all your work important folders and files somewhere else safe every 1 hour or so (it can be incremental).

---

