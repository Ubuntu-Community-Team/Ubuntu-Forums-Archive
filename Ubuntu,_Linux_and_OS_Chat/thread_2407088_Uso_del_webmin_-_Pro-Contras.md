---
title: "Uso del webmin - Pro-Contras"
date: 2018-11-29
forum: Ubuntu, Linux and OS Chat
---

### Post by juanferaviles on 2018-11-29
Hello, I have been reading about different topics and the truth is that the Ubuntu or Linux servers seem very good to me.
I have been using Windows server with xampp for years and I am surprised with the performance of Ubuntu server. Using the xampp in U.S18.04 I have had problems sending emails and they say that using webmin is very easy, but when one goes to administer several servers it is a problem because webmin only gives you one.
Do you recommend the webmin or is it better to use everything native? Pro and cons thank you.

---

### Post by mastablasta on 2018-11-30
webmin for long time didn't even work well with ubuntu. it was advised not to use it. it looks like it does work now.

i use Ajenti instead. the configuration is done via text (configuration) files anyway and the user interface is actually not needed. just a text editor. so often i would do things via command line. however, sometimes it is nice to have a good looking text editor available and some monitoring options.

Zentyal (Ubutnu based SBS) has a good UI, however they removed many features or rather moved them to community. not sure where are they now since it has been a wile since i tested them. another good UI for home user is Openmediabox (Debian based). not sure if the UI can already be installed on ubuntu. in any case very easy to use and rich in plugins.

there are a few other non ubuntu interfaces to explore (e.g. clearOS...). many of them offer a lot more than a home user would normally need.  my favourite non ubuntu UI is Nethserver which is CentOS based. easy to use, great community good documentation.

---

### Post by TheFu on 2018-11-30
Professional IT admins use devops tools to manage Unix servers.  Those would be Ansible, Puppet, Chef, CFEngine or Salt-Stack.  I prefer ansible.  1 or 2,000 systems can be managed with these tools.  Some scale to 100K+ systems.

IMHO, webmin is for hobbyists only or for places where a senior admin sets up 5 tasks for jr admins to handle through the webmin interface.  One problem with webmin is that it provides another attack vector for crackers to take over a system if it is available from anywhere outside the local machine, localhost.  The main technique to mitigate those attacks is to only allow webmin access from localhost and to force an ssh tunnel be used.  But for more than 1 computer, this would be a hassle.

Ansible is the easiest way to manage 5-200 servers that I know, but the admin still has to know how to perform all the tasks manually.

Someone coming from Windows will have a very steep learning curve to switch to the Unix mindset.  It is a different way to thinking, but very rewarding.  When I was new to Unix, I was always asking "why?", because some things didn't make sense to me. As I learned more, things started looking smarter and smarter.  Now I know that every odd choice has an excellent reason behind it.  For people like us, this stuff is fun.

Think I saw something in another post about sending email ... On Unix systems you need an MTA - Mail Transfer Agent.  Multiple different tools can perform that roll.  Sendmail was very popular until about 2000. After that, simpler and more secure options became more widely used - postfix and exim.  But those are full send/receive SMTP servers. If you just want to send outbound emails, there are some simpler answers that cannot receive at all.   Beware running sendmail.  It is an extremely complex system that only the very largest email providers need.  For ISP and home users, postfix is usually 100x more than we need for an MTA.  

Anyways, have fun with this stuff, and please try not to be hacked.

---

