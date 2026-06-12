---
title: "[SOLVED] Ubuntu to CentOS help"
date: 2008-06-10
forum: Server Platforms
---

### Post by altonbr on 2008-06-10
I love Ubuntu; I use it on all my servers and all my desktops (including my family, friends, strangers, etc.) but I'm stuck with a job that requires CentOS.

I'm getting quite frustrated with the differences between Ubuntu/Debian and CentOS (such as /etc/aoache2/ being found at /etc/httpd/ and non-modular, or the lack of APT (you don't know what you're missing until its gone).

I understand this is an Ubuntu forum, believe me, I have 1000+ posts, but does anyone know of any resources on Ubuntu/Debian -> CentOS or have any tips for me?

---

### Post by HalPomeranz on 2008-06-10
This should help:

[https://help.ubuntu.com/community/SwitchingToUbuntu/FromLinux/RedHatEnterpriseLinuxAndFedora](https://help.ubuntu.com/community/SwitchingToUbuntu/FromLinux/RedHatEnterpriseLinuxAndFedora)

It's a translator for people who are new to Ubuntu but familiar with Red Hat.  But you can also use it the other way.

---

### Post by atoponce on 2008-06-10
Going from Debian/Ubuntu to CentOS/Red Hat is like going from driving a Chevrolet to a Pugot.  You've got some learning curves ahead of you.

First, the /etc/default/ directory is the same as /etc/sysconfig in Red Hat.  Further, Red Hat likes to keep a close relationship with the BSD style of stuff, so packages are named as they were originally implemented- like you discovered with apache2/httpd.  Also, Red Hat mistakenly implemented SystemV init as BSD style with the implementation of /etc/rc.d/.

On top of that, you'll probably at some point notice the availability of centralized tools, such as the system-config-* tools.  Of course, SELinux will be a major learning curve, if you're familiar with AppArmor, as well as Xen over KVM.  YUM versus APT is another killer that will get you.  However, RPM has some great features that DPKG does not, such as "rpm -V".

Ultimately, the best way to learn is through CentOS or Fedora in a virtual machine, and start tinkering.  You've got some learning ahead of you, so you might as well get started. :)

---

### Post by altonbr on 2008-06-10
Asbolustely amazing advise from both of you, thank you! I'll tell you how it goes!

I also asked the company that owns this dedicated box to see if they can switch from CentOS to Ubuntu (or at the very least Debian) before we get started on the project. Its not so much lazy as its just what I'm comfortable in; I have almost 100 scripts and I'm sure each one will have to be modified in some way to work in CentOS (ie: "sudo aptitude install ...")

Anyway, thank you again :)

---

### Post by ibutho on 2008-06-10
> **altonbr said:**
> Asbolustely amazing advise from both of you, thank you! I'll tell you how it goes!

I also asked the company that owns this dedicated box to see if they can switch from CentOS to Ubuntu (or at the very least Debian) before we get started on the project. Its not so much lazy as its just what I'm comfortable in; I have almost 100 scripts and I'm sure each one will have to be modified in some way to work in CentOS (ie: "sudo aptitude install ...")

Anyway, thank you again :)

In my opinion, I think its best that you learn the Red Hat way of doing things instead of trying to convert the company to a different platform. If you are a Linux sysadmin, you should be able to adjust to the platform of choice of your employer or clients. In the long run, the experience you gain can make you more marketable. I had a similar experience to yourself a few years back, but the opposite way. I was used to Red Hat and Novell platforms, but a client wanted me to help them deploy an Ubuntu server. At that time I really detested Debian and Ubuntu, but I had to quickly get to grips with them so that I could help our client. Anyway, the good thing that came out of this is that I learnt to appreciate Debian and related distros although they were different to the platforms I was used to administering.

---

### Post by altonbr on 2008-06-10
> **ibutho said:**
> In my opinion, I think its best that you learn the Red Hat way of doing things instead of trying to convert the company to a different platform. If you are a Linux sysadmin, you should be able to adjust to the platform of choice of your employer or clients. In the long run, the experience you gain can make you more marketable. I had a similar experience to yourself a few years back, but the opposite way. I was used to Red Hat and Novell platforms, but a client wanted me to help them deploy an Ubuntu server. At that time I really detested Debian and Ubuntu, but I had to quickly get to grips with them so that I could help our client. Anyway, the good thing that came out of this is that I learnt to appreciate Debian and related distros although they were different to the platforms I was used to administering.

That's very true, I shouldn't be so short-sighted.

Plus, if my scripts were modified to run on multiple distros, how much more powerful would that be?

---

