---
title: "vmware server + likewise-open on Hardy x64?"
date: 2008-04-25
forum: Virtualisation
---

### Post by nullness on 2008-04-25
Hello,

Yesterday I upgraded a test server to Hardy x64 and was able to successfully get samba and likewise-open onto the our AD domain.  Everything seems to have gone well except for of course vmware server 1.0.5.  I had wanted to authenticate vmware server console with AD so it could be easily remotely administered, but unfortunately this did not work out.  I looked into the problem and found the following in the auth.log file:

Apr 24 15:48:58 psvhost002 vmware-authd[27493]: PAM unable to dlopen(/lib/security/pam_lwidentity.so)
Apr 24 15:48:58 psvhost002 vmware-authd[27493]: PAM [error: /lib/security/pam_lwidentity.so: wrong ELF class: ELFCLASS64]
Apr 24 15:48:58 psvhost002 vmware-authd[27493]: PAM adding faulty module: /lib/security/pam_lwidentity.so
Apr 24 15:48:58 psvhost002 vmware-authd[27493]: PAM (other) illegal module type: @include
Apr 24 15:48:58 psvhost002 vmware-authd[27493]: PAM pam_parse: expecting return value; [...common-auth]
Apr 24 15:48:58 psvhost002 vmware-authd[27493]: PAM (other) no module name supplied
Apr 24 15:48:58 psvhost002 vmware-authd[27493]: PAM unable to dlopen(<*unknown module path*>)
Apr 24 15:48:58 psvhost002 vmware-authd[27493]: PAM [error: <*unknown module path*>: cannot open shared object file: No such file or directory]
Apr 24 15:48:58 psvhost002 vmware-authd[27493]: PAM adding faulty module: <*unknown module path*>
Apr 24 15:48:58 psvhost002 vmware-authd[27493]: PAM (other) illegal module type: @include
Apr 24 15:48:58 psvhost002 vmware-authd[27493]: PAM pam_parse: expecting return value; [...common-account]
Apr 24 15:48:58 psvhost002 vmware-authd[27493]: PAM (other) no module name supplied
Apr 24 15:48:58 psvhost002 vmware-authd[27493]: PAM (other) illegal module type: @include
Apr 24 15:48:58 psvhost002 vmware-authd[27493]: PAM pam_parse: expecting return value; [...common-password]
Apr 24 15:48:58 psvhost002 vmware-authd[27493]: PAM (other) no module name supplied
Apr 24 15:48:58 psvhost002 vmware-authd[27493]: PAM (other) illegal module type: @include
Apr 24 15:48:58 psvhost002 vmware-authd[27493]: PAM pam_parse: expecting return value; [...common-session]
Apr 24 15:48:58 psvhost002 vmware-authd[27493]: PAM (other) no module name supplied

So from this I guess we can deduce two things: vmware isn't going to load the pam_lwidentity module from likewise-open since it is compiled for amd64 and apparently vmware doesn't like include directives in pam.d files.  Can anyone suggest a good workaround for the pam_lwidentity issue?

PS.  Sorry for double posting, I posted this question in the x64 forum before I noticed there was a virtualization forum, and this one seemed to be more appropriate for the question.

---

### Post by fjgaude on 2008-04-25
I'm not sure if this helps but if you haven't done these things in the install of vmware under Hardy you might consider them:

For Hardy

Taken from this thread:
[http://ubuntuforums.org/showthread.php?t=613976](http://ubuntuforums.org/showthread.php?t=613976) post #47

sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf  /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0

and additionally for 64 bit systems:

sudo ln -s /usr/lib32 /usr/l32
sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.9

---

### Post by fjgaude on 2008-04-25
I'm not sure if this helps but if you haven't done these things in the install of vmware under Hardy you might consider them:

For Hardy

Taken from this thread:
[http://ubuntuforums.org/showthread.php?t=613976](http://ubuntuforums.org/showthread.php?t=613976) post #47

```
sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf  /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0
```

and additionally for 64 bit systems:

```
sudo ln -s /usr/lib32 /usr/l32
sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.9
```

---

### Post by nullness on 2008-04-25
Thanks but I actually did follow that tutorial, the crux here is that vmware can't use 64-bit pam modules apparently and pam_lwidentity is amd64 :(

---

### Post by bamarob on 2008-04-25
How did you actually get likewise-open installed?  I just installed Hardy x64 in a virtual machine.  When I do:

sudo apt-get install likewise-open-gui

It says package cannot be found.  Isn't it supposed to be in the Universe repo.?  Did it not make it in?

Thanks,

Robert

---

### Post by fjgaude on 2008-04-25
> **bamarob said:**
> How did you actually get likewise-open installed?  I just installed Hardy x64 in a virtual machine.  When I do:

sudo apt-get install likewise-open-gui

It says package cannot be found.  Isn't it supposed to be in the Universe repo.?  Did it not make it in?

Thanks,

Robert

I see it here in 64-bit Hardy... both. VMware server may have an issue with the 64-bit PAM situation. Don't have any further knowledge. I do know that it handles 64-bit Ubuntu as a VM... it's the tools that likely have problems. Will have to wait and see if vmware does anything to assist Hardy in this matter.

Notice that vmware is not yet in the repositories.

---

### Post by nullness on 2008-04-28
> **fjgaude said:**
> I see it here in 64-bit Hardy... both. VMware server may have an issue with the 64-bit PAM situation. Don't have any further knowledge. I do know that it handles 64-bit Ubuntu as a VM... it's the tools that likely have problems. Will have to wait and see if vmware does anything to assist Hardy in this matter.

Notice that vmware is not yet in the repositories.

VMWare ATM doesn't seem to like the @include syntax used in PAM files either, not sure why yet.  BTW SuSE appears to work around this issue by having a 32-bit PAM package it uses for compatibility with VMWare and other 32-bit packages on their x64 server.

---

### Post by fjgaude on 2008-04-28
> **nullness said:**
> VMWare ATM doesn't seem to like the @include syntax used in PAM files either, not sure why yet.  BTW SuSE appears to work around this issue by having a 32-bit PAM package it uses for compatibility with VMWare and other 32-bit packages on their x64 server.

Interesting... I don't have a 64-bit VMware server install; it is 32-bit and that is why we have to include the ia32-libs, to handle all the 32-bit stuff of vmware.

Anyway... time moves us along.

---

### Post by nullness on 2008-04-28
Well I tried copying the 32-bit versions of pam_lwidentity.so and pam_winbind.so (figured I'd try em both) and while according to auth.log the logins succeed vmware for some reason decides they don't.  Also its safe to update the pam included with vmware with the three pam_*.so libraries in the 32-bit libpam package from Hardy as well.  Looks like VMWare will need to change some code in vmware-authd before this going to work.

---

