---
title: "FTP connection problems-help to figure it out"
date: 2008-03-23
forum: Server Platforms
---

### Post by Aliyans on 2008-03-23
hi
   I have been trying to set up ftp on my server for the last few days..i have tried to connect many times to server using cuteFTP cleint with ssl protocol  i will show u my vsftpd conf..below...i have port everthing set in there n local user only enabled.i used  exact same login details ..but it never connected..i think it says connection refused...i tried to login with anonymous user enabled as well with no effect..anybody can figure it out whats wrong?????

[IMG]http://img72.imageshack.us/img72/941/ftperrorvu2.jpg[/IMG]
```
listen=YES

local_enable=YES
userlist_enable=YES
userlist_deny=NO

chroot_local_user=YES
chroot_list_enable=YES

anonymous_enable=NO
anon_root=/home/ftp/
anon-mkdir_write_enable=NO
anon_other_write_enable=NO
anon_upload_enable=NO

write_enable=YES

force_dot_files=YES
dirmessage_enable=YES

xferlog_enable=YES
dual_log_enable=YES

ascii_download_enable=YES
ascii_upload_enable=YES

connect_from_port_20=YES

ftpd_banner=Welcome to FTP server

#Enable download,if set no all download requests will give permisiion denied
download_enable=YES

#If enabled all local logins are forced to use ssl connection for data transfer$
force_local_data_ssl=YES

guest_enable=NO


listen_ipv6=YES

#This command create log file for all ftp requests n responses
log_ftp_protocol=YES

#Set to NO if u want to disable PORT method of data connection
port_enable=YES
#Enable if u want port security checks
port_promiscuous=NO

#Enable this option for secure data connections,instead of openssl
ssl_enable=YES

#only applies if ssl enabled
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES


#Time out for port style data connection
connect_timeout=30

#Time out for data connection with no progress
data_connection_timeout=300
file_open_mode=0666

idle_session_timeout=300

#if vsftpd is in standalone mode this is the port for incoming ftp connections
listen_port=*****

#The max data tranfer rate for local user
local_max_rate=0
local_unmask=077

#if vsftpd in standalone mode,this is the max no of clients connected
max_clients:0
max_per_ip=0
pasv_max_port=0
pasv_min_port=0

secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/root/vsftpd.pem
vsftpd_log_file=/var/log/vsftpd.log
xferlog_file=/var/log/xferlog
```

Below is my /etc/shell    file content..i read in one thread there can be also something wrong..

```

/bin/csh
/bin/sh
/usr/bin/es
/usr/bin/ksh
/bin/ksh
/usr/bin/rc
/usr/bin/tcsh
/bin/tcsh
/usr/bin/esh
/bin/bash
/bin/rbash

```

---

### Post by HermanAB on 2008-03-24
Test the connection with telnet:
$ telnet ip.add.re.ss 21

If you get a response then FTP will probably also work.  If you don't get a response, then either the service is not running or it is blocked in your firewall.

See if the service is running:
$ ps -e | grep ftp

If you are running Firestarter, enable FTP in the GUI.

Cheers,

Herman

---

### Post by Aliyans on 2008-03-24
hi
   thanx Herman for ur help..those to commands not working on xtern or putty terminal[i'm on debian server]..by default there was no firewall ..but i installed firestarter as told in a tutorial while setting it up  which i could configure now only..but even after opening ports in firestarter i couldnt connect by cuteFTP client...accidently i opened  ports[which was meant for putty client] for vnc  diffrent  from usual 5900-5901..in firewall policy..i closed vnc desktop n now i'm not able to login to vncdesktop at all..so uninstalled firestarter n tried again  with no effect. is there any possibility to get vncviewer connect to server back agian??

---

### Post by Aliyans on 2008-03-24
hi
   Now i restarted system i got new vncdesktop..n its running...i checked ur second commad on xterm it did give results..but "$ telnet ipaddress 21" command not found

```
$ ps -e | grep ftp
  2547 ?        00:00:00 sftp-server

```
                i'm able to connect with winscp client..with with no other client like cuteFTP  or filezilla..Anybody can help me here okey..so far 35 views only one gentleman replied...i see huge list of Mods Here ..are they just manage spams n delete threads n posts..or help somebody who needs help or they dont come here very often??? sorry i'm just curious

---

### Post by Aliyans on 2008-03-25
hi
    Nobody????

---

### Post by Mr. C. on 2008-03-25
> **Aliyans said:**
> 
...i checked ur second commad on xterm it did give results..but "$ telnet ipaddress 21" command not found

You don't enter the $ - that's the shell prompt.  It is common to include the shell prompt in examples to help user's know where to enter the commands.  Run:

```
telnet yourserverip 21
```

Show the exact command and its output - don't interpret for us.

---

### Post by Aliyans on 2008-03-27
hi
     No i didnt enter $ in my command..i written that in my post to let u know that i was on user rather than root...that all the fault to found ??

---

### Post by Mr. C. on 2008-03-27
Show the exact command and exact error message - copy / paste, don't interpret.

---

### Post by Aliyans on 2008-03-28
hi
    Exact command : ```
telnet ip.add.re.ss 21  
```
   
    Here ip.add.re.ss = my server ip .Dont take it  as it is there
    Exact Error code :```
bash: telnet: command not found
```

---

### Post by Mr. C. on 2008-03-28
Ok, fair enough.  Install the telnet package "inetutils-telnet".

---

### Post by Aliyans on 2008-03-29
> **Mr. C. said:**
> Ok, fair enough.  Install the telnet package "inetutils-telnet".

hi
    Ok. i have installed it...
Comand used:```
sudo apt-get install inetutils-telnet
```

Out put [last 3 lines]:```
Setting up shishi-common (0.0.30-2) ...
Setting up libshishi0 (0.0.30-2) ...

Setting up inetutils-telnet (1.5.dfsg.1-2) ...


```

Now i tried to use below n see output

Commad : ```
 telnet ip.add.re.ss  21
```
Ouput : ```
Trying ip.add.re.ss...
telnet: Unable to connect to remote host: Connection refused
```

Here i put ip address as my server's ip. i donno i'm correct ot not, i'm trying to connect from my server if i'm using this command on xterm[which is on vncdesktop of my server]. so should i be using my local ip means my home connection ip , is it correct or not? so tried with my ip as well..i have a dynamic ip here[external] n i'm behind a router[wireless] . is there anything with my router??

Command used for local ip:```
telnet  loc.al.ip.  21
```

Output :  ```
Trying loc.al.ip....
telnet: Unable to connect to remote host: Connection timed out
```

---

### Post by Aliyans on 2008-03-29
hi
     Bump...up

---

### Post by Mr. C. on 2008-03-30
Aliyans,

It is difficult to determine what is going on here, as important data has been obfuscated and the description of source and destination hosts and IP addresses is a little confusing.  For example, you say "ip address as my server's ip" - is that the loopback IP 127.0.0.1, your server's private LAN ip, or its public IP?  If you feel the need to obfuscate, you need to be extra clear to help us understand the exact details.

Let's forget telnet for the moment.  From the FTP server machine, do you see that FTP is listening.  Try the netstat command below, and look for the LISTEN line that refers to a service listening on port :21 as shown.  Show that line.  If it doesn't exist, FTP is not listening on that port, which means it is either not running, or configured to listen on another port (but your conf does not suggest that).

```
$ netstat -an --tcp
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
...  
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      
...
```


Now, back to telnet.  The telnet tool was suggested to see if you can connect to the port.  You are trying to help us understand from which IP addresses you can connect and which you cannot.  Let's just try the ftp client itself locally.

From the FTP server itself, try and report what happens with:

```
ftp 127.0.0.1
ftp servers_LAN_IP

```

If that succeeds, try from another machine on the LAN:
```
ftp servers_LAN_IP
```
and show what happens.

---

### Post by Aliyans on 2008-03-30
hi
    Ok i tried it ..here its what i get...
Command: ```
netstat -an --tcp
```

Output : ```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:6001            0.0.0.0:*               LISTEN     
tcp6       0      0 :::5901                 :::*                    LISTEN     
tcp6       0      0 :::80                   :::*                    LISTEN     
tcp6       0      0 :::1630                 :::*                    LISTEN     
tcp6       0      0 ::ffff:**.***.***.:1630 ::ffff:84.***.**.:52658 ESTABLISHED
tcp6       0      0 ::ffff:**.***.***.:5901 ::ffff:84.***.**.:52660 ESTABLISHED
```

NB: those *=my ip[local=server  n external]

   I tried with port 5901 from my cuteftp  ...i'm connecting  but it ended timedout..as shown below... i can even do same with port 80 ..using those protocols i used for 5901[FTP,FTP with TLS/SSL, FTP with AUTH SSL-Explicit   etc]

```
STATUS:>  	[30/03/2008 19:54:25] Getting listing ""...
STATUS:>  	[30/03/2008 19:54:25] Connecting to FTP server... **.***.***.***:80 (ip = **.***.***.***)...
STATUS:>  	[30/03/2008 19:54:25] Socket connected. Waiting for welcome message...
ERROR:>   	[30/03/2008 19:55:26] Timeout (60000 ms) occurred on receiving server response.
STATUS:>  	[30/03/2008 19:55:26] Waiting 30 seconds...
STATUS:>  	[30/03/2008 19:55:56] ============== Attempt #1 ==============
STATUS:>  	[30/03/2008 19:55:56] Connecting to FTP server... **.***.***.***:80 (ip =**.***.***.***)...
STATUS:>  	[30/03/2008 19:55:59] Socket connected. Waiting for welcome message...
ERROR:>   	[30/03/2008 19:56:59] Timeout (60000 ms) occurred on receiving server response.
STATUS:>  	[30/03/2008 19:56:59] Waiting 30 seconds...

```

      Its same for port 5901  as well....here also *=server ip

Commad: ```
ftp 127.0.0.1 ftp servers_LAN_IP
```

Output : ```
bash: ftp: command not found
```

---

### Post by Mr. C. on 2008-03-30
Install the "ftp" package to use command line ftp.

There's too much going on here to follow what you are doing.

I see that you've changed the default FTP listen port.  Comment out the ListenPort directive in vsftdp.conf and restart the server.  Later on, you can change the FTP port if you desire.

Step back, use a basic default configuration and get that working.  If you cannot connect to the FTP server locally, as in :

```
ftp localhost
```

there's no need to go further.

---

### Post by Aliyans on 2008-03-30
hi
    Yes i changed default port for safety purpose..there was a attack[hack] in the subnet of my server just few days after i taken it..u know better than me may be, all these things.I dont to xpose those in a publicly viewed post.but i dont understand why those ports[5901,6001,80 n 1630]which i didnt written in vsftpd.conf is shown listen in "netstat -an --tcp" command output.??? 

Okey...

Command:```
ftp localhost
```
Output:```
ftp: connect: Connection refused
```

I tested those ports above with my server..n results are below with commands..if u can make out anything!!
```
$ftp **.***.***.***  5901
Connected to **.***.***.***.
RFB 003.003

$ftp **.***.***.*** 1630
Connected to **.***.***.***.
SSH-2.0-OpenSSH_4.3p2 Debian-9
```

 And this the port i given directive in vsftpd.conf n when i tested it refused it..
```
$  ftp **.***.***.***  55778
ftp: connect: Connection refused
```


    I also want to show u..my current vsftpd.conf  again n u can see the port as well
```
listen=YES

local_enable=YES
userlist_enable=YES
userlist_deny=NO

chroot_local_user=YES
chroot_list_enable=YES

anonymous_enable=NO
anon_root=/home/ftp/
anon-mkdir_write_enable=NO
anon_other_write_enable=NO
anon_upload_enable=NO

write_enable=YES

force_dot_files=YES
dirmessage_enable=YES

xferlog_enable=YES
dual_log_enable=YES

ascii_download_enable=YES
ascii_upload_enable=YES

connect_from_port_20=YES

ftpd_banner=Welcome to FTP server

#Enable download,if set no all download requests will give permisiion denied
download_enable=YES

#If enabled all local logins are forced to use ssl connection for data transfer$
force_local_data_ssl=YES

guest_enable=NO

listen_ipv6=YES

#This command create log file for all ftp requests n responses
log_ftp_protocol=YES

#Set to NO if u want to disable PORT method of data connection
port_enable=YES
#Enable if u want port security checks
port_promiscuous=YES
#Enable this option for secure data connections,instead of openssl
ssl_enable=YES

#only applies if ssl enabled
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES

#Time out for port style data connection
connect_timeout=100

#Time out for data connection with no progress
data_connection_timeout=120
file_open_mode=0666

idle_session_timeout=600

#if vsftpd is in standalone mode this is the port for incoming ftp connections
listen_port=55778

#The max data tranfer rate for local user
local_max_rate=0
local_unmask=077

#if vsftpd in standalone mode,this is the max no of clients connected
max_clients:0
max_per_ip=2
pasv_max_port=1645
pasv_min_port=1631

secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/root/vsftpd.pem
rsa_private_key_file=/root/vsftpd.pem
vsftpd_log_file=/var/log/vsftpd.log

```

    Thanx for helping  i appreciate that very much  Is there anymore details i can provide u..u said lots of going on here...i donno???:(

---

### Post by Mr. C. on 2008-03-30
I don't think you understand ports.  You can't just use any port and expect any service will respond.  You must configure a service to listen on a specific port.  The port for FTP by default is 21, so the command:
```

ftp localhost
```

will never succeed, because the ftp client is trying to connect on the *default* port 21.  So you have to do:

```
ftp -P 55778 localhost

```
if your config line **listen_port=55778** is active.

To see what services are listening on various ports, try:

```
lsof -nP -i
```

---

### Post by netlogic on 2008-03-30
USE LFTP.
ftp doesn't support SSL.

You have
**force_local_data_ssl=YES**

That means you are only allowing SSL connections.

I suggest reading the man page. It is really helpful.
good luck.

---

### Post by Aliyans on 2008-03-31
> **netlogic said:**
> USE LFTP.
ftp doesn't support SSL.
You have
**force_local_data_ssl=YES**
That means you are only allowing SSL connections.
.
hi  
              I understand that . i want only SSL connections.. n i'm trying to connect with client that support SSL.not juft ftp.. i think vsftpdd support SSL..Mr.C didnt say anything about it..n he understands that i want SSL connections only...

> **Mr. C. said:**
> I don't think you understand ports.  You can't just use any port and expect any service will respond.  You must configure a service to listen on a specific port.

Hi
     No. not much Mr.C . As said in my first post i'm new to linux. i dont understand ports much on linux..its not easy things to do on linux..especially somebody new to it..and somebody who followed a guide n ended up things not working..[ 4 me only SSLftp not working..evrything else fine]

  So i give u the results of commands u gave me

  ```
$ ftp -P 55778 localhost
ftp: P: unknown option
```

```
$ lsof -nP -i
COMMAND   PID    USER   FD   TYPE DEVICE SIZE NODE NAME
Xrealvnc 2383 Aliyans    0u  IPv4   5981       TCP *:6001 (LISTEN)
Xrealvnc 2383 Aliyans    3u  IPv6   5984       TCP *:5901 (LISTEN)
Xrealvnc 2383 Aliyans    5u  IPv6 251006       TCP **.***.***.***:5901->**.***.**.***:49179 (ESTABLISHED)
Xrealvnc 2383 Aliyans   10u  IPv6 560290       TCP **.***.***.***:5901->**.***.**.**:50794 (ESTABLISHED)
```

            I have to say sorry if i'm giving trouble to u???

---

### Post by netlogic on 2008-04-01
Hi Aliyan!

I think what MrC is trying to do is make you learn Linux. He is trying to make you find your own solution by offering Linux troubleshooting skills. I think many people who hang out on various Linux forums and mailing lists are burned out from people asking them to write the configs for them. Finding the shortcuts to Linux isn't ideal. It is a very good idea to read all documents that come with the software packages. Of course, some programmers write crappie manuals. However, I think vsftpd.conf is written very well. Before we give up and  make you a config file, have you read the vsftpd documentation and read the man page for vsftpd.conf? Have you typed, &#8220;man vsftpd.conf?&#8221; There are tons of options for vsftpd. There is a good reason for it, because FTP servers were made before firewall. It was before NAT became very fashionable. Anyway, check out this thread from few days ago. The issue is very similar.


[vsftpd with ssl]("http://ubuntuforums.org/showthread.php?t=718168")


Good luck! if you are still stuck please let us know, but you need to read the manual. In Linux, you can't brute force your configurations like Windows. You really have understand and read the manual.

---

### Post by Aliyans on 2008-04-03
hi
    well.. not so similar..let me see what Mr.C tell about it

---

### Post by netlogic on 2008-04-03
I GIVE UP!
Tell me what you want to do with your vsftp server. Also, I want you to tell me where your FTP server will be in your network.  This forum is more addicting than Slashdot. If I help you write it, you should help the next user with the similar question. I will write a config that you can copy to your /etc directory.

LOL... I am a huge sucker...lol.

---

### Post by Aliyans on 2008-04-03
hi
   I want to tranfer files between my home pc n my server using cuteftp[ssl  protocol]..FTP server in  where my server provider is located.lol....its not in my network..... i'm always ready to help within my limits..but let me sort out myself..then go for other..thats a good idea.rather than giving trouble to others..

---

### Post by Aliyans on 2008-04-19
hi
   Mr.C still this is not sorted

---

### Post by Mr. C. on 2008-04-21
Aliyans,

I'm not sure what state things are currently in for your setup.  So let's ask some basics:

1) have you been able to configure and connect to the FTP server with a basic, stock, vanilla configuration - no port changes, no SSL, just straight FTP?

2) Are you aware that NATing firewalls have trouble with FTP over SSL/TLS ?  Here's a little explanation I found for you: [http://geekswithblogs.net/lance/archive/2005/08/23/50912.aspx](http://geekswithblogs.net/lance/archive/2005/08/23/50912.aspx)

3) Have you been able to establish a connection to the remote FTP server using a standard FTP client ?  You should be able to connect, but get an error message that Non-anonymous sessions must use encryption.

4) Have you tried the connection with telnet to the server's port, and then issued the AUTH TLS command ?  Eg: 
```

$ telnet *FTPhostIP* *FTPlistenport*
Trying *FTPhostIP*...
Connect to *FTPhostIP*
220 (vsFTPd 2.0.5)
AUTH TLS
234 Proceed with negotiation.
```

---

### Post by netlogic on 2008-04-22
# TRY THIS.
listen=YES
# limited the bandwidth
# in case you want to limit people's bandwidth
local_max_rate=45000

local_enable=YES
# i'm going to make an assumption you want them to write.
write_enable=YES

# change your default permission here
local_umask=022

# not a good idea for strangers to write
anon_upload_enable=NO

# not a good idea for strangers to create directory
anon_mkdir_write_enable=no

# Activate directory messages - messages given to remote users when they
# go into a certain directory.
dirmessage_enable=YES

# Make sure PORT transfer connections originate from port 20 (ftp-data).
# i don't know your NAT issue, so I am going to assume we need some persistent
# connections
connect_from_port_20=YES

# where it will get logged
xferlog_file=/var/log/vsftpd.log

# good idea to log people's uploads/downloads
xferlog_enable=YES

# You may change the default value for timing out an idle session.
idle_session_timeout=6000

# You may change the default value for timing out a data connection.
data_connection_timeout=2200

# You may fully customise the login banner string:
ftpd_banner=blah. blah. you suck. 

#==============CHROOT settings=====================
# You may restrict ALL local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
chroot_local_user=YES

# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
chroot_list_enable=YES
# (default follows)
chroot_list_file=/etc/vsftpd.chroot_list
# ==============================================

# Debian related stuff
# Some of vsftpd's settings don't fit the Debian filesystem layout by
# default.  These settings are more Debian-friendly.
# This option should be the name of a directory which is empty.  Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
# leave this way it is. don't change it. you will break it.
secure_chroot_dir=/var/run/vsftpd

# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd

# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem

# This option specifies the location of the RSA key to use for SSL
# encrypted connections.
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

# USE SSL!
ssl_enable=YES
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES

# Show hidden files and the "." and ".." folders.
# Useful to not write over hidden files:
force_dot_files=NO

# how many connection per ip address
max_per_ip=10

# how many leechers
max_clients=4

# If you find problems when connecting behind NAT router, set pasv_min_port 
# and pasv_max_port, and allow outbound 
# make sure these ports are open on your router
pasv_min_port=12000
pasv_max_port=12100
# log usertime
use_localtime=YES

---

