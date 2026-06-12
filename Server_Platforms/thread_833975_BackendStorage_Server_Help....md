---
title: "Backend/Storage Server Help..."
date: 2008-06-19
forum: Server Platforms
---

### Post by stoynev on 2008-06-19
Hellow folks, I am researching for an backend server solution and I need help..

What I want is to Have 1 server with only applications installed on it.., and another server (backend/storage) with all the data and DB.

Can any 1 suggest me architecture and from where to start, what do I need like software and how to setup both servers...


Thank you.

---

### Post by hyper_ch on 2008-06-19
Hmmm, sounds to me like you'll need a thin client setup. Local workstations that connect to the server for applications and stuff... and then you can just mount the data(base) server into the local thinclients

---

### Post by stoynev on 2008-06-19
No, the thing I am researching for is kindda different...

lets say that I have 1 server with linux installed and lots of user accounts (20-25 accounts that use X , not always 20-25 at same time.. normally 10 accounts at same time ), E-mail server...etc. 

And one separate server for the data from the user accounts, and storage of the E-mail data..., 

Actually all the necessary applications will be installed on the 1st server...and the second will be storage/backend with all the application files..

So if something happens to the application server, the data will be safe in the storage server.

---

### Post by doogy2004 on 2008-06-19
I use Ubuntu 8.04 LTS Server with LAMP, Samba, and OpenSSH for remote CLI

The file server is Samba
The database is MySQL

just create shares in samba and access samba from your application server

---

### Post by wirelessmonkey on 2008-06-19
Sounds like an NFS server...

---

### Post by doogy2004 on 2008-06-20
> **wirelessmonkey said:**
> Sounds like an NFS server...

same idea different protocol, samba works with windows

---

### Post by stoynev on 2008-06-20
1st.. Whats the difference between NFS (Network File System) and RFS (Remote File System) (I have read alots wiki but I cant figure it out?)

OK, thats my plan..

[Machine 1] The Storage Server It will have 4-5 HDD - 500GB Each .., and I will install NFS Server... 

[Machine 2] The App Server.., I will install Linux With X (Gnome) and The Users /home/ dir will be mounted from [Machine 1] (NFS Client) so when I add new user, his home directory will be in the storage server...

The E-mails will be mounted too, so they will store at the Storage Server [Machine 1] ...

**Is that Correct Arch. ?** :rolleyes::?:

---

### Post by gtdaqua on 2008-06-20
> **stoynev said:**
> 1st.. Whats the difference between NFS (Network File System) and RFS (Remote File System) (I have read alots wiki but I cant figure it out?)

OK, thats my plan..

[Machine 1] The Storage Server It will have 4-5 HDD - 500GB Each .., and I will install NFS Server... 

[Machine 2] The App Server.., I will install Linux With X (Gnome) and The Users /home/ dir will be mounted from [Machine 1] (NFS Client) so when I add new user, his home directory will be in the storage server...

The E-mails will be mounted too, so they will store at the Storage Server [Machine 1] ...

**Is that Correct Arch. ?** :rolleyes::?:

But how will Machines 3, 4 access? All those machines will have an NFS partition mounted which will point to Machine 1?

EDIT: I meant: you have said you need to setup only 2 servers.. but how will users access it? (assuming someone is going to use the app server)

---

### Post by eldragon on 2008-06-20
for email you could always rely on a imap server on the backend storage server. that would leave minimal configuration on the user side.

dovecot is quite easy to setup, but maybe you are looking for something more complex.

---

### Post by rickyjones on 2008-06-20
It really sounds like the original poster is trying to create a terminal service environment with the applications hosted on one server and all the user data hosted on a different server for certain purposes (easier to back up, not relying on a single server, if one server goes down the other is still available for some functions, etc...). 

In the case of having a terminal server hosting certain applications for users and then having the data housed on another server then the OP is definitely on the right track. I'd use NFS to facilitate the remote storage requirement. I'm going to assume that users will access the terminal server via thin client or remote X sessions.

Sincerely,
Richard

---

