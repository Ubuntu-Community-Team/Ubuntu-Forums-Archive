---
title: "vmware-server package broken"
date: 2007-04-28
forum: Server Platforms
---

### Post by PraysToPan on 2007-04-28
Hi All,

I recently tried to give the vmware-server package a try.  It has a number of issues.  So then I tried to report the bugs on launchpad, however, there is no package listed there.  I then tried to email the issues to the package maintainer listed however the email address [email]vmware-build@vmware.com[/email] is nonexistant.  So if anyone is listening, here is a copy of my email:

Bug in .deb for vmware-server for Ubuntu
From: 
Jonathan Skanes <jon@skanes.ca>
  To: 
[email]vmware-build@vmware.com[/email]
  Date: 
Yesterday 23:24:26
   
Hi,

I just installed the vmware-server package for Ubuntu from the Feisty 
commercial repository.  It appears that it installs a buggy pam.d file.  This 
makes remote connections to vmware impossible.

The distributed version ends up looking like this:

#%PAM-1.0
auth       sufficient       %pamdir%/pam_unix2.so shadow nullok
auth       required         %pamdir%/pam_unix_auth.so shadow nullok
account    sufficient       %pamdir%/pam_unix2.so
account    required         %pamdir%/pam_unix_acct.so

There is no need for fully qualified path names in Ubuntu pam configs.  Also, 
there is no pam_unix2.so in my default install of Feisty.  Here's my working 
version:

#%PAM-1.0
auth       required         pam_unix_auth.so shadow nullok
account    required         pam_unix_acct.so

Also, can you use the virtual dependency 'inet-superserver' rather 
then 'netkit-inetd'?  Those of us who prefer xinetd or others to netkit-inetd 
would very much appreciate that.

Oh, it also might be a nice idea to see the packages listed for bug reports on 
launchpad.

Thanks,
Jonathan Skanes

---

### Post by Yann2 on 2007-04-30
This patch doesn't work for X64 machines: 

In /var/log/auth.log:

Apr 30 14:54:45 pc463 sshd[5228]: (pam_unix) session opened for user yann by (uid=0)
Apr 30 14:55:11 pc463 vmware-authd[5253]: PAM unable to dlopen(/lib/security/pam_unix_auth.so)
Apr 30 14:55:11 pc463 vmware-authd[5253]: PAM [error: /lib/security/pam_unix_auth.so: wrong ELF class: ELFCLASS64]
Apr 30 14:55:11 pc463 vmware-authd[5253]: PAM adding faulty module: /lib/security/pam_unix_auth.so
Apr 30 14:55:11 pc463 vmware-authd[5253]: PAM unable to dlopen(/lib/security/pam_unix_acct.so)
Apr 30 14:55:11 pc463 vmware-authd[5253]: PAM [error: /lib/security/pam_unix_acct.so: wrong ELF class: ELFCLASS64]
Apr 30 14:55:11 pc463 vmware-authd[5253]: PAM adding faulty module: /lib/security/pam_unix_acct.so
Apr 30 14:55:11 pc463 vmware-authd[5253]: PAM (other) illegal module type: @include
Apr 30 14:55:11 pc463 vmware-authd[5253]: PAM pam_parse: expecting return value; [...common-auth]
Apr 30 14:55:11 pc463 vmware-authd[5253]: PAM (other) no module name supplied
Apr 30 14:55:11 pc463 vmware-authd[5253]: PAM unable to dlopen(<*unknown module path*>)
Apr 30 14:55:11 pc463 vmware-authd[5253]: PAM [error: <*unknown module path*>: cannot open shared object file: No such file or directory]
Apr 30 14:55:11 pc463 vmware-authd[5253]: PAM adding faulty module: <*unknown module path*>
Apr 30 14:55:11 pc463 vmware-authd[5253]: PAM (other) illegal module type: @include
Apr 30 14:55:12 pc463 vmware-authd[5253]: PAM pam_parse: expecting return value; [...common-account]
Apr 30 14:55:12 pc463 vmware-authd[5253]: PAM (other) no module name supplied
Apr 30 14:55:12 pc463 vmware-authd[5253]: PAM (other) illegal module type: @include
Apr 30 14:55:12 pc463 vmware-authd[5253]: PAM pam_parse: expecting return value; [...common-password]
Apr 30 14:55:12 pc463 vmware-authd[5253]: PAM (other) no module name supplied
Apr 30 14:55:12 pc463 vmware-authd[5253]: PAM (other) illegal module type: @include
Apr 30 14:55:12 pc463 vmware-authd[5253]: PAM pam_parse: expecting return value; [...common-session]
Apr 30 14:55:12 pc463 vmware-authd[5253]: PAM (other) no module name supplied


Any Idea?

---

### Post by PraysToPan on 2007-04-30
We might as well keep this on the one messageboard: [http://www.vmware.com/community/thread.jspa?threadID=82445&tstart=0](http://www.vmware.com/community/thread.jspa?threadID=82445&tstart=0)

Jon

---

### Post by plm on 2007-05-07
> **Yann2 said:**
> This patch doesn't work for X64 machines: 

In /var/log/auth.log:

Apr 30 14:54:45 pc463 sshd[5228]: (pam_unix) session opened for user yann by (uid=0)
Apr 30 14:55:11 pc463 vmware-authd[5253]: PAM unable to dlopen(/lib/security/pam_unix_auth.so)
Apr 30 14:55:11 pc463 vmware-authd[5253]: PAM [error: /lib/security/pam_unix_auth.so: wrong ELF class: ELFCLASS64]
...

Any Idea?

I encountered the same problem yesterday when trying to install the vmware-server on my 64 bit ubuntu server. The problem is that vmware tries to load the 64 bit pam libraries, but vmware-authd is a 32 bit program. 

The vmware-server package comes with its own 32 bit pam libraries. The package installs /etc/pam.d/vmware-authd, with the following content:
> 
#%PAM-1.0
auth       sufficient       %pampath%/pam_unix2.so shadow null              ok
auth       required         %pampath%/pam_unix_auth.so shadow               nullok
account    sufficient       %pampath%/pam_unix2.so
account    required         %pampath%/pam_unix_acct.so

I'm not sure about %pampath% but it was some "variable" between %..%. I assume that this was to be replaced by the real path of the 32 bit pam libraries during installation, but something went wrong. So I search my system and found them in /usr/lib/vmware-server/lib/libpam.so.0/security, i.e. inside the vmware-server package. Just edit the vmware-authd file in /etc/pam.d and replace %pampath% with /usr/lib/vmware-server/lib/libpam.so.0/security, i.e. the file becomes:
> 
auth       sufficient       /usr/lib/vmware-server/lib/libpam.so.0/security/pam_unix2.so shadow null              ok
auth       required         /usr/lib/vmware-server/lib/libpam.so.0/security/pam_unix_auth.so shadow               nullok
account    sufficient       /usr/lib/vmware-server/lib/libpam.so.0/security/pam_unix2.so
account    required         /usr/lib/vmware-server/lib/libpam.so.0/security/pam_unix_acct.so


After this I could login with the remote console.

---

### Post by systimax on 2007-05-07
Who is responsible for packages in the commercial Rep? the vendor? ubuntu? Canonical?

---

### Post by Chayak on 2007-05-08
To start off unless you download the software directly from VMware and install it using their packages they don't have to fix anything.  The only install package they support for linux is their .rpm and the .tar.bz which you download from their site not the repositories.

---

### Post by fago on 2007-06-03
I've used this successfully. However, a few days ago there was an updated package released and it stopped working for me. I had no success with this, but now its working with the entries from
[https://bugs.launchpad.net/ubuntu/+bug/112937](https://bugs.launchpad.net/ubuntu/+bug/112937)

---

### Post by ericdegen on 2007-06-04
This is a good and  interesting thread as I am in the planing phases of putting together a 64 bit VMware Server box.  I have not decided on which distro to use yet, so I covet your experiences with Ubuntu or any others that are 64 bit.

Have you resolved this satisfactorily? are you running Feisty or another flavor? Thanks!

---

### Post by citybird on 2007-06-14
Thank you so much for this thread. I have been looking all over for this solution.

Unable to connect to VMware Server Remote Connection solved ;-)

---

### Post by Betelgeuse on 2007-06-20
I've solved this unable to connect from another machine. Here what I did :

I've edited /etc/pam.d/vmware-auth.d file

----------------
#%PAM-1.0
# auth       sufficient       /usr/lib/vmware-server/lib/libpam.so.0/security/pam_unix.so shadow nullok
# auth       required         /usr/lib/vmware-server/lib/libpam.so.0/security/pam_unix_auth.so shadow nullok
# account    sufficient       /usr/lib/vmware-server/lib/libpam.so.0/security/pam_unix.so
# account    required         /usr/lib/vmware-server/lib/libpam.so.0/security/pam_unix_acct.so
auth       sufficient       /lib/security/pam_unix.so shadow nullok
auth       required         /lib/security/pam_unix_auth.so shadow nullok
account    sufficient       /lib/security/pam_unix.so
account    required         /lib/security/pam_unix_acct.so
----------------

as you see, I've commented out the originals and tell vmware to use the original files that comes with ubuntu...
I've tried connecting from my laptop machine and it connects now.

Last weekend, I've setup a production server. it's ubuntu server 6.06 LTS version and I've installed vmware-server from the tar.gz file. There was no remote connection problem but there was error logs on /var/log/auth.log file and I was annoyed and this same trick solved that too...

---

### Post by wilbur.harvey on 2007-06-25
As the previous post recommended

I've edited /etc/pam.d/vmware-auth.d file
----------------
#%PAM-1.0
# auth sufficient /usr/lib/vmware-server/lib/libpam.so.0/security/pam_unix.so shadow nullok
# auth required /usr/lib/vmware-server/lib/libpam.so.0/security/pam_unix_auth.so shadow nullok
# account sufficient /usr/lib/vmware-server/lib/libpam.so.0/security/pam_unix.so
# account required /usr/lib/vmware-server/lib/libpam.so.0/security/pam_unix_acct.so
auth sufficient /lib/security/pam_unix.so shadow nullok
auth required /lib/security/pam_unix_auth.so shadow nullok
account sufficient /lib/security/pam_unix.so
account required /lib/security/pam_unix_acct.so

This worked for me, so far nothing else has.
I can now connect to the vmware server, which was installed from the canonical repository, from a remote machine.

Thank you Betelgeuse

Wilbur

---

### Post by chefdog on 2007-08-04
I started another thread about this issue, but I'll move my comments to this thread, here is a copy of my post:

Allright,

Got Vmware server up and running on 64bit Ubuntu Feisty Linux, creating new vmware guest's does work, copying and open existing vmware guests; also no problem.
Now I want vmware guest (Windows HomeServer) to install on a raw partition, so accessing the harddrive natively (no virtual disks).

My system; AMD64 X2 3800 EESFF, 4GB ram, 2 WD raptors in raid for OS, 1TB HD space for vmware guest OS, mobo is a Nvidia 630a with geforce 7025 onboard.

I do have the dedicated drive (1TB) next to my OS drives, I can setup the guest, but when I run the guest for installing HomeServer I get errors (from the /var/log/auth.log):

Aug 3 20:22:04 chefdog-homeserver vmware-authd[4680]: PAM (other) illegal module type: @include
Aug 3 20:22:04 chefdog-homeserver vmware-authd[4680]: PAM pam_parse: expecting return value; [...common-session]
Aug 3 20:22:04 chefdog-homeserver vmware-authd[4680]: PAM (other) no module name supplied
Aug 3 20:22:04 chefdog-homeserver vmware-authd[4680]: login from 192.168.1.100 as marco
Aug 3 20:22:38 chefdog-homeserver vmware-authd[4703]: PAM (other) illegal module type: @include
Aug 3 20:22:38 chefdog-homeserver vmware-authd[4703]: PAM pam_parse: expecting return value; [...common-auth]
Aug 3 20:22:38 chefdog-homeserver vmware-authd[4703]: PAM (other) no module name supplied
Aug 3 20:22:38 chefdog-homeserver vmware-authd[4703]: PAM unable to dlopen(<*unknown module path*>)
Aug 3 20:22:38 chefdog-homeserver vmware-authd[4703]: PAM [error: <*unknown module path*>: cannot open shared object file: No such file or directory]
Aug 3 20:22:38 chefdog-homeserver vmware-authd[4703]: PAM adding faulty module: <*unknown module path*>
Aug 3 20:22:38 chefdog-homeserver vmware-authd[4703]: PAM (other) illegal module type: @include
Aug 3 20:22:38 chefdog-homeserver vmware-authd[4703]: PAM pam_parse: expecting return value; [...common-account]
Aug 3 20:22:38 chefdog-homeserver vmware-authd[4703]: PAM (other) no module name supplied
Aug 3 20:22:38 chefdog-homeserver vmware-authd[4703]: PAM (other) illegal module type: @include
Aug 3 20:22:38 chefdog-homeserver vmware-authd[4703]: PAM pam_parse: expecting return value; [...common-password]
Aug 3 20:22:38 chefdog-homeserver vmware-authd[4703]: PAM (other) no module name supplied
Aug 3 20:22:38 chefdog-homeserver vmware-authd[4703]: PAM (other) illegal module type: @include
Aug 3 20:22:38 chefdog-homeserver vmware-authd[4703]: PAM pam_parse: expecting return value; [...common-session]
Aug 3 20:22:38 chefdog-homeserver vmware-authd[4703]: PAM (other) no module name supplied

---

### Post by hazb on 2007-08-26
(not important, this post should be removed, sorry)

---

### Post by jafo on 2007-09-04
I have the issue as well, removing the fully qualified path fixes.

I also agree with the OP regarding the use of 'inet-superserver' rather
then 'netkit-inetd'.

I likes me some xinetd.

---

