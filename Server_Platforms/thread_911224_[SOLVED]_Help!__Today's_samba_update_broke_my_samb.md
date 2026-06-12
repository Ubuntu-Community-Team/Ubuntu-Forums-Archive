---
title: "[SOLVED] Help!  Today's samba update broke my samba server"
date: 2008-09-05
forum: Server Platforms
---

### Post by CaptSaltyJack on 2008-09-05
I did an apt-get upgrade today, which updated samba (to 3.0, I think).  I noted the new changes in the smb.conf and merged them with my own smb.conf file.  Did a restart.

Now, smbpasswd refuses to work:

```

$ smbpasswd
Old SMB password:
New SMB password:
Retype new SMB password:
Could not connect to machine 127.0.0.1: NT_STATUS_LOGON_FAILURE
Failed to change password for (my username)

```

Surely someone else has got to be having the same problem since the update.  How do I fix this?

---

### Post by HermanAB on 2008-09-05
Hmm, don't fix your computer if it isn't broken.  Windows systems are permanently broken, so with that OS, constant updates is usually a good idea - not so with Linux.

Most Linux problems are caused by finger trouble and updates.  I re-install my machines once every year or three and once they are working properly, I leave them alone.  This way, I can easily get multi-year uptimes.

Cheers,

Herman

---

### Post by Krupski on 2008-09-05
> **CaptSaltyJack said:**
> I did an apt-get upgrade today, which updated samba (to 3.0, I think).  I noted the new changes in the smb.conf and merged them with my own smb.conf file.  Did a restart.

Now, smbpasswd refuses to work:

```

$ smbpasswd
Old SMB password:
New SMB password:
Retype new SMB password:
Could not connect to machine 127.0.0.1: NT_STATUS_LOGON_FAILURE
Failed to change password for (my username)

```

Surely someone else has got to be having the same problem since the update.  How do I fix this?

Strange. I also did an update today on my fileserver box and noticed that Samba got updated. However, 'smb.conf' did not get modified in any way, and the shares still work as before.

Try this: rename your 'smb.conf' file to something else to get it out of the way, then try running 'smbpasswd' again.

---

### Post by CaptSaltyJack on 2008-09-05
Yeah the shares work fine.  I just can't change my SMB password.  It's highly possible this was broken before today's update.

At any rate:

```

$ sudo mv smb.conf smb.konf
$ smbpasswd
Can't load /etc/samba/smb.conf - run testparm to debug it

```

---

### Post by CaptSaltyJack on 2008-09-05
(sigh) Nevermind.. sudo smbpasswd (user) worked.  Apparently I was typing the wrong password for my "old" password.  Go figure (I'm almost positive I knew what it was).

I guess a message more like "incorrect password" rather than "could not connect, logon failure" would be a little more appropriate.

---

### Post by Krupski on 2008-09-05
> **CaptSaltyJack said:**
> (sigh) Nevermind.. sudo smbpasswd (user) worked.  Apparently I was typing the wrong password for my "old" password.  Go figure (I'm almost positive I knew what it was).

I guess a message more like "incorrect password" rather than "could not connect, logon failure" would be a little more appropriate.

I suspected that's what happened... that's why I suggested renaming smbpasswd to get it out of the way!  :)

---

### Post by windependence on 2008-09-06
> **HermanAB said:**
> Hmm, don't fix your computer if it isn't broken.  Windows systems are permanently broken, so with that OS, constant updates is usually a good idea - not so with Linux.

Most Linux problems are caused by finger trouble and updates.  I re-install my machines once every year or three and once they are working properly, I leave them alone.  This way, I can easily get multi-year uptimes.

Cheers,

Herman

Ditto that. I only apply security updates and then ONLY if they are really needed.......because *nix just runs. ;)

-Tim

---

### Post by Piraja on 2008-09-06
> **HermanAB said:**
> Most Linux problems are caused by finger trouble and updates.

Maybe so — but updates can also fix problems. I accepted today's Samba updates and realized that an annoying bug has been fixed (see [https://bugs.launchpad.net/bugs/216104](https://bugs.launchpad.net/bugs/216104) and its duplicates) and now I can finally access the shares on my Ubuntu desktop from my Ubuntu laptop with Nautilus — which did not previously happen. Nice!!

---

### Post by windependence on 2008-09-06
Indeed. Sometimes however, in a large production environment, it is disruptive to apply a patch or upgrade unless you absolutely have to. That was the point Hermann and I were making. We were saying IF the server isn't broke don't upgrade, but in your case the server obviously had a bug and was broke.

-Tim

---

