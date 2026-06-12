---
title: "Virtualized windows viewing linux partitions"
date: 2007-12-10
forum: Virtualisation
---

### Post by afderrick on 2007-12-10
Ok I did some quick looking and didn't immediately find anything and am needing a quick answer here.  I have virtualized Windows under VirtualBox and it was very easy.  The question I have is there is a file I need on my linux folder that I need to get to my windows folders now.  Is it possible to do this since I am virtualized would I still use the same methods as I would otherwise?  Is that an easier way to do it?  Or since this is a one time thing should I just burn a CD and copy it over that way?  Thanks in advance for your help.

---

### Post by Portable_Jim on 2007-12-11
I have heard that mounting a partition twice causes severe corruption.

You could try setting up shard folders and networking between the host and guest, otherwise it would be easiest to transfer the file using a drive that both OSs can get to (eg, USB drive or CD).

---

### Post by lil_B on 2007-12-11
From the Manual

> 

4.4 Folder sharing

Shared Folders allow you to access files of your host system from within the guest
system, much like ordinary shares on Windows networks would &#8211; except that shared
folders do not need a networking setup. Sharing is accomplished using a special ser-
vice on the host and a file system driver for the guest, both of which are provided by
VirtualBox.

   In order to use this feature, the VirtualBox Guest Additions have to be installed.
Currently, Shared Folders are limited to Windows XP, Windows 2000 and Linux 2.4
and 2.6 guests.

   To share a folder with a virtual machine in VirtualBox, you must specify the path of
the folder to be shared on the host and chose a &#8220;share name&#8221; that the guest can use
to access it. Hence, first create the shared folder on the host; then, within the guest,
connect to it.
   
There are several ways in which shared folders can be set up for a particular virtual
machine:
    
    &#8226; In the graphical user interface of a running virtual machine, you can select
      &#8220;Shared folders&#8221; from the &#8220;Devices&#8221; menu, or click on the folder icon on the
      status bar in the bottom right corner of the virtual machine window.
   
    &#8226; If a virtual machine is not currently running, you can configure shared folders in
      each virtual machine&#8217;s &#8220;Settings&#8221; dialog.
                                    
    &#8226; From the command line, you can create shared folders using the the VBoxMan-
       age command line interface; see chapter 8, VBoxManage reference, page 82. The
       command is as follows:
       
VBoxManage sharedfolder add "VM name" -name "sharename" -hostpath "C:\test"
 
There are two types of shares:
  1. VM shares which are only available to the VM for which they have been defined;
  2. transient VM shares, which can be added and removed at runtime and do not
     persist after a VM has stopped; for these, add the -transient option to the
     above command line.

Then, you can mount the shared folder from inside a VM the same way as you would
mount an ordinary network share:
  
  &#8226; In a Windows guest, starting with VirtualBox 1.5.0, shared folders are
     browseable and are therefore visible in Windows Explorer. So, to attach the
     host&#8217;s shared folder to your Windows guest, open Windows Explorer and look
     for it under &#8220;My Networking Places&#8221; -> &#8220;Entire Network&#8221; -> &#8220;VirtualBox Shared
     Folders&#8221;. By right-clicking on a shared folder and selecting &#8220;Map network drive&#8221;
     from the menu that pops up, you can assign a drive letter to that shared folder.
     Alternatively, on the Windows command line, use the following:
     
net use x: \\vboxsvr\sharename
    
     While vboxsvr is a fixed name (note that vboxsrv would also work), replace
     &#8220;x:&#8220; with the drive letter that you want to use for the share, and sharename
     with the share name specified with VBoxManage.
   


---

### Post by mozetti on 2007-12-11
Just to chime in, I used the instructions from the VirtualBox Help (posted above) to make my linux partitions available to my XP Virtual Machine. Works like a charm.

---

### Post by Portable_Jim on 2007-12-11
> **mozetti said:**
> Just to chime in, I used the instructions from the VirtualBox Help (posted above) to make my linux partitions available to my XP Virtual Machine. Works like a charm.
That was what I was referring to when I talked about sharing

---

