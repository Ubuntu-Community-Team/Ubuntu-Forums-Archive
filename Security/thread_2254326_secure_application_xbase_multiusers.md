---
title: "secure application xbase multiusers"
date: 2014-11-26
forum: Security
---

### Post by johand2 on 2014-11-26
Hi,

I have a question about security, rather a noob here.

I have successfuly, ubuntu server, created a chroot jail, and copied over the needed files and that works.
Now, I want to write xbase harbour applications so multiple users can use them with shared databases.
How do I best secure this ? access is by ssh bash logins with an ssh terminal client.
All users need to access the files for execution, and be able to write/read from the dbf database files.
I can set read only for the applications, but it will of course not work for the databases.
What is the best way to secure this ? using ACL ? or are there simpler solutions I dont know of ?
ACL enabled looks promising, I can as the docs say secure it against deletion and renaming.

Best would be that the databases only be accessable by the applications, and no user can see them.

Please advise.

Johan

---

### Post by redmk2 on 2014-11-26
> **johand2 said:**
> Hi,

I have a question about security, rather a noob here.

I have successfuly, ubuntu server, created a chroot jail, and copied over the needed files and that works.
Now, I want to write xbase harbour applications so multiple users can use them with shared databases.
How do I best secure this ? access is by ssh bash logins with an ssh terminal client.
All users need to access the files for execution, and be able to write/read from the dbf database files.
I can set read only for the applications, but it will of course not work for the databases.
What is the best way to secure this ? using ACL ? or are there simpler solutions I dont know of ?
ACL enabled looks promising, I can as the docs say secure it against deletion and renaming.

Best would be that the databases only be accessable by the applications, and no user can see them.

Please advise.

Johan
You can use file system (ext4 or ...) ownership and permissions to restrict the users use.  You can set up a common group and assign inherited group permissions on a section of the file system tree.  You can also use Linux ACL's to fine tune any outliers.  This is Linux not Windows so there is no GPO's at all.  But then again GPO's aren't really needed for what you want to do IMO.

Do you want specific instructions for this type of setup?

I never tell someone to (or not to) do anything.  But I have to ask;  Why are you using dBase/Clipper in a Linux environment?  Do you have legacy code/data that you are dealing with?

---

### Post by johand2 on 2014-11-27
Hi, I like to see some more specific instructions if you can.

On the dBase environment, no I have no legacy code to run, but historically feel confortable with it, and I need the easy database acces from within the language.
I dont like C like stuff, python, php and such. Or do you have a beter suggestion for a multiuser programmable environment ? (not webbased!)

---

### Post by redmk2 on 2014-11-27
> **johand2 said:**
> Hi, I like to see some more specific instructions if you can.
It is the eve of a national holiday here in the USA so I will not be able to properly respond for at least a day.  I will provide examples and specific terminal commands then.  

What we will be doing has nothing to do with a chroot environment.  Linux (as with UNIX) has always been a multi user, multi tasking environment.  The Linux host can accept multiple users running multiple tasks concurrently and securely.  Why do you feel you need a chroot environment for security?   What are you trying to separate?  Are these end users or developers that you need to provide security for?  Do you need data protection or version control?> 

On the dBase environment, no I have no legacy code to run, but historically feel confortable with it, and I need the easy database acces from within the language.
I dont like C like stuff, python, php and such. Or do you have a beter suggestion for a multiuser programmable environment ? (not webbased!)

It depends upon what database backend you are going to use.  If it is SQL compliant (i.e. mySQL or MariaDB or ...) there are dozens of languages that have SQL libraries.  If you are going to use xbase databases then Harbour is fine.  I'm not recommending one language over another.  It really depends on what your requirements are.  What are you using to create the GUI front end?  If you are using QT or GTK there are plenty of options that understand both QT or GTK  and SQL.

In the end it's your choice of which language you use.  It is an unusual one that relies on a small group of core developers.  The first question most likely would be; do I have to compile this app or can I use an interpreted language?

I'll be back the day after tomorrow.

---

### Post by johand2 on 2014-11-27
As the users will have access by terminal emulator (ssh) and start a text based application, xbase-harbour, I just want to protect as much as possible.
So its end users and data protection.


Therefore, chroot them will only allow them on their own playground, just to be sure.

Regarding compiled or interpreted, it doesnt matter for me, it must be untamperable, and also its databases.
I just like the Clipper language, but also REXX for example will do. Just users must be able to execute it, and not able to modify programs, and be able to write to database only with the applications.
Thats all.

---

### Post by redmk2 on 2014-11-28
> **johand2 said:**
> As the users will have access by terminal emulator (ssh) and start a text based application, xbase-harbour, I just want to protect as much as possible.
So its end users and data protection.

Therefore, chroot them will only allow them on their own playground, just to be sure.

The Linux chroot is best used to isolate applications from the rest of the OS.  It really won't secure the application itself, the users from themselves or from users outside the chroot environment.  Read the "Basic Concepts" and "Uses of chroots" sections from[ this site]("https://help.ubuntu.com/community/BasicChroot") to see what I mean.  [This site]("https://securityblog.redhat.com/2013/03/27/is-chroot-a-security-feature/") provides a little more high level description of those concepts.
> 
Regarding compiled or interpreted, it doesnt matter for me, it must be untamperable, and also its databases.
I just like the Clipper language, but also REXX for example will do. Just users must be able to execute it, and not able to modify programs, and be able to write to database only with the applications.
Thats all.
It's really up to you.  If you like xbase languages then so be it.  I went from dBase III to PERL.  It was pretty painless.  The advantage is that I can administer the Linux with PERL as well as interface with SQL based databases.  Either way you will  have to use the SQL language to interface with that type of database.  I assume you are using a SQL back end on this project.
  
We can create a secure environment without the chroot.  What is the directory structure you want to use for the application (the compiled prg executables) and the data.  Is it like this:
```
/harbour/prg
/harbour/data
```

or maybe:
```
/harbour/prg
/harbour/prg/data
```

In any event all of this will have a common "root" directory (i.e. *harbour* or somesuch).

How many logins (*usernames*) will there be.  I'm not asking how many human users, just how many logged in users there will be.  How will you make this data available the end user?  Are you just going to display the data in text form at the terminal Command Line Interface (CLI)?

I think with your next set of answers we will be able to create a secure file system structure for both the application and the data it produces.

---

### Post by johand2 on 2014-11-30
I have removed the jail, it is indeed not needed.
Now, I solved with using the setuid on the files and it works as I want. Access without looking into the files!
My problem is now solved for the moment.
Thanks for your efforts.

---

