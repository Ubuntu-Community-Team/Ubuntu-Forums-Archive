---
title: "Problems installing VirtualBox additions on Ubuntu server"
date: 2009-04-11
forum: Virtualisation
---

### Post by jocampo on 2009-04-11
Hello forum friends ...

I just installed Ubuntu Server using VirtualBox (host is a Linux box also, Ubuntu Hardy desktop ) but when I'm running the VirtualBOx additions and getting this error

THis System does not seem to have support for OPenGL direct rendering.
VIrtualBOx requires 2.6.27 or later for this. PLease see the log
file /var/log/vboxadd-install.log if your guest uses Linux 2.6.27 and you still see this message

... then screen says...

BUilding the VIrtualBox GUest additions kernel module

... and at the end says

Could not find X.org or XFree86 on the guest system

Of course, I am not running any GUI, this is UBuntuServer and I am not planning to do that but I want to be able to expand the screen in order to read what I type better.

Any ideas?

THanks in advance,

---

### Post by jocampo on 2009-04-11
Bump!

no one? please, I'm sure someone else there faced this issue as well...

---

### Post by bodhi.zazen on 2009-04-11
Well , why do you not simply ssh into the server if there is no X ?

Is there some feature of the guest additions you need ?

You *may* need to install a generic kernel.

---

### Post by jocampo on 2009-04-11
> **bodhi.zazen said:**
> Well , why do you not simply ssh into the server if there is no X ?

Is there some feature of the guest additions you need ?

You *may* need to install a generic kernel.

Thanks for taking the time and reply! I really appreciate that.

The main feature that I need is able to resize the screen, make it bigger. I followed the instructions here and still no success, getting this error now:

Could not find X.org or XFree86 on the guest system. The X Window drivers will not be installed.

Why I should try to use ssh if I can fix that installing the VBadditions? does not make sense to me ... it's a workaround, but not a fix

---

### Post by bodhi.zazen on 2009-04-11
In your case you should know that part of what the Virtualbox Additions do are to fix the resolution in X , so if you are not running X , installing the Additions really do not help you much.

If you ssh in, you still have a terminal, as you would in VBox, and you can resize the terminal and font all you wish.

---

