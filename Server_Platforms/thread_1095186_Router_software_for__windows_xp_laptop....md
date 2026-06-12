---
title: "Router software for  windows xp laptop..."
date: 2009-03-13
forum: Server Platforms
---

### Post by hockey97 on 2009-03-13
Hi, I have a router for my house.

Currently my sister got a brand new blue-ray player which I bought for her on her birthday well me and my other sister chipped in.

well anyways my sister is really bugging me to find a way that I can connect the net flix thing to the internet.

So I am asking help here if there is any software that is free that can act like a router.


My thoughts were to turn her laptop into a router kinda and then connect the blue-ray reciver to her laptop by a Ethernet cable.

Is this possible?

The problem is that the blue-ray thing is only ethernet connections to the internet.

and her room is on the 2nd floor and our router is in the basement.

So their is no way we can drill holes and feed up a Ethernet wire to her bedroom.

Do you think that will work???


I know with linux ubuntu since I have it on my computer which is on the main floor.  I know that I can install some software package that will allow my computer to act as a router.

the laptop is wireless.


is this possible and what software would work on windows xp?

---

### Post by netztier on 2009-03-13
> **hockey97 said:**
> 

is this possible and what software would work on windows xp?

Comes with the default XP package, I think? it's called "internet connection sharing".

It can be configured to "share" it's WiFi connection to the LAN that is connected to it's Ethernet port. Never done this myself on XP, but with the GUI, it should be pretty straightforward. The fact that the WiFi network itself is not directly attached to the Internet but behind another Router is not relevant, it should work all the same.

regards

Marc

---

### Post by jimv on 2009-03-13
It's called "Internet COnnection Sharing", and it's really easy to set up in XP.

[LIST=1]
[*]Open up the Network Connections Control Panel.

[*]Right click on the wireless connection and click Properies.

[*]Click the Advanced tab.

[*]Check the box that says  "Allow other network users to connect through this computer's internet connection"

[*]Click Apply, and close the window.
[/LIST]

Now you should be able to just plug an ethernet cable into the laptop and the other thing and it will be able to access the net.

---

### Post by albandy on 2009-03-13
> **hockey97 said:**
> Hi, I have a router for my house.

Currently my sister got a brand new blue-ray player which I bought for her on her birthday well me and my other sister chipped in.

well anyways my sister is really bugging me to find a way that I can connect the net flix thing to the internet.

So I am asking help here if there is any software that is free that can act like a router.


My thoughts were to turn her laptop into a router kinda and then connect the blue-ray reciver to her laptop by a Ethernet cable.

Is this possible?

The problem is that the blue-ray thing is only ethernet connections to the internet.

and her room is on the 2nd floor and our router is in the basement.

So their is no way we can drill holes and feed up a Ethernet wire to her bedroom.

Do you think that will work???


I know with linux ubuntu since I have it on my computer which is on the main floor.  I know that I can install some software package that will allow my computer to act as a router.

the laptop is wireless.


is this possible and what software would work on windows xp?

The ethernet connection of the player it's for broadcast what the player is playing or to play shared video files in the player?

I think wifi it's too slow to let the player play hi-res movies throght the lan.

Also I think you should not share the internet connection because it will use NAT, I think you should make a bridge between the wifi interface and the ethernet interface.

To make a bridge in windows you should select the two net devices (the wifi and the ethernet) and select make a bridge in options.

---

### Post by hockey97 on 2009-03-13
Thanks. I forgot all about that. 

I did a bridge.  

 I never did used it and I do remeber seeing it in the network connections settings before.

At that time I never thought it would be usefull cause I never got around my head why you you want to share a internet connection through your computers.

Now I see why...lol

Thanks guys. I played around with it and had to go in dos to force the wireless card to be in capadable mode. Otherwise it wouldn't work.

so it's working and I am guessing my sister will be happy to be able to use netflix.

she got me a wii for my birthday and that boom blox games which she likes.

lol

I really didn't want a game console. 

Thanks guys for reminding me of such a feature.

---

### Post by Iowan on 2009-03-14
> **hockey97 said:**
> Thanks guys. I played around with it and had to go in dos to force the wireless card to be in capadable mode. Otherwise it wouldn't work.CLI is a wondrous thing... long live CLI  :D

---

