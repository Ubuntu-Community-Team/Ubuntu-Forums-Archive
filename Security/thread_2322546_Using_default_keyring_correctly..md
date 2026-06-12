---
title: "Using default keyring correctly."
date: 2016-04-28
forum: Security
---

### Post by crip720 on 2016-04-28
Have a clean install Ubuntu 16.04 and every so often default keyring will pop up asking that an application wants the password.  I do not mind if keyring wants password, but would like to know if there is any way to have keyring mention what application wants to use it?  So far have no user keys listed in Password and keyrings, probably since I have been hitting cancel for the pop ups.  Do not really like to give password to something that does not mention what it is for.  I know most times it is for an application that I am using/running.  Thank you.

---

### Post by UbuntuAddict99 on 2016-04-28
Hello Crip720,

In my personally experience and ICT knowledge _**DO NOT EVER USE SAVED PASSWORDS!**_
It is a treasure trove of information for a computer to save the safest place for your password are in your memory. Or in a notebook that you keep hidden in you house.


But for a response to your question.

[U][B]IF, 
[/B][/U]I remember correctly, whatever program and or online service you use Eg, E-mail. That asks you to save your password should save it to your key chain. I COULD be wrong the last time i used a Key chain was back in 2005 on a Emac G4 OS X Apple PC. and when you access your Key chain it will show the password and the application/service that the password is for in a golden list of information.

I know it is not a fully descriptive professional answer but i hope it has helped.

Happy Linuxing.

---

### Post by crip720 on 2016-04-28
I have had used keyrings on Ubuntu's before 16.04, but on the pop up it just says an app wants the password, never gives what app is asking for it.  I have been just hitting cancel and nothing seems to be complaining yet on 16.04.  Just wondering if it is needed.  I think two of the apps that are asking are chrome and maybe vpn that I have open in terminal.

---

### Post by DuckHook on 2016-04-29
*Your thread has been moved to **Security** as the forum more suited to your issue.*

> **crip720 said:**
> ...I think two of the apps that are asking are chrome and maybe vpn that I have open in terminal.Many system processes use the keyring to keep password data and are innocuous, WIFI passwords for one. When in doubt, always look at logs: in your case, dmesg and auth.log

Your logs are your best friend, and the first line of inquiry when smelling something fishy.

---

### Post by crip720 on 2016-04-29
Basically what I would like to know is there a way to have the keyring pop up to mention what app is asking, instead of the pop up just saying some unnamed app wants it?  Thank you.

---

### Post by DuckHook on 2016-04-29
> **crip720 said:**
> Basically what I would like to know is there a way to have the keyring pop up to mention what app is asking...Not that I know of. It's one of the little irritations in Ubuntu. You have good instincts, though... wanting to know what something is up to before agreeing. In the same spirit, I would point out that even if such reporting were enforced, it wouldn't represent any real security. Malware would likely be written well enough to report itself as something innocuous. You are always better to look in your logs. You could also allow the keyring addition and then look in the keyring to see what it is. You could delete the key entry if you didn't like it.

---

### Post by crip720 on 2016-04-29
I will mark this solved for now.  Do you know of any common apps(like browsers) that absolutely need keyring access, I have been just hitting cancel on 16.04 and everything is still working.  Thank you.

---

### Post by DuckHook on 2016-04-30
> **crip720 said:**
> I will mark this solved for now.  Do you know of any common apps(like browsers) that absolutely need keyring access, I have been just hitting cancel on 16.04 and everything is still working.  Thank you.The answers to your questions are in your logs.

---

