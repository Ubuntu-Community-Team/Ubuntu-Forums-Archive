---
title: "Error when i run RKHUNTER"
date: 2008-05-28
forum: Security
---

### Post by xMoDx on 2008-05-28
Does someone have same experience? can someone explain what should i do to fix this


What i changed 

i removed comment because i would like that i will be receiving email reports of my rkhunter logs

> #
# Email a message to this address when a warning is found.
# Multiple addresses may be specified simply be separating them
# with a space.
#
[COLOR="Red"]MAIL-ON-WARNING=myname@xmodx.com   [email]admin@xmodx.com[/email][/COLOR]

[B]
ERROR: @ Terminal when i execute rkhunter -c[/B]
> Invalid MAIL_CMD configuration option - command 'mail' is non-existent or not executable.

---

### Post by Monicker on 2008-05-28
Seems like a config file somewhere is set to use the mail command for delivering the report.  I think installing the mailx package might resolve that for you.

---

### Post by xMoDx on 2008-05-28
> **Monicker said:**
> Seems like a config file somewhere is set to use the mail command for delivering the report.  I think installing the mailx package might resolve that for you.


Yes, you are correct i did set it on config that rkhunter should send logs to my email, apt-get install mailx solve the error but i still dont recieve any email, **do you have idea what is causing this?**

---

### Post by Monicker on 2008-05-29
Do you have an MTA configured for sending locally generated emails to an external address?  I usually just relay from postfix to my isp's mail server.  I believe you should have been prompted to install exim or postfix along with mailx.  If so, you will need to make sure they know how to communicate to external mail servers.  During the postfix install it prompts you for the configuration to use. In my case I just chose "smart host", and put the address of my isp mail server.

---

### Post by xMoDx on 2008-05-29
> Do you have an MTA configured for sending locally generated emails to an external address? 


sorry but i dont have any idea, 

> 
I usually just relay from postfix to my isp's mail server.

could you please give a simple example?

> During the postfix install it prompts you for the configuration to use

nope it did not prompt me, i check usng Synaptic Package Manager Exim is already been installed, btw im using ubuntu Hardy

---

### Post by hyper_ch on 2008-05-29
the email-domain that you want to sent the email to, is that on the same server where you run rkhunter from?

---

### Post by xMoDx on 2008-05-29
> **hyper_ch said:**
> the email-domain that you want to sent the email to, is that on the same server where you run rkhunter from?


nope, rkhunter is running on my personal box

---

### Post by fcorourke on 2008-05-29
Hi, I am fairly new to Ubuntu and Lnux. I installed RKHUNTER -- where would it be?? I have looked around and notice nothing that seems linked or pointing at anything to do with scanning anything.  I would appreciate the help, sorry for being/feeling so dense.

    Fred

---

### Post by fcorourke on 2008-05-29
never mind I am to lazy -- ran it and now need to check out warnings. Thanks everyone.

    Fred

---

