---
title: "SAMBA4, 13.04 and provision is out of place"
date: 2013-07-11
forum: Server Platforms
---

### Post by BloodyIron on 2013-07-11
I'm setting up a SAMBA4 domain controller on 13.04 because it's the only version to have a non alpha/beta version of SAMBA4 in the package manager.

That aside, I'm actually trying to provision at this point.

Multiple tutorials say the provision tool should be in /usr/share/samba/provision however I can only folders /usr/lib/python2.7/dist-packages/samba/provision/ and /usr/share/pyshared/samba/provision/

Where is the provision tool?

I performed the following command to install:

apt-get install samba4 ntp krb5-user samba4-clients cups


Citations:

[http://www.matrix44.net/cms/notes/gnulinux/samba-4-ad-domain-with-ubuntu-12-04](http://www.matrix44.net/cms/notes/gnulinux/samba-4-ad-domain-with-ubuntu-12-04)

[http://linux-on-a-server.com/samba-4-active-directory-my-first-successfully-test/](http://linux-on-a-server.com/samba-4-active-directory-my-first-successfully-test/)

---

### Post by BloodyIron on 2013-07-11
It looks like I may need to use /usr/bin/samba-tool to provision. Which is in line with the SAMBA4 documentation (apart from location), but not in line with tutorials outside of the SAMBA4 documentation, bleh.

---

### Post by Toxic64 on 2013-08-30
My friend, use my tutorial on how to install Samba4 as an AD DC.

You can find it[ here]("http://ubuntuforums.org/showthread.php?t=2146198").

Obviously you missed the part where you MUST install the prerequisites packages for samba4 to work.

Feel free to skype me if you need help.

---

