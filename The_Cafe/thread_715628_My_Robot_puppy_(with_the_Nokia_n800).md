---
title: "My Robot puppy (with the Nokia n800)"
date: 2008-03-05
forum: The Cafe
---

### Post by linux23dragon on 2008-03-05
**UPDATE-27-09-08:  Youtube videos are now updated**

Hi guys and girls

I've built my very own Open Source Linux robot using the Nokia n800 and the Advanced Bioloid Robot kit from Robotis.

Have a look for your self.  This link will show you my movie in HD mode (goes for 8-9 minutes) :-

[[COLOR="Blue"]Robot dog (with Nokia n800) link[/COLOR]]("http://au.youtube.com/watch?v=y4PNvsZU9IA&feature=PlayList&p=EB7A4E55165D1465&index=0")

This next movie is the Bioloid robot by it self  (goes for 30 seconds):-

[[COLOR="Blue"]Robot puppy without Nokia n800 link[/COLOR]]("http://au.youtube.com/watch?v=oLl3pBiFVBg&feature=PlayList&p=EB7A4E55165D1465&index=1")

Hope you guys like it :)

---

### Post by nutz on 2008-03-05
Does it defecate on the carpet?

---

### Post by linux23dragon on 2008-03-05
> **nutz said:**
> Does it defecate on the carpet?

lol

No.   But I could add a water gun in there somewhere  ;)

---

### Post by nutz on 2008-03-05
> **linux23dragon said:**
> lol

No.   But I could add a water gun in there somewhere  ;)

Now that is a good dog!

---

### Post by linux23dragon on 2008-03-05
> **nutz said:**
> Now that is a good dog!

The good thing about the program (The dog is currently using), is that it will turn off the servos when the robot goes to sleep.  This extends the battery charge life some what.

The standard programs (that comes with the Bioloid robot kit), will keep the servos running continuously no mater what.

---

### Post by CaptainCabinet on 2008-03-05
Now that is cool. :D
Nice one. So is it completely built by you from the ground up? Besides the phone face. :)

---

### Post by linux23dragon on 2008-03-05
> **CaptainCabinet said:**
> Now that is cool. :D
Nice one. So is it completely built by you from the ground up? Besides the phone face. :)

Well, I did not do the tooling to make the parts nor did I develop the software.  But I did assemble the parts, program the robot and added all of the needed parts.

That is :-

I Installed the Bluesmirf and configured the baud rate of the bluetooth connection (BT to MCU only), using minicom.  And Modified the head of the robot  to allow me to mount the n800.  

It takes 12 hours to assemble all together (no breaks) 

EDIT: Here is a post I made to show how I programed the Bluetooth device :- [[COLOR="Blue"]Post link[/COLOR]]("http://robosavvy.com/forum/viewtopic.php?t=551&start=21") *<-might need to click on it twice to get the actual page*

You can program (develop and compile your software) this robot using the AVR-GCC tool chain.  yes you only need to know the C programing language.  The source code is Open Source too :)

More information can be found on the same youtube page links.

---

### Post by Linuxratty on 2008-03-05
Do you control it,or can it do things on it's own?

---

### Post by CaptainCabinet on 2008-03-05
More than I could ever do. :)
The best thing I've ever made is a bird house. And that's remained unoccupied in the garden for over 2 years.

---

### Post by linux23dragon on 2008-03-05
> **Linuxratty said:**
> Do you control it,or can it do things on it's own?

Hi Linuxratty.

You can controll the robot with another Nokia n770,  n800 or Notebook/PC.  The demos (I've posted) demonstrates that the robot can work without the remote (The robot just depends on its very own sensors in this case).

The built in sensors it uses detects light and sound and movement.  You can add tilt sensors or even gyros (gyroscope).  And you can install a small web cam on it too.  In fact the Nokia n800 already has one of those built in.

"Just imagine having my robot dog walking around giving me video surveillance of my own house or back yard".

You can add or remove as many moves as you like.  And you can make the robot say anything you like as well (by remote control).  The robot uses text generated voice,  but I can see the potential of voice commands in the near future (just like the Asus Eee PC).

---

### Post by linux23dragon on 2008-09-27
I've updated the youtube videos for all to see :)

Enjoy

---

### Post by delfick on 2008-09-27
> **linux23dragon said:**
> but I can see the potential of voice commands in the near future (just like the Asus Eee PC).

that'd be awesome :)

especially if you get the dog to be able to communicate with electrical devices in your house (i.e. lights (if that's even possible), tv, computer, etc)

"dog, change channel to 7"

:)

---

### Post by linux23dragon on 2008-09-27
> **delfick said:**
> that'd be awesome :)

especially if you get the dog to be able to communicate with electrical devices in your house (i.e. lights (if that's even possible), tv, computer, etc)

"dog, change channel to 7"

:)

Well it might be possible since the nose sensors do have [[COLOR="RoyalBlue"]***infeared***[/COLOR]]("http://en.wikipedia.org/wiki/Infrared_Data_Association") diodes (like what your TV, DVD, Foxtel remotes use).



mmmm :)

---

### Post by earthpigg on 2008-09-27
awesomeness.

---

### Post by linux23dragon on 2008-09-27
> **earthpigg said:**
> awesomeness.

Thanks earthpigg :)

---

### Post by smartboyathome on 2008-09-27
Thanks for showing me this! I am definately going to let my friend know (they're in a robotics group I go to sometimes).

---

### Post by linux23dragon on 2008-09-28
> **smartboyathome said:**
> Thanks for showing me this! I am definately going to let my friend know (they're in a robotics group I go to sometimes).


Your welcome smartboyathome.  I hope your mate will like it :)

Also the robot can be humanoid too.  Some people have already experimented with gyros and other tilt sensors as well. This will allow the robot to walk correctly (lifting its feet instead of shuffling around) and climb  stares.  Some people have even made them do cart wheels and martial fighting too.

---

### Post by earthpigg on 2008-09-28
kung fu robot?!

*runs for the hills*

---

### Post by smartboyathome on 2008-09-28
> **earthpigg said:**
> kung fu robot?!

*runs for the hills*

No, Ninja Robot. ;)

Anyway, I think they would love this. How does it compare to the Lego robots though (what they use currently)?

---

### Post by smuki on 2008-09-28
Nice work there mate, and quite a good pup too (love those ones that are house trained). It moves a good deal more than I thought it would from the start of the clip.

---

### Post by linux23dragon on 2008-09-29
> **smuki said:**
> Nice work there mate, and quite a good pup too (love those ones that are house trained). It moves a good deal more than I thought it would from the start of the clip.

Thanks smuki

The amount of moves it can do by itself also surprised me.  And thats just the robot puppy responding to its own sensors.  You can also control the robot puppy via a remote Nokia n800/770 or any other computer that has WiFi. 

You can also make it say anything you like too, just type in the text and hit enter :)

---

### Post by linux23dragon on 2008-09-29
> **smartboyathome said:**
> No, Ninja Robot. ;)

Anyway, I think they would love this. How does it compare to the Lego robots though (what they use currently)?


I think you can do more with the Lego robots since you build the parts you need.  So you can experiment more with robotic structure ideas.

In fact the Lego kits can be used to build custom automation tools too.  So in effect you have a prototype tool box.

The Advance Comprehensive Bioloid kit has 26 different projects.  You have wheels and servos to play with.  But you are restricted with a number of parts that you cannot build from scratch.  Thats not a bad thing.  It has its place in the market for other types modifications or add ons you might need to focus on instead. 

**UPDATE EDIT** I just found this [**_[COLOR="Blue"]Bioloid robot[/COLOR]_**]("http://au.youtube.com/watch?v=aQe0WFJG1K4") on youtube by ***balhan00***.  It shows how you can use the wheels that comes with the kit.   

I'm not sure if you can make humanoids or puppy robots as big or strong, using the Lego kits.  But its worth a go.  I don't own a Lego kit, yet.  But I have researched about it some time ago.

I take it that your friends already uses the Lego bots?

---

### Post by linux23dragon on 2008-09-29
> **earthpigg said:**
> kung fu robot?!

*runs for the hills*

Here, ***srobot*** is in the middle of developing the [[COLOR="Blue"]**_cart wheel_**[/COLOR]]("http://au.youtube.com/watch?v=B-OhwUHise8").

***davidaearthy*** had used the bioloid's servos current load as a [[COLOR="Blue"]**_tilt sensor_**[/COLOR]]("http://au.youtube.com/watch?v=tDuTL-l93kY")

***kymhorsell*** demonstrates the [[COLOR="Blue"]**_self defense_**[/COLOR]]("http://au.youtube.com/watch?v=ysgAbLrRoiY") and other demo moves.

The bioloid humanoid is very top heavy due to the internal battery pack, mounted into its back.  As you can see [[COLOR="Blue"]**_here_**[/COLOR]]("http://au.youtube.com/watch?v=bIZZ-e8ACcg").  So you are limited.

There are other robot kits that can give you more movements without to much trouble.

Like the Robonova.

***condortan*** demonstrates the Robonova doing a [**_[COLOR="Blue"]kungfu dance[/COLOR]_**]("http://au.youtube.com/watch?v=P12o6us58yo") on youtube

UPDATE [**_[COLOR="Blue"]More Martial Arts[/COLOR]_**]("http://au.youtube.com/watch?v=lWCubn20szg")by ***BauerMECH***

The Robonova is a very well balanced humanoid robot that can move very fast.  But you can't turn it into a robot dog.

---

### Post by Steve H on 2008-09-29
I tell you what, I'm really impressed with that!! It responded much better than I was expecting...

A really good little job you've done there, keep up the good work!! If you could knock me up a Pat Labor exoskeleton type robot suit I would be very apperciative....

:D

---

### Post by linux23dragon on 2008-09-29
> **Steve H said:**
> I tell you what, I'm really impressed with that!! It responded much better than I was expecting...

A really good little job you've done there, keep up the good work!! If you could knock me up a Pat Labor exoskeleton type robot suit I would be very apperciative....

:D

Thanks Steve H

Glad you liked it.  

Would that be an Pat Labor exoskeleton robot suit to fit a human?
You must be a robot entertainer for various functions?

---

### Post by fedex1993 on 2008-09-29
very cool but i dont know if i want to do that with that nice of a tablet pc :)

---

### Post by linux23dragon on 2008-09-30
> **fedex1993 said:**
> very cool but i dont know if i want to do that with that nice of a tablet pc :)

Thank you fedex1993.

The Nokia n800 is only mounted to the robot head with four double sided foam tape squares.  I can (and have) pull the Internet tablet off very easily without any damage.

The Internet tablet communicates to and from the robot via Bluetooth.  So its a no fuss attachment.

---

