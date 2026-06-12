---
title: "I want to setup SFTP, but which software should I use?"
date: 2007-08-29
forum: Server Platforms
---

### Post by kentl on 2007-08-29
My title says it all. I want to setup SFTP for myself and 3 users.

I do not want the other people to be able to logon through SSH, I just want to provide file storage to them.

I have OpenSSH installed and it's pretty secure, with key authentication only, DenyHosts, changed port and a strong key pass phrase.

However for my SFTP users (and myself) it would be nice to logon using username and password only. I want to enforce a maximum quota per user, so that they do not fill up my HDD. It would also be good if they could not see the entire filesystem.

What do you recommend, and why? :grin:

---

### Post by timcredible on 2007-08-29
.

---

### Post by steve.horsley on 2007-08-29
Does setting their shell to /bin/false stop them gaining a shell prompt? I think it should. System->Administration-Users and Groups: edit user : advanced.

Don't know about quotas, except maybe put their homes on a separate partition.

---

### Post by kentl on 2007-08-29
Is rssh an alternative? It seems difficult to install and configure but it might give me a lot back when it's done, or?

---

### Post by HermanAB on 2007-08-29
You need the sshd daemon and gftp as the GUI.

Cheers,

Herman

---

### Post by freebeer on 2007-08-29
FWIW, I set up proftpd pretty much as you describe and administer it with gproftpd.

---

### Post by kentl on 2007-08-30
> Does setting their shell to /bin/false stop them gaining a shell prompt? I think it should. System->Administration-Users and Groups: edit user : advanced.

Don't know about quotas, except maybe put their homes on a separate partition.

I don't have Gnome, or any x server on the computer I want to act as an SFTP server. I need a command based solution, I think.

The quotas part is really very important. And doing a repartition isn't something I'm looking forward to, now that I've got a lot of other things set up fine. Also, if I need one partition per user, I'll have to repartition if I get more users later on.
> You need the sshd daemon and gftp as the GUI.
Well, I want to host an SFTP server. Isn't gftp a client? Sorry for not being clear enough. 8-[
> FWIW, I set up proftpd pretty much as you describe and administer it with gproftpd.

proftpd is something I've been having my eyes on. Perhaps it's my best choice. A new course comrade who seems to know a lot about Linux also recommended it or vsftp.

The vsftp features list seems nice: [http://vsftpd.beasts.org/#features](http://vsftpd.beasts.org/#features)

But that's also true fro proftpd: [http://www.proftpd.org/features.html](http://www.proftpd.org/features.html)

I think it sounds nice that proftpd has similar configuration files to Apache. As I will be configuring Apache soon as well. On the other hand, the "virtual users" of vsftpd seems nice. I can't see a need for a "real" user when these people will only login through SFTP to perform their work.

Comments? (You're probably all more insightful than me as this is all new to me :-) )

---

### Post by HermanAB on 2007-08-30
Vsftpd and Proftpd are similar and good quality.  A while ago, a bug in proftpd caused me to switch to vsftpd, so I can vouch for both.  You'll be happy with either one.

Cheers,

H.

---

### Post by steve.horsley on 2007-08-30
> 
[QUOTE]Does setting their shell to /bin/false stop them gaining a shell prompt? I think it should. System->Administration-Users and Groups: edit user : advanced.

Don't know about quotas, except maybe put their homes on a separate partition.
I don't have Gnome, or any x server on the computer I want to act as an SFTP server. I need a command based solution, I think.[/QUOTE]
Edit /etc/passwd and change the shell in there. Its near the end of the line, and is usuallt /bin/bash. Try changing it to /bin/false for one of your users and see if they can still get a shell - I think this will stop them.

---

### Post by kentl on 2007-10-08
> You'll be happy with either one.
Maybe I will. :-) I just wanted to tail this thread to my new thread where I have set up vsftpd. This is the continuing story, now with a decision to try vsftpd: [http://ubuntuforums.org/showthread.php?t=570717](http://ubuntuforums.org/showthread.php?t=570717)

I have no idea on how to set up quotas for the virtual users. And to be frank, the "documentation" of vsftpd is utter c--p. I'm saying that out of frustratio though, perhaps I'll feel different about it in the morning. ](*,)

---

### Post by nix4me on 2007-10-08
Here is how to do exactly what you want:
[http://www.howtoforge.com/mysecureshell_sftp_debian_etch](http://www.howtoforge.com/mysecureshell_sftp_debian_etch)

The debian instructions should work just fine.

nix4me

---

### Post by kentl on 2007-10-08
Thanks for your answer, still, things that make me not try it at the moment are:
[LIST]
[*]The entire Sourceforge web page for the project is in French. I do not speak French and would like to be able to read the manual.
[*]The English project description (one paragraph) is full of spelling and grammatical errors. I take it as a warning sign.
[*]The linked page mentions nothing about user file space quotas, which is my primary goal at the moment and absolutely necessary.
[*]I have sftpd installed and working, except for the quotas. If it's not impossible to have quotas for the users in sftpd, I'll stick with it.
[/LIST]

---

### Post by Wim Sturkenboom on 2007-10-09
I've used Miles Brennan's [Linux Home Server HOWTO - FTP server](http://www.brennan.id.au/14-FTP_Server.html) to setup my secure vsftp. It describes the setup on Fedora, but I've successfully applied it to Slackware.

*man edquota* should give sufficient info about quota setup. If not, [http://tldp.org/HOWTO/Quota.html](http://tldp.org/HOWTO/Quota.html)

---

### Post by MJN on 2007-10-09
Note however that FTP-over-SSL is not the same as SFTP so it might not suit the OP's needs (I'd suggest aiming towards SFTP given the simplicity of configuration (i.e. none!), at least for a standard out-of-the-box solution)...
 
Mathew

---

### Post by kentl on 2007-10-09
> I've used Miles Brennan's Linux Home Server HOWTO - FTP server to setup my secure vsftp. It describes the setup on Fedora, but I've successfully applied it to Slackware.
> Note however that FTP-over-SSL is not the same as SFTP so it might not suit the OP's needs (I'd suggest aiming towards SFTP given the simplicity of configuration (i.e. none!), at least for a standard out-of-the-box solution)...
I want something secure and usable from Windows as well. As I have other people who will be connecting using Windows. I think the Filezilla client supports SFTP so I'm in the clear and can use it.

> man edquota should give sufficient info about quota setup. If not, [http://tldp.org/HOWTO/Quota.html](http://tldp.org/HOWTO/Quota.html)
Well it seems that you can only assign quotas on a user-partition basis. As all my virtual users are seen as the account ftp on my system setting a quota for ftp would set a limit on the max upload for all users together. I would not have individual precision.

It could be a solution though. If I create a real user account for each of my virtual users. Map real account with virtual account in the individual user set up and enforce quota on the real account. But if I have one real account per user, why am I then using virtual accounts? :-)

I hope that there is something else I can do to enforce quotas on a per-user basis when I use virtual users with vsftpd. If there isn't I guess I'm using the wrong software for my needs. :/

---

### Post by MJN on 2007-10-09
I think there may be still some confusion here:
 
> **kentl said:**
> I think the Filezilla client supports SFTP so I'm in the clear and can use it.
 
[quote=kentl]I hope that there is something else I can do to enforce quotas on a per-user basis when I use virtual users with vsftpd. If there isn't I guess I'm using the wrong software for my needs. :/[/quote]
 
VSFTP only supports FTP, not SFTP hence you need to make that distinction now and decide in which direction you wish to travel - FTP or SFTP (to me there's no contest).
 
If you're only talking about supporting 3 users then you could adopt an otherwise-unscalable solution - _give them their own partition_, mount it as their /home/~ then you've got automatic quota limitations (Edit: Just noticed Steve has mentioned this already - oh well 'great minds' and all that!). Using the SFTP sub-system of OpenSSH they can access the server using a variety of SFTP clients as already discussed.
 
Your other requirement of only allowing SFTP access (no shell access) is not something I'm familiar with however I did stumble across a couple of articules discussing exactly this issue: [http://www.debian-administration.org/articles/94](http://www.debian-administration.org/articles/94) and [http://www.minstrel.org.uk/papers/sftp/](http://www.minstrel.org.uk/papers/sftp/) Note however that I'm sure this is one of those requirements that can have multiple, totally different, solutions so I'd look around for whatever may suit your needs (particularly simplicity) best.
 
Mathew
 
Edit: have you searched for user-related quota solutions? A quick Google search found [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch28_:_Managing_Disk_Usage_with_Quotas](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch28_:_Managing_Disk_Usage_with_Quotas) which sounds like exactly what you're after?

---

### Post by kentl on 2007-10-09
> I've used Miles Brennan's Linux Home Server HOWTO - FTP server to setup my secure vsftp. It describ[es the setup on Fedora, but I've successfully applied it to Slackware.
man edquota should give sufficient info about quota setup. If not, [http://tldp.org/HOWTO/Quota.html](http://tldp.org/HOWTO/Quota.html)
Well I have a running system already. So the first link might be good but as it mentions nothing about quotas I don't think it will help me. The other explains quotas. But as all virtual users use the real account named ftp I can only use it to put a maximum on the total file storage by all virtual users, which isn't what I'm looking for.

> VSFTP only supports FTP, not SFTP hence you need to make that distinction now and decide in which direction you wish to travel - FTP or SFTP (to me there's no contest).
So maybe I should skip vsftpd, it can't handle hard quotas in itself and I absolutely want them.
> If you're only talking about supporting 3 users then you could adopt an otherwise-unscalable solution - give them their own partition
I've mentioned it to, and I don't want to have to create partitions for each user. I want something scalable.

> Using the SFTP sub-system of OpenSSH they can access the server using a variety of SFTP clients as already discussed.
Does it have some kind of hard quota feature? I looked around earlier and I didn't find much information about setting up FTP using OpenSSH, do you have any good links you recommend?

> Your other requirement of only allowing SFTP access (no shell access) is not something I'm familiar with however I did stumble across a couple of articules discussing exactly this issue: [http://www.debian-administration.org/articles/94](http://www.debian-administration.org/articles/94) and [http://www.minstrel.org.uk/papers/sftp/](http://www.minstrel.org.uk/papers/sftp/) Note however that I'm sure this is one of those requirements that can have multiple, totally different, solutions so I'd look around for whatever may suit your needs (particularly simplicity) best.
I'll read them, thanks! :-)

> Edit: have you searched for user-related quota solutions? A quick Google search found [http://www.linuxhomenetworking.com/w...ge_with_Quotas](http://www.linuxhomenetworking.com/w...ge_with_Quotas) which sounds like exactly what you're after?
I read it. Unfortunately it works the way I thought, I've read a bit about quotas earlier. In my case I have virtual users using vsftpd, they all use the ftp account on the system. By setting a quota for the ftp account I can put a limit on the maximum upload of all users. But not on individual virtual users.

---

### Post by MJN on 2007-10-09
Phew - nice bit of quoting there! ;)

To be honest, it sounds to me like you've probably got more than enough options on your plate and short of someone coming along and relaying exactly how they're already achieving what you want to do you'll probably have to take stock and decide how to continue. Indeed, I can't help but feel that any involvement with 'standard' FTP (using VSFTPD), and virtual users in particular, is doing little more than clouding the issue and restricting your options.

To me, the simplest (and hopefully most effective) solution to your requirements would be to have 'proper' user accounts for these 3 people and separate your requirements out in to three disparate areas - file transfer, access control and storage quotas.

For file transfer using the SFTP sub-system of openssh-server has got to be the simplest, and most secure, solution. It is enabled by default[1] I believe (see /etc/ssh/sshd_config). Having quickly scanned the sshd manpage it looks like SFTP is not that much configurable in itself - which I take to be a good thing as it means it'll work, safely and securely, out of the box!

Access control (SFTP-only) will need some further investigation but it sounds from the couple of links above that this is totally achievable - it's just a matter of how and which way you prefer.

Quotas, again, seem to be doable - at the file system level - it doesn't sound like there's any need to perform this function at the higher level (S/FTP etc).

This may sound like a long way of saying '*Google for it*' but that's not intentional - I just think the VSFTPD work so far has sent you down a rabbit hole to which there may well be a solution at the end but in what form I don't know. Hence, I think it preferable if you modularise the solutions - at least get the SFTP access working first - then you can overlay imposing access restrictions, and quotas, on top.

Just my 2p worth, and probably somewhat overpriced at that!

Mathew

[1] Try accessing your server on port 22 with an SFTP client - I bet you're running an SFTP server already without realising it!

---

### Post by kentl on 2007-10-09
Well I already have my system partitioned and giving the users the ability to log in through SSH is really not something I intended. Still, if there is no other solution that's what I'll have to do. I'll research some more and come back to this thread.

---

### Post by MJN on 2007-10-09
Yeah it'd be good to hear how you get on as I'm sure your requirements would be echoed by many others - speaking of which I'm surprised noone has come forward with a turnkey solution/HowTo (I'm sure they will just as you've sweated blood for weeks working it out for yourself!).

Mathew

---

### Post by MJN on 2007-10-09
One more thing before I go - here's a guide for implementing per-user quotas using the **quota** package:

[http://itmission.org/Main/SettingUpQuotas](http://itmission.org/Main/SettingUpQuotas)

Looks simple enough?

Now you just need to find out how to stop shell access! :)

Mathew

P.S. Did you try an SFTP connection?

---

### Post by Brazen on 2007-10-09
> **kentl said:**
> Well I already have my system partitioned and giving the users the ability to log in through SSH is really not something I intended. Still, if there is no other solution that's what I'll have to do. I'll research some more and come back to this thread.

scponly is the program you are looking for.  It is a wrapper to openssh and will deny users from getting shell access and you can chroot users into a directory.  So, they can only access file transfers (using either the new Filezilla client or WinSCP) and they don't have file access to your entire system like the standard openssh server gives.

Another option, if you only want to deny shell access and not chroot them into a directory, would be to open /etc/passwd and change /bin/bash for the users to /bin/nologon

---

### Post by Wim Sturkenboom on 2007-10-10
> **kentl said:**
> I want something secure and usable from Windows as well. As I have other people who will be connecting using Windows. I think the Filezilla client supports SFTP so I'm in the clear and can use it.
I use a vsftp server and connect using Filezilla from windows. The filezilla setup uses FTP over SSL with explicite encryption).

> **kentl said:**
> Well it seems that you can only assign quotas on a user-partition basis. As all my virtual users are seen as the account ftp on my system setting a quota for ftp would set a limit on the max upload for all users together. I would not have individual precision.
There are two things I don't understand; maybe someone can explain it to me so I can learn from this thread.

The need for a partition per user (if I 'translate' that correctly from your post)  does not make sense (in my opinion). If a user has a partition, the user will never be able to exceed the size of that partition and hence the 'quota' is already set. Further it would not be a flexible solution.
*[COLOR="Red"]So I'm missing something here[/COLOR]*

And I'm sorry, but *[COLOR="Red"]what is a virtual user[/COLOR]* :oops: I ignored 'virtual' as I assumed you were talking about a normal user.

---

### Post by MJN on 2007-10-10
I think we're in need of some clarification here regarding the quota package. It does **not** require a partition-per-user. The partition-per-user discussion was a merely a simple, albeit crude, suggested method for limiting user storage space. Ignore that now - and take a look at quota as it really is a per-user quota system (the only partition-related aspect is the fact that the partition that it is to be used on must be mounted in a fashion that allows quota to do its stuff and intervene when space is consumed).
 
The concept of FTP virtual users is simply that users have an FTP account, but nothing else. Specifically, they don't have a 'real' system account on the host machine (just storage space and means to access it via FTP).
 
Mathew

---

### Post by kentl on 2007-10-10
I wrote user-partition basis as you can't set a quota for directories, only whole partitions.

As FTP users using the setup I've had with vsftpd are virtual, that is, simulated by vsftpd (which in turn uses PAM for that) you can't set any quotas on them. As these virtual users need a way of reading and writing to the disk they must be associated with a real user account. For this the ftp account was created. If I would have set a quota for the ftp account it would only have controlled the total amount of stored information for all my virtual ftp users. When in reality I wanted to control this individually.

---

### Post by kentl on 2007-10-10
I've looked at scponly and creating a nice SFTP solution. I've decided to hold that off into the future for now and try out [Pro FTPd]("http://www.proftpd.org/features.html") instead. It seems really easy which I think is nice.

From what I've read about quotas I'll might need to recompile my kernel and configure some more stuff. And I really have spent far too much time on this ATM. :-)

Thanks for your help though! It wasn't wasted. I'll use scponly to setup an SFTP solution when time allows. And I'm sure others will find parts of this thread useful as well. For the time being, I'll leave this thread. But by all means, keep the discussion going. :) Thanks!

---

### Post by Brazen on 2007-10-10
Yes, quotas will not work well with virtual users.  But I don't see any reason not to use regular user accounts for your ftp access.  The only reason for virtual users is if you want them to log in to ftp as one user but be seen by the system as another user, which it seems like you would particularly NOT want this, so don't use virtual users.

---

### Post by Wim Sturkenboom on 2007-10-10
@MJN, thanks for clarifying that.

Is there any advantage in virtual users above normal user accounts without a shell?

---

### Post by kentl on 2007-10-10
> Is there any advantage in virtual users above normal user accounts without a shell?
If you want to provide normal FTP it might be. If you have a virtual user the worst thing that can happen is that the files in the chrooted jail (if you use such) gets compromised. On the other hand, if a normal user account with privileges gets compromised, more harm can be done.

---

### Post by Brazen on 2007-10-10
> **kentl said:**
> If you want to provide normal FTP it might be. If you have a virtual user the worst thing that can happen is that the files in the chrooted jail (if you use such) gets compromised. On the other hand, if a normal user account with privileges gets compromised, more harm can be done.

There is really nothing preventing a virtual user from causing as much corruption or finding any exploit that a normal user would since a virtual user gets the same privileges on the system as the normal user it is defined as.

---

### Post by kentl on 2007-10-10
Brazen: Well not everyone agree with you on that. By having all virtual users tied to one real account some reason that it's easier to secure. Like 
 [http://www.debiansec.com/linux/services/ftp.html#introduction](http://www.debiansec.com/linux/services/ftp.html#introduction)

---

### Post by Wim Sturkenboom on 2007-10-11
Thanks for the explanations and the link.

---

