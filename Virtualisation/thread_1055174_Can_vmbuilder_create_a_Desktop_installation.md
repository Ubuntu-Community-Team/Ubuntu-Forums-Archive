---
title: "Can vmbuilder create a Desktop installation?"
date: 2009-01-30
forum: Virtualisation
---

### Post by stephanhughson on 2009-01-30
Hi,

I've been using vmbuilder to create Ubuntu 8.10 virtual servers with lots of success, thanks goes out to the developers :-)

My company now needs some virtual Ubuntu Desktop computers for development work. Can we just put:

sudo vmbuilder kvm ubuntu --suite intrepid --flavour desktop

instead of 

sudo vmbuilder kvm ubuntu --suite intrepid --flavour virtual


I'm guessing not as I got an error when I did...

It nearly works, then I get 

"VMBuilder.exception.VMBuilderException: Process (['chroot', '/tmp/vmbuildergyIaLs/root', 'apt-get', '--force-yes', '-y', 'install', 'linux-image-desktop', 'grub']) returned 100. stdout: Reading package lists...
Building dependency tree...
Reading state information...
, stderr: E: Couldn't find package linux-image-desktop"

Does anyone have any ideas or information about this please?

---

### Post by stephanhughson on 2009-01-30
Actually maybe I can use "generic". There is a kernel called that.

I'm not sure if this will install all the desktop stuff I want though.

Maybe vmbuilder isn't the way in this case and I should use virt-install and an ISO image.

---

### Post by stephanhughson on 2009-01-30
Hmm, well that did install Ubuntu, but I think it was just the cut-down server version, but with a normal kernel.

It was a long shot :-) I'll use virt-install with an iso image.

If anyone knows how to get this to work another way (as long as it's a neat nice way), please let me know.

---

