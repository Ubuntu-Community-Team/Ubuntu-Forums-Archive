---
title: "Revelation PW Manager Error Nightmare!"
date: 2009-02-21
forum: Security
---

### Post by Jimmy9pints on 2009-02-21
I started using revelation a while back and had been very happy with it. Increasingly, as the list of passwords got ever-longer, I started to rely on it more and more. To increase security I started generating random (and therefore unmemorable)  passwords with it. Last night, all of a sudden, it wouldn't open my rev_settings file!

The error message is:
```
Invalid file format

The file '/home/jam/Revelation/rev_settings' contains invalid data.
```

Now I can't access any of my passwords!

Is there anything I can do to recover this seemingly corrupt data.

Any help greatly appreciated.

James.

---

### Post by brian_p on 2009-02-22
> **Jimmy9pints said:**
> 

Is there anything I can do to recover this seemingly corrupt data.


I won't mention restoring from a backup but you could think along the lines of some possible recent python library update being a cause.

The man page for the application is useless so I'm guessing /home/jam/Revelation/rev_settings is a file created by you and it contains the passwords encrypted with AES - which makes it undecipherable.

---

### Post by Jimmy9pints on 2009-02-23
So in short Brian, you answer is "no"?

Well I hope that I don't have the same problems with the new software I am using, Lastpass.

---

### Post by brian_p on 2009-02-24
> **Jimmy9pints said:**
> 

So in short Brian, you answer is "no"?


If the file has truly been corrupted 'yes'. But, if not, being a little optimistic and rolling back the python library versions might be productive.

---

