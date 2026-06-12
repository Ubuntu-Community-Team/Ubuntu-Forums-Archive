---
title: "Kerberos with AD fails to authenticate"
date: 2023-08-22
forum: Server Platforms
---

### Post by randreea23 on 2023-08-22
Hello, I am facing an issue with some Ubuntu servers (where I installed desktop version Ubuntu 20.04) connecting to the AD server. 
The AD server is in fact a Windows server and the ubuntu servers were joined to the AD using the [FONT=courier new]realm [/FONT]tool. It worked fine for almost 2 years until last week.

Long story short, there was a security patch applied to the AD server a week before which apparently brought down the authentication system on our machines - this is the believed theory right now.

So in terms of configuration, as far as I can find out we are using Kerberos with AD.
This is the content of the [FONT=courier new]/etc/sssd/sssd.conf[/FONT] (which got automatically configured by running [FONT=courier new]realm join <domain>[/FONT])

```


[sssd]
domains = mydomain.com
config_file_version = 2
services = nss, pam

[domain/mydomain.com]
default_shell = /bin/bash
krb5_store_password_if_offline = True
cache_credentials = True
krb5_realm = MYDOMAIN.COM
realmd_tags = manages-system joined-with-adcli
id_provider = ad
fallback_homedir = /home/%u
ad_domain = mydomain.com
use_fully_qualified_names = True
ldap_id_mapping = True
access_provider = simple
simple_allow_groups = AD_GROUPS

```

I have no experience with authentication systems and AD and Kerberos so I'm slowly trying to get the hang of it but it all seems very complicated and confusing. 
Still I don't understand what the difference is between using [FONT=courier new]ad[/FONT] and [FONT=courier new]ldap[/FONT] for the [FONT=courier new]id_provider [FONT=arial]- [/FONT][/FONT]it seems that the authentication does not work AT ALL when using [FONT=courier new]ad [FONT=arial]([/FONT][/FONT]which is what we were using so far[FONT=courier new][FONT=arial]).
[/FONT][/FONT]
After a lot of tweaking different configurations and looking at the logs, I think the problem is on the Kerberos level. I saw messages in the [FONT=courier new]/var/log/sssd/sssd_mydomain.log[/FONT] like so:
```

[write_krb5info_file_from_fo_server] (0x0020): There is no server that can be written into kdc info file.
[ad_resolve_callback] (0x0080): write_krb5info_file failed, authentication might fail.

```

And looking into the /var/log/sssd/krb5_child.log:
```

(Tue Aug 22 13:45:31 2023) [krb5_child[2151201]] [tgt_req_child] (0x1000): Attempting to get a TGT
(Tue Aug 22 13:45:31 2023) [krb5_child[2151201]] [get_and_save_tgt] (0x0400): Attempting kinit for realm [MYDOMAIN.COM]
(Tue Aug 22 13:45:31 2023) [krb5_child[2151201]] [validate_tgt] (0x2000): Found keytab entry with the realm of the credential.
(Tue Aug 22 13:45:31 2023) [krb5_child[2151201]] [validate_tgt] (0x0400): TGT verified using key for [HOSTNAME$@MYDOMAIN.COM].
(Tue Aug 22 13:45:31 2023) [krb5_child[2151201]] [sss_send_pac] (0x0040): sss_pac_make_request failed [-1][14].
(Tue Aug 22 13:45:31 2023) [krb5_child[2151201]] [validate_tgt] (0x0040): sss_send_pac failed, group membership for user with principal [username\@MYDOMAIN.COM@MYDOM.COM] might not be correct.
(Tue Aug 22 13:45:31 2023) [krb5_child[2151201]] [get_and_save_tgt] (0x2000): Running as [259953316][259800513].
(Tue Aug 22 13:45:31 2023) [krb5_child[2151201]] [sss_get_ccache_name_for_principal] (0x2000): krb5_cc_cache_match failed: [-1765328243][Can't find client principal username@MYDOMAIN.COM in cache collection]

```


I heard that this [FONT=&amp]Microsoft patch KB5028169 was applied - which would be the reason for why our servers cannot be reached anymore using the SSO credentials. Also someone mentioned this patch brought down a lot of linux machines but meanwhile there was a linux (Red Hat?) patch that supposedly fixes the issue. I tried to find some mention of this patch but I didn't manage. The only open issue that seems related to what I am trying to solve is this: [https://forums.ivanti.com/s/article/Active-Directory-domain-join-fails-with-IPS-and-ICS-when-July-11-2023-KB5028169-OS-Build-14393-6085-Patch-is-applied?language=en_US](https://forums.ivanti.com/s/article/Active-Directory-domain-join-fails-with-IPS-and-ICS-when-July-11-2023-KB5028169-OS-Build-14393-6085-Patch-is-applied?language=en_US)
[/FONT]
Do you know if there is such a patch or what other configuration I can try in order to fix this? Thanks a lot![FONT=&amp][URL="https://forums.ivanti.com/s/article/Active-Directory-domain-join-fails-with-IPS-and-ICS-when-July-11-2023-KB5028169-OS-Build-14393-6085-Patch-is-applied?language=en_US"]



[/URL][/FONT][U][URL="https://forums.ivanti.com/s/article/Active-Directory-domain-join-fails-with-IPS-and-ICS-when-July-11-2023-KB5028169-OS-Build-14393-6085-Patch-is-applied?language=en_US"]
[/URL][/U]

---

### Post by MAFoElffen on 2023-08-22
That Update was released November 8th, 2022. You are not that current are you(?)

Microsoft released an OOB (Out Of Band) Update to correct the problem they caused with Kerberos on that Update patch: [https://techcommunity.microsoft.com/t5/ask-the-directory-services-team/november-2022-out-of-band-update-released-take-action/ba-p/3680144](https://techcommunity.microsoft.com/t5/ask-the-directory-services-team/november-2022-out-of-band-update-released-take-action/ba-p/3680144)

RE:
[https://www.bleepingcomputer.com/news/microsoft/microsoft-fixes-windows-kerberos-auth-issues-in-emergency-updates/](https://www.bleepingcomputer.com/news/microsoft/microsoft-fixes-windows-kerberos-auth-issues-in-emergency-updates/)
[https://www.theregister.com/2022/11/21/microsoft_kerberos_fix_windows/](https://www.theregister.com/2022/11/21/microsoft_kerberos_fix_windows/)

To correct it, you just apply the emergency OOB update to the affected Windows Server that was broken by that update...

---

### Post by randreea23 on 2023-08-24
I think the AD servers are more current than that yes, the last patch  they applied was this KB5028169 which was released in July 2023. 
Unfortunately I do not have any control over the AD servers so I need to make do with what is provided.

What I understood from talking to some people is that this July patch hardened the Kerberos authentication scheme:


> 
The Windows updates released on or after July 11, 2023 will do the following:                
[LIST]
[*]                   Removes the ability to set value **1** for the **KrbtgtFullPacSignature** subkey. 
[*]                   Moves the update to Enforcement mode (Default) (**KrbtgtFullPacSignature**** = 3)** which can be overridden by an Administrator with an explicit Audit setting. 
[/LIST]


which is part of a longer process of changing the Kerberos protocol:
[https://support.microsoft.com/en-gb/topic/kb5020805-how-to-manage-kerberos-protocol-changes-related-to-cve-2022-37967-997e9acc-67c5-48e1-8d0d-190269bf4efb](https://support.microsoft.com/en-gb/topic/kb5020805-how-to-manage-kerberos-protocol-changes-related-to-cve-2022-37967-997e9acc-67c5-48e1-8d0d-190269bf4efb)

Now  I am not sure if there is even a linux patch to the krb5 libraries that  I could apply in order to conform to the new changes.

---

### Post by MAFoElffen on 2023-08-25
That was what Microsoft was hoping to do, and what their intent was, BUT...
RE:
> 
*"While Microsoft has started enforcing security hardening for Netlogon and Kerberos beginning with the November 2022 Patch Tuesday, the company says this known issue is not an expected result."*

But... That was when they broke Kerberos trying to harden it, back in November 2022...

Are you saying that another Kerberos hardening patch has come along in July 11, 2023 and broke it "again"? LOL

---

### Post by randreea23 on 2023-08-25
Haha, I am not sure but I would not be surprised. I saw they released another patch this month to fix yet another Kerberos issue: [https://support.microsoft.com/en-au/topic/august-8-2023-kb5029242-os-build-14393-6167-1faba2e0-792e-4fd1-91df-212a11ad0eda](https://support.microsoft.com/en-au/topic/august-8-2023-kb5029242-os-build-14393-6167-1faba2e0-792e-4fd1-91df-212a11ad0eda)
But I don't know if it is relevant to my current issue. Again unfortunately I have no control or access to the AD servers. All I know is that they applied a patch on them, then a week later our SSO credentials didn't work anymore on our servers...

I keep investigating and digging through log files but nothing seems to be conclusive in terms of what is exactly happening. It is so strange, there are Ubuntu 6 servers we manage, all of them went down at the same day. On 5 of them me and a colleague kept investigating and tweaking configurations - all of them are switched to use [FONT=courier new]ldap[/FONT] instead of [FONT=courier new]ad[/FONT] for the protocol, that seems to somehow make it work (very unstable, but at least it's something). 

The last server nobody touched since this happened - I updated and restarted and I can reproduce a successful connection to it using the SSO credentials BUT establishing an ssh connection takes at least 5 minutes or more. Trying to run a command with sudo is the same - takes 5 minutes. Now I'm even more confused because what if there is actually some network issue that is causing all this... 
Also running the `[FONT=courier new]groups <SSO username>[/FONT]` takes 5 minutes to output - I read online that this can happen if the domain controller forest is very big and indexing through hundreds of groups is very slow. 

There are just so many things that can go wrong and I don't really know what to look into anymore.

---

### Post by MAFoElffen on 2023-08-25
Is there a common error message clients are getting, such as a Kerberos error message on a connect? I remember last February, where they published an article saying if it got a specific error, 
```

HTTP 400 - Bad Request (Request Header too long)

```
which as caused when a client was a member of too many security groups, and the generated Kerberos ticket was too long for the Kerberos Server to process. The fix for that was for all clients affected to make a registry change:
```

On each of these computers, set the MaxTokenSize registry entry to a larger value. You can find this entry in the HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\Kerberos\Parameters subkey. The computers have to restart after you make this change.

```
Where that value had to be enter there, had to be calculated for "each user" by a formula they came up with... PITA. Boiled down, it was affected by the number security groups they belonged to.

RE: [https://learn.microsoft.com/en-us/troubleshoot/windows-server/windows-security/kerberos-authentication-problems-if-user-belongs-to-groups](https://learn.microsoft.com/en-us/troubleshoot/windows-server/windows-security/kerberos-authentication-problems-if-user-belongs-to-groups)

---

### Post by MAFoElffen on 2023-08-25
If I were to guess, I would follow this path:

It looks like it is related to this CVE: [https://msrc.microsoft.com/update-guide/vulnerability/CVE-2022-37967](https://msrc.microsoft.com/update-guide/vulnerability/CVE-2022-37967)

And the documentation they generated on that to correct it for that update was this deployment guide: [https://support.microsoft.com/en-gb/topic/kb5020805-how-to-manage-kerberos-protocol-changes-related-to-cve-2022-37967-997e9acc-67c5-48e1-8d0d-190269bf4efb](https://support.microsoft.com/en-gb/topic/kb5020805-how-to-manage-kerberos-protocol-changes-related-to-cve-2022-37967-997e9acc-67c5-48e1-8d0d-190269bf4efb)

Where the July 2023 Update you noted in your post is in the Deployment timing of that guide name as "Initial Enforcement Phase"... The Update back in Oct 2022 that had caused problems before was noted as the Initial Deployment Phase.

And that there is one more phase planned for the roleout in October 2023.

Have you followed the instruction there in that deployment guide?

By the CVE Tracker in Ubuntu: [https://ubuntu.com/security/CVE-2022-37967](https://ubuntu.com/security/CVE-2022-37967)

You can see that Jammy 22.04 had an update (Released (2:4.15.13+dfsg-0ubuntu1) ) that addressed that...

---

### Post by MAFoElffen on 2023-08-25
Here you go. a breadcrumb hint to look for from the Reddit Patch Tuesday Megathread ([https://www.reddit.com/r/sysadmin/comments/14wtpne/patch_tuesday_megathread_20230711/](https://www.reddit.com/r/sysadmin/comments/14wtpne/patch_tuesday_megathread_20230711/))... There was a registry value that needed to be changed to be compliant with that enforcement...
> 
Remember 1: that Enforcement of KrbtgtFullPacSignature = 3 by Default comes with the July updates regarding Kerberos protocol changes related to CVE-2022-37967 (KB5020805-how-to-manage-kerberos-protocol-changes)

Windows updates address security bypass and elevation of privilege vulnerabilities with Privilege Attribute Certificate (PAC) signatures. This security update addresses Kerberos vulnerabilities where an attacker could digitally alter PAC signatures, raising their privileges.

Starting July 2023, Enforcement mode will be enabled on all Windows domain controllers and will block vulnerable connections from non-compliant devices.  At that time, you will not be able to disable the update (removes the ability to set value 1 for the KrbtgtFullPacSignature subkey) !

Remember 2: Netlogon protocol changes related to CVE-2022-38023 (KB5021130-how-to-manage-the-netlogon-protocol-changes)
The Windows updates released on July 11, 2023 will remove the ability to set RequireSeal=1

[COLOR=#ff0000]RequireSeal registry key is forced to be to 2[/COLOR] (All clients are required to use RPC Seal), contents of the registry value are ignored. This enables the Enforcement phase of CVE-2022-38023

Get your NetApp ONTAP, AWS FSx for NetApp ONTAP, Pulse Secure VPN/Ivanti Connect Secure, ... devices upgraded !


---

### Post by randreea23 on 2023-08-28
Thanks a lot for all the references. 
I never saw this error on any of the clients trying to authenticate :
```
HTTP 400 - Bad Request (Request Header too long)
```

Also I looked into the [CVE-2022-37967]("https://msrc.microsoft.com/update-guide/vulnerability/CVE-2022-37967") issue with a colleague - he could see the TGT being granted from the KDC server for the user trying to login. He even reverted this enforced flag back to Audit mode (meaning the auth system would allow requests even with the vulnerable flag but would log it somewhere) and it didn't seem to solve the problem. 

I saw the CVE tracker in Ubuntu as well - the samba package was updated to the latest version 

```
samba-common/focal-updates,focal-updates,now 2:4.15.13+dfsg-0ubuntu0.20.04.4 all [installed,automatic]
```

although I am not sure if it was relevant to my issue since as far as I could see on the servers they are using SSSD for authentication management and not Samba (but I don't know enough about the topic to say for sure). 

However some updates - while debugging a server, I noticed that SSH-ing to it took more than 5 minutes but it managed to connect eventually. I reproduced it a couple of times and randomly the SSH connection got established much faster and when I tested on the rest of the servers it seemed like the original problem went away. 
So now I'm quite inclined to believe that the originating issue was some misconfiguration somewhere outside of our Ubuntu servers which got fixed by someone or something. It is frustrating however that I don't know what caused and what fixed the issue since there is no guarantee this won't happen in the future. 
I noticed by checking the sssd logs in more detail (set the debug_level to 0x3ff0) that there are a LOT of groups and users that get parsed while trying to do an authentication request - and by a lot I mean that the log file size is around 200 MB for 1 authentication request. One theory that I have now is that the AD request was going through a lot of hops and to a very distant AD server which could explain the latency of the entire process and all the timeouts. 

Again thanks a lot for all your help and guidance!

---

### Post by MAFoElffen on 2023-08-28
Are the clients having the slow speed issues Win 10 & Win11?

I remember a Kerberos issue with Win10 machines using Kerberos, where the issue was where Windows 10 is to constantly looking for a Domain Master Browser over NetBIOS when logged in with as a  Kerberos / Domain user. That caused long slowdowns every time the user information needed group memberships. 

For that: Disabling &#8220;NetBIOS over TCP/IP&#8221; on Win10 clients by opening their network adapter details > &#8220;Properties&#8221; > &#8220;Internet Protocol Version 4 (TCP/IPv4)&#8221; > &#8220;Properties&#8221; > &#8220;Advanced&#8230;&#8221; > &#8220;WINS&#8221; &#8594; &#8220;Disable NetBIOS over TCP/IP&#8221; solved the issue for them.

That problem, I think started around, IDK... about 4 years ago or so?

Because you said you had Ubuntu Servers joined to the domain, but you didn't mention what the clients were. I just went back through and reread the first post where you said those severs are 20.04, but focal got that patch back-ported also, so... no matters there. 

I also dove a bit deeper looking at what you said were suspected warning messages. but found this about it: [https://github.com/SSSD/sssd/issues/5956](https://github.com/SSSD/sssd/issues/5956). The patch for that was applied upstream in 04/2022, so should have hit, but not sure for 20.04, if it got backported or not...

I don't know. In my test suite, I have Windows Server 2022 DataCenter as a Domain Controller and a few joined Ubuntu Servers, a Win11 RSAT and a Gnome Console and everything is running great. Here is the important stats on the 23.04 test server:
```

mafoelffen@lunerlander-02:~$ sudo grep . /etc/sssd/sssd.conf
[sssd]
domains = ferreira.local
config_file_version = 2
services = nss, pam
reconnection_retries = 4
full_name-format = %2$s
[nss]
#debug_level = 2
[pam]
#pam_verbosity = 1
[domain/ferreira.local]
#debug_level = 6
ad_server = dc1.ferreira.local
ad_domain = ferreira.local
krb5_realm = FERREIRA.LOCAL
ldap_uri = ldap://dc1.ferreira.local
ldap_search_base = dc=ferreira,dc=local
krb5_server = dc1.ferreira.local
krb5_kpasswd = dc1.ferreira.local
auth_provider = krb5
#hostid_provider = ad
access_provider = ad
id_provider = ldap
default_shell = /bin/bash
krb5_store_password_if_offline = True
cache_credentials = True
realmd_tags = manages-system joined-with-adcli
fallback_homedir = /home/%u
use_fully_qualified_names = True
ldap_id_mapping = True
mafoelffen@lunerlander-02:~$ sudo realm -v discover dc1.ferreira.local
 * Resolving: _ldap._tcp.dc1.ferreira.local
 * Resolving: dc1.ferreira.local
 * Performing LDAP DSE lookup on: 192.169.122.20
 * Performing LDAP DSE lookup on: 192.168.1.20
 * Successfully discovered: FERREIRA.LOCAL
FERREIRA.LOCAL
  type: kerberos
  realm-name: FERREIRA.LOCAL
  domain-name: ferreira.local
  configured: kerberos-member
  server-software: active-directory
  client-software: winbind
  required-package: libnss-winbind
  required-package: winbind
  required-package: libpam-winbind
  required-package: samba-common-bin
  login-formats: %U
  login-policy: allow-any-login

```

---

### Post by randreea23 on 2023-08-29
It varies - most people are using Win 10 but some are using WSL2 (me included) and some also have Ubuntu workstations as clients as well. The issue happened on all of the clients however. 

One mistake that I did when debugging this was that I kept using the hostname defined in the ssh config file where I had also defined parameters like: 
         ```

ServerAliveInterval 15
ServerAliveCountMax 3 
```

because I had the first successful ssh connection when I just did [FONT=courier new]ssh username@domain@hostname[/FONT] instead of just [FONT=courier new]ssh host[/FONT]. But I'm not sure if this has an impact because as far as I understand these configurations only apply to an established ssh session. 

Thanks for the tip regarding disabling "NetBIOS over TCP/IP", I'll keep it in mind for the future.

Yes, the warning messages with [FONT=courier new][write_krb5info_file_from_fo_server][/FONT], I saw that the sssd version installed on the servers was 2.2.3 - which seems to be quite old so I was looking into how to update it but I couldn't find any ppa with a newer version so I never tried that but I think it would've been a good direction to continue debugging. I saw they added quite a lot of changes related to krb5 since v.2.2.3. I don't really understand how it works with the official ubuntu packages - do they get patched when big issues arise but the base implementation stays the same? 

Regarding the configuration you have on your server - I have almost the same configuration except one thing (which apparently makes a big difference): the [FONT=courier new]id_provider = ldap[/FONT] is set to[FONT=courier new] id_provider = ad[/FONT] on our servers. 
I even saw on their website: [https://sssd.io/docs/ad/ad-ldap-provider.html](https://sssd.io/docs/ad/ad-ldap-provider.html) that they recommend to join to an AD using the integrated [FONT=courier new]id_provider = ad[/FONT].
This was one of the "fixes" we applied to some servers that seemed to partially make authentication work - but not for all users so it wasn't really a proper fix.

---

### Post by MAFoElffen on 2023-08-29
I see current as 2.2.3-3 (package 2.2.3-3ubuntu0.12)

I see Bugs on the current 2.2.3-3:
[https://bugs.launchpad.net/ubuntu/+source/sssd/+bug/1902808](https://bugs.launchpad.net/ubuntu/+source/sssd/+bug/1902808)
 --fixed for 20.10 and later. Didn't see where it was fixed for 2004... But here is the changlog since then:
```

sssd (2.2.3-3ubuntu0.12) focal-security; urgency=medium

  * Fix crash with mismatched packages (LP: #2023598)
    - debian/control: add a versioned dependency on libsss-certmap0 to the
      sssd-common package.

 -- Marc Deslauriers <marc.deslauriers@ubuntu.com>  Thu, 15 Jun 2023 18:16:57 -0400

sssd (2.2.3-3ubuntu0.11) focal-security; urgency=medium

  * SECURITY UPDATE: libsss_certmap fails to sanitise certificate data used
    in LDAP filters
    - debian/patches/CVE-2022-4254.patch: sanitize LDAP search filter in
      Makefile.am, src/lib/certmap/sss_certmap.c,
      src/lib/certmap/sss_certmap.exports, src/lib/certmap/sss_certmap.h,
      src/responder/pam/pamsrv_p11.c, src/tests/cmocka/test_certmap.c,
      src/util/util.c, src/util/util_ext.c.
    - CVE-2022-4254

 -- Marc Deslauriers <marc.deslauriers@ubuntu.com>  Tue, 06 Jun 2023 09:22:35 -0400

sssd (2.2.3-3ubuntu0.10) focal-security; urgency=medium

  * No-change rebuild against samba security update.

 -- Marc Deslauriers <marc.deslauriers@ubuntu.com>  Fri, 03 Mar 2023 08:21:36 -0500

sssd (2.2.3-3ubuntu0.9) focal; urgency=medium

  * d/p/lp1934997-authentication-fails-gpo-non-existent.patch:
    Fix authentication failure when GPO is enabled and
    SecEdit/GptTmpl.inf is missing (LP: #1934997).
  * d/p/lp1979350-GPO-ignore-non-ascii-symbols-in-GPT.INI.patch:
    Ignore non-ASCII characters in GPT.INI.  (LP: #1979350)

 -- Sergio Durigan Junior <sergio.durigan@canonical.com>  Tue, 21 Jun 2022 14:29:52 -0400

sssd (2.2.3-3ubuntu0.8) focal-security; urgency=medium

  * No-change rebuild against samba security update.

 -- Marc Deslauriers <marc.deslauriers@ubuntu.com>  Wed, 10 Nov 2021 10:20:51 -0500

sssd (2.2.3-3ubuntu0.7) focal-security; urgency=medium

  * SECURITY UPDATE: shell command injection in sssctl comment
    - debian/patches/CVE-2021-3621.patch: replace system() with execvp() to
      avoid execution of user supplied command in
      src/tools/sssctl/sssctl.c, src/tools/sssctl/sssctl.h,
      src/tools/sssctl/sssctl_data.c, src/tools/sssctl/sssctl_logs.c.
    - CVE-2021-3621

 -- Marc Deslauriers <marc.deslauriers@ubuntu.com>  Wed, 18 Aug 2021 08:19:23 -0400

sssd (2.2.3-3ubuntu0.6) focal; urgency=medium

  * debian/patches/fix-gpo-MS-ADTS-compliance.patch:
    - Backport several upstream patches from 2.3.x and 2.4.x in ad_gpo
      namespaces. This makes it compliant with MS ADTS spec, which allows
      gpos to be downloaded on user login. (LP: #1933116)

 -- Didier Roche <didrocks@ubuntu.com>  Fri, 18 Jun 2021 16:24:45 +0200

sssd (2.2.3-3ubuntu0.5) focal-proposed; urgency=medium

  * SRU: LP: #1931074: Fix tests to also pass with Python 3.8.10.

 -- Matthias Klose <doko@ubuntu.com>  Mon, 07 Jun 2021 10:01:44 +0200

sssd (2.2.3-3ubuntu0.4) focal; urgency=medium

  [ Marco Trevisan ]
  * debian/control:
    - Add missing (test) dependencies as per libcrypto usage (LP: #1905790)
    - Update Maintainer to Ubuntu devs
  * debian/rules: Compile using libcrypto as crypto backend (LP: #1905790)
  * debian/nss-database-pem-exporter: Add to sssd-common and run on postinst.
    When upgrading from previous versions (that were compiled using the NSS
    crypto backend) we need to migrate the trusted CA certificates that the
    user may have added to the SSSD's NSS system database (that defaults to
    /etc/pki/nssdb).
    To do this, and not to introduce a new dependency on libnss3-tools
    (which is not shipped by default, other than making the parsing not
    working in some scenarios) I've added a small C tool that we compile and
    install as part of the sssd-common package which is able to get all the
    trusted CA certificates for a NSS database and export them in PEM
    format.
    The nss-database-pem-exporter is then used in the postinst script where
    we now:
     1. Read the SSSD settings
     2. Convert all the certificates in the configured NSS databases
     3. Store them all, appending them to the (new) default location
        (/etc/sssd/pki/sssd_auth_ca_db.pem)
     4. Disables the configured locations if pointing to NSS dbs (needed or
        we'll leave the configuration with broken values).
    At this point nss-database-pem-exporter is then the only binary in the
    package that still depends on NSS libraries. (LP: #1905790)
  * debian/patches:
    - Get libsofthsm2 from right path for each architecture, this is now used
      for real (wasn't before) to test p11k components with libcrypto and
      p11-kit, also avoids a test build failure on armhf (LP: #1905790)

  [ Valters Jansons ]
  * Avoid sending malformed SYSLOG_IDENTIFIER to journald (LP: #1908065):
    - d/rules: Set --with-syslog=journald in override_dh_auto_configure.
    - d/p/lp-1908065-01-debug_prg_name-format.patch:
      Upstream patch to clean up program names.
    - d/p/lp-1908065-02-syslog_identifier-format.patch:
      Upstream patch to include "sssd[]" identifier in program names.
    - d/p/lp-1908065-03-remove-syslog_identifier.patch:
      Upstream patch to remove custom SYSLOG_IDENTIFIER from Journald.
    
 -- Marco Trevisan (TreviÃ±o) <marco@ubuntu.com>  Thu, 11 Feb 2021 15:31:14 -0500

sssd (2.2.3-3ubuntu0.3) focal; urgency=medium

  * d/apparmor-profile: Update profile. (LP: #1910611)
    - Extend read permissions to /etc/sssd/** and /etc/gss/**.
    - Add read/execute permission to /usr/libexec/sssd/*.

 -- Sergio Durigan Junior <sergio.durigan@canonical.com>  Mon, 18 Jan 2021 16:30:13 -0500

sssd (2.2.3-3ubuntu0.2) focal; urgency=medium

  * d/p/0003-Only-start-sssd.service-if-there-s-a-configuration-f.patch:
    Upstream patch to make sssd.service only able to start when there
    is a configuration file present.  (LP: #1900642)

 -- Sergio Durigan Junior <sergio.durigan@canonical.com>  Mon, 11 Jan 2021 14:33:54 -0500

sssd (2.2.3-3ubuntu0.1) focal; urgency=medium

  * Enable support for "ad_use_ldaps" for new Active Directory 
    requirement ADV190023 (LP: #1868703):
    - d/p/lp-1868703-01-ad-allow-booleans-for-ad_inherit_opts_if_needed.patch
    - d/p/lp-1868703-02-ad-add-ad_use_ldaps.patch
    - d/p/lp-1868703-03-ldap-add-new-option-ldap_sasl_maxssf.patch
    - d/p/lp-1868703-04-ad-set-min-and-max-ssf-for-ldaps.patch

 -- Matthew Ruffell <matthew.ruffell@canonical.com>  Tue, 10 Nov 2020 11:59:08 +1300

```
This is from 2.2.3-3, which back then, then changed to 2.2.3-3ubuntu0.1... which in change 'sssd (2.2.3-3ubuntu0.6)' Jun 2021, got backport changes from 2.3.x and 2.4.x... Like I said, current for Focal is now sssd(2.2.3-3ubuntu0.12).

---

### Post by randreea23 on 2023-08-30
Hmm I see - I did not stumble upon that bug report for sssd so far but it might be related on some level.
The servers have this version installed of sssd yeah: [FONT=courier new]2.2.3-3ubuntu0.12[/FONT]
So this version has some backported bug fixes from newer versions of sssd - that's good to know. But I guess there could be some bugs that only happen on Focal 20.04.

---

