---
title: "I am frustrated with Ubuntu!!"
date: 2008-04-04
forum: Testimonials &amp; Experiences
---

### Post by DScuglia on 2008-04-04
I am about ready to switch back to windows. I can get half of the applications to work right. When I try to add/remove for an application installation I keep getting a message that pops up "The list of applications is not available" refresh list. Every single time! When I refresh the list...it says the same thing. Then when I try to install ANY application, the menu pops up again. I get messages the says that the application requires additional hardware for i386 or not supported, or you cant do this, or that cant happen, or when I click on files...nothing....this is getting just....grrrrrr! I can't see how linux can have an advantage over windows other than open source......what am I doing wrong?

---

### Post by Crafty Kisses on 2008-04-04
First off, what version of Ubuntu are you using?

---

### Post by SunnyRabbiera on 2008-04-04
well hold on a minute.
firstly do not expect to learn an entirely new system in a week, things like this take time.
secondly, it could be the program mirrors. plus the add/remove applet is limited in what it can do, it is not the best way to install applications in your system.
You probably have to do something simplistic, like refresh your sources list, there is a application you can use called synaptic that works better then add/remove.
you will find it under system> administration> synaptic package manager.
thirdly what applications do you want/ need?
we can only provide help if you give us time.
and fourth, what Codename said also applies... we need to know your version to help us get you started.

---

### Post by Crafty Kisses on 2008-04-04
> **SunnyRabbiera said:**
> well hold on a minute.
firstly do not expect to learn an entirely new system in a week, things like this take time.
secondly, it could be the program mirrors. plus the add/remove applet is limited in what it can do, it is not the best way to install applications in your system.
You probably have to do something simplistic, like refresh your sources list, there is a application you can use called synaptic that works better then add/remove.
you will find it under system> administration> synaptic package manager.
thirdly what applications do you want/ need?
we can only provide help if you give us time.

Yeah, seriously.

---

### Post by hyper_ch on 2008-04-04
> **DScuglia said:**
> grrrrrr! I can't see how linux can have an advantage over windows other than open source

Then you should indeed go back to Windows.

---

### Post by SunnyRabbiera on 2008-04-04
look we can only do so much, stick around and let us see how we can help you.
believe me linux can be enjoyable, but only if you give it time.
I can understand your frustration, but patience is needed.

---

### Post by Crafty Kisses on 2008-04-04
> **hyper_ch said:**
> Then you should indeed go back to Windows.

Seriously, Ubuntu is a choice. Linux doesn't claim to be better than Windows, there are definitely advantages of Open Source, but if you don't see them, then Windows is for you.

---

### Post by SunnyRabbiera on 2008-04-04
Uh huh, but please give us a chance before doing anything rash...
lets start with the basics and work from there.

---

### Post by morganpatrick on 2008-04-04
I've had problems with repositories recently. If I were you I would try going to system > synaptic package manager, making sure your 'add/remove programs' is closed, and then go to settings > repositories and tell us what you see in there. I would click everything but source code or cd rom.

or, what would be even more helpful for the forum would be to open a terminal, and type

```
sudo gedit /etc/apt/sources.list
```

and then your root password. Then post what's in there in this thread. You shouldn't be getting architecture conflicts if you're just going to 'add/remove programs' so that makes me think you're accessing the wrong pool of applications. 

note that if there's a problem with that file, and someone can tell you what to replace it with, you'll have to do:

```
sudo gedit /etc/apt/sources.list
```

and then type your password to be able to save the file once you've edited it.

Also, you should tell us what version of ubuntu you're running and what type of processor (32bit, amd64, powerpc etc) you have so it can be determined what repositories you should have.

---

### Post by linux phreak on 2008-04-04
> **DScuglia said:**
> I am about ready to switch back to windows. I can get half of the applications to work right. When I try to add/remove for an application installation I keep getting a message that pops up "The list of applications is not available" refresh list. Every single time! When I refresh the list...it says the same thing. Then when I try to install ANY application, the menu pops up again. I get messages the says that the application requires additional hardware for i386 or not supported, or you cant do this, or that cant happen, or when I click on files...nothing....this is getting just....grrrrrr! I can't see how linux can have an advantage over windows other than open source......what am I doing wrong?

Hi.You must update your software sources to get the applications.Its system>administration>software sources.Check all the boxes.And in the ADD REMOVE window select "all available applications' from the box above.

---

### Post by Seti on 2008-04-04
Everybody calm down! Give the member a chance to give some more info!

Odds are, he's probably back to XP by now and is scouring the net for a good Registry Cleaner/Free Spyware Remover
Prove me wrong  DScuglia.

---

### Post by SunnyRabbiera on 2008-04-04
I am hoping he will be back too...

---

### Post by DScuglia on 2008-04-04
ok....here goes.....my ubuntu version is 7.10. I have tried to hit the refresh button.....then the add/rem downloads files 6 of 6 (pretty quick) then finishes. Then when I again attempt to install the item...the message box appears again, prompting me to refresh the list....I probably refreshed it about ten times before thinking that I must be an idiot, refreshing the list this many times. I was trying to install thunderbird. Then i tried other applications just to see what was going on..you guessed it....it did the same

---

### Post by DScuglia on 2008-04-04
I am a cop.....I don't give up that easy...but I do have a perpensity for anger

---

### Post by p_quarles on 2008-04-04
Moved to Testimonials & Experiences. If you want to request help, please do so without ranting.
> **DScuglia said:**
> I am a cop.....I don't give up that easy...but I do have a perpensity for anger
Anger has nothing to do with your Linux difficulties. There are other venues that can help with that.

---

### Post by DScuglia on 2008-04-04
someone tried to send me a message, but the pop up stopped it....try again pls

---

### Post by SunnyRabbiera on 2008-04-04
alrighty

first lets see on synaptic, there is a possibility that your mirrors are flaky right now.
but before we get into that is your connection stable, are you able to use the internet in Ubuntu?

---

### Post by kesman on 2008-04-04
Why don't you do this the terminal way so you could see if there's errors, and it would be much faster anyway...

---

### Post by SunnyRabbiera on 2008-04-04
> **kesman said:**
> Why don't you do this the terminal way so you could see if there's errors, and it would be much faster anyway...

I will take him into the terminal if it shows up to be needed, I just want to touch the bases first.

---

### Post by DScuglia on 2008-04-04
well.....i am parked right in front of a "staples" store. my wireless connection (the four bars..somehow strangely resembling the verizon bars) seems to be inconsistent

---

### Post by DScuglia on 2008-04-04
is there a better way to communicate......

---

### Post by SunnyRabbiera on 2008-04-04
> **DScuglia said:**
> well.....i am parked right in front of a "staples" store. my wireless connection (the four bars..somehow strangely resembling the verizon bars) seems to be inconsistent

ah, wireless can be a little flaky on linux but its not impossible to use.
do you have a more stable connection?
what do you use this current computer for?
you said you are a cop, do you use your computer for your job?

---

### Post by DScuglia on 2008-04-04
This is a laptop that I installed a new hard drive in. It is a sony viao. I am using the computer primarily for internet, ebay, on the go uses. I have winxp pro on my home desktop. I don't have access to a wired connection right now. I have another computer in my cruiser, but that one is for work.

---

### Post by DScuglia on 2008-04-04
actually...i don't have plans of returning to windows...but I have been messing around with this computer for hours, and I still have no freakin idea why things aren't  working

---

### Post by SunnyRabbiera on 2008-04-04
Okie

My next round of questions are going to be simplistic but important as I want some more information.

first, where are you located at?
do you live in the US or another country?
what is your primary ISP?
do you know the name of your wireless card?

some more bases I want to cover, they may help me in aiding you.

---

### Post by DScuglia on 2008-04-04
hello?

---

### Post by SunnyRabbiera on 2008-04-04
did you read my post?
this is a forum not a chatroom by the way, we respond when its possible.

---

### Post by ./Proxy on 2008-04-04
Do u have a internet conection?

---

### Post by SunnyRabbiera on 2008-04-04
He said he does, just a limited one on a wireless network.

---

### Post by DScuglia on 2008-04-04
by the way...I have icq with the same screen name

---

### Post by DScuglia on 2008-04-04
I am in Tennessee. My wireless card is Linksys wpc11 v.4. can't find my IP.

---

### Post by SunnyRabbiera on 2008-04-04
Hmm, well I dont use ICQ so sorry there.
If you need something more upfront I can offer to chat with you on other clients.
Do you use AIM?
YIM?
MSN?
Also I can provide you with e mail support too, I could give you my gmail account if needed

as for your ISP, not really important I just wanted to see if it might be an issue with the ISP...

---

### Post by DScuglia on 2008-04-04
yes......I have pigin (formerly giam) my aim is also dscuglia

---

### Post by SunnyRabbiera on 2008-04-04
I can do that...
give me a few secs and I will see you on AIM

---

### Post by DScuglia on 2008-04-04
i appolgize....its donscuglia

---

### Post by SunnyRabbiera on 2008-04-04
alrighty...
I will see you there.

---

### Post by SunnyRabbiera on 2008-04-04
Just in case you need to know my name it is ladymecha, I double posted as I know you are used to a more direct approach.

---

### Post by DScuglia on 2008-04-04
geez.....even my pigin is not working. for some reason it wont connect...it keeps timing out. i cant check my email because i cant install thunderbird

---

### Post by SunnyRabbiera on 2008-04-04
what is your mail provider?
do you use something special or can you access webmail?

---

### Post by DScuglia on 2008-04-04
ok, lady.....I am about ready to throw this laptop out the window....then back up over it....!

---

### Post by SunnyRabbiera on 2008-04-04
Look I need to go to bed here in a few minutes, hopefully I can lend a hand when i wake up...
I can help but I am no good if I am half asleep.

---

### Post by DScuglia on 2008-04-04
[email]donscuglia@gmail.com[/email]

---

### Post by DScuglia on 2008-04-04
i certainly appreciate ya

---

### Post by SunnyRabbiera on 2008-04-04
ah, well with gmail you dont need thunderbird.
you can use its web client in firefox, you should have no issues with using gmail.

---

### Post by DScuglia on 2008-04-04
i made the mistake of upgrading to ubuntu 8.0, then my wireless card wouldn't work....then I re-installed 7.10

---

### Post by SunnyRabbiera on 2008-04-04
Yeh hardy is still in development so right now its not a good idea to use it.
but the future is promising for it.

---

### Post by DScuglia on 2008-04-04
Thanks for your help......I am off today so I will be around later

---

### Post by scannerdarkly on 2008-04-04
seems to me that the wireless connection is just not strong enough....meaning you could be to far away from the router.  I think if you could or can get to a wired connection we can get this working for you.  

If you can get wired or get a stronger wireless connection then go to System>Administration>Software Sources.  Then in the first tab make sure that you have all the sources checked marked.  You don't really need the CDROM one.  Then if you want you click on the Third Party Software and check mark those in there.  Most likely you will want them checked.  Once they are checked then click close and you will get prompted to either refresh or reload the list.  If the connection is good it should fix the problem.

---

### Post by Wyrmboy on 2008-04-04
Could it be that all you need to do is 

Applications>Add/Remove

Go the Preferences Button and check all the boxes under Downloadable from the Internet

---

### Post by DScuglia on 2008-04-04
holy crap......it works...thank you linuxphreak!!!!!

---

### Post by morganpatrick on 2008-04-04
Sir, I'm going to have to ask you to step away from the laptop .

---

### Post by Bark on 2008-04-04
> **DScuglia said:**
> I am about ready to switch back to windows. I can get half of the applications to work right. When I try to add/remove for an application installation I keep getting a message that pops up "The list of applications is not available" refresh list. Every single time! When I refresh the list...it says the same thing. Then when I try to install ANY application, the menu pops up again. I get messages the says that the application requires additional hardware for i386 or not supported, or you cant do this, or that cant happen, or when I click on files...nothing....this is getting just....grrrrrr! I can't see how linux can have an advantage over windows other than open source......what am I doing wrong?
Probably nothing - Ubuntu software is full of bugs and you've just discovered this for yourself.

---

### Post by morganpatrick on 2008-04-05
You're full of bugs.

---

