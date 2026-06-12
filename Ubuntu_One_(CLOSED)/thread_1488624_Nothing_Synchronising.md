---
title: "Nothing Synchronising"
date: 2010-05-20
forum: Ubuntu One (CLOSED)
---

### Post by beetleman64 on 2010-05-20
I've been using Ubuntu One since 9.10, and it worked very well, but with 10.04 I'm finding that noting synchronises. My contacts don't synchronise despite them being on the online page, my bookmarks don't work and neither do my files.

It's a shame, as I'm considering using the Ubuntu One music store, but I don't want to in case something goes wron

---

### Post by duanedesign on 2010-05-20
The contact syncing is currently down. They are making some improvements to help with the scaling of the system. With the new release brought a large number of new users. Last I heard it was hopefully going to be this week.

**EDIT:** The CouchDB is back up. You should now be able to sync Contacts

If you want to test the music store you can download one of the free tracks to get acquainted with the process. The 7digital website has [a list of the free tracks]("http://us.7digital.com/cms/free-downloads-usa/free-downloads.aspx").


To take a look at your file sync could you please run the following command in a Terminal.

```
u1sdtool -q; u1sdtool --start; u1sdtool -c
```

please post any error messages you might see in the Terminal.

After about a minute or two could you please run the following to see what state the syncdaemon is in.

```
u1sdtool -s
```

please post the output from that command
-
-

---

