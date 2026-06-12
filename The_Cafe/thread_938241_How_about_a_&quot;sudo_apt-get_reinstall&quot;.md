---
title: "How about a &quot;sudo apt-get reinstall&quot; ?"
date: 2008-10-04
forum: The Cafe
---

### Post by emshains on 2008-10-04
In terms of making the work with the system faster, I would like to see apt-get would get a new funtion of reinstalling. When I am trying to get something to work, or trying to do that again, usually I must reinstall a program or a library to get it configured right, so it really drives me mad, when I have to write all the command from the beginning just because it can't do "reinstalling". Although there is the --reinstall or something like that I'd rather see a stand alone function, just because of the typing. I see this as a way to make the system more work-friendly.

---

### Post by Sef on 2008-10-04
moved to community cafe.

---

### Post by doorknob60 on 2008-10-04
Two options:

```
sudo aptitude reinstall packagename
```

or

```
sudo apt-get install --reinstall packagename
```

IIRC anyways, I use Arch now :)

---

### Post by dammn on 2012-02-20
I had similar issue. Solved by:

apt-get install --reinstall linux-libc-dev

In general looks like upgrade messed up with symlinks etc so it has to be "regenerated" for upgraded systems.

---

### Post by Iowan on 2012-02-20
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.Closed

---

