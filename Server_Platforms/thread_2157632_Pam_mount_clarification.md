---
title: "Pam_mount clarification"
date: 2013-06-26
forum: Server Platforms
---

### Post by zenriko on 2013-06-26
Hello,

I am a new linux user and currently looking to setup LTS at my work, naturally I have a windows environment.
I have so far managed to setup an LTS and join it to our domain. However my main stumbling block is regarding mounting existing windows shares.

I have read a fair amount on Pam_mount and it's capabilities, but one thing I am unsure on is it's ability to mount X share based on X user.
Most, in fact all examples I've seen only demonstrate mounting single share with X user(s).

What I would like to know is; Is it possible to utilize Pam_Mount in such a way then when Class 1 logs in, they get Share1, Class 2 - Share2, and so-on
instead of all Class's getting Share1.

I understand %variable% username, but how do you implement variable shares? Or would I manually code each user to each share, I just don't understand how to achieve this.

I am first to admit I am next to clueless in all things linux.

---

