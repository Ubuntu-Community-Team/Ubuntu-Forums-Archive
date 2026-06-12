---
title: "Annoying Samba/CUPS problem"
date: 2010-07-18
forum: Server Platforms
---

### Post by petersk on 2010-07-18
I'm not sure if this is a lucid problem, but since upgrading, all my windows and OS/X machines cannot see the samba-shared printers connected to my ubuntu server if the server is restarted.  

On the Ubuntu server, I do a:
```

 /etc/init.d/smbd status

```
 and get the "use service smbd status" which I do, and it says it's running. 

Then I restart it:
```

service smbd restart

```
and the machines can see the printers as windows shared (really samba shared) printer again.

I'm not sure if I have to reinstall them on each machine, but I do because I usually determine I have the problem after somethings already in the non-existent queue.  So I delete the printers in windows, reinstall and then I can print again.

Any thoughts?
Kurt

---

### Post by capscrew on 2010-07-19
> **petersk said:**
> I'm not sure if this is a lucid problem, but since upgrading, all my windows and OS/X machines cannot see the samba-shared printers connected to my ubuntu server if the server is restarted.  

On the Ubuntu server, I do a:
```

 /etc/init.d/smbd status

```
 and get the "use service smbd status" which I do, and it says it's running. 

Then I restart it:
```

service smbd restart

```
and the machines can see the printers as windows shared (really samba shared) printer again.

I'm not sure if I have to reinstall them on each machine, but I do because I usually determine I have the problem after somethings already in the non-existent queue.  So I delete the printers in windows, reinstall and then I can print again.

Any thoughts?
Kurt

This is a bug due to CUPS starting before Upstart starts Samba (smbd).  See [**_[B][U]here_**[/U][/B]]("http://www.uluga.ubuntuforums.org/showthread.php?p=9466475").

---

