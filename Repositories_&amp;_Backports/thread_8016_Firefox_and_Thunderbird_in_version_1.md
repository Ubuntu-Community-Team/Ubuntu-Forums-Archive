---
title: "Firefox and Thunderbird in version 1"
date: 2004-12-13
forum: Repositories &amp; Backports
---

### Post by s001505 on 2004-12-13
Is it possible to install Firefox 1.0 and Thunderbird 1.0 through the apt system?

Regards 
Rune.

---

### Post by lockenkeyster on 2004-12-13
[QUOTE=s001505]Is it possible to install Firefox 1.0 and Thunderbird 1.0 through the apt system?

Regards 
Rune.[/QUOTE]

If you want to make the jump to Hoary, Firefox is already at 1.0 there, but Thunderbird is still back at 0.9...

Otherwise, you have to change to debian (sid?) sources to get them and then switch back, but I think that this type of mixing is generally not recommended.

Personally, I haven't noticed any huge changes between 0.9 and 1.0 for either of them, so you might be better off waiting for the Hoary release!

---

### Post by mage.merlyn on 2004-12-13
Hi, I did a search for Ubuntu backports, (google of course), and found the following link  [http://ubuntu-bp.sourceforge.net/]("http://ubuntu-bp.sourceforge.net/")
   
   Or as per the instructions on the page add the following to /etc/apt/sources.list.
   
   deb [http://ubuntu-bp.sourceforge.net/ubuntu](http://ubuntu-bp.sourceforge.net/ubuntu) warty-backports main universe
   
   Firefox 1.0-2 is there, but no Thunderbird, at least the last time I checked.
   
   Hope this helps.

---

### Post by jdong on 2004-12-13
[QUOTE=mage.merlyn]Hi, I did a search for Ubuntu backports, (google of course), and found the following link  [http://ubuntu-bp.sourceforge.net/]("http://ubuntu-bp.sourceforge.net/")
   
   Or as per the instructions on the page add the following to /etc/apt/sources.list.
   
   deb [http://ubuntu-bp.sourceforge.net/ubuntu](http://ubuntu-bp.sourceforge.net/ubuntu) warty-backports main universe
   
   Firefox 1.0-2 is there, but no Thunderbird, at least the last time I checked.
   
   Hope this helps.[/QUOTE]

Yes, I backported Firefox 1.0  to Warty, because it's already been tested quite a bit!

Neither debian nor Ubuntu have released packages of ANY SORT for Thunderbird 1.0 -- as soon as they do, I'll build backports for Thunderbird 1.0.

---

### Post by mattisking on 2004-12-18
[QUOTE=jdong]Yes, I backported Firefox 1.0  to Warty, because it's already been tested quite a bit!

Neither debian nor Ubuntu have released packages of ANY SORT for Thunderbird 1.0 -- as soon as they do, I'll build backports for Thunderbird 1.0.[/QUOTE]
 This is certainly not something I'd call a guaranteed thing. However, just being curious I simply tried the following (with success):
1) Using Hoary I installed Thunderbird 0.9 which is all that's currently available as others here have said.
2) I went to the Mozilla Thunderbird site and pulled down the Linux package which does not currently contain an installer (or build options).
3) After extracting the files I did a comparison between ~/thunderbird (after extraction) and /usr/lib/mozilla-thunderbird and what do you know... nearly a perfect match with the only exception being there appears to be a couple of additional files in 0.9 probably either bundled with 0.9 package or possibly generated as I've been using Thunderbird for a couple weeks now on Ubuntu. 
4) So, I simply copied these new files directly over the ones installed in /usr/lib/mozilla-thunderbird/. 
5) Once I verified I had copied all the files into place in their respective folders I deleted the downloaded/extracted thunderbird folder and went up and hit my Thunderbird icon and 1.0 loaded right up without any problems at all.

This is SO not the proper way to do things... but it worked for me.

---

### Post by jdong on 2004-12-18
It'll work, but problems can haunt you later -- especially when upgrading to the 'real' Thunderbird 1.0 from Hoary/Sid, since there _ARE_ many debian-specific patches applied -- see the .diff.gz!


If I get impatient, I'll try to force the 0.9.6 diff onto 1.0. But only if I get REALLY impatient.

---

### Post by castrojo on 2004-12-18
The debian tbird maintainer has a preview repository [here](http://www.jwsdot.com/debian/) that you could base a package off of.

---

### Post by ThePrawn on 2004-12-18
I just left the default firebird/thunderbird apps alone, to avoid being "haunted later" . . . downloaded the latest of each and put them in /usr/local/ -- created the necessary links, and vuala -- tbird and ffox are still there, but neither used nor in the way.

---

### Post by jdong on 2004-12-18
Ok, I built a backport for Thunderbird 1.0, based on the 0.9-6 patch that was in Hoary. (there were some ubuntu-specific patches in Hoary, which I didn't want to leave out!). It's uploaded to the staging area for now.


BTW, we have a backports forum! Yay!

---

### Post by HiddenWolf on 2004-12-25
[QUOTE=jdong]Yes, I backported Firefox 1.0  to Warty, because it's already been tested quite a bit!

Neither debian nor Ubuntu have released packages of ANY SORT for Thunderbird 1.0 -- as soon as they do, I'll build backports for Thunderbird 1.0.[/QUOTE]

It's the only thing I miss from running my hoary setup. FF 1.0 
TD 1.0 would be great. go go go.

---

