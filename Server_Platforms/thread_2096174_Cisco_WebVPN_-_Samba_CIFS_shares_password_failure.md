---
title: "Cisco WebVPN - Samba CIFS shares password failure"
date: 2012-12-19
forum: Server Platforms
---

### Post by leeplastic on 2012-12-19
Hello,
 
I am having trouble accessing shares via clientless SSL VPN.
I have a Cisco ASA 5505 running 8.4(4)1
The share is on on Ubuntu server 11.04 running Samba 3.5.8
 
I appreciate this may not be strictly an Ubuntu issue and it seems to be an interoperbility issue between ASA and Samba. Or simply the smb.conf configuration.. but I'm not really a Linux engineer and my background is networking so I could be completely missing the point!
 
I suspect the issue is down to the interpretation of Lanman on the ASA as I know the usernames and passwords work correctly when accesing the shares from other platforms (Windows Vista and Ubuntu desktop 12.04)
 
When monitoring the Samba logs I get the following errors: (amongst others)

```

tail -f /var/log/samba/log.fw | grep testuser
ntlm_password_check: NT MD4 password check failed for user testuser
  Storing account testuser with RID 1000
  check_ntlm_password: sam authentication for user [testuser] FAILED with error NT_STATUS_WRONG_PASSWORD
  check_ntlm_password:  Authentication for user [testuser] -> [testuser] FAILED with error NT_STATUS_WRONG_PASSWORD
 
 
ntlm_password_check: NO LanMan password set for user testuser (and no NT password supplied)
  ntlm_password_check: LM password, NT MD4 password in LM field and LMv2 failed for user testuser
  Storing account testuser with RID 1000
  check_ntlm_password: sam authentication for user [testuser] FAILED with error NT_STATUS_WRONG_PASSWORD
  check_ntlm_password:  Authentication for user [testuser] -> [testuser] FAILED with error NT_STATUS_WRONG_PASSWORD

```
 
I know a password is set and sent to the server as I've seen the hashed password in a packet capture, I'm just not sure if the hash used by the ASA is one that is expected by Samba.
 
The ASA also displays the username and password correctly during a debug:

```

FW# CIFS:decoded_url........ [cifs://192.168.1.50/data]
CIFS:decoded_url with macro.. [cifs://192.168.1.50/data]
CIFS:fs........ [cifs]
CIFS:user...... []
CIFS:pass...... []
CIFS:host...... [192.168.1.50]
CIFS:path...... [/data]
CIFS:URL=[]; browsing = [no]
CIFS:fs........ [cifs]
CIFS:user...... []
CIFS:pass...... []
CIFS:host...... [192.168.1.50]
CIFS:path...... [/data]
CIFS: getcredentials (host=[192.168.1.50]; path=[/data])
In lua_session_is_ssoaso_allowed
CIFS: auto_signon_allowed = yes (username=[]; password=[])
CIFS:username=[testuser]; password=[xxxxxx]
netfs_api.c:netfs_mount: resource: //192.168.1.50/data
netfs_api.c:netfs_mount: failed to mount, error: 13
netfs_vnode_reclaim: reclaimable: 0, active: 0%, threshold: 20%, in progress: NO

```
 
/etc/samba/smb.conf - Global settings:
 

```

[global]
        log file = /var/log/samba/log.%m
        log level = 6
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        obey pam restrictions = yes
        map to guest = bad user
        encrypt passwords = true
        passwd program = /usr/bin/passwd %u
        passdb backend = tdbsam
        dns proxy = no
        writeable = yes
        server string = %h server (Samba, Ubuntu)
        unix password sync = yes
        workgroup = WORKGROUP
        os level = 20
        security = share
        syslog = 0
        panic action = /usr/share/samba/panic-action %d
        usershare allow guests = yes
        max log size = 1000
        pam password change = yes
        lanman auth = yes
        ntlm auth = yes
        client lanman auth = yes
        client ntlm auth = yes
        client ntlmv2 auth = yes


```
Any assistance would be greatly appreciated.

---

### Post by leeplastic on 2012-12-27
*bump*
I'm still not having much joy with this..

---

### Post by leeplastic on 2013-01-07
anyone?

---

