---
title: "Missing letters ..."
date: 2015-06-03
forum: Ubuntu Development Version
---

### Post by Elfy on 2015-06-03
not sure if this is local or not

Recent updates to at least xserver-common and a reboot apparently left me with missing letters. 

Running nouveau. 

Installed nvidia driver and rebooted and all was well. 

(Not hardware unless it's really random and worked in one of the other installs and then suddenly not 30 seconds later booting into this ;) )

---

### Post by ventrical on 2015-06-03
I just update/upgrade my xubuntu 15.10 and get new background theme?

Anybody else?

---

### Post by ventrical on 2015-06-04
I think I got what you got except is all over. I'll try to capture.

Ok .. capture worked.

See the missing letters?

---

### Post by ventrical on 2015-06-04
Elfy.

Please flag your version/flavor.

Thanks

---

### Post by ventrical on 2015-06-04
Merge with missing letters ?

---

### Post by Elfy on 2015-06-04
> **ventrical said:**
> I just update/upgrade my xubuntu 15.10 and get new background theme?

Anybody else?

That's the dev wallpaper - once we get closer to release it'll change to what will be in 15.10

---

### Post by Elfy on 2015-06-04
> **ventrical said:**
> I think I got what you got except is all over. I'll try to capture.

Ok .. capture worked.

See the missing letters?

Yep - that was what I was seeing.

---

### Post by grahammechanical on 2015-06-04
It reminds me of what I saw when I first tested the Wayland session on Ubuntu Gnome. I am not saying it is connected. It is just an observation. I have been trying to find useful information on Xfce and Wayland but without much success.

EDIT: I have just installed the gnome wayland session on Wily Ubuntu Gnome and I am still getting the missing letters. Also running Nouveau. I am getting it with Firefox and this forum but a mouse over usually corrects it.


Regards

---

### Post by ventrical on 2015-06-07
I think it is connected because I just installed nvidia-current on my ubuntu-gnome install and now the missing characters problem is resolved. However, there is now a problem with wayland protocol as when I try to log on it will re-cycle back to GDM. Wayland worked fine with nouveau ... but the missing characters are there.

Regards..

---

### Post by grahammechanical on 2015-06-07
What about Xubuntu? Is missing letters present when running on Nouveau? But not on proprietary? I am running Ubuntu Gnome on Nouveau because I read on the Gnome web site that Xwayland does not work with proprietary video drivers.

Regards.

---

### Post by ventrical on 2015-06-07
> **grahammechanical said:**
> What about Xubuntu? Is missing letters present when running on Nouveau? But not on proprietary?

Regards.

Yes .. so I assume there is a nouveau driver problem ... just a sec ... I am going to check it out again because I updated xubuntu today ... and also  have not tried nvidia-current on that install   ...   brb..

edit:  yes.. missing characters are still there after update/upgrade

... now installing nvidia -current .. brb

Edit:

yes ... nvidia driver solves problem of missing characters.  This is watching development 'under the hood' :) A real refreshing bug to watch after  :).. my fix for the day :) lol

Regards

---

### Post by ventrical on 2015-06-07
> **Elfy said:**
> not sure if this is local or not

Recent updates to at least xserver-common and a reboot apparently left me with missing letters. 

Running nouveau. 

Installed nvidia driver and rebooted and all was well. 



Ya.. that  works for now..

---

### Post by ventrical on 2015-06-12
nvidia-current was a horror on gnome3. Updates brought in new xorg-nouveau .. etc... remove nvidia-current and now  runs well again with nouveau.

regards

edit

this appears what the problems was:

```

server-xorg-video-nouveau 

```

and was updated. Now reverting my xubuntu install back to nouveau .. see whats happens..

---

### Post by ventrical on 2015-06-12
Nouveau driver now working ... no missing letters.

There was an initial /plymouthd/ apport error after restart. Tried to report it and it just disappeared without reporting.  (I eyeball my modem indicator lights on physical kvm).

---

