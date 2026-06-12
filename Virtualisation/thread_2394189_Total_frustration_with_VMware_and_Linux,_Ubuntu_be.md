---
title: "Total frustration with VMware and Linux, Ubuntu because I'm using it."
date: 2018-06-13
forum: Virtualisation
---

### Post by pksings2 on 2018-06-13
I have loved Ubuntu, been a advocate since the first release. Great job team! And thank you!

But  I have lost patience with it. Nouveau updated and my old video card is  no longer working.  16.04 would no longer boot to GUI, even with a newer  video card, 3 days later I saved everything I could and installed  18.04, wiping out the 16.04 instance. I had a great mailserver stack working. Postfix, amavis, spamassassin, dovecot.  4 different tutorials and I cannot mail through it. I had even saved everything from the previous working instance /etc/ /var , nothing works. 3 long evenings trying to solve it and nothing..... Nothing should be this difficult.  

So I thought I would just rollout a pre-configure VM that has all that working. After all, I have VMware workstation!

I have owned a copy of VMware workstation so long I do not remember what version my first copy was. I now own my last. And I'm not using it. It won't compile. For at least the 20th time.
VMware seems to purposefully have written the VMMON and VMNET modules so that each kernel change breaks the build process and a $150.00 upgrade is necessary to get it to work. Yes, there are patches to be found, unfortunately recently they are somewhat spotty in the successful implementation area. I can't get mine to work.  Part of it is the rapid kernel change cycle, new ones come often. Using an LTS version doesn't seem to help, they still change roughly every two weeks.

 There are some brilliant programmers at VMware. They could have solved this long ago.

They are the market leader in virtualization for a good reason, they have great products that work very well. But Workstation on Iinux appears to be the forgotten step-child. A kernel update and once again, it doesn't work.
They now want me to upgrade to version 14, and there are numerous posts that it doesn't even work. I had all the functionality I need from it in version 10. I upgraded to 12 to get it to compile without issues. Right back in the same boat a year later. Time to renew my annual subscription. 

I am now willing to pay the  cost for an Apple. My 2013 Macbook Pro continues to work day after day,  update after update. I upgraded Fusion last year because it was on sale  but the previous version was still working fine. 

I'm done here...

Thank  you again Canonical, great job, please keep up the good work.  Linux/unix is taking over the world and you are a really big part of the  reasons it is.  I just need a less frustrating unix box. I just can't do this anymore.

---

### Post by sp40140 on 2018-06-13
jump to VBox. It will work with your vmware virtual machines. I was using vmware player (free version) until they came up with version 14. Too much trouble. So jumped to VBox. It's just as good.
I am now thinking of going with kvm.

Also, if you are running critical / sensitive / important stuff, I would advice against randomly updating / upgrading without proper backup / testing and all that. This is one reason big companies don't like to update to latest and greatest.

However, as you have made up your mind. Good luck with whatever you pick next (but you will likely run into similar situation regardless of the OS you use).

---

### Post by LHammonds on 2018-06-15
You did not mention what your host OS was.  Are you running Windows?

There are other virtual management options out there.  I never really liked VMware workstation or the free player variant.

On Windows-based PCs, I use Oracle VirtualBox to run my Linux servers.

On servers, I run VMware ESXi or Nutanix (basically Linux KVM) as the host OS and run Linux as the guest OS.

I never have a problem with the guest OS, however, I only run the headless server editions and not the GUI desktops which can be particular with the GFX hardware/virtualization.

LHammonds

---

