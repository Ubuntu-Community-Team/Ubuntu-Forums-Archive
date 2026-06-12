---
title: "bookmarks and browser performance?"
date: 2011-12-15
forum: The Cafe
---

### Post by Matrix01 on 2011-12-15
does web browser run faster when bookmarks are erased?

---

### Post by ajgreeny on 2011-12-15
No.  Do you think they slow your browser down significantly?

Bookmarks are only used or queried when you click on one, the rest of the time they just sit there as an unused file in your browser profile.

---

### Post by stonewilson on 2011-12-16
*aj* is right, bookmarks on your browser won't slow your browser down, try to erase the cookies browser has saved, they may slow your browser down.

---

### Post by lovinglinux on 2011-12-16
> **ajgreeny said:**
> No.  Do you think they slow your browser down significantly?

Bookmarks are only used or queried when you click on one, the rest of the time they just sit there as an unused file in your browser profile.

In fact, they do.

Bookmarks are usually stored on sqlite databases and not static files that just sits there in your profile. If you have tons of bookmarks and, most importantly, if you delete bookmarks very often, the database can become really slow. This affects Firefox startup, typing urls in the address bar and other stuff that rely on querying the bookmark database. A bookmark database full of left-overs can decrease browser performance considerably.

I strongly recommend keeping your bookmark database optimized, by vacuum it regularly. You can do that with BleachBit, [an extension](https://addons.mozilla.org/en-US/firefox/search/?q=vacuum&cat=all) or [a script](http://www.webgapps.org/tutorials/firefox/optimization/database-optimization).

---

### Post by ajgreeny on 2011-12-17
> **lovinglinux said:**
> In fact, they do.

Bookmarks are usually stored on sqlite databases and not static files that just sits there in your profile. If you have tons of bookmarks and, most importantly, if you delete bookmarks very often, the database can become really slow. This affects Firefox startup, typing urls in the address bar and other stuff that rely on querying the bookmark database. A bookmark database full of left-overs can decrease browser performance considerably.

I strongly recommend keeping your bookmark database optimized, by vacuum it regularly. You can do that with BleachBit, [an extension]("https://addons.mozilla.org/en-US/firefox/search/?q=vacuum&cat=all") or [a script]("http://www.webgapps.org/tutorials/firefox/optimization/database-optimization").
Thanks for that, lovinglinux, I stand corrected.  I have used the shell script you linked to myself a few times in the past, and admit that I forgot about the database now used for bokmarks;  I was still thinking html files.

Silly me!

Nevertheless, I never saw any noticeable difference in speed or performance of Firefox when I used the script, and I do have quite a lot of bookmarks, though I seldom delete any of them.

---

### Post by lovinglinux on 2011-12-17
> **ajgreeny said:**
> Thanks for that, lovinglinux, I stand corrected.  I have used the shell script you linked to myself a few times in the past, and admit that I forgot about the database now used for bokmarks;  I was still thinking html files.

Silly me!

Nevertheless, I never saw any noticeable difference in speed or performance of Firefox when I used the script, and I do have quite a lot of bookmarks, though I seldom delete any of them.

I have seen a lot of difference in the past, but since I keep the database optimized, I also don't see much difference nowadays. However, since my script vacuums all databases in the profile, I do feel difference with some extensions that store a lot of data on databases. They can slow down Firefox as well.

Another thing to consider is that the performance compromise will be more evident on systems with slow hard drives.

---

### Post by Matrix01 on 2011-12-18
Does browsing history need to be cleared as well?

---

### Post by lorin30 on 2011-12-18
Even better, if you have the memory, try caching your profile in RAM as detailed here:  [http://ubuntuforums.org/showthread.php?t=1120475](http://ubuntuforums.org/showthread.php?t=1120475)
The writeup is a couple years old but I've used it on 11.10/FF 8 and the speed difference is amazing.  About:config, history and bookmarks load more or less instantaneously.

---

### Post by lovinglinux on 2011-12-18
> **Matrix01 said:**
> Does browsing history need to be cleared as well?

History can add a lot of data to the database and thus could slow it down. However I am not sure how big the history need to be to affect performance. If you are experiencing low performance, backup *place.sqlite* database and delete the history to see if you experience any improvement. Probably just vacuum the database will do tho.

---

### Post by LinuxFan999 on 2011-12-18
Besides clearing bookmarks and history, it would be a good idea to clear the browsing cache too, as letting it fill up not only affects speed, but stability too. I have noticed that certain browsers crash more frequently (a notable example is Safari) if the cache is allowed to fill up, so it is a good idea to clear that too.

---

### Post by del_diablo on 2011-12-18
Amount of bookmarks is not a issue even on a Atom Netbook. Deleting them just convinces you that its good, so you get placebo.

---

### Post by Matrix01 on 2011-12-18
i am on atom netbook.

> **del_diablo said:**
> Amount of bookmarks is not a issue even on a Atom Netbook. Deleting them just convinces you that its good, so you get placebo.

---

### Post by Matrix01 on 2011-12-18
how do u clear browsing cache?

> **LinuxFan999 said:**
> Besides clearing bookmarks and history, it would be a good idea to clear the browsing cache too, as letting it fill up not only affects speed, but stability too. I have noticed that certain browsers crash more frequently (a notable example is Safari) if the cache is allowed to fill up, so it is a good idea to clear that too.

---

### Post by bikeboy on 2011-12-19
> **lovinglinux said:**
> In fact, they do.
I strongly recommend keeping your bookmark database optimized, by vacuum it regularly. You can do that with BleachBit, [an extension](https://addons.mozilla.org/en-US/firefox/search/?q=vacuum&cat=all) or [a script](http://www.webgapps.org/tutorials/firefox/optimization/database-optimization).

Fairly sure Firefox does those optimisations itself these days, based on appropriate criteria.

---

