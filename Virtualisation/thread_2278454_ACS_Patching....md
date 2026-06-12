---
title: "ACS Patching..."
date: 2015-05-16
forum: Virtualisation
---

### Post by KillerKelvUK on 2015-05-16
Anyone got any pointers for patching the 15.04 kernel (3.19) with acs override?

---

### Post by redger on 2015-05-21
did you overcome this ?

here's the repository the Arch instructions ultimately point to [https://github.com/zman0900/linux-vfio-aur]("https://github.com/zman0900/linux-vfio-aur")  and it looks as though it's the same patches as were generated way back
the actual patch used can be found here [https://github.com/zman0900/linux-vfio-aur/blob/master/override_for_missing_acs_capabilities.patch]("https://github.com/zman0900/linux-vfio-aur/blob/master/override_for_missing_acs_capabilities.patch")

you could try asking zman0900 

did you try the patches I posted 

[http://ubuntuforums.org/showthread.php?t=2266916]("http://ubuntuforums.org/showthread.php?t=2266916") ... right at the bottom of the page

---

### Post by KillerKelvUK on 2015-05-21
Hey, no not moved forward with it yet, I had some USB and redirection problems which took my attention but am back on it this weekend.

I was working to the original patch from Alex W found here... [https://lkml.org/lkml/2013/5/30/513](https://lkml.org/lkml/2013/5/30/513) ...my link and yours are very similar but yours look more developed now.

Ref your post linking patches yes I've had that running previously (think the patch is against a 3.16 kernel originally but it worked on a 3.18) if all else fails I'll revert to using that with 15.04 but was looking to try and keep versions to 15.04 entry level as I've gotten a reasonably stable mix now.

---

### Post by KillerKelvUK on 2015-05-23
So its building the debs now...using the latest kernel sources for 3.19 and patched using the arch git repo linked by redger in post #2 above.  The patch succeeded for 3 out of 4 hunks, the last hunk is the one that failed so I manually inspected the quirk.c file and the unpatched code segment looked almost identical to the patch so I'm taking a punt that this is okay.

Will post back the results after build and test.

---

### Post by KillerKelvUK on 2015-05-24
Okay so I have patched 3.19-18 kernel and its working...my 'punt' as per post #4 was wrong, the failed hunk was a single line addition to /drivers/pci/quirks.c which I had to manually locate and add, then built the debs again and this time my IOMMU groups have only a single PCI device apart from one which contains the 3 chipset controllers.  Passed through my dvb card to a guest without issue first time

:popcorn:

I can look at providing a diff (patch) for the file I manually edited if anyone would like this otherwise its no v.difficult as long as you know what to look out for.

p.s. redger, your kernel build guide is what I followed *again*, I can only ever get this to work using the 'fakeroot debian/rules editconfigs' method, all others result in an error.

---

### Post by jclaeyssens on 2015-05-27
> **KillerKelvUK said:**
> So its building the debs now...using the latest kernel sources for 3.19 and patched using the arch git repo linked by redger in post #2 above.  The patch succeeded for 3 out of 4 hunks, the last hunk is the one that failed so I manually inspected the quirk.c file and the unpatched code segment looked almost identical to the patch so I'm taking a punt that this is okay.

Will post back the results after build and test.

KillerKelvUK, I am working on patching the kernel as you. As in your case, the patching gave me an error on the last hunk, but I don't seem to find the place to insert the line. Could you post your quircks.c file so I could learn how to interpret the location system of this whole patch thing?

---

### Post by KillerKelvUK on 2015-05-28
> **jclaeyssens said:**
> KillerKelvUK, I am working on patching the kernel as you. As in your case, the patching gave me an error on the last hunk, but I don't seem to find the place to insert the line. Could you post your quircks.c file so I could learn how to interpret the location system of this whole patch thing?

So if you look at the ACS patch file there are 4 lines which start with a similar pattern of text: "@@ -3384,6 +3384,107 @@", I believe these are the diff headers that denote a HUNK and the lines below are the modified/patched code that needs to be inserted/removed.  In the ACS patch file the 4 lines are...  (TIP: open the patch file in gedit and it should highlight the code segments for easy reading/reference)

```

@@ -2554,6 +2554,16 @@ bytes respectively. Such letter suffixes
@@ -3384,6 +3384,107 @@ struct pci_dev *pci_get_dma_source(struc
@@ -3483,6 +3584,7 @@ static int pci_quirk_intel_pch_acs(struc
@@ -3495,6 +3597,7 @@ static const struct pci_dev_acs_enabled

```

You may have noticed that the first line above is a patch to the *your_kernel_source*/Documentation/kernel-parameters.txt file while the rest are a patch to the *your_kernel_source*/drivers/pci/quirks.c file.  So if it was the 4th HUNK that failed then it stands to reason it was the code segment associated to the last @@ line in the above list.

You'll notice that within that code segment there is only a single line (line number 144) which has a + symbol at the start which denotes this is a code line to add/insert into the file, so where does this need to be added in the 3.19 quirks.c file?  The location is pretty straight forward as the point for this is part of the @@ header i.e. @@ -3495,6 +3597,7 @@ [COLOR=#ff0000]**_static const struct pci_dev_acs_enabled_**[/COLOR] <-- this bit in red.  If you search the quirks.c file for this line of red text you'll find a direct match and the lines below it look similar but not the same to the patch file.  From what I can infer from the very technical explanations for ACS this part of the code I believe deals with associating vendor hardware IDs with different types of ACS capability, the line of code the patch is looking to insert is about allowing any vendor hardware ID access to the ACS rules that relax IOMMU grouping.  Ergo the patched code needed is "{ PCI_ANY_ID, PCI_ANY_ID, pcie_acs_overrides }," and it needs inserting into this section of code just above the line which has "{ 0 }" in.

That should then be it, you've manually patch the 4th HUNK that failed.

---

