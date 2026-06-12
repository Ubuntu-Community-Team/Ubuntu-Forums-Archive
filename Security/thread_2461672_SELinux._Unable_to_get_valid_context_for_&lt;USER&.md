---
title: "SELinux. Unable to get valid context for &lt;USER&gt;  but user loged via ssh."
date: 2021-05-05
forum: Security
---

### Post by washide on 2021-05-05
**Hello,**

***Issue:***
-unit : [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e hasn't  started,
-i can log via terminal for user floki uid 1000 ( but problably it shouldn't be possible gog in  in this issuse , for me it is better)
-user have corect context i suppose,
-no AVC errors in audit.log





***System  version:***
```
root@xxx:/var/log# lsb_release  -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.2 LTS
Release:        20.04
Codename:       focal
```


system in graphical target  but it is server edition and i don't use X.
```
floki@xxx:~$  systemctl get-default
graphical.target

```




***Context user:***
```
floki@xxx:~$ id -Z
unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023
```



```
root@xxx:/var/log# systemctl --failed
  UNIT              LOAD   ACTIVE SUB    DESCRIPTION
&#9679; [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e loaded failed failed User Manager for UID 1000
```




```
root@xxx:/home/floki# systemctl status user@1000
&#9679; [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e - User Manager for UID 1000
     Loaded: loaded (/lib/systemd/system/user@.service; static; vendor preset: enabled)
    Drop-In: /usr/lib/systemd/system/user@.service.d
             &#9492;&#9472;timeout.conf
     Active: failed (Result: exit-code) since Wed 2021-05-05 09:52:50 UTC; 42min ago
       Docs: man:user@.service(5)
    Process: 771 ExecStart=/lib/systemd/systemd --user (code=exited, status=224/PAM)
   Main PID: 771 (code=exited, status=224/PAM)
May 05 09:52:50 xxx systemd[771]: pam_selinux(systemd-user:session): Username= floki SELinux User= unconfined_u Level= s0-s0:c0.c1023
May 05 09:52:50 xxx systemd[771]: pam_selinux(systemd-user:session): Unable to get valid context for floki
May 05 09:52:50 xxx systemd[771]: pam_selinux(systemd-user:session): conversation failed
May 05 09:52:50 xxx systemd[771]: pam_unix(systemd-user:session): session opened for user floki by (uid=0)
May 05 09:52:50 xxx systemd[771]: PAM failed: Cannot make/remove an entry for the specified session
May 05 09:52:50 xxx systemd[771]: [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e: Failed to set up PAM session: Operation not permitted
May 05 09:52:50 xxx systemd[771]: [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e: Failed at step PAM spawning /lib/systemd/systemd: Operation not permitted
May 05 09:52:50 xxx systemd[1]: [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e: Main process exited, code=exited, status=224/PAM
May 05 09:52:50 xxx systemd[1]: [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e: Failed with result 'exit-code'.
May 05 09:52:50 xxx systemd[1]: Failed to start User Manager for UID 1000.
```



**Logs:**
-----
**auth.log**


```
May  5 09:52:50 xxx sshd[760]: pam_unix(sshd:session): session opened for user floki by (uid=0)
May  5 09:52:50 xxx systemd-logind[587]: New session 3 of user floki.
May  5 09:52:50 xxx systemd: pam_selinux(systemd-user:session): Open Session
May  5 09:52:50 xxx systemd: pam_selinux(systemd-user:session): Open Session
May  5 09:52:50 xxx systemd: pam_selinux(systemd-user:session): Username= floki SELinux User= unconfined_u Level= s0-s0:c0.c1023
May  5 09:52:50 xxx systemd: pam_selinux(systemd-user:session): Unable to get valid context for floki
May  5 09:52:50 xxx systemd: pam_selinux(systemd-user:session): conversation failed
May  5 09:52:50 xxx systemd: pam_unix(systemd-user:session): session opened for user floki by (uid=0)
May  5 09:52:51 xxx sshd[760]: pam_selinux(sshd:session): Open Session
May  5 09:52:51 xxx sshd[760]: pam_selinux(sshd:session): Username= floki SELinux User= unconfined_u Level= s0-s0:c0.c1023
May  5 09:52:51 xxx sshd[760]: pam_selinux(sshd:session): Set executable context: [] -> [unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023]
May  5 09:52:51 xxx sshd[760]: pam_selinux(sshd:session): Security Context unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023 Assigned
May  5 09:52:51 xxx sshd[760]: pam_selinux(sshd:session): Set key creation context to unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023
May  5 09:52:51 xxx sshd[760]: pam_selinux(sshd:session): Key Creation Context unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023 Assigned
```



**sys.log**


```
May  5 09:52:27 xxx systemd-timesyncd[551]: Initial synchronization to time server 91.189.89.199:123 (ntp.ubuntu.com).
May  5 09:52:38 xxx kernel: [   57.796158] hv_balloon: Max. dynamic memory size: 4024 MB
May  5 09:52:50 xxx systemd[1]: Starting User Manager for UID 1000...
May  5 09:52:50 xxx systemd[771]: PAM failed: Cannot make/remove an entry for the specified session
May  5 09:52:50 xxx systemd[771]: [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e: Failed to set up PAM session: Operation not permitted
May  5 09:52:50 xxx systemd[771]: [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e: Failed at step PAM spawning /lib/systemd/systemd: Operation not permitted
May  5 09:52:50 xxx systemd[1]: [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e: Main process exited, code=exited, status=224/PAM
May  5 09:52:50 xxx systemd[1]: [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e: Failed with result 'exit-code'.
May  5 09:52:50 xxx systemd[1]: Failed to start User Manager for UID 1000.
May  5 09:52:50 xxx systemd[1]: Started Session 3 of user floki.
```




**Seusers**
```
root@xxx:/var/log# semanage login -l


Login Name           SELinux User         MLS/MCS Range        Service


__default__          unconfined_u         s0-s0:c0.c1023       *
floki                 unconfined_u         s0-s0:c0.c1023       *
root                 unconfined_u         s0-s0:c0.c1023       *
user1                staff_u              s0                   *
user2                staff_u              s0-s0:c0.c1023       *


cat /etc/selinux/default/seusers
root:unconfined_u:s0-s0:c0.c1023
__default__:unconfined_u:s0-s0:c0.c1023
user1:staff_u:s0
user2:staff_u:s0-s0:c0.c1023
floki:unconfined_u:s0-s0:c0.c1023
```





**auditd.logs:**
No AVC problems

r```
oot@xxx:/home/floki# ausearch -m SERVICE_START -ts recent |  grep failed
type=SERVICE_START msg=audit(1620208320.011:70): pid=1 uid=0 auid=4294967295 ses=4294967295 subj=system_u:system_r:init_t:s0 msg='unit=user@1000 

```


I have problem close to : [https://access.redhat.com/solutions/4383921](https://access.redhat.com/solutions/4383921) but not exacly becouse my file /etc/selinux/default/seusersexist. 


Best Regards

---

### Post by TheFu on 2021-05-05
SELinux isn't normally used on Debian-based Linux.  Apparmor is.  You'll find very little help with SELinux on Debian/Ubuntu because 99.99999% of us use something else.

---

### Post by washide on 2021-05-07
When user manager   [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e doesnt work  i cant start users unit  after login via pts/* orr tty . In  my opinion  if it is possible download SELinux from  repo it would be nice to have working packages but mayby i have done some mistake . I want  believe that it is may fault and  Ubunt probably is  ok.

---

