---
title: "Add custom host for apache webserver"
date: 2006-08-02
forum: Server Platforms
---

### Post by nilsvdburg on 2006-08-02
Hi,

I've been looking for this for a while but couldn't find any answer.

I have an apache web server configured on my Ubuntu Dapper machine y I work on several projects. I used to work in windows but i think it is time to start working on Linux, so i tried to configure my apache the same way i had it on Windows, but there is one thing i can't find where to configure.
I like to use some virtual host and on windows to make it work i added some lines to c:\windows\system32\drivers\etc\host where adding some lines like 
192.168.1.3 servername1
192.168.1.3 servername2

So when i typed the address servername1 or servername2 it just looked in the computer with the apache running on it instead of looking it on internet.

So i would like to know if there is any file on ubuntu where i can make the same changes.

I hope I've explained me correctly and someone can help me with this.

Thanks,
nils

---

### Post by slakkie on 2006-08-03
You want to edit the file /etc/hosts

---

### Post by ragdemai on 2006-08-04
> **slakkie said:**
> You want to edit the file /etc/hosts

which line i need to edit? & what to add-in ?

---

### Post by slakkie on 2006-08-05
Read the man page on hosts: man hosts

It will describe the format of the /etc/hosts file.

---

