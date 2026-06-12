---
title: "Samba users without home directory"
date: 2015-12-04
forum: Server Platforms
---

### Post by gardenair on 2015-12-04
I want to configure samba server. There are 10 users who are using windows 7 and windows 8. When ever I create a users Linux automatically create its home directory. For samba server if there are 100 users then there should be 100 home directories ? These home directories are used in samba server ? I am sure not. So is there any way  that I should create a users account  without home directory ?
What is your opinion about it ? Is it compulsory that should be a home directory for every samba users ?

---

### Post by darkod on 2015-12-04
According to this it's easy to do it: [http://askubuntu.com/questions/536977/create-a-user-for-samba-only-cli](http://askubuntu.com/questions/536977/create-a-user-for-samba-only-cli)

Note that the options used in adduser will not allow any linux access for that user (disabled-password, disabled-login) because that's what the question was about. But you need the same, you don't care about linux logins, you want samba to be used by windows users.

Steps 1 and 2 should be all you need.

---

### Post by gardenair on 2015-12-05
thanks for the reply. Well how can we do in command line ? I does not want to use guest account. I want users without home dir and that users will access the samba share?  Which switch should i use to create such users ?

---

### Post by darkod on 2015-12-05
I don't understand. Those are commands for the command line. Of course, you will use your admin account on the linux box to log in, and then you can create all share users that you want using those adduser command, and then tell samba to accept them with the smbpasswd.

---

### Post by gardenair on 2015-12-05
well i does not found the exact answer.
[COLOR=#111111][FONT=Ubuntu]
I want that i should create a user account without home directory and then assign smbpasswd of that users to login .I found in post which you mentioned .....
[/FONT][/COLOR]```
[COLOR=#111111][FONT=Ubuntu]
sudo adduser --no-create-home --disabled-password --disabled-login sambausername[/FONT][/COLOR]
```

I found in ubuntu forum

[http://askubuntu.com/questions/29359/how-to-add-user-without-home](http://askubuntu.com/questions/29359/how-to-add-user-without-home)


```
[COLOR=#111111][FONT=Ubuntu]To add user without home directory the commands are,[/FONT][/COLOR]
useradd -M username
[COLOR=#111111][FONT=Ubuntu]or[/FONT][/COLOR]
useradd --no-create-home username
[COLOR=#111111][FONT=Ubuntu]or[/FONT][/COLOR]
adduser -M username
[COLOR=#111111][FONT=Ubuntu]or[/FONT][/COLOR]
adduser --no-create-home username
```

is it is same thing which I want ? i.e " To add a user without /home dir "

The last thing to add smbpasswd and share resources. :)

---

### Post by darkod on 2015-12-06
Yes, it's the same thing if you want no home folder. It should also be the same whether you use useradd or adduser, the basic command is useradd and ubuntu team has added adduser which has little differences but it calls up on useradd too.

The --disabled-password and --disabled-login are your choice whether to use them or not. If you do, that user will not have ubuntu password and ubuntu login, only samba. If you need it only for opening samba shares from windows, he doesn't need ubuntu login anyway. So, it's your choice which of the options you want to use...

---

