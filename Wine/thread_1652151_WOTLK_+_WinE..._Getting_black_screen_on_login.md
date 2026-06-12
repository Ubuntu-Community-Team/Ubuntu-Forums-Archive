---
title: "WOTLK + WinE... Getting black screen on login"
date: 2010-12-24
forum: Wine
---

### Post by Sanity8080 on 2010-12-24
The patches downloaded fine for WoW-WotLK, but when I try to hit the play button, it gives me a black screen, and I can hear the sound effects, and see the hand pointer, but nothing else... 

My graphics card is: 

VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M] (prog-if 00 [VGA controller])

The version of WinE is whatever was available last week to download through apt-get...

Keep in mind, I'm fairly new to ubuntu, and am doing this to prove to my husband that I am just as computer savvy as he is (more so, perhaps, since he won't touch linux in any flavor)

---

### Post by Sanity8080 on 2010-12-24
So without running openGL, I can get to login screen, but it blinks... Badly.  So I turned off compiz, but it still blinks.... working backwards from the troubleshooting doc, (trust me, this made sense in my head) I enabled opengl in the config.wtf file, but then I get a crash screen (wowerror message that becomes smilies when I paste it here) and don't get the sign on screen anymore, blinking or not

[http://pastebin.com/CXLkDH7e](http://pastebin.com/CXLkDH7e)

---

### Post by cwwilson721 on 2010-12-24
Why do you INSIST on NOT using opengl?

Without it, you get what you have.

Run it in opengl. Or not. But you get the 'black' if you don't.

D3D doesn't work in wine/WoW. opengl does.

---

### Post by Sanity8080 on 2010-12-27
> **cwwilson721 said:**
> Why do you INSIST on NOT using opengl?
 
Without it, you get what you have.
 
Run it in opengl. Or not. But you get the 'black' if you don't.
 
D3D doesn't work in wine/WoW. opengl does.
 
If you had read my second message completely, you would have seen that I DID enable opengl... it crashed, and wouldn't even open the log in screen at all.  
 
Thank you, though, because I was able to get wow and my character loaded, but it is not playable at current, as my graphics card is beyond ancient.

---

