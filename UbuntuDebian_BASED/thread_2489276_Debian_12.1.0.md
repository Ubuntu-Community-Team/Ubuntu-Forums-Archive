---
title: "Debian 12.1.0"
date: 2023-07-24
forum: Ubuntu/Debian BASED
---

### Post by rm70 on 2023-07-24
I installed Debian on my laptop and needed upper level access in terminal to solve wireless network issue to my dismay i can not access root or sudo privilege. I am able to log into computer with my user name and password ok.   I have tried ever command others on sites have suggested to resolve this to no avail. I get [user name]: sorry try again. I have tried apt-get update, apt-get upgrade nothing i have tried works. sure could use help guys. Thanks

---

### Post by ajgreeny on 2023-07-25
When you installed the OS did you choose to have a separate root password or to use the same password as the first user and use sudo in the same way as we do with Ubuntu?

I have had several Debian installations and have always chosen the sudo method, ignoring any need for a root password which makes life a lot simpler.

---

### Post by rm70 on 2023-07-25
i used the same name. I am the only user so I saw no reason to deviate. thanks for responding,

---

### Post by ajgreeny on 2023-07-25
> **rm70 said:**
> i used the same name. I am the only user so I saw no reason to deviate. thanks for responding,

So do you mean that you use the one user's password (ie, you) for carrying out administrative actions such as installing and removing application packages?

Let's see the output from your Debian VM of terminal command **groups** which may give us a clue.

---

### Post by SeijiSensei on 2023-07-26
Debian has a separate root password. I set mine to be the same as my own login password, but you have to set the root password explicitly during installation. I used to use RedHat which also has a root password; after moving to Ubuntu it took a while to get used to sudo. On Debian, you'll need to the use **su** command and enter root's password.

If you haven't set a root password, you can fix that by booting into a shell in rescue mode. Google will tell you where to go from there.

---

### Post by Dennis N on 2023-07-26
You don't need the root password in Debian 12. Just leave it blank and click continue. The instructions at the top of that page tell you that if you skip setting the root password, you are automatically set as the administrator with sudo rights. Just like Ubuntu.

---

### Post by ajgreeny on 2023-07-26
> **Dennis N said:**
> You don't need the root password in Debian 12. Just leave it blank and click continue. The instructions at the top of that page tell you that if you skip setting the root password, you are automatically set as the administrator with sudo rights. Just like Ubuntu.
Yes.
And thats exactly how I use my installation of Debian 12 even though it started as Debian 10 a few years ago.
Being just like Ubuntu and using sudo makes life a lot easier all round for me.

---

