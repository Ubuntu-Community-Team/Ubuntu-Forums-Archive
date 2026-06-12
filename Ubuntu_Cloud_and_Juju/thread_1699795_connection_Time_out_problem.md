---
title: "connection Time out problem"
date: 2011-03-04
forum: Ubuntu Cloud and Juju
---

### Post by cloud25 on 2011-03-04
i am doing the private cloud in my laptop by following the UEC beginner guide procedure .in the step of running an instance i got problem as connection time out after creating the ssh key ..which as follow..


server@node:~$ cd  ~/.euca
[email]server@node:~/.euca[/email]$ source eucarc
[email]server@node:~/.euca[/email]$ cd -
/home/server
server@node:~$ euca-add-keypair mykey > mykey.priv
server@node:~$ chmod 600 mykey.priv
server@node:~$ euca-describe-keypairs
[Errno 110] Connection timed out


how to overcome this error???/

---

### Post by Rusty au Lait on 2011-03-04
2 questions.

Do other euca-xxx commands time-out as well?

Is there a second file named mykey.priv in the ~/.euca subdirectory?

If the install went without error, I suspect the problem is  sourcing eucarc

---

### Post by cloud25 on 2011-03-04
but there is no sub directory in that location of ~/.euca..is it possible to run an instance through web browser.

---

### Post by raymdt on 2011-03-05
> But there is no sub directory in that location of ~/.euca

You didn't make Step 5 and Step 7  of this tutorial

[https://help.ubuntu.com/community/UEC/PackageInstall](https://help.ubuntu.com/community/UEC/PackageInstall)

---

### Post by Rusty au Lait on 2011-03-07
~/.euca is a hidden sub-directory.

If, from your home directory, the command
ls -A
does not show the sub-directory named '.euca', your problem does concern your install.

---

### Post by raymdt on 2011-03-08
I suppose that somebody who want to install uec should know that .euca is a hidden directory.:D

---

