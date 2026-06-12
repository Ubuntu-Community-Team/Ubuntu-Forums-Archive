---
title: "postfix: How to set display name in FROM header when using zoho smtp relay"
date: 2024-11-18
forum: Server Platforms
---

### Post by NotQuiteSU on 2024-11-18
I set up zoho for my smtp relay for new 24.04 server. I mostly followed this guide: [https://gist.github.com/cristiroma/d0cc9f0c23bbba0994f3b263dabd7e75](https://gist.github.com/cristiroma/d0cc9f0c23bbba0994f3b263dabd7e75)

When an email as sent, the display name is that of the linux account (root, admin), rather than the display name of the account, or one I choose. (eg -Jeeves [email]jeeves@mydomain.com[/email])
The emails come from admin (jeeves@mydomain.com)

I tried to use the generic maps like suggested here, but no luck [https://stackoverflow.com/questions/14370224/change-outgoing-mail-address-from-rootservername-rackspace-sendgrid-postfix](https://stackoverflow.com/questions/14370224/change-outgoing-mail-address-from-rootservername-rackspace-sendgrid-postfix)

I'd like to avoid specifying the FROM/Sender header in every email I script/send.

---

