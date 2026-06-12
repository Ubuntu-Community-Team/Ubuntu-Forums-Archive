---
title: "Syslog to PostgreSQL"
date: 2005-03-14
forum: Server Platforms
---

### Post by BoBoB on 2005-03-14
I have searched all over the web, and have found no useful information, just security concerns written by paranoid sysops.

If someone know how I can enable logging from my 10 Ubuntu PC's to a Postgres server, let me know.

My goal is to enable the following steps:

1. Enable forwarding of all logs on all my PC's to a common SQL server.
2. Enable security.

As long as the requirements in step 1 is not met, step 2 is of NO INTEREST!

I'm ranting about the security issue because most of the people who know how to do this are quite paranoid about security, and are forgetting the fact that this may not be an easy task to perform with full security enabled - like portmap, IP access to the SQL server, passwords, etc. All of this is MUCH easier to apply after I get things to work.

All PC's are running Warty - release 19.Oct.2004.

---

### Post by rich on 2005-03-14
This isn't something I've ever got round to doing (it's on the "when I am a competent admin" list) but I thought that this was what syslog did.

[http://www.syslog.org/](http://www.syslog.org/)


I'd imagine it would cope fine with 10 machines - is there a different reason for wanting it in SQL ?



Rich

---

### Post by BoBoB on 2005-03-14
[QUOTE=rich]I'd imagine it would cope fine with 10 machines - is there a different reason for wanting it in SQL ?[/QUOTE]
I have a lot of experience in SQL, and can retrieve about any statistics I want out of an SQL table. I also have some experience in PHP and PostgreSQL, so I would really want to get access to all my logs via my SQL database.
I'm using PostgreSQL with several other applications, so that's my first choice on the Linux platform.

(MySQL is not an option at all. It lacks way to much advanced ANSI SQL compatibility)

I'll check out syslog.org, thanks for the link.

---

