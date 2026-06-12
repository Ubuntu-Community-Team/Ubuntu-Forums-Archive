---
title: "Firefox tries to download file on every startup"
date: 2012-03-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by matt2053 on 2012-03-13
I downloaded a .deb from Dropbox website. When I tried to open it with Software Center, I got an error about unresolvable dependencies. Anyway, I tried again later and it worked properly. But now, every single time I launch Firefox, it pops up the dialog saying "You have chosed to download file.extension, what would you like to do?" or some such wording. So far, I've tried deleting everything from my Downloads folder, and wiping my Firefox history. What else could I try?

Posting here because I'm using Precise Beta1.

---

### Post by alphacrucis2 on 2012-03-14
Have you tried uninstalling the deb package.

---

### Post by matt2053 on 2012-03-14
Tried it just now at your suggestion. No change in behavior. I think it's a Firefox problem and not a package problem.

---

### Post by Gregory Lee on 2012-03-14
> **matt2053 said:**
> What else could I try?
Try saving it?  Or look in /tmp/ and see if it's there -- if so, delete it.  Well, those are just ideas.

---

### Post by lisati on 2012-03-14
Do you still have the download page open in a tab in Firefox? If so, you might want to navigate to another page in that tab.

---

### Post by matt2053 on 2012-03-14
I have saved it, opened it, canceled it, quit Firefox, wiped history, rebooted machine. It still pops up and tries to download this file every time I launch Firefox or open a new tab.

---

### Post by plucky on 2012-03-14
> **matt2053 said:**
> I have saved it, opened it, canceled it, quit Firefox, wiped history, rebooted machine. It still pops up and tries to download this file every time I launch Firefox or open a new tab.

Have you tried renaming the .mozilla hidden folder to .old-mozilla in your /home directory and then launch Firefox.
This should reset Firefox to a new profile.
You can always revert back to the old profile by reversing the renaming operation. 

You will lose your Bookmarks and History,so make a backup.

Does Dropbox run a sync program like Ubuntu One does on every startup?

Could be that is producing the Popup.

Good Luck

---

### Post by matt2053 on 2012-03-14
> **plucky said:**
> Have you tried renaming the .mozilla hidden folder to .old-mozilla in your /home directory and then launch Firefox.

That did the trick, thanks!

---

