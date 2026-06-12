---
title: "[SOLVED] Internet History"
date: 2008-05-14
forum: Ubuntu Christian Edition
---

### Post by Pursuer on 2008-05-14
You all have been so helpful, so I am assuming you would know how I can do this.
I am wondering if I can prohibit my internet history from being deleted. Also, is there a way to find any internet history that has been deleted, elsewhere on my computer?
I am having issues and don't even know where to find the cache files. I used to be able to find them easily on Windows, but I am obviously not using that anymore! :)
Thank you in advance for any help you can give me!

---

### Post by MaindotC on 2008-05-14
I think you are referring to browsing history, and that would probably be through Firefox, your web browser, right?  You can prevent your browsing history from being deleted by opening Firefox and selecting Edit -> Preferences.  In the Preferences menu, select the "Privacy" button that is in the shape of a padlock.  Near the bottom you'll see a box labeled "Private Data".  You can select (or unselect) "Always clear my private data when I close Firefox" and choose "Settings" to choose what it should and should not allow.

You can access the cache by typing in the browser:
```

about:cache

```

Let me know if you need more help.

---

### Post by Pursuer on 2008-05-14
I guess I need to be a bit more specific... sorry about that.
On Windows when my internet history would be deleted, I could still go to I think it was Cache... and I would still be able to view sites that had been deleted (it was not/is not me doing the deleting) through the internet history.
Is there a way for me to do that on here?
Thank you for answering me so quickly, too. :)

---

### Post by MaindotC on 2008-05-14
Yes you can access those files by typing in Firefox:
```

about:cache

```
The cache directory is usually  /home/your_user_name/.mozilla/firefox/qxc228ug.default/Cache

---

### Post by Pursuer on 2008-05-14
I did that and the only results I got were from this morning (it's very early here) and yesterday, after the history was deleted, nothing else.
I should be getting more of it then?

---

### Post by MaindotC on 2008-05-14
If you follow the directions I posted in my first post regarding Firefox then you should retain your browsing history from now on.  Did you already have firefox configured that way?

---

### Post by Pursuer on 2008-05-14
I did that. From now on it should be traceable through cache now, even if the history gets deleted? Thank you so much!!

---

