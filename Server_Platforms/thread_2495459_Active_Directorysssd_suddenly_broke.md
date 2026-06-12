---
title: "Active Directory/sssd suddenly broke"
date: 2024-02-20
forum: Server Platforms
---

### Post by Gholam on 2024-02-20
Windows Server 2022 domain controller, Ubuntu 22.04, sssd 2.6.3, system joined to AD via 'realm join', /etc/sssd/sssd.conf looks like this:

```

[sssd]
domains = dev.domain.com
config_file_version = 2
services = nss, pam, sudo, ssh


[domain/dev.domain.com]
default_shell = /bin/bash
krb5_store_password_if_offline = True
cache_credentials = True
krb5_realm = DEV.DOMAIN.COM
realmd_tags = manages-system joined-with-adcli
id_provider = ad
fallback_homedir = /home/%u
ad_domain = dev.domain.com
use_fully_qualified_names = False
ldap_id_mapping = True
access_provider = ad
ad_gpo_access_control = permissive
ldap_user_extra_attrs = altSecurityIdentities:altSecurityIdentities
ldap_user_ssh_public_key = altSecurityIdentities
ldap_user_tokengroups = True

```

Everything was fine since the system was set up, until this morning, after I ran February 2024 updates on the DC, suddenly on some (but not all) servers, AD users are unable to log on, either locally or over SSH, with an 'Access denied' message.

I rolled back the update (actually restored the sole DC from snapshot, as it was faster), but this did not help.

The only thing I can see in the logs that looks out of place is this, in /var/log/sssd/sssd_pam.log:

[pam] [cache_req_common_process_dp_reply] (0x0040): [CID#2] CR #3: Could not get account info [14]: Bad address

Adding debug_level = 9 to sssd.conf did not produce anything useful either.

However, running 'id username' as root for any AD user succeeds and returns their uid and gids, successfully resolving group names.

Leaving the domain, deleting the computer account and rejoining works (a new computer account is created as expected), but does not resolve the issue.

Not sure where to even look for more info...

---

