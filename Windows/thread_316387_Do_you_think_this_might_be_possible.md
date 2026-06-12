---
title: "Do you think this might be possible?"
date: 2006-12-10
forum: Windows
---

### Post by marianom on 2006-12-10
My coworker is getting a new laptop so he's giving me his dell inspiron (2 years old, 1 gig ram). It's still with the original windows xp. Of course first thing I will do is erase it and install a brand new and beautiful edgy.
However, I'll be developing a few python libraries and I need them to work both in linux and windows. Kinda I would like to uninstall windows, install ubuntu and then with vmware install the xp so that I can easily switch when I need to try the libraries.

Do you guys think there's a chance that I can keep the original windows version after this? I mean, if when I'm installing it will ask for the license code (or whatever it's called) and it will accept the previous one (the one that came with the machine)?
I don't want to buy an xp license just for this (or anything else for the matter) but since we bought the machine and we were charged for the windows I think it's ours and I should be capable of installing it this way if I want to.

I realize there might be better places to ask this (for example the dell customer service) but I would like to hear your advices first, before trying over there.

---

### Post by bernied on 2006-12-10
I think it's Microsoft you need to ask, not Dell. I think licences are specific to a machine, the question is whether your vm 'machine' is recognised as being the same machine as the machine itself.

---

### Post by Dr. C on 2006-12-10
> **bernied said:**
> I think it's Microsoft you need to ask, not Dell. I think licences are specific to a machine, the question is whether your vm 'machine' is recognised as being the same machine as the machine itself.

You may wish to consult a lawyer in your country. The Windows XP EULA is silent on the subject of virtualization. What really matters is how a court of law in your country would interpret the EULA in this situation and not how Microsoft says the EULA should be interpreted. For example Microsoft may say no but a court of law may interpret the EULA to say yes. The court may give you the benefit of the doubt since Microsoft drafted the contract and the contract is not clear on the matter. There is also the question of the enforceability of the EULA. 

Then there is the question of the DRM (product activation) preventing running an DELL OEM version in a VM even if the EULA allows this. My understanding is that OEM versions of XP from large computer makers such as DELL are locked to th BIOS of the computer and will not activate at all, on a computer with a different BIOS such as a virtual machine.

---

### Post by marianom on 2006-12-11
Thanks both of you for your input.

---

### Post by rlozano on 2006-12-11
> **marianom said:**
> My coworker is getting a new laptop so he's giving me his dell inspiron (2 years old, 1 gig ram). It's still with the original windows xp. Of course first thing I will do is erase it and install a brand new and beautiful edgy.
However, I'll be developing a few python libraries and I need them to work both in linux and windows. Kinda I would like to uninstall windows, install ubuntu and then with vmware install the xp so that I can easily switch when I need to try the libraries.

Do you guys think there's a chance that I can keep the original windows version after this? I mean, if when I'm installing it will ask for the license code (or whatever it's called) and it will accept the previous one (the one that came with the machine)?
I don't want to buy an xp license just for this (or anything else for the matter) but since we bought the machine and we were charged for the windows I think it's ours and I should be capable of installing it this way if I want to.

I realize there might be better places to ask this (for example the dell customer service) but I would like to hear your advices first, before trying over there.

laptops do come with their OEM licenses at the back. you can always re-install your windows OS using that key found at the back of your laptop.

---

### Post by bernied on 2006-12-11
> **rlozano said:**
> laptops do come with their OEM licenses at the back. you can always re-install your windows OS using that key found at the back of your laptop.I would have thought that the big question is whether Windows will allow this licence to be registered for the virtual machine, if it has already been registered for the hard machine, whether it is legal or not. I'm sure the OP would not relish spending years fighting with Microsoft over the terms of their licence without a windows install on their machine.

Has anyone actually done this??

---

### Post by marianom on 2006-12-11
Here in ubuntu forums I saw a lot of people using vmware. They must have succesfully introduced the license code, otherwise it won't work. 

I hope there's no difference regarding the preinstalled xp in the dell.

---

### Post by Dr. C on 2006-12-11
> **marianom said:**
> Here in ubuntu forums I saw a lot of people using vmware. They must have succesfully introduced the license code, otherwise it won't work. 

I hope there's no difference regarding the preinstalled xp in the dell.

This one really depends on the particular OEM version of Win XP. Microsoft started blocking activation for large OEM vendor keys in 2003 or 2004 I think. These versions of XP do not require activation when installed on the orginal hardware, but will not activate at all if installed on onther hardware emulated or not. If installation on the original hardware does not require acitvation and the laptop is recent then there is a good change that that version of XP will not activate in a VM. In onther cases it will work and activate in a VM.

---

### Post by marianom on 2006-12-11
Pretty sure it didn't require activation that time (november 2004). Let's see how it goes: maybe I have a slight chance to make it works.

---

### Post by Wall86 on 2006-12-16
i know with hardware, that if you change over 3 major hardware parts on your computer, that your version of windows will not register properly.

you can try to contact macrohard about this, tell them that your no longer using the orginal install at all, blah blah blah, and see if they will let you.

---

### Post by drr422 on 2007-01-10
I just had an idea about moving a windows partition to vmware.  I recently had to take an image of a windows partition and restore it on another harddrive.  This might work if you want to move your current windows partition to vmware.  Aquire an Acronis True Image cd, install it onto windows, making sure to burn that rescue cd, then image the C:/ drive onto a seperate partition or a removable drive (or a dvd if you can).  Verifiy the image after its done.  Load the rescue cd in vmware, making sure your backup location is available in vmware, then you should be able to restore it to it.  You might have to partition the vmware thing with your filesystem you want windows to run in cause thats what i did.  

But this would mean that your exact windows partition would be restored in vmware.  You'll have to install vmwaretools, and it might not work, so proceed at your own risk.

---

### Post by bsalt on 2008-01-27
This idea hit me. I'm going to try it out soon... but what if you just purchased the Windows XP install media from Newegg, and then used the license on your computer? I'm not sure if this is against any Microsoft licensing, but I do believe it would work. I'm in the same boat as you - I need Windows for an application at work, and a couple apps just for home, but if I wanted to go with just Windows, my laptop would already be slower and slowing down each day with XP.

---

