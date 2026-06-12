---
title: "mail cammand from postfix is not parsing the html content on outlook"
date: 2024-03-22
forum: Server Platforms
---

### Post by ahsantahir414 on 2024-03-22
Hi,

We have postfix installed on our linux server and we get html report showing table on our outlook inbox which is fine. 
But recently our client told us to change the relayhost to new ip under main.cf file under /etc/postfix.

After the change the email we are getting not correctly parsing the html.

I want to figure out why the mails are not getting parsed to html code to table.

Cammand we are using in our reports which was working previously 

[B]echo -e "$EMAIL_BODY" | mail -s "$(echo -e "$SUBJECT\nContent-Type: text/html")" "abc@xyz.com"

[/B]Any help would be appreciated

Regards

---

### Post by Irihapeti on 2024-03-22
*Thread moved to **Server Platforms** for a better fit.*

---

