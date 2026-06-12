---
title: "Compiled mysql start on boot?"
date: 2010-03-24
forum: Server Platforms
---

### Post by Ikith on 2010-03-24
I just compiled mysql apache and php from source and I have apache to start up from boot but I don't exactly know how to get mysql to do the same. Can someone please help me out. Thank you.

Edit: Also how do I add mysql to path? Should I just symlink it to somewhere thats in the path or what? And if that is the case wheres the best place to symlink it too.

---

### Post by cdenley on 2010-03-24
Why did you install from source? It is not supported, more difficult to maintain, less stable, and more difficult to get help on forums when you inevitably run into these problems.

---

### Post by Ikith on 2010-03-24
Because I like learning how to do things. Instead of letting someone else do everything for me (along the lines of software that is not OS... They can keep the OS to lazy mode ;))

This is not a problem its more of a set back the server itself runs perfectly fine I just need to figure out how to make it run from boot.

The reason I installed apache from source... The repo version of it screws everything up... I mean it runs but everything is just thrown everywhere and it just sucks! I just finished an apache web server class about apache httpd and only apache httpd and I could not figure out the repo version but when I compiled apache it was perfect :) Same with php.

I would like an answer not a post telling me why I should have pulled it from the repo etc etc.

---

### Post by cdenley on 2010-03-24
> **Ikith said:**
> 
The repo version of it screws everything up... I mean it runs but everything is just thrown everywhere and it just sucks!

At least the packages come with init scripts! Personally, I like the modular configuration much better.

> **Ikith said:**
> 
I would like an answer not a post telling me why I should have pulled it from the repo etc etc.

I'm just saying, if you're not using ubuntu packages, I wouldn't count on someone here being able to help you. Good luck.

---

