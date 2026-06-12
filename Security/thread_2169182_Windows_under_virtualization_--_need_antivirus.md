---
title: "Windows under virtualization -- need antivirus?"
date: 2013-08-20
forum: Security
---

### Post by Tom_ZeCat on 2013-08-20
Gonna be upgrading my memory soon, from 4 GB to 8.  At that time I'm going to install VirtualBox and Windows 7 to run under it.  That way I can install some programs that either did not run well or at all in WINE.  Those are Final Draft 8 (a screenplay and stage play word processor) and Quicken 2012.  Those are the main ones.  I _might_ install some graphics programs -- Photoshop, PhotoImpact, and Paint Shop Pro.  Although I've found Gimp capable of doing quite a lot, I work as a photographer and have years of experience making things happen in PS, PI, and PSP.  

There really isn't that much else Windows-based that I'll need to run.  Treepad Business runs flawlessly under WINE after a few minor tinkers.  Even if it didn't, the Linux-based Cherry Tree is almost as good and is gaining ground on TPB every day.  

So, what I'm wondering about is if I need antivirus installed in Win 7 given what I'm doing.  I don't see the need to ever access the internet with a Windows browser ever again.  I have Firefox, Chrome, and Rekonq in Kubuntu.  That handles everything I want.  The idea of running one of those programs or Internet Explorer under WINE or VirtualBox is a real knee slapper.  In Firefox I'm using NoScript and Flashblock.  I whitelist sites that I know I can trust.  I'll only use Chrome or Rekonq occasionally.  

Can Windows-based programs running in Win 7 under Kubuntu/VirtualBox reach out to the Internet and direct a virus to my PC?  Or can a virus infiltrate via my Linux browsers into my Windows 7 install?  Or will this setup contain the risk so that I have no need for any antivirus program in Windows?  And if I don't need a Windows-based AV program, is there a way to make Windows shaddap and quit buggin' me to install one?

---

### Post by cariboo on 2013-08-20
Windows 7 checks for updates without any user intervention, so it will connect to the internet without you knowing about it. If you don't feel you need the updates, or anything else from the internet once you have installed everything you need, just disable the network connection, and you should be quite safe.

---

### Post by Tom_ZeCat on 2013-08-21
> **cariboo907 said:**
> Windows 7 checks for updates without any user intervention, so it will connect to the internet without you knowing about it. If you don't feel you need the updates, or anything else from the internet once you have installed everything you need, just disable the network connection, and you should be quite safe.

Thanks for the help.  I'm gonna do it that way then.  I think Windows also has a way to shut off the nagging to install an antivirus.  Gonna look for that.

---

### Post by slw210 on 2013-08-21
You can set Windows 7 to manual updates only.

"Control Panel\System and Security\Action Center\Change Action Center settings" should allow the turning off of the popup.

---

### Post by Buntu Bunny on 2013-08-23
> **cariboo907 said:**
> Windows 7 checks for updates without any user intervention, so it will connect to the internet without you knowing about it.

That was one of the reasons I disliked Windows. Then it would hog resources so that I had to abandon my computer for awhile after boot, until Windows was done doing it's thing.

> **slw210 said:**
> You can set Windows 7 to manual updates only.

"Control Panel\System and Security\Action Center\Change Action Center settings" should allow the turning off of the popup.

And then it pesters you, and pesters you, and pesters you ......

Have I mentioned lately that I love Ubuntu?

---

### Post by startas on 2013-08-24
Yeah, better buy a book "windows 7 for dummies" :D And its not a joke, there is the whole series of that kind of books for many things, os/programs, so if you lack knowledge about windows and you want to use it, just buy/download that book :) [http://www.amazon.com/Windows-For-Dummies-Book-Bundle/dp/0470523980](http://www.amazon.com/Windows-For-Dummies-Book-Bundle/dp/0470523980)

---

### Post by sheffrem on 2013-08-25
you surely need an antivirus has windows connect to the internet even if it is run as a virtual machine though making virus intrusion very possible

---

### Post by Tom_ZeCat on 2013-08-25
> **sheffrem said:**
> you surely need an antivirus has windows connect to the internet even if it is run as a virtual machine though making virus intrusion very possible

That's what I figured.  I think I'll use the firewall to block any Windows app from accessing the Internet unless there's an extremely good reason for it to do so.  Then I'm only running Windows if I really need the Windows app.  Much of the time I can do everything I need with Kubuntu and Linux apps only.  

And to the person who was frustrated by Windows' interruptions, I feel your pain.  I had to use Windows HDMIed to my TV to watch a fav TV show recently.  As soon as the show started to get good, I was greeted by the following window:  

[IMG]http://img534.imageshack.us/img534/9585/ogmm.jpg[/IMG]

I'm enjoying working in Kubuntu without being constantly pestered.  (Granted, the above popup is more Mozilla's responsibility than Microsoft's, but you get the idea.)

---

### Post by Kevin_Arnold on 2013-08-26
You really don't need anti-virus software on Win 7 if you're not going to be doing stupid stuff in Internet Explorer.  Getting updates from Microsoft is a good idea and won't open you up to a virus.  

I know it is fun to trash Microsoft but it really isn't an issue.  If you are worried, just install Microsoft Security Essentials... It is free and isn't a resource hog. I know Win 8 just had it by default, don't remember about 7 though.

---

### Post by coldraven on 2013-08-26
After installing and updating just switch off the network interface in Virtualbox. Windows will be completely isolated from the internet.
It is almost certainly impossible for a virus to jump from the Linux host to the virtual guest.
I do however suggest removing any Java plug-ins from Firefox. You can test if you have any here:
[http://www.java.com/en/download/testjava.jsp](http://www.java.com/en/download/testjava.jsp)

---

