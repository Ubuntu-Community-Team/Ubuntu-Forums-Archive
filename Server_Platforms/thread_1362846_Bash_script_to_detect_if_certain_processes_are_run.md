---
title: "Bash script to detect if certain processes are running"
date: 2009-12-23
forum: Server Platforms
---

### Post by nerr on 2009-12-23
Hey everybody,

I'd like to create a script that basically does a quick check to see if a certain process is running, and then outputs whether it is or not to a file that can be read to a web page using PHP.  For example, if I wanted to see if rtorrent is running, the script would do a quick check (probably using 'ps aux | grep rtorrent', or something similar) and then output if rtorrent is running or not to a file.  The file is then read and displayed on a page on my web server, which I use to check up on the server's status when SSH is unavailable.

I think the whole 'ps aux | grep rtorrent' thing is where I should start, but I'm not sure how to pinpoint for sure that the process I'm looking for really is running, and that the script doesn't detect the grep command instead.  I'm fairly new to bash scripting, so any help would be greatly appreciated.

Thanks a lot!

---

### Post by sisco311 on 2009-12-23
```
if [ $(pidof rtorrent) ]; then
  echo "rtorrent" >> /path/to/file
fi

```

---

### Post by nerr on 2009-12-23
Hahaha, yes!  That'll do it. :) Wow, that was easy.  Thanks a lot!

---

### Post by sisco311 on 2009-12-23
> **nerr said:**
> Hahaha, yes!  That'll do it. :) Wow, that was easy.  Thanks a lot!

You are welcome!

BTW, *ps -ef | grep rtorrent | grep -v grep* is not so *elegant* but it works. :evil:

---

