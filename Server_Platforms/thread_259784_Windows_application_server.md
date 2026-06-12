---
title: "Windows application server"
date: 2006-09-17
forum: Server Platforms
---

### Post by BentNoodle on 2006-09-17
Totally new to ubuntu and this forum.  Wondering if ubuntu can be used in some way as an application server for Windows applications (HSoft HandiTax 2006).

Any suggestions appreciated.

---

### Post by kgeil on 2006-09-17
I don't know very much about it, but when I was mulling this over myself, the first thing that comes to mind is running a virtual machine on the server. Windows emulation looks like a solution. 
[http://www.winehq.com/](http://www.winehq.com/) 
Perhaps there's a better way.  This method definitely breaks the "keep it simple"rule.

---

### Post by BentNoodle on 2006-09-17
Thanks for the suggestion.  Definitely worth considering.

The application is not run on the server, as the client machine links to the executable file on the "server" PC via the network.  The issue we are having is that Windows XP Professional (existing file server / workstation) will not allow multiple users to access the executable file simultaneously.

Hence the need for a file / application server.  I think that ubuntu would allow multiple user access to the file so theoretically it should work.  Only issue would be if the application requires DLL files / registry entries on the server (don't know anything about this) which would ordinarily be installed during the applications set-up routine.

I was just crossing my fingers that I could just "pluck" the application from Windows XP Professional and copy to a shared area of ubuntu.

Does anyone have any experience with this, or any suggestions (we can not really afford a Windows Server OS and more hardware)?

---

### Post by etcpool on 2006-09-18
would samba as a pdc and logon domain do the job?

---

### Post by kgeil on 2006-09-18
I do know that you can run as many virtual machines you want, so each one can have it's own registry keys.  You would probably have to buy multiple licenses.  It also seems like you would need a lot of processing power to do this.

---

### Post by inthewayboy on 2006-09-18
Coming from the Win32 side I think you should be okay, assuming the application runs as you say it does. The application can be stored on a network drive and then run from the client without installation.

Getting ubuntu to file share with windows should be all you need to accomplish this. The networking protocol essentially negates any issues with what the application is served from, outside of any kooky application issues. I've seen some pretty messed up requirements over the years because of badly coded applications, and this would be one place where that may show it's face a little more than normal.

As little as I know about this whole scenario you would need to install the samba package and then edit the /etc/samba/smb.conf file to setup a share.

I think you still might have to figure out the authenication issues with this if it works, but seems like the winbind package will handle that easily.

Good luck!

---

