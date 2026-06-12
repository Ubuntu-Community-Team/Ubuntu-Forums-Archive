---
title: "searching for plaintext passwords, and wiping them"
date: 2013-04-19
forum: Security
---

### Post by talz13 on 2013-04-19
I've been updating a lot of my security practices over the last couple days, such as making use of google's multi-factor authentication, and other such things.  Something that I became curious about was, are passwords that I use being stored in plaintext in various places around my system?  I did a simple recursive grep on my home directory against a substring of the password in question, and the screen was immediately flooded with lines containing my password clear as day in the history log file in the .lftp folder.

Immediately, I ran 'shred' on that file, as I have no need of those logs, but, where else on my ubuntu system is storing my various passwords in plaintext?  I could run a ```
grep -R / "{password here}"
``` but that seems like it might take FOREVER to complete.

Are there any tools that might assist me with this?

---

### Post by Stonecold1995 on 2013-05-04
Using grep will be as fast as you'll get.  I don't think any other tool will match its spead.

However, a way you can significantly speed it up is by ignoring directories containing large files which you KNOW don't contain your password.  For example, I occasionally search for my password that way too, I just avoid directories like ~/Videos, ~/Music, ~/Pictures, etc because grep has no reason to spend hours looking through hundreds of gigabytes of video data and the like.

I'd say search in ~/.config ~/.local ~/.cache /etc /var etc.

One more tip: running grep with the -i flag (ignore case, so PaSsWoRd is detected along with password and PASSWORD) makes it take SIGNIFICANTLY longer.  And by significantly longer I mean this:
```
alex@kubuntu:~$ dd if=/dev/urandom of=/tmp/largefile bs=1024 count=102400
102400+0 records in
102400+0 records out
104857600 bytes (105 MB) copied, 38.2717 s, 2.7 MB/s
alex@kubuntu:~$ time grep string < /tmp/largefile


real    0m0.186s
user    0m0.172s
sys     0m0.012s
alex@kubuntu:~$ time grep -i string < /tmp/largefile


real    0m22.089s
user    0m20.676s
sys     0m0.396s
```

---

