---
title: "Ubuntu Security Center"
date: 2010-10-26
forum: Security
---

### Post by fmfrisch on 2010-10-26
I'm currently writing a python-application. This will be my first "real" python application. The aim is be to create a app with a plugin-interface for different available security apps in the ubuntu repo's. Right now what I'm aiming for is for it to read the logs of rkhunter and chkrootkit. Later plans is to get it to host a interface for ClamAv and Apparmor. The app would let you by pressing a button launch different security app's checks and then display the logs warnings in a nicer way. It would also integrate with the notify function in ubuntu. 

The feel would be of a windows anti-virus software.

there are some security-info apps out there already but they are mostly for server-admins. This app would instead be for the security-aware person who uses the normal edition of ubuntu.

My question is whether there are people who would find this in anyway useful?

---

### Post by dogdo on 2010-10-26
Yes what your proposing sounds like a really useful idea. 

A security centre for desktop users for ubuntu would be a definite plus for me-im tired of having to check things in the terminal all the time.

---

### Post by cariboo on 2010-10-26
Aren't the rkhunter and chkrootkit logs already viewable through the log file viewer? it may be a better idea to create an updated version of Firestarter.

---

### Post by fmfrisch on 2010-10-26
Yes they are viewable in logviewer. But its not presented in a very nice way for a person who knows nothing about computers. What i would do is to search the logs if something finds a virus/rootkit i'll change the color of my appindicator red and there will be a notification saying "you're computer has been compromized" or what have you. ie something understandable and easy that ones grandmother would be able to handle

---

### Post by Rubi1200 on 2010-10-26
I think that, in theory, this is a good idea and I commend you for your efforts to try and help fellow Ubuntu users.

However, if I may, I would like to express some concerns I have.

1. part of the skill involved in reading the logs from tools like rkhunter and chkrootkit is understanding what is and what is not a real threat. 

Having something pop up or turn red will not only cause unnecessary alarm, but upon further investigation may prove to be nothing more than a false positive. 

Take a look at the numerous threads here from people, excuse my saying this, freaking out over nothing.

2. the same applies for ClamAV (and other antivirus programs on Linux).

3. I am also concerned that users may install these tools for no good reason other than to use your interface to see something pretty.

4. where I do see something like this being useful is for tools like AppArmor and possibly Upstart (or some way of having a GUI to control services in /etc/init.d).

Please do not take offense at what I have written. 

As I said, your project is potentially very valuable. 

My comments merely express some concerns I, as an ordinary user, would have about something like this.

I wish you the best of luck in your endeavors.

---

### Post by dogdo on 2010-10-26
Dont know if they have a copyright on it but opensuse have a nice interface for apparmor.

---

### Post by OpSecShellshock on 2010-10-26
Lately the only AV utilities in Windows that bring up highly visible warnings are the fakes.

Also, I'm not sure it would be responsible to put a front end on things like chkrootkit and rkhunter because of the false positives (as mentioned above). The fact is, they're just not particularly useful utilities for non-advanced users. I could see it possibly working if it had some kind of a reminder to reset the baselines every time other software updates were applied, though.

If you're going to incorporate some of the logged events, such as those that are network-based, you could put in a function that identifies, for example, the port, and then have a utility that checks it against the IANA's list of well-known port numbers [here]("http://www.iana.org/assignments/port-numbers") (with the caveat that anything over 1024 is not necessarily used for what's listed, and I don't think it's been updated in a while). There would need to be some kind of visual distinction made between server-side and client-side ports, and then people could see if they have some application running that might use those services.

Basically I'd suggest that a utility that performs accounting of process and network activity, and allows users to, in a sense, learn their system without studying it (if that makes sense), would be much more useful on a Linux desktop than a rootkit or malware scanner would be.

---

### Post by bodhi.zazen on 2010-10-26
> **dogdo said:**
> Dont know if they have a copyright on it but opensuse have a nice interface for apparmor.

And Fedora has a nice graphical interface for SELinux.

I would add a graphical interface for Apparmor to the "wishlist" for Ubuntu, both for monitoring (alerts) and configuration.

---

### Post by fmfrisch on 2010-10-26
Please this is a brainstorm I will not take offense, I appreciate all of your concerns!

As for the false positives I've already thought a lot about that. If you use any of these rootkit checkers you'll soon realize that plain untampered UBuntu will cause a bunch of false positives. Which is one of the reasons why I think this app could be useful. If the software new what false-positives are triggered by the current edition of ubuntu then there is no need for the app to bring that to the users attention.

As for the alarm that was a bit of overstatement. As you also might know you usually get like 42 warnings and a "no rootkits were found". As for a actual alarm that would happen when a actual rootkit is found. Now correct me if you have different experiences; this is very unusual? - That's what i've found at least. The 42 warnings i would present in a "everything is ok, but there were some minor warnings"-sort of way.

and then maybe order the warnings of severity-levels.

As for the people using it because it looks good. I agree. I do not need UBuntu needs a security center for the average browsing/office/multimedia user. But if you believe that ubuntu/linux will grow than there is sooner or later going to be a need for this. So why not already now start a security-aware Ubuntu-user - before all hell breaks loose.

For me I would say the biggest security issue with linux is the users believe in linux being airtight out of the box "and i dont have to do anything".

 I do agree though, this is a very fine line and either you could create a app that is misleading in insuring the user everything is safe even though you have a rootkit eating up your computer from the inside. Or you make the user get rid of linux "bc its virus infested already from the start".

---

### Post by fmfrisch on 2010-10-26
[QUOTE=]I would add a graphical interface for Apparmor to the "wishlist" for Ubuntu, both for monitoring (alerts) and configuration.[/QUOTE]

there is the apparmor-notify that i at least find very useful!

---

### Post by bodhi.zazen on 2010-10-26
> **fmfrisch said:**
> there is the apparmor-notify that i at least find very useful!

Yes and no. It only help if you modify your aa profiles so they are quiet (silent) by default. Otherwise it is like the boy who cries wolf and it gets ignored.

Quiet by default is difficult to achieve for some common applications (firefox) as they are large applications with diverse uses.

---

### Post by dogdo on 2010-10-26
> **fmfrisch said:**
> there is the apparmor-notify that i at least find very useful!

I just installed this from the official repos's but i cant seem to find the interface-nor can i see any notifications...

---

### Post by bodhi.zazen on 2010-10-26
> **dogdo said:**
> I just installed this from the official repos's but i cant seem to find the interface-nor can i see any notifications...

There is no interface, you get a pop up notice if there is an apparmor alert.

You first need to enable apparmor profiles (they are in complain mode) you then need to generate alerts (should not be that hard to generate an alert).

---

### Post by dogdo on 2010-10-26
> **bodhi.zazen said:**
> There is no interface, you get a pop up notice if there is an apparmor alert.

You first need to enable apparmor profiles (they are in complain mode) you then need to generate alerts (should not be that hard to generate an alert).

I using 10.04 with all the default profiles in enforce mode. 

Does firefox have a new profile for 10.04? the last times i tried to make firefox profiles i always borked the system-a UI is definitely needed to make new profiles-for those of us that dont do well with the terminal.

---

### Post by mainerror on 2010-10-27
> **Rubi1200 said:**
> I think that, in theory, this is a good idea and I commend you for your efforts to try and help fellow Ubuntu users.

However, if I may, I would like to express some concerns I have.

1. part of the skill involved in reading the logs from tools like rkhunter and chkrootkit is understanding what is and what is not a real threat. 

Having something pop up or turn red will not only cause unnecessary alarm, but upon further investigation may prove to be nothing more than a false positive. 

Take a look at the numerous threads here from people, excuse my saying this, freaking out over nothing.

2. the same applies for ClamAV (and other antivirus programs on Linux).

3. I am also concerned that users may install these tools for no good reason other than to use your interface to see something pretty.

4. where I do see something like this being useful is for tools like AppArmor and possibly Upstart (or some way of having a GUI to control services in /etc/init.d).

Please do not take offense at what I have written. 

As I said, your project is potentially very valuable. 

My comments merely express some concerns I, as an ordinary user, would have about something like this.

I wish you the best of luck in your endeavors.

This.

In my opinion we should not try to get Ubuntu to adapt to the old way of thinking but to move the way people are thinking about security now into a better more correct direction.

No application on earth will ever manage to secure a computer if the problem is between chair and keyboard. It was attempted by other companies in the past to actually give the users a feeling of security and to **re**act on mistakes they did. Now as you can see the re in react is bold and that for a very good reason.

I'm absolutely certain that it is possible to educate future users how to use a computer in the right way to prevent the need of so called security tools. Mostly it is related to browsing on sites you shouldn't, opening spam mails even tho you exactly know you shouldn't, downloading applications promising you to become a rock star if you download it, the list is endless.

The main problem is that due to super special security kits the user feels save. He thinks "Meh I'm secure due to my super special invincible l33t security kit" and he will continue making mistakes. If now a company would really put effort in trying to educate people on what security really means and what to avoid by explaining how to spot such obvious dangerous places/actions then we'd not have to discuss this exact problem right now.

I'm totally aware that the world is not flat and I'm not naive so I know that even if you are a security aware user sometimes strange things can happen but that is exactly where knowledge would save you. Ubuntu or Linux in general out of the box is a very secure system compared to other options which makes it a very good starting point for teaching upcoming generations how to really use their computers in a more secure way and that is by "THINKING" and not by not thinking because you are secure anyway due to using Ubuntu + a super security kit. This would be the wrong direction in my opinion.

---

### Post by fmfrisch on 2010-10-27
> **mainerror said:**
> This would be the wrong direction in my opinion.

About previous writer or about hte application im trying to write?

---

### Post by mainerror on 2010-10-27
> **fmfrisch said:**
> About previous writer or about hte application im trying to write?

Oh no. Don't get me wrong. I was referring to the whole situation. I mean that the security-awareness education is stagnating. We ain't moving in the right direction if we just code an application and tell people to use it. They will think they are secure but they ain't that more secure.

---

### Post by emarkay on 2010-10-27
No "quotes" in this post, but there are some good thoughts here.  

IMHO, anything that allows a better understanding, without "thinking for you" (Oh how I HATE when things "pop up" or reconfigure based on some sub-genius' idea of what their marketing department thought I wanted to do) and is configurable from "do nothing but the basic task" to "Help me Obi Wan" can only be a good thing; as long as it's peer reviewed and monitored/updated for bugs and updates.

---

