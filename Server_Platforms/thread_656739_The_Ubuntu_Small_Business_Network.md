---
title: "The Ubuntu Small Business Network"
date: 2008-01-02
forum: Server Platforms
---

### Post by blazewon22 on 2008-01-02
K so I've decided to start my own business this year and I given my paltry budget Ubuntu seems like a good choice for my 5 employee outfit. 

I'm a longtime Windows Admin, since NT 3.5.1 and am having a hella hard time trying to get setting up a Ubuntu network. i've also been using OSX server for 3 years. Maybe its my windows way of thinking but i am trying to create a client/server network. I've been reading the forums and scouring google, but i have not really found a way to accomplish my goals.

The Server would be file/print hosting the printers and home directories. I would like users to be able to authenticate through the server for access to their workstation and then be able to lock down the desktop so they cant install/update the workstations. I would like to manage that from the server.

If someone has a post or other documentation i would appreciate it. 

In a nutshell I need to understand are these things possible with Ubuntu Server and Desktop and how to implement:
[LIST]
[*]Create home folders on the server for end-users desktops (NFS or Samba?)
[*]Create ACLs so the home folders are private. Also i would like other folders that are restricted (i.e. accounting).
[*]Have the server provide dhcp? I know it can do DNS
[*]Allow users to login to their laptops when not on the network but have an offline home folder that can sync when reconnected to the network.
[*]Image Ubuntu Desktops with Ubuntu server?
[/LIST]

Barnes and Noble doesn't have a lot of answers for me.

Thanks!

---

### Post by rsw686 on 2008-01-03
Well you can use Samba for the file sharing. Yes there is a DHCP daemon as well. Not sure on the locking down of workstations.

---

### Post by crouton on 2008-01-03
One option is a Samba domain (which acts like a NT4 domain - lots of pages available on this.)  You get the usual features (centralized user management, logon profiles, optional roaming profiles, groups, etc) plus some extras like the filesharing.  DHCPD woulud be a valid dhcp server, you already know how to do DNS per your post.  Home folders are already private unless you specify otherwise with filesystem permissions and you can play with group-access folders for things like Accounting, HR, etc.  ACL is available but is intended for more granular permissions (which you may or may not need.)

As for imaging the desktops, there are numerous programs that can do this.  You may want to ask yourself if it is truly necessary, as you can come up with a master image that handles 90% of your configuration/specialization needs and tweak accordingly rather than have to image multiple configurations.

---

