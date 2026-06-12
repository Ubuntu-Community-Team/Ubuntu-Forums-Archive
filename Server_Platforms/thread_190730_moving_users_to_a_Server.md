---
title: "moving users to a Server"
date: 2006-06-06
forum: Server Platforms
---

### Post by pvonbert on 2006-06-06
We have a small group with a few w2k, one linux box serving printers and personal and comon
directories to around 20 people among profs, students and staff.
The linux box is a poorly PII running Ubuntu 5.10 and I must say thanks to all
developers, updated/upgraded through all the betas of Dapper and now the final one
without any major hitch (must I say I miss the daily updates).
As nobody uses it as a desktop, I thought I reinstall Dapper Server flavor, possible
LAMP, and here comes the question:

How do I transfer the user settings (passwords mainly) to the new system?
I'm sure read that somewhere, but cannot find it, sorry guys.

I'll backup the following files and directories (are this all the files I need to
take care of?).
How do I go on restoring them back?. Tar'ing the /home, /samba and /cups
files is no problem, but how about the /etc/ files (passwd, shadow, gshadow, etc).

If somebody has a reference for this job, which I suppose not very uncommon, it will
be appreciated.

List of files to backup:

/etc/
group
gshadow
hostname
hosts
passwd
protocols
shadow
sudoers
ca-certificates.conf
resolv.conf

/etc/samba
smb.conf

/etc/cups
cupsd.conf
cupsd-browsing.conf
printers.conf

/etc/X11
xorg.conf

/home/
all users dirs

---

