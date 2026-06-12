---
title: "WindowsXP clients unable to authenticate"
date: 2012-07-12
forum: Server Platforms
---

### Post by thehiers on 2012-07-12
A couple mornings ago, all the users in a small office were able to log into their windows machines which are members of an ubuntu domain controller.  Later in the afternoon, when they tried to log back onto their machines, they began getting a message: "Windows cannot connect to the domain, either because the domain controller is down or otherwise unavailable, or because your computer was not found."

The samba log for that machine has this error: rpc_server/srv_netlog_nt.c:603(_netr_ServerAuthenticate3)
  _netr_ServerAuthenticate3: netlogon_creds_server_check failed. Rejecting auth request from client CLIENTNAME machine account CLIENTNAME$

At the same time in the auth.log I'm seeing errors such as:
Jul 12 07:18:03 Server nscd: nss_ldap: could not connect to any LDAP server as cn=adminuser,dc=church,dc=org - Can't contact LDAP server
Jul 12 07:18:03 Server nscd: nss_ldap: failed to bind to LDAP server ldapi://127.0.0.1: Can't contact LDAP server
Jul 12 07:18:03 Server nscd: nss_ldap: could not search LDAP server - Server is unavailable

The smb.conf and ldap.conf files have not changed.

I'm guessing I have an LDAP problem, but I'm not sure where to start.  Any advice would be greatly appreciated.

Thanks
Richard

---

### Post by kennethconn on 2012-07-12
What have you done so far in the troubleshooting process (network connectivity to server, status of the LDAP service, what changes have there been recently)?

---

