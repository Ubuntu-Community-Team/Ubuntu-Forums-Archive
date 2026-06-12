---
title: "Update Information Notification Bug"
date: 2012-10-31
forum: Ubuntu Development Version
---

### Post by ventrical on 2012-10-31
Since the kmod update I have this persistent notification of a red triangle with an exclamation point in it on the menu bar at top right. All is updated. It just won't go away.

---

### Post by jerrylamos on 2012-10-31
I don't have a red triangle.  From time to time I get an update notifier crash so I choose ignore future.....

One of the first things I do on an install is software sources > repositories > check Ubuntu partners > updates select never.  Then sudo apt-get update && sudo apt-get dist-upgrade most days when I want to do the update not when update comes crashing down on what I'm doing.

BTW, check "removes"  carefully before doing "y".

And since this is "unstable" development have a backup partition I use 12.04.1 and a couple partitions for unstable development.  I'll update this apt-sources 13.04 then when daily build shows raring I'll install into another partition then alternate installs & updates.  I don't have a 12.10 I'm using.

---

### Post by grahammechanical on 2012-11-01
Does it not have a drop down menu with an error message?

I get that kind of thing when there is a missing package header. And it usually prevents updating.

Regards.

---

### Post by ventrical on 2012-11-01
> **grahammechanical said:**
> Does it not have a drop down menu with an error message?

I get that kind of thing when there is a missing package header. And it usually prevents updating.

Regards.

Must be a ghost :)  I just updated/upgraded and it disappeared. Halloween? :)

Regards,
ventrical

---

### Post by grahammechanical on 2012-11-02
I have had this twice now and it has appeared after I updated with Synaptic. I think it is because I have the Extras repositories enabled for Raring and they do not yet exist. At least it proves that the notification indicator is working.

Regards

---

### Post by ventrical on 2012-11-02
I used  terminal to update/upgrade and that took care of it (for now it seems). Clicking on that indicator icon produced an error dialog context with menu items .. etc.. I then would click "show updates" and then it would notify me "No updates Available" and return to error status.

Perhaps it is the new 3.7.x-xRC3 kernel fixed it?

I do have an assumption that this problem will arise again, being that apport is literally useless at this stage.

---

