---
title: "Samba problem please check my .conf file"
date: 2009-01-18
forum: Server Platforms
---

### Post by Jeztastic on 2009-01-18
Hi,

I have tried to follow [this tutorial here]("http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+usernames") but with no success. Windows is still unable to map the network drive.

```
[global]
    ; General server settings
    netbios name = server
    server string =
    workgroup = 2WIRE778
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[sambaserver]
    path = /home/jez/samba
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = jez
    force group = jez
```

I am not sure I completely understand the instructions regarding usernames - which need to be Windows, Ubuntu, or Samba usernames. My Ubuntu box is <jez@server>, and my windows laptop is <jezxp>, but I'm not sure if I've done this right.

---

### Post by cmnorton on 2009-01-18
A good thing to try is running smbpasswd on the Ubuntu system. This will create your samba user and password. If you are mounting Windows drives with my-name my-passwd, then Ubuntu's samba server needs to know that information. I always add it with smbpasswd.

---

### Post by Jeztastic on 2009-01-18
> **cmnorton said:**
> A good thing to try is running smbpasswd on the Ubuntu system. This will create your samba user and password. If you are mounting Windows drives with my-name my-passwd, then Ubuntu's samba server needs to know that information. I always add it with smbpasswd.

I have used smbpasswd, but was unsure whether to give my windows or ubuntu username/password. I went for my ubuntu username, not sure if this is correct.

The other thing is that smb.conf mentions a smbuser file which I do not appear to have.

---

### Post by capscrew on 2009-01-18
Quoting [http://computer-vet.com/tech/linuxfileserver.html]("http://computer-vet.com/tech/linuxfileserver.html")

> smbusers

You also might need to edit the /etc/samba/smbusers file if you want to give certain users special access to the computer. By default, Linux will look at the Windows user name that is accessing files, and try to match it to a user name on the Linux system. If one doesn't exists, it will give it the permissions of the lowly nobody user. Since we mounted our directory with read/write access for everyone, that shouldn't matter. But for a higher level of control, use /etc/samba/smbusers. You can either add each user name in as a Linux user, or you can map them to an existing Linux user in smbusers. Edit the file, and add lines like this:

   root = administrator scotts

This line will take the administrator and scotts Windows user names and give them root access on Linux. Possibly not the best configuration, but the easiest if your security needs are light. And handy for remote

Edit: Create your own /etc/samba/smbusers file

---

### Post by Jeztastic on 2009-01-18
Thanks capscrew. That tutorial clears up a few things for me. So hard to find tutorials that actually explain things properly, rather than listing commands you don't understand.

---

### Post by Jeztastic on 2009-01-30
OK, still getting nowhere. I have set everything up umpteen times, but still unable to connect. Windows seems to be able to recognise that there is a computer called 'server' on the network, but is unable to connect to it. Please help! This is driving me nuts!

---

### Post by capscrew on 2009-01-30
Post your smb.conf file again.

---

### Post by Jeztastic on 2009-01-30
```
[global]
	name resolve order = hosts wins bcast
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
	announce version = 5.0
	username map = /etc/samba/user.map
	null passwords = yes
	encrypt passwords = yes
	passdb backend = tdbsam
	netbios name = server
	server string = 
	printing = CUPS
	path = \
	default = sambaserver
	workgroup = 2wire778
	syslog only = yes
	os level = 20
	printcap name = CUPS
	syslog = 1
    ; General server settings





; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[sambaserver]
    path = /home/jez/samba
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = jez
    force group = jez
```

XP can see the home network - named 2wire778. However it then gives me an error massage that it's not accesible. Starting to think windows is the problem, not linux. There's a surprise...

---

### Post by capscrew on 2009-01-30
Jez,

I don't think it is a Windows problem.  There are problems with your smb.conf file.

First, you have not described that type of security to be used.  If you don't feel the need for any security other than the file permissions, then describe it in the Global section as: ```
security = share
```

Second, you allow guest in the share, but have not defined what account is to be used as the guest.  The guest account is described in the Global section as:```
#  Bad user means "user not found in unix passwd" and 
#  we will default to the guest account that we have defined  
        map to guest = bad user
# This is the user account with the name "nobody"
        guest account = nobody


```

I suggest you take a deep breath -- relax, and start over.  Do you have a copy of the original, unmolested smb,conf file?  If not, no problems.  There should be a copy at:> /usr/share/samba/smb.conf  

I would rename any/all of the smb.conf versions you have been messing with and copy the original to /etc/samba/smb.conf.  I would make a copy in that directory as smb.conf.original.  Now you can modify the smb.conf file without worry.

Read as much as you can from [**www.samba.org/samba/docs/**]("www.samba.org/samba/docs/")

If you have questions and want to google for the answer (a good idea) append this to the search keywords > site:[www.samba.org/samba/docs/](www.samba.org/samba/docs/)

Make it simple.  Here is a simple share that works:```
[Test]
        comment = Beachbees Test Share
        path = /smb/test
        guest ok = yes

        writable = yes
        create mask = 0770
        directory mask = 0770


```

Let me know if you need further help.

---

### Post by Jeztastic on 2009-01-31
```
[global]
workgroup = 2wire778
netbios name = server
encrypt passwords = yes
username map = /etc/samba/smbusers
security = share
guest ok = yes
guest account = jez
 

[sambaserver]
path = /home/jez/samba
writable = yes

```

Still not working, and I've tried to make everything as simple as possible.

The share shows up in Webmin, and tells me that it's Read/Write to everyone...

---

### Post by capscrew on 2009-01-31
Exactly how is it not working?  What error messages?  What can't you accomplish?

Are you still using webmin to configure the smb.conf file?

---

### Post by Jeztastic on 2009-01-31
No, I'm configuring the conf file directly. I'm using Webmin's text editor, but I don't see that that would make a difference. 

I have been attempting to map the share as a network drive. I directed XP to look for \\server\sambaserver. I get the error mesage:```
the network path \\server\sambaserver could not be found
```

I have also attempted to search for the share using My Network Places > Add Network Place. When I do this, XP will find the workgroup 2wire778 in Microsoft Windows Network, but will not interact with it any further.

---

### Post by capscrew on 2009-01-31
> **Jeztastic said:**
> No, I'm configuring the conf file directly. I'm using Webmin's text editor, but I don't see that that would make a difference. 

I have been attempting to map the share as a network drive. I directed XP to look for \\server\sambaserver. I get the error mesage:```
the network path \\server\sambaserver could not be found
```

I have also attempted to search for the share using My Network Places > Add Network Place. When I do this, XP will find the workgroup 2wire778 in Microsoft Windows Network, but will not interact with it any further.

Have you tried \\ip_address\share ?  Can you ping the host server?

Edit: The last question shows why you should not use hostnames that are ambiguous.  I am asking if you can ping the host you have named "server" by name.

---

### Post by Jeztastic on 2009-01-31
Yes and yes.

I am also getting an error message:```
2wire778 is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to check if you have access permissions. The network path is not found.
```

I have no idea how to edit permisions on the workgroup. If this is the problem I will google it... I have had a poke around in the router, doesn't seem that the problem is there...

---

### Post by capscrew on 2009-01-31
> **Jeztastic said:**
> Yes and yes.

Yes what?  I can't help you if you won"t carry on a conversation.  

Are you saying that the unc \\ip_address\share fails?

Are you saying that you are successful when you ping server?

---

### Post by Jeztastic on 2009-01-31
hang on, we are cross posting I think. I am carrying on the conversation as best I can! Yes, I can ping server, and yes, I have tried unc \\ip_address\share which also fails. I apologise if my answer wasn't as clear as I though it was.

---

### Post by capscrew on 2009-01-31
Is the XP client in the same workgrop as "server" (Samba)?  Why is your smb.conf file so minimal?

---

### Post by Jeztastic on 2009-01-31
Yes, the client is in the same workgroup as the server. The smb.conf is minimal because I am just trying to get the share to work. I read [www.samba.org/samba/docs/](www.samba.org/samba/docs/) and googled, and tried to build the minimum I needed to get it to work. If there's less in there, there's less to go wrong. 

If I am missing something vital please tell me.

---

### Post by capscrew on 2009-01-31
Jez,

I am attaching a smb.conf.txt file. Rename it and try it without any changes to the content other than your workgroup and the path to the share.  

Make sure you are in the smbpasswd database (smbpasswd -a).

I need to be away for the 4 or so hours.  I will check back then.

Good luck,

Cap

**Edit: ** [COLOR="DarkGreen"]It's 5 hours later.  How did you do?  Did it work?[/COLOR]

---

### Post by Jeztastic on 2009-02-01
Thanks Capscrew! Still not there yet, but closer... I can now see Server in the workgroup from XP. However, I cannot access the share.

I get an error message:

```
\\Server is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions. The network path was not found.
```

smb.conf:

```
#
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Workgroup/NT-domain name your Samba server will part of
        workgroup = 2wire778

# server string is the equivalent of the NT Description field
   ;hostname
        server string = Ivy Place Server

# This will prevent nmbd to search for NetBIOS names through DNS.
        dns proxy = no

        netbios name = Server

#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
        log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
        max log size = 1000

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead.
        syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
        panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server.
        security = share

# Samba will need to know what password database type you are using.  
        passdb backend = tdbsam

        obey pam restrictions = yes

#  Bad user means "user not found in unix passwd" and 
#  we will default to the guest accout that we have defined  
        map to guest = bad user
        guest account = nobody

# No root user!
        invalid users = root

# This controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;       unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;       pam password change = no


############ Misc ############

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
;       socket options = TCP_NODELAY
        username map = /etc/samba/smbusers


#======================= Share Definitions =======================
# Basic Share for testing
# 

[samba]
        comment =  Samba Share
        path = /home/jez/samba
        guest ok = yes
        writable = yes


```

smbusers:

```
jez = jezxp
```

---

### Post by Jeztastic on 2009-02-01
Ok, really baffled now. I've gone away and come back, and I can't access the workgroup again. Nothing's changed.
[Edit] It's *&%$@! Zonealarm!!! Everything works if I turn Zonealarm firewall right off!!! Aaaargh!!!

Adding the server ip address to Zonealarm solved it. Be warned people. I feel vindicated too - I thought the problem seemed to be at the Windows end. 

Thanks for your help Capscrew.

---

### Post by capscrew on 2009-02-01
Jez,

Does this mean you still can see server in the workgroup?

Lets try something with the file system.  On the Ubuntu host (server), I would like you to create this structure /srv/samba.

Set the permissions to 0777 on the /srv and the /srv/samba directory.

Modify the [samba] share path.

Lets see how that works.

---

### Post by Jeztastic on 2009-02-01
Hi, maybe I wasn't clear, it all works OK now. I added the server's ip address to the Windows firewall safe list, and I can see all my shares. In fact, I added an extra share just for fun. :-) 

The plus side to this is I now know a whole lot more about Samba than I would have done otherwise. Enjoy the superbowl, I hope you got better weather in California, it's snowing here in the UK!

---

### Post by capscrew on 2009-02-01
Glad it all works.  The temp here is 23 C.  :D

---

