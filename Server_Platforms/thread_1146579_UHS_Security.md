---
title: "UHS Security"
date: 2009-05-02
forum: Server Platforms
---

### Post by stretch427 on 2009-05-02
Hey, I'm new to home servers and before I begin file backup I want to make sure my connection is secure. 

I took a look at SSHhowto: but I was confused. Can someone link me somewhere or explain how to secure my connection

Thanks!

---

### Post by gombadi on 2009-05-02
> 
Hey, I'm new to home servers and before I begin file backup I want to make sure my connection is secure. 


Can you give us a bit more info on what you are trying to do.
I am not sure what you mean by file backup - are you going to do a backup to a remote server via an ssh connection?

If you are asking how to make ssh more secure(less open to script kiddies) then -
- change to a non standard port
- Add AllowUsers for the usernames you want to connect
- Disable root ssh logins
- use keys instead of passwords

If you can give us a bit more info on what you are trying to acheive then we will be able to better answer your question.

---

### Post by stretch427 on 2009-05-02
Bare with my ignorance but basically I'm trying to create a small file server. I want to restrict access to a certain user group. How? Command?
I also want to use keys instead of passwords. Again don't know how. Command?
And disable root ssh logins. ? Command?

---

### Post by daboroe on 2009-05-02
same here i want to do this too. its very easy to set up pgp keys to do this. so yeah lol.

---

### Post by gombadi on 2009-05-03
> **stretch427 said:**
> Bare with my ignorance but basically I'm trying to create a small file server. I want to restrict access to a certain user group. How? Command?
I also want to use keys instead of passwords. Again don't know how. Command?
And disable root ssh logins. ? Command?

The main config file for ssh server is /etc/ssh/sshd_config. 

Root logins are normally disabled by default. Normally the root account on Ubuntu does not have a password unless you set one so you can not ssh in as root. You can also make sure the following line is in the ssh config file -
```

PermitRootLogin no

```

To allow certain users or groups to ssh in you can set the AllowUsers and AllowGroup values in the config file.

For example
```

AllowUsers user1,user2@192.168.5.4,user3@*example.com
AllowGroups sshusers

```

From the command line type "man sshd_config" on the server to see a full description of the configuration options available.

As for keys there are many good pages on the Internet and threads in these forums that will give you detailed instructions on how to setup and configure your system to allow key only access. No point in duplicating the effort.
If you have more than one client connecting to the server then you will have to generate separate keys and put them all in the authorized_keys file.


After making changes to the ssh config don't forget to reload it so the changes take effect -

```

sudo /etc/init.d/sshd reload

```

---

### Post by stretch427 on 2009-05-03
I did that and noticed that root login was set to yes by default. or at least I didn't know of anything I did to set it that way. I changed that and restarted

but I didn't see anything like this in the config file. could it be called something else? 
> 
```

AllowUsers user1,user2@192.168.5.4,user3@*example.com
AllowGroups sshusers

```

---

### Post by gombadi on 2009-05-03
The AllowUsers and AllowGroups are not in the config file by default but you can add them to restrict who can login to the machine using ssh.

You should change the usernames to the people you want to be able to login and if you want you can add an ip address so the users can only login from that ip address.

The man pages and google will be able to provide more information about the sshd_config file options.

---

