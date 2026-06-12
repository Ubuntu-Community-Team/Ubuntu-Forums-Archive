---
title: "SSSD fails to connect/authenticate with LDAP server when run as a service"
date: 2023-12-20
forum: Security
---

### Post by dav96che on 2023-12-20
Hi all,

I have been attempting to setup the AD functionality on a Supermicro server running Ubuntu 22.04.3 following the steps laid out in these two tutorials:
[https://ubuntu.com/server/docs/service-sssd-ad]("https://help.ubuntu.com/community/Kerberos#Configuration") and [https://help.ubuntu.com/community/Kerberos#Configuration](https://help.ubuntu.com/community/Kerberos#Configuration)

By my estimation, I have the required packages and configuration complete, but I am running into an issue with the sssd service. From the domain specific logs generated, I see the following errors (paraphrased, as the server is isolated, and I have to type this by hand):[INDENT]
[sdap_process_result]: ldap_result error: [Can't contact LDAP server]
************
[sdap_get_tgt_recv]: Cannot parse child response: [22][Invalid Argument]
************
[sdap_cli_kinit_done]: Cannot get a TGT: ret [22] (Invalid Argument)
[sdap_cli_connect_recv]: Unable to establish connection [13]: Permission denied
[/INDENT]

As a result, I am not able to access any AD user accounts (as confirmed by the output from 'id <username>').

I have verified that the connection to the LDAP server is valid (DNS works correctly), and I am able to successfully acquire a Kerberos TGT (using kinit with a valid principal). Also the permissions on /etc/sssd/sssd.conf and /var/lib/sss/private/pipes are set to 0x600 and 0x700 respectively with an owner:group of root:root. 

Furthermore, while troubleshooting this issue, I discovered that stopping the sssd service and running the process directly from the command line will work as expected (ie. "sudo sssd -i -d5"). When run this way, the sssd process displays no errors, and I am able to successfully query AD users with 'id <username>'.

This is the strangest finding because it appears that my configuration will work, provided that I run the sssd process manually. As far as I can tell, the sssd.service runs exactly the same command: "ExecStart=/usr/sbin/sssd -i ${DEBUG_LOGGER}"

For reference, my sssd.conf file (created by realm after joining the domain) looks like this:[INDENT]
[sssd]
domains: <REDACTED>
config_file_version = 2
services = nss, pam

[domain/example.local]
default_shell = /bin/bash
krb5_store_password_iff_offline = True
cahce_credentials = True
krb5_realm = EXAMPLE.LOCAL
realmd_tags = manages-system joined-with-adcli
id_provider = ad
fallback_homedir = /home/%u
ad_domain = example.local
use_fully_qualified_names = False
ldap_id_mapping = True
access_provider = ad
[/INDENT]

Any additional insights would be very much appreciated.

---

