---
title: "The server is back up!"
date: 2009-08-21
forum: The Cafe
---

### Post by dragos240 on 2009-08-21
Feel free to drop by and leave a message via ssh. You can use vi, echo, or nano.

Server: 24.34.53.70
Port: 22 ( I might change )
Guest user: ubuntuforums
Password: ubuntu

I have upgraded to the latest kernel, and also I have limited each user to 40 applications. So fork bombing won't work. Also any seggestions would be appreciated. :popcorn:

---

### Post by hessiess on 2009-08-21
If you are going to alow random people to log into your server, then you rilly should chroot the environment and limit the commands people can use to just `vi echo and nano', for example `df, ifconfig, lspci, svn...' can all be used currently.

---

### Post by dragos240 on 2009-08-21
> **hessiess said:**
> If you are going to alow random people to log into your server, then you rilly should chroot the environment and limit the commands people can use to just `vi echo and nano', for example `df, ifconfig, lspci, svn...' can all be used currently.

Hmm..... could that be configured in:
/etc/security/limits.conf?

---

### Post by hessiess on 2009-08-21
> **dragos240 said:**
> Hmm..... could that be configured in:
/etc/security/limits.conf?

not sure, but there is information about setting up a chrooted ssh server here: [http://www.howtoforge.com/chrooted_ssh_howto_debian](http://www.howtoforge.com/chrooted_ssh_howto_debian).

Also, gcc and g++ are available, so your server could be exploited for compiling software.

---

### Post by dragos240 on 2009-08-21
But..... I don't use debian, for this server. I use arch!

---

### Post by hessiess on 2009-08-21
> **dragos240 said:**
> But..... I don't use debian, for this server. I use arch!
there is a page on the arch wiki: [http://wiki.archlinux.org/index.php/Openssh-chroot](http://wiki.archlinux.org/index.php/Openssh-chroot)

---

### Post by dragos240 on 2009-08-21
Sadly that package does not exist anymore.

---

### Post by hessiess on 2009-08-21
> **dragos240 said:**
> Sadly that package does not exist anymore.

Thats annoying, if the package does not exist, someone should take the wiki page down. have you asked about it on the Arch forum?

---

### Post by dragos240 on 2009-08-21
Will do.

---

### Post by lukjad on 2009-08-21
Pity, but I am on Windows right now :(

---

### Post by Bachstelze on 2009-08-21
> **lukjad007 said:**
> Pity, but I am on Windows right now :(

So am I. Do you not know about putty?

---

### Post by dragos240 on 2009-08-21
> **lukjad007 said:**
> Pity, but I am on Windows right now :(

That is a pitty...... that you don't know about putty........

EDIT: Hymn, you beat me!

---

### Post by BbUiDgZ on 2009-08-21
> **dragos240 said:**
> That is a pitty...... that you don't know about putty........

EDIT: Hymn, you beat me!

sshsecureshellclient is better imo
[http://www.filewatcher.com/m/SSHSecureShellClient-3.2.9.exe.5517312.0.0.html](http://www.filewatcher.com/m/SSHSecureShellClient-3.2.9.exe.5517312.0.0.html)

---

### Post by Mighty_Joe on 2009-08-21
> **BbUiDgZ said:**
> sshsecureshellclient is better imo
[http://www.filewatcher.com/m/SSHSecureShellClient-3.2.9.exe.5517312.0.0.html](http://www.filewatcher.com/m/SSHSecureShellClient-3.2.9.exe.5517312.0.0.html)

Is that being maintained any more?  I used to use it but my impression is that SSH Communications Security Corp. pretty much abandoned it in 2003 to concentrate on their cash cows.  I recall it had some pretty restrictive license terms too.
Personally, I use [Cygwin]("http://www.cygwin.com/") and OpenSSH.

---

### Post by .Maleficus. on 2009-08-21
[quote=README]Remember, I have a log.[/quote]
*shat bricks*

Well, at least it wouldn't let me cd into the "harley" folder.

..but it would let me cd into "/".  And run "lspci".  I'd either take down your login info from the OP or hurry up getting the chroot setup.  Remember, not everyone who browses the forums is a member.


Edit:  Phew, and ubuntuforums isn't in /etc/sudoers.  That's good too (I figured you probably wouldn't do that but I had to check ;)).

---

### Post by TuckLive on 2009-08-21
I left a message under /home/ubuntuforums/TuckLive  :lolflag:

---

### Post by dragos240 on 2009-08-21
> **.Maleficus. said:**
> *shat bricks*

Well, at least it wouldn't let me cd into the "harley" folder.

..but it would let me cd into "/".  And run "lspci".  I'd either take down your login info from the OP or hurry up getting the chroot setup.  Remember, not everyone who browses the forums is a member.

Wait, so if you wanted to, you could get my password? Well.... anyways I am trying.

---

### Post by dragos240 on 2009-08-21
Also I will be shutting down the sshd server for a little while to get the chroot working.

---

### Post by JohnFH on 2009-08-21
I can't login.  Is it still running?

I can ping it but ssh is not accepting the details you gave.

---

### Post by chris200x9 on 2009-08-21
lolololol I scp'd you ASCII porn lolololol

---

### Post by .Maleficus. on 2009-08-21
> **dragos240 said:**
> Wait, so if you wanted to, you could get my password? Well.... anyways I am trying.
Could I get your password?  No, I'm not that skilled.  Does that mean somebody else here couldn't?  Nope, doesn't mean that either.

I think this was already linked to ([http://www.howtoforge.com/chroot_ssh_sftp_debian_etch](http://www.howtoforge.com/chroot_ssh_sftp_debian_etch)) but I'd take a read through that and set it up that way.  There's nothing Debian specific so if you just follow the steps carefully you should be fine.

---

### Post by dragos240 on 2009-08-21
> **JohnFH said:**
> I can't login.  Is it still running?

I can ping it but ssh is not accepting the details you gave.

No it isn't. I am working on chroot.

---

### Post by dragos240 on 2009-08-21
> **.Maleficus. said:**
> Could I get your password?  No, I'm not that skilled.  Does that mean somebody else here couldn't?  Nope, doesn't mean that either.

I think this was already linked to ([http://www.howtoforge.com/chroot_ssh_sftp_debian_etch](http://www.howtoforge.com/chroot_ssh_sftp_debian_etch)) but I'd take a read through that and set it up that way.  There's nothing Debian specific so if you just follow the steps carefully you should be fine.

I can't do that either, as the chroot patch for openssh is now nonexitant, there are no downloads for it on the sourceforge page. :(

---

### Post by v8YKxgHe on 2009-08-21
In later/recent versions of SSH, there is a 'ChrootDirectory' option you can use in your SSHd config file (/etc/ssh/sshd_config). There is no need to patch SSH.

See manpage for 'sshd_config'.

---

### Post by hessiess on 2009-08-21
> **dragos240 said:**
> Wait, so if you wanted to, you could get my password? Well.... anyways I am trying.

Wouldn't be possible, the passwords are stored in /etc/shadow, which can only be viewed by root, and even if you could read it, it wouldn't help as the passwords are hashed, unless a bad has algorithm is used the only way to get the password would be a brute force attack, which would be imposable in a reasonable time frame if the password is sufficiently long and random.

---

### Post by Regenweald on 2009-08-21
By the time this thread is of age, dragos240 you are going to be a damn good server admin. I'll set up one of my own one of these days, BSD though :)

---

### Post by dragos240 on 2009-08-21
> **Regenweald said:**
> By the time this thread is of age, dragos240 you are going to be a damn good server admin. I'll set up one of my own one of these days, BSD though :)

Right now, not so much. Look at my post "Incorrect permission(s) blues :("

---

### Post by schauerlich on 2009-08-21
> **dragos240 said:**
> Right now, not so much. Look at my post "Incorrect permission(s) blues :("

Is it up yet?

(twss)

---

### Post by Regenweald on 2009-08-21
> **dragos240 said:**
> Right now, not so much. Look at my post "Incorrect permission(s) blues :("

Whatever man :) the fun is in the learning....you'll get there

---

### Post by dragos240 on 2009-08-21
> **EDavidBurg said:**
> Is it up yet?

(twss)

The cake (title) is a lie.

---

