---
title: "Testing Ubuntu Desktop Next live session - password"
date: 2014-10-14
forum: Ubuntu Development Version
---

### Post by grahammechanical on 2014-10-14
Found the answer on this blog

[http://mhall119.com/2014/10/unity-8-desktop/](http://mhall119.com/2014/10/unity-8-desktop/)

> [COLOR=#333333][FONT=Georgia]The easiest way to try out the Unity 8 Desktop Preview is to use the daily Ubuntu Desktop Next live image:   [http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/)   This will allow you to boot into a Unity 8 session without touching your current installation.  An easy 10 step way to write this image to a USB stick is:[/FONT][/COLOR]
> 
[LIST=1]
[*]Download the ISO
[*]Insert your USB stick in the knowledge that it’s going to get wiped
[*]Open the “Disks” application
[*]Choose your USB stick and click on the cog icon on the righthand side
[*]Choose “Restore Disk Image”
[*]Browse to and select the ISO you downloaded in #1
[*]Click “Start restoring”
[*]Wait
[*]Boot and select “Try Ubuntu….”
[*]Done *
[/LIST]
> [COLOR=#333333][FONT=Georgia]* Please note – there is currently a bug affecting the Unity 8 greeter which means you are not automatically logged in when you boot the live image.  To log in you need to:

[LIST=1]
[*]Switch to vt1 (ctrl-alt-f1)
[*]type “passwd” and press enter
[*]press enter again to set the current password to blank
[*]enter a new password twice
[*]Check that the password has been successfully changed
[*]Switch back to vt7 (ctrl-alt-f7)
[*]Enter the new password to login
[/LIST]
[/FONT][/COLOR]


Regards.

---

### Post by ventrical on 2014-10-15
Nice find. 3:00am here and trying this now. I didn't know we could do this without SDC.

---

### Post by Elfy on 2014-10-15
blog post misses known issues - [https://wiki.ubuntu.com/Unity8DesktopIso](https://wiki.ubuntu.com/Unity8DesktopIso)

---

### Post by ventrical on 2014-10-15
Thanks elfy.

---

### Post by grahammechanical on 2014-10-15
One of my known issues for the installed Desktop Next is that pressing Shift just once will put the keyboard permanently into Caps Lock mode and that means it is impossible to type a numeric character or a full stop. I will test to see if it applies to the live session.

Regards.

---

### Post by Elfy on 2014-10-15
> **grahammechanical said:**
> One of my known issues for the installed Desktop Next is that pressing Shift just once will put the keyboard permanently into Caps Lock mode and that means it is impossible to type a numeric character or a full stop. I will test to see if it applies to the live session.

Regards.

Given that could play havoc - perhaps add the bug to the wiki , if it's not just a local issue to you and not reproducible

---

### Post by ventrical on 2014-10-15
Just  absolutely awesome .. writing to you from the *live* session on nVidia GeForce 220/218. There are a couple of verbose bug messages at startup but it irons itself out. I had to click <skip intro> when it asked me to swipe from the top edge and then I was in . This is an older Core 2 Duo and It is faster than unity7. Just give it time to boot into live session (less that a minute).Regards.

---

### Post by ventrical on 2014-10-15
This:
> 

[LIST=1]
[*]Download the ISO
[*]Insert your USB stick in the knowledge that it’s going to get wiped
[*]Open the “Disks” application
[*]Choose your USB stick and click on the cog icon on the righthand side
[*]Choose “Restore Disk Image”
[*]Browse to and select the ISO you downloaded in #1
[*]Click “Start restoring”
[*]Wait
[*]Boot and select “Try Ubuntu….”
[*]Done *
[/LIST]




 worked.

 So who needs SDC anymore?

---

### Post by ventrical on 2014-10-15
It kind of goes berserk if you try to install an app. After SSO login it's starts to do some flikerty fancy Mir stuff , I assume. I am going to hard install on my ATi HD 5450 silent and see what happens.

I am happy to see it actually working again.  After all the other installs went to fail (no show mouse) it seems like it is onwards and upward with unity8 testing.

 Instead of getting just a few bisquits during Utopic cycle .. it looks as if the devs are about to throw us a rack of ribs .:)lol

Regards

---

### Post by ventrical on 2014-10-15
Total fail with ATi graphics but  fair success on a nVidia hdd install. Was able to install apps and even get them working.

---

### Post by grahammechanical on 2014-10-15
I have just been listening to yesterday's Ubuntu On Air Ubuntu Community Q&A. It was mentioned that AMD is standardizing on an open source foundation layer with both open source and proprietary drivers built on top of it that will support both Wayland and Mir. It was also said that Nvidia are to support Wayland and Mir as well as Xserver. This was in response to a question asking if there would be more focus on graphic drivers. It is very near the end of the session. About 58 minutes in.

I can get into Desktop Next with my GT220 using Nvidia drivers not using Nouveau.

Regards.

---

### Post by Chanath on 2014-10-15
Would this be a desktop version? It is somewhat funny to consider a laptop as a phone. I am writing from Ubuntu Next. One cannot shut off the laptop or reboot.

---

### Post by grahammechanical on 2014-10-15
Yes, it is an ISO image for installing on to a desktop/laptop machine. At the present time it is still the Ubuntu for Devices user interface. But it is the branch where convergence is being worked on.  I am using the ubuntu-desktop-next image of 15th October. I am running a live session. There is a Intro feature that does not work too well. With this image I got past the instruction to swipe from the right edge but got no further when I tried to swipe from the top as next instructed. I am posting this from Browser. I was able to activate my Ubuntu One sign one. The issue I had with the Shift key putting the keyboard into permanent Caps Lock mode does not exist in the live session. Perhaps that is because the live session uses the US keyboard and on my installed versions I was using a UK keyboard. This is all one paragraph because Browser is not accepting my Enter key as a Return key. Cannot create a pargraph.

---

### Post by ventrical on 2014-10-15
> **grahammechanical said:**
> This is all one paragraph because Browser is not accepting my Enter key as a Return key. Cannot create a pargraph.

+1 .. both live and hdd install.

---

### Post by ventrical on 2014-10-15
> **Chanath said:**
> Would this be a desktop version? It is somewhat funny to consider a laptop as a phone. I am writing from Ubuntu Next. One cannot shut off the laptop or reboot.


On the hdd install you can eventually log off and if you wait, it will roll back to lightdm/unity greeter logon and you can shut down from there. It behaves like a shell within a shell.

Regards..

---

### Post by grahammechanical on 2014-10-15
> if you wait That is my problem. Impatient. Using a US keyboard layout avoids the problem with the shift key in the UK layout. But here is a strange thing. The live session uses an open source video driver and it runs on my Nvidia card. But the install needs the Nvidia driver to get beyond the lightdm login screen.

---

### Post by ventrical on 2014-10-16
We practically have the same nVidia cards and I am using nouveau.. so .. beats me.

Regards..

---

### Post by Chanath on 2014-10-16
I am not sure, whether to install it or not. I like new things, but this "desktop" looks pretty childish. I am not sure, it would be good as the existing desktop.

---

### Post by ventrical on 2014-10-16
> **Chanath said:**
> I am not sure, whether to install it or not. I like new things, but this "desktop" looks pretty childish. I am not sure, it would be good as the existing desktop.


Your right. But I doubt they will be letting go of conventional unity any time in the near future. The point is that  the computer market is very fluid and dynamic atm.  To compete, Canonical has to be on the edge of what's trending. iPad etc.. has been trending for some time now. All the schools where I live (In Canada) have iPods, slates or slabs of some sort. So today's youth are being educated  on 'touch', not keyboards. Current Canonical Think Tanks are trying to roll out a convergence where older legacy towers, current desktop form factors and slates are all gathered under one tent .  10 years from now Unity will probably morph into Harmony  Desktop so we are testing now for what may be the ubuntu-framework of tomorrow.

---

### Post by grahammechanical on 2014-10-16
Ubuntu for devices is built on Uptopic desktop code. Ubuntu Desktop Next is the Ubuntu for devices code modified to run on a desktop. That was the first step, as I see it. And it required X and lightdm to get that far.

 Now the developers need to bring the usual Ubuntu desktop UI out from behind the mobile UI. That is not so easy. I think. The usual desktop apps will need to run on Mir and Unity 8. Some may need to run on Xmir. There will be image updates and not the package updates using apt-get. Lots of other ideas that are standard in Ubuntu for devices will be tried out. The plan is

14.04 = Unity 7 default + Unity 8 option
14.10 = Unity 7 default + Unity 8 new revision option
15.04 = Unity 7 default + Unity 8 new revision option
15.10 = Potentially Unity 8 default + Unity 7 option
16.04 = Unity 8 default + Unity 7 option.

It is a long road to travel in not that long a length of time. Get ready for the bumps.

Regards.

---

### Post by ventrical on 2014-10-16
> **grahammechanical said:**
> There will be image updates and not the package updates using apt-get. 

That's not a bump. That's a crater. !

Scary stuff..

---

### Post by grahammechanical on 2014-10-17
I have installed the Desktop Next daily for 16th. It works with Nouveau. I conclude that phased updates are causing installed development releases to be out of phase with the daily images. The install version that I replaced still had kernel 3.16.0-6. Whereas, the new install had kernel 3.16.0-22. I did run dist-upgrade before junking the install. I got one package with unmet dependencies. That will happen sometimes with dist-upgrade.

Regards.

---

