---
title: "So i'm installing windows now..."
date: 2006-06-22
forum: The Cafe
---

### Post by GarethMB on 2006-06-22
I'm not giving up on K/Ubuntu. I'm just sick to death of wine not being able to run windows only programs well. I want to play some games and this is the only way other than Cedega i can do it. It's going to be pretty annoying to set windows up. I've got drivers to find, firewall to install, clamwin to install and then ton's of 'next' clicking to do. Worst of all though i'm going to have to change my sig.

If Ubuntu had native games i don't think i'd ever touch windows. I prefer all the GNU/linux programs to windows ones.

---

### Post by mips on 2006-06-22
would it not work if you installed windows in vmware ?

---

### Post by GarethMB on 2006-06-22
I'm sure it would, but that's bound to be more hassle than its worth.

---

### Post by zAo on 2006-06-22
Dude, but a gameconsole and remove Windows. (no, not a XBOX :))

---

### Post by Brunellus on 2006-06-22
[QUOTE=zAo]Dude, but a gameconsole and remove Windows. (no, not a XBOX :))[/QUOTE]
consoles don't do certain types of games that PCs do well--MMORPGs, FPS, turn-based strategy.

---

### Post by Jasper Houtman on 2006-06-22
What's wrong with an xbox? I love my Xbox, modded it (is very easy to to because it was build by microsoft :P ). 

It plays all my movies, music, playstation one games (and snes, nes megadrive, mame, etc).

I could even run [linux]("http://www.xbox-linux.org") on it!

---

### Post by Jasper Houtman on 2006-06-22
[QUOTE=Brunellus]consoles don't do certain types of games that PCs do well--MMORPGs, FPS, turn-based strategy.[/QUOTE]

Not true, helped my brother getting a keyboard and mouse working on his 360.
With those playing MMORPGs, FPS and strategy is the same way as you would on a pc.

---

### Post by Brunellus on 2006-06-22
[QUOTE=Jasper Houtman]Not true, helped my brother getting a keyboard and mouse working on his 360.
With those playing MMORPGs, FPS and strategy is the same way as you would on a pc.[/QUOTE]
the game-types are there, but the specific game *titles* are not.  

It's like saying to someone who likes Shakespeare's tragedies--"well, this theatre company also performs tragedies, but none by Shakespeare.  They only perform tragedies by Marlowe."

To which the theatregoer would respond "But I wanted SHAKESPEARE!"

To which his friend says "But they're all TRAGEDIES.  And Marlowe is a perfectly good tragedian!"

---

### Post by GarethMB on 2006-06-22
I have an xbox and i've owned a gamecube, and whilst i was satisfied with both some games just need a PC.

---

### Post by Kimm on 2006-06-22
Keep an eye on [this](http://www.alkyproject.com/) project

---

### Post by FISHERMAN on 2006-06-22
[QUOTE=zAo]no, not a XBOX[/QUOTE]
IMHO, the Xbox(the original one, not the new 360) is one the only decent things made by MS.

---

### Post by kassetra on 2006-06-22
[quote=GarethMB]I'm sure it would, but that's bound to be more hassle than its worth.[/quote]

You're the second person that I've seen think that.  The first person installed vmware through synaptic and saw it's not a hassle at all. 

Have you looked at it?

---

### Post by bruce89 on 2006-06-22
[QUOTE=kassetra]Have you looked at it?[/QUOTE]
What the heck is it anyway, I mean, what does it actually do?

---

### Post by mips on 2006-06-22
Allows you to create virtual machines within linux from where you can run other os's. It is not the same as emulation.

VMWare server would be a better option to install but I dunno if it is available in the repos, guides do exist.

[www.vmware.com](www.vmware.com)

---

### Post by DrSturgeon on 2006-06-22
You'd want vmware server... It's not in the repositories, but it's freaking easy to install.  Just download it, and run the install script.

But I'm pretty sure there's no 3d acceleration in vmware, so it won't work for games.

---

### Post by bruce89 on 2006-06-22
Is Xen supposed to be the same idea as VMWare, but free software?

---

### Post by mips on 2006-06-23
[QUOTE=bruce89]Is Xen supposed to be the same idea as VMWare, but free software?[/QUOTE]

Yes, Xen is GPL I think. VMWare player/server is free from a financial point of view but not GPL'd, proprietory/no source.

---

### Post by AndyCooll on 2006-06-23
And Xen will only work with Linux distros at the moment as far as I'm aware.

:cool:

---

### Post by fuscia on 2006-06-27
[quote="GarethMB's sig"]Using Ubuntu as a sole OS since 10/3/2006-Thats dd/mm/yyyy for all you Americans.
[/quote]

does that mean you'll be back?:confused:

---

### Post by bruce89 on 2006-06-27
It means since the 10th of March of this year.  Not sure what you mean by
[QUOTE=fuscia]does that mean you'll be back?:confused:[/QUOTE]

---

### Post by fuscia on 2006-06-27
[QUOTE=bruce89]It means since the 10th of March of this year.  Not sure what you mean by[/QUOTE]

ooooooooooooooooooooooooooh, i see now.

---

### Post by G Morgan on 2006-06-27
VMware is of no use for games since you don't get Hardware GFX Acceleration. Runs any Windows apps pretty well though. Personally I have an Ubuntu VM in my XP partitions and a XP VM in my Ubuntu Partition. This way I can use all my Windows apps in Ubuntu and if I'm playing games in XP and I suddenly decide to browse the web I can do so in an isolated environment.

Xen is similar to VMware in some ways but works via a different method. Xen runs beneath all your OSes, every single OS is virtualised even Dom0. VMware runs in a host OS. The VMware player available in the repos only allows you to play VMs not create them (there are legal ways around this on the web by editing the config file by hand). VMware Workstation is a paid for product but gives you the full ability to run several VM's at once and gives you a GUI interface for editing a VM. VMware Server is free but is a beta product AFAIK, it allows you to create VMs as well.

Another option is Qemu which is GPL but its only a worthwhile tool with the KQemu kernel module which is closed source but free. So it kind of defeats the point to a large extent.

---

