---
title: "Ubuntu and Eye Candy...a question/solution"
date: 2005-12-25
forum: The Cafe
---

### Post by varunus on 2005-12-25
Many people have read poofyhairguy's Composite Manager howto over in the Tips and Tricks section of the forums.  Unfortunately, only those with NVIDIA cards or old Radeons can really enjoy the full benefits of compositing.

EXA is a proposed solution to this problem; it will implement XRender acceleration for many cards.  However, it is very difficult to track the development of EXA.  I have not seen any changes in any drivers aside from the Radeon ones over the past few months; the status page has not really been updated either.  I suppose this is due to work being focused on modularizing X.  I hope we'll see some development soon.

However, upon doing a little research, I took a look at a library we've probably all heard of: glitz.  This library implements everything that the XRender library does, but it uses OpenGL to do it!  I believe that the Xglx package in dapper is based off of glitz (or at least I've heard it somewhere); and frankly, if it were not for the graphical issues with using Xglx, I'd switch to it right now.  It lets me composite on my Intel 855GM graphics card, and get all the eye candy I'd ever want.  The only issue is the graphical problems associated with alpha software and the complete X rewrite it provides.  Also, rebuilding X from the ground up is a long term process; linux needs a short term fix, which appears to be EXA.

However, I took a look at the xcompmgr source code and compared it with the glitz and XRender libraries, and it seems that xcompmgr could theoretically be rewritten to use glitz instead of XRender!  This would have the immediate benefit of everyone who has an OpenGL capable card being able to composite!

My question is this; has anyone thought of this before?  Are there some implementation problems with it?  I am fairly inexperienced in X programming; I know C and C++, but have never programmed X before.

Does anyone on the forums know if this has been done before or thought about before?  Switching xcompmgr to glitz could have many short term benefits for linux eye candy in general...

---

### Post by poofyhairguy on 2005-12-25
[QUOTE=varunus]Many people have read poofyhairguy's Composite Manager howto over in the Tips and Tricks section of the forums. Unfortunately, only those with NVIDIA cards or old Radeons can really enjoy the full benefits of compositing. EXA is a proposed solution to this problem; it will implement XRender acceleration for many cards. However, it is very difficult to track the development of EXA. I have not seen any changes in any drivers aside from the Radeon ones over the past few months; the status page has not really been updated either. I suppose this is due to work being focused on modularizing X. I hope we'll see some development soon. However, upon doing a little research, I took a look at a library we've probably all heard of: glitz. This library implements everything that the XRender library does, but it uses OpenGL to do it! I believe that the Xglx package in dapper is based off of glitz (or at least I've heard it somewhere); and frankly, if it were not for the graphical issues with using Xglx, I'd switch to it right now. It lets me composite on my Intel 855GM graphics card, and get all the eye candy I'd ever want. The only issue is the graphical problems associated with alpha software and the complete X rewrite it provides. Also, rebuilding X from the ground up is a long term process; linux needs a short term fix, which appears to be EXA. However, I took a look at the xcompmgr source code and compared it with the glitz and XRender libraries, and it seems that xcompmgr could theoretically be rewritten to use glitz instead of XRender! This would have the immediate benefit of everyone who has an OpenGL capable card being able to composite! My question is this; has anyone thought of this before? Are there some implementation problems with it? I am fairly inexperienced in X programming; I know C and C++, but have never programmed X before. Does anyone on the forums know if this has been done before or thought about before? Switching xcompmgr to glitz could have many short term benefits for linux eye candy in general...[/QUOTE] What you are trying to do has never exactly been done before (well...it has I just can't find the source code), but something was close that I can find the code for. Luminocity. It does what you would hack Xcompmgr to do in theory- its a window manager with a compositor that uses OpenGl to get its effects. Its a neat little toy (I put a guide how to install it in the wiki but I never tried with Breezy) but its not really usuable and it never meant to be. Honestly hacking up Xcompmgr might not be the best idea. It has a memory leak and it has been surpased by other compositors such as the one in Kwin. But the concept is good. If you really want to help you could (my suggestion): 

1. Help test and hammer on the EXA for Intel cards. I know many EXA developers use those cards because their specs are open. Getting that to work would help more people, because I can promise you now major distro wants anything to do with Xcompmgr and any forks of its nature. EXA might get turned on by default in a big distro one day though. 

2. Help make the MESA drivers better. Thats the way to help out the Xgl and make your card better. 

3. Help test and develop the new compositor in Metacity. Since that will be shipped one day if you could help get it working using some of the Luminocity then lots could benefit (not eye candy geeks lol). And many more ways. I suggest just using Xcompmgr as a test subject though- thats all it was meant to be. As I wrote about it my eye candy blog, it seems that it was a tech demo that is out of time. 

Great idea though, and good conversation. Glad to see people getting into this stuff- part of the plan of the newest Xorg release is to get people excited about such things again. 

Here is best link on topic: 

[http://www.gnome.org/~seth/blog/relations](http://www.gnome.org/~seth/blog/relations) 

And if you can find it, apparently a glxcompmgr exists that is what you want already:

 [http://www.burtonini.com/blog/2005/Jun/07](http://www.burtonini.com/blog/2005/Jun/07)

---

