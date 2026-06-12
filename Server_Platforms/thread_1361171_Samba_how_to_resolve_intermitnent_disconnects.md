---
title: "Samba: how to resolve intermitnent disconnects?"
date: 2009-12-21
forum: Server Platforms
---

### Post by Icky_Ev on 2009-12-21
Running Samba 3.3 on 9.04 to support approx a dozen Windows stations. Have XP SP2 up to 7. Client boxes are set up with samba box as WINS server and LM/Hosts enabled, NETBios enabled over TCP/IP. 

There have been constant ongoing issues, and I'm about to rip my hair out- and the rest of the team is probably ready to come help! 

Sometimes there are no problems whatsoever- the computers all hop right onto the samba share and play nice all day. More typically, at least a couple have issues throughout the day. 

1) Win boxes refusing to see the server, via "Map Network Drive", "Network Places" and cmd. CMD/Net Use usually spits out "network path not found"

2) Win boxes seeing the server but refusing to connect to the server (network path not found, network drive inaccessible, etc) 

3) Win boxes randomly disconnecting from the server and refuses to reconnect.

Restarting the Windows boxes sometimes fixes it, sometimes ipconfig/release/renew works, and usually disabling the network interfaces entirely for about 3 minutes fixes things. And sometimes the only thing you can do is wait until it decides to work again. 

Restarting samba assures total network meltdown. 

Please, please, PLEASE tell me you spot some glaring newb error in my samba config file:

```


[globa]
read raw = no
write raw =no
name resolve order = hosts wins bcast
announce version = 5.0
socket options = TCP_NODELAY
read prediction = true
force directory mode = 
deadtime =0
null passwords = true
username map = /etc/samba/smbusers
passdb backend = tdbsam
keepalive = 600
wins support = yes
netbios name = FUNGUS
server string = 
printing = CUPS
revalidate = yes
workgroup = FUNGUS
force create mode =
syslog only = yes
printcap name = CUPS
security = user
syslog = 1
read size = 65536


[My Files ]
writeable =yes
path = /FUNGUS/samba
guest ok = no


```

---

### Post by Muttley99 on 2009-12-21
This may sound picky but you missed the [l] out of global! 

Where's your [homes] section?
TBH, can't remember whether it was Windows or Linux required!

Also, didyou testparm your config file?

testparm smb_conf

---

### Post by Icky_Ev on 2009-12-21
Heh, global is in the actual file. Minor typo on my part. ;) I was eyeballing the smb.conf since the server and my daily driver aren't on the same network.

Homes is commented out. We don't use them. Possible clue? 

Here is the result of testparm... 

running testparm smb_conf resulted in unable to load configuration file. Coaxed it to work by going into /etc/samba and runnign testparm smb.conf. If that's a clue. 

```

loading smb config files from smb.conf
Unknown parameter encountered: "read prediction"
Ignorning unknown parameter: "read prediction"
Invalid octal number force directory mode
Unknown parameter encountered: "revalidate"
Ignorning unknown parameter "revalidate"
Invalid octal number force create mode
Unknown parameter encountered: "read size"
Ignoring unknown parameter "read size"
Processing section "[Profiles]"
WARNING: No path in service Profiles - making it unavaliable!
NOTE: Service Profiles flagged unavailable.
Processing section "[prints]"
Processing section "[printers]"
Processing section "[MyFiles]"
Loading services file OK.
Server Role: ROLE_STANDALONE

```

---

### Post by Muttley99 on 2009-12-22
Create a log file;

Add this to your [global] section;

[HTML]log file = /var/log/samba/%m.log
max log size = 100[/HTML]

This should log each workstation connection to the server.

Post your log here.
I'll try and help but there are other people much more experienced than me with this; lets hope they can help! :)

Also, I would suggest you comment out the errors found in the tesparm!

I think windows also require encrypted passwords;

[HTML]encrypt passwords = yes[/HTML]

---

### Post by Icky_Ev on 2009-12-22
Log file rolling. Also have commented out the errors and have a clean testparm now. 

Have not added the encrypted passwords- one change at a time. ;) 

Will report back! :lolflag:

---

### Post by Icky_Ev on 2009-12-22
We've had most of the usual issues here today and nothing in the log files. 

The only thing in any of the log files are the same errors testparm showed. :\

---

### Post by Muttley99 on 2009-12-23
> **Icky_Ev said:**
> We've had most of the usual issues here today and nothing in the log files. 

The only thing in any of the log files are the same errors testparm showed. :\

You commented out the errors! Are you reading the correct smb.conf file?
Check with this command;

[HTML]smb -b | grep smb.conf[/HTML]

Also add;

[HTML]log level = 3[/HTML]

to [global]

If you see no problems tomorrow, change the logging from each machine to each share: alter the log line;

[HTML]log file = /var/log/samba/%S.log[/HTML]

Also your workstations, have you mapped each to a drive by adding the ip OR the workgroup name?

---

### Post by Icky_Ev on 2009-12-23
> **Muttley99 said:**
> You commented out the errors! Are you reading the correct smb.conf file?
Check with this command;

[html]smb -b | grep smb.conf[/html]



I'm getting "smb: command not found"  :\


> **Muttley99 said:**
> 
Also your workstations, have you mapped each to a drive by adding the ip OR the workgroup name?

We've tried  \\FUNGUS\MyFiles, by the IP and by its FQDN (fungus.pond.lan). We've found that using \\FUNGUS is the best option 95% of the time.

---

### Post by msw on 2009-12-23
I noticed in your smb.conf that the netbios name and workgroup are the same name. This a no no in  Linux/Samba and Windows networking.

Have you fixed all the other errors in the smb.conf after running testparm?

---

### Post by Muttley99 on 2009-12-23
msw made a good point! they shouldn't be the same.

try;

[HTML]smbd -b ¦ grep smb.conf[/HTML] that should be a pipe! I'm on a windows netbook right now!

The reason I asked about IP or netbios name; to make connections understand your IP relates to your netbios name. This can be added to your /etc/hosts file.
I can't remember the correct method of making this entry, but it should be as simple as entering;

[HTML]192.168.x.x /Fungus[/HTML]

just google 'etc/exports linux' to be sure of the correct syntax.

---

### Post by Icky_Ev on 2009-12-23
> **Muttley99 said:**
> msw made a good point! they shouldn't be the same.


Ah-ha! Maybe that's it. I'll change that after everyone has gone home tonight. As of this moment, everything is working, and restarting samba always upsets things badly. 

> **Muttley99 said:**
> 
try;

[html]smbd -b ¦ grep smb.conf[/html] that should be a pipe! I'm on a windows netbook right now!


Result is:

CONFIGFILE: /etc/samba/smb.conf

> **Muttley99 said:**
> 

The reason I asked about IP or netbios name; to make connections understand your IP relates to your netbios name. This can be added to your /etc/hosts file.
I can't remember the correct method of making this entry, but it should be as simple as entering;

[html]192.168.x.x /Fungus[/html]just google 'etc/exports linux' to be sure of the correct syntax.

[/quote]

Already have that set up- I think, I'll double check the syntax though. 

Thank you for the help, I really do appreciate it.

---

### Post by msw on 2009-12-23
The proper entry for both Windows and Linux host files are:

192.168.xx.xxx   mywindowspc

192.168.xx.xxx  mylinuxpc

Now, if you are resorting in editing hosts files on any pc, this tells me that there is something fundamentally wrong with the TCP/IP network. Samba requires a properly configured network to function and without this being so (and along with the netbios name/ workgroup name issue) you have some things to get straightened out in order to get Samba to work flawlessly like it should.

---

### Post by Icky_Ev on 2009-12-23
> **msw said:**
> 
Now, if you are resorting in editing hosts files on any pc, this tells me that there is something fundamentally wrong with the TCP/IP network. Samba requires a properly configured network to function and without this being so (and along with the netbios name/ workgroup name issue) you have some things to get straightened out in order to get Samba to work flawlessly like it should.

I was going to check the server's /etc/hosts. No plans whatsoever to go tampering with the Windows machines. ;) 

Samba is just the only thing having hiccups. The other services are just peachy- is there any problem with running samba services off the same drive running a lamp stack and postfix server? Security threats not withstanding, this network has no internet exposure. ;) 

I will look into your suggestion about the names ASAP this evening. I really do appreciate it. 

I just tell the team one day... ONE DAY... we will be able to afford a REAL network admin. You know. Give everyone an incentive. :popcorn::lolflag:

---

