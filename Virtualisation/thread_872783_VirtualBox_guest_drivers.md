---
title: "VirtualBox guest drivers"
date: 2008-07-28
forum: Virtualisation
---

### Post by qbox on 2008-07-28
Hi
I have ubuntu 8.04 and VirtualBox on it with installed XP.
I need somehow to install drivers for graphic card on guest XP. I cant install original drivers because system show me the message that I dont have minimum requirement.
Any trick to bypass this?

---

### Post by Fire_Chief on 2008-07-28
You need to install the VirtualBox Guest Additions (Under the Devices menu of the VirtualBox VM window). This will install the correct drivers in the XP VM to greatly improve the graphical and mouse performance. Note that VirtualBox does not support 3D acceleration but 2D works very well.

Cheers!

---

### Post by qbox on 2008-07-28
Thanks but that isnt help me. :(
Everything is still the same.

---

### Post by Fire_Chief on 2008-07-28
Can you explain in more detail what you are experiencing and trying to accomplish?

---

### Post by qbox on 2008-07-28
Im want to start a game under Vbox and the game first search for a graphic adapter engine. I need to add another adapter under Vbox.

---

### Post by Fire_Chief on 2008-07-28
What game is it? Does it require a card capable of hardware 3d acceleration (DirectX)? If so, you won't be able to run this in Virtualbox.

---

### Post by qbox on 2008-07-29
Minimum system requirements :

    * Operating system: Windows XP, Windows Vista
    * DirectX 9.0c
    * Pentium 4 1.8 GHz, Athlon XP 1800+ CPU
    * 512 MB RAM
    * 100% DirectX 9.0c compatible graphics card with 64 MB RAM,
    * Vertex Shader 1.1 and Pixel Shader 1.3 support
    * (Pixel Shader 2.0 recommended)
    * NVIDIA GeForce4 Ti or better
    * ATI RADEON 9500 or better
    * 100% DirectX 9.0c compatible sound card


They never say that I need 3D..... ahhhh I will probably install microSHIT winWORST (ms w\) on another machine......

---

### Post by Fire_Chief on 2008-07-29
When you see items like vertex shader and pixel shader, those are clues that it's a 3d accelerated game. Did you see if the game can be run under Wine? 

Check out [http://appdb.winehq.org/]("http://appdb.winehq.org/") and see how well your game is supported.

Cheers!

---

### Post by qbox on 2008-07-29
Hmm no way on Vbox then.
I try with wine and I see that the game is supported. The tester say that everything work PEFECT.
BUT!!
When I start the game the game ask for me to be a Administrator. I googled alot but no one dont know how to fix problem with programs who ask for administrator tights. in my case I need w\ administrator right, no linux.

I start the game with wine and one message tel me this
nsufficient privileges: you must be administrator when you run this application for the first time.

i cant understand how tester start the game under wine without admin rights :) I send him a mail but no one reply to me :)
I report to wine bugs and no one dont have a clue how to fix the problem with programs who ask for a admin rights.

I think about making crack by bypassing the check for admins.
Any sugestions how to do this? Or what tools to use ?
:))))

---

### Post by KatBuntu on 2008-07-29
Maybe you can try the VMware workstation 3-D acceleration new capability on this forum.

[http://ubuntuforums.org/showthread.php?t=846675]("http://ubuntuforums.org/showthread.php?t=846675")

---

### Post by Fire_Chief on 2008-07-30
Did you see a how to on installing the game on the Wine site? It should also list any known bugs or gotchas with the game. Be sure to follow the how to very closely and it should give you good results.

Cheers!

---

### Post by qbox on 2008-07-30
I make all what he tell in the installation guide but without any results. 
aaahhhh I will wait to fix this bug....

---

