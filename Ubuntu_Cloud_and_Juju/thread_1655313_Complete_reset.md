---
title: "Complete reset"
date: 2010-12-29
forum: Ubuntu Cloud and Juju
---

### Post by iamcgg on 2010-12-29
I installed UEC a few times, each time beating on the thing trying to get it to work until I was sure I had beaten it so bad it was beyond fixing. Reformat, reinstall, try again. I'm wondering if there's a simple way to wipe the eucalyptus/walrus/etc. config completely and start over fresh without having to reformat and reinstall. I wish there were a way to go through the initial guided setup again and have it come in clean without any of the junk from the previous fail.

Any ideas?

---

### Post by raymdt on 2010-12-30
Hi Iamcgg,
eucalyptus ist just a programm  like all other packages on ubuntu. You don't need to format or reinstall ubuntu just because your eucalyptus installation is broken.
You can try this to desinstall completely eucalyptus.

On CLC (cc, walrus,sc ) and NC
```

sudo apt-get remove --purge eucalyptus*

```then run
 ```

locate  eucalyptus

```So you can see if there are still any eucalyptus files ( not euca2ools ) on your pc.
You can remove those files manually.(Sometimes you need to desinstall the image-store-proxy too)

After that you can use this guide to reinstall eucalyptus.
[https://help.ubuntu.com/community/UEC/PackageInstall](https://help.ubuntu.com/community/UEC/PackageInstall)


(Sorry for my poor English  -:)

---

### Post by kim0 on 2010-12-30
Hey raymdt, thanks for all the helpful comments :) Could you ping me on irc (kim0) thanks

---

### Post by raymdt on 2010-12-30
Hi Kim0,
thanks too. I'll ping you when i am online -:)

---

