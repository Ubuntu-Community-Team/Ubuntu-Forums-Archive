---
title: "Setting up a 'public' ssh server"
date: 2008-07-14
forum: Server Platforms
---

### Post by Jawshie on 2008-07-14
I'm setting up a server with some requirements that I need help defining and getting more information on. Hopefully the fine people on the forums can offer me some help. I am building a server for somebody who wants to allow students on our campus to program in a Unix-based command line environment. To access it, I need to set up SSH (I can do that!!!) that they will access from their Windows clients via putty or something. 

I need my Ubuntu server to be able to join the Windows Server 2003 domain or at least just validate against it. There will not be any remote printing or accessing shares or anything like that so I do not need access to resources (though if we could, that wouldn't hurt). They mainly just need to be able to use the same passwords that they use to log in with the Windows Clients into the network. Also, we have 2 domains: one for students and one for faculty. I may need to validate against both if possible. 

Since they will be using this for class, I also need their folders to be hidden from each other but admins and professors will need to access it. I understand permissions fairly well but what will be difficult is doing it for each and every student individually. Is there a way to set a default profile based on domain or can I set up a script to add student accounts? Will student accounts be added automatically if they log in and they have accounts on the domain or will they all need to be created automatically? 

I'll probably think of something else later. Thanks for all the help in advance!

---

### Post by silverglade00 on 2008-07-14
> **Jawshie said:**
> They mainly just need to be able to use the same passwords that they use to log in with the Windows Clients into the network. Also, we have 2 domains: one for students and one for faculty. I may need to validate against both if possible. 


I have exactly this same setup that I have been working with. The software that you are looking for is Likewise. I believe it is in the repos as open-likewise or likewise-open. There is a GUI for it that makes it literally a 4-step process: 
1. Enter domain name to join. (ex. students.university.edu)
2. Enter username on domain with admin rights. (ex. adminuser)
3. Enter that user's password.
4. Click the Join The Domain button.

As for the two domains, it worked with no extra setup for me, but our domains are set for the student domain to trust the faculty one. Their home folders will be created on first login using the files in /etc/skel. You can modify that directory as needed. The home folder will be inside a folder in home (home/local/DOMAINNAME/user1). I am still working on how to add domain users to local groups, so maybe we can work on this together.

---

### Post by Jawshie on 2008-07-18
This works pretty well but like you said... there arent any local groups. I can not keep people out of each other's home folders with this method. 

I remember seeing a similar setup when somebody used a script to manually add usernames but the password would be grabbed from the domain when the user logged on. 

What are my other options for AD authentication?

---

