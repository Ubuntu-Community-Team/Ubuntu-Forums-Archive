---
title: "trying to install new driver, not sure if i should"
date: 2010-05-11
forum: Ubuntu Studio
---

### Post by mr.thraz on 2010-05-11
i have a [prodikeys pc-midi]("http://www.prodikeys.com/") 

after abandoning windows for Ubuntu my prodikeys has been solely a qwerty keyboard. 

i just found a linux [driver]("https://sourceforge.net/projects/pc-midi-linux/") for it.

but his installation instructions call for a kernel patch.

i was going to try and do it myself,

but after going to [this page]("https://help.ubuntu.com/community/Kernel/Compile") i thought that might not be a good idea.

it states:

> Reasons for NOT compiling a custom kernel
_***You merely need to compile a special driver. For this, you only need to install the linux-headers packages.***_
You have no idea what you are doing, and if you break something, you'll need help fixing it. Depending on what you do wrong, you might end up having to reinstall your system from scratch.
You got to this page by mistake, and checked it out because it looked interesting, but you don't really want to learn a lot about kernels.


i was wondering how i would go about using the headers to install this driver?

---

### Post by mr.thraz on 2010-05-12
notta one reply?

---

### Post by sgx on 2010-05-12
> **mr.thraz said:**
> notta one reply?
Google can point you to tutorials on compiling, but in this case,
you should get a new keyboard that is known to work. Keyboards that work
on a Mac should work in linux. No drivers needed. When you find something of interest, google it with its name in quotes, and words like linux, problem, fails, and won't etc this line:

"axiom 61" linux problem

gives you tons of info on a popular midi keyboard

Cheers

---

### Post by mr.thraz on 2010-05-12
i have a board thats known to work, i have tons of equipment that work.

pics of my [mixxx rig]("http://picasaweb.google.com/mrthraz/DAWLove?feat=directlink#5432098240655754514") and my [Ubuntu-studio daw]("http://picasaweb.google.com/lh/photo/-1ctF5fnzKPS-iaZPHpQvw?feat=directlink").

the reason i need the prodikeys is i'm producing a hip-hop album using all Open Source Software and hardware costing no more than $100 a piece.

being that you can buy a prodykeys for 30 to 60 bucks moves a huge stumbling block from my project.

i also know how to read and have looked up many methods of compiling the kernel i would need after the patch.

thats not what i asked!


i saw, linked to and quoted a page on this site that said "do not compile a kernel for new drivers, use the header files."

thats all it said.

what does that mean?

thats my question.

---

### Post by sgx on 2010-05-12
I didn't mention 'kernel'.
I did mention google, not to be insulting, but because others
have failed to use the prodikeys in linux, and I don't want you,
or anyone to waste their time. An m-audio Keyrig fits your budget,
and is worth a look. The bundled software has some excellent vintage keys, and a nice GM module, and clever layering interface.

The headers and a package called 'build-essentials' or similar, can be installed with synaptic package manager, and as long as you have a separate /home partition, its trivial to reinstall linux, in case something odd occurs when compiling something. 
For hiphop, I think the calf-plugins, and rakarrack, used to fx the zynaddsubfx and phasex synths would be a powerful combination.

Is the budget part of a university project or magazine article?

---

### Post by mr.thraz on 2010-05-12
sgx,

thanks for replying.

sorry i was getting frustrated.

i finally bit the bullet and patched a kernel.

the prodikeys now appears in jack's alsa midi connections.

I'm now compiling a kernel with rt and pae that should fit my needs nicely.

i really would have hated to have to go out and bought another piece of equipment but the keyrig would have been it if this hadn't worked.



the budget is there because this is my own "bridge the digital divide" project.

I'm blogging the creation of my album and showing step by step the production methods using Ubuntustudio in an attempt to get ghetto kids (like i was) into cs as well as introduces them to foss community.

now with the prodikeys working my last stumbling block is getting open shot to work. 


thanks for taking the time and being so patient.

---

### Post by sgx on 2010-05-13
Thats a great project! Kids need something larger than life to get
involved in, and with music, the sky is the limit. It kept me off
the streets then, and still does. :)

Pettinhouse has some free soundfont drumkits to use in qsynth,
but I play the beats I like into audacity at various velocities,
and use the samples to make hydrogen kits. Theres quite a variety
to add the element of the unknown to traditional percussion. These are
the ones with soundfonts, the others are Kontackt/Battery format.

[http://www.pettinhouse.com/html/download.html](http://www.pettinhouse.com/html/download.html)

Air-ambient
Rnb-soul
Trance
Indastria
House
Scratch
Spit
Modem
Casio SK1
C64
The pro-midi patterns are also very well done.

There is a kit-making post in the last hydrogen topic, several days back.

Cheers

---

