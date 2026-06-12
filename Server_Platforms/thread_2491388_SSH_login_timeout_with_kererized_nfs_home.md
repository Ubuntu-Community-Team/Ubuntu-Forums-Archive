---
title: "SSH login timeout with kererized nfs home"
date: 2023-10-06
forum: Server Platforms
---

### Post by sparrow33 on 2023-10-06
We use kerberized ssh servers with kerberized NFS 4.2 home directories. 
If the Kerberos ticket expires and the user is still in the home directory, then he has to wait for a timeout of approx. 2 minutes until he can authenticate himself again with kinit.
Can the timeout be reduced?  
Is there another way to make it more user-friendly?
For a while, you could avoid the timeout if you mounted the user home directories via autofs instead of the static NFS mount via fstab. However, that does not work anymore either.

---

### Post by MAFoElffen on 2023-10-06
I hadn't heard of a delay of kerberized ssh or mounting NFS Homes after the kerberos ticket expired...

I wasn't sure, so I checked the Doc's at RedHat for setting up kerberization of Home directories via NFS... RE: [https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/linux_domain_identity_authentication_and_policy_guide/krb-nfs-client](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/linux_domain_identity_authentication_and_policy_guide/krb-nfs-client)
> 

[LIST]
[*]                     Configure SSSD to renew Kerberos tickets:
[LIST]
[*]                             Set the following parameters in the IdM domain section of the /etc/sssd/sssd.conf file to configure SSSD to automatically renew tickets:                         

```

[domain/EXAMPLE.COM]
...
krb5_renewable_lifetime = 50d
krb5_renew_interval = 3600

``` 
[*]                             Restart SSSD:                         
```


[root@nfs-client ~]# systemctl restart sssd

``` 
[/LIST]
         
[/LIST]


So it looks like setting krb5_renew_interval time less than the krb5_lifetime automatically renews the ticket, and as long as it doesn't exceed krb5_renewable_lifetime (usually 10 days), that the NFS shares stay mounted, because the ticket is still alive and valid... (But how they have that, krb5_lifetime is usually set to 9-10 hours = 540-600 minutes... 3600 minutes is 60 hours.)

You'd have to get the math worked out related to the other settings in your environment.

Well, that's one way to deal with that.

---

### Post by sparrow33 on 2023-10-09
Thanks MAFoElffen for the tip, but unfortunately this only delays the problem and does not comply with the security recommendations for Kerberos tickets. I know the options for extending Kerberos tickets via crontab krenew or a personal keytab file. 
Mounting the NFS share is not the problem either. The problem is that users have to wait about 2 minutes until they can get a new Kerberos ticket via kinit. If I could shorten this timeout, it would help us.

---

### Post by MAFoElffen on 2023-10-09
The only thing I can think of... What happens if the user does this:
```

klist purge &#8211;li 0x3e7

```
Which would purge any cached kerberos tickets in their credential cache and forces a refresh of the current tickets in that cache on the next kinit, without havig to reboot that computer. (Which is what they usually recommend.)

---

### Post by sparrow33 on 2023-10-10
Sorry, but I think this is no way to shorten the timeout after the kerberos ticket is expired. Also, the command 'klist purge &#8211;li 0x3e7' is only for Windows (computer account). The corresponding Linux command kdestroy doesn't help me either.

---

### Post by MAFoElffen on 2023-10-10
Dang. I'm out of ideas on that. Maybe someone else knows, or has ideas on that.

Sorry.

---

