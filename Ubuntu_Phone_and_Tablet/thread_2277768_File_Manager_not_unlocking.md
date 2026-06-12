---
title: "File Manager not unlocking"
date: 2015-05-11
forum: Ubuntu Phone and Tablet
---

### Post by msknight on 2015-05-11
I haven't put my phone in to RW mode yet, but I have downloaded File Manager and when I ask it to go to unlock mode it asks for a password, but no input keyboard pops up.

I would like to just be able to copy some files in to the ringtone directory, but if I can do this without having to RW the whole phone, it would be a distinct bonus. Any ideas please?

---

### Post by msknight on 2015-05-11
Well, it looks like I do need to put it in to RW mode ... not good for a consumer device in terms of adding new ringtones ... but that aside, I can't find the phablet-config command.

...I'm using the terminal on the phone and developer mode is enabled.

---

### Post by lgd on 2015-05-11
Click the password field.

Make the system writable once only.

---

### Post by msknight on 2015-05-11
The password field isn't responding.

I can't find the phablet-config command in order to run it. ... I wonder if ... hmmm ... give me a minute or two to try something.

---

### Post by msknight on 2015-05-11
Nope - even running** sudo phablet-config writable-image** didn't work.

---

### Post by lgd on 2015-05-11
This is only for installation on a pc with connected phone. Look at askubuntu. I only know  a good German wiki. You can use this what your command will do, too:
```

sudo touch /userdata/.writable_image 

```
but this is until you delete the file again and umount it. Better is
```

sudo mount -o remount,rw / 

```
and then umount it, after your ringtones are there:
```

sudo umount /

```

---

### Post by msknight on 2015-05-12
Thanks I'll give that a try tonight.

---

