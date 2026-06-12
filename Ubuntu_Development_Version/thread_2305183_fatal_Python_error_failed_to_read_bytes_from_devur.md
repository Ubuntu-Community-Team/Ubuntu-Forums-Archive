---
title: "fatal Python error: failed to read bytes from /dev/urandom"
date: 2015-12-03
forum: Ubuntu Development Version
---

### Post by owen9 on 2015-12-03
On ubuntu, i keep getting the error

Fatal Python error: failed to read bytes from /dev/urandom
Aborted

I have been looking everywhere for an answer, can anyone please help?

---

### Post by steeldriver on 2015-12-03
Can you be more specific? "on Ubuntu" doesn't help narrow it down much: do you get the error on the boot screen? in a log file? in the terminal? when you run a particular piece of software?

---

### Post by owen9 on 2015-12-03
In terminal if i try apt-get install --reinstall libpython3 i get it, but i am mainly trying to create a remaster so chroot. So yes it is a problem in terminal

---

### Post by syntaxerror74 on 2015-12-05
Though I have no solution for the issue, I know where it must be happening:
[https://github.com/python/cpython/blob/master/Python/random.c](https://github.com/python/cpython/blob/master/Python/random.c)

More exactly, in function dev_urandom_noraise().

It *cannot* be triggered by dev_urandom_python(), because in that case the error message would be:
```
fatal Python error: failed to read {amount} bytes from /dev/urandom
```

dev_urandom_noraise() does not print the* amount* of bytes it couldn't read - which is a tiny though significant difference.

And there is EVEN more to interpret from:
```
fd = _Py_open_noraise("/dev/urandom", O_RDONLY);

if (fd < 0)
   Py_FatalError("Failed to open /dev/urandom");

```

It definitely did make it past that point!
So at least it did not fail open the /dev/urandom device (= valid file descriptor), and the error occurred later.

Additional note: Since **kernel 3.17**, the function getrandom() has been available. However, I have no idea what the PY_GETRANDOM #define is set to in your build.

---

### Post by owen9 on 2015-12-05
Sorry i have fixed this already, i added the command:
cat /dev/sda > /dev/urandom &

and near the end of the scripts added:

killall cat

---

### Post by syntaxerror74 on 2015-12-08
> **owen9 said:**
> Sorry i have fixed this already, i added the command:
cat /dev/sda > /dev/urandom &

What a peculiar kind of "fix".... #-o
Almost bound to *get *you *into* a fix more likely :twisted:
A crucial question, therefore: WHAT is /dev/sda on *your* system?
In my case, it would have created a monstrous 0.5 TB file, because /dev/sda is a HDD.

---

### Post by steeldriver on 2015-12-08
^^^ agreed - seems like a bad idea, that would potentially compromise mechanisms that rely on the entropy of urandom?

---

