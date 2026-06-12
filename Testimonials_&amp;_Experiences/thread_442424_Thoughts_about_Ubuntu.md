---
title: "Thoughts about Ubuntu"
date: 2007-05-13
forum: Testimonials &amp; Experiences
---

### Post by Talon2 on 2007-05-13
My thoughts concerning Fiesty:

Fiesty is somewhat more annoying to use than were Dapper and Edgy.  There are 3 areas that I continue to have problems with:

- Power management.  Something happened in Fiesty.  Suspend and hibernate used to work reasonbly well on my systems prior to Fiesty.  Now it seems that I have one problem after another.  The really interesting thing is that often with no changes on my part power management will break, fix or change how it operates.  It is like power mangement has a mind of its own.  I have investigated the technical details in an attempt to try to figure out what is going on but I've got to admit that power management is one of the biggest, most complicated messes I've even seen in the world of computing.  If a person goes to launchpad and does a search with "suspend" you get hundreds of hits with more being added daily.

- Video support.  I have systems that have nVidia cards, ATI cards, integrated S3 and integrated Intel chipsets.  There are problems to one degree or another with all of these video solutions.  Enabling desktop effects magnifies these problems greatly.

- Networking support.  Wireless and Winmodem support is poor and troublesome.

My opinion is that the end user experience in each of these areas has deteriorated since Dapper.  It was Dapper that stuck around on one of my systems and convinced me to go with Ubuntu.  Had I started with Fiesty I most likely would not be here writing this message right now.  I've been using computers for many years and I compiled my first 2 Linux programs yesterday with gcc.  It will take me a while to get familiar with programming on this os but I'm willing to give it a go.  I'm also willing to try to help with one of more of the problem areas.  It isn't obvious who I should contact to offer my help.  If anyone knows please tell me.

---

### Post by BoyOfDestiny on 2007-05-13
> **Talon2 said:**
> My thoughts concerning Fiesty:

Fiesty is somewhat more annoying to use than were Dapper and Edgy.  There are 3 areas that I continue to have problems with:

- Power management.  Something happened in Fiesty.  Suspend and hibernate used to work reasonbly well on my systems prior to Fiesty.  Now it seems that I have one problem after another.  The really interesting thing is that often with no changes on my part power management will break, fix or change how it operates.  It is like power mangement has a mind of its own.  I have investigated the technical details in an attempt to try to figure out what is going on but I've got to admit that power management is one of the biggest, most complicated messes I've even seen in the world of computing.  If a person goes to launchpad and does a search with "suspend" you get hundreds of hits with more being added daily.

- Video support.  I have systems that have nVidia cards, ATI cards, integrated S3 and integrated Intel chipsets.  There are problems to one degree or another with all of these video solutions.  Enabling desktop effects magnifies these problems greatly.

- Networking support.  Wireless and Winmodem support is poor and troublesome.

My opinion is that the end user experience in each of these areas has deteriorated since Dapper.  It was Dapper that stuck around on one of my systems and convinced me to go with Ubuntu.  Had I started with Fiesty I most likely would not be here writing this message right now.  I've been using computers for many years and I compiled my first 2 Linux programs yesterday with gcc.  It will take me a while to get familiar with programming on this os but I'm willing to give it a go.  I'm also willing to try to help with one of more of the problem areas.  It isn't obvious who I should contact to offer my help.  If anyone knows please tell me.

Well, sorry to hear about the issues, but I'm glad you want to help.

[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

File bug reports and suggestions there. 
If things that used to work no longer do, these are known as regressions.

---

### Post by maniacmusician on 2007-05-13
In order, for your problems;

- It's not that power management support has gone down...just that some changes were made that affected your particular system negatively. It works fine for a lot of people. The best thing to do to get to the root of this problem is find the error messages relating to this problem and start a bug on launchpad.

- This is bound to happen. Video drivers from nVidia and ATI are in binary form, so it's impossible for devs to predict what will happen in every scenario since they dont have access to the code. The open source versions of these drivers are also not great, as they were created from incomplete specs and reverse engineering.  You shouldn't be having problems with Intel bugs though. Have you tried to get to the root of these problems by checking error logs? Video-related errors are usually in /var/log/Xorg.0.log

- A new, much improved version of NetworkManager was integrated into feisty. While it means better support for most people, performance might have degraded for you. As for Winmodems, I doubt that there will ever be good support for them. Especially since no one releases specs for them and they're also starting to become antiquated

---

### Post by aysiu on 2007-05-13
I've moved this to Testimonials and Experiences, seeing as how there's no reason to believe your experiences can be generalized beyond... your experience.

Just as a counter-example (my experience, which also cannot be generalized for everyone)--Feisty allowed me to have correct screen resolution and working suspend on my laptop when Dapper and Edgy didn't.

A lot of it depends on what hardware you have. As BoyofDestiny points out, your best course of action is to file a bug report.

---

### Post by Talon2 on 2007-05-13
> **aysiu said:**
> I've moved this to Testimonials and Experiences, seeing as how there's no reason to believe your experiences can be generalized beyond... your experience.

Just as a counter-example (my experience, which also cannot be generalized for everyone)--Feisty allowed me to have correct screen resolution and working suspend on my laptop when Dapper and Edgy didn't.

A lot of it depends on what hardware you have. As BoyofDestiny points out, your best course of action is to file a bug report.

I do NOT appreciate you moving this post.

I already have filed or added to related bugs as appropriate.  I have discussed the issues in the support forums.  I'm looking for a place to discuss the issues in a general way.  Just how important was it to move this post?!?

---

### Post by Talon2 on 2007-05-13
> **maniacmusician said:**
> In order, for your problems;

- It's not that power management support has gone down...just that some changes were made that affected your particular system negatively. It works fine for a lot of people. The best thing to do to get to the root of this problem is find the error messages relating to this problem and start a bug on launchpad.

- This is bound to happen. Video drivers from nVidia and ATI are in binary form, so it's impossible for devs to predict what will happen in every scenario since they dont have access to the code. The open source versions of these drivers are also not great, as they were created from incomplete specs and reverse engineering.  You shouldn't be having problems with Intel bugs though. Have you tried to get to the root of these problems by checking error logs? Video-related errors are usually in /var/log/Xorg.0.log

- A new, much improved version of NetworkManager was integrated into feisty. While it means better support for most people, performance might have degraded for you. As for Winmodems, I doubt that there will ever be good support for them. Especially since no one releases specs for them and they're also starting to become antiquated

MM, you reply is appreciated but you didn't tell me anything I didn't already know.  Here are my replies back in order of your answers:

- I'm not speaking about only one system.  I support 12 systems of various ages and configurations, only 2 of which are in my office.  I made the mistake of upgrading 10 to Fiesty.  Power management support has went downhill on ALL 10 systems.  Go take a look in lauchpad and tell me power management has not deteriorated in general.

- I do not use the binarys from ATI or nVidia.  Video is supported by open source drivers all the way around.  Yes, I am seeing poblems with Intel drivers, however, only when desktop effects is active so this could very well be problems related to Compiz.  All in all video support is very poor.

- I don't actually have any Winmodems.  That there is not even support for the Winmodems where binary drivers have been supplied by manufacturers makes it difficult for me to move folks to Ubuntu.  I fail to see why binaries are used for wireless networking and not for winmodem networking.  The majority of networking problems I have experienced seem to be related to power management.  Resuming does bring the nic back to life.

Have a good day.

---

