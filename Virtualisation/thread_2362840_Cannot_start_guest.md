---
title: "Cannot start guest"
date: 2017-06-02
forum: Virtualisation
---

### Post by danielsender on 2017-06-02
I'm running 16.04 (64b) on a Dell Precision M90. I was running without issues Centos 7 guest on virtualbox. The other day, the system crashed and now I cannot get Centos to fully boot. I get the grub menu, select the kernel version and I see the triple progress bar moving very slowly and once it gets to the end, that is the three bars are completely superimposed, then it gets stuck with the screen black. I tried selecting other kernel versions than the last one, but the behaviour is still the same. I really need help on this since I have very important stuff in that virtual machine.

Thanks.

---

### Post by deadflowr on 2017-06-02
Which system crashed the host or the guest?
(and I guess that in either case the guest was running as well?)

---

### Post by danielsender on 2017-06-02
I was not close to the machine, but I suppose that it was the guest that crashed because the host was running OK when I got back.

---

### Post by danielsender on 2017-06-02
I don't think it matters, but I wrote by error M90, should be M6500.

---

### Post by danielsender on 2017-06-03
any ideas?

---

### Post by danielsender on 2017-06-03
I posted the issue on the virtualbox forums, getting the following response: "[COLOR=#333333][FONT=&quot]*You are using the Ubuntu fork of VirtualBox and we do not support it here. You would need to ask them if there is an issue with VirtualBox. That said I don't really see anything in the log that points to VirtualBox as being the cause, but you would need to ask them to be sure, I would suspect the guest as being corrupt.*"

So, if this is the case of having the guest being corrupted, how would I go about fixing the guest, how do I mount the virtual image so I can start poking there?

Thanks[/FONT][/COLOR]

---

### Post by KillerKelvUK on 2017-06-04
Hey, not speaking for the forum here but maybe the lack of response is due to the guest being centos so less distro specific knowledge here. Have you run through the basic like confirming your virtualbox will run other guests without issue? I'd suggest you prove your host and virtualbox install are working without issue so then you can focus on this being a distro specific install issue and maybe try the centos forums if no further luck here?

I've little experience with virtualbox but can you not add the centos disk image as a 2nd drive in another virtual machine i.e. create a new Ubuntu live CD guest, that way the tools in the Live CD such as gparted and fsck will be able to see the centos disk?

Also it looks like there are plenty of search results on mounting a vdi inside an ubuntu host. ([https://askubuntu.com/questions/19430/mount-a-virtualbox-drive-image-vdi](https://askubuntu.com/questions/19430/mount-a-virtualbox-drive-image-vdi))

---

### Post by SeijiSensei on 2017-06-04
Try booting in safe mode or whatever it's called on RHEL flavors these days.  That will boot into single-user mode and give you a root shell.  At that point I'd copy all the files that matter to a backup device, then rebuild the VM from scratch.

If you can't find a safe-mode option, use the ability to edit the line of code that starts the boot record and add "single" to the end of the command.

See this for more details: [https://ma.ttias.be/boot-in-single-user-mode-on-centos-7-rhel-7/](https://ma.ttias.be/boot-in-single-user-mode-on-centos-7-rhel-7/)

I use CentOS on virtual servers, but it's been a while since I've actually installed it from a disk image.

When you're finished, I strongly recommend replacing the Ubuntu version of VirtualBox with the one available from Oracle's repository.  For more details, see [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

---

### Post by danielsender on 2017-06-05
Hi guys,

The moderator at the VirtualBox forum looked at the VirtualBox log files y said that everything looked ok ([https://forums.virtualbox.org/viewtopic.php?f=7&t=83335&p=394627#p394627](https://forums.virtualbox.org/viewtopic.php?f=7&t=83335&p=394627#p394627)), so after pressing Esc during to boot I noticed a message related to the selinux stuff, so I followed this advice: [https://www.centos.org/forums/viewtopic.php?t=50336](https://www.centos.org/forums/viewtopic.php?t=50336) and the issue was solved. So in other words, it was not a VirtualBox but a Centos problem.

Thanks for your help.

---

