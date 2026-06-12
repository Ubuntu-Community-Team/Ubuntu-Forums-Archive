---
title: "Multi user screen session"
date: 2010-10-28
forum: Server Platforms
---

### Post by sipickles on 2010-10-28
Hi
I have a server running Ubuntu 9.04.

I'd like to share an ongoing screen session with two users, so either one can login and work in the shared screen windows.

I can't get it to work despite extensive googling.

Here's what I am doing:

1st user (simon):
```
simon@urth:~$ sudo chmod u+s /usr/bin/screen
simon@urth:~$ screen -S shared
[in screen terminal]
^a :multiuser on
^a :acladd michaelm

```
2nd user (michaelm):
```
michaelm@urth:~$ screen -rx simon/shared
Must run suid root for multiuser support.
```

I don't know how to overcome this.

I tried:
```
simon@urth:~$ sudo chmod 755 /var/run/screen
simon@urth:~$ screen -S shared
Directory '/var/run/screen' must have mode 775.
```

Thanks for any advice

Simon

---

### Post by AndyCee on 2010-10-28
> I don't know how to overcome this.

I tried:
Code:

simon@urth:~$ sudo chmod 755 /var/run/screen
simon@urth:~$ screen -S shared
Directory '/var/run/screen' must have mode 775.

Thanks for any advice

Simon

Err, apologies if this is obvious, but you've set permissions to 7**5**5 when the error requested 7**7**5.

---

### Post by sipickles on 2010-10-28
The chmod command came from here:

[http://www.debian-administration.org/articles/572#comment_6](http://www.debian-administration.org/articles/572#comment_6)

With the perms set to 775, I can start screen in the 'simon' terminal. I do *^a:multiuser on, ^a:acladd michaelm* but still get this in the 'michaelm' terminal:

```
michaelm@urth:~$ screen -x simon/
Must run suid root for multiuser support.
michaelm@urth:~$ screen -x simon/shared
Must run suid root for multiuser support.

```

---

### Post by rportlock on 2011-02-02
I was having the same problem, it turned out that my [FONT="Courier New"]/usr/bin/screen[/FONT] was actually a wrapper script that ran [FONT="Courier New"]/usr/bin/screen.real[/FONT]. I was able to get things working by running:

```
$ sudo chmod u+s /usr/bin/screen.real
```

I realize it might be a couple of months late, but I figured I'd post just in case somebody else has the same problem.

---

