---
title: "Python is too smart for its own good..."
date: 2011-04-11
forum: The Cafe
---

### Post by kevin11951 on 2011-04-11
My computer has 2GB of RAM...  So,

I created a 4GB file using "dd" and then tried to use the "open()" and "read()" functions in python to try to load it into memory...

Python's reply?

```
OverflowError: line is longer than a Python string can hold
```

Does anyone know of a way to force Python to load a file into memory at all costs?

---

### Post by 3Miro on 2011-04-11
Obviously you cannot fit a 4GB file on a 2GB machine. Are you deliberately trying to break things.

If you have to process that file, try reading the file a chunk at a time (i.e. 100MB at a time or something like that).

---

### Post by RiceMonster on 2011-04-11
> **3Miro said:**
> Obviously you cannot fit a 4GB file on a 2GB machine. Are you deliberately trying to break things.

If you have to process that file, try reading the file a chunk at a time (i.e. 100MB at a time or something like that).

If it's a text file, it can also be read line by line (not the case here, though).

Loading an entire file into memory is generally not a good idea.

---

### Post by BrokenKingpin on 2011-04-11
> **3Miro said:**
> Obviously you cannot fit a 4GB file on a 2GB machine.
This is why there is swap partitions.

---

### Post by szymon_g on 2011-04-11
are you using 32 or 64 bit system (i.e. kernel + everything including python)?

---

### Post by kevin11951 on 2011-04-11
Forgot to mention, but yes, I am doing this to mess around, not any real purpose...

---

### Post by kevin11951 on 2011-04-11
> **3Miro said:**
> Obviously you cannot fit a 4GB file on a 2GB machine. **Are you deliberately trying to break things.**

If you have to process that file, try reading the file a chunk at a time (i.e. 100MB at a time or something like that).

Yes... :P

> **szymon_g said:**
> are you using 32 or 64 bit system (i.e. kernel + everything including python)?

32bit

---

### Post by szymon_g on 2011-04-11
> **kevin11951 said:**
> 32bit

than it is your answer /i think/. ah, btw, are you sure you have got enough memory /i mean: ram + swap/?

---

### Post by 3Miro on 2011-04-11
> **BrokenKingpin said:**
> This is why there is swap partitions.

Assuming one exists, and then things would be very slow. It will make all other programs slow to a raw as Linux will try to swap them first before it starts swapping the large file. 

Chunk by chunk is a better way.

Also, on a 32-bit machine, you probably cannot have an array (or in this case string) bigger than 4GB. It has to be indexed and it can only be indexed by a 32-bit integer (limited to 2^32 = 4GB).

---

### Post by tgm4883 on 2011-04-11
> **BrokenKingpin said:**
> This is why there is swap partitions.

While that is true. It's generally considered bad programming to try and load the full file into memory. 

That being said, is the file text? If so, you can process the file in other ways. If not, then IDK why you are getting a string error.

---

