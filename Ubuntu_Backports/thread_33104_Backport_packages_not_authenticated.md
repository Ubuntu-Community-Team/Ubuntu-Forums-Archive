---
title: "Backport packages not authenticated?"
date: 2005-05-09
forum: Ubuntu Backports
---

### Post by dewey on 2005-05-09
I haven't been able to use the backports for awhile now, because of the authentication, and have waited around 2 weeks to see if it would fix itself, without luck.
```
dewey@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  libavcodeccvs libpostproc0 libxvidcore4 mplayer-386
The following packages will be upgraded:
  firestarter freeciv freeciv-client-gtk freeciv-data freeciv-server gaim
  gaim-data gaim-encryption gimp gimp-data gimp-python gnome-menus libgimp2.0
  libgnome-menu0 libsmbclient mozilla-firefox mozilla-firefox-gnome-support
  prelink python-xdg samba samba-common smbclient synaptic
23 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 38.0MB of archives.
After unpacking 1401kB disk space will be freed.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  firestarter freeciv-data freeciv-server freeciv-client-gtk freeciv gaim
  gaim-data gaim-encryption gimp gimp-data libgimp2.0 gimp-python
  libgnome-menu0 gnome-menus mozilla-firefox-gnome-support mozilla-firefox
  prelink python-xdg smbclient samba samba-common synaptic libsmbclient
Install these packages without verification [y/N]? n
E: Some packages could not be authenticated

```
When I disable the backport repo, none of the packages want to be upgraded, is there any way I can get them to authenticate properly?

---

### Post by dewey on 2005-05-10
No ideas?  Is there anyway to clear my backport keys and redownload them or something. in case there is a conflict?

---

### Post by XDevHald on 2005-05-10
[QUOTE=dewey]No ideas?  Is there anyway to clear my backport keys and redownload them or something. in case there is a conflict?[/QUOTE]
 This issue is still being instate of being resolved, I did contact the developer of synaptic to find out a way to possibly disable the error and/or sign the packages, but the only thing I find useful of what he said was "[i]The admin of the backports is going to need to sign each package individually or setup a way to get them to authenticate automatically on send out"

[/i]Reason why the packages have been kept back is due to the version not being stable with the repo that you installed and/or have installed but has recent dependencies that go with it, but the versions need to be upgraded. You'll need to wait for the updates or do a request for the dependencies/repo's you're needing to make your dependencies install correctly.

This is not enough info, I know, but if you need more, please contact jdong for more info.

---

### Post by Firetech on 2005-05-11
[QUOTE=dewey]When I disable the backport repo, none of the packages want to be upgraded, is there any way I can get them to authenticate properly?[/QUOTE]
 Not yet (It is safe to continue without authentication... Atleast, I do so...), but the held back packages could be upgraded using "sudo apt-get dist-upgrade", which will fix that kind of issues. That command can REMOVE packages though, so look carefully before accepting the changes!

---

### Post by jdong on 2005-05-11
Ugh, the last time I tried signing, I corrupted all the debs in the repo. You can just answer "y" to the warning, and it'll continue to install.


Google the board -- I've discussed a few times why I havent' been rushing to implement signing.

---

### Post by dewey on 2005-05-11
[QUOTE=jdong]Google the board -- I've discussed a few times why I havent' been rushing to implement signing.[/QUOTE]
I looked around and noticed the problems with signing the packages, I just didn't see anyone complaining about the authentication issue now, so I figured it was only me.

---

### Post by ingo.lists@vum.at on 2005-08-15
> I looked around and noticed the problems with signing the packages, I just didn't 
> see anyone complaining about the authentication issue now, so I figured it was 
> only me.
Not only you - I had the same concern; but thanks to this thread I decided to hit the "y". Hope once the signing-problem can be solved.
Ingo.

---

