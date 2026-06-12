---
title: "Server Project for School Using Breezy"
date: 2006-01-14
forum: Server Platforms
---

### Post by GMathews on 2006-01-14
Hi there

I met my principal of my previous secondary school last week by chance and I found
Out that he was interested in obtaining about 8 computers for his school
which had to come out of the school's own budget. The school is in fact 
a public school and funds dont come easy for projects like this. Anyways
he asked me for my opinion regarding networking all these computers with a 
common office printer/copier. I then thought about it and since Ive just been recently
aquainted to the Ubuntu/Linux world I thought that maybe setting up a server
which can handle a few of his requirements which could be based on the ubuntu 
system and other open source programs. Ive drawn up a few of the requirements 
and they are as follows :

1. 6 Windows XP computers on a LAN connected to a server with Ubuntu on it. 
   How exactly do I go about doing this? I know how to basically connect 
   a few computers on a LAN for playing games but will it be the same method ie.
   using a 8 point HUB to connect all of them?

2. Now remember that it is a school so I was thinking of maybe create individual
   accounts for each student of lets say 5-10MB of space each.Im not really
   sure about the total number of students who will have an account on this server
   but Im guessing in the region of around 100.It might expand in later years. 


    Now when the student logs on on the Windows Computers via a Client a drive must get mounted on
   the Windows machine that he/she is working on. I am basing this idea on the Novell
    Client my university uses.
   
   Is there a similiar open source server for ubuntu and a client which can be used on a Windows 
   machine? Using the same software (or alternate) can I create a login screen/message
   to state for example (welcome to XXX School, Property belongs to XXX School, Rules
   of using these computers, etc)

3. The server will be connected to an Office printer. Now on the 6 machines is there an
   open source printing software (or is any needed) so that it is password protected? I am
   asking for this so that only teachers with the password can use the printing facilities.
   
   Or maybe using the same method as mentioned in point 2, create account for teachers as 
   well and then allow for printing rights for these accounts together with a printing count(ticker)
   for each account. I am running Breezy on my personal machine and I have problems with my Canon 
   i350 (it detects it fine but  I need to download drivers from turboprint it seems which further 
   costs money. Are there printers (officejet) that don't need any more drivers to print on the Ubuntu system? 

4. Any other open source software that you can recommend for this venture?

5. Also I want to know if there is an open source program similiar to Novell which can run
   in Windows which can perform the functions listed above...just for interests sake then I can
   compare the windows vs ubuntu servers although Id prefer the server running in Linux due to stability.

6. This is a question for more experienced Windows users. I want to create 2 windows accounts on each of the
   6 machines. One called 'Administrator' and the second called 'Student/Teacher'. The latter should not have
   write privilages on  C:\ but only for the mounted drive, for example F:\ (5-10Mb as mentioned in point 1)


I am very keen on setting this network up which I intend to base the server on the Ubuntu system
as Im sure Novell and other software must be pretty expensive. The school intends to get
the computers by the end of this year so I have some time to research it well. Please post 
your suggestions / links to guides or any other important information that could help 
me in this project. 

I am still a newbie to the whole linux setup. I have Breezy On my system with dual boot with XP so 
I can test any of your recommendations on my pc before attempting it on this network. Please
try and explain it in easy terms and fully if you can. Im sure that if you are able to help me you 
will be helping others with regard to the demands for a server/client network of a similiar nature.

Thanks a lot :)

GMathews

---

### Post by Novastorm on 2006-01-15
Noble as your intentions are i would suggest you implement a system that you can support. You mention that you are quite new to the world of linux, as am I, so at home i have a linux server to learn with, but my clients all have windows based setups, as i know that if they call me with a problem i can fix it without too much trouble, and won't need to rely on people posting a multitude of possible fixes on a forum. As for your questions about what you need, maybe you should look at [http://www.clarkconnect.org]("http://www.clarkconnect.org"). Good luck ;)

---

### Post by bluefrog on 2006-01-16
a samba-ldap server will centralize authentication for both windows and linux pcs. Home folders could be stored on the server.

for more information use samba.org mneu "by example" read all chapters will put you on track. More information oon how setting up a samba-ldap server at idealx.org

setting up a ltsp server would allow you to use thin clients (less money, less maintening...).  ltsp.org

james

---

