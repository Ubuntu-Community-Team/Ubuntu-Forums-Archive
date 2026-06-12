---
title: "kernel: [ 9781.834868]"
date: 2008-09-23
forum: Security
---

### Post by jmore9 on 2008-09-23
I have googled and searched but i am not able to find info on this kernel message number.  Complete line is :

Sep 23 11:48:35 jeff-desktop kernel: [ 9781.834868] hub 2-1:1.0: port 4 disabled by hub (EMI?), re-enabling

then i see

Sep 23 11:48:35 jeff-desktop kernel: [ 9781.834898] usb 2-1.4: USB disconnect, address 3

At the time the machine had been running for about 1.5 hours.  The above refers to the web cam that is connected to it as security cam.  When i checked the machine at 11:50am the web cam light was of

right after the 2 above items is the following :

Sep 23 11:48:35 jeff-desktop -- MARK --

What does -- MARK -- mean ?

It looks like the usb cam was disconnected at 11:30:08.  there is no one that has access to the machine because it is locked up in my apt.
I have been using this for over a year and this is the first.  Also this machine has 0 that is none connection to internet or any other machine.  Nothing else is on it except for the web cam software.

I am using 8.04 plain

---

### Post by cariboo on 2008-09-23
Have a look here:

[http://ubuntuforums.org/showthread.php?t=500186](http://ubuntuforums.org/showthread.php?t=500186)

Post #1 may solve your problem.

Jim

---

### Post by niteshifter on 2008-09-23
Hi,

Could be an issue with braille tty (brltty) but as the setup worked for more than a year I'd look at:

Cabling / connector(s).
The webcam itself, it may be failing.

Basically the kernel message is saying the usb sub system saw noise at that connection point.

---

### Post by lmno745 on 2008-09-23
What is World of Warcraft?Players from across the globe can leave the real world behind and undertake grand quests and heroic exploits in a land of fantastic adventure and [yoga mats]("http://www.yoga-mats.cn/") . Do you want to [China Travel guide]("http://www.china-travel-guide.cn/") yourself?So please let us do this task for you, one of our World Of Warcraft powerlevelers work for you as a full- time job other than part-time.s a massively multiplayer online game, World of Warcraft enables thousands of players to come together online and battle against the world and each other. As we know, When you first start a game of World of Warcraft, you will be taken to your race's starting area. All the races except trolls and gnomes begin in a unique location.So it takes a long time to powerlevel a powerful character for many players, for the player's energy and time are limited. [http://www.yogawww.com](http://www.yogawww.com), [http://www.chinatravelvip.com](http://www.chinatravelvip.com), WOW Power Leveling is our primary service, we offer [wow gold]("http://www.wowchina.us/") & [wow gold]("http://www.wowgoldsell.com/") service,and is on sale now for a limited time! You can purchase our power leveling service at a much lower price than any of our competitors. We don't use any Bots or Macros to power level your character.All of our employees are skilled World of Warcraft players, who personally powerleveling your character, to provide even more safety to your account.  We will complete the wow power leveling in a very short time, and you can play the character at your desired level. During the progress of World of Warcraft powerleveling, you can get all information about your World of Warcraft powerleveling status anytime.We use real players (WOW Power Leveler) to level your character, ALL HAND MADE. Your account will be safe and secure,GUARANTEED.Our goal is to make sure all our customers are satisfied with their wow powerleveling & [cheap wow gold]("http://www.howtogold.com/") orders. We upgrade your characters levels, skills and more.safety to your account.[http://www.yogawww.com](http://www.yogawww.com), [http://www.chinatravelvip.com](http://www.chinatravelvip.com), [www.wowchina.usOur](www.wowchina.usOur) team consists of veteran players with over 1 years of playing experience, they offer quality and professional service to all our customers. No risk is ever involved during this process.Our staff will not chat to anyone during this progress, so don't afraid about your character.Our service is standing by 24/7 to serve you.

---

### Post by jmore9 on 2008-09-24
Don't know what happened but ran it for 10 hours after wards and there was no problems.  So i would guess that i have some unwanted visitors in my apt. when i was away !

I will get a steel or heavy wood cabinet and put the machine in it with locked doors and that should end that problem.

As i said earlier , it ran for months with no problem.  No internet to screw things up, No other users , No other use than running the web cam as a security cam.

I have in the past had some of the people than live in this apt. building in Grand Rapids, MI steal / hijack my telephone service so i guess i should not be surprised that there are thieves living here also.

But back to the problem i think they unplugged the cam and then plugged it back in which stops camstream from aquiring the video.  It keeps working but there is no images saved after that time.

Thanks for your responses

Jeff M

---

### Post by oscarsfriend on 2008-09-24
This sounds to me like a problem that effects some people with USB TV turners, and (I think) USB hard drives (I had it myself with a TV turner).  IIRC it was some bug introduced into the kernel that would intermittently cause USB 2.0 devices to be incorrectly recognized as USB 1.0 devices, and the device would spontaneously "disconnect" (not literally, but it would no longer be seen to be connected).  Try Googling for "Nova T-500 USB disconnect", and you'll see what I mean.  I'm not sure of the current status of the bug, but I don't think it was fixed in Gutsy (and maybe not Hardy).

---

