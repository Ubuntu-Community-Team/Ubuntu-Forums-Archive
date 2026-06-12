---
title: "Alternate install CD vs Server Editon (LTSP-server)"
date: 2008-05-18
forum: Server Platforms
---

### Post by Lapp-Same on 2008-05-18
Hi

If I install LTSP with alternate CD would i get the server in a desktop enviroment or like the server edition using commands in a terminal?


-And is it like "Skolelinux", "Edubuntu" or other school servers that root or a admin can login on the server and change which user can use wich program and what the diffrent users can accses (internet, hard drives, and soo on...)

-And that only admin/root can install programs?

-And that i can change the default Theme of the LTSP-server?
And the users can change it them self later if they want someting diffrent?

Thanks for you're comment!

-Christoffer- (Norway)

---

### Post by Lapp-Same on 2008-05-18
Any one?

---

### Post by Lapp-Same on 2008-05-19
> **Lapp-Same said:**
> Any one?

No one who knows?

---

### Post by bobsta63 on 2008-05-19
> **Lapp-Same said:**
> Hi

If I install LTSP with alternate CD would i get the server in a desktop enviroment or like the server edition using commands in a terminal?


-And is it like "Skolelinux" or other school servers that root or a admin can login and change which user can use wich program and what the diffrent users can accses (internet, hard drives, and soo on...)

-And that only admin/root can install programs?

-And that i can change the default Theme of the LTSP-server?
And the users can change it them self later if they want someting diffrent?

Thanks for you're comment!

-Christoffer- (Norway)

Hi Christoffer,

You may want to check out Edubuntu (Ubuntu but designed for schools) as I know that comes with LTSP already installed and should be ready to run out of the box, Hope this helps,

Regards,
Bobby

---

### Post by Lapp-Same on 2008-05-19
> **bobsta63 said:**
> Hi Christoffer,

You may want to check out Edubuntu (Ubuntu but designed for schools) as I know that comes with LTSP already installed and should be ready to run out of the box, Hope this helps,

Regards,
Bobby

I have, but didn't want a school edition... I wanna have the orginaly Ubuntu.. since i like it the best... I'am gone use it for thin-clients at home... on the TV's, notepads and soo on...
but thank for you're post :)

---

### Post by Lapp-Same on 2008-05-19
Anyone who can help me?


-Christoffer-

---

### Post by Oak37 on 2008-05-19
I don't believe there is that much of a difference between edubuntu and ubuntu or for that matter between any versions from an aesthetic viewpoint.
You should be able to install ubuntu and then install LTSP on that. The server edition might be the better choice but it lacks a GUI by default but you can install one if needs be.

---

### Post by Thirtysixway on 2008-05-19
Edubuntu is Ubuntu, but with ltsp already enabled, and it has more applications for administration/management of a network.  Things like viewing the desktop of clients, etc.  I would just install the normal Ubuntu and add on ltsp.

---

### Post by Lapp-Same on 2008-05-19
> **Thirtysixway said:**
> Edubuntu is Ubuntu, but with ltsp already enabled, and it has more applications for administration/management of a network.  Things like viewing the desktop of clients, etc.  I would just install the normal Ubuntu and add on ltsp.

The plan where to install Ubuntu 8.04 Server Edition "Hardy Heron"
And soo X window... the dhcp, ltsp and soo on


But is it better the way you say to install orginally Ubuntu and so install Dhcp3-server and Ltsp-server ?

---

### Post by hvc123 on 2008-05-22
matey you can install ltsp on any distro.


try this 

sudo apt-get install ltsp-standalone-sserver (or something like that)

failing that use search in synaptic it is there.

to stop users installing stuff and the like all you have to do is dont give them access to the 'wheel'/'admin' group

---

### Post by Lapp-Same on 2008-05-22
> **hvc123 said:**
> matey you can install ltsp on any distro.


try this 

sudo apt-get install ltsp-standalone-sserver (or something like that)

failing that use search in synaptic it is there.

to stop users installing stuff and the like all you have to do is dont give them access to the 'wheel'/'admin' group

Then just the root or the administrator user can install stuff that others can use?

How can i change the default skin for everything? where do i place it? If I download a new Theme... how do i make it default? by adding it to root or administrator?

---

### Post by Intrelude on 2008-05-23
> **Lapp-Same said:**
> Hi

If I install LTSP with alternate CD would i get the server in a desktop enviroment or like the server edition using commands in a terminal?

I'm new to Ubuntu as well and have been trying to get this to work for the last 3 days between classes.  I am trying to set up an Ubuntu-based LTSP environment.  I tried to use the Alternate Install CD but during the install, I kept getting errors during the base install.  I got the regular 8.04 server to install, but when it boots up, all I get is text-based environment.  I had to then install using:

sudo aptitude install ubuntu-desktop

To get the graphical interface.  I'm still trying to get the server to act right.  The synaptic package manager seems to hang a lot of times and then when I shutdown I have to hold down the power button.

---

### Post by Lapp-Same on 2008-07-06
> **Intrelude said:**
> I'm new to Ubuntu as well and have been trying to get this to work for the last 3 days between classes.  I am trying to set up an Ubuntu-based LTSP environment.  I tried to use the Alternate Install CD but during the install, I kept getting errors during the base install.  I got the regular 8.04 server to install, but when it boots up, all I get is text-based environment.  I had to then install using:

sudo aptitude install ubuntu-desktop

To get the graphical interface.  I'm still trying to get the server to act right.  The synaptic package manager seems to hang a lot of times and then when I shutdown I have to hold down the power button.

If allready hangs with just one desktop user, how the hell are you gone expect its gone work with heavy-desktop users...?

---

### Post by cariboo on 2008-07-06
For you guys that want to set up LTSP go here for documentation:

[http://wiki.ltsp.org/twiki/bin/view/Ltsp/Documentation](http://wiki.ltsp.org/twiki/bin/view/Ltsp/Documentation)

I set this up a couple of years ago just for fun, the instructions are well written and a gui just gets in the way as most of the scripts have to be enterd in a terminal.

Once you do get it running either get rid of the gui or set it up to manually start, otherwise it's just a waste om memory and cpu cycles.

Jim

---

