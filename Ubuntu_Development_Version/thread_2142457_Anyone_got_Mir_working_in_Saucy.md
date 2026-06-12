---
title: "Anyone got Mir working in Saucy?"
date: 2013-05-05
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-05-05
Just reassigning  a thread to the new cycle as suggested.

 So far I have not seen the 'mir'  executable replaced.

---

### Post by ventrical on 2013-05-05
Anyone know if we have to re-assign the 'mir' ppa:  ?

---

### Post by grahammechanical on 2013-05-06
@ventrical

You have lead me into temptation. I have put in a fresh install of Saucy. But I am getting a "unable to locate package mir" error message. I am going to try changing the url of the PPA to Raring or even Quantal.

Edit: Changing the url of the PPA to either raring or quantal does not bring in MIR.

Edit 2: I am having better success install Ubuntu Touch core apps. There is a saucy ppa for them. If only I can remember how to install each app. Ah, it is

```
sudo apt-get install ubuntu-nameofapp-app
```

for example

```
sudo apt-get install ubuntu-clock-app
```

It now has a nice clock icon but I think we still need to install the sdk in order to get the app to launch. The SDK brings in necessar libraries.

Edit: Yes, we do need the SDK installed. Then the core app will launch. The stopwatch funchtion of the clock is now working.

Regards.

---

### Post by ventrical on 2013-05-06
> **grahammechanical said:**
> @ventrical

You have lead me into temptation. I have put in a fresh install of Saucy. But I am getting a "unable to locate package mir" error message. I am going to try changing the url of the PPA to Raring or even Quantal.

Edit: Changing the url of the PPA to either raring or quantal does not bring in MIR.

Regards.

Uh??  My ppas were already set to mir/raring/.  Did you actually set your mir ppas to /saucy/?

because thats news to me.

---

### Post by grahammechanical on 2013-05-06
```
sudo add-apt-repository
```

will automaticially set them to saucy. That is what I tried.

Regards

---

### Post by ventrical on 2013-05-06
> **grahammechanical said:**
> @ventrical

You have lead me into temptation. I have put in a fresh install of Saucy. But I am getting a "unable to locate package mir" error message. I am going to try changing the url of the PPA to Raring or even Quantal.

Edit: Changing the url of the PPA to either raring or quantal does not bring in MIR.

Edit 2: I am having better success install Ubuntu Touch core apps. There is a saucy ppa for them. If only I can remember how to install each app. Ah, it is

```
sudo apt-get install ubuntu-nameofapp-app
```

for example

```
sudo apt-get install ubuntu-clock-app
```

It now has a nice clock icon but I think we still need to install the sdk in order to get the app to launch. The SDK brings in necessar libraries.

Regards.

 I got the calculator and the calendar apps working  without any re-configure. Looks like 'mir' has gone south or is in scramble mode. Most likely a reconfiguration of the ppa I assume.

  I'll try your :

sudo apt-add-repository

---

### Post by ventrical on 2013-05-06
> **grahammechanical said:**
> ```
sudo add-apt-repository
```

will automaticially set them to saucy. That is what I tried.

Regards

```


ventrical@ventrical-AcerAMD64bitDual:~$ sudo add-apt-repository
[sudo] password for ventrical: 
Error: need a repository as argument
ventrical@ventrical-AcerAMD64bitDual:~$ 



```

---

### Post by grahammechanical on 2013-05-06
Yeah, it is ppa:blah, blah.

```
sudo aad-apt-repository ppa:mir-team/staging
```

That will give it a repository belonging to whatever version of Ubuntu the command is being run on. ruantal main; raring main; saucy main. 

Regards

---

### Post by ventrical on 2013-05-06
I installed it on another install that did not have 'mir' ppa.  The ppa installed ok:

Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en_CA                      


but there is absolutely nothing there. Nothing got downloaded in terminal or synaptic.

Reboot?

 of course.

 Let's try . :)

oh .. btw .. I have btrfs on this install.  Whew !

The fun starts :)

EDIT:

nothing after reboot either.

---

### Post by ventrical on 2013-05-06
Looks like mir has gone south for  the time being:

 This means that even if you load the ppa in saucy, the ppa will install successfully but none of the mir components will unless you use synaptic, but there are conflicts with 'mir' executable and libmirserver0.

---

### Post by cecilpierce on 2013-05-08
I tried it with saucy and raring, no luck at all, says broken packages, solved that and still would not go ???

I have had better luck with wayland, its working pretty good, they are working on a login manager.

---

### Post by ventrical on 2013-05-08
If you try to install  the recently removed 'mir' executable it will remove the libmirserver0 which makes no sense at all.  I have no control over what is happening with the ppa but I am sure that this could be a transitional phase to saucy.

I'm sure wayland will be successful to which ever length it will go but I really don't have the time to fiddle with it.

---

### Post by cecilpierce on 2013-05-08
I guess we'll have to wait and see what happens down the road with all this mess...:P

All I have is time (retired) and watching TV (Leave it to Beaver on now haha) and bike riding at the beach.

---

### Post by ventrical on 2013-05-08
Meh?  Work.. loads of it..   one of my jobs .. ground crew...

Meh as ground crew.

[http://www.youtube.com/watch?v=2K2wIRGg8pU&feature=youtu.be](http://www.youtube.com/watch?v=2K2wIRGg8pU&feature=youtu.be)

---

### Post by cecilpierce on 2013-05-08
> **ventrical said:**
> Meh?  Work.. loads of it..   one of my jobs .. ground crew...

Meh as ground crew.

[http://www.youtube.com/watch?v=2K2wIRGg8pU&feature=youtu.be](http://www.youtube.com/watch?v=2K2wIRGg8pU&feature=youtu.be)

Nice! Better get that door fixed though before he falls out at 10,000.

Didn't see any mir vid's ?
 Thanks

---

### Post by ventrical on 2013-05-08
> **cecilpierce said:**
> Nice! Better get that door fixed though before he falls out at 10,000.

Didn't see any mir vid's ?
 Thanks


hehe ... thats the thing .. I was so busy this winter I couldn't  get to fixing the door.

 I  will be having a little time coming up where I will be looking into the 'mir' problem. I've see some of the vid demos.  I assume now it works still on raring but nothing with saucy.  I think this one needs time.

My apologies for being way off topic here...

---

### Post by cecilpierce on 2013-05-08
I'll be looking forward to trying it in saucy if it ever gets there and you figure out how to get it up and running.

):P

---

### Post by anca-emanuel on 2013-05-09
[http://irclogs.ubuntu.com/2013/05/08/%23ubuntu-mir.html](http://irclogs.ubuntu.com/2013/05/08/%23ubuntu-mir.html)
> [COLOR=#000000][23:06] <RAOF> thomi: Could we please turn on Saucy builds in the PPA?
[/COLOR][COLOR=#000000][23:07] <thomi> RAOF: yeah, I'm surpised they're not on already. will check now
[/COLOR][COLOR=#000000][23:07] <RAOF> Ahem. Or maybe I could actually add the PPA back after blowing away my install.[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#4D4D93][FONT=Times New Roman]
[/FONT][/COLOR]

---

### Post by dino99 on 2013-05-09
mir was a marketing attack for scarying xorg/wayland/gnome peoples

so waiting for them doing the job (mainly)

---

### Post by anca-emanuel on 2013-05-09
> **dino99 said:**
> mir was a marketing attack for scarying xorg/wayland/gnome peoples
so waiting for them doing the job (mainly)

Hmm interesting...

In the meantime: [http://theravingrick.blogspot.ro/2013/05/woof-woof.html](http://theravingrick.blogspot.ro/2013/05/woof-woof.html)
[http://www.iloveubuntu.net/ubuntu-touch-developers-announced-successful-first-run-unity-top-mir](http://www.iloveubuntu.net/ubuntu-touch-developers-announced-successful-first-run-unity-top-mir)

---

### Post by DisappearingOak on 2013-05-09
Well, Canonical is running a business... they have the right to do things their way and that may mean breaking some perceived obligations to the wayland developers, after all. Business is business. I think the worry stems mostly from the fact that wayland would lose proprietary driver support and fall off, but I think it will probably work out seeing people saying that the proprietary drivers will be egl-based (whatever that is) and will probably work for both wayland and mir. No use with the hate posts now. I think Canonical will still 'support' Wayland in their official distro line-up, if they intend to keep KDE and GNOME, which I think they will. In the end, it's free software, and competition is healthy and drives innovation, or so they say, or used to say a year ago when I started using Linux. 

As far as I understand, Mir is a modern type of X made from scratch, it acts as a mediator which draws stuff for it's clients/compositors i.e., it's still a display server, and Wayland is a new pardigm, it is not a server, it's a protocol that enables clients/compositors to become their own server and draw stuff themselves, interfacing directly with the display hardware. What benefits one has over the other, I do not know but they both claim to provide faster graphics with less latency than X which is apparently bloated. in the end, I think people will use whatever works out the best..

---

### Post by rrnbtter on 2013-05-10
Greetings,
> **anca-emanuel said:**
> Hmm interesting...
In the meantime: [http://theravingrick.blogspot.ro/2013/05/woof-woof.html](http://theravingrick.blogspot.ro/2013/05/woof-woof.html)
[http://www.iloveubuntu.net/ubuntu-touch-developers-announced-successful-first-run-unity-top-mir](http://www.iloveubuntu.net/ubuntu-touch-developers-announced-successful-first-run-unity-top-mir)

It's interesting that the above link shows small screen devices as the target for mir's trial run.  I've noticed a great deal of support taking place in the RC Kernels change logs and also in the upstream links for small screen touch devices. It possible that they have it working in that genre so desktop support shouldn't be that far away. I think the problem may be that small screen support is directed at specific devices whereas desktop has to support an endless array of architecture.

---

### Post by ventrical on 2013-05-10
> **rrnbtter said:**
> Greetings,


It's interesting that the above link shows small screen devices as the target for mir's trial run.  I've noticed a great deal of support taking place in the RC Kernels change logs and also in the upstream links for small screen touch devices. It possible that they have it working in that genre so desktop support shouldn't be that far away. I think the problem may be that small screen support is directed at specific devices whereas desktop has to support an endless array of architecture.



That's a fair analogy.  So far, nothing in saucy except for 1 file as of yesterday.

---

### Post by Chanath on 2013-05-12
I tried to look at Mir in Raring, but not succeeded. 
What I gathered at Mir wiki was this;
> **Running Mir natively**

 You can also run Mir natively. To do so, log in to VT1 (Ctrl+Alt+F1) *after*  you are already logged in to X. If you do so before then you will not  be assigned adequate credentials to access the graphics hardware and  will get strange errors.
 VT switching away from Mir will only work if Mir is run as root. In  this case we need to change the permissions to the Mir socket so that  clients can connect: 
 
$ sudo mir_demo_server 
<Ctrl+Alt+F2> - log in to VT 2 
$ sudo chmod 777 /tmp/mir_socket 
$ some-mir-client 
<Ctrl+Alt+F1> - switch back to Mir. Watch your friends be amazed! 

What is actually some-mir-client?
There is no command "some."
Or should the last line be something else?

The link; [http://unity.ubuntu.com/mir/using_mir_on_pc.html](http://unity.ubuntu.com/mir/using_mir_on_pc.html)

---

### Post by serdotlinecho on 2013-05-12
[Mir & Unity 8]("https://lists.ubuntu.com/archives/ubuntu-devel/2013-May/037083.html")

---

### Post by Chanath on 2013-05-12
Tried Mir with saucy too, but it gets stuck. There is no way to minimize a window. Firefox can be used but cannot make it smaller or delete it. I used /usr/share/applications to run Firefox. Then it got stuck. The information was taken from [http://unity.ubuntu.com/mir/using_mir_on_pc.html](http://unity.ubuntu.com/mir/using_mir_on_pc.html) I used the method with X. There was no menu, or panel, or icons. In the 2nd method, I only got a large arrow, nothing else. There was no command called some-mir-client. Does anyone know what that is?

---

### Post by grahammechanical on 2013-05-12
@Chanath

Did you see this on that page you linked to? > [h=2][SIZE=2]Getting some example client applications[/SIZE][/h][COLOR=#000000][FONT=Roboto]If you installed Mir using the packages from the mir-team staging PPA, you can get some example programs by installing the [/FONT][/COLOR]mir-demos[COLOR=#000000][FONT=Roboto] package:
[/FONT][/COLOR]
```
sudo apt-get install mir-demos
```

[COLOR=#000000][FONT=Roboto]If you are building from source you can find client applications in the bin/ subdirectory of the build directory.[/FONT][/COLOR]

Regards.

---

### Post by anca-emanuel on 2013-05-15
[https://lists.ubuntu.com/archives/ubuntu-devel/2013-May/037117.html](https://lists.ubuntu.com/archives/ubuntu-devel/2013-May/037117.html)

Yes that is unity 8 (next).
Demo: [http://youtu.be/E9AzRxsnfTE](http://youtu.be/E9AzRxsnfTE)


[https://lists.ubuntu.com/archives/ubuntu-devel/2013-May/037119.html](https://lists.ubuntu.com/archives/ubuntu-devel/2013-May/037119.html)
> [COLOR=#000000]I hope that we'll get that before end of month.[/COLOR]

---

### Post by EgoGratis on 2013-05-16
It looks like we will get something to play with in this dev cycle:

[http://www.phoronix.com/scan.php?page=news_item&px=MTM3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTM3MzY)

---

### Post by ventrical on 2013-05-16
> **EgoGratis said:**
> It looks like we will get something to play with in this dev cycle:

[http://www.phoronix.com/scan.php?page=news_item&px=MTM3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTM3MzY)



Ok .. great ... but what happened to the 'mir' executable and other files that we signed up for in raring (and now report being broken in saucy)? I guess I just get annoyed at the fact that I have a benign ppa sitting on  some of my installs after going through the work and the risk to  experiment with that server.  I know .... I can remove the  ppa .. etc... but my point is  that  (and it may be too soon to assume this)  it appears that 'mir' is going the way of Wayland ...  so all this sleep time is downtime for me.

 Ok .. rant over. :) 

thanks..

---

### Post by cecilpierce on 2013-05-16
It don't look good does it ?

---

### Post by ventrical on 2013-05-16
> **cecilpierce said:**
> It don't look good does it ?



  I had to go do my other 'daily build across a single platform' :) 

Disclaimer: Video may be very boring . It is  a perspective from a mop-head. (me working  my  uh.... marbles off ) :) Now that's  done I'll have more time for  psudeo-mir ! :) Oh joy! :)

[http://www.youtube.com/watch?v=cXUx1l3ynjc&feature=youtu.be](http://www.youtube.com/watch?v=cXUx1l3ynjc&feature=youtu.be)

---

### Post by grahammechanical on 2013-05-16
I just watched a UDS session on Unity 8 desktop for 13.10. A much better discussion than the last session I attended. They mentioned the need for MIR PPAs to be set up for Saucy and the need to get the MIR code and the Unity 8 code into the Saucy repos. It looks like Universe repo. As we have already found out the apps will be there but they will be mainly fake apps. It is intended to use lightdm in some way to give the option at login to stay with Unity 7 or to switch to MIR and Unity 8. It is doubtful if this stuff will be part of the Saucy release ISO. More likely it will be something to install through app-get after installation for those who want to run what is just a MIR/Unity 8 preview.

Regards

---

### Post by ventrical on 2013-05-16
> **grahammechanical said:**
> I just watched a UDS session on Unity 8 desktop for 13.10. A much better discussion than the last session I attended. They mentioned the need for MIR PPAs to be set up for Saucy and the need to get the MIR code and the Unity 8 code into the Saucy repos. It looks like Universe repo. As we have already found out the apps will be there but they will be mainly fake apps. It is intended to use lightdm in some way to give the option at login to stay with Unity 7 or to switch to MIR and Unity 8. It is doubtful if this stuff will be part of the Saucy release ISO. More likely it will be something to install through app-get after installation for those who want to run what is just a MIR/Unity 8 preview.

Regards


  I can see the need to hone in their resources and focus on tablets and phones. Win8 (which Mir Demos emulate  to a near exactitude) really has the jump  on Ubuntu.  Perhaps patience is the order of the day on this chapter of the Mir server.

---

### Post by grahammechanical on 2013-05-16
> [COLOR=#000000]Win8 (which Mir Demos emulate to a near exactitude) really has the jump on Ubuntu.[/COLOR]

Wash your mouth out! :) :)

But can it run the same platform on PC, phone; tablet & TV? If the devs can pull that one off by 14.04, then that will be something. They are certainly going for it. I think that by the TT cycle we will have a good idea about it working. I certainly like the idea of sticking a cell/mobile phone in a dock that is connected to a TV/monitor and having a desktop OS on screen that can also do the work of a mobile phone simply by holding down the left mouse button and swiping the pointer from the left side of the screen.

From the talk at UDS some of those core apps may end up a desktop apps. The community developed calendar looks like it will get approval for inclusion in Unity Touch and it may end up as a desktop calendar.

---

### Post by EgoGratis on 2013-05-16
> **ventrical said:**
> Ok .. great ... but what happened to the 'mir' executable and other files that we signed up for in raring (and now report being broken in saucy)? I guess I just get annoyed at the fact that I have a benign ppa sitting on  some of my installs after going through the work and the risk to  experiment with that server.  I know .... I can remove the  ppa .. etc... but my point is  that  (and it may be too soon to assume this)  it appears that 'mir' is going the way of Wayland ...  so all this sleep time is downtime for me.

 Ok .. rant over. :) 

thanks..

Probably devs are to busy to care ATM but if the plan is to offer experimental desktop session in Ubuntu 13.10 probably we will get something rather sooner then later... But look at it this way it will do (much)  more than it did in the raring dev cycle if it will really be workable GUI session i imagine working on FOSS graphic drivers. Demos on Mac and mobile device from few days back do show development is going on in fast pace and i do imagine "current snapshot" will be shared soon.

---

### Post by ventrical on 2013-05-16
> **grahammechanical said:**
> Wash your mouth out! :) :)

But can it run the same platform on PC, phone; tablet & TV? If the devs can pull that one off by 14.04, then that will be something. They are certainly going for it. I think that by the TT cycle we will have a good idea about it working. I certainly like the idea of sticking a cell/mobile phone in a dock that is connected to a TV/monitor and having a desktop OS on screen that can also do the work of a mobile phone simply by holding down the left mouse button and swiping the pointer from the left side of the screen.

From the talk at UDS some of those core apps may end up a desktop apps. The community developed calendar looks like it will get approval for inclusion in Unity Touch and it may end up as a desktop calendar.


It's only a matter of time when  reflective contact lenses can be used to shutter icons, characters and other commands via a virtual goggles interface (ordinary LCD reading glasses)[in fact I have been experimenting with this concept for years now]. With a look and a blink, all the commands can be executed. Just wear a pendant with all the required hardware and power supply, turn out the lights and dream your way onto the internet. Way things are going , Mir just might be an after thought.

  In the meantime .. I have pumice soap and will wash my proverbial mouth out with it  and just roll with what we have today. :)

---

### Post by EgoGratis on 2013-05-16
> [h=3][FONT=Arial]Unity 8 in 13.10[/FONT][/h] [FONT=Arial]While 13.10 is  very very focused on Ubunty Touch for phones, we all know that the real  prize is the fully converged client OS. With that in mind, I think it's  important to get the code up on as many device types as possible as soon  as possible. There was a rich discussion about the steps to offer Unity  8 on top of Mir as an option in 13.10. Now, keep in mind that the  result will only be the Phone UI on the desktop, and the default will be  the Unity that we know and love today (with Smart Scopes and other  enhancements of course!). Still in all, I am betting that basing Unity 8  on QML means that it will be surprisingly functional on a desktop even  though it won't have any real desktop support in terms of things like  workspace switching, etc..[/FONT]


[http://theravingrick.blogspot.com/2013/05/feel-like-friday-post-vuds.html](http://theravingrick.blogspot.com/2013/05/feel-like-friday-post-vuds.html)

---

### Post by ventrical on 2013-05-16
> **EgoGratis said:**
> Probably devs are to busy to care ATM but if the plan is to offer experimental desktop session in Ubuntu 13.10 probably we will get something rather sooner then later... But look at it this way it will do (much)  more than it did in the raring dev cycle if it will really be workable GUI session i imagine working on FOSS graphic drivers. Demos on Mac and mobile device from few days back do show development is going on in fast pace and I do imagine "current snapshot" will be shared soon.

 I do not mean to be unfair in my comments about Mir. Perhaps it is a larger undertaking than originally proposed and just satisfying basic depends is a mountain in and of itself. It may be hardware exclusive meaning that I may have to spend more money to upgrade my equipment but , rather than assume the worse, I'll just wait it out like everyone else.  Ubuntu has always only developed to become better after all.

---

### Post by EgoGratis on 2013-05-16
Yes to develop good display server is a large undertaking by any means and convergence nature of it should prevent hardware exclusiveness. And then there is Unity 8 and not just Mir display server. Unity 8 isn't just slightly modified Unity 7... All this has to fall together then we will be able to test it until then some "virtual terminal tech demos" are it.

---

### Post by EgoGratis on 2013-05-16
But yes i do agree instead of posting videos running Unity 8 on Mir on Mac (and wearing KDE shirt) PPA would be better for us in Ubuntu +1 section. Or better to bring in that Unity 8 session for us to test it by default.

It's not done yet we all know that but that is exactly the reason why we are here... in Ubuntu +1 section.

---

