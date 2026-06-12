---
title: "Samba with xinetd"
date: 2008-05-03
forum: Server Platforms
---

### Post by smiler_jerg on 2008-05-03
Hello everyone,

I've installed xinetd and Samba on Hardy Heron Server, so I can get a basic file-server running. However, I'm having difficulty with non-guest access. I've tried two different modes of operation, to diagnose where the fault lies:

**xinetd [COLOR="Red"]stopped[/COLOR], smbd [COLOR="Green"]started[/COLOR]**
My Mac OS 10.5 client can see the server and connects automatically as a guest, displaying the single share on the server. If I try to connect as a user ("Connect as..." in Leopard), I get no errors, but it silently falls back to a guest connection (the title bar says "Connected as: Guest").

**xinetd [COLOR="Green"]started[/COLOR], smbd [COLOR="Red"]stopped[/COLOR]**
My Mac sees the client and connects as guest, but if I attempt to connect as a user, I get an error:
> There was an error connecting to the server.  Check the server name or IP address and try again.

If you are unable to resolve the problem contact your system administrator.
This happens even if I select 'Guest' in the login box, despite Mac OS connecting as guest automatically without it.

**Why xinetd?**
I want to reduce the long-term power load of the server as much as possible. One of my goals is to implement every power-saving feature I can find (which doesn't seem very easy under Linux), as I intend to leave this server running for on-demand access. (I'll be adding more services later, but one at a time seems wise!) With xinetd, smbd only runs when it's needed.

I've attached the smb.conf in use throughout this. You may notice a 'use netbios = No' line. This was intended to stop NetBIOS discovery, so that I can use Avahi without multiple icons for a single server appearing on clients. If I've got this wrong, please tell me!

*Edit: 'use netbios = No' should be 'disable netbios = Yes' This has no affect on the issues above though.*

Any help is greatly appreciated!

---

### Post by andguent on 2008-05-03
I'm reading your post, and not 100% sure what you are looking for. I get the desire for xinetd though.

Are you looking to have guest access, user/password access, or both? I'm reading it as both and working on that assumption.

An important line I don't see in your smb.conf is 'security ='. I believe the best option here is 'security = user' based on what you want to do.

I posted a mini howto on setting up samba with user authentication at the link below. It may or may not answer some questions.
[http://ubuntuforums.org/showpost.php?p=4707595&postcount=13](http://ubuntuforums.org/showpost.php?p=4707595&postcount=13)

No matter how far you get, post back your results and we can go further if needed.

---

### Post by smiler_jerg on 2008-05-03
You're quite correct - I want both. I'm using security = user.

I made considerable progress with this today, but got stuck again. I posted the following in Linux questions (as it's a Samba issue, and thought I'd reach more people there.)
> I have a share that I want to be:[LIST]
[*]Read only accessible by guests
[*]Read & write accessible by valid users.[/LIST]
I eventually got this working with these lines:
```
public = Yes
read only = Yes
write list = @netusers
```
netusers is the group of users allowed to write to this share. The problem I have is that when I create a new file in the share remotely, the file is created with my primary group (the same as my username), rather than the netusers group:
```
-rw-r--r--   1 alex alex      910 2008-05-03 10:39 a-file.txt
```
There is an option in samba:
```
force group = netusers
```
However, this does more than simply forcing the group on new files (I don't understand what more it does though!), and has the side-effect of disabling guest access.

I thought that perhaps I could fix this by mapping my username to the netusers group in Samba's user database with pdbedit, but it doesn't seem to do anything. For example, trying to change my full name:
```
# sudo pdbedit -u alex -f "Alexander"
```
just prints all my details (the same as pdbedit -Lv) with the old full-name unchanged.

Any ideas?

---

### Post by andguent on 2008-05-03
I would recommend throwing the following into your share settings:
```
create mask = 0774
directory mask = 0774
force group = netusers
```

If you are familiar with chmod, these numbers should make sense, otherwise they are gibberish. It forces all newly created files (over samba) to be fully accessible to the owner & group, but only readable by everyone else (guest).

You can add new users to netusers via:
```
sudo adduser alex netusers
```

---

### Post by smiler_jerg on 2008-05-03
> I would recommend throwing the following into your share settings:
Those settings have some rather undesired effects:[list]
[*]using 'force group' disables guest access
[*]the 'create mask' has no effect.[/list]
I think, as I'm using Mac OS X (which supports Unix Samba extensions) the permissions are set by the client. I think this setting only affects DOS clients (even Windows NT/XP will set permissions if ACL is enabled on Samba).

> You can add new users to netusers via:
I'm already a member of that group, but it's not my primary group, so new files are created with the 'alex' group instead of 'netuser'. Is there not a way to have Samba create new files as the netuser group instead, without blocking guests?

---

### Post by andguent on 2008-05-03
Nearly all of my Samba experience is with Win 2000/XP connecting to Samba on Linux. If any of these options behave differently to a Mac client, I wouldn't know. I've never had issues with them before.

It may be worth creating two shares that point to the same directory. One share requires user authentication, and permits read/write. The second share is guest only, and is read only. Just an idea, never actually tried it.

---

### Post by ghostknife on 2008-05-03
"force group" is used to set the "primary group" of any authenticated users for that the shares it covers.

You might concider add a "+" sign in front of the group name. This is a minor security concideration, which causes only users who actually belong to the group to receive it as their primary groups. Otherwise any user who gets to authenticate to the share will receive it as their primary groups, which could be unwanted.

Thus make it's value:
```

force group = +netusers

```

This is the exact configuration I use for a share which does what you want (with the file creation using the desired group)
```

[Stats]
        comment = stats
        valid users = @stats
        write list = root, @stats
        path = /home/Public/stats
        force group = stats

```

---

### Post by smiler_jerg on 2008-05-04
rlhartmann on Linux Questions solved this _[here](http://www.linuxquestions.org/questions/linux-networking-3/samba-gid-on-new-files-with-rw-users-and-ro-guest-639601/?posted=1#post3142017)_. I'm grateful to everyone for their help.

He suggested setting the sgid bit on the directory, so that the directory's gid is inherited by new files. This worked just as it should - I just didn't know about it.
```
# chmod 2775 share-dir
# touch share-dir/new-file
# ls -la share-dir
drwxrwsr-x 7 alex netusers   45 2008-05-04 11:32 .
drwxr-xr-x 2 root root       8  2008-05-01 18:43 ..
-rwxrwxr-x 1 alex netusers   0  2008-05-04 11:33 new-file
```

> **andguent said:**
> Nearly all of my Samba experience is with Win 2000/XP connecting to Samba on Linux.
Samba's a complicated beast. Before I started reading about this problem, I'd have thought it wouldn't matter, but Samba has several methods for storing permissions for DOS, Windows XP and Unix-like OSs. Quite remarkable!

> **andguent said:**
> It may be worth creating two shares that point to the same directory.
I'd thought of this too. I tried two shares with the same name, but the configurations merged together - I guess I should've predicted that! It's working now though.

I've attached my final smb.conf file for people to see if they end up in the same situation.

Now to see if this still works when Samba's started by xinetd...

---

### Post by ghostknife on 2008-05-04
You mentioned the problemed is partly solved. You still have other problems?

---

### Post by smiler_jerg on 2008-05-04
> **ghostknife said:**
> You mentioned the problemed is partly solved. You still have other problems?
The original reason for posting this thread was regarding running Samba as a xinetd service, which I haven't yet configured. Now that the service is behaving as I want when started by init.d, I'll try to get it working with xinetd.

Hopefully there won't be any problems. I'll post here with the result :).

---

### Post by smiler_jerg on 2008-05-04
Okay, xinetd wasn't a problem at all. I already had the configuration from playing around before, and it Just Worked. For those who might be interested:

xinetd is configured using two main files. /etc/services and /etc/xinetd.conf. If you inspect xinetd.conf, you'll notice that it includes /etc/xinetd.d/.

To have Samba start automatically when its required, first install xinetd.
```
# sudo apt-get install xinetd
```
Then create a new file called 'samba' in /etc/xinetd.d/ with the settings for Samba's service.
```
# sudo nano /etc/xinetd.d/samba
service netbios-ssn
{
	port		=	139
	socket_type	=	stream
	wait		=	no
	only_from	=	192.168.0.0
	user		=	root
	server		=	/usr/sbin/smbd
	log_on_failure	+=	USERID
	disable		=	no
	mdns		=	yes
	instances	=	1
}
```
only_from specifies what IP addresses are allowed to connect. 192.168.0.0 means anyone who's IP address starts with 192.168.

In my configuration, I haven't set up the NetBIOS daemon 'nmdb', as I don't need it. It would have to run all the time to function, so cannot be started with xinetd (as far as I know), and is technically obsolete anyway. I'm using _[avahi](http://avahi.org/)_ for my Mac.

You should also check that the ports are defined in the /etc/services file. I found that they already were for Ubuntu Server.
```
# grep -e 139 -e 445 /etc/services
netbios-ssn	139/tcp				# NETBIOS session service
netbios-ssn	139/udp
microsoft-ds	445/tcp				# Microsoft Naked CIFS
microsoft-ds	445/udp
```
You should see the first four lines, and they shouldn't have any characters before them (# or ; which comment out the line). If these lines are missing, add them using nano.

To ensure xinetd recognises the new configuration, restart it.
```
# sudo /etc/init.d/xinetd restart
```
Now try connecting to a share. In Windows, go to Start>Run and type \\192.168.2.3\ replacing the numbers with your server's IP address. Similarly for Linux, Mac OS et al: smb://192.168.2.3/

I hope someone will find this useful. I found this information liberally scattered across the Internet, so I've brought it together here.

---

### Post by andguent on 2008-05-04
Glad to hear it all worked out. Thank you for posting back and letting us know how it went, it makes the thread ten times more useful when someone reads it a year from now. :)

---

### Post by scasparz on 2010-03-01
This is a rather old thread, I would like to resurrect. 

Am playing with Samba in a xinetd environment. All right, starting samba through a super server takes some time, yet on the other hand it is my understanding that xinetd provides some good safety precautions, which could be of help say in the case of a DOS kind of attack. Not to mention I need xinetd for my firebird rdbms.

My smb.conf is a rather simple one. Made for a Primary Domain controller, just tdb namespace/security, no LDAP, no Kerberos, no printers, no issues reported by testparm. Has been tested without xinetd and it works fine for what I expect it to do. Meanwhile I have developed a netbios-ssn configuration for xinetd, trying to keep it a bit minimalistic, which goes like this:

service netbios-ssn

{

	port		= 139

	socket_type	= stream

	protocol	= tcp

	wait		= no

	user		= root

	server		= /usr/sbin/smbd

	disable	        = no

}


inside the /etc/xinetd.d folder. Being old school am not using swat. 
I keep the samba services down, expect them to be launched by xinetd on demand, which is exactly what happens.

Under such a scheme samba works very well thank you, yet I am getting a small issue here. Every time I open a new connection on this samba server from a remote XP client, I can see (ps -ef | grep mbd) a new smbd instance being launched, plus a couple of smbd zombies, each one a child to the first -non zombie- instance. 

Being zombies, these two smbd instances cannot be killed, unless of course the parent instance is killed as well, which of course closes down the connection.

If I would open another connection, from say another XP client, then another three smbd instances are brought, again the later two of them zombie children to the first of the three.

Am happy to report, that all three smbd instances are killed by themselves, once the connection is closed.

Am using ubuntu 9.04 server, fully patched.

So here is my point. All right, it works, yet this does not seem pretty good to me. Do not know if this is supposed to be normal, yet each one of the zombies consumes its own resources, I can find no reason in wasting without a reason. Have tried to include the server_args = -F clause, without success.

Have googled “**samba and xinetd**”, not much have been found. To make things worse [www.xinetd.org](www.xinetd.org) is not avail, while every reference I have found on xinetd at [www.samba.org](www.samba.org) is swat related. 



cheers everyone

---

### Post by vpablos on 2010-10-20
I'm currently using this configuration

service netbios-ssn
{
	disable		= no
#	type		= UNLISTED
	id		= netbios-ssn
#	port		= netbios-ssn
	socket_type	= stream
	protocol	= tcp
	user		= root
	wait		= no
	instances	= 5
	server		= /usr/sbin/smbd
}                                                                               

# This is the udp version.
service netbios-ns
{
	disable		= no
#	type		= UNLISTED
	id		= netbios-ns
#	port		= netbios-ns
	socket_type	= dgram
	protocol	= udp
	user		= root
	wait		= yes
	instances	= 5
	server		= /usr/sbin/nmbd
}

I've taken and adapted it from:

[http://www.comptechdoc.org/os/linux/usersguide/linux_ugsamba.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugsamba.html)
[http://books.google.com/books?id=EaRyTDUns_YC&pg=PA66&lpg=PA66&dq=samba+inetd&source=bl&ots=YIrvhshHym&sig=GAoTtHgMPjVHq5cAYMM8TaXSWWA&hl=en&ei=RdK-TO2LFom6jAfNse20Ag&sa=X&oi=book_result&ct=result&resnum=7&ved=0CDsQ6AEwBjgK#v=onepage&q=samba%20inetd&f=false](http://books.google.com/books?id=EaRyTDUns_YC&pg=PA66&lpg=PA66&dq=samba+inetd&source=bl&ots=YIrvhshHym&sig=GAoTtHgMPjVHq5cAYMM8TaXSWWA&hl=en&ei=RdK-TO2LFom6jAfNse20Ag&sa=X&oi=book_result&ct=result&resnum=7&ved=0CDsQ6AEwBjgK#v=onepage&q=samba%20inetd&f=false)

---

### Post by vpablos on 2011-01-03
In last versions there is a problem with instances parameter. The correct configuration is the following one:

service netbios-ssn
{
disable = no
# type = UNLISTED
id = netbios-ssn
# port = netbios-ssn
socket_type = stream
protocol = tcp
user = root
wait = no
instances = 5
server = /usr/sbin/smbd
}

# This is the udp version.
service netbios-ns
{
disable = no
# type = UNLISTED
id = netbios-ns
# port = netbios-ns
socket_type = dgram
protocol = udp
user = root
wait = yes
instances = 1
server = /usr/sbin/nmbd
}

---

