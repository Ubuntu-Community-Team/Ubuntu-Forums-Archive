---
title: "passphrase input-box for encrypted disk is not shown"
date: 2016-01-02
forum: Ubuntu Development Version
---

### Post by sudodus on 2016-01-02
Iso-testing Lubuntu Alternate i386 iso file, testcase

'Alternate Install (Encryption) in Lubuntu Alternate i386 in Xenial Xerus Daily' (alias Alpha1 in this case)

[Bug #1530548](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1530548) appears in the installed system:

The passphrase input-box for encrypted disk is not shown (and the plymouth dots are not shown either, only a dark blue background). Pressing some of the

***ctrl + alt + (F1-F7)*** keys

and after that

***Escape***

brings a text screen with the text 'Please unlock disk sda5_crypt', and it is possible to enter the passphrase, and I arrive at the login screen.

(Otherwise the encrypted disk and also encrypted home work.)

Edit: I found that it affects Ubuntu Gnome Xenial amd64 too. Probably it affects all flavours.

-0-

Please test it, and mark 'affects me too' if it does :-P

---

### Post by sudodus on 2016-01-03
A better workaround (than hitting ctrl+alt+(F1-F7) keys and then Escape) is to remove the boot options 'splash $vt_handoff'

You can do it 'live' after pressing the left shift key during boot and then the 'e' key.

-o-

You can actually enter the passphase while the dark blue screen (in Lubuntu) is displayed (without any help text and without feedback stars or dots). But it is confusing and would make most users think that the boot has failed. I did not think of it until I had a nights sleep ;-)

---

