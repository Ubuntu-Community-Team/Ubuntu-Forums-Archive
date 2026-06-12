---
title: "How to append stings in Shell script"
date: 2009-07-17
forum: The Cafe
---

### Post by dileep.kk on 2009-07-17
Hi all,
As Iam beginner to shell script,I want to know how I can concatinate strings.
Here the input strings are from command line  arguments.So I want to know is there any way to concatinate strings that coming from commandline.Here the number of arguments from command line may vary.

---

### Post by Tibuda on 2009-07-17
Confused. If you want to concatenate all the arguments, you can only use "$*". To concatenate two strings stored in variables A and B you can use "$A$B".

---

