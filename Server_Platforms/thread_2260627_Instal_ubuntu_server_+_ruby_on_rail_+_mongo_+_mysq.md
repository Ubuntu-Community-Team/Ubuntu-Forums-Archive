---
title: "Instal ubuntu server + ruby on rail + mongo + mysql + apche"
date: 2015-01-13
forum: Server Platforms
---

### Post by Minh_Chau on 2015-01-13
I want to install ubuntu server + Ruby on rail + Mongo db + mysql + apche run ruby and php ? help me

---

### Post by TheFu on 2015-01-13
This is not a trivial task.  Do 1 at a time, starting with the base.  It is best to ask 1 question at a time ad to be highly specific, since ruby versions and rails version are highly version specific for compatible versions on different versions of Ubuntu.

Also - if you are going to program RoR, then you do not want to use the system version of Ruby - it is extremely out of date. You'll use something like rvm or rbenv to manage your ruby development and deployment environments.

So ... there are many, many how-tos for apache/mysql/php on the internet. If you aren't developing specifically for these, following the help.ubuntu.com guide is probably fine.  Don't know anything about Mongo - sorry.

For other instructions, howtoforge.com is a reasonable place to get things working, but do not expect to be secure when completed.  To lock down web apps is really difficult.  Start by reading the OWASP guides for you language to be certain you don't accidentally allow a back door into your network.

Thank you.

---

