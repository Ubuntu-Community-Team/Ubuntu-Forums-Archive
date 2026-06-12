---
title: "Just installed VMware from source, now upgrading kernel, and it have issues."
date: 2008-03-19
forum: Virtualisation
---

### Post by nexus_2006 on 2008-03-19
Here's a pretty complicated issue, don't know if anyone can help me or not.

I am running Dapper and just installed VMware from the source.  Everything is workingn fine, but I want to change the kernel to one with SMP support.  (the 2.6.15-29-386 to the 2.6.15-29-686)

When I installed VMware and ran vmware-install.pl it built a kernel module for the 2.6.15-29-386 which I have now.  When I use Synaptic to change the kernel image and header packs to the -686 one that I want will I only have to re-run vmware-install.pl or will I have to remove the entire VMware install and start again, and if so how the hell do I get all that off there??

Anybody, any ideas?

---

### Post by fjgaude on 2008-03-19
Not sure, but just running vmware-config.pl might do the trick.

That file should be in /usr/bin directory.

Let us know how you are doing.

---

### Post by nexus_2006 on 2008-03-19
OK, I'll go ahead and give it a shot.  If it breaks the thing you guys are here to help me sort it out, right? ;)

I'll let you know how it goes.

---

### Post by jayson.rowe on 2008-03-19
First, you couldn't have installed VMWare from source, as they don't freely distribute their soruce code. Perhaps you installed from a perl script using pre-compiled binaries that were compressed in a tar.gz file?

In any event with a kernel upgrade, you will have to rebuild the kernel module, or at least configure VMWare to load a different one (I think VMWare WS 5+ and VMWare Server 1.0.x have pre-made Dapper modules, but I haven't run Dapper in some time, so I can't remember for sure).

Regardless of which scenario is true, you should be able to run "sudo /usr/bin/vmware-config.pl" and be on your way. If you still have trouble building the module, you could try the latest any-any update patch.

---

### Post by jayson.rowe on 2008-03-19
Whoops someone beat me too it :)

I always hit the forums, hit "New Post" and open up all the ones I want to read/help w/ in tabs and come back...didn't realize there were answers already posted when I replied.

As the others said as well, vmware-config should get you back on track.

---

### Post by nexus_2006 on 2008-03-19
I assumed it would be something like that, thanks.  And yes, I used a pre-configured perl script to install binaries distributed by VMware.

Anyway, the problem I have now is that I selected the kernel that I wanted in Synaptic, added it to grub, rebooted.  If I try to boot into the old .15-29-386 everything runs fine, loads X, etc.
When I select the .15-29-686 version it loads faster, both processors are present now, but it gives me an Xorg error "cannot load module nvidia" and throws me out to the command prompt login.  I've apt-gotten the nvidia-glx package again (after removing it) because I assumed that the module that was installed wasn't compatible with the new kernel.  No go as its getting the same version.  How do I convince Ubuntu apt-get to get the right version of the package for the kernel that I want to use.

I'm assuming the display driver won't be the only kernel module screwed up by manually getting a newer/different kernel.  How is this supposed to work?

---

### Post by fjgaude on 2008-03-19
Well, you are dong something that I've never done... the kernels have changed so much in the last two years that many, many of the older applications and programs are no longer valid. It's best in my view to only use a kernel that has been matched with the support apps.

You see apt-get thinks you are using the old kernel, and I can't say how to change that. Maybe someone else here has done this before and can help you with it. I do believe what you said, lots of other programs are going to fail with the newer kernel.

---

### Post by nexus_2006 on 2008-03-19
I think I'll jump over to the right forum for this kind of question and try to get a better response.  If I get VMware working again with the method posted above (i.e. if it really is that easy) I'll come back and let everyone know.

---

### Post by nexus_2006 on 2008-03-20
Got it.  Had to install several packages, not just the linux kernel image but the headers, restricted drivers module, and a linux-kernel-686 (or something like that).  Ran vmware-config.pl and vmware started up just fine too.  I had to build a new vmnte module for the kernel, but it did that pretty fast and easy.  Thanks for the help guys.

---

### Post by fjgaude on 2008-03-20
Good! Can you tell us what link we could use that helps you get to where you are?

---

