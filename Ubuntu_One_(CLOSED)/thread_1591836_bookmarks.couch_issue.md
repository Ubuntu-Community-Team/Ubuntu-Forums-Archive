---
title: "bookmarks.couch issue"
date: 2010-10-09
forum: Ubuntu One (CLOSED)
---

### Post by solitaire on 2010-10-09
I'm just wondering what the size of your "~/.local/share/desktop-couch" folder is on your machines?

Is just that the [~/.local/share/desktop-couch/bookmarks.couch] file in my install (10.04 upgraded to 10.10) was a massive file!!!

Should there not be a process to tidy the database from time to time?

My current "bookmark.couch" was 4.3Gb!!!! 

I had to install "dekstopcouch-tools" to get easy access to the tools to compact the database down to a more manageable 3Mb. (a 999% reduction!!!)

I was wondering where my storage space was going to, know I know!!

**UPDATE**

How do you reinstall Couchdb / DesktpoCouch?

I found out that if you use "desktopcouch-tools" under root it messes up the Couch Databases so much that couchDB fails to load and I loose UbuntuOne sync functions as well as anything that depends on the Couch DB's

---

### Post by afrodeity on 2012-02-01
Are you saying don't use desktop-couch tools?

---

### Post by freacert on 2012-04-24
Another way to clean up the bookmarks.couch file is
(worked for me!)

[https://answers.launchpad.net/ubuntu/+source/bindwood/+question/162623](https://answers.launchpad.net/ubuntu/+source/bindwood/+question/162623)

You can reduce the size of bindwood's database by:
 * Connecting to your local desktopcouch database (by browsing to /home/USERNAME/.local/share/desktop-couch/couchdb.html)
* Opening the bookmarks database
* Clicking the Compact & Cleanup link, selecting Compact Database,  and clicking Run (this can take a while - you can keep track of its  progress via the Status link to the right)
 Same process works for any other desktopcouch database (e.g. gwibber-messages...)

---

### Post by afrodeity on 2012-04-25
> **freacert said:**
> Another way to clean up the bookmarks.couch file is
(worked for me!)

[https://answers.launchpad.net/ubuntu/+source/bindwood/+question/162623](https://answers.launchpad.net/ubuntu/+source/bindwood/+question/162623)

You can reduce the size of bindwood's database by:
 * Connecting to your local desktopcouch database (by browsing to /home/USERNAME/.local/share/desktop-couch/couchdb.html)
* Opening the bookmarks database
* Clicking the Compact & Cleanup link, selecting Compact Database,  and clicking Run (this can take a while - you can keep track of its  progress via the Status link to the right)
 Same process works for any other desktopcouch database (e.g. gwibber-messages...)

This is what happens if I use the solution
```

Desktop CouchDB

Your desktop CouchDB is the data store for many of your applications. You can browse around it to see which data your applications are storing.

You should bookmark this page (by going to Bookmarks > Bookmark This Page or pressing Ctrl-D) so you can easily come back to browse your CouchDB again.

Don't bookmark the CouchDB page itself, because its location may change!

Taking you to your Desktop CouchDB in 22 seconds... take me there straight away from now on (remember to bookmark this page first!)

```
Oops! Google Chrome could not connect to localhost:45627

---

### Post by freacert on 2012-04-25
> **afrodeity said:**
> 
Oops! Google Chrome could not connect to localhost:45627

And what happens if you open couchdb.html with firefox?

---

### Post by afrodeity on 2012-04-25
waiting for localhost but nothing happens. The take me straight there link not working, wants to go to [http://FvtACtXoEl:XHaAlDLdEN@localhost:45USERNAME627/_utils](http://FvtACtXoEl:XHaAlDLdEN@localhost:45USERNAME627/_utils)

---

