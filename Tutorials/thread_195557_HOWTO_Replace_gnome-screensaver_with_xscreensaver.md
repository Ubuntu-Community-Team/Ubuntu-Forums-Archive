---
title: "HOWTO: Replace gnome-screensaver with xscreensaver"
date: 2006-06-13
forum: Tutorials
---

### Post by 23meg on 2006-06-13
[COLOR="DarkSlateBlue"]Note: I have [another guide]("http://www.ubuntuforums.org/showthread.php?t=198809") for adjusting screensaver settings in Dapper without replacing gnome-screensaver. **I prefer the method described in that guide to this one**, but your mileage may vary. Both have their pros and cons so make sure you check out both before applying the instructions.
[/COLOR]
[SIZE="2"]**[COLOR="Red"]Problem:[/COLOR]**[/SIZE] Dapper ships with gnome-screensaver instead of xscreensaver, which gives the user no option to set individual screensaver settings. 

[SIZE="2"]**[COLOR="Red"]Details:[/COLOR]**[/SIZE] In Dapper display power management functions were decoupled from the screensaver with the introduction of Gnome Power Manager. xscreensaver provides both functions, thus became partially redundant. Refer to [the gnome-screensaver FAQ]("http://live.gnome.org/GnomeScreensaver/FrequentlyAskedQuestions"), [the upstream bugzilla discussion]("http://bugzilla.gnome.org/show_bug.cgi?id=316654") and [the Launchpad discussion]("https://launchpad.net/distros/ubuntu/+source/gnome-screensaver/+bug/22007") for more details if interested. 

Ubuntu has a tendency to stick with the GNOME suite of applications unless absolutely necessary, and the GNOME developers do have reasons for doing what they're doing, so gnome-screensaver does have its longer term use, but in immediate practical terms we need a way of configuring screensaver options; otherwise most of them are either unusable or have crippled functionality. The following isn't a very elegant modification, but one that works nevertheless. Refer to the "Drawbacks" part at the bottom for possible dysfunctions after applying this. 

[SIZE="2"]**[COLOR="Red"]Solution:[/COLOR]**[/SIZE] Get xscreensaver back, disable gnome-screensaver.

[SIZE="3"]**1.**[/SIZE] To configure gnome-screensaver not to function, go to System / Preferences / Screensaver and uncheck both checkboxes. 

[SIZE="3"]**2.**[/SIZE] To totally stop gnome-screensaver from running, kill its process```
sudo killall gnome-screensaver
```and prevent it from being launched on startup ```
gconftool-2 --type boolean -s /apps/gnome_settings_daemon/screensaver/start_screensaver false

```**If** the latter doesn't seem to be working persistently for some reason, resort to making gnome-screensaver unexecutable:
```
sudo chmod -x /usr/bin/gnome-screensaver
```

[SIZE="3"]**3. **[/SIZE] Install xscreensaver. ```
sudo apt-get install xscreensaver
```

[SIZE="3"]**4.**[/SIZE] [COLOR="Gray"]Optional:[/COLOR] Install the extra screensavers in the repositories that don't come installed as default. ```
sudo apt-get install xscreensaver-data-extra xscreensaver-gl-extra
```

[SIZE="3"]**5. **[/SIZE]Add the xscreensaver daemon to your list of startup programs. Go to System / Preferences / Sessions / Startup Programs, click "Add" and type "**xscreensaver -no-splash**".

[SIZE="3"]**6.**[/SIZE] Modify the System / Preferences / Screensaver menu entry to launch the xscreensaver configuration window instead of the gnome-screensaver one: ```
gksudo gedit /usr/share/applications/gnome-screensaver-preferences.desktop

```Locate the following line:```
Exec=gnome-screensaver-preferences
```and change it to ```
Exec=xscreensaver-demo
```and comment out the last four lines to make them look like this:```
#X-GNOME-Bugzilla-Bugzilla=GNOME
#X-GNOME-Bugzilla-Product=gnome-screensaver
#X-GNOME-Bugzilla-Component=general
#X-Ubuntu-Gettext-Domain=gnome-screensaver
```

[SIZE="3"]**7. **[/SIZE]Click System / Preferences / Screensaver to launch the xscreensaver configuration window, go to the "Advanced" tab and **uncheck the "Power Management Enabled" checkbox**. This should stop xscreensaver's power saving features from conflicting with Gnome Power Manager.

[SIZE="3"]**8.**[/SIZE] [COLOR="Gray"]Optional:[/COLOR] Create a launcher to lock the screen manually. Right click your desktop, choose "Create Launcher", and enter the following as the command: "**xscreensaver-command -lock**".

[SIZE="2"][COLOR="Red"]**Drawbacks:**[/COLOR][/SIZE] 

- System / Quit / Lock Screen doesn't function after applying this, since it locks the screen via gnome-screensaver. I'm looking for a fix to this; in the meantime you can use the launcher you created in step 8 as a workaround. ([COLOR="Red"]Update[/COLOR]: See [this post]("http://ubuntuforums.org/showpost.php?p=1518635&postcount=32") for a suggested fix. I haven't tried it yet)
 

- In my experience the screen won't get locked when closing the laptop lid but this may be due to my (mis)configuration; I'll report back on this after experimenting a bit.

- You get the standard xscreensaver unlock dialog when unlocking the screen instead of the Dapper one, which detracts from the overall polish a bit, if you mind such things.

---

### Post by bulldog on 2006-06-13
Thank you for this HowTo.
All worked fine and no messing up so far:)

---

### Post by ayoli on 2006-06-13
yes, that's work, but i prefer to use alacarte to add a new menu entry for xscreensaver-demo, this way keep everything to restore easily gnome screensaver, and btw why edit manually conf file when the graphical way works ;)

---

### Post by 23meg on 2006-06-13
> **ayoli]yes, that's work, but i prefer to use alacarte to add a new menu entry for xscreensaver-demo, this way keep everything to restore easily gnome screensaver, [/QUOTE]Having menu items for both doesn't make sense when gnome-screensaver is completely disabled said:**
> and btw why edit manually conf file when the graphical way works ;)It's easier and less error prone to describe the non-graphical way in a guide, and you can't comment out lines with Alacarte.

---

### Post by ayoli on 2006-06-13
> **23meg]Having menu items for both doesn't make sense when gnome-screensaver is completely disabled said:**
> 
menu items can be hide/shown and if ppl totally don't want gnome-screensaver why don't just apt-get remove it ?
[QUOTE=23meg]It's easier and less error prone to describe the non-graphical way in a guide...
i agree with that ;)

---

### Post by 23meg on 2006-06-13
[QUOTE=ayoli]menu items can be hide/shown and if ppl totally don't want gnome-screensaver why don't just apt-get remove it ?[/QUOTE]Because removing it also removes ubuntu-desktop; just disabling it is a less aggressive method and makes it easier to revert back to it if desired.

---

### Post by ayoli on 2006-06-13
ah yes, true. but weird to have a dep that force to keep unwanted/unused  apps.

---

### Post by NoWhereMan on 2006-06-13
it's only me, or "fade to black" option doesn't work?

---

### Post by ayoli on 2006-06-13
xscreensaver "fade to black" option works perfectly on my laptop :)

---

### Post by NoWhereMan on 2006-06-13
d'oh. that's strange...

---

### Post by n00bWillingToLearn on 2006-06-16
This is probably a stupid questions but the gnome screensaver FAQ says:

> 
**Why gnome-screensaver, what happened to xscreensaver?**

 gnome-screensaver is a new screensaver that can replace xscreensaver. It is designed to integrate well with the desktop and provide a control interface that is desktop neutral. It simplifies and streamlines the experience for the user and provides more capability for the system administrator and vendor. 
It is designed to support: 
[LIST]
[*]a desktop neutral control interface via DBus 
[*]a desktop neutral and standard way to install and manage screensaver themes 
[*]switching users directly from the unlock dialog 
[*]allowing a system administrator to set a mandatory policy for any setting 
[*]a secure separation of user input processing and authentication from the screen locking window 
[*]a separation between the screensaver theme engine and the theme settings 
[*]integration with the desktop (themes, fonts, toolkit) 
[*]translation into many languages by the GNOME Translation Project 
[*]instantly applying settings changes****[/LIST]Does "allowing a system administrator to set a mandatory policy for any setting" mean that the Ubuntu devs could have just turned off the extra features and they can be turned back on, or is it really impossible to get all the features of xscreensaver in gnome-screensaver.

---

### Post by ayoli on 2006-06-16
if you mean editing the  screensavers i guess it possible by editing the right .desktop file in /usr/share/gnome-screensaver/themes/
but for me the most missing feature in gnome-screensaver is the fade in/out.

---

### Post by 23meg on 2006-06-16
> Does "allowing a system administrator to set a mandatory policy for any setting" mean that the Ubuntu devs could have just turned off the extra features and they can be turned back on, or is it really impossible to get all the features of xscreensaver in gnome-screensaver.No, it doesn't mean that; it means the system administrator can set a global screensaver policy that affects all users.

---

### Post by 23meg on 2006-06-19
**Update: **I posted another guide for adjusting screensaver settings in Dapper **without** replacing gnome-screensaver altogether. I prefer the method described in that guide to this one, but your mileage may vary. Both have their pros and cons so make sure you check out both before applying the instructions.

Check it out here:

[http://www.ubuntuforums.org/showthread.php?t=198809](http://www.ubuntuforums.org/showthread.php?t=198809)

---

### Post by Shay Stephens on 2006-06-19
I used synaptic to remove gnome screen saver and install xscreensaver.  It gave the creepy warning that desktop would be uninstalled, and in the past I have avoided doing that but this time I threw caution to the wind and went with it.

End result, gnome screensaver is gone, xscreensaver is running, LCD monitor powers down properly, and I still have my desktop ;)

---

### Post by ayoli on 2006-06-19
[QUOTE=Shay Stephens]I used synaptic to remove gnome screen saver and install xscreensaver.  It gave the creepy warning that desktop would be uninstalled, and in the past I have avoided doing that but this time I threw caution to the wind and went with it.

End result, gnome screensaver is gone, xscreensaver is running, LCD monitor powers down properly, and I still have my desktop ;)[/QUOTE]

ubuntu-desktop package seems to be safely removable, but could cause pb with  upgrades, if new packages are added to the ubuntu-desktop you're will not be able to have them installed with a dist-upgrade.
cheers

---

### Post by enopepsoo on 2006-06-24
cool tutorial, man!:KS

---

### Post by stanz on 2006-06-25
[quote=ayoli]if you mean editing the  screensavers i guess it possible by editing the right .desktop file in /usr/share/gnome-screensaver/themes/[/quote]
Geezz...I went to the files...How does one edit files like that?
:confused:

---

### Post by ayoli on 2006-06-26
[QUOTE=stanz]Geezz...I went to the files...How does one edit files like that?
:confused:[/QUOTE]
in each desktop file you'll find a exec line, for example /usr/share/gnome-screensaver/themes/antspotlight.desktop got a line:
```
Exec=antspotlight -root
```
where you can give more options to tweak this screensaver if needed, there's a manpage wich tells:
```
antspotlight   [-display  host:display.screen]  [-window]  [-root]  [-install]  [-visual visual] [-delay microseconds] [-fps]
```
I guess most of screensavers got their manpage.
so, it's not a very intuitive method, that's one of the reasons why I prefer xscreensaver (the other is the fade potion ).
edit: 23meg as made a [guide]("http://www.ubuntuforums.org/showthread.php?t=198809") for that.
regards.

---

### Post by 23meg on 2006-06-26
In a new guide I described a more convenient way to figure out screensaver options through xscreensaver; check this out:

[http://www.ubuntuforums.org/showthread.php?t=198809](http://www.ubuntuforums.org/showthread.php?t=198809)

---

### Post by ayoli on 2006-06-26
> **23meg]In a new guide I described a more convenient way to figure out screensaver options through xscreensaver said:**
> http://www.ubuntuforums.org/showthread.php?t=198809[/url]
yep I mentioned that at the end of my previous post ;)

---

### Post by 23meg on 2006-06-26
Thanks for the edit; to remind again, I recommend that everyone check out both guides and decide which one to use for themselves.

---

### Post by autocrosser on 2006-07-03
Just if anyone is interested in a mouse "hot-spot" for Xscreensaver---I missed using Brightside's hot-spot to turn on the screensaver (it won't work as "start screensaver" without editing deeper that I want to)--So I went to "custom action" for the mouse corner I wanted & put in--  xscreensaver-command -activate  in the "entering region" box--make sure you tic the "terminate above application" checkbox too:D

---

### Post by benp on 2006-07-23
Hey,

Thanks for the guide. I went with replacing gnome-screensaver rather than working around its limitations, since I'm used to xscreensaver-demo and don't care about screen locking. But I have run into a problem... Totem(-xine) doesn't disable xscreensaver when watching movies fullscreen. It did disable gnome-screensaver properly, and I recall it disabling xscreensaver in Breezy.

I haven't been able to find anything in Totem's help or man pages relating to the screensaver.

The obvious way to get it working is just to use the gnome-screensaver/xscreensaver-demo combo, but I thought I'd ask first if anyone knows how to get Totem to disable xscreensaver.

Thanks,
Ben

---

### Post by benplaut on 2006-07-25
> **benp said:**
> Hey,

Thanks for the guide. I went with replacing gnome-screensaver rather than working around its limitations, since I'm used to xscreensaver-demo and don't care about screen locking. But I have run into a problem... Totem(-xine) doesn't disable xscreensaver when watching movies fullscreen. It did disable gnome-screensaver properly, and I recall it disabling xscreensaver in Breezy.

I haven't been able to find anything in Totem's help or man pages relating to the screensaver.

The obvious way to get it working is just to use the gnome-screensaver/xscreensaver-demo combo, but I thought I'd ask first if anyone knows how to get Totem to disable xscreensaver.

Thanks,
Ben

Hey! Who are you!? :mrgreen: 

>>>>>>>>>>>>>>>>>>>>>>
I installed xscreensaver on my sis's laptop, and most of the hacks are showing as 'not installed'... any suggestions?

---

### Post by stanz on 2006-07-27
> **ayoli said:**
> in each desktop file you'll find a exec line, for example /usr/share/gnome-screensaver/themes/antspotlight.desktop got a line:
 I guess most of screensavers got their manpage.
so, it's not a very intuitive method, that's one of the reasons why I prefer xscreensaver (the other is the fade potion ).
edit: 23meg as made a [guide]("http://www.ubuntuforums.org/showthread.php?t=198809") for that.
regards.
Hi All....I finally got back here...
and I'm wondering why i can't, "apt-get xscreensaver"?
Are ya switching repo's? One's for Breezy?
> 23meg ;; Thanks for the edit; to remind again, I recommend that everyone check out both guides and decide which one to use for themselves. I'll check them again, I notice you say this is for Dapper, but I get::
> Package xscreensaver is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  xscreensaver-data
E: Package xscreensaver has no installation candidate
 Ya mentioned getting 'data' also, but idonno...:confused:
So, different source...or, well- I'll check what I got to be sure. :-k
Thanks All...!!

---

### Post by yeehawjared on 2006-08-26
guide worked perfectly.  I have a dell inspiron 9300 and was searching for a way to turn off the LCD.  Thanks!

---

### Post by Greeface on 2006-08-30
> **23meg said:**
> 
- You get the standard xscreensaver unlock dialog when unlocking the screen instead of the Dapper one, which detracts from the overall polish a bit, if you mind such things.

I installed the version from Breezy, which looks pretty nice.  It is available [here.](http://packages.ubuntu.com/breezy/x11/xscreensaver)  After you install it you should lock the version in Synaptic so it doesn't just get updated again.

---

### Post by giacomolg on 2006-09-09
Thank you for the little guide. I've found these pros for xsceensaver
1) GL screensaver work smother
2) Xscreensaver has the *preview* bottom
3) Configuration possibilities
4) Fade in/out option

But I have also one problem: some of the screensavers present in /usr/lib/xscreensaver (that have a correpondent xml config file in /usr/share/xscreensaver) aren't showed in the xscreensaver-demo list.

Why? Have you had this problem as well? Is there a work-around?

Thank you in advance!!

---

### Post by giacomolg on 2006-09-09
Found (the) solution: unfortunately I had to manually add a line for each screensaver in ~/.xscreensaver

Bye

---

### Post by morphx on 2006-09-13
I recently installed Ubuntu on my laptop as my primary OS (dual booting with XP) and I've just felt in love with it... still... there're many things I miss from XP and being able to easily configure my screensavers is one them.

So, after reading this, and other similar posts, I decided to try to do a full replacement for gnome-screensaver-preferences
After a couple of days I've managed to come up with an application that will let you (a) see the list of all your screensavers, (b) preview them in a small window and (c) change their settings.
The application does not yet support changing parameters specific to the daemon (such as when to start the screensaver, whether to lock the screen or not, etc...) but so far it can be simply used to setup your screensavers so they run the way "we" want them.

If anyone is interested, it can be downloaded form this address:
[http://software.xfx.net/ftp/xfx-screensaver-settings_0.1.tar.gz]("http://software.xfx.net/ftp/xfx-screensaver-settings_0.1.tar.gz")

Comments... suggestions... ideas... they are all welcomed!

---

### Post by dhasenan on 2006-09-19
If you want System->Quit->Lock Screen to work, just do this:
```

$ sudo ln -f /usr/bin/xscreensaver-command /usr/bin/gnome-screensaver-command
```

after following the rest of that guide. The query, throttle, and unthrottle flags from gnome-screensaver-command won't work, though.

---

### Post by giacomolg on 2006-09-19
Thanks for the tip. What do the *query, throttle, and unthrottle* flags do?

Bye:confused:

---

### Post by Quoll on 2006-09-21
23Meg - what can I say? This was one of the things bugging me since upgrading to Dapper and your HOWTO works flawlessly. (The other was a mis-synced Linux clock and I now have that sorted too.)

This is what Ubuntu is all about. Thank you!

---

### Post by P_Badger on 2006-10-06
Thanks 23meg, you're a Saint! So far option 1 seems to be working great since I've never really found myself needing to lock my screen. 

Hopefully the "gui nazis" who've crippled gnome screensaver will eventually get the point that all they're doing is pissing people off.

---

### Post by lorddaddy84 on 2006-10-11
> **giacomolg said:**
> Thanks for the tip. What do the *query, throttle, and unthrottle* flags do?

Bye:confused:

Any ideas?

---

### Post by shoki on 2006-10-25
[SIZE=3]**5. **[/SIZE]Add the xscreensaver daemon to your list of startup programs. Go to System / Preferences / Sessions / Startup Programs, click "Add" and type "**xscreensaver -no-splash**".

I can not seem to get this to actually save. Are there any tricks to getting it to save the session?

Thanks
--Shoki

---

### Post by hikaricore on 2006-10-26
You shouldn't need to actually save the session to get startup programs to launch.  I've never personally had any trouble with them.  Is it just xscreensaver that won't launch or is it anything?  Try putting something trivial like gedit in your startup programs and logout then back into X.  If it pops up then you may just be having trouble launching xscreensaver for one reason or another, you might try making a bash startup script and adding it there instead.  :)

---

### Post by shoki on 2006-10-27
gedit dosent work either... it's not a big deal... when I boot up I just launch xscreensaver and it works. Yeah I ad the command and it goes into the box of programs to launch and then when I start session manager again the command is gone.  I searh for a how to on start-up scripts later.

Thanks again,
--Shoki

---

### Post by autocrosser on 2006-10-28
I can say that this guide also works in Edgy--I also went to my Sessions & disabled the Gnome-Power-Manager items--I use Xscreensaver monitor contrls & it works much better than GPM.

---

### Post by 23meg on 2006-12-17
> **morphx said:**
> I recently installed Ubuntu on my laptop as my primary OS (dual booting with XP) and I've just felt in love with it... still... there're many things I miss from XP and being able to easily configure my screensavers is one them.

So, after reading this, and other similar posts, I decided to try to do a full replacement for gnome-screensaver-preferences
After a couple of days I've managed to come up with an application that will let you (a) see the list of all your screensavers, (b) preview them in a small window and (c) change their settings.
The application does not yet support changing parameters specific to the daemon (such as when to start the screensaver, whether to lock the screen or not, etc...) but so far it can be simply used to setup your screensavers so they run the way "we" want them.

If anyone is interested, it can be downloaded form this address:
[http://software.xfx.net/ftp/xfx-screensaver-settings_0.1.tar.gz]("http://software.xfx.net/ftp/xfx-screensaver-settings_0.1.tar.gz")

Comments... suggestions... ideas... they are all welcomed!Hi, sorry for missing your post; I've neglected this thread for a while. Thanks for your contribution. I've tried your app in Edgy, but it fails to change the settings, perhaps since the change of the gnome-screensaver theme directory has changed to /usr/share/applications/screensavers . It will be nice if you can make a version for Edgy with the appropriate change, as well as providing the source code.

---

### Post by raul_ on 2007-01-01
I don't seem to have gnome-screensaver installed :-k should i just install xscreensaver or should i follow the whole guide from the point where you install xscreensaver?

EDIT: maybe i should just tell what i want to do...i want to prevent my screen from going blank after a period of times (it's really annoying when i'm watching movies) so i went to the gnome power manager and put all the options to either "never" or "do nothing". But this didn't seem to do the trick. So i searched the forums and the solution was going to System->Preferences->Screensaver . The only problem is....i don't have that option. I tried installing xscreensaver but that option still doesn't appear. I tried editing the menus but it's not there...

Update: Just installed gnome-screensaver and disabled it :P

---

### Post by Disastorm on 2007-01-03
> **shoki said:**
> [SIZE=3]**5. **[/SIZE]Add the xscreensaver daemon to your list of startup programs. Go to System / Preferences / Sessions / Startup Programs, click "Add" and type "**xscreensaver -no-splash**".

I can not seem to get this to actually save. Are there any tricks to getting it to save the session?

Thanks
--Shoki

type this in the console:
sudo chown -R <your username> ~/

---

### Post by matthinckley on 2007-05-11
I did this a little differently.. instead of disabling the gnome-screensaver startup in gconf-editor and placing xscreensaver -no-splash in my sessions (I want xscreensaver for all users, not just me), I moved /usr/bin/gnome-screensaver to /usr/bin/gnome-screensaver.old and created a new file /usr/bin/gnome-screensaver with the following in it:

```
#!/bin/bash
xscreensaver -no-splash
```

this way gnome calls my script for every user

---

### Post by blumagic on 2007-05-27
All,

I actually want to bring back my gnome screensaver. Do you have way to back out of this workaround?

Thanks,

blu.....

---

### Post by cor2y on 2007-06-06
blumagic , i am not sure but do the reverse of what was done in the tutorial.
Remove xscreensaver.
Re-add gnome screensaver to the list it was edited out of , well as uncomment the gnome screensaver references , also remove xscreensaver from the startup list.

---

### Post by ldh on 2007-11-01
I tried/used this process - and it did work -- however now my Desktop pc will not suspend automatically.  
If I put the system to sleep it works great and comes "awake" perfectly. Prior to making these changes the system would suspend within 45 minutes as I had setup in the Power preference.   So my question,  How do I undo -- what I have done?  Or do you have some idea how to resolve?
Thanks in advance:confused:

ldh

---

### Post by ldh on 2007-11-02
Thanks folks but no reply necessary --- I simply reversed the original steps..went into Synaptic and removed xscreensaver and all is back to normal now with the manner in which this computer enters standby.

---

### Post by naurus on 2007-12-21
I think you should put how to add xscreensaver to startup into your (awesome) tutorial. Here's how i did it:

> sudo gedit /etc/init.d/xscreensaver
Add this to the file (it should be empty to begin with) and save:
> #!/bin/bash

xscreensaver -no-splash &
Now run these three commands
> cd /etc/init.d/
sudo update-rc.d xscreensaver defaults
sudo chmod +x xscreensaver

Now you should be set. If this doesn't work, try taking a look at the comments on [http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

Naurus

---

### Post by Nysa on 2007-12-23
similar issue...
i tried to revert back to gnome-screensaver undoing as given above here..after deinstalling xscreensaver... however, the gnome lock does not work (gnome-screensaver-command: no screensaver is running on display :0.0) any more, although the screen goes blank as usual after some time... am i missing something silly? any help appreciated..

---

### Post by birdywa on 2007-12-29
I have tried this in gutsy, but when the screensaver is supposed to turn on, it just logs out and goes to the login screen. I followed the instructions exactly, and I don't see why it wouldn't work in gusty. Please help - I don't want to use the barely functional gnome-screensaver.

---

### Post by K_Boomer on 2008-01-12
:confused:  whenever i go to the xscreensaver menu, I get a warning that the xscreensaver daemon is not running in "1:0." then my computer either freezes up or restarts regardless if i press "ok" or "cancel". do you know what might be the problem?

---

### Post by autocrosser on 2008-01-13
Did you make sure that Gnome-screensaver can't be running? Secondly, it sounds like you didn't include a startup in Sessions.....Command should be: xcreensaver -no-splash (make sure you have the space between xscreensaver & -no-splash)

---

### Post by jonathanwalshuk on 2008-01-17
I think it should be xscreensaver -nosplash that you add to the startup programs in  the session manager.

---

### Post by autocrosser on 2008-01-17
No--according to Xscreensaver's docs it is -no-splash     
Please read---  [http://www.jwz.org/xscreensaver/man1.html](http://www.jwz.org/xscreensaver/man1.html)

In any case--you REALLY need to go thru the first post line by line & do exactly what it said.

---

### Post by jonathanwalshuk on 2008-01-18
That's funny I looked at [http://www.jwz.org/xscreensaver/man1.html](http://www.jwz.org/xscreensaver/man1.html) and you are right in that it says -no-splash at the start of the document, however later oon it talks about -nosplash.

Any way I tried it the first way, and on accessing the screensaver control panel it would flash up the warning about the daemon not running, but switching to the -nosplash option makes it work fine and dandy.

---

### Post by autocrosser on 2008-01-18
Strange--mine works well with -no-splash  Guess whatever makes it work (shrug)

I'll talk to him about the difference--if any....

---

### Post by metalguy639 on 2008-04-12
> **birdywa said:**
> I have tried this in gutsy, but when the screensaver is supposed to turn on, it just logs out and goes to the login screen. I followed the instructions exactly, and I don't see why it wouldn't work in gusty. Please help - I don't want to use the barely functional gnome-screensaver.

Same here. :( Did not realize that it would only work with a different Ubuntu version. Now my PC crashes every time I click on a screen saver to view it. I would really like to just have the screensavers from the xscreensaver, I really don't need the extra preferences & settings. I tried uninstalling this and it did not work. Then it would not launch ANY screen saver nor would it. I get an error message saying it will not launch the screensaver. I need a step by step how to guide to get rid of this now and get the other gnome screensavers back on the PC. I tried reversing what was said in the first post and it crashed my PC. I need to know what the reverse codes are of some of the stuff mentioned in the first post. I would like to have the extra screensavers they are really cool so if after I get this fixed if there is a way to just install the extra screen savers and use them in the gnome screensaver that would be fine.

---

### Post by cgarre on 2008-05-18
Perfect !!!! works great .... and [http://ubuntuforums.org/showpost.php?p=1518635&postcount=32](http://ubuntuforums.org/showpost.php?p=1518635&postcount=32) also works. So now there is no major difference between what i used to have and now .. Thanks everyone .. i am on XscreenSaver, without any issue.

---

### Post by cgarre on 2008-05-26
bad xscreensaver too .. since there are times i get authentication failure, when i try to unlock, even though i am not given an opportunity to enter password !!!!! 

I revert back to gnome-screensaver and now when i lock i get gnome-screensaver-command: no screensaver is running on display :0.0


:-(

Even though i can see gnome-screensaver running.

---

### Post by Mecandes on 2008-07-07
Hmm, getting odd yellow error messages at the top of the screen in most of the XScreenSaver screensavers on Hardy Heron.

---

### Post by Moon Jaguar on 2008-08-16
Works good with Mint Elyssa so far.

---

### Post by peterius on 2008-09-01
I figured if gnomescreensaver is what's there, I don't want to screw with that, so instead I linked all the screensaver modules from xscreensaver into the gnomescreensaver directory and then I copied the .xml files from the config and then ran the migrate-xscreensaver-config.sh with the accompanying .xsl file from the gnomescreensaver cvs data directory as per gnomescreensaver FAQ.

It doesn't work.  At first I thought it was just the screensavers that did things with the screen image, but it seems to be some of the others too.  They show up in the sparse gnomescreensaver config panel, graphics and all, but when my system goes to sleep, the screen just turns black.

---

### Post by helpdeskdan on 2008-09-18
I installed xscreensaver and use screensaver-settings.  No strange configuration required!!

[http://software.xfx.net/utilities/sss/index.htm](http://software.xfx.net/utilities/sss/index.htm)

---

### Post by timbalisto on 2008-12-06
I can confirm that this guide works on Hardy Heron. The only problem I have is power management. With the Gnome power settings, I had the display put to sleep after 40 minutes, but after the change to xscreensaver, the display won't sleep. I can't do it with xscreensaver's power management because I just want the monitor to go on standby, not the computer. Any help would be appreciated.

---

### Post by timbalisto on 2008-12-06
I see now that the power management in xscreensaver says "Display Power Management", but the options it gives seem like it's meant for the system instead of the monitor. I'll try it though.

---

### Post by rflook on 2008-12-07
Great guide but i am having one problem - im using a mythbuntu distro (7.10) which means if i am correct im am using xfce4. Now the one thing i cant get to work is to make the xscreensaver manager come up, even when changing the /usr/share/applications/gnome-screensaver-preferences.desktop file it still loads up the gnome manager - not really sure how thats possible but it does.

Anyone know how i can sort this problem out?

---

### Post by Snypez on 2009-02-04
Not to resurrect an old thread but just wanted to mention this works in 8.10 intrepid. I replaced the ss and used the code to fix system | lock screen. Now the only small issue is in the user switcher panel app the lock screen function does not work. I have no idea where the config for this is but I am looking into it. If anyone else knows how to change this behavior please post. Thanks 23meg for this extremely easy to follow guide!

---

### Post by Snypez on 2009-02-18
New update. I am also getting the yellow errors mentioned earlier in this thread. From much research I have found that this is actually caused by the version of perl that ships with ubuntu. I found someone on another thread who said "adding a debian sid repository to my third party software, and using the Perl version from there" corrects the problem but as of now I don't know how to do this. If anyone has any suggestions please post them. If I figure it out before anyone else responds I will paste a step by step to ensure this thread remains up to date.

---

### Post by Nano_ext3 on 2009-04-15
> - System / Quit / Lock Screen doesn't function after applying this, since it locks the screen via gnome-screensaver. I'm looking for a fix to this; in the meantime you can use the launcher you created in step 8 as a workaround. (Update: See this post for a suggested fix. I haven't tried it yet)

This DOES work FYI, worked good to soft link it.

---

### Post by Nano_ext3 on 2009-04-15
How would one restore gnome-screensaver to check back to see if it works or not, after a new kernel comes out?

---

### Post by webkris on 2009-04-24
Greets - 
Followed the How-To.
I can see and demo all the screen savers.
I set my saver for 1 minute. Screen goes blank - then nothing?
I select a non-GL saver. Screen goes blank - then nothing...
I manually activate the screen saver "gnome-screensaver-command --activate" Screen goes blank - then nothing...

I have logged out, and restarted.
What should I try next?

- Kris

---

### Post by Nano_ext3 on 2009-04-24
> **webkris said:**
> Greets - 
Followed the How-To.
I can see and demo all the screen savers.
I set my saver for 1 minute. Screen goes blank - then nothing?
I select a non-GL saver. Screen goes blank - then nothing...
I manually activate the screen saver "gnome-screensaver-command --activate" Screen goes blank - then nothing...

I have logged out, and restarted.
What should I try next?

- Kris

Kris,

I would remove gnome-screensaver entirely, not just stop it from running as per the guide.  Then reinstall xscreensaver after doing "sudo apt-get --clean" To clean apt's cache.  ( I think thats the command).  Make xscreensaver your only option.  I found this more simple than messing  with permission blocking of gnome-screensaver.  However you will have to create a custom launcher for xscreensaver-demo, with the "Menu Editor" in System > Preferences > Menu.

Thanks,

_Nano

---

### Post by khelben1979 on 2009-05-08
Why this long guide? Why not just disable all the settings in Gnome Screensaver and then just install xscreensaver at make it default?

---

### Post by bschultzjames on 2009-05-22
Thanks for this tutorial!  It's been very helpful.  


I still have one question.  Is there a way to set xscreensaver as the default screensaver?  I followed the directions listed and I *still* have to run xscreensaver once to deactivate gnome-screensaver.  [When I run xscreensaver I get fun warnings asking me if I would like to disable gnome-screensaver and I happily click "okay" each time :)].

Again:  is there a way to permanently set up xscreensaver as the default screensaver and COMPLETELY disable gnome-screensaver?


Thanks!
-b

---

### Post by javyn999 on 2009-06-07
Hrm, has anyone else noticed that the Xscreensaver freezes in Jaunty?  I want 4 cows bouncing at once dang it.  I have a Geforece 6200 256 meg agp8x video card, I'd assume it can handle a measly 4 bouncing cows with compiz enabled!

---

### Post by Bob63 on 2009-06-07
> **javyn999 said:**
> Hrm, has anyone else noticed that the Xscreensaver freezes in Jaunty?  I want 4 cows bouncing at once dang it.  I have a Geforece 6200 256 meg agp8x video card, I'd assume it can handle a measly 4 bouncing cows with compiz enabled!

Well, I'm using Jaunty and it works fine for me with one or several cows, and fast or slow bounce rate. I have an on-board NVIDIA GPU (NVS 210S/GeForce 6150LE) using Compiz and I have the proprietary NVIDIA driver activated as well.

System>Preferences>Appearance is set to normal, and I'm not using very many Compiz effects.

Sorry to say the problem appears to be in your settings somewhere. Do you have many Compiz effects selected?

---

### Post by khelben1979 on 2009-06-07
delete my post here.

---

### Post by eladamri on 2009-06-10
I love the HowTo.

Does anyone know how I can get the F-Spot screensaver working within xscreensaver?

---

### Post by stormzen on 2009-07-03
I saw xscreensaver freeze.  I think it happened when gnome power settings kicked in.  Since the guy working on gnome-screensaver is so religious about his approach to the application, I think Ubuntu should make xscreensaver the default.  It should work with gnome power settings.  The only thing I did differently ( as far as I know ) is set it so that the monitor never blanked out.

---

### Post by javyn999 on 2009-07-04
My problem was not the screensaver after all.  I disabled the sleep/hibernate settings in the power options and all works well.

---

### Post by ghibli on 2009-10-18
Thank you so much for your ADVICE!

---

### Post by itsguardianjon on 2009-12-22
this is going to sound like im repeating wat was said earlier but i did all of the above and no i cant get rid of xscreensaver daemon doesn't seem to be running on display ":0.0"

---

### Post by Huufarted on 2010-02-12
It looks like gnome-screensaver is no longer a dependency for ubuntu-desktop.  Looks like we can just apt-get remove gnome-desktop now without affecting ubuntu.

---

### Post by mattkerle on 2010-05-24
> **itsguardianjon said:**
> this is going to sound like im repeating wat was said earlier but i did all of the above and no i cant get rid of xscreensaver daemon doesn't seem to be running on display ":0.0"

any response on this issue? I went through the howto, then rolled it back but I'm getting this error message so I'm guessing I missed something, but I don't know how to troubleshoot...

I can now lock my screen from <username>->lock screen, but the keyboard shortcut doesn't work and if i try to run it from the command line I get this:
```
$ gnome-screensaver-command --lock
gnome-screensaver-command: no screensaver is running on display :0.0
```

(oh yeah, and I have this cool thing where the unlock dialog isn't visible behind the screensaver, so when I want to unlock the screen I have to ctrl+alt+del and just hope for the best!!!)

---

### Post by mattkerle on 2010-05-25
never mind, turns out that I had a dodgy version of the /usr/bin/gnome-screensaver-command from my hacking which I'd forgotten about, swapped it back to the original and all is now well, super+L works just fine again :-)

Still have the amazing invisible login screen though, which seems to be related to running the GLMatrix screensaver, in fact it seems to be most if not all the GL* screensavers and some of the others, such as StarWars.

Screensavers that don't include: Halo, Hypercube, Grav, IFS etc

I've still got the xscreensavers extras pack installed, so I'm thinking it may be something to do with openGL or the particular screenies involved?? except I seem to recall GLMatrix worked fine before I start messing with things..

---

### Post by Bob63 on 2010-05-25
Not trying to be a know-it-all, but I see that some folks are still having problems. The instruction in the first post are still reasonably valid even under lucid, and since I was able to make it work (and the xscreensaver package is much more recent now) I thought I'd offer a couple of suggestions.

This post is for those still having problems with xscreensaver not working - by not working I mean that when you run xscreensaver through the System > Preferences > Screensaver, you get the message about it not running on Display 0:0.

Make sure the screensaver **startup** launcher is correct in the command it issues. You make this launcher through System > Preferences > Startup Applications. The command line it issues should be:

```
xscreensaver -nosplash
```xscreensaver is the name of the command line executable which launches the daemon. If you installed the xscreensaver package from the repos, then the executable file is in the path, so no need to add any part of the path.

Also, the menu entry launches the gui which allows you to configure both general settings for xscreensaver and to tweak setting for nearly all the individual screensavers. The command which the menu entry uses is different:

```
xscreensaver-demo
```If you are unsure that gnome-screensaver is disabled, one way to check without launching xscreensaver (and so not getting the warning about gnome-screensaver still running or the xscreensaver daemon not running) is by using the system monitor at System > Administration > System Monitor. Select the **Processes** tab, and scroll down the list and see if gnome-screensaver is listed. If you have clicked on the column header for **Process Name**, the list will be in alphabetical order. Similarly, if the xscreensaver daemon was successfully launched, there will be an entry for it in this list.

---

### Post by otternox on 2010-06-12
Have any of you looked here? 
[http://software.xfx.net/utilities/sss/index.htm](http://software.xfx.net/utilities/sss/index.htm)

After installing this .deb, you can use gnome-screensaver and change all the settings you want.  At least that worked a year ago.  Now I can't get it to work on 10.04.

Can anyone else try this?

---

### Post by chiliman on 2010-06-12
Thank you for this how-too.  Instructions on first post worked perfectly for me on lucid.
configuring the screen savers = win \\:D/

---

### Post by mattkerle on 2010-06-17
with screensaver-settings did anyone get that working? I installed it but the doco for how to actually run the thing was non-existant?? maybe I'm missing something obvious but it didn't seem to replace the existing screensaver applet, or add a new menu entry anywhere i could see, or show up on the PATH, so uninstalled it as a waste of time.

maybe I'm lacking mono? it's written in C# of all things...

---

### Post by lordawesome on 2010-09-19
Giggity... Works like a charm on my ancient p4!!!

---

### Post by JaradT on 2010-10-26
I got it working.
Hopefully I don't screw anything up.

---

### Post by bmo92663 on 2010-11-10
:guitar: Thanks man, worked like a charm.

---

### Post by cpaul on 2010-11-29
> **dhasenan said:**
> If you want System->Quit->Lock Screen to work, just do this:
```

$ sudo ln -f /usr/bin/xscreensaver-command /usr/bin/gnome-screensaver-command
```

after following the rest of that guide. The query, throttle, and unthrottle flags from gnome-screensaver-command won't work, though.

This won't work at least in Gnome 2.22.3.  

The 'Lock Screen' actually only send a dbus request to invoke the lock method of the dbus object org.gnome.ScreenSaver.

Since you have disabled the gnome-screensaver, the dbus object org.gnome.ScreenSaver is not created while the Gnome starts. 

We need to create the dbus object org.gnome.ScreenSaver and implement the Lock method.

I use the below python script to create the org.gnome.ScreenSaver.

----------- myscreen-dbus.py --------
```

#!/usr/bin/python

import dbus
import dbus.service
import dbus.glib
import gobject
import os

class ScreenDbusObj(dbus.service.Object):
    def __init__(self):
        session_bus = dbus.SessionBus()
        bus_name=dbus.service.BusName("org.gnome.ScreenSaver",bus=session_bus)
        dbus.service.Object.__init__(self,bus_name, '/org/gnome/ScreenSaver')

    @dbus.service.method("org.gnome.ScreenSaver")
    def Lock(self):
        os.system( "xscreensaver-command -lock" )


if __name__ == '__main__':
    object=ScreenDbusObj()
    gobject.MainLoop().run()

```

You should keep this script running on the background. The 'Lock Screen' button will call the method Lock and the method Lock will execute the xscreensaver-command -lock.

To automatically start this script, you need to add the command, i.e. /path-to-the-script/myscreen-dbus.py & in the System/Preferences/Sessions.

Furthermore, the options is used by xscreensaver-command and gnome-screensaver-command for lock is different.  For xscreensaver-command, the option is -lock. But for gnome-screensaver-command, the option is --lock ( there are two hyphen before the 'lock').

---

### Post by tracyjames on 2010-11-30
didnt work for me :(   im using ubuntu 10.04 dual booted with win7,

intel i5, 4gb RAM, 500GB SATA, Nvidia 9600gt

did i go wrong somewhere ? or its unavaible in 10.04 ?

---

### Post by Bob63 on 2010-11-30
> **tracyjames said:**
> didnt work for me :(   im using ubuntu 10.04 dual booted with win7,

intel i5, 4gb RAM, 500GB SATA, Nvidia 9600gt

did i go wrong somewhere ? or its unavaible in 10.04 ?
what didn't work? xscreensaver in general or the lockscreen function.

---

### Post by l300lvl on 2011-11-04
i was just curious if anyone's been able to get the dpms working properly after switching to xscreensaver, it seems that no matter what i try, removing gnome-screensaver or just disabling it and/or certain power management settings in gconf, when the display is suspended/goes to sleep, via dpms, i get hard locks. so my only choice was to remove xscreensaver altogether and revert to gnome screensaver.

---

### Post by ba0bab on 2012-07-29
Excellent, worked like a charm. This is Ubuntu and it's helpful community at it's best!

---

### Post by jhansonxi on 2012-08-05
Has anyone been able to use myscreen-dbus.py (comment #94) on Ubuntu 12.04 (Precise Pangolin)?  When it's running it doesn't seem to exist on dbus:
qdbus org.gnome.ScreenSaver /ScreenSaver org.gnome.ScreenSaver.Lock

Error: org.freedesktop.DBus.Error.UnknownMethod
Method "Lock" with signature "" on interface "org.gnome.ScreenSaver" doesn't exist

---

### Post by rareish on 2012-08-07
very cool thanks for this little, how to:)

---

