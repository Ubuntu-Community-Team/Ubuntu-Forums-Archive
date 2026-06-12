---
title: "blade of darkness on wine"
date: 2009-02-01
forum: Wine
---

### Post by Naegling23 on 2009-02-01
Im trying to get blade of darkness (severance for you european types) running on wine.

According to winehq, the program runs fine if I do the following:

Add the following registry key with regedit

HKEY_CURRENT_USER/Software/Wine/OpenGL/DisabledExtensions = GL_KTX_buffer_region

(the key is a string value)

However, I tried, and failed, perhaps I added the value wrong, can anyone give me some specific details on how to do the registry edit.

---

### Post by cogadh on 2009-02-01
Perhaps a screenshot of what you actually did to the registry would help us determine what you might have done wrong.

---

### Post by Naegling23 on 2009-02-01
I think I did this right, here it is.

---

### Post by cogadh on 2009-02-02
Ah, that 'splains it. You created a string under "HKCU/Software/Wine" called "OpenGL" with a value of "DisabledExtensions = GL_KTX_buffer_region"

What you actually need to do is create a new *key* called "OpenGL" under  "HKCU/Software/Wine" (right-click on the "Wine" directory in the registry tree and select New > Key). Within that key, you need to create a string called "DisabledExtensions" with a value of "GL_KTX_buffer_region".

---

### Post by Naegling23 on 2009-02-02
ah, thanks.  Thats why I asked, I really was unclear on how to set that up, so I figured a mistake was likely possible.  I'll try this out when I get home, if it works, I'll mark the thread as solved.

Im really hoping this game works, its an older (win95) game that never ran right on winxp, I've been trying for a few years to get it running under wine without success, but finally decided to solve the problem.  What a fun game, hopefully I get it working.

---

### Post by Naegling23 on 2009-02-02
your fix worked!!!!!

I cant wait to play this game again!

---

### Post by shababhsiddique on 2012-08-30
> **cogadh said:**
> Ah, that 'splains it. You created a string under "HKCU/Software/Wine" called "OpenGL" with a value of "DisabledExtensions = GL_KTX_buffer_region"

What you actually need to do is create a new *key* called "OpenGL" under  "HKCU/Software/Wine" (right-click on the "Wine" directory in the registry tree and select New > Key). Within that key, you need to create a string called "DisabledExtensions" with a value of "GL_KTX_buffer_region".

I did exactly as you said. My pc is a dual core intel graphics builtin motherboard, i have played bod flawlessly on windows now trying to run on ubuntu. the video setup is set to vodoo 1-2 D3D. I cant run the game, when it starts i see a black screen and nothing happens. If this game really runs please tell me what I am missing.

---

