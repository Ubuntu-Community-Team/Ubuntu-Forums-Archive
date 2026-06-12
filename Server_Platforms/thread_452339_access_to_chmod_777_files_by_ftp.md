---
title: "access to chmod 777 files by ftp"
date: 2007-05-23
forum: Server Platforms
---

### Post by ryu kun on 2007-05-23
It is told everywhere that we shouldn't keep our files' permissions 777 in a ftp folder. But I don't understand how one can change those files. First they should login to my ftp server, don't they? So they need a ftp username/password? If someone doesn't have such an account, how can it be possible for him to change a [777] file in a subfolder on my ftp server?

---

### Post by kidders on 2007-05-24
Hi there,

The main concern is that if you intentionally create security holes in your Linux box, it's inevitable that, sooner or later, you'll forget to take account of one of them, and get badly bitten. It's important to bear in mind that security problems often arise as a result of a *combination* of mistakes, rather than just one.

Examples of possible risks in your case include...[LIST]
[*]Inappropriate execute permissions can cause code to run locally, even though (by definition) it was never intended to do so. Since this would only ever be done by a malicious user (and that user would also have the authority to arbitrarily modify the contents of the file), serious damage could be caused. For example, *everything* else on your entire system with improper permissions could be deleted.
[*]By inappropriately allowing write access to things, viruses could be injected into files ... possibly unintentionally. Your FTP server would then become a distribution point for malicious software, designed to damage other systems.
[*]Inappropriate read permissions negate file ownership, which is an important tool for controlling filesystem access.
[/LIST]

These, and a wide range of others could be exploited...[LIST]
[*]Locally, by a malicious user, without involving FTP at all.
[*]Remotely over FTP, or over other communications protocols.
[*]Via a bug in your FTP software, a web server, or anything else.
[*]Via an unrelated pre-existing security hole, or one you create in the future.
[/LIST]

When thinking about filesystem security...
[LIST]
[*]Remember that FTP is an outdated and highly vulernable protocol.
[*]Always assume a malicious user is either not going to use a valid username & password to access your files, or has guessed someone's.
[*]Ignore FTP altogether, and consider what might happen if someone got access to your system by some other means.
[/LIST]

I hope that's of some help. In general, if you find yourself typing **chmod 777 ...**, you are almost certainly making a mistake. Unfortunately, it's one that Linux will absolutely crucify you for. :-(

[SIZE=1][COLOR=Silver][*[UAResolved]*]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR][/SIZE]

---

