---
title: "Why is there an old version of VirtualBox OSE in Ubuntu repository?"
date: 2008-10-10
forum: Virtualisation
---

### Post by abcuser on 2008-10-10
Hi,
in Ubuntu 8.04 in synaptic I have searched for "virtualbox" string and I see there is VirtualBox OSE version 1.5.6 in Ubuntu repository. This version is from February 2008. But there was series of 1.6 and now 2.0 released.

Why is there no newer version of VirtualBox OSE in Ubuntu repository?
But PLE
Regards,
Abcuser

---

### Post by DJ_Peng on 2008-10-10
[Feature Freeze]("https://wiki.ubuntu.com/FeatureFreeze") for new versions of Ubuntu come a couple of months before the release date. The features for Hardy, including which versions of programs will be available, were frozen on [14 February]("https://wiki.ubuntu.com/HardyReleaseSchedule"). The good news is that [version 2.0.2 is proposed for Intrepid]("http://packages.ubuntu.com/intrepid/misc/virtualbox-ose"), so we should be all caught up on the 30th of this month.

---

### Post by tuxxy on 2008-10-10
for now you could download 2.0.2 PUEL version from [here]("http://www.virtualbox.org/wiki/Downloads")

---

### Post by caver1 on 2008-10-10
if you reload in Synaptic you will see that VBox 2 is in there for Hardy.
Just upped mine and works fine.
Hardy64
caver1

---

### Post by abcuser on 2008-10-10
@tuxxy, I know I can install PUEL version, but I would like to have OSE version.

@caver1, I have click on Reload button in Synaptic and after reload I have search for virtualbox and still got 1.5.6 version. Can you please provide more info how did you get 2.0.2 in hardy? I hope you didn't mess up module numbers like 2.6.24-16 etc which are Linux kernel numbers and not VirtualBox versions.

---

### Post by caver1 on 2008-10-10
You say your Synaptic only shows 1.5?  My Synaptic shows 1.6 which I was running and 2. right under that. Hardy64bit.
Tuxxy is right the link tuxxy gave you is for the binaries which is the PUEL version. 
Then if you add the repository from that page to yours then it will alwys update the PUEL version.
I forgot that I had added their repository.
Works great and loads much faster.   [http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)
caver1

---

### Post by abcuser on 2008-10-11
@caver1, you are right. If I add repository from web page: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) I can see 1.6.6 and 2.0.2 versions, but both of them are PUEL licenses.

Thanks for help, but you are missing my point. I am talking about OSE (open source edition) version not PUEL version. It looks like if I want to have the latest version of OSE version I must compile it myself.

I have found out the how-to: [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)
but there is also this interesting info about PUEL version:
"While this is non-free and only for personal use, it adds USB support and virtual Remote Desktop support. Without this, your USB devices can't be used in the guest OS and you cannot use Windows Remote Desktop as a server in the guest OS."

I thought OSE and PUEL versions is the same code, but as I see PUEL adds some features like Remote Desktop which is what I am looking for. It looks like I will have to install PUEL version anyway.

---

