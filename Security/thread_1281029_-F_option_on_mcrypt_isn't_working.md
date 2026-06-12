---
title: "-F option on mcrypt isn't working?"
date: 2009-10-02
forum: Security
---

### Post by RobertL on 2009-10-02
The -F option on mcrypt seems to be ignored. The documentation says it is supposed to "force output on standard output or input from stdin if that is a terminal. By default mcrypt will not output encrypted data to terminal, nor read encrypted data from it."

I've tried several combinations of options and command lines but I can't get output to go to stdout, whether it's a terminal or not. For example:

mcrypt -F -d -b -m ecb <name of encrypted file> | more

This example sends nothing to more. I want the plaintext to go to stdout so I can pipe it into a python program without creating a plaintext file that might get left behind. But it seems to always create the plaintext file and -F seems to have no effect.

This is the mcrypt version that comes with Ubuntu 9.04 (i686-pc-linux-gnu), mcrypt v.2.6.4 linked against libmcrypt v.2.5.7.

Anybody have any wisdom on this? What am I missing?

---

### Post by alap77 on 2010-08-10
Try like this:

mcrypt -F -d -b -m ecb < name of encrypted file | more

---

