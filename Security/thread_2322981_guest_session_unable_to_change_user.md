---
title: "guest session unable to change user"
date: 2016-05-02
forum: Security
---

### Post by mperezr on 2016-05-02
When I login as guest I am unable to changue to other user or execute  any command with sudo (ubuntu  15 , 16, lubuntu... , on ubuntu 12.04  its works ) :[INDENT]   [I]
su USER
      setgid operation not permitted

[/I]
 [/INDENT]
I need the guest user can do it . Any solution? 
  I've tried modifying the script ( /usr/sbin/guest-account )  adding the user to the root group and does not work
  Regards

---

### Post by sudodus on 2016-05-02
Welcome to the Ubuntu Forums :-)

The guest user is designed to work like that. The intention is that the guest should not be able to damage the system, and not be able to read private documents, that belong to other users.

If you want a user with 'more permissions', you must ***create a new user and give it the permissions you want to give it***.

---

### Post by mperezr on 2016-05-02
Thanks :D, but I need the session data to be deleted ...

I thought about creating a user your home this located in / tmp but perhaps the beginning of the session is slow

---

### Post by sudodus on 2016-05-02
Please remember that a user with permissions to run sudo can do 'anything', including to write outside its home directory, and damage your system in many ways by mistake or by intention ;-)

You can wipe all files in this special user's home directory at logout or the next login. I'm sure it would be possible. I don't know where to tweak the system to do it at logout. I'm sure there are people who know, and I hope you can get help with it :-)

At the next login, it should work to create a desktop file for it, and put that file in **autostart**.

---

### Post by mperezr on 2016-05-02
Thanks , and can the guest user run as program as root if I configure that?

---

### Post by sudodus on 2016-05-02
'Everything is possible', but I think it is more difficult the modify the guest user than to make a new regular user, give it superuser privileges and remove created files at logout or login.

---

### Post by ubu_dynamite on 2016-05-02
> **mperezr said:**
> Thanks , and can the guest user run as program as root if I configure that?

You could set "setuid" on a file normal users on the system who have permission to execute this file gain the privileges of the user who owns the file.

[COLOR="#FF0000"][SIZE=4]Be careful with that command though users could really mess your system if you set it to the wrong file.[/SIZE][/COLOR]

---

### Post by bashiergui on 2016-05-02
> **mperezr said:**
> Thanks :D, but I need the session data to be deleted ...If you want to delete everything after a session and have root then look at Tails
[https://tails.boum.org](https://tails.boum.org)

Or run as a sudo user in a virtual machine. Revert to a snapshot after every session.

---

