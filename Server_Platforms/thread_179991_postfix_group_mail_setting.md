---
title: "postfix group mail setting"
date: 2006-05-21
forum: Server Platforms
---

### Post by kimes on 2006-05-21
I'm mail server newbie, I'm just wondering how i can implement group mail feature in postfix..

let's say, my host is abcd.com and one man send mail to [email]sales@abcd.com[/email].
Then the mail should go(foward) to every sales employee (jon@abcd.com, [email]jane@abcd.com[/email], [email]mary@abcd.com[/email] etc..)

This seems to be easily done by forward feature. But I could not get the way.
Could you give me a little clue?

Many thanks

---

### Post by Glut on 2006-05-22
quickest option is to add a line to /etc/aliases (or where-ever your aliases files is)
sales:        [email]fred@abcd.com,jane@abcd.com[/email],mary

Then type 'newaliases'

---

