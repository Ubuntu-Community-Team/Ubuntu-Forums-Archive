---
title: "SSH and Pure-FTPD virtual users"
date: 2008-07-23
forum: Security
---

### Post by generatorlabs on 2008-07-23
OK please excuse newb stance here. I have been living in the matrix with windows as the OS. Thank god it crashed!

Anyway here I go: I isuccessfully installed Pure-FTPD with virtual users. I created a few virtual users and tested funtionality on the local network. All was OK. Then i scoured the web for TLS and or SSH implementation. I sucessfully installed ssh (tested with loacalhost ok) but I could not get ssh to work. I tried using TLS and I beleive I got that to work with Filezilla as my client. I enabled the -Y 2 switch on Pure-FTPD and it appeared to be working. So for the most part I feel good about my progress because I have Zero experience with linux.

Now my real goal is to get SFTP to work over SSH. I have followed the directives of many web posts but have had little success. I can accomplish this though:

I can log into the FTP server with the SFTP option in Filezilla if I log in as my administrator account. I cannot log into the FTP as one of the virtual users. I have created (or so I think) "real" parallel user accounts with limited access. The accounts are set up to use FALSE shell and parts of a common FTPGroup. The users have limited IP priveledges and are supposed to be funneled thru the localhost if they dont have a valid shell.

Why can my admin account use the ssh tunnel? How can I tell if I am actually using SSH? Is my admin account somehow bypassing it? Filezilla does not specifically say that a SSH session has occured although I do have SFTP checked as the login option.

If there is anyone that can help me past this hurdle I would appreciate it immensely. I have faith this is a great OS with a newb trying to do advanced things beyond his understanding. At this point my lack of experience has got the best of me. I am even willing to pay someone a few bucks for some one-on-one e-mail support or phone support. Can't afford much though. My job will not reimburse me for this. Thanks for the help!

---

### Post by cdenley on 2008-07-23
SFTP is completely seperate from FTP, and has nothing to do with Pure-FTPD or your virtual users. I don't think you can use ssh with anything besides your local user accounts. If you want to restrict shell access for users using sftp, use scponly. If you want encrypted file transfers with your virtual users, configure your FTP server to support SSL encryption.

---

### Post by generatorlabs on 2008-07-23
Thanks for the reply:

So my ultimate goal is to securely connect to my FTP server. I have SSH installed. I can use SSH locally. 

How do I configure Pure-FTPD to use it? The users who will use this will almost never be on the local network. I only see a -Y switch in the Pure-FTPD docs. This switch is for enabling TLS. I see no switches or reference to SSH. 

I see a option for PAMAuthentication but I don't really understand what that switch is for. I have it set to off for now.

Am I to understand that virtual users with parallel real accounts cannot use ssh when at a remote location?

How would you do it? Should I scrap the idea of virtual users?
I only cling to the idea of virtual users because of they security concerns posted by so many others. 

Thnaks

---

### Post by flygy6 on 2008-07-23
ssh uses pam authentication.  So does sftp.  sftp encrypts data and pure-ftpd with tls/ssl encrypts the authentication session only.  sftp encrypts the data as well as the authentication session.  Any virtual users created will only work with pure-ftpd.  If you want to use the same users for sftp and pure-ftpd enable PAM on pure-ftpd and create users in the system with useradd or adduser.

---

### Post by cdenley on 2008-07-23
SFTP has nothing to do with FTP!

Pure-FTPD has nothing to do with your ssh server. Pure-FTPD will not accept ssh/sftp connections. If you want to use encryption with Pure-FTPD, you will need to enable SSL/TLS and connect with FTPS or FTPES. If you want to connect with SFTP (SSH), then you can only connect to sshd. If you only want to accept SFTP connections, remove Pure-FTPD since it only seems to be confusing you. All you need for an SFTP server is openssh-server (sshd). As far as I know, it will only use local users (PAM authentication).

---

### Post by flygy6 on 2008-07-23
Using a restricted shell such as rssh or scponly as the specific user's shell will prevent them from having access to another shell that can execute commands such as bash or sh.  This should provide security for you.  Note that if you choose to not use pure-ftpd you will have to manually configure a chroot jail if you are interested in confining users to certain portions of the filesystem.

---

### Post by generatorlabs on 2008-07-23
Thank you so much!!...like I said I am a total newb to this.....

I think I understand much better.

OK, so I don't really need Pure-FTPD to be able to share files with my co-workers. I could scrap Pure-FTPD, enable local users with appropriate rights/permisions and they could log in as though they were on the local network but they are in remote locations. They would be able to browse the network folders etc. but would be limited to what they could do to those folders by the rights assigned. I can use Filezilla to engage either a FTP sesion or a SSH session by selecting the appropriate interface.

Do I seem to have this right?


Is there a downfall to using this approach rather than using FTP over TLS? For the most part the users logging in will be trusted so I am not too concerned with rogue activity. I am concerned about the traffic and passwords passing thru the net. Some of the traffic should be shielded from prying eyes. From my perspective the FTP option seems to be set up for allowing non-trusted sources the ability to engage with a network and get/send pre-defined files. 

I really appreciate guys/gals like yourselves who spend the time answering dumb questions like this. I only hope someday I could be the guy on the other side of the question.

I wait anxiously to see if I am on the right track. Thanks for the responses.

---

### Post by flygy6 on 2008-07-23
It sounds like you are on the right track now.  The only down side (which is hardly a down side) to using sftp instead of ftp is that all data will be encrypted instead of just some of the data, and this will create some added overhead.  

Good Night and Good Luck,
flygy6

---

