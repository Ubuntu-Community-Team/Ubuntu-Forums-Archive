---
title: "unable to burn cd/dvd"
date: 2011-04-25
forum: Server Platforms
---

### Post by lazerz on 2011-04-25
im using this command to burn the image of ubuntu....

sudo mkisofs -b boot/grub/stage2_eltorito \ -no-emul-boot -boot-load-size 4 -boot-info-table \ -V "Custom Live CD" -cache-inodes -r -J -l \ -o ~/live-cd.iso $CD





I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: Missing pathspec.
Usage: genisoimage [options] -o file directory ...

Can someone tell how to workaround this error? em so close

---

