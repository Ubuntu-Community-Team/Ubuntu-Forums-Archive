---
title: "SELinux, SSP, etc. on Ubuntu.  Info Please."
date: 2009-05-23
forum: Security
---

### Post by rookcifer on 2009-05-23
I am coming from Fedora and have switched to Kubuntu.  I was wondering if Ubuntu has any plans to compile its packages the way Fedora does -- with SSP, FORTIFY_SOURCE, fstack-protector, etc.. How about Exec-Shield or PaX? Some of these hardening features are now built into GCC, thus it is only a matter of utilizing and testing them.  I read on the Ubuntu wiki that such a plan is in place, but I have no idea if it ever got off the ground.  Can anyone fill me in?  Perhaps Ubuntu is already doing some of this?

My second question pertains to SELinux.  Even though Ubuntu provides an option to install SELinux, there is absolutely no documentation pertaining to it, which is a shame.  About the only documentation I found describes how to install it.  Nothing about policies, troubleshooting, etc.. What exactly is the Ubuntu ref policy?  Is it the same as the "targeted" policy?

---

### Post by cariboo on 2009-05-23
Ubuntu uses Appamour instead of Selinux, have a look at this [thread=1008906]sticky[/thread].

---

### Post by rookcifer on 2009-05-23
> **cariboo907 said:**
> Ubuntu uses Appamour instead of Selinux, have a look at this [thread=1008906]sticky[/thread].

But Selinux can indeed be used as per :

[https://wiki.ubuntu.com/SELinux](https://wiki.ubuntu.com/SELinux)

[https://help.ubuntu.com/community/SELinux](https://help.ubuntu.com/community/SELinux)

I am just wondering if there is any other documentation anywhere besides the above links which do nothing but explain how to install it.

---

### Post by HermanAB on 2009-05-23
If you want to use SELinux, install Redhat or CentOS.

---

### Post by rookcifer on 2009-05-23
> **HermanAB said:**
> If you want to use SELinux, install Redhat or CentOS.

As I said in my initial post, I am coming from Fedora and do not wish to go back (for reasons unrelated to this).  So, Red Hat/Fedora is not a possibility.  If Selinux is not recommened, that's fine, I was just wondering if there was any documentation on it (because Selinux can be used as I proved with the links in my previous post).

And does anyone know about Ubuntu's plans to implement SSP, fstack-protector, FORTIFY_SOURCE, etc..?  Or Exec-Shield or PaX?  Google turns up a lot of "brain storming" posts about this, but I am unsure of the status of these hardened projects.

---

### Post by HermanAB on 2009-05-23
The only distribution house that supports SELinux is Redhat.

---

### Post by rookcifer on 2009-05-23
> **HermanAB said:**
> The only distribution house that supports SELinux is Redhat.

Then, what's this all about:


[https://wiki.ubuntu.com/SELinux]("https://wiki.ubuntu.com/SELinux")

and this:

[https://help.ubuntu.com/community/SELinux]("https://help.ubuntu.com/community/SELinux")

And Red Hat is not the only distribution that supports Selinux.  Gentoo supports it (I know because I used Gentoo).  Debian supports it.  Fedora (part of Red Hat) supports it.  And according to Wikipedia, Ubuntu as of 8.04 supports it.

---

### Post by Jestersage on 2009-05-24
So how is apparmor compared to SELinux in terms of security?

---

### Post by cariboo on 2009-05-24
HAve a look at this [page]("http://www.novell.com/linux/security/apparmor/selinux_comparison.html") for a comparison of Apparmour and Selinux

---

### Post by movieman on 2009-05-24
> **Jestersage said:**
> So how is apparmor compared to SELinux in terms of security?

Basically apparmor is simpler but less secure: in particular, since it's pathname-based, renaming the executable eliminates any protection you previously had.

But for 90% of users it's perfectly adequate.

---

