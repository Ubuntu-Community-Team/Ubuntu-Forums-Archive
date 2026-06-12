---
title: "Snow Leopard on Ubuntu in VirtualBox with an AMD machine"
date: 2011-04-20
forum: Virtualisation
---

### Post by BrianHaidet on 2011-04-20
I'm sorry if this has been covered somewhere; if it is, I can't find it.  

I had bought a Mac Mini in order to use xcode to develop for the iPod/iPhone but Apple pulled support for the sdk from Leopard, requiring Snow Leopard.  The really cheep computer I had bought cannot handle this new operating system, so I decided to turn to VirtualBox.  

I have read, and executed, multiple tutorials (with multiple ISOs and a DMG) for installing OSX onto an Ubuntu VirtualBox, but none of them have worked.  I think the issue may have to do with the fact that I have a 64 bit AMD machine, because I believe even some Hackintoshes need Intel.  

I am running 10.10 with VirtualBox 4.0.4 r70112
The images that do boot give me a "kernel panic" but I do not know what this is.  

If anyone has any ideas why it is not working, please offer suggestions.

Thanks

---

### Post by collisionystm on 2011-04-20
What .iso of osx are you using? I have made it work with iatkos and a few others.

---

### Post by collisionystm on 2011-04-20
KEEP IN MIND, it is very very very very slow. I had a i7 with 8gb of ram and the stupid thing was still molasses. I mean it wasn't slow slow, but it will annoy the living crap out of you.

---

### Post by BrianHaidet on 2011-04-20
I have tried a few:
Snow_Leopard_10.6.1-10.6.2_SSE2_SSE3_Intel_AMD_by_Hazard.iso
snowleopard_10a432_userdvd.dmg
snowleopard_10a432_userdvd.iso
OSX86_ModCD-031111-171757.iso

only the two hackintosh versions even tried to boot, but they got that kernel error.

---

### Post by collisionystm on 2011-04-20
Yeah you can only run an x86 version of osx. look for iatkos
 
It works. 
 
[http://www.kickasstorrents.com/iatkos-v7-dvd-10-5-7-for-intel-amd-t2718902.html](http://www.kickasstorrents.com/iatkos-v7-dvd-10-5-7-for-intel-amd-t2718902.html)

---

### Post by BrianHaidet on 2011-04-20
cool. thanks.

downloading it right now.

---

### Post by BrianHaidet on 2011-04-20
Oh, actually, I just noticed this is an image for Leopard, and I need Snow Leopard.  I looked for the same "brand" name with AMD attached and I could only find pages like this 
[http://www.btscene.eu/verified-search/torrent/iatkos+s3+snow+leopard+10+6+3+intel+amd/](http://www.btscene.eu/verified-search/torrent/iatkos+s3+snow+leopard+10+6+3+intel+amd/)
that have AMD in the title but not in the description.

---

### Post by BrianHaidet on 2011-04-21
Ok.  I downloaded the Snow Leopard version of iATKOS and even though it specified intel, it installed.  However, it generated annother kernel panic AFTER installing, when I pressed the "restart now" button that it makes you press.  

I just tried to restart, which re-installed OSX over the "existing" copy
I tried restarting with out the virtual DVD inserted, and it got stuck on the grey apple logo screen
Same grey-screen when I had the DVD attached but booted from HD first.

---

### Post by BrianHaidet on 2011-04-23
I found somewhere that said you could update a hackintosh to snow leopard, so I tried installing the iATKOS leopard and it didnt panic, but it did get stuck on the grey screen.

I feel like I am setting something wrong in Virtual Box...

any suggestions please?

---

### Post by Jinren on 2011-04-26
I know this doesn't answer your question directly, but have you seen this tutorial/method: [http://randosity.wordpress.com/2010/06/21/running-mac-os-x-in-virtualbox/](http://randosity.wordpress.com/2010/06/21/running-mac-os-x-in-virtualbox/)

I had no difficulty at all with this method, worked perfectly and easily.

Hope this is helpful.

---

### Post by BrianHaidet on 2011-04-29
no, I hadn't seen that.  Thanks!  Ill try it out after I fix my 11.4 display bug.....

---

### Post by BrianHaidet on 2011-05-29
Thanks!  The Nawcom disk worked pretty easily.  The only issue now is that my audio does not work.  The USB doesn't work either but I found somewhere that you need to reboot for the virtualbox expansion pack to enable so the USB will probably get better.

---

### Post by cariboo on 2011-05-30
It is against Apple's EULA to install OSX on anything but Apple branded hardware, THis thread is closed.

---

