---
title: "10 Rocking Feature in 10 Days: AppArmor"
date: 2007-10-16
forum: The Fridge Discussions
---

### Post by TheFridge on 2007-10-16
If you are joining us now, here is a bit of a refresher: as we close in on the 7.10 (also known as Gutsy Gibbon) release, we are taking a look at the various cool features that we are going to get as part of this new Ubuntu. We have already looked at [Deskbar and Tracker]("http://fridge.ubuntu.com/node/1154"), [Bulletproof X and Graphical X configuration]("http://fridge.ubuntu.com/node/1156"), [sharing your computer with Fast User Switching]("http://fridge.ubuntu.com/node/1162"), [Desktop Effects with Compiz]("http://fridge.ubuntu.com/node/1157"), [ Better Firefox plugins and Gnash]("http://fridge.ubuntu.com/node/1169") and  [Better hardware support]("http://fridge.ubuntu.com/node/1173"). Today we turn to AppArmor, the application security framework. 
 **So what does AppArmor do?**
 AppArmor helps you keep your computer secure by restricting what certain applications can do. This means that if somebody discovers a new way to exploit protected software, AppArmor helps reduce the risk by limiting access to resources defined in the application profile.
 **So what sort of profiles are currently enabled in Gutsy**
 Currently 7.10 ships with the framework and all the application tools, although only CUPS (the printing tool) has a profile enforced by default. The plan for Ubuntu 8.04 (called Hardy Heron in it&#8217;s development cycle) is to have a larger set of profiles enabled.
 However, there is a beta profiles package in the universe component cunningly named *apparmor-profiles*. These profiles are in what is called &#8220;complain&#8221; mode, which warns the user that an application is doing something wrong without actually stopping it. The complain mode contrasts with the &#8220;enforce&#8221; mode, which does exactly that.
 **So how do I make an AppArmor profile?**
 If you are an end user or a sysadmin that wants to help out with the development of Ubuntu or AppArmor or merely needs to create a profile for an application they use, it is fairly easy. AppArmor builds in easy tools to profile applications and create profiles. A great tutorial to get started can be found on the [AppArmor page]("https://help.ubuntu.com/community/AppArmor") on the help wiki.
 **So will this break my system?**
 Nope! One of the key reasons this is being rolled across two releases (the framework in 7.10, the profiles in 8.04) is to eliminate such issues.
 **What if I screw with AppArmor and it goes boink?**
 Hey, there is an answer for that too. AppArmor builds in a cool little utility called *aa-logprof* to help fix AppAmor and get you a working system again. You can read more about aa-logprof on the [AppArmor page]("https://help.ubuntu.com/community/AppArmor") too.
 **Got any shiny pictures of AppArmor in action?**
 Nope. AppArmor is designed to be one of those silent things that you never notice. 
 If you want to read more about AppArmor, aside from the Ubuntu Help page, you can also try the OpenSuse page on [AppArmor]("http://en.opensuse.org/Apparmor")
 See you all tomorrow!
 

[More...](http://fridge.ubuntu.com/node/1175)

---

### Post by supaneko on 2008-12-15
So, did you ever get any screenshots for AppArmor in action or any further information about how to make use of it? :)

---

