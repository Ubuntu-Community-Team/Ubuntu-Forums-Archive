---
title: "Accessing Windows share Through VPN"
date: 2008-10-04
forum: Windows
---

### Post by jakeo25 on 2008-10-04
Using Hardy, I have established a VPN using the package VPN connection Manager.  I connect with my company's VPN and can easily Remote Desktop with XP computers.  

What I need now is an ability to browse windows shares, e.g. \\server\share.  The shares do not show up in the Network, or 'Windows Network'.  This also does not seem to work using Nautilus' "Location", or any other method I can find.  Is there another service I need to install on Ubuntu locally so I can look at Windows Shares?

Thanks

Jake

---

### Post by henjj on 2008-10-28
I'm having the same problem.  I can connect, I can't figure out how to browse the shares.  In XP you just go to start, run, type in \\nameofserver, and all of the files come up in an explorer window.  What is the equivalent in Ubuntu?

---

### Post by fiddledd on 2008-10-28
Have you changed the permissions in the Windows folder to allow the Ubuntu user access? 

If not:

On the Windows box right click on the shared folder and click Properties, then select the Security tab and click Advanced. You should then be able to set permissions for yourself on the Ubuntu box.

---

