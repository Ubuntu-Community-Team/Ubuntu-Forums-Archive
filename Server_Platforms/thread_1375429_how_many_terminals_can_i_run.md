---
title: "how many terminals can i run?"
date: 2010-01-07
forum: Server Platforms
---

### Post by tomdagreek on 2010-01-07
hello. had a question
i know the trick where u can press alt and f1 or f2 and so on to bring a new terminal screen.
how many terminals can i run?
running 9.04 with no gui
thanks

---

### Post by Grim76 on 2010-01-07
Not sure how many you can get to, but you can run screen in each of those with multiple sessions.  Not sure what number you can get that up to though.

---

### Post by fancypiper on 2010-01-07
I believe you can access 6 and the 7th will be the x session.

You can tweak it for more, but I have lost my note on how to do so.

---

### Post by tgalati4 on 2010-01-08
There are normally 6 console terminals started at boot:

tgalati4@washme:~$ ps -ef | grep tty
root      4184     1  0 Jan04 tty4     00:00:00 /sbin/getty 38400 tty4
root      4185     1  0 Jan04 tty5     00:00:00 /sbin/getty 38400 tty5
root      4190     1  0 Jan04 tty2     00:00:00 /sbin/getty 38400 tty2
root      4192     1  0 Jan04 tty3     00:00:00 /sbin/getty 38400 tty3
root      4195     1  0 Jan04 tty6     00:00:00 /sbin/getty 38400 tty6
root      4733     1  0 Jan04 tty1     00:00:00 /sbin/getty 38400 tty1
tgalati4 18340 18323  0 21:55 pts/0    00:00:00 grep tty

But you can open as many as you want through the terminal program.

---

### Post by Project PWNED on 2010-01-08
Install screen, terminals are so old school, and screen just runs on one terminal. Type: screen. Ctrl+A and C to create a new screen. Ctrl+A and N to go to the next one. It's a pain in the *** to learn at first, but you'll eventually like it better than switching terminals, which gets confusing. There's a package called byobu that is screen, but much better, including system notifications like CPU load, updates available for Ubuntu, disk space, RAM usage, etc.

Honestly, I'd go with byobu.

---

