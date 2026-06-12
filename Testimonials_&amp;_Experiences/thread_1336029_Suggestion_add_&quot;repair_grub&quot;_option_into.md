---
title: "Suggestion: add &quot;repair grub&quot; option into Live CD menu"
date: 2009-11-24
forum: Testimonials &amp; Experiences
---

### Post by veko on 2009-11-24
Here's a humble suggestion: add "repair grub" option into Live CD menu. 

I know this is not exactly the developers forum, but I hope some comments would pass to them too.


My story: I recently bought a new laptop with Windows Vista. I naturally ordered a free update to Windows 7, and while waiting it, installed Ubuntu 9.10 (I prefer Linux anyway, but wanted to see whether 7 is as good as they claim). The upgrade rewrote the MBR and erased grub, which was expected of course. I had Live CD and instructions ready to reinstall grub (such as in [How-to geek]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out")). But I soon realized that these didn't work! I was dumbfounded for a moment before I realized that grub2 which Ubuntu 9.10 uses, is apparently set up differently.

I then googled for further instructions and found several helpful links, such as [RecoveringUbuntuAfterInstallingWindow ]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"). (I added the link here to guide others as well).

All this took about one hour, before I finally got grub repaired and my computer working again. Ok, I admit, I was slow, double checking things and spending some time reading grub2 manual. But, as a result my computer works as expected.



My point is: although I'm new to Ubuntu, I have some 10 years of experience in various Linuxes. I knew what to do and what information I should look for. My search was not helped the fact that most of the instructions were for grub, not grub2, which would easily have confused more unexperienced users.

If this had happened to some newcomer, I'm pretty sure that we'd have witnessed the last 2 seconds he'd ever use Ubuntu or any other Linux again. These are the kind of things that keep Linux not being accepted suitable for the general public.

Ease of use is the key, so as I said above, I suggest adding "repair grub" option into Live CD menu. Come to think of it, a general "repair computer" with suitable options would be handy too.

---

### Post by Onesimus on 2009-11-24
Why not submit this idea at Brainstorm ([http://brainstorm.ubuntu.com]("http://brainstorm.ubuntu.com"))  ?

---

### Post by armandh on 2009-11-24
I have often wondered why such a useful tool was not there right along with the mem test, 
or at least next to the partition editor in the live cd [since it exists in the install anyway]

I suppose it is because the terminal based command is so familiar to the cognoscenti. 
noob that I am that is no help.

---

### Post by julianb on 2009-11-24
a "repair grub" tool would be great, and like veko says, even better if the tool were designed to be capable of re-installing other software too.

on my machine, i accidentally deleted bash and had to figure out how to reinstall it from apt. since the only CD i had was a minimal (netinstall) type CD the solution required setting the system to boot dash instead of bash and then reinstalling bash while in the dash shell.

---

### Post by HeadHunter00 on 2009-11-24
That would be amazing.

---

### Post by veko on 2009-11-25
> **Onesimus said:**
> Why not submit this idea at Brainstorm ([http://brainstorm.ubuntu.com](http://brainstorm.ubuntu.com))  ?

Blimey, it seems to be there already:

[I][Restoring the bootloader by Ubuntu installation CD]("http://brainstorm.ubuntu.com/idea/1242/")
Written by vinlos the 29 Feb 08 at 10:46.  Global category: Installation.                New
[/I]           
Strangest thing, though, this was first proposed almost two years ago, it's one of the top 10 most popular ideas ever, and it's not implemented yet.

Thanks for pointing to Brainstorm, Onesimus.

---

