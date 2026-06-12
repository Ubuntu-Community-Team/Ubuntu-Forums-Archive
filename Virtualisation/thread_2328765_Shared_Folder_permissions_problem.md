---
title: "Shared Folder permissions problem"
date: 2016-06-24
forum: Virtualisation
---

### Post by AlessandroBraghini on 2016-06-24
Hi, I have a problem with my CentOS Linux 7 Virtual Machine: I set a shared folder , which is the document root for my vhosts, but I have an issue: only users in group vboxsf can create/modify/delete files in it, even the root user (I tried a touch somefile.txt) was not able to create a file in the path, it gaves me a "protocol error".
I did this command: sudo adduser root vboxsf, and after that, touch command goes and root user created a file somefile.txt in the path, I checked it on the finder of my local machine.
So when i'm browsing a site pointed to the IP of my VM I can access to it, but not create files in the root document, such the cache, if I delete it and go to my site address hosted on VM it doesn't recreate it, or if I get an error log file, it doesn't create the file in the path.
I think the user in this case is apache, or am I wrong?
I tried to do: sudo adduser apache vboxsf, but i still have the problem.
Can someone please help me? thank you.
Have a nice day!

---

### Post by MAFoElffen on 2016-06-24
I read that you are using VirtualBox with a CentOS 7 host...

What is your host CPU? 

What is your host OS and it's version?

Are you using and what is your version of the Extension pack or Guest Addition?

Did you read [this]("https://help.ubuntu.com/community/VirtualBox/SharedFolders")?

---

### Post by &amp;KyT$0P# on 2016-06-24
I thought that web servers run as user 'www-data'?

Check that:
 - you have restarted the webserver or system after adding its user to vboxsf
 - you're not trying to write symlinks to the shared folder from inside a VM
 - you don't have a Guest Additions version mismatch

If that doesn't help, in the VM please cd into the shared folder and post the output of these commands:
```
ls -la
```
```
id www-data
```
```
id apache
```

Also, what VirtualBox version are you using and what Ubuntu version is your host?

---

