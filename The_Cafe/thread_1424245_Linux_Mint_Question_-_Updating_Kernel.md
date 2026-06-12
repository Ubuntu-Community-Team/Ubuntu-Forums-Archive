---
title: "Linux Mint Question - Updating Kernel?"
date: 2010-03-07
forum: The Cafe
---

### Post by Roasted on 2010-03-07
My buddy is here tinkering with Linux Mint 8. He has a Broadcom 4312 wireless card, and in my laptop I have a Broadcom 4322 wireless card. Both use the Broadcom STA driver.

With Ubuntu 9.10, I noticed that the default kernel with the Broadcom STA driver is VERY problematic, stuff freezes, etc. The fix was simply to install Ubuntu, update to the newest kernel with a wired connection, THEN install the STA driver and wireless works great.

Well, this is happening with him and Mint 8 as well. But the thing is, the update manager doesn't bring down the newest kernel in Mint. I have to search for it in synaptic. Is there a reason for this?

Also - If he uses the default kernel and installs the Broadcom STA driver, it fails as I mentioned above. But if he updates to the newest kernel, THEN installs the STA driver, it also fails. It must be done in a specific order. Install - Update Kernel - Install STA. If you try installing the STA driver prior, it backfires bigtime and I have NO idea how to fix it other than to reinstall. Since this is a fresh install and installing Ubuntu/Mint takes 10 minutes and 30 seconds (timed it :P) we opted for that.

Two questions - Why can't Mint update kernels in update manager? Secondly, why do we have problems installing the Broadcom STA driver when we tried it once before? Like I said, updating, THEN installing STA is fine. But if we try to install STA, then update, then install STA again (since the first time fails with the default kernel), we get a system error.

Any ideas?

---

### Post by ajgreeny on 2010-03-07
The default in mint is to install updates only to apps that their developers put in grades 1 to 3 of the safety grading they have made up for themselves.  You will see in the mint update manager that only items with grade 1 to 3 appear, but it is very easy to change that to all 5 grades, by going to the update manager preferences and selecting all 5 of the options shown there.  The new kernel should then appear as it does in ubuntu.

Their reasoning for this is that new kernels can sometimes cause problems for users who have installed proprietary drivers etc etc, and therefore those updates are not available by default.

---

### Post by Roasted on 2010-03-07
> **ajgreeny said:**
> 


Their reasoning for this is that new kernels can sometimes cause problems for users who have installed proprietary drivers etc etc, and therefore those updates are not available by default.

I don't understand why they would remove that functionality from update manager. If a new kernel gives you problems, just select the older one in the grub menu. That way you can obtain new kernels easily, and easily switch to old ones if the new ones are problematic - whereas their current method seems to be a little more involved with getting new kernels in in the first place.

---

### Post by Post Monkeh on 2010-03-07
> **Roasted said:**
> I don't understand why they would remove that functionality from update manager. If a new kernel gives you problems, just select the older one in the grub menu. That way you can obtain new kernels easily, and easily switch to old ones if the new ones are problematic - whereas their current method seems to be a little more involved with getting new kernels in in the first place.

i've had kernel updates stop me seeing anything when  i reboot before because my ati driver was removed.

i was able to sort it by manually reconfiguring xotg, then re-installing my ati driver.

booting to a blank screen after an update is not impressive,

---

### Post by Roasted on 2010-03-08
I don't see how a failed kernel would prevent you from selecting options at the grub screen. After all, the kernel is at the OS level... which is after the boot level (grub screen)...

---

### Post by Post Monkeh on 2010-03-08
> **Roasted said:**
> I don't see how a failed kernel would prevent you from selecting options at the grub screen. After all, the kernel is at the OS level... which is after the boot level (grub screen)...

once ubuntu booted my resolutions were stuffed up - out of range for my monitor and so the screen was blank.

not too hard to fix if you know how, but not many people know how.

---

### Post by Roasted on 2010-03-08
> **Post Monkeh said:**
> once ubuntu booted my resolutions were stuffed up - out of range for my monitor and so the screen was blank.

not too hard to fix if you know how, but not many people know how.

Even still, I think it's a lesser tradeoff to have it harder to install a new kernel rather than making it easier to install a new kernel/having the ability to select a different one at the boot screen if they run into issues...

---

### Post by ajgreeny on 2010-03-08
As I said you can easily change the Mint system back to "normal" in the preferences of update-manager.

Linux Mint is most definitely a distro for the new user, who just expects absolutely everything to work with no glitches.  A new kernel that drops you to a command line would be OK for you or me, perhaps, but for most users who just switch on and probably don't even notice the grub menu, it would be a show-stopper and lead to many complaints to Mint about things going wrong.

If you don't like the default way of doing things change it, that's what is so good about linux distros; very little can not be changed and you can make most things do what you want.

---

### Post by Post Monkeh on 2010-03-08
> **Roasted said:**
> Even still, I think it's a lesser tradeoff to have it harder to install a new kernel rather than making it easier to install a new kernel/having the ability to select a different one at the boot screen if they run into issues...

i think you misunderstand. 
when the new kernel was installed, it totally disabled my ati driver, so even selecting a previous kernel didn't help - i had to reconfigure my driver.

i don't use mint, but if they're going for newbie friendly then i think they've got this one right. if you know enough about linux to know about updating the kernel, then i'd say generally speaking you'd know how to find out how to update it, which would also mean you'd be competent enough to deal with any issues that arise from doing so.

new users on the other hand may just think "oooh, updates, yay!!!" then scratch their head if it gives them problems.  mint is geared to be friendly to the new user, and some sacrifices have to be made to do this - it's not like they STOP you upgrading the kernel, they just don't force you (which, while not technically true, would be the case if they automatically updated the kernel. most users just install updates without thinking that it may lead to problems)

---

### Post by Roasted on 2010-03-08
I understand now. Thanks for filling in the blanks. It does seem like Mint has a little bit of user friendliness edge on Ubuntu, which may be why I hear Mint more with new Linux users moreso than Ubuntu, however, I still hear Ubuntu quite a lot to begin with.

I have to wonder though - what is it about Mint that relieves the potential "threat" of a grub update disabling a video driver, like in your case Post Monkeh? Or is the argument simply this - the kernel in Mint and Ubuntu would do the same thing (therefore if one crashed your ATI driver, the other would as well) - but the only "keep-safe" is the fact that kernels in mint don't auto come down through update manager.

Am I on the right path?



Side Question, though... and this is one of those curve ball questions that is serious yet sarcastic at the same time.

My buddy has a laptop. Dual boots Mint (project distro in school) and Ubuntu (preferred distro). Inside is a Broadcom 4312 chip.

In Ubuntu with newest kernel - install Broadcom STA driver, reboot, bam you have wireless.
In Mint with newest kernel - install Broadcom STA driver, uh oh... error... no wireless.

I guess for being user friendly, you take some/give some. In my case, I'll take Ubuntu... but it's still a bummer to see a distro so closely related to Ubuntu that somehow cannot utilize and even install the STA driver in a proper fashion. Any thoughts regarding this?

---

### Post by Post Monkeh on 2010-03-08
> **Roasted said:**
> I understand now. Thanks for filling in the blanks. It does seem like Mint has a little bit of user friendliness edge on Ubuntu, which may be why I hear Mint more with new Linux users moreso than Ubuntu, however, I still hear Ubuntu quite a lot to begin with.

I have to wonder though - what is it about Mint that relieves the potential "threat" of a grub update disabling a video driver, like in your case Post Monkeh? Or is the argument simply this - the kernel in Mint and Ubuntu would do the same thing (therefore if one crashed your ATI driver, the other would as well) - but the only "keep-safe" is the fact that kernels in mint don't auto come down through update manager.

Am I on the right path?



it's not that it crashed my ati driver.

installing a new kernel causes my ati driver (proprietary) to revert to the open source driver. this happens on all distros, not just ubuntu.

when that happens, because all my settings are for the proprietary driver, my screen resolutions get messed up and i can't see anything until i ctrl/alt/f1 into a terminal and fiddle around with my settings. new users won't know to do this.

for your wireless problem, i don't know. i tried mint on my desktop, but the wireless wasn't as good for me as it was in ubuntu, so i can relate to your story. i don't knw what causes it, in other distros i tried my wireless card woulnd't work at all, in ubuntu and some other ones it did work.

---

