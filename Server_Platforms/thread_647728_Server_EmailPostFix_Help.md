---
title: "Server Email/PostFix Help"
date: 2007-12-22
forum: Server Platforms
---

### Post by Oen386 on 2007-12-22
I have followed this setup (#14):

[http://www.howtoforge.com/perfect_server_ubuntu7.10_p5](http://www.howtoforge.com/perfect_server_ubuntu7.10_p5)

I should mention that I selected OpenSSH, MySQL, Apache, and PostFix when I did the Ubuntu 7.10 server install.

(I am using TimeWarner, in case this could just be port blocking?)

I have had no luck. I am not sure what the issue is. I thought maybe ports were blocked, but I tried a similar setup on a friend's machine a while back with no issues.

I am wondering if I need to setup Gmail SMTP, and if so what steps do I need to take from here?

Thanks,
Oen

---

### Post by rsw686 on 2007-12-22
Most residential ISPs block ports 80 for incoming requests and 25 for incoming/outgoing (besides their smarthost). They require you to go through their smarthost to send mail. You will most likely need to pay for business service to do what you want to do.

Besides saying you have no luck, what is the specific problem you are having. Have you tested out the daemons on the local machine with telnet?

---

### Post by Oen386 on 2007-12-23
> **rsw686 said:**
> Besides saying you have no luck, what is the specific problem you are having. Have you tested out the daemons on the local machine with telnet?

Yeah I ran the telnet tests listed on the link I gave.

I am not sure how to run more tests to identify the problem, I was hoping for something like that.

I tried "sendmail -bv [email]my@email.com[/email]" thing, but got nothing at the address I specified.

I do not quite understand what a Smarthost is. Could that be something like Gmail that handles my outgoing/incoming email?

---

### Post by Oen386 on 2007-12-23
Well I think I found a solution.. but I am stuck with the Thawte cert.

[http://ubuntuforums.org/showthread.php?t=329294](http://ubuntuforums.org/showthread.php?t=329294)

---

### Post by Oen386 on 2007-12-23
Found the answer... its working great!

---

