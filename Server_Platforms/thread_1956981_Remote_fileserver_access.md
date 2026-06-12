---
title: "Remote fileserver access"
date: 2012-04-11
forum: Server Platforms
---

### Post by AbyssWolf1105 on 2012-04-11
Ok. So I set up my Ubuntu 10.04LTS Server on my old rig that was gathering dust in the corner. Best decision I have ever made seeing as how now I have a magic 500GB of space on my computer now made free. 

I have a few friends who want to also have access to this rig, some of which live in different states. I was wondering what would be the best way to do this. I tried setting up SSH and Squid tonight. I'm not an Ubuntu pro by any means, so some of this is rather confusing to me. 
If someone could point me to the direction of a fairly simple walk-through or spend a little time educating me I'd be ecstatic!

Any questions just ask. I have tomorrow off of work so I'll be messing around with this all day.

---

### Post by CharlesA on 2012-04-12
Check this out:

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

You probably want to look into port forwarding as well.

Note: If you do decide to use SSH, ***please*** use a very strong password or keys to connect as there are bots that will try to bruteforce their way into your server.

---

### Post by cj13579 on 2012-04-12
> **CharlesA said:**
> Note: If you do decide to use SSH, ***please*** use a very strong password or keys to connect as there are bots that will try to bruteforce their way into your server.

Agree with this - you can also use a package called *denyhosts*:

```
sudo apt-get install denyhosts
``` 
 
This scans your SSH logs to find brute-force attacks and then blocks the IPs they came from.

---

### Post by newbie-user on 2012-04-12
If you already have openssh-server installed, then that's basically all you need. You would have to supply your IP address to your friends and then do some port forwarding on your home router. If you have a dynamic IP from your ISP, then you might want to consider signing up for a dynamic DNS service and registering a domain name so that your friends can just connect to yourserver.yourdomain.com.

---

### Post by bubylou on 2012-04-12
I would definitely use ssh and use authentication keys with it.  Make sure to make some other security changes, such as disabling root login, changing the port, etc. You want to ensure your server is locked down before allowing access to it from the internet. Also what are you using squid for?

You can also install openssh by either
tasksel or apt-get install openssh-server

---

### Post by AbyssWolf1105 on 2012-04-13
> **CharlesA said:**
> 
Note: If you do decide to use SSH, ***please*** use a very strong password or keys to connect as there are bots that will try to bruteforce their way into your server.

> **cj13579 said:**
> Agree with this - you can also use a package called *denyhosts*:

```
sudo apt-get install denyhosts
``` 
 
This scans your SSH logs to find brute-force attacks and then blocks the IPs they came from.

Ok, so I did this. And I'm in the process of putting together the ssh keys. I've spent most of my day off, and time off of work reading and trying to put all of this together. 

> If you already have openssh-server installed, then that's basically all you need. You would have to supply your IP address to your friends and then do some port forwarding on your home router. If you have a dynamic IP from your ISP, then you might want to consider signing up for a dynamic DNS service and registering a domain name so that your friends can just connect to yourserver.yourdomain.com. 


I have a static IP, that I requested from my ISP, which eventually I will get a domain name registered. When.. I have more money and whatnot. 

> 
I would definitely use ssh and use authentication keys with it. Make sure to make some other security changes, such as disabling root login, changing the port, etc. You want to ensure your server is locked down before allowing access to it from the internet. Also what are you using squid for?


There's no real sensitive information on it or any computer on the network, at the moment. But, I'll start doing the things you listed just to be on the safe side.

Thanks to a few friends we've confirmed that you can get files off of the server, but they can't put anything into it yet. 
We did this through FileZilla. 

They all use windows, and my main computer is a Windows PC as well. I know I can connect through my network settings in Windows and use the built in GUI for navigating through the files I've made and such. But is there a way that someone on the recesses of the internet could do the same?

---

### Post by CharlesA on 2012-04-13
Domain registration is fairly cheap. I got a domain registered for 10 years for around 150 bucks.

Are they getting any errors when they try to put files on the server with filezilla? My bet is you need to adjust the permissions.

---

### Post by AbyssWolf1105 on 2012-04-13
That is definitely something to keep in mind, I could actually afford that. 

But now backtracking a step. I was able to get permissions fixed in the folders. But now, when I do a 
```
ls -ld /home/shares/music
```
it shows that as having four root users, I dont know if this could be bad in any way. I mean. I'm sure having four root users could be pretty bad. But I guess what I'm trying to say is, is there any way to remove everyone, besides myself, as a root and still let them have read/write capabilities on that folder.

Also... How would one give somebody their own personal dump folder, that would be available to only the person whom it's named after. I tried googleing it but, I dont quite think I know what I'm trying to google... :-k

---

### Post by CharlesA on 2012-04-13
Can you post what that says?

You can chroot users to their own home directories, or lock the other user's home directories down by changing the default permissions. If you have files they would need access to outside their home directories a chroot wouldn't work.

---

### Post by AbyssWolf1105 on 2012-04-13
Sure!

```
drwxrwxr-x 4 root users 4096 2010-04-11 23:32 /home/shares/music
```

And that makes sense. I'll look more into it tomorrow.

---

### Post by CharlesA on 2012-04-13
The permissions look right, anyone in the "users" group would have full access (read, write, execute).

Are the users you are trying to connect with in that group?

---

### Post by newbie-user on 2012-04-14
You would need to add your friends to the users group first. If they're not part of the users group, they can't write to the directory since your "world" permission set is r-x, which is only read and execute. Root and the users group have rwx, which is read, write, and execute. 

If you want to give each user their own personal file space, then you'd have to chown each personal directory to the user and chmod so that only the user has rwx.

chown -R username directory
chmod -R 700 directory

---

### Post by d4m1r on 2012-04-14
I would;

1) Register a free domain @ no-ip.org (for example yourname.no-ip.org)
2) Setup a FTP server for then to download/upload or even delete/create fils on the server using a FTP client. You can create 1 account per user and let them browse the server or lock the accounts down to a specific folder.

---

