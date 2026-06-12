---
title: "Security question about repositories?"
date: 2005-09-20
forum: Server Platforms
---

### Post by ry_ry on 2005-09-20
I have the Universe repository enable in my sources.list and sometimes security updates come from there. Are these safe? How secure are these repos. anyway?

I know in the sources.list file Ubuntu states that they don't provide support for the Universe and Multiverse repos., so I'm wondering if getting any security updates from these two repos. are safe?

Also is getting packages from the Backports safe also, since the Ubuntu team has not checked these out too?

---

### Post by Mustard on 2005-09-20
I would think that only those repositories that are officially supported and that use the secure signatures, are the ones that are 'secure'.

---

### Post by ry_ry on 2005-09-21
[QUOTE=Mustard]I would think that only those repositories that are officially supported and that use the secure signatures, are the ones that are 'secure'.[/QUOTE]

So using the Universe, Multiverse and Backports are a bad idea, since they are not secure? Why are the Universe and Multiverse even included in the sources.list right out of a new install if they are unsafe and unsecure?

I guess I'll have to reformat and start all over again, and make sure not to use the Universe, Multiverse and Backports repositories again since they are unsafe and unsecure. Someone should tell the Unofficial Ubuntu Guide to remove those extra repositories from their guide since they are dangerous to your install.

Well, this sucks. There should be a sticky or some big warning in the forums about how unsecure and unsafe these extra repositories are.

Thanks for your input. I off to wipe my system and reformat, reinstall and make sure not to use the Universe, Multiverse and Backports at all. Looks like I've got alot more work to do. After a month and a half of trying to get everything configured and worked out, now I'm back to square one, and now to start over again. :(  I should have known not to use the extra repositories.  ](*,)

---

### Post by LordHunter317 on 2005-09-21
[QUOTE=Mustard]I would think that only those repositories that are officially supported and that use the secure signatures, are the ones that are 'secure'.[/QUOTE]Nope.  Even that process has holes where a trojan can sneak in: it requires due dilligence on the part of the developer.  One mistake and you still end up with something you didn't intend to.

It really comes down to who you decide you can trust.

If you're ok with Universe etc. not having official security updates when something goes bad, then they're not for you.  If you're OK with that, then use them.  If you're not, then don't.

---

### Post by matthew on 2005-09-21
[QUOTE=ry_ry]So using the Universe, Multiverse and Backports are a bad idea, since they are not secure? Why are the Universe and Multiverse even included in the sources.list right out of a new install if they are unsafe and unsecure?

I guess I'll have to reformat and start all over again, and make sure not to use the Universe, Multiverse and Backports repositories again since they are unsafe and unsecure. Someone should tell the Unofficial Ubuntu Guide to remove those extra repositories from their guide since they are dangerous to your install.

Well, this sucks. There should be a sticky or some big warning in the forums about how unsecure and unsafe these extra repositories are.

Thanks for your input. I off to wipe my system and reformat, reinstall and make sure not to use the Universe, Multiverse and Backports at all. Looks like I've got alot more work to do. After a month and a half of trying to get everything configured and worked out, now I'm back to square one, and now to start over again. :(  I should have known not to use the extra repositories.  ](*,)[/QUOTE]
May I gently suggest you try to keep the spreading of FUD (fear, uncertainty, doubt) to a minimum? If you are uncomfortable using those repos, that is fine. In the original sources.list they are not automatically enabled but must be activated by the user who wants to use them. They are also accompanied by the following text:
> ## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
I think it is pretty clear from the beginning that the software contained within those repos comes with no warranty. No one is attempting to deceive anyone here. There is no underground conspiracy to slip something past you. If you activated those repos without reading the comments and are now frustrated that you have done so, I'm sorry. Screaming that they are "unsafe and insecure" is not necessary. It just makes you come across as paranoid and ungrateful to those who have put forth a lot of effort to provide those repos for those who want them. If you are not among that number, no hard feelings here, just don't use them. No need to take to the streets in doomsday prophet mode.

---

### Post by skoal on 2005-09-21
Locked. ry_ry, I think we understand your concern, as you see it.  Posting several times over and over again (on the same topic) just seems pointless.

/edit - Follow the other discussion here: [http://www.ubuntuforums.org/showthread.php?t=67896](http://www.ubuntuforums.org/showthread.php?t=67896)

\\//_

---

