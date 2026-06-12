---
title: "[SOLVED] How to reverse a command.."
date: 2008-04-13
forum: The Cafe
---

### Post by Merovius on 2008-04-13
How can i reverse this command or at least go back to my old mozilla folder??

mv .mozilla .mozilla_old

I used it to fix another issue (it did) but didn't realize I would lose everything in Firefox.

TIA

---

### Post by Claus7 on 2008-04-13
Hello,

mv .mozilla_old .mozilla

Regards!

---

### Post by Merovius on 2008-04-13
Thanks for the direction.  Didn't seem to work though. I guess I need to put Firefox back together again from scratch. Thank god I exported my favorites not to long ago. I will only lose the most recent ones. Favorites was what i hoped to get back. 

Thanks again anyway!

---

### Post by LaRoza on 2008-04-13
> **Merovius said:**
> Thanks for the direction.  Didn't seem to work though. I guess I need to put Firefox back together again from scratch. Thank god I exported my favorites not to long ago. I will only lose the most recent ones. Favorites was what i hoped to get back. 

Thanks again anyway!

If a default .mozilla directory were created, delete it then change the name of the other to the proper name.

(Also, open Nautilus and press Ctrl + h to do it in a GUI)

If you didn't restart Firefox, do it.

---

### Post by Claus7 on 2008-04-13
Hello,

you do not have to thank me. The good would have been to have your browser back as it was. If you haven't done anyhting else I think that this should have worked. In this folder (.firefox_old) there is no folder that has your favourites? I think that in /.mozilla/firefox/w6pgom85.default or /.mozilla_old/firefox/w6pgom85.default , depending on what you did with the move command you will find all your bookmarks. I would advice you to search there first. Also in /.mozilla/firefox/w6pgom85.default/bookmarkbackups you will find them by date.

Hope this helped!
Regards!

---

### Post by Acglaphotis on 2008-04-13
how about:

```

cp .mozilla_old/firefox/[heregoesyourprofilename]/* .mozilla/firefox/[newprofile]

```

Or something like that.

---

### Post by Merovius on 2008-04-13
Claus7, 

I browsed were you told me and found a backup from today that had all my old favorites. I'm good to go now.

Thanks for certain this time.  :)

---

