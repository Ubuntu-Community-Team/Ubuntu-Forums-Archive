---
title: "Network drive and access rights"
date: 2010-12-16
forum: Security
---

### Post by tranduyhung on 2010-12-16
Hi, I want to set up a network drive on our server to share data, but with access rights.
For example:

[LIST]
[*]Everyone can access "Public" folder
[*]"Teachers" folder is only for teachers
[*]"Students" folder is only for students
[*]"Principal" folder is only for head master of the school, he is the only one can access this folder
[/LIST]

Is there any way I could do this on Ubuntu?

Thank you so much!

---

### Post by Morbius1 on 2010-12-16
Yes you can. Let's take the first two requirements:

[1] Everyone can access "Public" folder:

Create a share definition in smb.conf that looks like this:
```
[Public]
path = /path-to-public-folder
read only = no
guest ok = yes
```Then you need to alter the permissions on the target directory:
```
sudo chmod 0777 /path-to-public-folder
```[2] Teachers" folder is only for teachers

[a] You're going to have to create local server users for every remote teacher user and give them a samba password:
```
sudo useradd -s /bin/true teacher1
sudo smbpasswd -a teacher1
```[b] Create a share definition in smb.conf that looks like this:
```
[Teachers]
path = /path-to-teachers-folder
read only = no
valid users = @teachers
force group = teachers
create mode = 664
directory mode = 775
```[c] Then you need to create a "teachers" group:
```
sudo groupadd teachers
```[d] Then you need to add the remote teacher users to the teachers group:
```
sudo gpasswd -a teacher1 teachers
```[e] Then you need to modify the ownership and permissions of the shared folder:
```
sudo chown :teachers /path-to-teachers-folder
sudo chmod 0775 /path-to-teachers-folder
```Alas, you're not done yet:

[1] You're going to have to logout and login again for all the group stuff to take affect

[2] You're going to have to restart samba
```
sudo service smbd restart
```OR you can just reboot.

---

### Post by tranduyhung on 2010-12-16
Thank you very much, Morbius1! You helped me alot.
:)

---

