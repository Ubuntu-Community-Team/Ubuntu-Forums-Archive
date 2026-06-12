---
title: "how to install smtp for use remote"
date: 2018-12-07
forum: Server Platforms
---

### Post by programercek on 2018-12-07
Hi,

I created emails testing12345@ and works. For receiving emails working fine, for sending not working.

I want to use settings to work remote my SMTP server.

I need to send my credentials with other programs, like Google, Outlook, Thunderbird but not working.

In Thunderburd, Gmail I receiving my emails, but want to use my SMTP credentials and connect to the server not working.

From Thunderbird I got: Sending of the message failed.The message could not be sent using Outgoing server (SMTP) mail.domain.com for an unknown reason. Please verify that you Outgoing server SMTP settings are correct and try again.

So, I think my settings on server is not OK.

Can you help me please?

Best

---

### Post by SeijiSensei on 2018-12-08
Your provider may block outbound SMTP traffic to defeat spambots.

Try opening a terminal and typing

```
telnet gmail-smtp-in.l.google.com 25
```

If it hangs with no reply from GMail's server, you're out of luck.

Some ISPs offer a server of their own through which you can relay mail.  Give them a call.

---

