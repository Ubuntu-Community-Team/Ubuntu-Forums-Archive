---
title: "browser login issue with vsfptd"
date: 2007-07-26
forum: Server Platforms
---

### Post by jimmyjam1979 on 2007-07-26
Hello all. I'm looking for a little help with VSFTPD (v2.0.5) running on Feisty Fawn. VSFTPD is running, I can login with local users (no anonymous), and can transfer files back and forth using a client like Filezila or FireFTP. However, if I try to login just using a browser and no client, I receive the infamous 500 OOPS: child died error. I've researched different forums and found suggestions like "make sure the home directory exists" or "tweak your firewall", but I have no FW at the moment and all directories do exist. And, using a client works fine.

Any suggestions are welcome. Also, I'm newer to linux. Thanks a bunch

---

### Post by Mr. C. on 2007-07-26
What is the URL you are using to login ?

MrC

---

### Post by jimmyjam1979 on 2007-07-26
[ftp://jyakunich.dyndns.org](ftp://jyakunich.dyndns.org)
Obviously, it's using dyndns. But it does the same thing when I try it with the IP address.

---

### Post by Mr. C. on 2007-07-26
That URI will attempt an anonymous login.  See your logs to convince yourself.

You need to supply a username and password, as in:

```
ftp://username:password@server
```

MrC

---

### Post by jimmyjam1979 on 2007-07-27
And...that worked! Learn something new everyday. Thanks. And I had looked at the logs and noticed the browser was attempting an anonymous login, but was confused by the fact it was still prompting for a username and password. 

Do you know if this is this specific to vsftpd? I have a little experience with Windows FTP and you don't have to do it this way. You can simply input your username/password when prompted. Just curious. Thanks again.

---

### Post by Mr. C. on 2007-07-27
It is not the server that was failing, it was the *client*, since it failed to provide the credentials. 

MrC

---

### Post by jimmyjam1979 on 2007-07-28
Totally understand what you mean by the client failing...and that is verified in the logs. I guess the thing that's confusing is that, originally, I would provide proper credentials when I was prompted, but it would still error. 

What I mean is, before your suggestion, I would simply enter the URL with out the username:password in it, and then be prompted for username/password in a seperate dialog box. I would enter credentials that I know were correct, only to have it fail. And the log indicates that an anonymous login was attempted, even though I entered a usable username and password. I'm wondering why an anonymous login was attempted if I was prompted for authentication and I used a login account that I know works? Does that make sense?

Not trying to nag...just trying to understand.

---

### Post by Mr. C. on 2007-07-28
No problem.  What client did you use to connect, and what platform?  Was it IE in Windows ?

There is a security issue you should be aware of, with connecting to an FTP server over the net. Your username and password are transmitted in clear text.

MrC

---

### Post by jimmyjam1979 on 2007-07-28
I tried IE7 and Firefox 2.0 on Windows, and Firefox 2.0 on OpenSuse 10.2. I encountered the same issue across the board. 

As for the security issue you mention...I am aware of that. Actually it is my next next goal...securing the darn thing. I just wanted to make sure it is up and running smoothly first. 

If you have any suggestions regarding security, I'm all ears. I want to change the default port vsftpd listens too from 21 to something uncommon, and look into SSL. Should I do more??

---

### Post by Mr. C. on 2007-07-29
Ok, so I've confused myself.

I seem to recall that browsers did not prompt for FTP password unless a username was present in the URL.  I'm probably mistaken as both IE 7 and Firefox 2 do.  I'm a bit embarrassed that I didn't know that, yet frankly, I've not used FTP via browser in years.  Previous versions of Firefox (prior to 1.5) failed to authenticate due to a bug.

I had no problem connecting via both browsers to a vsftpd server with local users.  So, we're back to square one with why you are unable to authenticate.

You can setup ftp over ssl, or you can even use sftp that comes with ssh.  What you decide to setup will depend on how you intend to use the server, what is most convenient for you, and what client you use.  Generally, when I have large transfers *and* I'm on a secure net, I use simple FTP transfers, avoiding the overhead of encryption.  And 99% of all transfers I do otherwise are via ssh, scp, or sftp.

Regardless, it is good to gain the knowledge of configuring some form of public key encryption, as the concepts apply in numerous services such as email, web server, ftp server, ssh, etc.

MrC

---

### Post by jimmyjam1979 on 2007-07-29
No worries man...even if we can't get it resolved, at least I've got a good work around. The only reason I want it to work via just a browser is so some family and friends can transfer/download/upload/backup files for themselves. They are much less computer savvy than I, so I'd like to keep an extra piece (a client) out of the equation. 

Would you like to see my vsftpd.conf? I don't think that's the problem, but I can post it. I wouldn't think it would be a firewall/router issue, because a client works. I'm begining to wonder if maybe my install is messed up, as it doesn't seem to be a configuration issue. 

Agreed on public key encryption..definitely plays a role in many other scenarios.

---

### Post by Mr. C. on 2007-07-29
Unfortunately, it is the scenario that you need that is the most problematic.  If you care about security, you should  assume that your friends and families PCs are infected with various forms of malware, including key loggers.  The number of infected PCs is overwhelming.

I certainly wouldn't allow plain text logins over an insecure net.

Feel free to post your vsftpd.conf file - just strip out the comments for easier reading.

MrC

---

### Post by jimmyjam1979 on 2007-07-30
You are right about security with family & friends' computers. Luckily I've taught them enough to have some virus/malware protection and tried to train on what to do and what not to do. Point taken though.

Here is my vsftpd.conf so far:

listen=YES
local_enable=YES
write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
max_clients=5
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
# This option specifies the location of the RSA key to use for SSL
# encrypted connections.
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key


If anything looks sketchy, let me know. Also, the bottom section regarding SSL caught my attention after our converstaion about it. Tell me if I'm wrong, but it looks like the Ubuntu version of vsftpd uses SSL by default, with this snakeoil.pem & .key. Another thread on these forums alluded to that, which is how I noticed it. The only thing I am not sure of is, is there a different line that I need to actually enable it, or is it enabled simply by using those two lines beginning with rsa_.....? To me, it seems like it's got the key & certificate defined (I verified that they both exist), but there is nothing instructing vsftpd to actually enable SSL. Just a guess.

Thanks for sticking with me, man.

---

### Post by Mr. C. on 2007-07-31
Sorry for the delay in responding.

The one area of concern that you should be aware of is the combination of chroot_local_user and write_enable.  This is a possible security issue.  Be sure to create empty etc, lib, usr, bin, and dev directories in each users chroot'd home.  Make those directories unwritable.  You can also use hide_file as in :

```
hide_file={bin,etc,dev,lib,usr}
```

to hide those directories (just hides, doesn't prevent their use).

Run ldd on your vsftpd daemon to see if the tls libraries are linked into your vsftpd.

Setting the config variables doesn 't enable tls; that is enabled via connecting to the correct port with a TLS-capable client.

MrC

---

### Post by jimmyjam1979 on 2007-07-31
Ok..could you explain a little bit about hiding the 5 directories in each home directory? Is that just a command, or an entry in vsftpd.conf? 

And, same goes for "Run ldd on your vsftpd daemon to see if the tls libraries are linked into your vsftpd". I'm not sure how to do that. 

Sorry, they are just a little beyond my skills up to this point. This is the best way for me to learn it though. Thanks.

---

### Post by Mr. C. on 2007-07-31
Sure, it is a vsftpd.conf variable.  Test it out.  Add it to your conf file, restart the server, and create one of the directories in your home directory.  Then, long in via ftp and note that you won't see that directory in a directory listing.  But you can CD into it.

I don't have my system up right now, and dont' recall the path the binary is in.  It is probably /usr/sbin, but may not be.  if it is, run:

```
ldd /usr/sbin/vsftpd
```

You can show the output if it does not make sense to you.  You are looking for the tls shared library.

If vsftpd is elsewhere, you can find it with :

```
locate vsftpd | less
```

look for the one in bin or sbin and then run ldd using that full path.

MrC

---

### Post by jimmyjam1979 on 2007-08-03
Sorry I haven't responded sooner. I will do as you suggested. In an effort not to drag this out much longer, I have one last scenario. I decided to start from scratch with vsftpd.conf to try and resolve my initial issue...getting the child died error trying to login just from a browser. So, I made one change at a time, restarting the daemon each time, and checked to make sure it still worked. The error returned as soon as I commented out anonymous_enable=yes and uncommented local_enable=yes. So when I disallow anonymous and allow local users, I can't log in from the browser (unless I do it the way you suggested with the username and password in the URL). 

Just wondering if a little more detail about when the error starts may shed some light. The thing is, I know this should work, but I'm not sure what I'm missing. 

Thanks again man.

---

### Post by Mr. C. on 2007-08-03
The great thing about this being your thread and issue, is that you get to respond whenever you feel like it! :-)

I had a few minutes to test your setup.

The default for vsftpd is anonymous_enable=yes, so commenting it out would be a no-op.  However, local_enable=No is the default, so your commenting out would default back to anonymous logins.

I have a similar setup that you had (anon=no, local=yes), but with some other settings, and that works just fine.  When I use your setup, I too receive the child died error.  This was caused by a non-existent chroot dir:

```
secure_chroot_dir=/var/run/vsftpd
```

Be sure that exists, and is not writable by the ftp user.

When anonymous_enable is *not* disabled, you will not be prompted for login.  When you disable anonymous_enable, the browser will prompt.  So, you want:

```
anonymous_enable=no
local_enable=yes
```

About your earlier question of enabling SSL, use:

```
ssl_enable=yes
```

MrC

---

### Post by jimmyjam1979 on 2007-08-05
Wow...I think it's working now. I successfully logged in using three different browsers (IE7, FFox, and Opera)...it prompted me for credentials...I used them...it worked...no error. It's 1:30am here, so I haven't thoroughly tested. I still need to put the rest of my settings in place from my original configuration (remember I started from scratch), but I think I'm going in the right direction. Once I get it all back together (which should be in a day or two), I'll let you know how it goes. 

One thing...how do I go about making sure the /var/run/vsftpd directory is unwritable by an ftp user?

ssl_enable=yes...got it. 

I use these kind of threads for a lot of research, but this is the first time I've actually participated. It's been a great experience so far.

---

### Post by Mr. C. on 2007-08-05
Good to hear.

```
chown root:root /var/run/vsftpd 
chmod 755 /var/run/vsftpd 

```
MrC

---

### Post by jimmyjam1979 on 2007-08-07
Ok...so, I have all my changes to vsftpd.conf in place, except for a couple minor things, and it seems to be working pretty well. Using either a browser or a client, I can log in to the server without errors and perform the tasks that I originally intended. So for now, I think I'm good...that is, until I try to get a little more ambitious with my config and end up jacking it all up;). If I have anymore questions over the next week or so, I may post again. 

Just an FYI...after this little adventure, I've realized how poor browsers can be at handling ftp traffic, but firefox is particularly bad (with passive FTP). After googling firefox ftp problems, I came across others who were having similar issues to mine. Honestly, I think it was contributing to the issues I was having, making the whole scenario that much harder to troublshoot. 

One last question...in the future, is there a way to contact you directly via these forums if I have a problem I think you may know about? I know there is a wealth of people with a wealth of knowledge on these forums, but you were extremely helpful to me and you didn't make me feel like an idiot. And as you can see, no one else chimed in with any suggestions. Just curious. And if there is a way that I could give you positive feedback regarding you help, let me know. Thanks again man.

---

### Post by Mr. C. on 2007-08-07
Glad you're up and running.

Its probably best to continue to post additional questions in the forums here, so that others can assist, and learn from the answers.  Feel free to PM me if you're not getting help, or if I don't catch your post.  There are plenty of helpful people here; sometimes it may take a bit for someone to chime in; other times responses are very quick.

Hearing that you've met your goals is thanks enough for me.

Regards,
MrC

---

### Post by WilSteele on 2007-09-14
I am also having troubles with FTP. I've tried both proftpd and vsftpd. I can't seem to login at remotely using ftp at all either with browser or client (i use Filezilla). The client seems to see my server, but won't except local user name and pword for logon or anonymous. All i seem to get is failled log on errors.

This is the first time i have run ftp on linux, usually i have it running on my windows machine, but i am moving all of  my server to ubuntu linux now.

---

