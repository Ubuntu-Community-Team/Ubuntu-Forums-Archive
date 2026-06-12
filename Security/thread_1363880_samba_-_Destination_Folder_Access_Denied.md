---
title: "samba - Destination Folder Access Denied"
date: 2009-12-25
forum: Security
---

### Post by jfernandez1977 on 2009-12-25
Hi,

I'm new to ubuntu and samba.  I have 2 machines, one has Ubuntu 9.10 and the other is running Vista.  I have just installed Samba on Ubuntu machine.  I could see the shared directory from my Vista machine, but when I tried to copy files into the shared directory, I got the "You need permission to perform this action" error.

in smb.conf file, I set "security = share" and the shared folder's permission is 777.

Could somebody point out what security area I have missed.  Thank you.



JF

---

### Post by xmtrdude on 2009-12-26
I am having the exact same problem in Jaunty 9.04.  Anybody?

---

### Post by CharlesA on 2009-12-27
You need to make sure that the file permissions allow you access as well. Have you added yourself as a rw user?

---

### Post by xmtrdude on 2009-12-28
CharlesA - sorry so long on the reply... holidays you know.  Yes, I have added myself as user in both SYSTEM>ADMINISTRATION>USERS & GROUPS and in Samba.  I am using the Samba Configuration tool.  I have also tried editing smb.conf directly in gedit, and setting "security=share" AND "security=user", and neither seems to work.  In the Samba configuration tool, it says that all the shared folders are set rw, and I have set access on all the folders to allow everyone.

On the flipside, in Ubuntu PLACES>NETWORK, I can see all the other computers on my network, but can not access any of the files on any of them.  It always gives me "Cannot mount destination" message.

Any thoughts?

---

### Post by xmtrdude on 2009-12-31
Bump

---

### Post by Morbius1 on 2009-12-31
Please post the output of the following:

Open **Terminal**
Type** testparm -s**
Type [B]ls -dl /path/to/shared/folder

[COLOR=Blue]EDIT: [/COLOR][/B][COLOR=Blue]There is one more thing you can do. In Vista, open the Command Prompt ( not run but command prompt )[/COLOR][COLOR=Blue]and type [/COLOR][B]:
net view

[/B]If there are any errors post them please.

---

### Post by CharlesA on 2009-12-31
> **Morbius1 said:**
> Please post the output of the following:

Open **Terminal**
Type** testparm -s**
Type [B]ls -dl /path/to/shared/folder

[COLOR=Blue]EDIT: [/COLOR][/B][COLOR=Blue]There is one more thing you can do. In Vista, open the Command Prompt ( not run but command prompt )[/COLOR][COLOR=Blue]and type [/COLOR][B]:
net view

[/B]If there are any errors post them please.

That is a nice command. Thanks!

@xmtrdude: Are there any firewalls running on the machine doing the serving and the  machines that are the clients? Port 445 needs to be open.

---

### Post by xmtrdude on 2009-12-31
mark@upstairs:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Documents]"
Processing section "[Music]"
Processing section "[Pictures]"
Processing section "[Videos]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    encrypt passwords = No
    map to guest = Bad User
    obey pam restrictions = Yes
    passdb backend = tdbsam
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Documents]
    path = /home/mark/Documents
    read only = No
    guest ok = Yes

[Music]
    path = /home/mark/Music
    read only = No
    guest ok = Yes

[Pictures]
    path = /home/mark/Pictures
    read only = No
    guest ok = Yes

[Videos]
    path = /home/mark/Videos
    read only = No
    guest ok = Yes
mark@upstairs:~$ ls -dl /home/mark/Music
drwxr-xr-x 3 mark mark 4096 2009-12-28 19:38 /home/mark/Music

I just picked one of the folders at random for the last command.  Do you need to see them all?

Typing "net view" at the command prompt in Vista returns:

"System Error 1240 has occurred.

The account is not authorized to log in from this station."


@CharlesA: no firewalls on any of the machines.  The network is behind a firewall on the router.

---

### Post by Morbius1 on 2009-12-31
There's actually two things wrong with your setup so let's see if this fixes it:

Open **Terminal **
Type **gksu gedit /etc/samba/smb.conf**

Look though the file for this line:
> encrypt passwords = NoAnd put a # sign in front of it:
> [COLOR=Blue]#[/COLOR]encrypt passwords = NoSecond, and this is a little unorthodox in the "Classic Samba" world, all your shares have guest access and write enabled but your linux file permissions for "others" which would be guest ( at least on the one you posted ) allow for read only. You could change the permissions on your files or you can use this technique instead:

In the [COLOR=Blue][global][/COLOR] section of smb.conf add the following line:
> force user = markSave the smb.conf file, exit gedit, and back in the Terminal type:
**sudo service samba restart**

Wait a few minutes and see if you can access the files.

---

### Post by xmtrdude on 2009-12-31
OK, that's got me going.  I can now write to my shared folders on the Ubuntu box.  Thanks!
However, I still have the same problem going from Ubuntu to Vista.  I can see the computers on the network, but when I try to open them, Ubuntu gives me "Unable to mount location -- Failed to retrieve share list from server."

Any ideas?

---

### Post by Morbius1 on 2009-12-31
Well, lets go see if we can get any errors with these. They should scan the network if there's a problem give you an error.

Open **Terminal**
Type **findsmb**
Type **smbtree**

---

### Post by xmtrdude on 2009-12-31
mark@upstairs:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.10.4    UPSTAIRS      +[WORKGROUP] [Unix] [Samba 3.3.2]
192.168.10.6    DOWNSTAIRS     [DOWNSTAIRS] [Windows Vista (TM) Home Premium 6002 Service Pack 2] [Windows Vista (TM) Home Premium 6.0]
mark@upstairs:~$ smbtree
Password: 
WORKGROUP
    \\VISTA-LAPTOP           
timeout connecting to 63.123.155.104:445
timeout connecting to 63.123.155.104:139
cli_start_connection: failed to connect to VISTA-LAPTOP<20> (0.0.0.0). Error NT_STATUS_ACCESS_DENIED
    \\UPSTAIRS               upstairs server (Samba, Ubuntu)
        \\UPSTAIRS\Deskjet-D1500-series    HP Deskjet D1500 series
        \\UPSTAIRS\IPC$               IPC Service (upstairs server (Samba, Ubuntu))
        \\UPSTAIRS\Videos             
        \\UPSTAIRS\Pictures           
        \\UPSTAIRS\Music              
        \\UPSTAIRS\Documents          
        \\UPSTAIRS\print$             Printer Drivers
    \\DOWNSTAIRS             Downstairs
timeout connecting to 63.123.155.104:445
timeout connecting to 63.123.155.104:139
cli_start_connection: failed to connect to DOWNSTAIRS<20> (0.0.0.0). Error NT_STATUS_ACCESS_DENIED


For clarification, "DOWNSTAIRS" is the name of the Vista desktop I am attempting to connect to, and "VISTA-LAPTOP" I guess is pretty self explanatory.  "UPSTAIRS" is the Ubuntu box.

---

### Post by Morbius1 on 2010-01-01
OK, it appears as though in order to resolve both the vista machines netbios names, Ubuntu is actually leaving the LAN (63.123.155.104). I'm guessing that's the public IP Address of your router.

This has happened to someone I worked with before and this resolved the matter. Whether it works for you I cannot guarantee.

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

Add the following line to [COLOR=Blue][global][/COLOR] section of smb.conf:
```
**[COLOR=Black]name resolve order = bcast host lmhost wins[/COLOR]**
```By default bcast is last in smb.conf but in a home network it's the only one that's functional.

Save the file, exit gedit, and in the Terminal type: [B]sudo service samba restart

[/B]If it doesn't work you can always go back and comment out ( add a # sign in front of the line ) that line and restart samba again.
There is something you can do on the Windows machines about this but I'm trying to avoid even suggesting it because the last thing you should do is listen to windows advice on a linux forum  [B]:wink:
[/B]

---

### Post by xmtrdude on 2010-01-01
That worked!  I now have a functional network!  I did have to reboot the machine, though.  Just restarting the Samba service didn't completely do it.  I really appreciate all the help.  I consider myself fairly knowledgeable on the Windows side of things, but I'm still pretty new to the Linux stuff.

By the way, I don't know where that IP address came from.  I thought the same as you, that it was the public side of my router, so I logged into the router and checked, and it isn't.  I ran whois on it and it came back as a number belonging to Verizon.  Don't know why that would be, my ISP is Comcast.

Anyway, thanks for all the help!

---

### Post by Morbius1 on 2010-01-01
You're very welcome. Occasionally I get one of these networking questions right :)

You know, I just realized you hijacked this thread and I was an accomplice. I hope we don't end up in forum prison [-o<

I wonder if the original poster got anything out of this.

---

### Post by xmtrdude on 2010-01-01
I noticed that, too.  Actually, I don't know if it qualifies as "hijacking" since it is the same subject.  "Piggy-backing" maybe.  I know! Let's call it "Tag-team"! :biggrin:

Maybe the OP won't mind if it solves his problem, too.

---

### Post by chiriones on 2010-01-03
I had the same problem with the address 63.123.155.104 and I have Comcast as well.  I did a google search on Comcast  63.123.155.104 and saw that others are having the same problem.  Apparently Comcast's DNS nameserver is resolving any unrecognized hostname to 63.123.155.104.  

I resolved the problem using "name resolve order" in my smb.conf as well, but I put WINS before bcast and enabled WINS:

[global]
 wins server = 10.0.0.18
 name resolve order = wins bcast lmhost host

It is described in the samba documentation here: [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html#id2583584](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html#id2583584)  

The tips on this forum were very helpful to me for finding a solution.  Thanks to all who contributed.

---

### Post by ragbash on 2010-01-19
> **Morbius1 said:**
> OK, it appears as though in order to resolve both the vista machines netbios names, Ubuntu is actually leaving the LAN (63.123.155.104). I'm guessing that's the public IP Address of your router.


Ok, this is kind of eerie.. I recently switched ISPs and lost my DSL provided DSL/router combo (which I loved, it had built in DNS and some of the best functionality I've ever seen in a router). So I had to switch to a Linksys and my Samba went kind of goofy. Checking some things via the command line, I stumbled upon something I found odd:

$ smbclient -L windows_box        
timeout connecting to 63.123.155.104:445
timeout connecting to 63.123.155.104:139
Error connecting to 63.123.155.104 (Operation already in progress)
Connection to windows_box failed (Error NT_STATUS_ACCESS_DENIED)

Since I had no clue whose IP that was, and I couldn't locate it with any reverse lookup utilities, I decided to google it and found this thread. It is not my public IP, an IP associated with my network, a DNS server I use, or even part of my ISP's IP scheme.. I'm completely baffled why my box is trying to communicate with whatever machine that is, especially on ports generally considered proprietary to Windows.. Anybody have any insight into this?

I've also been seeing various oddities since the router swap such as:

$ ping google.com
PING google.com (72.14.204.147) 56(84) bytes of data.
YPBINDPROC_DOMAIN: Domain not bound
YPBINDPROC_DOMAIN: Domain not bound

$ smbclient -L windows_box
YPBINDPROC_DOMAIN: Domain not bound
YPBINDPROC_DOMAIN: Domain not bound


This is on a network with a Windows XP machine hosting 5 SMB shares and the linux box is running Samba version 3.028 on a Ubuntu Linux 8.04.1 platform with two data shares and a user home share.. Of course, all shares are on the same workgroup, both machines are on the same subnet, using the same router, etc.. All that changed really was the router.. 

$findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
$

---

### Post by ScottJ97 on 2010-02-21
> **ragbash said:**
> 
Since I had no clue whose IP that was, and I couldn't locate it with any reverse lookup utilities, I decided to google it and found this thread. It is not my public IP, an IP associated with my network, a DNS server I use, or even part of my ISP's IP scheme.. I'm completely baffled why my box is trying to communicate with whatever machine that is, especially on ports generally considered proprietary to Windows.. Anybody have any insight into this?


What's happening is that Comcast's DNS server is attempting to redirect a nonexistent domain name to their search page, rather than returning a proper NXDOMAIN. This is a dirty trick by Comcast.

Try doing nslookup of various one-word domains: google, dflkbfkljg, etc. They will all return 63.123.155.104.

So somehow your PC is trying to contact a server using a one-word name and instead of getting the appropriate server on your LAN, it thinks it's an Internet domain name and it's going out to DNS and getting this bogus IP address from Comcast.

DNSMasq can fix the DNS issue using the 'bogus-nxdomain' option. My home router is a Linksys WRT54G running DD-WRT firmware and it uses DNSMasq for DNS. I added one line to the "Additional DNSMasq Options" in the web setup:

```
bogus-nxdomain=63.123.155.104
```This won't solve your problem but I hope it will get you one step closer.

---

### Post by ScottJ97 on 2010-02-21
> **ScottJ97 said:**
> What's happening is that Comcast's DNS server is attempting to redirect a nonexistent domain name to their search page, rather than returning a proper NXDOMAIN. This is a dirty trick by Comcast.


Actually I just figured out there's an easier way. Go to [http://dns-opt-out.comcast.net/](http://dns-opt-out.comcast.net/) and follow the instructions.

---

### Post by james840a on 2011-02-13
Hello,

I'm new to ubuntu/samba servers. I am running a test so i can get use to linux, I have 2 machines, one has Ubuntu Server 10.04 with Samba and the other is running Vista. I can see the shared directory from my Vista machine and map to it, but when I tried to copy/create files/folders into the shared directory, I got the "You need permission to perform this action" error. I am using SWAT and Webmin to administrate the Samba and future email/web server. I have created a couple users with passwords to login to the shared folder. But they can only read, and i have them as read/write

have I missed something thanks,

 attached is my smb.conf

# Samba config file created using SWAT
# from UNKNOWN (192.168.1.8)
# Date: 2011/02/13 17:00:57

[global]
    netbios name = SA_SMB_SERVER
    server string = %h server (Samba, Ubuntu)
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    default service = share
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    
[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[share]
    comment = Share
    path = /srv/samba/share
    write list = @users
    read only = No
    create mask = 0777
    directory mask = 0777

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

---

### Post by rvchari on 2011-02-13
> **jfernandez1977 said:**
> Hi,

I'm new to ubuntu and samba.  I have 2 machines, one has Ubuntu 9.10 and the other is running Vista.  I have just installed Samba on Ubuntu machine.  I could see the shared directory from my Vista machine, but when I tried to copy files into the shared directory, I got the "You need permission to perform this action" error.

in smb.conf file, I set "security = share" and the shared folder's permission is 777.

Could somebody point out what security area I have missed.  Thank you.



JF

i am not an linux expert but i am able to successfully connect to my office windows machine.
i simply right clicked on the folders / drive that i access from my windows machine, went to properties and activated share.
after this, i clicked on places > network on my ubuntu laptop and selected the share folder.
my user name in windows machine is different from what i use in ubuntu but i connect with the username and password of my windows machine and i made it to remember password parmanently.

now i can access my windows with ease....
i never had to redo any config or tweaking.... samba took care of everything...

sometimes our solution lies in the simplicity and we tend to go round and round.... (i struggled a lot to understand samba in the initial stages !!!)

also check if ur auto DHCP is enabled...

---

### Post by Morbius1 on 2011-02-14
james840a:

Dealing with actual Servers ( with a capital S ) is a little out of my comfort zone but I have the following observations:

(1) If you use SWAT always run the following command since SWAT is destructive in that it doesn't modify the existing smb.conf it replaces it with it's own which puts the burden on you to get it just right:
```
testparm -s
```If you do it for example on the smb.conf you posted you would have seen the following error message:
> ERROR: the 'unix password sync' parameter is set and there is no valid 'passwd program' parameter.(2) default service = share
I'm not personally familiar with that parameter. I looked it up in man smb.conf which didn't help me much as the samba documentation seems to be written for a different species than human. I'll try to see if I can find examples of what that does exactly.

(3) The error message from your original post appears not to be a samba problem but a linux file permissions problem. Make sure the permissions on the target folder is consistent with your authentication parameters in smb.conf.

Do a:
```
ls -dl /srv/samba/share
```Will it allow the members of "@users" to write to that directory?

---

### Post by james840a on 2011-02-14
Thanks for the reply,

When i did the testparm -s  i did get the error ERROR: the 'unix password sync' parameter is set and there is no valid 'passwd program' parameter.  which i will search later

i didnt try the ls -dl /srv/samba/share  yet but will on another share

but i did try  chmod 777 /srv/samba/share
and that worked.

I think i will stay away from SWAT, but i will stick with Webmin as i need to be able to admin it remotely. Have any of you used Webmin?

I am very new to Linux, but my friend is a linux guy but not in servers. Our office wants to set up new servers for File and print, Web site, Email and FTP. So i am jumping into it and learning. I come from the MCSE background from the late 90's with NT/2000 

Thanks for the support and im sure i will have many more questions in the future.

Ja

---

