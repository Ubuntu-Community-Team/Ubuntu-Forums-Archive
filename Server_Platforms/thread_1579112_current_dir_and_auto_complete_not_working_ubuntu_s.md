---
title: "current dir and auto complete not working ubuntu server 10"
date: 2010-09-21
forum: Server Platforms
---

### Post by Executionher on 2010-09-21
#if I login as root I get the following:

Last login: Tue Sep 21 17:32:06 2010 from 192.168.1.138
root@myserver:~# 

#The account works great!! When I want to auto complete a command I can just press tab #this works for directories aswell :-)

#Now where the problem start is here:
#I add a user with the following command:

useradd -d /home/myuser -m myuser

#Setpassword:

passwd myuser

#and then add the user to the admin group:

adduser myuser admin

#After all this is done I login with the user and all I get is this:

Last login: Tue Sep 21 17:33:01 2010 from 192.168.1.138
$ 

#(No myuser@myserver:~# or anything like that just a dam $ sign)
#I cant even use the tab comand 2 change dir's or complete comands

I was told that this should work:

Uncommenting the following lines, by removing the # in the beginning of the lines in /etc/bash.bashrc file:

#if [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#fi

This does not work @ all. Is there a way to have it exactly the same as for the root user?

---

### Post by the_original_billq on 2010-09-21
It is likely your default shell for adding users is Bourne shell, not bash.

Look at /etc/defaults/useradd, and change:

 SHELL=/bin/sh

to

 SHELL=/bin/bash

So that future user adds will default to bash.

For your current user, you should change their login shell to bash.

 chsh -s /bin/bash user_name

HTH,
Bill

---

### Post by Executionher on 2010-09-21
Thanks a million Bill !!! It solved my problem :guitar:

---

