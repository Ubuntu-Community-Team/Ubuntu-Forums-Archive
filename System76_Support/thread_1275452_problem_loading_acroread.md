---
title: "problem loading acroread"
date: 2009-09-25
forum: System76 Support
---

### Post by Eyore15 on 2009-09-25
I'm trying to install acroread on my new Starling using the recommendations at [www.knowledge76.com](www.knowledge76.com)

I began by following these directions:

Any Ubuntu Release

    * Click Applications &#8594; Add/Remove. In the top right, change the setting to All available applications. Select Other in the left panel and then select the Ubuntu restricted extras package. Click Apply Changes.
    * Open your terminal (Applications > Accessories > Terminal) then copy and paste the following commands into the terminal window. Enter your user password when prompted. 

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list  --output-document=/etc/apt/sources.list.d/medibuntu.list

sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update


I then issue the command:

sudo apt-get install acroread

and after entering my password, i receive the following message

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package acroread has no installation candidate

Does anyone have an idea of what is going on here?  More importantly,how to solve it?

tnx

mark miller

---

### Post by drs305 on 2009-09-25
Acroread is no longer in the Medibuntu repositories or currently in the (EDIT: Karmic 64-bit) partner repositories. You can download it from this site, which has a deb file:
[http://get.adobe.com/reader/otherversions/]("http://get.adobe.com/reader/otherversions/")

Once you have downloaded it to your desktop, doubleclick on it and it should install.

---

### Post by HotShotDJ on 2009-09-25
> **drs305 said:**
> Acroread is no longer in the Medibuntu repositories or currently in the partner repositories.I'm quite sure that this is not true.  I have Acroread installed and I did it from a repository... but I'm not sure which one.  Let me do some digging before you try to download it separately...  I'll update this post in a few moments.

Ok, drs305 is correct.  Acroread is not in Medibuntu or in the standard partner repository.  It can be found in archive.canonical.com (see my post below).

---

### Post by drs305 on 2009-09-25
> **HotShotDJ said:**
> I'm quite sure that this is not true.  I have Acroread installed and I did it from a repository... but I'm not sure which one.  Let me do some digging before you try to download it separately...  I'll update this post in a few moments.

It was in the repositories but has been removed from Medibuntu - at least the latest releases (Jaunty/Karmic). All that is retained are the acroread fonts.
[http://packages.medibuntu.org/]("http://packages.medibuntu.org/")

HotShotDJ, I hope you can find a repository because many users have asked lately.

Added: For general knowledge - you can find out which repository a package came from in Synaptic by typing the package name in the Quick Search box (upper right). Then in the lower left pane select "Origin" and in the upper left pane scroll through each section. When the correct repository is found, the package will appear in the right pane.

---

### Post by HotShotDJ on 2009-09-25
> **drs305 said:**
> It was in the repositories but has been removed from Medibuntu - at least the latest releases (Jaunty/Karmic). All that is retained are the acroread fonts.Yes.  That is right.  It is no longer in Medibuntu.  I just checked my system, it is now in archive.canonical.com/ubuntu jaunty partner.  You should be able to find them under the Third Party Tab in Software Sources.  They are disabled by default, but all you need to do check them off (I have the Source Code one checked off, although I don't think that is necessary), *et Voilà*!  Acroread version 9.1.3-1jaunty1 will be found in Synaptic Manager.

---

### Post by drs305 on 2009-09-25
HotShotDJ,

Thanks for checking. I visited the canonical partner site and the only place it is missing is in the Karmic 64-bit partner section, which is still completely empty. It's in Jaunty's 64-bit partner repository so hopefully it will make it into the Karmic beta or soon thereafter.

---

### Post by HotShotDJ on 2009-09-25
> **drs305 said:**
> It's in Jaunty's 64-bit partner repository so hopefully it will make it into the Karmic beta or soon thereafter.I hope so too!  Even more, I hope that they quit moving it around.  It really doesn't matter where it lands, as long as it stays put -- it really is frustrating to keep having to figure out where to find it every other release.

---

