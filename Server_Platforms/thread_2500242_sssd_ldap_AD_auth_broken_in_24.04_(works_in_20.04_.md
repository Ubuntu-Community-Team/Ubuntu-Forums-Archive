---
title: "sssd ldap AD auth broken in 24.04 (works in 20.04 and 22.04)"
date: 2024-08-27
forum: Server Platforms
---

### Post by midr-tietoevry on 2024-08-27
hello all,
I've been tasked to provide AD account auth for some applications and AD integration using kerberos/realmd should not be done, so I have set up sssd with ldap integration on a fresh installed 24.04 server. Sssd connects to the AD and user id lookups work fine (ie getent passwd <AD user>) but any authentication attemps fail with error "su: Authentication failure".
I've put on full debug logs in sssd, nss, pam and domain sections, but nothing more specific then this is logged:
```

[FONT=&amp][COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [pam] [pam_dp_send_req] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0100[/COLOR]): [CID[COLOR=#6a9955]#1] Sending request with the following data:[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [pam] [pam_print_data] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0100[/COLOR]): [CID[COLOR=#6a9955]#1] command: SSS_PAM_AUTHENTICATE[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [pam] [pam_print_data] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0100[/COLOR]): [CID[COLOR=#6a9955]#1] domain: domain[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [pam] [pam_print_data] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0100[/COLOR]): [CID[COLOR=#6a9955]#1] user: USER@domain[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [pam] [pam_print_data] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0100[/COLOR]): [CID[COLOR=#6a9955]#1] service: sshd[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [pam] [pam_print_data] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0100[/COLOR]): [CID[COLOR=#6a9955]#1] tty: ssh[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [pam] [pam_print_data] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0100[/COLOR]): [CID[COLOR=#6a9955]#1] ruser: not set[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [pam] [pam_print_data] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0100[/COLOR]): [CID[COLOR=#6a9955]#1] rhost: 1.2.3.4[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [pam] [pam_print_data] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0100[/COLOR]): [CID[COLOR=#6a9955]#1] authtok type: 1 (Password)[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [pam] [pam_print_data] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0100[/COLOR]): [CID[COLOR=#6a9955]#1] newauthtok type: 0 (No authentication token available)[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [pam] [pam_print_data] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0100[/COLOR]): [CID[COLOR=#6a9955]#1] priv: 1[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [pam] [pam_print_data] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0100[/COLOR]): [CID[COLOR=#6a9955]#1] cli_pid: 4729[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [pam] [pam_print_data] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0100[/COLOR]): [CID[COLOR=#6a9955]#1] child_pid: 0[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [pam] [pam_print_data] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0100[/COLOR]): [CID[COLOR=#6a9955]#1] logon name: USER[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [pam] [pam_print_data] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0100[/COLOR]): [CID[COLOR=#6a9955]#1] flags: 1[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [pam] [pam_dom_forwarder] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0100[/COLOR]): [CID[COLOR=#6a9955]#1] pam_dp_send_req returned 0[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [pam] [sbus_dispatch] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]4000[/COLOR]): Dispatching.[/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [pam] [pam_dp_send_req_done] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0200[/COLOR]): [CID[COLOR=#6a9955]#1] received: [9 (Authentication service cannot retrieve authentication info)][domain][/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [pam] [pam_reply] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]4000[/COLOR]): [CID[COLOR=#6a9955]#1] pam_reply initially called with result [9]: Authentication service cannot retrieve authentication info. this result might be changed during processing[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [pam] [pam_reply] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0400[/COLOR]): [CID[COLOR=#6a9955]#1] Local auth policy allowed: smartcard [False], passkey [False][/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [pam] [filter_responses] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0100[/COLOR]): [CID[COLOR=#6a9955]#1] PAM response filter: [ENV:KRB5CCNAME:sudo].[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [pam] [filter_responses] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0100[/COLOR]): [CID[COLOR=#6a9955]#1] PAM response filter: [ENV:KRB5CCNAME:sudo-i].[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [pam] [pam_reply] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0200[/COLOR]): [CID[COLOR=#6a9955]#1] blen: 33[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [pam] [pam_reply] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0200[/COLOR]): [CID[COLOR=#6a9955]#1] Returning [9]: Authentication service cannot retrieve authentication info to the client[/COLOR][/COLOR]
[COLOR=#cccccc]

[/COLOR][COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [be[domain]] [pam_print_data] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0100[/COLOR]): command: SSS_PAM_AUTHENTICATE[/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [be[domain]] [pam_print_data] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0100[/COLOR]): domain: domain[/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [be[domain]] [pam_print_data] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0100[/COLOR]): user: USER[COLOR=#d4d4d4]@[/COLOR]domain[/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [be[domain]] [pam_print_data] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0100[/COLOR]): service: sshd[/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [be[domain]] [pam_print_data] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0100[/COLOR]): tty: ssh[/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [be[domain]] [pam_print_data] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0100[/COLOR]): ruser: [/COLOR]
[COLOR=#cccccc]([/COLOR][COLOR=#B5CEA8]2024[/COLOR][COLOR=#D4D4D4]-[/COLOR][COLOR=#B5CEA8]0[/COLOR][COLOR=#F44747]8[/COLOR][COLOR=#D4D4D4]-[/COLOR][COLOR=#B5CEA8]26[/COLOR][COLOR=#B5CEA8]12[/COLOR][COLOR=#cccccc]:[/COLOR][COLOR=#B5CEA8]0[/COLOR][COLOR=#F44747]5[/COLOR][COLOR=#cccccc]:[/COLOR][COLOR=#B5CEA8]27[/COLOR][COLOR=#cccccc]): [be[domain]] [pam_print_data] ([/COLOR][COLOR=#569CD6]0x[/COLOR][COLOR=#B5CEA8]0100[/COLOR][COLOR=#cccccc]): rhost: [/COLOR][COLOR=#b5cea8]1.2.3.4[/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [be[domain]] [pam_print_data] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0100[/COLOR]): authtok [COLOR=#4ec9b0]type[/COLOR]: [COLOR=#b5cea8]1[/COLOR] (Password)[/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [be[domain]] [pam_print_data] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0100[/COLOR]): newauthtok [COLOR=#4ec9b0]type[/COLOR]: [COLOR=#b5cea8]0[/COLOR] (No authentication token available)[/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [be[domain]] [pam_print_data] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0100[/COLOR]): priv: [COLOR=#b5cea8]1[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [be[domain]] [pam_print_data] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0100[/COLOR]): cli_pid: [COLOR=#b5cea8]4729[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [be[domain]] [pam_print_data] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0100[/COLOR]): child_pid: [COLOR=#b5cea8]0[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [be[domain]] [pam_print_data] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0100[/COLOR]): logon name: [COLOR=#569cd6]not[/COLOR] [COLOR=#4ec9b0]set[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [be[domain]] [pam_print_data] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0100[/COLOR]): flags: [COLOR=#b5cea8]0[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [be[domain]] [dp_attach_req] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0400[/COLOR]): [RID[COLOR=#6a9955]#4] DP Request [PAM Authenticate #4]: REQ_TRACE: New request. [sssd.pam CID #1] Flags [0000].[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [be[domain]] [dp_attach_req] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0400[/COLOR]): [RID[COLOR=#6a9955]#4] [CID #1] Backend is offline! Using cached data if available[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [be[domain]] [dp_attach_req] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0400[/COLOR]): [RID[COLOR=#6a9955]#4] Number of active DP request: 1[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [be[domain]] [sss_domain_get_state] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]1000[/COLOR]): [RID[COLOR=#6a9955]#4] Domain domain is Active[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [be[domain]] [find_password_expiration_attributes] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]4000[/COLOR]): [RID[COLOR=#6a9955]#4] No password policy requested.[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [be[domain]] [fo_resolve_service_send] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0100[/COLOR]): [RID[COLOR=#6a9955]#4] Trying to resolve service 'LDAP'[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [be[domain]] [get_server_status] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]1000[/COLOR]): [RID[COLOR=#6a9955]#4] Status of server 'domain-controller' is 'name resolved'[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [be[domain]] [get_port_status] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]1000[/COLOR]): [RID[COLOR=#6a9955]#4] Port status of port 389 for server 'domain-controller' is 'not working'[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [be[domain]] [get_port_status] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0080[/COLOR]): [RID[COLOR=#6a9955]#4] SSSD is unable to complete the full connection request, this internal status does not necessarily indicate network port issues.[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [be[domain]] [fo_resolve_service_send] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]0020[/COLOR]): [RID[COLOR=#6a9955]#4] No available servers for service 'LDAP'[/COLOR][/COLOR]
[COLOR=#CCCCCC]([COLOR=#b5cea8]2024[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]8[/COLOR][COLOR=#d4d4d4]-[/COLOR][COLOR=#b5cea8]26[/COLOR] [COLOR=#b5cea8]12[/COLOR]:[COLOR=#b5cea8]0[/COLOR][COLOR=#f44747]5[/COLOR]:[COLOR=#b5cea8]27[/COLOR]): [be[domain]] [be_resolve_server_done] ([COLOR=#569cd6]0x[/COLOR][COLOR=#b5cea8]1000[/COLOR]): [RID[COLOR=#6a9955]#4] Server [NULL] resolution failed: [5]: Input/output error[/COLOR][/COLOR]
[/FONT]

```


sssd.conf:
```

[sssd]
config_file_version = 2
services = nss,pam
domains = DOMAIN


[nss]
fallback_homedir = /home/%u
default_shell = /bin/bash


[pam]


[domain/DOMAIN]
id_provider = ldap
auth_provider = ldap
ldap_uri = ldaps://domain-controller
ldap_search_base = DOMAIN
ldap_default_bind_dn = cn=ACCOUNT,dc=DOMAIN
ldap_default_authtok_type = password
ldap_default_authtok = supersecret
ldap_user_object_class = person
ldap_group_object_class = group
ldap_schema = ad
ldap_referrals = False
ldap_id_mapping = True
use_fully_qualified_names = false
enumerate = false
cache_credentials = false
ldap_id_use_start_tls = False
ldap_tls_reqcert = demand 
ldap_tls_cacert = /etc/ssl/certs/ca-certificates.crt



```

having had challenges with sssd before in 24.04 I have spun up a 20.04 machine and copied sssd conf over to it. Here everything works. Next I did the same with a 22.04 server and here it works as well.
Having checked that I have performed a release upgrade of the 22.04 server to 24.04 and now ldap auth also works through sssd.
I have compared sssd default and systemd service files for the upgraded and installed servers and I find no difference. 

another curious observation I made is when I started trying to start sssd manually with strace to see if that brought some light into this. Nothing logged to strace, but I found that when sssd is started manually on the fresh installed 24.04 server then ldap auth works as well.
So there is something done different during systemd startup compared to manual start that stops proper ldap authentication but not other user info lookup.

My though is this is some security constraint introduced with 24.04 that is not activated when upgrading from 22.04 to 24.04 and only comes into effect when starting sssd through systemd but I don't really know where to start troubleshooting this, so any help is appreciated.

best regards
Mirco

---

### Post by mfuk on 2024-11-27
Hi Mirko,
I have the same problem.
Did you find a solution?

Best Regards
Marco

---

