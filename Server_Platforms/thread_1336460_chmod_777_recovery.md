---
title: "chmod 777 recovery ??"
date: 2009-11-24
forum: Server Platforms
---

### Post by marciasa on 2009-11-24
Hello, 
I really need some help!!
last night by mistake I have chmod 777 all of my server instance ( ubuntu daper); 
now I can't access via ssh anymore;
is there any known way to recover my data ?
or to reconnect to it ?

please I am desperate

---

### Post by scorp123 on 2009-11-24
> **marciasa said:**
> is there any known way to recover my data ? Well, let's ask the obivious: You don't have any backups, right?

Well then: Boot a live CD and backup your **/home** partition (or directory?), e.g. to an external USB disk. And maybe a few essential files from **/etc**? e.g. **/etc/fstab**, **/etc/ssh/*key*** (if you restore those SSH daemon key files then the SSH identity will remain the same...). And then reinstall. All of it.

Sounds cruel. I know that. I've made this mistake too, ages ago. But ultimately chasing after each and every file permission (and trust me: there are many many files, pipes, device files, and what not) takes _LONGER_ and is less likely to succeed than a fresh reinstallation.

Yes, it sucks. But with all file permissions gone to Walhalla there is not much left to do. Collect what you can ... and reinstall.

---

### Post by marciasa on 2009-11-24
hello there,

thanks for your reply; 
it turns out that I HAVE SSH ACCESS!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
just downloaded all my precious var/www content and my beloved website :D
now I just need to get hold of the db, 

I know is in var/lib/mysql/mydb

can I then just copy that on the reinstalled instance, or can it in anyway be imported via phpmyadmin or some other tool?

thanks again; I was desperate; stupidly enough that was 2 months of work, with nearly zero back ups ;

I kept saying it to myself to back-up...back-up....remember to back-up, but I had to bang against it :)

thanks

---

