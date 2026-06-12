---
title: "Virtualbox Ubuntu host error"
date: 2024-11-16
forum: Virtualisation
---

### Post by joepesci2 on 2024-11-16
Hello everyone.
I have installed Virtual Box with
sudo apt install virtualbox

When i create a virtual machine, the first time it starts correctly, i can use it without problems.

But when i turn off the virtual machine and turn the virtual machine back on, it gives me an error and it cannot start.

First i get an error of insufficient memory, although i have plenty of ram.
It also gives an error of: Failed to load R0 module 0x80004005.

I dont quite understand why this error could be, i have been looking for something similar but i havent found anything.

Could it be because the virtualbox-ext-pack is not installed?
In principle it isnt necessary for the correct functioning of Vbox, but i dont know if its necessary to install it in Ubuntu.

Thank you very much.

---

### Post by TheFu on 2024-11-19
Usually, it is recommended that you use Oracle's version of virtualbox, not the one in the Ubuntu Repos.  [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)  It isn't a 1-step process until after you setup Oracle's vbox repo on your system.  Things just work better with that version.  I'd post the instructions, but since you didn't say which version of Ubuntu and the instructions for each release are a little different .... 

Googled the error you posted and [https://forums.virtualbox.org/viewtopic.php?t=104378](https://forums.virtualbox.org/viewtopic.php?t=104378) was the best result. Says the install isn't good.

---

### Post by joepesci2 on 2024-11-20
> **TheFu said:**
> Usually, it is recommended that you use Oracle's version of virtualbox, not the one in the Ubuntu Repos.  [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)  It isn't a 1-step process until after you setup Oracle's vbox repo on your system.  Things just work better with that version.  I'd post the instructions, but since you didn't say which version of Ubuntu and the instructions for each release are a little different .... 

Googled the error you posted and [https://forums.virtualbox.org/viewtopic.php?t=104378](https://forums.virtualbox.org/viewtopic.php?t=104378) was the best result. Says the install isn't good.


Hi TheFu, how are you?
This is a bit discouraging for me, because i thought i knew it was better to install everything from official Ubuntu repositories and avoid third-party repositories and .deb packages.

But now i see that for many things you have to add other repositories, download .deb packages from other websites...
I see a lot of disorganization in all this, dont judge me badly, its just my frustration as a new user.

If it helps,  was trying Ubuntu 24.10 before, but right now im trying Kubuntu 24.10

Maybe you can help me a bit more.

Thank you very much for your help and your time.

---

### Post by TheFu on 2024-11-20
There are a few exceptions to every rule.
If you are new to Ubuntu, running 24.10 isn't a good idea. Stick with LTS releases.  By running 24.10, you've signed up to update to a new release every 6 months.  That's a bunch of work.  Also, large, complex, projects tend to skip non-LTS release updates.  The 6-month changes are just too hard for large corporations to keep up with.

BTW, whenever posting for help, best to be clear in the first post which release you are running.  **inxi -bz** will tell you, and us, that information.

---

### Post by joepesci2 on 2024-11-20
> **TheFu said:**
> There are a few exceptions to every rule.
If you are new to Ubuntu, running 24.10 isn't a good idea. Stick with LTS releases.  By running 24.10, you've signed up to update to a new release every 6 months.  That's a bunch of work.  Also, large, complex, projects tend to skip non-LTS release updates.  The 6-month changes are just too hard for large corporations to keep up with.

BTW, whenever posting for help, best to be clear in the first post which release you are running.  **inxi -bz** will tell you, and us, that information.

Hi TheFu.
Thank you very much for your advice, as im still in the testing phase and i dont care much about reinstall, i will continue to try Kubuntu 24.10 a bit more.
In future posts i will directly post the version im using.

For the correct functioning of Virtual Box, should i follow the steps in the link you provided?
Or are there any specific steps?

Thank you very much for your help and your time.

---

### Post by TheFu on 2024-11-20
I stopped using virtualbox over a decade ago. It didn't fit my needs and I'm not a fan of the Oracle license agreement.  But if you are happy with it, it is one of the more capable AND more popular choices.

In short, I only know that setting up the Oracle PPA and using that version of VirtualBox seems to make for a much more stable and happier vbox install.  Remember that using a PPA was also in the suggested order. It is easy to oversimplify suggestions by others and there are trade-offs in every choice.

Following the instructions from the project team behind the software seems like a smart thing to me.

---

### Post by joepesci2 on 2024-11-20
> **TheFu said:**
> I stopped using virtualbox over a decade ago. It didn't fit my needs and I'm not a fan of the Oracle license agreement.  But if you are happy with it, it is one of the more capable AND more popular choices.

In short, I only know that setting up the Oracle PPA and using that version of VirtualBox seems to make for a much more stable and happier vbox install.  Remember that using a PPA was also in the suggested order. It is easy to oversimplify suggestions by others and there are trade-offs in every choice.

Following the instructions from the project team behind the software seems like a smart thing to me.

I will do so.
Taking advantage of the post, can you tell me why you did not like Oracle license agreement?

Thanks for your help.

---

### Post by TheFu on 2024-11-20
> **joepesci2 said:**
> I will do so.
Taking advantage of the post, can you tell me why you did not like Oracle license agreement?

Thanks for your help.

Your should read them and understand them yourself.  Then decide if the terms are something you can agree to honor or not.  Everyone will have different levels of 1-sided legal agreements that they will accept.  Only you can decide.

---

