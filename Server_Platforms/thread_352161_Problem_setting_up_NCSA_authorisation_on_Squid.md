---
title: "Problem setting up NCSA authorisation on Squid"
date: 2007-02-02
forum: Server Platforms
---

### Post by greymoose58 on 2007-02-02
Squid was working fine with Dans Guardian on a Dapper server until I tried to set up user authentication. I followed this set of instructions [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch32_:_Controlling_Web_Access_with_Squid#Password_Authentication_Using_NCSA]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch32_:_Controlling_Web_Access_with_Squid#Password_Authentication_Using_NCSA")
 but when I restart squid i get the following output: 
```
 * Restarting Squid HTTP proxy squid 2007/02/04 03:59:27| aclParseIpData: WARNING: Netmask masks away part of the specified IP in '192.168.0.2/20'
2007/02/04 03:59:27| Invalid Proxy Auth ACL 'acl AUTHUSERS proxy_auth REQUIRED' because no authentication schemes are fully configured.
FATAL: Bungled squid.conf line 1899: acl AUTHUSERS proxy_auth REQUIRED
Squid Cache (Version 2.5.STABLE12): Terminated abnormally.

```

I'm not sure what part of the authentication scheme I haven't configured. Does anyone have any suggestions about what I may have missed?

Thanks in advance.

Emabarrased mutter: I didn't uncomment the lines in squid.conf when I edited them.

---

