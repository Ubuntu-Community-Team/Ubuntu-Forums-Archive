---
title: "NFS and security"
date: 2008-02-09
forum: Server Platforms
---

### Post by _sAm_ on 2008-02-09
On my (simple)home server running latest Ubuntu os I am sharing som files on the LAN, with NFS. In /etc/hosts.deny
I added 
portmap: ALL
 but can still use the folder from my Ubuntu desktop pc? Why dont the portmapper listen to the new rule?

---

### Post by faulkes on 2008-02-09
Could you perhaps describe what it is you are trying to accomplish overall by the changes you are making?

---

### Post by The Titan on 2008-02-09
Did you restart the server?  We could probably use a little more information here.

---

### Post by HermanAB on 2008-02-09
Well, if hosts.allow has "all: all" in it...

---

### Post by _sAm_ on 2008-02-09
I found the fault, well it was mine as always:-/ I forgot to run:sudo /etc/init.d/portmap restart

But now I have another problem, cus I cant use the NFS share from my desktop anymore. I have added portmap: 10.0.0.* to the  /etc/hosts.allow
And then restarted portmap(sudo /etc/init.d/portmap restart) and the NFS demon(sudo exportfs -a). I have also tried 10.0.0.16 witch is the ip for the desktop (ifconfig told me so). 

Any tips please? 

> Could you perhaps describe what it is you are trying to accomplish overall by the changes you are making?
Sure; I just want to learn how to make NFS sharing safe, and have been reading some guides for it. I dont know much about this stuff as you can see.

---

### Post by The Titan on 2008-02-09
> Sure; I just want to learn how to make NFS sharing safe, and have been reading some guides for it. I dont know much about this stuff as you can see.

This is a good practice, i know from experience that security is number 1 priority. 

anyways, this might be way off but I've had similar problems with other applications that maybe you just have to make that IP static, even if its the same IP. 

hope this helps!
-dan

---

### Post by faulkes on 2008-02-09
> **_sAm_ said:**
> 
But now I have another problem, cus I cant use the NFS share from my desktop anymore. I have added portmap: 10.0.0.* to the  /etc/hosts.allow
And then restarted portmap(sudo /etc/init.d/portmap restart) and the NFS demon(sudo exportfs -a). I have also tried 10.0.0.16 witch is the ip for the desktop (ifconfig told me so). 

Any tips please? 

Sure; I just want to learn how to make NFS sharing safe, and have been reading some guides for it. I dont know much about this stuff as you can see.

Not knowing much is fine, you're in the right place, asking questions, always a good start.

NFS uses a number of different services including portmap, so you may have to add 

```

nfsd: 10.0.0.*

```

to hosts.allow (but that is just a guess, nfsd runs on port 2049), alternatively you may want to restart the nfsd daemon (exportfs -a just tries to re-export new /etc/exports entries). 

Faulkes

---

### Post by _sAm_ on 2008-02-09
Thanks for your answers, but it didn't help. I will try to do a bit googeling to see what I can find. 

Btw. you restart the NFS server with; sudo /etc/init.d/nfs-kernel-server restart (or reload).

---

### Post by faulkes on 2008-02-09
Was there anything reported in /var/log/messages or /var/log/secure in regards to nfs/portmap or tcpd?

Faulkes

---

### Post by _sAm_ on 2008-02-09
/var/log/secure gave me a blank page, while /var/log/messages had a lot of stuff; but I am sorry, it didn't tell me much. As I said, don't no much about this. 

Here is the page that I tried to follow: [http://nfs.sourceforge.net/nfs-howto/ar01s06.html](http://nfs.sourceforge.net/nfs-howto/ar01s06.html)

I have searched some more – and learned about the SSHFS protocol – and its kind of awesome. I don't need to bother with portmap, the speed is very good(just mounted a folder from my Ubuntu (home) server and tried a 2.2gig file, and using SSH, and with multithreading. I had already set up SSH, so mounting it up was easy. What do you think, is there any point with NFS when I can use this instead?

---

### Post by faulkes on 2008-02-09
NFS use is all dependent upon your requirements, if you are just fooling around or just want to have some remote drives on other machines mounted, then something like sshfs or samba are perfectly fine alternatives.

Faulkes

---

### Post by _sAm_ on 2008-02-09
Just wondering; what makes NFS better(I have seen others asking for this, but no got any answer).

Edit:
> But even when it is completed, Szeredi points out that sshfs will not replace high-end systems like NFS or VPNs. It is intended only to provide fast, convenient access to remote directories, and do so securely, and with no configuration required on the remote host. ([http://www.linux.com/articles/49757](http://www.linux.com/articles/49757))

Still wondering:-)

---

### Post by faulkes on 2008-02-09
> **_sAm_ said:**
> Just wondering; what makes NFS better(I have seen others asking for this, but no got any answer).

Edit:
 ([http://www.linux.com/articles/49757](http://www.linux.com/articles/49757))

Still wondering:-)

There is nothing which makes NFS a better or worse solution perse, it all depends on your environment and the history of your environment.  That is from a business perspective.

For instance, I use NFS at work, albeit under CentOS not Ubuntu.  We use it because we're entirely a unix shop and we don't have to deal with any windows machines at all, even desktops/laptops.  If we did have a requirement to support windows, we would probably have selected Samba (or perhaps both).

So in short, there is no "better or worse" in regards to NFS, only in regards to your environment.

Faulkes

---

### Post by MountainX on 2008-04-01
Some general rules of thumb I have learned. Caveat: I'm a newbie so these could be wrong.

1. NFS has a history of being less secure than other common file sharing protocols. It is getting better, but most people still do not recommend NFS for use outside of a secured network (whatever "secured network" means).

2. NFS is faster than samba generally. Most posts I've seen on the topic indicate it is about twice as fast.

I asked some related questions about nfs vs. cifs and smbfs in a couple threads. I didn't get any definitive answers yet, but I got some answers. See:
[http://ubuntuforums.org/showthread.php?t=730447](http://ubuntuforums.org/showthread.php?t=730447) - Is Ubuntu As Secure As Windows 2003 As a File Server on My LAN?

---

