---
title: "User Security"
date: 2008-12-02
forum: Security
---

### Post by Drezard on 2008-12-02
Running a smallish Ubuntu server here. Im running it as an All-In-One server and I have a number of servers hosted off it. 

What I've done here is created a couple of users that I want to make the daemons run under. Basically is there a good guide for starting up daemons under different Users... Like starting qmail under the username mailbox and starting apache2 under the username webhost?

Daniel

---

### Post by The Tronyx on 2008-12-03
Hello,

I am not entirely sure if I get what you are saying but for daemons, whenever possible, it is generally a good idea to run them in a chroot jail.  This can bring up some complications but depending on the problem, nothing the community couldn't help out with.  If you don't want to run Apache as nobody you should give some serious though to jailing it.

---

### Post by cdenley on 2008-12-03
> **Drezard said:**
> Running a smallish Ubuntu server here. Im running it as an All-In-One server and I have a number of servers hosted off it. 

What I've done here is created a couple of users that I want to make the daemons run under. Basically is there a good guide for starting up daemons under different Users... Like starting qmail under the username mailbox and starting apache2 under the username webhost?

Daniel

Apache2 runs as user www-data in ubuntu by default. I'm not sure about qmail. Those daemons need to be started as root, though, in order to listen on port 80 or 25.

I disagree with 2point0. I think chroot's provide mostly a false sense of security, and aren't worth the trouble. If an attacker gets root in your chroot, they have root outside your chroot as well.

---

### Post by HermanAB on 2008-12-03
Yup, chroot is not worth the trouble.  It does nothing for security and increases the maintenance effort a lot.  On military systems, use of chroot is discouraged.  So if Uncle Sam doesn't want to use chroot, then you probably should not either.

---

### Post by The Tronyx on 2008-12-03
> **HermanAB said:**
> Yup, chroot is not worth the trouble.  It does nothing for security and increases the maintenance effort a lot.

I have to say I disagree.  TBH, the only reason someone should be able to own your box from a chroot is because it was jailed terribly in the first place.  By no means am I trying to be inflammatory, however, if someone compromises, your web server (for example) it doesn't mean you are rooted.  It can be fairly easy, depending on the person's code, to attach a PHP shell via remote file inclusion.  Once you have the shell, the command 'id' will generally display the user that Apache is running as and if you are on the receiving end of this attack, you had better hope it isn't root.  

Now, as the PHP shell provides a way to execute arbitrary commands on the server (with of course user/group limitations), it could be theorized that there it is only a matter of time until someone busts out of the chroot and wreaks havoc on the entire system.  The truth is that there is a giant gap between being able to own a poorly secured web server via remote file inclusion vulnerability and being able to root a server with a local privilege escalation vulnerability.  To summarize, most script kiddies who use google hacking to find RFI vulnerabilities are not very formidable attackers and since they cannot easily advance their exploitation from the jail, the damage they can do is limited.  Most often, breaking out of a chroot jail requires things that a proper jail should not facilitate.  Lastly, if they do keep at it for a reasonable amount of time, it should be on the user to monitor their security in which case targeted attacks should not go unnoticed.

For the sake of keeping it simple, no, chrooting is not fool proof but it will not only discourage most fools but it can also buy you time and give you an additional layer of security which is always a good thing.

  > On military systems, use of chroot is discouraged.  So if Uncle Sam doesn't want to use chroot, then you probably should not either.

Uncle Sam probably doesn't want people to use solid encryption either.

---

### Post by cdenley on 2008-12-03
> **2point0 said:**
> I have to say I disagree.  TBH, the only reason someone should be able to own your box from a chroot is because it was jailed terribly in the first place.  By no means am I trying to be inflammatory, however, if someone compromises, your web server (for example) it doesn't mean you are rooted.  It can be fairly easy, depending on the person's code, to attach a PHP shell via remote file inclusion.  Once you have the shell, the command 'id' will generally display the user that Apache is running as and if you are on the receiving end of this attack, you had better hope it isn't root.  Now, as the PHP shell provides a way to execute arbitrary commands on the server (with of course user/group limitations), it could be theorized that there it is only a matter of time until someone busts out of the chroot and wreaks havoc on the entire system.  The truth is that there is a giant gap between being able to own a poorly secured web server via remote file inclusion vulnerability and being able to root a server with a local privilege escalation vulnerability.  To summarize, most script kiddies who use google hacking to find RFI vulnerabilities are not very formidable attackers and since they cannot easily advance their exploitation from the jail, the damage they can do is limited.  Most often, breaking out of a chroot jail requires things that a proper jail should not facilitate.  Lastly, if they do keep at it for a reasonable amount of time, it should be on the user to monitor their security in which case targeted attacks should not go unnoticed.

For the sake of keeping it simple, no, chrooting is not fool proof but it will not only discourage most fools but it can also buy you time and give you an additional layer of security which is always a good thing.

  

Uncle Sam probably doesn't want people to use solid encryption either.

As far as I know, on any Linux chroot, if the attacker has root, breaking out of the chroot is rather trivial. I've tried it myself. If you have ideas on how to prevent this, please tell me. Other types of jails such as in OpenBSD may be different, I'm not sure. If someone gets a shell through apache as you described, they can wreak havoc with the web server whether it is chrooted or not. With the user privilege seperation used on a default install, the damage will be limited to the web server, unless the attacker manages to escalate privileges. If that happens, breaking out a chroot is rather trivial.

---

### Post by The Tronyx on 2008-12-03
> As far as I know, on any Linux chroot, if the attacker has root, breaking out of the chroot is rather trivial.

I agree, I was referring to the user having a non-root account, such as whatever user (hopefully not root) Apache is running as.

> 
If someone gets a shell through apache as you described, they can wreak havoc with the web server whether it is chrooted or not.

Right, but there is much to be said for mitigating damage with regards to an attack.  I would much rather have someone replace my index.html than to delete the contents a second drive mounted as /backup or even obliterate / in its entirety.

---

### Post by cdenley on 2008-12-03
> **2point0 said:**
> Right, but there is much to be said for mitigating damage with regards to an attack.  I would much rather have someone replace my index.html than to delete the contents a second drive mounted as /backup.

What could chrooting do to mitigate damage that isn't already done with user privilege seperation? Why would the www-data user have write access to /backup?
> 
or even obliterate / in its entirety

Only root can do that. If they escalate to root privileges, it doesn't matter if you used a chroot.

---

### Post by The Tronyx on 2008-12-03
> **cdenley said:**
> What could chrooting do to mitigate damage that isn't already done with user privilege seperation?

Take away the ability for a user to access the C compiler which can be used to run a publicly available exploit for privilege escalation.  I understand that this can be done without a chroot, however, I feel that it is easier to do this in a chroot environment.

I am not saying that chrooting is infallible or even that it is difficult to get out of as root.  What I am saying is that it is an additional level of security and a practice which I use.

> 
Why would the www-data user have write access to /backup?

You would be amazed at some of the improperly configured servers I have seen.

---

### Post by Drezard on 2008-12-04
So whats the verdict?

---

### Post by hyper_ch on 2008-12-04
the verdict is that security is an ongoing process and not a place-it-once-and-forget-about-it...

it is also very different from who wants to implement it and for what reasons and against what threads... there are some general recommendations but in the end you should know yourself what you do.

---

### Post by cdenley on 2008-12-04
Apache2 already runs as a non-root user by default. I'm not sure about qmail, but you wouldn't be able to start it as a non-root user and listen on port 25. The daemon would need to start a listening process as root, then start other processes as a non-root user. In other words, if it doesn't already run as a non-root user, I don't think there is an easy way to make it, unless there is a qmail-specific configuration option.

Most server software in the repos use user privilege seperation by default.

---

