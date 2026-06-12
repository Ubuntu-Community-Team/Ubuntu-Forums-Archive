---
title: "Access a second (data) partition within virtualbox?"
date: 2008-07-19
forum: Virtualisation
---

### Post by pmac7 on 2008-07-19
Hi!

I've gotten too attached to MS Office 2007 (especially Outlook, OneNote, and Access which don't work in WINE) to part with it completely, but I've fallen for Ubuntu's interface.  

So I guess my first question is what is the best way to use these programs in Ubuntu?  (While I appreciate OOo, it does not have some of the features of MS Office 2007 that I use regularly)

I have installed VirtualBox (via [http://ubuntuforums.org/showthread.php?t=769883](http://ubuntuforums.org/showthread.php?t=769883) ) in an attempt to solve this problem.  However, I have run into another problem. ](*,) I have 3 partitions on my machine: XP Pro SP3, Data ('My Documents' folder), and Ubuntu Hardy Heron.  I want to access the files in my Data partition from the virtualized XP, but it doesn't recognize the partition.  How can I access the second partition from within VirtualBox?

Thanks in advance for you help!

---

### Post by squaregoldfish on 2008-07-20
I have to say I'd vote for VirtualBox as the way forward for running Windows apps under Linux, as long as you've got the RAM to run both operating systems at once.

As for your Data partition, is it mounted under Linux? If so, the easiest way is to set up a Shared Folder on your virtual machine, pointing to the directory where the partition is mounted. It will then turn up as a separate drive in Windows.

HTH,
Steve.

---

### Post by pmac7 on 2008-07-20
Ok- how would I go about doing that?  I appreciate your help Steve!

---

### Post by squaregoldfish on 2008-07-20
You should be able to figure this out without too much trouble. However, I'll let you off on this occasion ;)

In the main VirtualBox window, select the Windows VM. Towards the bottom of the Details tab on the right hand side, there's an entry name Shared Folders - click it to open the settings window.

Click the little icon that's a folder with a + sign. Select the folder you want to share, and give it a suitable name. Click OK.

When you start the Windows VM, you should have a new network drive that's linked directly to that folder.

Steve.

---

### Post by pmac7 on 2008-07-21
thanks :)

---

### Post by Ghuloomo on 2008-07-29
I have installed Vbox 1.5.6 and added my partions and some folders to the shared folders, but i'm having troubing accessing them now. HOW? :D
will they be in My Computer? coz nothing appeard..

---

### Post by squaregoldfish on 2008-07-30
The shared folders don't turn up automatically. You have to mount them as network drives. So if you had a shared folder called 'data', you mount it using this network path:

```
\\vboxsvr\data
```

It's best to map a network drive to a drive letter and set it to reconnect.

Steve.

---

