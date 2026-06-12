---
title: "superuser created in django, what does this mean?"
date: 2012-12-29
forum: Security
---

### Post by tojonukokhadush on 2012-12-29
while following django project i happened to create a superuser as shown in the screenshot. so what in the case i am not going onto the project again(its really a tough game :mad:); does it alter any security issues regarding my system? please help!

---

### Post by nosmadar on 2012-12-29
I think it's hard to say without knowing what Django does when it creates a "super user".  Normally, one would think that it means the user can use the "sudo" command.  But what does Django need to to?  What would it need access to?  Perhaps your user just got added to the "Django Auth system" as a super user, which only grants it the Access needed to manage Django in the Unbuntu world. Hopefully Django is set up so that's the case.

---

### Post by uRock on 2012-12-29
Moved to Security Discussions.

---

### Post by tojonukokhadush on 2012-12-30
hey nosmadar, thanks for replying!

i just followed this link that teaches me to make web developer framework in python programming language-

[https://docs.djangoproject.com/en/dev/intro/tutorial01/](https://docs.djangoproject.com/en/dev/intro/tutorial01/)

since i am new to whole of the linux; so could not figure out what changes those commands are going to bring so was worried!

actually the command was like this-

python manage.py syncdb

hope nothing bad i have done :-)

---

