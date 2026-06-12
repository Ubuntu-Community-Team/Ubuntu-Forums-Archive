---
title: "Connect to Windows Server 2003 console session"
date: 2008-04-16
forum: Server Platforms
---

### Post by SPWebb on 2008-04-16
Hi,

I am new to Ubuntu and have just installed version 8.04

I need to remote desktop onto a server running Windows Server 2003 R2 SP2, I know in Windows I would just use the "/console" method, but this doesn't seem to work in Ubuntu.

Can someone tell me how to connect to the console session?

Thanks

Scott

:KS

---

### Post by cdenley on 2008-04-16
```

rdesktop -0 mywin2k3serverip

```

You can also install VNC on the server.

---

### Post by SPWebb on 2008-04-16
Hi,

Thanks for the reply, unfortunately VNC is not an option.

Do I need to type that command into the terminal or can I do something within the Terminal Client?

Thanks

Scott

---

### Post by cdenley on 2008-04-16
I didn't see anywhere to enable that option in the "terminal server client" frontend. As far as I know, you have to use that command in the terminal. You might be able to force that option anytime rdesktop is used

```

echo alias rdesktop=rdesktop\\\ -0>>~/.bashrc

```
After running this command, log out, then log back in. I haven't tested this, so I'm not sure it works. You won't be able to use the remote desktop client without this option, if it does work.

---

### Post by HermanAB on 2008-04-16
Microsoft purchased their remote desktop schtuff from Citrix.  Rdesktop is the Linux client for that.  On Win 2003, enable remote control for the user - to do this, the user MUST have a password. Then on Linux, run rdesktop (90% scaling seems to work well):
$ rdesktop -g 90% serveripaddress

Win 2003 allows 2 simultaneous RDP sessions by default, but a third one for the Administrator is available on console 0:
$ rdesktop -g 90% -0 serveripaddress

[http://www.linuxquestions.org/linux/articles/Jeremys_Magazine_Articles/Windows_Admin_with_rdesktop](http://www.linuxquestions.org/linux/articles/Jeremys_Magazine_Articles/Windows_Admin_with_rdesktop)

Cheers,

Herman

---

### Post by Deathrend on 2008-04-17
> **HermanAB said:**
> Win 2003 allows 2 simultaneous RDP sessions by default, but a third one for the Administrator is available on console 0

That's not exactly correct.  The console is the physical console on the server itself.  Basicly it's the same thing you would log into as though you where on the server itself.  Believe me, I know all about it, working with several people that seem to just "Disconnect" instead of logging off of production servers *mutter*.  It's useable via RDP by anyone that can log in to the PC remotely.  Most servers are set to only allow Administrators to log in at all however.

My suggestion, if you jsut need apps on the server running in the console, would be to RDP in, then go to Terminal Services manager, find the console, right click, and select remote control.  Unless you need it specificly for the third desktop, that would be the eisest way to go.  If you need more, I would suggest setting it up as a Terminal server, windows XP installed before a specific date includes it's own CAL's for this, which makes it free for as many CAL's as the server can support (Normally 5 users at once).

GL

---

