---
title: "Likewise restricting access for domain users"
date: 2010-03-03
forum: Security
---

### Post by oj0kksn5 on 2010-03-03
hello,

i am currently trying to intergrate a ubuntu 8.04 machine onto our windows network. i have used likewise-open to allow users to login to the machine via they domain account, also i have allowed the domain admins to be able to sudo the machine. however i want to be able to restrict the menu or applications based on your domain account as i dont not want lower end users being able to open terminal etc.

i have look on the internet for a solution but all solutions are local users only

cheers

---

### Post by oj0kksn5 on 2010-03-04
anyone?

---

### Post by docsmooth on 2011-05-24
Likewise Open will make the Domain users look like local users to the majority of your tools, so the gconf commands you've likely seen for local users should work exactly the same for your Likewise Open Domain users.  Just remember to quote the user properly, because your shell will likely interpret the "\" as an escape character.

(I know it's an old thread, but still shows up high in search results.)

---

### Post by ggsict on 2011-06-30
Has anyone had any luck doing this?  I'm in exactly the same situation; everything is good to go for Windows domain users on an Edubuntu subnet but I need to lock down users.

I was going to use Sabayon but there's a bug in Likewise that stops Sabayon being able to see the domain users and therefore be able to apply profiles to them.  I really need a solution other than Sayabon. 

People mention gconf-editor but I still can't see how you apply it to domain users.

---

