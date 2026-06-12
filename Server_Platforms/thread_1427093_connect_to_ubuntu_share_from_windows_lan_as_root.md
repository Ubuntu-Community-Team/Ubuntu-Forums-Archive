---
title: "connect to ubuntu share from windows lan as root"
date: 2010-03-11
forum: Server Platforms
---

### Post by halit.yilmaz on 2010-03-11
hi all.

i have a server machine (ubuntu server installed on it) and 37 windows installed pc s and one ubuntu desktop installed laptop on the lan. i keep all the important documents on server. i can reach to shared folder with user name and password form my ubuntu desktop and i can modify them. 

there is no problem to see documents from windows clients. but if i need to change a document myself from a windows client what should i do.

for windows server and client process you can type \\server_name\admin$ and a login screen pops up. how can i do this for ubuntu server.

i do it on my ubuntu desktop like this:
```

smb://WORKGROUP;usernam@ip_or_server_name\shared_folder

```any idea?

---

### Post by johnson.d on 2010-03-11
If you want the write access only for you and read only access for others accessing the same share you can do the following:
1) Create a new user on the server by using the following command

$ sudo useradd <user-name>

2) Create a samba user linking the username you have created

$ sudo smbpasswd -a <user-name>

Where <user-name> is the same username created using useradd

3) Append the following lines to /etc/samba/smb.conf 


[<share-name>]
path = /<share>
browseable = yes
read only = yes
guest ok = yes 


[<share-name1>]
path = /<share>
browseable = no
read only = no
valid users = <user-name>


Here we are creating two share entries in smb.conf file having the same path but different share names. The    <user-name> specified here is the same which was created using useradd command.

At the Windows client side:

1) Map a network drive to the second share entry i.e. <share-name1> and uncheck the reconnect at logon option. Every time it connects it ask for the login credentials.Now you can have write access to the share and others will be having only read access to the folder.

---

### Post by halit.yilmaz on 2010-03-11
thank you. it didn't work at first. then when i changed the ownership of shared folder it worked.

thank you very much for your help

---

