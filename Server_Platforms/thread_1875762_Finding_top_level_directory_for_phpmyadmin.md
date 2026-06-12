---
title: "Finding top level directory for phpmyadmin"
date: 2011-11-05
forum: Server Platforms
---

### Post by quadrantids on 2011-11-05
I'm using phpMyAdmin on Ubuntu 11.10: could someone please tell me where the top level directory is for phpmyadmin on Ubuntu? (I want to create the "config" writable folder: there seem to be phpmyadmin folders in etc and in usr/share.

---

### Post by CharlesA on 2011-11-05
The folders are stored in /usr/share

---

### Post by quadrantids on 2011-11-06
Thanks, but I'm still having trouble: could you please tell me what Terminal commands to issue to be able 
to write to this directory and then
to create the "config" folder and finally
to restore the security in the same directory?

---

### Post by CharlesA on 2011-11-06
You'd have to create a directory with sudo and then chown them to root.

```
sudo mkdir /usr/share/phpmyadmin/config
```
```
sudo chown root:root /usr/share/phpmyadmin/config
```

Just be careful not to change permissions of anything else.

---

### Post by quadrantids on 2011-11-07
Thanks: I now have the "config" folder but I still get the warning from the setup home page "cannot load or save configuration". What am I doing wrong?

(I should say that the latest phpmyadmin on ubuntu 11.10 uses labels and icons when browsing tables and there's not enough room on my screen so I want to set icons only.)

---

### Post by CharlesA on 2011-11-07
I've never heard of that happening before.

Can you run this please:

```
ls -ld /usr/share/phpmyadmin/config
```

The Ubuntu wiki says to run chmod o+rw config, so it's world writable.

---

### Post by quadrantids on 2011-11-07
This is what I get (see attachment).

---

### Post by CharlesA on 2011-11-07
Yeah, run the chmod command I posted earlier.

That should get it working.

---

### Post by quadrantids on 2011-11-07
I hate to appear dumb but I can't see that you did post a chmod (do you mean chown the same?)

So what would the command be for chmod?

I appreciate you help.

---

### Post by CharlesA on 2011-11-07
> **quadrantids said:**
> I hate to appear dumb but I can't see that you did post a chmod (do you mean chown the same?)

So what would the command be for chmod?

I appreciate you help.

```
sudo chmod o+rw /usr/share/phpmyadmin/config
```

---

### Post by quadrantids on 2011-11-07
I've run the chmod (see attachment) and now when I go to localhost/phpmyadmin/setup, the setup overview page shows WITHOUT asking for my username and password, but still saying "cannot load or save configuration"...

---

### Post by CharlesA on 2011-11-07
Don't know that else to do then.

I haven't really had to configure phpmyadmin in that way.

Have you purge and reinstalled it?

---

