---
title: "Proftpd access rights to various folder for various users"
date: 2012-01-16
forum: Server Platforms
---

### Post by rado3105 on 2012-01-16
Hi I have users: r-c, admin, peter. Folder /media/wd1500GB has many subfolders. All subfolders have chmod a+rwx(because of samba).I want to user r-c to read/write all subfolders in wd1500GB. But users admin, peter cant read /wd1500GB/Auta

I installed proftpd and change config like this:
> <Directory /media/wd1500GB/Auta>
<Limit READ>
Allow r-c
DenyALL
</Limit>
<Limit READ WRITE>
Allow r-c
</Limit>
</Directory>

<Directory /media/wd1500GB/>
<Limit READ>
Allow admin peter
</Limit>
<Limit READ WRITE>
Allow r-c
</Limit>
</Directory>

But when I login to ftp user peter and admin can see /wd1500GB/Auta and also can write them and also can write to other subfolders. Why? What I am doing wrong?

---

### Post by rado3105 on 2012-01-16
I dit it like this:
[http://rado3105.blogspot.com/2012/01/install-and-configure-proftpd-in-debian.html](http://rado3105.blogspot.com/2012/01/install-and-configure-proftpd-in-debian.html)

I used symlinks.
This I put in /etc/proftpd/proftpd.conf:

> <Limit LOGIN>
 AllowGroup ftp
 DenyAll
 </Limit>

<Directory /home/ftpadmin>
     <Limit READ WRITE>
      Allow ftpadmin
       DenyAll
     </Limit>
   </Directory>

When I connect to that fpt using ftpadmin as user I cant write there, but I should be. What is wrong?

---

### Post by rado3105 on 2012-01-17
I had to removed this rules:

> <Limit LOGIN>
AllowGroup ftp
DenyAll
</Limit>

<Directory /home/ftpadmin>
<Limit READ WRITE>
Allow ftpadmin
DenyAll
</Limit>
</Directory>

It now writes....

---

