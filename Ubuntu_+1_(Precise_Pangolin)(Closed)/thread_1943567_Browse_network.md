---
title: "Browse network"
date: 2012-03-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by tajreed on 2012-03-19
What does 'browse network' supposed to show in 12.04? Is there additional software necessary? I get the following.

"Error: DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Please select another viewer and try again"

---

### Post by PaulW2U on 2012-03-19
> **tajreed said:**
> What does 'browse network' supposed to show in 12.04? Is there additional software necessary? I get the following.


I see other PCs and my NAS drive that are present on my local network. Yes, I so have additional software installed such as winbind and samba.

Do you have a local network? If not, may be that is why you get the error message.

---

### Post by tajreed on 2012-03-19
Yes, I have a printer, laptop, pc and external HD. All through a wireless router.

---

### Post by cariboo on 2012-03-19
The browse networks only works if you have Windows networking set up, for example if you have windows computers on your network, and have a shared directory set up, or if you have samba installed on your Ubuntu computers.

---

