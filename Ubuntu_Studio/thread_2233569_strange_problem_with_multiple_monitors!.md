---
title: "strange problem with multiple monitors!"
date: 2014-07-09
forum: Ubuntu Studio
---

### Post by anonymous0programmer on 2014-07-09
I have had a few problems with multiple monitors in the past but nothing like this.
When I plug in my HDTV through hdmi and I set it as my laptop monitor to the right of the TV both monitors go blank. Then I unplug the cable and the laptop monitor shows the ubuntu studio Loading screen "Linux for creative Humans" without the spinning animation. And it just stays like that. I tried restarting xorg at the time and it just goes black. After this happened I got a problem with logging into my account. I type in my pass and click login and the screen goes black as though it were loading the session but then it goes back to the login screen. 

I fear this may be because I switched to the proprietary drivers. I have an nvidia GEFORCE 310M laptop card. I have had problems with it before because it is one of the less supported cards. I hate nvidia lol. 

I am going to try a few things and will update the post if I find anything peculiar.

*update*
well it seems when I try to do it with the guest account it works so that tells me it has to do with user settings.... oops lol

*update* 
I tried logging into my account from a terminal and it logged in but not from the display manager. I assume this has to do with the nvidia card and the user settings entirely. What now?

---

### Post by brianmc on 2014-07-11
You say you can log into your account with a terminal?

Once in there, use **sudo useradd** to create a fresh user account to play with. If you can get that working to your satisfaction, copy over the various settings files. It may-well be that you can quickly clear issues with your own account by renaming ~/.Xdefaults out the way before trying a graphical login.

---

