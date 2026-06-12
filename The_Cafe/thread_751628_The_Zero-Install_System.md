---
title: "The Zero-Install System"
date: 2008-04-10
forum: The Cafe
---

### Post by skymera on 2008-04-10
Just Stumbled across this link.
Seems very good and secure, check out the link for more info and a video guide.

[http://zero-install.sourceforge.net/](http://zero-install.sourceforge.net/)

Your thoughts?

---

### Post by cardinals_fan on 2008-04-10
> **skymera said:**
> Just Stumbled across this link.
Seems very good and secure, check out the link for more info and a video guide.

[http://zero-install.sourceforge.net/](http://zero-install.sourceforge.net/)

Your thoughts?
I see that this is written by the guy behind ROX, which is a very good piece of work.  It looks like it could be really awesome, so I'm trying it now.  I'll post back with results...

EDIT:  I've tried it.  In most ways, this seems really nice.  Unfortunately, it will only work on special feeds designed for 0launch.  So, it's really just a package management system for any distro - still a great program, but not useful *yet*...

---

### Post by madjr on 2008-04-10
> **cardinals_fan said:**
> I see that this is written by the guy behind ROX, which is a very good piece of work.  It looks like it could be really awesome, so I'm trying it now.  I'll post back with results...

EDIT:  I've tried it.  In most ways, this seems really nice.  Unfortunately, it will only work on special feeds designed for 0launch.  So, it's really just a package management system for any distro - still a great program, but not useful *yet*...

it would be great if all distros supported this method...

or maybe we should help compile those packages to work with zero-install and add the feeds.

this could be an universal solution.

your distro don't have "X" package? then install zero-install and get the package (of course we would need to work on the packaging).

i gotta see if the same piece of software would work in fedora 9 beta and hardy,  or gutsy and hardy...

interesting

---

### Post by p_quarles on 2008-04-10
I'm not really seeing the point. It basically downloads and installs applications to your home directory. This doesn't seem particularly helpful, and I have some concerns about the actual security implications of something like this. While it may be convenient to install software "without having to be root," that doesn't make it wise. If this became widely adopted, it would be easy to start distributing code that would steal all the usual unencrypted information in the home directory. In other words, if you'd rather keep the passwords that Firefox has stored to yourself, this might raise some red flags.

---

### Post by talex5 on 2008-04-13
> **p_quarles said:**
> I'm not really seeing the point. It basically downloads and installs applications to your home directory.

You can turn on sharing by following these instructions:

[http://0install.net/sharing.html](http://0install.net/sharing.html)

> This doesn't seem particularly helpful, and I have some concerns about the actual security implications of something like this. While it may be convenient to install software "without having to be root," that doesn't make it wise. If this became widely adopted, it would be easy to start distributing code that would steal all the usual unencrypted information in the home directory. In other words, if you'd rather keep the passwords that Firefox has stored to yourself, this might raise some red flags.

You're comparing "Installing something with Zero Install" with "Not installing it". Not installing software is indeed more secure, but not very useful.

However, try comparing "Installing something with Zero Install" with "Installing the same thing as a .deb". Note that all the problems you listed also affect .deb packages, as well as executable shell scripts, tarballs, etc, today.

---

### Post by p_quarles on 2008-04-13
> **talex5 said:**
> You can turn on sharing by following these instructions:

[http://0install.net/sharing.html](http://0install.net/sharing.html)
That really wasn't my concern. 

> You're comparing "Installing something with Zero Install" with "Not installing it". Not installing software is indeed more secure, but not very useful.
I am? That's news to me. I had thought I was comparing to using a secure and established method of installing software to an insecure and untested method. 

> However, try comparing "Installing something with Zero Install" with "Installing the same thing as a .deb". Note that all the problems you listed also affect .deb packages, as well as executable shell scripts, tarballs, etc, today.
You won't find me suggesting that people install every single .deb package they find on dark corners of the internet. The packages in the repositories for major distributions, on the other hand, are subject to a great deal of scrutiny and are consequently much more safe.

As for source packages and shell scripts -- that's simply incorrect. Binaries are -- and will always be -- a potential vector for easy malware distribution. While high-level languages can also deliver negative effects, the nature of open code prevents it from being hidden.

---

### Post by talex5 on 2008-04-17
> **p_quarles said:**
> That really wasn't my concern. 
I am? That's news to me. I had thought I was comparing to using a secure and established method of installing software to an insecure and untested method. 


If you're comparing the source of the packages then that's fine, but it doesn't have much to do with the packaging system.

If you only run software approved and reviewed by your distribution, then it should be safer (or at least as safe) if the reviewed package is distributed with Zero Install (because it doesn't run as root, can't corrupt other packages at install time, etc, even by accident).

If you run software from less trusted sources then that's obviously more risky whatever you do, but slightly less so if using Zero Install.

For example, from best to worst:

1. Get a Zero Install package of ROX Edit approved by Ubuntu (note: not available).
2. Get a .deb package of ROX Edit approved by Ubuntu (note: not available).
3. Get a Zero Install package of ROX Edit from its developer (assuming they have a good reputation).
4. Get a .deb package from the developer (note: not available).

> 
As for source packages and shell scripts -- that's simply incorrect. Binaries are -- and will always be -- a potential vector for easy malware distribution. While high-level languages can also deliver negative effects, the nature of open code prevents it from being hidden.

See: [http://www.vnunet.com/vnunet/news/2119652/puzzling-trojan-affects-openssh](http://www.vnunet.com/vnunet/news/2119652/puzzling-trojan-affects-openssh) (vulnerability affecting only the source package)

Virtualisation / sandboxing is likely to give you more safety than reading the source.

Finally, note that both .deb and Zero Install packages can be downloaded as binaries or compiled from source, at the user's choice.

---

