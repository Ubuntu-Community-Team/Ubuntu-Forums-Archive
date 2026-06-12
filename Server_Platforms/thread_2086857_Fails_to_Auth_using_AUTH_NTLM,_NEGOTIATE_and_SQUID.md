---
title: "Fails to Auth using AUTH_NTLM, NEGOTIATE and SQUID Proxy"
date: 2012-11-22
forum: Server Platforms
---

### Post by MartinChir on 2012-11-22
The following is the current issue I have with Squid Authentication in a Active Directory Domain:

```
user@texas-nix:/etc/squid3$ wbinfo -t
checking the trust secret for domain TEXAS via RPC calls failed
failed to call wbcCheckTrustCredentials: WBC_ERR_WINBIND_NOT_AVAILABLE

wbinfo -g = OK
wbinfo -u = OK
```

I have Samba installed on the same machine and it is authenticating with the domain servers without issues

---

