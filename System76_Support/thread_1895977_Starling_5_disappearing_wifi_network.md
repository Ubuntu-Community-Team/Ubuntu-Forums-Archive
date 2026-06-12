---
title: "Starling 5 disappearing wifi network"
date: 2011-12-15
forum: System76 Support
---

### Post by chownoir on 2011-12-15
I've got a problem that I seem to have figured out a work around but not sure if it's indicative of a bigger long term problem.

I've owned this netbook for about 5 months and this problem has occurred a few times. My home wifi connects fine automatically most of the time after I turn it on. The problem is when it shows no wifi connection at all after powering up. Using the function key to turn the wifi off and on does nothing. The drop down menu won't even show my network or neighbors. It's a truncated menu that only shows enable network and edit connections as the only available options. It doesn't even show a choice of show hidden networks. 

Clicking the enable network off and on does nothing. The workaround is I plug in a land line connection. It recognizes it right away and I have a connection. As soon as that happens, the network menu reverts back to normal. All options available and all wifi options show up, mine and neighbors. I unplug the land line and it automatically connects the wifi like normal.

Anyone know what's going on to cause this? I've been pretty happy with my netbook. It's doing everything I need and no other problems. I've been travelling quite a bit since I got it 5 months ago and I've connected with no problems. But this just seems weird to me. Appreciate any thoughts.

Thanks.

---

### Post by chownoir on 2011-12-21
Anyone?

---

### Post by isantop on 2011-12-21
My guess is that this is a glitch with Network Manager. Have you tried turning wireless Off, then on using Fn+F11?

---

### Post by chownoir on 2011-12-22
Turning it off and on via Function key works fine when it's running regularly.

The problem arises when it doesn't show a signal and the truncated menu. The function key doesn't work. I try rebooting and nothing happens. The only way it fixes it is for me to connect using the ethernet to my router. Then it blinks on with full menu. All other wifi networks show up and it automatically connects to my home one normally. 

After that the function key command works again. But it's got to be after I plug in. Everything related to the wifi is frozen and no commands available on the drop down except for edit connection before plugging in. Other wifi networks don't even show up.

---

### Post by isantop on 2011-12-23
How frequently does this happen? Could you try running from a LiveCD to rule out the possibility of a bad installation?

---

### Post by dodo3773 on 2011-12-26
Did you try switching to "wicd" network manager and seeing if the problem still persists?

---

### Post by newbie5 on 2011-12-28
Hey,
 
Had a similiar issue with my Starling, shortly after updating. Thanks for posting your quick fix - going to use this to get back online then try to figure out what is going on and long term fix.
 
Found this old thread: [http://ubuntuforums.org/showthread.php?t=1247040 ]("http://ubuntuforums.org/showthread.php?t=1247040")
Could be related.

---

### Post by chownoir on 2011-12-28
It's happened 4 times since I received it in July. I use it daily and love it. 

I don't have a LiveCD and don't know how to switch to wicd in network manager. As I said, I'm just concerned if it's a long term problem or indicative of a potential bigger issue. The workaround of plugging in the ethernet to fix it seems to be fine and if I'm at home, it's not a problem. I'm worried if it occurs when I'm on the road and how to fix it. 

Aside from this one issue, the product has exceeded my expectations and I've been very happy with how it runs otherwise. I'm not savvy at all with linux or very tech knowledgeable but I'm not afraid to poke at things with clear instructions. I just don't even know how to get to a command line and do things from there.

I love how the Starling is great for travel, I can surf, log in for work email and do spreadsheets and documents for work with more than enough processing power in the little machine to have multiple items open and still work quickly and efficiently. The wifi connects easily anywhere I go. Very happy with the purchase. I want to be able to use this for as long as I can.

I like it so much, I've become a bit of a System76 evangelist to a couple other work friends who have similar needs but didn't want a windows machine with the bloat to weigh down the processing speed or deal with virus scares. They've all been impressed by how productive I can be on the machine and now are looking at the Lemur since the Starling is no longer available.

Just hoping this problem is minor and wont' bite me down the line when I really need to use the computer. Thanks.

---

### Post by isantop on 2011-12-28
> **newbie5 said:**
> Hey,
 
Had a similiar issue with my Starling, shortly after updating. Thanks for posting your quick fix - going to use this to get back online then try to figure out what is going on and long term fix.
 
Found this old thread: [http://ubuntuforums.org/showthread.php?t=1247040 ]("http://ubuntuforums.org/showthread.php?t=1247040")
Could be related.

Actually, we're using a different wireless chipset on the newer Starlings which has eliminated the issues we had with Star1s and WiFi.

> **chownoir said:**
> It's happened 4 times since I received it in July. I use it daily and love it. 

I don't have a LiveCD and don't know how to switch to wicd in network manager. As I said, I'm just concerned if it's a long term problem or indicative of a potential bigger issue. The workaround of plugging in the ethernet to fix it seems to be fine and if I'm at home, it's not a problem. I'm worried if it occurs when I'm on the road and how to fix it. 

Aside from this one issue, the product has exceeded my expectations and I've been very happy with how it runs otherwise. I'm not savvy at all with linux or very tech knowledgeable but I'm not afraid to poke at things with clear instructions. I just don't even know how to get to a command line and do things from there.

I love how the Starling is great for travel, I can surf, log in for work email and do spreadsheets and documents for work with more than enough processing power in the little machine to have multiple items open and still work quickly and efficiently. The wifi connects easily anywhere I go. Very happy with the purchase. I want to be able to use this for as long as I can.

I like it so much, I've become a bit of a System76 evangelist to a couple other work friends who have similar needs but didn't want a windows machine with the bloat to weigh down the processing speed or deal with virus scares. They've all been impressed by how productive I can be on the machine and now are looking at the Lemur since the Starling is no longer available.

Just hoping this problem is minor and wont' bite me down the line when I really need to use the computer. Thanks.

I don't think this issue indicates a deeper issue.

That brings up a good point. Have you had it happen when you aren't at home? If not, it could be something funky with your router, and that would be an entirely different set of fixes.

---

### Post by chownoir on 2011-12-28
Haven't had it happen on the road. Only at home. I'm kind of confused how my router at home would make all the networks disappear though?

And it happened again tonight, except now the ethernet work around isn't fixing it. It detects the ethernet connection and I'm fine. But the function key +11 isn't doing anything. When I unplug the ethernet, the menu is still truncated, no networks showing up, the menu choice for enabling wireless doesn't even show up. 

I'm now officially stuck. No wifi connection. Guess I'm glad I started this?

---

### Post by chownoir on 2011-12-28
Another piece of data fwiw, I got it working again with the ethernet workaround. The only difference this time was the power was plugged in along with the battery. When I was trying it earlier running on just the battery, nothing happened. Then I remembered all the other times I was plugged in. Dragged the cord over, shut down, plugged in, powered up with the ethernet plugged in. Everything fired up with full menu. I unplugged ethernet and it's now working fine.

When I'm at home, I normally have the battery pulled out and it runs off the power cord. I'm usually flopped on the couch and the netbook stays there every night unless I need to travel. That's the only time the battery gets put in. Otherwise it stays out.

Don't know if that makes a difference.

---

### Post by chownoir on 2012-01-05
This is a dead end then and I just have to live with it and hope it doesn't occur when I'm on the road?

---

### Post by isantop on 2012-01-05
I'm thinking the issue has something to do with your router, rather than your netbook. Since it hasn't happened on the road yet, this is a more likely explanation.

---

