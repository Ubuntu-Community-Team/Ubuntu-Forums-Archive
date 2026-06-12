---
title: "[SOLVED] Is Ubuntu As Secure As Windows 2003 As a File Server on My LAN?"
date: 2008-03-20
forum: Security Discussions
---

### Post by MountainX on 2008-03-20
I've been using Windows 2003 on my file server for my family and home office. We have wireless networking. I keep financial data and other important stuff on the file server.

I want to run Ubuntu on this file server now. (My client computers are all becoming Ubuntu machines.). However, today I read about problems with NFS. What I read got me very concerned. Did I understand correctly that any (outside) user who accesses my LAN via the wireless network can, while root on their machine, impersonate any user on my local network and get access to any files?

Does a similar vulnerability exist in Windows? 

I found this security guide: [http://ubuntuforums.org/showthread.php?t=712490](http://ubuntuforums.org/showthread.php?t=712490)

However, it just tells one what to do but the actions are well-explained. For example, it recommends this entry in fstab:
```
tmpfs /dev/shm tmpfs defaults,ro 0 0 
```
I find it a bit strange and I'd like to understand what I'm doing before I do it.

What I want to do is share folders on the file server over my LAN with some measure of security. I don't even want everyone in my family to have access to all the files. Advice appreciated!

Thanks.

**_[COLOR="Red"]SOLUTION:[/COLOR]_**
From the replies in this thread below, my solution is to not use NFS. I used samba instead. I also worked through the following security guides:

[http://www.itsecurity.com/features/u...tall-resource/](http://www.itsecurity.com/features/u...tall-resource/)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[http://ubuntuforums.org/showthread.php?t=694198](http://ubuntuforums.org/showthread.php?t=694198)

I now feel comfortable that Linux is at least as secure as Windows, when used as a file server in the context in which I'm using it.

**[COLOR="Red"]What is the final word on security weaknesses in NFS?[/COLOR]** A related discussion is going on here:
[http://ubuntuforums.org/showpost.php?p=4610305&postcount=11](http://ubuntuforums.org/showpost.php?p=4610305&postcount=11)

---

### Post by jpkotta on 2008-03-20
> **MountainX said:**
> Did I understand correctly that any (outside) user who accesses my LAN via the wireless network can, while root on their machine, impersonate any user on my local network and get access to any files?


Of course any one could make a user with the same name on a machine they control.  That's why there must be something else, like a password, to control access to the NFS share.  I know next to nothing about NFS, but I'm sure they have a password or some other authentication system.  If you go the Samba route, there are passwords.


> 
However, it just tells one what to do but the actions are well-explained. For example, it recommends this entry in fstab:
```
tmpfs /dev/shm tmpfs defaults,ro 0 0 
```
I find it a bit strange and I'd like to understand what I'm doing before I do it.


tmpfs is a filesystem that isn't on a disk, it's in RAM.  It can be used to store small files that don't need to be persistent across reboots.  I'm guessing making it read only will prevent anyone filling it up and leaving you with less RAM, but I don't really understand why the guide recommends this.  In any event, I don't forsee any problems with doing this.

> 
What I want to do is share folders on the file server over my LAN with some measure of security. I don't even want everyone in my family to have access to all the files. Advice appreciated!

Thanks.

The simplest solution, I think, is to use sshfs.  If you use that, you get: almost no configuration aside from ssh, encryption as the data flows across the network, and you can trust it almost as much as you trust ssh.  The downside is it can't mount automatically, and it really doesn't work well if you're transferring massive amounts of data (e.g. 100s of MB).

---

### Post by Mustard on 2008-03-21
On the questions of security with NFS I can't really comment on how people can exploit weaknesses.  This is basically how I have mine set up on a desktop machine running Ubuntu 7.10 and a laptop running 7.10 both connected to through a wired router.

My hosts.deny on my box running the server looks like this..
```
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

# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID
ALL:ALL
```

My hosts.allow..

```
# /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
ALL:192.168.1.3
```

The server exports is this..
```
 # /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#
/home/mustard/Public 192.168.1.3(rw) 
```

The fstab on my client machine looks like this...

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1     /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6     /home           ext3    defaults        0       2
/dev/hda5     none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
192.168.1.1:/home/mustard/Public /home/maximus/Public nfs rw 0 0 
```

I've also had to allow the IP's of the two computers on my firewall, as the firewall was blocking the file share.  I did this through simply allowing all connections from the relevant IP addresses. See relevant image below for an example of the firewall setting on the server.
[[IMG]http://img233.imageshack.us/img233/6445/fson3.th.gif[/IMG]](http://img233.imageshack.us/my.php?image=fson3.gif)

I'd be interested to know if anyone can see some glaring security issues with this method.

---

### Post by Mustard on 2008-03-21
This link covers some security issues and how to go about closing holes.
[http://tldp.org/HOWTO/NFS-HOWTO/security.html](http://tldp.org/HOWTO/NFS-HOWTO/security.html)

---

### Post by hackertarget on 2008-03-21
No matter what operating system you are using you need to spend some time securing your system and at least have a basic understanding of possible issues. Googling a basic guide to securing a new operating system install would usually be sufficient.

As to the original question I would say on a home network the Ubuntu box in general would be more secure as its *mostly* immune to any spyware / malware infection that are forever popping up on home networks.

And although everyone has heard it I will repeat - Whether its Windows or Linux you should always have good backups. Easy to do if you have an Ubuntu server, just set up a cron job to rsync your data at night.

---

### Post by linuxtoindia on 2008-03-21
in windows u have complete easy knowldge of ur system .,, in linux even u dont know what to secure and where it is... in windows u can get the security packs ., antivirus,, intrusion prevention and many more things  ,, in linux just u have to scratch ur head!:lolflag:

---

### Post by Mustard on 2008-03-21
> **linuxtoindia said:**
> in windows u have complete easy knowldge of ur system .,, in linux even u dont know what to secure and where it is... in windows u can get the security packs ., antivirus,, intrusion prevention and many more things  ,, in linux just u have to scratch ur head!:lolflag:

Heh..well thats not really true.  In windows you have a lot of closed source applications that you have no idea how efficient they really are that you implicitly trust because someone told you they are 'safe'.  You have no way of comfirming that yourself, since you can't even see the code that they use.

On the flip side, you have linux, with open source code, that you can actually read yourself to confirm what is going on (assuming you can read code of course).

---

### Post by linuxtoindia on 2008-03-21
oh,, how many normal people have the source code knowldge??
do they have time for learining this??
istead of it they prefer worlds most trusted company! and pay for the security and the trust
!

---

### Post by PmDematagoda on 2008-03-21
> **linuxtoindia said:**
> oh,, how many normal people have the source code knowldge??
do they have time for learining this??
istead of it they prefer worlds most trusted company! and pay for the security and the trust
!

Windows code is closed, this means that you cannot have a look at it and you may not be able to fully understand the true processes that go on within the program, this may also lead to you being unaware of certain vulnerabilities on the program. Linux on the other hand gives you the ability to understand exactly what is going on and if you spot a vulnerability, it gives you the chance of fixing it without coming under attack by lawyers.

What do you think programmers do?;) Systems administrators sometimes look at the source code themselves before implementing it.

The worlds most trusted company? Windows? You are joking, name one situation where you could call them trusted. And secure? If Windows is as secure as you say it is, then how come there are security vulnerabilities and viruses?

---

### Post by peterbrewer on 2008-03-21
> **linuxtoindia said:**
> oh,, how many normal people have the source code knowldge??
do they have time for learining this??
istead of it they prefer worlds most trusted company! and pay for the security and the trust
!

More importantly there are a limited number of programmers looking at a closed source application.  With open source even if you can't read the code many others probably will have meaning the quality in theory should be higher.

Also open source apps have no reason to put back doors in where as closed source apps sometimes do for government access etc.

---

### Post by MountainX on 2008-03-21
> **Mustard said:**
> 
I'd be interested to know if anyone can see some glaring security issues with this method.

I too would really benefit from specific comments on Mustard's approach because I'd like to use all or some of it. Thanks.

---

### Post by dannyboy79 on 2008-03-21
is the OP saying he uses unsecured WIFI? I would strongly suggest against that to begin with, if it is secure, then there's no way they would get on your network, let along access your NFS share. Unless you were using WEP and someones sniffed your packets for a long time but how paranoid do you want to get??? Use WPA and then you won't have to worry (to much) about someone hacking your network or any shares in it.

For the guy who says he makes his firewall only allow connections from a certain IP, well that's all good if someone doesn't sniff you out and make it look like his machine is your by IP spoofing. It can be done. I read a whole article about packet sniffing and brute forcing a machine. Good luck either way.

---

### Post by jpkotta on 2008-03-21
> **linuxtoindia said:**
> oh,, how many normal people have the source code knowldge??
do they have time for learining this??
istead of it they prefer worlds most trusted company! and pay for the security and the trust
!

Don't feed the troll.  

Back on topic, if you use my suggestion of sshfs, you won't have to worry about unencrypted WIFI, because the traffic is encrypted by ssh.  I don't even see where OP said he had unencrypted WIFI.

I would set up a Samba or NFS share for anything that you don't care about, and use sshfs for anything that is sensitive.  This is what I do, and it works very well.  Encrypted WIFI is a separate, but nontheless important, issue.

---

### Post by MountainX on 2008-03-21
> **dannyboy79 said:**
> is the OP saying he uses unsecured WIFI?

For the guy who says he makes his firewall only allow connections from a certain IP, well that's all good if someone doesn't sniff you out and make it look like his machine is your by IP spoofing. It can be done. I read a whole article about packet sniffing and brute forcing a machine. Good luck either way.

I wasn't saying I use unsecured WIFI. (I use WAP.) But I was just using that because my LAN is connected to the public Internet in several ways (DSL, Cable) and I have WIFI. So I was assuming someone could find a way in to my LAN and I wanted to know how to prevent access to my file server except by authorized users.

I liked the idea of only allowing certain IP addresses to access the file server, but if that isn't very secure, then what other options are there?

These security discussions always start getting depressing because it seems there is never any reasonable solution. Either it requires a full time security expert or it requires not using the Internet, or ... you get the idea.

I just want to make my Ubuntu file server at least as secure as my Windows 2003 file server. On the Windows machine I renamed the admin account and I used NTFS permissions to restrict access appropriately. I did a few other things. It does not have the problem that any admin that gets into my LAN can get any files on the file server, afaik. I'd like at least the same security with Ubuntu. 

The article I referred to in my original post made it sound like there are security issues with Ubuntu that I don't understand at all. So far this thread hasn't helped clarify much. :confused:

---

### Post by linuxtoindia on 2008-03-21
those virus and se curity threats are created by some ridiculous and useless people ,, wait one day for them to develop virus for linux and the hacking threats ,, and that day will you find a new platform??

this time it wud be''home without windows!''
or decayed apple''
or may be sunix''

dnt mind!
]

even me a bigfan of linux ,,
these are the questions of a new comer@!

---

### Post by MountainX on 2008-03-22
I have decided to follow Mustard's approach. I know Dannyboy79 said people can spoof IP address, but no one else offered a better solution than Mustard's.

I have a few questions:
1. How can I specify host names in hosts.allow? I want to put the IP address in /etc/hosts and then use the host name everywhere else. But the man for denyhosts says only IP addresses can be used with ALL. I want something like this in hosts.allow:

ALL: myhostname_as_specified_in_hosts_file

2. I don't have an /etc/exports file. What application creates it?

3. How easily can someone spoof an IP address on my private LAN (in the 192.168.*.* range)? If they are coming in from the outside, they can't use a private address, right?

4. What does the following command do?
sudo chown root:admin /bin/su sudo

Thanks.

---

### Post by ubernoob on 2008-03-22
> I wasn't saying I use unsecured WIFI. (I use WAP.
Yes, you just did! ;) It will take about 5 minutes to breake WEP and have access to your network. (I assume you mean WEP and not WAP)


> I have decided to follow Mustard's approach. I know Dannyboy79 said people can spoof IP address, but no one else offered a better solution than Mustard's.


I would agree with jpkotta. Use sshfs to transfer sensitive content. NFS doesn't support password and user accounts. (Maybe NFS4 does. You might want to look into that). I would have a look at Samba, but I'm not sure if it is as fast as NFS.


> 
I have a few questions:
1. How can I specify host names in hosts.allow? I want to put the IP address in /etc/hosts and then use the host name everywhere else. But the man for denyhosts says only IP addresses can be used with ALL. I want something like this in hosts.allow:

ALL: myhostname_as_specified_in_hosts_file

I haven't checked it out, but i don't think you can use host names. There might be security issues with that. You should try to google it.

> 
2. I don't have an /etc/exports file. What application creates it?

probably nfs-server. Or else i guess you have to make one yourself.

> 
3. How easily can someone spoof an IP address on my private LAN (in the 192.168.*.* range)? If they are coming in from the outside, they can't use a private address, right?

No, not from the outside. But they can come from the WLAN, or if some other machine in your network gets compromised.

> 
4. What does the following command do?
sudo chown root:admin /bin/su sudo

you will change group access to the file /bin/su and sudo. Why would you do that? I would not recommend it.

---

### Post by MountainX on 2008-03-22
Sorry if I typed WEP somewhere by mistake. I use WAP.

I can't use sshfs because I transfer large files (videos, disk images, virtual machine images, etc.) all the time. Sometimes it takes hours without ssh. Plus I read that sshfs gives errors on large files.

**So the bottom line seems to be that Windows server is a better OS for general file server usage with decent security?!? You've got to be kidding me?** :confused:

UPDATE: I'm going to move the following into a new thread because I just don't understand it.
BTW, the command:
```
sudo chown root:admin /bin/su sudo
```
is recommended several places, including here:
[http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/)

I also saw someone say they thought Ubuntu might already default to that... I'd like to know more about it before I do/don't do it.

---

### Post by ubernoob on 2008-03-22
> Sorry if I typed WEP somewhere by mistake. I use WAP.
There isn't any encryption protocol called WAP. So I guess you mean WPA then.

> So the bottom line seems to be that Windows server is a better OS for general file server usage with decent security?!? You've got to be kidding me?
In windows, you can only use windows share (SMB), while in Linux, you can choose between Samba (SMB), NFS and ssh. So i don't know how you made your conclusion.

If you want similart file server and security as in windows, you should go for samba. It's not less secure in linux.

The line you didn't paste: chmod 04750 /bin/su
Makes the file not runable for other people than root or the group admin. So only they can run the command. I guess you have limited user accounts on your system, so you won't need this command. Beside, there is no known vulnerabilities in either sudo or su and it is very unlikly that someone will use it on a home server if they knew about it.

---

### Post by MountainX on 2008-03-22
Thank you.

Yes, I meant WPA.

OK, I'll use samba. Glad to know it will be similar to what I'm used to.

Obviously, I wasn't understanding the situation fully. But I did find it unbelievable that Windows would be more secure than Linux in any significant way. That's why I was feeling confused.

I do have limited user accounts, so I won't worry about using that chown command. However, I did start the other thread and I still want to understand it now that it has gotten my curiosity. Thanks.

---

### Post by jflaker on 2008-03-22
> **linuxtoindia said:**
> oh,, how many normal people have the source code knowldge??
do they have time for learining this??
istead of it they prefer worlds most trusted company! and pay for the security and the trust
!

NOT MANY can read code, but if you wanted to know....you can........unlike windows

---

### Post by MountainX on 2008-04-01
> **MountainX said:**
> 

OK, I'll use samba. Glad to know it will be similar to what I'm used to.


I'm changing course now. I'm in the process of moving to **[COLOR="Red"]nfs[/COLOR]** because cifs (Gutsy and Hardy) and smbfs (on Hardy) don't work well with gedit (and some other apps) when the shares on are Windows servers. See [http://ubuntuforums.org/showthread.php?t=738168](http://ubuntuforums.org/showthread.php?t=738168) (gedit/cifs)

The security issues of nfs still concern me and cause some confusion, however.

See:
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch29_:_Remote_Disk_Access_with_NFS](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch29_:_Remote_Disk_Access_with_NFS)

"I don't recommended using NFS over insecure networks. NFS doesn't encrypt data and it is possible for root users on NFS clients to have root access the server's filesystems."


    *  *Restrict its use to secure networks*
This is not possible. I have wireless networking (but I do use WPA). I also have cable broadband.

    * *Export only the most needed data*
ALL my data is on the file server, including personal financial data, etc. So again, I can't follow that guideline.

    * *Consider using read-only exports whenever data updates aren't necessary.*
Not an option for me.

    * *Use the root_squash option in /etc/exports file (default)* 
As mentioned, this is the default.

    ** Make NFS run on predefined TCP and UDP ports as this makes the management of firewall rules much easier. *
This sounds too complex for me at the moment...

---

### Post by MountainX on 2008-04-01
I just found another good faq on NFS. 
[http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html)

It covers a lot of stuff, but here is some info from the security section:

With NFS, there are two steps required for a client to gain access to a file contained in a remote directory on the server. The first step is mount access. Mount access is achieved by the client machine attempting to attach to the server. The security for this is provided by the /etc/exports file. This file lists the names or IP addresses for machines that are allowed to access a share point. If the client's ip address matches one of the entries in the access list then it will be allowed to mount. This is not terribly secure. **If someone is capable of spoofing or taking over a trusted address then they can access your mount points.** To give a real-world example of this type of "authentication": This is equivalent to someone introducing themselves to you and you believing they are who they claim to be because they are wearing a sticker that says "Hello, My Name is ...." Once the machine has mounted a volume, its operating system will have access to all files on the volume (with the possible exception of those owned by root; see below) and write access to those files as well, if the volume was exported with the rw option.

The second step is file access. This is a function of normal file system access controls on the client and not a specialized function of NFS. Once the drive is mounted the user and group permissions on the files determine access control.

An example: bob on the server maps to the UserID 9999. Bob makes a file on the server that is only accessible the user (the equivalent to typing chmod 600 filename). A client is allowed to mount the drive where the file is stored. On the client mary maps to UserID 9999. **This means that the client user mary can access bob's file that is marked as only accessible by him.** It gets worse: If someone has become superuser on the client machine they can su - username and become any user. NFS will be none the wiser. 

--------
Other references:

[http://nfs.sourceforge.net/nfs-howto/ar01s05.html](http://nfs.sourceforge.net/nfs-howto/ar01s05.html)
[http://nfs.sourceforge.net/](http://nfs.sourceforge.net/)

---

### Post by dannyboy79 on 2008-04-01
ok, so you're not using WPA, you're using WEP. That's your first problem right there. You want a secure network but you're using inferior WIFI security measures. If you used WPA and used NFS, the only way someone could spoof an allowed ip address is if they had access to your internal network, which wouldn't happen unless they entered your house or you had inferior WIFI security setup. Can't your WIFI router only allow certain MAC address on it, mine can. That would stop outsiders from being able to connect in the first place. What about making your DHCP server only had out so many addresses and that's it. however many computers you have, then make your dhcp server on your router only hand out that many IP's. Do you really think people are out there war driving and know that you have super critical info that they want and they'll spend the amount of time (outside your house) to hack into your network? There's a point in which your security worries will just make it impossible because you're expecting to be protecting Fort Knox. I wish you the best in whatever you do chose. If it's Windows because you feel it's more secure as a file server than so be it.

---

### Post by MountainX on 2008-04-01
> **dannyboy79 said:**
> ok, so you're not using WPA, you're using WEP. 

I'm using WPA.

---

### Post by netlogic on 2008-04-01
Quick Answer: yes.
Many people can own a 2003 server without a firewall within few hours.

---

### Post by MountainX on 2008-04-01
> **netlogic said:**
> Quick Answer: yes.
Many people can own a 2003 server without a firewall within few hours.

Did everyone see the news about the Pwn2Own hacking challenge?

See
[http://www.regdeveloper.co.uk/2008/03/29/ubuntu_left_standing/](http://www.regdeveloper.co.uk/2008/03/29/ubuntu_left_standing/)

or google Pwn2Own

Ubuntu was the only OS not cracked in this contest.

---

### Post by hyper_ch on 2008-04-02
> **MountainX said:**
> I can't use sshfs because I transfer large files (videos, disk images, virtual machine images, etc.) all the time. Sometimes it takes hours without ssh. Plus I read that sshfs gives errors on large files.
Have you ever benchmarked the transfer of large files and small files with nfs and sshfs?

Where did you read, that sshfs gives errors on large files?

---

### Post by MountainX on 2008-04-02
> **hyper_ch said:**
> Have you ever benchmarked the transfer of large files and small files with nfs and sshfs?

Where did you read, that sshfs gives errors on large files?

I have not done any benchmarks. However, I was speaking to someone on IRC yesterday who had done benchmarks and NFS file transfers took on 40% as much time as sshfs for him. Several others have told me similar things.

Regarding large file transfers giving errors with sshfs, I read that here on the Ubuntu forum.

---

### Post by netlogic on 2008-04-02
There is overhead, because you are encrypting. Of course, you will have overhead. For the statement about the file corruption, it doesn't exist.

---

