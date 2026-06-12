---
title: "Ubuntu server in the classroom"
date: 2009-07-27
forum: Server Platforms
---

### Post by jgb2185 on 2009-07-27
My brother has asked me to help him set up a classroom Linux server to act as a file server for assignments that his computer science students must turn in in electronic form. The client PCs run Windows XP. Each student will need a personal folder accessible only to him or her, and (of course) my brother as teacher and admin.
 
I immediately suggested Ubuntu Server (Jaunty). I am, however, deeply ignorant on the topic of integrating Windows Active Directory with a Linux server. Given the parameters above, will it be necessary to set up integration via a utility such as likewise-open, or is there a simpler (perhaps web-based) solution?
 
Thanks...
 
JGB

---

### Post by irv on 2009-07-27
For a file server it is just the software. If your brother is not to comfortable at the command line, you may want to just setup a desktop version and not the server. The only thing that make it a file server is samba. Here is a like to setting up samba.
[http://www.kindawannadothat.com/2009/04/how-to-setup-a-simple-file-server-in-debian-ubuntu/]("http://www.kindawannadothat.com/2009/04/how-to-setup-a-simple-file-server-in-debian-ubuntu/")

---

### Post by jgb2185 on 2009-07-29
Thanks, Irv. I understand that Samba will be necessary for file sharing. My concern is with folder permissioning.

Assume that I set up Ubuntu Server or Desktop on the server machine and get Samba configured. How, then, do I control access to the individual students' home folders, as they access them from their Windows XP client machines? I understand *nix permissioning, but not the relationship between perms and clients on a foreign OS. 

If I install nothing beyond Samba, what is the student's experience when opening their folder on the server? Do they get prompted for an Ubuntu username and password? Is there a way to avoid that with Ubuntu+Samba alone?

JGB

---

### Post by irv on 2009-07-29
Maybe I will get corrected if I am wrong, but if you setup all the students on the computer being used as a server, it will setup a user directory under users for each one. When you then setup a user for each under samba I would think they could then see and have access to that directory. I don't think any one else could see it. You then could setup a group called teacher and give that group rights to all those directory.
If I am wrong, someone please correct me. Or if there is another way to do this please post.

---

### Post by jgb2185 on 2009-07-29
So, under the setup you suggest, Irv, a student would be prompted for an Ubuntu username and password upon trying to access the server folder. Is that correct?

Thanks...

JGB

---

### Post by irv on 2009-07-29
> **jgb2185 said:**
> So, under the setup you suggest, Irv, a student would be prompted for an Ubuntu username and password upon trying to access the server folder. Is that correct?

Thanks...

JGB
Yes, I have my samba setup that way, and when I use the network on my XP machine it ask for my password. I have the same password to logon to Ubuntu as I do Samba.

---

### Post by jgb2185 on 2009-07-29
Thanks for the clarification. That may be acceptable for classroom use; I'll have to check with my brother.

JGB

---

### Post by ugm6hr on 2009-07-29
Why not set up a web server and install an E-learning environment such as Moodle.

It allows much more than just file serving, is perfect for school use, and is in the Ubuntu repo.

Your brother will also be able to do the "admin" stuff himself. i.e. adding new assignments, new users etc.

Simply installing Ubuntu Server and moodle should do the trick...

[http://docs.moodle.org/en/Step-by-step_Install_Guide_for_Ubuntu](http://docs.moodle.org/en/Step-by-step_Install_Guide_for_Ubuntu)
[http://docs.moodle.org/en/Installing_Moodle](http://docs.moodle.org/en/Installing_Moodle)

---

### Post by omichaels on 2009-07-29
In some ways the Sakai CLE (Collaboration and Learning Environment) is an even better option than Moodle as it provides each users (teachers and learners) with a personal learning workspace that includes a resource repository for files and links that can easily be shared and submitted for assessment against predefined tasks. It also includes the Open Source Portfolio (OSP) ePortfolio that enables users to create a variety of protfoios to showcase their learning.

The Sakai and OSP learning curve is a little steeper than Moodle, but this is due to the fact that there is a lot more scope in use.

Edit, both Moodle and Sakai have authentication modules that can integrate with the MS AD. This will eliminate need for Linux account mgt and is a compelling reason for using one of these web apps to meet the requirement.

My $0.02

---

### Post by ugm6hr on 2009-07-30
> **omichaels said:**
> My $0.02

Currently values higher than my $0.02 ;)

I only have personal experience as an admin of Dokeos, which is more corporate-orientated.  It sounds like you have used a number of alternatives; I merely suggested moodle since it is well-adopted in secondary and higher education around the world.  I have only heard of Sakai in passing, but it certainly sounds an excellent option in this case (where file storage for students and teachers is the predominant feature required).

Nevertheless, I agree that almost any e-learning environment is likely a better solution than any other option.

---

