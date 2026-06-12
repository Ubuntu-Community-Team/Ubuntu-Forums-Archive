---
title: "FreeRadius - Ubuntu 10.04 - Problems."
date: 2010-07-08
forum: Server Platforms
---

### Post by Roasted on 2010-07-08
I'm trying to set up FreeRadius from Ubuntu's repos in 10.04 for use on our Windows domain at work. I've been following this guide:

[http://deployingradius.com/documents/configuration/active_directory.html](http://deployingradius.com/documents/configuration/active_directory.html)

But at this step:

```
The next step is to try the same login with the ntlm_auth program, which is what 
FreeRADIUS will be using:

$ ntlm_auth --request-nt-key --domain=MYDOMAIN --username=user --password=password
If all goes well, you should see authentication succeeding (NT_STATUS_OK). You should 
also see the NT_KEY output, which is needed in order for FreeRADIUS to perform MS-CHAP 
authentication.
```

I get this error:

```
NT_STATUS_NO_LOGON_SERVERS: No logon servers
```


:(

Any thoughts?

---

### Post by MidSpeck on 2010-07-08
Could be any number of things.

You could do some checking using "wbinfo" and make sure that the connection to your Windows server is working as it should be.

Run wbinfo by itself to see your options.

Once that's working, I imagine that ntlm_auth will be working as well.

---

### Post by Roasted on 2010-07-09
I tried that, and ran a few of the options there, such as domain information (which showed us our windows domain) as well as domain users (which brought back administrator as I expected).

Not too sure what else to do. I'm at a helluva road block...

---

### Post by MidSpeck on 2010-07-09
What does ```
wbinfo -a domainname\\username
``` return?  You may have to enter your password twice since it will try plaintext and then challenge/response.

---

### Post by Roasted on 2010-07-09
Original output:

administrator@UbuntuRadius:~$ wbinfo -a OURDOMAIN\\administrator
Enter OURDOMAIN\administrator's password:
plaintext password authentication failed
Could not authenticate user OURDOMAIN\administrator with plaintext password
Enter OURDOMAIN\administrator's password: 
challenge/response password authentication failed
error code was NT_STATUS_ACCESS_DENIED (0xc0000022)
error messsage was: winbind client not authorized to use winbindd_pam_auth_crap. Ensure permissions on /var/run/samba/winbindd_privileged are set correctly.
Could not authenticate user OURDOMAIN\administrator with challenge/response
administrator@UbuntuRadius:~$ 

The permissions on winbindd_privileged were 750, so I set them to 777 to test it. Then I got this output:


administrator@UbuntuRadius:~$ wbinfo -a OURDOMAIN\\administrator
Enter OURDOMAIN\administrator's password: 
plaintext password authentication failed
Could not authenticate user OURDOMAIN\administrator with plaintext password
Enter OURDOMAIN\administrator's password: 
challenge/response password authentication failed
error code was NT_STATUS_NO_LOGON_SERVERS (0xc000005e)
error messsage was: No logon servers
Could not authenticate user OURDOMAIN\administrator with challenge/response
administrator@UbuntuRadius:~$

---

### Post by Roasted on 2010-07-12
Up...

---

### Post by MidSpeck on 2010-07-12
Could you post the relevant sections of smb.conf and krb5.conf?

I guess I'm especially looking for the following lines in smb.conf:
security, realm, password server, idmap uid, idmap gid
And in krb5.conf:
default_realm, and the realm for your domain.

Anything else you've changed or think is relevant for your domains would be good too.

---

