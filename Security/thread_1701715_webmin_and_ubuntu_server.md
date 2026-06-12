---
title: "webmin and ubuntu server"
date: 2011-03-06
forum: Security
---

### Post by nicholasraad83 on 2011-03-06
I was told their are numerous security issues when installing webmin on a ubuntu server. ID like to confirm if this is true or not and in what circumstances...

also what can i do to button up security if this is the case.

i apologize if this issue was discussed before just trying to get a solid answer.

---

### Post by wacky_sung on 2011-03-06
Security has to do with how you secure the server but not just installing webmin which security issues arises.I been using webmin and enjoy the convenient of using it in a single box which you are in total control.

---

### Post by bodhi.zazen on 2011-03-07
Webmin is not in itself a security risk, but ...

You need to secure the interface (strong password, tunnel over ssl (https), etc)

---

### Post by silverado679 on 2011-03-07
Any specific ways webmin should be set-up to ensure its as secure as possible would be helpful.
 
Also if their is a better control panel instead of webmin out their that would also be helpful....  Love Cpanel but dont want to pay $35.00 a month...

---

### Post by silverado679 on 2011-03-07
> **bodhi.zazen said:**
> Webmin is not in itself a security risk, but ...
 
You need to secure the interface (strong password, tunnel over ssl (https), etc)
 
Sorry must of just posted after you did.

---

### Post by Soul-Sing on 2011-03-07
> **nicholasraad83 said:**
> I was told their are numerous security issues when installing webmin on a ubuntu server. ID like to confirm if this is true or not and in what circumstances...

also what can i do to button up security if this is the case.

i apologize if this issue was discussed before just trying to get a solid answer.

it is true that webmin was dropped out of the off. ubuntu software sources, almost three/four years ago(?), because of security issues. But imo it has/is strongly improved. I should be more concerned bout the things bodhi put forward.

---

### Post by EJeanmaire on 2011-03-07
What do you want Webmin to do?  Obviously it would help your Linux-experience by manually performing the server administration tasks.

---

### Post by CharlesA on 2011-03-07
> **bodhi.zazen said:**
> Webmin is not in itself a security risk, but ...

You need to secure the interface (strong password, tunnel over ssl (https), etc)

+1. IIRC Webmin uses SSL by default now, but I still wouldn't expose it directly to the internet.

---

### Post by cprofitt on 2012-04-01
I just completed a red-team blue-team exercise this weekend and one of  the issues that caught the blue-team was the fact that webmin allowed  the following?


port 10000

login user:  admin
password:  blank

check 'remember me'

this allowed the red-team to change the root password and then login via other services.

I still have to test webmin on Ubuntu since I am not sure if this was  the particular setup of the exercise or a default initial configuration.

---

### Post by CharlesA on 2012-04-02
Webmin uses existing sudo/root users IIRC

---

### Post by cprofitt on 2012-04-02
> **CharlesA said:**
> Webmin uses existing sudo/root users IIRC

Yesterday it was using something other than root... we were unable to login using root, but had the ability to change the password for root after using admin + blank password.

I just installed webmin on a 11.10 box... and that hole does not appear to be there... which is fantastic.

---

### Post by CharlesA on 2012-04-02
> **cprofitt said:**
> Yesterday it was using something other than root... we were unable to login using root, but had the ability to change the password for root after using admin + blank password.

I just installed webmin on a 11.10 box... and that hole does not appear to be there... which is fantastic.
Hrm. That makes me think it was prepped before the exercise. Good to know that doesn't exist on the default install.

---

### Post by boldford on 2012-04-02
One of the first things to do before exposing a Webmin equiped server to the Internet is to change the default port from 10000.

---

### Post by roffisserver on 2012-04-02
When I installed Webmin I had already taken security precautions. I think you should do the same. Since I installed I haven't had any issues.

---

