---
title: "SAMBA question"
date: 2009-01-24
forum: Server Platforms
---

### Post by dcollamore on 2009-01-24
This might be an oddball question, but I have a SAMBA server set to user mode security with a few shares that I need anonymous access to, so I have guest ok set on these shares.  This works well, but I'd like it to work better; specifically, I'd like to not even have to see a login window from Windows clients on these shares; I want the share to simply be available, instantly and with no hassle.  It's also easier to directly address files via UNC paths this way.  Is there a way to do this for these shares while maintaining user mode security?  I haven't been able to find anything in the SAMBA docs (but they are lengthy, and I may have missed something), and Google is not much help for this it seems.  I really do NOT want to go to share mode.

Thanks in advance for any input!

---

### Post by albinootje on 2009-01-24
> **dcollamore said:**
> I'd like to not even have to see a login window from Windows clients on these shares; I want the share to simply be available, instantly and with no hassle.

You can make a batch file on MS-Windows, and put that batch file in the user's AutoStart directory.

See here an example :
[http://www.rlmueller.net/LogonScriptFAQ.htm](http://www.rlmueller.net/LogonScriptFAQ.htm)

-> What can be done with a batch file logon script, besides launch a VBScript program

---

### Post by dcollamore on 2009-01-24
Unfortunately that won't really work for my environment; I'm looking at machines that have never been on my network before, and never will be again after they leave.  I'm really looking for something server-side.  Any ideas?

---

### Post by cariboo on 2009-01-24
I have the same situation, where computers I service are connected to my internal network to be able to access updates and other software. Note the computer is repaired before it is allowed to connect to the network. The update directory on the server is owned by root and the permissions are set to 777 and this is what the share looks like in samba:

```
[updates]
	comment = Project Dakota
	path  = /home/win_updates
	guest ok = yes
	browseable = yes
	writeable = yes
```

I've never had to enter a username or password for that directory. THe only thing I have to do is change the workgroup to the one I use on my network.

Jim

---

### Post by dcollamore on 2009-01-25
Is that in user mode security though?  That looks very like my public shares, and I still have to enter <i>something</i> in a login box, and more importantly, I can't address the share directly through UNC paths.

---

