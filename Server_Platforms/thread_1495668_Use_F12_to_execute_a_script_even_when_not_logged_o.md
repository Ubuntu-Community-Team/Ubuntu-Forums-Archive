---
title: "Use F12 to execute a script even when not logged on"
date: 2010-05-28
forum: Server Platforms
---

### Post by sylvester_0 on 2010-05-28
Hi gang - I have a rather strange request. Put simply, I'd like to know how to bind a script to a F key (F12) that will run as root even when not logged in. I have a headless server on client premises where it'd be easier for them to press F12 to run this script that will be rarely needed than to give them SSH instructions etc.

I know this must be do-able, but I can't get my Google-fu on for this question. The only way that I can possibly think of doing it is to touch a file whenever that key is pressed and have the script idly checking for that file every few seconds in a loop. However, I don't know where I'd dig in to create this event.

Any pointers are much appreciated!

---

### Post by HermanAB on 2010-05-28
Google for "setuid root".

---

### Post by sylvester_0 on 2010-05-29
Thanks - I knew about this already. The big part of the equation that I need help with is using the F12 key to run a script when not logged on. I don't have any clue where I'd begin googling for that.

---

