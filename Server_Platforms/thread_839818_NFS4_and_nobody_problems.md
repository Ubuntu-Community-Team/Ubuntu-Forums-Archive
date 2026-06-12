---
title: "NFS4 and nobody problems"
date: 2008-06-24
forum: Server Platforms
---

### Post by gauss on 2008-06-24
I have a Heron, [FONT="Courier New"]server[/FONT], and a Heron, [FONT="Courier New"]client[/FONT]. I have users [FONT="Courier New"]foo[/FONT] and [FONT="Courier New"]bar[/FONT] and group [FONT="Courier New"]baz[/FONT] with identical numerical GIDs and UIDs on both. I'd like to mount [FONT="Courier New"]server[/FONT]'s [FONT="Courier New"]/home/foo[/FONT] as [FONT="Courier New"]client[/FONT]'s [FONT="Courier New"]/home/foo[/FONT] and have followed [https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto). I'd like to be able to "see" the same users and groups on both machines within [FONT="Courier New"]/home/foo[/FONT].

It mounts correctly but all UID's (e.g. both [FONT="Courier New"]foo[/FONT] and [FONT="Courier New"]bar[/FONT]) in [FONT="Courier New"]/home/foo[/FONT] on [FONT="Courier New"]client[/FONT] are mapped to [FONT="Courier New"]nobody[/FONT] and all GID's are mapped to [FONT="Courier New"]nogroup[/FONT]. This means that [FONT="Courier New"]foo[/FONT] can't use [FONT="Courier New"]/home/foo[/FONT] on [FONT="Courier New"]client[/FONT] like it can on [FONT="Courier New"]server[/FONT]. E.g.
```
$ ssh server
``` fails on [FONT="Courier New"]client[/FONT] with
```
Bad owner or permissions on /home/foo/.ssh/config
``` which is correct since [FONT="Courier New"]config[/FONT] has owner [FONT="Courier New"]nobody[/FONT] and [FONT="Courier New"]nobody[/FONT] has a different UID than [FONT="Courier New"]foo[/FONT].

Here's [FONT="Courier New"]/etc/exports[/FONT] on [FONT="Courier New"]server[/FONT]:
```
/srv    client(ro,fsid=0,insecure,no_subtree_check,async)
/srv/foo client(rw,nohide,insecure,no_subtree_check,async)
``` Also [FONT="Courier New"]/etc/fstab[/FONT] binds [FONT="Courier New"]/srv/foo[/FONT] to [FONT="Courier New"]/home/foo[/FONT] on [FONT="Courier New"]server[/FONT].

Here's [FONT="Courier New"]/etc/fstab[/FONT] on [FONT="Courier New"]client[/FONT]:
```
server:/foo /home/foo  nfs4    proto=tcp,soft,defaults 0       0
```

Is there any way I can get what I want with NFS: to be able to view the same UIDs and GIDs on [FONT="Courier New"]client[/FONT] as I see on [FONT="Courier New"]server[/FONT] so that [FONT="Courier New"]foo[/FONT] on both boxes can "act the same"?

Thanks for any insight you can provide.

---

### Post by gauss on 2008-06-24
This seems to work. For server's /etc/exports:
```
/home/foo client(rw,no_subtree_check,sync)

```

For client's /etc/fstab:
```
server:/home/foo /home/foo nfs defaults,soft 0 0
```

---

