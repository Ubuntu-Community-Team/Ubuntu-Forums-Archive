---
title: "samba pdc &amp; xp clients; users problem"
date: 2008-01-22
forum: Server Platforms
---

### Post by beaker15 on 2008-01-22
hello,
I'm having a problem connecting my Windows client to my Samba PDC. I currently have several Windows XP pro machines connected as a workgroup (so users logon locally, no AD) and i'm setting up a Samba PDC to have them connect as a domain. I've looked around on the net and I'm pretty sure I've set up smb.conf as it should be (no problems with testparm). Anyway I'm at a stage where I'm trying to connect an XP machine to the domain but when it prompts me for a username/password with permission to join the domain, it comes up with 'user not found', even though the users that i'm trying  do exist on Samba and ubuntu. Also, I created a samba group called Admin with these users in and included  the line 'admin users = @Admin' in smb.conf so the users i'm trying should definitely have access.
Any ideas?
Is it something to do with windows local user accounts?
Is it something to do with winbind?
does the xp machine i'm trying on need to be added manually to samba?

thanks in advance

---

### Post by smileypaul on 2008-01-22
I havent set up samba as a PDC is over a year.. so its slipped out of my memory.. but something is telling me that you need to create a machine account as well.. look into this

---

### Post by freebeer on 2008-01-22
yep.. you need to add machine accounts, too.

I'm not sure about the clients being set up as a workgroup, though... they probably need to be set up as part of the domain.  That's what I did (never tried workgroups).

---

### Post by cdenley on 2008-01-23
If you have this line in your smb.conf, your machine accounts will be created automatically.
```

add machine script = /usr/sbin/useradd -s /bin/false -d /var/lib/nobody %u

```

Have you tried entering the root login when joining the domain. That is what I had to do, until I configured it to allow the admin group to do this. Sorry, I don't remember how I did that. If you want to try the root account, you will need to have a samba password for root, and can't have a line like this in smb.conf.
```

invalid users = root

```

Are you running gutsy? I've had problems running a samba pdc on gutsy, so I would suggest using dapper.

---

### Post by beaker15 on 2008-01-23
thanks for the replies, i've managed to successfully logon to my domain now after adding the client pc to samba. I'm going to try it using that script to add machines next too.

thanks again

PS now i'm just left with the problem of how to logon to my domain from the windows logon screen when my wireless connection doesn't establish until after windows has loaded...but thats for another forum

---

