---
title: "CD drive not found in Virtualbox"
date: 2008-12-25
forum: Virtualisation
---

### Post by grv16mk on 2008-12-25
I have been using virtualbox for running Windows XP on my Ubuntu laptop for several months now. This morning i decided to update to the newest version. I went to my virtual computer and it would not reconize my cd drive. It is the same settings as before but I can not use the drive on my virtual computer. Does anyone know how to fix this?

---

### Post by inobe on 2008-12-25
welcome to ubuntu forums

this fella had the same problem, in fact so did i at one point' however i wasn't as lucky.

[http://ubuntuforums.org/showthread.php?t=1019585](http://ubuntuforums.org/showthread.php?t=1019585)

he basically reinstalled vb, i am **guessing** he forced an update in synaptic !

this way he was able to keep his setup.

---

### Post by Dedoimedo on 2008-12-27
When you say not found:
Does this mean you no longer have a drive show up in vm - or discs you insert are no longer readable?

There could be several reasons:

1. physical drive damaged.
2. /etc/fstab changed so it longer has the cd listed.
3. messed up /dev tree.
4. settings for vm changed.

I'd check all these, before reinstalling. The solution might be simple enough.

Dedoimedo

---

