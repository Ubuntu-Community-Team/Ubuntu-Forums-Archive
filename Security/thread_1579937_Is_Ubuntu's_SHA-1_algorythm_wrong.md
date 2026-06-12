---
title: "Is Ubuntu's SHA-1 algorythm wrong?"
date: 2010-09-22
forum: Security
---

### Post by HDave on 2010-09-22
If I enter the following at a command line:

```
echo admin | sha1sum
```

The result I get is:

```
4015bc9ee91e437d90df83fb64fbbe312d9c9f05
```

However, [a quick google ]("http://www.sha1-lookup.com/index.php?q=d033e22ae348aeb5660fc2140aec35850c4da997") will tell you that the real value should be:

```
d033e22ae348aeb5660fc2140aec35850c4da997
```

What gives?  There is a discrepancy for SHA-256 as well.

---

### Post by The Cog on 2010-09-22
Wild guess, but the echo command adds a newline to the string as it prints it. Maybe that's the explanation?

---

### Post by sisco311 on 2010-09-22
> **The Cog said:**
> Wild guess, but the echo command adds a newline to the string as it prints it. Maybe that's the explanation?

Correct!

```
echo -n admin | sha1sum 
d033e22ae348aeb5660fc2140aec35850c4da997  -

```

---

### Post by dynamo2 on 2010-09-22
Ubuntu's SHA-1 algo's not wrong, your using it the wrong way. 
e.g - if i do in a terminal:

sha1sum 

then type in admin

then 2 ctrl-d's

output is: d033e22ae348aeb5660fc2140aec35850c4da997

---

### Post by CharlesA on 2010-09-22
Did an sha1sum on an iso using ubuntu and hash calc and it looks the same.

```
charles@thor:~/.VirtualBox$ sha1sum ubuntu-10.04.1-desktop-i386.iso
c413b150859cdc49ddd86bfd890216e6e084e034  ubuntu-10.04.1-desktop-i386.iso

```

---

### Post by HDave on 2010-09-22
> **The Cog said:**
> Wild guess, but the echo command adds a newline to the string as it prints it. Maybe that's the explanation?

Precisely it!  :popcorn:

---

### Post by sisco311 on 2010-09-22
Don't forget to mark this thread as solved. Thanks!

---

