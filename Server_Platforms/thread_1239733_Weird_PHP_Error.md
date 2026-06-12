---
title: "Weird PHP Error"
date: 2009-08-13
forum: Server Platforms
---

### Post by animuson on 2009-08-13
> 
Warning: Unknown: write failed: No space left on device (28) in Unknown on line 0

Warning: Unknown: Failed to write session data (files). Please verify that the current setting of session.save_path is correct (/var/lib/php5) in Unknown on line 0


What does this mean, how do I make it go away?

---

### Post by razzbar on 2009-08-14
I don't think you've provided enough information for anybody to help you. What were you doing, when does it happen, etc.

---

### Post by dmalcomd on 2009-08-14
> **razzbar said:**
> I don't think you've provided enough information for anybody to help you. What were you doing, when does it happen, etc.

Quote razzbar, maybe check filesystem isn't in read only (sometimes happens!)

---

### Post by hessiess on 2009-08-14
The drive storing the filesystem for /var/lib/php5 is lickly full or read-only.

---

### Post by wojox on 2009-08-14
You need to 

```
locate php.ini
```

Then open it and look for session.save_path and correct it from there.

---

