---
title: "wireless set to off on restart"
date: 2009-07-18
forum: System76 Support
---

### Post by miniyak on 2009-07-18
just recently when i restart my pangolin my wireless card is turned off and it takes about 5-10 minutes to get it on by pressing the fn-f11 key combination. pressing these combo seem completely unresponsive and it feels as though it comes on when it wants.

---

### Post by thomasaaron on 2009-07-20
You definitely should not have to push the wireless key combination to get it going. However, if you're pushing it, that could be contributing to the long wait.

Does this happen on a **fresh restart**?
Or is it happening after **resuming** from suspend or hibernate?

If it's happening after a **fresh restart**, what happens if you just wait? Does it eventually come on? If so, after how long?

---

### Post by miniyak on 2009-07-20
this happens only on a fresh start

if i wait the connection stays off, left clicking on the network tray icon results in faded options. normally i have to wait 5-10 minutes

this mourning i had to do a full start cold because it failed to go into stand-by yesterday, sure enough the problem was still there. I hit the fn-f11 combo, then came back latter and it was working. I was gone for about 5 minutes

---

### Post by thomasaaron on 2009-07-20
Please boot a couple of times from a live CD and see if this happens. That way we will know if it is a hardware issue or a configuration problem.

---

### Post by miniyak on 2009-07-21
I just tried the 9.04 live cd and had the same issue. I waited without intervention for about 10 minutes, and also waited while after turning the wireless on

However this time i noticed another anomaly. whenever i manually turn the card on it does actually turn on. I know this because it will allow me to connect to a hidden network. The card is just failing to see the wireless networks initially. From the live cd it only found one network at first (out of 9 in my area, not my own) after about 15 minutes. Then after turning the card off then back on it recognized 3 more one being my own.

knowing this i restarted back into my hard disk install and tried to connect to my network as though it was a hidden one. This failed but after i turned the wireless off then back on a few of the networks were found including my own. ( 2 minutes to connect vs. 15 )

---

### Post by gila_monster on 2009-07-21
miniyak,

forgive me if I am missing something, as I've lost track of the chain of events a bit. My understanding here is that you are having trouble getting the machine to have wireless on when you boot? And then, if you turn the wireless on with fn-f11, it doesn't see the wireless networks?

I'm not sure I can address the first, but I have seen the second on my machine. There is something about networkmanager that prevents it from seeing wireless networks when you turn the wireless on after NM is running. I forget the command off the top of my head (replying at work, which I shouldn't be), but you need to restart networkmanager once the wireless is on. Then it sees the networks just fine.

I've not figured out if this is a NM problem, or a kernel problem or what.

---

### Post by miniyak on 2009-07-21
gila_monster,

you got it right

1- no wireless on boot (with install and live cd)

2- Manual turn on = missing networks

3- waiting or manual toggling on/off of the wireless card results in eventual connection (not quite sure what goes on in the background that trigers working state)

I guess i could end the nm-applet process for the system monitor then start it back up with the terminal next time i have to do a reboot, but im not sure how well that will work

It is good to see there is an explanation for some of this issue though
random cause + random effect is tough to trouble shoot

---

### Post by jml on 2009-07-21
To risk stating the obvious, it seems to me that Jaunty may have gone a bit too far in achieving cutting edge, vs. stability/reliability.  It's not just wireless networking.  I have read many comments and have experienced the random freeze up that occurs with routine use, with the entire system "waiting" for a few seconds before it returns to normal.  Hopefully, this will improve in the next release.

Joe

---

### Post by miniyak on 2009-07-21
...this is really topic for another thread but i agree with jml. Given the choice i would have chosen stability by default and put cutting edge on a separate partition. Ease of support is what the LTS release idea is suppose to remedy. Works great for canonical, but hardware vendors like s76 have to decide between reliability or selling points for preinstalls. At least s76 backs their decision up with good support. Ok compromise for now, so long as ubuntu is a niche thing, but like i said probably a topic for another thread.....

---

### Post by gila_monster on 2009-07-21
miniyak,

Okay, when I get home, I'll check on the proper command (I usually just enter it from alt-f2) and you'll at least be up and running. It's not optimal, but it works, and it's not hard.

EDIT: The command I use is

```
gksudo /etc/init.d/NetworkManager restart
```

---

### Post by thomasaaron on 2009-07-22
All of that aside, though, this one just flat out isn't right...

> 1- no wireless on boot (with install and live cd)

I absolutely can't duplicate that in the shop, and wireless works out of the box with your computer (i.e. no System76 driver necessary).

So, unless you've flashed your BIOS or something on a firmware level, I'd call this one a bad wireless card.

It's also possible that a wire is loose on your wireless card, so you might want to remove your battery/ac and remove the larger panel on the bottom of your machine and check the antenna wires.

Once that is resolved, the rest of the problems may resolve themselves.

---

### Post by miniyak on 2009-07-22
besides changing boot priority i have stayed out of the bios and i would not intentionally mess with firmware.

I will have time to check the card in about an hour or so

---

### Post by miniyak on 2009-07-22
sorry web service was down this afternoon ( comcast...)

Anyway, i figured out the issue... well, it sort of figured it self out.

I unscrewed the panel to take a peek inside and found that everything seemed to be in order antennas secure and card fastened in place properly. ( though for future support i recommend referencing that the fan is attached to the panel. Almost pulled it out thinking it was just the panel, i should have read the manual) Then i put the panel back on without touching anything.

After this i booted back up and everything worked fine then tested the live cd again and everything worked there too. At first i was surprised then i realized one discrepancy i thought was negligible. That this was the first or maybe second time i have "shutdown" since getting the laptop in May (even from live cd). I "restarted" plenty of times and figured this was the same as a shutdown but now i'm thinking that restarting leaves some things "hot" for lack of a better term.

Definitely correct me if i'm wrong but i going to say the moral to the story is that selecting shutdown is the only "fresh start".

Thanks for the help, Tom and gila_monster

---

