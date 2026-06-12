---
title: "HOWTO Install pureadmin/pure-ftpd with virtual users support"
date: 2006-07-11
forum: Tutorials
---

### Post by tcollogne on 2006-07-11
Hi all,

I am using Kubuntu Dapper Drake and have written this little guide for installing PureAdmin/Pure-FTPD with virtual users on kubuntu (probably also works on ubuntu). I hope this can help some people with problems.

1) Install attached pureadmin
```
sudo aptitude install pureadmin
```
2) Create group ftpgroup
```
sudo groupadd ftpgroup
```
3) Create use ftp user
```
sudo useradd -g ftpgroup -d /dev/null -s /etc ftpuser
```
4) Create ftpuser directory
```
sudo mkdir /home/ftpusers
```
5) Create joe user directory
```
sudo mkdir /home/ftpusers/joe (you can create a directory for each ftp user)
```
6) Create virtual user joe
```
sudo pure-pw useradd joe -u ftpuser -d /home/ftpusers/joe
```
7 ) Update virtual user db
```
sudo pure-pw mkdb
```
8 ) Create symbolic links
```
sudo ln -s /etc/pure-ftpd/pureftpd.passwd /etc/pureftpd.passwd
sudo ln -s /etc/pure-ftpd/pureftpd.pdb /etc/pureftpd.pdb
sudo ln -s /etc/pure-ftpd/conf/PureDB /etc/pure-ftpd/auth/PureDB'
```
11) Create config files (File names are case sensitive)
```

echo "no" > /etc/pure-ftp/conf/AnonymousOnly
echo "yes" > /etc/pure-ftp/conf/NoAnonymous 
echo "/etc/pure-ftpd/pureftpd.pdb" > /etc/pure-ftp/conf/PureDB 
echo "yes" > /etc/pure-ftp/conf/PAMAuthentication
echo "yes" > /etc/pure-ftp/conf/CreateHomeDir

```

12) Modify permissions of /home/ftpusers directory and of any subdirectories. Owner must be ftpuser while Group must be ftpgroup :
```
sudo chown -R ftpuser:ftpgroup /home/ftpusers
```
13) Run Command
```
sudo pureadmin
```
When you go to manage users, you should see the user joe we created. It seems that adding users with PureAdmin doesn't work for
me, so when I want to add a new user, I use step 6 &7.

If you get the message that the status of the server can not be found (something with permission denied in the logfile viewer), you need to stop pureadmin
then create the dir /var/run/pure-ftpd (sudo mkdir /var/run/pure-ftpd). When you restart pureadmin, the problem is solved.

Beware that every time you shutdown your pc, the directory gets deleted. So you should repeat the above step.

Please post your experiences using the above guide. This can help other people.
Back to top 	
View user's profile Send private message

[FLeiXiuS: I edited a few things to make it more reable to our viewers.  I made step 11 easier to understand.  PM me with concerns]

---

### Post by stiankarlsen on 2007-02-24
I've followed your every step, but i keep getting **[WARNING] Authentication failed for user [joe]** when I try to log in

---

### Post by Pontiac on 2007-03-12
I run into the same issue.  I've even changed the PAMAuthentication so that it contains no and I still cannot get any virtual users to connect.

When I restart the server, i get:

Restarting ftp server: Running: /usr/sbin/pure-ftpd -l puredb:/etc/pure-ftpd/pureftpd.pdb -u 1000 -E -O clf:/var/log/pure-ftpd/transfer.log -j -B

Which is good.  I see that it is hitting the pdb file for the users, but its still not actually authenticating by that database.

---

### Post by inception on 2007-03-24
Very nice guide :)
I run Server Ed. though, so only blackbox here.
I've made virtual users, they're in the .pdb file, but I can't get pure-ftpd to read them, don't know how to. Anyone can help me? :)

It's original documentations was pretty hard to get and confusing.

---

### Post by inception on 2007-04-03
PureFTP is now 6 feet under and replaced with ProFTPd, since it had a config file.

---

### Post by Pontiac on 2007-04-04
Does ProFTPd have virtual users instead of using system accounts?

---

### Post by joechiang on 2008-02-13
i got it to work
after i start pureadmin

edit tab -> preference -> search system
manage -> users joe should appear
edit user and change password for joe

then it worked

---

### Post by kevindontenville on 2008-03-12
Hi

Noted that some of the command lines may have a type in them?

They show on the guide as 

/etc/pure-ftp/conf 

but on my install are 

/etc/pure-ftpd/conf  (note the d on pure-ftpd)

It may be different on Kubuntu (I have Ubuntu) but I suspect the path names should be similar.

Hope that helps someone!

K

---

### Post by orkerone on 2008-06-02
Yeah, the same for me. Had to add the "d" letter to get things working. If not, I get an error message about the file specified not existing.

And even after, I can't see my user in PureAdmin interface. And can't connect to my IP, too. But thanks for the tutorial :)

---

### Post by Endolith on 2008-06-22
> **stiankarlsen said:**
> I've followed your every step, but i keep getting **[WARNING] Authentication failed for user [joe]** when I try to log in

I get the same error.  Has anyone fixed this?

Similar thread: [http://ubuntuforums.org/showthread.php?t=684590](http://ubuntuforums.org/showthread.php?t=684590)

---

### Post by rko618 on 2009-05-25
Thanks for posting this guide! I was able to get it to work. I also skipped step 11 which did not seem necessary (maybe it was 3 years ago when this guide was written).

Is it possible to have symlinks to outside the chroot'd directory work? I read some of the documentation and it looks like I will have to compile Pure FTP by hand to get that enabled.

---

### Post by alacrityit on 2009-06-09
for all the Authentication failed issues, try this:

```
sudo mv /etc/pure-ftpd/auth/PureDB 50PureDB
```

or link it that way to begin with, this will check the PureDB before the other modes of auth.

---

### Post by bartos on 2009-07-22
Nice article
My problem is that I can log in from outside my network but not from inside.
If someone can point me to a config file or or option to fix this.

Thanks

---

### Post by Debiaq on 2009-07-25
Hello Everyone, when i try to restart pureftp i have tis message:

> 
Restarting ftp server: /usr/sbin/pure-ftpd-wrapper: Invalid configuration file /etc/pure-ftpd/conf/AnonymousOnly~: No corresponding directive


In /conf/AnonymousOnly - i have only "no" directive .. 

**Please help !**

---

### Post by oldneuro on 2010-08-11
FYI

I ran into the same problem where pureadmin couldn't create users. The problem is that when you start pureadmin, under edit->preferences->external, the default password and puredb file were both "(NULL)". I changed them to /etc/pure-ftpd/pureftpd.passwd and /etc/pure-ftpd/pureftpd.pdb respectively and from that point pureadmin was able to properly manipulate virtual users. This was a bug in at least Ubuntu 8.04, but seems to have been fixed in at least Ubuntu 10.04.

---

### Post by hhamilton4 on 2012-01-01
This is a great article.  It worked for my virtual ftp users.  The problem now is after adding ftpuser, I now get a login panel.  I cannot login as ubuntu or root, this is no surprise.  How can I get the autologin as ubuntu after adding the ftpuser account?

---

### Post by murderousone on 2012-03-05
great tutorial.. i got everything working following your info to the T......

but im having some trouble...

ive added user joe to the ftp user & user group..

logs in fine & also im able to browse the created home directory fine..

if i chown the directory, allows the user joe to upload/download/create directorys etc.

but how do i make vusers have certain permission to some of the created directory's... 

meaning..  certain directory's will b readable only & some writable..

example.
virtual user
joe logs into ftp, home directory: /home/joe/

but user joe cannot create/delete/execute on  /home/joe/directory1 = meaning readable only.
     & 
for 2nd directory 
user joe can create/delete/execute ON  /home/joe/directory2 = write-able & readable.


any help would b greatly appreciated... thanks in advanced...

---

### Post by murderousone on 2012-03-06
> **hhamilton4 said:**
> This is a great article.  It worked for my virtual ftp users.  The problem now is after adding ftpuser, I now get a login panel.  I cannot login as ubuntu or root, this is no surprise.  How can I get the autologin as ubuntu after adding the ftpuser account?

keeping it non technical & not 2 confusing.
the reason those account don't work anymore, is because those accounts arent in the puredb... 

the server is authorizing the groups/passwords & users using the PureDB file.  basically matching the users/groups/passwords assigned & the way u added them in the PUREDB.... 

enter
```
pure-pw list 
```if its not in the list then you wont b able to connect.

so u basically have to add your ubuntu/root user name & group name the user is running on,
 & add it to the puredb, like how you would add your Vusers...
 same way u add users ftpgroup/ftpusers... 

using root or a direct system account is def not recommended... but to each is own.

once u add the root user & group, remember to save those accounts/groups to the puredb file using the command:
 ```
pure-pw mkdb
```also a restart is always good after making changes the the puredb.

using this command
```
/etc/init.d/pure-ftpd restart
```

---

