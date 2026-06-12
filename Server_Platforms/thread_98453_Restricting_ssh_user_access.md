---
title: "Restricting ssh user access"
date: 2005-12-03
forum: Server Platforms
---

### Post by juicybananahead on 2005-12-03
Hi there,

I've set up my pc to accept ssh connections from the outside world but now I want to restrict user access when they log into my system. Specifically, I want them only to be allowed access to /home/guest and /home/share . Can anyone help me out here? Could I do this with permissions? I had a look around and chroot seems to be used as well but it mystifies me...

/juicy

---

### Post by LordHunter317 on 2005-12-03
You shouldn't be letting guest users on via SSH ever.  What are you trying to accomplish here?

---

### Post by bluefrog on 2005-12-03
with ssh (if not mistaken) your users have the same right than if they are logged on phisically so they have the rights you've given them.

so if user-paul can see only /home/user-paul it will be the same via ssh

---

### Post by juicybananahead on 2005-12-03
[QUOTE=LordHunter317]You shouldn't be letting guest users on via SSH ever.  What are you trying to accomplish here?[/QUOTE]
I don't want to set up an ftp server because I'm fairly sure that the transmissions aren't encrypted. I'm thinking of letting my friend in Japan (let's call him donal) download WinSCP to his computer and download files from my computer from two specific places: /home/donal and /home/share . Sorry if the guest thing threw you, I just want to let known friends of mine have access but I don't want the transmissions to be unencrypted. ;)

---

### Post by atoponce on 2005-12-03
[quote=juicybananahead]I don't want to set up an ftp server because I'm fairly sure that the transmissions aren't encrypted. I'm thinking of letting my friend in Japan (let's call him donal) download WinSCP to his computer and download files from my computer from two specific places: /home/donal and /home/share . Sorry if the guest thing threw you, I just want to let known friends of mine have access but I don't want the transmissions to be unencrypted. ;)[/quote]

Set donal up as a user on the sever, and only give him access to those two directories by assigning him to a certain group.  You can do this easily using the "User Acount Editor".  When he logs into WinSCP and/or PuTTY, those permissions will be in place.

---

### Post by syslink on 2005-12-11
you could always use denyhosts to restrict ssh access, or sftp if you're concerend about ftp transmissions.

---

### Post by psusi on 2005-12-11
Yes, there is sftp, or you can just install apache and use https.  Nothing like a good SSL connection authenticated with client certificates for good security.  Configuring filesystem access permissions is also more flexible.

---

### Post by J.C. Denton on 2005-12-11
Take a gander at these two sections from the "Securing Debian" manual:
[LIST]
[*][Part 1](http://www.debian.org/doc/manuals/securing-debian-howto/ch-sec-services.en.html#s-chroot)
[*][Part 2](http://www.debian.org/doc/manuals/securing-debian-howto/ch-sec-services.en.html#s-auto-chroot)
[/LIST]
They take about chroot environments, and tools to automagically set them up.  Hope this helps :)!

---

### Post by LordHunter317 on 2005-12-11
[quote=atoponce]
Set donal up as a user on the sever, and only give him access to those two directories by assigning him to a certain group.[/quote]That won't keep him from viewing, only from writing.  If that's a concern, just that won't work.

[QUOTE=psusi]Yes, there is sftp, or you can just install apache and use https.  Nothing like a good SSL connection authenticated with client certificates for good security.  Configuring filesystem access permissions is also more flexible.[/QUOTE]Not for uploading, since mod_webdav doesn't support changing ownership.

You have two solutions, and they're essentially the same: use rssh to chroot his sftp, or use FTP/SSL and chroot him that way.  In either case, you'll probably have to bind mount your shared directory into his home, if you really don't him to be able to view anything.

---

