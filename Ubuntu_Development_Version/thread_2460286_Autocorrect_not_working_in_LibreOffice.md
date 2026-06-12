---
title: "Autocorrect not working in LibreOffice"
date: 2021-04-06
forum: Ubuntu Development Version
---

### Post by sgage on 2021-04-06
Hi All,

There seems to be a problem with autocorrect in LibreOffice in Hirsute/MATE. There is no auto-capitalization of first words in a sentence, and the replacement table is not being implemented. 

This exact issue came up in Fedora 34 prerelease back in February, and just resolved itself with a system update. We were never able to figure out what package fixed it, but it wasn't an update to LO.

It is NOT a bug in LO, or at most, it's an interaction between LO and some 'plumbing'. It's some system component that is causing this. I was away from Hirsute for almost 2 weeks, and when I logged in today, got 200 and something updates, so hard to say what is responsible.

Anyone have any idea what's going on?

---

### Post by dino99 on 2021-04-06
Let devs know about that issue: report against LO both on launchpad and upstream.
Lo is not perfect; myself on gnome, when i try to select rows & columns on calc, i often lost the first part before ending the selection.

---

### Post by sgage on 2021-04-06
> **dino99 said:**
> Let devs know about that issue: report against LO both on launchpad and upstream.
Lo is not perfect; myself on gnome, when i try to select rows & columns on calc, i often lost the first part before ending the selection.

I really don't think it's a problem with LO. I reinstalled an older version that worked perfectly 2 weeks ago, and it has the same problem. In my Fedora experience, it resolved itself in a system update one fine day when there was no LO update. It's some system component that LO uses, and I wish I knew what it was.

---

### Post by dino99 on 2021-04-06
Do you get some helpfull warnings/errors from 'journalctl -b' ?

By the way if no one blame Lo, devs will not pay attention; if Lo is not the right package, they will switch to the related package.

---

### Post by zerubbabel on 2021-04-21
Yes, I just installed 21.04 and am experiencing the same problem -- auto-correct doesn't work, but it was working fine yesterday in 20.04, with the same LibreOffice version and profile.

---

### Post by sgage on 2021-04-22
I think it has something to do with the GTK stack - the problem does not exist in Kubuntu 21.04. The same issue occurred in Fedora Workstation, which is Gnome, a month or so ago, and after a couple of weeks was fixed. Once a lot of MATE people update to Hirsute, perhaps it will be properly addressed.

---

### Post by Yellow Pasque on 2021-04-22
[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1925379](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1925379)

---

### Post by sgage on 2021-04-22
Thanks for the link - I have added a "me too" comment with a bit more info.

---

### Post by ajgreeny on 2021-04-22
I am running Xubuntu 21.04 as a VM in KVM/QEMU and have the same problem - almost.

If I type 1/2 it does not automatically change to ½ unless I highlight it in the text then go to Tools -> Autocorrect -> Apply when the change occurs.
However, if I try to repeat that with a second typing of 1/2, highlight it, and again go through the Tools -> Autocorrect -> Apply, nothing happens.
Once and only once it happens, not automatically as it does in Xubuntu 20.04 with the same LO version 7.1.2.2.

I have added myself to the bug; we'll see how many more have the problem.
Hopefully it will get solved as it is a nuisance to have to go through the character-map to get ½ to appear when it's needed.

---

### Post by Hagar Delest on 2021-04-24
Personally, I use the VCL=gen plugin (x11) and it works fine (LO 7.1.2.2 on Xubuntu Hirsute).

---

### Post by ajgreeny on 2021-04-24
> **Hagar Delest said:**
> Personally, I use the VCL=gen plugin (x11) and it works fine (LO 7.1.2.2 on Xubuntu Hirsute).
Please explain more about this.
I have searched and come up with nothing about LO Autocorrect so I don't have a clue what you mean.

---

### Post by ajgreeny on 2021-04-24
As is mentioned in post 7 of the bug I have also found that autocorrect works if a tab is used instead of a space.
You can then backspace and replace the tab with a space which at least removes any need to go through the palaver of character-map to get, for example, fractions to show.

---

### Post by Hagar Delest on 2021-04-25
Try to launch from terminal: SAL_USE_VCLPLUGIN=gen soffice
It will use the x11 plugin instead of the gtk3. It will look different but all should work fine.

---

### Post by sgage on 2021-04-25
> **Hagar Delest said:**
> Try to launch from terminal: SAL_USE_VCLPLUGIN=gen soffice
It will use the x11 plugin instead of the gtk3. It will look different but all should work fine.

Hey, that works! Menu/Toolbar/StatusBar text doesn't take on the DE-customized fonts, but the main editing area is fine. Until the fixed GTK+3.0 reaches the repo, this is a decent workaround. Thanks for posting how to do it. I have to admit, I'd never heard of SAL_USE_VCLPLUGIN before...

---

### Post by Yellow Pasque on 2021-04-25
> **sgage said:**
> I have to admit, I'd never heard of SAL_USE_VCLPLUGIN before...

Probably because LO autodetects what desktop you're using and that works 99.9% of the time.

---

### Post by Hagar Delest on 2021-04-25
Indeed. The issue with the autocorrect feature is a new one I think. In the past, it was mostly a rendering issue.
See also this discussion: [https://ask.libreoffice.org/en/question/235915/why-did-the-icons-disappear-in-the-menus-of-version-64/](https://ask.libreoffice.org/en/question/235915/why-did-the-icons-disappear-in-the-menus-of-version-64/)
I prefer the x11 setting in fact, mostly because of the visual consistency of the menus (alignment of the icons).

I've tweaked the soffice script in /usr/lib/libreoffice/program so that even when launched from external applications (attachment of a mail, a download...) LO starts with the x11 plugin.

---

### Post by ajgreeny on 2021-04-25
I started by trying that ***SAL_USE_VCLPLUGIN=gen soffice*** command in terminal in my Xubuntu 20.04  then in 21.04 as well, but the size of everything, text, icons, scrollbars etc was so tiny as to be useless in either version of the Distro, so I'm afraid that will not be of use to me unless there is a way to change the zoom of the desktop which is no longer using gtk-3.

I'm not totally sure, and it is not easy to confirm this, but it seemed to me that the LO window appeared much faster than it normally does when first started in a session; has anyone else noticed this, and might that also occur because the system is not using gtk-3.

---

### Post by Hagar Delest on 2021-04-25
Weird, in the screenshots I've provided on the AskLO site, there is a difference but not that big.

---

### Post by sgage on 2021-04-25
> **Hagar Delest said:**
> Weird, in the screenshots I've provided on the AskLO site, there is a difference but not that big.

I think the size difference might depend on if you increased your font sizes or display scaling in your GTK theme. I have an eye problem that requires me to do both, and when I launch LO with that command I find the menus/toolbars/etc. to be quite small. I can still use the controls and such, but it is suboptimal. Hope they fix it soon!

---

### Post by ajgreeny on 2021-04-25
No. I've made no changes made to my scaling or font sizes.

I will show two scrsenshots tomorrow when able to of the differences between the default and the VCLPLUGIN screens.
My guess is that the plugin text size is about 40% of the default and approx the same difference for icons and scrollbar, etc etc.

---

### Post by ajgreeny on 2021-04-26
As promised here are the two screenshots (both the same size in pixels) of the LO Writer screen, one with command soffice, the second with the vclplugin, which I hope shows the big difference in font, icon and all other GUI sizes.

---

### Post by sgage on 2021-04-26
> **ajgreeny said:**
> As promised here are the two screenshots (both the same size in pixels) of the LO Writer screen, one with command soffice, the second with the vclplugin, which I hope shows the big difference in font, icon and all other GUI sizes.

Yes, I saw the same thing - I just attributed to the fact that I have my UI elements scaled up. In any case, it should be fixed soon. There's a PPA with the fixed GTK+3.0, and it works fine here. See

 [https://launchpad.net/~dtl131/+archive/ubuntu/mediahacks2](https://launchpad.net/~dtl131/+archive/ubuntu/mediahacks2)

for details.

---

### Post by Yellow Pasque on 2021-04-26
> **sgage said:**
> Yes, I saw the same thing - I just attributed to the fact that I have my UI elements scaled up. In any case, it should be fixed soon. There's a PPA with the fixed GTK+3.0, and it works fine here.

Ah, I'm glad it worked for you. I hope things are looking better. Have you noticed any issues with other GTK apps in your system?

---

### Post by ajgreeny on 2021-04-26
> **Yellow Pasque said:**
> Ah, I'm glad it worked for you. I hope things are looking better. Have you noticed any issues with other GTK apps in your system?
I have not seen any problems with any other GTK (or other GUI library) applications in 21.04 so far, though truth to say, I do not use it very much; my daily OS is still 20.04 and like many users I run LTS versions only for my main OS, and the intermediate versions I run as VMs only using KVM/QEMU just to see how they are going.

---

### Post by Yellow Pasque on 2021-04-26
I'll admit that I don't know a whole lot about code these days. (Computer science classes were many years and many, many, many, beers ago.) So I don't know a good way to test it. Hopefully, Sebastian Bacher will be able to cobble it all together. He's a rockstar. :guitar:

---

### Post by sgage on 2021-04-26
> **Yellow Pasque said:**
> Ah, I'm glad it worked for you. I hope things are looking better. Have you noticed any issues with other GTK apps in your system?

So far, so good - no 'unintended consequences' in other GTK stuff. I will let you know if anything crops up...

---

### Post by sgage on 2021-04-28
Looks like help is on the way (from the bug report on launchpad):

 ```
Sebastien Bacher (seb128) 16 hours ago
Changed in gtk+3.0 (Ubuntu):
status: 	Confirmed &#8594; In Progress
importance: 	Low &#8594; High
```

---

