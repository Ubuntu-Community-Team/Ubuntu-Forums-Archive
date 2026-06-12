---
title: "How does delete behave?"
date: 2009-09-13
forum: Ubuntu One (CLOSED)
---

### Post by osomphane on 2009-09-13
When you delete a file, does it go away on all machines or does it get moved to the thrash can?

---

### Post by indigoshift on 2009-09-15
Delete doesn't work for me at all.  Then again, I'm doing it all through Firefox because my system's not updated at all.  Still using the initial Hardy.

---

### Post by Vishal Agarwal on 2009-09-15
There are two different commands.
1. Move to trash
2. Delete

If you opt first one, it is moved to trash and with the second option it's get deleted. with the first option you can recover the file but with the second on you cannot. If u want to delete any file permanently, then move it to trash and then open the trash and delete it. This is the most safest way to do it.

---

### Post by joshuahoover on 2009-09-15
> **osomphane said:**
> When you delete a file, does it go away on all machines or does it get moved to the thrash can?

When you delete a file in your ~/Ubuntu One folder, the file will be deleted across all those machines sharing that account the next time they sync. 

Thank you,

Joshua

---

### Post by joshuahoover on 2009-09-15
> **indigoshift said:**
> Delete doesn't work for me at all.  Then again, I'm doing it all through Firefox because my system's not updated at all.  Still using the initial Hardy.

This is true. There is a current bug in the web interface that prevents deleting files from working. We should be fixing this very soon. Thanks! -Joshua

---

### Post by osomphane on 2009-09-15
So, can you opt to Move to Thrash stuff in your UbuntuOne folder? If you Move to Thrash, do all computers use the move to thrash command upon sync or do they delete the file entirely?

---

### Post by joshuahoover on 2009-09-18
> **osomphane said:**
> So, can you opt to Move to Thrash stuff in your UbuntuOne folder? If you Move to Thrash, do all computers use the move to thrash command upon sync or do they delete the file entirely?

Good question. :-) Once you move a file to the trash Ubuntu One will delete it across the cloud and all other computers setup to sync on that account.

---

### Post by Findarato on 2009-09-19
> **joshuahoover said:**
> Good question. :-) Once you move a file to the trash Ubuntu One will delete it across the cloud and all other computers setup to sync on that account.

I guess the file only gets put in the "trash" of the computer that actually deleted it though, right ? (It doesn't appear in the trash of all the computers across the cloud)

---

### Post by osomphane on 2009-09-21
I think modifying this to send the file to thrash on all clients would be good in the case where a malicious user gains access to one of your computers and decides to do away with all your files... I know Live Mesh will send to recycle bin, too.

---

### Post by joshuahoover on 2009-09-25
> **Findarato said:**
> I guess the file only gets put in the "trash" of the computer that actually deleted it though, right ? (It doesn't appear in the trash of all the computers across the cloud)

Ubuntu One deletes the file once it is moved out of the ~/Ubuntu One folder. There is currently no concept of a synchronized "trash".

---

### Post by osomphane on 2009-11-02
I didn't mean a synchronized thrash... Rather a deletion will send items to the thrash can, not delete them outright. This can help prevent people from maliciously/accidentally deleting stuff on every machine they sync.

Recovering items from thrash would cause them to be newly synced across systems, but all other systems also have the original in the trash.

---

