---
title: "The latest upgrade 17.10 dosen't show up after intallation"
date: 2017-06-12
forum: Ubuntu Development Version
---

### Post by chichimfi on 2017-06-12
Hello everyone,

please can anyone help me with this ?

I had ubuntu 16.04, I upgraded it to 16.10 then to 16.10, until now everything is fine .. but then I want to upgrade it to 17.10 and I did the same things like before, when the installation finished the laptop restarted but I found that it still on 17.04 version, I  tought that it may not be installed but when I try to upgrade it says that the software is up to date.
when I check it from terminal it says 17.10

---

### Post by deadflowr on 2017-06-12
*Thread moved to **Ubuntu Development Version**.*
17.10 is still very much a work in progress.

---

### Post by Bucky Ball on 2017-06-12
> **deadflowr said:**
> 17.10 is still very much a work in progress.

^^^
This. 17.10 not due for official release until October. If you're looking to get into Ubuntu, suggest the stable 16.04 LTS, which has five years of support rather than nine months.

17.10 is no place to start, presuming that is what you're doing. ;)

---

### Post by ventrical on 2017-06-13
> **chichimfi said:**
> Hello everyone,

please can anyone help me with this ?

I had ubuntu 16.04, I upgraded it to 16.10 then to 16.10, until now everything is fine .. but then I want to upgrade it to 17.10 and I did the same things like before, when the installation finished the laptop restarted but I found that it still on 17.04 version, I  tought that it may not be installed but when I try to upgrade it says that the software is up to date.
when I check it from terminal it says 17.10

Those 17.04 inidicators are sort of like vanilla files. You are now running in 17.10 development version so you are in testing version.

Regards..

---

### Post by jbicha on 2017-06-13
If you log in to GNOME, the Settings app will show you the correct Ubuntu version.

Unity is just stuck in the past. :( </badjoke>

---

### Post by ventrical on 2017-06-13
> **jbicha said:**
> If you log in to GNOME, the Settings app will show you the correct Ubuntu version.

Unity is just stuck in the past. :( </badjoke>

It's really uncalled for Jeremy. A lot of people worked hard on unity here in development version. Mark has been very professional about all of this. He has put  his faith  and hope in people like you to incorporate some of the unity ideas into gnome3.  You now are an ambassador of gnome3. Many of us have taken up testing gnome3 as flagship DE without any slights and we are doing it because we enjoy testing. Could you please then show some professional courtesy for those of us who tested unity (as well as gnome3) as dilligently as possible in the previous versions? 

Regards..

---

### Post by jbicha on 2017-06-14
I apologize for offending you or anyone else.

I too have fixed numerous issues on Unity over the years. I fixed gnome-control-center to show the correct version automatically from now on; maybe I'll eventually do the same for unity-control-center for 17.10. I had to fix 17.04 shortly before release! (gnome-control-center now picks up the version automatically but always before it was hard-coded and had to be manually updated every release cycle.)

I think it is a disservice to Unity users to lead them to think that they will be able to use the same Unity they loved in 16.04 LTS just as well in 18.04 LTS. It will not work as nicely. And so far, I have not seen anyone step forward to help with keeping Unity7 working well. With no developers or maintainers, you're going to have more and more of this kind of issue.

---

### Post by ventrical on 2017-06-14
> **jbicha said:**
> I apologize for offending you or anyone else.

I too have fixed numerous issues on Unity over the years. I fixed gnome-control-center to show the correct version automatically from now on; maybe I'll eventually do the same for unity-control-center for 17.10. I had to fix 17.04 shortly before release! (gnome-control-center now picks up the version automatically but always before it was hard-coded and had to be manually updated every release cycle.)


Even more the reason why we welcome your contributions to the development forum (as it seems you are the only principle developer stepping up at the moment).

> 
I think it is a disservice to Unity users to lead them to think that they will be able to use the same Unity they loved in 16.04 LTS just as well in 18.04 LTS. It will not work as nicely. And so far, I have not seen anyone step forward to help with keeping Unity7 working well. With no developers or maintainers, you're going to have more and more of this kind of issue.

 I have to respectfully disagree with this assessment .. but please leave it with me and I will try to get a clarification on the developers and maintainers  current status.

Regards..

---

### Post by ventrical on 2017-06-14
> **jbicha said:**
> 
I think it is a disservice to Unity users to lead them to think that they will be able to use the same Unity they loved in 16.04 LTS just as well in 18.04 LTS. It will not work as nicely. And so far, I have not seen anyone step forward to help with keeping Unity7 working well. With no developers or maintainers, you're going to have more and more of this kind of issue.

The team has been asked to focus on GNOME and other desktops including keeping KDE unblocked.  The quality of the 18.04 release will depend largely on community involvement so , yes , xubuntu, lubuntu kubuntu and the other official flavours will be supported and need to be tested. 

 It has also been pointed out to me in plain language, that if Jeremy is correct about unity7 possibly causing troubles then we should perhaps pull it from the archives . That is a big if and it will remain in the archives until that time.

  I am not trying to mislead other end_users (or was I ) but now I have a clearer understanding, as Mark has enlightened me, that unity7 at this  time is more or less a footnote unless someone steps forward.

> 
 If there are folks interested in updating Unity7 for new dependencies  and behaviours in the underlying system, we can easily provide  per-package-upload abilities to that community. 

Regards..

---

### Post by ventrical on 2017-06-14
> **jbicha said:**
> I apologize for offending you or anyone else.



My apologies also if some of my statements had caused confusion. Now that I have a clearer understanding of the situation, I stand corrected.

Regards..

---

### Post by rrnbtter on 2017-06-14
Greetings,
Honest criticism is hard to take. Especially when it comes from a friend, an acquaintance,  a family member or a complete stranger.  It been my experience with this forum that every statement is partly right and partly wrong. It's my opportunity to learn from the part that is right and the part that is wrong. 
That being said I am delighted that we have a "dev" participating in this forum. He has to be given a free pass or I can't learn anything. 

So far as the Ubuntu version being misrepresented.  I didn't think that it becomes 17.10 until October.  At least I don't think that what I am using is what I'm expecting to have. So no, in my opinion it's partly 17.04 and partly 17.10.  Hopefully I'm at least half right!

---

### Post by ventrical on 2017-06-14
+1 :)

---

### Post by jbicha on 2017-06-15
> **rrnbtter said:**
> He has to be given a free pass or I can't learn anything.

Please don't give me a pass. I have to abide by the Ubuntu [Code of Conduc]("https://www.ubuntu.com/about/about-ubuntu/conduct")t too!

@ventrical, I didn't mean to accuse you of misleading people, but when I re-read what I wrote, I can see I gave that impression. I apologize for that.

I think Mark made his statements about Unity still being available in 18.04 LTS sincerely and with hope that there will be some people step up to keep things running. Since Ubuntu's beginning, he has always encouraged other desktops to build on top of Ubuntu from Kubuntu (first release was only 6 months after Ubuntu's first release!) to Ubuntu GNOME (I think that investment paid off well for him!) to the newest flavor Ubuntu Budgie (and of course several other flavors too).

---

### Post by jbicha on 2017-06-15
> **ventrical said:**
>  itseems you are the only principle developer stepping up at the moment).


It looks to me like Canonical as a company is encouraging their developers and others to be more pro-active in communicating what they're working on.

If you're not subscribed to the [Ubuntu Insights]("https://insights.ubuntu.com/") site, perhaps you should be!

Until recently, you probably wouldn't hear anything from the Ubuntu Kernel Team (as an example) unless you subscribed to the particular mailing list where they published their weekly meeting reports. And I don't ever remember the Ubuntu Desktop team sending out weekly reports but we are now!

So although developers aren't directly active on the Forums, I think they are communicating more than ever. :D

---

### Post by ventrical on 2017-06-16
> **jbicha said:**
> Please don't give me a pass. I have to abide by the Ubuntu [Code of Conduc]("https://www.ubuntu.com/about/about-ubuntu/conduct")t too!

@ventrical, I didn't mean to accuse you of misleading people, but when I re-read what I wrote, I can see I gave that impression. I apologize for that.

I think Mark made his statements about Unity still being available in 18.04 LTS sincerely and with hope that there will be some people step up to keep things running. Since Ubuntu's beginning, he has always encouraged other desktops to build on top of Ubuntu from Kubuntu (first release was only 6 months after Ubuntu's first release!) to Ubuntu GNOME (I think that investment paid off well for him!) to the newest flavor Ubuntu Budgie (and of course several other flavors too).

No offense taken whatsoever. Just to be a little more clear, I was asked if I would like to be team Captain of Ubuntu Development Version a few years back and I took up the task from the previous admin. I made a few changes and one of them was to build some bridges between Canonical Developers and UbuntuForums. In the last couple of years I have been corresponding with Mark, Will Cooke , Mark Deslauriers and others and they have been remarkably helpful in answering several questions I had about unity8, mir and many other questions concerning ubuntu and development.

 In my most recent communications about GNOME and unity7 remaining in the archives I now have Will Cooke and Mark at the ready  to share with us all the pointers and access we need to get the ball rolling.  I started a thread here at the forums and Will Cooke is following the thread. Of course we would need a sub-group to take up some of the work to address all of the concerns that Will has pointed to.

  Also , in no uncertain terms, Will and Mark have affirmed their commitment of directing the team to test/develop  GNOME and the other current distros and that if unity7  causes trouble with GNOME moving forward , that it will be pulled from the archives. So I can accept that. I also hope that my most recent efforts do not give the impression that I am trying to run interference on GNOME.  I moved past it, however difficult it has been. So if you decide that unity7 is causing troubles for GNOME being in the archives during 17.10/18.04 and want it pulled then I will certainly go along and support your decision.

  Keep in mind that there are  a lot of end_users who , over the last few years, have taken up the task to learn how to use unity and to now have to , once again, take up a new learning curve with GNOME is a lot to ask. Thats not a slight against GNOME. It's just a fact that many persons have become dependent on the refined user_friendliness  of unity7 and how it themes into the stream of things. So unity7 concept has kept the new user in mind .  Whether one likes it or dislikes it is not the point. The point is that is ease of use was a real draw from persons making transitions and conversion from Windows. So I am not speaking for Mark but I think he is trying communicate that he hopes that we can make GNOME as smooth and sleek and sexy as Unity was, that GNOME devs on the ubuntustack of things can incorporate some of the core ideas and concepts that went into developing Unity.

 So the Canonical desktop team has shared their views on what needs to be done.  Perhaps you could send us a short list  on some of the things *you* think need to be maintained (unity) and some of the heavy lifting that it will involve. It would at least give me a better outlook on what needs to be done and if I can commit to it.

Thank you  and regards...

and .. as usual .. sorry to be off topic :)

---

