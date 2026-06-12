---
title: "[SOLVED] so it captures my mouse...and never lets it go!"
date: 2008-09-17
forum: Virtualisation
---

### Post by novus721 on 2008-09-17
I just got my Sun xVB VirtualBox up and running (finally) but I am having problems in the final stretch - 

My HOST key will NOT release my mouse, and pressing Enter continuously does nothing either. The only way to get my mouse and keyboard back is to restart x with ctrl+alt+bk. The icons at the bottom of virtualbox confirm that both my keyboard and my mouse are captured. 

any ideas? thanks everyone!

---

### Post by novus721 on 2008-09-17
scratch that, it's just not recognizing my keyboard - the mouse is working fine, the keyboard is keeping it from being recognized

---

### Post by tuxxy on 2008-09-17
Can you type anything in your guest OS?

Load virtualbox manager and select file > prefs > input and try changing your host key, maybe its already binded to something else

---

### Post by novus721 on 2008-09-17
I can't type anything at all. I've tried changed it to two other keys...no difference

I also unchecked the enable keyboard from the menu so that I have to do it manually. Thanks for your help though!

UPDATE -

Thanks to a bit of research and lwvmobile, I found out that you can't have complex characters enabled for your language support. Once I got rid of that, everything worked fine.

PS - for anyone who wondered, Greek characters are not complex. &#932;&#941;&#955;&#949;&#953;&#945;, &#949;&#967;;

---

