---
title: "digikam symlink fix for network share"
date: 2008-09-07
forum: Ubuntu Studio
---

### Post by tone33 on 2008-09-07
I want to use digikam for my pictures which are located on another network share.  Specifically at /media/Pictures/Pictures/.  So I follow the instructions here:  [http://lists.kde.org/?l=kde-bugs-dist&m=117536777106366&w=2](http://lists.kde.org/?l=kde-bugs-dist&m=117536777106366&w=2) and i get this:  "Failed to update old Database to new Database format".  and cannot get into digikam.  I can go into ~/.kde/share/config/digikamrc config file and change album path back to local share and digikam will start back up just fine.  But I can't seem to get the symlink working correctly.  Here's the symlink command I'm using from the local directory I pointed digikam to use for albums:

```
tone@ubuntu-desktop:~/Pictures$ ln -s digikam3.db /media/Pictures/Pictures/
```

Then I get this:

```
ln: creating symbolic link `/media/Pictures/Pictures/digikam3.db': File exists
```

And when I try to run digikam (from terminal) I get this:

```
tone@ubuntu-desktop:~/Pictures$ digikam
digikam: WARNING: [bool Digikam::AlbumDB::execSql(const QString&, QStringList*, bool)] sqlite_compile error: unable to open database file on query: SELECT name FROM sqlite_master WHERE type='table' ORDER BY name;
digikam: WARNING: [bool Digikam::AlbumDB::execSql(const QString&, QStringList*, bool)] sqlite_compile error: unable to open database file on query: SELECT value FROM Settings WHERE keyword='Locale';
digikam: WARNING: [bool Digikam::AlbumDB::execSql(const QString&, QStringList*, bool)] sqlite_compile error: unable to open database file on query: REPLACE into Settings VALUES ('Locale','UTF-8');
digikam: WARNING: [bool Digikam::AlbumDB::execSql(const QString&, QStringList*, bool)] sqlite_compile error: unable to open database file on query: SELECT name FROM sqlite_master WHERE type='table' ORDER BY name;
digikam: WARNING: Failed to open new Album Database

```

am i doing my symlink wrong? any ideas?

---

### Post by paulg on 2008-09-08
From your provided link it sounds like you missed the steps copied below. Based on your results of creating the symlink the db file already exists so the link command won't work. You need to make sure you delete the appropriate configuration files in your /media/Pictures/Pictures folder (see the excerpt from your howto below) then the symlink command you posted will work.


```

==Configuration Cleanup==
First, if you've already run digiKam and it has hung (or done nothing) you must do \
the following to clean up the corrupt digiKam configuration:

1. Verify that digiKam is not still running. If it's running, kill it off. (The \
digiKam process may be running even if you don't see digiKam on your desktop. Use the \
"ps" and "kill" commands to verify and kill off the process, or, simply bring up KDE \
System Guard, find the digiKam process, and, kill it.)

2. Delete your digiKam config file, located at: ~/.kde/share/config/digikamrc

3. Go to the folder you specified as the "Albums Library Folder" and delete the two \
files that digiKam created: "digikam3.db" and "digikam3.db-journal".

```
[-Source]("http://lists.kde.org/?l=kde-bugs-dist&m=117536777106366&w=2")

Thanks for the work around. I had looked at using digikam instead of reinstalling picasa but I couldn't understand why it wouldn't allow me to save pictures to a networked folder which is a bummer since that's where all my bulk storage is. But I digress, this looks like it should do what I need for now. Wish it could save the db remotely too so that tags could be shared across users on the network but I'm sure I'm not the only end user wishing that.

---

### Post by tone33 on 2008-09-10
i'll double check my steps, but i did delete the config file, maybe just not the last time.  So i'll delete it again and see if i get a different message when trying to create the symlink.  (although I'm out of town currently so won't get back to it for a few days..)

I agree that being able to access pictures on a share from any computer, saving the tags so all users get the same tags is ideal for me too.  That's one thing i didn't like about Picasa, on windows it's profile specific.

---

