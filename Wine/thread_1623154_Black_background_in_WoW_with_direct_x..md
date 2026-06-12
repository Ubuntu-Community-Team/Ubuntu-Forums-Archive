---
title: "Black background in WoW with direct x."
date: 2010-11-16
forum: Wine
---

### Post by Aydos on 2010-11-16
Hello. I am an avid gamer and someone who always wants to go full Linux, but I always end up booting into Windows more than I want just to game.

I am currently only playing WoW which I know runs flawlessly in WINE so I decided to swap back over. 

Everything was working fine and I decided to do a reinstall of Ubuntu going from 10.04 to 10.10, so I did a full format and reinstall.

I just run WoW from my Windows drive. I installed Wine 1.37 and the game launcher perfectly like normal. I loaded in and had everything running fine.

 I then decided to try Open GL out even though I was getting really high FPS. I logged out, edited the config.wtf like normal with the Open GL command and bam the game was in Open GL. However, I could not move most of the grraphics optiosn off of their lowest setting. I then logged out removed the Open GL command from the wtf file and decided to go back to playing it with Direct X.

This is where my problem comes in. When I launch the game I now can hear Sindragosa in the background, I can see the Username, Password, and Authenticator Headers and Windows, I can see the options buttons on the side, I can see everything except the background where Sindragosa flys around the mountains and lands. Also, if I log in to my account I can see the Addons button and I can see the names of all of my characters and the options to choose them and all other menus from this screen, but the background is black so I cannot see my characters standing in their home town.

Now I did not try selecting a character and going past this, because this was a problem in itself. 

Does anyone have any clue what is going on and how to fix it?

Btw I am running on my desktop gaming rig that has an i7 920, 6 gigs of ram, and a NVIDIA 275 GTX with the official drivers from Nvidia, so I know it is not my system being weak.

---

### Post by cwwilson721 on 2010-11-16
It's not hardware, or WoW, or even wine (kind of) It's Microsoft, and the woefully under-revealed D3D implementation, and keeping the code hidden.

Why? Because D3D is "closed source", and you can't easily convert that into usable code for 'open source' projects like wine to take and develop for.

Go blame Microsoft, switch back (AND STAY) in opengl, forget the eye-candy, and whomp on others in PvP because you OWN the FPS.

Same hardware, same settings, same everything (except wine w/opengl and Windows in D3D), and wine is faster.

[Need proof?]("http://www.youtube.com/watch?v=xQFBK1yNIxE")

---

### Post by Aydos on 2010-11-16
Thank you for your reply. I keep up with all of your posts and I do agree that in some systems the FPS in Linux with Open GL can be faster that that of Windows, but it is not always the case.

In windows 7 on my system with every slider maxed on Ultra, all extra eye candy turn on, AA maxed. I easily get over 200 FPS in Raids and PvP (except for standing in SW yesterday during the elemental invasion with the rest of my server lol). In Ubuntu with WINE and Open GL I only get around 80 in the same circumstance.

I like the eye candy and WoW ran fine before the wipe and it ran fine with direct x on this install as well before I tried Open GL. Something in me going from direct x to OpenGL and then back to direct X messed this up.

I have googled and checked the AppDB and I can find nothing on my problem.

---

### Post by Aydos on 2010-11-17
Is there something that WINE saves after opening a game in OpenGL that is overiding the default settings ? 


I only ask, because the game works flawlessly in DirectX before adding the SET gxApi "opengl" to the config.wtf file and when I remove that line from the config.wtf I get the black screen.

So in theory some setting is overwritten somewhere by adding that to the file and I need to set it back.

This is all hypothetical, but it is the closest thing to making since.

---

