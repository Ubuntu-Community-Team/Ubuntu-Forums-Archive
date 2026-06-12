---
title: "Trouble opening Open Office files - /tmp permission pbm?"
date: 2009-05-19
forum: Security
---

### Post by tv0571 on 2009-05-19
Recently, I've been unable to open many attachments (from net-based email accounts) through Firefox.  Even after downloading, if I launch the file directly, I get an error.  For example:

/tmp/Travel Schedule.xls could not be saved, because you cannot change the contents of that folder.


It appears that as Ubuntu launches the appropriate application, in this case Open Office Spreadsheet, it needs to write something in /tmp.  I checked the spreadsheet app, and this is the default path for temp files.  I didn't change that so I assume it is the default.

However, /tmp is a root owned directory to which my user account doesn't have write privileges, right?  I don't want to change the owner of /tmp do I?

This used to work fine - I don't know what changed.

btw, the default download directory in Firefox is not /tmp...  It is in my user path, and it is indeed putting the files there - only during the file open does it try to use /tmp.

---

### Post by pytheas22 on 2009-05-19
/tmp should be owned by root, but all users should be able to read and write to it.  Perhaps those settings were changed for some reason.  What is the output of:
```

ls -l / | grep tmp
```

---

### Post by tv0571 on 2009-05-20
drwxrwxrwt  15 root root  8192 2009-05-20 07:35 tmp

---

### Post by tv0571 on 2009-05-20
and you are right, I can "touch" a file into existance in tmp under my own id.

---

### Post by pytheas22 on 2009-05-20
The permissions on /tmp look fine.  I did a quick Google search, however, and found [this page]("http://kb.mozillazine.org/Unable_to_save_or_download_files").  Apparently this is a bug in Firefox.  There are a number of possible solutions listed there; do any of them help?

In a worst case, refreshing your Firefox profile by typing:
```

mv ~/.mozilla ~/.mozilla-OLD
```

and then restarting Firefox would probably work, but it would also cause you to lose your browsing history, bookmarked pages, etc.

---

### Post by dstempfley on 2009-05-20
Bookmarks are easy.  Copy the bookmarks.html from ~/.mozilla-OLD directory. into your new profile.  If you only have one profile then the bookmarks.html is:

~/.mozilla/firefox/$( sed -n -e "s/Path=//p" \
    ~/.mozilla/firefox/profiles.ini )/bookmarks.html

Or you can just find it yourself, but I wanted to play with sed :)

/Dion

---

### Post by tv0571 on 2009-05-20
Thanks.  That helped.  

I traced the problem to either a Del.i.cous plugin or FireBug.  I removed both and the attachment problem went away.

---

