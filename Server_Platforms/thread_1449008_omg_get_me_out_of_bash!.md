---
title: "omg get me out of bash!"
date: 2010-04-07
forum: Server Platforms
---

### Post by 98cwitr on 2010-04-07
I dont know what I did or how I did it, but after searching on google I assume that I entered bash and have no idea how to get out. I'm using ubuntu server 9.10 on virtualbox (previously on QEMU) and when I try to type something I get

^[*someletter* or when I press a number key (top row) I get (arg *someNumber*)

Display all *someNumber* agruments...only key that seems to be responsive is the Enter key on the numpad. 

I was told to just press q and then enter and that should exit...but it doesn't, I've tried everything and just have to hard shutdown the VM, which doesnt sit well with me. 

1. What did I do to get into this, so I can be sure NEVER to do it again?

2. How the hell do I get out of it?

---

### Post by wojox on 2010-04-07
Sounds like you got stuck in vi. To get out press 

```
:q <enter>
```

---

### Post by 98cwitr on 2010-04-07
ill try that next time i get stuck, which i assume will be sometime soon...haha.

---

### Post by KB1JWQ on 2010-04-07
vi/vim is actually a great text editor.  Taking a bit of time to learn it pays dividends in the long run.

---

### Post by 98cwitr on 2010-04-08
I use nano on a headless system, just what I'm used to I guess :)

---

