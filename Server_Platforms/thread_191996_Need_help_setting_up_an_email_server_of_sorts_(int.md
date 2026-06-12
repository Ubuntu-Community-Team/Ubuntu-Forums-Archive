---
title: "Need help setting up an email server of sorts (internal)"
date: 2006-06-08
forum: Server Platforms
---

### Post by derrick1985 on 2006-06-08
Hi,

I don't know exactly the name of what I want to set up but i'll explain it here and see if anybody can help me.

I have a small home office that so far, each computer collects it's emails seperately from the ISP. I want to make  a server box (Cel. 366, 64MB Ram) collect the mail from the accounts and forward it to the correct machines on the home network. Also, I want the option of a shared calander that can be access on the windows machines via Outlook. Is this possible?

Thanks

Derrick

---

### Post by LordHunter317 on 2006-06-08
The best way to do this would be to centeralize email on that server and make everyone access it through IMAP.  Otherwise, there is no point.  Postfix, getmail, and Davecot or Courier-IMAP can do this pretty easily.  

As for shared calendering, there are no good solutions.  phpGroupWare has one, as does the Horde suite and eGroupWare.  You can decide if any of those are acceptable.

---

### Post by derrick1985 on 2006-06-08
Yes, but will this work fine on a computer that won't have a GUI?

---

### Post by LordHunter317 on 2006-06-08
Yes :)

---

### Post by derrick1985 on 2006-06-08
Ok then, are there any guides that I can follow to get this up and running?

---

