---
title: "Recommendation to update your kernel to v3.0.1 bugs fixed"
date: 2011-08-10
forum: Security
---

### Post by wacky_sung on 2011-08-10
I will strongly encourage you to update your current kernel version to the latest for the bugs fixed and security as well.

_Location to get the latest kernel version_
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

_Steps to install the new kernel_
[http://www.howopensource.com/2011/08/how-to-install-linux-kernel-3-0-in-ubuntu-11-04-10-10-and-10-04/](http://www.howopensource.com/2011/08/how-to-install-linux-kernel-3-0-in-ubuntu-11-04-10-10-and-10-04/)

:guitar::guitar::guitar::guitar::guitar::guitar:

---

### Post by uRock on 2011-08-10
The current supported kernels get security patches. There is no reason to upgrade to an unsupported kernel.

---

### Post by bodhi.zazen on 2011-08-10
> **uRock said:**
> The current supported kernels get security patches. There is no reason to upgrade to an unsupported kernel.

I agree.

Compiling your own kernel is not trivial or easy, and the Ubuntu kernel is patched.

You can use the ppa

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Also be aware that the new kernel, 3.0.x , is in rapid development and last time I tried it I had breakage.

@wacky_sung - From your recent posts it seems you feel the Ubuntu repositories are out of date. I would suggest you use gentoo or arch linux for what you want.

Also, as I mentioned in your other thread, you should be using Launchpad, and not the forums, for bug reports, including security concerns.

Also, unless you are willing to personally support users compiling a custom kernel, probably not a good thing to advise.

---

### Post by wacky_sung on 2011-08-11
> I agree.

Compiling your own kernel is not trivial or easy, and the Ubuntu kernel is patched.

You can use the ppa

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Also be aware that the new kernel, 3.0.x , is in rapid development and last time I tried it I had breakage.

Ans: Isn't i pointing people to use the link i have provided to use it or they can try to compile it themselves. It is undeniable there are bugs and instability in testing new kernel but the latest 3.0.1 is a stable version.I have tested it out and it's working fine.If you think it is a poison, other may take it as an antidote.


> @wacky_sung - From your recent posts it seems you feel the Ubuntu repositories are out of date. I would suggest you use gentoo or arch linux for what you want.

Ans: I did appreciated for you suggestion and i look forward to test it out.

> 
Also, as I mentioned in your other thread, you should be using Launchpad, and not the forums, for bug reports, including security concerns.

Also, unless you are willing to personally support users compiling a custom kernel, probably not a good thing to advise.

Ans: For donkey years I have been self learn security through forums, reading and testing of security as my personal interest. I am not keen to fill for those bug reports because i am tried of it and you have to continue to followup until it has been confirmed to be a bugs.Since in the beginning i have already confirm to break it which can regard to an web application bug. I always believe submit those bugs to bugs search engines which eventually speed up the process and force the developer to patch it fast.

By the way,I just follow the guide as below to install the new kernel.Is that so difficult as ABC.
[http://linuxpoison.blogspot.com/2011/08/how-to-install-latest-kernel-30-on.html](http://linuxpoison.blogspot.com/2011/08/how-to-install-latest-kernel-30-on.html)

.

---

### Post by bodhi.zazen on 2011-08-11
LOL, that link is a guide on installing the kernel from the ppa I already advised.

I would use the ppa rather then downloading the deb, adding the ppa means you will get updates.

Yes bug reports are frustrating, but you need to understand the process.

[https://bugzilla.redhat.com/show_bug.cgi?id=729748](https://bugzilla.redhat.com/show_bug.cgi?id=729748)

That bug was fixed in less then 24 hours, it is not that difficult.

If you want bugs fixed you need to talk the talk and walk the walk.

Look at the links I have given you, join the bug squad.

[http://www.chiark.greenend.org.uk/~sgtatham/bugs.html](http://www.chiark.greenend.org.uk/~sgtatham/bugs.html)

Yes, you need to learn to communicate effectively with the developers, and yes there is a learning curve.

---

### Post by cariboo on 2011-08-11
Reporting a bug is pretty straight forward, provide the developers with as much information as possible, including a way to reproduce the problem. You should get a reply to your bug within a couple of hours, especially in the case of a kernel/security problem.

---

### Post by wacky_sung on 2011-08-12
@ bodhi.zazen + cariboo907

Thank for showing me how to file for those bugs. Pardon me for being a headstrong person. I can only say once bitten shy twice. I prefer to submit through search engines.Not all bugs in which developers reacted as mentioned. I have witness those real security issues being directed to the developers but not action taken until release to the public.Probably i am those problematic buggers finder and dislike to report to the developer directly. By the way, i did no damage to those web application bugs found within a site.

---

### Post by uRock on 2011-08-12
You don't want to report bugs, yet you want them to get fixed? Most of the security flaws you have learned about require someone to install bad code on their system in order to cause the insecurity. This is why people are recommended to stick with the official repos when installing applications.

---

### Post by eveg on 2011-08-12
> **uRock said:**
> The current supported kernels get security patches. There is no reason to upgrade to an unsupported kernel.
 thank you

---

### Post by wacky_sung on 2011-08-12
> **uRock said:**
> You don't want to report bugs, yet you want them to get fixed? Most of the security flaws you have learned about require someone to install bad code on their system in order to cause the insecurity. This is why people are recommended to stick with the official repos when installing applications.

I think you totally does not understand my intention by submitting to those opensource bugs search engines.

[http://www.exploit-db.com/](http://www.exploit-db.com/)
[http://osvdb.org/](http://osvdb.org/)
[http://1337day.com/](http://1337day.com/)

Why you are so scare of bad code?The reasons behind those malicious codes are people who has ill intention.People stick with official repos because they do not read the source code of the non official repos.

---

### Post by uRock on 2011-08-12
> **wacky_sung said:**
> I think you totally does not understand my intention by submitting to those opensource bugs search engines.

[http://www.exploit-db.com/](http://www.exploit-db.com/)
[http://osvdb.org/](http://osvdb.org/)
[http://1337day.com/](http://1337day.com/)

Why you are so scare of bad code?The reasons behind those malicious codes are people who has ill intention.People stick with official repos because they do not read the source code of the non official repos.

I am not scared of bad code. I get my code from trusted sources. There is no benefit for me to upgrade to an unsupported kernel. 

There may be holes in my current kernel which may need patching, but we come back to the problem of access. How would a hacker get "bad" code on my system to take advantage of the "holes" in my kernel? 

The new kernel may fix some exploits, but what about the unknown exploits which are lurking in the new kernel?

---

### Post by wacky_sung on 2011-08-12
> **uRock said:**
> I am not scared of bad code. I get my code from trusted sources. There is no benefit for me to upgrade to an unsupported kernel. 

There may be holes in my current kernel which may need patching, but we come back to the problem of access. How would a hacker get "bad" code on my system to take advantage of the "holes" in my kernel? 

The new kernel may fix some exploits, but what about the unknown exploits which are lurking in the new kernel?

I think you are not talking with senses.Did you see where is the link for the source i getting the compile kernel?FYI those kernel are compiled for the Ubuntu 11.10.

---

### Post by uRock on 2011-08-12
> **wacky_sung said:**
> I think you are not talking with senses.Did you see where is the link for the source i getting the compile kernel?FYI those kernel are compiled for the Ubuntu 11.10.

Yes, they are compiled for 11.10, but I am not running 11.10. My desktops are humming along with 10.04 and my netbook with 11.04. If I needed hardware compatibilities offered by the new kernel, then I would do it, but when it comes to security I feel safe with what I have. It is not worth it, IMHO, to upgrade the kernel and risk breakage.

BTW, I appreciate that you are offering up info on the new kernel. For those who need, it may be a good thing.:)

---

