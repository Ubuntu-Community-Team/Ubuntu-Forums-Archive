---
title: "Howto Add Linux client to SAMBA domain"
date: 2014-03-26
forum: Tutorials
---

### Post by TheHesser on 2014-03-26
Hello all,

I was looking to add a Ubuntu 12.04 machine to our existing SAMBA domain. I am not sure how our domain is setup because I work for a International Charity and they had it installed before I came as the IT administrator. :roll:

I found a few different ones and messed up the installation twice so I thought to post the one that worked for me! It is the manual on the Clear Foundation website but I think they left out one important detail.

You will need to ensure that you have connectivity to the Internet for this installation. Log in to the workstation and let's get started.
If security is a high concern and your workstation will never leave the environment, you may specifically NOT want it to used cached credentials.
[B]
Install needed packages[/B]
1.         We will need a command line for most of this stuff. Open the terminal application under Applications » Accesories » Terminal .
2.         We will be doing a lot of configuration as root. Type the following in the terminal window:
[TABLE]
[TR]
[TD]sudo su -
[/TD]
[/TR]
[/TABLE]
You will be prompted for a password.
Type the following:
[TABLE]
[TR]
[TD]apt-get install winbind samba
[/TD]
[/TR]
[/TABLE]
 
**Change Samba Configuration file**
3.         Add the following lines to the /etc/samba/smb.conf in the [global] section.
[TABLE]
[TR]
[TD]security = domain
netbios name = PC##
password server = [DOMAIN CONTROLLER]
workgroup = [DOMAIN NAME]
idmap uid = 10000000-19999999
idmap gid = 10000000-19999999
winbind use default domain = yes
winbind enum users = no
winbind enum groups = no
winbind use default domain = yes
template shell = /bin/bash
template homedir = /home/%D/%U
domain master = no
winbind enum users = yes
winbind enum groups = yes
add machine script = /usr/sbin/useradd -d /var/lib/nobody -g 100 -s /bin/false
[/TD]
[/TR]
[/TABLE]

Of particular note above, make sure your netbios name, password server, and workgroup parameters match the local machine name which is unique on the network, the DNS name that is resolvable for the ClearOS server, and the Domain name for your ClearOS server respectively.
Find and delete the line that says:
[TABLE]
[TR]
[TD]workgroup = WORKGROUP
[/TD]
[/TR]
[/TABLE]
 
4.         Lastly, run the testparm   command to validate your entries are in the configuration and that it looks good.
 
**Create user folders**
 
5.         Make a directory for your domain users that matches the name of your domain. In this example, our domain is 'IE' so we will run the following:
[TABLE]
[TR]
[TD]mkdir /home/[DOMAIN NAME]
[/TD]
[/TR]
[/TABLE]
 
**Change NS Switch Configuration**
6.         Modify your /etc/nsswitch.conf so that it looks like this:
[TABLE]
[TR]
[TD]passwd:         compat winbind
group:          compat winbind
shadow:         compat winbin
hosts:          files dns wins
networks:       files
protocols:      db files
services:       db files
ethers:         db files
rpc:            db files
netgroup:       nis
[/TD]
[/TR]
[/TABLE]
 
7.         There are several changes to pam.d that will need to change from the default format. There are 4 files that need to be either replaced, edited or modified.
[h=3]common-account[/h]8.         Blow away and replace your /etc/pam.d/common-account file away with the following to command from the shell.
[TABLE]
[TR]
[TD]cp /etc/pam.d/common-account /etc/pam.d/common-account~
echo "account sufficient pam_winbind.so" > /etc/pam.d/common-account
echo "account required pam_unix.so" >> /etc/pam.d/common-account
[/TD]
[/TR]
[/TABLE]
[h=3]common-auth[/h]9.         Blow away and replace your /etc/pam.d/common-auth file away with the following to command from the shell.
[TABLE]
[TR]
[TD]cp /etc/pam.d/common-auth /etc/pam.d/common-auth~
echo "auth sufficient pam_winbind.so" > /etc/pam.d/common-auth
echo "auth required pam_unix.so nullok_secure use_first_pass" >> /etc/pam.d/common-auth
[/TD]
[/TR]
[/TABLE]
[h=3][/h][h=3]common-password[/h]10.     Using vi or your favorite editor, add a snippet to the end of /etc/pam.d/common-password in the line:
[TABLE]
[TR]
[TD]password    [success=2 default=ignore]     pam_unix.so obscure sha512
[/TD]
[/TR]
[/TABLE]

So that it has min=4 max=50
[TABLE]
[TR]
[TD]password    [success=2 default=ignore]     pam_unix.so obscure sha512 min=4 max=50
[/TD]
[/TR]
[/TABLE]
 
[h=3]common-session[/h]11.     Add a entry to the /etc/pam.d/common-session by running the following command:
[TABLE]
[TR]
[TD]echo "session required pam_mkhomedir.so umask=0022 skel=/etc/skel" >> /etc/pam.d/common-session
[/TD]
[/TR]
[/TABLE]
 
With all of these modifications, it is time to reboot the workstation.
[TABLE]
[TR]
[TD]reboot
[/TD]
[/TR]
[/TABLE]
 
**Join the computer to the domain**
12.     Don't forget to login and switch user back to root.
[TABLE]
[TR]
[TD]sudo su -
[/TD]
[/TR]
[/TABLE]
 
13.     Run the following to join the workstation to the domain. Replace the relevant value for the domain name.
[TABLE]
[TR]
[TD]net rpc join -U administrator
[/TD]
[/TR]
[/TABLE]
 
You will be prompted for winadmin's password. Once you supply it you should get the following message:
[TABLE]
[TR]
[TD]Joined domain [NAME].
[/TD]
[/TR]
[/TABLE]
 
14.     Add the domain_users group to the sudoers list by editing the /etc/sudoers
[TABLE]
[TR]
[TD]echo "%allusers ALL=(ALL) ALL" >> /etc/sudoers
[/TD]
[/TR]
[/TABLE]
 
Time to reboot again.
[TABLE]
[TR]
[TD]reboot
[/TD]
[/TR]
[/TABLE]
 
15.     After reboot open a terminal again. Don't forget to login and switch user back to root.
[TABLE]
[TR]
[TD]sudo su -
[/TD]
[/TR]
[/TABLE]
 
16.     Using vi or your favorite editor, add a snippet to the end of /etc/lightdm/lightdm.conf in the line:
[TABLE]
[TR]
[TD]greeter-show-manual-login=true
[/TD]
[/TR]
[/TABLE]
 
17.     Then restart lightdm :
[TABLE]
[TR]
[TD]sudo service lightdm restart[/TD]
[/TR]
[/TABLE]

I hope this manual helps because it has helped me for using computers that didn't have a Windows Licence anymore and install Ubuntu on it!

---

