---
title: "Songbird bypasses DansGaurdian"
date: 2007-06-01
forum: Ubuntu Christian Edition
---

### Post by TravMan63 on 2007-06-01
Has anyone else tried using Songbird... 

and noticed that it bypasses the filtering software?

I've just been running CE from live cd and haven't been able to fully check this out, but I'm guessing
it's possible to have Songbird be subject to the filtering as well.


TM
--
other notes - Installed Ubuntu 5.1 on our Church's notebook.  Installed Fluxbox as WM, unfortunately video output wouldn't work...

Great to see a CE version!
-----
Plans:
Install Ubuntu CE with XFCE on Church Youth PC (INSTALLED 2007-06-06)
Install on kids laptops...

---

### Post by mhancoc7 on 2007-06-01
> **TravMan63 said:**
> Has anyone else tried using Songbird... 

and noticed that it bypasses the filtering software?

I've just been running CE from live cd and haven't been able to fully check this out, but I'm guessing
it's possible to have Songbird be subject to the filtering as well.


TM
--
other notes - Installed Ubuntu 5.1 on our Church's notebook.  Installed Fluxbox as WM, unfortunately video output wouldn't work...

Great to see a CE version!
-----
Plans:
Install Ubuntu CE with XFCE on Church Youth PC
Install on kids laptops...

It should not be bypassing it in the latest release. (v3.2). There was a bug in v3.0 that would have allowed this, but should br fixed now. Please let me know which version you are using.

Thanks, Jereme

---

### Post by TravMan63 on 2007-06-01
> It should not be bypassing it in the latest release. (v3.2).

Where do I find the version #?

I have a feeling I have an older version (7.04)
TM

---

### Post by mhancoc7 on 2007-06-01
> **TravMan63 said:**
> Where do I find the version #?

I have a feeling I have an older version (7.04)
TM

Open the Dansguardian GUI and tell me what version it is.

Jereme

---

### Post by TravMan63 on 2007-06-04
Is this the Parental Controls window?  That is v1.6.

I did not find any update in the add/remove applications window. (I did a search for guardian and dansguardian - with all available applications selected)

TM

---

### Post by antoniuk on 2007-06-04
2 things

first, you can find the version of Dansguardian by going into synaptics package manger and sleecting installed and scrolling to it.

Second, how can there be 3.2? 2.8 is the latest stabel avaiable with aptitude and 2.9 is the latest beta

---

### Post by mhancoc7 on 2007-06-04
> **TravMan63 said:**
> Is this the Parental Controls window?  That is v1.6.

I did not find any update in the add/remove applications window. (I did a search for guardian and dansguardian - with all available applications selected)

TM

Yes, you should upgrade using the script found here.

[http://www.whatwouldjesusdownload.com/christianubuntu/2007/05/popular-packages.html](http://www.whatwouldjesusdownload.com/christianubuntu/2007/05/popular-packages.html)

Jereme

---

### Post by TravMan63 on 2007-06-05
> **antoniuk said:**
> 2 things

first, you can find the version of Dansguardian by going into synaptics package manger and sleecting installed and scrolling to it. ... 

1)
Does synaptics package manager = Add/Remove Applications?
In the Add/Remove Applications, Dansguardian does not show - I selected all (and also tried
each category individually), and 'installed'.  It doesn't show

----> I'll answer that myself - (for others who may not have known as well) - it is NOT the same...

Add/Remove is located in the 'main menu'
Synaptic package manager is located in System/Administration
(perhaps they should be grouped together?)
----

Back to the main topic:
The versions # are: 2.8.0.6 (anti virus 6.4.4.1-2) and 1,6 (gui)

Synaptic also reports that these are the latest versions
I am running from the live CD
TM

---

### Post by mhancoc7 on 2007-06-05
> **TravMan63 said:**
> 1)
Does synaptics package manager = Add/Remove Applications?
In the Add/Remove Applications, Dansguardian does not show - I selected all (and also tried
each category individually), and 'installed'.  It doesn't show

----> I'll answer that myself - (for others who may not have known as well) - it is NOT the same...

Add/Remove is located in the 'main menu'
Synaptic package manager is located in System/Administration
(perhaps they should be grouped together?)
----

Back to the main topic:
The versions # are: 2.8.0.6 (anti virus 6.4.4.1-2) and 1,6 (gui)

Synaptic also reports that these are the latest versions
I am running from the live CD
TM

See: [http://ubuntuforums.org/showpost.php?p=2782674&postcount=7](http://ubuntuforums.org/showpost.php?p=2782674&postcount=7)

You need to use this script to upgrade the GUI and the configuration. The GUI is not in the repos and is only available in Ubuntu CE or from this script. 

Jereme

---

### Post by TravMan63 on 2007-07-07
I've noticed the older version also allows Konquerer to bypass it as well.

I'll have to check later if the update fixes that.

---

### Post by mhancoc7 on 2007-07-07
> **TravMan63 said:**
> I've noticed the older version also allows Konquerer to bypass it as well.

I'll have to check later if the update fixes that.

The current script should force all browsers through the filter.

Jereme

---

