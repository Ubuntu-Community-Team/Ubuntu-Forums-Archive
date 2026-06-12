---
title: "FireFox address bar and camel case selection, navigation"
date: 2008-04-25
forum: The Cafe
---

### Post by legolas_w on 2008-04-25
Hi
Have you ever tried to press CTRL+Shift and Left arrow key to select some part of the URL in firefox address bar?
or do you tried to quickly navigate to some point offset of the URL in the address bar using CTRL+Arrow key?

It works fine in Windoz but in Linux it does not works properly, 
Any comment?

Thanks

---

### Post by y-lee on 2008-04-25
Never noticed it but you are right. 

Change the below attribute in Firefoxes **about:config** should fix it for you.

```
layout.word_select.stop_at_punctuation = True

```.

---

