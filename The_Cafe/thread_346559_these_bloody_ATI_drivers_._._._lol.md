---
title: "these bloody ATI drivers . . . lol"
date: 2007-01-25
forum: The Cafe
---

### Post by Patrick-Ruff on 2007-01-25
sup all. 

I've been wondering lately, since ati's fglrx appears to have absolutly no possibility of supporting aiglx any time soon, are the open-source drivers going to get more then experimental 3d acceleration on cards like mine? (the r300)

if anyone has any news on this or has a good prediction I'd definitely be interested to hear it.

---

### Post by Stemp on 2007-01-26
I don't know for the r300, but it work very well for my ATI 9600 (r350) ;)
So you should give a try.

---

### Post by jdong on 2007-01-26
There's been a lot of  these "when will fglrx do AIGLX" threads... the truth is nobody knows. As far as I know there's no ATI insiders here at the forums, and from what I've seen at the ATI bugzilla there isn't any news there either.

So, the only answer we have is it'll be here when it's here.

---

### Post by Patrick-Ruff on 2007-01-27
I didn't say anything about when will ati support this nonsense.  I was talking about the open source drivers.

and your R350 is under expiremental 3d accel, so that "working very well" you say you have, is basicalyl your card crippled at 50%, unless you're using the fglrx driver.s

---

### Post by mykalreborn on 2007-01-27
it's really a pitty dude. i can't raise enough money to buy an nVidia card. so that means i can't enjoy the beauty of beryl.. :(
maybe in the future... who knows...

---

### Post by Patrick-Ruff on 2007-01-27
well I have a laptop that is only capable of handling an ATI x300.

---

### Post by dbbolton on 2007-01-27
> **mykalreborn said:**
> it's really a pitty dude. i can't raise enough money to buy an nVidia card. so that means i can't enjoy the beauty of beryl.. :(
maybe in the future... who knows...
why not use xgl ?  it worked with my radeon xpress 200m (not exactly a powerhouse graphics card)

---

### Post by mykalreborn on 2007-01-27
> why not use xgl ? it worked with my radeon xpress 200m (not exactly a powerhouse graphics card)

not for me. i read somewhere that the ati driver fails in Radeon RV200 series 9xxx (<9500) cards. my card is an ATI Radeon RV200 9200 Pro and it's practicaly impossible to get xgl working. trust me... i've tried... oh boy have i tried.

---

### Post by Patrick-Ruff on 2007-01-27
XGL isn't even worth it when you get it working. it doesn't have an accelerated GTK, which is really lame.  AIGLX  fixes that and everything runs smoothly.

---

### Post by Mateo on 2007-01-28
XGL was easy to set up for me, but it was buggy (either that or beryl was, not sure which).

---

### Post by Patrick-Ruff on 2007-01-28
it was XGL, trust me.

---

### Post by jdong on 2007-01-28
fglrx+xgl works great on my ATI x1400 laptop... plus or minus the few quirks that are inherent with a nested X-server setup (i.e. DPMS display timeouts, keyboard mapping...) fortunately I've had enough experience with using Xnest as a remote desktop solution that Xgl was second nature.

---

### Post by Patrick-Ruff on 2007-01-28
I just resented the fact that I couldn't get games working well and all that other crap. it took away too much functionallity to be worth it.

---

### Post by Stemp on 2007-01-28
> and your R350 is under expiremental 3d accel, so that "working very well" you say you have, is basicalyl your card crippled at 50%, unless you're using the fglrx driver.s

When I said «working very well», it was for aiglx/beryl. 
I also tried some low 3D graphics games, like Penguin-Racer or Epsxe's emulation games.
So for my needs the free driver is working veryl well and I prefer a card crippled at 50% rather than a binary blob :tongue:

---

### Post by jdong on 2007-01-28
> **Patrick-Ruff said:**
> I just resented the fact that I couldn't get games working well and all that other crap. it took away too much functionallity to be worth it.

fullscreen games launch at DISPLAY=:0 <gamename> just fine. Anything else won't be accelerated as well as native (it is still HW accelerated by the Xgl stack, but there is an additional layer of indirection that ruins performance)


Note also that with Beryl active with NVidia indirect rendering on my desktop, most games will launch in a distorted fashion too -- I'd have to momentarily switch back to Metacity to get games to work. So it's not just an Xgl thing.

---

### Post by Patrick-Ruff on 2007-01-29
I like playing in windowed mode

---

### Post by Kernel Sanders on 2007-01-29
I cant get Edgy working with my ATI Radeon 9600XT :(

I'm hoping Feisty will be better as it will come with preconfigured official drivers \o/ :cool:

---

### Post by Patrick-Ruff on 2007-01-30
I don't know if that will help you or not.  I did more reading on the whole fiesty situation, for those of us who have unsupported cards with the open source drivers will be forced to use fglrx (preinstalled) and it will not automatically have 3d windows and all that nice stuff.  

so really, we're not going to see many good things in the ATI area for a while . . .

---

### Post by WalmartSniperLX on 2007-01-30
All I can say is Ive had nothing but problems with XGL with my X1600 and of course aiglx wont work. However my friend with a geforce 6200 has No probs in XGL :D minus the no direct rendering, it still runs smooth. Damn ati's drivers :D

---

### Post by jdong on 2007-01-30
I'll also add that fglrx's performance is significantly lower than the performance of the SAME card with windows catalyst drivers... and frankly I am not terribly impressed with Catalyst -- some aspects of its design I am highly opposed to and question.

---

### Post by WalmartSniperLX on 2007-01-31
> **jdong said:**
> I'll also add that fglrx's performance is significantly lower than the performance of the SAME card with windows catalyst drivers... and frankly I am not terribly impressed with Catalyst -- some aspects of its design I am highly opposed to and question.

I would have to 2nd that, all the way.

---

### Post by Patrick-Ruff on 2007-02-01
definately, I think us ATI users are screwed for a while. unless someone starts really developing those open source drivers (though, I seriously doubt it would be easy . . . but /somebody/ has to do it.)

really, it's the ONLY reason I can't enjoy ubuntu on my laptop.  (well that and the low battery life . . . )  I've been trying to think of possible ways we can get something done about this . . . but I keep comming up blank.  

maybe an online petition? haha, I don't know anymore, based on everyone in this community I've ever talked to's reactions towards these drivers it doesn't seem like we are capable of coding it our selves.

---

### Post by RobNyc on 2007-02-04
I feel like not even using Linux at home cuz I have a x1600 pro and I have a nvidia mx 4000 at work and no prob

---

### Post by Patrick-Ruff on 2007-02-04
yeah I bet.  I guess we have to just keep hoping (and boycotting ATI untill they decide to do something good driver wise :D.)

---

