---
title: "Grub GUI similar to lilo but better."
date: 2007-10-25
forum: Ubuntu Brainstorm
---

### Post by suchawato on 2007-10-25
I use Super Grub Disc to switch between my Windows and GNU/Linux  partitions. This is because this method has proved to be the fastest.
If GRUB had a 16 or 8 bit simple GUI with an easy confuguration tool for setting up multiple partitions and harddrives with different OS', this would be greatly apprecieated.
Even just a menu.
multi-partition managing with Windows sucks.

---

### Post by adrian15 on 2007-10-25
You can do the same thing with a separated /boot partition where you use grub with the configfile or with the rootnoverify commans. You can see some examples in this [halt mailing list post]("https://listas.ensanjose.net/pipermail/halt/2007-February/000246.html").

---

### Post by suchawato on 2007-10-25
like I said though:
an** easy** configuration tool. No Art student is gonna want to have to figure out grub editing commands to easily boot to different partitions. 
We are right-brained people. (art students)

---

### Post by adrian15 on 2007-10-25
> **suchawato said:**
> like I said though:
an** easy** configuration tool. No Art student is gonna want to have to figure out grub editing commands to easily boot to different partitions. 
We are right-brained people. (art students)

I mean that if someone has to develop this tool the easiest way is using grub and either the chainload commands or either the configfile commands.

adrian15

---

### Post by meierfra on 2007-10-25
> like I said though:
an easy configuration tool. No Art student is gonna want to have to figure out grub editing commands to easily boot to different partitions.
We are right-brained people. (art students)


Post the output of 

```
sudo fdisk -l    (l is a Lower case L)
```

and 

```
cat /boot/grub/menu.lst   (l is a lower case L)
```

and we can tell you exactly would you need to do.

---

### Post by snickers295 on 2007-10-25
i find grub very easy to edit right now.
these GUIs aren't easy to get everything the way you want it and are a slowing down the system.

---

### Post by suchawato on 2007-10-27
One thing to keep in mind, is that about half the world are right-brained people.
Visual learners.
Text editing is not such a good option for these folks.
Remember item number "3" of the Ubuntu Philosophy:
"Every computer user should be given every opportunity to use software, even if they work under a disability."

---

### Post by meierfra on 2007-10-27
> One thing to keep in mind, is that about half the world are right-brained people.
Visual learners.
Text editing is not such a good option for these folks.
Remember item number "3" of the Ubuntu Philosophy:
"Every computer user should be given every opportunity to use software, even if they work under a disability." 

This paragraph you wrote required more  text editing than you will have to do to fix grub.

---

### Post by suchawato on 2007-10-27
> **meierfra said:**
> This paragraph you wrote required more  text editing than you will have to do to fix grub.
LOL. :)

---

### Post by suchawato on 2007-10-27
I understand the reservations people have with GUI's.
A GUI takes power away from the user, and instead gives them the option of pre-chosen commands.
However, GUI's are nessicary.
As Neil Stephenson put it in his essay In The Beginning Was The Command Line: "Most Linux users are Morloks" -Reffering to the analogy of Morloks and the Eloi of H.G. Wells: The Time Machine. Meaning that by Morloks, they are natural tinkerers and fidelers, who like to understand the intricate workings of things. Whereas the "Eloi" do not, and prefer things to "Just Work".
The problem is that in the World of Computer users, as well as in the world in general, Morloks are a minority.
And, a part of the stated purpose of the Ubuntu project is to create a sytem that "just works",
if a user *has* to text edit *anything* in order to do the basic functions they want it to do; then it isn't "just working" and is therefor, to the most of the users out there (not morloks), a headache.
There are plenty of other Gnu/Linux disto's out there that are plenty made with Morloks in mind. We do need at least Just ONE that "just works" if it is to be a viable alternative to Windows, which is the stated purpose of Ubuntu, Stated in [Bug # 1]("https://bugs.launchpad.net/ubuntu/+bug/1").

---

### Post by KeaponLaffin on 2007-10-27
Folks got a point.
When GRUB breaks, most often yer pretty much screwed. You can't even get to a command line to edit menu.lst or use the 'e' 'o' or whatever commands to edit the GRUB config. I gotta fix this problem this morning with an error 17(I think) where GRUB just hangs and doesn't even let me edit.

But for regular GRUB problems, it would be nice to have a friendlier GUI. Not one that necessarily 'limits the users options' but one with a nice list you can pick from..Including manual editing. Something like you can choose an 'fdisk -l' list then scroll down the list to add-delete-modify which partitions are bootable. Just use the spacebar,enter or whatever to 'flag' or 'unflag' partitions instead of manually editing. 

Just because Ubuntu is 'The Friendly Linux' doesn't make it the 'Idiot Linux' ;) Adding a GUI here and there for system functions doesn't remove any freedom or make manual editing options harder to find for those users who are more comfortable and confident with text editing the config files.

---

### Post by smartboyathome on 2007-10-27
> **KeaponLaffin said:**
> Folks got a point.
When GRUB breaks, most often yer pretty much screwed. You can't even get to a command line to edit menu.lst or use the 'e' 'o' or whatever commands to edit the GRUB config. I gotta fix this problem this morning with an error 17(I think) where GRUB just hangs and doesn't even let me edit.

But for regular GRUB problems, it would be nice to have a friendlier GUI. Not one that necessarily 'limits the users options' but one with a nice list you can pick from..Including manual editing. Something like you can choose an 'fdisk -l' list then scroll down the list to add-delete-modify which partitions are bootable. Just use the spacebar,enter or whatever to 'flag' or 'unflag' partitions instead of manually editing. 

Just because Ubuntu is 'The Friendly Linux' doesn't make it the 'Idiot Linux' ;) Adding a GUI here and there for system functions doesn't remove any freedom or make manual editing options harder to find for those users who are more comfortable and confident with text editing the config files.

If you can at least boot up to GRUB, it has a built in command line, so you can just switch over to another install (if available), and edit GRUB from there.

---

