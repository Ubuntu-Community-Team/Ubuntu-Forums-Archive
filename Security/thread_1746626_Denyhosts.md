---
title: "Denyhosts"
date: 2011-05-02
forum: Security
---

### Post by jramshu on 2011-05-02
I was recently looking at my auth.log file and noticed a WHOLE lot of  hacker attempts. 
If you want to see who's been trying to get in use this:
```
grep 'Failed' /var/log/auth.log
```If the output is too long use this:
```
grep 'Failed' /var/log/auth.log | more
```I looked around and decided to go with denyhosts to  help stop some of it. It worked good and within a few minutes had my  first IP blocked. I also decided I would do some testing myself. Then  the problem came after I used an invalid name and password. I went into  the auth.log file and deleted the ip I was using.

Done right? Nope. After a few minutes my IP was blocked again.

I found out that the daemon was re-writing my IP back into the   /etc/host.deny file. It took me a little bit but I did figure it out. So  this is for anyone who has encountered the same problem.

You have to stop denyhosts by using this 
```
sudo /etc/init.d/denyhosts stop
```Then navigate to the  /var/lib/denyhosts directory and delete every instance that your test IP  shows up in these files "hosts, hosts-restricted, hosts-root,  hosts-valid, offset, suspicious-logins, user-hosts, users-hosts,  users-invalid, users-valid. Though it probably wasn't necessary to  delete the IP from all, especially the 'hosts-valid' file.
Then go to /etc/host.deny and delete your blocked IP address.

Then type(or copy and paste) this
```
sudo /etc/init.d/denyhosts start
```That will let you get back  on. It took me a little reading to find this stuff and just figured I  would make it a little easier for others who have ran into this problem.
When the daemon is running the --purge flag will not remove your blocked IP.

By the way I should mention, you will have to be sitting in front of the server or logged in from a different IP.

I hope this makes sense, I'm not the best explainer out here.

---

### Post by bodhi.zazen on 2011-05-02
Yep, this is the problem with using denyhosts (or similar) and blacklisting an IP forever.

Keep in mind, many alerts are false positives.

If you block an IP for 10 minutes it is sufficient to deter most intruders without the hassles you discovered. A determined intruder will simply change IP :twisted:

Also if you use ssh, a better strategy is to use keys and disable password authentication.

---

### Post by jramshu on 2011-05-02
Thanks for the info. I have been looking around on forums to see what others recommend. I'm still learning the way the system works and really appreciate the information and help that I have received here.
Thanks to all, it is greatly appreciated.

---

### Post by jramshu on 2011-05-02
Since I posted this I checked my auth.log file, it makes me wonder if it's a script or a person. I can't figure out the randomness of the user names, odd to say the least. Here are the results.
```
@server1:~$ grep 'Failed' /var/log/auth.log | more
May  1 20:16:37 server1 sshd[3030]: Failed password for invalid user ____ from 117.16.94.82 port 44916 ssh2
May  1 20:16:44 server1 sshd[3033]: Failed password for root from 117.**.**.** port 45206 ssh2
May  1 20:16:49 server1 sshd[3035]: Failed password for root from 117.**.**.** port 45612 ssh2
May  2 20:33:14 server1 sshd[1039]: Failed password for invalid user aryan515 from 124.137.**.** port 25127 ssh2
May  2 20:33:19 server1 sshd[1043]: Failed password for invalid user kashi179 from 124.137.**.** port 25485 ssh2
May  2 20:33:22 server1 sshd[1045]: Failed password for invalid user sanaiq from 124.137.**.** port 25671 ssh2
May  2 20:33:27 server1 sshd[1047]: Failed password for invalid user aryan521 from 124.137.**.** port 25815 ssh2
May  2 20:33:31 server1 sshd[1049]: Failed password for invalid user kashifraza_55 from 124.137.**.** port 26017 ssh2
May  2 20:33:34 server1 sshd[1051]: Failed password for invalid user sandhu118 from 124.137.**.** port 26181 ssh2
May  2 20:33:39 server1 sshd[1053]: Failed password for invalid user aryan523 from 124.137.**.** port 26313 ssh2
```I guess I need to disable password authentication. Here is my newly updated host.deny file.
```
@server1:~$ cat /etc/hosts.deny
# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
#                  See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
# The PARANOID wildcard matches any host whose name does not match its
# address.
#
# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID
# DenyHosts: Sun May  1 20:16:45 2011 | sshd: 117.16.**.**
sshd: 117.16.**.**
sshd: 124.137.**.**

```Is this pretty normal? Would using keys stop this kind of stuff?
Any suggestions? 
I don't like to admit but, I am having trouble figuring out how to do key authentication.
I'm givin' her hell though.:lol:
There really isn't anything on the server, figured I would learn as much as I could before putting anything important on it.

EDIT: Would psad be a better defense? Thanks and I apologize for all the questions.

---

### Post by bodhi.zazen on 2011-05-03
Yep, if you install openssh server it get hammered by the script kiddies as they are called.

IMO ssh keys are the best defense. Keys will not quiet the logs, but since you disable password authentication they will not be able to log in without the key.

See the tutorial here on ssh keys

[http://bodhizazen.net/Tutorials/](http://bodhizazen.net/Tutorials/)

---

### Post by jramshu on 2011-05-03
Thanks again. I have been ready the sticky's as suggested. I should have started there to begin with. I guess I got too excited and jumped to far ahead of myself. Learn the basics first. I appreciate the patience and will refrain from asking anymore questions until I thoroughly read the tutorials you have provided,and suggested, to get a better grasp at the different ways to secure the server. I'm thrilled all you guys are here and very willing to help. Makes learning all this stuff that much easier. Again much appreciated. I look forward to a long relationship with Ubuntu and Ubuntu forums.

---

### Post by jramshu on 2011-05-03
Followed your tutorial bodhi.zazen on using keys and it worked perfectly. I did use the "easy way" to transfer it. 
Tested it to be sure I did it right, should be able to disable password authentication on the server now.

Thanks a bunch and looking forward to reading the rest of the tutorials.

---

### Post by bodhi.zazen on 2011-05-03
> **jramshu said:**
> Followed your tutorial bodhi.zazen on using keys and it worked perfectly. I did use the "easy way" to transfer it. 
Tested it to be sure I did it right, should be able to disable password authentication on the server now.

Thanks a bunch and looking forward to reading the rest of the tutorials.

If the key works, yes disable password authentication.

---

### Post by jramshu on 2011-05-03
Thanks for all your help. Everything works great now that I fixed my typo. Password auth has been disabled.

---

