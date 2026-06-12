---
title: "folder permissons"
date: 2006-08-15
forum: Server Platforms
---

### Post by Rollo Tamasi on 2006-08-15
Hi guys, i have ssh'd into my server and i want to have access to view/edit my conf folder and it's entire contents via ftp. The end result i want to acheive is to be able to download files from the said folders and edit them and then upload them once more all via ftp.

I attempted to run "chmod 777 etc/httpd/conf" while logged in as root but i get an error stating that the operation is not permitted.

What command should i be running?

I want to give myself permisson to view and edit the conf folder

---

### Post by jordilin on 2006-08-15
> **Rollo Tamasi said:**
> Hi guys, i have ssh'd into my server and i want to have access to view/edit my conf folder and it's entire contents via ftp. The end result i want to acheive is to be able to download files from the said folders and edit them and then upload them once more all via ftp.

I attempted to run "chmod 777 etc/httpd/conf" while logged in as root but i get an error stating that the operation is not permitted.

What command should i be running?

I want to give myself permisson to view and edit the conf folder

It should be chmod 777 **/etc**/httpd/conf. If you are root you should be able to change the permissions of everyone.

---

### Post by Rollo Tamasi on 2006-08-15
hi, i ran the command as you advised and i get this msg:

-bash-3.00$ -bash-3.00$ chmod 777 /etc/httpd/conf
-bash: -bash-3.00$: command not found
-bash-3.00$ chmod: changing permissions of `/etc/httpd/conf': Operation not permitted
> -bash-3.00$

---

### Post by lamego on 2006-08-15
Rollo,
you are not expected to past the "bash" prompt !

Second, do not change the permission to 777, the file default permission is ok, your problem seems to be lack of kownledge. 
Please read a guide: [https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by LordHunter317 on 2006-08-15
I'm not sure what you want to do, but I am sure this isn't the way to accomplish it.

Please explain with more details.  If you have to be touching your configuration this often, something is wrong.

---

### Post by chonger on 2006-08-16
> **jordilin said:**
> It should be chmod 777 **/etc**/httpd/conf. If you are root you should be able to change the permissions of everyone.

> **Rollo Tamasi said:**
> hi, i ran the command as you advised and i get this msg:

-bash-3.00$ -bash-3.00$ chmod 777 /etc/httpd/conf
-bash: -bash-3.00$: command not found
-bash-3.00$ chmod: changing permissions of `/etc/httpd/conf': Operation not permitted
> -bash-3.00$

Rollo,

   It seems that at the prompt, you typed in "-bash-3.00$ chmod 777 /etc/httpd/conf". Why do you think the -bash-3.00 is necessary? What does that command do? Is it a valid command?

   Then you attempted run the chmod command again. It seems that you were not careful to make sure you are the 'root' user this time. By default, your command prompt would end with a '#' if you are root. In this case it looks like you are not the root user when you ran the command.

---

