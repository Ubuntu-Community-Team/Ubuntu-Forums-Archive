---
title: "Is php memory causing 404 error?"
date: 2009-03-02
forum: Server Platforms
---

### Post by R.Bucky on 2009-03-02
I have a fresh install of Ubuntu Server 8.04 with a Concrete5 base, Wordpress Blog, Glype proxy, and a couple of straight html files. My logs show a php memory limit has been met. I set the php memory at 150M (php.ini) after my initial problem, which manifests itself by producing a 404 error after about a week now. Previously, the nasty 404 appeared after 24-36 hours. Then I changed the memory limit.

How would I clear my php memory without restart my server? Clearly, this problem cannot be normal. What suggestions do people have?

Thank you

---

### Post by jpeddicord on 2009-03-02
Yikes, PHP should *never* be reaching that limit. What software are you running on it? Sounds like it has a memory leak problem.

edit: never mind, you already listed what you have running on it. :)
What you could do as a temporary fix would be a cron job to run every 10-12 hours to restart Apache or your PHP processes to clear out the memory usage.

---

### Post by R.Bucky on 2009-03-02
Thanks for the response - I do not have the experience to say that it was a memeory leak. But, it surely sounds that way. 150M is way too much. 

Two words - Cron job!

---

### Post by Vegan on 2009-03-02
Interesting, I have never seen a memory leak with PHP5. I have never bothered to modify the php.ini file and it runs my phpBB fine even when using the forums heavily.

:guitar:

---

### Post by R.Bucky on 2009-03-04
This is all quite strange. My server is up now. I am away on business, so it is nothing that I did at all. The server is setup to disallow remote access. Very strange! I am anxious to look at the logs

---

