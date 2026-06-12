---
title: "samba problems with unprivileged windows users"
date: 2009-03-17
forum: Server Platforms
---

### Post by sulla on 2009-03-17
Dear all!

Since long I am experiencing strange samba problems:.

I have#
* an ubuntu 8.04 server with samba 3.0.28.a and kernel 2.6.24-23-server acting purely as a smb server
* Windows XP SP3 clients with built in SMB client, unprivileged users only.

The problem i experience is:
When browsing the network shares - holding e.g. hundreds of photos - in thumbnail preview mode a lot of data is transferred during browsing. When browsing as an unprivileged windows user "user", every once in a while, windows explorer hangs. The sort of hang that only the reset button can resolve. In taskmanager, network transfer drops to zero. Active applications (Firefox) continue to work fine, just everything associated with windows explorer (log out, browse folders...) is impossible. The task is unresponsive and can not be killed with the taskmanager. Just reset helps. When browsing the same shares with a windows-user with administrative rights I do not observe those problems (by chance only?!). It does not matter if I start explorer-windows in a separate job or not.

On Ubuntu the smb logfile in /var/log/samba just shows that the client disconnected at the same instance that the explorer hang occurs. No error message whatsoever.

Anybody any idea of what is going on here?

my /etc/samba/smb.conf is (I exlcuded all lines commented out!)
   workgroup = HOME_NETWORK
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   invalid users = root
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
   create mask = 0664
   directory mask = 0775

[photos]
 comment = Servers photos NAS
 browseable = yes
 writable = yes
 locking = no
 path = /NAS/share-photos
 public = no
 valid users = @share
 force group = share

---

### Post by askreet on 2009-03-17
I have seen this same error with folders containing videos, it's likely worse in fact because it has to get the first frame to generate a thumbnail.

I never did find a resolution, I just stopped putting all my videos in the same folder and started browsing in "Detail" view, to avoid thumbnails loading.

---

### Post by sulla on 2009-03-26
Dear All!

I filed a bug report at samba.org ([https://bugzilla.samba.org/show_bug.cgi?id=6202](https://bugzilla.samba.org/show_bug.cgi?id=6202))

With the help of the samb team (many thanks indeed to Volker!) I was able to analyse wireshark sniffs of the network traffic at the server. Volker suspected a network problem, as there were "lost segments".

As it was a client hang rather than a server hang, I replaced the NForce3 on-board ehternet card of the client with a Netgear 311A PCI Ethernet card and for some time the issues have not reappeared. I was able to transfer files reliably like never before.

So, unless further hangs occur, I think it was a network hardware bug, no samba bug.

Thanks for help,
Wolfgang

---

