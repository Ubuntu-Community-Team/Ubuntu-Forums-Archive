---
title: "Postfix problem"
date: 2009-11-23
forum: Server Platforms
---

### Post by milindras on 2009-11-23
Hi all,
I have a strange problem on my Profix installed on a Ubuntu live web server.We are using postfix for sending & receiving mails. For a perticular virtual server if I change or deleted an existing Alias, it will stops sending & receiving emails for the whole server. I have attached the error when I get on those occations. 
 
So to get into normal mail operation, I have to delete the whole Alias & re-create it again as a fresh one. Even when the problem occur, if i create a new one that starts to work.
 
For an example
[EMAIL="info@mydomain.co.uk"][COLOR=#22229c]info@mydomain.co.uk[/COLOR][/EMAIL] has an alias > [EMAIL="name1@ctc-solutions.co.uk"][COLOR=#22229c]name1@ctc-solutions.co.uk[/COLOR][/EMAIL]
If I add another one
[EMAIL="info@mydomain.co.uk"][COLOR=#22229c]info@mydomain.co.uk[/COLOR][/EMAIL] has an alias > [EMAIL="name1@ctc-solutions.co.uk"][COLOR=#22229c]name1@ctc-solutions.co.uk[/COLOR][/EMAIL], [EMAIL="name2@mydomain.co.uk"][COLOR=#22229c]name2@mydomain.co.uk[/COLOR][/EMAIL]
Its working fine. But if you edit a existing alias like
[EMAIL="info@mydomain.co.uk"][COLOR=#22229c]info@mydomain.co.uk[/COLOR][/EMAIL] has an alias > [EMAIL="name1@ctc-solutions.co.uk"][COLOR=#22229c]name1@ctc-solutions.co.uk[/COLOR][/EMAIL], [EMAIL="name2222@mydomain.co.uk"][COLOR=#22229c]name2222@mydomain.co.uk[/COLOR][/EMAIL]
it will stop all mail sending & receiving
If you delete/change or etc.. [EMAIL="name2222@mydomain.co.uk"][COLOR=#22229c]name2222@mydomain.co.uk[/COLOR][/EMAIL] or the other one, but still mail not working.
If I delete the whole record & re create that or create another new alias, then it starts wroking.
 
Thanks

---

