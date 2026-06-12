---
title: "New BQ Aquaris M10 user with some questions"
date: 2016-05-03
forum: Ubuntu Phone and Tablet
---

### Post by icewater on 2016-05-03
I just received my Aquaris M10 today, and overall I'm thrilled to have it.  I have a few questions.

How do I uninstall Facebook Photos (or other apps that don't seem to allow that option by click-hold of the icon)?  I'm looking to remove the code from my device, not hide or "disable" it.

How do I install a trusted root certificate on the device so that it recognizes the certificates I've created for my personal sites?

How can I safely set up an ssh server on my tablet?

Is there any (secure) way to control the tablet directly from my laptop keyboard?

Is there a preferred/possible way to synchronize files with another personally-owned Linux machine?

Are error logs available for applications (in particular, at the moment, the Browser app)?  I have trouble logging into the web interface of my owncloud instance.

And, finally: the BQ pattern in metal dots on the front is labeled "capacitive button" in the documentation.  Is it currently used for anything?  Is it just there for app developers to take advantage of it if they like? 


TIA for any info / suggestions!

---

### Post by KFoder on 2016-05-03
You can uninstall most programs (including Facebook photos) from the Ubuntu app store, it can be filtered to only show installed programs, from there it's easy to remove unwanted programs.

It is somewhat buggy, and you may have to reload it a couple of times if you want to remove many programs.

---

### Post by The_Woodpecker on 2016-05-03
I would have thought that most of that can be done through the store. as for error logs in the Browser app. I don't know, I find it quite buggy on my laptop. Although it may be different on the tablet. 
For syncing/file sharing just use the folder sharing option

---

### Post by icewater on 2016-05-03
I see no Facebook icon in the Ubuntu Store.  Yet, when I go to "System Settings | Updates" there is an update for "Facebook Photos" waiting.  I want to uninstall this completely.  Is there a way?

Where is the "folder sharing" option?

---

### Post by jyoti3 on 2016-05-03
Icewater, "Facebook photos" is a scope, it does not appear in the list of apps of your tablet/phone but in the scopes list (the scopes list appears if you slide the finger up). To uninstall it, go to the Ubuntu store and search for "facebook scope" ... maybe these links will help, if you can not find easily:


scope://com.canonical.scopes.clickstore?q=Facebook%20Photos%20Scope

[https://uappexplorer.com/app/com.canonical.scopes.fbphotos](https://uappexplorer.com/app/com.canonical.scopes.fbphotos)

You can also write "canonical" in the Ubuntu store and search the scopes made by Canonical. Then just click to uninstall.

---

### Post by icewater on 2016-05-03
jyoti3, thanks, I found it and uninstalled it  :-)

Actually I have noticed a couple of times in different contexts I have thought that the list of items/options/whatever that were presented to me initially were the only options available, when a search would have found what I wanted or more items.  It might be worthwhile to make it more obvious to users that what's displayed is a subset and additional items are available through search.

---

### Post by Tao_Joannes on 2016-05-06
On the second part of your question I'm in the same boat.

from what I gather the best practice is setting up a container with libertine as described in the problems with apt-get thread

---

### Post by krusty8 on 2016-05-16
> **Tao_Joannes said:**
> On the second part of your question I'm in the same boat.

from what I gather the best practice is setting up a container with libertine as described in the problems with apt-get thread

I guess [this is the thread you were referring to]("http://ubuntuforums.org/showthread.php?t=2323131").

---

