---
title: "I just installed Ubuntu on my mom's laptop"
date: 2008-03-16
forum: The Cafe
---

### Post by Antarctica on 2008-03-16
Note:  This is just a story about me installing Ubuntu on my mom's laptop and my experience with Linux and Ubuntu.

I finally installed Ubuntu on my mom's laptop, and it runs with almost no problems!

I used to be sick and tired of her asking me to fix her computer when she was running Windows.  I was always fixing some little stupid problem such as getting the wireless Internet to work or changing a file's extension from something wrong to the right one just to get a program to run it.  You know... stupid stuff.  Then, yesterday I decided to install Ubuntu onto the laptop.  I had been running Linux on my desktop since July 2006 and Ubuntu since November 2006, and let me tell you... Ubuntu is the best yet.  I'll admit that it turned me off during the releases of Dapper and Edgy, but the Ubuntu team never gave up and fixed as many problems as they could.  Since the release of Gutsy, I've had very few problems with Ubuntu.

Anyway, the installation went very well.  The only problem that I have with the laptop is that Ubuntu runs a bit slow compared to my desktop.  Of course, you're comparing a Gateway laptop with a 1.2 Intel Celeron processor and 256 MB RAM to a 3.0 GHz AMD Athlon64 X2 dual core processor with 3.0 GB RAM and a 500 GB SATA 3.0 Gbit/s hard drive.  Of course the laptop is gonna be slow compared to the desktop.  The cool thing is that I found some tweaks for the laptop, and it runs a bit faster, but I wish it would run even faster than that.  It's all cool though.

I think that my mom will really like Ubuntu.  She can do everything she normally does without dealing with stupid, easy to fix problems or those problems that result from poor programming and lack of administrative restrictions.  I'm glad that Linux developers and programmers focused more on the GUI, user functionality, and user friendliness because regular computer users like my mom wouldn't know the first thing to do if she saw a bash prompt.  It's gonna be really easy and cool for her.  She'll be able to surf the Internet without any worries, check her email, listen to music, and everything will be organized.  But yeah, that's my rant and I just wanted to let the world know.  If you have any questions or comments, hit me up, okay?

---

### Post by hhhhhx on 2008-03-16
cool! :)

---

### Post by freebeer on 2008-03-16
Nice.  You might want to set up remote access on that then if she has any issues, you can fix it remotely. (ninja style)

---

### Post by rs3 on 2008-03-16
I've only managed to convert my parents over to Firefox and Thunderbird so far; they continue to run XP, but I'll get 'em someday. ;)

Great work!

(and freebeer: That is absolutely a great idea.  I live about 2000 miles from my parents, so that'd be a must-have to resolve issues.)

---

### Post by Antarctica on 2008-03-16
> **freebeer said:**
> Nice.  You might want to set up remote access on that then if she has any issues, you can fix it remotely. (ninja style)
How do I set up remote access on her laptop?  Btw I think it would be kinda slow since her laptop is already running somewhat slow on Ubuntu.  Any suggestions on how to speed it up also?

---

### Post by Antarctica on 2008-03-16
> **rs3 said:**
> I've only managed to convert my parents over to Firefox and Thunderbird so far; they continue to run XP, but I'll get 'em someday. ;)

Great work!

(and freebeer: That is absolutely a great idea.  I live about 2000 miles from my parents, so that'd be a must-have to resolve issues.)
The next time you're on their computer, load a bunch of spyware, viruses, crap, etc. onto her computer and blame Internet Explorer and the lack of administrative access and organization.  Then tell her that most of the stuff you download and install comes FREE from an online catalog (They probably wouldn't understand apt-get or Synaptic Package Manager).  If they still don't want to switch to Ubuntu, tell them that they could've saved over $500 with Windows XP or Vista and Microsoft Office.

---

### Post by steveneddy on 2008-03-16
Very good post.

---

### Post by MONODA on 2008-03-16
hmmm... i would have installed xubuntu. anyway, if you have compiz enabled, turn it off, it will make it faster.

---

### Post by Antarctica on 2008-03-16
Oh yeah, I forgot to mention... the only thing that would keep the laptop from running Ubuntu is some stupid poker game my mom downloaded and played on Windows.  I remembered installing Ubuntu once on her other computer, the desktop.  I could get WINE to run the program, but it depended on Internet Explorer, which I installed also.  The program wouldn't recognize IE, so back to Windows I went (At least I put Windows 2000 on it.  I think 2000 was the best since it was lightweight and was NT based, much better than 98.)  Anyway I think I got Windows covered... Virtualbox.

---

### Post by Antarctica on 2008-03-16
> **MONODA said:**
> hmmm... i would have installed xubuntu. anyway, if you have compiz enabled, turn it off, it will make it faster.
Xubuntu would run faster, but I personally don't like it and have more experience in GNOME and KDE.  Also, Compiz is disabled totally and most unused services are turned off too.  I also profiled GRUB to speed up boot time.  Those are a few tweaks.  I'm hoping there's more that'll speed up the laptop without sacrificing user friendliness and functionality.

---

### Post by LookTJ on 2008-03-16
> **Antarctica said:**
> Oh yeah, I forgot to mention... the only thing that would keep the laptop from running Ubuntu is some stupid poker game my mom downloaded and played on Windows.  I remembered installing Ubuntu once on her other computer, the desktop.  I could get WINE to run the program, but it depended on Internet Explorer, which I installed also.  The program wouldn't recognize IE, so back to Windows I went (At least I put Windows 2000 on it.  I think 2000 was the best since it was lightweight and was NT based, much better than 98.)  Anyway I think I got Windows covered... Virtualbox.
PokerTH is available.

---

### Post by O3. on 2008-03-16
c00_l

---

### Post by mridkash on 2008-03-16
I've installed Ubuntu on my parents computer since last 6 or so months. I'm happy to know everything going smoothly, we got rid of pirated software, my mom does good image editing with Gimp and they use Amarok, pidgin, firefox, digiKam all the time. For some specialty needs (IE only websites), I've installed legit Win XP on Virtual box for them.
And now, I love to make them software, like a video cutting and joining script using mplayer, add to VCD script, easy backup software etc. All just a right click away using nautilus-actions.
Now, I dont get Win specific complaint calls, or "system-is-slow" calls from them, rather, I get calls like, how can I do this. And I reply, I'll make you the thing which does that.

And also, we use simple vnc viewer over ssh for remote access.

---

### Post by rs3 on 2008-03-16
> **Antarctica said:**
> Xubuntu would run faster, but I personally don't like it and have more experience in GNOME and KDE.  Also, Compiz is disabled totally and most unused services are turned off too.  I also profiled GRUB to speed up boot time.  Those are a few tweaks.  I'm hoping there's more that'll speed up the laptop without sacrificing user friendliness and functionality.

Sounds like you covered all the possible bases there.  Unless she makes use of it, though, I would also disable multiple workspaces and the workspace switcher.  And although I have never done it myself (and don't rightly know how to yet), I understand you can replace nautilus with thunar (which is XFCE's file manager) which would free up a little memory.

---

### Post by madjr on 2008-03-16
> **Antarctica said:**
> Xubuntu would run faster, but I personally don't like it and have more experience in GNOME and KDE.  Also, Compiz is disabled totally and most unused services are turned off too.  I also profiled GRUB to speed up boot time.  Those are a few tweaks.  I'm hoping there's more that'll speed up the laptop without sacrificing user friendliness and functionality.


gnome will run fine, just remove all the applets from the panel you won't use and uninstall "tracker" and remove it from startup programs.

1 panel also frees up mem i think

also firefox 3 beta goes faster

---

### Post by EdThaSlayer on 2008-03-16
I found the part where you talked about the difference between the laptop and desktop. Nice story though.

---

### Post by sumguy231 on 2008-03-16
> **Antarctica said:**
> The next time you're on their computer, load a bunch of spyware, viruses, crap, etc. onto her computer and blame Internet Explorer and the lack of administrative access and organization.  Then tell her that most of the stuff you download and install comes FREE from an online catalog (They probably wouldn't understand apt-get or Synaptic Package Manager).  If they still don't want to switch to Ubuntu, tell them that they could've saved over $500 with Windows XP or Vista and Microsoft Office.

This kind of thing makes us all look bad. Don't do it.

---

### Post by Barrucadu on 2008-03-16
I've put Ubuntu on my mum's laptop - unbeknown to her. I can't wait until she gets home later today and the inevitable "MICHAEL, WHAT HAVE YOU DONE!?" echoes through the house :)
Of course, I'll refuse to tell her how to get back into Windows for at least 24 hours.

---

### Post by sumguy231 on 2008-03-16
> **Barrucadu said:**
> I've put Ubuntu on my mum's laptop - unbeknown to her. I can't wait until she gets home later today and the inevitable "MICHAEL, WHAT HAVE YOU DONE!?" echoes through the house :)
Of course, I'll refuse to tell her how to get back into Windows for at least 24 hours.

[quote=sumguy231]This kind of thing makes us all look bad. Don't do it.[/quote].

---

### Post by Bartender on 2008-03-16
> **Antarctica said:**
> a Gateway laptop with a 1.2 Intel Celeron processor and 256 MB RAM 

Have you checked into how much RAM the Gateway will take?  Without knowing the exact model it's hard to tell, but if you could get a gig of RAM under the hood it would act a LOT snappier.  256 is borderline.  Even 512 would make a huge difference.

Your mom would be so impressed with your computer skills!   :)

---

### Post by Lord Illidan on 2008-03-16
> **Bartender said:**
> Have you checked into how much RAM the Gateway will take?  Without knowing the exact model it's hard to tell, but if you could get a gig of RAM under the hood it would act a LOT snappier.  256 is borderline.  Even 512 would make a huge difference.

Your mom would be so impressed with your computer skills!   :)

Agreed, RAM can make a huge difference.

---

### Post by rs3 on 2008-03-16
> **sumguy231 said:**
> This kind of thing makes us all look bad. Don't do it.

+1

---

### Post by Antarctica on 2008-03-16
> **Bartender said:**
> Have you checked into how much RAM the Gateway will take?  Without knowing the exact model it's hard to tell, but if you could get a gig of RAM under the hood it would act a LOT snappier.  256 is borderline.  Even 512 would make a huge difference.

Your mom would be so impressed with your computer skills!   :)
Gosh, I go to sleep and I wake up and go to work, and when I come back my thread went from 1 page to 3 pages!  Wow!

But yeah, the laptop... it's a Gateway MA6 I think.  I should upgrade it to 512 MB RAM.  I'll probably do that within the next few weeks.

---

### Post by divindavid on 2008-03-16
i am glad your mom likes ubuntu my mom likes it too but she still wants to use XP  but theres time i am only 13 and ubuntu will only get better

---

### Post by freebeer on 2008-03-16
> **rs3 said:**
> 
(and freebeer: That is absolutely a great idea.  I live about 2000 miles from my parents, so that'd be a must-have to resolve issues.)

No problem.  I'm in a similar situation where I'll be setting up my father's machine.  Although I live next door to him, I'm anticipating a lot of "how do I do...?" questions.  I'll be able to control his mouse/screen and he can follow the bouncing mouse.  (click here, open application here, etc.) And I won't have to leave my house to do it.  ;)

---

### Post by n3tfury on 2008-03-16
> **Antarctica said:**
> \ I was always fixing some little stupid problem such as getting the wireless Internet to work or changing a file's extension from something wrong to the right one just to get a program to run it.  You know... stupid stuff. 

i have a comment:  those aren't windows problems. 

> **Antarctica said:**
> The next time you're on their computer, load a bunch of spyware, viruses, crap, etc. onto her computer and blame Internet Explorer and the lack of administrative access and organization.  Then tell her that most of the stuff you download and install comes FREE from an online catalog (They probably wouldn't understand apt-get or Synaptic Package Manager).  If they still don't want to switch to Ubuntu, tell them that they could've saved over $500 with Windows XP or Vista and Microsoft Office.

worst.  idea. ever.

> **Barrucadu said:**
> I've put Ubuntu on my mum's laptop - unbeknown to her. I can't wait until she gets home later today and the inevitable "MICHAEL, WHAT HAVE YOU DONE!?" echoes through the house :)
Of course, I'll refuse to tell her how to get back into Windows for at least 24 hours.

this is the second worst idea ever.

---

### Post by jflaker on 2008-03-16
> **mridkash said:**
> I've installed Ubuntu on my parents computer since last 6 or so months. I'm happy to know everything going smoothly, we got rid of pirated software, my mom does good image editing with Gimp and they use Amarok, pidgin, firefox, digiKam all the time. For some specialty needs (IE only websites), I've installed legit Win XP on Virtual box for them.
And now, I love to make them software, like a video cutting and joining script using mplayer, add to VCD script, easy backup software etc. All just a right click away using nautilus-actions.
Now, I dont get Win specific complaint calls, or "system-is-slow" calls from them, rather, I get calls like, how can I do this. And I reply, I'll make you the thing which does that.

And also, we use simple vnc viewer over ssh for remote access.

There is a plugin for FF to impersonate IE, Netscape and opera...It is User Agent Switcher.  I had an issue with TurboTax.com not allowing Linux/FF.....turned on UAS and I was working around the site limitation.

The UAS can allow you to get on IE only sites and 99% of the time, there are no functional issues.

---

### Post by days_of_ruin on 2008-03-16
> **rs3 said:**
> I've only managed to convert my parents over to Firefox and Thunderbird so far; they continue to run XP, but I'll get 'em someday. ;)

Great work!

(and freebeer: That is absolutely a great idea.  I live about 2000 miles from my parents, so that'd be a must-have to resolve issues.)
And it sounds like the OP lives even further away then that
:lolflag:

---

### Post by days_of_ruin on 2008-03-16
> **Antarctica said:**
> The next time you're on their computer, load a bunch of spyware, viruses, crap, etc. onto her computer and blame Internet Explorer and the lack of administrative access and organization.  Then tell her that most of the stuff you download and install comes FREE from an online catalog (They probably wouldn't understand apt-get or Synaptic Package Manager).  If they still don't want to switch to Ubuntu, tell them that they could've saved over $500 with Windows XP or Vista and Microsoft Office.

one word:NO!

---

### Post by Antarctica on 2008-03-16
> **n3tfury said:**
> i have a comment:  those aren't windows problems. 



worst.  idea. ever.



this is the second worst idea ever.
No, those are Windows problems.  Windows relies heavily on file extensions to know what program to use for a specific file.  I could change a text file's extension to .exe and Windows would try to run it whereas in Linux I could change the file extension to whatever I want or even remove it and it will run the file as what it's supposed to be.  As for the wireless Internet working... there are several programs that conflict with each other that can cause the wireless internet to not work.

Idea #2... about getting that person's parents to switch to Ubuntu.  It was just a practical joke to show that regular browsing the Internet in Internet Explorer can cause viruses to be downloaded and the computer to become unstable.

Barracadu's idea... I disagree with you totally.  Total immersion!  You may not like it at first since it's a huge change, but you may grow into it and never want to switch back.

---

