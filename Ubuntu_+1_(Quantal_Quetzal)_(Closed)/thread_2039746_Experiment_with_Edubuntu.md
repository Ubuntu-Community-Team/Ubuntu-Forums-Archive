---
title: "Experiment with Edubuntu"
date: 2012-08-09
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-08-09
I have  an early install of Edubuntu (quantal) on a machine (2.2GHz/1GBSDRAM) which is  currently running 3.4.0-1-generic-pae.

 On this install Nautilus still shows the enduser in permissions (not me) and Disk Utility is like it was  before all the changes.

  The experiment I want to do is upgrade it to current but force or lock the versions of Nautilus and Disk Utility.

 Before I do this I am just wondering if anybody might have any input or pointers. It is, after all , a beta test!

Thanks in advance

---

### Post by balloons on 2012-08-09
Ventrical, likely you could make this work, although you may have to hand edit dependencies or do other crazy stuff :-) My guess is everything will go fine actually by just apt-pinning the old versions. Though it's kind of funny to not want the upgrade :-) I had to do the same thing earlier with a library I had installed. It was broken, but holding it didn't cause anything else to break. It did hold some other packages (which is where you may run into issues), but only like 2 or 3 in my case. I'm thinking most of gnome and gtk, etc, will still update for you.

---

### Post by ventrical on 2012-08-09
Hi guitara,

 Maximum breakage !! :) Oh joy !!  I tried to lock  those two versions, then force them. No go. After upgrading through synaptic everything went south from there!!

 However, as resillient as Ubuntu is and synaptic is , through a lot of work in the terminal, it amazingly healed itself and is now installing  other packages that were busted in the pipes.  I haven't had this much fun in a long time.

 I may try to follow-up on some of your suggestions a little later but it was just a riot trying to bring this  install back from a broken state.

  The one thing I have learned in the last couple of days is that the 'proposed' repository can really break a system to pieces, but, through apt and the other tools we have , it can most often be brought back to restored state! :)

  I have Edubuntu Precise working on one of my laptops.  It is a very stable install. I am not sure why I do not hear more of it.

edit : gnome-gtk etc.. were all ready to be pulled - gnome control center also ..

---

### Post by ventrical on 2012-08-09
Setting up grub-pc (1.99-22ubuntu1) ...
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-8-generic


and a bundle of new artwork also :)

---

### Post by ventrical on 2012-08-09
Here is Edubuntu City :)

---

### Post by ventrical on 2012-08-13
I took this experiment a step further. I decided to try something with the Lucid repositories. I added them (Lucid repos) to the sources list and then updated! It worked. Now when I went to check the Nautilus  in synaptic I had both the current for (quantal) and that for lucid.  I then installed gnome. I coughed up a but but installed some files which somehow enabled one of my dinosaur NVIDIA cards to produce exceptional compiz cube graphics ..etc.

 At this point I am going to uninstall ubuntu-desktop, the other gnome and cairo-dock which I installed also. It will not load ubuntu 3D because of low memory (390MB-SDRAM).

 There is one depends  that this whole process looks for .. a gtklib. I am not worry about borking this install but I have a theory that old gnome from Lucid can be made to run on the quantal kernels... I'll gt back on this.

 If you try this and synaptic stalls when you try to install gnome(Lucid) just click <details>. The reason why it hangs is that it wants you to choose between gdm and lighdm. Choose gdm >ok and it will install gnome.

 Lots of fun :)

---

### Post by ventrical on 2012-08-13
As expected I near most completely destroyed that install :) There is, of course, major problems with newer depends and my proceedure caused major breakage but I think it is rebuildable.. I just about had it working .. but could not get the nautilus icon to come up in (quantal)  from the (Lucid version) but in theory, it all worked out ok. 

hmmmmmmm ... lemme see here...<squint> :)

---

### Post by balloons on 2012-08-16
Playing around like this on a test box is a bunch of fun, and as ventrical mentioned, has the side benefit of teaching you some things :-) Glad you went ahead with things.. I enjoyed reading!

---

### Post by ventrical on 2012-08-20
Hey Guitara ! :)

Thanks for the comments.  I'm just getting back now. Like you and everyone esle here I have been up to my elbows in .. err .. stuff :) <the real life job> :)

Here , at my *virtual* work it has been like the *running of the bulls* ! As soon as you wrangle one bull, there is another behind you trying to run you into the pavement. Of course I say this in reference to bugs, breakage and the general destruction of a clean install :)

 One small thing I noticed (as being the novice Ubuntu user as I am:) is that if I destroy a perfectly good working desktop I can always mount *THAT* filesystem and import all my important files to a stable install on the same hdd!! ie; like all my ISO files for zsyncing!

 One really neat thing that I noticed while I was experimenting with Edubuntu is that I sort of got distracted with Gnome Shell and Gnome Classic and the Lucid repositories and Lubuntu install. What came up was this sort of hybrid desktop , a cross between Gnome Shell and Gnome Classic and even compiz cube was working !! Only problem is  that I inadvertently destoyed that  install so I can't  authenitcate it and had not documented the anomolous behaviour. 

  I plan to keep on  trying to build some sort of reasonable facsimile of a system recovery tool and experimenting with Edubuntu on a newer machine with an Intell 516 Pentium4/64bit.

Thanks for your interest :)

regards, 

ventrical

---

