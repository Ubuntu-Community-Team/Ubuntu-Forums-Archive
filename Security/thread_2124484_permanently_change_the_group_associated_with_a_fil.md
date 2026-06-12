---
title: "permanently change the group associated with a file system object"
date: 2013-03-11
forum: Security
---

### Post by fab333 on 2013-03-11
My problem is that if the user 'ross' change the group associated with a file from 'ross' to 'friends', 
but then 'ross' enter in the file and save it, it'll be again results in the 'ross' group, and not longer to 'friends'.
So every time that 'ross' makes a change in the file (in a editor, emacs generally), 
have to chgrp the file every time, to make available the file to the all members of 'friends'.
Does exist a method to make the change in the group associated with a file permanent,
so to avoid to use chgrp every time that someone of the group re-save the file?

Thanks

---

### Post by apmcd47 on 2013-03-11
How is ross changing the file? Is he using an editor? If so, which editor?

Andrew

---

### Post by fab333 on 2013-03-11
generally emacs

---

### Post by Morbius1 on 2013-03-11
This is why the UNIX gods created setgid.

On the directory that you are sharing with other members of the friends group - let's call it /home/shared:

Change the group of the shared folder to friends:
```
 sudo chown :friends /home/shared
```
Change permissions to one of the following:
```
sudo chmod 2775 /home/shared
```
This will force all new files to "inherit" the group of the parent folder - in this case: friends.
Or this one:
```
sudo chmod 3775 /home/shared
```
Same as above only this will prevent anyone other than the owner of the saved file from deleting it.

---

### Post by apmcd47 on 2013-03-11
> **fab333 said:**
> generally emacs
Odd. I don't have emacs so I can't confirm. Nobody is deleting or renaming the file while it is being edited?
> **Morbius1 said:**
> This is why the UNIX gods created setgid.
No, because once it is changed, it shouldn't keep changing back.  It is however meant for setting the default group in a particular directory so that users don't have to use the *newgrp* or *chgrp* command when creating shared files, and it should probably be used if the file is in such a specialist directory.

Andrew

---

