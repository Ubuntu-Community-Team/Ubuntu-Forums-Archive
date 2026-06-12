---
title: "network drives Samba"
date: 2008-03-02
forum: Server Platforms
---

### Post by aknight_sa on 2008-03-02
good day guys,

i have created a Domain controller using Samba for my office... i have been able to make people join the domain and make shares.. what i need to do is make a public folder where other employee's can get public files from. i want this shared folder to be available as a network drive under my computer (windows XP, Vista clients) rather than going to the my network places.

thanks

---

### Post by jonabyte on 2008-03-02
You will need to create the share in the smb.conf and on the computer.
Then on each computer simply map the drive for example:

```
net use f:\ \\samba\share
```

---

### Post by koenn on 2008-03-02
> **jonabyte said:**
> You will need to create the share in the smb.conf 
Then on each computer simply map the drive for example:

```
net use f:\ \\samba\share
```
and that, you should be able to automate by using a logon script.
samba supports logon scripts - look for a sample 'logon script' entry in the [global] section (or : [http://www.oreilly.com/catalog/samba/chapter/book/ch06_06.html](http://www.oreilly.com/catalog/samba/chapter/book/ch06_06.html) )

---

### Post by koenn on 2008-03-02
> **jonabyte said:**
> You will need to create the share in the smb.conf and on the computer.

just a share on the server, in smb.conf - no shares on the (client) computer(s)

---

### Post by aknight_sa on 2008-03-02
> **jonabyte said:**
> You will need to create the share in the smb.conf and on the computer.
Then on each computer simply map the drive for example:

```
net use f:\ \\samba\share
```

isnt there a way to do it automatically.. currently when someone joins the domain and logs on he gets his home directory from samba as a mapped network drive in my computer

---

### Post by koenn on 2008-03-02
yes, a logon script. look 1 or 2 posts up  :)

---

### Post by aknight_sa on 2008-03-02
> **koenn said:**
> yes, a logon script. look 1 or 2 posts up  :)

how is the home folder being mapped without a script??

---

### Post by koenn on 2008-03-02
there are several ways of doing this
on windows clients, you can map drives "persistent"-ly, so you map once, and it's rememberd over reboots
you can also asign a "home drive" through a property of the user account (on Windows - I don't kow how samba accounts do this) - this is typically done while creating a new user.

however, using a logon script is often the prefered sollution. If, for whatever reason, you need to change the drive letter or the path to the share, you only have to make changes in 1 place (the script), and changes will take effect automatically the next time the user logs on. 
Variables such as U% (or %username% in Windows) allow you to make user-specific settings from a common script/config file

The other sollutions require you make changes on every computer/forevery account

---

