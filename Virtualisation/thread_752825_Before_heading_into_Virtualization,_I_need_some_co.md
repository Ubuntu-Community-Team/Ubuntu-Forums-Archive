---
title: "Before heading into Virtualization, I need some confirmations"
date: 2008-04-12
forum: Virtualisation
---

### Post by Browser_ice on 2008-04-12
I very recently learned about the existance of Virtualisation of O/S systems on the same PC. This sounds very interesting for me as I currently have Win-XP Pro and Ubuntu 7.10 on dual boot. I kept my XP until now because of some softwares I use that I cannot run under Ubuntu (I admit I haven't used Wine but I do not think it will be 100% bug free for them) and starting a cross platform development project.

So before I decide (don't know when) to go ahead with having Ubuntu as main O/S and XP as Virtual O/S, I need a confirmation on a few things.

- Can **everything** running in XP run on a VM under Ubuntu and be bugfree ?
=== ex: 3dmax 7, gmax, Photoshop (I know about Gimp), QuArK, all recent games including Steam,... 

- Can I convert my Windows XP into a VW file, save-it o DVDs, reformat my whole PC, re-install Ubuntu and then install that VM file as a VM O/S ?  How big will that VM file be ?

- Can I exchange files (or more like access) bethween Ubuntu and any VM O/S ?

- Do I use the same VM software to use XP &  Fedora (office uses it) ?

- If I do a backup of my VM O/S, will it be saved on external Media (DVD) or can it reside as a file under Ubuntu ?

- Will O/S updates work without problems on the VM O/S ?

- I see in the forum references to VirtualBox. Is this another name for a VM O/S or something different ?


If I have other questions, I'll reply back here.

---

### Post by keratos on 2008-04-12
1. "Everything" is a very ver very wide scope. What exactly do you mean by this. I doubt whether "every" app has been tested to run. But generally, most apps should run because virtualisation that uses a hypervisor (e.g. virtualbox, vmware etc) actually changes the host O/S (in your case that would be ubuntu). The guest O/S (in your case XP) is effectively oblivious to its host. Indeed, newer CPUs have virtualisation extensions that support even ""superior""  virtualisations supported by hardware itself (the CPU) and not sofware mods to the O/S as in the case of hypervisors. However this is relatively new technology and perhaps not as robust as the hypervisors - yet!

2. YES. And its size would be dependent on the apps you installed in XP!! Most of my XP VDIs (the VM file) are around 3G and that includes the usual media apps, burning S/W, office, image processing. No games though.

3. YES

4. YES

5. EITHER. Depends on how you backup. The VM file is just that, a file, like any other file so you could use brasero of K3b to back it up. Moreover, the virtualisation S/W would usually create a local directory (say in your /home directory) and place relevant files in there so all that would be required is to backup that local directory. For example, in virtualbox these are in ~/.VirtuaBox and for vmware, in ~/.VMware

6. YES

---

### Post by Browser_ice on 2008-04-12
One thing I forgot to mention, I want to have all the VM O/S independant (meaning with its own desktop or window if you like). Unless  you guys give me good reasons not to

- what's the difference between VirtualBox, VMware and Xen ?

- can I have the folder containing the VM O/S placed on a different drive then my Ubuntu's

- besides USB and drivers, what are the other most common problems with VM O/S ?

---

### Post by popch on 2008-04-12
> **Browser_ice said:**
> 
- Can **everything** running in XP run on a VM under Ubuntu and be bugfree ?
=== ex: 3dmax 7, gmax, Photoshop (I know about Gimp), QuArK, all recent games including Steam

Since the applications will be running under XP (and not under VM) 'practically' every application will run in a virtual machine without any problems at all.

There are a few differences, though:

Access to USB devices is not the same in a VM as in a real machine. 
XP in a virtual machine will 'see' another graphics card, other disk controllers, other optical drives and another BIOS. Any application relying on access to one of these things will become aware of running in a virtual machine and then may or may not keep on working.
You need a PC with quite enough real RAM in order to use virtualisation.

> **Browser_ice said:**
> 
- Can I convert my Windows XP into a VW file, save-it o DVDs, reformat my whole PC, re-install Ubuntu and then install that VM file as a VM O/S ? How big will that VM file be ?

As has been said, your typical file will be on the order of 3GB. Actually, when you just move the contents of your existing partition into that file, that's going to be the amount of data in that file.

> **Browser_ice said:**
> Can I exchange files (or more like access) bethween Ubuntu and any VM O/S ?.

Yes. Most products which support virtualisation also support some kind of 'shared folders'. Some users find it more convenient to just set up SAMBA shares.

> **Browser_ice said:**
>   
  - Do I use the same VM software to use XP &  Fedora (office uses it) ?
  
 Yes. You just create different 'virtual machines' which are just different disk files. Depending on the capacity of your computer, you might even be able to run more than one virtual machine at the same time.
 
 > **Browser_ice said:**
> 
  - If I do a backup of my VM O/S, will it be saved on external Media (DVD) or can it reside as a file under Ubuntu ?.

A virtual machine is just a number of files in your file system. You may save it to DVD, a USB stick, to a file server or wherever your fancy takes you.


> **Browser_ice said:**
> - Will O/S updates work without problems on the VM O/S ?.

Yes, provided you let your virtual machine access the internet. Some of us do not do that, for security reasons. Remember: no internet access, no firewall needed.

> **Browser_ice said:**
> I see in the forum references to VirtualBox. Is this another name for a VM O/S or something different ?

VMWare and VirtualBox are two different products with different strengths and weaknesses.

Personally, I find using VirtualBox in Ubuntu a bit more convenient than VMWare.

---

### Post by Jose Catre-Vandis on 2008-04-12
Suggest you just give it a try?

Visit virtualbox.org and download the binary for either ubuntu or windows (;))

Install, install your preferred OS, and see what you think. The biggest problem you will have is with games, due to the virtualisation of the graphics card (you can't use your real one to its full potential) Suggest you stick to dual boot for that, but the benefits of having XP sat there sitting while you are in ubuntu are great indeed

---

### Post by popch on 2008-04-12
> **Jose Catre-Vandis said:**
> Visit virtualbox.org and download the binary for ... ubuntu

Or even simpler - install it from the repository.

---

### Post by Browser_ice on 2008-04-12
The thing is that in order for me to go ahead, I will have to reformat my whole PC because :
- my Ubuntu drive iis too small
- dual boot where 90% of my disks are for windows Xp, I want to move away from Windows but keep a few softwares I can't run under Ubuntu
- it would be alot easier I think to install XP under VM then convert my existing XP

So we are talking about alot of work that if something goes wrong, the same amount of working days are needed to rever back to what I had before is something f... ups up.

Should I wait for Ubuntu 8 or stay with my 7.10 ?

---

### Post by Jose Catre-Vandis on 2008-04-12
can you do any partition resizing with gparted to give you enough space on Ubuntu, or are you talking about HDDs restricting your changes?

---

### Post by Browser_ice on 2008-04-13
I haven't done anything yet and the HD layout is not restricting me. I am just stating that its alot of work to do it + reverting back if it doesn't work. So I wouldn't want to do all this for nothing.  My free time is limited because I always do 12 hours working shifts.

Using VirtualBox, can we maximize the VM O/S windows ? I assume yes.

Hummm, about the graphic card issue under the VM O/S....  maybe I should do the oposite then ?   Having XP as main but with little space as possible and Ubuntu as VM O/S ? I have no games in Ubuntu.

What about Ubuntu V8 coming soon ?  What does that change to what I want to try ?  I read they changed the VM tool to KD something.

---

### Post by keratos on 2008-04-13
> **popch said:**
> Or even simpler - install it from the repository.

No mention here that the repository version is OSE (Open Source Edition) and DOES NOT include USB support in addition to other limitations. 

I agree with Jose - goto virtualbox.org instead (provided you dont mind to the "odd few" closed course binaries, if you're totally open then I'm afraid you will not be able to use virtualbox with USB etc. and VMware used to be totally closed source - unless that's changed , I cant be bothered to goolge right now!)

---

### Post by keratos on 2008-04-13
> **popch said:**
> Or even simpler - install it from the repository.

Agreed. Download (for free) the binaries from their site. Note these are not open source !!!

---

### Post by keratos on 2008-04-13
> **popch said:**
> Since the applications will be running under XP (and not under VM) 'practically' every application will run in a virtual machine without any problems at all.

There are a few differences, though:

Access to USB devices is not the same in a VM as in a real machine. 
XP in a virtual machine will 'see' another graphics card, other disk controllers, other optical drives and another BIOS. Any application relying on access to one of these things will become aware of running in a virtual machine and then may or may not keep on working.
You need a PC with quite enough real RAM in order to use virtualisation.


Not quite!

Virtualisation drivers are often "generic" and as such, may not meet specific software requirements. Take a game on XP for example. Running under XP native may have no issue however, running under VMware/Virtualbox etc. the video card driver is generic and certainly will not have access to the specialised graphics polygon and bitblk drivers that hard gamers need.

So to suggest "every application will run in a virtual machine without any problems at all" is misleading because whilst it will "run" it may not perform to the user's expecation due to limitations in driver support.

---

### Post by keratos on 2008-04-13
> **Browser_ice said:**
> I haven't done anything yet and the HD layout is not restricting me. I am just stating that its alot of work to do it + reverting back if it doesn't work. So I wouldn't want to do all this for nothing.  My free time is limited because I always do 12 hours working shifts.

Using VirtualBox, can we maximize the VM O/S windows ? I assume yes.

Hummm, about the graphic card issue under the VM O/S....  maybe I should do the oposite then ?   Having XP as main but with little space as possible and Ubuntu as VM O/S ? I have no games in Ubuntu.

What about Ubuntu V8 coming soon ?  What does that change to what I want to try ?  I read they changed the VM tool to KD something.

... These and previous posts by you are, no insult intended, all very generic questions and are readily answered 

here [http://en.wikipedia.org/wiki/Virtualization](http://en.wikipedia.org/wiki/Virtualization)
and
here [http://www.vmware.com/virtualization/](http://www.vmware.com/virtualization/)
and
here [http://www.virtualization.info/](http://www.virtualization.info/)
and 
here [http://www.virtualbox.org/wiki/VirtualBox](http://www.virtualbox.org/wiki/VirtualBox)


.. i could go on. I found these whilst posting this, by typing a few words in google.

---

### Post by popch on 2008-04-13
> **keratos said:**
> ...

Virtualisation drivers are often "generic" and as such, may not meet specific software requirements. Take a game on XP for example. Running under XP native may have no issue however, running under VMware/Virtualbox etc. the video card driver is generic and certainly will not have access to the specialised graphics polygon and bitblk drivers that hard gamers need. ...

I fully agree here and have so stated in the post you quoted. "'Practically' every application" is what I wrote.

---

### Post by StageCraft on 2008-04-13
> One thing I forgot to mention, I want to have all the VM O/S independant (meaning with its own desktop or window if you like). Unless  you guys give me good reasons not to

From my experience with virtual box, you may want to move the screen with the virtualization to a second monitor if you have one. mine has acted a bit funky around the edges. nothing major and everything still works but it can get a bit annoying. 

> - what's the difference between VirtualBox, VMware and Xen ?

- can I have the folder containing the VM O/S placed on a different drive then my Ubuntu's



You should be able to save the .VDI file to an external hard drive (I think you mentioned that you had one) then it wont take up any extra space, and you can make dynamic hard drives in VBox so that its only taking up as much space as it has to.

---

