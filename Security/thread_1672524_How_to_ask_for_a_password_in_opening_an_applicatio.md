---
title: "How to ask for a password in opening an application"
date: 2011-01-21
forum: Security
---

### Post by extraordinary_boy08 on 2011-01-21
Hi everyone!

I just would like to know how to ask for a password in opening an application in ubuntu. The scenario is like in opening any application from system administration and the system will ask for a password to execute the application.

Thanks in advance! 

:)

---

### Post by Bucky Ball on 2011-01-21
Not the greatest idea because then you will be running your applications as root. DANGER Will Robinson.

The reason you are asked for a password to do admin tasks is because you are potentially able to do something that could break your install. You are changing the configuration.

There are ways of doing what you ask but unwise. Once you input a password you are logged on as root and consequently have the ability to change you system setup.

---

### Post by extraordinary_boy08 on 2011-01-21
> **Bucky Ball said:**
> Not the greatest idea because then you will be running your applications as root. DANGER Will Robinson.

The reason you are asked for a password to do admin tasks is because you are potentially able to do something that could break your install. You are changing the configuration.

There are ways of doing what you ask but unwise. Once you input a password you are logged on as root and consequently have the ability to change you system setup.

Thanks for the response! Maybe I should just plan the application with built in command that asks for a password to make my application more secure..

---

### Post by cariboo on 2011-01-21
How is asking for a password before running an application more secure? 

Who's password is supposed to entered before running the application?

---

