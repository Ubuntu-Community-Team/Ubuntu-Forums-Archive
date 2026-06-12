---
title: "Sendmail username/group?"
date: 2009-03-30
forum: Server Platforms
---

### Post by Loan_Refi on 2009-03-30
Hi I have been triying to set up Sendmail for about 5 days whenever I have time. 

I did it for sending email from commandline fast & easy. I only have a need for outbound email only.

I have setup Sendmail + Nail successfully as follows;

# apt-get install sendmail
# apt-get install Nail

after I install sendmail I configured sendmail with the following command;
# sendmailconfig
I answered Yes for the the questions and I set up Masquerade to show my domain name in;

/etc/mail/sendmail.mc

I added the following lines to the bottom of the file;

MASQUERADE_AS(MyDomain.com)dnl
FEATURE(masquerade_envelope)dnl
FEATURE(masquerade_entire_domain)dnl
MASQUERADE_DOMAIN(MyDomain.com)dnl

Replace mydomain.com with your domain name.

I have been using it this setup with MS.Exchange no POP account and I only use it for outgoing mail.

I have set up Sendmail on two other machines for using Drupal & fax to email "gtkfax".

In case anyone has knowledge on how to set the correct email username correctly please let me know.  

This is what I did to set my emial to display correctly;

I created a new user with with;

useradd 
I set the password with
passwd newuser

when I send out an email I change to the username I created and it displays my correct email address

BUT 

Then I found out by reading these Nail instructions;

[http://linux.die.net/man/1/nail](http://linux.die.net/man/1/nail)

that you can set the "From" address by typing;

-r [email]joesomebody@example.com[/email] 

So there is no need to create a new user account for your system just so one can display the correct From email address.

I still want to know if anyone has knowledge on how to set the /etc/mail/genericstable so that I can avoid having to type "From [email]myemail@example.com[/email]" everytime I send an email.

What I want to do is map my real email address to my local user account so this process would be done automatically.

All help is greatly appreciated.
Thanks!

---

### Post by Brunellus on 2009-03-30
Thread moved.  If you're asking a new question, start a new thread;  do not hijack an existing thread.

---

