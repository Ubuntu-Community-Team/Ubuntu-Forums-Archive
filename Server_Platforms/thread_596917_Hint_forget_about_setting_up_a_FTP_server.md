---
title: "Hint: forget about setting up a FTP server"
date: 2007-10-30
forum: Server Platforms
---

### Post by Badbunny on 2007-10-30
Contrary to my usual posting profile (which consists of asking ill-defined questions and misunderstanding the answers) I'll offer a little piece of information I recently acquired:

**Do not set up a FTP server. Use SSH instead.**

I know that has been said over and over, but I didn't take the advice as I had used FTP before, and hence thought it would be easier to set up. Also, I thought SSH was command-line only. So I proceeded to bang my head against a brick wall for two weeks, trying to set up a FTP server (vsftpd) running with SSL. Two days after I succeeded, I thought I'd give SSH a try. 

It took me ten minutes with [these instructions]("https://help.ubuntu.com/community/SSHHowto"). So please, for the sake of whatever you hold sacred, don't do as I did. It is easy, a badly trained ape could do it. A badly trained ape just did.

---

### Post by MrFSL on 2007-10-30
A co-worker just approached me with the exact same question.

"How to I get my ftp server working..."

Funny enough I told him to use sftp or scp with ssh. More secure, easier setup, etc.

Seriously, for all those people setting up Windows/Samba shares, or any other file transfer system - don't rule out ssh. It is always my first choice.

---

### Post by HermanAB on 2007-10-30
There is nothing wrong with FTP.  Each solution has its place. For example, FTP is designed to be very efficient and provide a large download capacity without taxing a server, by reversing most of the computational load to the clients.  It also provides controlled anonymous access.  

FTP is often called insecure, which is not quite true.  FTP is not *private*.  Security is a different thing.  FTP allows you to have a high capacity, secure, public file server.

If you have trouble with FTP, try FileZilla.

I agree that SSH is usually easier to set up on Linux, since on most Linux systems it is installed by default and hence you don't have to do anything - unfortunaltely Ubuntu is the exception!  So, if you use Ubuntu, then you have double the trouble since first it is not installed by default and second, installing Cygwin on Windows is not easy either.

---

### Post by MJN on 2007-10-30
You don't need Cygwin - there are many really good native SSH and SCP/SFTP clients for Windows (indeed arguably better than the Linux counterparts).

The main problem with FTP is firewalls/NATs and the consequence this has on the use of the data port.

You're right, it has got its place but if you can avoid it you are wise to do so. That's not to say it can't be done but it is all-too-often a right pain (I think we've had an FTP question every day this week on here!) and just when you think you've nailed it you end up facing a subtly different usage scenario (e.g. change of client, low MTU path, NAT and double-NAT etc) which mucks it all up again. There are other drawbacks too even when you do have it working such as no file attributes, no checksumming etc etc. It's naff! ;)

Mathew

---

### Post by MrFSL on 2007-10-30
I agree every application has it use and place. - However, if you take what I must assume to be the majority of users that utilize this forum - their file transfer needs are not going to be so great as to warrant concern about "computational load."

> Cygwin on Windows is not easy either.

Cygwin is unnecessary as there are already precompiled ssh packages. Must notably is the free standalone binary called winscp. Which gives the novice user a file browser looking interface.

> FTP is often called insecure, which is not quite true. FTP is not *private*.

FTP password transactions are not secure by default. FTP file transactions are not encrypted by default. This is not so much a public verses private debate.

---

### Post by HermanAB on 2007-10-30
If you wish to run an X Server on Windoze, then you need either Cygwin or Xming.  Clients are useless without a server somewhere and Ubuntu doesnt install sshd by default.

---

### Post by MJN on 2007-10-30
Err... Who said anything about X servers? We're talking about FTP servers!

(the clue is in the title... ;))

Mathew

---

### Post by MJN on 2007-10-30
<snipped double post>

---

### Post by James79 on 2007-10-30
Two things I wished openssh would have out of the box which many FTP servers do:

- "chroot jails"
- multiple failed logins = IP blacklisting

Previous to using Ubuntu as my server OS, I had run WinSSHD for a little while. I had both of those built in and was simple to setup.

I know there are 3rd party scripts to analyse log files and modify /etc/hosts.deny accordingly, but that seems a little gimmicky to me. The chroot jails I've seen described appear equally so.

My server is private and hence these aren't really problems. But they would be nice to have built in. I'm surprised that they aren't.

---

### Post by netlogic on 2007-10-30
Hello Strange Ubuntu People...
Do spending too much time on computers make us strange? It made me wonder today.
 
Anyway, FTPd can be very useful, because it is a very low resource application. They are great for anonymous FTP. It is lighter than the HTTP download on the server. However, we know the authentication in FTP has  history of faults. The good rule is if the security of content is important, use SSH. Always, use FTP server for making anonymous downloads. They are both very useful tools.

> 
 You don't need Cygwin - there are many really good native SSH and SCP/SFTP clients for Windows (indeed arguably better than the Linux counterparts).

True... Copsshd is one click. It generates the keys and runs the whole thing as a service.

> 
Two things I wished openssh would have out of the box which many FTP servers do:

- "chroot jails"
- multiple failed logins = IP blacklisting

here is how to chroot with ssh
[http://www.howtoforge.com/chrooted_ssh_howto_debian](http://www.howtoforge.com/chrooted_ssh_howto_debian)

fail2ban works with your iptables and blacklist the failed attempts.

---

### Post by HermanAB on 2007-10-30
X servers and SSH kinda go together.  Apart from transferring files, you can run programs remotely using SSH.  So if you have sshd on Ubuntu and Xming with PuTTY on Winders, then you can launch gnome-panel from Winders and run any 'buntu app at the click of a menu button.

So, SSH gives more 'bang for your buck' than FTP.

Cheers,

Herman

---

### Post by MJN on 2007-10-31
Herman,
 
You're wandering off on a tangent here. We were talking about the comparisons between FTP and other file transfer protocols. If you're going to divert make it a little clearer to avoid confusion! Your initial mention of Cygwin had nothing to do with the topic being discussed and made it sound like you thought it was an essential requirement on a Windows machine (which it's not in case that's what you do actually think).
 
Mathew

---

### Post by James79 on 2007-10-31
> **netlogic said:**
> 
here is how to chroot with ssh
[http://www.howtoforge.com/chrooted_ssh_howto_debian](http://www.howtoforge.com/chrooted_ssh_howto_debian)

fail2ban works with your iptables and blacklist the failed attempts.

Thanks for the link/info. 

I'm aware that it is possible, but I simply wished those features could be* built-in*. It would be nice if I could put "chroot_these_users=user1,user2" directly into /etc/ssh/sshd_config. Ditto for the fail2ban functionality.

I suppose there might be a technical reason for them to be omitted.

---

### Post by Endolith on 2008-05-11
Use SSH instead of FTP??  But SSH would allow users access to my whole file system, allow them to execute commands, even forward X to their home computer.  How is that better than FTP?

I'd like to set up an FTP server so that people can access a select set of shared files (not my entire filesystem!), but it seems there is no easy way to do this securely, either.

Does anyone know of a secure method to share files across the Internet?

---

### Post by Badbunny on 2008-05-11
You can edit the permissions (both users' and directories) to prevent that.

For anonymous access, FTP could do the trick.

---

### Post by Endolith on 2008-05-11
> **Badbunny said:**
> You can edit the permissions (both users' and directories) to prevent that.

How?

> For anonymous access, FTP could do the trick.

Not for anonymous.  For at most 5 users with passwords.

---

### Post by MrFSL on 2008-05-12
> **Endolith said:**
> Use SSH instead of FTP??  But SSH would allow users access to my whole file system, allow them to execute commands, even forward X to their home computer.  How is that better than FTP?

I'd like to set up an FTP server so that people can access a select set of shared files (not my entire filesystem!), but it seems there is no easy way to do this securely, either.

Does anyone know of a secure method to share files across the Internet?

You can jail an ssh session:
[http://www.google.com/search?hl=en&q=jailed+ssh&btnG=Google+Search](http://www.google.com/search?hl=en&q=jailed+ssh&btnG=Google+Search)

---

### Post by Badbunny on 2008-05-12
> **Endolith said:**
> How?

Something like this:
[LIST]
[*]make a group "remote" (or any other name)
[*]make the remote users part of the group "remote" and remove them from group "users"
[*]make sure folders you do not want the other users to see (/home/yourname etc) are only readable to the group "users" (or even to yourself only)
[*]Edit the folders you want to share so that the group "remote" has read access to them
[*}Be very, very careful if you edit the permissions of the system folders. I see no need to do this, as any *ahem* confidential material is most likely in your home directory.
[/LIST]

The way I have this set up is:
/home/remote is where all the remote users have read and write access to. They all have their own /home/user/ -directories as well, with the usual permissions. They also have access to my and each others' public_html. No user has read access to other users' home, except the public_html. 

Hope that made sense. Depending on your desktop, there is a GUI to do all that permission and group stuff.

---

### Post by inportb on 2008-05-12
> **MrFSL said:**
> You can jail an ssh session:
[http://www.google.com/search?hl=en&q=jailed+ssh&btnG=Google+Search](http://www.google.com/search?hl=en&q=jailed+ssh&btnG=Google+Search)

Yeah, that's the preferred way. Also, check out scponly and rssh.

---

### Post by Endolith on 2008-05-12
> **MrFSL said:**
> You can jail an ssh session:
[http://www.google.com/search?hl=en&q=jailed+ssh&btnG=Google+Search](http://www.google.com/search?hl=en&q=jailed+ssh&btnG=Google+Search)

I looked into that, but the consensus seems to be that using SSH for file transfer alone is a misuse of SSH.  SSH is meant to be a secure shell for remote access, not a file transfer protocol.

[http://ubuntuforums.org/showthread.php?t=367573&page=2#11](http://ubuntuforums.org/showthread.php?t=367573&page=2#11)

---

### Post by MJN on 2008-05-12
Take a look at FTP over SSL, aka FTPS. All the benefits if simple user-containment ala traditional FTP but with the security of an encrypted transport layer. vsftpd is but one of many such FTP servers that support FTPS, and there's sure to be an SSL-compatible client for OS X too (which I'm sure you mentioned but I can't see that now!).

Mathew

---

### Post by Badbunny on 2008-05-12
That is worth looking into, if you can get it to work. I scratched my head till it bled trying to configure that one out, but it just wouldn't. I don't know if it was a firewall issue or what, but nevertheless, I gave up. SSH was a lot easier. No messing around with certificates and various ports.

Now, you all do as you want to, this was just me trying to add my two cents to the pile. Vsftpd sure seemed like a well-built software with a lot of options, a pity I never got it to work.

---

### Post by Endolith on 2008-05-15
> **MJN said:**
> Take a look at FTP over SSL, aka FTPS. All the benefits if simple user-containment ala traditional FTP but with the security of an encrypted transport layer. vsftpd is but one of many such FTP servers that support FTPS, and there's sure to be an SSL-compatible client for OS X too (which I'm sure you mentioned but I can't see that now!).

Alright I'll look into that.  OS X has Cyberduck, which is GPL and supports "FTP (File Transfer Protocol), FTP/TLS (FTP secured over SSL/TLS), SFTP (SSH Secure File Transfer), WebDAV (Web-based Distributed Authoring and Versioning) and Amazon S3."

---

### Post by Endolith on 2008-05-15
Ugh you have to configure it with a text file?  :( I don't know why so many programs depend on error-prone methods like this.

ProFTPD apparently also has a module for FTP TLS [http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-TLS.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-TLS.html) and a configuration program [http://85.214.17.244/gadmintools/index.php?option=com_content&task=view&id=15&Itemid=29](http://85.214.17.244/gadmintools/index.php?option=com_content&task=view&id=15&Itemid=29)

---

### Post by MJN on 2008-05-16
Sigh...
 
Based on your previous responses I had a niggling feeling that whatever was proposed you still wouldn't be happy... I never thought a text file configuration method would be the reason though.
 
Just crack on and have a go with it - you'll never know if you're up to it or not if you don't try. Perseverence will reap rewards, and you may well find it's not as hard or error-prone as you might think!
 
Mathew

---

### Post by Endolith on 2008-05-19
> **MJN said:**
> Sigh...
 
Based on your previous responses I had a niggling feeling that whatever was proposed you still wouldn't be happy...

Yep.  Nothing really addresses the problem.  I created a [separate thread]("http://ubuntuforums.org/showthread.php?t=795272") for it.

---

### Post by Badbunny on 2008-05-19
> **Endolith said:**
> Ugh you have to configure it with a text file?  :( I don't know why so many programs depend on error-prone methods like this.

ProFTPD apparently also has a module for FTP TLS [http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-TLS.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-TLS.html) and a configuration program [http://85.214.17.244/gadmintools/index.php?option=com_content&task=view&id=15&Itemid=29](http://85.214.17.244/gadmintools/index.php?option=com_content&task=view&id=15&Itemid=29)

Or you could install webmin, vsftpd and a webmin module for vsftp.

---

### Post by Endolith on 2008-06-25
I used PureAdmin to set up a PureFTPd server.  The admin program is a little buggy, but I got it working.  Those of you having trouble with vsftp might want to try it.  The autopackage from the website worked a little better than the Ubuntu deb, but still needed some tweaking to work.

[http://ubuntuforums.org/showthread.php?t=213266](http://ubuntuforums.org/showthread.php?t=213266)
[http://ubuntuforums.org/showthread.php?t=684590](http://ubuntuforums.org/showthread.php?t=684590)

---

### Post by Endolith on 2008-07-07
I got PureFTPd running, using PureAdmin, and I can share files by putting them in /home/ftp and then using chown to change them to user ftpuser and ftpgroup (then virtual users in the FTP setup are controlling this system user, if I understand correctly).

I would like it better if I could create links in /home/ftp that point to other places on my hard drive, some of which are read-only for the ftpuser and some of which are read/write. Is there a way to do this with symlinks? When I change the owner of the link, it doesn't give any error, but the owner hasn't changed when I use ls.

---

