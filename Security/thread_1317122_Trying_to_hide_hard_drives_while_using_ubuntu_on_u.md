---
title: "Trying to hide hard drives while using ubuntu on usb"
date: 2009-11-06
forum: Security
---

### Post by vamike999 on 2009-11-06
Hello,

I am new to ubuntu and really like it. I am using my ubuntu on a ubs stick and do not want to get virus on my windows laptop for work. Is there a way i can still vew ubuntu on my usb but make it so ubuntu can not view all other hard drives on the laptop so i do not mess something on on these hard drives since its used for work. Thanks much for your help

---

### Post by JugglinPhil on 2009-11-06
How about unmounting all found hdds right after starting up?

---

### Post by vamike999 on 2009-11-06
is there any link on how to do this? could i write a script to run that would maybe check to see what drives exists? like for example if put the usb in my work laptop or my dads laptop there could be different drives. Some way to detect then un mount them?

---

### Post by JugglinPhil on 2009-11-06
If you've got the option in gconf enabled all mounted drives will show up on the desktop, then you can just right click them and choose unmount. To find out if you have it enabled just type gconf-editor in a terminal, then go to apps, nautilus click on desktop and see on the right if 'volumes_visible' is checked.

---

### Post by vamike999 on 2009-11-06
it was checked i went in and un-checked it, then went back into examples to test and still was able to see my drives :-( I also tried re-booting did not help at all. after i re-booted it was checked again.

---

### Post by vamike999 on 2009-11-06
sorry made a mistake it did stay un-checked but i can still access my drives just by going into example then hitting on my drive of 113 gig. it opens right up

---

### Post by JugglinPhil on 2009-11-06
Sorry if I didn't make myself clear enough, but you should keep it checked. That way you can see your drives and unmount them from your dektop, which stops any access to them. Not showing the volumes on your desktop does not disable access to the drives themselves, they just don't show up on the desktop. Hope this is more clear now.

---

### Post by vamike999 on 2009-11-06
hmm ya but still gets me back to point a) i am trying to keep a virus from getting to my pc's hard drive right now i can see them and i can click on it and it opens right up. is there a way to make it so they are not seen at all?

---

### Post by vamike999 on 2009-11-06
also i saw this link kind of what i am trying to figure out 

[http://ubuntuforums.org/showthread.php?t=1221225&highlight=mount+hard+drives](http://ubuntuforums.org/showthread.php?t=1221225&highlight=mount+hard+drives)

but how does one use the "[B]cmos-disabled"? or can anyone explain what this is for a newbies 
[/B]

---

### Post by Agent ME on 2009-11-06
You're worried about a linux virus transferring over to the windows install?

There are already very few known linux viruses, which most people are virtually not at risk at all for, and I've never heard of a multiplatform virus actually made that could infect a different system install.

Not only is it silly to worry about it for that reason - but, if a virus has infected your linux install and is advanced enough to be able to spread between separate platforms, what makes you think it won't mount the system's hard drives despite your system settings and carry out the infection anyway?

There isn't a real need to worry about this, or at least not from this approach.

---

### Post by cariboo on 2009-11-07
I like to add a question, don't you have an av scanner installed on your Windows partition?

---

### Post by JugglinPhil on 2009-11-07
> **Agent ME said:**
> You're worried about a linux virus transferring over to the windows install?

There are already very few known linux viruses, which most people are virtually not at risk at all for, and I've never heard of a multiplatform virus actually made that could infect a different system install.

Not only is it silly to worry about it for that reason - but, if a virus has infected your linux install and is advanced enough to be able to spread between separate platforms, what makes you think it won't mount the system's hard drives despite your system settings and carry out the infection anyway?

There isn't a real need to worry about this, or at least not from this approach.
It can actually be rather dangerous, not for Linux but for Windows, as Viruses that can't harm Linux sometimes just wait until they get their chance, e.g. on a Windows hdd.
I don't think they can mount drives though, as their power over Linux itself is very limited/0.

---

### Post by JugglinPhil on 2009-11-07
> **vamike999 said:**
> also i saw this link kind of what i am trying to figure out 

[http://ubuntuforums.org/showthread.php?t=1221225&highlight=mount+hard+drives](http://ubuntuforums.org/showthread.php?t=1221225&highlight=mount+hard+drives)

but how does one use the "[B]cmos-disabled"? or can anyone explain what this is for a newbies 
[/B]
So have you actually unmounted them? If you can see and access your drives on your Desktop:
Just right click each of them and choose unmount. That way you won't have access to it.

---

### Post by vamike999 on 2009-11-08
well but this is kind of the point i want my drives to not be mountable or see able i want them to be invisible. guess what you are telling me is there is just no way to do this. Linux does not have the ability to be used as a usb drive and some how lock off the hard drives so they are never seen. Its ok if there is no way to do it but just trying to figure out if this is the limitation of Linux.

---

### Post by Agent ME on 2009-11-08
It's just a silly thing to worry about. Assuming you even got some sort of strange linux virus that liked to try to copy itself to other installs onto your USB install, what makes you think it wouldn't be advanced enough to disregard your settings that tell it not to mount your hard drives?

---

### Post by JugglinPhil on 2009-11-09
> **Agent ME said:**
> It's just a silly thing to worry about. Assuming you even got some sort of strange linux virus that liked to try to copy itself to other installs onto your USB install, what makes you think it wouldn't be advanced enough to disregard your settings that tell it not to mount your hard drives?
The point is that it is not active in Linux at all, it has no power whatsoever. It cannot copy itself to anywhere, but that is not the problem: The trouble is that it might be copied/moved by accident, which can't happen if you don't have your drives mounted.
@vamike999
This surely isn't a limitation of Linux, but rather a limitation of our knowledge. Maybe you can PM some staff/experienced members to have a look at your thread? 
I seriously woudn't worry too much about infecting your windows drives, it is probably still safer than going online with windows itself.

---

### Post by vamike999 on 2009-11-09
yes but people always say do not worry. I want something however that is a 100 proof. I want a usb drive in write only mode and not to be able to see my hard drives. This would be a 100 proof. I want to be able to go to infected and high risk sites with knowing i will not get anything 100% of the time. If the hard drives can be mounted by clicking on them this tells me a virus could do the same and is not a 100% proof. So was trying to see if i could whip something up that was a 100 proof.

---

### Post by noway2 on 2009-11-09
A network that is completely non functioning is the one that is 100% secure.

If you are concerned about transferring a virus TO your windows system, you can install a virus scanner on your Linux system and keep it updated.  This should be at least as effective as the ones that run on a windows box, but far less intrusive.

---

### Post by JugglinPhil on 2009-11-09
If you want 100% security don't use the internet. That's the price we pay for global networking, it is never 100% safe no matter what you do.

---

