---
title: "Gazelle Professional laptop and NVidia graphics?"
date: 2012-08-28
forum: System76 Support
---

### Post by MikeYPK on 2012-08-28
I was under the impression that the Gazelle Professional laptop comes with Intel HD4000 integrated graphics (which it does).

But what is confusing me is that it has a couple of nVidia stickers on it. Does that mean that it actually has the nVidia chips in it as well, and just not enabled right now? Or are the nVidia stickers a mistake?

Curious mind want to know.

---

### Post by zenlunatic on 2012-08-28
I haven't seen any pictures with those on it (don't own one) but it's possible.  Some newer systems I've seen from other vendors have dual video cards which can be used accordingly.

---

### Post by Carborundum on 2012-08-28
My Gazelle Professional (gazp7) has no NVIDIA stickers on it.

---

### Post by isantop on 2012-08-28
> **MikeYPK said:**
> I was under the impression that the Gazelle Professional laptop comes with Intel HD4000 integrated graphics (which it does).

But what is confusing me is that it has a couple of nVidia stickers on it. Does that mean that it actually has the nVidia chips in it as well, and just not enabled right now? Or are the nVidia stickers a mistake?

Curious mind want to know.

> **Carborundum said:**
> My Gazelle Professional (gazp7) has no NVIDIA stickers on it.

Those would have been a goof at the factory. The stickers are not supposed to be there.

---

### Post by MikeYPK on 2012-08-28
> **isantop said:**
> Those would have been a goof at the factory. The stickers are not supposed to be there.

Thanks for the response. I had false hopes for a while, but HD4000 ain't bad. It's enough for my purposes :-)

---

### Post by 3Miro on 2012-08-28
> **isantop said:**
> Those would have been a goof at the factory. The stickers are not supposed to be there.

This isn't the first time they mess up like that. My Pangolin came with Intel HD 3000 and an Nvidia sticker. This was about a year ago and I guess it is still happening every now and they.

Why are they putting the wrong stickers on?

---

### Post by Ubun2to on 2012-08-31
Technically, you have both. It works this way-the processor can double as a GPU as well as a CPU. But, just because you have a dedicated card does not mean the GPU built into the CPU goes away. You can disable dedicated cards in the BIOS, but there is no standard BIOS layout, so you might have to hop around for awhile before you find it.

---

### Post by cprofitt on 2012-08-31
Ubun2to:  I am not sure of how the Gazelle Professional (2012 version) has no Nvidia card, but I know that there is no option exposed in bios to turn it on or off. I have been told, not by System76, that the Clevo model the Gazelle is based on has the part soldered on to the motherboard though.  Can a System76 person fill us in on this detail? Is the Nvidia part on the board, but disabled or was a different board used?

---

### Post by Ubun2to on 2012-08-31
> **cprofitt said:**
> Ubun2to:  I am not sure of how the Gazelle Professional (2012 version) has no Nvidia card, but I know that there is no option exposed in bios to turn it on or off. I have been told, not by System76, that the Clevo model the Gazelle is based on has the part soldered on to the motherboard though.  Can a System76 person fill us in on this detail? Is the Nvidia part on the board, but disabled or was a different board used?

The new Intel HD Graphics are basically as good as they get-they are starting to give the dedicated mobile graphics card a run for their money.
If you want a good graphics card, though, the desktop is where you need to go. You can rig a Leopard Extreme with a 4 GB nVidia card.

---

### Post by pgm_01 on 2012-09-01
> **cprofitt said:**
> Ubun2to:  I am not sure of how the Gazelle Professional (2012 version) has no Nvidia card, but I know that there is no option exposed in bios to turn it on or off. I have been told, not by System76, that the Clevo model the Gazelle is based on has the part soldered on to the motherboard though.  Can a System76 person fill us in on this detail? Is the Nvidia part on the board, but disabled or was a different board used?

The way all Optimus systems are designed is that they use the Intel graphics to display everything on the screen.  The Nvidia card, when needed, does its processing and dumps the information into the frame buffer on the Intel "card" to display.  There is no unsoldering anything, either you have Optimus or you don't.  The closest Sager/Clevo unit to the Pangolin is the Sager NP2252, the Gazelle is a related model similar to the [Clevo W258 ELQ]("http://www.clevo.com.tw/en/products/prodinfo_2.asp?productid=393") but using Intel's high end chips verses the lower end one listed on the page and having much better screen options.

I am hoping that they will offer switchable graphics using Bumblebee, next time since Clevo finally added a backlit keyboard option making the current P150em almost the laptop of my dreams and an excellent candidate for the Serval. :D I appreciate what System76 does in making sure that their machines run out of the box, there is no hunting for drivers to get things running, no headaches where you have something sort of working.  Nvidia has made some movement toward making Bumblebee and their drivers work together better so maybe next update things will meet System76's standards.

---

### Post by cprofitt on 2012-09-01
> **pgm_01 said:**
> The way all Optimus systems are designed is that they use the Intel graphics to display everything on the screen.  The Nvidia card, when needed, does its processing and dumps the information into the frame buffer on the Intel "card" to display.  There is no unsoldering anything, either you have Optimus or you don't.  The closest Sager/Clevo unit to the Pangolin is the Sager NP2252, the Gazelle is a related model similar to the [Clevo W258 ELQ]("http://www.clevo.com.tw/en/products/prodinfo_2.asp?productid=393") but using Intel's high end chips verses the lower end one listed on the page and having much better screen options.

I am hoping that they will offer switchable graphics using Bumblebee, next time since Clevo finally added a backlit keyboard option making the current P150em almost the laptop of my dreams and an excellent candidate for the Serval. :D I appreciate what System76 does in making sure that their machines run out of the box, there is no hunting for drivers to get things running, no headaches where you have something sort of working.  Nvidia has made some movement toward making Bumblebee and their drivers work together better so maybe next update things will meet System76's standards.

I am not sure what use I would have for a backlit keyboard, but it would be a nice option to see.

---

### Post by cprofitt on 2012-09-05
I for one get all I need out of the Intel Graphics solution and am happy there is an option out there to get a top end machine without Optimus in the way.

---

### Post by pedro.nariyoshi on 2012-09-05
I think the Bumblebee project is awesome, but until NVIDIA releases some support, I'd stick with Intel HD, I have a HD3000, I can run Starcraft fairly well, HD4000 is about twice as fast, not to mention Haswell, which I've heard will also be a big leap on Intel Graphics.

---

### Post by cprofitt on 2012-09-05
What is haswell?

---

### Post by jbelmonte on 2012-09-06
> **cprofitt said:**
> What is haswell?

[Haswell]("http://en.wikipedia.org/wiki/Haswell_(microarchitecture)") is the codename for a processor microarchitecture to be developed by Intel's Oregon team as the successor to the Ivy Bridge architecture.

---

