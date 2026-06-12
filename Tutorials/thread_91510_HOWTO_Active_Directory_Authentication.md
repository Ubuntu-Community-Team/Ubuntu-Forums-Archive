---
title: "HOWTO: Active Directory Authentication"
date: 2005-11-17
forum: Tutorials
---

### Post by tfiedler on 2005-11-17
I searched high and low for a good cookie cutter recipe and couldn't find one, so I pieced together parts from various sources to come up with one that I have used for 4 Ubuntu linux servers, and which continues to work for me.

These instructions assume your domain information is DOMAIN (old style domain name) and the DNS resolvable one is DOMAIN.INTERNAL. Our Active Directory environment is running on Windows 2000, but I have tested these instructions in a VMWare Team with Windows 2003 native mode and they worked there as well.

=========================================================

[SIZE="5"]Installing and Configuring Kerberos, Samba, and Winbind on Ubuntu Server 5[/SIZE]

[SIZE="4"]Steps[/SIZE]

**Step 1:  Install the Required Packages**

*Note: Enter Y when asked if you want to install the additional packages*

[FONT="Courier New"]
apt-get install krb5-user
apt-get install winbind samba[/FONT]

**Step 2:  Edit the /etc/krb5.conf File**

```

[logging]
    default = FILE10000:/var/log/krb5lib.log
[libdefaults]
    ticket_lifetime = 24000
    default_realm = DOMAIN.INTERNAL
    default_tkt_enctypes = des3-hmac-sha1 des-cbc-crc
    default_tgs_enctypes = des3-hmac-sha1 des-cbc-crc
[realms]
    DOMAIN.INTERNAL = {
        kdc = domainserver.domain.internal
        admin_server = domainserver.domain.internal
        default_domain = DOMAIN.INTERNAL
}
[domain_realm]
    .domain.internal = DOMAIN.INTERNAL
    domain.internal = DOMAIN.INTERNAL

```

**Step 3:  Edit /etc/samba/smb/conf **

*Notes: Change the NETBIOS name parameter to be correct for the server. Make a backup copy of the original file!!!*

1) Make the edits. The configuration shown is the bare minimum and doesn't share anything.

```

[global]
        security = ads
        netbios name = CMHRG02
        realm = DOMAIN.INTERNAL
        password server = domainserver.domain.internal
        workgroup = DOMAIN
        idmap uid = 500-10000000
        idmap gid = 500-10000000
        winbind separator = +
        winbind enum users = no
        winbind enum groups = no
        winbind use default domain = yes
        template homedir = /home/%D/%U
        template shell = /bin/bash
        client use spnego = yes
        domain master = no

```

2) Test the configuration with the testparm command

**Step 4:  Edit /etc/nsswitch.conf to look like the example below**

```

passwd:         compat winbind
group:          compat winbind
shadow:         compat
hosts:          files dns wins
networks:       files
protocols:      db files
services:       db files
ethers:         db files
rpc:            db files
netgroup:       nis

```

**Step 5:  Modify the PAM settings**

1) /etc/pam.d/common-account should contain only the following lines

```

account sufficient	pam_winbind.so
account required		pam_unix.so

```

2) /etc/pam.d/common-auth should contain only the following lines

```

auth    sufficient      pam_winbind.so
auth    required        pam_unix.so nullok_secure use_first_pass

```

3) Modify the /etc/pam.d/common-password file, so the max parameter is set to 50, similar to the one shown below

```

password   required   pam_unix.so nullok obscure min=4 max=50 md5

```

4) Make sure the /etc/pam.d/common-session file contains the following line

```

session required        pam_mkhomedir.so umask=0022 skel=/etc/skel

```

**Step 6:  Make a directory to hold domain user home directories**

*Note: Use the value you put in the WORKGROUP tag of the /etc/samba/smb.conf file*

```
mkdir /home/DOMAIN
```

**Step 7:  Initialize Kerberos**

1) ```
kinit domain_admin_account@DOMAIN.INTERNAL
```

Next check to be sure you got a ticket from the domain controller

2) ```
klist
```

**Step 8:  Join the system to the **

```
net ads join -U domainadminuser@DOMAIN.INTERNAL
```

**Step 9:  Restart Samba-related Services (Or reboot the server)**

*Note: The order is important*

```

/etc/init.d/samba stop
/etc/init.d/winbind stop
/etc/init.d/samba start
/etc/init.d/winbind start

```

**Step 10:  Restart SSH and Test Connectivity**

*Note: If you rebooted the server in the previous step, just try and login.*

```

/etc/init.d/ssh restart

ssh useraccount@server

```

If you can login using your active directory username and password then everything is working!

**Step 11:  Configure SUDO**

1) First create a group in Active Directory called UnixAdmins and add the names of people whom you want to be able to use sudo to admin the server. 

2) Next, add the UnixAdmins group to the /etc/sudoers so these users can use sudo

```
%UnixAdmins ALL=(ALL) ALL
```



[SIZE="4"]HELPFUL COMMAND LINES[/SIZE]

1) List the derived UNIX GID values for Active Directory groups

```
for gid in $(wbinfo -r <username>); \
do SID=$(wbinfo -G $gid);GROUP=$(wbinfo -s $SID); echo $gid is $GROUP; done
```

2) See the Active Directory SID for a particular named user

```
wbinfo –n <username>
```

---

### Post by herot on 2005-11-17
will these intructions allow me to have access to my windows 2003 server shares??? i am thinking of making the ubuntu desktop a viable option at my workplace...

---

### Post by evs on 2005-11-17
[QUOTE=herot]will these intructions allow me to have access to my windows 2003 server shares??? i am thinking of making the ubuntu desktop a viable option at my workplace...[/QUOTE]

You should be able to access the shares with the default Samba config.  I used to use my laptop with Hoary at work, and it was fine.  Go to Places->Connect to Server and choose Windows Share and you'll need to save your user name and password and stuff.  

This howto is great, I tried this like a year ago unsuccessfully.  I wasn't using Winbind, however, so maybe that will make the difference.  I can't wait till I get a chance to test some new machines on the network.  Thanks a lot.

---

### Post by darius_underhill on 2005-11-18
HI Sir!

I apologize for being so ignorant but here is my situation.  I was just promoted to System Admin from a Technical Support agent (due to the lack of IT personel left).  And one of the task delegated to me is setup a centralized username/password authentication for all our workstations.  our network is currently composed of around 20 Windows XP and 10 Ubuntu Linux (breezy).  

I imagine that i should use Microsoft's Active Directory for the windows xp workstations.  However i am not too sure if i am to use your HOWTO so that my Ubuntu Linux workstations will authenticate using Active Directory.  Can I use your Howto so that all of our windows xp and ubuntu linux workstations to authenticate with a single active directory server?

Please help or atleast point to some reference I can use.

Thanks.

---

### Post by intangible on 2005-11-18
I have already set up my Linux boxes manually to join the domain, but I was wondering if anyone has had any luck with this tool: [http://sadms.sf.net](http://sadms.sf.net) ?  It looks like the perfect tool to do all this with a gui instead of manually, and they have a Ubuntu package :D

---

### Post by slamp on 2005-11-27
great tutorial! i have now joined my ubuntu server into my domain. i do have a question.

how do i setup multiple groups in a folder in linux?

i want groups that can read/write and groups that can only read.

so far i have setup a group in active directory and made to be able to read and write to the samba share, but i do not know of anyway to make another one that can only read.

---

### Post by slamp on 2005-11-28
Replying to my own question.

ACL was the answer!

---

### Post by intangible on 2005-11-30
If you're using ACLs, check out this, love the intergration with nautilus: [http://rofi.pinchito.com/eiciel/](http://rofi.pinchito.com/eiciel/)

**sudo apt-get install eiciel**

[http://packages.ubuntu.com/breezy/gnome/eiciel](http://packages.ubuntu.com/breezy/gnome/eiciel)

---

### Post by Mujaheiden on 2006-01-10
Hi,
I dont know what's my DOMAN or my DOMAIN.INTERNAL. Im on the uinimaas.nl Active direcory. Which should It try?
thx

---

### Post by derelict on 2006-01-10
Greetings,

I followed the howto step by step but I'm getting "kinit(v5): Cannot resolve network address for KDC in requested realm while getting initial credentials" when I run "kinit [email]Administrator@home.brr[/email]". However, I can nslookup the computer I specified on "[realms] kdc" (it's both the AD PDC and DNS server). What can I be doing wrong? :confused: 

Thanks in advance :)


[quote=Mujaheiden]
I dont know what's my DOMAN or my DOMAIN.INTERNAL. Im on the uinimaas.nl Active direcory. Which should It try?
[/quote]
In your case DOMAIN is uinimaas and DOMAIN.INTERNAL is uinimaas.nl

---

### Post by stevea1210 on 2006-01-10
[QUOTE=derelict]Greetings,

I followed the howto step by step but I'm getting "kinit(v5): Cannot resolve network address for KDC in requested realm while getting initial credentials" when I run "kinit [email]Administrator@home.brr[/email]". However, I can nslookup the computer I specified on "[realms] kdc" (it's both the AD PDC and DNS server). What can I be doing wrong? :confused: 

Thanks in advance :)



In your case DOMAIN is uinimaas and DOMAIN.INTERNAL is uinimaas.nl[/QUOTE]


Are you using home.brr or HOME.BRR.  Caps is required.

---

### Post by derelict on 2006-01-11
Yes, all references of "home.brr" on the krb5.conf file were on capital letters as shown by the HOWTO, I keep getting that error :confused:  
I can ldapsearch the AD server and obtain user info without any problem.

---

### Post by stevea1210 on 2006-01-11
There were two things not mentioned in this how to that could possibly cause isssues for some people.  Derelict, can you check the below out. 

1) /etc/hosts isn't edited.  The default ubuntu installation would give you
```
127.0.0.1     localhost.localdomain     localhost     ubuntu 
```
That should be modified to include the domain that you are joining.  It should look more like this
```
127.0.0.1      FQDN      localhost       pc name
```
Example using domain from the how to with pc name of "test"
```
127.0.0.1     test.domain.internal     localhost     test
```

suggest a reboot after that to ensure no naming conflicts anywhere.

2)syncing time with the domains NTP server
the /etc/default/ntpdate file should be edited to reflect the FQDN of your ntp server (usually your domain controller)

Again using the domain from the how-to, modify as needed.

```
# servers to check
NTPSERVERS="domainserver.domain.internal"
# additional options for ntpdate
NTPOPTIONS="-u"

```

Then restart the service
```
sudo /etc/init.d/ntpdate restart
```

Kerberos won't give you a ticket if the times are too far apart between the DC and the PC

---

### Post by derelict on 2006-01-11
OK, it looks like it's making progress :)
I changed the hosts file to 
"127.0.0.1       ubuntu.home.brr         localhost       ubuntu"
and I'm now getting
"kinit(v5): KDC has no support for encryption type while getting initial credentials"

Here's the [libdefault] section of my krb5.conf, up to the [realms] section:
```

ticket_lifetime = 24000
default_realm = HOME.BRR
default_tkt_enctypes = des3-hmac-sha1 des-cbc-crc
default_tgs_enctypes = des3-hmac-sha1 des-cbc-crc

```

I'm running AD on a 2003 Server, should I change the enctypes? The time difference between hosts was already below 30 seconds, it had occured to me before that Kerberos needed some time sync.

---

### Post by derelict on 2006-01-11
[QUOTE=derelict]
I'm now getting
"kinit(v5): KDC has no support for encryption type while getting initial credentials"
[/quote]

I solved it by resetting the Administrator password :) It looks like I now have a Kerberos ticket already, I'll post back the whole result (hopefully successful!)

Thanks steve :)

---

### Post by derelict on 2006-01-11
OK, I successfuly added the computer to the realm, thanks for all the help so far! However, I was aiming at being able to login with an AD user via the graphical startup prompt; do I have to edit /etc/pam.d/gdm?

Thanks in advance! :)

---

### Post by stevea1210 on 2006-01-12
Following this how to should allow you to log in with an AD account.  There are three main ways to login, based on editing the smb.conf.
As it is set now, you should be able to login with just username password.  The line 
```
 winbind use default domain = yes
```
will have winbind assume all logins are from the default domain.

If you set that to no, or comment it out, you would need to prepend the username with the domain.  The winbind seperator determines which character goes between the domain and username.
```
winbind separator = +
```

If you copied this smb.conf, it would be:
DOMAIN+username  (ensure caps in domain)

The default (read, commenting out that line with a #) is backslash, so it would be:
DOMAIN\username  (caps again).

BTW you're welcome,  love to help when I can.

---

### Post by derelict on 2006-01-13
Once again you got it :) 
It's logging in perfectly, I'm now working on changing the AD password via Linux (smbpassword, correct?) and getting it to create the user directory (/home/domain/user) with 700 permissions. Thanks! :)

---

### Post by zachariah on 2006-01-19
Just to add I used SADMS to successfully do all the legwork on the .conf files and it works fairly well. You have to read the documentation very carefully and follow everything to the letter, but you will end up with a Ubuntu box that can log in to the domain just like any XP machine. 

It will also configure the previously unmentioned pammount file to allow each user to automatically link to shares on the Windows server. This works best if your user files are all in one directory and are all named after the login name.

Edited to add:
After updating the Linux kernel image, the AD logins refused to work. Running the SADMS configuration did the trick, but it was a scary moment.

Your SADMS settings file should read like the following:

```
# My Settings

realm=MY.FQDN.IN.CAPS
dns=your.dns.server.with.FQDN
kdc=yourkerberosservername *(must be DNS resolvable)*
domain=DOMAINNAMEINCAPS *(just the root name, eg for google.com you would just enter GOOGLE)*
server=localhost NETBIOS name, default is ubuntu or linux
hostOu=Computers *(or whichever AD unit you want the system to be listed)*
administrator=administrator
administratorPassword=yourpassword *(no need to save this in plain text, you can enter it within SADMS!)*
users=domain users *(or whatever you prefer the default users to be)*
hostsAllow=10.
winsServer=IP.address.of.yourWINSserver

```

---

### Post by ariek on 2006-02-01
Thanks for this great howto, exactly what I needed!

Arie

---

### Post by antihippy on 2006-02-01
Hi,

I am interested in trying out SADMS but I cannot get it to install.  I am fairly new to Ubuntu and Linux in general. I've been on the SADMS website and downloaded, what I think is, the correct package: sadms-install-ubu-2.0.1.tar.gz
I've unpacked it and I now have a folder called sadms-2.0.1.  When I try doublicking the start script I run it in terminal and I can see lots of errors flicking past.  I have winbind and samba installed.

How do I install sadms?  Have been thick about something?

I've been all over the sadms project pages and there's not much help.

Any help would be much appreciated.

Thanks

PS - I don't think that there is anything wrong with SADMS - it's just my newbieness.

---

### Post by RxTech on 2006-02-01
I'm having a problem, everything worked fine, i was able to join the domain but i log in...using domain logins or locals.

I get this error message in my auth.log
```

Feb  1 16:29:43 testws sshd[4090]: (pam_unix) auth could not identify password for [MYUSERNAME]
Feb  1 16:29:45 testws pam_winbind[4090]: user 'MYUSERNAME' granted access
Feb  1 16:29:45 testws sshd[4085]: error: PAM: Authentication information cannot be recovered for MYUSERNAME from testws.mydomain.com



Feb  1 16:44:08 testws login[4096]: (pam_unix) auth could not identify password for [MYUSERNAME]
Feb  1 16:44:10 testws pam_winbind[4096]: user 'MYUSERNAME' granted access
Feb  1 16:44:14 testws login[4096]: FAILED LOGIN (1) on `tty1' FOR `MYUSERNAME', Authentication information cannot be recovered


```

Any ideas??

PS. I'm authenticating to a win2k3 dc

---

### Post by Mujaheiden on 2006-02-13
:(  I think this Active Directory login is too difficult for me. I have no clue as to what im doing, and what I doe doenst work. Ill just wait for an automix like script, if ever...
Thanx anyway

---

### Post by SuperMike on 2006-03-01
tfiedler,

Wow, got this working, but had to alter the steps slightly. This is way cool stuff here!!! It's sensational that you figured all this out, though. Perhaps things have changed in Ubuntu 5.10 or something. What's cool about this is that my PC is now a member of the AD domain and if I add a unix account with useradd and don't specify a password or use passwd, I can use the password from the AD domain instead of the password on the Unix account. Note that you do not need to use smbpasswd anymore! That's one less admin chore -- and you won't have to worry about password synchronization again with Samba because it passes on to the AD domain.

Here's what I had to do that was so special.

1. Had to put my FQDN in /etc/hosts on the 127.0.0.1 line before localhost. (For noobs -- do hostname to find your hostname. Then, tack on the domain on the end. In my case it was something like UBUNTU.MY_AD_DOMAIN.COM.) 

2. Had to turn on Ubuntu Universe option in /etc/apt/sources.list, then do this:

apt-get update
apt-get install krb5-user

...Note that when you do this and it begins to install it, a blue screen will pop open and ask you for the IP address of your closest domain controller for the domain you want to authenticate against.

apt-get install winbind samba

3. Had to use a variation on your /etc/krb5.conf file:

[logging]
    default = FILE10000:/var/log/krb5lib.log
[libdefaults]
    ticket_lifetime = 24000
    default_realm = MY_AD_DOMAIN.COM
    default_tkt_enctypes = des3-hmac-sha1 des-cbc-crc
    default_tgs_enctypes = des3-hmac-sha1 des-cbc-crc

[realms]
MY_AD_DOMAIN.COM = {
         # The "kdc" should be the IP addr of your closest domain controller.
         kdc = 192.168.0.2
}

[domain_realm]
        .my_ad_domain.com = MY_AD_DOMAIN.COM
        my_ad_domain.com = MY_AD_DOMAIN.COM
# end

Note that I did not use admin_server or default_domain because I was getting errors. I commented them out and to my surprise my kinit statement was working.

4. In reference to all those files in /etc/pam.d that you had us edit, if you get one character wrong, you will blow your authentication! Warning! Therefore, I cut and paste from your post and was back in business again.

5. My smb.conf was almost exactly the same. I just want to comment that my password server line reflects the IP address of the closest domain controller. This should match what's in krb5.conf

[global]
unix charset = LOCALE
workgroup = MY_AD_DOMAIN
realm = MY_AD_DOMAIN.COM
netbios name = UBUNTU
server string = Samba
security = ADS
password server = 192.168.0.2
winbind use default domain = yes
client use spnego = yes
domain master = no
username map = /etc/samba/smbusers
log level = 1
syslog = 0
log file = /var/log/samba/%m
max log size = 50
printcap name = CUPS
ldap ssl = no
idmap uid = 10000-20000
idmap gid = 10000-20000
template primary group = "Domain Users"
template shell = /bin/bash
winbind separator = +
printing = cups

[public]
path = /tmp/public
available = yes
browseable = yes
public = yes
writable = yes
create mode = 0755
directory mode = 0755
read only = no

6. I think I had to backup and remove all my /var/lib/samba/*.tdb files and bounce winbind and samba like you mention in order for this to work properly, not caching stuff generated from my previous tests.

7. I found I had to play with chmod on /tmp/public to let other users in. You could do it the world-read-writable way (your security experts will have a cow) with chmod a+x /tmp/public, but you're better off mapping the Linux user account to a folder with chown and setting perms with chmod u+x /tmp/public/my_user_folder

Hope this helps everyone!

---

### Post by SuperMike on 2006-03-02
Some oddities about Samba that I found are these. I don't know if it's just this version, or if it's Ubuntu, or what.

* The shares act funny in Windows 2000 and XP. If you do Start, Run, \\<server and doubleclick the share, then create a new folder, it appears properly and you are given a chance to rename it. But if you close that window and repeat this step, you can create folders but not have a chance to rename them until you refresh your window with F5 key. The same goes for renaming them, creating new files, etc. I can see people getting fairly aggravated by this. I don't know how to fix that.

* Another way the shares act funny is that you cannot edit the NTFS perms from Windows. It will let you start it, but then it won't let you apply those changes. Instead, these must be applied with chown and chmod on the Linux server. This is to be accepted, of course. Just wanted to make you aware of this in case you were a noob and were assuming you can just edit the NTFS permissions from within Windows.

* I had to turn off my firewall for now to get this going. I'm not really sure what all ports need to be opened up to make this work.

* I tried editing the /etc/pam.d/common* files to see if I could trick my Linux so that it only authenticated to the company domain. I wanted to not have to use useradd for every new Samba account I wanted to add to the system. Unfortunately, this almost worked, but not completely. I noticed that it caused the passwords to lockout on the domain controller, but it still wouldn't let me have access to the session. I would imagine with some tweaking in these files I just might get it to work.

---

### Post by StRobo on 2006-03-02
Great howto since it solved all my problems. However, I have one problem and can't seem to quite figure out the correct way to do it.

The user logged on will be a 'domain user' and as such is NOT part of the cdrom, audio, video groups for instance.

Assume I have a user 'foo' that logs in correctly. How do I 'attach' this domain user to the audio group?

---

### Post by Draaku on 2006-03-03
Hi, I am trying the sadms app, and here is what i get:

could not acquire Kerberos ticket
+WARNING
Kerberos requires administrator's password
to have been reset once since domain install
in order to add DES encryption keys to user
account which only has a RC4 key when
initially created.
[ERROR]
returned error code 4
command line was <./_install.sh  'FROOT.NAU.EDU' 'nau.froot.nau.edu' 'froot.nau.edu' 'FROOT' 'ucc123' 'Computers' 'fg32' '*****' 'Domain Users' '134.114.70.0/255.255.255.0' ''>

---

### Post by stevea1210 on 2006-03-03
[QUOTE=Draaku]Hi, I am trying the sadms app, and here is what i get:

could not acquire Kerberos ticket
+WARNING
Kerberos requires administrator's password
to have been reset once since domain install
in order to add DES encryption keys to user
account which only has a RC4 key when
initially created.
[ERROR]
returned error code 4
command line was <./_install.sh  'FROOT.NAU.EDU' 'nau.froot.nau.edu' 'froot.nau.edu' 'FROOT' 'ucc123' 'Computers' 'fg32' '*****' 'Domain Users' '134.114.70.0/255.255.255.0' ''>[/QUOTE]

I have read on some sites that the admin password on the DC needs to be reset before it will work.  I think this was ties to win 2k, but I could be remembering incorrectly.  Reset the admin account password, then reset it again to what it was previously (for convenience).  Then try it again.

---

### Post by stevea1210 on 2006-03-03
[QUOTE=StRobo]Great howto since it solved all my problems. However, I have one problem and can't seem to quite figure out the correct way to do it.

The user logged on will be a 'domain user' and as such is NOT part of the cdrom, audio, video groups for instance.

Assume I have a user 'foo' that logs in correctly. How do I 'attach' this domain user to the audio group?[/QUOTE]

I had the same problem.  I wrote a down and dirty script to add domain users to local groups on the linux box.  Here is the link
[http://ubuntuforums.org/showpost.php?p=458664&postcount=6]("http://ubuntuforums.org/showpost.php?p=458664&postcount=6")

Give that a try, it should take care of it.  You can add users to audio, as well as any other needd groups using it.

---

### Post by stevea1210 on 2006-03-03
[QUOTE=SuperMike]Some oddities about Samba that I found are these. I don't know if it's just this version, or if it's Ubuntu, or what.

* Another way the shares act funny is that you cannot edit the NTFS perms from Windows. It will let you start it, but then it won't let you apply those changes. Instead, these must be applied with chown and chmod on the Linux server. This is to be accepted, of course. Just wanted to make you aware of this in case you were a noob and were assuming you can just edit the NTFS permissions from within Windows.

[/QUOTE]

Make sure the partition on the samba server is mounted with acl.  Below is a line from my /etc/fstab.  Note the acl in it.

```
/dev/hdc1       /netshares     ext3    acl,defaults      0       1

```
Aftr editing fstab, remount the drives
```
sudo mount -a
```

That should fix the inability to edit acl's from windows.

---

### Post by Draaku on 2006-03-06
[quote=stevea1210]I have read on some sites that the admin password on the DC needs to be reset before it will work.  I think this was ties to win 2k, but I could be remembering incorrectly.  Reset the admin account password, then reset it again to what it was previously (for convenience).  Then try it again.[/quote]

domain admin will not change password to help me with this. doesnt want to risk it. is there no other way? I have rights to add computers and users to domain, and I just reset my password.

---

### Post by stevea1210 on 2006-03-07
[QUOTE=Draaku]domain admin will not change password to help me with this. doesnt want to risk it. is there no other way? I have rights to add computers and users to domain, and I just reset my password.[/QUOTE]

After resetting your password, did you try it again?
When you are trying to get your ticket, are you using your username/password 
(since your password was just reset)?

AFAIK, each place I read about the admin password needing reset, that was always the solution.  I don't know of another way around it.  I'm not saying it isn't possible, just that I haven't heard of any.

Another option is to try to swet talk the admin on how joining your Ubuntu box to the domain will aid in blah blah.  It will make his life  blah blah.  What's the worst that can happen?

---

### Post by bluemax on 2006-03-09
I completed all the steps up to joining the domain. I thought I should be logged in as an actual AD user when I did that, so I created a new user for my username in AD, and then logged in as that user. But then, when I try to do the 'net ads join' command I get this error:
```
Failed to open /var/lib/samba/secrets.tdb
```

Is this because I set everything up as a different user (who isn't a domain user)?

EDIT: Actually I get this error no matter which user I'm logged in as, when I try to join the domain. Any ideas what's wrong? File permissions maybe?

---

### Post by stevea1210 on 2006-03-09
[QUOTE=bluemax]I completed all the steps up to joining the domain. I thought I should be logged in as an actual AD user when I did that, so I created a new user for my username in AD, and then logged in as that user. But then, when I try to do the 'net ads join' command I get this error:
```
Failed to open /var/lib/samba/secrets.tdb
```

Is this because I set everything up as a different user (who isn't a domain user)?

EDIT: Actually I get this error no matter which user I'm logged in as, when I try to join the domain. Any ideas what's wrong? File permissions maybe?[/QUOTE]

It is the permissions on /var/lib/samba/secrets.tdb.  I had that issue also.  I chmoded mine to 777, which may be (and probably is) overkill.  I wasn't sure if all users needed read/write/execute on it, but that did fix the issue.  

```
sudo chmod 777 /var/lib/samba/secrets.tdb 
```

BTW, this is for my home network, not a corporate environment, so a few 777's isn't as big of a risk as in a corporate setting.  If anyone knows what the actual NEEDED permissions on this are, I would be all ears.

---

### Post by StRobo on 2006-03-10
I had the same issue but instead of chmod'ing I simply ran 
```
sudo net ads join
```
and that worked great.

Thanks for all the info in this thread. It truly is a great one.\\:D/

---

### Post by Swab on 2006-03-18
Followed the guide and everything is working, however each time I log in as a domain user I have to manually issue the kinit command to get a ticket... does anyone have a way around this?

---

### Post by scav on 2006-03-18
replace pam_winbind.so with pam_krb5.so

---

### Post by Swab on 2006-03-18
Thanks, I'll try that on Monday!

---

### Post by wmarchewka on 2006-03-18
Hi all. I am able to log on using a active directory user and pass. But when i try to connect to any shares via "Connect to Server...", it prompts me for a username and pass. The logged on user and domain is there, its wanting a password. If i type in a password, i am to sucessfully browse the share.Is this normal behaviour? I thought that since i am logging on as a ad user, i would be able to view any shares that the user had permission for? The user is a new user i created on my 2K3 server, and i added them to  UnixAdmins. The user works from a XP machine and is able to browse shares, but just not from the Ubuntu box. I can do all this sucessfully too...

    * Test domain computer account: net ads testjoin.
    * Test winbindd: wbinfo -u to list AD users and wbinfo -g for groups.
    * Test kerberized Samba: net ads user and net ads group should show you your AD users and groups (i.e. same as above).
    * Test kerberized connection to a remote Windows server: smbclient -L //WINSERVER -k from the Samba server. While you're at it, connect locally to the Samba server the same way.
    * Finally, test connectivity from a Windows box: Start -> Run -> \\SAMBASERVER.
    * Run wbinfo -t it should return: checking the trust secret via RPC calls succeeded, otherwise you have done somthing wrong (use the command testparm -v to check your samba configuration). 

So what am i missing? Thanks in advance. I thought i triple checked all the config changes that this thread called for...

---

### Post by wmarchewka on 2006-03-19
I found that i am actually having the same trouble as Swab, where i have to manually enter the Kinit command. Scav, you said to replace pam_winbind.so with pam_krb5.so, and i have tried in both the common-auth and common-account and neither seemed to work...

---

### Post by stevea1210 on 2006-03-19
$wmarchewka:
Is this the line you put in your /etc/pam.d/common-auth?
```
auth    sufficient    pam_krb5.so
```
instead of having 
```
auth     sufficient      pam_winbind.so
```

Of cource after installing libpam-krb5.

I wasn't getting a ticket at logon either, and making the above changes took care of it for me.  I now get one at each logon.  BTW, I didn't touch my common-account for this.

---

### Post by dingbatca on 2006-03-22
Just trying to get the base packages for binding to AD. I get an error, any ideas? Clean install of 5.10.  I also updated the system with apt-get update, and upgrade.

root@cslinux4:~# apt-get install winbind samba
Reading package lists... Done
Building dependency tree... Done
Package winbind is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package winbind has no installation candidate
root@cslinux4:~#                                   

root@cslinux4:~# apt-get install krb5-user
Reading package lists... Done
Building dependency tree... Done
Package krb5-user is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  krb5-doc
E: Package krb5-user has no installation candidate

---

### Post by Swab on 2006-03-22
[QUOTE=dingbatca]Just trying to get the base packages for binding to AD. I get an error, any ideas? Clean install of 5.10.  I also updated the system with apt-get update, and upgrade.

root@cslinux4:~# apt-get install winbind samba
Reading package lists... Done
Building dependency tree... Done
Package winbind is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package winbind has no installation candidate
root@cslinux4:~#                                   

root@cslinux4:~# apt-get install krb5-user
Reading package lists... Done
Building dependency tree... Done
Package krb5-user is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  krb5-doc
E: Package krb5-user has no installation candidate[/QUOTE]


I think winbind and krb5-user are both in the universe repository

---

### Post by dingbatca on 2006-03-22
I am well versed in Gentoo and Redhat/Fedora/CentOS, but I must state that I have no clue how to use apt-get.  How do I switch to the "universe repository"?

---

### Post by Swab on 2006-03-22
[QUOTE=dingbatca]I am well versed in Gentoo and Redhat/Fedora/CentOS, but I must state that I have no clue how to use apt-get.  How do I switch to the "universe repository"?[/QUOTE]

You can add repositores by following either of these wiki pages... should get you up and running.

[https://wiki.ubuntu.com/AddingRepositoriesCliHowto](https://wiki.ubuntu.com/AddingRepositoriesCliHowto)
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by dingbatca on 2006-03-29
OK, all 6 of my client systems are up and running with graphical log in and pam_mount running.  Now I am stuck on a new issue.  When ever I log into a different system my UID & GID changes.  Any ideas?

---

### Post by StRobo on 2006-03-31
No great ideas other than modifying the         
idmap uid = 500-10000000
idmap gid = 500-10000000
values a bit.

You could probably get different uid/gid values if you have a different amount of local users on the different systems. You could try to set 
idmap uid = 1000-10000000
idmap gid = 1000-10000000

This is just in theory though as I can not try it right now and I have not tried it before either.

HTH

---

### Post by sigtau66 on 2006-04-05
I have a good one for everybody to see if they can figure out.  When I try to join the domain with my box, I get this unique error:

```
[2006/04/05 21:59:27, 0] utils/net_ads.c:ads_startup(191)
  ads_connect: Invalid credentials

```

This is after I enter my password and hit enter.  Now, here comes the wrinkle. :D 

When I first did this on my box, it was successful, BUT I had misconfigured my smb.conf file in a major way.  For the NETBIOS name, I stupidly typed in my domain controller's name.  DOH!](*,)   So it told me the host account already exists, but it was modifying it..blah, blah, blah.  Well, I don't seem to have messed up my domain as all my windows boxes can log in.

Now, though, I can't join this machine to the domain.  I've changed the smb.conf file to reflect the right netbios name.  I've reset the administrator password for the domain admin.  Hell, I've even created a new domain admin account and got a ticket for that account and it still doesn't work.  I've renamed all the /var/lib/samba/*.tdb files and restarted samba and winbind.  

At this point, google isn't helping me so I was wondering if any of you have ran into and what the solution is.

Anybody? :)

---

### Post by intangible on 2006-04-06
Manage your active directory and remove delete any references to the old computer name and the new one and then try to rejoin.

---

### Post by sigtau66 on 2006-04-06
> Manage your active directory and remove delete any references to the old computer name and the new one and then try to rejoin.

Did that too.  

Right now, this isn't a problem because I just rebuilt my box again.  The funny thing is that right after I posted that last night, I wanted to try a reboot.  Once I rebooted, I COULDN'T login.  All my credentials were wrong.  It was an odd issue.  So, seeing no way around it and since nothing was on it, I just rebuilt.

I'm going to try this again later today and MAKE sure not to screw up my smb.conf file.

---

### Post by bushtor on 2006-04-10
Hi,

I've started to implement this howto, but before proceeding I just want to ensure that it covers about what I need.

My scenario:

A W2003 domain controller and DNS server with around 300 user accounts.
Ubuntu 5.10 server with samba as file- and print server.

When a user for the first time log in to the w2003 server, 
a personal home folder should be created in ubuntu as described in this howto.  
At the same time a personal profile folder should be created in /ubuntuserver//home/<domain>/profiles/<username>
All the above with correct access credientials   

Can someone confirm that following this thread gives me the above mentioned personal (samba hosted) home folders for each user logging in to the w2003 dc?

How do I have personal profile folders created automaticaly the same way as the home folders?

Please comment if ths howto does not fit into my scenario and point me in the right direction ;-)

When having this up and running, we're looking for a good and reliable print manager running under ubuntu.  We need to keep track of the users' page count etc..  What are you guys using for this purpose?

regards

Tor

---

### Post by kubark42 on 2006-04-25
I used this a combination of this howto and SADMS to get my park of kubuntu realtime machines authenticating against the university's AD server. Great!

Just two things that are annoying. 

1) I can't figure out how to change the shares server based on the login. There are two windows shares here, Poseidon and Atlas. Poseidon is for students and Atlas for researchers. So if bob.student logs in, he should authenticate to Poseidon, whereas fred.researcher should authenticate to Atlas.

2) The IT department tracks printer usage based on user accounts. Right now, the printer installed on the machine uses a generic account for printing. Ideally, the user login/password would be used, instead of the generic account.

I've googled a lot, but am really out of my depth when it comes to AD. Any ideas for how to fix these two problems?

---

### Post by WesternH on 2006-06-30
Guys, i got this error message in /var/log/samba/log.winbind 
rpc_client/cli_pipe.c:cli_rpc_pipe_open_noauth(2240)
  cli_rpc_pipe_open_noauth: rpc_pipe_bind for pipe \lsarpc failed with error NT_STATUS_BUFFER_TOO_SMALL

can anyone help me?
I still can't log on the domain after follow the instruction here. Everything seen to be fine and there are no error messages except this on the the log.winbind. Do i have to edit the /etc/pam.d/login ?
Thanks for your time.

---

### Post by Novack on 2006-07-13
Thanks for the great FAQ.

However, I have 2 problems.

First, with sudo. I can get sudo access for single AD users working, but not for groups.

This works:
myadmin ALL=(ALL) ALL

This doesn't:
%UnixAdmins ALL=(ALL) ALL



Secondly, can anyone tell me how I can add AD users as members to local unix groups? 
I can run this command OK with the expected results:
```
for gid in $(wbinfo -r <username>); \
do SID=$(wbinfo -G $gid);GROUP=$(wbinfo -s $SID); echo $gid is $GROUP; done
```
However, running 'getent passwd' (which I found from the winbindd guide on the Samba website) does not return the logged in AD user like it should according the Samba guide.

---

### Post by k999 on 2006-07-18
Hi,

Can I set this up so that the user logs in with her home directory on a samba share? I want everything the user saves to be on the server where everything is backed up, as well as one place to administer user accounts, and the most user friendly way to do this is to make the home directory lie on a samba share.

I also want the directories on the samba share to be accessible from a terminal window, and not just from the GUI. When I use "Places" > "Connect to Server..." I just get an icon on the desktop, it doesn't seem like the share is mounted locally.

---

### Post by jr_hearty on 2006-07-18
I'm running 6.06.  When I try to install krb5-user, it says the package is no longer available.  Does anyone have suggestions?

---

### Post by jon_anderson_ca on 2006-07-19
> **StRobo said:**
> Assume I have a user 'foo' that logs in correctly. How do I 'attach' this domain user to the audio group?

Take a look at ["Giving power to the user in front of the screen"]("http://www.debian-administration.org/articles/308"), from [debian-administration.org]("http://www.debian-administration.org/"). It shows how to configure pam_group to let the local user be in audio/cdrom/floppy/video/etc. without messing up /etc/group.

---

### Post by HighPlainsDrifter on 2006-07-21
By "reset" the password, do you mean you had to give the administrator account a completely new password?

---

### Post by digitalexpl0it on 2006-07-26
hello all,

I've been following this thread for a few days and I have to say is thank you for the documentation. It helped me out a lot. I've been creating a little GUI to help those who are new to linux or not comfirtable on editing conf files from the cammd prompt or using gedit or whatever. For those who want to test out the app I'll post it below.

Note: this application is still alpha and could mess up your linux box so make sure you backup everything so if somthing does happen you can go into rescue mode log in as root then copy back the files. This application does backup the conf files before writing to them but if you dont save the _BACKUP it will over write the back file if you try to reconfigure the conf files with the GUI.

Also you will need to install lib to run this. I am in the proccess of installing ubuntu on vmware so I can make a better howto and what libs you need to install.

[IMG]http://www.daemonprojects.com/xantar/Screenshot-1.jpg[/IMG]

[IMG]http://www.daemonprojects.com/xantar/Screenshot-3.jpg[/IMG]

Remember to run the application as root.
File Download: [http://www.daemonprojects.com/xantar/Xantar.run]("http://www.daemonprojects.com/xantar/Xantar.run")

you will need to run the following before running Xantar

apt-get install libstdc++5

---

### Post by Scott07 on 2006-09-14
> **jr_hearty said:**
> I'm running 6.06.  When I try to install krb5-user, it says the package is no longer available.  Does anyone have suggestions?

Yes I have just got it working about 10 minutes ago, what you need to do is install kerberos manually.  This means you need to install the bits and bob's needed to compile packages from source as far as I remember these are:
make,
gcc-base
gcc

You will also need to install the cursors/ncursors libary and the C developers version (again in the package manager) and something to do YaST (there are a few tools in the package manager).  

Now go here: [http://www.mit.edu/~kerberos/dist/index.html](http://www.mit.edu/~kerberos/dist/index.html) and download the Kerberos source and extract it.  Then fire up konsole (or equlivant) in Super-User mode and cd to the src directory in the extracted kerberos folder.  Type "./configure" and let it run (it might stop with an error code because you dont have a dependancy, you should be able to find one to cover that in the package manager just have a hunt arround).  After configure has done type "make" (again you might have some dependancy problem) and once thats done type "make install".  Kerberose will now be installed and working so you can follow the steps in the first post to get it to work.  

Just a warning, I have only tried this on a windows 2000 active directory domain.

Have fun!

---

### Post by ximok on 2006-09-18
Ok, when I join a win2k machine to my Win2k AD Domain it joins within a few seconds.

My linux boxes take anywhere from 10 to 45 minutes when I do net ads join!!

As root:

kinit [email]adminuser@ABCDEF.XYZ[/email]

<type in password>
klist shows me my tickets (which look ok?)

net ads join

(wait forever)](*,) 

command completes

net ads testjoin shows that my join is complete.  It just took forever.

I can login just fine after it joins, it just takes way too long to be anything efficient during install.

Ideas?

Here are some files for you to view
krb5.conf
```
[logging]
        default = FILE:/var/log/krb5.log

[libdefaults]
        ticket_lifetime = 24000
        clock_skew = 300
        default_realm = ABCDE.XYZ
#       dns_lookup_realm = false
#       dns_lookup_kdc = true

[realms]
        COLSD.ORG = {
                kdc = kdc1.abcde.xyz
                kdc = kdc2.abcde.xyz
                admin_server = kdc1.abcde.xyz
                default_domain = ABCDE.XYZ
}

[domain_realm]
        .abcde.xyz = ABCDE.XYZ
        abcde.xyz = ABCDE.XYZ
```


smb.conf
```
[global]
        security = ads
        realm = ABCDE.XYZ
#       password server = kdc1.abcde.xyz
        workgroup = ABCDE
        winbind separator = +
        allow trusted domains = No
        idmap uid = 10000-2000000
        idmap gid = 10000-2000000
        winbind enum users = No
        winbind enum groups = No
        winbind cache time = 15
        template homedir = /home/%D/%U
        template shell = /bin/bash
# spnego disabled due to bug
        client use spnego = No
        encrypt passwords = Yes
        winbind use default domain = Yes
        winbind nested groups = Yes
        restrict anonymous = 2
```

---

### Post by nailbombjoe on 2006-11-09
I followed your instructions and it worked perfectly on Ubuntu Server 6.06.1.  Thanks for the awesome howto!

---

### Post by nailbombjoe on 2006-11-09
Try configuring your linux box to use the AD DNS server for domain name lookups.  I know that if you don't do that with 2000 and XP boxes that joining and logging into the domain will be super slow.  I'm not positive that it will help you but it is worth a shot.

---

### Post by nailbombjoe on 2006-11-09
Try configuring your linux box to use the AD DNS server for domain name lookups. I know that if you don't do that with 2000 and XP boxes that joining and logging into the domain will be super slow. I'm not positive that it will help you but it is worth a shot.


> **ximok said:**
> Ok, when I join a win2k machine to my Win2k AD Domain it joins within a few seconds.

My linux boxes take anywhere from 10 to 45 minutes when I do net ads join!!

As root:

kinit [email]adminuser@ABCDEF.XYZ[/email]

<type in password>
klist shows me my tickets (which look ok?)

net ads join

(wait forever)](*,) 

command completes

net ads testjoin shows that my join is complete.  It just took forever.

I can login just fine after it joins, it just takes way too long to be anything efficient during install.

Ideas?

Here are some files for you to view
krb5.conf
```
[logging]
        default = FILE:/var/log/krb5.log

[libdefaults]
        ticket_lifetime = 24000
        clock_skew = 300
        default_realm = ABCDE.XYZ
#       dns_lookup_realm = false
#       dns_lookup_kdc = true

[realms]
        COLSD.ORG = {
                kdc = kdc1.abcde.xyz
                kdc = kdc2.abcde.xyz
                admin_server = kdc1.abcde.xyz
                default_domain = ABCDE.XYZ
}

[domain_realm]
        .abcde.xyz = ABCDE.XYZ
        abcde.xyz = ABCDE.XYZ
```


smb.conf
```
[global]
        security = ads
        realm = ABCDE.XYZ
#       password server = kdc1.abcde.xyz
        workgroup = ABCDE
        winbind separator = +
        allow trusted domains = No
        idmap uid = 10000-2000000
        idmap gid = 10000-2000000
        winbind enum users = No
        winbind enum groups = No
        winbind cache time = 15
        template homedir = /home/%D/%U
        template shell = /bin/bash
# spnego disabled due to bug
        client use spnego = No
        encrypt passwords = Yes
        winbind use default domain = Yes
        winbind nested groups = Yes
        restrict anonymous = 2
```

---

### Post by ScatterBrain on 2006-12-06
> **Novack said:**
> However, running 'getent passwd' (which I found from the winbindd guide on the Samba website) does not return the logged in AD user like it should according the Samba guide.
 
Did anyone ever resolve this? I have the same problem - although I can use chmod, chown, etc to assign permissions using the Windows usernames and groups and that does work.
 
I would prefer to see the results show up in 'getent passwd' and 'getent group' though.

---

### Post by ScatterBrain on 2006-12-06
> **ScatterBrain said:**
> Did anyone ever resolve this? I have the same problem - although I can use chmod, chown, etc to assign permissions using the Windows usernames and groups and that does work.
 
I would prefer to see the results show up in 'getent passwd' and 'getent group' though.
 
 
Nevermind...I found [this post]("http://www.elwoods.org/home/2006/07/18/follow-up-thoughts-on-ubuntu-plus-active-directory/") which changed these settings in **/etc/samba/smb.conf**:
 
```
winbind enum users = yes
winbind enum groups = yes
```
 
and now both 'getent' commands work as I wanted them too.
 
Oh, and in addition - at least in my testing environment using Windows 2003 Server R2 and Ubuntu 6.06 fully updated - I had to remove these lines from **/etc/krb5.conf **before I could get a Kerberos ticket:
 
```
default_tkt_enctypes = des3-hmac-sha1 des-cbc-crc
default_tgs_enctypes = des3-hmac-sha1 des-cbc-crc
```
 
I hope this helps someone out in the future!
 
Great Howto by the way!

---

### Post by ppateel on 2006-12-09
Hi,
 I am a complete newbe. So please bear with me.

 I am trying to follow the tutorial using ubuntu 6.10 (edgy eft). I want to connect the linux box to a Windows 2003 Active Directory server. 

I had to make a small change in /etc/pam.d/common-auth as below
```
auth    required        pam_unix.so nullok_secure
``` 
because it would not let me do sudo if I used the original code
```
Original Code 
auth    required        pam_unix.so nullok_secure use_first_pass
``` 

. After I made that change when I do a kinit I get the following error message after I enter my password.
```
KDC reply did not match expectations while getting initial credentials
``` 
What am I doing wrong ? Any help or suggestion is greately appreciated.

Prahalad

---

### Post by acgiglyph on 2006-12-11
I too was struggling with this problem but was able to get it to work.  While the base article was a GREAT start it does leave some items out that I will try to spell out below.  

The /etc/pam.d/common account needed the following info
# account-required pam_unix.so
account-required pam_winbind.so

Also here are some links that really helped on my quest.

[http://www.linuxquestions.org/questions/showthread.php?t=313520](http://www.linuxquestions.org/questions/showthread.php?t=313520)
[http://www.justlinux.com/forum/showthread.php?threadid=118288](http://www.justlinux.com/forum/showthread.php?threadid=118288)
[http://developer.novell.com/wiki/index.php/HOWTO:_Configure_Ubuntu_for_Active_Directory_Authentication](http://developer.novell.com/wiki/index.php/HOWTO:_Configure_Ubuntu_for_Active_Directory_Authentication)
[http://lists.samba.org/archive/samba/2005-May/105985.html](http://lists.samba.org/archive/samba/2005-May/105985.html)
[http://www.mail-archive.com/samba@lists.samba.org/msg80201.html](http://www.mail-archive.com/samba@lists.samba.org/msg80201.html)

I know that this is frustrating for many users, but as you can see, it can be done and is VERY rewarding when completed.  Best of luck to you all.

---

### Post by numbers1thru9 on 2006-12-12
Hey all, I followed the directions and was able to setup the pc to join the domain and it worked, there was no problem. But I knew everything was going too well becasue I cant seem to login with my AD username. I set the separator to \ and it wont login. also when i login with the account that I setup when i installed the system, it will not keep the ticket and i have to issue a new kinit statement when i login. I can ssh user@DOMAIN perfectly but i want to be able to login with a AD name on the GUI. can anyone help me make this happen? also if i change pam_winbind.so to pam_krb5.so it killed the box and i had to re-image the machine becasue i would get an auth failed error with any username. I really want this to work. any help is appreciated

---

### Post by Alastairroy on 2007-01-02
> **derelict said:**
> I solved it by resetting the Administrator password :) It looks like I now have a Kerberos ticket already, I'll post back the whole result (hopefully successful!)

Thanks steve :)

Hi sorry to bother you was wondering if you can remember the cammand to reset the administrator password I am having the same problem have tried most of the other things and none have worked so far.

Thanks in advance

---

### Post by rickyjones on 2007-01-02
Hey,

Just wanted to post to say that I got this working perfectly using the directions in the first post. I have a VMWare install of Windows 2003 SP1, all default + an install of AD. Then I'm using the latest Ubuntu Server release in another VM to test the authentication. Works like a charm!

> Hi sorry to bother you was wondering if you can remember the cammand to reset the administrator password I am having the same problem have tried most of the other things and none have worked so far.

By "Reset the Administrator Password" we mean to change the main administrator password on the Windows Server machine. You can do this via Active Directory Users and Computers tool.

-Richard

---

### Post by Rever75 on 2007-01-23
HI All,
  I got this working great on my Ubuntu Edgy box. However when a users password expires it does not prompt me to change my password. Is this possible while using GDM and Ubuntu? I got this working using Novell SLED 10 (configure was done differently) so I believe it is possible. Any help would be great as I like Ubuntu over SLED and will need to install 10 new Linux Systems that will be Authenticating via M$ AD Windows Server 2003.

---

### Post by NaughtyusMaximus on 2007-02-09
I really need some help configuring this.  No matter what I change, I am unable to *properly*  join the domain.  I always end up with this error:

```
root@LS-001:/home/me# kinit me
Password for me@HATCON.LOCAL: 
root@LS-001:/home/me# klist
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: me@HATCON.LOCAL

Valid starting     Expires            Service principal
02/09/07 16:06:56  02/09/07 22:46:56  krbtgt/HATCON.LOCAL@HATCON.LOCAL


Kerberos 4 ticket cache: /tmp/tkt0
klist: You have no tickets cached
root@LS-001:/home/me# net ads join
[2007/02/09 16:07:14, 0] libads/ldap.c:ads_add_machine_acct(1414)
  ads_add_machine_acct: Host account for ls-001 already exists - modifying old account
Using short domain name -- HATCON
Joined 'LS-001' to realm 'HATCON.LOCAL'
root@LS-001:/home/me# net ads testjoin
[2007/02/09 16:07:35, 0] libads/kerberos.c:ads_kinit_password(164)
  kerberos_kinit_password HATCON@HATCON.LOCAL failed: Client not found in Kerberos database
[2007/02/09 16:07:35, 0] libads/kerberos.c:ads_kinit_password(164)
  kerberos_kinit_password HATCON@HATCON.LOCAL failed: Client not found in Kerberos database
[2007/02/09 16:07:35, 0] utils/net_ads.c:ads_startup(191)
  ads_connect: Client not found in Kerberos database
Join to domain is not valid
root@LS-001:/home/me# 

```

my krb5.conf file looks like this:

```
[logging]
 default = FILE10000:/var/log/krb5lib.log

[libdefaults]
 ticket_lifetime = 24000
 default_realm = HATCON.LOCAL
[realms]
 HATCON.LOCAL = {
  kdc = pc-001.hatcon.local
  admin_server = pc-001.hatcon.local
  default_domain = HATCON.LOCAL
}
[domain_realm]
 .hatcon.local = HATCON.LOCAL
 hatcon.local = HATCON.LOCAL

```

My AD Server running Windows 2003 Server R2 is 'PC-001.HATCON.LOCAL', and the local ubuntu machine is LS-001.  If anyone has any suggestions, please help - I'm thrown for a loop on this one.

---

### Post by NaughtyusMaximus on 2007-02-12
Any ideas?

---

### Post by NaughtyusMaximus on 2007-02-12
I managed to get it to work, after using SADMS, and then modifying the pam.d files according to the directions on the first page.  I'm still not sure where the discrepancy between this config and the one I did manually is, but I'm very happy that it works ;)

---

### Post by Hotei on 2007-02-22
First off thank you to everyone that has helped with this How-To.  It is wonderful and works right out of the box so to say.  So moving forward to transition my old samba server to this one I am having a bit of trouble and I don't know how to get it solved.  When providing a share, I need people to be able to read/write, and just read from the share.  Because it is using AD, I am unclear how to make this work.  Typcially it would go:

[share1]
        path = /home/share1
        valid users = user1, user2, user3, @somegroup, @anothergroup
        read list = user1,@anothergroup
        write list = user2,user3,@somegroup
        create mask = 0777
        directory mask = 0777

I have the permissions set like so:

drwxrwsrwx   2 user2  somegroup   4096 2007-02-22 10:39 share1

This setup doesn't work in my new AD aware Samba Server.  Help please?

---

### Post by flashingcurser on 2007-03-16
> Secondly, can anyone tell me how I can add AD users as members to local unix groups?

I have the same question. Users can log in just fine, however for them to have permissions to cdrom and audio groups, I have to add their AD users directly to the /etc/group file. 

Imagine if you will one hundred users, and you will see what a pain it is. There has to be a more eloquent way of doing this. Frankly, there is little security problem with changing permissions on sound /dev, that is pretty clunky too.

I have tried unsuccessfully to use pam_group.so, but I can't seem to get it to recognize AD users. Though that would seem to be the ideal way.

Anyone have a good way of doing this?

---

### Post by cprofitt on 2007-03-26
> **Draaku said:**
> domain admin will not change password to help me with this. doesnt want to risk it. is there no other way? I have rights to add computers and users to domain, and I just reset my password.

Good Admin...

No reason to change the AD Domain Admin password just to get a linux box on the domain!

---

### Post by mlbensi on 2007-04-20
> **Scott07 said:**
> Yes I have just got it working about 10 minutes ago, what you need to do is install kerberos manually.  This means you need to install the bits and bob's needed to compile packages from source as far as I remember these are:
make,
gcc-base
gcc

You will also need to install the cursors/ncursors libary and the C developers version (again in the package manager) and something to do YaST (there are a few tools in the package manager).  

Now go here: [http://www.mit.edu/~kerberos/dist/index.html](http://www.mit.edu/~kerberos/dist/index.html) and download the Kerberos source and extract it.  Then fire up konsole (or equlivant) in Super-User mode and cd to the src directory in the extracted kerberos folder.  Type "./configure" and let it run (it might stop with an error code because you dont have a dependancy, you should be able to find one to cover that in the package manager just have a hunt arround).  After configure has done type "make" (again you might have some dependancy problem) and once thats done type "make install".  Kerberose will now be installed and working so you can follow the steps in the first post to get it to work.  

Just a warning, I have only tried this on a windows 2000 active directory domain.

Have fun!


Quick question.

Will this manual install of Kerberos work on a Ubuntu server running 6.10 as well as it does on the 6.06 version?

Thanks in advance,

Matt

---

### Post by legolas_w on 2007-04-24
Hi
Thank you for reading my post
Does any one tried and become successfull in using Ubuntu 7.04 (feisty fawn) with windows 2003 ?

I will be very grateful if you share your step to integrate Feisty Fawn with Windows server 2003.



Thanks

---

### Post by brechtvb on 2007-04-25
Can someone explain me the difference between nsswitch and pam ?
they both use winbind but what is the connection between nsswitch.conf and pam ?

all answers appreciated

---

### Post by rickyjones on 2007-04-25
> **legolas_w said:**
> Hi
Thank you for reading my post
Does any one tried and become successfull in using Ubuntu 7.04 (feisty fawn) with windows 2003 ?

I will be very grateful if you share your step to integrate Feisty Fawn with Windows server 2003.



Thanks

I don't know if anyone has tried this yet but if I find the time later this week I'll probably try it just to see.

-Richard

---

### Post by legolas_w on 2007-04-25
Hi
It is very nice of you.

I am looking forward to see the result of your try 

Thank you very much.

---

### Post by rickyjones on 2007-04-27
I just tried to quickly do it tonight but it failed... not sure exactly why, still need to look into it a little more. When we got to the point of joining the computer to the domain it would come back with an error (didn't write it down) and the computer account would be disabled in Active Directory. I will try this again tomorrow most likely.

-Richard

---

### Post by legolas_w on 2007-04-28
thank you very much, looking forward to read your steps.

thanks

---

### Post by rickyjones on 2007-04-28
I have confirmed that Ubuntu Server 7.04 will indeed connect to an Active Directory domain. I followed all the steps from the first post and confirmed that it works. Following is the description of my environment.

**Environment**
Our environment consists of a Windows 2003 Standard Server configured as a domain controller, DNS server, and file server. It has the latest service pack, SP2, installed. It is configured using the following information:
* Domain: contoso.com
* Netbios Domain: CONTOSO
* Hostname: server01
* FQDN: server01.contoso.com
* IP: 192.168.1.253

There have been small changes to group policy settings (roaming profiles, redirected My Documents, etc…) If the experiment continues to fail I will reinstall and leave all settings as default.

The Ubuntu Server is version 7.04 with all available updates installed in the beginning. I will configure the hostname and domain configuration files, along with pointing the server to the Windows server for its DNS.
* Domain: contoso.com
* Hostname: server02
* FQDN: server02.contoso.com
* IP: 192.168.1.252

**Configuration on Ubuntu Server 7.04**
During the installation I assigned the hostname of “server02” and had the installer use the entire disk for the partitioning scheme. For the main user I used my name, richard, as the username. I used my normal password. Please note that I am creating a different username than that of which exists on my Active Directory domain. I did not install the DNS server or LAMP stack. Once the system was installed I made a backup of /etc/apt/sources.list and edited the original so that it did not use the install CD. That is the only change that I made. I then performed an update and then upgrade for the packages. I then installed the SSH server via sudo apt-get install openssh-server. All the other commands will be done via Putty. The next thing that I did was edit the network interfaces file for a static IP address. All the commands are typed into a root bash shell (sudo bash). I edited hosts to include server02.contoso.com and I also edited hostname to show server02.contoso.com. Next I edited the resolv.conf file to point to my domain controller. I have verified that DNS works – I can ping the FQDN for server01. Now I’m going to reboot the Ubuntu server to make sure that the new hostname is correctly configured. Now I’ll follow the directions from the beginning of this thread. Following all the steps exactly allowed me to join the domain. On reboot I tried to SSH in using [email]domain_user@DOMAIN.LOCA[/email]L and it did not work. Will reboot and try it again using just the username, not the full username. That worked!

Hope that helps everyone!

-Richard

---

### Post by rickyjones on 2007-04-28
Alright, now that I have this working I'm wondering if someone will be able to assist me to push this project a little further.

Here is the scenario: A small company has approximately 10 client workstations, all Windows XP Professional. In order to streamline administration and to centralize a lot of the information the management (including IT) have decided to implement a Windows 2003 Standard Server. This server will be responsible for Active Directory, DNS, and printing. Because it is not best practice to use the domain controller as a network file server, IT has recommended installing an Ubuntu 7.04 file server for the network. IT has determined that it is feasible to join this computer to the domain, therefore allowing network users to log into this machine. However, management has declared that shared folders on this file server must be locked down. User home directories must be accessed only by those users and the associated managers. The logical way to do this is to assign security rights using Windows ACLs.

How do we do ACL support using Samba? I'm completely stuck on this point. My smb.conf file contains the following (for the share only):

```

[data]
comment = Data
path = /data
use nt acls = yes

```

From the domain controller I can access the folder but cannot create new folders or files in it. I am unable to edit the security permissions. On Ubuntu I chmodded the /data folder as 777 for testing. This had no effect.

Any ideas guys?

Thanks,

-Richard

---

### Post by legolas_w on 2007-04-28
Hi Richard.
Thank you for your steps.
Will it work with ubuntu desktop edition?
I do not have server edition and i just need to login into domain using my domain username/password and also i need to have a shared folder and access to other colleague shared folders.

I have ubuntu Desktop edition DVD and i will install all of its packages next day, Thank you very much for your steps, i will share the result.


Thanks

---

### Post by rickyjones on 2007-04-28
I don't see why it wouldn't work with Ubuntu Desktop... I will try to test that later on tonight.

-Richard

---

### Post by Simon2468 on 2007-05-02
I built a laptop with Ubuntu v7.04 and started to follow these instructions to get it to join my 2003 domain.  Like someone earlier, I got this error: "KDC reply did not match expectations while getting initial credentials".  

Before resolving it, I closed the lid on my laptop and after reopening it, it seemed to have crashed.  The screen was black, with only the mouse pointer visible.  It responded to the mouse but no amount of key-pressing and button-clicking could coax it to wake.  (Previously, closing the lid and re-opening had just required me to re-enter my ubuntu creds.  So, I powered off and on and it came up to the login screen.  And there was my problem.

It would no longer allow me to login.  Entering the same userid and hitting enter or tab resulted in a denial of access without an attempt to enter my password - I'm guessing it was trying to do an AD lookup first.

Anyway, the short version is: can you do a "local login" to an ubuntu box - whatever is the equiv of using the local SAM database on Windows.  In Windows, it would be COMPUTER\User instead of DOMAIN\User.  Is there an ubuntu equivalent?

Otherwise, I'll have to rebuild it!

---

### Post by rickyjones on 2007-05-02
> **Simon2468 said:**
> I built a laptop with Ubuntu v7.04 and started to follow these instructions to get it to join my 2003 domain.  Like someone earlier, I got this error: "KDC reply did not match expectations while getting initial credentials".  

Before resolving it, I closed the lid on my laptop and after reopening it, it seemed to have crashed.  The screen was black, with only the mouse pointer visible.  It responded to the mouse but no amount of key-pressing and button-clicking could coax it to wake.  (Previously, closing the lid and re-opening had just required me to re-enter my ubuntu creds.  So, I powered off and on and it came up to the login screen.  And there was my problem.

It would no longer allow me to login.  Entering the same userid and hitting enter or tab resulted in a denial of access without an attempt to enter my password - I'm guessing it was trying to do an AD lookup first.

Anyway, the short version is: can you do a "local login" to an ubuntu box - whatever is the equiv of using the local SAM database on Windows.  In Windows, it would be COMPUTER\User instead of DOMAIN\User.  Is there an ubuntu equivalent?

Otherwise, I'll have to rebuild it!
After joining it to the domain you should still be able to use local logins unless there is an issue with your configuration. I can login to my domain-joined Ubuntu servers with my original login without issue. 

-Richard

---

### Post by Gizmo_RA2 on 2007-05-02
ok here goes,

I have got 200+ computers on a network, and they are running win2k and winxp.
This is a school environment.
We are trying to create a test machine to test if ubuntu will work on the current win2k domain controllers.

I have followed the instructions, and got it on the domain, and it can tell me if there is an error in the password or not. and it attempts to login,
it brings up the ubuntu login banner telling you you've logged in, and then it takes me back to the login screen.

I then installed gnome, and it tells me the account has been disabled, also I can't see the contents of that home directory to tell if it has copied the profile correctly, either that or the directory is empty.

I can log into that account on the windows machines fine, and the Active Directory tells me the account is not disabled, any ideas?

---

### Post by Simon2468 on 2007-05-03
> **rickyjones said:**
> After joining it to the domain you should still be able to use local logins unless there is an issue with your configuration. I can login to my domain-joined Ubuntu servers with my original login without issue. 

-Richard


Great.  So, how do you distinguish between doing a local login and doing a network login?  How does ubuntu know which to do?

---

### Post by Gizmo_RA2 on 2007-05-03
> **Simon2468 said:**
> Great.  So, how do you distinguish between doing a local login and doing a network login?  How does ubuntu know which to do?

Correct me if i'm wrong, but I believe it is to do with the list of where to check and what order they are in.
When you set it up as far as I am aware you tell it which order of authentication methods to check sort of like the dns order where it checks the host file, then the dns servers and stuff.

I believe if you have set your ubuntu machine up as documented here, it should check the local machine first then check against your Active Directory afterwards.

---

### Post by Simon2468 on 2007-05-04
So you just type in the ID the same way?  I take it that means if you've been foolish enough to build your ubuntu machine with the same ID that you use to log into AD that it won't be able to tell the difference?

I used my network ID as my login name when I created the first set of creds during the build - figured it might save time later.

---

### Post by tgilbert328 on 2007-05-09
Speaking of foolish...

I followed the directions right up to step 10.  At Step 11, I type sudo nano /etc/sudoers to add my newly created AD group to the list. PRB.  It asks me for my root password, which I enter.  Doesn't work.

I am a wee bit concerned and I think it is looking for network authentication of root rather than local.  Did I do something wrong in the config?  How can I recover the password?  Ideas?

Without root, I obviously can't do much.  I made backups of all of the conf files I touched, but since I don't have su, I can't restore them.  I am wondering if I have to boot from live cd, mount the hard drive and manually restore...

ideas?  

Finally, I wonder if the documentation should be modified to move step 11 up in the list prior to the samba/winbind  restart...

Tim

---

### Post by rickyjones on 2007-05-09
> **tgilbert328 said:**
> Speaking of foolish...

I followed the directions right up to step 10.  At Step 11, I type sudo nano /etc/sudoers to add my newly created AD group to the list. PRB.  It asks me for my root password, which I enter.  Doesn't work.

I am a wee bit concerned and I think it is looking for network authentication of root rather than local.  Did I do something wrong in the config?  How can I recover the password?  Ideas?

Without root, I obviously can't do much.  I made backups of all of the conf files I touched, but since I don't have su, I can't restore them.  I am wondering if I have to boot from live cd, mount the hard drive and manually restore...

ideas?  

Finally, I wonder if the documentation should be modified to move step 11 up in the list prior to the samba/winbind  restart...

Tim

Try running "visudo" as root - this launches a specific instance of nano to edit the sudoers file. 

-Richard

---

### Post by tgilbert328 on 2007-05-09
Thanks Richard, I will give it a try.  Its not looking good for me though.  I had made backups of all of the files which were modified.  I attempted to restore those files by mounting it from Ubuntu LiveCD and using its root to make the changes.

After regressing, its worse.  Now I can't login at all from local or network accounts.  Its strange, it prompts for a password twice...

Tim

---

### Post by ziggie216 on 2007-05-14
Does anyone know what kind of permission I would need? Domain Admin?

$ sudo net ads join -U [email]username@DOMAIN.COM[/email]
[email]username@DOMAIN.COM[/email]'s password:
[2007/05/14 16:37:50, 0] libads/ldap.c:ads_add_machine_acct(1414)
  ads_add_machine_acct: Host account for computername already exists - modifying old account
[2007/05/14 16:37:50, 0] libads/ldap.c:ads_join_realm(1772)
  ads_join_realm: ads_add_machine_acct failed (dlee3): Insufficient access
ads_join_realm: Insufficient access

---

### Post by rickyjones on 2007-05-14
> **ziggie216 said:**
> Does anyone know what kind of permission I would need? Domain Admin?

$ sudo net ads join -U [email]username@DOMAIN.COM[/email]
[email]username@DOMAIN.COM[/email]'s password:
[2007/05/14 16:37:50, 0] libads/ldap.c:ads_add_machine_acct(1414)
  ads_add_machine_acct: Host account for computername already exists - modifying old account
[2007/05/14 16:37:50, 0] libads/ldap.c:ads_join_realm(1772)
  ads_join_realm: ads_add_machine_acct failed (dlee3): Insufficient access
ads_join_realm: Insufficient access

You will need domain admin status to modify an existing computer account. A regular user can join a computer to the network but cannot modify the computer account.

-Richard

---

### Post by warlockvix on 2007-05-15
Great guide! I just have one problem and I'm not sure how to fix it. I have set up my Ubuntu box just like the guide and I can sign onto it locally and with AD accounts. When I setup AD users with their home folders (via ssh user@ubuntupc) the home drives are created.

My problem is that users can map to their Ubuntu-based home folders as a network drive from a Windows XP machine but they can not add files or edit any existing files. When users try, they get a Windows pop stating Access Denied. But if they sign on locally to the Ubuntu box, they can add files and edit existing ones in their home folder.  My goal is to redirect my users "My Documents" to this Ubuntu box and eliminate the Windows 2K server that currently fulfills this role. To do this, they need to be able to write to the folde. So did I miss a step? Is what I want to do possible? Any ideas?

The home folders all reside in /home/DOMAIN/ which is listed in the smb.conf below 


SMB.CONF

[global]
        security = ads
        netbios name = UBU
        realm = DOMAIN.COM
        password server = SERVER.DOMAIN.com
        workgroup = DOMAIN
        idmap uid = 500-10000000
        idmap gid = 500-10000000
        winbind separator = +
        winbind enum users = yes
        winbind enum groups = yes
        winbind use default domain = yes
        template homedir = /home/%D/%U
        template shell = /bin/bash
        client use spnego = yes
        domain master = no
        preferred master = no
        local master = no
        nt acl support = yes
[SHARE]
        path = /home/DOMAIN/
        read only = Yes
        browseable = No


EDIT - NVM. I fixed it. I freed up my [SHARE] so it's not read only and locked down the home dirs. It worky now.

---

### Post by ziggie216 on 2007-05-17
Is there a way to login via gnome using AD account? as for right now I have everythign setup but only to be able to login in via ssh

---

### Post by warlockvix on 2007-05-17
Following the guide should allow you to sign on via gnome with AD accounts or local accounts. Any errors?
Can you post your smb.conf file and krb5.conf file?

---

### Post by ziggie216 on 2007-05-17
all the DOMAIN and domain were replaced with the actual name.

krb5.conf
```
[logging]
    default = FILE10000:/var/log/krb5lib.log

[libdefaults]
        default_realm = DOMAIN.COM
        ticket_lifetime = 24000
        default_tkt_enctypes = des3-hmac-sha1 des-cbc-crc
        default_tgs_enctypes = des3-hmac-sha1 des-cbc-crc

# The following krb5.conf variables are only for MIT Kerberos.
        krb4_config = /etc/krb.conf
        krb4_realms = /etc/krb.realms
        kdc_timesync = 1
        ccache_type = 4
        forwardable = true
        proxiable = true

# The following libdefaults parameters are only for Heimdal Kerberos.
        v4_instance_resolve = false
        v4_name_convert = {
                host = {
                        rcmd = host
                        ftp = ftp
                }
                plain = {
                        something = something-else
                }
        }
        fcc-mit-ticketflags = true

[realms]
        DOMAIN.COM = {
                kdc = nascdca01.domain.com
                admin_server = nascdca01.domain.com
                default_domain = DOMAIN.COM
        }

[domain_realm]
        domain.com = DOMAIN.COM
        .domain.com = DOMAIN.COM

[login]
        krb4_convert = true
        krb4_get_tickets = false
```


smb.conf
```
[global]
        security = ads
        netbios name = computer_name
        realm = DOMAIN.COM
        password server = nascdca01.domain.com
        workgroup = DOMAINAD
        idmap uid = 500-10000000
        idmap gid = 500-10000000
        #winbind separator = +
        winbind enum users = yes
        winbind enum groups = yes
        winbind use default domain = yes
        encrypt passwords = yes
        template homedir = /home/%D/%U
        template shell = /bin/bash
        client use spnego = yes
        domain master = no
        log file = /var/log/samba/log.%m
        max log size = 1000
        syslog = 0
```


I just checked the auth.log and notice this
```
May 16 08:01:02 COMPUTER_NAME pam_winbind[20446]: user 'USERNAME' granted access
May 16 08:01:02 COMPUTER_NAME gdm[20446]: (pam_unix) could not identify user (from getpwnam(USERNAME))
May 16 08:01:02 COMPUTER_NAME gdm[20446]: Couldn't set acct. mgmt for USERNAME
```

---

### Post by warlockvix on 2007-05-17
I haven't played too much with the winbind seperator but I would allow it to be read, so I would remove the # in front of it. What happens when you type in **kinit ****user@DOMAIN.COM**? Does it some back with a response? What about **wbinfo -g** and **wbinfo -u**?Also, your nsswitch.conf and all your pam.d/common-* are similiar to the guide, correct?

---

### Post by ziggie216 on 2007-05-17
> **warlockvix said:**
> I haven't played too much with the winbind seperator but I would allow it to be read, so I would remove the # in front of it. What happens when you type in **kinit ****user@DOMAIN.COM**? Does it some back with a response? What about **wbinfo -g** and **wbinfo -u**?Also, your nsswitch.conf and all your pam.d/common-* are similiar to the guide, correct?

kinit works fine, I was about to use klist as well
wbinfo -g and -u works fine

I had everything configured as it said in the guide, even tried to use 
winbind separator = \
winbind separator = +

---

### Post by MockY on 2007-05-17
I have tried to make this work for soon a year and I finally gave up. I installed 2XApplicationServer instead and I am once again happy with Ubuntu in a business environment.

---

### Post by warlockvix on 2007-05-18
As much as I hate to do this, I'm going to post a link to another guide. [[COLOR="Blue"]Linky[/COLOR]]("http://www.infosecwriters.com/text_resources/pdf/  AD_and_Linux_TMunn.pdf").
I used this guide to further my configuration on my Ubuntu server. It might be useful. 

I was able to come up with a similiar error in my auth.log as yours by messing with my /etc/pam.d/gdm file. I altered the path of the *.so files and it was not happy. In all my /etc/pam.d/common-* files and now in my gdm file, I have /lib/security/ in front of the *.so files. Like this -

common-auth -

auth    required        /lib/security/pam_env.so
auth    sufficient      /lib/security/pam_unix.so likeauth nullok
auth    sufficient      /lib/security/pam_krb5.so use_first_pass
auth    sufficient      /lib/security/pam_winbind.so use_first_pass
auth    required        /lib/security/pam_deny.so
account required        /lib/security/pam_unix.so broken_shadow
account sufficient      /lib/security/pam_succeed_if.so uid < 100 quiet
account [default=bad success=ok user_unknown=ignore] /lib/security/pam_krb5.so
account [default=bad success=ok user_unknown=ignore] /lib/security/pam_winbind.$
account required        /lib/security/pam_permit.so
#account        requisite       /lib/security/pam_succeed_if.so user ingroup un$
password        requisite       /lib/security/pam_cracklib.so retry=3
password        sufficient      /lib/security/pam_unix.so nullok use_authtok md$
password        sufficient      /lib/security/pam_krb5.so use_authtok
password        sufficient      /lib/security/pam_winbind.so use_authtok
password        required        /lib/security/pam_deny.so
session required        /lib/security/pam_limits.so
session required        /lib/security/pam_unix.so
session optional        /lib/security/pam_mkhomedir.so skel=etc/skel/ umask=0007
session optional        /lib/security/pam_krb5.so

It might be worth a try to add the full path, at least with the gdm file. 

Also, my krb5.conf looks like this -

krb5.conf -


[logging]
        default = FILE10000:/var/log/kr5lib.log
[libdefaults]
        default_realm = DOMAIN.COM
        ticket_lifetime = 24000
        default_tkt_enctypes = des3-hmac-shal des-cbc-crc
        default_tgs_enctypes = des3-hmac-shal des-cbc-crc

[realms]
DOMAIN.COM = {
                kdc = myserver.domain.com
                admin_server = myserver.domain.com
                default_domain = DOMAIN.COM
        }
[domain_realm]
        .domain.com = DOMAIN.COM
        domain.com = DOMAIN.COM


Of course, DOMAIN replaces what is actually there and I removed a few things from the file that I wouldn't be needing.

---

### Post by ziggie216 on 2007-05-22
I'm locked out from my system after a restart. Tried both the local and the domain name and it doenst accept it. Any idea what happend?

---

### Post by warlockvix on 2007-05-22
depends on what you changed. But this happened to me and PAM was locking me out. Bootup with a system rescue CD [[COLOR="RoyalBlue"]Linky[/COLOR]]("http://www.sysresccd.org/Screenshots") and mount your partition. Change the common-* files back and you'll be able to sign back on, as long as it's PAM locking you out.

---

### Post by ziggie216 on 2007-05-22
were you able to resolve the problem and not get lock out again?

---

### Post by NaughtyusMaximus on 2007-05-22
Thanks to everyone who has contributed to this thread.  I've followed the instructions and have managed to set up a (mostly) working samba file share using my Windows 2003 Active Directory to authenticate users.


The only problem I still have is that when users create files on the share, the username that they are created under is always listed as 'root', instead of their actual username.  This seems to be resulting in some files being not writable by the same user that created them.

All of the users who have access to the smb share are members of the same AD Group 'HCLOffice', and any file created by a member of that group should be readable and writable by other members of the group.

The relevant section of my smb.conf file is as follows:


```
[GIS]
        path = /shared/GIS
        comment = GIS Data
        browseable = yes
        writable = yes
;        public = yes
       valid users = @"HATCON/Domain Users"
       admin users = @"HATCON/HCLOffice"
       read list @"HATCON/Domain Users"
       write list = @"HATCON/Domain Users"
```


If anyone has any suggestions about how I should change this section, I would be eternally grateful!

---

### Post by warlockvix on 2007-05-23
Yes. I was playing with the common-auth (commenting things out do to issues I thought were related to PAM) and suddenly after a reboot, I couldn't sign on. So I booted up with the system rescue cd and changed everything back. Voila! I was able to sign back on.

---

### Post by ziggie216 on 2007-05-23
> **warlockvix said:**
> Yes. I was playing with the common-auth (commenting things out do to issues I thought were related to PAM) and suddenly after a reboot, I couldn't sign on. So I booted up with the system rescue cd and changed everything back. Voila! I was able to sign back on.

but where u able to log in using an AD account still though?

---

### Post by ziggie216 on 2007-05-24
got it fixed... does the order of lines make a differnece?

---

### Post by eveljkov on 2007-06-13
whew....I started as a total linux/ubuntu noob to connecting to AD :)

Everything went fine.

I can see my server in Network Places except I have domain and domain.org listed where domain contains all my Windows machines and domain.org which contains samba.  It prompts for a login but nothing works

I've tried:

user
domain\user
host\user
[email]user@domain.org[/email]
local\root
local\localuser

I changed the winbind from + to \ and tried all the above

can't get'er logged in

I can see my server in ADUC.

btw.....SBS2003 as my PDC

trying to connect Fiesty on an ooooold compaq proliant so no gnome gui

do I even need to connect samba to AD in order to use this as a simple print server?  I already have CUPS configured.  I just want to be able to use hte printer directory in XP to pick a printer.

---

### Post by trekuhl on 2007-06-19
does anyone know if the domain functional level in 2003 server has to be left at default "2000 mixed" mode? i am running "2003 mode" as all my servers are 2003. anyone that has successfully joined their ubu svr can you check your level in 2k3 server? (goto admin tools --> active directory domains and trusts --> right click domain name and click on "raise functional level and it tell you current mode and give upgrade options)

i am getting an error when i try to add the ubu server in step 8 "Join the system to the; net ads join -U [email]domainadminuser@DOMAIN.INTE[/email]RNAL"

i get error:
" sudo net ads join -U [email]admin@DOMAIN.INTE[/email]RN
Password:
[email]admin@IDOMAIN.INTE[/email]RN's password: 
Using short domain name -- DOMAIN
Failed to set servicePrincipalNames. Please ensure that
the DNS domain of this server matches the AD domain,
Or rejoin with using Domain Admin credentials.
Disabled account for 'UBUSVR1' in realm 'DOMAIN.INTERN'

i look on the AD server and find the computer name for the ubu server and it is indeed DISABLED. i enable, and then run the command again from ubu svr to add and AD disabled again.

obviously its something on the micro$haft side in AD disabling the account. off the top of my head i would think it is perhaps because i am running in 2003 mode instead of mixed mode for compatibility with 2k and NT servers...

any thoughts?

thanks!

---

### Post by trekuhl on 2007-06-20
ok figure out my problem. 

DNS on the w2k3 machines didnt have any A or PTR for the ubu machine, even though DHCP on a w2k3 machine handed it out (and we have DNS set to update both secure and nonsecure, woudl figure it would have entered it in when DHCP gave out the address)

---

### Post by bensode on 2007-06-25
EDIT: Didn't enable the correct repository.  Disregard my post below ...

Hey this is going to sound goofy but I followed the guide for installing the Kerberos portion last week on a test box and now repeating the same process today to move into production, I'm not able to get the krb5-user package installed.

I have allowed the universe and multiverse in /etc/apt/sources.list but when I attempt the install with sudo apt-get install krb5-user I get this :

bensode@samba1:~$ sudo apt-get install krb5-user

Reading package lists... Done

Building dependency tree... Done

Some packages could not be installed. This may mean that you have

requested an impossible situation or if you are using the unstable

distribution that some required packages have not yet been created

or been moved out of Incoming.



Since you only requested a single operation it is extremely likely thatEDIT: Didn't enable the correct repository.  Disregard my post below ...

the package is simply not installable and a bug report against

that package should be filed.

The following information may help to resolve the situation:



The following packages have unmet dependencies:

  krb5-user: Depends: libkrb53 (= 1.4.3-5) but 1.4.3-5ubuntu0.3 is to be installed

             Depends: libkadm55 (= 1.4.3-5) but 1.4.3-5ubuntu0.3 is to be installed

E: Broken packages

EDIT: Didn't enable the correct repository.  Disregard my post aboce ...

---

### Post by rickyjones on 2007-06-28
I just wanted to post to let everyone know that I just finished a VMWare test of the AD/Ubuntu integration. I created a Windows 2003 Enterprise server install and updated it to Service Pack 2. I installed Active Directory and left it as-is. I then installed Ubuntu 7.04 Desktop (latest downloaded ISO) in another VMWare disk. Using the directions from page 1 I have this server authenticating perfectly against the active directory. I can log in at the GDM just fine.

Thanks,

-Richard

---

### Post by toobuntu on 2007-07-02
check out [http://sadms.sourceforge.net/]("http://sadms.sourceforge.net/")

It automates the process of configuring samba and PAM/kerberos with a GUI and works great!

SADMS = Samba as Active Directory Member Server

---

### Post by rickyjones on 2007-07-03
> **toobuntu said:**
> check out [http://sadms.sourceforge.net/]("http://sadms.sourceforge.net/")

It automates the process of configuring samba and PAM/kerberos with a GUI and works great!

SADMS = Samba as Active Directory Member Server

Have you had a chance to use this? I'd be interested in hearing some first hand experience - It'd save me the trouble of having to write my own script to do it. :).

---

### Post by toobuntu on 2007-07-06
I have used sadms successfully on 2 ubuntu workstations and 1 server on which I put a GUI (Xorg).  Let me know if you have any questions, and I'll try to be as helpful as I can.

---

### Post by rickyjones on 2007-07-06
When I have the time I'll try to look at it as well :). Might just be a ton easier than writing scripts to do it...

Thanks for the heads up!

-Richard

---

### Post by sillyVM on 2007-07-12
Tested working on ubuntu server 7.04 with acticve directory on win2000

except need to change /etc/hosts

IP_ADDRESS server_name.domain.internal domain
#example 192.168.1.1 dns.domain.com domain.com

---

### Post by Sergnsk on 2007-07-17
have a problem same as some had before

Using short domain name -- QQQ
**Failed to set servicePrincipalNames**. Please ensure that
the DNS domain of this server matches the AD domain,
Or rejoin with using Domain Admin credentials.
Disabled account for 'SSS-DESKTOP' in realm 'QQQ.XX'

Any solutions? 

Try use sadms - same problem

---

### Post by toobuntu on 2007-07-17
In sadms, stage 1 is to install SADMS itself (Samba server) and stage 2 is to install the PAM modules (for authentication to Active Directory).

1. Sadms must be run as root (i.e. invoke with sudo).

2. For kerberos authentication to work, you will probably need to reset the password of the 'Domain Admin' account in 'Active Directory Users and Computers' (not to worry, because you can set it back again right away even before running Sadms).  Do this for the Domain Admin account being used to add the Ubuntu machine to the Window$ domain.

3. See attached png of my working sadms configuration.

Hope this helps.

---

### Post by micro420 on 2007-07-17
### just ignore my entire post unless you're bored.  I solved my own problems and am leaving it here in hopes it will help others.

#### edit: regarding 1) below, as with SAMBA in LInux, you specific user lists with @ in the smb.conf. For example, valid users = @users.  However, to create ACL's from the Windows Server AD, you have to specific the domain name (workgroup or netbios??) and the group.  For example, valid users = @"domainname\users". That seems to do the trick after using SADMS to join my samba server to the AD.    

1) if I do everything manually by hand on the first page of this tutorial, I get it working fine.  However, since I grab a kerberos ticket as an administrator, all my users are able to map any of the samba shares, regardless of permission on the LInux box.  I believe this is because it is passing my administrator kerberos ticket.  If I destroy the administrator kerberos ticket (kdestroy), then I am unable to access any shares from the Windows machine to the samba server unless I create another kerberos ticket as administrator (kinit [email]administrator@DOMAIN.NAME[/email])


### Edit: Regarding 2) below, it turns out that the information SADMS is asking for is the samba server, NOT the Windows Server AD.  Once i set that up correctly, the Winbind service started up correctly.

2) if I use SADMS, I cannot get the winbind service to start.  It always shows up red colored, even if I try to start it manually with /etc/init.d/winbind start.  It starts for a second, and then just shuts itself down.  I have tried rebooting but winbind still does not run.  I think initially when I installed SADMS I had it going, but I accidentally clicked the STOP button on the Winbind and now I cannot get it restarted for whatever reason.  I also get this error, which I believe is related to winbind not being able to start, saying that I need to reset my administrative password on the windows server for some kind of encryption.  However, no matter how many times I have reset it, the same error keeps popping up.  Again, I believe it is because Winbind is not running.

---

### Post by Sergnsk on 2007-07-17
The problem with Failed to set servicePrincipalNames solved.

Just add a string to /etc/hosts

192.168.111.111 myhost.my.ru myhost

---

### Post by fxtq on 2007-08-09
> **flashingcurser said:**
> I have the same question. Users can log in just fine, however for them to have permissions to cdrom and audio groups, I have to add their AD users directly to the /etc/group file. 

Imagine if you will one hundred users, and you will see what a pain it is. There has to be a more eloquent way of doing this. Frankly, there is little security problem with changing permissions on sound /dev, that is pretty clunky too.

I have tried unsuccessfully to use pam_group.so, but I can't seem to get it to recognize AD users. Though that would seem to be the ideal way.

Anyone have a good way of doing this?

Hi, I'm using ubuntu 7.04 feisty on a Windows 2003 Server Domain. I added a linux-devices group to the AD. This group is always mapped to the same gid on linux. So I added a group linux-devices with the groupadd command to the linux-machine. I used the same gid samba uses when it maps linux-devices group from the AD at login. groupadd complained about a duplicate group entry, so I forced groupadd with -f to ignore it. Afterwards I set the linux-devices group as ownergroup of the desired devices in udev. I think /etc/udev/rules.d/40-permissions and restarted udev. Now every Domain-user in the linux-devices group could access /dev/dsp,/dev/floppy ... 
Afterwards I added the AD-admin users directly to the admin group in /etc/group. They now could do administrative tasks like sudo ...:guitar:

Greetings

---

### Post by ChrisWDP on 2007-08-20
I've been trying to get this running, but I still cannot log on with an Active Directory Domain account.

By following the directions from this topic, plus other postings, I've been able to accomplish the following:

kinit user account:  I'm able to get ticket from the Domain Controller
klist: I can view the ticket
net time set: Sync the time up with the network 
net ads join -U Administrator: Join the AD Domain

The following commands work as well
getent passwd
wbinfo -u
wbinfo -g
testparm

However when I try the following, the give me the following errors:
SSH user@domain
Permission Denied

SSH user@Server IP Address
Connection Refused

When I try to log on with a domain account, I get bad user name or password and/or Authentication failed.

Can anyone help point me in the right direction of possible sources of the problem?

Thanks in advance.

---

### Post by rickyjones on 2007-08-20
Try logging in as just the user. Example: instead of USER@DOMAIN try just USER. It should log you in. That is how mine works at least.

-Richard

---

### Post by ChrisWDP on 2007-08-20
Thanks for the quick response. Unfortunately, I tried just the User name, in both capital letters and lower case, without any reference to the Domain and I received 'Authentication Failed'.

I ran klist to make sure the ticket was still there and it is.

---

### Post by rickyjones on 2007-08-20
> **ChrisWDP said:**
> Thanks for the quick response. Unfortunately, I tried just the User name, in both capital letters and lower case, without any reference to the Domain and I received 'Authentication Failed'.

I ran klist to make sure the ticket was still there and it is.

With Windows it should be case in-sensitive.

Have you tried logging onto a Windows client with the same un/pw? If it works then try resetting the password on the domain and trying again.

-Richard

---

### Post by ChrisWDP on 2007-08-20
It does work on a windows client no problem.

Just to be clear, when you say try 'resetting the password on the domain', are you referring to the specific account I am trying?

For reference, a year ago I was able to get this to work, but that box got messed up and I've started again. Plus I lost my notes I had. At that time to get it to work I did reset the Administrator password in order to get a Kerbos ticket.

This time around I'm trying it on Fiesty Fawn.

---

### Post by rickyjones on 2007-08-20
> **ChrisWDP said:**
> 
Just to be clear, when you say try 'resetting the password on the domain', are you referring to the specific account I am trying?


Yes, reset the password for the account that you are trying. Also, check your domain controller's event logs, specifically the security log, for any events that might give us a clue to help solve this problem. :)

Thanks,

-Richard

---

### Post by ChrisWDP on 2007-08-20
I reset the password and still received the 'Authentication Failed' message.

In reviewing the Domain Controller's event logs, the following was recorded:

Pre-authentication failed:
Event ID: 675
User Name: Administrator
User ID: DOMAIN\administrator
Service Name: krbtgt/domain

This was followed by the following:
Logon Failure
Event ID: 529
Reason: Unknown user name or bad password
User Name: administrator
Domain: domain
Logon Type: 10
Logon Process: User32
Authentication Package: Negotiate

---

### Post by rickyjones on 2007-08-20
> **ChrisWDP said:**
> I reset the password and still received the 'Authentication Failed' message.

In reviewing the Domain Controller's event logs, the following was recorded:

Pre-authentication failed:
Event ID: 675
User Name: Administrator
User ID: DOMAIN\administrator
Service Name: krbtgt/domain

This was followed by the following:
Logon Failure
Event ID: 529
Reason: Unknown user name or bad password
User Name: administrator
Domain: domain
Logon Type: 10
Logon Process: User32
Authentication Package: Negotiate

I'm not positive on what the problem is at this point. Have you tried to rejoin the computer to the domain after deleting it's computer object from AD? I'd have to look at my setup at home to see what you should normally see in the event logs.

Sorry, I wish I could be more help right now!

-Richard

---

### Post by ChrisWDP on 2007-08-20
I've removed the computer from the AD domain and then rejoined the domain after rebooting Ubuntu, and still no luck.

One other thing I saw another post is: "the user from AD have to exist in /etc/passwd on the ubuntu workstation'.

Is this true? If so I don't see the User ID for AD in that file. How do add that User ID to that file?

Thanks for help.

~Christian

---

### Post by rickyjones on 2007-08-20
> **ChrisWDP said:**
> I've removed the computer from the AD domain and then rejoined the domain after rebooting Ubuntu, and still no luck.

One other thing I saw another post is: "the user from AD have to exist in /etc/passwd on the ubuntu workstation'.

Is this true? If so I don't see the User ID for AD in that file. How do add that User ID to that file?

Thanks for help.

~Christian

Having the ID in /etc/passwd would bypass the whole point of authenticating to AD.

Something else is wrong I think...

-Richard

---

### Post by ChrisWDP on 2007-08-21
This morning, I made one change, and now with klist I'm receiving and error: No credentials found (ticket cache FILE: /tmp/krb5cc_1000). I corrected the change to match what I had before, but I'm still receive the error.

To try and find the problem here are my krb5.conf and smb.conf files.

**_krb5.conf_**
[logging]
	default = FILE:/var/log/krb5.log
        *(I had changed this line this morning  to *default = FILE1000:/var/log/krb5lib.log. *After I got the error I changed it back to how you see it above.)* 
[libdefaults]
	ticket_lifetime = 24000
	default_realm = DOMAIN.INT
#	default_tkt_enctypes = des3-hmac-shal des-cbc-crc
#	default_tgs_enctypes = des3-hmac-shal des-cbc-crc
#	default_tgs_enctypes = aes256-cts arcfour-hmac-md5 des3-hmac-sha1 des-cbc-crc des-cbc-md5
#	default_tkt_enctypes = aes256-cts arcfour-hmac-md5 des3-hmac-sha1 des-cbc-crc des-cbc-md5
#	permitted_enctypes = aes256-cts arcfour-hmac-md5 des3-hmac-sha1 des-cbc-crc des-cbc-md5

[realms]
	DOMAIN.INT = {
		kdc = 172.16.100.3
#		admin_server = 172.16.100.3
#		default_domain = DOMAIN.INT
	}

[domain_realm]
	.domain.int = DOMAIN.INT
	domain.int = DOMAIN.INT

[appdefaults]
	pam = {
	debug = false
	ticket_lifetime = 36000
	renew_lifetime = 36000
	forwardable = true
	krb4_convert = false
}

**_smb.conf_**
[global]
        security = ads
        netbios name = battlestar
        realm = DOMAIN.INT
        password server = 172.16.100.3
        workgroup = DOMAIN
#	winbind separator = +
        idmap uid = 500-10000000
        idmap gid = 500-10000000
        winbind enum users = yes
        winbind enum groups = yes
        template homedir = /home/%D/%U
        template shell = /bin/bash
        client use spnego = yes
        client ntlmv2 auth = yes
        encrypt passwords = true
        winbind use default domain = yes
        restrict anonymous = 2
# to avoid the workstation from
# trying to become a master browser
# on your windows network add the
# following lines
        domain master = no
        local master = no
        preferred master = no
        os level = 0

Both files are probably a mess, I've lost track of the number of posts I've read which have had different setup parameters.

I also saw a posting by SuperMike posted on March 1st, 2006 saying he think he had to backup and remove all the /var/lib/samba/*.tdb files. Has anyone else tried this?

The other item he mentioned is he had to play with chmod on/tmp/public. Has anyone else tried this? If so which commands did you have to do with chmod.

Thanks for any help in advance.

---

### Post by Chris_Hansen on 2007-08-22
Hi Everyone,

I am in bad need of help, and hope that one or more of you can rescue me :)

I have followed the howto here, and have also tried SADMS .

I am able to get a ticket, but when i try to join the domain this is the error i keep getting no matter what i try:

[2007/08/22 09:46:45, 0] utils/net_ads.c:ads_startup(289)
  ads_connect: Invalid credentials

I have reset the admin password several times, with no change...

Can someone please help out ?

---

### Post by a_artha on 2007-09-14
Configure Windows 2003 as NIS server using MS tools available in R2.

Configure Users and Groups with userid and groupid respectiveley.
Set the Home Directory

Add the Following in the /etc/hosts file in your ubuntu desktop

ActiveDirectoryMachineName   ipaddress

Configure the Ubuntu machine for NIS Authentication

enjoy with simple steps

---

### Post by ooounohu on 2007-09-27
@ChrisWPD,
Have you had any luck with your authentication?

@anyone,
I've tried this guide as well and it all seems fine but I cannot log in as an AD user, the same situation as ChrisWPD.  I try my AD user and password and either get a small window saying "Authentication failed." or "Incorrect username or password. Letter must be typed in the correct case.".  If further information is needed please let me know and I will post.

Thanks,  OOOUNoHu

---

### Post by ooounohu on 2007-09-28
OK, I fixed out the login issue.  I believe it was the following line that I missed in the /etc/samba/smb.conf
```
# smb.conf
        winbind use default domain = yes
```

Now I have a new issue.  I log in with my AD account, "First Last" w/out the quote - YES there is a space between my first name and my last name.  Authentication works fine, I receive a message stating "creating /home/DOMAIN/First Last", I get a desktop background and then a few messages stating:
"The application "gnome-panel" attempted to change an aspect of your configuration that your system administrator or operating system vendor does not allow you to change. Some of the settings you have selected may not take effect, or may not be restored next time you use the application."
I assume this is because I have a space in my user name so I try a AD account that does not have have a space.  This results in a usable desktop but a lot of the applets don't work such as the volume control, the NetworkManager never appears.

I'll admit that I'm a noob to Linux but about 50% competent concerning AD.  Any suggestions out there?  I assume it is a local (Linux) permissions issue but I don't know where to begin even troubleshooting.  I've run across [this thread]("http://www.linuxforums.org/forum/suse-linux-help/87146-authentication-via-ad.html") which seems to be a similar scenario but there is no resolution.  Any help is much appreciated while I read up on "pam" (assuming that's the issue)...

Thanks,  OOOUNoHu

---

### Post by Joel Duckworth on 2007-10-05
Thanks this tutorial has been a great help in simplifying authentication across our network. Is it possible to set it up to use a second domain controller if the first down?

---

### Post by soterogouveia on 2007-10-09
IT Works!!!!


.....but I have a problem.... when I try to change password it "freezes", or when my password expires, it just gives me a box saying "you hav to change your password", but I can't change it.

Anyone with the same problem? Can anyone help me?

---

### Post by mcfly1204 on 2007-10-10
I have been able to add Ubuntu systems to AD without a problem, however, I cannot seem to access Samba shares from a Windows System.  Every time I do so, I am prompted with a login windows where no login combinations seem to work.  I will post my share parameters below.  I hope my issue lies within this:

[test10092007]
path = /media/RAID
comment = D2D Backups
browseable = yes
writeable = yes
;public = yes
valid users = @"QMC+Administrators"
admin users = @"QMC+Domain Admins"
read list = @"QMC+Domain Users"
write list = @"QMC+Administrators"

---

### Post by artAlexion on 2007-10-11
I had AD login via sadms configuration working well on gutsy for about 2 weeks, and then after rebooting after some updates since last Friday, I am having trouble with cifs mounts.  I think the problem can be traced to the sadms config changes.  Is anyone else having problems with sadms and gutsy?

---

### Post by Joel Duckworth on 2007-10-11
Is it possible to set it up to speak to multiple domain controllers in case one is unavailable? I've search for this but can't seem to find any information.

---

### Post by toobuntu on 2007-10-27
> **artAlexion said:**
> I had AD login via sadms configuration working well on gutsy for about 2 weeks, and then after rebooting after some updates since last Friday, I am having trouble with cifs mounts.  I think the problem can be traced to the sadms config changes.  Is anyone else having problems with sadms and gutsy?

I had the same issue with Feisty.  I forget which packages got updated, but AD authentication no longer worked, and it was most definitely due to updating stuff that SADMS installed and configured (seen by aptitude/apt/dpkg as needed dependencies).

In my case, AD auth was in a testing environ, so I reverted to local accts via SAM.  Now with Gutsy, I need to set up single sign on in a production environ and looking under the hood of SADMS to try to do it in an easy manner that won't break!

---

### Post by Joel Duckworth on 2007-10-28
I had issues with Gusty using my configuration I was using on Dapper. I traced it to having the FQDN set properly. I previously had this in my settings
/etc/hostname: example01
/etc/hosts: 10.0.0.1 example01
/etc/resolv.conf: 
 nameserver 10.0.0.2
 search domain.com 

Using these hostname settings when you try a 'hostname -f' it doesn't return the FQDN so the joining to the domain failed for me with the following message:
"Failed to set servicePrincipalNames..."

I updated my settings as follows (which they should have been on anyway)
/etc/hostname: example01
/etc/hosts: 10.0.0.1 example01.domain.com example01
/etc/resolv.conf 
 nameserver 10.0.0.2
 search domain.com
 domain domain.com

Now a 'hostname -f' returns the FQDN properly and adding the machine to the domain worked ok. 

Maybe you've got similar issues?

---

### Post by tfiedler on 2007-11-01
Just an update, but I just reran through my steps and they worked for the new version of Ubuntu 7.10 server as well... just thought everyone might like that information.

-todd

---

### Post by Joel Duckworth on 2007-11-01
Yep, it's great news.

---

### Post by al3xm on 2007-11-15
Hi,

I followed these instructions back when I was running Dapper and it has been working great, however I think it was around the time I upgraded to Feisty I noticed that in the windows permissions list on XP it now lists files on samba shares as belonging to "Unix User\user" whereas before it used to list them as "ServerName\user". I've now upgraded to Gutsy and this still occurs.

This isn't a huge problem as everything still works but I was never able to find out why this was. Anyone any ideas?

Alex

---

### Post by Richard_Sabre on 2007-11-15
Using ubuntu 7.10 I can get kinit working and can also view the certificate with klist. I joined the domain and can view all users with wbinfo -u, but I still can't login with an AD user and it prompts for a password when trying to connect to other network shares.

---

### Post by metoor30 on 2007-11-19
If anyone is receiving this error

kinit(v5): KDC has no support for encryption type while getting initial credentials


And has a OU structure, make sure that the user you are using is in the root users folder and not within an OU in your structure.  I'm sure there is a way to specify which OU the user is in, but I did not find it in this post.  I will look through the Kerberos Docs and see if I can find anything...

---

### Post by djc8484 on 2007-12-06
Thank you!  This worked like a champ just using out of the box Gutsy server.  One question:

Is there a way to restrict login access after this is complete?  Right now every user in AD can login to my Gutsy server.

Thanks again!

---

### Post by schapman43 on 2008-01-23
Finally, Finally, FINALLY!!!!!!  I got my Kubuntu box joined to my AD 2003 domain.  My problem?  I needed to set the host name properly in the hosts file.  Slightly retarded I know! :)

---

### Post by schapman43 on 2008-01-23
> **djc8484 said:**
> Thank you!  This worked like a champ just using out of the box Gutsy server.  One question:

Is there a way to restrict login access after this is complete?  Right now every user in AD can login to my Gutsy server.

Thanks again!


I'm definitely no pro at this but I believe what you are looking for is in the PAM settings.

---

### Post by KyferEz on 2008-03-07
I just followed the guide and now have all sorts of problems, in addition I couldn't get it to work!!!

Problems:
Sudo password problems. If I enter a command with sudo, it asks for my password twice!!!
If I try to do anything in the gui that pops up the box to enter admin password, It always fails and I KNOW I'm entering the correct password.

when I try to do  sudo ntpdate restart I get an error "can't find host restart"

When I do kinit [email]username@mydomain.loca[/email]l I never get a ticket.

So it looks like my following this has screwed my system, as far as the password is concerned, and I don't know where to look to fix it!!!

HELP, I don't want to reinstall.

The problem with Linux is that it's way to easy to fubar something when simply trying to setup a program or service that will nixes the whole system for someone who isn't a Linux expert. It's way to difficult to do something that should be stupid-simple, like connecting to a Windows Active Directory domain!!!  :(  /rant

I'm a Linux fan, but boy am I frustrated!!!

---

### Post by jodema on 2008-03-26
Hi I have followed this how to and can now authenticate using active directory and everything works fine the problem I have is that every time the machine is restarted it won't authenticate on active directory until I first log on as a local user and issue a kinit command and a net join command I can then log off as a local user and log on as an active directory user. 

How can I log on to active directory from startup. 

I'm using Gutsy.

---

### Post by Joel Duckworth on 2008-04-07
Hi, I'd like to suggest a few improvements to the HOWTO after some experience with this setup. 

For redundancy the password server should be as follows in smb.conf

```
password server = domain1.example.com, domain2.example.com, *
```

If you're also pointing your DNS at a pair of domain controllers I recommend changing the DNS timeout so that DNS is resolved quicker if the primary server is down.

in /etc/resolv.conf add

```
options timeout:0.5
```

With these small changes if the domain controller that is listed first in the config goes offline the authentication will still take place from the second one. There may be a delay of ~30s while the first one times-out. If DNS is running of both the domain controllers (usual setup) then with the primary DNS down you won't experience 5 second delays for DNS queries.

For details on the DNS see

```
man resolv.conf
```

---

### Post by insanepyro on 2008-04-08
[B]Using short domain name -- PYROSDOMAIN
Failed to set servicePrincipalNames. Please ensure that
the DNS domain of this server matches the AD domain,
Or rejoin with using Domain Admin credentials.
Disabled account for 'UBUNTU-MACG3' in realm 'PYROSDOMAIN.LOCAL'[/B]

I keep having this issue, I've tried everything I could find on this issue and I'm completly stuck.

My PDC is a Windows 2003 box.

Which is **pyroswin03box.pyrosdomain.local**
**pyrosdomain.local** being the domain.

I'm using **ubuntu breezy on a MAC G3**

I get my kerbos ticket 


[B][B][B]Valid starting     Expires            Service principal
04/08/08 10:21:48  04/08/08 20:20:16  krbtgt/PYROSDOMAIN.LOCAL@PYROSDOMAIN.LOCAL
        renew until 04/09/08 10:21:48[/B]


Kerberos 4 ticket cache: /tmp/tkt1000[/B][/B]


Here is my hosts file


[B]127.0.0.1 ubuntu.PyrosDomain.local
192.168.0.1 pyroswin03box.PyrosDomain.local PYROSDOMAIN.LOCAL[/B]


Here is my samba config

[B][global]
security = ADS
realm = PYROSDOMAIN.LOCAL
workgroup = PYROSDOMAIN
password server = pyroswin03box.PyrosDomain.local
spnego = yes
wins support = no
wins server = 192.168.0.1
invalid users = root
# Winbind settings
idmap uid = 10000-20000
idmap gid = 10000-20000
# For testing
debuglevel = 2

# A shared folder for testing purposes
[SharedFolder]
path = /home/insanepyro
available = yes
public = yes
writable = yes
force create mode = 0666
force directory mode = 0777[/B]

heres my krb5.conf
[B]
[libdefaults]
 default_realm = PYROSDOMAIN.LOCAL
 krb4_config = /etc/krb.conf
 krb4_realms = /etc/krb.realms
 kdc_timesync = 1
 ccache_type = 4
 forwardable = true
 proxiable = true
# The following libdefaults parameters are only for Heimdal Kerberos.
 v4_instance_resolve = false
 v4_name_convert = {
  host = {
   rcmd = host
   ftp = ftp
  }
  plain = {
   something = something-else
  }
 }

[realms]
PYROSDOMAIN.LOCAL = {
        kdc = pyroswin03box.PyrosDomain.local
        admin_server = pyroswin03box.PyrosDomain.local
}
[domain_realm]
 .pyrosdomain.local = PYROSWIN03BOX.PYROSDOMAIN.LOCAL
 pyrosdomain.local = PYROSWIN03BOX.PYROSDOMAIN.LOCAL
[login]
 krb4_convert = true
 krb4_get_tickets = true[/B]



The machine shows up in AD computers, but as disabled.
I remove the machine but it comes back after a join attempt as disabled.
Any help would be greatly appreciated this is driving me nuts.

---

### Post by chemist109 on 2008-04-10
> **jodema said:**
> Hi I have followed this how to and can now authenticate using active directory and everything works fine the problem I have is that every time the machine is restarted it won't authenticate on active directory until I first log on as a local user and issue a kinit command and a net join command I can then log off as a local user and log on as an active directory user. 

How can I log on to active directory from startup. 

I'm using Gutsy.

jodema, I'm having a similar problem.  I can't authenticate via AD at the initial boot, but if I restart winbind, I can then authenticate via AD.  

Alternatively, If I wait a very long time, it also seems to finally get the AD users.

---

### Post by shushotora on 2008-04-15
Thanks to the original tutorial i was able to join my domain, however when i try to login as a user i get a message Access Denied and then a user name and password invalid message. is it possible its unable to create the user folders? if anybody has an idea can they please let me know.

---

### Post by bolivartech on 2008-04-28
> **shushotora said:**
> Thanks to the original tutorial i was able to join my domain, however when i try to login as a user i get a message Access Denied and then a user name and password invalid message. is it possible its unable to create the user folders? if anybody has an idea can they please let me know.
you might try using domain\username and see if that works

---

### Post by shushotora on 2008-04-29
Gave that a try and i am still getting an access denied message. Hrrm, maybe there is a permissions thing i missed?

---

### Post by nanugtr on 2008-05-01
> **chemist109 said:**
> jodema, I'm having a similar problem.  I can't authenticate via AD at the initial boot, but if I restart winbind, I can then authenticate via AD.  

Alternatively, If I wait a very long time, it also seems to finally get the AD users.

New here,
I got my Ubuntu 8 to join AD but im having same problems as Chemist109
PLS HELP!

---

### Post by j3r3my86 on 2008-06-10
Hi

I'm new to this and I've been trying to get my Linux client to join a W2k3 domain and work properly for about a week already

I've shifted from using manual configurations to using SADMS as some of you guys introduced here.

My latest update is I'm able to join the domain and then the problems come.

At times, I'm able to login to user1 only and at time to user2 only. 

I'm currently setting up this client in a school environment and there are lots of students and teachers account within the whole forest. My admin id allows me to view the 100+ OUs created (one for every school). However with that, my client is not able to retrieve EVERY account that I would actually NEED (i.e accounts that are for my school's users at least). 

I did a save of ouput from "List Users" in the SADMS menu and did a manual match of IDs i retrieved against the AD. A very large portion is not retrieved, I'm getting accounts from other school's OUs.

I've also edited idmap uid and gid to 1000-33554431 in smb.conf (the number was found from one of the howtos for AD winbind at help.ubuntu.com) but still not able to get the correct lists of user accounts.

In fact, many a times I would not be able to retrieve anything and if I do, it will be a partial list not containing the accounts that I really need.

Please provide me some guidance on my problem. Very desperately need one :| 

and also thx for all the inputs so far for this thread.. has been useful but doesn't contain help for my problem =(

---

### Post by Kileli on 2008-07-14
Ok guys Few Question i have been struggling to get my Linux machine connected to my Domain for about a week now. i tried following this HOW TO: but to no success the only way i seam to be able to get it to join is to use LIKEWISE.  Only i still cannot see the share drives on the windows server.what is the difference between likewise and this how to: i really want to make this work. also i was thinking about building a Linux server that would also communicate with the windows server. is that even possible.
i have to admit i am the definition of a noob in the Linux world but i catch on quick any help would be most appreciated. i have to learn as much as i can as fast as i can so i will be able to support several machines at work.

---

### Post by caaron on 2008-07-31
Everything worked but joining my system to the domain

here is the error I get

Using short domain name -- DOMAIN
Deleted account for 'WORKSTATION' in realm 'DOMAIN.LOCAL'
Failed to join domain: Type or value exists

Any ideas?

---

### Post by gab on 2008-08-07
This HowTo was what I needed to get AD integration of my Linux boxes up and running, thanks!

My "problem" is more or less a curyosyty. I have a lockal user whit the same loginname as one of the AD users. The local user has $HOME=/home/<login> and the AD user has $HOME=/home/AD/<login>. When I tyr to login, I punch login and the password and get loged in and the $HOME is /home/<login>. It does not mather if i use the password to the lockal or the AD user, I end up in /home/<login>.

Is there anybody that has any idea of how to conf pam (I thinck pam is the key) so that I get the right $HOME.

---

### Post by whitenight639 on 2008-09-05
This How to is using ubuntu server, im a noob with regards to networking and AD but at work we have 20 odd low spec laptops that arn't capable of running XP can we use ubuntu to connect to AD, if so can we use the normal desktop edition or do we need to use ubuntu server? 

comments would be appreciated!

---

### Post by dboot on 2008-09-10
Can anyone help me with these errors?

```

[root home]# kinit DOMAINADMIN@DOMAIN.COM
Password for DOMAINADMIN@DOMAIN.COM: 
[root home]# klist
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: DOMAINADMIN@DOMAIN.COM

Valid starting     Expires            Service principal
09/10/08 02:27:10  09/10/08 03:07:10  krbtgt/DOMAIN.COM@DOMAIN.COM


Kerberos 4 ticket cache: /tmp/tkt0
klist: You have no tickets cached
[root home]# net ads join -U DOMAINADMIN@DOMAIN.COM
DOMAINADMIN@DOMAIN.COM's password: 
Failed to join domain!
[root home]# net ads info
LDAP server: 192.168.1.5
LDAP server name: windowserver.domain.com
Realm: DOMAIN.COM
Bind Path: dc=DOMAIN,dc=COM
LDAP port: 389
Server time: Wed, 10 Sep 2008 02:26:45 EDT
KDC server: 192.168.1.5
Server time offset: -69

```

Thanks for any suggestions!

---

### Post by MrFrame on 2008-11-02
Hi,

I applied the provided setup about 10 months ago successfully. Thanks for that.
Meanwhile a new request arised, which I currently don't know how to address:
A dedicated AD User account should be setup to inherit root privileges in order to "clean up" user shares, i.e. delete files and directories.
I tried alread to add "write list" with the acccount's name to the smb.conf [global] and [homes] sections, but w/o any luck.

Any ideas on how to set this up?

Thanks.

---

### Post by DouglasK on 2008-11-06
I've followed through the howto and am having good success on Ubuntu 8.10 (Intrepid Ibex, I think) until the "net ads join" stage.  I'm getting my ticket fine:

```
$ klist
Ticket cache: FILE:/tmp/krb5cc_1000
Default principal: myusername@MYSUBDOMAIN.MYDOMAIN.ICS

Valid starting     Expires            Service principal
11/06/08 13:01:01  11/06/08 19:41:01  krbtgt/MYSUBDOMAIN.MYDOMAIN.ICS@MYSUBDOMAIN.MYDOMAIN.ICS


Kerberos 4 ticket cache: /tmp/tkt1000
klist: You have no tickets cached
```But when I perform the net ads join, I get the following (with debug enabled):
```
$ net ads join -U myusername@MYSUBDOMAIN.MYDOMAIN.ICS -d1
Enter myusername@MYSUBDOMAIN.MYDOMAIN.ICS's password:
[2008/11/06 13:01:18,  1] libnet/libnet_join.c:libnet_Join(1770)
  libnet_Join:
      libnet_JoinCtx: struct libnet_JoinCtx
          in: struct libnet_JoinCtx
              dc_name                  : NULL
              machine_name             : 'MYHOSTNAME'
              domain_name              : *
                  domain_name              : 'MYSUBDOMAIN.MYDOMAIN.ICS'
              account_ou               : NULL
              admin_account            : 'myusername@MYSUBDOMAIN.MYDOMAIN.ICS'
              admin_password           : *
              machine_password         : NULL
              join_flags               : 0x00000023 (35)
                     0: WKSSVC_JOIN_FLAGS_JOIN_WITH_NEW_NAME
                     0: WKSSVC_JOIN_FLAGS_JOIN_DC_ACCOUNT
                     0: WKSSVC_JOIN_FLAGS_DEFER_SPN
                     0: WKSSVC_JOIN_FLAGS_MACHINE_PWD_PASSED
                     0: WKSSVC_JOIN_FLAGS_JOIN_UNSECURE
                     1: WKSSVC_JOIN_FLAGS_DOMAIN_JOIN_IF_JOINED
                     0: WKSSVC_JOIN_FLAGS_WIN9X_UPGRADE
                     0: WKSSVC_JOIN_FLAGS_ACCOUNT_DELETE
                     1: WKSSVC_JOIN_FLAGS_ACCOUNT_CREATE
                     1: WKSSVC_JOIN_FLAGS_JOIN_TYPE
              os_version               : NULL
              os_name                  : NULL
              create_upn               : 0x00 (0)
              upn                      : NULL
              modify_config            : 0x00 (0)
              ads                      : NULL
              debug                    : 0x01 (1)
              secure_channel_type      : SEC_CHAN_WKSTA (2)
[2008/11/06 13:01:19,  1] libnet/libnet_join.c:libnet_Join(1801)
  libnet_Join:
      libnet_JoinCtx: struct libnet_JoinCtx
          out: struct libnet_JoinCtx
              account_name             : NULL
              netbios_domain_name      : NULL
              dns_domain_name          : NULL
              dn                       : NULL
              domain_sid               : NULL
                  domain_sid               : (NULL SID)
              modified_config          : 0x00 (0)
              error_string             : 'failed to find DC for domain MYSUBDOMAIN.MYDOMAIN.ICS'
              domain_is_ad             : 0x00 (0)
              result                   : WERR_DOMAIN_CONTROLLER_NOT_FOUND
Failed to join domain: failed to find DC for domain MYSUBDOMAIN.MYDOMAIN.ICS
```I can ping the DC machine by hostname without issue, fwiw.  Any thoughts on how to work around this?

~~Douglas K

---

### Post by innovate2000 on 2008-11-25
Has anyone found a resolution? I am using Intrepid Ibex and have the same experience that DouglasK has. I've been working this for several days trying this and that but am at my wits end. ANy help appreciated (please post here for others who are in the same boat). Thanks

---

### Post by Rudy507 on 2008-12-11
I'd like to put a link to this thread in here because it has to do with my question:
[http://ubuntuforums.org/showthread.php?t=897860](http://ubuntuforums.org/showthread.php?t=897860).

I didn't exactly follow the instructions that started this thread to join my Ubuntu box to a Windows Active Directory DOMAIN (instead, I followed [these](http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/)). 

I am wondering how to map to a user's network drive (i.e. smb://DOMAIN/username$) so THAT is the user's Home location (instead of the default user/home). 

I also need to set permissions so that the AD users don't have access to even read the root directory (or other people's stuff), install anything, etc... Would this be done by adding a Active Directory's group to Ubuntu, and setting that group's permissions while logged in as root or Super User?

---

### Post by Daga on 2008-12-11
> **innovate2000 said:**
> Has anyone found a resolution? I am using Intrepid Ibex and have the same experience that DouglasK has. I've been working this for several days trying this and that but am at my wits end. ANy help appreciated (please post here for others who are in the same boat). Thanks

It seems the Russians are pretty smart:

[http://forum.ubuntu.ru/index.php?topic=10062.msg308220](http://forum.ubuntu.ru/index.php?topic=10062.msg308220)

(For the benefit of those of you who don't want to run to Google translate and can't understand Russian: ) It looks like you can join the domain without including '@MYSUBDOMAIN.MYDOMAIN.ICS' on the "net ads join" command.

Woohoo!

---

### Post by lukekurtis on 2008-12-13
I'm also having exactly the same issue as DouglasK.  I've followed this doc exactly:

[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

Anybody have any suggestions or solutions here?

---

### Post by Daga on 2008-12-15
> **lukekurtis said:**
> I'm also having exactly the same issue as DouglasK.  I've followed this doc exactly:

[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

Anybody have any suggestions or solutions here?
Here's how I resolved the problem on my computer:

1. Add the IP of the Windows DNS server to /etc/resolv.conf (you may wish to edit the network settings normally. I tend to 'hack')

2. Use "net ads join -U {username}" ... whenever I specified the computer or domain after the username, it said it could not look up the DC.

HTH

---

### Post by moTaro on 2008-12-19
> **slamp said:**
> great tutorial! i have now joined my ubuntu server into my domain. i do have a question.

how do i setup multiple groups in a folder in linux?

i want groups that can read/write and groups that can only read.

so far i have setup a group in active directory and made to be able to read and write to the samba share, but i do not know of anyway to make another one that can only read.


You can solve this in guru manner rather than groups, since your result should be one write and one read group.

Make 2 new user domains name them for example

domain user: readonly
domain user: readwrite

on shared resources add them to advanced secuirity and on readonly user deny write delete and create directory, and readwrite give full control.

Use this users only for mounting shares from windows resources on ubuntu box, and let them log in authenticate with their own user ex: bobby, pass bobby.

---

### Post by Daga on 2008-12-30
> **Daga said:**
> Here's how I resolved the problem on my computer:

1. Add the IP of the Windows DNS server to /etc/resolv.conf (you may wish to edit the network settings normally. I tend to 'hack')

2. Use "net ads join -U {username}" ... whenever I specified the computer or domain after the username, it said it could not look up the DC.

And... I've run into this problem another way. The error is caused when the "net ads join" command is unable to look up a DNS/WINS entry for _ldap._tcp.dc._msdcs.YOUR.DOMAIN (try running the command with "-d 3", you'll see what I'm talking about).

The first time I apparently set up the Windows DNS server correctly so the problem was in talking to the server. The second time I didn't, and the Windows server was confused. Make sure that on the DNS server you have "Forward Lookup Zones" -> "_msdcs.YOUR.DOMAIN" -> "dc" -> "_tcp". If not, try the instructions located here:

[http://support.microsoft.com/kb/817470](http://support.microsoft.com/kb/817470)

---

### Post by Leoembon on 2009-04-14
Hi, the How to is really good, but I am not succeeding at logging the Active Directory. Its everything allright up to the time I do the "net ads join -U administrador". After I enter the pass the terminal gives me this:

root@sistemasubuntu:/home/leo# net ads join -U administrador
Enter administrador's password:
Failed to join domain: failed to lookup DC info for domain 'CANUDASSUC1.COM.AR' over rpc: The network name cannot be found

I've tried everything, with the domain, with the realm, everything. 
But if I enter "rpc" instead of "ads" then I receive "Joined domain CANUDASSUC1." (Which is ok). But it has no positive reaccions, I cannot enter the net.

The domain controller is a W2K one.

Here's my smb.conf:
[global]
	workgroup = CANUDASSUC1
	realm = CANUDASSUC1.COM.AR
	server string = Samba file and print server
	bind interfaces only = Yes
	security = ADS
	update encrypted = Yes
	client schannel = No
	server schannel = No
	null passwords = Yes
	obey pam restrictions = Yes
	password server = cabas101.canudassuc1.com.ar
	guest account = smbguest
	passwd program = /usr/bin/passwd '%u'
	passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
	passwd chat timeout = 120
	password level = 6
	username level = 6
	unix password sync = Yes
	log file = /var/log/samba/samba.log
	max log size = 1000
	smb ports = 135 445 139
	name resolve order = wins lmhosts bcast
	client signing = No
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	printcap name = cups
	machine password timeout = 120
	add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
	delete user script = /usr/sbin/userdel '%u'
	add group script = /usr/sbin/groupadd '%g'
	delete group script = /usr/sbin/groupdel '%g'
	add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
	delete user from group script = /usr/sbin/userdel '%u' '%g'
	add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
	logon script = %G.bat
	logon path = \\%L\profiles\%u
	logon drive = m:
	logon home = \\%L\homes\%u
	os level = 33
	local master = No
	domain master = No
	dns proxy = No
	wins server = 192.168.2.1
	ldap ssl = no
	remote announce = 192.168.2.1
	remote browse sync = 192.168.2.1
	idmap uid = 500-10000000
	idmap gid = 500-10000000
	template shell = /bin/bash
	winbind separator = +
	winbind cache time = 360
	winbind use default domain = Yes
	winbind trusted domains only = Yes
	winbind nested groups = No
	winbind nss info = no
	guest ok = Yes
	hosts allow = 127., 192.168.2.
	cups options = raw
	follow symlinks = No

[homes]
	comment = Home Directories
	path = /home
	read only = No
	locking = No
	share modes = No

[netlogon]
	comment = Network Logon Service
	path = /home/netlogon
	read only = No
	locking = No
	share modes = No

PLEASE HELP ME!!

---

### Post by bkortleven on 2009-08-26
OK, after some struggling, I found a maybe helpful thing to check if it isn't working right away:

I did a ```
net ads testjoin
``` and always got a message like ```
[2009/08/26 13:47:10, 0] libads/kerberos.c:ads_kinit_password(228)
  kerberos_kinit_password SEWER$@MAIN.LOCAL failed: Client not found in Kerberos database
[2009/08/26 13:47:10, 0] libads/kerberos.c:ads_kinit_password(228)
  kerberos_kinit_password SEWER$@MAIN.LOCAL failed: Client not found in Kerberos database
Join to domain is not valid: Improperly formed account name

```

Apparently, the administrator password cannot be empty!

I created a new domadm account with a password (in this test server, a lot of services depend on the 'administrator' user and its (empty) password, so I didn't want to break stuff by just putting a password there.
When using the domadm user for joining etc, it all works.

wbinfo -n on an AD user gives me the info from the windows server.

Just for your convenience: if it gives you an error like the above, check if your administrative user does have a password set...

---

### Post by bkortleven on 2009-08-26
@ Leoembon:

check if your /etc/hosts file contains an entry to resolve the AD servers' name to its IP...
Do a ping on the name you set in /etc/krb5.conf file's admin_server entry to check if it resolves correctly.

I had a similar issue before, and that did the trick for me.

---

### Post by pawhtiobo on 2009-08-26
Hi :)

[http://www.likewise.com/](http://www.likewise.com/)

Just a nice tool also :)

---

### Post by cg88 on 2009-11-09
Great tutorial! After following the initial tutorial and configuring NTP, my machine is able to authenticate against AD.

I do have one issue still. Authentication works great for any user unless they are required to change their password. I've been testing using SSH, and get the following output:

```
WARNING: Your password has expired.
You must change your password now and login again!
passwd: Authentication token manipulation error
passwd: password unchanged
Connection to _computer-name_ closed.
```

Any ideas? Once this is working, I'll be completely set. Thanks!

---

### Post by exodius on 2009-11-12
Hi. may be not the right place to post, but...  I want to integrate test machine with ubuntu installed to authenticate with ADS..find some guide here  [http://www.ubuntugeek.com/how-to-integrate-windows-active-directory-and-samba-in-ubuntu.html](http://www.ubuntugeek.com/how-to-integrate-windows-active-directory-and-samba-in-ubuntu.html) but obviously smth there was wrong and now i can't logon on even with local accounts.. i think
problem is in pam modules

 
**Modify the PAM settings**
 
[LIST]
[*]/etc/pam.d/common-account should contain only the following lines
[/LIST]
 account sufficient    pam_winbind.so
account required    pam_unix.so
 
[LIST]
[*]/etc/pam.d/common-auth should contain only the following lines
[/LIST]
 auth    sufficient      pam_winbind.so
auth    required        pam_unix.so nullok_secure use_first_pass
 
[LIST]
[*]Modify the /etc/pam.d/common-password file, so the max parameter is set to 50, similar to the one shown below
[/LIST]
 password   required   pam_unix.so nullok obscure min=4 max=50 md5
 
[LIST]
[*]Make sure the /etc/pam.d/common-session file contains the following line
[/LIST]
 session required   pam_mkhomedir.so umask=0022 skel=/etc
 Make a directory to hold domain user home directories
 Note: Use the value you put in the WORKGROUP tag of the /etc/samba/smb.conf file
 mkdir -p /home/DOMAIN






Any help is appreciated...Thank you!

---

### Post by Saghaulor on 2009-11-12
I just got an Ubuntu 9.10 box to authenticate to AD.

Here's what I did. (Before changing any of the files mentioned below, make sure to create a backup copy to save yourself future headache.)

[LIST]
```
sudo aptitude install likewise-open-gui
```
[/LIST]
[LIST]
Modify /etc/hosts, added entry for the domain controller, use FQDN (fully qualified domain name) ie, server.domain.local
[/LIST]
[LIST]
Verify that the hostname of Ubuntu box doesn't contain special characters, check /etc/hostname, if it did make sure the /etc/hosts file is corrected
[/LIST]
[LIST]
Modify connection manager to dhcp(address only) and added Domain Controller in DNS Server field
[/LIST]
[LIST]
Modify /etc/sudoers file to add AD domain admins to sudoers.
Add to the bottom of the file
> 
%your_fqdn_here\\Domain^Admins ALL=(ALL) ALL

[/LIST]
[LIST]
Modify /etc/samba/lwiauthd.conf, add to the bottom 
> 
winbind use default domain = yes

to have AD member use only their username and not "your_fqdn\username" 
[/LIST]
[LIST]
Modify /etc/nsswitch.conf, change the line the refers to hosts to 
> hosts:          files dns

[/LIST]
[LIST]
Using likewise-open, add the computer to the domain. Be sure to use the full domain name, ie, domain.local.
[/LIST]
[LIST]
Reboot and your AD members should be able to authenticate to the the DC, using the Ubuntu box. In addition, your AD admins should be able to administer the Ubuntu box.
[/LIST]


A thank you goes out to Likewise-open and these folks for their help.
[http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/]("http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/")

---

### Post by pigmy31 on 2009-11-13
Hi,

I've configured (kerberos, samba, pam) on my profesional ubuntu box (Karmic Koala 64bits) to be able to join my enterprise active directory.

It works fine (ie when I start nautilus and I click on a windows shares, no password is required) when I :

[LIST=1]
[*]start my session
[*]open a terminal, type kinit and give my domain password
[/LIST]
Without this second action, a password is asked for any share acceded. I think that it's not the normal process.

When I look the file /var/log/samba.log.winbindd, I can see :[INDENT]Kinit failed: Client not found in Kerberos database
[/INDENT]I have also the following message :[INDENT]Could not receive trustdoms
[/INDENT]How may I correct my configuration to access windows shares without any domain password during my session ?

Thanks,
Michel

---

### Post by boltronics on 2010-02-02
> **cg88 said:**
> Great tutorial! After following the initial tutorial and configuring NTP, my machine is able to authenticate against AD.

I do have one issue still. Authentication works great for any user unless they are required to change their password. I've been testing using SSH, and get the following output:

```
WARNING: Your password has expired.
You must change your password now and login again!
passwd: Authentication token manipulation error
passwd: password unchanged
Connection to _computer-name_ closed.
```

Any ideas? Once this is working, I'll be completely set. Thanks!

Just bumped into this problem myself. The answer lies in /etc/pam.d/common-password - add the line:

```
password	[success=2 default=ignore]	pam_winbind.so
``` to the top of the default common-password file.

Note the warning [here]("http://wiki.samba.org/index.php/Samba_&_Active_Directory#password_changes") about changing domain passwords using this technique.

---

### Post by SirBismuth on 2010-02-02
Thanks **Saghaulor**, already had the likewise-open-gui installed.  

Also, the line > Modify /etc/samba/lwiauthd.conf, add to the bottom did not count for me, as I did not have that file on my system, so I ignored it.

Now I can authenticate on the AD domain, and access the relevant shares.

B

---

### Post by jeevanpk on 2010-02-03
Please help me something which can get integrated my ADS with FTP

---

### Post by jeevanpk on 2010-02-03
:p> **jeevanpk said:**
> Please help me something which can get integrated my ADS with FTP

---

### Post by CAEman on 2010-02-19
[CENTER]Dear Experts![/CENTER]
 
First, excuse me for my English.
There is local Linux machine wich I have cofigured kerberos and ldap - kinit and ldapsearch are working.
Ldapsearch works like this:
ldapsearch -v -x -D CN=user,CN=Users,DC=domain -W -LLL "(cn=user)"
ldap_initialize( <DEFAULT> )
Enter LDAP Password:
filter: (cn=user)
requesting: All userApplication attributes
dn: CN=user,CN=Users,DC=domain
objectClass: top
objectClass: person
objectClass: organizationalPerson
objectClass: user
cn: user
distinguishedName: CN=user,CN=Users,DC=domain
instanceType: 4
whenCreated: 20071003134645.0Z
whenChanged: 20100212095526.0Z
displayName:: 0J/QtdGA0LXQutGA0LXRgdGC0L7QsiDQkNC90LTRgNC10Lkg0J/QtdGC0YDQ vtCy
0LjRhw==
uSNCreated: 389673
memberOf: CN=group,CN=Users,DC=domain
uSNChanged: 44764302
name: user
objectGUID:: TTTD/aBhEE6PxsIlWWxZoA==
userAccountControl: 66048
badPwdCount: 0
codePage: 0
countryCode: 0
homeDirectory: \\server\users\personal\user
homeDrive: Z:
badPasswordTime: 129104512781569552
lastLogoff: 0
lastLogon: 129110472236388768
pwdLastSet: 128880768398237296
primaryGroupID: 513
objectSid:: AQUAAAAAAAUVAAAAVnD5YpbP+W9E8DV3OXwAAA==
accountExpires: 0
logonCount: 733
sAMAccountName: user
sAMAccountType: 805306368
objectCategory: CN=Person,CN=Schema,CN=Configuration,DC=domain
lastLogonTimestamp: 129104421266577456
"
And with "(cn=*)" I can view all AD users on Windows server (like any other AD user).
 
But "$ ssh **[COLOR=#474747]user@localhost[/COLOR]**" gives:
"
sshd[7005]: nss_ldap: could not search LDAP server - Server is unavailable
sshd[7005]: Invalid user user from 127.0.0.1
sshd[7010]: pam_krb5[7010]: default/local realm 'DOMAIN'
sshd[7010]: pam_krb5[7010]: configured realm 'DOMAIN'
sshd[7010]: pam_krb5[7010]: flag: debug
sshd[7010]: pam_krb5[7010]: flags: forwardable not proxiable
sshd[7010]: pam_krb5[7010]: flag: no ignore_afs
sshd[7010]: pam_krb5[7010]: flag: no null_afs
sshd[7010]: pam_krb5[7010]: flag: user_check
sshd[7010]: pam_krb5[7010]: flag: no krb4_convert
sshd[7010]: pam_krb5[7010]: flag: krb4_convert_524
sshd[7010]: pam_krb5[7010]: flag: krb4_use_as_req
sshd[7010]: pam_krb5[7010]: will try previously set password first
sshd[7010]: pam_krb5[7010]: will let libkrb5 ask questions
sshd[7010]: pam_krb5[7010]: flag: use_shmem
sshd[7010]: pam_krb5[7010]: flag: external
sshd[7010]: pam_krb5[7010]: flag: warn
sshd[7010]: pam_krb5[7010]: ticket lifetime: 43200s (0d,12h,0m,0s)
sshd[7010]: pam_krb5[7010]: renewable lifetime: 86400s (1d,0h,0m,0s)
sshd[7010]: pam_krb5[7010]: minimum uid: 1
sshd[7010]: pam_krb5[7010]: banner: Kerberos 5
sshd[7010]: pam_krb5[7010]: ccache dir: /tmp
sshd[7010]: pam_krb5[7010]: ccname template: FILE:%d/krb5cc_%U_XXXXXX
sshd[7010]: pam_krb5[7010]: keytab: FILE:/etc/krb5.keytab
sshd[7010]: pam_krb5[7010]: token strategy: v4,524,2b,rxk5
sshd[7010]: pam_krb5[7010]: pam_authenticate called for 'user', realm 'DOMAIN'
sshd[7010]: nss_ldap: could not search LDAP server - Server is unavailable
sshd[7010]: pam_krb5[7010]: error resolving user name 'user' to uid/gid pair
sshd[7010]: pam_krb5[7010]: error getting information about 'user'
sshd[7010]: nss_ldap: could not search LDAP server - Server is unavailable
"
And after password input:
"
sshd[7142]: error: PAM: Authentication failure for illegal user user from localhost
sshd[7142]: Failed keyboard-interactive/pam for invalid user user from 127.0.0.1 port 45307 ssh2
sshd[7148]: pam_krb5[7148]: default/local realm 'DOMAIN'
sshd[7148]: pam_krb5[7148]: configured realm 'DOMAIN'
sshd[7148]: pam_krb5[7148]: flag: debug
sshd[7148]: pam_krb5[7148]: flags: forwardable not proxiable
sshd[7148]: pam_krb5[7148]: flag: no ignore_afs
sshd[7148]: pam_krb5[7148]: flag: no null_afs
sshd[7148]: pam_krb5[7148]: flag: user_check
sshd[7148]: pam_krb5[7148]: flag: no krb4_convert
sshd[7148]: pam_krb5[7148]: flag: krb4_convert_524
sshd[7148]: pam_krb5[7148]: flag: krb4_use_as_req
sshd[7148]: pam_krb5[7148]: will try previously set password first
sshd[7148]: pam_krb5[7148]: will let libkrb5 ask questions
sshd[7148]: pam_krb5[7148]: flag: use_shmem
sshd[7148]: pam_krb5[7148]: flag: external
sshd[7148]: pam_krb5[7148]: flag: warn
sshd[7148]: pam_krb5[7148]: ticket lifetime: 43200s (0d,12h,0m,0s)
sshd[7148]: pam_krb5[7148]: renewable lifetime: 86400s (1d,0h,0m,0s)
sshd[7148]: pam_krb5[7148]: minimum uid: 1
sshd[7148]: pam_krb5[7148]: banner: Kerberos 5
sshd[7148]: pam_krb5[7148]: ccache dir: /tmp
sshd[7148]: pam_krb5[7148]: ccname template: FILE:%d/krb5cc_%U_XXXXXX
sshd[7148]: pam_krb5[7148]: keytab: FILE:/etc/krb5.keytab
sshd[7148]: pam_krb5[7148]: token strategy: v4,524,2b,rxk5
sshd[7148]: pam_krb5[7148]: pam_authenticate called for 'user', realm 'DOMAIN'
sshd[7148]: nss_ldap: could not search LDAP server - Server is unavailable
sshd[7148]: pam_krb5[7148]: error resolving user name 'user' to uid/gid pair
sshd[7148]: pam_krb5[7148]: error getting information about 'user'
sshd[7148]: nss_ldap: could not search LDAP server - Server is unavailable
"
How is it possible to configure local Linux machine with authorization on Windows AD server having only such account on a server?
 
Thanks in advance.

---

### Post by CAEman on 2010-02-26
May be somebody knows how it possible to do by script?

---

### Post by doncrawley on 2010-04-04
The following steps were tested on Ubuntu 9.10.

The easiest way to do this is to install Likewise-Open and Likewise-Open-GUI from the repository:

sudo apt-get install likewise-open likewise-open-gui

After installation is complete, go to System>>Administration>>Active Directory membership to join the Ubuntu computer to the AD domain.  You'll have to restart, then you can log on using your AD user account and credentials.  The user account is in the form domain\username, for example, soundtraining\doncrawley.

Here's a [link to a YouTube video]("http://www.youtube.com/watch?v=TwKhR7t___A") demonstrating how to do it, except that he downloads the packages from their site.  You can just use apt-get or aptitude to install it directly from the Ubuntu repository.

---

### Post by CAEman on 2010-04-09
Thanks. 
But how is it possible "to join the Ubuntu computer to the AD domain" having only such account on a server?

---

### Post by kfsone on 2010-04-15
Just installed a fresh 9.10 server, did the following:

$ sudo apt-get -y install likewise-open5
...
$ sudo vi /etc/nsswitch.conf
[ put dns ahead of m4 ]
$ sudo domainjoin-cli join CRS.local $USER $PASS
[ joined ]
$ sudo reboot
[ reboot, relogin ]
$ ls /etc/samba
ls: cannot access /etc/samba: No such file or directory

I can login as username@CRS, but I want to make CRS the default domain.

So I tried enabling "assume-default-domain" in /etc/likewise-open/lsassd.conf ... restarted likewise-open5. Didn't work.

I tried

$ sudo apt-get -y install samba

Rebooted, still no /etc/samba/lwiauthd.conf,
still no default domain.

---

### Post by CAEman on 2010-04-16
Try to add in /etc/ldap.conf:
host [ldap server IP address]
base dc=[domain]
 
And appropriate configuration of pam.

---

### Post by guimenez on 2010-09-23
Please, i need help

i've successfully join ubuntu 10.04 to 2008 active directory.
now i need every time a user login, it will map a is shared folder from server

i've 2 groups: basic and medium

if i login with a user that as basic group it will mount is shared folder from server.

my server as this folder structure:

2008server
       |
       |----- basic
       |                |
       |                |- basic_user (shared)
       |
       |----- medium
                         |
                         |- medium_user (shared)

i've try smb://2008server/'%g'/'%u'

but nothing

hope someone help me on this

thanks

---

### Post by kinitsu on 2010-10-06
What do you guys have on

>  root@proxy:~# net ads join -U domain admin
Enter domain admin's password:
Using short domain name -- domain
Joined 'mycomputer' to realm 'mydomain.local'
DNS update failed!when I check the AD to see if "mycomputer" account was created, it wasn't.

---

### Post by upallnight on 2010-12-09
Likewise Open is the easiest complete solution for Linux workstations to authenticate to an Active Directory domain. I wish I had found it sooner.
The likewise-open package in the Ubuntu repo works fine, but I found the install script from:
[http://www.likewise.com/products/likewise_open/](http://www.likewise.com/products/likewise_open/)
has some new features.

Its really as simple as typing the AD domain then logging in with an account that has permission to manage the Domain. Then test it by logging in with an AD account on your local machine:
```
ssh example\\steve@localhost
```

For Ubuntu help on Likewise Open see
[https://help.ubuntu.com/8.04/serverguide/C/likewise-open.html](https://help.ubuntu.com/8.04/serverguide/C/likewise-open.html)
or
[https://help.ubuntu.com/community/LikewiseOpen](https://help.ubuntu.com/community/LikewiseOpen)

---

### Post by C Morris on 2012-06-12
I followed the instructions down to step 6, then I realized DNS was misconfigured so it wasn't working.  Unfortunately, I got called away and due to the idle time my ssh session was lost.  So now I can't log in.  Is this installation totally hosed now?

---

### Post by snake2903 on 2012-11-02
This is great tutorial but i have questions.

In my company we have 3 server for our domain, example:

Our domain name:    INT.COMPANY.COM

3 servers that give as above domain name:

dc-1.int.company.com     this is main server
dc-2.int.company.com
dc-3.int.company.com

Is this good configuration of krb5.conf file for my situation:

```

[logging] 
default = FILE10000:/var/log/krb5lib.log     

[libdefaults]          
ticket_lifetime = 24000          
default_realm = INT.COMPANY.COM 
         default_tkt_enctypes = des3-hmac-sha1 des-cbc-crc 
         default_tgs_enctypes = des3-hmac-sha1 des-cbc-crc

[realms] 
INT.COMPANY.COM = 
{ 
   kdc = dc-1.int.company.com
   kdc = dc-2.int.company.com 
   kdc = dc-3.int.company.com
   admin_server = dc-1.int.company.com
   master_kdc = dc-1.int.company.com     
   default_domain = INT.COMPANY.COM          
}

 [domain_realm]
 .domain.local = INT.COMPANY.COM         
  domain.local = INT.COMPANY.COM 


```The part that is confusing me is:
Is it good that i defined my main domain server as master_kdc?
Do i need define admin_server for secondary domain servers (dc-2 and dc-3 ) so it looks like this?
```

admin_server = dc1.int.company.com
admin_server = dc2.int.company.com
admin_server = dc3.int.company.com

```Will this configuration automatically switch me to secondary kdc if kdc1 crash?

And this is my smb.conf file how i think it should be configured

```

[global]
workgroup = INT
realm = INT.COMPANY.COM
#netbios name = computer_name
server string = %h server (Samba %v, Ubuntu)
dns proxy = no
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
security = ADS
domain master = no
idmap uid = 10000-20000
idmap gid = 10000-20000
template shell = /bin/bash
template homedir = /home/%D/%U
winbind enum groups = yes
winbind enum users = yes
winbind use default domain = yes
usershare allow guests = yes


```Do i need in smb.conf file add this lines because we have multiple servers for same domain and one is master server?

password server = dc1.int.company.com
domain master = dc1.int.company.com?

I hope you understand me :smile:

---

### Post by guido24 on 2013-06-28
For the memory on the internet:

net ads join -U Administrator@...

was also extremely slow on my Linux box. Using:

net ads join -U Administrator@... -d 10

I was able to conclude that deleting an entry in the kerberos memory (krb5.keytab) did not progress obviously. I deleted the krb5.keytab, did another kinit, problem solved.

Please note that other essential information may be present in your krb5.keytab, so be carefull.

---

### Post by ikki_72 on 2013-10-03
for a AD with hostname ad00.comp.local

where would i need to reconfigure?

```
user1@ubuntu:~$ cat /etc/samba/smb.conf
# Global parameters
[global]
workgroup = COMP.LOCAL
realm = COMP.LOCAL
preferred master = no
server string = Samba file and print server
security = ADS
encrypt passwords = yes
log level = 3
log file = /var/log/samba/%m
max log size = 50
winbind separator = +
printcap name = cups
printing = cups
idmap uid = 10000-20000
idmap gid = 10000-20000

[homes]
comment = Home Directories
valid users = %S
read only = No
browseable = No

[printers]
comment = All Printers
browseable = no
printable = yes
guest ok = yes
```

```
user1@ubuntu:~$ sudo net ads join -U Administrator@COMP.LOCAL -d 10
INFO: Current debug levels:
  all: 10
  tdb: 10
  printdrivers: 10
  lanman: 10
  smb: 10
  rpc_parse: 10
  rpc_srv: 10
  rpc_cli: 10
  passdb: 10
  sam: 10
  auth: 10
  winbind: 10
  vfs: 10
  idmap: 10
  quota: 10
  acls: 10
  locking: 10
  msdfs: 10
  dmapi: 10
  registry: 10
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
INFO: Current debug levels:
  all: 10
  tdb: 10
  printdrivers: 10
  lanman: 10
  smb: 10
  rpc_parse: 10
  rpc_srv: 10
  rpc_cli: 10
  passdb: 10
  sam: 10
  auth: 10
  winbind: 10
  vfs: 10
  idmap: 10
  quota: 10
  acls: 10
  locking: 10
  msdfs: 10
  dmapi: 10
  registry: 10
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
doing parameter workgroup = COMP.LOCAL
doing parameter realm = COMP.LOCAL
doing parameter preferred master = no
doing parameter server string = Samba file and print server
doing parameter security = ADS
doing parameter encrypt passwords = yes
doing parameter log level = 3
doing parameter log file = /var/log/samba/%m
doing parameter max log size = 50
doing parameter winbind separator = +
doing parameter printcap name = cups
doing parameter printing = cups
doing parameter idmap uid = 10000-20000
WARNING: The "idmap uid" option is deprecated
doing parameter idmap gid = 10000-20000
WARNING: The "idmap gid" option is deprecated
pm_process() returned Yes
lp_servicenumber: couldn't find homes
set_server_role: role = ROLE_DOMAIN_MEMBER
Substituting charset 'ANSI_X3.4-1968' for LOCALE
Netbios name list:-
my_netbios_names[0]="UBUNTU"
added interface eth0 ip=fe80::250:56ff:feb1:34f4%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=10.0.0.210 bcast=10.0.0.255 netmask=255.255.255.0
Registered MSG_REQ_POOL_USAGE
Registered MSG_REQ_DMALLOC_MARK and LOG_CHANGED
Enter Administrator@COMP.LOCAL's password:
libnet_Join:
    libnet_JoinCtx: struct libnet_JoinCtx
        in: struct libnet_JoinCtx
            dc_name                  : NULL
            machine_name             : 'UBUNTU'
            domain_name              : *
                domain_name              : 'COMP.LOCAL'
            account_ou               : NULL
            admin_account            : 'Administrator@COMP.LOCAL'
            machine_password         : NULL
            join_flags               : 0x00000023 (35)
                   0: WKSSVC_JOIN_FLAGS_IGNORE_UNSUPPORTED_FLAGS
                   0: WKSSVC_JOIN_FLAGS_JOIN_WITH_NEW_NAME
                   0: WKSSVC_JOIN_FLAGS_JOIN_DC_ACCOUNT
                   0: WKSSVC_JOIN_FLAGS_DEFER_SPN
                   0: WKSSVC_JOIN_FLAGS_MACHINE_PWD_PASSED
                   0: WKSSVC_JOIN_FLAGS_JOIN_UNSECURE
                   1: WKSSVC_JOIN_FLAGS_DOMAIN_JOIN_IF_JOINED
                   0: WKSSVC_JOIN_FLAGS_WIN9X_UPGRADE
                   0: WKSSVC_JOIN_FLAGS_ACCOUNT_DELETE
                   1: WKSSVC_JOIN_FLAGS_ACCOUNT_CREATE
                   1: WKSSVC_JOIN_FLAGS_JOIN_TYPE
            os_version               : NULL
            os_name                  : NULL
            create_upn               : 0x00 (0)
            upn                      : NULL
            modify_config            : 0x00 (0)
            ads                      : NULL
            debug                    : 0x01 (1)
            use_kerberos             : 0x00 (0)
            secure_channel_type      : SEC_CHAN_WKSTA (2)
dsgetdcname: domain_name: COMP.LOCAL, domain_guid: (null), site_name: (null), flags: 0x40001011
debug_dsdcinfo_flags: 0x40001011
	DS_FORCE_REDISCOVERY DS_DIRECTORY_SERVICE_REQUIRED DS_WRITABLE_REQUIRED DS_RETURN_DNS_NAME 
Opening cache file at /var/run/samba/gencache.tdb
Opening cache file at /var/run/samba/gencache_notrans.tdb
sitename_fetch: Returning sitename for COMP.LOCAL: "Default-First-Site-Name"
dsgetdcname_rediscover
ads_dns_lookup_srv: 1 records returned in the answer section.
ads_dns_parse_rr_srv: Parsed AD00.COMP.LOCAL [0, 100, 389]
LDAP ping to AD00.COMP.LOCAL
interpret_string_addr_internal: getaddrinfo failed for name AD00.COMP.LOCAL [Name or service not known]
Failed to resolve[AD00.COMP.LOCAL] into an address for cldap
internal_resolve_name: looking up COMP.LOCAL#1c (sitename (null))
no entry for COMP.LOCAL#1C found.
resolve_lmhosts: Attempting lmhosts lookup for name COMP.LOCAL<0x1c>
resolve_lmhosts: Attempting lmhosts lookup for name COMP.LOCAL<0x1c>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: Attempting wins lookup for name COMP.LOCAL<0x1c>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name COMP.LOCAL<0x1c>
bind succeeded on port 0
Socket options:
	SO_KEEPALIVE = 0
	SO_REUSEADDR = 1
	SO_BROADCAST = 1
	Could not test socket option TCP_NODELAY.
	Could not test socket option TCP_KEEPCNT.
	Could not test socket option TCP_KEEPIDLE.
	Could not test socket option TCP_KEEPINTVL.
	IPTOS_LOWDELAY = 0
	IPTOS_THROUGHPUT = 0
	SO_SNDBUF = 229376
	SO_RCVBUF = 229376
	SO_SNDLOWAT = 1
	SO_RCVLOWAT = 1
	SO_SNDTIMEO = 0
	SO_RCVTIMEO = 0
	Could not test socket option TCP_QUICKACK.
Running timed event "tevent_req_timedout" 0x7f7c2b915a50
discover_dc_netbios: failed to find DC
libnet_Join:
    libnet_JoinCtx: struct libnet_JoinCtx
        out: struct libnet_JoinCtx
            account_name             : NULL
            netbios_domain_name      : NULL
            dns_domain_name          : NULL
            forest_name              : NULL
            dn                       : NULL
            domain_sid               : NULL
                domain_sid               : (NULL SID)
            modified_config          : 0x00 (0)
            error_string             : 'failed to find DC for domain COMP.LOCAL'
            domain_is_ad             : 0x00 (0)
            result                   : WERR_DCNOTFOUND
libnet_Join:
    libnet_JoinCtx: struct libnet_JoinCtx
        in: struct libnet_JoinCtx
            dc_name                  : NULL
            machine_name             : 'UBUNTU'
            domain_name              : *
                domain_name              : 'COMP.LOCAL'
            account_ou               : NULL
            admin_account            : 'Administrator@COMP.LOCAL'
            machine_password         : NULL
            join_flags               : 0x00000023 (35)
                   0: WKSSVC_JOIN_FLAGS_IGNORE_UNSUPPORTED_FLAGS
                   0: WKSSVC_JOIN_FLAGS_JOIN_WITH_NEW_NAME
                   0: WKSSVC_JOIN_FLAGS_JOIN_DC_ACCOUNT
                   0: WKSSVC_JOIN_FLAGS_DEFER_SPN
                   0: WKSSVC_JOIN_FLAGS_MACHINE_PWD_PASSED
                   0: WKSSVC_JOIN_FLAGS_JOIN_UNSECURE
                   1: WKSSVC_JOIN_FLAGS_DOMAIN_JOIN_IF_JOINED
                   0: WKSSVC_JOIN_FLAGS_WIN9X_UPGRADE
                   0: WKSSVC_JOIN_FLAGS_ACCOUNT_DELETE
                   1: WKSSVC_JOIN_FLAGS_ACCOUNT_CREATE
                   1: WKSSVC_JOIN_FLAGS_JOIN_TYPE
            os_version               : NULL
            os_name                  : NULL
            create_upn               : 0x00 (0)
            upn                      : NULL
            modify_config            : 0x00 (0)
            ads                      : NULL
            debug                    : 0x01 (1)
            use_kerberos             : 0x00 (0)
            secure_channel_type      : SEC_CHAN_WKSTA (2)
dsgetdcname: domain_name: COMP.LOCAL, domain_guid: (null), site_name: (null), flags: 0x40001011
debug_dsdcinfo_flags: 0x40001011
	DS_FORCE_REDISCOVERY DS_DIRECTORY_SERVICE_REQUIRED DS_WRITABLE_REQUIRED DS_RETURN_DNS_NAME 
sitename_fetch: Returning sitename for COMP.LOCAL: "Default-First-Site-Name"
dsgetdcname_rediscover
ads_dns_lookup_srv: 1 records returned in the answer section.
ads_dns_parse_rr_srv: Parsed AD00.COMP.LOCAL [0, 100, 389]
LDAP ping to AD00.COMP.LOCAL
interpret_string_addr_internal: getaddrinfo failed for name AD00.COMP.LOCAL [Name or service not known]
Failed to resolve[AD00.COMP.LOCAL] into an address for cldap
internal_resolve_name: looking up COMP.LOCAL#1c (sitename (null))
no entry for COMP.LOCAL#1C found.
resolve_lmhosts: Attempting lmhosts lookup for name COMP.LOCAL<0x1c>
resolve_lmhosts: Attempting lmhosts lookup for name COMP.LOCAL<0x1c>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: Attempting wins lookup for name COMP.LOCAL<0x1c>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name COMP.LOCAL<0x1c>
bind succeeded on port 0
Socket options:
	SO_KEEPALIVE = 0
	SO_REUSEADDR = 1
	SO_BROADCAST = 1
	Could not test socket option TCP_NODELAY.
	Could not test socket option TCP_KEEPCNT.
	Could not test socket option TCP_KEEPIDLE.
	Could not test socket option TCP_KEEPINTVL.
	IPTOS_LOWDELAY = 0
	IPTOS_THROUGHPUT = 0
	SO_SNDBUF = 229376
	SO_RCVBUF = 229376
	SO_SNDLOWAT = 1
	SO_RCVLOWAT = 1
	SO_SNDTIMEO = 0
	SO_RCVTIMEO = 0
	Could not test socket option TCP_QUICKACK.
Running timed event "tevent_req_timedout" 0x7f7c2b916330
discover_dc_netbios: failed to find DC
libnet_Join:
    libnet_JoinCtx: struct libnet_JoinCtx
        out: struct libnet_JoinCtx
            account_name             : NULL
            netbios_domain_name      : NULL
            dns_domain_name          : NULL
            forest_name              : NULL
            dn                       : NULL
            domain_sid               : NULL
                domain_sid               : (NULL SID)
            modified_config          : 0x00 (0)
            error_string             : 'failed to find DC for domain COMP.LOCAL'
            domain_is_ad             : 0x00 (0)
            result                   : WERR_DCNOTFOUND
lang_tdb_init: /usr/share/samba/en_US:en.msg: No such file or directory
Failed to join domain: failed to find DC for domain COMP.LOCAL
return code = -1
```

weirdly, I can ping via hostname only but not fqdn


```
user1@ubuntu:~$ ping AD00
PING AD00.COMP.LOCAL (10.0.0.229) 56(84) bytes of data.
64 bytes from 10.0.0.229: icmp_req=1 ttl=128 time=0.281 ms
64 bytes from 10.0.0.229: icmp_req=2 ttl=128 time=0.343 ms
^C64 bytes from 10.0.0.229: icmp_req=3 ttl=128 time=0.340 ms

--- AD00.COMP.LOCAL ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 10009ms
rtt min/avg/max/mdev = 0.281/0.321/0.343/0.032 ms
user1@ubuntu:~$ ping AD00.COMP.LOCAL
ping: unknown host AD00.COMP.LOCAL
```

---

