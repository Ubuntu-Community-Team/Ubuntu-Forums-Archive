---
title: "VMware/Dual Boot"
date: 2008-02-20
forum: Virtualisation
---

### Post by fk4rp6 on 2008-02-20
I have a laptop running the latest distro of Ubuntu desktop and set to dual boot with Windows XP Pro.  I'm trying to setup VMware so I can load my XP install without having to reboot if I just need to run a simple program.  And still have the option of rebooting into the same XP install if I need to run something a little more resource intensive.

I was able to setup VMware to my Windows partition.  But when I power up the virtual machine it freezes when it tries to load GRUB and gives me "Error 17".

From what I've read this has something to with it being unable to mount the drive/partition.  I'm guessing that would be because Linux is running at the time.

Do I need to switch to using a Windows Boot loader?  If so how would I go about doing so?  Or is what I'm trying to do just not possible?

---

### Post by spiderbatdad on 2008-02-20
Not sure what you're trying to do here. Sounded like you wanted to run vmware-server from linux to be able to run windows from your linux environment, but then you installed vmware on xp.
This is what  I did. [http://ubuntuforums.org/showthread.php?p=4361087#post4361087](http://ubuntuforums.org/showthread.php?p=4361087#post4361087)

---

### Post by spiderbatdad on 2008-02-20
I think i see what is going on now. Have you tried running vmware through the terminal with sudo?
You will probably need to remove the existing virtual disk space and start over with this method.

---

### Post by fk4rp6 on 2008-02-20
Yup, that's how I usually run VMware.  So when I originally set it up I used sudo vmware through terminal to run the application.  

Just to make sure I removed the virtual disk and added it back.  Running VMware as mentioned.

Same trouble.

---

### Post by spiderbatdad on 2008-02-20
So you are trying to access your existing windows partition through vmware by mounting the disk?

---

### Post by fk4rp6 on 2008-02-20
Currently.  Though I'm not even sure if I'm doing that right.  When I setup VMware I did have it mount my Windows partition.

I would like to just be able to manage one Windows install.  And have the option of accessing that Windows install through VMware or by booting straight to it.

---

### Post by spiderbatdad on 2008-02-20
I'm curious about this too, though I don't dual boot. I see ways of making the other disk browseable as a virtual disk,  but not actually using the existing file system as an operating system. Maybe a symlink between the vmware file and the xp mount point. I know that sounds stupid.

---

### Post by spiderbatdad on 2008-02-20
You can use vmware-vdiskmanager to import a Boot Camp partition's .vmdk to a normal .vmdk file then create a native Virtual Machine around that.
Beware, this may violate EULA if the os is OEM installed, as you are essentially installing the os to another machine, albeit a virtual machine.;)
[http://communities.vmware.com/thread/122192](http://communities.vmware.com/thread/122192)

---

### Post by bodhi.zazen on 2008-02-20
There is a sticky at the top of this forum which discusses how to do this.

Keep in mind this is Beta and data loss can occur, so be careful.

---

