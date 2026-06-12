---
title: "ftp_scanner attack"
date: 2007-12-18
forum: Server Platforms
---

### Post by mjpolifka on 2007-12-18
This post is meant as a warning to the community.  I don't believe this "virus" caused any damage to my system, nor is it very powerful (I just haven't made a very good IPTABLES script because the one I had didn't work so I sort of gave up).

A program called ftp_scanner was installed on one of my unused users' home directories in a directory called FBISRI.  It proceeded to spawn about 20 processes of ftp_scanner, slowing my server to a crawl (making it especially difficult to remove).  I deleted the user, changed every password on my system, and changed the permissions of the directory to nobody:nogroup and 000.  I haven't deleted anything because I wanted to read the bash scripts to see what it was doing.

What I do know is that there is a file called pass with a bunch of dictionary passwords, and that I've recieved e-mails (my address is on my web server) complaining of attempted ftp access (user Administrator) from my IP address.

A few things I want to know:
I have no user called Administrator.  Is that an alias for root?  My root password was on the list (it wasn't completely dictionary, they added numbers, etc.) so I want to know if that could have been compromised.  I have changed my root password to something not on the list.  On that same note, how would I know if my system has been compromised?  How, using the command line, do i see what files have been added, deleted, or modified?  I have to do this whole thing over ssh because I've gone home for winter break and the server is a few hundred miles away.  My other option would be to shut it down until I return, but I'd rather not do that.

I am very new when it comes to security, if there's anything I need to do, any reports I should file, etc. please tell me what to do.  I'm not particularly worried, just interested in what you all think.  Worst case in my mind is I have to reinstall my OS, which takes all of a half hour.  Also, if anyone wants the scripts and binaries let me know, you can probably make more sense of them than I can.

---

### Post by koenn on 2007-12-18
your server has been compromised.

From your account of the events, I gather
- someone managed to install a program on it (ftp_scanner),, and
- has been using that program to find ftp servers on the internet, then
- try to break in to them as user "administrator" and a password list
(so presumably they were targetting Windows servers, and used yours for the attack so any traces would lead to you, not 'them'.

On first sight, seeing that the installed in a user home directory, you might assume the impact is limited - but there's no way of knowing. Your root password may have been on that list by coincidence, maybe not. You can only check file time stamps fto find possible modifications. A rootkit hunter might work, I don't know. 

Reinstalling would probably be a good idea. 

And running a server without a firewall because you couldn't figure out iptables is kinda ... dumb?

oh, and yes, i wouldn't mind having a look a those scripts

---

### Post by mjpolifka on 2007-12-18
dumb is a good word.  But considering it's just media and we were just messing around, I didn't think too much of it.  Even now that I've been attacked and likely compromised, the impact is essentially null.

The thing is that he didn't actually install a program, just wrote some files.  Most of the files are either ASCII or Bash files, only two were C programs and they were compiled in a directory to which they had access without root privleges (I probably shouldn't have had a compiler installed in a server, especially since I don't even use it, only apt).  From the seemingly bash nature of it, I wouldn't think he was targeting windows machines.  But the scripts could just be a small part of what's actually going on, I'll find out later when I read them.

I haven't looked at the script, but if it tried to access my machine with the "administrator" user, would it be able to gain root access or not?

I'll link the files to my apache folder tonight and post a link so you can look at them.  I think I'll reinstall when i get back to school, using server edition this time since I'm not using almost any of the programs that came with the regular Ubuntu install.  I'll also read some more how-to's for IPTABLES, lol.

---

### Post by koenn on 2007-12-18
> **mjpolifka said:**
> the impact is essentially null.
I'm pretty sure your server was used to attack** other servers.** You have no way of knowing whether those attacks were succesful or not. What if they were ? Would the admins/owners of those servers also consider this a harmless event?
Add to that that the attacks (to those other servers) originated from *your* server - you're quite sure you can't be held (partially) responsible, legally ? 


> **mjpolifka said:**
> 
From the seemingly bash nature of it, I wouldn't think he was targeting windows machines.  
Think about it : it's not hard to write a bash script that tries to log on to a Windows File sharing server. It's not at all hard to connect to a Windows  FTP server with a Linux client, even a command line client (and bash scripts are just commands). And programs on a Linux host can access services on Windows servers without problem. Your web browser is probably doing it al the time. 

> **mjpolifka said:**
> but if it tried to access my machine with the "administrator" user, would it be able to gain root access or not?

Only if there is a user account 'Administrator' (which you say there isn't). 'Administrator' would fail to authenticate, so no access.
But then again, your server was not the target - they already could do with it  what they needed to : run programs to attack other servers.

---

### Post by mjpolifka on 2007-12-18
That is a good point.  While I agree with you, and do not offer this as an excuse but simply food for thought, i would bring up the following counter-point:  Wouldn't those servers have been hacked anyway, given time?  Whether from the original scripter or from another server which failed to have a firewall, I don't believe I actually caused any damage that wouldn't have been caused otherwise.

That being said, no more running my server without a firewall.

The folder that was on my computer is up on my webserver.  Unfortunately I can't link it due to the profanity filter, lol.  The page is [http://mitchandjay.kicks-***.net/FBISRI](http://mitchandjay.kicks-***.net/FBISRI)

---

### Post by PetePete on 2007-12-18
any idea how they got access?
to my understanding you can run a server without a firewall, just as long as  the ports that are open are fully patched/up-to-date.

you running any php scripts maybe?

---

### Post by stmurray on 2007-12-18
> That is a good point. While I agree with you, and do not offer this as an excuse but simply food for thought, i would bring up the following counter-point: Wouldn't those servers have been hacked anyway, given time?

The point is that if the attacker used you to attack an FTP site that somebody REALLY cared about (like one that was owned by the FBI, CIA, NSA, etc), and the owner of the site investigated, then they would come knocking on your door.  You would (maybe) eventually prove your innocence, but that could be after a LOT of hassle (computers being siezed, name in the paper, etc)....

---

### Post by stmurray on 2007-12-18
Addedum to my last post.  I checked out your web site and it says you are running an ftp server, allowing users to upload files.  As the files that were uploaded appear to be files to attack ftp sites, then it's pretty safe bet that is how you were compromised.....especially if your password was found.  You should read up on securing an ftp server...

i also noticed that you talk about music files on the ftp site.  Be careful that these aren't copyrighted, or you may have the RIAA knocking on your door.   (check out [http://blog.wired.com/27bstroke6/2007/12/bush-administra.html](http://blog.wired.com/27bstroke6/2007/12/bush-administra.html) to see what the RIAA is doing to copyright violators these days....)

---

### Post by airtonix on 2007-12-18
I resent the implication that the perp is a male.

you dont actually know it isnt a 300pound 19 year old female. or do you?

/end-rant

---

### Post by p_quarles on 2007-12-18
> **mjpolifka said:**
> That is a good point.  While I agree with you, and do not offer this as an excuse but simply food for thought, i would bring up the following counter-point:  Wouldn't those servers have been hacked anyway, given time?  Whether from the original scripter or from another server which failed to have a firewall, I don't believe I actually caused any damage that wouldn't have been caused otherwise.

That being said, no more running my server without a firewall.
Yes, one would hope that any critical server would have decent security. That doesn't prevent your server from participating in a DDoS attack, or even just being a general nuisance. 

Plus, the consequences of running a zombie server are more likely to be bad for you than anyone else: your ISP could get complaints and shut off your access completely; you could find your IP address banned from internet sites you use. Etc., etc. 

Finally, please don't make the mistake of believing that the difference between a secure system and a vulnerable system is simply the presence of a firewall. A firewall does not block access to any ports which you have made available via the internet. You need to make sure that any services available to the WAN are locked down with respect to known exploits.

---

### Post by mjpolifka on 2007-12-18
Ok lets see...

I believe he got access through ether the ftp or ssh servers.  I had a user on there (who was no longer using it, I failed to remove it, which was dumb) who's password was "password" (was meant to be temporary).  He (sorry, just habit to use he) tried logging in using random semi-dictionary passwords, then uploaded the scripts to the ftp folder (the user's home folder)

I see your point about the FBI/corporations/etc.  So what do I do to secure it?  I changed all the passwords to make them stronger, especially my root password.  I keep the system updated with security patches.

No php, the only things I have running are ftp, ssh, and apache.

The RIAA would have to perform an illegal search in order to access my media files.  Obviously, the cost of a good defense attorney is steep, I'm not saying I'm protected from any loss.

So what suggestions do any of you have?  As I said, I'm very new at this security thing, I just learned about networking last summer.  What daemons should I be running for ftp/ssh?  Right now I'm using wu-ftpd and openssh.  I also have webmin on there, but I don't use it, so that's just an open port for no reason.  I think I'll get rid of that.  I also scanned it with nmap and it came up with two things that I don't believe should be open: netbios-ssn on port 139 and microsoft-ds on port 445.  ipp is also open on port 631, but that might be normal, I'm not sure what that is though.

---

### Post by p_quarles on 2007-12-18
> **mjpolifka said:**
> I see your point about the FBI/corporations/etc.  So what do I do to secure it?  I changed all the passwords to make them stronger, especially my root password.  I keep the system updated with security patches.
You need to reinstall the system. If the attacker obtained root access, s/he could have done anything to your server. You can no longer be sure that the application that changes the root password *actually* changes the root password. 

Reinstall your system, and practice better security in the future. No one who knows what they're talking about is going to give you different advice.

---

