---
title: "unintelligent multimedia import required"
date: 2010-06-17
forum: The Cafe
---

### Post by spezticle on 2010-06-17
fspot and picassa or all these other things....
they're trying to make it more complicated than needed.

i just need something that, when i stick my memory card in, it MOVES not COPIES (fspot doesn't give choice of move), from memory card to ~/Pictures

all these other photo management programs want to jack up the file names, renaming them this or that, or put them into folders by date automatically NOT considering that the time on the camera was wrong when the pictures were taken and there's not really any choice to modify how these programs work to do their thing.

so
is there a script i could run or a program that would be smart enough to know it's a camera or memory card with pictures and put them in ~/Pictures but quit with the auto organize crap, i'll do that myself.

---

### Post by sydbat on 2010-06-17
> **spezticle said:**
> fspot and picassa or all these other things....
they're trying to make it more complicated than needed.

i just need something that, when i stick my memory card in, it MOVES not COPIES (fspot doesn't give choice of move), from memory card to ~/Pictures

all these other photo management programs want to jack up the file names, renaming them this or that, or put them into folders by date automatically NOT considering that the time on the camera was wrong when the pictures were taken and there's not really any choice to modify how these programs work to do their thing.

so
is there a script i could run or a program that would be smart enough to know it's a camera or memory card with pictures and put them in ~/Pictures but quit with the auto organize crap, i'll do that myself.Just mount your card reader and do not open one of those programs. Then manually move your photos into whatever folder(s) you want. Simple!

---

### Post by spezticle on 2010-06-17
yeah, i'm doing this for somebody else though... it's not my actual preference.
they want it so that when they stick the memory card in it will automatically move them from the card to HDD and then burn to CD.

she's used to the windows picture import.

it's the manual part that is trying to be avoided.
manually doing things confuses her

---

### Post by sydbat on 2010-06-17
> **spezticle said:**
> yeah, i'm doing this for somebody else though... it's not my actual preference.
they want it so that when they stick the memory card in it will automatically move them from the card to HDD and then burn to CD.

she's used to the windows picture import.

it's the manual part that is trying to be avoided.
manually doing things confuses herShe's blonde, right? ):P

I do not think there is anything that does this automatically (I did not even know Windows had this feature), and I suck at scripts, so if we keep this thread on the first page, someone might be able to help.

---

### Post by spezticle on 2010-06-17
haha
yes.
blonde.

this is extremely frustrating because they want the computer to work fast and not have problems like windows constantly has.
but
they want everything to work the way windows does.

so essentially what they want is for windows to not suck, not to use an OS that works well but requires you to think. *shrugs*
i'm not entirely sure how to give them what they want w/o using windows.
so far all of the things they want to use this computer for, i've ended up using a virtualbox with windows installed to do the tasks, which, essentially, i might as well wipe out ubuntu and just put windows back on here.
the other problem is that this is a dell dimension 3000 with an 80gb ide hdd 5400rpm and 512mb ram with a 333mhz bus but spending money to make the computer newer and faster isn't an option for them either. well, i mean, of course it's an option, but they dont want to do it.

---

### Post by alphaniner on 2010-06-17
For a script, I would use the last few lines of the 'dmesg' log (**dmesg | tail** or **tail /var/log/dmesg**) to figure out where the device was mounted, then do a cp -r /media/mountpoint/* ~/Pictures.  You'd have to manually run the script after inserting the device though.  Pretty sure it should work, though I'm equally sure there are better ways of going about it.

---

### Post by spezticle on 2010-06-17
Well, i've come up with a solution, but i'm not sure how well it will work in the long run.
But i want to know what people more experienced think before i spend the hours setting it up.

So, the idea is to install windows XP in a virtual machine. Did this already.

6 Different people have login accounts on this computer.
So i have either the option of using 6 different virtual hard disks, with 6 different installs of XP, OR I can use 1 virtual hard disk shared among the 6 users. The latter requires fast user switching in Ubuntu disabled because if user 1 is logged in and leaves the virtual machine running and user 2 tries to use it, i'm sure there will be errors seeing as user 1 is already using the shared virtual hard drive.

To eliminate confusion with these people, i created a share in the virtual box which points drive Z: to ubuntu home folder and then changed windows 'my documents' to drive Z: so that if they're in windows or ubuntu they have the same 'my documents'. (will this pose any security threats for ubuntu seeing as there's a path connecting windows and ubuntu?)

So, when they turn on the real computer, they're in Ubuntu. They'll use firefox for web browsing and whatever else.

But when they want to use the "i need windows for these applications"
like itunes, "The Print Shop", "Business cards premier", and all the other lame programs they want to use but have to because they don't want to learn how to use the alternatives available in ubuntu, i want to make a shortcut that starts up the VB xp install automatically in the 1 click way that wont confuse them.

they'll probably end up using the windows VB 90% of the time, probably even for web browsing as well, and ubuntu will sit in the background only running windows inside the virtual box.

Why go through all this when I could just install windows for them and leave it be? because they want to run linux.

At least when they jack it up with viruses i can ssh their ubuntu, replace the .vdi (hard drive file) for xp with a previous one that isn't jacked up and i can fix windows problems a lot more easily this way than actually having to use a windows only pc.

booting up linux, then starting the VM with windows has still been faster than just booting up their old setup with just windows.
and maybe eventually they'll realize that the only time their computer runs like crap is when they use the windows vbox.

---

### Post by kevdog161 on 2010-06-17
[http://www.damonlynch.net/rapid/index.html](http://www.damonlynch.net/rapid/index.html)

I just found this program like an hour ago via google.  Configure a few options and set it as the default image importing program.  I believe you can even set it to automatically import upon camera connect.

---

