---
title: "Photoshop with Virtualbox"
date: 2012-11-14
forum: Virtualisation
---

### Post by neophus on 2012-11-14
Hello

I have virtual box 4.2 (64 bits) with photoshop cs5 It's works but I have a little problem with buffer, I can't use this (alt+clic) I have message "impossible to use buffer" etc...
I've already search on web to find the problem, perhaps it's a command on virtualbox or over witch use alt and apparently it do conflict with photoshop

someone have an idea?

thanks you

---

### Post by pkadeel on 2012-11-14
Alt + Click shouldn't interfere with VB or the host OS however to be sure you can check the preferences of VB and see whether Auto-Capture Keyboard is enabled and the Host key is "Right Ctrl" or any other key except the "Alt" key.

You can also use sticky key feature in windows to change the Alt key for guest OS so that interference of Host OS can be avoided.

---

### Post by neophus on 2012-11-14
thanks but where I must to go to change that?

---

### Post by pkadeel on 2012-11-14
> **neophus said:**
> thanks but where I must to go to change that?
I am sorry but I checked it in windows and this sticky key feature is not what i thought it is. It is just an Accessibility feature to avoid the Press and Hold of Alt key.

---

### Post by neophus on 2012-11-15
Okay but perhaps in virtualbox we can change no?

---

### Post by neophus on 2012-11-16
help please ! I can't resolve this problem ! I have test a lot of things it doesn't work and it's a problem for me in my work !

---

### Post by pkadeel on 2012-11-16
If you post the full error message then someone might be able to help you otherwise it is very difficult to guess about the error when you say 
> I have message "impossible to use buffer" etc...

---

### Post by neophus on 2012-11-16
the message is (I translated as I can beacause it's french text) "Impossible to use buffer because the duplicate zone is not defined (alt-clic to define one source point)

I have test to desactivate in ubuntu all alt shortcut in preferences system/keyboard/shortcut

also change in keyboard layout/options/comportement with alt and windows touch (I tested virtually all choices)

I had disabled right click icon at the low right corner

I had search on my keyboard in windows host 

I have all the time the same message

---

### Post by pkadeel on 2012-11-16
> **neophus said:**
> the message is (I translated as I can beacause it's french text) "Impossible to use buffer** because the duplicate zone is not defined **(alt-clic to define one source point)
To me, it sounds more an application error rather than OS error.
You need to check the photoshop cs5 settings first.

---

### Post by neophus on 2012-11-17
I've found the problem ! I must to disable mouse integration and it works, but I must to do that each time when I restart my VM but it's better than nothing...

thanks for you help

---

### Post by Sar on 2012-12-18
Sounds like you're trying to use the clone stamp tool, but you haven't selected anything as your source. Try using a layer with content as the source and alt-clicking to define the source to copy/clone from first.

"Impossible to use buffer** because the duplicate zone is not defined **(alt-clic to define one source point)

This will likely be this error:

Could not use the clone stamp because the area to clone has not been defined (Alt-click to define a source point).

---

### Post by haqking on 2012-12-18
> **neophus said:**
> I've found the problem ! I must to disable mouse integration and it works, but I must to do that each time when I restart my VM but it's better than nothing...

thanks for you help

only if you dont check the box to say dont show this again or disable the absolute pointer in the guest settings.

However i have noticed in some Linux VM's this doesnt apply

---

