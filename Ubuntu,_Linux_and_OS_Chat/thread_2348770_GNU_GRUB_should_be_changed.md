---
title: "GNU GRUB should be changed"
date: 2017-01-07
forum: Ubuntu, Linux and OS Chat
---

### Post by thecrazydude778 on 2017-01-07
Hello!

So here is a simple question. 
Why does the GNU GRUB **screen** exist?

What I mean by this is that why does the GNU GRUB have to have a screen. Yes, the GNU GRUB cannot be removed as it boots Ubuntu (No GNU GRUB = No Ubuntu) but that's why I specifically said** _screen_** as the _**screen**_ doesn't have to be there. Why can't it be something like a loading BIOS screen where the system would boot normally unless your press F12 or the Delete Key to enter the BIOS configuration or the Boot Device Selection. It would make it simpler as there is no Enter key that needs to be pressed and even though you don't have to press a key with the GNU GRUB you still have to wait at least 7 to 30 seconds for the loader to select the highlighted setting.

So why doesn't the GNU GRUB do a similar thing? If this was how the GNU GRUB would work, when you boot up you would be greeted with a simple screen that would say something like Ubuntu Boot Loader and that screen would disappear within 3 seconds unless you press a button if you press a button* **then*** it would give you the normal selection screen like the GNU GRUB does normally. It would improve boot times specifically on installations when the GNU GRUB takes 30 seconds to automatically select the default. It would be convenient to people who have slow boot times on their computer just to save a couple of seconds. If Windows can do it so can Ubuntu (I think). 

So it would change from having to press the Enter key at a good old GRUB screen (or waiting a couple of seconds) to not having to do anything at all. There isn't much of a difference other then a couple of seconds but I always hate having to see the plain and old looking GNU GRUB screen. It isn't much as many people don't even think about the GRUB much at all.

Another thing to point out is that you probably can change the time of when the default selection is selected but that would be hard for first time users unless a program was created to shorten the GNU GRUB selection time. That might exist but there would still be a little bit harder for people who are new as they would have to either get a Debian package which is easier (unless software center's not working) or they would have to use the terminal which unless they have clear, easy to follow instructions; might be a bit to hard for people that haven't tried Ubuntu before.

I just wanted to make this thread just to see what other people would think about the idea and if it was possible to actually make something like this in an actual Ubuntu release.

So what do you think about this idea? Do you think that the GRUB should be revamped to a more User-Friendly interface (Not having to touch anything)? Do you think that the GRUB is fine just the way it is?

Thanks for reading!

---

### Post by ajgreeny on 2017-01-07
Think what would happen to most new users who did not know about grub, nor anything else about Ubuntu in a dual boot situation and who wanted to boot their existing OS until they became more familiar with Ubuntu.

They would have to search for a way to boot to the more familiar Windows OS, which as things are now would be automatically shown to them in what you are calling the grub screen, ie, the grub menu.

For those who know what they are doing and have used Ubuntu for some time it is easy to change the grub settings so as to not show the menu, if that is your wish.

I see no reason to change anything from how it is at present.
"If it ain't broke, don't fix it!"

---

### Post by oldfred on 2017-01-07
If you only have Ubuntu installed that is the default. No grub screen.
We get many threads where users then need to get to grub menu to add kernel boot options or use recovery mode. You then have to hold shift key with BIOS or press Escape Key (perhaps more than once) if UEFI.

You can also change delay, but we do not normally suggest 0 as then you cannot get to grub menu ever.
[https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2](https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2)
> 
[LIST]
[*]**GRUB_HIDDEN_TIMEOUT=0** 


[LIST]
[*]No menu is displayed. The system is immediately booted to the default OS. 
[*]This is the default setting with only one identified operating system. 
[LIST]
[*]To display the menu under this condition, place a *#* symbol at the start of the line and ensure the GRUB_TIMEOUT setting is a positive integer. 
[/LIST]

[*]If the value is set to *0*, a *keystatus* check is performed to determine if the *SHIFT* key is depressed. If GRUB 2 determines the *SHIFT*  key is depressed during the boot process, the menu will be displayed.  This gives the user a method of interrupting an automatic boot which  would normally not display the menu. 
[/LIST]

[*]
[/LIST]


       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

---

### Post by thecrazydude778 on 2017-01-07
I didn't really think about people who dual boot as I usually just use Ubuntu but that is a very good point about people who would probably use Windows as well as Ubuntu. Also, I'm probably going to check out who to change the delay. Also, it looks like it kind of already has a loading BIOS screen idea as oldfred pointed out with holding down the Shift key or mashing the delete key. 

Another thing to point out...
> "If you only have Ubuntu installed that is the default. No grub screen."

That doesn't make much sense to me as one of my computers (running Ubuntu only) still has a GRUB screen when booting up even though no other operating systems other than Ubuntu have been installed. However, it might have been the installation as when it first started up it was acting a bit strange but I'll probably update (or reinstall) the latest version of Ubuntu on it anyway and see if that fixes the problem.

Also thanks for the link I'll probably try reducing the delay later.

Thanks.

---

