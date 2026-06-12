---
title: "Samba Server users limit ?"
date: 2015-09-30
forum: Server Platforms
---

### Post by gardenair on 2015-09-30
Hi,
          I have 70 users in my office environment which are using windows 7 and windows 8 on there desktop PC's .For sharing files like Ms office document I want to create samba server. Kindly could you please let me know that could samba server manage 70 users .Creating users in ubuntu and assigning smb password ?  

2- Question is I see a tutorial configuring samba server.[U][I]Here force group, create mask, and directory mask is a new thing for me .Could you please explain it and its purpose ?
[/I][/U]

```
[allusers]
  comment = All Users
  path = /home/shares/allusers
  valid users = @users
  [COLOR=#ff0000]**force group = users**[/COLOR]
  [COLOR=#ff0000][B]create mask = 0660
  directory mask = 0771[/B][/COLOR]
  writable = yes
```


Thanks
gardenair

---

### Post by SeijiSensei on 2015-09-30
70 users is not very many; Samba should be able to handle that just fine.  You'll have to invest some time to create accounts for all of them at the beginning, but after that it should just hum along.  

As for the "force group" option, this tells Samba what group should be assigned to the stored files *at the OS level*.  Ubuntu does not have a "users" group like some distributions do, so unless you create the group yourself, it's not relevant to you.  The "force user" and "force group" options make life easier if you want to let everyone have access to all the files.  In the example you give the "force group" and "mask" parameters set all new files to have read/write permissions for the owner and for all members of group users.  Then files created by one user can be modified by the others.  You may or may not want that given how your office works.  The directory mask works similarly, though 771 means any new directories are readable and writable by owners and members of group "users" and listable by anyone else.

---

### Post by TheFu on 2015-09-30
I agree with SeijiSensei.  I've run networks with hundreds of samba users and I've heard of networks with over 2K users.  Somewhere around 50 users, it becomes worth the trouble to use LDAP for the user-store.  You may want to look into that too.

---

### Post by gardenair on 2015-10-01
Thanks "[COLOR=#000000]SeijiSensei" and " [/COLOR][COLOR=#000000]TheFu" for the reply. Well as i understand it stand that an organization even have 2000 users samba can handle all the users smoothly.[/COLOR]
[COLOR=#000000]New users come in organization and old also resign so the addition and deletion of user not also affect the users data base in samba server.
Am I right ?


[/COLOR]

---

### Post by SeijiSensei on 2015-10-01
The simplest method for managing users in Samba is to give each person an account in Linux and a parallel account in Samba.  As TheFu suggests, when the number of users gets large, other authentication methods may be preferable.  Personally I've never found LDAP all that manageable, but perhaps the tools are better these days.  However Samba4 is designed to emulate a Windows Active Directory server, so that might be the best route for you.  I've not used this method, but this tutorial looks helpful: [http://www.tiltingatlinux.com/2014/04/basic-samba4-domain-controler-on-ubuntu.html](http://www.tiltingatlinux.com/2014/04/basic-samba4-domain-controler-on-ubuntu.html)

---

### Post by bab1 on 2015-10-01
> **SeijiSensei said:**
> ...Ubuntu does not have a "users" group like some distributions do, so unless you create the group yourself, it's not relevant to you. 

Ubuntu does have a user-group  called ***users*** by default.  In the Ubuntu distro it is always gid=100.  See below ```
getent group users
users:x:100:bab,jim,larry,bill,bob,sherry,louise

```
> 

+1 for Samba serving 1000's of users.  I have only managed about 200 users at one time.  I never had any problems.  In fact some Windows users were surprised to find out that Linux/Samba was used to store their files.  ;-)

---

### Post by gardenair on 2015-10-01
Thanks once again for your replies. There is a question that windows server also provide file server what will be the main benefit if I implement ubuntu file server ?

---

### Post by SeijiSensei on 2015-10-01
Linux and Samba are free.  More importantly, Windows Server requires not only a license for the server software, but a license for every single connected client machine (a so-called [Client Access License]("https://www.microsoft.com/en-us/licensing/product-licensing/client-access-license.aspx"), or CAL). These generally run about [$30/desktop]("http://shop.lenovo.com/us/en/itemdetails/0C19608/460/2B7023D911AD49ECADE0A6D015EB8C20") in bulk, and MS [just raised the price]("http://www.zdnet.com/article/microsoft-to-hike-by-13-percent-its-user-client-access-license-prices-as-of-august-1/") of these licenses.  For 70 users, you'll be paying three times as much for the CALs as you would for the [server software itself](http://www.newegg.com/Product/Product.aspx?Item=N82E16832416555).  It's a version of the "razor-and-blades" pricing strategy.

Sorry about the misinformation on the users group.  Looking at this machine, I do have a users group, but it is unpopulated.
```

$ grep users /etc/group
users:x:100:

```
Early Linux distributions automatically added new users to the "users" group, but that's no longer considered secure.  Both Debian-flavored distributions like Ubuntu, and RedHat flavors like CentOS, put each user into a personal group.
```

grep seiji /etc/group
seiji:x:1000:

```

---

