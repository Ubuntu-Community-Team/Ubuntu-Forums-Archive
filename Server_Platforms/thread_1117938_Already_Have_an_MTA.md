---
title: "Already Have an MTA"
date: 2009-04-06
forum: Server Platforms
---

### Post by fdamstra on 2009-04-06
I have a third party MTA installed on my server providing SMTP services.  However, Ubuntu doesn't seem to know that it provides the 'mail-transport-agent' virtual package.

So whenever I try to install something that uses mail services, such as logwatch, it wants to install exim.  I don't want it to do this.  

How can I convince the server that it already has an MTA?

---

### Post by brian_p on 2009-04-06
> **fdamstra said:**
> I have a third party MTA installed on my server providing SMTP services.  However, Ubuntu doesn't seem to know that it provides the 'mail-transport-agent' virtual package.

What MTA is it? Does it come in a .deb package?

---

### Post by jettero on 2009-04-06
> **brian_p said:**
> What MTA is it? Does it come in a .deb package?

Personally, I'd like to know how to do this whether it's a .tar or a .deb.  In Gentoo, you can just put an entry in /etc/portage/package.provided.

There simply must be a way to tell the package system that you have something already.

---

### Post by fdamstra on 2009-04-07
> **brian_p said:**
> What MTA is it? Does it come in a .deb package?
It's PowerMTA, a commercial product with Goodmail support, which is a requirement for a client.

It came in an RPM, but I used alien to convert it to a .deb and installed with dpkg -i.

---

### Post by jettero on 2009-04-07
> **fdamstra said:**
>  I used alien to convert it to a .deb and installed with dpkg -i.

Hrm, does alien let you specify virtual packages as a switch?  Can you modify the .dsc or control files?

---

### Post by jettero on 2009-04-08
It seems to me you can do this with the -g option.

alien --scripts -g --to-deb powermta.rpm
cd $tempdir # (whatever it is)

edit the debian/control file and add this to the binary (not source) package:

Provides: mail-transport-agent

then issue: debuild -us -uc and you're golden.

I just tried this myself with a tcl8.5 deb and it totally tried to replace exim4 on my system with tcl.  Hehe.

---

