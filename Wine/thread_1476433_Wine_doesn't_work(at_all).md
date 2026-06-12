---
title: "Wine doesn't work(at all)"
date: 2010-05-07
forum: Wine
---

### Post by N_L on 2010-05-07
For past few day's I've been trying to get wine to work and no progress so far.
I'm using 10.4 ubuntu 64bit and downloaded wine from their website, 1.1.43 version it says.
First thing first, notepad and internet explorer do work.
Secondly, at first I managed to install applications but not to run them. Icon just pops at start bar and says loading and then disappears. Now I can't even install them. In terminal it gives me some cXXXXX error and with right click>run with wine it does same thing like when I tried to install it.
And yes, I've tried several different programs to install.
Never used wine before and it's on default settings.

And now that I think of it, I think I managed to run 1 application once, didn't work any more after that try hmm.
I uninstalled completely and installed several times.

Don't know what else to do, any ideas?

---

### Post by cogadh on 2010-05-07
What applications are you trying to run? Did you check [AppDB]("http://appdb.winehq.org/") to see if they are compatible with Wine? Have you run any of these apps from the terminal to get Wine's error message and if so, what *exactly* did they say? Have you tried deleting your .wine directory and starting over with a fresh configuration?

---

### Post by N_L on 2010-05-07
Tried installing some small apps from download.com, got irfanvew still on desktop and tried teamspeak. Got any suggestions of some I should download to try?
Beside that I want to install Bioshock and secret of monkey island special edition(tried this too). Maybe WoW too, we'll see.
I did clean .wine directory several times before installing it again.

Fixed terminal error, was missing .dll which I got with winetricks. But running it gives same thing. Irfanview setup installed fine, no luck opening it, or uninstalling for that matter.
Gonna try to get 1 more app and try again..

Edit: Just to make it clear, those first 2 applications I only used for testing.

---

### Post by hikaricore on 2010-05-07
[http://appdb.winehq.org](http://appdb.winehq.org)

Pay attention.

P.S. Why are you trying to install teamspeak in wine when there is a native version?

---

### Post by Zireth ZH on 2010-05-08
> p.s. Why are you trying to install teamspeak in wine when there is a native version?

lol...

BTW some programs needs more than just a click on the setup.exe... u gotta tweak em a bit and it all matters on which program or game ur trying to run...

---

### Post by N_L on 2010-05-13
> **hikaricore said:**
> [http://appdb.winehq.org](http://appdb.winehq.org)

Pay attention.

P.S. Why are you trying to install teamspeak in wine when there is a native version?

> **Zireth ZH said:**
> lol...
I know it works, it just came up on my mind and I wanted to test it. Anyhow just installed MS office and it works so problem solved I guess, gotta find out how to install those specific programs I need. (bioshock)
BTW some programs needs more than just a click on the setup.exe... u gotta tweak em a bit and it all matters on which program or game ur trying to run...
Yeah, gotta learn what to do. 

Thanks all

---

### Post by N_L on 2010-05-14
I had to reinstall one program and I decided to reinstall wine along the way... Bad decision. Now after reinstalling several times can't run anything with wine, not just programs but configuration, uninstall etc. Also folder .wine is now locked and can't delete it and it doesn't show when I run sudo nautilus...
Anyone got idea? Really need this fixed becausue I need it to work for classes in few hours :(

rm: cannot remove `/home/nolimit/.wine/dosdevices/y:': Permission denied
rm: cannot remove directory `/home/nolimit/.wine/dosdevices/c:/winetrickstmp': Permission denied

Edit: ```
chmod -R u+rw $HOME/.wine
``` fixed it. Let's see if I can get it to work.

All works well, sorry for alert :p

---

### Post by cogadh on 2010-05-16
That probably happened because you ran Wine using sudo. Never EVER do that. Wine is designed to be used with normal user permissions only, not admin or root permissions. Also, the .wine directory is a hidden directory. In order to see it in Nautilis, you need to show hidden files by pressing ALT+H.

---

### Post by HC48 on 2010-05-17
Hello,
 I'm a beginner but used Wine ok in Karmic with irfanview, Cdex, Unfreez and Hot potatoes. 
I now have problems in Lucid getting irfanview to work in Wine. Unfreez is working but I haven't tried the other programs yet.I have got PlayOnLinux and tried to get an older version of Wine as advised in another thread:

[http://ubuntuforums.org/showthread.php?t=1466070&highlight=F-spot](http://ubuntuforums.org/showthread.php?t=1466070&highlight=F-spot)

because my first problem was F-Spot (which I have abandoned).   I have downloaded Wine 1.1.36 with PlayOnLinux but I think I still have the latest version of Wine functioning as my downloads of Irfanview (new and old versions) will not start. I have allowed the execution in iview 'permissions' and configured Wine for this program to no avail. It doesn't seem to be in the approved list on the Wine site,but it worked very well in Jaunty. I'm no good with the terminal yet, still learning, and afraid to make a mess.The synaptic packets are Wine 1.1.44...
Anyway if it's too complicated to solve I shall give up. I have digicam but I did like Irfanview...
I will try the other programs meanwhile.
I'd be really grateful if anyone can explain/help (in simple terms :! please)
H :)

---

### Post by cogadh on 2010-05-17
You should really start your own thread with this issue as it has absolutely nothing to do with the topic of this thread.

---

### Post by HC48 on 2010-05-18
"I now have problems in Lucid getting irfanview  to work in Wine."

Sorry if my problem isn't relevant. I have looked in other threads too of course and have learned a few things here which helped anyway.
Have a good day.
H :)

---

