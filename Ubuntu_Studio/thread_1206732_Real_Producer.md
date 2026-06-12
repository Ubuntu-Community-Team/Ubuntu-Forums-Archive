---
title: "Real Producer"
date: 2009-07-07
forum: Ubuntu Studio
---

### Post by jonathanpeter on 2009-07-07
I'm trying to get real producer working on ubuntu (I was using Fedora before and it worked perfectly).

I've installed the application to /usr/local/producer11

The main executable is called "producer" and it can be run from the command line.

When I do

cd /usr/local/producer11
./producer blah blah

I get:

"/usr/local/producer11/producer: not found"

producer does exist and I have executable permissions.  Any ideas?

---

### Post by raboofje on 2009-07-07
> **jonathanpeter said:**
> ```
$ cd /usr/local/producer11
$ ./producer blah blah
/usr/local/producer11/producer: not found
```

producer does exist and I have executable permissions.  Any ideas?

Is this a shell script? Could you post the first few lines (especially the one starting with '#!')?

I think I've seen this error message come up when the interpreter specified on the '#!' line does not exist.

---

### Post by rotten777 on 2009-07-07
> **jonathanpeter said:**
> I'm trying to get real producer working on ubuntu (I was using Fedora before and it worked perfectly).

I've installed the application to /usr/local/producer11

The main executable is called "producer" and it can be run from the command line.

When I do

cd /usr/local/producer11
./producer blah blah

I get:

"/usr/local/producer11/producer: not found"

producer does exist and I have executable permissions.  Any ideas?


You've done the obvious chmod +x to ensure it is set as an executable?

Try it without flags.

Also check to see if it is a link to another location and if so make sure it is valid.

---

