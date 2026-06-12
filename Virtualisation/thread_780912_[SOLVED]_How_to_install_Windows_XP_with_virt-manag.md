---
title: "[SOLVED] How to install Windows XP with virt-manager"
date: 2008-05-03
forum: Virtualisation
---

### Post by Bill Roberts on 2008-05-03
I've successfully created a virtualization environment using kvm.  I've installed a virtual ubuntu desktop from an iso file, but now I want to install Windows XP and virt-manager doesn't allow me to select CD as a source.  Don't seem to have sound either. Can anyone help?

---

### Post by Scooter7 on 2008-05-03
I'm having the same problem.

To be more specific, I'm running KVM inside Ubuntu 8.04, and I'm trying to create a new Virtual System.   I have my WinXP disk in my drive and mounted, but the 'CD-ROM or DVD' option is grayed out:

[img]http://shadowserve.ath.cx/stuff/images/dvd_option_gray.png[/img]

Any idea why?

---

### Post by anderson_mcsouza on 2008-05-11
I had the same problem, so I created a ISO image to continue installing my windows XP VM.
It worked fine on the first step of installation process (partitioning, formating and file coping from cd to disk). When this step finished and the guess windows restarted (VM got down and I started it again) I received the following screen:

[IMG]http://us.f13.yahoofs.com/bc/48270a94_2418/bc/ubuntu/windowsXpVMError.png?bfc8wJIBfjL4uDgU[/IMG]

Any ideas?

Thanks, 
Anderson Souza

---

### Post by mshu on 2008-05-11
I was never able to install WIn XP under KVM.
After the initialize (copying system files) the KVM does not know how to reboot, instead it shuts off and my cd rom drive is gone. 

After that the installation just totally buggy and I have never successfully preform a clean install.

Anyone have an idea how to use vitt-manager to do a clean install of Win XP ? I try to use both CD ROM and ISO image, same result.

><

---

### Post by breagerey on 2008-05-20
After much frustration this is how I got an XP64 VM to work (mostly) in virt-manager.
It's probably not the proper way.. but it works on my system. ;)

Create the image file for XP using the virt-manager GUI[LIST]
[*]Click new 
[*] Give it a name
[*] Give it an iso to install from (you're not gonna use it so just pick one)
[*] Assign the storage space how you like (I've only used files)
[/LIST]

After it's created and it fails to start, shut it down.
Install XP onto the image from the command line
> kvm -boot d -cdrom /dev/<yourcd> <path_to_img_you_created>

To get to this VM via virt-manager I had to add the following /etc/libvirt/qemu/<myXPinstall>.xml just under </os>
 > <features>
    <acpi/>
  </features>
After you make changes to the xml you need to redefine it.
> sudo virsh
define /etc/libvirt/qemu/<myXPinstall>.xml
quit

I was then able to start my XP64 VM from virt-manager
I've got networking but I can't get sound to work.

If I start the vm from the command line with  > kvm -soundhw all XP.img
XP can see that there is a multimedia device but fails to install it.

I can't get sound even that far via virt-manager. :(

Regarding greyed out items in virt-manager:
It seems to be a permissions issue.
If you run > sudo virt-manager you'll probably find that they are no longer greyed out.

I have no idea how bad of an idea any of this is... :?
... but I do now have a working VM of XP64 :D

---

### Post by albert_gerritsen on 2008-05-24
I have a very similar experience as mshu. I had an ISO to start with and the first part went fine, but after the first reboot the cdromdrive was gone... After some fiddling around, i got it back and continued the installation but to no avail; the installation hangs at random points in time.

Starting the installation without using virt-manager (as described by breagerey) worked a lot better for me (thanx for the info breagerey!!).

I dont have time to systematically test what is going wrong and see if i can file a bug report...

---

### Post by Bill Roberts on 2008-08-13
Went with VMware instead - poor performance but at least it works.

---

