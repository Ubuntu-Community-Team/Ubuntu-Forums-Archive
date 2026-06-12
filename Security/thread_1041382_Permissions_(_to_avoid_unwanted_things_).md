---
title: "Permissions ( to avoid unwanted things )"
date: 2009-01-16
forum: Security
---

### Post by spiriad on 2009-01-16
I want to make an automated system to compile & run the source codes from different persons and to tell if the output is the same with the standard one(wich is given by me). Ok, this is quite simple, but the tricky part is,how do I avoid the "bad intentions" that may result from running those compiled sources.(Eg.: a program that should return the sum of two numbers, is designed to halt the sysyem :shock:).Generaly speaking, how do I prevent those programms do things like: network accesing, creating to many child processes (causing a DOS), generating to much output (thus the system remains out of space), using to much memory, calling system functions, etc. How to protect my system from this kind of (posible) abuses ? (I mention that the sources submitted are , for now, c++ sources, but should work for other languages too).

Thanks, Adrian

---

### Post by pdtpatrick on 2009-01-16
lol thats kinda confusing.. maybe state the question a bit more clearly. Reading that one gave me a headache :(

---

### Post by spiriad on 2009-01-16
I want to block the programs that are trying to do other things than that expected. Eg.: block them using too much memory, block them sending system signals (calls), block them generating to much output, etc.

---

### Post by bodhi.zazen on 2009-01-16
> **spiriad said:**
> I want to block the programs that are trying to do other things than that expected. Eg.: block them using too much memory, block them sending system signals (calls), block them generating to much output, etc.

By default ubuntu uses Apparmor, see the sticky at the top of these forums, it may help.

---

