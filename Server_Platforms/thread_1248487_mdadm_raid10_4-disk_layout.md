---
title: "mdadm raid10 4-disk layout?"
date: 2009-08-24
forum: Server Platforms
---

### Post by Socar on 2009-08-24
[B][COLOR=Red]Crap. I thought I looked over all possibilities but apparently not. Taking away disk 2 and 4 from my own example will make the array fail.

Sorry! :)[/COLOR] 

[/B][I] Hi,

I've been looking over the different kinds of layouts available for mdadm software raid and found that I'm going for Raid10. However I'm missing a very specific layout (which I hope is achievable by using a layout combination of some sort).

The default n2 layout yields redundance on a very specific level with 4 disks; any 2 disks can fail given that they're not each other's mirrors. This, I don't like :)
So, I've looked into the different levels on Wikipedia ([http://en.wikipedia.org/wiki/Non-standard_RAID_levels#Linux_MD_RAID_10](http://en.wikipedia.org/wiki/Non-standard_RAID_levels#Linux_MD_RAID_10)) but found nothing that would suggest redundancy with **any** 2 disks going down in a 4-disk set.
Also, I need to keep the disk storage capacity of a default RAID1+0 array (i.e. 200% of the smallest disk in the array).

The **f2** layout (as far as I can see) duplicates the sectors once with the offset of one disk. 

For 4 disks, I imagine it'd look like this:

```
A1     A2     A3     A4
A5     A6     A7     A8
A9     A10    A11    A12
A13    A14    A15    A16
A17    A18    A19    A20
…      …      …      …
A4     A1     A2     A3
A8     A5     A6     A7
A12    A9     A10    A11
A16    A13    A14    A15
A20    A17    A18    A19
```Now, remove the two disks in the middle. Oops, there goes our A2, A6, A10, A14 and A18 sectors! Array dead.

So, consider the following:

```
A1     A2     A3     A4
A5     A6     A7     A8
A9     A10    A11    A12
A13    A14    A15    A16
A17    A18    A19    A20
…      …      …      …
A3     A4     A1     A2
A7     A8     A5     A6
A11    A12    A9     A10
A15    A16    A13    A14
A19    A20    A17    A18
```Voilà! Now with this offset of 2 disks, **any** two disks may fail while still keeping default storage capacity of a RAID1+0 array.

So, my question is, is this possible? If so, I'd be eternally grateful to whoever finds me the answer :)[/I]

---

### Post by fjgaude on 2009-08-24
Well, I'm not sure and don't understand your layout for raid10.

First two drives are used one a mirror of the other, than the two are stripped. So is would seem that there's no way you could lose two drives and still have all your data intack.

For, if either drive in the strip set is lost you are toast. So you would have to make sure you lost two drives that were part of the back up, or mirror to the strip set. Don't know how to do that, yet?

---

