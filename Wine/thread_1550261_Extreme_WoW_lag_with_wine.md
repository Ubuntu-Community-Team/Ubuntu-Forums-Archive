---
title: "Extreme WoW lag with wine"
date: 2010-08-10
forum: Wine
---

### Post by lilespo on 2010-08-10
I just made the switch from windows 7 to ubuntu and when i switched i moved my WoW onto an external harddrive and now i put it onto ubuntu without installing it with wine. Now  im pretty confident this works all i do is right click the launcher and click run with wine windows program loader and it starts up just fine i can login and everything the only problem is i get extremely low fps im talking like 1 fps. Does anybody know how i can solve this lag?
Thank You.

---

### Post by apostra on 2010-08-10
Hey there,

go to WTF folder and delete the wtf.conf file then try it again.

Did you copy paste your wow files into the .wine/..... ?

---

### Post by lilespo on 2010-08-10
> **apostra said:**
> Hey there,

go to WTF folder and delete the wtf.conf file then try it again.

Did you copy paste your wow files into the .wine/..... ?

I deleted the config.WTF and its still extremely laggy where is my .wine folder? im not sure if i have one.

---

### Post by apostra on 2010-08-10
Hey again,

Go to Application -> Wine -> Configure wine.  When the window pop up, have a look around to check it out, all the tabs etc, then close it.

Now go to Places-> Home -> press  Ctrl+H  to show the hidden files. If you are on terminal, the command is ls -a. Your wine directories nwo should be there.

You need to run once the configure wine, to create the directories. 

Also which version of wine do you have? ( wine --version on terminal to check it out )

Have fun

---

### Post by lilespo on 2010-08-10
> **apostra said:**
> Hey again,

Go to Application -> Wine -> Configure wine.  When the window pop up, have a look around to check it out, all the tabs etc, then close it.

Now go to Places-> Home -> press  Ctrl+H  to show the hidden files. If you are on terminal, the command is ls -a. Your wine directories nwo should be there.

You need to run once the configure wine, to create the directories. 

Also which version of wine do you have? ( wine --version on terminal to check it out )

Have fun
Ok my WoW is now in .wine Program files but i still have the lag when running it something wierd though is the blizzard entertainment and lich king cinematic run flawlessly its the login screen,character selection and game itself that are getting 1 fps
P.s im running wine-1.1.42

---

### Post by apostra on 2010-08-10
Sorry for the double  post mate.

You said you just made the switch to ubuntu from windows7. Did you activate your graphic's card drivers? I you  have nvidia then

go to System -> Administration > Hardware Drivers -> click activate.

Also try with no visual effect first. System-> Preferences-> Appearence-> Visual Effects to None.

Have fun

Edit: Cool you reply before i double post hehe

---

### Post by lilespo on 2010-08-10
> **apostra said:**
> Sorry for the double  post mate.

You said you just made the switch to ubuntu from windows7. Did you activate your graphic's card drivers? I you  have nvidia then

go to System -> Administration > Hardware Drivers -> click activate.

Also try with no visual effect first. System-> Preferences-> Appearence-> Visual Effects to None.

Have fun

Edit: Cool you reply before i double post hehe
When i  click hardware drivers it just says downloading and updating package indexes. I also tried to run it with no effects and it still had the lag :( sorry if im a little nooby with this stuff

---

### Post by apostra on 2010-08-10
Hey there again,

so after downloading and updating what happens, is it marked as activated? I think the problem is with your graphic's drivers. If its activated then do a restart before you try it again.

---

### Post by lilespo on 2010-08-10
> **apostra said:**
> Hey there again,

so after downloading and updating what happens, is it marked as activated? I think the problem is with your graphic's drivers. If its activated then do a restart before you try it again.
I tried restarting my computer and running hardware drivers again and it said the same  thing. So i basically cant start up hardware drivers because it just says updating and downloading package indexes theres no way to activate it from hardware drivers because it doesnt open correctly it just gives me that message.
Is there another way i can activate it from terminal or something else?

---

### Post by apostra on 2010-08-10
Hey there,


Try to install it through Synaptic Package Manager, search for nvidia, maybe would work.

Also copy paste the wow folder into the .wine/drive_c/Programs File/   directory. Open configure wine and choose add program then add wow. 


Unfortunatelly I cant help more. Your problem seems to me is your drivers. Personally had really bad time with installing drivers without hardware drivers. i didnt knwo how to fix it (still noobie) and i end up formating the pc all over. So i'm not feel that confident to  advice you.

I would say you to go to related sub-forum and seek advice there.

Your problem is the drivers, post details of your pc, your graphic card, the issue with the Hardware Drivers etc and wait for responses. Think and examine the proposed ways to solve this. Then give a try to wow again.

Good Luck mate.

P.S dont do google search and do what is been told to others, did this and had another bad time :~))) curiosity killed the cat :~P Do what is suggested to you through forums, for you and your pc only, not others pc.

---

### Post by jakubez on 2012-10-07
Hi
I got same problem
i turned all effects off and choosed least resolutions and it stoped me to lag so hard but still lagging much more than on windows and do you have black ground under Npc and players? if u got and solved that problem please tell me how
thans :-)

---

### Post by overdrank on 2012-10-07
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

