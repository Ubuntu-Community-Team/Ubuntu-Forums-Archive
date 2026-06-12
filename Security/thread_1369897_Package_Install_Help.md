---
title: "Package Install Help"
date: 2010-01-01
forum: Security
---

### Post by JohnRLaw on 2010-01-01
I just installed ubuntu on my net-book yesterday so I am still getting up  to speed. The problem I have is when I try to install a package using dpkg in the terminal window I get a message that I don't have rights to install the package. When working in the gui environment a window appears, I put in the password and everything is great. I need to know how to get the correct admin rights when using the terminal to install a program. Any help out there is appreciated, Thank you.

---

### Post by bruno9779 on 2010-01-01
the command used by ubuntu to give root privileges to a commad is:

```
sudo
```

(Super User DO)

so, you should put it before the command you want to authorize:

```
sudo dpkg -i [packagename]
```

Be careful of what you sudo

EDIT: and welcome aboard!!!

---

### Post by ehickman on 2010-01-01
If you are doing something in a terminal and you don't have the permissions you need. you can use sudo to gain root permissions

sudo dpkg (what ever you are doing here)
then type password hit ENTER and your on your way

---

### Post by bruno9779 on 2010-01-01
I like your attitude, getting on the command line right away.

I strongly advise you to check this out: [http://linuxcommand.org/](http://linuxcommand.org/)

One of the best tutorials on the CLI out there.
It is complete and has an even learning curve, making it great for basic and intermediate users

---

### Post by JohnRLaw on 2010-01-01
Thank you for your help. I think it will go now.

---

