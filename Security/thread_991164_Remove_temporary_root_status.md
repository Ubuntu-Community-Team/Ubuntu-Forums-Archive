---
title: "Remove temporary root status"
date: 2008-11-23
forum: Security
---

### Post by Capslock118 on 2008-11-23
Hi,

I have a fingerprint reader utilizing fprint.

In order to login, use sudo/su in the console I am required to use the fingerprint instead of the password. This is great! except in the console, I can do something in sudo once and it works. After that I get a "Segmentation fault". If I wait maybe 10min or whatever it may be the temporary sudo rights are taken away and I can try again and it will work.

So basically, if I need to use sudo more than once for a multi-step process, i am out of luck until my temporary rights are taken away.

Before I can permanently fix this issue, what I am looking for is a command, if there is one, that will force the OS to take away my temporary sudo rights, there by allowing me to try to access sudo privileges using my fingerprint / password again.

Again, I understand that a work around is not ideal, but regardless, if such a command exists it would be good to know it.

Any thoughts?

---

### Post by Capslock118 on 2008-11-23
haha,

of course, as soon as I post I just happen to hit the right set of keywords in google and came up with this:
[URL="http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg946814.html"]
http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg946814.html[/URL]

It looks like this thread may even solve the issue permanently but the "sudo -k" is what I was looking for :)

Writing things down tends to clear the mind.

---

### Post by bodhi.zazen on 2008-11-23
If you like you can configure sudo.

Use visudo 

See this link : 

[http://www.gratisoft.us/sudo/man/sudoers.html#sudoers_options](http://www.gratisoft.us/sudo/man/sudoers.html#sudoers_options)

> **timestamp_timeout** 
Number of minutes that can elapse before **sudo** will ask for a passwd again. The default is 5. Set this to 0 to always prompt for a password. If set to a value less than 0 the user's timestamp will never expire. This can be used to allow users to create or delete their own timestamps via sudo -v and sudo -k respectively.

---

