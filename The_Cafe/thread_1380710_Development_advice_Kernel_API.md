---
title: "Development advice: Kernel API"
date: 2010-01-14
forum: The Cafe
---

### Post by k64 on 2010-01-14
I was thinking of (possibly) writing and building a utility that automates device support in Linux by automatically scanning both the devices on your computer for functionality and the Kernel API to enable the functionality of the device components. Translation: Once this utility is in there, device support will be automated, and any hardware, anywhere will be able to work with Linux, because the utility will access the API directly.

I wanted to know your opinion on such an automatic utility, if it would be useful.

---

### Post by Dekkon on 2010-01-14
It would be extremely useful if you can develop at that level. Though, me personally, I would extend/change the Restricted Drivers app and innoviate that; thats open source. ;)

---

### Post by k64 on 2010-01-14
> **Dekkon said:**
> It would be extremely useful if you can develop at that level. Though, me personally, I would extend/change the Restricted Drivers app and innoviate that; thats open source. ;)

I personally am thinking of something built into Ubiquity that automatically writes and builds a custom kernel for your hardware using the Kernel API on the Live CD, and then, when the installation is complete and you reboot, the first time you use the custom kernel you have the option to upload the kernel source code onto Launchpad. Oh, and then your custom kernel will automatically be FOSS.

---

### Post by Frak on 2010-01-14
So, how would you plan to do it.

---

### Post by schauerlich on 2010-01-14
"I'm going to write a program that will make the Linux kernel work on anything. It will do it by already knowing how to use everything. It will know how to use things by already knowing how to use them. Good idea y/n?"

---

### Post by Giant Speck on 2010-01-14
> **schauerlich said:**
> "I'm going to write a program that will make the Linux kernel work on anything. It will do it by already knowing how to use everything. It will know how to use things by already knowing how to use them. Good idea y/n?"

[FONT=Courier New]Good idea [Y/n]?  y
WARNING:  The following packages cannot be authenticated!
liblulz-2.0  icwutudidthar-dev
Install these packages without verification [y/N]? _[/FONT]

---

### Post by gnomeuser on 2010-01-14
That sounds like lib_not_really_a_driver_but_much_pretty_much_the_same_just_with_increased_complexity

I believe the complexity both of the states you will have to check and the arms race you will have with the kernel API which is not and cannot in sanity be stable will go way beyond the complexity of our driver model. Not to mention that to drive or even probe hardware in the first place they are likely to require some form on initilization which this model will also have to either depend on the kernel doing or the driver, or doing it on it's own. 

The problem would quickly turn into essentially redundantly reinventing the majority of the kernel for no gain.

The kernel already does your device probing, it already loads drivers that enable and report functionality. We already have for the most part at least, nicely reusable versions of commonly needed code so drivers do not implement more that strictly required to enable functionality.

Now I would love to see the design for this proposal, but for now all I see is handwavy blue sky ideas which at least to me seem to have no firm grounding in understanding how the kernel works nor how it is architeched to work or how the proposed idea fits into this scheme, how it plans to address things such as API instability?

I don't feel right calling this a delusional idea but the OP really gives no other option given the lack of information. Sorry.

---

### Post by Xbehave on 2010-01-14
for drivers make localmodconfig or make localyesconfig already exist, for the userspace API it's vey hard to tell what APIs get used (i.e how can you tell that i use the lirc api unless i use lirc while your app is running?) but if you figured out how to do it consistently then it would be worth it (ideally your app would come with a make script so i can make localapiyesconfig or make localapimodconfig, without worrying to much about how your app works)

---

