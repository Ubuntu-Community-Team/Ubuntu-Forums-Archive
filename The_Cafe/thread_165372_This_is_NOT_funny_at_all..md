---
title: "This is NOT funny at all."
date: 2006-04-24
forum: The Cafe
---

### Post by snellgrove on 2006-04-24
[img]http://static.flickr.com/54/134279694_96ed85bf47_o.png[/img]

I really may as well go back to using Windows if its going to say this after every time I run apt-get update / upgrade.

why why why oh why, did they make a stupid pop up thing like this. Its scary.

:rolleyes:

---

### Post by Rikostan on 2006-04-24
It's not after every single update... only the major ones.

 Not sure why it scares you though.

---

### Post by awakatanka on 2006-04-24
Whehehe funny stuff. 

Gnome xp :mrgreen:

---

### Post by MetalMusicAddict on 2006-04-24
[QUOTE=snellgrove]I really may as well go back to using Windows if its going to say this after every time I run apt-get update / upgrade.[/QUOTE]
Bye.

---

### Post by mr_frodo on 2006-04-24
what's wrong with that?

---

### Post by helpme on 2006-04-24
Keep in mind that dapper is still not stable so you'll get a lot more updates then you will with the stable version.

That said, though I can see the reasoning behind it, I really don't like that I now get the message to restart my computer though only some service needs to be restarted.

---

### Post by engla on 2006-04-24
When does this occur?

I dist-upgraded with aptitude today and my kernel was updated.. I haven't see that warning. And btw,** you can say no.** (In OSX with those warnings, you can force kill the program via the dock and continue. In Windows, you just have to comply...)

---

### Post by Rikostan on 2006-04-24
[QUOTE=engla]When does this occur?

I dist-upgraded with aptitude today and my kernel was updated.. I haven't see that warning. And btw,** you can say no.** (In OSX with those warnings, you can force kill the program via the dock and continue. In Windows, you just have to comply...)[/QUOTE]




I saw it yesterday when updating a Dapper Beta box after a kernal update, but I have never seen in in Breezy as far as I recall.

Actually in Windows you can restart later a lot of times too, but lately they have made the box pop up every 15 minutes or so and remind you to reboot.

---

### Post by awakatanka on 2006-04-24
[QUOTE=engla]In Windows, you just have to comply...)[/QUOTE]
Can kill the process to. If you don't have it on automate

---

### Post by Stormy Eyes on 2006-04-24
Chances are that you got a kernel update. When I update the kernel via GNOME's "Update Notifier" on dapper, I get that message as well. You can say no and continue on your merry way.

---

### Post by snellgrove on 2006-04-24
Yeah, the sole reason I have auto-updates not running on my PC @ work (XP) is the constant (and therefore, extremely annoying) reminders about rebooting.

The reason I find this "reboot" reminder annoying, is because I know it doesn't need it for most of the time, Ubuntu is a proper O/S. It doesn't require to be constantly rebooted for small changes to the O/S to take effect. When the kernel changes, thats fine.. but when something minor changes, and it tells me to reboot.. bah it annoys me. The not so literate out there will think this is how PC's are: things that need rebooting constantly.

---

### Post by prizrak on 2006-04-24
Breezy gets the same kind of pop up as well after kernel upgrades. That makes perfect sense to me actually, kernel can't be applied w/o a restart :) 
As far as restarting just one service, we are trying to convince people that Ubuntu is easy to use and is suitable for non techies. Now how many non-techies do you know that can restart a service (or even know what a service is). I guess a more sane policy would be restarting the service in the background and only pop up things like that for kernel upgrades. As said before Dapper is not complete yet, it needs a little bit of polish.

---

### Post by adamkane on 2006-04-24
Most users like to keep all their apps open all the time. It's ill-advised, but widespread.

---

### Post by Kindred on 2006-04-24
That would annoy me too.. kernel upgrade or not.

---

### Post by GreyFox503 on 2006-04-24
I'm ok with this, but I think they should tell you why you're being recommended to reboot.  If you downloaded a new kernel, it should just say so!  I've seen a lot of people mention it around here.

[quote=Rikostan]Actually in Windows you can restart later a lot of times too, but lately they have made the box pop up every 15 minutes or so and remind you to reboot.[/quote]

No, anything but that!  Whoever thought this was a good idea.... well you can finish that sentence.  I hope this never happens to Ubuntu.

---

### Post by woedend on 2006-04-24
hey guys...i know this is a matter of "by default", but its very easy to remove this and other annoying things...its the first thing I do when I install.  Remove update-notifier and notification-deamon, both are which annoying to me.  If  you want to keep the metapackage for some reason, you don't have to remove them, just make them inexecutable.

---

### Post by Stormy Eyes on 2006-04-24
[QUOTE=GreyFox503]I'm ok with this, but I think they should tell you why you're being recommended to reboot.  If you downloaded a new kernel, it should just say so!  I've seen a lot of people mention it around here.[/QUOTE]

Normally, I wouldn't care enough to ask this, but I can't resist playing Devil's Advocate: does Grandma know what a kernel is?

---

### Post by jasay on 2006-04-24
[QUOTE=woedend]just make them inexecutable.[/QUOTE]That's genius.  I love file permissions!:D

 . . . off to break my computer with inappropriate file permissions.

---

### Post by prizrak on 2006-04-24
> That would annoy me too.. kernel upgrade or not.
Why? You might know to need a restart but someone else wouldn't, this one of those things that make the OS easier for non techs. If you are a tech you can easily disable it no one is stopping you. This is what I really don't understand about some of the techies, in a system where defaults can easily be changed, why be annoyed about them? The defaults are there to make the system as easy/stable/usable/informative as possible w/o requiring a computer science degree. After all Ubuntu aims to be easy to use for non-techs and powerful and customizeable enough if you are on the techie side. 
> Normally, I wouldn't care enough to ask this, but I can't resist playing Devil's Advocate: does Grandma know what a kernel is?
I'm with Stormy on this.

---

### Post by jimcooncat on 2006-04-24
Need a better balance on the wording. 

"Tux has been fortified with new armor, but the computer needs to be restarted for him to use it!" 

No, that's not it.

---

### Post by teet on 2006-04-24
[QUOTE=Rikostan]I saw it yesterday when updating a Dapper Beta box after a kernal update, but I have never seen in in Breezy as far as I recall.

Actually in Windows you can restart later a lot of times too, but lately they have made the box pop up every 15 minutes or so and remind you to reboot.[/QUOTE]

This is off topic, but you can change that 15 minute interval in windows to something larger.  I believe you go to start-->run and type gpedit.msc  I think the setting is hidden somewhere in there.  I changed it to be like 1000 minutes or something.

Back to the topic, I don't see a problem with this warning.  I've only seen it once or twice and it was after a kernel upgrade.  Windows wants me to reboot after every single little update.

-teet

---

### Post by Orunitia on 2006-04-24
[QUOTE=snellgrove]
I really may as well go back to using Windows if its going to say this after every time I run apt-get update / upgrade.

:rolleyes:[/QUOTE]

Sorry but if you're using linux because it doesn't ask you to restart after every update, you're using it for the wrong reasons. :P

---

### Post by krusbjorn on 2006-04-24
[QUOTE=Orunitia]Sorry but if you're using linux because it doesn't ask you to restart after every update, you're using it for the wrong reasons. :P[/QUOTE]

Yeah, and the kernel wont be updated very often once Dapper goes stable, so it's not a big issue.

---

### Post by Stone123 on 2006-04-24
[QUOTE=snellgrove]
I really may as well go back to using Windows if its going to say this after every time I run apt-get update / upgrade.

why why why oh why, did they make a stupid pop up thing like this. Its scary.

:rolleyes:[/QUOTE]
?
If there is security issue that needs a reboot wouldent you reboot?
This "i am going back to windows" will never work here so keep it up then.

---

### Post by DJ_Max on 2006-04-24
[QUOTE=Orunitia]Sorry but if you're using linux because it doesn't ask you to restart after every update, you're using it for the wrong reasons. :P[/QUOTE]
Couldn't have said it better myself.

BTW, you do know you can click *Restart Later*? That isn't too scary.

---

### Post by jobezone on 2006-04-24
"Please make sure that you save all your work before restarting". Yes, and please don't dry your hands in the oven.

(EDIT: :-) )

---

### Post by woedend on 2006-04-24
[QUOTE=jasay]That's genius.  I love file permissions!:D

 . . . off to break my computer with inappropriate file permissions.[/QUOTE]

Lol...its not going to break your computer.  I made 5 or 6 things(gnome-screensaver,gnome-power-manager,sshagent,updatenotifier)  are 4 I remember, I believe there were two more.  Anyhow, I made all those unexecutable for a couple months, only it was annoying to redo it every time they were upgraded. Now that I think Dapper is close to being finished, I dont worry about the metapackage and just remove them all.

---

### Post by jasay on 2006-04-24
[QUOTE=woedend]Lol...its not going to break your computer.  I made 5 or 6 things(gnome-screensaver,gnome-power-manager,sshagent,updatenotifier)  are 4 I remember, I believe there were two more.  Anyhow, I made all those unexecutable for a couple months, only it was annoying to redo it every time they were upgraded. Now that I think Dapper is close to being finished, I dont worry about the metapackage and just remove them all.[/QUOTE]Haha.  I wasn't really worried about it.  More just suggesting that I was so excited that I was going to go try it out.  Worst that could happen is a note in a log file, right?  Or I guess a pop up like when a panel applet fails to load.

I think I'll write a script to de-executable-ize a number of packages once Edgy hits the repos.  I don't like removing ubuntu-desktop since I basically live on the devel versions of ubuntu.

---

### Post by woedend on 2006-04-24
removing ubuntu-desktop isn't too bad though, because if packages are added or removed, you can tell.  Basically, just remove everything you need to, then periodically try to install ubuntu-desktop via synaptic, it will list everything thats to be installed/removed.  If you notice anything other than what you originally removed to be installed or removed, click cancel and manually install/remove what needs to be.  
However, that script is a good idea.  Is it possible to chmod -x  multiple files at once or must you make a new line for each single program to be done?
for instance, would chmod -x /usr/bin/updatenotifier, /usr/bin/sshagent           work to undo both?  Either way, that sounds like a good idea.  I could just have it run everytime i restart

---

### Post by prizrak on 2006-04-24
According to the man entry for chmod its per file :)

---

### Post by briancurtin on 2006-04-24
this thread is pretty funny

---

### Post by benplaut on 2006-04-24
[QUOTE=jimcooncat]"Tux has been fortified with new armor, but the computer needs to be restarted for him to use it!"[/QUOTE]

you're a damn genious :mrgreen:

---

### Post by YourSurrogateGod on 2006-12-10
This can be irritating at times. However, I can understand it if it's a major kernel update/upgrade. It's possible to check beforehand as to what you're updating.

On another hand, it would be really cool if one could dynamically move the kernel in and out of memory without having to reboot the bloody thing.

---

### Post by Jessehk on 2006-12-10
How about something like:

"The kernel, the core of the operating system, which is responsbile for the majority of the processes of your computer has been updated. Your computer will have to be restarted."

?

---

### Post by prizrak on 2006-12-10
> **YourSurrogateGod said:**
> This can be irritating at times. However, I can understand it if it's a major kernel update/upgrade. It's possible to check beforehand as to what you're updating.

On another hand, it would be really cool if one could dynamically move the kernel in and out of memory without having to reboot the bloody thing.

That is possible with a microkernel. If HURD ever reaches a level of usefulness it will be able to do it. Linux is a monolithic kernel so it has to be restarted. I personally don't see much issue, kernel upgrades are few and far between. Unlike Windows Ubuntu doesn't force you to restart so you can just keep working and shut down at the end of the day instead of keeping the system running through the night.

---

### Post by darkhatter on 2006-12-10
> **snellgrove said:**
> [img]http://static.flickr.com/54/134279694_96ed85bf47_o.png[/img]

I really may as well go back to using Windows if its going to say this after every time I run apt-get update / upgrade.

why why why oh why, did they make a stupid pop up thing like this. Its scary.

:rolleyes:

you need to do some reading, its  kernel update ](*,)

---

