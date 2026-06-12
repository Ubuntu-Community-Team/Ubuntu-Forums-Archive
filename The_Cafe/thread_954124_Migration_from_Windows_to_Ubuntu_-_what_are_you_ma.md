---
title: "Migration from Windows to Ubuntu - what are you major problems ?"
date: 2008-10-20
forum: The Cafe
---

### Post by bluelightav on 2008-10-20
Hi Everybody,

I am involved in a migration project in the south of India. The aim is to provide a hight quality office computing environment based on as much open source software as possible. Sounds good? But there are problems and some of them are real blockers. If you do similar things what are the blockers for you?

So far for me 2 things make life difficult:

Tally is India's accounting software no 1. There is no discussion about whether this is needed to shifting to open source here. There 100 000 of well trained bookkeepers who can just be hired to do the job. Tally LTD didn't show much interest in providing a solution to use their software and the Indian government has only started recently to use Open Source software. A pressure from the government or that the government would use Linux and demands Tally on Linux would help here. Or a proper porting via wine.

Skype must work on Ubuntu. If one works in migrating in office environments it is not a question whether one likes Skype or not or whether it is "evil". It is a simple question that not having Skpe keeps people from migrating. There are way to many microphone issues on Ubuntu.

---

### Post by Bölvaður on 2008-10-20
> **bluelightav said:**
> There are way to many microphone issues on Ubuntu.

Please elaborate on microphone issues. I have had problems with microphones but of same quantity on windows when I used that. I have used teamspeak, ventrilio and skype for 2-3 years every day almost, on little more than 10 computers with little more than 20 mics.
Analog microphones seem fine overall, but usb seem to be big problem no matter what os you are running, in my past experience, but still it is always fixable. (I remember reinstalling windows xp from scratch to get usb headset working like it should... bad times:()



*added*
Oh the biggest problem for migration are twofold for most people, one isn't a RL problem but here is the other one:
**Unstandardized propitiatory filetypes**. File sharing between people that are unable to open standard documents is a fading problem, but it needs to be foreseen and tackled before anyone receiving files from your company staff cant open your files, or via-versa. (That is one of the reasons MS Word 2007 was forbidden in UK government organizations)

---

### Post by LaRoza on 2008-10-20
> **bluelightav said:**
> 
Tally is India's accounting software no 1. There is no discussion about whether this is needed to shifting to open source here. There 100 000 of well trained bookkeepers who can just be hired to do the job. Tally LTD didn't show much interest in providing a solution to use their software and the Indian government has only started recently to use Open Source software. A pressure from the government or that the government would use Linux and demands Tally on Linux would help here. Or a proper porting via wine.

I see that some important parts of India use Linux: [http://en.wikipedia.org/wiki/Ooo#Market_share](http://en.wikipedia.org/wiki/Ooo#Market_share) so you might want to check out what they do. 

It seems like it doesn't work well in Wine. [http://appdb.winehq.org/objectManager.php?sClass=application&iId=328](http://appdb.winehq.org/objectManager.php?sClass=application&iId=328)

It may be the only solution to use Windows for Tally, or to use Windows in a VM.

> 
Skype must work on Ubuntu. If one works in migrating in office environments it is not a question whether one likes Skype or not or whether it is "evil". It is a simple question that not having Skpe keeps people from migrating. There are way to many microphone issues on Ubuntu.
You have to pick supported hardware.

For microphone issues (non USB), it is a sound card issue: [https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards)

---

### Post by myusername on 2008-10-21
no ipod touch compatibility (with album artwork)

---

### Post by bluelightav on 2008-10-23
One more major problem is the handling of multiple languages/keyboards. In international communities and working teams people often speak/write several languages. This is not working well on Ubuntu/Gnome. I have lots of problems with settings being applied after the next reboot. This problems are known, bugs reproted and I really hope this is addressed soon.
It is embarrassing to tell people how good Ubuntu is and than this type of difficulties.:confused:

---

### Post by zmjjmz on 2008-10-23
> **myusername said:**
> no ipod touch compatibility (with album artwork)

Check out PwnPlayer. It will be for Jailbroken iPods, have filesystem browsing, and have a coverflow.

---

### Post by Bölvaður on 2008-10-23
Kubuntu has great keyboard layout switcher. Just one button away from having different language layout for your keyboard.

I think you need to make a clear list and try to find out how to tackle each one. Everything is possible in linux, so if you really want to do something, you have nothing stopping you.
Next thing I would want to see is you stop whining, or at least rephrase your questions to be direct and obviously a question and not a rant or whining :)


On other notes, two men go into a pub, well.. the third one was missing. So the two of them waited for the third one to be able to continue with the sketch. Linus comes in and asks the bartender to give him a beer. So the two blokes ask Linus to fill in for the third one, because he's late. Linus was well up for it, but under the conditions of no MS jokes.
The two blokes said "sorry then, but the pun is about Windows crashing". So they continue to wait for the third guy.
One of the blokes said to the other one "Perhaps we should have lied to Linus, Steve B. isnt comming.".
"Well perhaps" said the other guy "we are the ones that are late. Perhaps we missed the punch"
So they asked the bartender to turn on the tv and saw that SB's airplain had crashed in the antartica.
"oh sh... call for Linus, I think...." well you can fill in your own joke here.. perhaps SB crahsed.. or froze...

---

### Post by bluelightav on 2008-10-23
> **Bölvaður said:**
> Kubuntu has great keyboard layout switcher. Just one button away from having different language layout for your keyboard.


Next thing I would want to see is you stop whining, or at least rephrase your questions to be direct and obviously a question and not a rant or whining :)



Hi Bölvaður,
it is not about whining. I am involved in Open Source since a couple of years now and it is not about my PC at home. It is about hundreds of users in my community. It is a fact that installing Skype on Windows takes as much as as minute and works most of the time out of the box. So it is with Tally and keyboard switching. That there are drawbacks with Windows is another thing:)
I don't know whether you have worked on a larger scale with Linux. Migration on the technical level is one thing, migrating the "physiochemical" state of a drugged Windows user is another one. My experience in Open Source is that human resources are scarce for lot of NGOs (such as ours in Auroville) and if I get service calls in because the microphone on Skype doesn't work or the keyboard doesn't switch it drains expert resources from the more important stuff like contributing to Open Source projects or training user is the use of Open Source applications. I am used working in India that lots of things don't work out of the box. Still I feel that such stuff like keyboard switching or Skype should be fixed as it indeed does make people leave Ubuntu (I have seen it) and migration much more difficult. You can argue that if people leave because of this it is their own fault but as far as I am concerned Ubuntu wants exactly to break this and provide a desktop Linux which works for the most common user.

Does the KDE keyboard swichter work under Gnome?

---

### Post by Lord Xeb on 2008-10-23
The biggest problem I had was just the change of how things were laid out. I was so much different from what I was use to. I have never really had a problem with Ubuntu. I took me a week to figure out things and I was set. I can do everything that I normally do with OO that I could do with MSO. The second biggest was just learning how do things over again. After getting acquainted, I fell in love :D

---

### Post by d_skillz on 2008-10-23
Main difficulties will be you have to realise that you will do things a little differently than you are used to. Quickbooks, Adobe Photoshop, Adobe Illustrator, 3D studio Max, Quark. These are just a few business tools that have no linux equivalent, I would suggest you try to find a suitable open source quivalent to any software you currently use on your windows system.

---

### Post by heroidi on 2008-10-24
the reason's are adobe photoshop, corel draw and counter strike those are the reasons why i havn't deleted windows yet:mad:

---

