---
title: "Ubuntu host vista guest, gaming"
date: 2009-04-15
forum: Virtualisation
---

### Post by Kain000 on 2009-04-15
Hey everyone, 
Ive been playing around with virtualbox 2.2 and it is great.  I installed the copy of vista the came with my laptop (that runs ubuntu :) )  I installed mainly because I have built myself a hardware intensive rig but only use it's power for BOINC, and was curious about it's abailities as a gaming rig.    

OK so right now I"ve got my tower with a q6600 4GB ram and dual 512MB Geforce 9600's in SLI.   

I've sucessfully installed vista, and it's updates.

i've installed Steam and the game warhammer 40K, Dawn of War 2

When I go to play the game, steam starts fine and launches DOW2, but it reports that it could not find a sutiable hardware rendering deivce" and says that I should make sure I have the latest drivers and the harware is within spec for the game. 

I have installed the guest os additions, and from what research i've done you cannot install a video card driver (such as the disk that came with the cards) on a guest os.   I have the drivers from Nvidia on my host ubuntu system and compiz works fine.

Under general in the virtualbox window, i have checked the "enable 3d acceleration" box as it should allow me to use the cards to their fullest.


One curious thing was under the enable 3d acceleration box ,there is the slider that allows you to set the amount of video memory to allow the guest os, but the maximum is 128 MB, and I have confirmed with the 'Nvidia x server settings app', inside ubuntu, that indeed the host does see both cards, and each to have 512MB of memory.

the game wont play because it doesnt see a graphics card worthy enough, and I cannot install the windows drivers.  I am at a loss.

Any Ideas?

---

### Post by mister_playboy on 2009-04-15
I don't think there is any fix for this at the present time.  Virtualization is young (in the mainstream, anyway) and this kind of thing just isn't supported... yet.

---

### Post by MysticGold04 on 2009-04-15
The only solution (for now) is for you to dual boot Vista so that you can have the correct hardware drivers installed for your card.  Running XP or Vista in a VM will not allow direct access to the video card chipset, and therefore your game(s) will not detect it. 

If you decide to re-install Vista, I'd backup anything on your drive you want to keep and re-install Vista FIRST and then Ubuntu, otherwise it's much more difficult to get things right.

---

### Post by Kain000 on 2009-04-15
ahh, as I thought.... :( thanks tho for the replys.   My next question about this is here: [http://ubuntuforums.org/showthread.php?p=7079493#post7079493]("http://ubuntuforums.org/showthread.php?p=7079493#post7079493") any advice on this one?

---

### Post by Dedoimedo on 2009-04-16
You only get opengl support in VirtualBox and partial directx in VMware. It's a beginning of 3D, but not full-fledged yet.

If your games uses directx instead of just opengl, you will have issues running it in VirtualBox.

Dedoimedo

---

### Post by mjnaik2 on 2009-04-21
try this:
right click on your shortcut to your game and click on properties. then go to the place where it says target and at the end of the line, add -opengl

Eg:
"F:\Games\PC_GTA.SanAndreas -(rip)-(ToeD) Game\GTA.San.Andreas" -opengl

i dont know if it will work but just try it  :D

cheers! 

mjnaik

---

