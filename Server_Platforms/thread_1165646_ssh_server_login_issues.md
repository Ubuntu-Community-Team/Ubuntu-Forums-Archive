---
title: "ssh server login issues"
date: 2009-05-20
forum: Server Platforms
---

### Post by csmithmaui on 2009-05-20
For some reason I am getting the following message when I ssh to my server:

Failed to initialize account for user USERNAME: NT_STATUS_ACCESS_DENIED

It still lets me into the system but I can't sudo and I get Input/output errors when I try to execute some scripts that I can normally execute.  Any idea what could be causing this?  Thanks in advance for any help.

csmithmaui

---

### Post by HermanAB on 2009-05-20
That is a Microsoft Windows NT error message.  I suppose it comes either from your Samba server, or you are using Active Directory and it comes from that.

---

### Post by csmithmaui on 2009-05-21
thanks for the reply...I think you might be right...when I google that error message it always pops up with a bunch of samba related websites but I haven't found anything that explains what is going on.  Has anyone else ever seen this...maybe I just need to configure my samba server differently.

---

