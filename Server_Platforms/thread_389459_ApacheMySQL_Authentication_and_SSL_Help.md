---
title: "Apache/MySQL Authentication and SSL Help"
date: 2007-03-20
forum: Server Platforms
---

### Post by nick1 on 2007-03-20
Greetings,

I'm hoping someone who's been down this road many times can tell me if I have my story straight.
I would like to use apache and mysql to authenticate users to an "administrator only" portion of my website.
I would also like the communications over that portion of the website to be encrypted.
This is all on a LAMP installation of the newest version of Ubuntu server.

I've done some research and it looks like I need the following:

1.) Apache/MySQL authentication : mod_auth_mysql
2.) Secure Communications : SSL

Is this correct?  I've read of something called mod_myauth for apache2.
What is the difference between mod_auth_mysql and mod_myauth ?
I was a little surprised of the lack of documentation on setting up mod_auth_mysql.
Can you recommend some thorough tutorials on these subjects?

Any other advice from the battlefield would be greatly appreciated.
Thank you for your time,

*Nick*

---

### Post by astrogazer on 2007-03-21
I believe most developers seem to use a scripting approach only by utilizing session tracking.

---

