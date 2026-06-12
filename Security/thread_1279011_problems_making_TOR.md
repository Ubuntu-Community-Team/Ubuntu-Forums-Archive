---
title: "problems making TOR"
date: 2009-09-30
forum: Security
---

### Post by jethroman12 on 2009-09-30
Hi i'm new to linux and i compiled TOr from source and it compiled fine but when i tried it tor or vidllla  couldn't find the Torrec file so tired CDing to the directory Vidilla said it was in and it wasn'there!    what did i do wrong i checked on the tor website and this forum and i can't  find any advice please tell me what i did wrong

---

### Post by cdenley on 2009-09-30
Why did you compile it from source?
[http://www.torproject.org/docs/debian.html.en#ubuntu](http://www.torproject.org/docs/debian.html.en#ubuntu)

---

### Post by jethroman12 on 2009-09-30
that url didn't have the actual package just the hash and checksum so i compiled it in source

---

### Post by cdenley on 2009-09-30
If you actually read the instructions in that link, they tell you how to add a repository containing tor and any dependencies. Once you add the repository, you can install it the correct way. Notice the last line of instructions:
> 
**Now Tor is installed and running**. Move on to step two of the "Tor on Linux/Unix" instructions. 


---

### Post by jethroman12 on 2009-09-30
i tried that and it said it wasn't a valid url

heres the url i put in

[http://deb.torproject.org/torproject.org/jaunty/main.html](http://deb.torproject.org/torproject.org/jaunty/main.html)

---

### Post by cdenley on 2009-09-30
The instructions were:
> 
deb     [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) <DISTRIBUTION> main


If you're using jaunty, that would mean you should add this to your sources.list file:
```

deb     http://deb.torproject.org/torproject.org jaunty main

```

---

