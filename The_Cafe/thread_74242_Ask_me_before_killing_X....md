---
title: "Ask me before killing X..."
date: 2005-10-11
forum: The Cafe
---

### Post by JimmyJazz on 2005-10-11
Does the fear of ever accidentally hitting ctrl+alt+backspace while working on a large project in gnome ever grasp you?  It does me since I do alot of graphic design work and often forget to save my work.  Perhaps to remedy this UBUNTU could add a simple dialogue asking whether you really meant to have X exit in such a promt and rude fasion.  To me it would make the desktop seem much more stable and a less scary place to be, just an idea though. Discuss...

---

### Post by A-star on 2005-10-11
you need to press 3 keys all together,
how accidental can this be?

I never have this problem and I think very few people will have the same problem.

---

### Post by GeneralZod on 2005-10-11
There's a chance that this would not be implementable by the GNOME devs alone; I suspect that CTRL+ALT+Backspace is responded to directly by X, circumventing any Window Manager you may be running, but I don't know for sure.

And, like the poster above me, I've also never managed to do this accidentally, so I feel quite safe as it is :)

Edit: VVV

Hello, teammate! :D

---

### Post by Knome_fan on 2005-10-11
Not exactly what you want, but you can disable ctrl+alt+backspace in your xorg.conf using the DontZap option. [http://www.x.org/X11R6.8.2/doc/xorg.conf.5.html](http://www.x.org/X11R6.8.2/doc/xorg.conf.5.html) If I understand this correctly, all you have to do is create a ServerFlags section and the turn the DontZap option to true: Section "ServerFlags" Option "DontZap" "true" EndSection Of course it doesn't ask you, it's simply disabled now. P.S.: I think the thread is very real. At least when I see myself doing graphic works I can imagine banging my head plus my fists on the keyboard and accidently hitting ctrl+alt+backspace

---

### Post by jatos on 2005-10-11
Hmm yes it does seem an inpropable mistake, who goes to make a habit of pressing three keys at the same time?

Though if you doing a lot of important work I would say just save reguarly; lets face it theres 101 things that could go wrong, with any PC so just make sure you save reguarly and where have an automatic backup system so that if something does go wrong you don't lose your stuff.

---

### Post by 23meg on 2005-10-11
just to share some paranoia: i wish gnome would ask me before powering down the computer.. see here -> [http://www.ubuntuforums.org/showthread.php?t=40663](http://www.ubuntuforums.org/showthread.php?t=40663)

---

### Post by Stormy Eyes on 2005-10-11
[QUOTE=JimmyJazz]Does the fear of ever accidentally hitting ctrl+alt+backspace while working on a large project in gnome ever grasp you?[/QUOTE]

No. I'm more likely to have a cat press his nose against my PC's power button and hold it long enough to shut the machine down. In fact, this has actually happened to me. Accidentally hitting CTRL+ALT+BACKSPACE has not.

---

### Post by primeirocrime on 2005-10-11
My keyboard has keys that get stucked, specially Ctrl and Backspace :), so that happened to me yeah, I would like to have a turnback point. And also the Cat prevention combo, she can mess everything up, from interrupting a dsl connection [she only needs to do the cat rubbing in the phoneline] to the power button hard reset.

---

### Post by -Rick- on 2005-10-11
I think nothing should intercept it. If, for example, something goes wrong and you can't see anything normally on your screen anymore a CTRL+ALT+BACKSPACE is handy...

---

### Post by nsa_767 on 2005-10-11
Even though I think it highly unlikely that one may press those keys accidentally, perhaps it isn't such a bad idea to disable them.... Think of all the recent Windows converts, who are so very used to pressing them.... LOL

---

### Post by Kimm on 2005-10-11
Just do like me and get obsessed of pressing ctrl+s all the time... Its rather anoying when I do it automaticly with a file that is on a floppy though ;)

---

### Post by Stormy Eyes on 2005-10-11
[QUOTE=nsa_767]Even though I think it highly unlikely that one may press those keys accidentally, perhaps it isn't such a bad idea to disable them.... Think of all the recent Windows converts, who are so very used to pressing them.... LOL[/QUOTE]

Who the hell uses CTRL+ALT+BACKSPACE on Windows? I understand CTRL+ALT+DELETE, but not the "Kill X now, dammit!" combo.

---

### Post by nsa_767 on 2005-10-11
Sorry, my apoplogies.... Haven't used windows in a while... LOL, even forget how to CTRL+ALT+DELETE.... Wonderful isn't it, forgetting such things... though a windows migrant might be more likely to CTRL+ALT+BACKSPACE accidently, since he was trying to CTRL+ALT+DELETE

---

### Post by poofyhairguy on 2005-10-11
I think that the developers would say "no ne should do it anyway." Its not really a feature that they would boast that you can restart the xserver.

---

### Post by Stormy Eyes on 2005-10-11
[QUOTE=poofyhairguy]I think that the developers would say "no ne should do it anyway." Its not really a feature that they would boast that you can restart the xserver.[/QUOTE]

No, I've always understood CTRL+ALT+BACKSPACE to be an emergency switch. "Thank you for pressing the self-destruct button. This X server will self-destruct in 3 minutes."

---

### Post by JimmyJazz on 2005-10-11
ctrl+alt+f1 works fine as an emergency switch for me.  Trust me the possiblilty of loosing all your X server program all in a split second will be an anxiety for many users (in the future) especially those that are much less linux savvy.
Actually I'm kinda a big hot key user so its not to unusual to press 3 keys all at once.  I really don't see a point in being able to kill X in such a hasty fasion when in an emergency one could just ctrl+alt+f1 into a terminal and kill GDM quite easily.  Ubuntu works so well most the time I never really have emergencys :)

---

### Post by doclivingston on 2005-10-11
I don't think making it bring up a confirmation dialog would be particularly helpful, because normally you want to use it when something has happened to X - you either it won't be able to bring up the confirmation dialog, or you won't be able to say yes.

As others have said, you can disable it with the DontZap option.

---

