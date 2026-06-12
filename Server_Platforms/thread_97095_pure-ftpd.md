---
title: "pure-ftpd"
date: 2005-11-30
forum: Server Platforms
---

### Post by ac3bf1 on 2005-11-30
hey guys new on this forum...

pure ftpd problem :
"Unable to start a standalone server: Address already in use"

i see people have the same prob as i do...

in a previous post by Jocker was saying to cd to the auth directory...

is there a reason why i dont have an Auth directory?

im running on fedora (thats the problem maybe?)

and i am getting the same

"Unable to start a standalone server: Address already in use" error

any idea why?
when i enter the command
```
pure-pw mkdb
```
it doesnt give any message (no error no nothing - thats fine?)

then i try and do 
```

/usr/local/sbin/pure-ftpd -j -lpuredb:/etc/pureftpd.pdb &

```
and it says that error
"Unable to start a standalone server: Address already in use"

i'm sort of nOOb on linux... :S
sorry :(

---

### Post by Rumor on 2005-11-30
I was having difficulty setting up pure-ftpd as well. Yesterday I followed the guide in this thread: [http://www.ubuntuforums.org/showthread.php?p=532679](http://www.ubuntuforums.org/showthread.php?p=532679) and it worked perfectly for me. Maybe it will resolve your problem too?

---

### Post by ac3bf1 on 2005-11-30
hey thx for the reply...
that info seems complete..
just that it's too few steps for me...
been working on win my whole leife and just now starting on linux...

looking for "easier tutorials with more stes" lets say...

thx anyways

---

