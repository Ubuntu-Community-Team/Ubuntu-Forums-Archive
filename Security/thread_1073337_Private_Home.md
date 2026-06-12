---
title: "Private Home"
date: 2009-02-18
forum: Security
---

### Post by ientzy on 2009-02-18
Hello,
I have a windows NT as PDC and workstations with ubuntu 8.04.2 joined to that domain. All Home directory from all users domain ar not Private, every user can access every home from other user. How can i make the Home private for everyone who have home already make, and for everyone who will login to that workstation. I tray to change the settings from smb.conf change from 0755 to 0700 the home directory but don`t work. I must to change to another place to work?

---

### Post by bodhi.zazen on 2009-02-18
I need more information, what do you mean by "private home" and what does that have have to do with smb.conf ??

First "Private home" :

"home" usually refers to a user's home directory (ie /home/user_name ) and is made "private" with :

```
sudo chmod 770 /home/user_name
```

Next issue is samba. Are you running the ubuntu machine as a server or client ? What are you sharing over samba ?

There is a huge difference between installing and configuring Ubuntu as a a samba server and using Ubuntu as a client to  connect to a Windows Network.

---

### Post by ientzy on 2009-02-18
> **bodhi.zazen said:**
> I need more information, what do you mean by "private home" and what does that have have to do with smb.conf ??

First "Private home" :

"home" usually refers to a user's home directory (ie /home/user_name ) and is made "private" with :

```
sudo chmod 770 /home/user_name
```

Next issue is samba. Are you running the ubuntu machine as a server or client ? What are you sharing over samba ?

There is a huge difference between installing and configuring Ubuntu as a a samba server and using Ubuntu as a client to  connect to a Windows Network.

Hello, i have ubuntu like client on windows NT domain. And i don`t want to make manualy with chmod 770 for all users. I don`t have 1 user/ station, and all users can to login everywhere. this is the problem. Thanks for help, but this isn`t what i want.

---

### Post by hyper_ch on 2009-02-18
I have no clue what you mean either. Care to explain?

---

### Post by bodhi.zazen on 2009-02-18
It is hard to help you if you can not describe what you do want.

---

### Post by ientzy on 2009-02-19
> **bodhi.zazen said:**
> It is hard to help you if you can not describe what you do want.

I have a network with Windows Domain NT 4.0 as primary domain, at this domain ar connected workstations with ubuntu 8.04.2. People user the workstations with users from windows domain. All users have same group and automatic, by default all users from the same group have access to read home directory from another user.  I want to change the rights and make private home for every user who use the workstation.

---

### Post by The Cog on 2009-02-19
No, still don't understand. 

Where are the home directories that are the problem? Are they on the individual Ubuntu workstations, on a common Ubuntu server, on individual Windows workstations or on a common Windows server.

The users who can see into other peoples directories - are they users on Windows workstations or on Ubuntu workstations?

---

### Post by ientzy on 2009-02-20
> **The Cog said:**
> No, still don't understand. 

Where are the home directories that are the problem? Are they on the individual Ubuntu workstations, on a common Ubuntu server, on individual Windows workstations or on a common Windows server.

The users who can see into other peoples directories - are they users on Windows workstations or on Ubuntu workstations?

The home directory are in the Ubuntu Workstation, and isn`t individual user with his workstation. I have many users how use the same Ubuntu Workstation, and this is the problem, if one of them already login to the Ubuntu Workstation and someone else come and login at the same Ubuntu  Workstation, the second user, can see and read all the documents, from the home directory of the first user. How can I stop this, but not manually with chmod command, isn`t any way to make this automatic? All users are make in Windows Domain NT, and user to Ubuntu Workstations. 



<SERVER WINDOWS DOMAIN NT> ----> <UBUNTU WORKSTATION(with user from domain)>

---

### Post by bodhi.zazen on 2009-02-20
so you are asking how to make the home directories on the Ubuntu machine private.

I do not see how that has to do with anything outside of the Ubuntu machine and your references to a windows domain are confusing your question.

this is not a question of permissions on network shares, it is a question of permissions on the local ubuntu machine.

The solution, as I said, is to change the ownership of home. It is a one liner :

```
sudo chmod 770 /home/*
```

---

### Post by lensman3 on 2009-02-20
You might go google for "User Private Groups Scheme".  The command is "chmod g+s /dir" or "chmod 2770 /dir".  This method is usually used to get a group of users to only create files that belong to the common group.  The common group is set in the /etc/group file.  This bit is called the SGID bit but it requires the umask to be properly set.

Instead of chmod 770, I would use 700 on the dot file and make sure everybody belongs to a separate group.  Then change everybody's directory tree by: "chmod -R 700 * and also change the hidden files and directories too.  Otherwise people will be able to see files with the incorrect permissions.

You are not assigning user ID's with numbers less that 500 are you?  I think the numbers less than 500 are reserved for privileged accounts.

With Samba in the mix--->Good luck!

---

