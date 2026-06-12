---
title: "postfix architecture"
date: 2009-12-19
forum: Server Platforms
---

### Post by linuxfrance on 2009-12-19
Hello 
this is my first post here , so If any mistake with this post please let me know .

question 1 : is this a good  postfix architecture  ??

I have 2 postfix Servers :

[LIST]
[*]DMZ_postfix which has basic protection (192.168.0.1). and forward emails to LAN_postfix
[*]LAN_postfix which has the users accounts , amavis_new , spamassassin and clamav
[/LIST]
is it good to install tha anitspam and the anti firus on the lan server ,or I had to do it on the DMZ server ??

Question 2 : Lan_postfix server consider my DMZ_postfix as local , is it normal ?

I have something like this in the log :
```

Passed Clean LOCAL 192.168.0.1 , 217.17.80.8 

```
I understand that emails sent from my server arr considered LOCAL , but not emails coming from outside .
 
infact amavis consider all my emails as LOCAL 

Thank you in advance for your help

---

### Post by linuxfrance on 2009-12-19
any , Idea , I think Iwill try a mailing list for postfix :(

---

### Post by craigp84 on 2009-12-20
Hi linuxfrance,

Q1 this is a workable architecture, i wouldnt have any grave concerns putting this layout into production.

For me, i would put the anti-spam on the DMZ (dont want to even bother wasting bandwidth transferring spam inside the network, just filter it at first contact. On top of that, a lot of the ability to filter spam (graylisting springs to mind) requires that you do it on the first mailserver the inbound connections hit.

I would do the virus filtering inside the lan -- virus filters require updating, and ideally you want to block all traffic outbound from the DMZ where possible (if  a trojan / bot does get it, it can't talk back out to its master for instructions).

Q2 This goes back to the reason for putting spam filtering on the DMZ instance -- you loose some information & some ability to test the sender to see if they're an obvious spammer.

---

### Post by linuxfrance on 2009-12-20
so this is a normal behaviour for Q2 when using this design . 

thank you for your answer

---

