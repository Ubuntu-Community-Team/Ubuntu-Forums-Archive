---
title: "Clueless noob questions (CouchDB, Ubuntu One folder)"
date: 2010-04-08
forum: Ubuntu One (CLOSED)
---

### Post by HankB on 2010-04-08
I've got Ubuntu One syncing my Tomboy Notes and I think I understand what's going on there. I'd like to explore file syncing and I'm just not grokking some of these points and I seem to come up empty handed when I search for information. I've looked at the FAQs and see a reference to an Ubuntu One folder, but I don't know where to look to find more information on that. I presume it is a folder that Ubuntu One can sync (as opposed to just syncing individual files.) How does it get created? Does UO automagically sync it or do I need to configure that?

I see comments that UO will sync all CouchDBs on my system. I wish I knew the implications of that! (e.g. what apps use CouchDB?)

The UO page has an entry for "User Defined Folders." How do I define folders?

I thought I saw comments that hinted at UO integration into Nautilus. Is that true? I've looked but did not find.

I suppose these questions would be answered by a user guide. Don't hesitate to point me in that direction!

If it matters, I'm running 9.10 and using Gnome.

thanks,
hank

Edit: I found the "Ubuntu One" file! I see that it contains the one file I have synced. So I have two copies of this file on my system now. Does that mean I should perform further editing on the original? Or should I use the one in the Ubuntu One folder? Can I delete the original? (Two copies of the same file can only lead to confusion.)

---

### Post by duanedesign on 2010-04-08
> I see comments that UO will sync all CouchDBs on my system. I wish I knew the implications of that! (e.g. what apps use CouchDB?)

you can see the CouchDB databases on your computer by putting the following address into Firefox. Replacing [COLOR="Red"]USERNAME[/COLOR] with your username.

```
file:///home/[COLOR="Red"]USERNAME[/COLOR]/.local/share/desktop-couch/couchdb.html
```

> The UO page has an entry for "User Defined Folders." How do I define folders?
User Designated Folders are available in Lucid. You can Sync any folder in your users home directory by right-clicking and selecting 'Sync with Ubuntu One'

> I thought I saw comments that hinted at UO integration into Nautilus. Is that true? I've looked but did not find.

When you open your Ubuntu One folder you should see a little strip across the top with an option to 'Connect'

I thought rye had a good [blog post]("http://blog.rtg.in.ua/2009/11/ubuntu-one.html") explaining some of the Ubuntu One workings.

---

### Post by HankB on 2010-04-08
Hi Duane (?)
Thanks for the reply.

The CouchDB URL you provided redirects to a service not running on my system. However I see:
```
[Thu, 08 Apr 2010 03:19:24 GMT] [info] [<0.1.0>] Apache CouchDB has started on http://127.0.0.1:58375/

```in /home/hbarta/.cache/desktop-couch/desktop-couchdb.log. when I try to connect to that, it asks for an administrator password which I don't know. So I'm still in the dark WRT CouchDB usage on my system.

I guess I'll have to wait for Lucid for user defined folders.

I checked out the blog entry that you suggested and it does give a good explanation of the background processing that makes this work. It does not tell me which copy of my single synced file I should now work with.

thanks,
hank

---

### Post by HankB on 2010-04-09
I can answer another question. After syncing a file to another PC, I edited it on the other PC and then watched as it was synced to the U1 server. Following this, I watched the two copies on the PC on which the file originated to see which would update. That was yesterday afternoon. This morning neither file on the originating machine had updated. I clicked the Disconnect button on the U1 folder and then clicked it again to reconnect. At that time the copy in the U1 folder updated and the original did not. So it seems that the behavior of the U1 sync at present is to copy the file to the U1 folder and then keep that synced (more or less... It seems that portion of the process is not yet bulletproof.)

The other thing I noticed is that it left the time stamp on the synced copy as the time it synced rather than the time it was modified on the other host.

---

### Post by joshuahoover on 2010-04-12
> **HankB said:**
> I can answer another question. After syncing a file to another PC, I edited it on the other PC and then watched as it was synced to the U1 server. Following this, I watched the two copies on the PC on which the file originated to see which would update. That was yesterday afternoon. This morning neither file on the originating machine had updated. I clicked the Disconnect button on the U1 folder and then clicked it again to reconnect. At that time the copy in the U1 folder updated and the original did not. So it seems that the behavior of the U1 sync at present is to copy the file to the U1 folder and then keep that synced (more or less... It seems that portion of the process is not yet bulletproof.)

You may need to disconnect/reconnect to get files to recognize changes made on the server or another client that is synchronizing files on the same account. This is a server side issue that we need to improve.

> The other thing I noticed is that it left the time stamp on the synced copy as the time it synced rather than the time it was modified on the other host.

You're right, the modified time is when the file synchronized, not the last modified time of the file itself. The reason for this is because we currently do not carry over meta data on the files like modified timestamps, etc.

---

