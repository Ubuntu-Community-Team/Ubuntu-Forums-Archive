---
title: "What to do when being hacked?"
date: 2010-08-10
forum: Security
---

### Post by jrobot on 2010-08-10
I got a static dyndns.org address and enabled ssh and sftp on my machine so that I could access it remotely. I also created a new user account and locked it in a jail with jailkit (I'm a hobbyist FX artist and need to share large files with third parties).

Today I happened to be looking at my auth.log file with gedit when it suddenly started changing rapidly - displaying multiple login attempts with random usernames that look like they are being generated from a dictionary file. Needless to say, I freaked out a bit, instantly changed my router settings so that it no longer forwarded anything to port 22 on my machine, and took my static ip offline.

Excerpt from beginning of attack:
```

Aug  9 22:25:23 **COMPUTER_NAME** sshd[3991]: Invalid user nagios from 201.71.131.4
Aug  9 22:25:23 **COMPUTER_NAME** sshd[3991]: pam_unix(sshd:auth): check pass; user unknown
Aug  9 22:25:23 **COMPUTER_NAME** sshd[3991]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201-71-131-4-arpa.vsp.com.br 
Aug  9 22:25:23 **COMPUTER_NAME** sshd[3991]: pam_winbind(sshd:auth): getting password (0x00000388)
Aug  9 22:25:23 **COMPUTER_NAME** sshd[3991]: pam_winbind(sshd:auth): pam_get_item returned a password
Aug  9 22:25:25 **COMPUTER_NAME** sshd[3991]: Failed password for invalid user nagios from 201.71.131.4 port 42829 ssh2
Aug  9 22:25:27 **COMPUTER_NAME** sshd[3995]: Invalid user hadoop from 201.71.131.4
Aug  9 22:25:27 **COMPUTER_NAME** sshd[3995]: pam_unix(sshd:auth): check pass; user unknown
Aug  9 22:25:27 **COMPUTER_NAME** sshd[3995]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201-71-131-4-arpa.vsp.com.br 
Aug  9 22:25:27 **COMPUTER_NAME** sshd[3995]: pam_winbind(sshd:auth): getting password (0x00000388)
Aug  9 22:25:27 **COMPUTER_NAME** sshd[3995]: pam_winbind(sshd:auth): pam_get_item returned a password
Aug  9 22:25:29 **COMPUTER_NAME** sshd[3995]: Failed password for invalid user hadoop from 201.71.131.4 port 43075 ssh2
Aug  9 22:25:31 **COMPUTER_NAME** sshd[3997]: Invalid user kiosk from 201.71.131.4
Aug  9 22:25:31 **COMPUTER_NAME** sshd[3997]: pam_unix(sshd:auth): check pass; user unknown
Aug  9 22:25:31 **COMPUTER_NAME** sshd[3997]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201-71-131-4-arpa.vsp.com.br 
Aug  9 22:25:31 **COMPUTER_NAME** sshd[3997]: pam_winbind(sshd:auth): getting password (0x00000388)
Aug  9 22:25:31 **COMPUTER_NAME** sshd[3997]: pam_winbind(sshd:auth): pam_get_item returned a password
Aug  9 22:25:33 **COMPUTER_NAME** sshd[3997]: Failed password for invalid user kiosk from 201.71.131.4 port 43315 ssh2
Aug  9 22:25:35 **COMPUTER_NAME** sshd[3999]: Invalid user postgres from 201.71.131.4
Aug  9 22:25:35 **COMPUTER_NAME** sshd[3999]: pam_unix(sshd:auth): check pass; user unknown
Aug  9 22:25:35 **COMPUTER_NAME** sshd[3999]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201-71-131-4-arpa.vsp.com.br 
Aug  9 22:25:35 **COMPUTER_NAME** sshd[3999]: pam_winbind(sshd:auth): getting password (0x00000388)
Aug  9 22:25:35 **COMPUTER_NAME** sshd[3999]: pam_winbind(sshd:auth): pam_get_item returned a password
Aug  9 22:25:37 **COMPUTER_NAME** sshd[3999]: Failed password for invalid user postgres from 201.71.131.4 port 43558 ssh2
Aug  9 22:25:39 **COMPUTER_NAME** sshd[4002]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201-71-131-4-arpa.vsp.com.br  user=root
Aug  9 22:25:39 **COMPUTER_NAME** sshd[4002]: pam_winbind(sshd:auth): getting password (0x00000388)
Aug  9 22:25:39 **COMPUTER_NAME** sshd[4002]: pam_winbind(sshd:auth): pam_get_item returned a password
Aug  9 22:25:39 **COMPUTER_NAME** sshd[4002]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Aug  9 22:25:41 **COMPUTER_NAME** sshd[4002]: Failed password for root from 201.71.131.4 port 43825 ssh2
Aug  9 22:25:42 **COMPUTER_NAME** sshd[4004]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201-71-131-4-arpa.vsp.com.br  user=root
Aug  9 22:25:42 **COMPUTER_NAME** sshd[4004]: pam_winbind(sshd:auth): getting password (0x00000388)
Aug  9 22:25:42 **COMPUTER_NAME** sshd[4004]: pam_winbind(sshd:auth): pam_get_item returned a password
Aug  9 22:25:42 **COMPUTER_NAME** sshd[4004]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Aug  9 22:25:44 **COMPUTER_NAME** sshd[4004]: Failed password for root from 201.71.131.4 port 44082 ssh2

```

Excerpt from end of attack:
```

Aug 10 15:52:27 **COMPUTER_NAME** sshd[3978]: Invalid user sites3 from 61.31.200.194
Aug 10 15:52:27 **COMPUTER_NAME** sshd[3978]: pam_unix(sshd:auth): check pass; user unknown
Aug 10 15:52:27 **COMPUTER_NAME** sshd[3978]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61-31-200-194.static.tfn.net.tw 
Aug 10 15:52:27 **COMPUTER_NAME** sshd[3978]: pam_winbind(sshd:auth): getting password (0x00000388)
Aug 10 15:52:27 **COMPUTER_NAME** sshd[3978]: pam_winbind(sshd:auth): pam_get_item returned a password
Aug 10 15:52:29 **COMPUTER_NAME** sshd[3978]: Failed password for invalid user sites3 from 61.31.200.194 port 46403 ssh2
Aug 10 15:52:31 **COMPUTER_NAME** sshd[3980]: Invalid user sites4 from 61.31.200.194
Aug 10 15:52:31 **COMPUTER_NAME** sshd[3980]: pam_unix(sshd:auth): check pass; user unknown
Aug 10 15:52:31 **COMPUTER_NAME** sshd[3980]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61-31-200-194.static.tfn.net.tw 
Aug 10 15:52:31 **COMPUTER_NAME** sshd[3980]: pam_winbind(sshd:auth): getting password (0x00000388)
Aug 10 15:52:31 **COMPUTER_NAME** sshd[3980]: pam_winbind(sshd:auth): pam_get_item returned a password
Aug 10 15:52:33 **COMPUTER_NAME** sshd[3980]: Failed password for invalid user sites4 from 61.31.200.194 port 47263 ssh2
Aug 10 15:52:35 **COMPUTER_NAME** sshd[3983]: Invalid user sites5 from 61.31.200.194
Aug 10 15:52:35 **COMPUTER_NAME** sshd[3983]: pam_unix(sshd:auth): check pass; user unknown
Aug 10 15:52:35 **COMPUTER_NAME** sshd[3983]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61-31-200-194.static.tfn.net.tw 
Aug 10 15:52:35 **COMPUTER_NAME** sshd[3983]: pam_winbind(sshd:auth): getting password (0x00000388)
Aug 10 15:52:35 **COMPUTER_NAME** sshd[3983]: pam_winbind(sshd:auth): pam_get_item returned a password
Aug 10 15:52:37 **COMPUTER_NAME** sshd[3983]: Failed password for invalid user sites5 from 61.31.200.194 port 48068 ssh2
Aug 10 15:52:39 **COMPUTER_NAME** sshd[3985]: Invalid user sites6 from 61.31.200.194
Aug 10 15:52:39 **COMPUTER_NAME** sshd[3985]: pam_unix(sshd:auth): check pass; user unknown
Aug 10 15:52:39 **COMPUTER_NAME** sshd[3985]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61-31-200-194.static.tfn.net.tw 
Aug 10 15:52:39 **COMPUTER_NAME** sshd[3985]: pam_winbind(sshd:auth): getting password (0x00000388)
Aug 10 15:52:39 **COMPUTER_NAME** sshd[3985]: pam_winbind(sshd:auth): pam_get_item returned a password
Aug 10 15:52:41 **COMPUTER_NAME** sshd[3985]: Failed password for invalid user sites6 from 61.31.200.194 port 48956 ssh2
Aug 10 15:52:43 **COMPUTER_NAME** sshd[3988]: Invalid user sites7 from 61.31.200.194
Aug 10 15:52:43 **COMPUTER_NAME** sshd[3988]: pam_unix(sshd:auth): check pass; user unknown
Aug 10 15:52:43 **COMPUTER_NAME** sshd[3988]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61-31-200-194.static.tfn.net.tw 
Aug 10 15:52:43 **COMPUTER_NAME** sshd[3988]: pam_winbind(sshd:auth): getting password (0x00000388)
Aug 10 15:52:43 **COMPUTER_NAME** sshd[3988]: pam_winbind(sshd:auth): pam_get_item returned a password
Aug 10 15:52:44 **COMPUTER_NAME** sshd[3988]: Failed password for invalid user sites7 from 61.31.200.194 port 49814 ssh2
Aug 10 15:52:46 **COMPUTER_NAME** sshd[3990]: Invalid user sites8 from 61.31.200.194
Aug 10 15:52:46 **COMPUTER_NAME** sshd[3990]: pam_unix(sshd:auth): check pass; user unknown
Aug 10 15:52:46 **COMPUTER_NAME** sshd[3990]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61-31-200-194.static.tfn.net.tw 
Aug 10 15:52:46 **COMPUTER_NAME** sshd[3990]: pam_winbind(sshd:auth): getting password (0x00000388)
Aug 10 15:52:46 **COMPUTER_NAME** sshd[3990]: pam_winbind(sshd:auth): pam_get_item returned a password
Aug 10 15:52:48 **COMPUTER_NAME** sshd[3990]: Failed password for invalid user sites8 from 61.31.200.194 port 50612 ssh2
Aug 10 15:52:51 **COMPUTER_NAME** sshd[3993]: Invalid user sites9 from 61.31.200.194
Aug 10 15:52:51 **COMPUTER_NAME** sshd[3993]: pam_unix(sshd:auth): check pass; user unknown
Aug 10 15:52:51 **COMPUTER_NAME** sshd[3993]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61-31-200-194.static.tfn.net.tw 
Aug 10 15:52:51 **COMPUTER_NAME** sshd[3993]: pam_winbind(sshd:auth): getting password (0x00000388)
Aug 10 15:52:51 **COMPUTER_NAME** sshd[3993]: pam_winbind(sshd:auth): pam_get_item returned a password
Aug 10 15:52:52 **COMPUTER_NAME** sshd[3993]: Failed password for invalid user sites9 from 61.31.200.194 port 51510 ssh2
Aug 10 15:52:54 **COMPUTER_NAME** sshd[3996]: Invalid user sites10 from 61.31.200.194
Aug 10 15:52:54 **COMPUTER_NAME** sshd[3996]: pam_unix(sshd:auth): check pass; user unknown
Aug 10 15:52:54 **COMPUTER_NAME** sshd[3996]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61-31-200-194.static.tfn.net.tw 
Aug 10 15:52:54 **COMPUTER_NAME** sshd[3996]: pam_winbind(sshd:auth): getting password (0x00000388)
Aug 10 15:52:54 **COMPUTER_NAME** sshd[3996]: pam_winbind(sshd:auth): pam_get_item returned a password
Aug 10 15:52:57 **COMPUTER_NAME** sshd[3996]: Failed password for invalid user sites10 from 61.31.200.194 port 52361 ssh2

```

At one point, the dictionary attack actually guessed my username but kept going afterwards:
```

Aug 10 01:38:01 **COMPUTER_NAME** sshd[9949]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=203-144-218-154.static.asianet.co.th  user=*MY_USER_NAME* 
Aug 10 01:38:01 **COMPUTER_NAME** sshd[9949]: pam_winbind(sshd:auth): getting password (0x00000388)
Aug 10 01:38:01 **COMPUTER_NAME** sshd[9949]: pam_winbind(sshd:auth): pam_get_item returned a password
Aug 10 01:38:01 **COMPUTER_NAME** sshd[9949]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Aug 10 01:38:03 **COMPUTER_NAME** sshd[9949]: Failed password for *MY_USER_NAME* from 203.144.218.154 port 35489 ssh2

```

I ran a whois:
```

$ whois 61.31.200.194
#
# Query terms are ambiguous.  The query is assumed to be:
#     "n 61.31.200.194"
#
# Use "?" to get help.
#

#
# The following results may also be obtained via:
# http://whois.arin.net/rest/nets;q=61.31.200.194?showDetails=true&showARIN=false
#

NetRange:       61.0.0.0 - 61.255.255.255
CIDR:           61.0.0.0/8
OriginAS:
NetName:        APNIC3
NetHandle:      NET-61-0-0-0-1
Parent:
NetType:        Allocated to APNIC
NameServer:     TINNIE.ARIN.NET
NameServer:     SEC1.AUTHDNS.RIPE.NET
NameServer:     NS4.APNIC.NET
NameServer:     NS3.APNIC.NET
NameServer:     NS1.APNIC.NET
NameServer:     NS2.LACNIC.NET
Comment:        This IP address range is not registered in the ARIN database.
Comment:        For details, refer to the APNIC Whois Database via
Comment:        WHOIS.APNIC.NET or http://wq.apnic.net/apnic-bin/whois.pl
Comment:        ** IMPORTANT NOTE: APNIC is the Regional Internet Registry
Comment:        for the Asia Pacific region. APNIC does not operate networks
Comment:        using this IP address range and is not able to investigate
Comment:        spam or abuse reports relating to these addresses. For more
Comment:        help, refer to http://www.apnic.net/apnic-info/whois_search2/abuse-and-spamming
RegDate:        1997-04-25
Updated:        2010-07-30
Ref:            http://whois.arin.net/rest/net/NET-61-0-0-0-1

OrgName:        Asia Pacific Network Information Centre
OrgId:          APNIC
Address:        PO Box 2131
City:           Milton
StateProv:      QLD
PostalCode:     4064
Country:        AU
RegDate:
Updated:        2004-03-01
Ref:            http://whois.arin.net/rest/org/APNIC

ReferralServer: whois://whois.apnic.net

OrgTechHandle: AWC12-ARIN
OrgTechName:   APNIC Whois Contact
OrgTechPhone:  +61 7 3858 3188
OrgTechEmail:  search-apnic-not-arin@apnic.net
OrgTechRef:    http://whois.arin.net/rest/poc/AWC12-ARIN

#
# ARIN WHOIS data and services are subject to the Terms of Use
# available at: https://www.arin.net/whois_tou.html
#

% [whois.apnic.net node-3]
% Whois data copyright terms    http://www.apnic.net/db/dbcopyright.html

inetnum:        61.31.0.0 - 61.31.255.255
netname:        TFN-NET
descr:          Taiwan Fixed Network CO.,LTD.
descr:          7FI., No. 498, Ruei-Guang Rd., Nei-Hu
descr:          Taipei Taiwan 114.
country:        TW
admin-c:        TT164-AP
tech-c:         SH376-AP
mnt-by:         MAINT-TW-TWNIC
changed:        hostmaster@twnic.net.tw 20020425
status:         ALLOCATED PORTABLE
source:         APNIC

person:         Ting Tseng
nic-hdl:        TT164-AP
e-mail:         ting_tseng@twfn.com.tw
address:        7Fl., No. 498, Ruei-Guang Rd., Nei-Hu
address:        Taipei, 114, R.O.C
phone:          +886-2-6606-3836
fax-no:         +886-2-6606-3802
country:        TW
changed:        hostmaster@twnic.net.tw 20051212
mnt-by:         MAINT-TW-TWNIC
source:         APNIC

person:         Steve Huang
address:        Taiwan Fixed Network CO.,LTD.
address:        7FI., No. 498, Ruei-Guang Rd., Nei-Hu
address:        Taipei Taiwan 114
country:        TW
phone:          +886-2-6606-3870
fax-no:         +886-2-6600-1077
e-mail:         steve_huang@howin.com.tw
nic-hdl:        SH376-AP
mnt-by:         MAINT-TW-TWNIC
changed:        hostmaster@twnic.net 20020425
source:         APNIC

```

Port scan of 61.31.200.194 with Network Tools revealed open ports: 21, 22, 3306, 6000, 8080

Also found attacking IPs 61.31.200.194, 203.144.218.154, 203.144.218.154, and many others. Could this be a botnet attack?

What is the purpose of guessing lots of usernames, each with just one or a few password attempts? How can I get this sort of thing to be detected automatically without having the auth.log file open all the time? Do I have anything to worry about when coming online again? Is there an easy way to change my settings so that there is a long pause before a new access attempt can be made? Is there a better solution? If I do that and get attacked, I won't be able to log in myself.

I'm running Ubuntu 10.04 LTS behind a WRT54GL router with firmware v4.30.13.

Thank you in advance for any help you can offer me - I'm a relative newbie when it comes to Linux and networking/security.

---

### Post by Iowan on 2010-08-10
Moved to Security Discussions

---

### Post by cherva on 2010-08-10
There are two things to do
1) Install fail2ban - a program that looks at your logs and ban people that type wrong passwords a specified number of times. It works for ssh,apache2,imap,pop3,ftp.....
2) Open the SSH port just for some IPs that you ssh from ( if this is possible )

---

### Post by hudsonl on 2010-08-10
I would also change your port number to something else other than 22.

Doesn't totally prevent ... but does help a lot ... use some high unused port that you can remember.

Then when connecting to your machine you'll just need to include the port number.

ssh -P xxxx  mymachine.athome.com

---

### Post by Velnias on 2010-08-10
Don't worry, just use key for ssh authentication.

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")

And don't forget to disable ssh password authentication.

Good luck.

---

### Post by rookcifer on 2010-08-10
> **Velnias said:**
> Don't worry, just use key for ssh authentication.

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")

And don't forget to disable ssh password authentication.

Good luck.

I second that.  This will solve all of your ssh brute force problems.

---

### Post by linux18 on 2010-08-10
Ok, using my "1337" (its just 'proxify / ip : port') tools I have isolated what is on the other side of their ip. It appears to be a Chinese site for automatically guessing passwords and phone numbers routed through a danish server. Unless you DOS them (it's china's hackers, you won't make it halfway through a DOS attack) just block the ip 1000 times easier. Also, consider hosting your files on an off site server like mediafire and only host links on your server.

---

### Post by Grenage on 2010-08-10
All good advice; and I second fail2ban.  If you have a web presence, you will always get these automated attacks; most people simply don't see them.

An SSH key is ideal, but not always practical.  If you're not using a key, use a damn good password; alternate ports are a plus, because I imagine that most of these bots are only scanning a few commonly used SSH ports.

---

### Post by Ryan Dwyer on 2010-08-10
I've been running my SSH on a port that isn't 22 for the last two years and I've never had a single login attempt that isn't me.

I also use key based authentication only, but I think I'm being paranoid.

---

### Post by linux18 on 2010-08-10
with a fast connection it only takes a minute to scan the ~65000 ports at an ip address and only a few minutes to scan an entire country for servers connected to a broadband connection. changing ports and passwords won't keep you safe for long. only allow your computer to accept ssh commands from specific ip's and install some of the tools mentioned here to make sure your computer is safe.

---

### Post by Grenage on 2010-08-10
> **Ryan Dwyer said:**
> I've been running my SSH on a port that isn't 22 for the last two years and I've never had a single login attempt that isn't me.

I also use key based authentication only, but I think I'm being paranoid.

Then you are quite fortunate. :)

Keys aren't the mark of paranoia, they're just good sense and practice.

---

### Post by jrobot on 2010-08-10
Wow, thanks for the fast responses. I'm definitely going to change my port and install fail2ban, but as I mentioned before, I do need to allow other people to log in to the jailed account, so I don't think that key authentication would be a practical solution, unless I can enable/disable it for different accounts. Is doing so possible, and if so, how difficult is it?

---

### Post by r+9 on 2010-08-10
I was just reading about a microsoft security analysis that noticed that brute force attacks were trying one password on many accounts to avoid "only so many attempts per hour".
They noticed better security if you reduced password complexity but restricted password reuse among different users.

Anyway that appears to be what you've got there.  Rather exciting, but I imagine frightening for you.

this wasn't the one I read but it's on the same subject.
[http://techreport.com/discussions.x/19305]("http://techreport.com/discussions.x/19305")

---

### Post by needhelppeeps on 2010-08-10
My ssh has not been hacked in 2 years. I do not use password auth but instead use a key. I also limited it to the IPs I remote into from, so someone would have to first compromise a client machine to even try getting to mine.

IMO leaving your ssh wide open to all IPs and relying on a password to protect you is pretty dangerous.

---

### Post by bodhi.zazen on 2010-08-10
Nothing like reading the logs to instill a healthy dose of paranoia.

After running ssh servers for many years I have come to the conclusion that the following is sufficient :

1. Use keys and disable password logins.

2. Do not allow root to ssh in ( /etc/ssh/sshd_config ). Do not use common user names (see below).

3. Specify allowed users in ( /etc/ssh/sshd_config ) .

For #2 and # see man sshd_config Allow / Deny users =)

4. Limit attempts at a password (see man sshd_config)

> AllowUsers ssh_user
DenyUsers admin administrator apache backup nagios oracle root smbuser staff sysadmin web webdav webmaster  
MaxAuthTries 2

You will see a lot of this in the logs :

> User root from 220.178.2.205 not allowed because listed in DenyUsers

5. Leave the port at the default (22) . Changing the port quiets the logs, but does not, IMHO, increase security, and makes it a bit of a hassle to ssh / scp / sftp (you always need to specify the port, lol).

6. Personally I use iptables to drop brute force attacks. 

7. Take care with denyhosts / fail2ban , those services can introduce additional vulnerabilities and lead to a DOS of ssh. If your servers are properly configured these services do not all much.

8. Rather the denyhosts / fail2ban, take a look at tcpwrapper (hosts.deny hosts.allow). These files are very easy to configure and apply to all major services except apache.

---

### Post by jcolyn on 2010-08-10
> **Grenage said:**
> All good advice; and I second fail2ban.  If you have a web presence, you will always get these automated attacks; most people simply don't see them..

Also never use a username or password that can be picked from a dictionary..

Several years ago when I was running an Apache webserver I got these attacks several times a day but never got hacked.

Most come from APnic OR Ripe IP addresses

---

