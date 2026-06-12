---
title: "Configuring samba"
date: 2011-06-24
forum: Server Platforms
---

### Post by Vakz on 2011-06-24
Hello.

I am helping a teacher set up a small server for himself and his students (they're all 10 to 12 years old).

Simply enough, all I want is Ubuntu with samba. As the kids are young, we wanted it to be as simple as possible (they're currently using dropbox, but the school doesn't like using 3rd party, as it's considered insecure whenever the "top man" isn't an employee of the school).

The idea was that the kids will keep their stuff in their home folders, by creating a user for each of the children, and then network drive the home folder (they use Windows 7 on their laptops). That was simple enough. But my friend wants to be able to go into the folders, to be able to read what they're doing, leave comments, etc. So, the kids should have access to /home/<username>, while my friend should have access to simply /home. How can I configure samba to give his user access to /home, preferably as default?

---

### Post by Jake.Debord on 2011-06-24
I would make the /homes directory shared, then add the user to the read/wright access list in samba for that folder

---

### Post by Vakz on 2011-06-24
What should I add to smb.conf to give him the proper permissions and such?

---

### Post by Jake.Debord on 2011-06-24
Are you on a headless server? (no gui)?

---

### Post by Vakz on 2011-06-24
Ya, using the server edition.

EDIT: I just realized; could I configure samba through webmin? Feels like this should make things more simple for my friend as well, as he has pretty much never touched a linux system in his life.

---

### Post by Jake.Debord on 2011-06-24
Yes, webmin will make it easy as pie. Just locate the shared folder, go to security and access control and add his user to the possible users list

---

### Post by kevinthecomputerguy on 2011-06-24
Excellent way
 
Page 3, halfway down has a guide on Samba \ webmin
 
[http://woodel.com/page3](http://woodel.com/page3)

---

