---
title: "messages"
date: 2008-03-06
forum: Windows
---

### Post by ellenW on 2008-03-06
About 3 weeks ago I first received the followingmessage in big Big Bold Letters.:
Internet Explorer reports: Revocation information for the security certificate for this site (suspect email in Eathlink.net mailbox and webmail). Has anyone else received this?
At first I clicked on view and got this message ... [http://crl.thawwte,com/ThawteSGCCA](http://crl.thawwte,com/ThawteSGCCA). Since a successful download meant that there were no issue, I clicked download (it said it came fro earthlink) and was told it was successful. No change I still cannot look at suspect mail.The main thing is I just hate to get messagess like this. Anyone have any ideas. Occasionally , suspect mail contans an email from a long lost friend unsing an address that I n longer use.
Thanks, Ellen:confused:

---

### Post by bswilson on 2008-03-17
Where do I begin?  The problem you're having is that your Internet Explorer browser has an expired [root certificate]("http://www.microsoft.com/technet/archive/security/news/rootcert.mspx?mfr=true").  You can get an updated one by running Windows Update.  Also check out this [IEBlog post]("http://blogs.msdn.com/ie/archive/2006/11/07/improving-ssl-extended-validation-ev-ssl-certificates-coming-in-january.aspx").

I think your real problem is that you're using Internet Explorer, and asking for help on a GNU/Linux OS forum.  That could explain the apparent apathy to your plight...

---

### Post by p_quarles on 2008-03-17
Moved to Windows Discussions.

---

