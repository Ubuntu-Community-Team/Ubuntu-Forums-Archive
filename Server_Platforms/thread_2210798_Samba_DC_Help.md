---
title: "Samba DC Help"
date: 2014-03-12
forum: Server Platforms
---

### Post by rifaadh_saif on 2014-03-12
Hello,

I know that there is a lot of documentation on how to install a samba DC server and i do not know why but i always get an error. Name it, i got all kinds of error, and i follow the instruction to the WORD. I would really appreciate it if anybody could provide me with a instruction link that they used and it worked please, so that if i get into a problem he could also help me please.

I have the 32 bit ubuntu server, I am going to install a fresh one before starting the instruction anybody will provide me. 

Thanks ahead, i appreciate any help.

---

### Post by lingpanda on 2014-03-14
> **rifaadh_saif said:**
> Hello,

I know that there is a lot of documentation on how to install a samba DC server and i do not know why but i always get an error. Name it, i got all kinds of error, and i follow the instruction to the WORD. I would really appreciate it if anybody could provide me with a instruction link that they used and it worked please, so that if i get into a problem he could also help me please.

I have the 32 bit ubuntu server, I am going to install a fresh one before starting the instruction anybody will provide me. 

Thanks ahead, i appreciate any help.
[B]
Step 1 [/B]

Fresh Install Of Ubuntu 12.04

```
# apt-get install build-essential libacl1-dev libattr1-dev \
   libblkid-dev libgnutls-dev libreadline-dev python-dev \
   python-dnspython gdb pkg-config libpopt-dev libldap2-dev \
   dnsutils libbsd-dev attr krb5-user docbook-xsl libcups2-dev acl
```

**Step 2**

To use the advanced features of Samba4 you need a filesystem that supports both the "user" and "system" xattr namespaces. 
You need this support on file systems that you will share with  samba. For many users that will be their /home volume. However the  'samba-tool' provision command also tests support by creating a  temporary file in the 'sysvol'. This might be /usr/local/samba for a  local install, or might be somewhere else. That filesystem also needs to  have ACL and XATTR support. 
 **ext3/ext4 File System**

 If you are using either ext3 or ext4 for your file system you will need to include the options "user_xattr","acl" and "barrier=1" in your /etc/fstab. For example: 
 /dev/hda3               /home                   ext3    user_xattr,acl,barrier=1     1 1
Simply change ext3 to ext4 if you are using it. Normally you will  want to just modify the existing line to add those options. Please use  caution when modifying your fstab as it can lead to an un-bootable  system if the wrong thing is modified. 
The **barrier=1** option ensures that tdb transactions are  safe against unexpected power loss.  A number of sites have corrupted  their AD database in sam.ldb by not having this option enabled. 

**Step 3**

Reboot Ubuntu

**Step 4**


```
wget http://ftp.samba.org/pub/samba/samba-4.1.7.tar.gz
```
[B]
Step 5[/B]

```
tar -zxvf samba-4.1.7.tar.gz
```

**Step 6**

```
cd samba-4.1.7
```

**Step 7**

 ```
./configure
```

**Step 8**

```
sudo make
```

**Step 9**

```
sudo make install
```

**Step 10**


```
# /usr/local/samba/bin/samba-tool domain provision --use-rfc2307 --interactive
```

This will run the provision tool interactively. Because some settings can't be set interactively, it's recommended to run samba-tool domain provision --help and have a look at the additional possibilities. 
The --use-rfc2307 option enables your Samba AD  automatically to store posix attributes. It also creates NIS information  in the AD, that allows you to administrate UIDs/GIDs and other Unix  settings (on the „Unix attributes“ tab in ADUC). It's easier if you  enable this feature during provisioning, than setting this up later by  hand. And even if you don't required it (yet), it's not affecting your  installation. 
**Important notes on the provisioning:** 
 
[LIST]
[*] As of Samba 4.0.0rc1 the provision command uses the Samba Internal DNS server by default. If you would like to use [Bind as DNS backend]("http://wiki.samba.org/index.php/Dns-backend_bind"), add --dns-backend=BIND9_DLZ to the provisioning command. This decision isn't final. You can [switch the backend]("http://wiki.samba.org/index.php/DNS#Changing_the_DNS_backend") whenever it's necessary. 
[/LIST]
 
[LIST]
[*] If you re-run the provisioning, you need to remove the /usr/local/samba/etc/smb.conf! You may also need to remove the samba database files if they were generated rm -rf /usr/local/samba/private/* 
[/LIST]
 
[LIST]
[*] The admin password needs to fulfill the password complexity  requirements. This means at least one uppercase letter, one number, and  at least eight characters length. If you don't use a complex enough  password, the provision script will fail, and you will need to start  over with a better password (remove /usr/local/samba/private/ and /usr/local/samba/etc/). 
[/LIST]
 
[LIST]
[*] If your website is example.com, the domain of your AD should be  a subdomain of it, like samdom.example.com (or ad.example.com,  corp.example.com). Avoid using example.com internally. 
[/LIST]

---

### Post by rifaadh_saif on 2014-03-16
Hey 

Thanks for your post, i will try it and let you know.

thanks

---

### Post by rifaadh_saif on 2014-03-18
Hey 

I was not able to download the [COLOR=#000000][FONT=Ubuntu Mono]samba-4.1.7 version, i downloaded instead the [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]samba-4.1.6 is there a difference?
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]i followed your steps. When i perform the command = ./configure, i get an error:



root@server01:/home/duser/samba-4.1.6# ./configure
Checking for program gcc or cc           : not found
Checking for program icc                 : not found
Checking for program ICL                 : not found
Checking for program cc                  : not found
/home/duser/samba-4.1.6/lib/replace/../../buildtools/wafsamba/wscript:213: error: could not configure a c compiler!

Could you please assist me?

Thanks,

---

### Post by lingpanda on 2014-03-19
> **rifaadh_saif said:**
> Hey 

I was not able to download the [COLOR=#000000][FONT=Ubuntu Mono]samba-4.1.7 version, i downloaded instead the [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]samba-4.1.6 is there a difference?
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]i followed your steps. When i perform the command = ./configure, i get an error:



root@server01:/home/duser/samba-4.1.6# ./configure
Checking for program gcc or cc           : not found
Checking for program icc                 : not found
Checking for program ICL                 : not found
Checking for program cc                  : not found
/home/duser/samba-4.1.6/lib/replace/../../buildtools/wafsamba/wscript:213: error: could not configure a c compiler!

Could you please assist me?

Thanks,
Are you using a fresh install of Ubuntu 12.04? Download a fresh 32bit Ubuntu 12.04 LTS server package. [http://www.ubuntu.com/download/server](http://www.ubuntu.com/download/server) After installing do the following.

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

Reboot your server and start over from my previous post.

---

### Post by rifaadh_saif on 2014-03-20
Hey 

I did the commands you told me to perform. I re-install ubuntu and ran those command. Then when i performed the "./configure" command, it gave me the same error message.



Thanks again for your assistance

---

### Post by lingpanda on 2014-03-21
> **rifaadh_saif said:**
> Hey 

I did the commands you told me to perform. I re-install ubuntu and ran those command. Then when i performed the "./configure" command, it gave me the same error message.



Thanks again for your assistance

Sorry this is my fault. I left out important packages to install before configuring. I've edited my initial post. You need to review step one again. Again sorry.

---

### Post by rifaadh_saif on 2014-03-21
Hello,

It's ok because your are helping me and i really appreciate it. I am going to redo the steps. Also Do i really need to perform the 2nd step? because i am install a ext4 file system format, also i do not understand the 2nd step and a little scared to play with that file.

Thanks,

---

### Post by lingpanda on 2014-03-21
> **rifaadh_saif said:**
> Hello,

It's ok because your are helping me and i really appreciate it. I am going to redo the steps. Also Do i really need to perform the 2nd step? because i am install a ext4 file system format, also i do not understand the 2nd step and a little scared to play with that file.

Thanks,

In my opinion step 2 is important. This is mine. I use vi as my editor. Use what ever you like.

```
# vi /etc/fstab
```

```
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/samba4server-root /               [SIZE=3]**ext4    errors=remount-ro,user_xattr,acl,barrier=1 1       1**[/SIZE]
```

Do the bold part exactly like this.

---

### Post by rifaadh_saif on 2014-03-21
Hello,

Do you want me to replace "9aa0ead8-2257-4d62-9c7e-edb8d05f1974 / " By [COLOR=#000000][FONT=Ubuntu Mono]/dev/mapper/samba4server-root /? Or do you want me to add it?
 [/FONT][/COLOR]
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=9aa0ead8-2257-4d62-9c7e-edb8d05f1974 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=cd93e096-46f8-411d-8476-8283d811db7a none            swap    sw              0       0

Thanks,

---

### Post by lingpanda on 2014-03-24
> **rifaadh_saif said:**
> Hello,

Do you want me to replace "9aa0ead8-2257-4d62-9c7e-edb8d05f1974 / " By [COLOR=#000000][FONT=Ubuntu Mono]/dev/mapper/samba4server-root /? Or do you want me to add it?
 [/FONT][/COLOR]
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=9aa0ead8-2257-4d62-9c7e-edb8d05f1974 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=cd93e096-46f8-411d-8476-8283d811db7a none            swap    sw              0       0

Thanks,

Yours should look like this.

```
UUID=9aa0ead8-2257-4d62-9c7e-edb8d05f1974 /               ext4    errors=remount-ro,user_xattr,acl,barrier=1 1        1
```

---

### Post by rifaadh_saif on 2014-03-24
Hey, 

Thanks again. I followed all your instruction and everything went fine on the installation but i am not able to join the domain with my windows 7 computer. 

Windows 7 configuration:

- I added my server IP on my host file of Windows 
- Set my Server IP on WINS section 
- DNS server is set as my server. 

Server setting:

- I changed a hostname file to input me domain name 
- also i changed the IP from 127.0.0.1 to 192.168.0.11

Is this k these changes? also do you have any ideas as of why my windows client does not detect my server?

Thanks,

---

### Post by lingpanda on 2014-03-25
> **rifaadh_saif said:**
> Hey, 

Thanks again. I followed all your instruction and everything went fine on the installation but i am not able to join the domain with my windows 7 computer. 

Windows 7 configuration:

- I added my server IP on my host file of Windows 
- Set my Server IP on WINS section 
- DNS server is set as my server. 

Server setting:

- I changed a hostname file to input me domain name 
- also i changed the IP from 127.0.0.1 to 192.168.0.11

Is this k these changes? also do you have any ideas as of why my windows client does not detect my server?

Thanks,
Did you remember to start samba on your server? Have you checked to see if your client can ping the server?

---

### Post by rifaadh_saif on 2014-03-25
Hey

Yes i am able to ping the server. Also i rebooted the computer before trying it.
 
But it is wired when i do the command "smbd status" or "nmbd status" it says that samba is not installed? also the folder "/etc/samba/smb.conf" does not exist. How come because i followed exactly your commands?

Thanks,

---

### Post by lingpanda on 2014-03-26
> **rifaadh_saif said:**
> Hey

Yes i am able to ping the server. Also i rebooted the computer before trying it.
 
But it is wired when i do the command "smbd status" or "nmbd status" it says that samba is not installed? also the folder "/etc/samba/smb.conf" does not exist. How come because i followed exactly your commands?

Thanks,

Your smb.conf location should be in 

```
/usr/local/samba/etc/smb.conf
```

This is the default location. You start samba like this

```
/usr/local/samba/sbin/samba
```

You can check to see if it's running by typing

```
status samba4
```

[h=2]Testing Connectivity to Your Samba AD DC[/h] First check that you have the right version of smbclient by running: 
  $ /usr/local/samba/bin/smbclient --version
This should show you a version starting with "Version 4.x".  
Now run this command to list the shares on your Samba server: 
 $ /usr/local/samba/bin/smbclient -L localhost -U%

       Sharename       Type      Comment
       ---------       ----      -------
       netlogon        Disk
       sysvol          Disk
       IPC$            IPC       IPC Service (Samba 4.x.y)
The output of the command should be similar to what is shown. The netlogon and sysvol shares are default shares needed for Active Directory server operation and created in your smb.conf during provisioning/upgrading. 
If the command failed, restart samba: 
 # killall samba
# /usr/local/samba/sbin/samba
To test that authentication is working, you should try to connect to the netlogon  share, using the Administrator account created during provisioning. The  output of the command should be similar to what is shown below: 
 $ smbclient //localhost/netlogon -UAdministrator -c 'ls'

Domain=[SAMDOM] OS=[Unix] Server=[Samba 4.x.y]
  .                                   D        0  Tue Dec 11 20:00:00 2012
  ..                                  D        0  Tue Dec 11 20:00:00 2012

---

### Post by rifaadh_saif on 2014-03-26
Hey,

Yes the "SMB.CONF" is located in [FONT=Ubuntu Mono]/usr/local/samba/etc/smb.conf

- i did the following command "[/FONT][FONT=Ubuntu Mono]/usr/local/samba/sbin/samba" and nothing came up so i am guessing that it started correctly

- But when i perform "[/FONT][FONT=Ubuntu Mono]status samba4" it give me an error "[/FONT]status: Unknown job: samba4"

- When i performed the command "/usr/local/samba/bin/smbclient --version" = it gave me "Version 4.1.6"

- When i performed the command "/usr/local/samba/bin/smbclient -L localhost -U%" i got this: 

Domain=[RIFAADH] OS=[Unix] Server=[Samba 4.1.6]


        Sharename       Type      Comment
        ---------       ----      -------
        netlogon        Disk
        sysvol          Disk
        IPC$            IPC       IPC Service (Samba 4.1.6)
Domain=[RIFAADH] OS=[Unix] Server=[Samba 4.1.6]


        Server               Comment
        ---------            -------


        Workgroup            Master
        ---------            -------

- Then i performed the command "smbclient //localhost/netlogon -UAdministrator -c 'ls' "and got an error:  

The program 'smbclient' can be found in the following packages: * smbclient
 * samba4-clients
Try: apt-get install <selected package>


- So it is wired the command " smbclient //localhost/netlogon -UAdministrator -c 'ls' " and " [FONT=Ubuntu Mono]status samba4 " gives me an error.

Thanks for your assistance[/FONT]

---

### Post by lingpanda on 2014-03-27
> **rifaadh_saif said:**
> Hey,

Yes the "SMB.CONF" is located in [FONT=Ubuntu Mono]/usr/local/samba/etc/smb.conf

- i did the following command "[/FONT][FONT=Ubuntu Mono]/usr/local/samba/sbin/samba" and nothing came up so i am guessing that it started correctly

- But when i perform "[/FONT][FONT=Ubuntu Mono]status samba4" it give me an error "[/FONT]status: Unknown job: samba4"

- When i performed the command "/usr/local/samba/bin/smbclient --version" = it gave me "Version 4.1.6"

- When i performed the command "/usr/local/samba/bin/smbclient -L localhost -U%" i got this: 

Domain=[RIFAADH] OS=[Unix] Server=[Samba 4.1.6]


        Sharename       Type      Comment
        ---------       ----      -------
        netlogon        Disk
        sysvol          Disk
        IPC$            IPC       IPC Service (Samba 4.1.6)
Domain=[RIFAADH] OS=[Unix] Server=[Samba 4.1.6]


        Server               Comment
        ---------            -------


        Workgroup            Master
        ---------            -------

- Then i performed the command "smbclient //localhost/netlogon -UAdministrator -c 'ls' "and got an error:  

The program 'smbclient' can be found in the following packages: * smbclient
 * samba4-clients
Try: apt-get install <selected package>


- So it is wired the command " smbclient //localhost/netlogon -UAdministrator -c 'ls' " and " [FONT=Ubuntu Mono]status samba4 " gives me an error.

Thanks for your assistance[/FONT]

Everything is working correctly. The reason you got those errors was because you didn't specify the complete location of the command. For instance you would type /usr/local/samba/bin/smbclient and then your command. 

Follow this guide here to join your windows machine to your domain. [https://wiki.samba.org/index.php/Configuring_a_windows_client_for_AD](https://wiki.samba.org/index.php/Configuring_a_windows_client_for_AD)

---

### Post by rifaadh_saif on 2014-03-27
Hey,

You are AWESOME!!! I mean AWESOME. It worked, i can't believe it :) i am so happy today. So what i am going to do is restart everything from the beginning to confirm if i understand and able to perform it perfectly again. So i will let you know if it went all good.

Thanks a million for all your help.

---

### Post by lingpanda on 2014-03-27
> **rifaadh_saif said:**
> Hey,
You are AWESOME!!! I mean AWESOME. It worked, i can't believe it :) i am so happy today. So what i am going to do is restart everything from the beginning to confirm if i understand and able to perform it perfectly again. So i will let you know if it went all good.

Thanks a million for all your help.

No problem.  Glad I could help.

---

### Post by rifaadh_saif on 2014-03-30
Hey,

just another quick question. 

I tried installing this same way but in a Virtual machine, the installation went great.

but when i try joining my Windows 7 to the samba DC i am getting an error: The network path was not found.

- Also the windows 7 is on a virtual machine

- i did some research google and found this url :[http://lucasmanual.com/mywiki/SambaDomainController#The_network_path_was_not_found](http://lucasmanual.com/mywiki/SambaDomainController#The_network_path_was_not_found)
- it said that it was an issue with the IP address on the windows machine. so i did what is said but it still did not resolve the issue.

I was wondering if you could please help me again.

Thanks,

---

### Post by lingpanda on 2014-03-31
> **rifaadh_saif said:**
> Hey,

just another quick question. 

I tried installing this same way but in a Virtual machine, the installation went great.

but when i try joining my Windows 7 to the samba DC i am getting an error: The network path was not found.

- Also the windows 7 is on a virtual machine

- i did some research google and found this url :[http://lucasmanual.com/mywiki/SambaDomainController#The_network_path_was_not_found](http://lucasmanual.com/mywiki/SambaDomainController#The_network_path_was_not_found)
- it said that it was an issue with the IP address on the windows machine. so i did what is said but it still did not resolve the issue.

I was wondering if you could please help me again.

Thanks,

I assume you installed the DC on a physical box and the Win 7 is a VM? Correct? If so how is your network interface setup on the VM? Both machines on the same network, Is Samba Running, Can you ping your DC from the VM? Do an ```
IPCONFIG /All
``` on your Win 7 from a command prompt and do a ```
IFCONFIG
``` from your DC using the terminal.  Give me the outputs.

---

### Post by rifaadh_saif on 2014-03-31
Hey,

Thanks again for you replay.

Yes my windows 7 is a VM and my ubuntu was on a physical machine and it works fine that way. I am able to connect my Windows 7 to the Samba DC.

But i tried for fun installing ubuntu on as a VM and tried to connect to it, but it gave me an error. My setup is in Bridge mode on my virtual box for both VM. I am able to ping windows 7 from my ubuntu server and from my ubuntu server to my windows 7 computer. 

Also i tried connecting to my VM ubuntu server from my physical windows 8 computer and it gave me the same error.

_**IPconfig output: **_



C:\Users\win7>ipconfig /all


Windows IP Configuration


   Host Name . . . . . . . . . . . . : win7-PC
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No


Ethernet adapter Local Area Connection 2:


   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Intel(R) PRO/1000 MT Desktop Adapter #2
   Physical Address. . . . . . . . . : 08-00-27-10-E8-49
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::b55a:9cab:af7e:178b%13(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.0.169(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Monday, March 31, 2014 8:58:41 PM
   Lease Expires . . . . . . . . . . : Monday, April 07, 2014 8:58:41 PM
   Default Gateway . . . . . . . . . : 192.168.0.1
   DHCP Server . . . . . . . . . . . : 192.168.0.1
   DHCPv6 IAID . . . . . . . . . . . : 302514215
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-1A-87-13-D5-08-00-27-9E-B3-16


   DNS Servers . . . . . . . . . . . : 192.168.0.11
   NetBIOS over Tcpip. . . . . . . . : Enabled


Ethernet adapter Local Area Connection:


   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Intel(R) PRO/1000 MT Desktop Adapter
   Physical Address. . . . . . . . . : 08-00-27-9E-B3-16
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::5106:2773:80c9:a500%11(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.0.171(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Monday, March 31, 2014 8:47:11 PM
   Lease Expires . . . . . . . . . . : Monday, April 07, 2014 8:47:11 PM
   Default Gateway . . . . . . . . . : 192.168.0.1
   DHCP Server . . . . . . . . . . . : 192.168.0.1
   DHCPv6 IAID . . . . . . . . . . . : 235405351
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-1A-87-13-D5-08-00-27-9E-B3-16


   DNS Servers . . . . . . . . . . . : 192.168.0.13
   NetBIOS over Tcpip. . . . . . . . : Enabled


Tunnel adapter isatap.{2034E8A5-2EEE-499D-9DDC-98B161A7CB9E}:


   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes


Tunnel adapter isatap.{89D96EA2-D02A-4804-8967-8D95D90111FC}:


   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #2
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes


Tunnel adapter Teredo Tunneling Pseudo-Interface:


   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes


**_IFconfig output:_**



root@server03:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:27:ac:e2:b5
          inet addr:192.168.0.13  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:feac:e2b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1468 errors:0 dropped:0 overruns:0 frame:0
          TX packets:564 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:136559 (136.5 KB)  TX bytes:49447 (49.4 KB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1087 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1087 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:96574 (96.5 KB)  TX bytes:96574 (96.5 KB)


Thanks again

---

### Post by lingpanda on 2014-03-31
> **rifaadh_saif said:**
> Hey,

Thanks again for you replay.

Yes my windows 7 is a VM and my ubuntu was on a physical machine and it works fine that way. I am able to connect my Windows 7 to the Samba DC.

But i tried for fun installing ubuntu on as a VM and tried to connect to it, but it gave me an error. My setup is in Bridge mode on my virtual box for both VM. I am able to ping windows 7 from my ubuntu server and from my ubuntu server to my windows 7 computer. 

Also i tried connecting to my VM ubuntu server from my physical windows 8 computer and it gave me the same error.

_**IPconfig output: **_



C:\Users\win7>ipconfig /all


Windows IP Configuration


   Host Name . . . . . . . . . . . . : win7-PC
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No


Ethernet adapter Local Area Connection 2:


   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Intel(R) PRO/1000 MT Desktop Adapter #2
   Physical Address. . . . . . . . . : 08-00-27-10-E8-49
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::b55a:9cab:af7e:178b%13(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.0.169(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Monday, March 31, 2014 8:58:41 PM
   Lease Expires . . . . . . . . . . : Monday, April 07, 2014 8:58:41 PM
   Default Gateway . . . . . . . . . : 192.168.0.1
   DHCP Server . . . . . . . . . . . : 192.168.0.1
   DHCPv6 IAID . . . . . . . . . . . : 302514215
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-1A-87-13-D5-08-00-27-9E-B3-16


   DNS Servers . . . . . . . . . . . : 192.168.0.11
   NetBIOS over Tcpip. . . . . . . . : Enabled


Ethernet adapter Local Area Connection:


   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Intel(R) PRO/1000 MT Desktop Adapter
   Physical Address. . . . . . . . . : 08-00-27-9E-B3-16
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::5106:2773:80c9:a500%11(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.0.171(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Monday, March 31, 2014 8:47:11 PM
   Lease Expires . . . . . . . . . . : Monday, April 07, 2014 8:47:11 PM
   Default Gateway . . . . . . . . . : 192.168.0.1
   DHCP Server . . . . . . . . . . . : 192.168.0.1
   DHCPv6 IAID . . . . . . . . . . . : 235405351
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-1A-87-13-D5-08-00-27-9E-B3-16


   DNS Servers . . . . . . . . . . . : 192.168.0.13
   NetBIOS over Tcpip. . . . . . . . : Enabled


Tunnel adapter isatap.{2034E8A5-2EEE-499D-9DDC-98B161A7CB9E}:


   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes


Tunnel adapter isatap.{89D96EA2-D02A-4804-8967-8D95D90111FC}:


   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #2
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes


Tunnel adapter Teredo Tunneling Pseudo-Interface:


   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes


**_IFconfig output:_**



root@server03:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:27:ac:e2:b5
          inet addr:192.168.0.13  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:feac:e2b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1468 errors:0 dropped:0 overruns:0 frame:0
          TX packets:564 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:136559 (136.5 KB)  TX bytes:49447 (49.4 KB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1087 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1087 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:96574 (96.5 KB)  TX bytes:96574 (96.5 KB)


Thanks again

Just so I understand you. BOTH machines are on VM(Win 7 and Samba)? I've had issues in the past with this same setup. I'm trying to recall how I fixed it as well. I'm looking at how I currently have this setup running. Let me see if I can remember.

---

### Post by rifaadh_saif on 2014-04-01
Hey,

Thanks again for your replay.

Yes both machine are on a VM. The VM i am using is virtual box. Perfect once you find it let me know. I will also keep on trying on my end and try to find a solution. If i find a solution i will let you know.

Thanks,

---

### Post by rifaadh_saif on 2014-04-03
Hey,

Were you able to find the solution for this issue?

Thanks,

---

### Post by lingpanda on 2014-04-04
> **rifaadh_saif said:**
> Hey,

Were you able to find the solution for this issue?

Thanks,

I have not had time to further research this. I did un-join my PC from the DC and was not able to rejoin.

---

### Post by rifaadh_saif on 2014-04-04
hey,

thanks again for your replay.

K great no problem. I am also still trying things. Just wanted to know if you got something.

Thanks,

---

### Post by rifaadh_saif on 2014-04-22
Hey,

It works now, i did it today. I simply downloaded the new ubuntu server edition and did the steps and it worked. Everything is fine. I got another question (sorry) i was wondering how can you handle the password restriction, account lock out,etc of an account? i know that we can install the windows server remote admin tool and it works great, i can create a user and i can log in with that user. It is just the account policies that i was wondering.

Thanks

---

### Post by lingpanda on 2014-04-22
> **rifaadh_saif said:**
> Hey,

It works now, i did it today. I simply downloaded the new ubuntu server edition and did the steps and it worked. Everything is fine. I got another question (sorry) i was wondering how can you handle the password restriction, account lock out,etc of an account? i know that we can install the windows server remote admin tool and it works great, i can create a user and i can log in with that user. It is just the account policies that i was wondering.

Thanks

Currently GPO's do not work for these. You must use samba-tool to set.

---

### Post by rifaadh_saif on 2014-04-23
Hey,

Thanks for your replay 

I googled Samba-tool and found all the commands but the account locked out count was not there?

Thanks again

---

### Post by lingpanda on 2014-04-23
> **rifaadh_saif said:**
> Hey,

Thanks for your replay 

I googled Samba-tool and found all the commands but the account locked out count was not there?

Thanks again

Account lockout was introduced in Samba 4.1.6 and may need to be set through GPO's. I'm not yet running that version. Run ```
/usr/local/samba/bin/samba-tool domain passwordsettings --help
``` See if it displays those options.

---

### Post by weaseldb83 on 2014-04-23
I gave up on samba a while ago. I just use G-FTP.

---

### Post by lingpanda on 2014-04-23
> **weaseldb83 said:**
> I gave up on samba a while ago. I just use G-FTP.

I think you might be confused about the difference between samba3 and samba4

---

### Post by rifaadh_saif on 2014-04-24
Hey,
@[[COLOR=#000000]weaseldb83[/COLOR]]("http://ubuntuforums.org/member.php?u=1682618")[COLOR=#000000]  thanks for your replay but i am not looking for a file transfer protocol. [/COLOR]

[COLOR=#000000]I am looking for a DC and file transfer protocol that works well and Samba does that. I do not know why you gave up on it because it is very easy to mange and [/COLOR][COLOR=#000000]deploy.

@[/COLOR][[COLOR=#000000]lingpanda[/COLOR]]("http://ubuntuforums.org/member.php?u=1780254")[COLOR=#000000]  [/COLOR]

[COLOR=#000000]Thanks again for your replay. [/COLOR]

[COLOR=#000000]Was that replay intended to me or @[/COLOR][[COLOR=#000000]weaseldb83[/COLOR]]("http://ubuntuforums.org/member.php?u=1682618")[COLOR=#000000] ?  

Do you know a way to implement lockout policies for user account?[/COLOR]

---

### Post by lingpanda on 2014-04-24
> **rifaadh_saif said:**
> Hey,
@[[COLOR=#000000]weaseldb83[/COLOR]]("http://ubuntuforums.org/member.php?u=1682618")[COLOR=#000000]  thanks for your replay but i am not looking for a file transfer protocol. [/COLOR]

[COLOR=#000000]I am looking for a DC and file transfer protocol that works well and Samba does that. I do not know why you gave up on it because it is very easy to mange and [/COLOR][COLOR=#000000]deploy.

@[/COLOR][[COLOR=#000000]lingpanda[/COLOR]]("http://ubuntuforums.org/member.php?u=1780254")

[COLOR=#000000]Thanks again for your replay. [/COLOR]

[COLOR=#000000]Was that replay intended to me or @[/COLOR][[COLOR=#000000]weaseldb83[/COLOR]]("http://ubuntuforums.org/member.php?u=1682618")[COLOR=#000000] ?  

Do you know a way to implement lockout policies for user account?[/COLOR]

My last reply was for @weaseldb83. I do now know how to implement lockout policies. It's supposed to be working as of Samba 4.1.6. I've just upgraded to Samba 4.1.7 but it does not seem to work. I've asked on the samba mailing list so I will let you know if I get a response.

---

### Post by lingpanda on 2014-04-29
> **rifaadh_saif said:**
> Hey,
@[[COLOR=#000000]weaseldb83[/COLOR]]("http://ubuntuforums.org/member.php?u=1682618")[COLOR=#000000]  thanks for your replay but i am not looking for a file transfer protocol. [/COLOR]

[COLOR=#000000]I am looking for a DC and file transfer protocol that works well and Samba does that. I do not know why you gave up on it because it is very easy to mange and [/COLOR][COLOR=#000000]deploy.

@[/COLOR][[COLOR=#000000]lingpanda[/COLOR]]("http://ubuntuforums.org/member.php?u=1780254")

[COLOR=#000000]Thanks again for your replay. [/COLOR]

[COLOR=#000000]Was that replay intended to me or @[/COLOR][[COLOR=#000000]weaseldb83[/COLOR]]("http://ubuntuforums.org/member.php?u=1682618")[COLOR=#000000] ?  

Do you know a way to implement lockout policies for user account?[/COLOR]

It appears Samba does not allow for account lock out yet. Read the following

```
**CVE-2013-4496.html:**

   
===========================================================
== Subject:     CVE-2013-4496: Password lockout not enforced for SAMR password changes
==
== CVE ID#:     CVE-2013-4496
==
== Versions:    All versions of Samba later than 3.4.0
==
== Summary:     In Samba's SAMR server we neglect to ensure that
==              attempted password changes will update the bad password
==              count, nor set the lockout flags.
==              This would allow a user unlimited attempts against the
==              password by simply calling ChangePasswordUser2
==              repeatedly.
==
==              This is available without any other authentication.
==
===========================================================

===========
Description
===========

Samba versions 3.4.0 and above allow the administrator to implement
locking out Samba accounts after a number of bad password attempts.

However, all released versions of Samba did not implement this check for
password changes, such as are available over multiple SAMR and RAP
interfaces, allowing password guessing attacks.

As this was found during an internal audit of the Samba code there are
no currently known exploits for this problem (as of March 11th 2014).

=======
Caveats
=======

Most sites do not configure the bad password lockout feature.  Typically
it is only enabled when Samba is configured as a Domain Controller, so
most file server deployments are not impacted.

Additionally, for this feature to be effective Samba must be the sole
source of authentication on the network.  (Otherwise synchronised
services such as an LDAP backend or the UNIX /etc/shadow file could be
the weak point instead).

This patch does not implement bad password lockout for the Active
Directory Domain Controller.  The bad password lockout feature is not
implemented at all in that configuration.  The Samba Team plans to
address this deficiency as feature in a future release of the AD DC.

The patch to remove the samr_ChangePasswordUser call is not strictly
required, as this call is only available to administrators already able
to reset passwords.  We include it to avoid a future well-meaning patch
that might restore it as a valid password-change mechanism.  If used, it
would also bypass restrictions on password complexity, history and any
restriction defined via the 'unix passwd sync', 'pam password change'
and 'ldap password sync' smb.conf options.

==================
Patch Availability
==================

Patches addressing all these issues have been posted to:

    http://www.samba.org/samba/security/

Samba versions 3.6.23, 4.0.16, and 4.1.6 have been released to
address this issue. Patches for 3.4.17 and 3.5.22 have not been
provided as these are now beyond our security support window.

==========
Workaround
==========

None.

=======
Credits
=======

This problem was found by an internal audit of the Samba code by
Andrew Bartlett of Catalyst IT.  Special thanks also go to Univention GmbH.

Patches provided by Andrew Bartlett, Stefan Metzmacher of SerNet and Jeremy Allison of the Samba
team.

==========================================================
== Our Code, Our Bugs, Our Responsibility.
== The Samba Team
==========================================================

```

I'm still not exactly clear on what this patch does however.

---

### Post by rifaadh_saif on 2014-04-30
Hey,

Thanks for all your help. You are amazing. I think i understand the patch, like it will add the lockout feature to the current samba that i am running. But now i will try to find a way to install the patch and see. But like they said they are looking in a way to integrate this into the Samba package.

Thanks,

---

### Post by lingpanda on 2014-05-05
> **rifaadh_saif said:**
> Hey,

Thanks for all your help. You are amazing. I think i understand the patch, like it will add the lockout feature to the current samba that i am running. But now i will try to find a way to install the patch and see. But like they said they are looking in a way to integrate this into the Samba package.

Thanks,

So I received confirmation from the Samba devs that this is only in Master and should be released with Samba 4.2.X.

---

