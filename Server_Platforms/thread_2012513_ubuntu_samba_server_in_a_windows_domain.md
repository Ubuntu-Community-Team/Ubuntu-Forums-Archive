---
title: "ubuntu samba server in a windows domain"
date: 2012-06-29
forum: Server Platforms
---

### Post by nervensaege on 2012-06-29
I have a problem setting up a samba file server in a windows domain. 
  We have windows domain (Windows Server 2008) and I would like to set  up a ubuntu server as NAS and Webserver (egroupware). I know that both  yould also be done by our windows sever but for some reason we need the  ubuntu machina additionally. The users of our windows domain shall be  able to mount the shared folders with there domain users.
  What did I already manage? The sever is running, the groupware is installed and also configuring  samba shares is no problem. Because the people shall be able to use  their domain users I also managed to include the server into the domain  with winbind and kerberos. That means it is possible to login on the  ubuntu server via ssh with a domain user.
  What does not work? It is not possible to mount a samba share from a windows client with a  domain user. Using the grafical samba config tool I am possible to add  domain users to the samba users and to configure a shared folder and  select domain users that shall be able to use it. BUT: after restarting samba the shared folders are visible in the  network and when I click on them I am asked to enter the username and  password. If i enter a domain user Windows always tells me that I am not  allowed to use that folder.
  Do you have any idea what the problem is? Sorry for my bad english, I'm german ;)
  Thx, Marko

---

### Post by bab1 on 2012-06-29
> **nervensaege said:**
> I have a problem setting up a samba file server in a windows domain. 
  We have windows domain (Windows Server 2008) and I would like to set  up a ubuntu server as NAS and Webserver (egroupware). I know that both  yould also be done by our windows sever but for some reason we need the  ubuntu machina additionally. The users of our windows domain shall be  able to mount the shared folders with there domain users.
  What did I already manage? The sever is running, the groupware is installed and also configuring  samba shares is no problem. Because the people shall be able to use  their domain users I also managed to include the server into the domain  with winbind and kerberos. That means it is possible to login on the  ubuntu server via ssh with a domain user.
  What does not work? It is not possible to mount a samba share from a windows client with a  domain user. Using the grafical samba config tool I am possible to add  domain users to the samba users and to configure a shared folder and  select domain users that shall be able to use it. BUT: after restarting samba the shared folders are visible in the  network and when I click on them I am asked to enter the username and  password. If i enter a domain user Windows always tells me that I am not  allowed to use that folder.
  Do you have any idea what the problem is? Sorry for my bad english, I'm german ;)
  Thx, Marko

See the bug mentioned in [**_[COLOR="RoyalBlue"]this thread[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=12063000").

---

