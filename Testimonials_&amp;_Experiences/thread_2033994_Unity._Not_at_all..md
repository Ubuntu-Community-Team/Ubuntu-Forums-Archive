---
title: "Unity. Not at all."
date: 2012-07-27
forum: Testimonials &amp; Experiences
---

### Post by Kreacher on 2012-07-27
Unity in 12.04 LTS

Where are all my menu items that were so convenient to get to with Gnome? 

No, I do not want to search the Dash Home or all over the place to find the apps and programs that were in my Gnome menu. They should be in the Unity menu, or whatever it is called, by default. Why should I have to search and add them there? 

Why does chat crash constantly when it worked perfectly in 10.04? I try to pull up a chat and the chat window opens then closes. Yes, it worked fine before the upgrade.

On boot, my screen goes white with vertical lines and symbols. Nothing readable. Same when I shut down. 

Can't auto login anymore. That doesn't seem to be available. At least that I can find. Get a sound when Ubuntu finally gets to the login. Can't seem to stop that either. 

Oh, and if 12.04 is supposed to be faster and more productive, it isn't. With the side bar, there is less screen space. If I hide the bar, it takes forever for it to scroll back out when I touch the mouse pointer to the side.

Unity? If this is Ubuntu's version of usable and improved, I'll go to SUSE or some other Linux. Unity makes Windows 3 seem powerful and intuitive.

I'm going to try to get things working, but I harbor little hope.

---

### Post by JRV on 2012-07-27
This will give you the menus:
```

sudo add-apt-repository ppa:diesch/testing
sudo apt-get update
sudo apt-get install classicmenu-indicator

```

The menus will be on the Ubuntu icon in the upper right of the panel.

The thing to autologin is in System=>User Accounts.

Hope this helps.

---

### Post by t0p on 2012-07-27
I'm with you on the stupid menu down the side of the screen.  There are various apps I use a lot, but I have to faff about with searching thru "Dash Home" before the apps are put on the menu... then, next time I boot, the apps have vanished and I have to go thru the Dash Home palaver again...

Seriously, if there's a way to add (and take away) "default" apps from that side menu, tell me how!!

Oh, and navigating the file system is so damn annoying! Pleeeze someone tell me how to personalize Unity.  I loved the old Gnome-based Ubuntu, and now I'm thinking of looking for a new Linux-based OS.

---

### Post by hakermania on 2012-07-27
Well, instead of 1) Clicking on the top left, 2) Go to the appropriate menu, 3) Probably to the next submenu 4) clicking on your application, now you:
1) Hit the windows key 2) Type in the 1st 2 chars of what you want to launch and hit [Enter]
Also, this applies not only to your Applications, but Also to Files&Folders, Music, Videos etc!

I think that's better. Also, for the applications that I frequently use and are on my launcher, I find the Windows Key + N (where N=0-9) very convenient!

What chat application do you use? I use Skype and works just fine. Also, I had no problems with Xchat so far.

I don't have a clue about the thingy that's going on while you boot...

Auto login can be enabled from System Settings->User Account->Unlock (top right)->Automatic Login(ON)

You can autohide the Sidebar and you can also set its sensitivity, from the same setting you can set it to auto hide.

Ah, and, as a side note, use what works best for you (no irony here)

---

### Post by ikt on 2012-07-27
> **Kreacher said:**
> Why should I have to search and add them there?

Because the operating system doesn't know which items you want on the launcher, and because it takes all of 5 seconds to do. 

Your other points have been addressed above.

Oh, and if you search hard enough you might find how to get access to gnome 2 again... here's a hint: [http://www.ubuntugeek.com/how-to-install-classic-gnome-desktop-in-ubuntu-12-04-precise.html](http://www.ubuntugeek.com/how-to-install-classic-gnome-desktop-in-ubuntu-12-04-precise.html)

---

### Post by AlanR8 on 2012-07-27
Choice...that's what its all about. If you don't like it, don't use it.

Use another desktop. Can you do that in Doze or Mac? Don't think so.

I didn't like Unity when it first came out but do you know, I GAVE IT A GO. 

After a while, I realised I liked it and I wouldn't want to move back. Been using my laptop in a corporate environment all week and have not felt in the least disadvantaged.

Good to hear your initial opinion.......

---

### Post by t0p on 2012-07-27
Thanks JRV for the info on how to get a nicer menu.  That has reduced my annoyance somewhat.

As for you, AlanR8: I don't care if Windows or Mac give you choice of desktops.  I'm using Ubuntu.

Like you, I gave Unity a go, and some of it is very nice but some very important things are wrong, or it is not at all clear how to change  the annoying default settings.

Progress is cool.  I'm not whining that Unity is different to Gnome - I'm peeved that Unity is, in many ways *worse* than Gnome (IMHO of course, YMMV and all the rest of it.

Oh, one more thing: where the heck are screensavers in Unity?  I can't find nary a mention anywhere...

---

### Post by Kreacher on 2012-07-27
Seems that I can not use Unity 3d. My NVida card, I guess. 

I ask: Why doesn't the operating system know what items I want on the launcher? It should be simple. I had on the old Gnome menu what I wanted. That's what I wanted on the new launcher. Besudes, if Unity knows to add Firefox, the Office programs and other stuff, then the statement "the operating system doesn't know which items you want on the launcher" makes no sense. If the OS didn't know, then it should have put nothing on the launcher and let everyone try to find and add stuff. Plus, the launcher had a couple of my wine programs added automatically. 

I use the chat that came with Ubuntu 10.04. Empathy?, I guess.

Thanks to all who have replied so far and who will reply. I'm going to try the suggestion by JRV.

---

### Post by t0p on 2012-07-27
Oh yeah, I would also prefer my Windows corner buttons on the right, not the left.  How do I do that, now that Themes are no longer with us?

---

### Post by AlanR8 on 2012-07-27
If you download Ubuntu Tweak and My Unity you'll be able to tweak many options like swapping the buttons to the right.

12.04 has no screen savers by default......

---

### Post by Kreacher on 2012-07-27
> **t0p said:**
> Oh yeah, I would also prefer my Windows corner buttons on the right, not the left.  How do I do that, now that Themes are no longer with us?
Once you install the fix from JRV, go to the System Tools and choose configuration editor. Then choose apps and then metacity. Once there, choose general. 

Find the button_layout. The setting is controlled by the colon (:). 

Example

:minimize,maximize,close

will set the controls to the right. Move the colon to the other side of close and the stuff is one the left again. You can also change the order of the controls. 

:close,minimize,maximize

Watch the commas and the colon. They'll get you every time you misplace one. :)

Note, might not work on all the Unity windows.

---

### Post by oldos2er on 2012-07-27
Moved to Ubuntu Testimonials & Experiences.

---

### Post by vexorian on 2012-07-27
> **AlanR8 said:**
> Choice...that's what its all about. If you don't like it, don't use it.

Use another desktop. Can you do that in Doze or Mac? Don't think so.

I didn't like Unity when it first came out but do you know, I GAVE IT A GO. 

After a while, I realised I liked it and I wouldn't want to move back. Been using my laptop in a corporate environment all week and have not felt in the least disadvantaged.

Good to hear your initial opinion.......

Choice is a wonderful thing, but if we want to appeal to more users than the guys who want to spend a week finding out the DE they like they most (I just did that, installed just about everything and tried to use just about everything). Then it is probably a good thing to give users sensible defaults. 

I think unity is ok as such. They need to improve performance though. And need to take it out of compiz and make a standalone app that can run with other compositing managers, as compiz really makes it hard to port unity to other distros. But I just wanted to say, that we need to consider new users' impressions, because even if you can easily change it, we would like the majority of users to like their first impression with the OS.


> Use another desktop. Can you do that in Doze or Mac? Don't think so. Believe it or not, you can in doze. But it is probably not going to make MS very happy and can be risky.

---

### Post by kurt18947 on 2012-07-27
> **t0p said:**
> I'm with you on the stupid menu down the side of the screen.  There are various apps I use a lot, but I have to faff about with searching thru "Dash Home" before the apps are put on the menu... then, next time I boot, the apps have vanished and I have to go thru the Dash Home palaver again...

Seriously, if there's a way to add (and take away) "default" apps from that side menu, tell me how!!

Oh, and navigating the file system is so damn annoying! Pleeeze someone tell me how to personalize Unity.  I loved the old Gnome-based Ubuntu, and now I'm thinking of looking for a new Linux-based OS.

There's a couple ways to add and remove apps from the launcher bar (I think that's what it's called.  One is to open an app from the dash.  The app should then be in the launcher bar.  Right-click and select 'keep in favorites' or whatever the phrasing is.  The other way is to find the app's icon in dash, right-click the icon and left-click 'add to favorites'.  Not that tough.  What would be *really* helpful would be a link to a good intro video on youtube or a good illustrated "Here's how you do the basics in Unity".   Put a launcher on the initial desktop.  I don't know that Unity is as bad as some make it out to be but it certainly IS different and requires a rejiggering of brain muscles.  Of course there are an abundance of Unity alternatives if Unity just won't fit.  Xfce & LXDE, Cinnamon and MATE come immediately to mind.

---

### Post by madjr on 2012-07-27
try this to learn your way around:

[http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-basic-unity-interface-desktop-tutorial](http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-basic-unity-interface-desktop-tutorial)

and then this to tweak some stuff you may want:

[http://www.webupd8.org/2012/04/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2012/04/things-to-tweak-after-installing-ubuntu.html)

---

### Post by JRV on 2012-07-27
> **t0p said:**
> 
Seriously, if there's a way to add (and take away) "default" apps from that side menu, tell me how!!


To add a program to the launcker bar open the program and the icon will appear in the launcher bar. Right click the icon then click "Lock to Launcher"

In Unity 3d (Not in 2d) you can then drag the icon off of the launcher bar and reinsert it where you want it.

To remove an icon from the launcher bar right click it and select "Unlock from Launcher".

---

### Post by diesch on 2012-07-27
> **t0p said:**
> I'm with you on the stupid menu down the side of the screen.  There are various apps I use a lot, but I have to faff about with searching thru "Dash Home" before the apps are put on the menu... then, next time I boot, the apps have vanished and I have to go thru the Dash Home palaver again...


What you see are just the running apps.

> **t0p said:**
> 
Seriously, if there's a way to add (and take away) "default" apps from that side menu, tell me how!!


If the app is running right click on the icon and choose "Lock to launcher" to add it or "Unlock from launcher" to remove it.

Or drag an icon from the dash into the launcher to add it and drag  aa little bit to the right and then into the trash to remove it.


> **t0p said:**
> 
Oh, and navigating the file system is so damn annoying! Pleeeze someone tell me how to personalize Unity..
 [Unsettings]("http://www.florian-diesch.de/software/unsettings/") gives you some options that aren't easily available by default.

---

### Post by Jerry N on 2012-07-27
> **hakermania said:**
> ....now you:
1) Hit the windows key 2)....

What if you don't have a windows key?  I use a big solid heavy reliable IBM PS/2 keyboard built in 1987.  It doesn't have a windows key or a propeller key or any of that stuff.  And yes I am old and crabby and set in my ways.

Jerry

---

### Post by Tamlynmac on 2012-07-27
As defined in this [sticky]("http://ubuntuforums.org/showthread.php?t=1921679"), this isn't a support section of the forums. It's been my experience that once support is offered or requested here the thread often gets closed.

To the OP:
> Kreacher
I'm going to try to get things working, but I harbor little hope.

Sorry, your experiencing problems and hope you stick with it. I think you'll find by posting support requests in the appropriate help sections of the forums, that solutions may be available.

Good Luck

---

### Post by Chdslv on 2012-07-28
> **Kreacher said:**
> Unity in 12.04 LTS

Where are all my menu items that were so convenient to get to with Gnome? 

Oh, and if 12.04 is supposed to be faster and more productive, it isn't. With the side bar, there is less screen space. If I hide the bar, it takes forever for it to scroll back out when I touch the mouse pointer to the side.

Unity? If this is Ubuntu's version of usable and improved, I'll go to SUSE or some other Linux. Unity makes Windows 3 seem powerful and intuitive.

I'm going to try to get things working, but I harbor little hope.

Well, a little bit of whining won't help, would it? Look at your Ubuntu 12.04 in Live mode and play with it. When you install, be careful and read everything happening on the screen. 

Once you have installed Ubuntu 12.04, update your installation, and then install your 3D driver for your computer. Then install flash-plugin from the Software Centre. Install Synaptic, if you want. 

Now, you don't like Unity, or you just can't learn how to work with it, so you'd like to have Gnome, and most probably old Gnome. **You can have it.** It is underneath Unity.

Here is an easy way. Use Software Centre and install Cairo Dock. You may install Compiz, CCSM before that, if you need eye candy and blings. Once Cairo dock is installed, log out and check the desktop environment choices at the sign in. Choose one you need. **It is that simple.  **

You'd have your Gnome and the old-Gnome there. Be happy!:D

---

### Post by vasa1 on 2012-07-28
> **madjr said:**
> try this to learn your way around:

[http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-basic-unity-interface-desktop-tutorial](http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-basic-unity-interface-desktop-tutorial)
...
Nice.
Also, [http://www.youtube.com/watch?v=xA9EHaNc2VI](http://www.youtube.com/watch?v=xA9EHaNc2VI)

I'm going to stick these two in my sig.

---

### Post by Elfy on 2012-07-28
If you want support then start support questions for the things you need help with.

The chances are that anything you want has been discussed ad infinitum - unity is not new - it's been about since 11.04.

If you don't like Unity - try gnome-shell, in fact the repositories have a whole bunch of other DE's.

Personally I use Xubuntu now. 

Closed.

---

