---
title: "HOW TO: Automating Cisco Router, Switch, and Firewall backups"
date: 2005-12-20
forum: Tutorials
---

### Post by GrammatonCleric on 2005-12-20
_**HOW TO: Automating Cisco Router, Switch, Firewall backups.**_

 
**Step 1: Download and install rancid.** 
-------------------------------------------------------------------- 

For additional information on rancid's complete functionality see the following site. 

[http://www.shrubbery.net/rancid/]("http://www.shrubbery.net/rancid/")
 
 
Install rancid, build-essential, and expect. 

```

sudo apt-get install rancid-core rancid-util build-essential expect  

```   
**Step 2: Create  .cloginrc file in the rancid directory.  **
-------------------------------------------------------------------- 
 
 
Opend a terminal and type the following. 
 
```

sudo gedit /var/lib/rancid/.cloginrc  

```  
Add entries for each router, switch, pix firewall you'd like to backup by using the following format. 
 
```

add password    IPADDRESS       {telnetpassword}      {enablepassword} 
  
```
 
IPADDRESS = the actual ip address of the device you want to backup.
telnetpassword = the actual telnet password for the device you want to backup.
enablepassword = the actual enable password for the device you want to backup.
 
The "{}" are required. At the bottom of the .clogin add the following line if you require SSH access to your equipment.  
 
```

add method     *    telnet ssh 
 
``` 
With this clogin will first try to telnet then ssh to your equipment. 
 
 
 
**Step 3: Protect the .cloginrc file.** 
-------------------------------------------------------------------- 
 
 ```

sudo chmod 640 /var/lib/rancid/.cloginrc 
 
```  
 
**Step 4: Create a backup directory for backup configs.  **
-------------------------------------------------------------------- 
 
 
```
sudo mkdir /var/lib/rancid/backups/
``` 
 
 
Step 5: Change ownership of the /usr/lib/rancid/backups/ directory. 
-------------------------------------------------------------------- 
 
 
```
sudo chown -R rancid.rancid /var/lib/rancid/backups/
``` 
 
 
**Step 6: Change permissions to the rancid directory.** 
-------------------------------------------------------------------- 
 
 
```
sudo chmod 770 /var/lib/rancid/ 

``` 
**Step 7: Set password for rancid account** 
-------------------------------------------------------------------- 

```
sudo passwd rancid
``` 
 
**Step 8: Test .cloginrc** 
-------------------------------------------------------------------- 
 
As the user rancid test accessing your equipment. 
 
```
su rancid
``` 
 
Now using once of the network devices that you've put in the .cloginrc for rancid type the following in the open terminal. 
 
```
/usr/lib/rancid/bin/clogin  IPADDESSOFDEVICE 
```  
You should see the clogin telnet (or ssh) to the device in question and switch to enable mode on the device. If everything works the proceed on to step 8. Otherwise take a look at your /var/lib/rancid/.cloginrc . 
 
 
[B] 
Step 9: Test grabing a backup config from the same device.[/B] 
-------------------------------------------------------------------- 

As rancid run the following test to make sure that you have everything setup correctly. 
 
```
/usr/lib/rancid/bin/clogin  -c 'write term' IPADDESSOFDEVICE > /var/lib/rancid/backups/test.cfg
``` 
 
 
Verify the output: 
 
```
less /var/lib/rancid/backups/test.cfg
``` 
 
 
If everthing checks out move on to step 10. 
 
 
**Step 10: Create the bash script for the backups** 
-------------------------------------------------------------------- 
 
Here's a sample script for you to copy and paste into a file (i.e. network_device_backup.sh) and to tweak, add, or change for your needs. But save the script somewhere the rancid user can access and execute the script from (i.e./var/lib/rancid/). If you are planning on backing up a various types of routers, switches, firewalls etc you may want to create serveral differnet scripts. 
 
```

#!/bin/bash 
# Variables 
 
clogin=/usr/lib/rancid/bin/clogin 
path=/var/lib/rancid/backups/ 
tdy=`date +%m%d%Y` 
 
#backup network device 
 
$clogin -c 'write term' 192.168.0.1 > $path/foo-$tdy.cfg 
 
``` 
*NOTE: When rancid is installed the default shell for the rancid user is csh. So for the script above to work the "#!/bin/bash' is needed. *


 
**Step 11: Make the script executable to rancid.** 
-------------------------------------------------------------------- 
  
```
sudo chmod 700 /path/to/script
``` 
 
 
**Step 12: Test the backup script.** 
-------------------------------------------------------------------- 
 
Test your script logged in as rancid. 
 
```
su rancid
``` 
 
 
Now from wherever you put the backup script verify that it works before adding it as a cron job. For this example I'm going to use the following location /var/lib/rancid/.scripts/routers.sh with the output path being /var/lib/rancid/backups/. 
 
```
 ./var/lib/rancid/.scripts/routers.sh 
```  
verify the config file that was generated to the output path you specified.
  
```
less /var/lib/rancid/backups/foo-12202005.cfg
``` 


**Step 13: Add script to CRON.** 
--------------------------------------------------------------------

As rancid add your script to CRONTAB.  
```

su rancid

``` 
Now add an entry for your script.

```
crontab -e
``` 
To backup your equipment every Friday at 5pm should look like...

0 17 * * 5  /var/lib/rancid/.scripts/routers.sh >/dev/null 2>&1 

Save the entry (crtl+x).

Verify the entry in crontab is correct.

```
crontab -l
``` 

For more infor on CRONTAB see the following post.
[http://ubuntuforums.org/showthread.php?t=102626]("http://ubuntuforums.org/showthread.php?t=102626")

You're all set... enjoy!

---

### Post by troffasky on 2008-06-17
> **GrammatonCleric said:**
> 
As the user rancid test accessing your equipment. 
 
```
su rancid
``` 


> 
*NOTE: When rancid is installed the default shell for the rancid user is csh. So for the script above to work the "#!/bin/bash' is needed. *



Looks like RANCIDs user in 8.04 has it's shell set to /bin/false, so using 'su' will silently fail. You can use vipw to change it to /bin/bash.

---

### Post by zivley on 2008-08-20
> **GrammatonCleric said:**
> 
Open a terminal and type the following. 
 
```

sudo gedit /var/lib/rancid/.cloginrc  

```  
Add entries for each router, switch, pix firewall you'd like to backup by using the following format. 
 
```

add password    IPADDRESS       {telnetpassword}      {enablepassword} 
  
```
 
IPADDRESS = the actual ip address of the device you want to backup.
telnetpassword = the actual telnet password for the device you want to backup.
enablepassword = the actual enable password for the device you want to backup.
 
The "{}" are required. At the bottom of the .clogin add the following line if you require SSH access to your equipment.  
 
```

add method     *    telnet ssh 
 
``` 
With this clogin will first try to telnet then ssh to your equipment. 
 


Very nice and useful howto! Just what I've been looking for!
But what if my routers use local authentication with username/password and not only password?
How exactly would the /var/lib/rancid/.cloginrc file look in this case?
TIA
Ziv

---

### Post by GrammatonCleric on 2008-08-20
Hi Ziv,

The .cloginrc format is.

```


 add password <router name glob> <vty passwd> <enable passwd>

 add user <router name glob> <username>
       The default user is $USER (i.e.: the user running clogin).

 add userprompt <router name glob> <username prompt>
       What the router prints to prompt for the username.
       Default: {"(Username|login|user name):"}

 add userpassword <router name glob> <user password>
       The password for user if different than the password set
       using 'add password'.

 add passprompt <router name glob> <password prompt>
       What the router prints to prompt for the password.
       Default: {"(\[Pp]assword|passwd):"}

 add method <router name glob> {ssh} [...]
       Defines, in order, which connection method(s) to use for a device
       from the set {ssh,telnet,rsh}.  e.g.: add method * {ssh} {telnet} {rsh}
       will attempt ssh connection first.  if ssh fails with connection
       refused (i.e.: not due to authentication failure), then try telnet,
       then rsh.
       Default: {telnet} {ssh}

 add noenable <router name glob>
       equivalent of -noenable on the cmd line to not enable at login.

 add enableprompt <router name glob> <enable prompt>
       What the router prints to prompt for the enable password.
       Default: {"\[Pp]assword:"}

 add enauser <router name glob> <username>
       This is only needed if enable asks for a username and this
       username is different from what user is set to.

 add autoenable <router name glob> <1/0>
       This is used if you are automatically enabled by the login process.

 add cyphertype <router name glob> <ssh encryption type>
       Default is 3des.

 add identity <router name glob> <path to ssh identity file>
       Default is your default ssh identity.


```Hope this helps.

- GC

---

### Post by zivley on 2008-08-20
Yes, it helps, thanks!

---

### Post by zivley on 2008-08-20
Another little question, let's say I set the default user "rancid" on every router with priv 15
is there a way I can set a global variable of the user to be used on every device? or I still need to add an entry for every single device even the same user/pass is set on all of them?

---

### Post by chk9 on 2008-09-05
> **zivley said:**
> Is there a way I can set a global variable of the user to be used on every device? 

```

add user *              $env(USER)

```

will set the default user for all devices...

---

### Post by ronni on 2008-09-10
Hi,

I have followed the howto, and are able to login to an HP Switch using:
/usr/lib/rancid/bin/clogin  IPADDESSOFDEVICE

But when I try to use:
/usr/lib/rancid/bin/clogin  -c 'write term' IPADDESSOFDEVICE > /var/lib/rancid/backups/test.cfg

I get the following error:
couldn't compile regular expression pattern: parentheses () not balanced
    while executing
"expect -nobrace -re { [24;1H([^#>\r\n]+)?[#>](\([^)\r\n]+\))?} {} -re {[
]+} { exp_continue }"
    invoked from within
"expect {
            -re $reprompt       {}
            -re "\[\n\r]+"      { exp_continue }
        }"
    (procedure "run_commands" line 25)
    invoked from within
"run_commands $prompt $command"
    ("foreach" body line 169)
    invoked from within
"foreach router [lrange $argv $i end] {
    set router [string tolower $router]
    # attempt at platform switching.
    set platform ""
    send_user ..."
    (file "/usr/lib/rancid/bin/clogin" line 749)


I have found that if I comment out line 625 that looks like this:
regsub -all {^(.{1,11}).*([#>])$} $reprompt {\1([^#>\r\n]+)?[#>](\\([^)\\r\\n]+\\))?} reprompt

or if I put a ] after \1  the error disappear, but the output in test.cfg is just some weird mess.

Any suggestions?

-Ronni

---

### Post by don_777 on 2008-10-24
Thanks for the information.
I have a problem with the configuration. I do everything as mentioned but when I am ready to execute "*/usr/lib/rancid/bin/clogin IPADDRESSDEVICE*" it gives the error  "*/home/rancid/.cloginrc must not be world readable/writable*", so I have no idea how to solve this problem. If some body has an idea?

---

### Post by don_777 on 2008-10-29
Never mind I found the problem. The rancid user has to be in the root group and not under the rancid group.

---

### Post by -lodogg- on 2009-04-15
The tutorial above was really good, so thank you!

I did get everything setup and working but I have a few minor issues.  For some reason rancid is defaulting to my user directory for the .cloginrc file.  I placed the file in /home/mydirectory/.cloginrc and it works fine any suggestions on how I can change this?

Also if I (su rancid) it seems like the account does not have permission to write to /var/lib/rancid/backups/ directory.

Thanks,
-lo

---

### Post by -lodogg- on 2009-04-16
bump

I found out that I can control what password file is called by the command listed below.  But for firewalls I keep getting the "term length 0" in the file:\  The command for an ASA is "term pager 0", so the question is how do I change this in rancid?  And is the command below to large?

Code:
sudo /usr/lib/rancid/bin/clogin -f /home/user/.cloginrc-firewall -c 'ch context; terminal pager 0; sh run' 10.2.2.1 > /home/user/backups/firewall-test.cfg

---

### Post by chk9 on 2009-04-17
> **ronni said:**
> I have followed the howto, and are able to login to an HP Switch using:
/usr/lib/rancid/bin/clogin  IPADDESSOFDEVICE


Ronni,

There are several login scripts like the 'clogin' for Cisco routers.
'hlogin' is for HP gear. 

From the clogin man page:
> DESCRIPTION
       clogin is an expect(1) script to automate the process of logging into a Cisco router,
       catalyst  switch,  Extreme switch, Juniper ERX/E-series, Procket Networks, or Redback
       router.  There are complementary scripts  for  Alteon,  ADC-kentrox  EZ-T3  mux,  Bay
       Networks (nortel), Cisco AGM, Foundry, HP Procurve Switches, Hitachi Routers, Juniper
       Networks, Netscreen firewalls, Netscaler, Riverstone, and Lucent TNT,  named  alogin,
       blogin,  elogin,  flogin,  hlogin,  htlogin,  jlogin,  nlogin, nslogin, rivlogin, and
       tntlogin, respectively.


Hope this helps, chk9

---

### Post by chk9 on 2009-04-17
> **don_777 said:**
> error  "*/home/rancid/.cloginrc must not be world readable/writable*", so I have no idea how to solve this problem. If some body has an idea?

This step should have solved that:
```
**Step 3: Protect the .cloginrc file. **
-------------------------------------------------------------------- 


Code:
sudo chmod 640 /var/lib/rancid/.cloginrc
```
Since this file does contain passwords; even better still is:
```
sudo chmod 600 /var/lib/rancid/.cloginrc
```

I did create rancid as a regular user and can login as rancid directly.

---

### Post by chk9 on 2009-04-17
> **don_777 said:**
> Never mind I found the problem. The rancid user has to be in the root group and not under the rancid group.

My rancid user is NOT in the root group, but the rancid group should have appropriate access to the files/folders rancid user wants to write to/read from... Check your permissions!

---

### Post by chk9 on 2009-04-17
> **-lodogg- said:**
> for firewalls I keep getting the "term length 0" in the file:\  The command for an ASA is "term pager 0"

I've put all ASA's on 'no pager' and you could put that in a separate script to run before the 'rancid-run' script in the crontab for rancid, if you have team-mates that like to put the pager statement back in.

---

### Post by jrogers360 on 2009-11-26
This was originally posted in 2005.  I'm curious, is it still applicable with recent rancid/ubuntu versions?  Or is there a more up to date one to be found?

---

### Post by j4v on 2010-01-19
This post has been really helpfull to me. But I have a problem, I have not a route to an IP 10.200.1.10, I must telnet 10.30.2.10 and I already do that:

add user 10.30.2.10             user
add password 10.30.2.10     {password}
add autoenable 10.30.2.10   1

How can I configure the .cloginrc file in order to first telnet 10.30.2.10, and then telnet 10.200.1.10 automaticaly if I must be logged in the first one to reach the second one??

---

### Post by nuzzy on 2010-01-27
I have a question for rancid users who are using this for their Cisco switches.  I noticed that my config has a lot of unnecessary info in the beginning, like listing everything in the bootflash and NVRAM directories as well as some other info not relevant to the actual config.  Is there a way to NOT output this info and just get the relevant config info?

---

### Post by mziel on 2010-03-01
> **nuzzy said:**
> I have a question for rancid users who are using this for their Cisco switches.  I noticed that my config has a lot of unnecessary info in the beginning, like listing everything in the bootflash and NVRAM directories as well as some other info not relevant to the actual config.  Is there a way to NOT output this info and just get the relevant config info?

Yes, there is - look in your bin/rancid:

```

#Main
@commandtable = (
        {'admin show version'           => 'ShowVersion'},
        {'show version'                 => 'ShowVersion'},
        {'show redundancy secondary'    => 'ShowRedundancy'},
        {'show idprom backplane',       => 'ShowIDprom'},
        {'show install active'          => 'ShowInstallActive'},
        {'admin show env all'           => 'ShowEnv'},
        {'show env all'                 => 'ShowEnv'},
        {'show rsp chassis-info',       => 'ShowRSP'},
(...)
        {'show running-config'          => 'WriteTerm'},
        {'write term'                   => 'WriteTerm'},
);

```

Just comment out unwanted commands.

---

### Post by hovrashko on 2010-03-19
> **GrammatonCleric said:**
> Hi Ziv,

The .cloginrc format is.

```


 add password <router name glob> <vty passwd> <enable passwd>

 add user <router name glob> <username>
       The default user is $USER (i.e.: the user running clogin).

 add userprompt <router name glob> <username prompt>
       What the router prints to prompt for the username.
       Default: {"(Username|login|user name):"}

 add userpassword <router name glob> <user password>
       The password for user if different than the password set
       using 'add password'.

 add passprompt <router name glob> <password prompt>
       What the router prints to prompt for the password.
       Default: {"(\[Pp]assword|passwd):"}

 add method <router name glob> {ssh} [...]
       Defines, in order, which connection method(s) to use for a device
       from the set {ssh,telnet,rsh}.  e.g.: add method * {ssh} {telnet} {rsh}
       will attempt ssh connection first.  if ssh fails with connection
       refused (i.e.: not due to authentication failure), then try telnet,
       then rsh.
       Default: {telnet} {ssh}

 add noenable <router name glob>
       equivalent of -noenable on the cmd line to not enable at login.

 add enableprompt <router name glob> <enable prompt>
       What the router prints to prompt for the enable password.
       Default: {"\[Pp]assword:"}

 add enauser <router name glob> <username>
       This is only needed if enable asks for a username and this
       username is different from what user is set to.

 add autoenable <router name glob> <1/0>
       This is used if you are automatically enabled by the login process.

 add cyphertype <router name glob> <ssh encryption type>
       Default is 3des.

 add identity <router name glob> <path to ssh identity file>
       Default is your default ssh identity.


```Hope this helps.

- GC
[SIZE=3]Hello!
 Thank you for your great post, but cent get trough step 8.
i dont understund content of file .cloginrc, seems to complex for this: 
Router Name: Lab_router 
ip address: 192.168.1.1 
telnet(vty) password cisco
enable secret class
 my .cloginrc:
  add password 192.168.1.1 {cisco} {class}
when i type
 /usr/lib/rancid/bin/clogin 192.168.1.1
i get this:
 Error: password file (/home/eric/.cloginrc) does not exist

Ill be very appreciated of any help, 
thanks,[/SIZE]
  [SIZE=3]Eric[/SIZE]

---

### Post by pininy on 2010-03-29
> **hovrashko said:**
> [SIZE=3]Hello!
 Thank you for your great post, but cent get trough step 8.
i dont understund content of file .cloginrc, seems to complex for this: 
Router Name: Lab_router 
ip address: 192.168.1.1 
telnet(vty) password cisco
enable secret class
 my .cloginrc:
  add password 192.168.1.1 {cisco} {class}
when i type
 /usr/lib/rancid/bin/clogin 192.168.1.1
i get this:
 Error: password file (/home/eric/.cloginrc) does not exist

Ill be very appreciated of any help, 
thanks,[/SIZE]
  [SIZE=3]Eric[/SIZE]

I have the same issue, anyone can help???

thomas@nms-01:/$ /usr/lib/rancid/bin/clogin 10.1.1.1

Error: password file (/home/thomas/.cloginrc) does not exist
thomas@nms-01:/$ 

i have follow the guide to the dot!

---

### Post by kcmjr on 2010-03-29
You MUST run the command as the rancid user "su - rancid" or you will get this exact error.  here is another (slightly different) install linked from the rancid web site.  Note that this install is for fedora not ubuntu and the setup is slightly different.[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch1_:_Network_Backups_With_Rancid](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch1_:_Network_Backups_With_Rancid)

Basically your rancid user has the wrong home folder set.

To change the user's home directory, just use the 'usermod' command,  which exists on all unices. It works like this:

usermod -d /path/to/new/homedir/ username

Best to do this from the root user logon or another admin user that is NOT the rancid user.

---

### Post by vevel on 2010-05-11
> **pininy said:**
> I have the same issue, anyone can help???

thomas@nms-01:/$ /usr/lib/rancid/bin/clogin 10.1.1.1

Error: password file (/home/thomas/.cloginrc) does not exist
thomas@nms-01:/$ 
[...]

You could theoretically have a different .cloginrc for every user on your system.  
You don't have to log in from the rancid account or with the rancid user. 
If you are trying to use clogin from your account (as opposed to running rancid-run to collect configs,
which can be done from the rancid user crontab), just make sure you have a
/home/whoever/.cloginrc and make sure that you have /usr/local/rancid/bin in your path.   

I have this in my ~/.profile to prepend the rancid path to my existing PATH:
PATH="/usr/lib/rancid/bin:$PATH"

---

### Post by Greem84 on 2010-06-02
I have a trouble with Step #9. clogin didn't send the 'show ver' command to the switch. 
I really don't know what I did wrong, can you help me please?
 
```

[EMAIL="rancid@lab-server01:/home/lab$"]rancid@lab-server01:/home/lab$[/EMAIL] /usr/lib/rancid/bin/clogin -u 'rancid' -p 'rancid' -c 'show ver' 172.24.99.10
172.24.99.10
spawn telnet 172.24.99.10
Trying 172.24.99.10...
Connected to 172.24.99.10.
Escape character is '^]'.
 
User Access Verification
Username: rancid
Password:
LAB-SW03#

```

---

### Post by Greem84 on 2010-06-02
I found the solution, I added the "-autoenable" option to my command.
Here is the result.
 
Thanks!\\:D/
 
```

rancid@lab-server01:/home/lab$ /usr/lib/rancid/bin/clogin -u 'rancid' -p 'rancid' -autoenable -c 'show ver' 172.24.99.10
 
spawn telnet 172.24.99.10
Trying 172.24.99.10...
Connected to 172.24.99.10.
Escape character is '^]'.
 
User Access Verification
Username: rancid
Password:
LAB-SW03#
LAB-SW03#terminal length 0
LAB-SW03#show ver
Cisco Internetwork Operating System Software
IOS (tm) C2950 Software (C2950-I6K2L2Q4-M), Version 12.1(22)EA13, RELEASE SOFTWARE (fc2)
Technical Support: [http://www.cisco.com/techsupport](http://www.cisco.com/techsupport)
Copyright (c) 1986-2009 by cisco Systems, Inc.
Compiled Fri 27-Feb-09 22:20 by amvarma
Image text-base: 0x80010000, data-base: 0x80680000
ROM: Bootstrap program is C2950 boot loader
LABD3-SW03 uptime is 2 weeks, 4 days, 22 hours, 11 minutes
System returned to ROM by power-on
System image file is "flash:/c2950-i6k2l2q4-mz.121-22.EA13.bin"
 
This product contains cryptographic features and is subject to United
States and local country laws governing import, export, transfer and
use. Delivery of Cisco cryptographic products does not imply
third-party authority to import, export, distribute or use encryption.
Importers, exporters, distributors and users are responsible for
compliance with U.S. and local country laws. By using this product you
agree to comply with applicable laws and regulations. If you are unable
to comply with U.S. and local laws, return this product immediately.
A summary of U.S. laws governing Cisco cryptographic products may be found at:
[http://www.cisco.com/wwl/export/crypto/tool/stqrg.html](http://www.cisco.com/wwl/export/crypto/tool/stqrg.html)
If you require further assistance please contact us by sending email to
[EMAIL="export@cisco.com"]export@cisco.com[/EMAIL].
cisco WS-C2950-12 (RC32300) processor (revision N0) with 19912K bytes of memory.
Processor board ID
Last reset from system-reset
Running Standard Image
12 FastEthernet/IEEE 802.3 interface(s)
32K bytes of flash-simulated non-volatile configuration memory.
Base ethernet MAC Address: 
Motherboard assembly number: 
Power supply part number: 34-0965-01
Motherboard serial number: 
Power supply serial number: 
Model revision number: N0
Motherboard revision number: B0
Model number: WS-C2950-12
System serial number: 
Configuration register is 0xF
 
LAB-SW03#exit
Connection closed by foreign host.

```

---

### Post by dothdew88 on 2010-08-20
Hey! I was hoping someone could help me with gettng Rancid to authenticate a user with AAA and a Tacacs server. I am kinda new to this kinda stuff. I have rancid installed on Ubuntu server 10.04 (lucid) anyhelp would be amazing

---

### Post by CritiKaster on 2010-11-25
great post, thanks a bunch, GrammatonCleric!

---

### Post by Rev. Dead Corpse on 2011-01-03
In keeping with the apparent theme of posting to this thread once every couple of months... Here's another Rancid oddity:

Trying to pull config diffs from HP Procurve switches. Latest versions of Tcl, Expect, diff stat, and 2.3.5 Rancid.

Getting random characters changes and white space changes seen as diffs. Things like ";password manager <removed>" in one config showing up in the next chrons run as "c5# ord manager". This generates a new email every time. 

Since we have these going directly into our ticketing system for change control, these pile up over time and need to be parsed out from actual config changes.

I've tried various diff switches in the control_rancid. Current command string in the control_rancid file is "cvs -f diff -TwbB -U 4 -ko | sed -e '/^RCS file: /d' -e/^--- /d' \ -e '/^+++/d' -e 's/^\([-+]\)/\1 /' >$TMP.dff"

I've also tried looking in the hrancid, hlogin, and htlogin files for more hints that might be scrambling my diffs, but no luck.

Here's a sample of what shows up in my ticket queue:

> retrieving revision 1.71
diff -T -w -b -B -U 4 -r1.71 10.5.2.55
@@ -47,6 +47,6 @@
untagged 1 
tagged Trk1 
exit 
spanning-tree Trk1 priority 4
- ;password manager <removed>
+ 72-nc6# manager
;

---

### Post by Rev. Dead Corpse on 2011-01-10
> **Rev. Dead Corpse said:**
> In keeping with the apparent theme of posting to this thread once every couple of months... Here's another Rancid oddity:

Trying to pull config diffs from HP Procurve switches. Latest versions of Tcl, Expect, diff stat, and 2.3.5 Rancid.

Getting random characters changes and white space changes seen as diffs. Things like ";password manager <removed>" in one config showing up in the next chrons run as "c5# ord manager". This generates a new email every time. 

Since we have these going directly into our ticketing system for change control, these pile up over time and need to be parsed out from actual config changes.

I've tried various diff switches in the control_rancid. Current command string in the control_rancid file is "cvs -f diff -TwbB -U 4 -ko | sed -e '/^RCS file: /d' -e/^--- /d' \ -e '/^+++/d' -e 's/^\([-+]\)/\1 /' >$TMP.dff"

I've also tried looking in the hrancid, hlogin, and htlogin files for more hints that might be scrambling my diffs, but no luck.

Here's a sample of what shows up in my ticket queue:

Never mind. I set rancid.conf to only pull one config at a time and it got rid of the issue I was seeing. It went from taking 5 minutes to config diff all 99 devices to almost a half-hour, but at least it looks like it's pulling them correctly now.

---

### Post by Rev. Dead Corpse on 2011-03-21
Spoke too soon. It made it maybe through the first couple of iterations and started doing it again.

Also, if you logon to our core Cisco 4507 and do an "sh run", it'll see it as a new diff even if you don't make any changes.

Annoying...

---

### Post by tems1234 on 2011-04-27
Need ur guys expertise on my concern; every time i did below command:


/usr/lib/rancid/bin/clogin  -c 'write term' IPADDESSOFDEVICE > /var/lib/rancid/backups/test.cfg
this will comeout 

bash: /var/lib/rancid/backups/test.cfg: Permission denied

---

### Post by eherna2000 on 2011-08-31
> **GrammatonCleric said:**
> _**HOW TO: Automating Cisco Router, Switch, Firewall backups.**_

 
**Step 1: Download and install rancid.** 
-------------------------------------------------------------------- 

For additional information on rancid's complete functionality see the following site. 

[http://www.shrubbery.net/rancid/]("http://www.shrubbery.net/rancid/")
 
 
Install rancid, build-essential, and expect. 

```

sudo apt-get install rancid-core rancid-util build-essential expect  

```   
**Step 2: Create  .cloginrc file in the rancid directory.  **
-------------------------------------------------------------------- 
 
 
Opend a terminal and type the following. 
 
```

sudo gedit /var/lib/rancid/.cloginrc  

```  
Add entries for each router, switch, pix firewall you'd like to backup by using the following format. 
 
```

add password    IPADDRESS       {telnetpassword}      {enablepassword} 
  
```
 
IPADDRESS = the actual ip address of the device you want to backup.
telnetpassword = the actual telnet password for the device you want to backup.
enablepassword = the actual enable password for the device you want to backup.
 
The "{}" are required. At the bottom of the .clogin add the following line if you require SSH access to your equipment.  
 
```

add method     *    telnet ssh 
 
``` 
With this clogin will first try to telnet then ssh to your equipment. 
 
 
 
**Step 3: Protect the .cloginrc file.** 
-------------------------------------------------------------------- 
 
 ```

sudo chmod 640 /var/lib/rancid/.cloginrc 
 
```  
 
**Step 4: Create a backup directory for backup configs.  **
-------------------------------------------------------------------- 
 
 
```
sudo mkdir /var/lib/rancid/backups/
``` 
 
 
Step 5: Change ownership of the /usr/lib/rancid/backups/ directory. 
-------------------------------------------------------------------- 
 
 
```
sudo chown -R rancid.rancid /var/lib/rancid/backups/
``` 
 
 
**Step 6: Change permissions to the rancid directory.** 
-------------------------------------------------------------------- 
 
 
```
sudo chmod 770 /var/lib/rancid/ 

``` 
**Step 7: Set password for rancid account** 
-------------------------------------------------------------------- 

```
sudo passwd rancid
``` 
 
**Step 8: Test .cloginrc** 
-------------------------------------------------------------------- 
 
As the user rancid test accessing your equipment. 
 
```
su rancid
``` 
 
Now using once of the network devices that you've put in the .cloginrc for rancid type the following in the open terminal. 
 
```
/usr/lib/rancid/bin/clogin  IPADDESSOFDEVICE 
```  
You should see the clogin telnet (or ssh) to the device in question and switch to enable mode on the device. If everything works the proceed on to step 8. Otherwise take a look at your /var/lib/rancid/.cloginrc . 
 
 
[B] 
Step 9: Test grabing a backup config from the same device.[/B] 
-------------------------------------------------------------------- 

As rancid run the following test to make sure that you have everything setup correctly. 
 
```
/usr/lib/rancid/bin/clogin  -c 'write term' IPADDESSOFDEVICE > /var/lib/rancid/backups/test.cfg
``` 
 
 
Verify the output: 
 
```
less /var/lib/rancid/backups/test.cfg
``` 
 
 
If everthing checks out move on to step 10. 
 
 
**Step 10: Create the bash script for the backups** 
-------------------------------------------------------------------- 
 
Here's a sample script for you to copy and paste into a file (i.e. network_device_backup.sh) and to tweak, add, or change for your needs. But save the script somewhere the rancid user can access and execute the script from (i.e./var/lib/rancid/). If you are planning on backing up a various types of routers, switches, firewalls etc you may want to create serveral differnet scripts. 
 
```

#!/bin/bash 
# Variables 
 
clogin=/usr/lib/rancid/bin/clogin 
path=/var/lib/rancid/backups/ 
tdy=`date +%m%d%Y` 
 
#backup network device 
 
$clogin -c 'write term' 192.168.0.1 > $path/foo-$tdy.cfg 
 
``` 
*NOTE: When rancid is installed the default shell for the rancid user is csh. So for the script above to work the "#!/bin/bash' is needed. *


 
**Step 11: Make the script executable to rancid.** 
-------------------------------------------------------------------- 
  
```
sudo chmod 700 /path/to/script
``` 
 
 
**Step 12: Test the backup script.** 
-------------------------------------------------------------------- 
 
Test your script logged in as rancid. 
 
```
su rancid
``` 
 
 
Now from wherever you put the backup script verify that it works before adding it as a cron job. For this example I'm going to use the following location /var/lib/rancid/.scripts/routers.sh with the output path being /var/lib/rancid/backups/. 
 
```
 ./var/lib/rancid/.scripts/routers.sh 
```  
verify the config file that was generated to the output path you specified.
  
```
less /var/lib/rancid/backups/foo-12202005.cfg
``` 


**Step 13: Add script to CRON.** 
--------------------------------------------------------------------

As rancid add your script to CRONTAB.  
```

su rancid

``` 
Now add an entry for your script.

```
crontab -e
``` 
To backup your equipment every Friday at 5pm should look like...

0 17 * * 5  /var/lib/rancid/.scripts/routers.sh >/dev/null 2>&1 

Save the entry (crtl+x).

Verify the entry in crontab is correct.

```
crontab -l
``` 

For more infor on CRONTAB see the following post.
[http://ubuntuforums.org/showthread.php?t=102626]("http://ubuntuforums.org/showthread.php?t=102626")

You're all set... enjoy!

Thank you very much this is awesome

---

### Post by eherna2000 on 2011-08-31
Thank you very much this is awesome!!!

---

### Post by NickCu on 2012-03-12
Hi all,

I was wondering if anyone knows how to manipulate the data returned from the clogin script. 

For example, If I were to run the below command:

[COLOR=Red]*~/bin/clogin -c "show ip ospf ne" 192.168.1.1 > /tmp/ospf.txt*[/COLOR]

And the output looked something like the below:

[SIZE=1][COLOR=RoyalBlue] Router#show ip ospf nei
Neighbor ID     Pri   State           Dead Time   Address         Interfae
192.168.1.2       0   FULL/DROTHER    00:01:54    192.168.1.2     Serial0[/COLOR][/SIZE]

If I could take the output and replace 00:01:54 with xxxxxx before writing it to the .txt file. The idea is to produce less unnecessary Diff's when it comes to troubleshooting... 

I've seen something similar to this with an in house perl script at my old workplace which did a replace on some REGEX however with limited scripting knowledge I don't know where to begin!

If anyone could provide a practical example, it would be much appreciated.  


Many thanks in advance.

---

### Post by gdebaar on 2012-07-05
This HOW TO is amazing. Thank you very much!

However I'd like to add something to the shell script. Everybody knows the situation: you change something on a switch and don't save it into permanent memory. 

I'd like to add a command to the bash script that makes the switch write the flash memory into permanent memory before backing it up. Could anyone of you help me what to do?

Thanks in advance

---

### Post by kool_kid on 2012-12-06
Hi,

Thanks for this amazing guide. I would like to know how to configure RANCID for ASA which does not prompt for username, as in my case. When I telnet to my ASA it is not prompting for username rather it prompts just for the password, how do I configure RANCID accordingly?

Your help is appreciated.

---

