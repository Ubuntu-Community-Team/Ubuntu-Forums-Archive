---
title: "Looking for Professional Broacasting Softwares"
date: 2009-06-14
forum: Ubuntu Studio
---

### Post by moe19790 on 2009-06-14
Hi,
 
Since my main job is related to Radio/TV. i would be thankful if you can advice about professional products "Even if its paid" for Broacasting something like
 
- Play out Video server
- Play out Audio Server
-Automation Softwares
- Recording Servers
- Characters Generators "To inserts logos, comments, news bar ....etc
- SMS softwares
 
[FONT=Times New Roman][SIZE=3]Thanks[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]MOe![/SIZE][/FONT]

---

### Post by Stochastic on 2009-06-14
Take a look at Rivendell for radio broadcast software.  It's not very easy to set up on Ubuntu but can be done.

---

### Post by moe19790 on 2009-06-15
Thanks....... Any Other suggestions people? btw any replacement for the Apple final cut?

---

### Post by Stochastic on 2009-06-15
> **moe19790 said:**
> Thanks....... Any Other suggestions people? btw any replacement for the Apple final cut?

Video editors are plentiful in Linux, but not too many are pro quality yet.  Blender, Cinelerra, and Kino are probably your best bet (but I'm not a video guy).  Do a search in this section of the forums for threads titled "Best Video Editor" and you'll find many heated discussions on the topic.

Back to your original list, what exactly is an automation server? and what type of SMS software are you looking for?  Lastly, what features would you need in a 'recording server'?

---

### Post by moe19790 on 2009-06-15
Automation Software is exactly what you advised with earlier "Play a list of songs/files" a pre-scheduled advertisement will pop up when its time . you can put and save prog for a month or so in advance and so on.

regarding the SMS software, i want a software which can be programed to read the txt sms received by the SIM Card /phone attached to the computer/server so, that it can be filtered and passed into the CG "Chartecter Generator" in order to instered it on the playout server "as a bar at the bottom of the t.v screen"

---

### Post by moe19790 on 2009-06-18
Come on people, show some support :D

---

### Post by akakingess on 2009-06-19
> **moe19790 said:**
> Come on people, show some support :D
I don't think anybody is ignoring you, just don't think that there is anything readily available or that there are too many people that may know what you are talking about. I know what you are talking about and couldn't tell you of any more info than you've gotten. As far as editors go, I'm an Avid guy and can't get away from my Windows-based Media Composer (I know, I know) long enough to try any of the "open-source" NLEs, but as far as ad insertion, sms, etc. I don't know that anybody has come up with a great solution for Linux. I mean you are talking about a very commercial (no pun intended) environment, and for the longest time that meant analog tape and a Mac for graphics. Let me know if you end up finding something out as I might know some people that would be interested, and I will ask some of the broadcasters I know in town, but my best bet is to google it, which I will. I will reply if I think I can be of any assistance, sorry if I disappointed....

akakingess

Didn't even notice the similar Avatar, I swear I just use it because I work nights and sometimes makes me feel like a nocturnal creature ;)

---

### Post by Stochastic on 2009-06-19
Part of running Linux is being able to hunt this information down for yourself rather than relying on people spoon-feeding you (please don't take that in any disrespectful manner, I'm just mentioning it because many new users expect this from the forums).

Don't expect a drop-in solution for Linux.  You'll probably need to hook together about four different apps to get the desired results.  This is normal in Linux, and I like it that way, it gives many more configuration options than a one-size-fits-all software box.

I know that a recording server can be setup, if you mean an audio recording server then you'll probably want to run ecasound in conjunction with some custom bash scripts (fairly advanced setup level).

As for the visual effects stuff, I'd hunt through some of the VJ software I posted about here: [http://ubuntuforums.org/showpost.php?p=6357124&postcount=3](http://ubuntuforums.org/showpost.php?p=6357124&postcount=3) to give you some ideas/leads.  The Pixel festival may have much more information for you to pour throuh: [http://www.piksel.no/pwiki/FrontPage](http://www.piksel.no/pwiki/FrontPage) it's dedicated to open-source realtime audio & video processing software.

SMS should be easily read by any computer, after all it's just text data.  Infact doing ```
apt-cache search sms
``` returns a few very interesting packages in the ubuntu repos: 
[gsm-utils]("http://packages.ubuntu.com/jaunty/gsm-utils") - GSM mobile phone access applications
[libgsmme1c2a]("http://packages.ubuntu.com/jaunty/libgsmme1c2a") - GSM mobile phone access library
[smsclient]("http://packages.ubuntu.com/jaunty/smsclient") - A program for sending short messages (SM / SMS)
[smstools]("http://packages.ubuntu.com/jaunty/smstools") - SMS server tools for GSM modems

then just run ```
apt-cache rdepends smstools
``` to find out which packages depend on smstools, and the result is:
Reverse Depends:
  [gnokii-smsd]("http://packages.ubuntu.com/jaunty/gnokii-smsd")

go forth and search!  Oh, and you do know about this handy site right: [http://www.google.com/linux](http://www.google.com/linux)


Hope that helps.

---

### Post by akakingess on 2009-06-19
Actually, I didn't know about google.com/linux, I just used to search google straight up, thank you for the tip!!

akakingess

---

### Post by moe19790 on 2009-06-20
> **akakingess said:**
> I
Didn't even notice the similar Avatar, I swear I just use it because I work nights and sometimes makes me feel like a nocturnal creature ;)

Ahahaahah, yes indeed :) at least it makes me happy 2 know there are some people feeling the same way as i do ;) lol :)

---

### Post by moe19790 on 2009-06-20
> **Stochastic said:**
> Part of running Linux is being able to hunt this information down for yourself rather than relying on people spoon-feeding you (please don't take that in any disrespectful manner, I'm just mentioning it because many new users expect this from the forums).

well, any new babe needs to be "spoon-feeding" at first until he is beeing able to feed by himself.. for my case i`ve been a dedicated windows user in fact windows professionally since what? windows 3.0 maybe? that makes it how long? some where close to 20 right? i believe 17 - 18 years if i`m not mistaken! so i`m all windows as they say, now i`m getting into a 100% new world for me... so for sure i would need guidness!

the second part is when we are talking about commercial use products, even if i do have a few names i still will come here and post them to take ur opinions about it. in home using/testing environments u can try anything the way u want.. but in real like/production environments there is no such a pleasure.. you install it, it should work perfectly :) so, i hope you will not get annoyed by my too many questions ;) 

i seriously want to thank you and all the guys around here for the great help they are doing for the new people like me :) nad hey thanks for the link.. never knew there was such a thing :D

---

### Post by moe19790 on 2009-11-07
its been ages since the last time in here :) so, any of you found good news?!

---

### Post by Silvernail on 2010-03-06
Have you looked at 'ubuntustudio'?

Its available in the synaptic downloader. There are 16 files plus dependencies.

I appears to be a complete OS dedicated to what  you want. I don't know if it has everything.

To deleted it  you will nearly have to do a reinstall of ubuntu. So back up.

HTH
Dave

---

### Post by jerehart on 2010-10-04
So... After digging and spending many hours trying to Rivendell up on  an OpenSource Linux Distro (OpenSuse, Ubuntu) I came across this.


 [http://rrabuntu.sourceforge.net/](http://rrabuntu.sourceforge.net/)
 

Some developers at Rivendell built a custom distro of Ubuntu with Rivendell included in the install scripts.
 I doesn't get easier than that! Ha... Free Radio Automation to the masses!
 

~Jeremiah

---

### Post by shaunthesheep on 2010-11-01
> **moe19790 said:**
> Thanks....... Any Other suggestions people? btw any replacement for the Apple final cut?

Lightworks Open Source is due to be released any day now. It is a professional video editor on a par with Avid Composer and Final Cut Pro. Its release was scheduled for the 3rd quarter 2010, but has not appeared as yet.

[http://www.editshare.com/index.php?option=com_wrapper&Itemid=208](http://www.editshare.com/index.php?option=com_wrapper&Itemid=208)

Editshare, the developers, have said they intend it to be multi-platform including Linux. They have also said that Windows is their first priority.

---

