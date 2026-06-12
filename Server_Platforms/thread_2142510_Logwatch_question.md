---
title: "Logwatch question"
date: 2013-05-05
forum: Server Platforms
---

### Post by brent1975 on 2013-05-05
Hello, I have a question for someone that is experienced with logwatch. I am currently running 12.04 with postfix that relays using gmail's smtp servers for email. Which is working perfectly. The main purpose is for folks to be able to register with the forums. So far it is working flawless.  I am using that method so I don't have to maintain a mail server and also because I am on a residential IP it would be blocked from a lot of domains.  I want to set up some sort of method that error logs are email to me. I came across log watch and seems like this is what I am wanting. But maybe there is something else out there that would be better. Here is my list of of what I would like to see.... A daily email weather or not there is issues, intrusion attempts, and any other system failure issue.  Would logwatch be the best solution for what I am looking for? any other options would be great to hear about. Also with how I have postfix set up on my server will logwatch work proper?

Any advice tutorials would be greatly appreciated.


-Brent

---

### Post by CharlesA on 2013-05-06
Logwatch will monitor dovecot and postfix, but I am not sure if it will detect intrusion attempts or not.

---

