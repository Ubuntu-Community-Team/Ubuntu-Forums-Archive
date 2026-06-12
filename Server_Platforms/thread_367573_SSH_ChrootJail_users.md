---
title: "SSH Chroot/Jail users"
date: 2007-02-22
forum: Server Platforms
---

### Post by Claudiof on 2007-02-22
Hi,

I have read a lot of tutorials and possible solutions to create a chroot/jail ambient.

But i haven't found a "really" solution for what i want...


I want the jail the users in their own home dir's.

Like

/home/claudio/

The user claudio cant get access to the /home/ dir..

How? :|

---

### Post by kidders on 2007-02-22
Hi there,

Aside from the fact that such an arrangement would be tremendously limiting for your users, it wouldn't really be feasibe, I'm afraid. If you chrooted your users into their own homes, they would literally have access to *nothing* they needed to do anything at all.

Without access to /dev their software couldn't even get hold of a reference to the user's own terminal window which, in turn, you couldn't attach a shell to without access to /bin, /usr, etc. Sorting that out (by duplicating all required data into each home directory) would probably allow users to log in, but they would be unable to run any applications or share any data. The only effective solution would basically amount to installing lots of virtual servers, one for each user, to which each could then have root access.

Can I ask why you would want to lock your users into one corner of your server? Perhaps there is a more standard way of achieving the effect you want.

---

### Post by herromega on 2007-03-01
well i need to lock my users in there home directory, now they can cd to another users home directory and read all there files, not edit but read is unsecure enough. i have a lab-webserver at school and alot of student have a shell account on the server and now i need to lock them in there home dir.

can this be done? thnx anyway!:KS

---

### Post by scxtt on 2007-03-01
what are you trying to accomplish? -- just that they can't do an "ls" (get a listing of files) in any directory outside of /home/$USERNAME? -- so they can't "look around", but can still use the system? (compile C programs, for example) ... all you'd really need to do is remove read ability from "other" ... something like **chmod -R o-r *** should remove "read" access for anyone who doesn't own the file ... any directory that already has o+x would remain usable ...

by default linux doesn't allow other users to modify other user's directories / files ,,,

---

### Post by herromega on 2007-03-01
> **scxtt said:**
> what are you trying to accomplish? -- just that they can't do an "ls" (get a listing of files) in any directory outside of /home/$USERNAME? -- so they can't "look around", but can still use the system? (compile C programs, for example) ... all you'd really need to do is remove read ability from "other" ... something like **chmod -R o-r *** should remove "read" access for anyone who doesn't own the file ... any directory that already has o+x would remain usable ...

by default linux doesn't allow other users to modify other user's directories / files ,,,

yeah, i need em to have limited access to all folders in /home/, they should only have access to there own home dir. but also get access to all other functions in the server.

now all students can access all files in other users folders, and thats really bad..

---

### Post by shufla on 2007-03-01
Hello,

> **herromega said:**
> yeah, i need em to have limited access to all folders in /home/, they should only have access to there own home dir. but also get access to all other functions in the server.

now all students can access all files in other users folders, and thats really bad..

Hm. Try to:
```

sudo dpkg-reconfigure -plow adduser

```
And answer 'no'.

Then:
```

sudo chmod o-r /home/*

```
You will achive that only users in same group are able to read other users files. I think that's enough?

For such scenario no user-jailing is needed.

Bye,
Luke

---

### Post by herromega on 2007-03-01
> **shufla said:**
> Hello,



Hm. Try to:
```

sudo dpkg-reconfigure -plow adduser

```
And answer 'no'.

Then:
```

sudo chmod o-r /home/*

```
You will achive that only users in same group are able to read other users files. I think that's enough?

For such scenario no user-jailing is needed.

Bye,
Luke

Thnx.. works great!

---

### Post by scxtt on 2007-03-01
> **herromega said:**
> yeah, i need em to have limited access to all folders in /home/, they should only have access to there own home dir. but also get access to all other functions in the server.

now all students can access all files in other users folders, and thats really bad..read-only access isn't a big deal, unless you have people w/ "things to hide" in text documents :-p ... also, you'll want to check into UMASK options, cause AFAIK, any new files that are created will have "read access" for "other" ... so you'd want a UMASK like 0220 (read/write for user, read/write for group, no access for "other") ... but most if this (w/ the exception of UMASK) is default unix behavior ...

---

### Post by kidders on 2007-03-02
> **herromega said:**
> yeah, i need em to have limited access to all folders in /home/, they should only have access to there own home dir. but also get access to all other functions in the server.

now all students can access all files in other users folders, and thats really bad..In the traditional Linux security model, users are responsible for maintaining the access control details of their own files. Like scxtt mentioned, sysadmins can help out with settings like the umask, but whether strangers can freely browse/modify a user's files is really his own responsibility.

Provided it's properly configured, the rest of your system should be immune to interference though. One common slip-up, for example, is to inadvertently include a clear text password in a file in /etc.

If you wanted to, you could remove the world execute bit from all your users' homes. That way, everyone but the owners would lose the ability to traverse them, unless the user in question specifically changed that.

---

### Post by bur[n]er on 2007-03-15
This thread sucks.  No one answered the topic of "SSH Chroot/Jail users" which brought me here via Google.

Here's what I've tried so far to limit a user to only /var/www so they can manage the website.  

```
sudo apt-get install scponly
```

This installs a new shell that you can set users to use via /etc/passwd and changing the path to /usr/bin/scponly.  This works to lock out ssh access, but the user can still list all the files around the system.

SCPonly's website says that I can set the shell to scponlyc and the user should be locked into that directory.

```
sudo nano /etc/passwd
```

I found and replaced the /usr/bin/scponly with /usr/sbin/scponlyc, hit ctrl+x,y to save and tried to login again.  This time, WinSCP on the client gave an error and wouldn't connect.  Frustrated and defeated, I give up temporarily on the scponly idea.

What we need is an easy way to limit an ssh/sftp/scp user to a single directory that they can't just 'cd ..' out of.

---

### Post by Frosty Cold Drink on 2007-03-15
> **'bur[n]er said:**
> This thread sucks.  No one answered the topic of "SSH Chroot/Jail users" which brought me here via Google.

... 

What we need is an easy way to limit an ssh/sftp/scp user to a single directory that they can't just 'cd ..' out of.

Most of the time I see this happening its not really what is needed and amounts to taking the wheels off a car so it can't break the speed limit. The other common situation is that SSH, SFTP, and/or SCP aren't even the right solution for the original problem. You can obviously tell, I discourage this and tend to promote [alternate solutions]("http://askcolddrink.blogspot.com/2007/03/how-can-i-give-someone-one-ssh-access.html").

That said, [http://gentoo-wiki.com/HOWTO_chroot_login](http://gentoo-wiki.com/HOWTO_chroot_login)

---

### Post by kidders on 2007-03-15
> **'bur[n]er said:**
> What we need is an easy way to limit an ssh/sftp/scp user to a single directory that they can't just 'cd ..' out of.I'm intrigued as to why anyone would want to do this. :confused: I'd tend to agree with Frosty Cold Drink, in that SSH/SCP probably aren't the right solutions for you.

If you could elabourate a little on why you need to keep your users out of /bin, /home, /usr/share/doc, and so on, (and, more importantly, what you *do* want them to be able to do), we may be able to find you a practical alternative.

---

### Post by chuckao on 2007-03-20
Yes, Burner is correct, it is a thread without correct answers. 

Let me try to explain my scenario.

I have users that need to connect in my server just to transfer their files. Well, I can use FTP, but users can get every file (with read access for all) in my server and I don't want this. It is a secure server 

Solution, ProFTPd implents 'jail'. So, users can transfer files but they are lock in their homes. 

But, how I wrote before, I have a secure server and I don't want to see passwords on the network as plain text. So, which service provides secure transfer? Exactly, SFTP (that is SSH).

Great!! But, Does openssh-server provide jail like ProFTPd? NO!!](*,) 

Thus, there are two solutions for the case above.:lolflag: 

[1] [http://www.minstrel.org.uk/papers/sftp/](http://www.minstrel.org.uk/papers/sftp/)
[2] [http://crux.nu/Main/ChrootSFTP](http://crux.nu/Main/ChrootSFTP)

and there is an another thread in this forum that provides antoher different solution but I don't know where.

Cheers,

---

### Post by kidders on 2007-03-20
> **chuckao said:**
> Solution, ProFTPd implents 'jail'. So, users can transfer files but they are lock in their homes. ... Great!! But, Does openssh-server provide jail like ProFTPd? NO!!](*,)

There seems to be a fundamental misunderstanding here. The SSH and FTP protocols are _not_ comparable. One is a terminal shell protocol (that just happens to offer a file transfer facility for convenience), where the other is specifically designed to copy files and do nothing else. In a sense, you are comparing OpenOffice and Nano, and complaining that OpenOffice is annoying because you can't disable the text formatting capabilities that Nano doesn't have.

Also, note that the term "chroot jail" does _not_ describe a means by which FTP servers prevent users accessing directories outside their own homes.

If all you want is a secure file transfer protocol, may I suggest FTPS.

I hope that helps a little.

---

### Post by Frosty Cold Drink on 2007-03-20
> **chuckao said:**
> Yes, Burner is correct, it is a thread without correct answers. 

Let me try to explain my scenario.

I have users that need to connect in my server just to transfer their files. Well, I can use FTP, but users can get every file (with read access for all) in my server and I don't want this. It is a secure server 

Solution, ProFTPd implents 'jail'. So, users can transfer files but they are lock in their homes. 

But, how I wrote before, I have a secure server and I don't want to see passwords on the network as plain text. So, which service provides secure transfer? Exactly, SFTP (that is SSH).

Great!! But, Does openssh-server provide jail like ProFTPd? NO!!](*,) 

Thus, there are two solutions for the case above.:lolflag: 

[1] [http://www.minstrel.org.uk/papers/sftp/](http://www.minstrel.org.uk/papers/sftp/)
[2] [http://crux.nu/Main/ChrootSFTP](http://crux.nu/Main/ChrootSFTP)

and there is an another thread in this forum that provides antoher different solution but I don't know where.

Cheers,

There are anwsers  before you posted.

For the lazy: [http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-TLS.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-TLS.html)

---

### Post by Mr. C. on 2007-03-20
Burner,

If you come up with your own conclusions based upon invalid assumptions, your options become limited.

a) Many FTP servers have various features to deny access in one form or another. Vsftpd, for example, has jailing capabilities, along with other security features.

b) To prevent clear text passwords, an encryption layer is required.  Either TLS/SSL or SSH provide this.  Several FTP servers support TLS/SSL.

c) ssh does not provide a "jail", as it is en encryption protocol; it encrypts a stream of data.  You can readily see that "jail" makes no sense in this context.

d) if your server is secure, you should provide unique user IDs to each user, for auditing purposes.  It can safely be said that all FTP servers provide this capability.

e) if your server is secure, you must understand the risk areas when creating a chroot environment.

MrC

---

### Post by chuckao on 2007-03-20
> **Frosty Cold Drink said:**
> There are anwsers  before you posted.

For the lazy: [http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-TLS.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-TLS.html)

Putz....thank you for this URL...I will try it now :mrgreen: 

And I agree that FTP is better than SSH to transfer files.

cheers,

---

### Post by ahman_ra on 2007-03-22
The problem isn't always so straight forward.  The clients I'm attempting to resolve only have the option of SFTP which I tried to make everyone see is BAD BAD BAD.  However, the expensive new systems the colleges are bringing online do these dead drops using sftp.  So, I have to catch sftp transfers, and i want to make it where they cannot see a thing.  I hope these other links work, I've trashed the system I'm typing from because I didnt think the revert-from method through.  (i'm getting a message that i need to change sudoers from 0444 to 0440, which it wont let me do):lolflag:

---

### Post by erat123 on 2007-12-16
what about wolfgang's jail?  I've used it in the past, and it worked very well!  only problem is, it doesn't look like it's working under gutsy.

[http://www.fuschlberger.net/programs/ssh-scp-sftp-chroot-jail/](http://www.fuschlberger.net/programs/ssh-scp-sftp-chroot-jail/)


If anyone can fix it up or find a work around, could you let all of us know, b/c this does exactly what we need it to do.

I've only been using it on Ubuntu 6.06 Server, so it's a few releases ago.. that whole LTS thing :-)

Thanks for any comments!

---

### Post by bEnChIzE on 2008-02-19
Hi guys!

I'm a newbie here in this forums.

I have a question.

I cannot jail the users to their home directory but I already input DefaultRoot ~ in the proftpd.conf and I already set their permission. 

Can someone please help me?

Thanks!

---

### Post by pancakedan on 2008-02-19
I am using jailkit to chroot users and works well, easy to setup on 6.06

Have windows users logging using winscp and jailed. 

[http://olivier.sessink.nl/jailkit/index.html#intro](http://olivier.sessink.nl/jailkit/index.html#intro)

---

### Post by Endolith on 2008-05-14
> **kidders said:**
> SSH/SCP probably aren't the right solutions for you.

If you could elabourate a little on why you need to keep your users out of /bin, /home, /usr/share/doc, and so on, (and, more importantly, what you *do* want them to be able to do), we may be able to find you a practical alternative.

I'd like to know what the practical alternative is, too.  All of the solutions I've seen include lots of warnings and complicated setup.  I don't want to set up something that has vulnerabilities I don't understand.  I know enough to know that what I don't know is dangerous.

For instance, I set up a user account with scponly as the default shell, but I can still access the entire filesystem through it.  I think "chroot" would prevent that, but [http://sublimation.org/scponly/wiki/index.php/Install](http://sublimation.org/scponly/wiki/index.php/Install) says > If you do use chroot(), your binary will need to be setuid. This should make any security conscious administrator wary.I don't know what that means, so I'm not going to explore it any further.

My application is just sharing files with friends (Running Windows, MacOS X, or Ubuntu) and letting them upload files, maybe including collaborative directories that we can both modify.  I trust them not to try hack into anything after they've entered their password or to maliciously fill up my drive with large files, but I don't want them to be able to look through my whole filesystem and I don't them to be able to modify or delete things in certain areas by accident; just the areas I've given permission for each user to access.

---

