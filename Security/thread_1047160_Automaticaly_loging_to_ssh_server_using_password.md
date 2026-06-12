---
title: "Automaticaly loging to ssh server using password"
date: 2009-01-22
forum: Security
---

### Post by kat666 on 2009-01-22
At begining sorry for my bad english.

I live in dormitory where i always need to log in to router using ssh to get access to internet. Also i don't have access to my home directory on router (i don't even know if exits) so i can't put there my public rsa key. The only way to log in is to enter password every time i want to connect.
Is it possible to store password somewhere on disk and it would be entered automaticly each time i run adequate script or program? I have even try to write a program in c which creates two proceces and child changes standard input and autput with pipes and run ssh with appropriate arguments, so parent can write to child's standard input. But it doesn't work with ssh (ssh takes control on terminal when launched) and i don't know why (works with other programs e.g. bash).

If someone have some idea how to solve this i would be grateful.

---

