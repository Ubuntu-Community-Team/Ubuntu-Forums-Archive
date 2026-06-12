---
title: "How to set up a windows xp virtual machine?"
date: 2012-05-19
forum: Virtualisation
---

### Post by p.wolf on 2012-05-19
I installed VirtualBox on ubuntu 12.04 and downloaded an xp iso and stored it in my home folder, however, when trying to set it up it said "FATAL: No bootable medium found! System halted." 
Please advise.

---

### Post by PhantomTurtle on 2012-05-19
It is illegal to download XP and install on a vmachine but I will explain what you are doing wrong. When you start a VMachine you must tell vbox to mount the iso or a CD you in your drive. So after you start the vmachine click on devices in the global menu. Next under CD/DVD devices choose "Choose a virtual disk file..." and then select your iso and reset your vmachine. Then when you are done go back to the CD/DVD devices menu and click on the mounted iso to unmount.

---

### Post by p.wolf on 2012-05-19
> **PhantomTurtle said:**
> It is illegal to download XP and install on a vmachine but I will explain what you are doing wrong. When you start a VMachine you must tell vbox to mount the iso or a CD you in your drive. So after you start the vmachine click on devices in the global menu. Next under CD/DVD devices choose "Choose a virtual disk file..." and then select your iso and reset your vmachine. Then when you are done go back to the CD/DVD devices menu and click on the mounted iso to unmount.

I have the registration key, but not a disc with the iso so i downloaded it from microsofts site.
After creating a new vm on first run it has this wizard, under media source I selected the iso, then i clicked next and start. Is this right?

---

### Post by forrestcupp on 2012-05-19
> **p.wolf said:**
> I have the registration key, but not a disc with the iso so i downloaded it from microsofts site.
After creating a new vm on first run it has this wizard, under media source I selected the iso, then i clicked next and start. Is this right?

Yes, that's how you do it. It should now boot to the installation and install it to your VirtualBox VM file.

---

### Post by scottbomb on 2012-05-19
> **p.wolf said:**
> After creating a new vm on first run it has this wizard, under media source I selected the iso, then i clicked next and start. Is this right?

Sounds right to me. You may have a bad .iso file.

The way I did mine, I did not mount it or anything like that. I just copied the .iso file to a folder normally accessable (such as /home) and then pointed VirtualBox to that .iso. 

You may have to delete and re-create the VM on your next try.

---

### Post by p.wolf on 2012-05-19
The iso is in my home folder and I tried this several times, failed every time. I don't understand what I'm doing wrong?!

---

### Post by holycow131415 on 2012-05-19
[http://www.youtube.com/watch?v=TB-8olhzK6w](http://www.youtube.com/watch?v=TB-8olhzK6w)

XP, 7, doesnt matter.

---

### Post by p.wolf on 2012-05-19
> **holycow131415 said:**
> [http://www.youtube.com/watch?v=TB-8olhzK6w](http://www.youtube.com/watch?v=TB-8olhzK6w)

XP, 7, doesnt matter.

Followed his instructions, still same result.

---

### Post by PhantomTurtle on 2012-05-19
> **p.wolf said:**
> Followed his instructions, still same result.

Maybe something is wrong with the iso then. That would be the only reason, or else it should boot. If you want to test it, in the same vmachine mount a Ubuntu live cd and check it that works.

---

### Post by p.wolf on 2012-05-19
> **PhantomTurtle said:**
> Maybe something is wrong with the iso then. That would be the only reason, or else it should boot.

Do you know where I could get a working copy of windows xp? I have the registration key, just not the disc, so it should be legal.

---

### Post by uRock on 2012-05-19
Outside of MSDNAA, I do not think it is posible to downlad a legitimate copy of Windows XP.

---

### Post by lisati on 2012-05-19
There's always *cough* *mumble* <insert-name-of-dubious-website-I'm-not-about-to-name-it> *mumble* *mutterings about being careful* Having said that, wherever you finally get a working disk and/or ISO file from, watch out for malware.

Speaking as a forum user (and not necessarily forum staff), I'm wondering what options are available at the MS website for people in this situation. One thing I've heard of is people being able to get OEM disks from their computer manufacturer.

edit: Ninja'd with suggetsion to check MSDNAA

---

### Post by uRock on 2012-05-19
> **lisati said:**
> Speaking as a forum user (and not necessarily forum staff), I'm wondering what options are available at the MS website for people in this situation. One thing I've heard of is people being able to get OEM disks from their computer manufacturer.

I hunted MS's site for quite some time searching for an ISO download via their site. Couldn't find anything aside from buying Windows 7. I do not think the OEM image will install to a VBox as the installer will be looking for the mobo model, IIRC.

---

### Post by lisati on 2012-05-19
> **uRock said:**
> I do not think the OEM image will install to a VBox as the installer will be looking for the mobo model, IIRC.
Now that you mention it I think you have a point. Out of curiosity I once tried running the recovery disks for one of my machines on another machine by a different manufacturer. It didn't work. :( 

@OP: good luck with your search for a safe and legal copy. I now step aside for others who might have more useful ideas.

---

### Post by PhantomTurtle on 2012-05-19
An OEM copy will be tied to that machine and will not work with other computers. There is a similar concept in normal CD's. Downloading just any iso will not work with your key because the keys are tied to the cd and will not work without the cd iso that it originally came from. (I know, it's really stupid. And that's why we use Ubuntu, because it's awesome and lets us use what's rightfully ours).

---

### Post by scottbomb on 2012-05-19
Any XP .iso I should install to the point at least where you enter your key. If it doesn't like the key, it will reject it. It sounds like the OP can't even get that far.

---

### Post by Rebelli0us on 2012-05-21
You can easily make your own ISO using NLite and any Windows CD.

---

### Post by emagar on 2012-07-10
Rebelli0us, could you expand on how to make an iso via NLite? I have a win7 recovery cd from this machine (from before I nuked windows) and wish to be able to use it with virtualBox. Thanks!

---

### Post by pqwoerituytrueiwoq on 2012-07-10
that is unlikely to work since the recover disk will want the mobo on the host not the virtual board
any retail (or [oem cd](http://www.newegg.com/Product/Product.aspx?Item=N82E16832116986)) iso/cd will work
a retail cd will work with a oem license key

you can have virtual box use a physical cd see attached image

> **p.wolf said:**
> Do you know where I could get a working copy of  windows xp? I have the registration key, just not the disc, so it should  be legal.
answering this directly is not allowed but you do know how to use google
and if your xp install does not ask for a key google how to change it

---

### Post by CharlesA on 2012-07-11
> **pqwoerituytrueiwoq said:**
> 
and if your xp install does not ask for a key google how to change it

I wouldn't trust **any** Windows XP CD that doesn't ask for the serial. With Win7, you can bypass filling in the serial during setup, but it will prompt you to activate that copy of Windows and you'd need the serial to do that.

Of all the XP installs I have done (retail, OEM and volume) I haven't run into any that didn't ask for a serial.

---

