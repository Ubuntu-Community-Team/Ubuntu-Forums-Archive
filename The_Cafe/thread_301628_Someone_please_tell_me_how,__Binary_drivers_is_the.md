---
title: "Someone please tell me how,  Binary drivers is the same as free windows"
date: 2006-11-17
forum: The Cafe
---

### Post by darkhatter on 2006-11-17
I've been hearing that exable a lot in: 

Poll: Binary NVidia/ATI Drivers in Ubuntu? 
[http://www.ubuntuforums.org/showthread.php?t=297392](http://www.ubuntuforums.org/showthread.php?t=297392)

to me the whole wanting Binary Drivers by default = wanting free Windows is B.S.

---

### Post by matthew on 2006-11-17
I don't think they're the same at all. 

The only explanation I can see is that people saying that must somehow think that using binary drivers in Linux means that the windows drivers have been converted rather than understanding the possibility (probability...) that the drivers were written from scratch for Linux.

---

### Post by paul6 on 2006-11-17
I think their reasoning is that accepting binary code in Ubuntu encourages more companies to keep their code binary and hidden instead of making it open source.

If more Linux distros started refusing to accept binary code, the companies would be forced to make their drivers open source so that people running Linux desktop systems would buy their products.

At least thats how I understand the argument.

---

### Post by darkhatter on 2006-11-17
I think Nvidia, and Ati just want to protect their investment, thats how I see binary drivers. I think giving the warning after installing the binary drivers in Ubuntu will do a lot more damage, then not including them all together

---

### Post by hizaguchi on 2006-11-17
I think the logic is that if you are willing to accept closed code in your kernel then you'd might as well be running a whole closed system.  In that case, you are not running Linux for freedom, but for the free price tag, and you'd probably switch back to Windows if they gave it out for free.

> **darkhatter said:**
> I think Nvidia, and Ati just want to protect their investment, thats how I see binary drivers. I think giving the warning after installing the binary drivers in Ubuntu will do a lot more damage, then not including them all together
That's fine, but kind of out of place here.  Would fit right in with any one of the other threads already discussing the topic. ;)

---

### Post by chaosgeisterchen on 2006-11-17
If anyone wants to use free 3D drivers in any time in future one should consider donating the **nouveau** - project (open source nVidia drivers).

---

### Post by maagimies on 2006-11-17
> **hizaguchi said:**
> I think the logic is that if you are willing to accept closed code in your kernel then you'd might as well be running a whole closed system.  In that case, you are not running Linux for freedom, but for the free price tag, and you'd probably switch back to Windows if they gave it out for free.But I do not like to use Linux just solely because it's free as in speech, I like it as an operating system. So by that logic I should consider running a closed source Unix, and hope that the NVIDIA drivers get ported to it?
I thought Linux is all about choice. I choose to run Linux, but I also choose to run closed source programs.

---

### Post by PriceChild on 2006-11-17
A company can't "just" offer open source drivers.

As i've said before, doing this would allow the opposition the ability to see exactly how your hardware works, allowing them to copy it extremely easily, letting them gain the advantage by using your technologies.

---

### Post by raublekick on 2006-11-17
no one is trying to limit the choice to use whatever you want on your system.  

including proprietary drivers by default is ok in a distribution like Sabayon because it is a small distro and the goal is to provide what only 3D drivers can provide. 

the goals for Ubuntu, however, are much different, and including these drivers conflicts with the goals. proprietary drivers and firmware are already included in Ubuntu, but they are necessary to get a most basic working system. without them i would not be able to get online right out of the box. 3D capabilities is not a necessary thing, therefor they are not necessary to include. not even Windows includes 3D drivers. Ubuntu right now provides much more than Windows does out of the box, because Windows will not let you run at 1920x1200 out of the box. 

the logic that including these drivers is like using Windows is a little flawed, indeed. including does not make a fully closed system, but it does discourage the use and development of open alternatives.


the whole not opening up the specifications for fear of competition stealing it is kinda flawed too. specifications would give developers a way to see how the hardware works, not how it is fully designed. schematics don't necessarily tell you the materials used, or how they work around certain design problems like heat distribution. lots of hardware is open, and good things have resulted. the basic examples are network cards. look how many are out on the market. there are so many because they are easy to make, but also because the design isn't totally closed. sure, there are a lot of crummy cards on the market, but there is a lot of competition, and it still pretty much comes down to the best manufacturer with the best price. videocards are much more difficult to manufacture, and there really aren't going to be new manufacturers being created to design new chips. hell, even processors are more open than videocards are.

open hardware is kinda touchy, but really, if i buy a piece of machinery, for any purpose, i should be able to get info to use it, fix it, and study it myself. imagine if your car design was closed, so you couldn't even do something as simple as an oil change yourself, or change a belt, or whatever.

---

### Post by InsomniacUK on 2006-11-17
> **hizaguchi said:**
> I think the logic is that if you are willing to accept closed code in your kernel then you'd might as well be running a whole closed system.

That's the worst argument in the world. ATi and nVidia cards need closed-source drivers to do anything slightly useful. Most people will install the drivers on their own anyway, so why not make the whole process a bit easier?

Just give people a choice whether to use the closed-source drivers during the install procedure and leave it at that. As long as it isn't forced on anyone, why should it be an issue?

---

### Post by king20878 on 2006-11-17
One thing that also needs to be considered is that often the makers of the product don't actually own the drivers for the products they're distributing.  They are often making a board that uses a chipset that uses a driver that is closed source, but that chipset is produced by an OEM manufacturer somewhere in Asia.  As much as they might want to open-source the driver, they don't have a say in it.

---

