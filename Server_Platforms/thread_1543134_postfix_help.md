---
title: "postfix help"
date: 2010-07-31
forum: Server Platforms
---

### Post by learnbash on 2010-07-31
hello folks,

i have mail server with following details.

1.postfix(virtual domains]
2. courierimap


i have a domain example.com that have email accounts like.

[EMAIL="user1@example.com"]user1@example.com[/EMAIL]
[EMAIL="user2@example.com"]user2@example.com[/EMAIL]
[EMAIL="user3@example.com"]user3@example.com[/EMAIL]
[EMAIL="admin@example.com"]admin@example.com[/EMAIL]
[EMAIL="staff@example.com"]staff@example.com[/EMAIL][alias for user1@,user2@,user3@]

how i restrict that only [EMAIL="admin@example.com"]admin@example.com[/EMAIL] have rights to send emails to [EMAIL="staff@example.com"]staff@example.com[/EMAIL]. No one from outside and no one from inside will not sent email to [EMAIL="staff@example.com"]staff@example.com[/EMAIL] only [EMAIL="admin@example.com"]admin@example.com[/EMAIL] will sent email to [EMAIL="staff@example.com"]staff@example.com[/EMAIL]. Please suggest how can i achieve that.

Edit/Delete Message

---

