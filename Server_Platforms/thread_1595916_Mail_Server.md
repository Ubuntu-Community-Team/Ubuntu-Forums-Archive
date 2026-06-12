---
title: "Mail Server"
date: 2010-10-13
forum: Server Platforms
---

### Post by Mr.Sean on 2010-10-13
Hello everyone I would like to ask a question. But first I would like to apologize if this is in the wrong board.

Anyway what I'm trying to do is set up a simple private use mail server, upon installing ubuntu 10.10 server edition I checked the box for mail server but since then I haven't been able to find anything that points me where I should be heading next. 

Thanks for your help,
  Mr. Sean.

---

### Post by whoop on 2010-10-13
This works:
[https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)

---

### Post by lisati on 2010-10-13
With Ubuntu Server Edition I use the [Postfix]("https://help.ubuntu.com/community/PostfixBasicSetupHowto") [MTA]("http://en.wikipedia.org/wiki/Mail_transfer_agent") to handle my requirements for email.

---

### Post by Mr.Sean on 2010-10-13
> **whoop said:**
> This works:
[https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)

Yes I did find that but I got turn away when it mentioned installing things.

---

### Post by Mr.Sean on 2010-10-13
> **lisati said:**
> With Ubuntu Server Edition I use the [Postfix]("https://help.ubuntu.com/community/PostfixBasicSetupHowto") [MTA]("http://en.wikipedia.org/wiki/Mail_transfer_agent") to handle my requirements for email.

Ok so I read through this sent an email to myself but it doesn't get delivered.

---

### Post by whoop on 2010-10-13
> **Mr.Sean said:**
> Ok so I read through this sent an email to myself but it doesn't get delivered.

Does your router or firewall have the proper ports opened ?

---

### Post by Mr.Sean on 2010-10-14
> **whoop said:**
> Does your router or firewall have the proper ports opened ?

I think I misunderstood how it works. Logging into the server and using mail returns 'No mail for USER' but it appears in the folders.

also when trying to log in remotely it says "Error sending username".

---

### Post by paulisdead on 2010-10-14
Try one of the tutorials from [http://howtoforge.com](http://howtoforge.com)

One of the ISPconfig tutorials for ubuntu would probably not be bad, since it gives you an easy to use control panel to manage everything from a web browser.  There are other great mail server tutorials there too.

---

