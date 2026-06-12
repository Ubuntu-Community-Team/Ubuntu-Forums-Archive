---
title: "Help! Need to stop SSH users snooping around"
date: 2007-05-24
forum: Server Platforms
---

### Post by feenster on 2007-05-24
Hi all,
I've got a server that is receiving data from various users outside my network via SSH (using Rsync). Each user is setup on my server, with their shell pointing to **/bin/bash**. They are authenticated against the server via a public key when the data is sent. They can also login via FTP to view their data with their username and password.

To be extra safe, I want to ensure that a user couldn't log in with SSH and look at the other folders/users on the server. If they could be locked into their home directory, that would be ideal. If not, is there another obvious way to handle this so **User-A** can't even see **User-B's** files?

Cheers,
     Matt

---

### Post by McLogic on 2007-05-24
[http://ubuntuforums.org/showthread.php?p=722564&highlight=gui#post722564](http://ubuntuforums.org/showthread.php?p=722564&highlight=gui#post722564)

This should help. I should note that it did not work for me -- perhaps it is missing a step.

---

### Post by nomb on 2007-05-24
I'm a little confused.  I thought if their home directory was chmoded and chowned to the user then it would only be able to be entered/modified by that user.

If your looking to create a sandbox for the users at their home directory then this should work nicely for you:
[http://www.securityfocus.com/infocus/1404]("http://www.securityfocus.com/infocus/1404")

EXERPT:[I]SSH 2.1.0 (and above) can be set to automatically chroot specified users and groups within their home directory. This gives administrators an excellent start toward providing a secure environment for their users. It's built into a daemon that you're probably already running, so there's no extra overhead. And since it's SSH, you also have the added benefit of encrypted sessions with no extra effort. 

[/I]

nomb

---

### Post by Soybean on 2007-05-24
Shouldn't it be sufficient to just "chmod 700" the home directories?

---

### Post by nomb on 2007-05-24
Thats exactly what I was saying.  :D  Glad to have someone in agreement.

---

### Post by feenster on 2007-05-24
Hi,
Yes, that would of course stop people actually opening up the other directories, but they would still be able to look at other files around the filesystem. They would also be able to list the directories of the other users - ie., they could see who else was storing their data there.

I've had a good Google and whilst there seems to be a few different ways to do this, they all seem pretty complex. Is there no easier way to do it? I was rather hoping there would be one command to do it, like with Proftpd ;)

Matt

---

### Post by elst on 2007-05-24
Apparently you can specify a command within an SSH key, so that the user can only run that command when they authenticate with the key - if the users only need rsync access you might be able to do something with this feature. scponly may also be useful for restricting user access. I haven't experimented with either yet myself.

If you want to restrict access into home directories then you need to turn off the "public home directory" feature of adduser:

sudo dpkg-reconfigure adduser

This doesn't affect existing accounts, but it prevents the adduser utility from giving new users world-readable home directories.

---

### Post by ruibernardo on 2007-05-24
Hi Feenster,

I also wanted to do that recently, and Scponly was a solution for me. I've posted a Howto about it two days ago.

[http://ubuntuforums.org/showthread.php?t=451510&highlight=chroot](http://ubuntuforums.org/showthread.php?t=451510&highlight=chroot)

Check if this is meets your needs.

---

### Post by Frosty Cold Drink on 2007-05-24
This has been pretty much anwsered already, but I submit the following anyway.

[http://askcolddrink.blogspot.com/2007/03/how-can-i-give-someone-one-ssh-access.html](http://askcolddrink.blogspot.com/2007/03/how-can-i-give-someone-one-ssh-access.html)

Anyway, SSH is Secure SHell. If you don't like the shell part, you shouldn't be using SSH. If you want to do it anyway, there are a few SSH solutions, but there are better options, as outlined previously in this thread.

Also, see this thread: [http://ubuntuforums.org/showthread.php?t=367573](http://ubuntuforums.org/showthread.php?t=367573)

---

### Post by feenster on 2007-05-25
Hi,
Thank you for all the replies.

The more I read and think about, the more I see my situation is different, and that I may not even need to allow people SSH access at all. The only reason they have SSH access at the moment, is to send data via Rsync through the Internet (using the --rsh="ssh -p xx" command. I wonder if I could achieve the same thing by setting up the Rsync daemon to receive data? Does that sound like a better solution? I could then give my users a null shell so they couldn't login. 

Matt

---

### Post by Frosty Cold Drink on 2007-05-25
If you don't want your data flying naked, you can use stunnel ([http://www.stunnel.org/](http://www.stunnel.org/), its in universe)

---

### Post by revertex on 2007-06-02
> **Frosty Cold Drink said:**
> If you don't want your data flying naked, you can use stunnel ([http://www.stunnel.org/](http://www.stunnel.org/), its in universe)

do you known SSH?

He's asking about stop ppl look at the entire / when logged.

The only viable solution is chroot users inside their homedir.

Also you can take a look at scponly, a restricted shell that only allow remote users copy files, and can lock users with chroot.

[http://ubuntuforums.org/showthread.php?p=2765654#post2765654](http://ubuntuforums.org/showthread.php?p=2765654#post2765654)

---

