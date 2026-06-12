---
title: "[IDEA] Auto removal of old kernels"
date: 2007-10-19
forum: Ubuntu Brainstorm
---

### Post by Archmage on 2007-10-19
It is kinda weird to me that after a while the grub fills up with old kernels and you have to hunt for them in synaptic, maybe it would be a good idea to delete the automagically  or at least all but one older.

Taken from here, but I also like the Idea:

[http://ubuntuforums.org/showthread.php?t=421664](http://ubuntuforums.org/showthread.php?t=421664)

---

### Post by tubasoldier on 2007-10-19
I agree with this. however, I also think that the original kernel should be kept in case there are booting issues later on. That way everyone knows what kernel they need to tell grub to boot. No guessing on what the last one was.
Of course it would not have to actually show up in grub, it just needs to be available in case you need to tell grub to boot a different kernel.

---

### Post by carac on 2007-10-19
> **Archmage said:**
> It is kinda weird to me that after a while the grub fills up with old kernels and you have to hunt for them in synaptic, maybe it would be a good idea to delete the automagically  or at least all but one older.

Taken from here, but I also like the Idea:

[http://ubuntuforums.org/showthread.php?t=421664](http://ubuntuforums.org/showthread.php?t=421664)



A better alternative might be a friendly mini-UI-applet in the System/Administration menu that should also handle GRUB !!!

---

### Post by insane_alien on 2007-10-19
it should keep at least 1 known working kernel. nothing worse than trying to boot into a borked kernel(it's rare on ubuntu updates but it has happened.

---

### Post by Zdravko on 2007-10-19
> **Archmage said:**
> It is kinda weird to me that after a while the grub fills up with old kernels and you have to hunt for them in synaptic, maybe it would be a good idea to delete the automagically  or at least all but one older.

Taken from here, but I also like the Idea:

[http://ubuntuforums.org/showthread.php?t=421664](http://ubuntuforums.org/showthread.php?t=421664)

Absolutely great proposal! I want only 1 (one) kernel installed. The older ones must be deleted!

---

### Post by FrancoNero on 2007-10-19
get rid off the way how grub looks like, in the first place. how about two fancy looking hi-res logos, one windows, one linux, and below, in small print, options for safe boot and memtest. i think the times where stuff before you enter the OS looks like Ms Dos should be finally be a thing of the past

---

### Post by Zdravko on 2007-10-19
Yes. I would love it in a more elegant way.

---

### Post by zsouthboy on 2007-10-19
Meh.

It's just an entry in Grub.

It's not bothering anyone, and the kernel itself takes up, what, 10 mb?

---

### Post by Twintop on 2007-10-19
> **zsouthboy said:**
> Meh.

It's just an entry in Grub.

It's not bothering anyone, and the kernel itself takes up, what, 10 mb?

If people have small /boot partitions (100-200MB), they might only be able to old 3-6 kernels before they run out of space. If a user installs from the release CD at the beginning and gets every kernel update through the next Ubuntu version release, they'll have that many or more. When apt tries to install a new kernel and gives them an out of space error, new users just know they're out of space, not exactly why they are out of space or that they need to remove by hand the old kernels.

> **carac said:**
> A better alternative might be a friendly mini-UI-applet in the System/Administration menu that should also handle GRUB !!!

What about giving a sort of expiration date on old kernels? I.E.: a new kernel, 2.6.22-14, is installed. The previous kernel, 2.6.22-13, remains and on a successful boot to desktop with the new kernel, the old kernel's expiration date is set to XX days. Once XX days are up, the system prompts the user saying something to the effect of, "Would you like to clean up old kernels? If everything is working in your current kernel, this is a safe option; however, if some things still do not work it is advised that you should not remove old kernels." Additionally, if a user logs in to the system with an old kernel, the expiration date for that kernel is reset to the default, since it is obvious that they need to or want to use it.

---

### Post by Zdravko on 2007-10-19
> **zsouthboy said:**
> Meh.

It's just an entry in Grub.

It's not bothering anyone, and the kernel itself takes up, what, 10 mb?
Having 10 entries looks terrible. A kernel takes more than 25 MB sometimes.

---

### Post by FredB on 2007-10-19
> **insane_alien said:**
> it should keep at least 1 known working kernel. nothing worse than trying to boot into a borked kernel(it's rare on ubuntu updates but it has happened.

I completely agree. Keeping at least one or two kernels by security is a great idea.

---

### Post by Zdravko on 2007-10-19
Yes. One more kernel is okay. But no more!

---

### Post by kevdog on 2007-10-21
What if you add custom kernel's later on?? Is the updater method actually going to detect kernels that are newer than the one it is using??

Kernel sizes can vary widely depending on how you compile it.  Most modules are compiled dynamically, but you can compile them statically which increases the size of the kernel.

It would be a great idea to keep one old kernel (as others have mentioned) however if custom kernels are added, then there could be more than 2 in the /boot partition

---

### Post by Zdravko on 2007-10-21
What do you mean with a custom kernel?

---

### Post by kevdog on 2007-10-21
Compile/configure a vanilla kernel.  I did this in Feisty (only b/c I was bored). Cant say that I noticed anything different, however the kernel I compiled at the time was newer than gutsy's kernel.  Also helped me run the svn version of conky.

Im only trying to mention a potential problem.  A lot of stuff in Ubuntu's repository is old software, and I end up installing a lot of things from source. I agree with your idea of limiting kernels, however just want to expose something that shouldnt be overlooked if this idea is going to be implemented.

Master Kernel thread is a good reference:
[http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel](http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel)

---

### Post by Zdravko on 2007-10-21
Hmm. I still don't understand what is wrong with the supplied kernel.

---

### Post by smartboyathome on 2007-10-21
> **Zdravko said:**
> Hmm. I still don't understand what is wrong with the supplied kernel.

For some, there are bugs with the kernel which make things just plain not work. I am going to be compiling my own kernel on another install of Gutsy just to test Gobohide and see how well it works.

---

### Post by Lozz on 2007-10-21
Personally I think the "howmany=" line in /boot/grub/menu.lst should be set to one by default. However older kernels should be kept available, so that they are available to boot should the need arise. For instance if a kernel upgrade went wrong.

---

### Post by glotz on 2007-10-22
Good idea. I have one older kernel myself in case there should be problems with the new one. (It should also be taken into consideration in the implementation though that there are peeps who need multiple kernels...)

---

### Post by Xbehave on 2007-10-22
> **Lozz said:**
> Personally I think the "howmany=" line in /boot/grub/menu.lst should be set to one by default. However older kernels should be kept available, so that they are available to boot should the need arise. For instance if a kernel upgrade went wrong.

agreed, also in my gusty install old kernels are listed as removable so i don't really have to track them down atall

---

### Post by amano on 2007-10-23
Maybe the default behaviour should be that just the current and a backup kernel are kept and the older ones automatically uninstalled.

But you should be able to turn this feature off, eg. for those with custom kernels.

---

### Post by FlyingIsFun1217 on 2007-10-23
I think it would be awesome to have an option to trim the Grub entries to the other OS', one for Ubuntu (which would be the latest kernel installed).

This and order support (keeping them in the specified boot order) would be a godsend!

FlyingIsFun1217

---

### Post by veratyr on 2007-10-24
I'm all for a more elegant visual display of grub and at least a better way of cleaning up unused kernels. Something along the lines of "option booting" in OS X for grub would be a nice touch.

---

### Post by amlucent23 on 2007-10-24
> **carac said:**
> A better alternative might be a friendly mini-UI-applet in the System/Administration menu that should also handle GRUB !!!

There is already one in the repos.. its called startup manager. it does everything that everyone here is asking for.:lolflag: All that would need to be done is have it installed and configured by default. I know its always one of the first apps I install on every ubuntu box.

---

### Post by Archmage on 2008-06-19
Is there any progress about the removing of old kernels? I still have all my Gusty Kernels in Hardy.

---

### Post by rockin_goliath on 2008-06-19
The average user isn't setting up special boot partitions or giving any thought to how many kernels they have. With things like these, they care about hard drive space. It would make more sense for the OS to not use disk space superfluously, but having one extra kernel around is a good security move. 

My Idea:

Create that "System Cleanup Utility" that has been proposed a couple of times already, and have an option on it to remove old kernels. It can keep one extra in case boot problems come up. It could also clean the apt cache, orphaned packages, tmp files, thunbnails, etc.

This doesn't stop anyone from setting up special partitions or keeping as many kernels as they want, it just makes it easier for average users to free up space.

---

### Post by 23meg on 2008-06-19
Relevant blueprint targeted for Intrepid: 

[https://blueprints.launchpad.net/ubuntu/+spec/cleanup-cruft](https://blueprints.launchpad.net/ubuntu/+spec/cleanup-cruft)

---

### Post by philinux on 2008-06-19
> **amlucent23 said:**
> There is already one in the repos.. its called startup manager. it does everything that everyone here is asking for.:lolflag: All that would need to be done is have it installed and configured by default. I know its always one of the first apps I install on every ubuntu box.

I use SUM to keep number to three, Recent Hardy updates have broken all sorts. Check the ABF for all the threads. Good job we have older kernels to fall back on.

---

### Post by soccerboy on 2008-06-19
already approved for inclusion in II.
[https://blueprints.launchpad.net/ubuntu/+spec/cleanup-cruft](https://blueprints.launchpad.net/ubuntu/+spec/cleanup-cruft)

---

### Post by Gina on 2008-06-21
Looks good :)

---

### Post by FlyingIsFun1217 on 2008-06-22
> **23meg said:**
> Relevant blueprint targeted for Intrepid: 

[https://blueprints.launchpad.net/ubuntu/+spec/cleanup-cruft](https://blueprints.launchpad.net/ubuntu/+spec/cleanup-cruft)

Beautiful. Wish I knew more about the system so that I could help out...

FlyingIsFun1217

---

