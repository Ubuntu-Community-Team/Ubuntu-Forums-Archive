---
title: "Windows Hell(p!) - Changed a drive letter, now I'm stuck"
date: 2008-01-04
forum: Windows
---

### Post by giambrone on 2008-01-04
OK here goes...

Triplebooting Vista, Ubuntu and XP...

It was all working until I got rid of Ubuntu... GRUB errors, fixed that, and then (unrelated) Vista started bluescreening on boot (couldn't fix that). And so I used XP to transfer everything from Vista to the XP partition. Earlier today I thought "lets get rid of Vista if its not booting". It was on C:/ and XP was on D:/ (so I used Acronis to Change drive letters - bad move!). I've now tried to turn on XP - but to no avail. It seems to go to the blue login screen, but sticks with the flag. I can move the mouse around etc - the same happens in Safe Mode... Any bright ideas?

Its a long one, and this is the only forum I use.

Thanks in advance,

Matt :KS

---

### Post by giambrone on 2008-01-05
OK that was probably the longest Windows repair installation I've ever done. But all seems to be well.

In case anyone else wants to know what I did...

1) Grab your XP disc
2) Boot it
3) Go to install a fresh copy
4) It will ask you if you want to repair XP instead (do this)
5) Enjoy :-)

Still no Vista though... but I don't think I'll ever get that back :-(

---

### Post by giambrone on 2008-01-05
Okay... new problem along the same lines...

To be honest it was a really stupid idea to change the drive letter... Its just easier to remember that C:\ is \...

With the XP repair I've now got a problem with all the programs, and I'm at what seems to be a dead end. iTunes won't open, nor will any of the other programs I installed on the previous copy - to make things worse the uninstallers/reinstallers aren't working. I've got the "Windows Install Clean Up" utility, and uninstalled iTunes etc - but iTunes just brings up an error report. 

Basically I'm going to run as many Windows Updates as possible, and see where it gets me.

Oh how I wish drives didn't have letters!!

Matt:KS

---

### Post by ptaeck on 2008-04-12
Hi giambrone! you should check this now... but if it is not too late:KS

[[COLOR="Red"]**easy 3-step method how to change your vista system drive letter**[/COLOR]]("http://ubuntuforums.org/showthread.php?p=4704519#post4704519")

---

### Post by FSHero on 2008-10-18
Hello,

For some stupid reason (not your fault), the thread you linked to is read-only. Thus, I will post my thoughts here!

Very recently (i.e. beginning of this month: September 2008), I bought a Dell Inspiron 1525. I installed Kubuntu 8.04 to dual-boot with a fresh installation of Windows Vista. (This was trouble in itself trying to get around the MediaDirect-cum-selfdestruct button, but I've sorted it out now!)

I installed EXT2 IFS from [www.fs-driver.org](www.fs-driver.org) to access my ~190GB ext3 partition. Everything was working fine (could boot into both Vista and Kubuntu) until this morning...

Then, this morning, I installed about 7 updates for Windows Vista. After restarting, I got the same symptoms as post #11 on the page [http://ubuntuforums.org/showthread.php?t=414133&page=2](http://ubuntuforums.org/showthread.php?t=414133&page=2)
I.e in Vista, all I got was the screen "Preparing your desktop". I had to Ctrl-Alt-Del and start the task manager. Then I ran E:\windows\system32\regedt32.exe

From here, I did the editing of the registry key, and upon restarting, everything worked!!!

Now why might this have happened? I can think of a few candidate reasons:
1) Mediadirect button / partitions are playing up
2) EXT2 IFS from fs-driver.org somehow pushed out C: drive letter
3) Updates bricked the system

But why...? This is a very strange error: everything working fine one minute, then the next minute... BOOM! I think it was the updates.

Interestingly, if I ran "explorer.exe" from the safe mode, I could get to the start menu, but most programs (e.g. right-click My Computer --> Manage) would fail to load. Also, typing "subst c: E:\" in cmd.exe allowed me to get some functionality back. e.g. I could start Firefox (that I had installed prior to my system breaking).

I thought I'd share the above experience with people in case it helped :)

---

### Post by FSHero on 2008-10-18
Wow, I think I just discovered why my computer plays up funny. Just now, I restarted my Vista OS. It went to the Kubuntu GRUB menu, so I selected vista here. NOW it goes funny.

I shut the computer. I pressed the MediaDirect button (to which I assigned Vista using the Dell utility CD). Now Vista was OKAY.

I think this has something to do with my partitioning scheme:
1st primary: few MBs fat16 diagnostics partition
2nd primary: windows vista
3rd primary: Kubuntu 8.04
extended: data, /home for kubuntu, linux-swap

So... my power button is assigned to Kubuntu (i.e. boot from MBR of 3rd primary partition). My MediaDirect button is assigned to Vista (i.e. MBR of 2nd primary partition). Thus... when I press the power button (or restart the computer), BIOS passes control to 3rd primary partition. Kubuntu would work normally from here, but Windows Vista probably thinks that the 3rd primary partition is the C: drive.

When I press the MediaDirect button, vista thinks the 2nd primary partition is the C: drive, and I get the desired behaviour.

---

