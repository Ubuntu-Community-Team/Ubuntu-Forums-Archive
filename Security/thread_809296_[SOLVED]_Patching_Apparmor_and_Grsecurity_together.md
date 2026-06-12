---
title: "[SOLVED] Patching Apparmor and Grsecurity together, is it possible?"
date: 2008-05-27
forum: Security
---

### Post by PmDematagoda on 2008-05-27
I was wondering if there was any way one could patch Apparmor onto a kernel and then patch Grsecurity on top of it(or the other way around, I don't really care:)), the fact is that I can easily patch Apparmor or Grsecurity seperately, but when it comes to patching them together I always get patching errors and I am unable to proceed further.

---

### Post by cookie971 on 2008-06-19
> **PmDematagoda said:**
> I was wondering if there was any way one could patch Apparmor onto a kernel and then patch Grsecurity on top of it(or the other way around, I don't really care:)), the fact is that I can easily patch Apparmor or Grsecurity seperately, but when it comes to patching them together I always get patching errors and I am unable to proceed further.

Why would you want to do that ? Can you please share your thoughts? 

I'm asking you this because AppArmor and Grsecurity do almost the same thing, they do ACL approx the same way using policy files, except for grsecurity which in my personal belief is much better just becuase of the nefty features in addition to ACL, like hiding processes, securing the chroot jail etc... Grsecurity should suit your needs if you configure it well, just watch out for PAX it could be a little too violent for some applications.

Cookie

---

### Post by PmDematagoda on 2008-06-20
> **cookie971 said:**
> Why would you want to do that ? Can you please share your thoughts? 

I'm asking you this because AppArmor and Grsecurity do almost the same thing, they do ACL approx the same way using policy files, except for grsecurity which in my personal belief is much better just becuase of the nefty features in addition to ACL, like hiding processes, securing the chroot jail etc... Grsecurity should suit your needs if you configure it well, just watch out for PAX it could be a little too violent for some applications.

Cookie

Thanks for that information cookie971, I talked to a person earlier who had experience with such systems and he told me that it was either Grsec or apparmor and not both together. The last time I used Grsec it was without PAX and it worked, but after I turned PAX on and turned some features on then it all went wrong, so I have to get some more experience in PAX.

---

### Post by /etc/init.d/ on 2008-06-20
PaX alone is the reason why Grsecurity provides more overall security than AppArmor.  Also, Grsecurity has a superb RBAC system -- I don't have much experience with AppArmor but I can't imagine it beating Grsecurity in this area. 

Unfortunately, the downloadable Grsecurity documentation is useless, but the help text associated with the kernel config options is very useful in deciding what to turn on.  I think you press shift+? while configuring the kernel to display them.

PaX will sometimes break legitimate applications, but there is a utility called chpax (I think the name has changed now though) that allows you to turn off PaX on a per-binary basis.

The latest grsec "test patch" is for 2.6.25.7, but I consider them stable releases.  The reason why they aren't "stable" is because there are still some bugs with PaX on 64-bit SMP kernels.

---

### Post by PmDematagoda on 2008-06-20
You can see the help text in config options by default when using xconfig to configure the kernel(it's in a section of the window), which is a reason why I like it so much:).

I'll give chpax(or whatever it's name is) a try as well, one thing about AppArmor, it is really easy to use, just know the basics and have a good example profile at hand and it becomes very easy to manage and use(oh, and keep an eye on the audit logs;)).

---

