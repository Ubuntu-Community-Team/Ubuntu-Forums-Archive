---
title: "gnome / grub2 in ubuntu server 10.10"
date: 2011-02-08
forum: Server Platforms
---

### Post by red1916 on 2011-02-08
Hi,

I installed ubuntu server 10.10, in an effort to learn as much as possible about linux so this question is more theory than anything in some aspects, so any link with extra info on the answer that you could share would be much appreciated... 

I had server 10.10 installed and was working in CLI perfectly. I installed gnome because I wanted to be able to start xwindows using "startx" if ever needed. but now server boots always to gnome. so there is two things I tried to do and I would like to learn how to do and in the quest I learnt lots but also got quite confused :)

1) remove gnome-ubuntu, why not, one can always get rid of things you don't need any more :)

to install it I used apt-get install ubuntu-desktop so I thought apt-get remove ubuntu-desktop, or aptitude purge ubuntu-desktop, should do? nop

also a note, is not gdm (the x display manager) I need to remove or modify, it is the whole gnome I want to remove. 

so far in forums, the approach I found is to reinstall again server edition. but isn't gnome just a package like all the rest? so shouldn't aptitude for example be able to remove it with all its dependencies?    

2) I also would like to know how to keep an xwindows package installed if that was my option but for ubuntu to boot on CLI

I found server 10.10 runs grub2 so the old tricks won't work... the closer I came was to do:

vi /boot/default/grub

change this line from "quiet" to "quiet text" 
GRUB_CMDLINE_LINUX_DEFAULT=”quiet text”

and after run
update-grub

now it will boot in CLI but to my surprise I found server was behaving strangely, some example:
a) I could not set up the wireless network, it just would not work (and it did before from CLI, I even follow all steps i did initially to configure it), 
b) if run startx is not possible to swith between users, for the user I got with su privilages so I don't log in as root, it starts gnome with user root.

so my question here is a little bit of both theory and practical:

maybe change runlevel is the approach, what are each runlevel doing in ubuntu?
is this CLI I am booting now different from the one originally I had right after initial installation?  because I got a feeling that gnome takes control of certain files, modifying the way OS works,  and that is why for example, I can't configure the wireless network now, as the file /etc/network/interfaces won't operate any more?    

sorry I am dumping here lots of different questions but after going through lots of forums and the official documentation I am still in darkness in all this grub modifying/ runlevels / gnome xwindows issues

so again, this server is a test/learning experiment for me so if questions are too stupid, or approach is wrong, whatever, feel free to communicate it ha ha ha...nut feelings hurt :) and of course, it s not any urgent so, please give priority on solving issued to others. 

thx in advance

---

### Post by theDaveTheRave on 2011-02-08
I did a similar thing with a server I set up for colleagues.

the difference was that 'they needed' the nice gui desktop (scared of terminal).

On my home desktop (running from a basic server install) I also have the gui set to run.

When I start up I get the graphical login screen, and somewhere near the bottom is a set of options to change the type of dekstop i log into. One of the options is 'terminal', which i sometimes choose.

I do agree however that this will push a bunch of 'gnome' stuff into the boot sequence, and have it sitting in the background. If you want a lighter desktop for the server (eg xbox) then simply install that instead.

regarding the other questions, I assume it should be more than easy to change the run level, word of warning though, things are using the 'upstart' system, now so the old fashioned 'run levels' may not apply (you'll need to do some research into that one). Using that as a starting point I guess the solution will be to somehow remove 'gnome' (or xdm) from the upstart procedure, then you will have to < startx > manually.

David

---

### Post by red1916 on 2011-02-08
> **theDaveTheRave said:**
> I did a similar thing with a server I set up for colleagues.

the difference was that 'they needed' the nice gui desktop (scared of terminal).

On my home desktop (running from a basic server install) I also have the gui set to run.

When I start up I get the graphical login screen, and somewhere near the bottom is a set of options to change the type of dekstop i log into. One of the options is 'terminal', which i sometimes choose.

I do agree however that this will push a bunch of 'gnome' stuff into the boot sequence, and have it sitting in the background. If you want a lighter desktop for the server (eg xbox) then simply install that instead.

regarding the other questions, I assume it should be more than easy to change the run level, word of warning though, things are using the 'upstart' system, now so the old fashioned 'run levels' may not apply (you'll need to do some research into that one). Using that as a starting point I guess the solution will be to somehow remove 'gnome' (or xdm) from the upstart procedure, then you will have to < startx > manually.

David

thx for the reply, yep, I wanted to have the xwindow option only to use occasionally but the goal is to run all in CLI with commands, basically, only start gnome in counted occasions and If I needed but in general keep running only CLI so memory resources are kept low. running gnome os any xwindow desktop in the background is nt desirable for servers I think.

do you know how to change the runlevel? and which one to use? ubuntu server 10.10 uses level 2 to boot up, but this was the same when i had the CLI from clean install and after installing desktop so I think nowadays runlevels don't matter any more.

so your approach to remove gnome from the upstart procedure sounds like what i wanted :)  start on CLI and if i wanted run startx. do you know how to do it?

---

### Post by theDaveTheRave on 2011-02-08
I can't remember how you change the run levels, or rather preventing the system going past a certain run level only.

It may be possible to apply it via GRUB somehow.

So you would have a 'terminal only' option in your GRUB list. Then you can make that one your default, if you know you are going to need a GUI you can just select another at boot time (if you are sat in front of the server that is!)

this page[http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html]("http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html") gives some details on run levels, it seems you will want to stop at run level 3,or 4 (run level 5 is the GUI, and 6 sets up a reboot - so don't do that one!).

a quick read suggest that the /etc/inittab file is the one you need to edit for changing run levels at boot time.
But again, double check this against upstart, as I know that things are changing over to this from the 'old' system v init.d scripts.

at the bottom of the howto there are some interesting comments (3, 5 and 9) that seem to be related to what you want to do.

David

---

