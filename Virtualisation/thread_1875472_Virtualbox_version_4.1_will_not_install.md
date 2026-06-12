---
title: "Virtualbox version 4.1 will not install"
date: 2011-11-04
forum: Virtualisation
---

### Post by 39er on 2011-11-04
This is to request assistance with a problem I am experiencing to upgrade virtualbox version 4.0 to 4.1. I am getting the message "Conflict with installed package virtualbox 4.0" and install is not possible.

I have tried a variety of approaches with dpgk and aptitude but it just will not update.

The current version 4.0.14 is working fine.

So what might be the problem?

Thank you for taking time to reply.

---

### Post by haqking on 2011-11-04
> **39er said:**
> This is to request assistance with a problem I am experiencing to upgrade virtualbox version 4.0 to 4.1. I am getting the message "Conflict with installed package virtualbox 4.0" and install is not possible.

I have tried a variety of approaches with dpgk and aptitude but it just will not update.

The current version 4.0.14 is working fine.

So what might be the problem?

Thank you for taking time to reply.

an upgrade is incompatible.

you need to remove and install the new version.

Best to add to sources list for future.

deb packages and source entries are here [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by 39er on 2011-11-06
> **haqking said:**
> an upgrade is incompatible.

you need to remove and install the new version.

Best to add to sources list for future.

deb packages and source entries are here [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)


Thank you sir haqking. Since the application is currently running, I opted not to tinker with it for reason not to create more work than necessary. I shall wait until the new LTS release of Ubuntu is available and then launch an updated version of Vbox.
Here I am following my philosophy: Don't fix which is not broken.

Best Regards,
-39er

---

### Post by haqking on 2011-11-06
> **39er said:**
> Thank you sir haqking. Since the application is currently running, I opted not to tinker with it for reason not to create more work than necessary. I shall wait until the new LTS release of Ubuntu is available and then launch an updated version of Vbox.
Here I am following my philosophy: Don't fix which is not broken.

Best Regards,
-39er

My point was that the newest version of VBOX has lots more features, the latest version 4.1.6

You dont need to upgrade your distro version to use the latest VBox

you download the .deb and install it and add the extensions pack and thats it regardless of of your distro version

---

### Post by CharlesA on 2011-11-07
> **haqking said:**
> My point was that the newest version of VBOX has lots more features, the latest version 4.1.6

You dont need to upgrade your distro version to use the latest VBox

you download the .deb and install it and add the extensions pack and thats it regardless of of your distro version

Yep. Even after 12.04 comes out there is probably going to be new versions of VBox.

If you have any VMs running, either power them off or save the state, uninstall the current version of vbox and install the latest.

---

### Post by 39er on 2011-11-07
> **haqking said:**
> My point was that the newest version of VBOX has lots more features, the latest version 4.1.6

You dont need to upgrade your distro version to use the latest VBox

you download the .deb and install it and add the extensions pack and thats it regardless of of your distro version


Ok, In the meantime I have learned a few more things as for example why Vbox 4.1 does not show up in the software list. The reason, I believe, is that I had set the source list to update only such applications which would apply to the 10.04 LTS distro.
Since I want to have peace of mind and not run after every quirk of potentially buggy updates I had set it this way...and promptly forgot about it. This, I am afraid,  happens to (19)39ers here and there.
Given the foregoing and since Vbox version 4.01 works, I shall not fix what is not broken. Interestingly enough, Charles As Philosophy tends to support this as well albeit in a different way.
I agree that there will be always new versions. In this case I will wait.
However, let me thank you for your suggestions.
Finally, how do you set this message to SOLVED to put this issue to bed.

---

### Post by haqking on 2011-11-07
> **39er said:**
> Ok, In the meantime I have learned a few more things as for example why Vbox 4.1 does not show up in the software list. The reason, I believe, is that I had set the source list to update only such applications which would apply to the 10.04 LTS distro.
Since I want to have peace of mind and not run after every quirk of potentially buggy updates I had set it this way...and promptly forgot about it. This, I am afraid,  happens to (19)39ers here and there.
Given the foregoing and since Vbox version 4.01 works, I shall not fix what is not broken. Interestingly enough, Charles As Philosophy tends to support this as well albeit in a different way.
I agree that there will be always new versions. In this case I will wait.
However, let me thank you for your suggestions.
Finally, how do you set this message to SOLVED to put this issue to bed.

no worries.

use the thread tools menu from the top.

cheers

---

