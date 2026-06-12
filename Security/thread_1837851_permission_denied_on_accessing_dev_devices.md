---
title: "permission denied on accessing /dev/* devices"
date: 2011-09-02
forum: Security
---

### Post by koda on 2011-09-02
Hi all,
I'm trying to access the various input nodes by doing
```
$ cat /dev/input/mouse0
```
However every kind of command ends with "Permission Denied".

I'm quite sure of being able to run these kind of commands in the past and several tutorials around mention that it should be possible to do so.

What happened? Did the security policy for accessing /dev/input changed?
How do I restore the old behaviour *without* using sudo chown or similar?

Koda

---

### Post by 2F4U on 2011-09-02
What about placing "sudo" in front of the command?

---

### Post by cariboo on 2011-09-02
Even better, use:

```
sudo -i
```

---

### Post by koda on 2011-09-03
I have to deploy this to users that don't have sudo access...

---

### Post by agillator on 2011-09-03
Then you would need to make them a member of the root group or change the permissions or ownership of /dev/input/mouse0 it seems to me. But from what you have said, I suspect you cannot do that. Why do they need access and what kind of access?

---

### Post by koda on 2011-09-04
Actually, I was trying to implement this feature [http://stackoverflow.com/questions/3649874/how-to-get-keyboard-state-in-linux/4225290#4225290](http://stackoverflow.com/questions/3649874/how-to-get-keyboard-state-in-linux/4225290#4225290) first; then i realized that no cat command worked either.
I was just puzzled by this policy change and wanted to shed some light on the reasons behind it.

---

### Post by koda on 2011-09-06
umh bump?

---

