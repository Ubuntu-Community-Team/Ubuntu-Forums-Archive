---
title: "Sense of running another ubuntu server"
date: 2008-11-11
forum: Server Platforms
---

### Post by self-defence on 2008-11-11
Hi,

I'm a little stuck and I can't decide what is my best option. Anyway I've got an ESXi VMWare running and on it there is an Ubuntu Server acting as a web server for the schools website. The server also has some other guest systems for other stuff but that's not important. But a professor has requested that I setup a web server with database support and php for the student's so that they could test the work that they have done.
Now is it sensible to setup another installation of Ubuntu server just for the students and just set up things so that the server is accessible form a sub domain. Or just setup the primary web server to host the student websites. But I'm a little concerned that I would put applications on the server that runs the main application and give access to the database that contains relatively important data. 
Because of this it would probably make sense to setup a new server for this right?

Now the other thing is if I do setup another server how do I setup access for 400 users. Since doing it by hand is not sensible and I do have all the student user names and passwords in the database. Could I hook that up to some kind of LDAP and have it generate access automatically?
I mean I'm a little in the dark here so any advice is welcome.

Thanks for the help.

Bye

---

### Post by hictio on 2008-11-11
> 
But I'm a little concerned that I would put applications on the server that runs the main application and give access to the database that contains relatively important data.
Because of this it would probably make sense to setup a new server for this right?


If the server's hardware can withstand the burden of another OS running, I would say that an extra one, devoted to what the students might need is the best choice, security wise.

> 
Now the other thing is if I do setup another server how do I setup access for 400 users.


Yeah, it might be a way to go... Does the data exists right now? Do you have to transfer that? Or you'll have to create it?

Incidentally, how are you administering this systems? Via SSH?

---

### Post by self-defence on 2008-11-11
The servers HW should be able to handle a few more VMs since it is a HP ProLiant M350 G5 with quad core 2.0 GHz and 8 GB of ram. And as for performance wise the student server does not need that much resources since it's going to be a development environment speed is not that important.
I administer the primary web server via ssh and webmin.
All the students get added into a mysql database anyway since they have access to the application running on the primary and can login. Now I can make an addition to this app so that anytime any user changes the password it can automatically update another database for the LDAP (I saw that LDAP can get user info from database) if this can be used anyway it would make it almost automatic.

The ESX is currently also running a gateway system for the network but it also doesn't seem to be using that much of recourses. So I think I can still run 3 to 5 low resource systems and 2 medium. But since all I plan to run is low resource system I think I'll be alright.

Anyway hictio thank you and any recommendations are much appreciated.

Bye

---

