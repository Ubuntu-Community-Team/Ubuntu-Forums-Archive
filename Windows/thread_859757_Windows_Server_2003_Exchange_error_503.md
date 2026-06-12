---
title: "Windows Server 2003 Exchange error 503"
date: 2008-07-14
forum: Windows
---

### Post by pawnrocket on 2008-07-14
I have researched this on technet and haven't had any luck. 

One of the servers at work is used as an email server. It is a Windows 2003 Server. 

When the server started "locking up" (after our tech company started installing a terminal server) a simple hard boot would bring everything back up and running. of course we lost a lot of emails.  However for a couple days the server has restarted but full exchange capabilities haven't been loading. 

When I attempt to connect to the server, it request a password (so that part is working) then after the password is entered I get an Error 503. 

technet said it was possibly because of upgrade issues from MS 2000 Server to 2003 Server. However the server was never updated in that why. It was a full install of 2003. 

I will give you more info if you need it
any ideas? 

Thanks.

---

### Post by rickyjones on 2008-07-15
> **pawnrocket said:**
> I have researched this on technet and haven't had any luck. 

One of the servers at work is used as an email server. It is a Windows 2003 Server. 

When the server started "locking up" (after our tech company started installing a terminal server) a simple hard boot would bring everything back up and running. of course we lost a lot of emails.  However for a couple days the server has restarted but full exchange capabilities haven't been loading. 

When I attempt to connect to the server, it request a password (so that part is working) then after the password is entered I get an Error 503. 

technet said it was possibly because of upgrade issues from MS 2000 Server to 2003 Server. However the server was never updated in that why. It was a full install of 2003. 

I will give you more info if you need it
any ideas? 

Thanks.

More information will need to be provided.

Windows Server 2003 Standard or Enterprise? Or is this Small Business Server? If so is it SBS Standard or SBS Premium?

You say that when you connect it asks for a password... you mean via remote desktop or via Outlook Web Access (OWA)?

Can you Remote Desktop (RDP) to the server? Have you checked the event logs for errors about services unable to start? Have you tried manually starting the various exchange services?

Sincerely,
Richard

---

