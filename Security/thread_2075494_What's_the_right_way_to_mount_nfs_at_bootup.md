---
title: "What's the right way to mount nfs at bootup?"
date: 2012-10-23
forum: Security
---

### Post by paulisdead on 2012-10-23
So I've been away from Ubuntu for the past year, but decided to go back now that the gnome remix is out for 12.10.

I'm having some seriously long stalls if I try to mount my nfs mounts on my centos 6.2 server during bootup.  If I manually mount them, they come up right away.  Although if I let it try to mount at bootup, it still takes awhile to mount even manually.  I can have a browser opened with 10 tabs loaded and NFS still hasn't mounted, so the network's definitely ready by then.  It takes about a minute after it's gotten to the desktop to mount the share via fstab.

Right now, I've got it in my fstab like so
192.168.0.9:/data/smb        /mnt/smb        nfs     proto=tcp,port=2049,_netdev,async,hard,intr 0       0

Originally I had it by hostname, but tried doing it by IP, just in case it wasn't resolving that early in the boot process.  I have the IP of the server in my /etc/hosts on the ubuntu clients, as well as their IPs in the /etc/hosts on the server.  None of that should have been necessary as I have a DNS server with reverse dns for all those systems, but threw that in the hosts files just to make sure.

The proto=tcp,port=2049 in the fstab is recent, I found that in the ubuntu nfs howto, so figured I'd try that, but it hasn't helped.

Network manager has the connection available to all users.

I could do autofs, I just hate using that, since it's so convoluted.  Plus under fc17, nautilus would hard lock the system if you left a nautilus window open inside a folder that autofs unmounted while the system was idle.  Not sure if that's going to be a problem under ubuntu.

---

