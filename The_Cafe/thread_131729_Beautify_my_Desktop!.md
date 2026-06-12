---
title: "Beautify my Desktop!"
date: 2006-02-17
forum: The Cafe
---

### Post by Seandq on 2006-02-17
[img]http://qcast.org/snapshot1.png[/img]
I need help. As you can see, my desktop is rather basic. I want to have some features added in like other users do in the Desktop Thread, like cool graphics, and transparency that looks good, and little widgets.

Help me out, what's the best way to beautify my desktop?

---

### Post by Stormy Eyes on 2006-02-17
Next time, please upload your screenshot to the Gallery and post a link in the thread. Some of us still have dialup.

---

### Post by Seandq on 2006-02-17
Sure. I'll do that now. I noticed the size and I'm trying to get it down.

I'll have it smaller in a second. Sorry about that.

---

### Post by Stormy Eyes on 2006-02-17
It's OK. I've got cable myself, but I still remember what it's like to use dialup.

---

### Post by Seandq on 2006-02-17
That better?

---

### Post by mstlyevil on 2006-02-17
If you want transparencies, shadows and fade effects there are several ways to do that. First off it only works with Nvidia 3D graphics cards and the latest drivers. If you use a ATI card or have a legacy Nvidia card or onboard graphics, transparencies are out of you reach. (They are possible but may degrade system performance because your system memory and your CPU have to make up the slack of the video.) If you have a Nvidia card then you should already be good to go in KDE.

I hope this reply helps and good luck. :-D

Edit: I just noticed you already have Kubuntu installed. These features are already included in Kubuntu. Also the widgets will be different. If I am not mistaken they are called super karamba in Kubuntu. You may need to install the bagharia theme for everything to intergrate properly. You should be able to find both SK and Bagharia in synaptic. To turn on transparancies you will need to go to the KDE control center and select desktop -> window behaviour -> transluency then put a check mark in use transluencies. That will enable the effects you are looking for

---

### Post by fuscia on 2006-02-17
you need to get yourself some pretty icons, son. [http://www.kde-look.org/content/show.php?content=24645](http://www.kde-look.org/content/show.php?content=24645)

---

### Post by equal on 2006-02-17
Yeah just in general, [www.kde-look.org](www.kde-look.org) is a good place to go. There's themes, icons, desktop pics, everything you could ever want to customize the look.

---

### Post by TeeAhr1 on 2006-02-17
sudo apt-get install xdesktopwaves
sudo apt-get install 3ddesk

See this thread for [xdesktopwaves ]("http://www.ubuntuforums.org/showthread.php?t=112333")info, this one for [3ddesktop switcher]("http://www.ubuntuforums.org/showthread.php?t=100169")

Yes, I have squandered most of my non-working week playing with this stuff (and xcompmgr, but you're running KDE so you don't need to mess with that).

---

### Post by jobezone on 2006-02-17
superkaramba !

---

### Post by Seandq on 2006-02-18
OK. Terrific, I'm not at my Ubuntu desktop at the moment, but I will institute that as soon as I can.
 
But tha's just KDE. What would I d to my GNOME desktop to beautify it?
 
I just want to know in case I need to use it.

---

### Post by mstlyevil on 2006-02-18
[QUOTE=Seandq]OK. Terrific, I'm not at my Ubuntu desktop at the moment, but I will institute that as soon as I can.
 
But tha's just KDE. What would I d to my GNOME desktop to beautify it?
 
I just want to know in case I need to use it.[/QUOTE]

Use this guide here. It will involve replacing Metacity with Kwin (KDE's window manager) This is the one I used to get those effects.

[Knome Guide Stealing KDE's Eye Candy]("http://doc.gwos.org/index.php/KnomeGuide")

Edit: You will want to install gdesklets either with Automatix or through apt-get (Synaptic or the command line) for the widgets.

```
sudo apt-get install gdesklets
```

You can go to gnomelook.org to get the themes and icons.

---

### Post by ice60 on 2006-02-18
i like this

> 4. HOWTO: CHANGE GTK THEMES AND ICONS FOR ROOT APPLICATIONS
Are you tired of that your root applications doesn't match your desktop theme?

[img]http://ubuntuforums.org/attachment.php?attachmentid=621&d=1112604992[/img]

Here's the answer, with these codes your root applications gets the same theme, icons and fonts.


```
sudo ln -s /home/<insert your username here>/.themes /root/.themes
sudo ln -s /home/<insert your username here>/.icons /root/.icons
sudo ln -s /home/<insert your username here>/.fonts /root/.fonts
```

it's from [here](http://www.ubuntuforums.org/showthread.php?t=77694)

---

### Post by Seandq on 2006-02-19
Thanks for all the great information!

---

### Post by mstlyevil on 2006-02-19
[QUOTE=Seandq]Thanks for all the great information![/QUOTE]

No problem. Did any of it work for you? If so could you please post a screenshot in the desktop thread.

---

### Post by Seandq on 2006-02-19
At this time, I'm on a rattedy 200MHZ Pentium I with dial-up at my grandparents in New Jersey since my grandma just passed away. I will do the eye candy when I get home tomorrow and then post a screenshot.

---

### Post by jobezone on 2006-02-19
Eh, no hurry. Take your time.

---

### Post by Seandq on 2006-02-20
Here's my new KDE Desktop. It looks bad, because Xdesktopwaves is running.

[http://ubuntuforums.org/showthread.php?p=755819&posted=1#post755819](http://ubuntuforums.org/showthread.php?p=755819&posted=1#post755819)

---

### Post by mstlyevil on 2006-02-21
[QUOTE=Seandq]Here's my new KDE Desktop. It looks bad, because Xdesktopwaves is running.

[http://ubuntuforums.org/showthread.php?p=755819&posted=1#post755819](http://ubuntuforums.org/showthread.php?p=755819&posted=1#post755819)[/QUOTE]

Good job.

---

### Post by Sirin on 2006-02-21
```
sudo apt-get install xdesktopwaves
sudo apt-get install 3ddesk
sudo apt-get install xcompmgr
sudo apt-get install gcompmgr
sudo apt-get install superkaramba
```

Eye candy is good for you! :-D

---

