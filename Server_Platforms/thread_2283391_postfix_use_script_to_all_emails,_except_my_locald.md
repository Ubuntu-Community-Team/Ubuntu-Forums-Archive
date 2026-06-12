---
title: "postfix use script to all emails, except my localdomain"
date: 2015-06-21
forum: Server Platforms
---

### Post by Joao_Rodrigues on 2015-06-21
hi guys
I am using ubuntu 14 and after a couple of months working on it i face some problems. hopefully you can help me.
i am using postfix as MTA in several machines. One of those machines work as a gateway to internet. the other machines are like regular mta's All machines have python scripts that do several functions, like generate email... Imagine this situation:
 Machine A - MTA Gateway, domain is gate.problem.com
 Machine B - MTa, domain is issue1.problem.com
 Machine C - Mta, domain is issue2.problem.com


 So in machine B,C any email that i want to send to internet domain has to pass by gateway. However some emails can go the other simple MTA in the network.

 I have configured postfix to pipe all emails to script if those email end in ".com", however when i send through gateway an email to issue2.problem.com (or issue1) those mails when received in issue2/1 call the pipe transport function (thats the problem!!)

 So. i want send all mails to script using pipe transport, except the mails destined to the local domain/machine, even if those emails are destinated to ".com" domain. Maybe postfix have a parameter that sends mail to user mailbox instead of calling the script

 Hope some answers.

 Best regards

---

