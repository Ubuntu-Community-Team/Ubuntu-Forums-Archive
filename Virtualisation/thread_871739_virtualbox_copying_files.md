---
title: "virtualbox copying files"
date: 2008-07-27
forum: Virtualisation
---

### Post by elitefox on 2008-07-27
Good Day! :popcorn:

host: ubuntu 8.04 final
guest: windows xp

using sun vmx virtualbox

problem: i don't know how to copy files from ubuntu or any other disk to the guest OS.

just thought it was as easy as copy from host OS then paste to guest OS :confused:


For every help,

Thanks in advance

---

### Post by UbuntuNerd on 2008-07-27
I think even though you're working with virtual box you still have to install samba file sharing but Im not 100 percent sure someone please correct me if Im wrong, have a look in this link it explains further 


[http://www.virtualbox.org/wiki/Sharing_files_on_OSE](http://www.virtualbox.org/wiki/Sharing_files_on_OSE)

---

### Post by overdrank on 2008-07-27
moved :)

---

### Post by elitefox on 2008-07-27
@overdrank

Thanks for moving it to the right place :lolflag:
i am new to this so i put it to absolute beginner ... :guitar:


@jperez78

currently looking at the link you gave
i didn't see those in tutorials i browse b4 installing vb :confused:


one more thing is vb OSE same as sun's vb?

---

### Post by kumoshk on 2009-06-06
What do you do when Samba doesn't work? It says it's unable to mount the share for some unknown reason.

(I'm using Ubuntu 32 within Ubuntu 64—both Jaunty.)

---

### Post by ushimitsudoki on 2009-06-06
You don't need Samba.

In VirtualBox, select the machine and then Settings > Shared Folders.

This will map folders from the host machine into the guest machine - they will show up in "My Computer". It will make perfect sense once you do it once.

Give it a go!

---

### Post by HermanAB on 2009-06-06
The easiest way to share files on a LAN is with good old FTP.  Install proftp or ssh-server on Linux and use Filezilla on Windows.

---

### Post by tacantara on 2009-06-06
> one more thing is vb OSE same as sun's vb?Sun makes both versions of VirtualBox.  The big difference (from my experiences with both) is that OSE is limited in available features (such as being able to move the mouse between the guest and the host without using the right CTRL key) and access to your machine's hardware (USB ports, etc.).  You can download the full version from Sun's website as a .deb package, so installation is fairly simple.

---

### Post by miki81 on 2010-06-02
> **ushimitsudoki said:**
> You don't need Samba.

In VirtualBox, select the machine and then Settings > Shared Folders.

This will map folders from the host machine into the guest machine - they will show up in "My Computer". It will make perfect sense once you do it once.

Give it a go!

Thanks a lot bro !
This is the easiest and the best way to share files. F*ck samba or lan folders, i have 8 gb per file .iso to share...

---

### Post by TheFu on 2010-06-02
> **tacantara said:**
> Sun makes both versions of VirtualBox.  The big difference (from my experiences with both) is that OSE is limited in available features (such as being able to move the mouse between the guest and the host without using the right CTRL key) and access to your machine's hardware (USB ports, etc.).  You can download the full version from Sun's website as a .deb package, so installation is fairly simple.

The only thing that I've noticed between the OSE and encumbered version is USB support. I just checked and the "Guest Additions" are released under a PUEL license. That means you can install them and use them in a company, but only if the end user does it and it isn't "IT policy".  

Ok, with that said, if you do install the OSE licensed server and the PUEL licensed "guest additions" then the mouse works seamlessly, you can have "direct access" to optical drive, graphics is much improved, and there appears to be a Direct3D option related to even better graphics support, I guess.

As to copying the files - I don't know of any reasonable way to push files from the host into the client OS without running an sftp, samba, file share, whatever.  

However, if you share part of the HostOS disks - "Shared Folders" on the VM settings tab, then the client OS can access any files easily with very high performance.  I treat the shared folders as local storage for both OSes and perform high disk IO work from client OSes daily. I haven't seen any issues with Ubuntu as the HostOS. I have seen problems with recursive access when Windows-whatever was the HostOS and Linux was the client.

---

### Post by espressobeanie on 2010-08-20
ushimitsudoki,

how do you do that? I install Guest Additions and I can't get any machine folders to mount.

---

### Post by Ginsu543 on 2010-08-22
You've revived a pretty old thread to get some answers to your current problem. To set up shared folders in VirtualBox, first click on the "Shared Folders" tab in Settings for the virtual machine you want. Add the folder/folders you want to share between VBox and Ubuntu. Once done, go ahead and boot up the VM. Once you're in Windows, go to "My Network Places." Double click "Entire Network." Double click "VirtualBox Shared Folders." You will see the folder(s) you just added (they will look something like \\VBOXSVR\Shared\). For most ease of use, right click on the folder(s) and select "Map Network Drive..." Assign an appropriate drive letter (D: or E: or whatever). Now, your shared folder will come up as a drive inside "My Computer" like your other drives.

---

### Post by johnaaronrose on 2011-01-24
I'm running Zentyal (a Ubuntu Server derivative) as a guest OS in Virtualbox. The host os is Ubuntu. I've got a shared folder set in Zentyal VM which is a folder within Ubuntu. How do I copy files from the Ubuntu VM to this folder? I can see the folder from the Shared Folders entry in the Virtualbox Devices menu. The Network entry in Ubuntu's Places menu shows a Windows Network but clicking on this gives 'Unable to mount location - Failed to retrieve shared list from server'. Clicking on Computer only gives floppy drive & file system - neither of which helps. I'd also like the facility of copying files from the Ubuntu Shared Folder to Zentyal.

---

