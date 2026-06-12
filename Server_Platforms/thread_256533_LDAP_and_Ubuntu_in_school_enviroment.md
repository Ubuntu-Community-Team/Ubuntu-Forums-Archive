---
title: "LDAP and Ubuntu in school enviroment"
date: 2006-09-13
forum: Server Platforms
---

### Post by Tobbera on 2006-09-13
Hi!

**Situation:**
I (as admin) run Ubuntu on all clients at my school. These fetch login-in info from a LDAP server (debian) that contains all students. The server also serves /home and a /global (dump-area) to the clients via NFS. *Almost everything works fine*. ;) 

**Questions / Issues:**
How do i manage groups in this enviroment? Via the LDAP-admin-tool I can't add users to groups like "sudo" "adm" and so on becouse they simply does not exists in the LDAP-directory. And if I try to manage groups in the server CLI it does not recognize my LDAP-users since the server only looks in /etc/group and not LDAP-directory. ](*,) 
*Example: I as admin (user "kalvin.clein" in LDAP) wants "adm" and "sudo" priviledges on the clients and server when I log in trough BASH and GDM.*

Another group-related issue is filespace. I want to make the students members of diffrent groups depending on witch year they are on. And then I want diffrent filespace (NFS mount) for diffrent classes/years. First-year-students has RWX to their filespace but --- to second and third years filespace.[I]Example: User student.1 should be member of groups "students" and "class1". Group "class1" should have RWX to /global/class1, all other users have ---.
[/I] 
How do i turn off the function that displays avaible updates (apt-get) in gnome to every (all students) thats logs on to the machine?


I'm sure I will come up with more issues as the term/semster goes on. The system has been up and running with pratically no problems at all for more than a month now.

---

### Post by Macchi on 2006-09-13
Sorry this is not yet a solution for you. But I am very interested on a ldap directory server that is "easy" to install and maintain. Among other things this is one of the key functions for a small business server based on Ubuntu. 

An interesting example in this area is the miru directory server: [http://developer.novell.com/wiki/index.php/%E3%81%BF%E3%82%8B_directory_server](http://developer.novell.com/wiki/index.php/%E3%81%BF%E3%82%8B_directory_server).
Miru is not an answer to our questions but it is good to look at it because as far as could understand it also has packages running on a generic ubuntu server, besides the original BSD solution.

I have done several experiments with ldap but still can't get it to work in a reliable way suitable for a production environment. It seems to be forbidden soil for uninitiated IT system generalists like me. I do hope for a good pratical solution.

---

### Post by tux73 on 2006-09-18
Is anybody able to post some news on this topic or some good hints?

Even for families it is a good idea, not only for (small) business use.

---

### Post by Tobbera on 2006-09-19
Update:

According to [this]("http://aqua.subnet.at/~max/ldap/") document, the machine running OpenLDAP-server (called server) should  be looking in the LDAP-directory for user and group information. That means that you should do the same configuration on the server as you do on the clients. I think this is gonna solv many user/group/NFS-related problems of mine.

---

### Post by andnos on 2006-10-18
how did you configure the clients to authenticate against the LDAP server? I have a similar environment....

---

### Post by Tobbera on 2006-10-20
> **andnos said:**
> how did you configure the clients to authenticate against the LDAP server? I have a similar environment....
Well, thats quite much configuration to explain in this thread.

You basicly configure PAM and NSS to contact the LDAP-server and request user/group information. There are several guides on-line, I'll point you to some:

[http://aqua.subnet.at/~max/ldap/]("http://aqua.subnet.at/~max/ldap/")
[http://www.imaginator.com/~simon/ldap/]("http://www.imaginator.com/~simon/ldap/")
[http://yolinux.com/TUTORIALS/LDAP_Authentication.html]("http://yolinux.com/TUTORIALS/LDAP_Authentication.html")
[http://enterprise.linux.com/article.pl?sid=05/09/15/1930256]("http://enterprise.linux.com/article.pl?sid=05/09/15/1930256")

---

### Post by Tobbera on 2007-01-25
I've now configured the server to search it's own LDAP database for user-information. This makes things alot simpler. I can 'su' to a ldap-user on ther server-machine. I can give ldap-users ownership and mods to NFS-shares on the server. I've also installed postfix/dovercot/squirrelmail(apache2-https) with LDAP as user backend. That works great! :D 

Now I've come to user-persmissions on NFS-folders.

I have a directory-structure like this:
```

/home/student.1
/home/student.2
[...]
/home/global
/home/global/teacherfiles
/home/global/students
/home/global/pictures

```

I want to give students and teachers diffrent access to theese folders. In /home/global/students I want all students to be able to write with default permission rw-r--r--. This is acomplished. What I also want is members of teacher-group to have permission to delete/modify all files in /home/global/students/ (and maybe whole /home) . This they don't have at the moment. Becuse all files are created with  rw-r--r-- no one alse than the creator/owner can write to this file. 

Regards
Tobias

---

