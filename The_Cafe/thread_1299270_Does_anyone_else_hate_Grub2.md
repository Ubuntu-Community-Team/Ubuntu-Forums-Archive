---
title: "Does anyone else hate Grub2?"
date: 2009-10-23
forum: The Cafe
---

### Post by jbrown96 on 2009-10-23
I've upgraded to Karmic, and all I can say is that Grub2 is a huge PITA. Here were my first experiences with it.
Installed on my laptop, but I couldn't get the provided nvidia drivers to work. No problem, I'll get them directly from nvidia and install them. Everything goes fine, and I reboot. Unfortunately, something didn't work, and my system freezes on boot. No problem, I'll just boot in single user mode, which will keep X.org from loading. Wait, where's my grub prompt. Oooo, grub2 doesn't give you the menu unless there are multiple kernels or OSes on your machine. Seriously, there's no way I can change my boot parameters without enabling the grub menu, but I can't do that because my system won't boot??? I'm literally about to tear my computer apart at this point. Stuff like this drove me to Linux. I want my machine to do what I say when I say it, but grub2 has decided that I don't get to tell it how to boot. 
So get my LiveCD, and boot that up. There's no /boot/grub/menu.lst file. Instead there several configuration files. On grub1 all I had to do to get a menu was, change hiddenmenu to #hiddenmenu. Of course there's nothing like that. I think GRUB_HIDDEN_TIMEOUT_QUIET=false this is the line that I need to change, but I'm not sure, so I change three different lines. Now I need to run update-grub just so it will load these changes??? Are you mad! And of course I can't figure out how to run this command from a LiveCD because it doesn't know where grub2 is. 
This did me the menu that I needed, and I was able to fix my system very easily once I got to the terminal.
I have looked at grub since, and most of the changes make no sense to me. Instead of having all the menu items in a single file (a la /boot/grub/menu.lst), they have been moved to their own files. They are so complicated and filled with code that I can't even begin to understand them. I guess you wold add entries to /etc/grub.d/40_custom file. Seriously WTF! Why is this so complicated. There's no sample entries in here like grub1. That's really helpful; if you are adding another Linux system you can reference your current Linux entries and get an idea of the format, and it works for Windows as well because there is a Windows example in /boot/grub/menu.lst, but of course that has been eliminated in grub2. 

I understand why Ubuntu was hamstringed into switching to grub2; the grub developers wouldn't add support for ext4 to grub1. I just don't understand why it's so needlessly complicated. I was so frustrated trying to do something that, in the past, took adding a single character to a well-known file. The developers completely failed at making it easy to use. I was trying to help a user install Windows alongside Ubuntu the other day. I flatly told him to install windows first because grub2 is too difficult to add an entry for windows. That's completely unacceptable. Grub2 is the new newCoke.

---

### Post by Sealbhach on 2009-10-23
I wonder what happened to *Keep It Simple*, *Stupid*.

.

---

### Post by coolbrook on 2009-10-23
I don't hate it per se.  It did drop kick my Puppy partition, but I can wait for the the kinks to be ironed out.

---

### Post by rajeev1204 on 2009-10-23
I dislike it very much too.

I have helped atleast 10 people on irc with grub problems with four simple steps from a live cd

sudo grub

find /boot/grub/stage1

root  (hdx,y)

setup  (hdx)

But with karmic around the corner and many many new users,i dont think i can do that so easy.



rajeev

---

### Post by drs305 on 2009-10-23
For others that may face similar situations:
> **jbrown96 said:**
> Wait, where's my grub prompt. Oooo, grub2 doesn't give you the menu unless there are multiple kernels or OSes on your machine. 
Hold down the SHIFT key and the menu will appear.

> 
There's no /boot/grub/menu.lst file. 
It's been replaced by /boot/grub/grub.cfg but the file you edit is mainly /etc/default/grub

> 
Instead there several configuration files. On grub1 all I had to do to get a menu was, change hiddenmenu to #hiddenmenu. Of course there's nothing like that. I think GRUB_HIDDEN_TIMEOUT_QUIET=false this is the line that I need to change, but I'm not sure, so I change three different lines. 

/etc/defalt/grub >> Put a comment in front of this line:
# GRUB_HIDDEN_TIMEOUT=0

> 
Now I need to run update-grub just so it will load these changes??? Are you mad! 

# 1 Yes;  #2  I hope not.

> 
Instead of having all the menu items in a single file (a la /boot/grub/menu.lst), they have been moved to their own files. They are so complicated and filled with code that I can't even begin to understand them. 

The scripts are there for those that need or want them. By and large, most users can get by on just editing two files:
/etc/default/grub = Basic settings
/etc/grub.d/05_debian_theme = splash images

I truly do understand the frustration. For you, there wasn't a lot of documentation available. Today there are a lot of great posts and other sources put together by volunteers to make the transition less painful for others.

Most of of your experiences could have been made much less difficult had these been available when you transitioned. I offer them here to help those who follow:

[Grub2 - help.ubuntu.com]("https://help.ubuntu.com/community/Grub2")

[Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275")

[Grub 2 Introduction]("http://ubuntuforums.org/showthread.php?t=1285897#post8072444")

[Illustrated Dual Boot Site (Herman)]("http://ubuntuforums.org/showthread.php?t=1285897#post8072444")

[Grub 2 - A Guide for Users]("http://kubuntuforums.net/forums/index.php?topic=3106368.0")

---

### Post by murderslastcrow on 2009-10-23
I actually like that it doesn't show up unless you have more than one option. :3 Just goes straight through. In my experience it's just as useful. Not sure if all the new features are all that great since I haven't really investigated them, but I've heard that it has a lot of unnecessary bulk?

Not sure if this is true, but since I haven't had any issues with it yet on several computers, I can't say I hate it.

---

### Post by jbrown96 on 2009-10-23
I've spent some time going through all the grub files when I wrote my post. I still have no idea how I would add a new entry. Where would it go? I certainly can't generate any of the config files that are already there. If I wanted to add an entry for windows it used to be so easy. How do I do it now? If I want to install Fedora, where would I add an entry for it, and what would it look like?

Thanks for the shift command. That's really what I'm looking for. The problem that I have is grub1 showed a message "press esc for menu" and grub2 doesn't have anything like that for shift. I shouldn't need to consult online documentation for a bootloader. It's such an essential part of the system that it should A) be extraordinarily simple to use and B) include all the doucmentation necessary to operate it sanely. 

Grub2 doesn't seem to be simple at all.

---

### Post by drs305 on 2009-10-23
> **jbrown96 said:**
> I've spent some time going through all the grub files when I wrote my post. I still have no idea how I would add a new entry. Where would it go? I certainly can't generate any of the config files that are already there. If I wanted to add an entry for windows it used to be so easy. How do I do it now? If I want to install Fedora, where would I add an entry for it, and what would it look like?

The os-prober is supposed to find other OSs when update-grub is run. Quite a few users have found the other operating systems weren't found on the initial install but *were* located the next time they ran it (sudo update-grub).

If your's consistently doesn't find a specific OS, the best thing to do as a workaround would probably be to add it to 40_custom. This file is imported into the menu with no changes, so it isn't updated until you change it. The good thing is that you can put whatever you want in the title (between the quotes) and it will stay there.

The 40_custom file is in the /etc/grub.d/ folder.
Open it for editing:
```

gksu gedit /etc/grub.d/40_custom

```

Here is a sample Windows entry:
> 
menuentry "Windows Vista from 40_custom" {
insmod ntfs
set root=**(hd0,1)**
search --no-floppy --fs-uuid --set CFFCFF9EECFF7F49
chainloader +1
}


The partitioning is different in Grub 2. The first drive is still 0 but the first partition is now one.  (sdb3 is drive 2, partition 3 for example).
Save the file and run "sudo update-grub" and see what happens on the next boot.

I am not familiar with Fedora so I don't know what the entry would be, but in general other linux entries look like:
> 
menuentry "Jaunty 2.6.28-15-custom" {
set root=(hd0,7)
linux /boot/vmlinuz-2.6.28-15-custom root=UUID=12c55255-27b3-488b-hje7e-9dbe4e2esfg5 ro quiet splash
initrd /boot/initrd.img-2.6.28-15-custom
}


---

### Post by jbrown96 on 2009-10-23
> **drs305 said:**
> The os-prober is supposed to find other OSs when update-grub is run. Quite a few users have found the other operating systems weren't found on the initial install but *were* located the next time they ran it (sudo update-grub).

If your's consistently doesn't find a specific OS, the best thing to do as a workaround would probably be to add it to 40_custom. This file is imported into the menu with no changes, so it isn't updated until you change it. The good thing is that you can put whatever you want in the title (between the quotes) and it will stay there.

The 40_custom file is in the /etc/grub.d/ folder.
Open it for editing:
```

gksu gedit /etc/grub.d/40_custom

```

Here is a sample Windows entry:


The partitioning is different in Grub 2. The first drive is still 0 but the first partition is now one.  (sdb3 is drive 2, partition 3 for example).
Save the file and run "sudo update-grub" and see what happens on the next boot.

I am not familiar with Fedora so I don't know what the entry would be, but in general other linux entries look like:

Thanks that does help. I'm not asking for tech support per say. I was just using it as an example, but that will help if I need to do it. I had no idea that update-grub actually looks for other operating systems to add. The great part about it is that the man page for update-grub is > UPDATE-GRUB(8)                                                                                                       UPDATE-GRUB(8)

NAME
       update-grub - stub for grub-mkconfig

SYNOPSIS
       update-grub

DESCRIPTION
       update-grub is a stub for running grub-mkconfig -o /boot/grub/grub.cfg to generate a grub2 config file.

SEE ALSO
       grub-mkconfig(8)

                                                             April 2009                                              UPDATE-GRUB(8)
And grub-mkconfig is > GRUB-MKCONFIG(8)                                  System Administration Utilities                                  GRUB-MKCONFIG(8)

NAME
       grub-mkconfig - manual page for grub-mkconfig (GNU GRUB 1.97~beta4)

SYNOPSIS
       grub-mkconfig [OPTION]

DESCRIPTION
       Generate a grub config file

       -o, --output=FILE
              output generated config to FILE [default=stdout]

       -h, --help
              print this message and exit

       -v, --version
              print the version information and exit

REPORTING BUGS
       Report bugs to <bug-grub@gnu.org>.

This gets back to my core complaint. Why is everything so damn different and undocumented? There's no indication that update-grub is looking for other OSes. In fact, the only thing that it says it does is take some unmentioned config files and turn them into a giant goobily-gook of a file at /boot/grub/grub.cfg. 

Here's actually a question with a system that I have. Grub always fails to boot on it. It mentions something about the env failing. I can get to the menu and edit the entry. The second line causes the problem; it's something about setting an environment variable on failure. I delete the line then ctrl+x to boot. The stupid thing is that I have to do this every time I boot because I have no idea where this menu entry is, so I can't delete the second line, which seems to be useless anyways (no I take that back -- it exists solely to piss me off).

---

### Post by Xbehave on 2009-10-23
1) I really don't get the point of it
2) It wont let me secure my PC by locking old kernels
> **drs305 said:**
> For others that may face similar situations:
It's been replaced by /boot/grub/grub.cfg but the file you edit is mainly /etc/default/grub

In particular this is stupid because i boot multiple distros so having a single manually configured /boot/grub/menu.conf means no distro ever steps on another's toes.

---

### Post by drs305 on 2009-10-23
> **Xbehave said:**
> 
In particular this is stupid because i boot multiple distros so having a single manually configured /boot/grub/menu.conf means no distro ever steps on another's toes.

I don't want to be a Grub 2 fanboy - I'm just a user - but I want others to understand the possibilites. If you are looking for a single, manually edited file there is the option of making the 10,20,and 30 files in /etc/grub.d/ non-executable. Put all your entries into 40_custom manually, update it manually whenever you want, and you have a menu that is totally unencumbered by the new GRUB 2 process.

---

### Post by Xbehave on 2009-10-23
> **drs305 said:**
> I don't want to be a Grub 2 fanboy - I'm just a user - but I want others to understand the possibilites. If you are looking for a single, manually edited file there is the option of making the 10,20,and 30 files in /etc/grub.d/ non-executable. Put all your entries into 40_custom manually, update it manually whenever you want, and you have a menu that is totally unencumbered by the new GRUB 2 process.
Sorry i wasn't attacking you i just quoted you because that's a "feature" that bugs me. If i do that will /boot/grub/grub.cfg, be human read/editable, I was under the impression that it shouldn't be touched?

On further reading it appears my main security qualm is better than it was last time i read about grub2. ([link]("http://grub.enbug.org/Authentication")).

However i still don't get the point for a PC system (especially now fedora has modified grub-legacy to support ext4)

---

### Post by drs305 on 2009-10-23
> **Xbehave said:**
> Sorry i wasn't attacking you i just quoted you because that's a "feature" that bugs me. If i do that will /boot/grub/grub.cfg, be human read/editable, I was under the impression that it shouldn't be touched?

I didn't think you were attacking me. :-)  

grub.cfg is not meant to be edited, for several reasons. One is that anytime update-grub is executed the contents are going to be changed. And it can run either by user input or automatically when a system component such as a new kernel is introduced. Some users do edit it - the world won't end. And still others edit it and then make it read only so it can't be changed (no comment).

You would edit the 40_custom page and that would be imported directly as is to grub.cfg. So if you think that 40_custom is readable, it would be the same in grub.cfg.  You would still make all your changes to 40_custom (you can actually call it anything you want as long as it is executable - with certain caveats). They are transferred into grub.cfg with "sudo update-grub".

---

### Post by jbrown96 on 2009-10-23
> **drs305 said:**
> I don't want to be a Grub 2 fanboy - I'm just a user - but I want others to understand the possibilites. If you are looking for a single, manually edited file there is the option of making the 10,20,and 30 files in /etc/grub.d/ non-executable. Put all your entries into 40_custom manually, update it manually whenever you want, and you have a menu that is totally unencumbered by the new GRUB 2 process.
My problem with this is that it's completely undocumented. The sad part is that there won't be any good resources. It's going to be a bunch of forum threads fixing problems for newbies. I want good documentation that let's me know the proper way to use things: man pages. There's literally nothing in the related man pages of config files to help users. Can I use the same format for entries from grub1? The comments in 40-custom say > # This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment. I'll simply add entries in an unspecified format! Come on, look at the other files in this directory, and there's no indication that it would be simple at all. Is it really too much to ask for a couple of examples or some decent documentation?

All of the problems that I have had were with basically broken systems. I can't get online and find a solution. Grub2 is unintuitive. I don't see the need to radically change the way the bootloader works. The whole problem is that the one time you need to do something with it: it doesn't work like you would expect it.

---

### Post by drs305 on 2009-10-23
> **jbrown96 said:**
> My problem with this is that it's completely undocumented. 

I am in agreement with this sentiment. I just posted the help.ubuntu.com page on [Grub2]("https://help.ubuntu.com/community/Grub2") yesterday. I am in no means an expert and there is a lot that isn't there (including examples of other OS entries). Official documentation is definitely lacking. 

I sent you a PM about the env problem. If it's with Grub 2, I would suspect it may be a problem with this part of /etc/grub.d/00_header
> 
if [ \${prev_saved_entry} ]; then
  saved_entry=\${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi


If the problem you have is with Grub 2, here are two possible solutions:
1. Enter /etc/default/grub and change DEFAULT=0 to "saved". Run update grub, and after a few reboots you may be able to change it back to 0 (or your choice). That may 'clean' it up.

2. In the same file, just comment out the entire section and see if the error message disappears. It will disable the save function but it sounds better than what you are having to do at the moment.

I fully realize that me referencing these 'obscure' files merely reinforces your intitial and continued feelings about Grub 2! 

:guitar:

---

### Post by 1roxtar on 2009-10-23
Having been using Linux/Ubuntu for the better part of a year, I see a lot of "linux pros" always trying to change so many things on a distro and when it doesn't do what they want, they seem to "throw the baby out with the bath water".  The distro gets the blame instead of the "tweaker". Ubuntu and Linux as a whole kicks butt. I love it, use it, promote it and I'm not looking back.  

:guitar:

---

### Post by jbrown96 on 2009-10-23
I think what's making the config files so crazy is that they have mixed configuration settings (like whether to show the menu and for how long) with the implementation of those config files. Since grub2 uses a lot of scripting, the code isn't complied. The problem is that while you can make changes to the scripts, it isn't pretty or easy. 
Grub1 didn't have much capacity for scripting, so it couldn't fall prey to this design flaw. Here's what grub2 should do. Have all the scripts and stuff because obviously some people want to mess with (or perhaps need to), but then separate the configuration settings from it. Then, grub2 would read through the configs, and then use that data with the scripts. It does this to some extent with the grub.cfg file that it warns you not to edit. However, I think they could do a much better job of separating scripts from settings.

---

### Post by Dullstar on 2009-10-24
Grub2 now only boots Ubuntu, so angry!  *groans* When will I get a computer that works?  In fifty thousand years.

---

### Post by Sealbhach on 2009-10-24
> **drs305 said:**
> I am in agreement with this sentiment. I just posted the help.ubuntu.com page on [Grub2]("https://help.ubuntu.com/community/Grub2") yesterday. 

Thank you for doing that, it looks nicely laid out.

.

---

### Post by Martje_001 on 2009-10-24
> **jbrown96 said:**
> Grub2 doesn't seem to be simple at all.
No, it doesn't. But it is way better than the previous Grub. Since Grub 2 we can:
 - Use scripts
 - Translate it (you probably won't notice as an English user, though ;))
 - Use a graphical interface
 - More architectures
 - Much more I can't think of right now!

---

### Post by twright on 2009-10-24
Grub 2 is designed to work automatically, without the need for constant user configuration. If it does not work automatically, that is a bug which should be fixed and thus should be reported in launchpad.

> **jbrown96 said:**
> I've upgraded to Karmic, and all I can say is that Grub2 is a huge PITA. Here were my first experiences with it.
Installed on my laptop, but I couldn't get the provided nvidia drivers to work. No problem, I'll get them directly from nvidia and install them. Everything goes fine, and I reboot. Unfortunately, something didn't work, and my system freezes on boot. No problem, I'll just boot in single user mode, which will keep X.org from loading. Wait, where's my grub prompt. Oooo, grub2 doesn't give you the menu unless there are multiple kernels or OSes on your machine. Seriously, there's no way I can change my boot parameters without enabling the grub menu, but I can't do that because my system won't boot??? I'm literally about to tear my computer apart at this point. Stuff like this drove me to Linux. I want my machine to do what I say when I say it, but grub2 has decided that I don't get to tell it how to boot. 
So get my LiveCD, and boot that up. There's no /boot/grub/menu.lst file. Instead there several configuration files. On grub1 all I had to do to get a menu was, change hiddenmenu to #hiddenmenu. Of course there's nothing like that. I think GRUB_HIDDEN_TIMEOUT_QUIET=false this is the line that I need to change, but I'm not sure, so I change three different lines. Now I need to run update-grub just so it will load these changes??? Are you mad! And of course I can't figure out how to run this command from a LiveCD because it doesn't know where grub2 is. 
This did me the menu that I needed, and I was able to fix my system very easily once I got to the terminal.
I have looked at grub since, and most of the changes make no sense to me. Instead of having all the menu items in a single file (a la /boot/grub/menu.lst), they have been moved to their own files. They are so complicated and filled with code that I can't even begin to understand them. I guess you wold add entries to /etc/grub.d/40_custom file. Seriously WTF! Why is this so complicated. There's no sample entries in here like grub1. That's really helpful; if you are adding another Linux system you can reference your current Linux entries and get an idea of the format, and it works for Windows as well because there is a Windows example in /boot/grub/menu.lst, but of course that has been eliminated in grub2. 

I understand why Ubuntu was hamstringed into switching to grub2; the grub developers wouldn't add support for ext4 to grub1. I just don't understand why it's so needlessly complicated. I was so frustrated trying to do something that, in the past, took adding a single character to a well-known file. The developers completely failed at making it easy to use. I was trying to help a user install Windows alongside Ubuntu the other day. I flatly told him to install windows first because grub2 is too difficult to add an entry for windows. That's completely unacceptable. Grub2 is the new newCoke.

---

### Post by longtom on 2009-10-25
> **twright said:**
> Grub 2 is designed to work automatically, without the need for constant user configuration. If it does not work automatically, that is a bug which should be fixed and thus should be reported in launchpad.

It hardly ever works that way.  There are always circumstances where you need to edit a config file.  Installing Windows secondly would immediately come to mind as a prime example.

Editing a config file shouldn't require a degree in computer science.  The way it was handled in Grub (1) was just about acceptable.  I would even think a gui interface for Grub 2 would be something which could be seriously considered.

Having said that, if that all is not acceptable for the snow white purist, some decent and, for the unwashed, easy understandable documentation is not too much to ask.

---

### Post by jbrown96 on 2009-10-25
> **longtom said:**
> It hardly ever works that way.  There are always circumstances where you need to edit a config file.  Installing Windows secondly would immediately come to mind as a prime example.

Editing a config file shouldn't require a degree in computer science.  The way it was handled in Grub (1) was just about acceptable.  I would even think a gui interface for Grub 2 would be something which could be seriously considered.

Having said that, if that all is not acceptable for the snow white purist, some decent and, for the unwashed, easy understandable documentation is not too much to ask.

Sad part is that I'm almost done with my CS degree!

---

### Post by Dullstar on 2009-10-25
Grub2 sucks, and hosed my dual boot.  I have downgraded to 8.04, and are back to using Wubi to install Linux.

EDIT:  Actually, it appears that it wasn't grub2 but damage during partitioning.

---

### Post by twright on 2009-10-25
> **Dullstar said:**
> Grub2 sucks, and hosed my dual boot.  I have downgraded to 8.04, and are back to using Wubi to install Linux.
Grub 2, the new boot loader being introduced in the Karmic **testing releases **which will not be installed automatically for upgrades, just fresh installs?

If you want to test unstable software and manually upgrade system components which have explicitly do not do so automatically incase of breakage then don't blame it for not working out perfectly.

---

### Post by Zoot7 on 2009-10-26
I'm a little leary of it myself. Not being able to easily edit menu.lst or reinstall it to the mbr like Grub 1 is a bit of a regression IMO.
Having said that it's worked okay for me and always found both XP and openSUSE no problems, however I am wondering whether it'll boot XP okay on my setup with 5 Hard drives.

Talking of Grub 2 and it's shortcomings has anyone tried out downgrading Karmic to grub legacy, according to this:
[http://ubuntuforums.org/showpost.php?p=8071880&postcount=18](http://ubuntuforums.org/showpost.php?p=8071880&postcount=18)
it's possible.

---

### Post by twright on 2009-10-26
> **Zoot7 said:**
> I'm a little leary of it myself. Not being able to easily edit menu.lst or reinstall it to the mbr like Grub 1 is a bit of a regression IMO.
Having said that it's worked okay for me and always found both XP and openSUSE no problems, however I am wondering whether it'll boot XP okay on my setup with 5 Hard drives.

Talking of Grub 2 and it's shortcomings has anyone tried out downgrading Karmic to grub legacy, according to this:
[http://ubuntuforums.org/showpost.php?p=8071880&postcount=18](http://ubuntuforums.org/showpost.php?p=8071880&postcount=18)
it's possible.
It should work fine; old Grub does not care whether it is being installed over new grub or not.

---

### Post by 1roxtar on 2009-10-26
I have Windows XP and Ubuntu 9.10 RC dual booted with a fresh install of Karmic and Grub is working flawlessly on my Acer Aspire One.

---

### Post by m-p{3} on 2009-10-27
I would probably like it more if I figured out how to boot an ISO directly from it.

---

### Post by drs305 on 2009-10-27
> **m-p{3} said:**
> I would probably like it more if I figured out how to boot an ISO directly from it.

A LiveCD or other ISO with an OS on it (other 'live' cds)?

Here you go:
[Grub2 - Booting an ISO]("https://help.ubuntu.com/community/Grub2#Booting%20an%20ISO")

---

### Post by running_rabbit07 on 2009-10-27
I did an upgrade instead of clean installing and it appears that I do not have grub 2.

---

### Post by drs305 on 2009-10-27
> **running_rabbit07 said:**
> I did an upgrade instead of clean installing and it appears that I do not have grub 2.

You don't. The default for upgrades is to keep Grub. You can update to Grub 2 by installing "grub-pc". 

The devs decided it would be safer to keep Grub on upgrades, with G2 only being installed on clean installations.

Here is a link to the Community docs on how to "upgrade" to Grub 2:
[Upgrading to GRUB 2]("https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202")

---

### Post by running_rabbit07 on 2009-10-27
> **drs305 said:**
> You don't. The default for upgrades is to keep Grub. You can update to Grub 2 by installing "grub-pc". 

The devs decided it would be safer to keep Grub on upgrades, with G2 only being installed on clean installations.

Here is a link to the Community docs on how to "upgrade" to Grub 2:
[Upgrading to GRUB 2]("https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202")

Thanks for that info. While I like to try new programs, I don't mess with core programs unless I have to. 

Karmic is awesome!

---

### Post by AmbientOcclusion on 2009-12-08
Grub 2 is a failure and a nightmare.

When things improve they become more efficient, grub 2 is not. The most irritating thing is that most of grub 2 's shortcomings are being masked by unconditional zealotry.

Grub worked. If there were some things that needed to be changed, then adding a layer of complexity and inefficiency is probably not the way to go.

---

### Post by s3a on 2009-12-08
What's wrong with grub2?

---

### Post by cariboo on 2009-12-08
> **AmbientOcclusion said:**
> Grub 2 is a failure and a nightmare.

When things improve they become more efficient, grub 2 is not. The most irritating thing is that most of grub 2 's shortcomings are being masked by unconditional zealotry.

Grub worked. If there were some things that needed to be changed, then adding a layer of complexity and inefficiency is probably not the way to go.

Grub-legacy is no longer maintained, except for Ubuntu, grub-legacy does not support ext4 and certainly won't support btrfs. Most other distro's that have ext4 set as the default already use Grub2.

---

### Post by Ginsu543 on 2009-12-09
I don't understand what it means for grub-legacy to not support ext4. All my Ubuntu partitions are in ext4 and grub boots them fine. I personally don't *hate* grub2. I use it on my Dell Mini 9 which got a fresh install of Karmic. But I use grub-legacy on my main rig because I installed Karmic on my RAID0 array and grub2 wouldn't install. The installer installed grub-legacy instead. Would someone kindly explain it to me?

Once I got accustomed to the way grub2 deals with things as opposed to grub-legacy, I have been able to set things up the way I want. But I also must say that some things in grub2 (like changing the names of non-Ubuntu OSes that show up in the boot screen) are much more complicated than in grub-legacy. In grub-legacy I just need to change the "title" line in menu.lst, but in grub2 I have to edit an actual script file. It just seems less intuitive to me to have to go to a particular line number and edit a particular portion of bash code to make grub2 do what I want. I totally get that grub2 allows for more functionality, but it is more arcane than grub-legacy.

---

### Post by Zoot7 on 2009-12-09
> **s3a said:**
> What's wrong with grub2?
IMO it's the needless and pointless complexity it introduces. Grub Legacy was a lot more easy configure.

---

### Post by rahilm on 2009-12-09
> **Zoot7 said:**
> IMO it's the needless and pointless complexity it introduces. Grub Legacy was a lot more easy configure.
Ya. That's true. I agree.
But I found grub2 to be more interesting to use given the fact that it can mount iso files although I am still trying to get it work

---

### Post by shrubyyc on 2009-12-09
> **ambientocclusion said:**
> grub 2 is a failure and a nightmare.

When things improve they become more efficient, grub 2 is not. The most irritating thing is that most of grub 2 's shortcomings are being masked by unconditional zealotry.

Grub worked. If there were some things that needed to be changed, then adding a layer of complexity and inefficiency is probably not the way to go.

qft!

---

### Post by Zoot7 on 2009-12-09
> **rahilm said:**
> But I found grub2 to be more interesting to use given the fact that it can mount iso files although I am still trying to get it work
Interesting that you mention that, a friend of mine got Grub (legacy I think) to boot an Acronis Rescue Image a while back.

---

### Post by artsci2 on 2009-12-09
I hate all grubs so much that I use a different HD for every system. 

First I disconnect all drives except 1 and install a distro as if it was a single drive syste, then disconnect that drive and connect drive #2 and install OS#2 etc. I choose the bootdrive using the BIOS or by Pressing F12 during bootup. 

My data is held in yet another drive that is separate from the OS carring drives.

Laptops are difficult to do this with and I'm hoping to see more systems work the way my recent install of Ubuntu Netbook Remix went with the Grub stuff going to the external drive that was recieving UNR and not on the internal HD. Previos installs forced Grub onto the internal HD and when the external HD was not attache Grub would and not allow booting the sys on the internal drive.

---

### Post by Ginsu543 on 2009-12-09
> **artsci2 said:**
> I hate all grubs so much that I use a different HD for every system. 

First I disconnect all drives except 1 and install a distro as if it was a single drive syste, then disconnect that drive and connect drive #2 and install OS#2 etc. I choose the bootdrive using the BIOS or by Pressing F12 during bootup. 

My data is held in yet another drive that is separate from the OS carring drives.
I also have my three OSes on three separate drives (Karmic, my main OS, is on a RAID0 array). I especially like to keep Windows on its own drive because I don't want to deal with the hassle of grub overwriting NTLDR or vice versa. So I too can boot up any OS I want by changing the boot order in BIOS. However, I do find it inconvenient to do that every time, so I just have grub installed and working on my Karmic drive, which can then find and load the other OSes on the other drives.

---

### Post by VanCardboardbox on 2009-12-09
I was running an eleven-OS multi-boot system using Grub-legacy. Shortly after Karmic came out with Grub2 I decided to rebuild the whole thing, providing an opportunity to replace old stuff with several recent releases.

I started out hating 2, but by the time the system was all set up and working I preferred Grub2 to legacy. As so often happens I mistook "I don't know how it works" for "it sucks". Once I got to know how to use it, it stopped sucking. I've replaced a couple of the OSes since the original setup and still have had no problems. 

The prober has yet to fail, successfully finding and creating working entries for Fedora 12, Mandriva 2010, SUSE 11.2, Mint 8, Vector 6.0, Sabayon 5, Zenwalk 6.2, MoonOS, AntiX M8.2, and poor old Windows XP. Once the prober has done its thing, I copy the results over to *x*_custom, customize each entry to my liking and turn the prober off. After customizing the display resolution and adding a background image, grub menus have never looked so nice, and the only thing I see are my custom entries.  

The only PITA is distros that don't offer to forgo installing a bootloader, so I had to reinstall Grub2 to my boot partition more than once. Painless, but it consumed some time.

I was originally frustrated by the lack of documentation, until I found [[COLOR="Purple"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1195275"). Everything I needed to know was there.

---

### Post by joes7 on 2009-12-10
> **s3a said:**
> What's wrong with grub2?

Nothing, of course:)! GRUB is my favourite boot loader because of its simplicity.

---

### Post by rahilm on 2009-12-10
Just wait till grub2 themes come out

---

### Post by bruno9779 on 2009-12-11
I like it

---

### Post by michaelzap on 2009-12-11
> **VanCardboardbox said:**
> The prober has yet to fail, successfully finding and creating working entries for Fedora 12, Mandriva 2010, SUSE 11.2, Mint 8, Vector 6.0, Sabayon 5, Zenwalk 6.2, MoonOS, AntiX M8.2, and poor old Windows XP. Once the prober has done its thing, I copy the results over to *x*_custom, customize each entry to my liking and turn the prober off. After customizing the display resolution and adding a background image, grub menus have never looked so nice, and the only thing I see are my custom entries.  

The only PITA is distros that don't offer to forgo installing a bootloader, so I had to reinstall Grub2 to my boot partition more than once. Painless, but it consumed some time.

Interesting. So, for example, if I wanted to try out Debian on my laptop which already has Vista and Karmic, I could just install it to a separate partition without the boot loader, boot into Karmic again and update Grub, and then restart and be able to choose Debian from Grub 2? What if I want to use LUKS encryption for my Debian installation? Any experience with that?

---

### Post by neuralnet on 2009-12-15
Yup grub2 sucks. I'm finding the load time for grub2 unacceptably slow. Grub used to start in an instant.. Now I'm waiting >10s for it to load. AFAIK there's little increase in functionality & requires even seasoned grubbers to RTFM from scratch - seemingly only to increase the load time by 1000%... I have 2 XP installs (NTFS) and Karmic (Ext4) - hardly excessive. Any ideas?

YES, I vote for a grub GUI too. It should be easier for the average user to set up & fix grub.

---

### Post by VanCardboardbox on 2009-12-15
> **michaelzap said:**
> Interesting. So, for example, if I wanted to try out Debian on my laptop which already has Vista and Karmic, I could just install it to a separate partition without the boot loader, boot into Karmic again and update Grub, and then restart and be able to choose Debian from Grub 2? What if I want to use LUKS encryption for my Debian installation? Any experience with that?

Yes, it should be that straight forward, though I have no experience with LUKS encryption so can't say how that will complicate matters. If Debian (or any OS you add) winds up installing a boot loader you can reinstall Grub2 from a live Karmic disc. Instructions can be found in the link in my original post. 

I'm a bit astonished to see all the hate on for Grub2 (and legacy Grub) to the extent that a user would actually choose to use the BIOS to select a HDD to boot from on each start up. This sounds more laborious that just learning how to get Grub to do what you want it to. To each their own, I guess.

---

### Post by lmeister3 on 2009-12-15
Grub2 single-handedly ruined my Ubuntu experience (at least on my laptop).  The fact that it just will not co-operate with traditional multi-booting methods is a major step back (for people who aim to multi-boot having installed linux first)

I tried to replace my Vista installation with 7 (after already having vista/ubuntu) and found that Grub2 won't settle for just being included into the Windows MBR.  Found myself unable to reinstall grub from a live cd to try and save my Ubuntu (no output on fdisk to see the disk devices for some reason).  I was forced to use the entire disk for 7 (for the time being) and gave up on having Ubuntu altogether. 

That said, I absolutely love Ubuntu and it is still my main OS on the Desktop at home.

Why change what is proven to work?  An OS's bootloader should never been its mainstay, so "themes" and "cool backdrops" for something you should see for 5 seconds at a time is beyond ridiculous. 

I still see no need for grub2

---

### Post by VanCardboardbox on 2009-12-15
^Not just about themes and splash. This is lifted from the great [[COLOR="Purple"]G2 tutorial thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1195275") in this forum:

[COLOR="Purple"]GRUB 2's major improvements over the original GRUB include:

    * New configuration file structure
    * Scripting support including conditional statements and functions
    * Dynamic module loading
    * Rescue mode
    * Themes
    * Graphical boot menu support and improved splash capability
    * Easily boot LiveCD ISO images directly from hard drive
    * Non-X86 platform support (such as PowerPC)
    * Universal support for UUIDs (not just Ubuntu)
    * Improved internationalization, including support for non-ASCII characters[/COLOR]

That tutorial also includes instructions on uninstalling Grub2 from a Karmic install and replacing it with Grub legacy.

---

### Post by drs305 on 2009-12-16
> **neuralnet said:**
> Yup grub2 sucks. I'm finding the load time for grub2 unacceptably slow. Grub used to start in an instant.. Now I'm waiting >10s for it to load. AFAIK there's little increase in functionality & requires even seasoned grubbers to RTFM from scratch - seemingly only to increase the load time by 1000%... I have 2 XP installs (NTFS) and Karmic (Ext4) - hardly excessive. Any ideas?

YES, I vote for a grub GUI too. It should be easier for the average user to set up & fix grub.

I'll assume that you have the timeouts set properly in the grub /etc/default/grub file. The situation you describe (10-15 second delay), if it is happening *before* the grub menu appears is often caused when Grub 2 is installed on a drive different than the one that initially is booted to. In this case, Grub 2 will spend time searching the boot drive looking for files before then searching for them on the next drive. If this is the case, changing the boot order in BIOS so the Grub 2 drive is first will eliminate the delay.

I think most Ubuntu users are eagerly awaiting the arrival of "StartupManager 2" or something equivalent.  ;-)

---

### Post by mike1947 on 2009-12-16
Grub 2 is not ready for prime time especially in a multiboot or chain-loading environment.  The authors in Ubuntu Unofficial Guide have it right.  The limitation in my Grub 2 is that it cannot chainload//dual boot across disk drives.  As long as 2 partitions are on the same drive multiboot is possible.   I have much more luck with Windows 7 which merely wants a blank NTFS partition and just adds an entry to W7 loader.  Problems largely went away with Grub legacy on boot drive and using W7 to shrink its own partition.  

Grub 2 was mis-designed.  Rather than having a multitude of shell scripts one python script would be fine and better much like the Ubuntu upgrade procedure.  The "improvements" amount to running multiple slow shell scripts slowing installations prettier splash screens and multiple ways to complexify something which was kept deliberately simple.  Sounds to me like Windows ME, or 2000.  It doesn't even rise to the level of NP or Visa or W7 let alone other good Linux products.  Perhaps in a couple of years when the GUI interface is ready for Grub 2 it will be a worthy product.  Without being easily able to chain load across disks (it fails to find other disk drives) it is a big step backwards.

---

### Post by twright on 2009-12-16
> **mike1947 said:**
> 
Grub 2 was mis-designed.  Rather than having a multitude of shell scripts one python script would be fine and better much like the Ubuntu upgrade procedure.  The "improvements" amount to running multiple slow shell scripts slowing installations prettier splash screens and multiple ways to complexify something which was kept deliberately simple.  Sounds to me like Windows ME, or 2000.  It doesn't even rise to the level of NP or Visa or W7 let alone other good Linux products.  Perhaps in a couple of years when the GUI interface is ready for Grub 2 it will be a worthy product.  Without being easily able to chain load across disks (it fails to find other disk drives) it is a big step backwards.
Grub has to work on EVERY distro, not just Ubuntu - Ubuntu is one of the few distros which actually ship Python. Whilst I can see that rewriting it is Perl might be a good idea, shell script is the scripting language native to Linux, and an extremely powerful one as well. Besides, it mainly launches other commands to do its work - the perfect job for shell script.

Sometimes something has to become more complex in order to be more robust, handling wider use cases. There may be issues now, but with such a ubiquitous piece of software, exposed to such a wide degree of bare metal hardware then of course there will be issues.

Just to put stuff in perspective, Grub 1's last major update was around 1999 so is looks very old by now. Whilst keeping ancient software in order not to break things might seem tempting, it is just a bad idea.

---

### Post by Crafty Kisses on 2009-12-16
I love Grub2. <3

---

### Post by GodLikeCreature on 2009-12-17
It took me a while to understand how to update kernel entries from OS sitting in other partitions.  I have a triple boot machine with Ubuntu Studio 9.04, Ubuntu Jaunty and Karmic.  

When Karmic was installed, it recognised the other two OS, but would not upgrade their entries when they had a kernel upgrade, so I would be stuck running an older version of the kernel.

It took a bit of research, but I found my way through, and I have to say update-grub feels like a great tool.  It successfully found all of my entries for all 3 computers.  Then I commented out those entries which were obsolete (I could only do that by allowing write access into grub.cfg temporarily, and am aware that those changes will go as soon as I run update-grub again, but hey...)

All in all, after a bit of understanding, I can´t say I hate grub2, it´s just different.  One annoying thing I found, though, was that trying to adjust screen resolution for the menu didn´t work at all for me.  I checked the supported entries from the grub menu itself, and no matter which one I tried, they all failed (except for the default 640x480, of course).  Every time one of those changes failed, there would be no boot menu, so I had to boot from a liveCD, then fix /etc/default/grub manually.

Honestly, I think Ubuntu is yet to really get the most out of GRUB2, and as usually happens with any change, there´s a period of getting used to, but I believe it is a step forward.  

After all, GRUB had a lot of haters in LILO fans, so I think let´s just give GRUB2 a chance.  As distros start getting the best out of it and we see its benefits up close, we will all like it...

---

### Post by Zoot7 on 2009-12-18
I'm starting to come around to Grub 2 now. :)
The os prober makes things very easy compared to Grub legacy. It just picked up and boots openSUSE, Fedora, Windows XP and Windows 7 aswell as Karmic no problem for me.

---

### Post by Dullstar on 2009-12-19
> **VanCardboardbox said:**
> I was running an eleven-OS multi-boot system using Grub-legacy. Shortly after Karmic came out with Grub2 I decided to rebuild the whole thing, providing an opportunity to replace old stuff with several recent releases.

I started out hating 2, but by the time the system was all set up and working I preferred Grub2 to legacy. As so often happens I mistook "I don't know how it works" for "it sucks". Once I got to know how to use it, it stopped sucking. I've replaced a couple of the OSes since the original setup and still have had no problems. 

The prober has yet to fail, successfully finding and creating working entries for Fedora 12, Mandriva 2010, SUSE 11.2, Mint 8, Vector 6.0, Sabayon 5, Zenwalk 6.2, MoonOS, AntiX M8.2, and poor old Windows XP. Once the prober has done its thing, I copy the results over to *x*_custom, customize each entry to my liking and turn the prober off. After customizing the display resolution and adding a background image, grub menus have never looked so nice, and the only thing I see are my custom entries.  

The only PITA is distros that don't offer to forgo installing a bootloader, so I had to reinstall Grub2 to my boot partition more than once. Painless, but it consumed some time.

I was originally frustrated by the lack of documentation, until I found [[COLOR=Purple]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1195275"). Everything I needed to know was there.

I guess it did work on m machine, as I found the issue may not be Grub2's fault.  I think files got damaged while partitioning.

---

### Post by scales on 2009-12-19
argh! I hate it! The old menu config file was so much more tweak friendly.  Also, it may just be ubuntu, but I constantly have to re-disable the recovery option remove newer kernels, and re-run update-grub. I am so frustrated with grub2

---

### Post by twright on 2009-12-19
> **scales said:**
> argh! I hate it! The old menu config file was so much more tweak friendly.  Also, it may just be ubuntu, but I constantly have to re-disable the recovery option remove newer kernels, and re-run update-grub. I am so frustrated with grub2
You should only change stuff in /etc/default/grub , trying to edit the other files will feel broken because, well, it is - they are not designed for editing.

---

### Post by scales on 2009-12-20
Right, i know how to remove things, the trouble is that in my /etc/grub i have the following:

abi-2.6.31-16-generic     grub                          memtest86+.bin                vmcoreinfo-2.6.31-16-generic
config-2.6.31-16-generic  initrd.img-2.6.31-16-generic  System.map-2.6.31-16-generic  vmlinuz-2.6.31-16-generic

yet when i boot up i have some "karmic development" option that i dont know how to remove.

---

### Post by drs305 on 2009-12-20
> **scales said:**
> yet when i boot up i have some "karmic development" option that i dont know how to remove.

This is a menu option? If so, inspecting the /boot/grub/grub.cfg file might provide some hints. That file is divided into sections. Each section is created by a script and marked by start and end identifiers such as:
> 
### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

By determining which section this "karmic development" entry is in, you may be able to locate it and remove the kernel, if that is what you want to do.

There is also the option, once you have identified the section (and the script which generated it) of modifying the script to eliminate the entry. It isn't as simple as a GUI tool but it can be done.

---

### Post by scales on 2009-12-20
> **drs305 said:**
> There is also the option, once you have identified the section (and the script which generated it) of modifying the script to eliminate the entry. It isn't as simple as a GUI tool but it can be done.

But thats why i hate this new grub! :(

---

### Post by twright on 2009-12-20
> **scales said:**
> But thats why i hate this new grub! :(
But that too is the point - if you don't want to be able to boot a kernel, you should just uninstall it :-)

---

### Post by julianb on 2009-12-21
> But that too is the point - if you don't want to be able to boot a kernel, you should just uninstall it 

Often I like to avoid deleting stuff: what if the new kernel turns out to be buggy? (well, I don't think I've ever encountered a buggy Linux kernel, but that doesn't mean it won't happen)

---

### Post by sfarthing on 2009-12-21
Grub2 has virtually guaranteed that Linux will NEVER increase it's user base past the fraction of 1% it currently enjoys.  Grub2 successfully breaks systems that were working perfectly and no easy fix is available.  With Grub2, Linux has permanently announced to the world that for desktop and laptop users, Linux as a reliable platform is not only irrelevant, it is to be avoided.  Linux has finally decided its one and only true love is hobbyists and hobbyists only.  Real world computer users can finally disabuse themselves of the notion that Linux on the desktop has any role among those that use computers to do real work.  The fact Canonical has unleashed this beast on the very desktop users they have courted proves the Linux community as a whole simply has no common sense clue about how to increase the user base past a fraction of 1%.  This is a very sad obituary for Linux on the desktop.

---

### Post by drs305 on 2009-12-21
> **sfarthing said:**
> Grub2 has virtually guaranteed that Linux will NEVER increase it's user base past the fraction of 1% it currently enjoys.  Grub2 successfully breaks systems that were working perfectly and no easy fix is available.  With Grub2, Linux has permanently announced to the world that for desktop and laptop users, Linux as a reliable platform is not only irrelevant, it is to be avoided.  Linux has finally decided its one and only true love is hobbyists and hobbyists only.  Real world computer users can finally disabuse themselves of the notion that Linux on the desktop has any role among those that use computers to do real work.  The fact Canonical has unleashed this beast on the very desktop users they have courted proves the Linux community as a whole simply has no common sense clue about how to increase the user base past a fraction of 1%.  This is a very sad obituary for Linux on the desktop.

I see this is your first post. Welcome to the Ubuntu forums!  ;-)

---

### Post by sfarthing on 2009-12-21
Thank you for the Welcome note.  I hope I am wrong about the future of desktop Linux.  I would love to see a vastly increased user base but remain extremely concerned.  But best to all.

---

### Post by ericmc783 on 2009-12-22
> **jbrown96 said:**
> I've upgraded to Karmic, and all I can say is that Grub2 is a huge PITA.

+1,000.

I, too, have found the same thing, after having several boot issues with grub 2 after doing some routine updates to 9.10. I liked being able to edit menu.lst, and found the new configuration options confusing.

---

### Post by sfarthing on 2009-12-23
Here is one frequently referred-to bit of documentation about how cool grub2 is because you can specify a 'bios boot partition' (NOT). [http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition) One problem. The key command specified does not work.  So what we have with grub2 is a fragile, poorly tested, poorly documented work-in-process component for an absolutely critical function that everyone must use.  It makes no sense that it has been inflicted on everyday Ubuntu users at such a premature stage.  That is why I feel this approach is holding Linux back from a wider audience.  When people are punished by grub2 just for trying Ubuntu, that lost goodwill does an amazing amount of damage to the future adoption of Ubuntu.  Oh, well...

---

### Post by malangaman on 2009-12-23
I share the opinion that Grub2 was shoehorned into place before it's time. It has been the source of hours of frustration while trying to make it work on a system with three OS partitions.

Grub used to be so easy!

It wasn't broke, so why did they try to fix it?

When I installed 9.10 I was locked out since Grub2 wouldn't recognize the other Ubuntu 8.04 partition but would recognize XP!

Hours of googling coupled with copious trials and errors followed until finally I got it to work.

That's not how one should enjoy an OS.

---

### Post by llazarte on 2009-12-23
> **drs305 said:**
> I see this is your first post. Welcome to the Ubuntu forums!  ;-)

I very much appreciate all the help you have given in this thread. Anyway, of course there is a **STRONG** reason why Ubuntu lovers start threads like this.

I think there is a very important message for those making decisions about Ubuntu releases: [COLOR=Red]**PLEASE, DONT BREAK IT!**[/COLOR]  _We love it_, and we are prepared to wait another year if necessary to play with Grub2 (1.9xx?). Stability is a key point! I love to play with new toys, I install early alphas when available. But I do not want to break my everyday tools!

I very much praise Canonical for bringing Linux to many more people. But I wander what shift on decision making happened with karmic:

[LIST]
[*]The nice UNR .img file which I could simple put on a 1G flash drive and share with friends is gone.
[*]And, worst of all, the Grub2 distributions breaks in about one of every 5 upgrades.
[/LIST]
It will help very much if Grub2 had a single, simple, documented file which admins could config, without being rewritten.

Thanks a lot to those who work on Ubuntu. Airing our frustrations helps to make it better!

---

### Post by Gemu on 2009-12-27
Its going to be confusing to talk about grub hard drive numbering with devices starting at 0 and partitions starting at 1 now. I guess it will be better to refer to them as sda1,2,3 and sdb1,2,3. in the future. I'm not particularly fond of the new (hd0,1) for what used to (hd0,0) thing but can live with it I guess.

 I dont mind adding entrys to /etc/grub.d/40_custom as long as they go into /boot/grub/grub.cfg when you do the sudo update-grub2 command. Sometimes they don't show up in there. I still haven't gotten my puppy menu to show up on grub.cfg . Its harder to edit than grub/menu.lst for sure.


I don't see what would be wrong with having an installable grub booting on its own tiny internal hard drive separate from all other drives. And then being capable to boot any OS, or ISO on the hard drives. File mounting, copying and pasting with the mouse, internet. That way windows MBR would never get over written nor would Grub for that matter. What if you could boot into a tiny OS and click icons that look like hard drives or ISO's and boot them. 


 So far I like grub legacy better. Grub legacy could boot an iso if it could just mount it couldn't it?

---

### Post by Gemu on 2009-12-27
I found out the reason my puppy entry wasn't showing up.
 

menuentry "puppy4.22 (on /dev/sdb7)" {
set root (hd1,7)


If that entire section after menuentry and before the  {  symbol is not in quotes, it won't show up on boot up. It may be in grub.cfg but it wont be visible upon start up.

So grub2 rocks for me again.

Were just going to have to get used to editing entrys in /etc/grub.d/40_custom

and doing a sudo update-grub2 every time you add a new one.

---

### Post by iris-n on 2009-12-29
I hate it too. It did recognise all my OSes, but it is slow as hell to start up. And it's ugly. Why change the look and feel of the menu? We are supposed to stare at that thing? Just give me a readable monospace font, dammit.

I think the main point is that boot managers aren't supposed to be interesting. I don't give a **** to it's shiny new features, to it's new and clever numbering scheme. Who does? Maybe that guy that had 11 OSes, but I think he is in the minority. I just want it to be able to dual boot windows and ubuntu without hassle. Is that too much to ask? 

And I'm shocked by the people who want it's new GUI. Are you insane? A GUI? In a boot loader??? What the hell for? It is supposed to be the simplest possible piece of software, to boot up the OS and get out of the way, not to add a huge layer of complexity on the most critical part of the system.

---

### Post by ryancammer on 2009-12-29
i just used the update manager to perform an upgrade after being in windows-land for a while, and lo and behold, i got this bizarre screen, GNU GRUB version 1.97~beta4 with a list of commands. i'm guessing something went awry during the upgrade. then i went documentation hunting, and the documentation is wrong. frankly, i didn't even know there was a grub2. then i started digging into what grub2 is....

umm, pretty pictures? WHO CARES? i want my system to work. i don't need the possibility of pretty pictures on a fragile system that previously worked before.

beta? beta??? i'll say. why would the powers that be even THINK it's okay to release a BETA BOOTLOADER to the public??? is this someone's pet project that they just *have* to get the world to see?

more complexity? for a bootloader? unnecessary.

so what i'm left with is a broken bootloader with a load of complexity, missing, incomplete, and erroneous documentation, and a community of pissed off users to commiserate with.

unfortunately, i have real work to get done, and now i'm stuck with a broken ubuntu install, and no way to fix it. the only thing i can think of to do is to find a distro WITHOUT this janky piece of broken beta software.

---

### Post by longtom on 2009-12-30
> **ryancammer said:**
> i just used the update manager to perform an upgrade after being in windows-land for a while, and lo and behold, i got this bizarre screen, GNU GRUB version 1.97~beta4 with a list of commands. i'm guessing something went awry during the upgrade. then i went documentation hunting, and the documentation is wrong. frankly, i didn't even know there was a grub2. then i started digging into what grub2 is....

umm, pretty pictures? WHO CARES? i want my system to work. i don't need the possibility of pretty pictures on a fragile system that previously worked before.

beta? beta??? i'll say. why would the powers that be even THINK it's okay to release a BETA BOOTLOADER to the public??? is this someone's pet project that they just *have* to get the world to see?

more complexity? for a bootloader? unnecessary.

so what i'm left with is a broken bootloader with a load of complexity, missing, incomplete, and erroneous documentation, and a community of pissed off users to commiserate with.

unfortunately, i have real work to get done, and now i'm stuck with a broken ubuntu install, and no way to fix it. the only thing i can think of to do is to find a distro WITHOUT this janky piece of broken beta software.

To all who have a problem with grub2 (like me...so I don't hate it, it's only a string of 0s and 1s), just install some older version of Ubuntu to get grub 1 into your mbr.  You can delete that install afterwords.

Alternatively, if you know how to get grub1 on without that, do that.  However, for not so technical guys like me above method works fine.

---

### Post by markjs on 2009-12-30
I hate it bad enough I just quit bothering.  I liked 8.04 but I am not going to downgrade, so I guess Linux still isn't ready for ease of use, and I am back to Windoze....

Thanks developers for taking something that worked great and fixing it, and now it is just a worthless big steaming pile of crap.... Well done!

](*,)

---

### Post by anaconda on 2009-12-30
yeah.. it is a PITA.

The problem I am having with it is that 1 out of 3 times grub2 wont even boot the system. It just hangs.

---

### Post by AlexanderDGreat on 2009-12-30
Hi can anyone help me? I'm using an Adaptec SCSI 29320 Hardware RAID with 2 Seagate 37gb Cheetah as Raid1 configuration. I used an alternate cd Karmic Koala to install. I have these partitions: /boot /swap / /home - but when I reach the installation of GRUB, it won't install!

Now I reboot, then I'm left with a blank screen. My question is, why won't GRUB install? Now, I've a broken OS, I can't get any work done. I can't install Karmic. I'm in agony and confused. :(

PS I used Jaunty before, and alternate install CD worked without errors.

---

### Post by pizza-is-good on 2009-12-30
Mine doesn't say grub2, it says Grub 1.97 beta 4 at the top.

It scared me at first, but it works fine. I still haven't had enough kernel revisions that they get annoying in grub, but when I do, we'll see how hard it is to delete them....:lolflag:

---

### Post by Sef on 2009-12-30
> Mine doesn't say grub2, it says Grub 1.97 beta 4 at the top.

Once it is stable it will become GRUB 2.

---

### Post by drs305 on 2009-12-30
At the risk of being labeled a Grub 2 fanboy, I'll respond to a few of the recent posts:

@ iris-n - For the slow start, is G2 installed on the second drive listed in your BIOS. If so, changing the boot order so G2 is on the first drive booted speeds things up quite a bit since Grub 2 looks on the first boot drive and then moves on to the second. I won't try to defend why it does it, or if it should know where to look, I'm just offering a possible way to improve its performance.

As far as the GUI - I think most of the talk of GUI is directed toward a GRUB 2 tweaker like StartUp-Manager that will allow users to set many of the default settings without manually editing any system files. For boot splash images and themes, it's not my cup of tea either but some people seem to want it. 

@ ryancammer
I am just a regular user who was frustrated that there was almost no documentation for Grub 2 when it was released. I've made several threads on how to use it and wrote the Ubuntu community doc. There are signficant gaps in my knowledge of Grub 2 and I've tried to avoid those topics (RAID, USB booting, etc). If there are any errors in my posts I want to correct them so please let me know. On the other hand, a command that doesn't work for some is not necessarily an error, so any alternate solutions are also welcome.

@ longtom,
You can install Grub legacy on a current installation. The instructions are in the community doc (see "GRUB2" link in my signature line).

@ AlexanderDGreat
I don't want you to feel like I ignored your post. I'd love to help but suspect your issue is RAID-related, and as I've said I don't have experience with RAID.

---

### Post by running_rabbit07 on 2009-12-30
Nope don't hate it. You don't even have to use it. Install Karmic, tell it not to install grub, place Jaunty disk in drive, use it to install grub and you can be happy.

I am happy with grub2, it works, it boots just as fast, and it didn't cost a thing.

---

### Post by longtom on 2009-12-31
> **Sef said:**
> Once it is stable it will become GRUB 2.

You see - I think that is the point many are making:

Why would the Ubuntu devs think it good to include an unstable boot loader?

---

### Post by jmsa on 2009-12-31
Someone says is not to hate a bunch of 0's and 1's, so I don't hate grub2 but it does not work for me. My case, dell vostro 1320, dual boot windows 7 and karmic. Each time a I boot Windows risk grub2 being striped letting system unbootable. It seems that grub 2 stages in MBR are larger than grub-legacy or Windows loader and some actions of some Windows (or Dell) software clean reagularly that extra zone... So every 2,3,4 or 5 windows boot (or every one if windows updates something) I must boot with a rescue CD a reinstall grub2. In this forums I found a solutions with easyBCD and letting W7 boot Ubuntu, I'm not confortable with that option so I'm going for grub-legacy instead someone has a solution not involving windows.

That proves grub2 is not ready, repeat, is not ready for prime time. I used to recommend ubuntu in dual boot to people that are acustomed to windows, but with grub2 I cannot do such recommendations.

---

### Post by emeraldgirl08 on 2010-01-01
> **running_rabbit07 said:**
> Nope don't hate it. You don't even have to use it. Install Karmic, tell it not to install grub, place Jaunty disk in drive, use it to install grub and you can be happy.

I am happy with grub2, it works, it boots just as fast, and it didn't cost a thing.

This seems easy enough to do and makes sense to me :)

Thanks!

---

### Post by iris-n on 2010-01-02
@drs305

Thanks for the reply. Actually the MBR is on the first disk, and grub2 is installed on the second. So if I just exchange the boot order, it won't boot at all. What I should do is to exchange the order and reinstall grub2. Not in the mood to learn its arcane ways. I'll just wait for 1.97.1 hit karmic updates, they fix the bug there.

Sorry about the GUI, it was ignorance of my part. Splash themes are still lame, though.

---

### Post by PapaRaven on 2010-01-21
1) Toshiba Satellite P35-6292 (has ATI Radeon Mobility 9600/9700)
2) Fresh install if Karmic minimal system from the server CD.
3) Boot into system.
4) Grub2 starts up but, in short order, got a black screen of death.

Who needs that kind of aggravation? I spent some time Googling on my adjacent Mac, but finally said f*^$# it.  Went into 'safe' mode and replaced Grub2 with Grub1 and the BSOD went away.

What the Googling exercise did do though is educate me on just how complicated Grub2 has become.  When it is out of Beta I'll probably give it another try, if only for the Hollywood special effects possible at boot time.  :popcorn:
(would there be any other reason to switch?)

---

### Post by AlexanderDGreat on 2010-01-22
> (would there be any other reason to switch?) -- True, why don't they get it? They change something drastically without looking at the consequences. This leaves us lifeless in the open. I installed Karmic on Raid1 setup server, Jaunty was ok, but Grub2 won't install. Frustrating... Have to search for answers before I can get REAL WORK DONE!

---

### Post by user1397 on 2010-01-23
Hmm while it seemed different and weird at first, grub2 essentially does its job, and much more efficiently than its predecessor.  we just have to get used to it, cause its here to stay.

---

### Post by d3v1150m471c on 2010-01-23
I have no problems with it. I can do a complete reboot in 30 seconds or less and my computer hauls balls. I also run preload.

Toshiba L305, Intel Core Duo T4200 2.0ghz, 2.8mb RAM.

---

### Post by gilson585 on 2010-01-23
Plain and simple, GRUB2 does not work with fakeraid and thus is forcing users back to either older versions of Ubuntu or reverting to legacy grub after the install is complete. I wrote a little how to for 9.10 karmic and fakeraid here [http://ubuntuforums.org/showthread.php?t=1360445](http://ubuntuforums.org/showthread.php?t=1360445) I know this in fact works on Raid 0 stripped setups though I have little feedback on if this process allows Raid 1 to boot. Although GRUB2 should be fixed by 10.04 and shall hopefully boot fakeraid flawlessly by then.

---

### Post by jeremyjjbrown on 2010-01-23
Grub2 is a crapshoot.

It worked great on my laptop with win7 and 9.04.

It wasted 10 or 12 hours of my time trying to get it to boot win7 and 10.04/9.10 on my desktop with very vanilla hardware. There's no way to fix it properly without a hack or work around. In grub0.9 I could edit a text doc and be back in business in a few minutes.

I my opinion including it in ubuntu way before it is ready is a much bigger gaffe than the sound and video joke that 8.10 was. One more strike like this one and I'll be moving to mint.

---

### Post by AlexanderDGreat on 2010-01-23
> One more strike like this one and I'll be moving to mint.

It will be worth switching just to NOT have breaks and sudden changes, count me in. Anyway, I'm fairly new, can you recommend some distro that wouldn't break and give shocking, weird, and time-wasting-errors? I think they're saying Debian Lenny or that Mint -- which one is easier, more friendly to use?

**I believe every distro has its own set of conduct and discipline by the developers so that they always stay consistent with security & software.** Sadly, I'm beginning to find out that Ubuntu's code of conduct is just to play around and apply this and that, we don't care if your system breaks as long as we have implemented what we want. The reason I can say this is because Ubuntu has done this to me a lot of times already. It confuses the hell out of me and new users as well.

---

### Post by jeremyjjbrown on 2010-01-24
> **AlexanderDGreat said:**
> It will be worth switching just to NOT have breaks and sudden changes, count me in. Anyway, I'm fairly new, can you recommend some distro that wouldn't break and give shocking, weird, and time-wasting-errors? I think they're saying Debian Lenny or that Mint -- which one is easier, more friendly to use?

**I believe every distro has its own set of conduct and discipline by the developers so that they always stay consistent with security & software.** Sadly, I'm beginning to find out that Ubuntu's code of conduct is just to play around and apply this and that, we don't care if your system breaks as long as we have implemented what we want. The reason I can say this is because Ubuntu has done this to me a lot of times already. It confuses the hell out of me and new users as well.

Mint is way easier. Debian is wonderfully stable, but not really for beginners.

---

### Post by llawwehttam on 2010-01-24
> **jeremyjjbrown said:**
> Grub2 is a crapshoot.

It worked great on my laptop with win7 and 9.04.

It wasted 10 or 12 hours of my time trying to get it to boot win7 and 10.04/9.10 on my desktop with very vanilla hardware. There's no way to fix it properly without a hack or work around. In grub0.9 I could edit a text doc and be back in business in a few minutes.

I my opinion including it in ubuntu way before it is ready is a much bigger gaffe than the sound and video joke that 8.10 was. One more strike like this one and I'll be moving to mint.

The last part is my opinion too except replace mint with arch.

---

### Post by AlexanderDGreat on 2010-01-24
> Mint is way easier. Debian is wonderfully stable, but not really for beginners. Downloading both of them now.

But since Ubuntu has also helped me tremendously, I'm going to give it one more shot, think I'm going for **LTS**, which one is better 8.04 or 8.10?

---

### Post by jeremyjjbrown on 2010-01-24
> **AlexanderDGreat said:**
> Downloading both of them now.

But since Ubuntu has also helped me tremendously, I'm going to give it one more shot, think I'm going for **LTS**, which one is better 8.04 or 8.10?

I suggest giving the Debian install manual a good look see before you decide which direction to fly to.

---

### Post by jeremyjjbrown on 2010-01-24
> **AlexanderDGreat said:**
> Downloading both of them now.

But since Ubuntu has also helped me tremendously, I'm going to give it one more shot, think I'm going for **LTS**, which one is better 8.04 or 8.10?

Go with 8.04 

Ubuntu implemented a lot of new stuff for 8.10 that causes mucho problems on some peoples hardware. Especially HD audio buses. There are also alot of video issues with 8.10.

---

### Post by jeremyjjbrown on 2010-01-24
After doing some digging I have to divert my blame for the grub2 problems I've been having from Ubuntu to the Grub people.

It seams they decided to move grub1 to legacy and stop supporting it way before they were finished with Grub2. There is supposed to be a GUI editor for grub2 that will make it easy to change settings, for now they are trying to get by letting startup manager do that job, except it doesn't do the job, and it doesn't default install with ubuntu, and no one tells you these things until you've spent your whole weekend <snip> about.

---

### Post by PapaRaven on 2010-01-24
> **ubuntuman001 said:**
> Hmm while it seemed different and weird at first, grub2 essentially does its job, and much more efficiently than its predecessor.  we just have to get used to it, cause its here to stay.

... Except when it doesn't work, per the previous 'crap shoot' comment.  Too bad its installation was not contingent on being [absolutely] known to be supported under certain configurations.  Hell, even providing an installation choice like, "Grub2 is now the default boot loader.  Would you like to install the legacy Grub[1] boot loader instead?  (Some configurations, to date, will not allow an out-of-box experience.)"  -- would have been the prudent approach.

---

### Post by AlexanderDGreat on 2010-01-25
> ... startup manager do that job, except it doesn't do the job, and it doesn't default install with ubuntu, and no one tells you these things until you've spent your whole weekend <snip> about. Oh, you spent your whole weekend reading about it too? I got my whole holidays making it work, and still I can't. I can't wait for 10.04 LTS - when that comes, grub2 comes with it I'm sure, more weekends to spend...

---

### Post by Dugger5688 on 2010-01-30
I also hate Grub2. Grub1 I could pretty much do any dumbass thing I wanted and it was damn, damn easy to just plop it right back on from a liveCD or the GRUB terminal if menu.lst was messed up. Just tried to do something as simple as make an external HDD mount in fstab (ntfs, no way to format it b/c it has crap I still want but no permissions for Samba unless I run it as my user) and then issued a sudo reboot over SSH and came back after I got connection timeouts to find my /boot, MBR and / thrashed by GRUB2.

---

### Post by RicardoJGD on 2010-01-30
I am sorry, 
but After being a Linux user since 1998, I never had a lot of problems like this time with grub2.
I had Ubuntu 9.04 instaled in my son's computer by wubi (to keep warranty from sellers), and tried to upgrade to 9.10 .....  "Oh, my GOD!!"
After 8 instalations, after upgrading packages, on the new boot... Where is GRUB?? the machine freeze saing lost initrd, lost image... I QUIT.
Downgraded to Ubuntu 9.04 and the machine is working very fine (thanks to home backup...)
I think there is a bug in the GRUB2 package, and I will wait for the 10.04 version, and the forum.
I need to study very deep Grub2 if it is the future (a dark future ...)

See you.
:popcorn:

---

### Post by Morbius1 on 2010-01-30
I have only 3 requirements when it comes to grub:

(1) It boots the distro it comes with. I don't use grub to multiboot so I don't care if it's even capable of booting another OS.

(2) My 3rd Party boot loader can find and boot grub2 - It can

(3) If the grub package gets updated that the installer remembers that I don't have grub in the   MBR but in the root partition of where the OS is installed. Some distros ( PCLinuxOS, the last time I used it ) have a hard time with that concept.

As long as those conditions are met, grub can go to version 3 for all I care.

---

### Post by jeremyjjbrown on 2010-01-30
> **Morbius1 said:**
> I have only 3 requirements when it comes to grub:

(1) It boots the distro it comes with. I don't use grub to multiboot so I don't care if it's even capable of booting another OS.

(2) My 3rd Party boot loader can find and boot grub2 - It can

(3) If the grub package gets updated that the installer remembers that I don't have grub in the   MBR but in the root partition of where the OS is installed. Some distros ( PCLinuxOS, the last time I used it ) have a hard time with that concept.

As long as those conditions are met, grub can go to version 3 for all I care.

What 3rd party bootloader do you use? I'm not interested in using Grub in it's current state.

---

### Post by Morbius1 on 2010-01-31
BootITNG: [http://www.terabyteunlimited.com/bootit-next-generation.htm](http://www.terabyteunlimited.com/bootit-next-generation.htm)

It's not pretty and it's not free. It initially takes a little getting used to but once it's initially set up everything is point and click. Been using it for years ( close to 10 if memory serves ) with only one incident. PCLinuxOS overwrote the MBR with grub even though that's not where grub was originally installed. The fix with BootIT took less time than it took to boot to the BootIT install disk.
 
It says on the web site that it's compatible with Vista and Win7's new bootloader but I have not tested this myself. Since it's commercial software I would guess that it is or else they'd be out of business.

---

### Post by KegHead on 2010-01-31
Hi!

My Dell 9 and compaq are flawless.

KegHead

---

### Post by spiralx on 2010-01-31
I also discovered it , the hard way, when I upgraded a 9.04 to a 9.10 and suddenly couldn't find the "list" I was so used to editing!

But - once I'd read it up (thanks, Ubuntu team, for not warning anyone), I was OK with it.  

Yes, it multi-boots Vista and Win-7 with 9.10 just fine.   I have just deleted off old kernels, with a bit of help from the Basic User Notes, too.

If I had fault to find - it's as DOS-ugly as it predecessor, and it desperately needs a decent GUI manager built-in to 10.04 to make it simple to change, tart up, etc.

---

### Post by DCMR2 on 2010-02-05
I'm just trying to change the boot order. I created an new *40_custom* file and copied entries from the *grub.cfg* file and rearranged and saved the file. Still the same menu on reboot. Does the *40_custom* file stay in the *etc/grub.d/* folder? Do I copy the entire contents of the *grub.cfg* file or just the menu entries? Linux in general suffers because average home computer users can't use it. Ease of use, look at Mac. I'm not complaining though, it's a powerful, free OS. 

Don

---

### Post by drs305 on 2010-02-05
> **DCMR2 said:**
> Does the *40_custom* file stay in the *etc/grub.d/* folder? Do I copy the entire contents of the *grub.cfg* file or just the menu entries? Linux in general suffers because average home computer users can't use it. Easy of use, look at Mac. I'm not complaining though, it's a powerful, free OS. 

Don

1, It stays in the /etc/grub.d folder.
2. Copy the menu entries below the existing 4-5 lines already in 40_custom.
Here is an example entry. Don't forget the **}** on the last line:
> menuentry "  Karmic Current"  {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 5a880a39-36a1-46f5-b106-e979608f295a
	linux	/vmlinuz root=UUID=5a880a39-36a1-46f5-b106-e979608f295a ro   splash quiet
	initrd	/initrd.img
}
3.. It must be executable.  (sudo chmod +x /etc/grub.d/*_*) This shouldn't be necessary.
4. You must run "sudo update-grub" for it to be incorporated into the grub.cfg menu.

Technique: Rename the file 06_custom to place your entries at the top of the menu instead of at the bottom.

Also, you said you created a "new" 40_custom. You just have one 40_custom file in the folder, right?

---

### Post by DCMR2 on 2010-02-05
Ahh, I missed the *sudo update-grub* step. I created a *40_custom.bak* file in case something went wrong. Thanks for the help. I'll give it another try.

---

### Post by Al Fischer on 2010-02-08
You can add me to the Grub2 haters group. and most likely to the ex-ubuntu users group. Looks like they got some leftovers from the MS developers team working.

It's like OK open your mouth and swallow this, Wasn't that GOOOD!

---

### Post by Kir_B on 2010-02-09
Hey everyone, I'm a relative newbie {4+ months} and I can say that I don't necessarily hate grub2. Now, having said that, I was  introduced to a non bootable system for three terrifying days, all because I read about how huch better grub2 was when compared to the "old used up grub legacy" {reading can be dangerious}. I  thought it would be wise to upgrade my grub, of course without knowing the risks involved disabling my vista & Ubuntu. I researched and attempted the upgrade for five days following instructions from a few different reputable sources {one of them from the Ubuntu documentation site}, before I ran completely out of luck. After completely researching the life out of my problem for three terrifying days, I finally swallowed my pride and started a thread seeking help. Lucky for me, all you folks are extremely helpful and I'm still running Linux,  and probably still will  be when death rips it from my dead cold hands.

So, no, I don't hate grub2 {after all, It's serving an important role for me NOW}, but I do feel that it was released before it was ready for prime time and it should have come with a;
[SIZE=7][COLOR=Red]BIG BOLD WARNING OF THE DANGERS !!!![/COLOR][/SIZE]

[SIZE=1][COLOR=Black]Peace everyone. Kir_b[/COLOR]\\:D/[/SIZE]

P.S. I did learn a tonne thanks to the grub2 upgrade, but it may have come at a future price, as I'm not near as terrified of buggering things up now. Only time will tell if wisdom prevails or... Oh and here's the link to the thread that solved my problem: [COLOR=#cc33cc][my grub2 nightmare won't end]("http://ubuntuforums.org/showthread.php?t=1325901")[/COLOR]

---

### Post by bhaverkamp on 2010-03-08
Yup, i agree. What POS! Somewhere along the line it's no longer auto selecting. I can't find the freaking file that's foo-bar'd. Did MS offer this to the OS community. Trying to make it as covoluted as windows?

---

### Post by tigang on 2010-03-12
I have an issue with Grub2 that I simply cannot find an answer to anywhere else... so I thought I'd try here.

I have four systems all running Karmic with Grub2, but one of them is a dual-boot with M$ XP on sda and Karmic on sdb. The dual-boot machine has worked flawlessly for 18 months, including the upgrade(?) to Grub2.

However... one day, after having installed a routine update offered to me by Update Manager, the next reboot took me to the Grub2 recovery prompt. I followed the Grub2 guide published under the Community Documentation pages and easily got things working again, but... now _**every single time**_ I install a system update that involves grub doing an automated 'update-grub' I get the dreaded Grub2 prompt on next reboot :mad:

Recovering from the prompt is easy... I just use the insmod, linux, initrd and boot commands and up comes Ubuntu. To correct the problem I do an install-grub and then an update-grub and then Grub2 behaves itself until the next system update, then it is back to the fatuous Grub2 prompt, arghhhhhhhhhh!!! :evil:

This is really frustrating, because there must be something set wrong somewhere that Update Manager and apt-get read for the grub-update they do to screw Grub2 for the next reboot, because my doing an install-grub and an update-grub only temporarily fixes the problem.

I have tried uninstalling Grub2 and then reinstalling it and even upgraded to 'in development' Lucid and the problem remains... in fact it happens more often now because Lucid has updates practically every day while it is in development.

So.... any ideas my esteemed colleagues?

---

### Post by drs305 on 2010-03-12
> **tigang said:**
> 
So.... any ideas my esteemed colleagues?

Is Grub 2 installed on sda or sdb? 

Have you tried 'purging' grub and grub-pc and then reinstalling. I posted the procedure yesterday here: [http://ubuntuforums.org/showpost.php?p=8949452&postcount=9]("http://ubuntuforums.org/showpost.php?p=8949452&postcount=9") If the link doesn't take you to the correct post, just remove the "&postcount=9".

If you are still having problems this would probably merit it's own thread with a re-description of the problem. Posting the results of  meierfra.'s [boot info script]("http://bootinfoscript.sourceforge.net/") might be helpful, although if your system is currently running it may not show us what happens after an upgrade.

---

### Post by tigang on 2010-03-12
Thank you for your reply drs305.

Grub2 is installed on sdb. I purged and reinstalled but have yet to receive a major update to test whether the problem is resolved.

I think I tried deleting and reinstalling Grub2 before, but I have a feeling I did not 'purge' to get rid of the old configuration files, so fingers crossed this has now worked.

I will post back as soon as I have the next major update to test it on.

Once again many thanks and best regards.

---

### Post by uRock on 2010-03-12
I think grub2 is the best. No more opening and editing files just to add a new OS. You just add the new OS and run sudo update-grub and then you can boot into your newly added OS and vice versa, delete the other OSes partition and run the same command. Why is this so hated?

---

### Post by anticapitalista on 2010-03-12
The old grub did the same.

---

### Post by tigang on 2010-03-27
Well... major update today... reboot and... GRUB PROMPT AGAIN... arghhhhhh!!!!! #-o

So let's recap... you completely purge and reinstall and it still needs a 'manual bootstrap' if an update requires Grub2 to update.

This is REALLY annoying... any other ideas folks?

Many thanks in advance.

---

### Post by thamadgreek on 2010-03-27
I was reading this and wanted to clarify that this will resolve my issue. I now can not find my vista partition when GRUB boots. I am able to get to my Ubuntu OS. How am I able to boot into my Vista partition? Your assistance is greatly appreciated.

---

### Post by Kir_B on 2010-03-27
> **thamadgreek said:**
> I was reading this and wanted to clarify that this will resolve my issue. I now can not find my vista partition when GRUB boots. I am able to get to my Ubuntu OS. How am I able to boot into my Vista partition? Your assistance is greatly appreciated.

It sounds like you need to update your grub config file.

Once your in your ubuntu, try the following command in a terminal:

```
sudo update-grub
```Hope that helps. kir_b

---

### Post by thamadgreek on 2010-03-28
> **Kir_B said:**
> It sounds like you need to update your grub config file.

Once your in your ubuntu, try the following command in a terminal:

```
sudo update-grub
```Hope that helps. kir_b


Fabulous worked like a charm. Thank you so much Kir_B!!:KS

---

### Post by Kir_B on 2010-03-28
> **thamadgreek said:**
> Fabulous worked like a charm. Thank you so much Kir_B!!:KS

Thanks for the response and I'm happy that it worked.

At some point that "sudo update-grub" command is going to be the most popular and/or most recognised command for Ubuntu/grub2 users.

I'm glad I could help.

---

### Post by tigang on 2010-03-30
> **tigang said:**
> Well... major update today... reboot and... GRUB PROMPT AGAIN... arghhhhhh!!!!! #-o

So let's recap... you completely purge and reinstall and it still needs a 'manual bootstrap' if an update requires Grub2 to update.

This is REALLY annoying... any other ideas folks?

Many thanks in advance.

I have only had problems with this one machine and the only difference is that this one has Windoze and Ubuntu on separate disks and the other machine (which has been fine) has the same on different partitions of the same disk.

Maybe there is a problem with the 'install updates' process that does something wrong when operating systems on the Grub2 menu span two physical devices? I'm stumped :?:... and more ideas my esteemed colleagues?

---

### Post by Kir_B on 2010-03-30
> **tigang said:**
> I have only had problems with this one machine and the only difference is that this one has Windoze and Ubuntu on separate disks and the other machine (which has been fine) has the same on different partitions of the same disk.

Maybe there is a problem with the 'install updates' process that does something wrong when operating systems on the Grub2 menu span two physical devices? I'm stumped :?:... and more ideas my esteemed colleagues?

That can not be the case, as I have had multiple episodes and like your latter machine, my box has Windoze on the sda3 partition and Ubuntu on the sda6 partition. 

In other words, I have Ubuntu and Windoze on the same hard drive and still, this has occurred on different occasions.

As to why, some of us are having such problems is anyone's guess, but I haven't had a problem for the last couple of Kernel updates. Here's hoping that I am done with this issue, but I'll continue to run the "sudo update-grub" command, prior to rebooting, following major updates involving Kernels, Headers, Mesa, Etc.

Good luck all. Kir_b [-o<

---

### Post by tigang on 2010-04-01
> **Kir_B said:**
> That can not be the case, as I have had multiple episodes and like your latter machine, my box has Windoze on the sda3 partition and Ubuntu on the sda6 partition. 

In other words, I have Ubuntu and Windoze on the same hard drive and still, this has occurred on different occasions.

As to why, some of us are having such problems is anyone's guess, but I haven't had a problem for the last couple of Kernel updates. Here's hoping that I am done with this issue, but I'll continue to run the "sudo update-grub" command, prior to rebooting, following major updates involving Kernels, Headers, Mesa, Etc.

Good luck all. Kir_b [-o<

Oh well, looks like it is just some messed up setting that cannot easily be changed. I will do the same as you and run an update-grub prior to all post-update reboots.

Thanks all - if there are any break-throughs please post back.

---

### Post by tigang on 2010-04-02
I don't believe it ](*,)

I just did an update that added a new Linux image, did a manual update of grub, rebooted and... the stupid Grub command prompt AGAIN!!!

I give up, I've tried everything now! I can't believe nobody else out there is not experiencing this.

---

### Post by Objekt on 2010-04-02
After putting up with GRUB 2 for the first few months, I moved back to legacy GRUB.

I'm not really happy with either version, for different reasons.  

Old GRUB works and is easy to configure, but is also easily confused.  Change the hard disk boot order in your BIOS, disconnect an external HDD, or delete a partition, and you may get an Error 17 (or some other number) on the next boot attempt because the boot-time drive or partition enumeration has changed.  Manual editing of menu.lst through a Live CD session, and/or BIOS settings, is required.  This, in turn, requires additional reboots.

GRUB 2 doesn't have the enumeration confusion problem, perhaps because it refers to volumes by UUID (if I understand it correctly?).  However, GRUB 2 also added 20 seconds to my boot time, for no apparent reason.  Others with multi-OS setups have reported this problem, but worse, to the tune of several minutes' delay.

I would gladly reinstall GRUB2, if the devs at least fixed that "mysterious boot delay" bug.

---

### Post by estyles on 2010-04-02
> **Objekt said:**
> GRUB 2 doesn't have the enumeration confusion problem, perhaps because it refers to volumes by UUID (if I understand it correctly?).  

You can specify UUID in your Grub (1) menu.lst as well, if you want to.  I hate that, because it screws up if you change the size of the partition (which I do on my home machine pretty often).  Or if you try to copy your installation (by duplicating the HD or if it's a VM, cloning the VM) for rolling out multiple machines (which I do on my work machine).

To answer the original question - I hate Grub 2 also.  =)  I can see the benefits to it, but the benefits don't really apply for me, and I'm not sure they help 90% of the users, while making it more difficult to fix problems that might occur.  One of my annoyances with Ubuntu is the design philosophy of not giving any options on install.  Having something like "default bootloader, choose bootloader, do not install bootloader" as options would be nice.  For those of us that want grub 1, let us choose.  For those of us who already have a grub setup in the MBR and don't want Ubuntu to overwrite it, let us choose not to install it.  But Ubuntu, in an attempt to be simple, goes with the (abhorrent to me) Apple approach to software design - don't offer the user too many options; choose for him.

---

### Post by tigang on 2010-04-02
I suppose I joined in this discussion because I was so frustrated with Grub2 on just one of (now) four machines that use it - the only one that has Ubuntu and Windoze on separate physical disks.

I have converted so many folk to Linux (mostly Ubuntu) and I hate to think that there is something that not even I can correct when my convertees are real novices.

Ok - so back in the 80's I used to manually load a bootloader in Octal using switches on the front of a DEC PDP machine, but things have moved on and I do not expect to have to manually load stuff into Grub to get my computer booted each time there is an update that adds a new Linux image!

Going back to my original question - any more ideas on top of 'purging grub and reinstalling' and doing an update of grub before rebooting after a major upgrade?

---

### Post by Objekt on 2010-04-02
For what it's worth, supposedly GRUB2's "mysterious long delay during boot" bug is fixed as of yesterday.  I base that statement on a comment at the end of this page: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933")

I really hope that isn't an April Fool's joke.  Anyway, I suppose I'll try reinstalling GRUB2 over the weekend, to see whether the problem is truly gone.

FWIW, I use only ext3 partitions for my Ubuntu installs.  I don't know of any real benefits of ext4 to what I do, so I stick with what I know.  I should be OK until they bring out the 1 EB drives.

---

### Post by deibu76 on 2010-04-03
Being a noob and a recent convert to Ubuntu (I started with Karmic in Nov), I have a few issues with Grub2:

(1) I had quite a few problems initially.  Doing a search to fix the problem almost totally brought up fixes for legacy Grub, which didn't work obviously, and which confused me completely. 

(2) On TOP of that, when I found out things were different thanks to this "Grub2", I checked at bootup and saw I had GRUB v 1.96.  So I thought, I DIDN'T have Grub 2, I had "Grub 1".  And, this Grub 0.9x - is that this "Legacy Grub" thing...  I assumed Grub2 would be version # 2.xx.

(2) Finally managed to modify the Grub2 configuration in /etc/default/grub.  Still keep my fingers crossed everytime I do so though.  I set "GRUB_DEFAULT=saved" because I prefer because I usually want to boot into the LAST OS I selected (otherwise I'll select it manually).  Since 1.97, in order to save the last selected entry, I now also have to add the line "GRUB_SAVEDEFAULT=true".  There were apparently some problems with just "GRUB_DEFAULT=saved" on its own, but it worked for me.

(3) I have two NTFS partitions - a 55GB sda1 (Windows 7), and a 135GB sda7, which holds media, docs, a couple of virtual machines.  Everytime I update grub, I get "Found MS-DOS 5.x/6.x/Win3.1 on /dev/sda7" and it gets tacked onto the menu.  Anybody have any idea what's it's finding to detect that?  There aren't any DOS-related files or anything on the drive that I can, so I'm not sure why!  Any ideas?  This one isn't really a big deal to me though.

OTOH, setting a background image and changing the countdown time were not a problem at all for me, once I figured out what I was doing and read the right doc.  So I have to say thumbs-up on that!

---

### Post by drs305 on 2010-04-03
> **deibu76 said:**
> Being a noob and a recent convert to Ubuntu (I started with Karmic in Nov), I have a few issues with Grub2:

(3) I have two NTFS partitions - a 55GB sda1 (Windows 7), and a 135GB sda7, which holds media, docs, a couple of virtual machines.  Everytime I update grub, I get "Found MS-DOS 5.x/6.x/Win3.1 on /dev/sda7" and it gets tacked onto the menu.  Anybody have any idea what's it's finding to detect that?  There aren't any DOS-related files or anything on the drive that I can, so I'm not sure why!  Any ideas?  This one isn't really a big deal to me though.


When "update-grub" is run it searches for kernels and various boot menus  including old menu.lst files and other grub.cfg files. It may be finding an old file containing the MS-DOS reference. I would think that would be from a Windows ini file which may have been incorporated at some point.

In any case, you could try searching for the string "MS-DOS 5.x/6.x/Win3.1" to see if there is a menu with this entry which is being imported by Grub2. Have your sda1 and sda7 partitions mounted when you run the command. It may take a while since you will be searching your entire /. You could also start by searching particular folders/partitions and expand if you didn't want to take the time to search everything at first.  You could also speed the search by excluding directories, such as VM folders, with "--exclude-dir=/*path.to.excluded.directory*". Added: If you use "sudo" you will avoid some "permission denied" messages during the search.
```
sudo grep -rli "MS-DOS 5.x/6.x/Win3.1" /
```
If nothing is found, you could try narrowing the term to "Win3.1".

If the search finds the string, you might be able to remove or rename the file if it is no longer needed so that Grub2 doesn't extract the contents during it's update. And of course it *is* going to find /boot/grub/grub.cfg.

And if this doesn't work and you *really* want that menu entry gone we can work something out in the Grub2 Tweaks link in my signature line.

---

### Post by deibu76 on 2010-04-11
Thanks for the help!  I never got around to trying to figure out what the problem was. But, when I went to change the splash image yesterday, after running update-grub, the entry went away.  So I'm not sure what changed but it's gone now!

---

### Post by LewRockwellFAN on 2010-04-11
It is, well, ... less than robust. Reliance on identifying the partitions in a manner dependent on boot order rather than partition label or UUID, which is, I think, GRUB's default behaviour, means it breaks to easily if you change the number of drives connected or change the boot order, etc. I think it is all fixable but I'm still working on it myself.

But one thing to remember - it is FREE. There are other solutions that I suspect do work better, although I have no experience with Acronis or such. But you'll have to drop some change.

---

### Post by KiLaHuRtZ on 2010-05-03
My 2 cents,...LILO is better than GRUB2. ;)

---

### Post by Andy Norfolk on 2010-05-05
I'm late to this discussion but I have to say that while there are some things I like about Grub2 I hate its lack of documentation and its indiscriminate and often wrong assumptions about other OSs on my multi-boot set-up. 

I have read a lot of the documentation now appearing in various user group forums. It is quite frankly a mess! What appears in the various files on my computer does not match what is described on some fora and they do not all agree about what you can expect to see in the various files that control grub2. I knew my way around the old grub and could edit its menu.lst file and get it to do exactly what I wanted it to do. The same is not true of the new grub. 

What is needed as a matter of urgency is an editor program that will allow easy modification of grub2's behaviour. Without one grub2 is a leap backwards into the dark ages of computing. With one it would be a very useful boot manager.

---

### Post by ronnielsen1 on 2010-05-05
Late also but I'd have preferred they kept grub. I don't need the extras of grub2, it's harder (I had grub figured out) and I'd have preferred they kept grub

---

### Post by Ms_Angel_D on 2010-05-05
Moved From T&E as this is not a Testimonial or Review but a discussion on Grub2.

---

### Post by kelstertx on 2010-05-08
It also doesn't help that GRUB_SAVEDEFAULT=true doesn't work, and neither does "sudo grub-set-default N". 

So let me sum this up... now I have to 
- edit a file with near-C code, 
- recompile every change with update-grub, 
- give up control over the order it places things in the menu 
(or remove executable bits on multiple files across multiple directoris and creating a custom40 menu entry to do everything)  
- forget about ever having saved defaults

Where is the improvement?  Going with Grub2 was the stupidest choice Ubuntu has made yet in my opinion.  Now the systems I make have to be "explained" to get around the shortcoming of no saved default for users who might not want to boot into Linux every time.  Grub2 is a piece of junk, the new features aren't needed, the added complexity is stupid, and I for one would have preferred to just stay with the original grub.

---

### Post by dragos240 on 2010-05-08
I resent it. Grub legacy forever.

---

### Post by ronnielsen1 on 2010-05-10
> Where is the improvement? Going with Grub2 was the stupidest choice Ubuntu has made yet in my opinion. Now the systems I make have to be "explained" to get around the shortcoming of no saved default for users who might not want to boot into Linux every time. Grub2 is a piece of junk, the new features aren't needed, the added complexity is stupid, and I for one would have preferred to just stay with the original grub.

Excellently said.

---

### Post by ronnielsen1 on 2010-05-10
[http://uk.answers.yahoo.com/question/index?qid=20100402111244AACIy8l](http://uk.answers.yahoo.com/question/index?qid=20100402111244AACIy8l)

> **Linux ubuntu help ...i want get rid of grub 2 and replace it with just the old grub how do i do this ?**



---

### Post by sammiam on 2010-05-12
GRUB2 is HORRIBLE :mad:   I'm going to downgrade back to GRUB 1 ... what a mess... like was stated in some earlier posts... what happened to the KISS method of GRUB... it sounds like someone just went out nelly willy and made changes... I HATE GRUB2

---

### Post by MasterNetra on 2010-05-12
I personally have had no issues really with Grub2, though I wish their was a suitable utility for lucid to mod it. Ubuntu though should of waited until Grub2 was more developed before using it. But meh.

---

### Post by crobar on 2010-07-30
Grub2 sucks, all I want to do is change the text of the ridiculously complex menu entry names that have been generated and I can't. I'm sure I could figure it out after a while, but I shouldn't need to spend hours searching for a solution then wondering if I'm going to screw up my bootloader just to get a pretty menu.

---

### Post by cariboo on 2010-07-30
Have you tired [Burg]("https://launchpad.net/~bean123ch/+archive/burg")? It's the easy way to setup a pretty grub menu.

---

### Post by Kir_B on 2010-08-10
Thanks cariboo907. I'm checking it out right now!  :D

Edit: More info can be found [here]("http://ubuntuforums.org/showthread.php?t=1371288&highlight=burg+howto").

---

### Post by Spice Weasel on 2010-08-10
< --- Using LILO.

I actually prefer it to Grub. It also provides sensible error messages and doesn't have a stupid menu, you just press a hotkey to boot in to an OS.

---

### Post by RiceMonster on 2010-08-10
> **Spice Weasel said:**
> < --- Using LILO.

I actually prefer it to Grub. It also provides sensible error messages and doesn't have a stupid menu, you just press a hotkey to boot in to an OS.

The horrors of pressing down and then enter.

---

### Post by Spice Weasel on 2010-08-10
> **RiceMonster said:**
> The horrors of pressing down and then enter.

'Fraid it's not like that if you have as many OSes installed as me. :p

---

### Post by Everybody Loves Hypnotoad on 2010-10-21
I have to say, after spending some time to try to understand how to change the bootloader settings (if that is even possible) that I too, hate the plague that is grub2. 

Paraphrase:
<snip>
men nu har vi baxat det ända hit.

---

### Post by mainerror on 2010-10-21
> **jbrown96 said:**
> Does anyone else hate Grub2?

<-- No.

---

### Post by Mario13 on 2010-11-22
Standing here, in the middle of a Maverik upgrade, without being able to boot my laptop, I wolud like to say: YES, I HATE GRUB2

---

### Post by iknik on 2011-07-21
Thank god I'm not the only one. I just gave up trying to boot into my newly installed Ubuntu 11.04, and it hasn't been the first time Grub2 has crossed me. Canonical's persistent refusal to document and fix its bootloader is both frustrating and surprising. When I was just converted to Ubuntu, I was very enthusiastic (and I still am about most parts of it) and I tried to convert my friends to Linux. But I actually stopped doing that some time ago, realizing that if any of my not too computer-savvy friends encounters a showstopping Grub2-error (I'd say the chance is about 25 %) he will never use any Linux distro ever again.

---

### Post by cgroza on 2011-07-21
Ahh come on, people ended up bashing even the damn boot loader!

---

### Post by uRock on 2011-07-21
Go back to sleep.

---

### Post by drs305 on 2011-07-21
iknik,

Sorry the installation didn't work out of the box (off the disk?). 

If you want help fixing whatever the problem is there are plenty of users on this forum who can probably help you. If you want help, just start a new thread and download/extract/run the boot info script from the following site and post the contents of RESULTS.txt.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by 3Miro on 2011-07-21
> **uRock said:**
> Go back to sleep.

You do realize that the thread is still open, right?

---

### Post by alphacrucis2 on 2011-07-21
> **iknik said:**
> Thank god I'm not the only one. I just gave up trying to boot into my newly installed Ubuntu 11.04, and it hasn't been the first time Grub2 has crossed me. Canonical's persistent refusal to document and fix its bootloader is both frustrating and surprising. When I was just converted to Ubuntu, I was very enthusiastic (and I still am about most parts of it) and I tried to convert my friends to Linux. But I actually stopped doing that some time ago, realizing that if any of my not too computer-savvy friends encounters a showstopping Grub2-error (I'd say the chance is about 25 %) he will never use any Linux distro ever again.

There is actually very good documentation for grub2 here:

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

and several other tutorials around which come near the top of a google search.

---

### Post by uRock on 2011-07-21
> **3Miro said:**
> You do realize that the thread is still open, right?

I reopened it. :D

---

### Post by GSF1200S on 2011-07-21
Its fine in Ubuntu as they have scripts that auto-add new operating systems, but I dont enjoy editing grub.cfg when Arch's grub 2 is running on the MBR.. I prefer Grub 1 definitely, but I dont hate Grub 2

---

### Post by 3Miro on 2011-07-21
> **uRock said:**
> I reopened it. :D

I saw your "sleep" post and the thread was still open, so I thought you might have forgotten to hit the "kill" button.

Since the thread is still open, I will comment that I find Grub 2 hard to customize, although it is much easier if it managed to automatically detect everything. The only problem I have had is that it couldn't work right with my Gentoo installation.

Gentoo uses Grub 1 an that is what I use right now.

---

### Post by Dustin2128 on 2011-07-21
Hate grub2 with a passion, personally- so needlessly complicated compared to 1.

---

### Post by Kir_B on 2011-07-21
> **iknik said:**
> Thank god I'm not the only one. I just gave up trying to boot into my newly installed Ubuntu 11.04, and it hasn't been the first time Grub2 has crossed me. Canonical's persistent refusal to document and fix its bootloader is both frustrating and surprising. When I was just converted to Ubuntu, I was very enthusiastic (and I still am about most parts of it) and I tried to convert my friends to Linux. But I actually stopped doing that some time ago, realizing that if any of my not too computer-savvy friends encounters a showstopping Grub2-error (I'd say the chance is about 25 %) he will never use any Linux distro ever again.

While I've been having an absolute blast using Ubuntu over the past two years, I was much like you. I sung the praises of Ubuntu to anyone and everyone I met, until about the third time that I got burnt by "something", that required me to reinstall grub2, at which point I stopped just telling people about it in a casual manner and instead, I now tell them what a great experience Ubuntu and it's community has been for me, followed by, but in order to partake in this wonderful experience, you must be willing to learn, which will involve a fair amount of reading and research. It's rather  unfortunate, as I'd love to see everyone I know experience this, but the majority of them haven't done a lot of reading since they were handed their high school diploma and hearing the word read, seems to somehow feel like too much work these days.

I do hope that Canonical gets this thing figured out soon, as right now, it's the only thing keeping a lot of us from converting people away from the :evil:Micro$oft monopoly:evil:.

Peace everyone. Kirby  ):P

---

### Post by beew on 2011-07-21
The thread should die. 

Some people might have problems with grub2 several releases ago when it came out (and these people are probably still running 8.10 without support on 20 year old machines if they are still complaining) but I have never had a problem, I multiple boot different Linuxes on several machines, it works beautifully (yeah I could have used grub legacy in Fedora to control grub but guess what I much prefer grub2 from Ubuntu)  

Old timers always look to the past with distorted lenses. Like those curmudgeons who rant in coffee shops, everything was better way back when: the music was better, the movies were betters, people were more beautiful, even junk food tasted better...  , then balm! things went downhil .  It must really sucks that Ubuntu no longer supports floppies:)

---

### Post by cariboo on 2011-07-21
> **beew said:**
> The thread should die. 

Some people might have problems with grub2 several releases ago when it came out (and these people are probably still running 8.10 without support on 20 year old machines if they are still complaining) but I have never had a problem, I multiple boot different Linuxes on several machines, it works beautifully (yeah I could have used grub legacy in Fedora to control grub but guess what I much prefer grub2 from Ubuntu)  

Old timers always look to the past with distorted lenses. Like those curmudgeons who rant in coffee shops, everything was better way back when: the music was better, the movies were betters, people were more beautiful, even junk food tasted better...  , then balm! things went downhil .  It must really sucks that Ubuntu no longer supports floppies:)

First off what are you doing hanging out with curmudgeons in coffee shops? :) :) And secondly in my opinion people are much better looking now. BTW I graduated high school in 1971 so you can figure how old I am from that. :) :)

---

### Post by beew on 2011-07-22
> **cariboo907 said:**
> First off what are you doing hanging out with curmudgeons in coffee shops? :) :) And secondly in my opinion people are much better looking now. BTW I graduated high school in 1971 so you can figure how old I am from that. :) :)

Well curmudgeons are usually loud. :)

Curmudgeonry has to do with the mindset rather than actually chronological age, you seem to be a very cool guy around here. :)

Since you are a fellow Canadian you might have listened to this guy on the CBC, now that is a curmudgeon though his rants are entertainingly stupid.

[http://en.wikipedia.org/wiki/Danny_Finkleman](http://en.wikipedia.org/wiki/Danny_Finkleman)

---

### Post by Gawains Green Knight on 2011-07-22
Ubuntu no longer supports floppies? Scandalous....

---

### Post by longtom on 2011-07-22
When installing another distro using Grub legacy - which is the majority of them - Ubuntu does not get detected.

Vice versa exactly the same occurs.  Adding Ubuntu to Grub legacy is manageable for somebody like me, who knows enough to stumble along.  Doing the same with Grub 2 appears a lot more complicated for me, so I use Grub legacy, because it works for me.

SO I don't hate Grub 2, I just find it difficult to use and complicated.  

But then it's only a boot loader, whether it flashes Grub or Grub 2 for half a second in the beginning - who cares?  As long as I can choose my OS I want to start I am happy.  How can you hate a boot loader .... :confused:

---

### Post by beew on 2011-07-22
> **longtom said:**
> When installing another distro using Grub legacy - which is the majority of them - Ubuntu does not get detected.



Then don't use grub legacy.  I have a dual boot between Fedora and Ubuntu, I just didn't install grub for Fedora and ubuntu takes care of boot, it is simple and easy.

If grub2 detects other OSes but grub legacy doesn't that would be a defect of grub legacy.

---

### Post by longtom on 2011-07-22
> **beew said:**
> Then don't use grub legacy.  I have a dual boot between Fedora and Ubuntu, I just didn't install grub for Fedora and ubuntu takes care of boot, it is simple and easy.

If grub2 detects other OSes but grub legacy doesn't that would be a defect of grub legacy.


Oh - I just don't use Grub 2 ... :P

---

### Post by iknik on 2011-07-22
> **drs305 said:**
> If you want help fixing whatever the problem is there are plenty of users on this forum who can probably help you.
I know. The community has never been Ubuntu's problem. But no, sorry. Yesterday I spent an entire evening just trying to get dual boot working (11.04 was already installed), googling for solutions and trying dozens of things. And frankly, I'm fed up with it (hence the post in this thread instead of a constructive one). Grub2 has been ....... for years now, and I'm done spending hours jumping through hoops when all I want to do is install an OS.

---

### Post by beew on 2011-07-22
> **iknik said:**
> I know. The community has never been Ubuntu's problem. But no, sorry. Yesterday I spent an entire evening just trying to get dual boot working (11.04 was already installed), googling for solutions and trying dozens of things. And frankly, I'm fed up with it (hence the post in this thread instead of a constructive one). Grub2 has been ....... for years now, and I'm done spending hours jumping through hoops when all I want to do is install an OS.

Well I have a multiboot with 6 OSes and grub2 works great. I am not sure what your problems are and "sucking donkey balls" is not a very good way to describe them.

---

### Post by mips on 2011-07-22
I don't like Grub2 either, way to complicated. Instead of making things simpler they complicated it 10 fold.

Thank god Arch still uses Grub1.

---

### Post by JASONFUSARO on 2011-07-22
I was baffled for awhile, until I found Linux Commands for Grub2 and in it is How to make a Dedicated GRUB Partition, that squared away some Distros not getting found using update-grub. Now I just modify the grub.cfg there on sda2 which is not tied to any particular distro and everything has been great, don't even have to worry about running update-grub on a new install, just install grub to the same partition that the distro is on, copy the menu entry for it into grub.cfg on the grub partition and reboot.

Haven't had a problem since. I think I am still a newbee too?


***EDIT***

Here are some links that have been a  real help to me.

Both are thorough and extremely well written.


[http://kubuntuforums.net/forums/index.php?topic=3117206.0](http://kubuntuforums.net/forums/index.php?topic=3117206.0)

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by capink on 2011-07-22
I stayed away from grub2 to give it a chance to mature and phase out whatever bugs it might contain. The first time I tried grub2  when Natty was released. Overall I like grub2 better than grub-legacy.

Editing the menu items is not much complicated than grub-legacy. There are only 4 easy modifications to make:

1. Instead of writing:

```
title [COLOR="Magenta"]<insert whatever name you want for your os>[/COLOR]
```

replace it with

```
menuentry "[COLOR="Magenta"]<insert whatever name you want for your os>[/COLOR]"
```


2. You put the rest of the entry in curly brackets {}

3. Instead of the command:

```
root	 (hdX,Y)
```

you write the following:

```
set root=(hdX,Y)
```

4. You replace the command kernel with the command linux.


everything else is the same when it comes to editing the menu entries.




**_[SIZE="2"]Advantages of grub2:[/SIZE]_**

[LIST]
[*]Automatic detection of OSs. Even if you don't like this you can turn it off using the following command

```
sudo chmod -x /etc/grub.d/{1,2,3}*
```



[*]No direct editing of the grub.cfg is a huge plus as it guards against mistypes and mistakes. To add any custom entry edit the file:

```
sudo gedit /etc/grub.d/40_custom
```

After you finish adding the entries you want you have to run the following command:

```
sudo update-grub
```

Any changes you made will be included after being checked.

Again, Even if you don't like this and want to edit grub.cfg directly you can do so. But first you have to remove the readonly flag by running this command:

```
sudo chattr -i /boot/grub/grub.cfg
```


Note that any changes you make by editing grub.cfg directly will be overwritten on the next kernel update. It is really better approach to edit /etc/grub.d/40_custom



[*]You can set the root based on UUIDs and LABELs. For me this is a major advantage as they are not subject to change.

You can do this by using the search command to set the root variable - instead of setting directly by: set root=(hdX,Y) -

```
search --no-floppy --fs-uuid [COLOR="Magenta"]<insert UUID here>[/COLOR] --set
```

or if you you want to use LABELs

```
search --no-floppy -l [COLOR="Magenta"]<insert LABEL here>[/COLOR] --set
```



[*]The ability to set variables and other bash like features is really handy. It might not be important for all people. But if you don't need it, don't use it.



[*]Booting ISO images is nice.



[*]Apparently, themes and background options are improved. It is not for me so I have not really tried it.
[/LIST]



There are things I miss in grub-legacy like being able to log into a grub terminal emulator by typing sudo grub. Also the ability to install grub to the harddisk in a grub terminal using the root and setup command, instead of having to boot fully into linux and use the grub-install commands. However, this was deemed dangerous and thus removed from grub2.

---

### Post by henteaser on 2011-12-09
I agree. Grub2 is the most stupid invention since ... well ... it's just the most stupid thing I can think of right now. 

I mean, I have to edit the default OS among a list of files that are not even human readable, but instead some kind of programming language. 

I guess the guy who came up with grub2 thinks he's smarter than all of us end users and has thought of every possible scenario out there, so let's not bother the end-user with those things.

Grub2 is even more stupid than the windows default setting of warning the user to access the program files folder:

---
This folder contains your program files. There is no need to edit them

[Click to show files]
---

In grub2 we can't even unlock the stupidity lock.

---

### Post by piledriver on 2012-05-12
After many years of trying, I finally got a version of Ubuntu to install on something and (almost) work properly. (Xubuntu 12.04, as PAE is required on all other versions, absolutely ridiculous, my little Pentium M laptop is faster than most P4 systems, PM arch was later essentially rebranded "CORE", you may have heard of it)

Grub2 borked the "other OS" autodetect, so I could only boot into Xubuntu or Windows, mageia2s entry did not work for direct loading, and it did not pick up on the grub1 install on the partition.

I manually recovered it editing  setting up a custom entries, as I set Mag2s bootloader on it's root partition, something that GRUB2 appears incapable of doing properly, *even when forced*.

In any case:
//rant mode on
I want a boot loader, not an unreliable, confusing mess larger than some complete operating systems.
... And supplied WITH NO ALTERNATIVES.

Not all noble intentions work out well... GRUB2 is one of the failing cases.

If they wanted something USEFUL they could develop a universal EFI emulator/miniOS that could be disc based, and boot to/from that. That would be MORE flexible, simpler, and universally useful.

Non-EFI bootloaders will be dead in a couple years in any case on new hardware, this would TRULY be a UNIFIED bootloader that would allow older hardware to be EFI compatible, and the world could move on. 
(Something like DUET+Clover)

Using Linux on the desktop since 1994.
(Slackware or Debian, mostly)
//end rant

---

### Post by wilee-nilee on 2012-05-13
Grub 2 the best thing since sliced bread, viva the os-prober and the 40_custom file. :)[I]
[/I]

---

### Post by zombifier25 on 2012-05-13
I prefer Burg :lolflag: It makes my computer NOT look like it's from the 90s.

(Grub is themeable, yes, but there are very few themes, and installing them is not as easy as Burg)

---

### Post by Bandit on 2012-05-13
I liked the 90's for the most part. Big hair, cowboy boots and rock ballads.. :)

---

### Post by wilee-nilee on 2012-05-13
> **zombifier25 said:**
> I prefer Burg :lolflag: It makes my computer NOT look like it's from the 90s.

(Grub is themeable, yes, but there are very few themes, and installing them is not as easy as Burg)

Burg is grub.

---

### Post by Lucradia on 2012-05-13
> **wilee-nilee said:**
> Burg is grub.

Burg Uses Retro GRUB ;)

---

### Post by wilee-nilee on 2012-05-13
> **Lucradia said:**
> Burg Uses Retro GRUB ;)

Just a little earlier version of grub 2, give it the name you like, it is grub 2 with themes.

Certainly a usable bootloader.

In a boot script it looks like this, identical files with burg rather then grub used.

```
/boot/grub/grub.cfg /boot/burg/burg.cfg /etc/fstab 
                       /boot/grub/core.img /boot/burg/core.img
```

---

### Post by cecilpierce on 2012-05-13
Burg is easy and fun to play with.
First one is Grub journey theme
  :)

---

### Post by flemur13013 on 2012-05-13
> Grub2 is a huge PITAYes! 

It's one of the kludgiest, most user-hostile pieces of software around; symptomatic of that is the fact that the author(s) can't even give it coherent version numbers (grub2=v1.9 or some nonsense:lolflag:).  Too bad it's so important. 

I always immediately replace it w/the previous "legacy" version, which isn't as bad.

---

### Post by flemur13013 on 2012-05-13
> **jbrown96 said:**
>  I still have no idea how I would add a new entry. Where would it go? 

Just edit the grub.cfg file like they SAY NOT TO DO BECAUSE THAT'S TOO EASY and keep  copies of the original and the new one.

---

### Post by kiyop on 2012-05-27
[My tool]("http://kiyoandkei.blog68.fc2.com/blog-entry-52.html") can search for menus for grub2 and grub legacy in all the partitions and boot linux using the information on the found menus.

> **jbrown96 said:**
> I still have no idea how I would add a new entry.
As you know now, add to /etc/grub.d/40_custom or so.

---

### Post by kiyop on 2012-05-28
There are two reasons I hate installing grub2 onto MBR.

1) Menuentries of Grub2 is not updated even when the kernel of an pre-installed linux distribution diffrent from the linux distribution which installed grub2 onto the MBR is updated. So, the old kernel is called before update-grub is executed in the linux distribution which installed grub2 onto the MBR.
In one of my computers, more than 10 linux distributions are installed on separate partitions, (for testing).

2) Some partitions cannot be recognized by grub2.
For example, a partition of an USB-3.0-HDD connected to an USB-3.0-port of one of my computers.
A partition of an USB-2.0-HDD connected to one of my computers which has a BIOS which does not support boot from USB-HDD. 
And a btrfs partition before.

So, I use my tool. 
Grub2 is useful. Grub2 makes good configuration file: for example, /boot/grub/grub.cfg.
I make my tool use Grub2 configuration file.

---

### Post by drs305 on 2012-05-28
> **kiyop said:**
> There are two reasons I hate installing grub2 onto MBR.

1) Menuentries of Grub2 is not updated even when the kernel of an pre-installed linux distribution diffrent from the linux distribution which installed grub2 onto the MBR is updated. So, the old kernel is called before update-grub is executed in the linux distribution which installed grub2 onto the MBR.
In one of my computers, more than 10 linux distributions are installed on separate partitions, (for testing).

Grub 2 updates the currently running menu when a kernel is added, but you are also correct that if it isn't the controlling Grub the controlling Grub's menu isn't automatically udpated. 

If this is a concern you could always have 'update-grub' run on boot and it would import the latest entries from your other installations' setups.

---

### Post by alelinuxbsd on 2012-05-29
More then hate i found Grub2 quite annoying and unnecessarily complex.
For example using Grub2 i can't access on Bsd system as, for example, OpenBSD.
Also i don't like that every OS on my system is visible during the boot.

With grub 1 is sufficient edit a single configuration file and everything is more easy and work.

---

### Post by kiyop on 2012-05-29
Thanks for the following comments of yours, drs305:)

> **drs305 said:**
> Grub 2 updates the currently running menu when a kernel is added, but you are also correct that if it isn't the controlling Grub the controlling Grub's menu isn't automatically udpated. 

If this is a concern you could always have 'update-grub' run on boot and it would import the latest entries from your other installations' setups.
Can we make "update-grub" executed everytime Grub2 code started without booting the linux distribution which has the controlling Grub2?
For example,

/dev/sda(MBR) has Grub2 code installed by ubuntu on /dev/sda2
/dev/sda1: Debian (not controlling grub2)
/dev/sda2: Ubuntu (controlling grub2)
Ubuntu is not booted.
Debian is booted always.
Is the grub2 menu (called by grub2 code on MBR) updated, when Debian kernel is updated?

In other words, can we add some code like "update-grub" in /etc/grub.d/00_header or /etc/grub.d/05_debian_theme in order that update-grub is executed whenever grub2 code on MBR read /boot/grub/grub.cfg on the controlling grub2 partition?

But.....even if the above thing can be done, "update-grub" takes loooong time (especially on one of my computer, which has more than 10 linux distributions) and I do not like it.
So, I disable /etc/grub.d/30_os-prober by adding
GRUB_DISABLE_OS_PROBER="true"
into /etc/default/grub
and I use my tool.

I know that you can boot Grub2 on another partition different from the partition with controlling grub2 by code in /boot/grub/grub.cfg (/etc/grub.d/40_custom):
```
menuentry "debian grub2 on /dev/sda1" {
insmod ext2 # or so
insmod multiboot
set root="(hd0,msdos1)"
multiboot /boot/grub/core.img
}

```I know that you can use Grub2 configuration file on another partition different from the partition with contolling grub2 by code like:
```
menuentry "/boot/grub/grub.cfg on /dev/sda1" {
insmod ext2 # or so
set root="(hd0,msdos1)"
configfile /boot/grub/grub.cfg
}
```

---

### Post by drs305 on 2012-05-29
kiyop,

I don't know of a way to update-grub from the Grub menu, but I can see why you wish that it did.

One thing I can think of would be to build a custom menu with the "maintenance-free" version of each OS. By mx-free, I mean that you don't specify the kernel but point to the symlink for the kernel and initrd image in /.  You could put this custom file in a data partition and place it's link in each of your OS's /etc/grub.d folders so it was included in every menu.

At least for Ubuntu family OS's, they all place symlinks in /, called *vmlinuz* and *initrd.img* These point to the most recent versions of the kernel in the /boot folder.

Here is a link to a thread about maintenance-free menus by forum member Cavsfan:
[http://ubuntuforums.org/showthread.php?t=1542338]("http://ubuntuforums.org/showthread.php?t=1542338")

---

### Post by kiyop on 2012-05-30
Thanks drs305. :)
I will read the thread for maintenance-free menus by forum member Cavsfan:
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

---

### Post by kiyop on 2012-06-29
I read roughly the thread for maintenance-free menus by forum member Cavsfan:
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

Unfortunately I understand that the method written in the thread can not boot correctly linux distributions with most recent kernel if the distributions does not make symlinks to the most recent kernel.

[s]For example, slackware does not make.
 [http://forums.debian.net/viewtopic.php?f=10&t=81227&p=441157#p441092](http://forums.debian.net/viewtopic.php?f=10&t=81227&p=441157#p441092)[/s]
EDIT: slackware seems to make a symlink /boot/vmlinuz to the recent kernel.  

Furthermore, some linux distributions need specific kernel options to be booted correctly and sometimes it changes. For example, "nomodeset", "acpi=off" and so on. 

To modify the kernel option for correct boot of a distribution installed in a partition, modification of the configuration files of the kernel loader (such as Grub2, Grub legacy, Grub4dos, lilo, syslinux, and so on) is necessary, but with Grub2 it is difficult for me to modify the file. Of course, I know that pressing E key at grub2 menu enables temporary edition of the configuration. But with my tool, linux kernel with modules boots and for me it is easier to modify with my tool, because I am used to operating commands on linux (with shell scripts).
My tool has good points of both of kernel loader (easy booting) and rescue linux distribution such as systemrescuecd (easy manupilation of shell commands).

So, I decided to use my tool and the configuration files prepared by Grub2 and so on.

---

