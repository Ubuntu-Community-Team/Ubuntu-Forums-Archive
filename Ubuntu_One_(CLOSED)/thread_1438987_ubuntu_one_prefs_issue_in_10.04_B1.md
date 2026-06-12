---
title: "ubuntu one prefs issue in 10.04 B1"
date: 2010-03-25
forum: Ubuntu One (CLOSED)
---

### Post by wokandabirder on 2010-03-25
Not sure if this is a bug that needs posting...

running 10.04 beta 1 and cannot manage U1 account through preference pane. Tried remove/reinstall and delete .conf no change.

Attached is error png

---

### Post by joshuahoover on 2010-03-26
> **wokandabirder said:**
> Not sure if this is a bug that needs posting...

running 10.04 beta 1 and cannot manage U1 account through preference pane. Tried remove/reinstall and delete .conf no change.

Attached is error png

This is a known error that we should have fixed by early next week. I think you can get around this by deleting the following config file: ~/.config/ubuntuone/syncdaemon.conf

Thank you,

Joshua

---

### Post by jaco223 on 2010-03-28
Running lucid beta 1 here Josh, ubuntu one client won't even start up from >preferences >ubuntu one.
I deleted the syncdaemon.conf file with no result.

---

### Post by wokandabirder on 2010-03-28
Thanks Joshua. 

Ubuntu One was working great under 9.10, and I'm sure that there are a few kinks to work out in Beta process of 10.04. CouchDB sync issues seem to be in the mix too. UbuntuOne is a great product and service. Keep up the great dev work.  I'll keep my eyes on things and post bug reports as need be.

---

### Post by wokandabirder on 2010-03-28
I didn't have the problems others are experiencing with the pref pane not starting up. Mine started up fine, but wasn't showing correct info, or synching.

I did the reinstall procedure Josh outlined in this thread:
[http://ubuntuforums.org/showthread.php?t=1297076&referrerid=1042836](http://ubuntuforums.org/showthread.php?t=1297076&referrerid=1042836)

I did my beta install via dirtro upgrade from 9.10 where U1 was working properly.

---

### Post by jaco223 on 2010-03-28
I reinstalled ubuntu one, I was able to start from>preferences>ubuntu one, the client started and showed my  login info, I was able to connect to "device", but the next tab for syncing remains grayed out, not able to sync files, or folders.

---

### Post by joshuahoover on 2010-03-29
> **jaco223 said:**
> I reinstalled ubuntu one, I was able to start from>preferences>ubuntu one, the client started and showed my  login info, I was able to connect to "device", but the next tab for syncing remains grayed out, not able to sync files, or folders.

Are you referring to the "Services" tab? If so, this tab is not functioning yet. It should be with our next update (next few days). If you are able to connect then you should be able to sync files. If you put a file in your ~/Ubuntu One folder what happens?

Thank you,

Joshua

---

### Post by wokandabirder on 2010-04-02
Just an update...

Everything is now working for me. I was getting some evolution-data-server crashes yesterday when trying to pull up ubuntu-one contact list, but that now also seems to be working.

Thanks to the team for the diligent work!

---

