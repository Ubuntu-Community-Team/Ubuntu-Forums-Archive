---
title: "phpmailer and gmail smtp and addReplyTo"
date: 2016-09-23
forum: Server Platforms
---

### Post by maclenin on 2016-09-23
I have set up a rudimentary [phpmailer]("https://github.com/PHPMailer/PHPMailer/wiki/Using-Gmail-with-XOAUTH2") contact form which uses smtp.gmail.com with xoauth2 authentication.

All works - as hoped - but for the reply-to behavior observed in a handful of test emails sent to a non-gmail email address.

If the **addReplyTo** field points to the oauthUserEmail (gmail.com address) or any other **gmail.com** address:

1. (Reply-) "To" field in Thunderbird will be filled by the addReplyTo gmail.com address.

2. (Reply-) "To" field on a mobile device will be filled by the oauthUserEmail (gmail.com address).

If the **addReplyTo** field points to any other (non-oauthUserEmail) / **non-gmail** email address:

3. (Reply-) "To" field in Thunderbird will be empty.

4. (Reply-) "To" field on a mobile device will be filled by the oauthUserEmail (gmail.com address).

Hoped-for reply-to functionality would to be able to reply-to any gmail or non-gmail addReplyTo-assigned email address.

Thanks for any thoughts.

---

