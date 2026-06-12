---
title: "Moving my VirtualBox XP Machine to Ubuntu 10.1.."
date: 2010-04-28
forum: Virtualisation
---

### Post by RazorV on 2010-04-28
Hey everyone,  I searched but really couldn't find anything so please excuse me if this has been covered - maybe someone can point me in the right direction.

Tomorrow when 10.04 is released I want to do a fresh Install of Ubuntu on my machine.  That's not a problem.  But I am also going to have to move my VirtualBox running XP to the new install.  

I know that in the /home/{username}/.VirtualBox there are two folders:
HARDDISKS
MACHINES

Can I just move the contents of these folders to a fresh install of VB on Ubuntu 10.04 and have VB run it just as it was on my old Install?

Thanks to all that can reply.  I really appreciate the help.

Greg

---

### Post by TheFu on 2010-04-29
I've only used VirtualBox on Windows Hosts, but with a little searching, you can find all sorts of step-by-step guides to migrate VMs between VirtualBox hosts. [http://jdpfu.com:82/2008/09/02/how-to-clone-a-virtualbox-domu](http://jdpfu.com:82/2008/09/02/how-to-clone-a-virtualbox-domu) is one.

With v3.x of virtualbox, there is an export/import command that may be easier. I have used it to successfully migrate from VirtualBox to KVM VM hosts, but only with non-Microsoft operating systems.

---

### Post by Cheesemill on 2010-04-29
Just make a backup of the entire .VirtualBox folder and restore it into the new installation.

---

### Post by B00R4dL3y on 2010-04-29
> **Cheesemill said:**
> Just make a backup of the entire .VirtualBox folder and restore it into the new installation.

+1 This always works for me.

---

### Post by RazorV on 2010-04-29
thanks so much for all the replies.  I will do an export and copy the .virtualbox directory to my external harddrive.


Hope it works and thanks again.

---

### Post by Gipsy25 on 2010-05-30
Question. If by any chance I forgot to copy .virtualbox folder but I have the virtual drives in a different partition, is there anyway to use those disks or I have to create the machines again ???? 

I copied the machines and forgot to copy everything else ... now i have 5 machines 10gb each and I cant use them, It wont let me import them.

Any help will be appreciated !!!

Regards !!!

---

### Post by JKyleOKC on 2010-05-31
You can use the drives but will have to re-create the machines themselves. Make them as nearly as possible the same as the old ones were, and then when the new-machine wizard asks you whether to create a new drive or use an existing drive, tell it to use an existing drive and select from the ones you have.

Since you have them in a different partition, you may need to run the Virtual Media Manager first; you can find this under the File menu of the VirtualBox program. When the VMM starts it will show you a window listing all the virtual drives of which VBox is aware; it will probably be empty the first time you open it. Click the Add button, select "Computer" as the source, and navigate to the location of your saved drives. Highlight each in turn and add it to the VMM list.

Once you've done that, they will show up in the new machine wizard when you tell it to use an existing drive, and you can pick from that list.

You don't even have to move the drives back into your ~/.VirtualBox directory; the program can find them anywhere on your system. However you may have to adjust the permissions on them for everything to work right...

---

