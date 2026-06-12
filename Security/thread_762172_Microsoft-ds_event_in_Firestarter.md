---
title: "Microsoft-ds event in Firestarter"
date: 2008-04-21
forum: Security
---

### Post by lemuriaX on 2008-04-21
Hello,

We've seen some events in Firestarter lately on one of the networks I work on. 

They say they are attempts to connect from a Windows computer that shares the same router, using Microsoft-ds on Port 445 and TCP Port 80. 

That originating Windows computer does not have file and printer sharing activated however. No networking or filesharing is set up, just a shared router.

Is that cause for concern or is there a legitimate reason why that might happen?

Thanks in advance,

lemuriax

---

### Post by lemuriaX on 2008-04-21
Maybe this is the wrong forum for this, sorry if so...

---

### Post by lemuriaX on 2008-04-22
*bump*

can we move this to the right forum too ?

---

### Post by stmurray on 2008-04-23
Do you have samba installed on machine that is the destination of the traffic?  If so, then the traffic is probably Windows doing it's SMB stuff.  

Windows is very chatty-- even if you don't have file and printer sharing enabled, it may still try to connect over 445, so I wouldn't worry about that    Other services- Fax Service, License Logging Service, Server service, Net Logon Service, Remote Procedure call locator, all go over 445 on later versions of Windows.  

The port 80 traffic is a puzzler. There is an "RPC over HTTP" service, so it may be that or it may be Windows Media player or other piece going out and looking for a home. Or it may be some other software like AOL IM or something like that on the Windows box. 

On the Windows box, you can try a netstat -anb to see if anything odd pops up there (the -b flag only works with newer versions of windows and shows the process behind a network connection or listener) 

I hope this helps

---

### Post by lemuriaX on 2008-04-23
Thanks for the reply.

I do have the smbclient, libsmbclient library, and samba-common files installed though have never done anything with them yet. That's good to know that it's probably just Windows checking on SMB stuff - the Windows computer never triggered these events before the other day but perhaps an update to XP changed it's behaviour in this regard.  The Port 80 events happen at the same time as the SMB events, usually when booting up and going online for the day, also new behaviour...

I ran the netstat -anb command and don't see anything out of the ordinary as far as I can tell.

---

### Post by Chayak on 2008-04-23
Nothing that strange.  Windows is *very* chatty.  It will continuously try to locate other machines and advertise it's presence on a network.  It would be easier if you had something like a wireshark capture to determine what the packets were.

---

### Post by Dr Small on 2008-04-23
It is most likely just Windows sending out requests to find other shares.
There should be nothing harmful with it, in itself.

---

### Post by lemuriaX on 2008-04-26
Okay thanks for the input everyone, I appreciate it.

And sorry if I was impatient at first, was just a wee bit concerned as this behavior is new on that particular network. I will look into installing wireshark capture or something like that to further study up on packet analysis.

---

