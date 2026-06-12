---
title: "Question on samba disable roaming profile"
date: 2008-03-28
forum: Server Platforms
---

### Post by cpthk on 2008-03-28
Hi:

I have samba set logon path = "" to disable roaming profile. This works fine. But the windows client will create a user profile under Documents and Settings. And when user logout, it will not be deleted itself. After couple days, it's taking so many disk spaces. I tried to enable the "Disable cached copies of roaming profile" in group policy. But still didn't work. Any clue?

Thanks.

---

### Post by rickyjones on 2008-03-28
> **cpthk said:**
> Hi:

I have samba set logon path = "" to disable roaming profile. This works fine. But the windows client will create a user profile under Documents and Settings. And when user logout, it will not be deleted itself. After couple days, it's taking so many disk spaces. I tried to enable the "Disable cached copies of roaming profile" in group policy. But still didn't work. Any clue?

Thanks.

Microsoft provides a tool that will delete all local user profiles. I recommend that you create a log off script for the computers that will call this tool.

[http://www.tomshardware.com/forum/54774-45-auto-delete-profile-logoff-restart](http://www.tomshardware.com/forum/54774-45-auto-delete-profile-logoff-restart)

-Richard

---

### Post by cpthk on 2008-03-28
> **rickyjones said:**
> Microsoft provides a tool that will delete all local user profiles. I recommend that you create a log off script for the computers that will call this tool.

[http://www.tomshardware.com/forum/54774-45-auto-delete-profile-logoff-restart](http://www.tomshardware.com/forum/54774-45-auto-delete-profile-logoff-restart)

-Richard

That tool can only be ran with administrative accounts, which regular accounts couldn't.

---

### Post by rickyjones on 2008-03-28
> **cpthk said:**
> That tool can only be ran with administrative accounts, which regular accounts couldn't.

You can use additional third party RunAs replacement tools to script this. Have the program execute with administrator privileges in a secure manner. 

[http://www.tek-tips.com/faqs.cfm?fid=2760](http://www.tek-tips.com/faqs.cfm?fid=2760)
[http://blogs.msdn.com/oldnewthing/archive/2004/11/29/271551.aspx](http://blogs.msdn.com/oldnewthing/archive/2004/11/29/271551.aspx)
[http://www.adminscripteditor.com/forum/tm.asp?m=1937&mpage=1&key=&#1939](http://www.adminscripteditor.com/forum/tm.asp?m=1937&mpage=1&key=&#1939)

Several different ways to do it.

You could also write the script and use the task scheduler to launch it with admin privileges.

-Richard

---

### Post by cpthk on 2008-03-30
I finally got it work out. The delete caches of roaming profile will work, but you have to make sure your profile is roaming profile not local. I realized```
logon path =
``` is different to ```
logon path = ""
``` If I disable it, windows will not consider as roaming profile, so it will then create local profile which will not be deleted automatically.

---

