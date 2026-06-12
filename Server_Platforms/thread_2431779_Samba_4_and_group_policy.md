---
title: "Samba 4 and group policy"
date: 2019-11-21
forum: Server Platforms
---

### Post by glennbtn on 2019-11-21
Hi All

New to running Samba ad on a server and could do with a little advise. 

I have build and Ubuntu 18.04 server with Samba 4 AD. The installation went fine with no issues and I have added a windows 10 pc to the domain and can login to the pc with any account I have created on the domain.

I have installed RSAT tools to user with users and computers and Group Policy. With this I set 2 parts of the policy on the default domain policy for expiry of the current password and the login text banner that say welcome to the domain (just for testing) When I login I don't get prompted to to change the password which is past the max days and also the login message does not appear. I did dig in to the registry on the Windows 10 box and can see the login text has been imported in to the settings.

If I run GPRESULT /H GPResult.html  to get info on the login it does say that under denied GPO that it was denied because it was empty but it's clearly not.

Can anyone suggest where the issue may lie or how to debug the issue as am at a loss at the moment 

Thanks

---

### Post by howefield on 2019-11-21
Thread moved to the "*Server Platforms*" forum for a better fit.

---

