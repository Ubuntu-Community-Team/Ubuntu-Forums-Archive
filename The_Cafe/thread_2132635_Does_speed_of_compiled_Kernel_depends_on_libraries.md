---
title: "Does speed of compiled Kernel depends on libraries used?"
date: 2013-04-05
forum: The Cafe
---

### Post by Flo89 on 2013-04-05
Hello :)

There are alternatives out to libc for example newlib etc.. They are supposed to be faster. If I compile a Kernel with that light weight libraries, will the kernel and system run faster? Some of the libraries have not all functions of libc, will then some software not run properly?

Thanks for explaining :)
Florian

---

### Post by MG&amp;TL on 2013-04-05
I think you may be misunderstanding what a kernel does. The kernel is simply the first program (and it is not a program in the normal sense) that gets loaded from your storage medium. It can't use any external libraries at all, as those would have to be loaded from disk, without knowing where on the disk they are yet!

So no, compiling a kernel won't depend upon the libraries used, mostly because there aren't any.

However, if you meant the userspace programs, (everything except the kernel and its modules), then compiling against a different C standard library may or may not give quicker programs, it depends upon whether the program in question actually uses *libc*, and/or whether it uses it extensively. To be honest, there are so many separate programs that it's not worth the effort, and you can just trust that the *libc* standard implementation is 'good enough'. :)

---

### Post by Flo89 on 2013-04-05
Thank you for the explanation!
I'm setting up a cross compiling environment for Arm  and so I have to choose which library to use. I suppose when the Kernel is compiled there will be usage of the functions of the library and therefore I thought there would be a difference in the compiled Kernel! Perhaps you could give me some advice regarding to this!

Best regards and thanks!
Florian

---

### Post by MG&amp;TL on 2013-04-05
> **Flo89 said:**
> Thank you for the explanation!
I'm setting up a cross compiling environment for Arm  and so I have to choose which library to use. I suppose when the Kernel is compiled there will be usage of the functions of the library and therefore I thought there would be a difference in the compiled Kernel! Perhaps you could give me some advice regarding to this!

Best regards and thanks!
Florian

:)

Nope, there isn't any usage of C standard library functions in the kernel as far as I know. For the commonly-used generic ones (like, say, *strcmp*), they tend to write/copy their own and compile it in. For things like file functions, there isn't any point, as the kernel doesn't really know about files except at the hardware levels.

There is no difference if you want to make your kernel faster, as you (probably) won't use *libc* at all for the kernel. If you want to do that, compile the kernel with the menu-based *make*
utility:

```
make menuconfig
```

And only select what you require for the hardware you have. This will *markedly *&#8203;increase performance.

---

### Post by Flo89 on 2013-04-05
Thank you, my friend :)

I'm sure you have remarked that I'm not fimiliar with that kind of stuff (coming from µC world without operating system) but with the help of people like you and some good books I'm sure this will work... In some days :D

---

### Post by MG&amp;TL on 2013-04-06
> **Flo89 said:**
> Thank you, my friend :)

I'm sure you have remarked that I'm not familiar with that kind of stuff (coming from µC world without operating system) but with the help of people like you and some good books I'm sure this will work... In some days :D

:)

Good luck in your quest! Without an operating system seems terrifying to me, but no doubt I'll have to get used to that at some point as well.

---

