---
title: "Postfix Forwarding Issue"
date: 2018-11-28
forum: Server Platforms
---

### Post by gbenge on 2018-11-28
Hello guys,


I'm new here and I'm also new to postfix, I will appreciate if you can help with this issue.

we just upgraded the MTA (mail transfer agent) of our email server from sendmail to postfix. Before the upgrade, there is this special email account created for all the staffs' email - i.e. whenever any email is coming in, a copy goes to this email account and also whenever anyone is sending email out, a copy is automatically sent to it. So after the upgrade, this changed - instead of a copy dropping in this account, we have multiple copies dropping in the account especially when an email drops on any group email account, multiple copies equivalent to the number of users in the group get forwarded to this special email account instead of just a copy.

Can anyone please give me idea of how this can be sorted out?

Thanks in anticipation

---

### Post by lisati on 2018-11-28
I've edited your post to tidy up the paragraph formatting. You only need to push Enter/Return at the end of a paragraph, not at the end of each line that you type. The forum software and the browsers used by people viewing your text will take care of formatting for you.

It has been a while since I've administered a Postfix system, but think that the [always_bcc]("http://www.postfix.org/ADDRESS_REWRITING_README.html#auto_bcc") option might be worth checking out.

---

### Post by slickymaster on 2018-11-28
Thread moved to **Server Platforms** for a better fit

---

### Post by gbenge on 2018-11-29
Thanks

---

### Post by wildmanne39 on 2018-11-29
Since you created another thread in the Fedora/RedHat and derivatives sub-forum because you are using Fedora this thread is closed!

---

