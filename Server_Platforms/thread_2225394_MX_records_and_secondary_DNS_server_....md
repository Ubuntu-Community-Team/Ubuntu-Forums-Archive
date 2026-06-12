---
title: "MX records and secondary DNS server ..."
date: 2014-05-21
forum: Server Platforms
---

### Post by mohammed8 on 2014-05-21
Hi,
I'm the administrator of a website ... For mail server we use google Applications ....
The problem is that when my local DNS server goes down for any reason, users of our email server can't receive emails because the Google MX records are no longer available.

I installed a secondary DNS server and all goes good (zone transfer performed) ... but the problem remain unsolved ... 

My question is : Are, the MX records transferred on the secondary DNS server !!!???

if NoT ... is there a solution to my problem 

Cordially

---

### Post by SeijiSensei on 2014-05-21
If you have the correct MX records in the zone file, then yes, they should be transferred.

Can you show us the zone file, particularly the copy that resides on your secondary server?  Wrap it in [noparse]```

```[/noparse] tags for readability.

Here's a test you can run.  Suppose the IP address of your secondary is 10.10.10.10.  You can query its MX records like this:
```
host -t mx example.com 10.10.10.10
```
Replace "example.com" with the name of your domain and "10.10.10.10" with the IP address of your secondary.  Run this test from a different machine with Internet access.

---

### Post by mohammed8 on 2014-05-21
Thank you for reply,

I did the test you suggested and all is OK  ...the MX records were transferred  ...

But 

the problem remain : W[COLOR=#000000]hen my local DNS server goes down for any reason, users of our email server can't receive emails 
[/COLOR]

So it's not related to MX records ...  !!!

Any suggestion !!! ???  Please

---

### Post by mohammed8 on 2014-05-21
Hello, :p

I think that the problem was resolved ...

The secondary DNS server was not declared in my parent nameserver ... 

So messages were not be able to find AMX records although they were on the secondary DNS server ...


Great thanks ...

---

