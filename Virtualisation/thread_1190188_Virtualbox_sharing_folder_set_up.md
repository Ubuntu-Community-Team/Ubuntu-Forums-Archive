---
title: "Virtualbox sharing folder set up"
date: 2009-06-17
forum: Virtualisation
---

### Post by myotis on 2009-06-17
I have WindowsXP running in VirtualBox on Ubuntu 9.04. I want Windows to have access to my Dropbox directory in my Ubuntu home directory. 

Looking at the Ubuntu help for Virtualbox it seems that I need to run this in terminal.

VBoxManage sharedfolder add "WindowsXP" -name "LinuxDropBox" -hostpath /home/graham/Dropbox

Where WindowsXP is the name of my Virtual Machine, LinuxDropBox is the name I want to appear in Windows as a share, and /home/graham/Dropbox, the name and location of the existing Dropbox directory.

Then I need to run 

net use x: \\vboxsvr\share

in the run command line in Windows

Does this all seem OK, or am I going to do something stupid.

Many thanks,

Graham

---

### Post by jbrown96 on 2009-06-17
That looks fine, although there are GUIs to set it up. I've used the Virtualbox manager to set up the share, and then went into the network settings in XP and created a new shared folder, which is nice because you can browse. Sometimes it's a little fussy and doesn't want to find the shares, so it's nice to have something to browse for it. 

I'm not sure what you're sharing, but the data transfer rate is pretty bad. I tried to use a shared folder for my music (stupid iphone needs itunes), and it just didn't really work. It was way too slow. So keep in mind that it won't be anywhere near as fast as your hard drive because it's doing the following

hard drive >>>> OS >>>> samba server >>>> samba client >>>> OS
|----------Ubuntu---------------------|    |---------Windows--|

---

### Post by Stefanie on 2009-06-17
yes it's easier with the GUI, I did it that way as well. 
Maybe you know this, but I think you have to install guest additions in windows xp if you want shared folders.

---

### Post by myotis on 2009-06-17
That's great, I just assumed it would need to done with the command line. Now all set up, and being through Samba it seems that the ext3 file system isn't an issue.

I am hoping its fast enough for what I need. I have a few statistics and GIS programs that are  Windows only. And I also need to edit occasional Word files with complex layouts which OO.org destroys.

Thanks for your help.

Graham

---

### Post by myotis on 2009-06-17
> **Stefanie said:**
> yes it's easier with the GUI, I did it that way as well. 
Maybe you know this, but I think you have to install guest additions in windows xp if you want shared folders.

Thanks, yes you do need the guest additions, but I had figured that bit out :-)

Graham

---

### Post by bodhi.zazen on 2009-06-17
> **Stefanie said:**
> yes it's easier with the GUI.

IMO it is easier to use a Samba server (rather then shared folders).

---

