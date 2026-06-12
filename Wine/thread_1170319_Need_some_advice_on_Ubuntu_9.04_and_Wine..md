---
title: "Need some advice on Ubuntu 9.04 and Wine."
date: 2009-05-26
forum: Wine
---

### Post by Saturate2009 on 2009-05-26
First off, I'm very new to Linux.  I finally got Jaunty working great on my Macbook pro 3.1.  Well, everything except flash player, because it's 64 bit and I can't seem to find a working tutorial to get that to work, along with the green picture on my isight.  Anyways, I have a few questions about Wine.
 
1:  How well does WoW run in Wine, compared to Windows?  I'm using an x260 and getting about 200 fps in old wow, 25 to 30 in Dalaran and 40+ in all 25 mans with 4 gigs of ram and Windows 7.  
 
2: Since WoW is a stand alone executable that doesn't require registry entrys, can I just copy the folder over from a NTFS drive that I mount and run it in Wine without having to download a massive 7 gig file?
 
3: Is there any way to get Ventrilo to work with push to talk, in Wine, without it having focus on the window? I kinda need to able to talk.  
 
4:I've read some posts on this forum, some say that Steam doesn't work on Wine.  Is there any way to play steam games on Wine?
 
Thanks ahead of time.  I hope I asked clear questions, and hopefully not nooby ones I could have answered by reading a few more posts.

---

### Post by asdfoo on 2009-05-26
> **Saturate2009 said:**
> First off, I'm very new to Linux.  I finally got Jaunty working great on my Macbook pro 3.1.  Well, everything except flash player, because it's 64 bit and I can't seem to find a working tutorial to get that to work, along with the green picture on my isight.  Anyways, I have a few questions about Wine.

1:  How well does WoW run in Wine, compared to Windows?  I'm using an x260 and getting about 200 fps in old wow, 25 to 30 in Dalaran and 40+ in all 25 mans with 4 gigs of ram and Windows 7.  

Depends on video card and drivers, if you have nvidia make sure you're using atleast 180.44 (i assume you mean gtx260), so yeah, visit nvidia.com, ATI is hit and miss, Intel is usually a no go.

Make sure you set the OffscreenRenderingMode key to fbo using regedit, open a terminal, type wine regedit, browse HKLM, Software, Wine, create a key called Direct3D, inside, create a String entry named OffscreenRenderingMode, set the value to fbo

> **Saturate2009 said:**
> 

2: Since WoW is a stand alone executable that doesn't require registry entrys, can I just copy the folder over from a NTFS drive that I mount and run it in Wine without having to download a massive 7 gig file?
 
Most likely, there's no harm in trying.  Just don't run it directly from the NTFS drive.

> **Saturate2009 said:**
> 
3: Is there any way to get Ventrilo to work with push to talk, in Wine, without it having focus on the window? I kinda need to able to talk.  
 
You might need to search the forums here or the AppDB for tips on that, unless someone else answers it here.

> **Saturate2009 said:**
> 
4:I've read some posts on this forum, some say that Steam doesn't work on Wine.  Is there any way to play steam games on Wine?

Steam works, just not the ingame / steam community stuff.  I play CS:S and L4D through steam now and then, I've also played TF2, Far Cry and some other titles, but all that depends on me having nvidia, different case per title with ati or intel hardware.

> **Saturate2009 said:**
>  
Thanks ahead of time.  I hope I asked clear questions, and hopefully not nooby ones I could have answered by reading a few more posts.

Yep, nice question format :)

---

### Post by Saturate2009 on 2009-05-26
Thanks very much for those answers.  Also.  Since you might still be around.  Will logitech drivers work on Ubuntu? I have a G5, use it's key bindings for WoW, since extra mouse buttons unbound act as a "click" action in WoW.. very annoying.  And is your performance good on Left 4 Dead using Wine?  Sorry for all of thse questions, just curious about Ubuntu, I'm loving it so far on my macbook, nothing like having to look stuff up when you're so used to knowing the answer in Windows ;P.:KS

---

### Post by asdfoo on 2009-05-26
> **Saturate2009 said:**
> Thanks very much for those answers.  Also.  Since you might still be around.  Will logitech drivers work on Ubuntu? I have a G5, use it's key bindings for WoW, since extra mouse buttons unbound act as a "click" action in WoW.. very annoying.  And is your performance good on Left 4 Dead using Wine?  Sorry for all of thse questions, just curious about Ubuntu, I'm loving it so far on my macbook, nothing like having to look stuff up when you're so used to knowing the answer in Windows ;P.:KS

I think additional mouse buttons should be reecognised automatically and Wine should handle it, if it doesn't you'd need to check first that a native linux app can bind/see those additional buttons, if yes and it doesn't in WoW then you'd file a bug report with Wine.

L4D, performance isn't so great, but it's playable, I finished all the campaigns and have done survival quite a bit, I get 30-40fps with my 8800GTS, the Wine devs are still working on how to best fix the performance problems, so hopefully it'll work much better in the near future.

---

