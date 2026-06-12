---
title: "How to install new version of VirtualBox"
date: 2009-07-25
forum: Virtualisation
---

### Post by blueridgedog on 2009-07-25
I have VirtualBox 2.1.  I get a notice when running that 3 is out.  If I download the .deb for 3 and attempt to install it, I am told "Error: Conflicts with the installed package 'virtualbox-2.1'".  

How can I upgrade VirtualBox?

---

### Post by moster on 2009-07-25
Why not remove old by synaptic?

---

### Post by ktechkio on 2009-07-26
To let package manager take over and solve problems on its own add the appropriate repository. See distribution at end of lines e.g jaunty

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) jaunty non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) hardy non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) gutsy non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) dapper non-free

---

### Post by moster on 2009-07-26
> **ktechkio said:**
> To let package manager take over and solve problems on its own add the appropriate repository. See distribution at end of lines e.g jaunty

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) jaunty non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) hardy non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) gutsy non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) dapper non-free

Do not give him incomplete information, you will only confuse him.

---

### Post by blueridgedog on 2009-07-26
> **ktechkio said:**
> To let package manager take over and solve problems on its own add the appropriate repository. See distribution at end of lines e.g jaunty

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) jaunty non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) hardy non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) gutsy non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) dapper non-free

I have:

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free

In my repository list and is how I installed VirtualBox originally.

---

### Post by blueridgedog on 2009-07-26
> **moster said:**
> Why not remove old by synaptic?

I have considered that option, but was hoping that there would be an upgrade path that did not risk my virtual machines.  If no upgrade option appears, then I will just un-install and re-install.

---

### Post by howefield on 2009-07-26
> **blueridgedog said:**
> I have considered that option, but was hoping that there would be an upgrade path that did not risk my virtual machines.  If no upgrade option appears, then I will just un-install and re-install.

Uninstalling Virtualbox won't mean you lose your virtual machines, if you created them in the default location, they are stored in your home directory, safe from any uninstall of the program.

You could though, create a backup of your vm by cloning to another location, using the clonehd command eg,

VBoxManage clonehd source destination

The actual command for your version of Virtualbox might be clonevdi rather than clonehd

---

### Post by blueridgedog on 2009-07-26
> **howefield said:**
> Uninstalling Virtualbox won't mean you lose your virtual machines, if you created them in the default location, they are stored in your home directory, safe from any uninstall of the program.

You could though, create a backup of your vm by cloning to another location, using the clonehd command eg,

VBoxmanage clonehd source destination

The actual command for your version of Virtualbox might be clonevdi rahter than clonehd

Thanks.  I will give it a shot.  Note, some of my hard disk images are in ~/VirtualBox/HardDisks and some are in ~/VirtualBox/VDI.  Those that are in VDI end in "img" and those that are in HaredDisks end in "vdi".  Why were some created one way and others another?

---

### Post by moster on 2009-07-26
I think but I never actually try it. "Mark for removal" will remove on virtualbox and leave everything else. And "Mark for complete removal" will remove settings too.

Your settings are in your home folder, hidden. Folder name is ".virtualbox" Backup that directory, and "Mark for removal" in synaptic. Then just install new virtualbox.

In the end, it is enough to have only you .vhd images. Even setting is not crucial. I have lost it several times and just make new virtual machine and add existing .vhd-s and that is all. Important data like that keep on separate partition, you can have "custom directory" for files like images.

---

