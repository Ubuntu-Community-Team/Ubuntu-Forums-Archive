---
title: "Restricting users"
date: 2010-08-26
forum: Server Platforms
---

### Post by djanie78 on 2010-08-26
Ok all is going well until... How can i restrict users to their home directories only?
My users will ssh into the server and will be taken to their home directories. I want them to stay there and not be allowed anywhere else.
Any ideas wise men... please

---

### Post by bernied on 2010-08-26
You might want a chroot jail for each user:
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

But maybe all you need to do is tweak your file permissions?
What is it you don't want the users to see?
If it's just the other users' files then chmod the home directories with o-rwx.

---

### Post by arubislander on 2010-08-26
Try googling: restricting ssh users to home directory

Good luck!

---

### Post by Lars Noodén on 2010-08-26
> **djanie78 said:**
> Ok all is going well until... How can i restrict users to their home directories only?
My users will ssh into the server and will be taken to their home directories. I want them to stay there and not be allowed anywhere else.
Any ideas wise men... please


Look at the configuration directive [ChrootDirectory](http://manpages.ubuntu.com/manpages/lucid/en/man5/sshd_config.5.html).  If they are connecting only via SFTP, that is easiest.

---

### Post by djanie78 on 2010-08-27
> **bernied said:**
> You might want a chroot jail for each user:
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

But maybe all you need to do is tweak your file permissions?
What is it you don't want the users to see?
If it's just the other users' files then chmod the home directories with o-rwx.

Users will be using winSCP and all i want them to see is stuff in their home folder, nothing else. They should not be able to go out of their folder at all.

---

### Post by Lars Noodén on 2010-08-27
> **djanie78 said:**
> Users will be using winSCP and all i want them to see is stuff in their home folder, nothing else. They should not be able to go out of their folder at all.

(Slightly Off topic -- winSCP suggests use of unreliable systems.  What application is holding the users back from upgrading to Linux?)

My guess is that winSCP is a SFTP client like [Filezilla](http://filezilla-project.org/).  In which case, using the directives **ForceCommand** and **ChrootDirectory** should allow them to get at what's in their own folder but not even see anything else.  

Add those users to a group and then constrain that group's access.


PS:  Your skilled users (i.e. non-Windows) might enjoy SSHFS, which follows the same constraints above, but allows access via a folder.

```

# for sshd_config, but test and verify 

Match Group *legacy*
    ForceCommand [internal-sftp](http://manpages.ubuntu.com/manpages/lucid/en/man8/sftp-server.8.html)
    ChrootDirectory [%h](http://manpages.ubuntu.com/manpages/lucid/en/man5/sshd_config.5.html)

# YMMV

```

No additional configuration of the chroot environment is necessary unless you want to provide interactive shells to those users in addition.

---

### Post by djanie78 on 2010-09-23
> **Lars Noodén said:**
> (Slightly Off topic -- winSCP suggests use of unreliable systems.  What application is holding the users back from upgrading to Linux?)

My guess is that winSCP is a SFTP client like [Filezilla](http://filezilla-project.org/).  In which case, using the directives **ForceCommand** and **ChrootDirectory** should allow them to get at what's in their own folder but not even see anything else.  

Add those users to a group and then constrain that group's access.


PS:  Your skilled users (i.e. non-Windows) might enjoy SSHFS, which follows the same constraints above, but allows access via a folder.

```

# for sshd_config, but test and verify 

Match Group *legacy*
    ForceCommand [internal-sftp](http://manpages.ubuntu.com/manpages/lucid/en/man8/sftp-server.8.html)
    ChrootDirectory [%h](http://manpages.ubuntu.com/manpages/lucid/en/man5/sshd_config.5.html)

# YMMV

```

No additional configuration of the chroot environment is necessary unless you want to provide interactive shells to those users in addition.

Aha i finally got around to fixing this issue. Thanks for pointing me in the right direction and it works beautifully

---

### Post by LightningCrash on 2010-09-23
You might set their system shell to rssh while you're at it.

---

### Post by djanie78 on 2010-09-23
> **LightningCrash said:**
> You might set their system shell to rssh while you're at it.

Good idea but i dont want them ssh'ing in at all. nosey people so i set their shell to false. this way only sftp, nothing else... i hope

---

### Post by LightningCrash on 2010-09-23
> **djanie78 said:**
> Good idea but i dont want them ssh'ing in at all. nosey people so i set their shell to false. this way only sftp, nothing else... i hope
IIRC they need a valid shell to sftp

You can set rssh to only allow the sftp command.

---

### Post by SeijiSensei on 2010-09-23
> **djanie78 said:**
> Ok all is going well until... How can i restrict users to their home directories only?

Why isn't Samba a better solution if all you want is to provide access to users' home directories on a Linux server?  Samba has a wide variety of methods to control access, plus the users' homes can be mapped to network drives, etc., making them easily available all the time without needing a client like WinSCP.

---

### Post by djanie78 on 2010-09-24
> **LightningCrash said:**
> IIRC they need a valid shell to sftp

You can set rssh to only allow the sftp command.

In I have got it working without installing rssh and setting user bash to false. There is loads of material out there showing how to do this. I suppose if i wanted them to be able to ssh in as well but of course restricted, rssh will be the answer but in my case no ssh at all. Works for me

---

### Post by LightningCrash on 2010-09-24
> **djanie78 said:**
> In I have got it working without installing rssh and setting user bash to false. There is loads of material out there showing how to do this. I suppose if i wanted them to be able to ssh in as well but of course restricted, rssh will be the answer but in my case no ssh at all. Works for me
I guess things have gotten better since the last time I implemented a chroot'ed SSH server.


> **SeijiSensei said:**
> Why isn't Samba a better solution if all you want is to provide access to users' home directories on a Linux server?  Samba has a wide variety of methods to control access, plus the users' homes can be mapped to network drives, etc., making them easily available all the time without needing a client like WinSCP.

You're assuming that the users are inside his building.

---

### Post by SeijiSensei on 2010-09-24
Even if they're not, they can use DNS to find the resource if the server is Internet facing or if he has a private name server visible to the clients.  Windows XP and later supports \\host.domain.name\share addresses as well as Netbios naming.

---

### Post by LightningCrash on 2010-09-24
> **SeijiSensei said:**
> Even if they're not, they can use DNS to find the resource if the server is Internet facing or if he has a private name server visible to the clients.  Windows XP and later supports \\host.domain.name\share addresses as well as Netbios naming.

From a security standpoint, that is a horrible idea.

[https://rhn.redhat.com/errata/RHSA-2010-0697.html](https://rhn.redhat.com/errata/RHSA-2010-0697.html)
^^^Seems like there's something on the order of that every 3 months.

---

### Post by SeijiSensei on 2010-09-24
> **LightningCrash said:**
> From a security standpoint, that is a horrible idea.

[https://rhn.redhat.com/errata/RHSA-2010-0697.html](https://rhn.redhat.com/errata/RHSA-2010-0697.html)
^^^Seems like there's something on the order of that every 3 months.

Perhaps his remote clients are on known, fixed IP addresses or connecting via VPN.  You don't have to open up the port to every Tom, Miguel, and Vladimir on the Internet if you have control over the network.  There's lots of ways to enforce security at the IP and the application layer.

---

### Post by LightningCrash on 2010-09-24
> **SeijiSensei said:**
> Perhaps his remote clients are on known, fixed IP addresses or connecting via VPN.  You don't have to open up the port to every Tom, Miguel, and Vladimir on the Internet if you have control over the network.  There's lots of ways to enforce security at the IP and the application layer.

The beauty of his solution is that it's secure and he's happy with it.

---

