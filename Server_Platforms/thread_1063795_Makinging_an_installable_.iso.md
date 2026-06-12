---
title: "Makinging an installable .iso"
date: 2009-02-08
forum: Server Platforms
---

### Post by sdamron on 2009-02-08
Hello Ubunteers!  ;)

I have built a RADIUS server using Ubuntu server and would like to make an installable .iso out of it.  That is to say, I would like to have it install with the setup that I have built and only need a couple of passwords set in order to be up and running on any hardware.  Can anyone point me to how this can be done?

TIA,

---

### Post by bigbearomaha on 2009-02-08
Well, I would say to use Remastersys to do that, but, remastersys does not play well with the kernel that buntu server uses.

the easiest way to use rematersys would be to change the kernel in server, or, use a release with a usable kernel ( like buntu, xubuntu, kbuntu, etc..) and then you are good to go with the remastersys method.

might help.  I guess.

Big Bear

---

### Post by sdamron on 2009-02-09
> **bigbearomaha said:**
> Well, I would say to use Remastersys to do that, but, remastersys does not play well with the kernel that buntu server uses.

the easiest way to use rematersys would be to change the kernel in server, or, use a release with a usable kernel ( like buntu, xubuntu, kbuntu, etc..) and then you are good to go with the remastersys method.

might help.  I guess.

Big Bear

Thanks!  I have seen that one recommended several times.  Do you know specifically what the issue is with the Kernel?

---

### Post by bigbearomaha on 2009-02-10
hmm.  It's been awhile since  I read it.   I think it was to do with that kernel not supporting mksquashfs or something like that.  I may be wrong on the app but the idea is that kernel doesn't come with regular support for some app like that, you would have tp recompile the kernel   or use a different kernel that does.

along that line anyway.  sorry, my memory doesn't work too hot this early in the morning.

Big Bear

---

