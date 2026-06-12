---
title: "How I got my Ubuntu installation working (I had network problems)"
date: 2007-12-20
forum: Testimonials &amp; Experiences
---

### Post by Gnigma on 2007-12-20
After about 6 months of fooling with it, I finally have Ubuntu installed in a machine I can actually use. No offense, Ubuntu gurus, but you were no help whatsoever. The problem with most Linux groups is this elitist attitude that you know more about computing than the average Windows user. You do. But I'd bet that more than 90% of all computer users could care less how to compile a program, and don't particularly care how it works, as long as it does. Whenever that kind of user asks about a problem, the answer might as well be in Cebuanese. Like me, they usually give up and go back to Windows, because they don't have time or inclination to learn Linux when Windows will do the same thing for less hassle. They'll usually pay more to save their own (valuable) time. This is for Windows (appliance) operators. I'm sure the Ubuntu wizards can make improvements to this procedure, but the target population for this may not understand them. Here Goes:

1) Get Ubuntu on CD. Get the latest stable version available. Have a working internet connection; broadband is a necessity. Make sure your wireless card and ethernet adapter is compatible with Ubuntu-- check the lists. Also, set your gateway/router to open security, then connect via ethernet (hardwire) to the machine you're installing on.
2) Boot from the CD and run the install--- only set up one user until it is up and running. Sometime in the last third of the install, you should be able to see the modem traffic leds flashing. If this does not happen, your internet connection isn't working. Stop here and change the settings on the gateway or modem for less security until this connection works. Eventually the install will complete. Reboot without the CD.
3) Log on. DO NOT TOUCH THE NETWORKING SETTINGS! Do not try to use the browser, don't look at the rest of the network--- the install is NOT complete! Instead, mouse the icons at the top right of the screen-- one of them will say "updates," and there will probably be one that says "restricted drivers." Click on the "updates."  Run the install program. This is where you need broadband-- mine had 148 updates that took 6 hours to download, and another hour plus to install. When it's done, rerun the "updates" installer for anything that failed. They won't take effect until you reboot, but don't reboot yet.
4) Do the same thing for the "restricted " items. I had to run this twice: once for the video card driver and once for the wireless card firmware. NOW reboot.
5) After you log on, check the web browser it'll probably connect right up via the ethernet hardline. if not, go to the gurus and good luck understanding them. If it works, exit the browser. Now go to System/administration/network. It'll ask you for your password. Enter the same as your login password. Highlight the wireless connection, then click properties. Disable roaming mode, unless it's a laptop, select DHCP on the little drop down menu, and enter your ESSID if it's not broadcast.
6) Exit the program and restart. Unplug the ethernet cable while it's shutting down. When you log back on, the wireless should work for your browser. You're done. Use it like it was yours.

I'm familiar with Linux, but certainly not an expert. This is just the way I've found that works (after months of trial and error.) I'm finally able to get away from Microsoft.  YeeHah!:guitar:

---

### Post by Presto123 on 2007-12-20
I've looked through your posts and almost all three bash Linux and the users who you wanted to have help you.

Simply, if you ask for simplified version of things, they would help. Believe me, I was entirely new 2 months ago. It's December, and with the help of the Linux "gurus" I got it all done and am now able to assist others.

Also, it takes time, there are so many new people coming into the Linux environment here and if you watched the "Absolute Beginners Forum" it is constantly changing with people asking for help. The new people ratio versus those with enough knowledge gets a bit off-kilter to say the least.

---

### Post by LaRoza on 2007-12-20
> **Gnigma said:**
> After about 6 months of fooling with it, I finally have Ubuntu installed in a machine I can actually use. No offense, Ubuntu gurus, but you were no help whatsoever. The problem with most Linux groups is this elitist attitude that you know more about computing than the average Windows user. You do. But I'd bet that more than 90% of all computer users could care less how to compile a program, and don't particularly care how it works, as long as it does. Whenever that kind of user asks about a problem, the answer might as well be in Cebuanese. Like me, they usually give up and go back to Windows, because they don't have time or inclination to learn Linux when Windows will do the same thing for less hassle. They'll usually pay more to save their own (valuable) time. This is for Windows (appliance) operators. I'm sure the Ubuntu wizards can make improvements to this procedure, but the target population for this may not understand them. Here Goes:


Interestingly, I was able to install Ubuntu with no help, just by following the prompts. Installing Ubuntu is extremely easy, compared to XP or Vista, but since the average user doesn't have to install their OS, it can be daunting.

"No offense, <offense>" is just a bigger insult. If you had trouble, I am sure people would have tried to help, and if you didn't understand, and explicitly stated what you didn't understand, I am sure their posts would have cleared things up.

In my experience, they usually try harder until they get it. 

The [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing) guide is very easy to follow. In fact, I recommend [http://psychocats.net](http://psychocats.net) to anyone with an Ubuntu question and the Ubuntu wiki.

Looking at your posts, you have formed a very quick and untrue opinion of Linux users. I and others are more than willing to walk others through sometimes complicated procedures (search for all my posts).

---

### Post by natehall on 2007-12-20
I followed an even easier path: I bought my computer preinstalled!  I've been trying on and off to get Linux for years. I had one computer I utterly messed up the Windows system and rather than buy some Windows product I tried to load various  Linux flavors. Never could get it working. My experiance with the people here has been great! I had to hunt all over the internet to get Windows help when I needed it but here in one spot I've got the cream of computer geekdom just waiting to pounce upon any issue that they believe they can help with.

---

### Post by natehall on 2007-12-20
By the way, thanks to the people here I've got Ubuntu running on that old clunker now.

---

### Post by erfahren on 2007-12-20
we're not all "gurus" here, Gnigma. If a post goes unanswered for a few hours it doesn't mean that no-one "wants" to help, it just means that no one who saw the post had an answer. 

Sometimes if I see a question that I can't immediately answer I'll spend a little time helping the poster research it, - I'm sure I'm not alone there. (Sometimes I spent my time finding the information and never got any kind of response to whether it worked or not - so it goes both ways.)

There's an "unanswered posts" team here to try to catch the ones that are passed over. I think we all do the best we can.

If it's any consolation, I didn't think the answer you got to your other post(s) was very clear either, and the poster was obviuosly no "guru".

You posted like you were wanting/expecting something equivalent to "customer support", it doesn't (usually) work that way. It occasionally takes time to research things.

There are ways to get paid-for support. Maybe if you want to use Linux but don't have the time to research that might be a option for you to consider.

---

### Post by JillSwift on 2007-12-20
I'd like to say that in the 3-4 months I've been using Ubuntu and reading/posting to this forum I've not seen but the tiniest smattering of "elitist attitude". And that tends to get smacked down by others.

Ubuntu is by leaps and bounds the easiest distro of Linux I've ever tried. And this forum is full of some of the most helpful folks I've ever met. =^_^=

---

### Post by hyper_ch on 2007-12-20
> **Gnigma said:**
> No offense,
Yeah right, you mean to offend by that...

> **Gnigma said:**
> Ubuntu gurus, but you were no help whatsoever.
I have serious doubts on that... ever looked into the forums besides when you have a problem?

> **Gnigma said:**
> The problem with most Linux groups is this elitist attitude that you know more about computing than the average Windows user.
Well, with what linux groups do you have those problems? Does it apply to this forum?

> **Gnigma said:**
> But I'd bet that more than 90% of all computer users could care less how to compile a program, and don't particularly care how it works, as long as it does.
90% of the Ubuntu users are the same, I daresay.


> **Gnigma said:**
> Whenever that kind of user asks about a problem, the answer might as well be in Cebuanese.
Then why don't you say what you don't understand? The only stupid question is the one unasked... and you know, maybe a little bit of effort from your side might help.


> **Gnigma said:**
> Like me, they usually give up and go back to Windows, because they don't have time or inclination to learn Linux when Windows will do the same thing for less hassle.
Linux is about freedom. Nobody is forcing you to use it but you have the choice... Do you know how to fly plane? Do you know how to navigate a submarine? New things take time to learn, that's how life is. If you are unwilling to learn, you should not try new things then...

Oh, and I forgot, 99% of the Windows user never had to install it... so how can you say Ubuntu is more complicated for installation?

---

### Post by lasthand on 2007-12-20
Actually hyper_ch, back in the day i remember trying to install Windows 98. Man that was a nightmare. Ubuntu was easy to install into my virtual box.

---

### Post by nowshining on 2007-12-20
> **Gnigma said:**
> After about 6 months of fooling with it, I finally have Ubuntu installed in a machine I can actually use. No offense, Ubuntu gurus, but you were no help whatsoever. The problem with most Linux groups is this elitist attitude that you know more about computing than the average Windows user. You do. But I'd bet that more than 90% of all computer users could care less how to compile a program, and don't particularly care how it works, as long as it does. Whenever that kind of user asks about a problem, the answer might as well be in Cebuanese. Like me, they usually give up and go back to Windows, because they don't have time or inclination to learn Linux when Windows will do the same thing for less hassle. They'll usually pay more to save their own (valuable) time. This is for Windows (appliance) operators. I'm sure the Ubuntu wizards can make improvements to this procedure, but the target population for this may not understand them. Here Goes:

1) Get Ubuntu on CD. Get the latest stable version available. Have a working internet connection; broadband is a necessity. Make sure your wireless card and ethernet adapter is compatible with Ubuntu-- check the lists. Also, set your gateway/router to open security, then connect via ethernet (hardwire) to the machine you're installing on.
2) Boot from the CD and run the install--- only set up one user until it is up and running. Sometime in the last third of the install, you should be able to see the modem traffic leds flashing. If this does not happen, your internet connection isn't working. Stop here and change the settings on the gateway or modem for less security until this connection works. Eventually the install will complete. Reboot without the CD.
3) Log on. DO NOT TOUCH THE NETWORKING SETTINGS! Do not try to use the browser, don't look at the rest of the network--- the install is NOT complete! Instead, mouse the icons at the top right of the screen-- one of them will say "updates," and there will probably be one that says "restricted drivers." Click on the "updates."  Run the install program. This is where you need broadband-- mine had 148 updates that took 6 hours to download, and another hour plus to install. When it's done, rerun the "updates" installer for anything that failed. They won't take effect until you reboot, but don't reboot yet.
4) Do the same thing for the "restricted " items. I had to run this twice: once for the video card driver and once for the wireless card firmware. NOW reboot.
5) After you log on, check the web browser it'll probably connect right up via the ethernet hardline. if not, go to the gurus and good luck understanding them. If it works, exit the browser. Now go to System/administration/network. It'll ask you for your password. Enter the same as your login password. Highlight the wireless connection, then click properties. Disable roaming mode, unless it's a laptop, select DHCP on the little drop down menu, and enter your ESSID if it's not broadcast.
6) Exit the program and restart. Unplug the ethernet cable while it's shutting down. When you log back on, the wireless should work for your browser. You're done. Use it like it was yours.

I'm familiar with Linux, but certainly not an expert. This is just the way I've found that works (after months of trial and error.) I'm finally able to get away from Microsoft.  YeeHah!:guitar:
i posted a similiar post awhile back this year about how bad the people were, u should go find it, however after some time i realized that some can be, some are there to help also and i was the one being a bit moronic myself..

I also got soo upset at the forums i had to leave a month or so ago, left, visited other sites on linux/ubuntu, other linux distro forums and came back. If u feel upset leave for a bit and come back in a week or month or two and try again..

also if u truly do and still think that people don't answer posts and all are elite, come back here urself and start answering posts urself and helping others, as even tho u feel that u got treated bad, stop the circle then and be nice and help others and give what u did NOT get. :)

i hope i explained that well..

---

### Post by quinnten83 on 2007-12-20
Well 
everyting has a learning curve.
speaking as someone who installs windows on a regular basis, the ubuntu installation is much better and more fun. And if you really know what you are doing a reinstallation is much safer for preserving your data  than windows.
anyhow justmy 2ct.

---

### Post by Gnigma on 2007-12-20
I am a simple hillbilly. My primative mind often has difficulty grasping the subtle nuances of your advanced civilization. Having said that, I feel like I do have to point out that I don't do passive aggression. If i don't like you, or you offend me, trust me, there will be no doubt in your mind. All I meant was that when someone  has decided to try Ubuntu, or any other distro, for that matter, there are things that the install does not tell you, that the forums don't tell you, that apparently you're just supposed to know. 
   Well, most people  don't just know. And yes, the people who do know are more than willing to help. It all comes down to time. Time is the one thing you can never get back in life-- once it's gone, it's gone, whether you used it or pissed it away. For what it's worth, I used Unix for about ten years in a previous job, and there's enough crossover that I understand the basics of Linux operation. I have installed Slackware and Gentoo on barebones systems. But, a higher-level install like Ubuntu should either do it for you or at least have enough information provided that you don't inadvertantly screw it up during install.
   I noticed that there are very few comments about the actual procedure. Mostly, there are defensive diatribes on how I may have offended some of the people here. Grow up. Get over it. I was being honest. It took me a lot of trial and error, and the help I got, while well intended, did not help. And I do intend to help other newbies with my experience (I wouldn't presume to call it expertice) when I can. So does anybody have any commentary about the actual install procedure? Can't we all just get along?:confused:

---

### Post by Yoke &amp; Chung on 2007-12-20
> **Gnigma said:**
> 


2) Boot from the CD and run the install--- only set up one user until it is up and running. Sometime in the last third of the install, you should be able to see the modem traffic leds flashing. If this does not happen, your internet connection isn't working. Stop here and change the settings on the gateway or modem for less security until this connection works. Eventually the install will complete. Reboot without the CD.
3) Log on. DO NOT TOUCH THE NETWORKING SETTINGS! Do not try to use the browser, don't look at the rest of the network--- the install is NOT complete! Instead, mouse the icons at the top right of the screen-- one of them will say "updates," and there will probably be one that says "restricted drivers." Click on the "updates."  Run the install program. This is where you need broadband-- mine had 148 updates that took 6 hours to download, and another hour plus to install. When it's done, rerun the "updates" installer for anything that failed. They won't take effect until you reboot, but don't reboot yet.


Thanks for sharing your experience. I am pretty new myself too, and have screwed up so many Ubuntu/ Xubuntu installations that I am pretty good at installations, lol.

Just want to share a few points:

1.) Play around with the LiveCD first before installation. The LiveCD is slow, but it is a good test on the hardware. You can use firefox to test your internet connection and so on. If you find any hardware not working, chances are it will not work after the installation (except display problem). For display case, it is usually due to driver and you can correct this after the installation.

2.) I usually have my ethernet unplugged during installation as I want a fast installation and test the new installation first. You can always update the OS later.

3.) If it is your first time installing Ubuntu, try not to install on a PC with built-in graphics adapter that has no dedicated graphics RAM using the LiveCD. It can be a nightmare.

---

### Post by aysiu on 2007-12-20
This post purports to be a guide for new users but is really relating personal experiences and opinions, so I've moved it to the appropriate subforum.

---

### Post by philinux on 2007-12-20
> **Gnigma said:**
> I am a simple hillbilly. My primative mind often has difficulty grasping the subtle nuances of your advanced civilization. 

Your grasp of english isn't hillbilly. Maybe slow down and read some.

---

### Post by rustybronco on 2007-12-20
> **Gnigma said:**
>  there are things that the install does not tell you, that the forums don't tell you, that apparently you're just supposed to know.or take the time to learn it and help others with the new found knowledge. we are given a mind for a reason, without use we have no need for it. 
>  Well, most people  don't just know. And yes, the people who do know are more than willing to help. It all comes down to time. Time is the one thing you can never get back in life-- once it's gone, it's gone, whether you used it or pissed it away. Time is not wasted when used to help others...
> But, a higher-level install like Ubuntu should either do it for you or at least have enough information provided that you don't inadvertantly screw it up during install. again, what is the problem with learning? we learn to walk ,yet still fall down in the process.
 I have learned much in my years by trial and error some teaching and the passion for learning with no regret on how my time was spent.
life on this earth is nothing except to help others, it is after we are done here that has the greatest meaning.

and thanks for the guide, it brought thought into my life again.

---

### Post by aysiu on 2007-12-20
> **Gnigma said:**
> No offense, Ubuntu gurus, but you were no help whatsoever. How often did you ask for help in those six months? > The problem with most Linux groups is this elitist attitude that you know more about computing than the average Windows user. You do. Please provide some evidence. >  But I'd bet that more than 90% of all computer users could care less how to compile a program, and don't particularly care how it works, as long as it does. I don't care about compiling programs or how the programs work, and Ubuntu has worked just fine for me these past two and a half years. > Whenever that kind of user asks about a problem, the answer might as well be in Cebuanese. If someone tells you something you don't understand, how about asking for clarification or an explanation? > Like me, they usually give up and go back to Windows, because they don't have time or inclination to learn Linux when Windows will do the same thing for less hassle. I know many Windows users who have hassles. I had a hassle in Windows just yesterday. I've seen people have hassles with every major operating system. My wife has hassles with supposedly "just works" Mac OS X. >  They'll usually pay more to save their own (valuable) time. I doubt it. I'm far more efficient on Ubuntu than most of the people I know are on Windows. My in-laws had their Windows computer get infested with spyware and it was down to a slow crawl. To open a program took a full two minutes. Were they saving time? No. > This is for Windows (appliance) operators. Windows, Mac, and Ubuntu are not appliances. If you can install and remove applications, add and remove users, etc., your computer is not an applicance. >  I'm sure the Ubuntu wizards can make improvements to this procedure They already do. Believe me. I've been here since Ubuntu 5.04. They've made *many* improvements on Ubuntu. > but the target population for this may not understand them. Here Goes:

1) Get Ubuntu on CD. Get the latest stable version available. Have a working internet connection; broadband is a necessity. Make sure your wireless card and ethernet adapter is compatible with Ubuntu-- check the lists. Also, set your gateway/router to open security, then connect via ethernet (hardwire) to the machine you're installing on.
2) Boot from the CD and run the install--- only set up one user until it is up and running. Sometime in the last third of the install, you should be able to see the modem traffic leds flashing. If this does not happen, your internet connection isn't working. Stop here and change the settings on the gateway or modem for less security until this connection works. Eventually the install will complete. Reboot without the CD.
3) Log on. DO NOT TOUCH THE NETWORKING SETTINGS! Do not try to use the browser, don't look at the rest of the network--- the install is NOT complete! Instead, mouse the icons at the top right of the screen-- one of them will say "updates," and there will probably be one that says "restricted drivers." Click on the "updates."  Run the install program. This is where you need broadband-- mine had 148 updates that took 6 hours to download, and another hour plus to install. When it's done, rerun the "updates" installer for anything that failed. They won't take effect until you reboot, but don't reboot yet.
4) Do the same thing for the "restricted " items. I had to run this twice: once for the video card driver and once for the wireless card firmware. NOW reboot.
5) After you log on, check the web browser it'll probably connect right up via the ethernet hardline. if not, go to the gurus and good luck understanding them. If it works, exit the browser. Now go to System/administration/network. It'll ask you for your password. Enter the same as your login password. Highlight the wireless connection, then click properties. Disable roaming mode, unless it's a laptop, select DHCP on the little drop down menu, and enter your ESSID if it's not broadcast.
6) Exit the program and restart. Unplug the ethernet cable while it's shutting down. When you log back on, the wireless should work for your browser. You're done. Use it like it was yours. No offense, but your guide isn't very good. It's tailored to your own experience and doesn't address common problems. There are no screenshots or even spaces between paragraphs. I don't see how you can say the Ubuntu community is no help and then present this useless-to-new-users guide.

> I'm familiar with Linux, but certainly not an expert. This is just the way I've found that works (after months of trial and error.) Exactly. This is why your guide isn't any good. That's the way you've found it works... on your one computer. That is not the typical scenario by a longshot. Believe me. I've seen literally tens of thousands of support threads over the years.

---

### Post by wolfen69 on 2007-12-20
one more thing. if you can install slackware or gentoo, why would you have a problem installing ubuntu? <scratches head>

like aysiu said, your "guide" isnt very good, and would probably lead to more confusion. but at least you're trying. good luck, and have fun.

---

### Post by Gnigma on 2007-12-20
Yoke & Chung, thanks for the feedback. 

Oddly enough, most of the responses to this thread seem to me to be rather argumentative. I particularly like the ones that analyze my comments singly, out of context, and the requests that I define my terms and give examples--- basic Socratic method for debate when you don't have a real argument, or when your oponent has a better argument--- get him involved in defensive explanations and proofs that are by their nature endless. You won't win the debate, but you might get a draw. 

I think most of you mean well, and you obviously know more about this system than I. Understand, though, that as I reread this thread, most of the posts seem, from my perspective, to show the condescending attitude that I originally pointed out. 

I reiterate: a computer is a box that I use to perform or simplify some tasks. As long as it does what I want, I don't care anymore to know HOW it works than I care to know HOW the refridgerator works, or the telephone. My whole point was (originally) that there are some key points in the installation that newbies need to know. I adamantly refuse to accept the traditional "install the system and spend weeks repairing problems" method. 

It has not gotten by me that this thread was moved due to an imaginary arguement over my editorial comments, rather than any invalidity of my instructions. I could easily make a case that you apparently don't want beginners to be able to do this without your help--- it was, after all, moved away from the target audience and picked apart on points having little to do with the procedure. Telling me I need to learn more is quite condescending. It borders on what used to be called "enabling," a key factor in co-dependence. Basically, you're creating a need for your own input.

Sorry, I couldn't resist. Gee, folks, lighten up! I'm just trying to help others like me who are so pressed for time that they can't take a course in how the OS in their computer works. I'm not saying that you don't help new users; I'm saying you don't help me. I work full time and I'm in school full time. My schedule is a seven day a week gig. Right now I'm on break from school, so I had time to contribute. Take it for what it is, but don't jump all over me for having opinions.

---

### Post by nowshining on 2007-12-20
this is in testimonials and experiences because well, over half of it has to do with ur experience with ubuntu and whethter that is good or bad. :) I'm not saying a lot of time I myself have had the same feelings, and I have, the best and like I said before to do is to treat others better than u've gotten treated and ignore or try to the bad and elitest stuff that gets dished out (i do myself) and yes I do understand. U could if u want to create a free website off [www.freewebs.com](www.freewebs.com) and well put ur guide, tips and howtwos there and then put it in ur sig.

:)

---

### Post by rustybronco on 2007-12-21
Look inside before looking outward.

---

### Post by dark_harmonics on 2007-12-21
My fear as an Ubuntu supporter and proponent is that others will see this thread and think its a real guide. I thought it was (even though i can install on my own) and decided to check it out.

**I think this thread's title needs changed or it needs deleted entirely.** It can only serve to confuse new users and pop up on desperate searches of the forums by people who need REAL help.

---

### Post by aysiu on 2007-12-21
> **dark_harmonics said:**
> My fear as an Ubuntu supporter and proponent is that others will see this thread and think its a real guide. I thought it was (even though i can install on my own) and decided to check it out.

**I think this thread's title needs changed or it needs deleted entirely.** It can only serve to confuse new users and pop up on desperate searches of the forums by people who need REAL help.
I've retitled the thread to more accurately reflect the contents.

---

### Post by dark_harmonics on 2007-12-21
> **aysiu said:**
> I've retitled the thread to more accurately reflect the contents.

Rock on!:guitar:

---

### Post by Gnigma on 2007-12-22
Actually, most of my original post IS about the installation procedure. Almost all of the RESPONSES are antagonistically directed towards my editorializing. Let me ask , has anyone tried to install the OS in the way I describe? Believe me, I have tried to install Ubuntu from your instructions, and it doesn't work, at least not without some major tweaking. All I tried to do was show that there is a basically trouble free way to do this without the necessity of major modification just to get it to do basic stuff like the internet. Also, you people who claim Windows is so hard to install, Do you really think it's easier for the average computer user to type in endless command lines or to run an install wizard in Windows? My Ubuntu system finally works; I'm happy with it. I was just trying to demystify  and simplify the process for many who are frustrated by the convoluted maze of results that often bogs down an enthusiastic new user. It's like speaking Chinese-- If you already speak Chinese, it's a piece of cake; if you're learning, it can be extremely difficult. The other thing is most people don't care how the silly thing works, as long as it does. I used to work on digital encryption systems. I have no doubt that I could study and read and learn enough about ANY system to make it work--- I don't want to.

---

### Post by hyper_ch on 2007-12-22
You fail to see that it might just be you for whom it doesn't work. There's a reason the install is as it is. However there's almost an endless list of different components and setups... your guide is just specific to you but for the average user it does not apply.
Command line is simpler... it just works.... no need to guide through different interfaces and you can just copy'n'paste ;)

---

### Post by Gnigma on 2007-12-22
Are you folks even looking at your own forums? I keep getting replies that it's only me that has a problem with the installs. In the beginner forum, you are getting multiple cries for help EVERY MINUTE! It's NOT just me. What you fail to realize is that there are more people out there that simply won't ask for help-- if it doesn't work, they'll just go on to something else. Don't get me wrong, I admire you all for attempting to correct all these problems, but, as they say in Chinese Medicine, you are treating the branch when you should treat the root. Again, has anyone tried to do an install the way I outlined? I'm sorry if my way takes the esoteric feeling out of it for you, but for most people, that's what they want. Try this: ASK the next 40 people you help if they'd rather you help them get their system up, or if they'd rather it work without having to have help.

---

### Post by hyper_ch on 2007-12-22
Gnigma:
Well, people that have no problems don't come to the forums and ask for help ;)

So it's not really off the grid that in a "support" forum all people ahve some problems ;)

But those that ask for help about installation (which is not so much anyway - not even in the beginner's forum) is a very, very small percentage of the total users of Ubuntu which do not have any such problems.

---

### Post by nowshining on 2007-12-22
well, actually Gnigma if a lot of users just take the minute or two to just EXPLORE, open up some things, click here, and there, read the buttons, the info. on the guis, and so forth but most of all THINK they would have less problems. Also they could do a search engine search for keywords and read a bit of history on linux/unix and how it works, read some articles on it, old+new, etc.. Then the beginners forum would be nearly empty or so.

If ur wondering, yes, i was new on linux/unix and yes i did the above and so far that's what helped me achieve pretty much of what I know today and what incl, fixes, tips and howtwos that I give others, I don't put up what I have not tried out yet on my machine.

Again some users should know that linux/unix is not like windows, as u gotta and will still need to THINK and install things on ur own & fix things on ur own.

Those who used windows and tweaked it will be comfortable with linux/unix
Those who just sat around and didn't change/tweak things will have a harder time.

Exceptions do apply like always.. :)


Gnigma I truly suggest going to freewebs.com and creating a free account and inputting any guides/tips, etc.. u have there and linking to it in ur sig. That way it will get seen more often and of course update it with newer tips/fixes/guides, etc.. when u find a fix/tip/howtwo. :)

---

### Post by nowshining on 2007-12-22
by the way also

Those who use linux have grown up and are not windows babies no more. Windows is training wheels, linux/unix is big boy/girl stuff. Which brings one into being also a man/woman.

edit: in other words instead of mommy/daddy spoon feeding u and watching out for every boo boo u get, ur now on ur own and now u must fix and do things on ur own instead of having mommy/daddy do them for u..

---

### Post by erfahren on 2007-12-22
I'm not going to say that your installation tips wouldn't work Gnigma, but you make it all sound a little daunting, like if a person doesn't have a network connection when installing then all will be "for naught". From personal experience that definitely isn't the case. 

I mainly use Ubuntu on a notbook with only a wifi connection. To do it the way you described - connected with ethernet, no security, and using dhcp with my router (the latter seemed implied) would require a lot of work before even beginning the install.

According to your caveats I wouldn't be able to get a internet connection at all with my setup after installing, and yet.....

You touched the key point when you mentioned the "convoluted maze of results".  Those arise because of the magnitude of different computers and hardware configuarions that exist. When hardware manufacturers release their drivers they make them primarily for Windows, Linux is not their primary concern. That, coupled with the fact that Linux was developed the way it was and how far it has come, it's simply amazing that it works as well and as inclusively as it does.

It's true that the Linux community in general is trying to reach out to new users. However, I think it's still implied that Linux is still *Linux*, it does take time to learn and a person will most likely have to do some research eventually.  

That brings me back to the main issue here. You *obviously* feel resentful that you don't have the time to research and fix any problems that may/will arise, and are blaming the people here on the forums for not giving assistance. You posted here two times over six months ago. You didn't give us enough of a chance to help, worked it out on your own, and then post back here basically saying (in so many words): "your guides suck, *this* is how it it's done". People put a lot of their own (free) time and effort (and it does take some time and effort, believe me!) into making those guides and they work for most people. 

Also, you said that the guides you followed were incomplete (basically), and without giving any input on what is specifically wrong with the guides you referenced, you ask for input on yours. 

So with all that considered we feel like we're on the defensive here and so most of the responses are directed towards your editorializing because we're just trying to get that part worked out. Do you see where we're coming from?

All that said (if you've read this far), I for one am a little curious as to what the original problem was with Firefox not be able to connect to the internet for you. I realize that you most likely consider that issue fixed, but the answer may be beneficial to another user that comes along who might be experiencing the same problem (since we are, after all, a community of *users helping users*.

To keep the issues seperate I'm posting to [your original thread about the old issue](http://ubuntuforums.org/showthread.php?t=413524).  (I just have a couple of questions.) I

---

### Post by Gnigma on 2007-12-22
My original problem with connecting to the internet was never solved. I went back to Windows XP, and that's what is running on that machine now. My original post was intended to give Windows-familiar users a way to install the system with as few residual problems as I could manage, while making it possible for them to get up and running as fast and easily as possible. You can argue all you want about the precious command line, you can even assume that Linux is for computer grown-ups, but the fact remains that people have to crawl before they walk. If it isn't easy enough, you lose another potential convert. (I really don't understand all this devotion to command line interfacing; it's NOT the most common interface, it has been around since the 1960s, and most commercial processing has moved beyond that phase into GUI.) If you ask a programmer to do something in machine code nowadays, you'll probably get a blank stare-- even if it is the most efficient way to use the machine. I personally like what you all are doing here, but you guys are so far up the learning curve that I feel a lot of potential users just won't even try--- not everybody wants to use the command line. And by the way, all your sig warnings about using unknown commands are sending a message to many that you can really screw the system up if you enter the wrong thing--- that's one reason many will choose to use something else.

---

### Post by nowshining on 2007-12-23
Explore, ask urself, background search, explore, search, background search, reviews, articles, all before one moves and decides to install ubuntu fully or half-way before commiting..

:) i always thought linux myself u could only use broadband, until i took that last chance when XP became soo unstable and slow after 2-4m or so and so that's when i decided to plunge into ubuntu. I haven't  regretted it since..

If people explore a bit about linux/ and do the above in the first sentence before taking a plunge then well they wouldn't have soo much trouble...

If u do get stuck, find a friend/neighbot/compuer lab in a library or such and go to them/there, do some more research to the problem and come back and try em' out. :)

Most of all tho READ AND THINK.

I almost ditched ubuntu because of no dial-up but i found out how to get that up and running and it's quite easy with a GUI app. and now i got more knowledge, and also i've read about linux/unix more and done more search engine searches on my problems, even if is NOT the ubuntu distro or a tid bit here and there, and then I combine them all and THINK and put the puzzle pieces together to fix my problem...

edit: if ur wondering I myself am no EXPERT per se, :P i'm still , well just above a newbie - still learning..

---

### Post by erfahren on 2007-12-23
*most* things in Linux can be done through the GUI now. *Some* software does need to be used through the the command line still but that's because the developer (or anyone else) never wrote the code to incorporate with a GUI ( since much software for Linux is written by a designer to accomplish what he/she needs to and then shares it (see the [Linux is not Windows](http://linux.oneandoneis2.org/LNW.htm) article.)

Also, using the command line to start programs that are problematic can give an output that can give a clue as to what's wrong (I personally don't know much about that, but it can be beneficial to others providing that level of support.)

The other thing is that it's faster and easier for people giving instructions and/or providing support to have someone cut & paste some commands into the terminal than to type out the steps going through the GUI. 

(It also can be easier for the one receiving the support as well since it can be a difference between simply providing the information asked for and trying to go through all the steps correctly to access the information.) 

[SIZE="3"]Case in point...[/SIZE]
(try this yourself to see the difference if you want.)

scenario: someone wants to see your xorg.conf

GUI method:
Click on "Places" and select "Home" . In the file browser's side pane click on "File System" and open the "etc" directory. Find the directory named "X11" in there and open it. Locate the file "xorg.conf" and right-click and open in the text-editor. Copy its contents and paste here.

-----------------------

Terminal (or "command line") method:
Cick on Applications > Accessories > Terminal. Copy & paste the code below and then copy & paste its output here:
```

cat /etc/X11/xorg.conf

```
----------------------------------

In the first method, in anticipation of any confusion that the instructions may cause, I felt like I had to give them in as much detail as I could . It was time consuming. The second method I didn't need to be concerned with that so much. 

The first method has a new user navigating a strange file system, possibly worrying that they may mess something up or get the wrong file. Possibly even going through the steps a couple times to ensure they have it right.

So honestly, which is easier?


I used Windows a few years before trying Linux and was quite proficient with it, even [tweaking my WinXP system](http://erfahren.bravehost.com/misc_files/messy_scrnshot_acer.htm) to use a custom visual style and icons (without a skinning application). I steered away from using its command line though, only using it when I needed to. didn't know enough about it to do much with it. I use the terminal all the time with Linux. some things are much quicker and easier to do in it. I've even wrote myself a couple little scripts. 

Anyway, the main argument (or what I believe it to be) has been hashed out before in many of places. Basically the "Linux isn't ready for the desktop" type thing, and you want us Linux users to concede to that (like it's some product that we're pushing on you). 

Maybe we just see this form different perspectives. To me, with Linux being a free open-source *operating system*, I'm amazed at what it can do, and don't think much about what it has problems with at this time (I have problems using the desktop effects all the time because of the proprietary ATI driver, but the novelty of them wears off eventually anyway!)

BTW: the thing in our signatures about the commands is in response to some rogue posters who instructed some people to enter malicious commands into the terminal. It's been taken care of. It's really not *all* that easy to screw things up through the terminal. :)

---

### Post by Gnigma on 2007-12-23
To all of you who keep recommending that I learn more about Linux before I have the audacity to complain, what do you think I did? I'm certainly no expert, but I did put a lot of time and energy into figuring out how to do it myself. During that learning period (which, admittedly, is far from over) I kept finding little tidbits that would have made the installation easier if I'd just known beforehand. A few questions:

Erfahren, how did you download the wifi driver without an internet connection, or did you activate it with line commands? And how long did THAT take? And you're telling me that that is easier than just downloading the driver off the web? I also have to say that I am not resentful of anything--- you all went on the defensive from the very first reply to my post, effectively showing me that you might need to work on a sense of humor. I have never blamed anyone here for my problems; I only made suggestions at how you might improve your procedure for newbies. Much has been said here about my original post from several months ago, using that as an example of how I didn't ask for help. The truth is, once I learned enough about the system, I didn't need help on that particular problem any more.

Hyper_ch, the average user uses a GUI, not the command line, and no matter how comfortable you are with it, the command line is archaic and intimidating  to new users. Face it, the average user is a Windows user, and in that system, when you use the command line, it's usually because something has screwed up. All I'm doing here is pointing out that background in your newbies--- they are NOT comfortable with it. Sure, they can eventually learn enough to deal with it, but they don't start out that way. Long lists of commands are confusing.

 Nowshining, you're sending mixed messages. You expound on how Linux is for "grown ups" who can learn, think, and do things on their own. Then you criticize me for not asking for enough help! How much help did you (ANY OF YOU) have to have to get your system up and working? Most of you sound like you're pissed that someone could do it without help. Yeah, I made mistakes, many of which were due to lack of information--- I found the information and resolved most of them.  I'm sure other things will come up, and I will resolve them the same way, or not, who knows?

I still get the feeling that this whole thread was moved, renamed, and redirected to hide it, for reasons I know not.:lolflag:

---

### Post by nowshining on 2007-12-23
>  
Nowshining, you're sending mixed messages. You expound on how Linux is for "grown ups" who can learn, think, and do things on their own. Then you criticize me for not asking for enough help! How much help did you (ANY OF YOU) have to have to get your system up and working? Most of you sound like you're pissed that someone could do it without help. Yeah, I made mistakes, many of which were due to lack of information--- I found the information and resolved most of them. I'm sure other things will come up, and I will resolve them the same way, or not, who knows? 

yes it's true, linux is for those who don't want windows/microsoft to do everything for them. I never really criticized u for not asking enough help, i mean DO THJINGS ON UR OWN, search a search engine, search the forums, on a specific error u may have - and read ol' posts of others that had the same problem, then think of how it would apply to me on the current system, or if that doesn't help - search some more, until u got the answer in ur head. U know i didn't start officially using ubuntu until july 22 2007, :) feisty was the one i started out with, i registered as u can see in 2006 or so because i needed help - i only posted 1 post back then, and they never really answered me with get gnome-ppp and try that. Nope :/ i thought mostly i had to do the whole linuxmodems thing and the hard work for my external modem. Left, came back a year later, ready and willing,  searched the forums a bit more fully that time and with new keywords, and i found my solution. :)

For me - i've had very little help from the forums - i mean little, I actually went out and did a lot on my own and with help from reading other forums via searches, some on this forum (small amount & rare), read articles on linux/unix, searched unix/linux on the net, read few linux news sites, had a problem and an error, again put it into a search engine with quotes, if that didn't get me anything, well I just then thought of any main keywords that would prob. get me more answers and or some if there not any for that particular term. 

Again I've had to help myself a lot on linux/ubuntu so far. :) but thanks to ubuntu being relatively easy I didn't need that much help. Again I also explored the system on my own and still do a bit and look up tweaks on my own, etc... 

Again - VERRRRRY little help on the forums from others, esp. this one. U may see my threads as U'll see the asking for help - maybe one or two or a bit more. A lot of those were/are from helping others. Oh and yes the second thing or so I had trouble with was "why is my password not shoing up as I type it in the terminal" = ubuntu forum search and or search engine search (i think the latter tho) and I go "oh that's why, it is taking it" lo and behold and I am where I am now.

I am not upset and u and ur guide tho in the end. I know the frustration, sometimes I get frustrated at em' to :/. That's why I suggest the main freewebs.com free website account and putting ur guide on there and making a guide of ur own and putting the url in ur sig for others that may see it on every post u made or basically underneath it. :) what do u think; I did.

Last time - ME = verrry little help from others, I helped myself the most on Ubuntu/Linux. I said those things because that was what I did to get up and know so much I do on ubuntu, again I don't know all, but I'm hoping to know at least half. Oh and yes I also did research on linux/unix and read a bit about it before switching to feisty that wonderful day i'll never forget. :lolflag:

---

### Post by erfahren on 2007-12-23
my wifi driver is "madwifi" (gotta love that name!) and is installed by default in both Feisty and Gutsy. I didn't have to download anything. I've seen some people who have my same card use "ndiswrapper' (which enables the use of native Windows drivers), but I didn't have to.

Admittingly, I wasn't quite "brand new" to Ubuntu when installing on my notebook, but had been only using it for a couple of months. I wasn't quite sure if and how well it would work at the time. I did expect some problems getting my wifi set up with WPA encryption and static IP address(es), I went by [this howto](http://ubuntuforums.org/showthread.php?t=202834) which may seem a little daunting at first but following the steps as outlined I was able to get it to work. (It actually works great after a reinstall as well, I basically just need to replace my /etc/network/interfaces file, enter my DNS address, reboot and start up the wifi. --on a fresh Windows install it takes me much longer 

Note: When I first got Vista I ended up having to research how to set up wifi with a static IP address for it as well. The network manager that Acer had preinstalled was confusing and I couldn't get connected through it. I ended up uninstalling it and using the Windows native one which was still a little confusing (and annoying) since it was much different than WinXP. -- it took me a few hours to figure it out, and resetting the security on my router a couple times in the process. 

When I was a new Linux user I *liked* doing things through the command line (for the most part), it made me feel like, I don't know, *a Linux user*!

I didn't ask for much help either. most of the questions I had easily came up in searches. One of the reasons I recommend Ubuntu to potential new users is that because of its popularity many searches on an issue will come up with Ubuntu specific results.

One main (last) thing I wanted to mention. Many of us recommend new users start out with Linux by using it in a dual-boot enviroment. (that way they still have access to the internet and can save entire web page guides to open up once in Linux if need be.)

---

### Post by erfahren on 2007-12-23
I apologize Gnigma, but I think I've personally spent enough time on this thread. You seem well-meaning (for the most part) and obviously pretty intellegent (that wasn't sarcastic). 

As mentioned though, much of this debate has been brought up before in various forms. I'm going to refer you to this post: [http://ubuntuforums.org/showthread.php?t=58017](http://ubuntuforums.org/showthread.php?t=58017)

You're welcome here at the forums (as far as I'm concerned) and it was interesting debating with you. 

 _EOF_

---

### Post by nowshining on 2007-12-23
yes it was interesting to have this fun little debate with ya. :), remember

Freewebs
Guide
Tips, Fixes, Howtwos
Contect me personally - ur welcome to...

I do hope u do return/stay to help others since u do know a bit urself. :)

---

### Post by rustybronco on 2007-12-23
> **Gnigma said:**
>  How much help did you (ANY OF YOU) have to have to get your system up and working? Most of you sound like you're pissed that someone could do it without help. Just to let you know, I have just installed hardy alpha2 on my laptop and other thjan adding acpi=force to the kernel line (yes it tells you that you need to add it) then a quick search on how to do it which I googled and came up with this thread [http://ubuntuforums.org/showthread.php?p=2595626](http://ubuntuforums.org/showthread.php?p=2595626)) other than clicking install nothing was needed.
and on my wife desktop i'm am posting this from the same live cd, just inserted it and powered it on and set it to boot from the cd/dvd-rom drive. yes not all installs are that easy and to tell the truth hardy was the first ubuntu distro to run on her machine ootb (blasted ati video card) , still all in all not hard to do.

---

### Post by tact on 2007-12-23
> **Gnigma said:**
> Actually, most of my original post IS about the installation procedure. Almost all of the RESPONSES are antagonistically directed towards my editorializing.

The little part of your "installation guide" that is actually about installing, once the fat is boiled away is:
1.  Have a working network connection
2.  install from CD
3.  Apply all available updates


This is not new.  Its been said a million times and pretty much falls into the realm of commonsense. 

Ciao

---

### Post by tact on 2007-12-23
> **Gnigma said:**
> 
Hyper_ch, the average user uses a GUI, not the command line...


Totally agreed.  

And the "average user" uses what?   Ohh..  you mentioned that also:
> **Gnigma said:**
> 
Face it, the average user is a Windows user, 

Again you are right.  


So the logic goes:
1.  the average user uses a GUI
2.  the average user is a windows user

Reducing for the common factor you have the statement then:
"Windows users are GUI users."

So clear and obvious.   

Just as obvious is the statement:
"linux is not windows"

ergo
a.  linux users are not (necessarily) GUI users (only) and 
b.  linux users are not "average" users

You strike me as an intelligent person and so these little factoids cannot have escaped you.  Yet you CHOSE to use linux.  Knowing.

Presuming you are an adult, making an informed choice, a knowing choice, of a not average operating system that is not windows - I wonder if, as an adult, you realised the need to take responsibility for your own choice.

The evidence to support the notion of you taking responsibility on yourself for your choice - is not present in the writing of your "guide".  

Had you done so (taken full responsibility on yourself for your choice) then perhaps your "guide" to installing ubuntu may have included much less sniping at the community here for perceived slights or elitism.

Taking full responsibility for one's own choice would have included many things, but certainly amongst those things would be:
1.  gratitude the community exists at all (it gives rise to the possibility of good help)
2.  no disappointment if the possibility of assistance didnt materialise because you also have ...
3.  a realisation that there is not a single person in this forum (or any other free/community based forum) who ***owes*** you any kind of assistance at all.  At most all you would be ***owed*** is simple human courtesy in any response you received to your requests for aid.  If anyone was rude to you - take it up with that person.

Taking swipes at the community generally for any individual's rudeness towards you is inappropriate at best.

---

