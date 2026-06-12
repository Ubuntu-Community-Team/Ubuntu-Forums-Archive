---
title: "sssd ldap user login failed"
date: 2023-05-15
forum: Ubuntu Cloud and Juju
---

### Post by vladpasichnyk123 on 2023-05-15
I'm trying to configure the sssd service to connect to my OpenDJ Ldap server for login with the users created within ldap.
The service connects to the server, looks up the users and saves them. I can list them with getent passwd. The problem is when I try to login with these ldap users. After inserting the password I get the error "Incorrect identification".

My /etc/sssd/sssd.conf configuration:

[sssd]
debug_level = 9
domains = LDAP
config_file_version = 2
services = nss, pam, ifp


[domain/LDAP]
id_provider = ldap
auth_provider = ldap
access_provider = simple
ldap_uri = ldap://server.com


ldap_search_base = ou=people,o=gluu


ldap_default_bind_dn = cn=directory manager


ldap_default_authtok_type = password
ldap_default_authtok = 'mypassword'


ldap_id_use_start_tls = False
ldap_schema = rfc2307bis
debug_level = 10
#cache_credentials = true
enumerate = true


[nss]
debug_level = 9


[ifp]
debug_level = 9


[pam]
debug_level = 10



Logs on /var/log/sssd/sssd_pam.log :

(Mon May 15 16:20:28 2023) [pam] [sss_parse_name_for_domains] (0x0200): name 'prova' matched without domain, user is prova
(Mon May 15 16:20:28 2023) [pam] [pam_print_data] (0x0100): command: SSS_PAM_AUTHENTICATE
(Mon May 15 16:20:28 2023) [pam] [pam_print_data] (0x0100): domain: not set
(Mon May 15 16:20:28 2023) [pam] [pam_print_data] (0x0100): user: prova
(Mon May 15 16:20:28 2023) [pam] [pam_print_data] (0x0100): service: su
(Mon May 15 16:20:28 2023) [pam] [pam_print_data] (0x0100): tty: pts/2
(Mon May 15 16:20:28 2023) [pam] [pam_print_data] (0x0100): ruser: vlad
(Mon May 15 16:20:28 2023) [pam] [pam_print_data] (0x0100): rhost: not set
(Mon May 15 16:20:28 2023) [pam] [pam_print_data] (0x0100): authtok type: 1
(Mon May 15 16:20:28 2023) [pam] [pam_print_data] (0x0100): newauthtok type: 0
(Mon May 15 16:20:28 2023) [pam] [pam_print_data] (0x0100): priv: 0
(Mon May 15 16:20:28 2023) [pam] [pam_print_data] (0x0100): cli_pid: 4267
(Mon May 15 16:20:28 2023) [pam] [pam_print_data] (0x0100): logon name: prova
(Mon May 15 16:20:28 2023) [pam] [pam_print_data] (0x0100): flags: 1
(Mon May 15 16:20:28 2023) [pam] [pam_initgr_check_timeout] (0x4000): User [prova] not found in PAM cache.
(Mon May 15 16:20:28 2023) [pam] [cache_req_set_plugin] (0x2000): CR #6: Setting "Initgroups by name" plugin
(Mon May 15 16:20:28 2023) [pam] [cache_req_send] (0x0400): CR #6: New request 'Initgroups by name'
(Mon May 15 16:20:28 2023) [pam] [cache_req_process_input] (0x0400): CR #6: Parsing input name [prova]
(Mon May 15 16:20:28 2023) [pam] [sss_parse_name_for_domains] (0x0200): name 'prova' matched without domain, user is prova
(Mon May 15 16:20:28 2023) [pam] [cache_req_set_name] (0x0400): CR #6: Setting name [prova]
(Mon May 15 16:20:28 2023) [pam] [cache_req_select_domains] (0x0400): CR #6: Performing a multi-domain search
(Mon May 15 16:20:28 2023) [pam] [cache_req_search_domains] (0x0400): CR #6: Search will bypass the cache and check the data provider
(Mon May 15 16:20:28 2023) [pam] [cache_req_validate_domain_type] (0x2000): Request type POSIX-only for domain LDAP type POSIX is valid
(Mon May 15 16:20:28 2023) [pam] [cache_req_set_domain] (0x0400): CR #6: Using domain [LDAP]
(Mon May 15 16:20:28 2023) [pam] [cache_req_prepare_domain_data] (0x0400): CR #6: Preparing input data for domain [LDAP] rules
(Mon May 15 16:20:28 2023) [pam] [cache_req_search_send] (0x0400): CR #6: Looking up prova@ldap
(Mon May 15 16:20:28 2023) [pam] [cache_req_search_ncache] (0x0400): CR #6: Checking negative cache for [prova@ldap]
(Mon May 15 16:20:28 2023) [pam] [sss_ncache_check_str] (0x2000): Checking negative cache for [NCE/USER/LDAP/prova@ldap]
(Mon May 15 16:20:28 2023) [pam] [cache_req_search_ncache] (0x0400): CR #6: [prova@ldap] is not present in negative cache
(Mon May 15 16:20:28 2023) [pam] [cache_req_search_dp] (0x0400): CR #6: Looking up [prova@ldap] in data provider
(Mon May 15 16:20:28 2023) [pam] [sss_dp_get_account_send] (0x0400): Creating request for [LDAP][0x3][BE_REQ_INITGROUPS][name=prova@ldap:-]
(Mon May 15 16:20:28 2023) [pam] [sbus_dispatch] (0x4000): Dispatching.
(Mon May 15 16:20:28 2023) [pam] [cache_req_search_cache] (0x0400): CR #6: Looking up [prova@ldap] in cache
(Mon May 15 16:20:28 2023) [pam] [ldb] (0x4000): Added timed event "ldb_kv_callback": 0x55b6962866a0


(Mon May 15 16:20:28 2023) [pam] [ldb] (0x4000): Added timed event "ldb_kv_timeout": 0x55b69627d740


(Mon May 15 16:20:28 2023) [pam] [ldb] (0x4000): Running timer event 0x55b6962866a0 "ldb_kv_callback"


(Mon May 15 16:20:28 2023) [pam] [ldb] (0x4000): Destroying timer event 0x55b69627d740 "ldb_kv_timeout"


(Mon May 15 16:20:28 2023) [pam] [ldb] (0x4000): Destroying timer event 0x55b6962866a0 "ldb_kv_callback"


(Mon May 15 16:20:28 2023) [pam] [ldb] (0x4000): Added timed event "ldb_kv_callback": 0x55b696286b50


(Mon May 15 16:20:28 2023) [pam] [ldb] (0x4000): Added timed event "ldb_kv_timeout": 0x55b69627f090


(Mon May 15 16:20:28 2023) [pam] [ldb] (0x4000): Running timer event 0x55b696286b50 "ldb_kv_callback"


(Mon May 15 16:20:28 2023) [pam] [ldb] (0x4000): Destroying timer event 0x55b69627f090 "ldb_kv_timeout"


(Mon May 15 16:20:28 2023) [pam] [ldb] (0x4000): Destroying timer event 0x55b696286b50 "ldb_kv_callback"


(Mon May 15 16:20:28 2023) [pam] [ldb] (0x4000): Added timed event "ldb_kv_callback": 0x55b69627f090


(Mon May 15 16:20:28 2023) [pam] [ldb] (0x4000): Added timed event "ldb_kv_timeout": 0x55b696286d30


(Mon May 15 16:20:28 2023) [pam] [ldb] (0x4000): Running timer event 0x55b69627f090 "ldb_kv_callback"


(Mon May 15 16:20:28 2023) [pam] [ldb] (0x4000): Destroying timer event 0x55b696286d30 "ldb_kv_timeout"


(Mon May 15 16:20:28 2023) [pam] [ldb] (0x4000): Destroying timer event 0x55b69627f090 "ldb_kv_callback"


(Mon May 15 16:20:28 2023) [pam] [cache_req_search_ncache_filter] (0x0400): CR #6: This request type does not support filtering result by negative cache
(Mon May 15 16:20:28 2023) [pam] [cache_req_search_done] (0x0400): CR #6: Returning updated object [prova@ldap]
(Mon May 15 16:20:28 2023) [pam] [cache_req_create_and_add_result] (0x0400): CR #6: Found 1 entries in domain LDAP
(Mon May 15 16:20:28 2023) [pam] [cache_req_done] (0x0400): CR #6: Finished: Success
(Mon May 15 16:20:28 2023) [pam] [pd_set_primary_name] (0x0400): User's primary name is prova@ldap
(Mon May 15 16:20:28 2023) [pam] [pam_initgr_cache_set] (0x2000): [prova] added to PAM initgroup cache
(Mon May 15 16:20:28 2023) [pam] [pam_dp_send_req] (0x0100): Sending request with the following data:
(Mon May 15 16:20:28 2023) [pam] [pam_print_data] (0x0100): command: SSS_PAM_AUTHENTICATE
(Mon May 15 16:20:28 2023) [pam] [pam_print_data] (0x0100): domain: LDAP
(Mon May 15 16:20:28 2023) [pam] [pam_print_data] (0x0100): user: prova@ldap
(Mon May 15 16:20:28 2023) [pam] [pam_print_data] (0x0100): service: su
(Mon May 15 16:20:28 2023) [pam] [pam_print_data] (0x0100): tty: pts/2
(Mon May 15 16:20:28 2023) [pam] [pam_print_data] (0x0100): ruser: vlad
(Mon May 15 16:20:28 2023) [pam] [pam_print_data] (0x0100): rhost: not set
(Mon May 15 16:20:28 2023) [pam] [pam_print_data] (0x0100): authtok type: 1
(Mon May 15 16:20:28 2023) [pam] [pam_print_data] (0x0100): newauthtok type: 0
(Mon May 15 16:20:28 2023) [pam] [pam_print_data] (0x0100): priv: 0
(Mon May 15 16:20:28 2023) [pam] [pam_print_data] (0x0100): cli_pid: 4267
(Mon May 15 16:20:28 2023) [pam] [pam_print_data] (0x0100): logon name: prova
(Mon May 15 16:20:28 2023) [pam] [pam_print_data] (0x0100): flags: 1
(Mon May 15 16:20:28 2023) [pam] [pam_dom_forwarder] (0x0100): pam_dp_send_req returned 0
(Mon May 15 16:20:29 2023) [pam] [sbus_dispatch] (0x4000): Dispatching.
(Mon May 15 16:20:29 2023) [pam] [pam_dp_send_req_done] (0x0200): received: [9 (El servicio de autenticación no puede recuperar la información de autenticación)][LDAP]
(Mon May 15 16:20:29 2023) [pam] [ldb] (0x4000): Added timed event "ldb_kv_callback": 0x55b6962862d0


(Mon May 15 16:20:29 2023) [pam] [ldb] (0x4000): Added timed event "ldb_kv_timeout": 0x55b696286d30


(Mon May 15 16:20:29 2023) [pam] [ldb] (0x4000): Running timer event 0x55b6962862d0 "ldb_kv_callback"


(Mon May 15 16:20:29 2023) [pam] [ldb] (0x4000): Destroying timer event 0x55b696286d30 "ldb_kv_timeout"


(Mon May 15 16:20:29 2023) [pam] [ldb] (0x4000): Destroying timer event 0x55b6962862d0 "ldb_kv_callback"


(Mon May 15 16:20:29 2023) [pam] [pam_reply] (0x4000): pam_reply initially called with result [9]: El servicio de autenticación no puede recuperar la información de autenticación. this result might be changed during processing
(Mon May 15 16:20:29 2023) [pam] [ldb] (0x4000): Added timed event "ldb_kv_callback": 0x55b6962862d0


(Mon May 15 16:20:29 2023) [pam] [ldb] (0x4000): Added timed event "ldb_kv_timeout": 0x55b69627f090


(Mon May 15 16:20:29 2023) [pam] [ldb] (0x4000): Running timer event 0x55b6962862d0 "ldb_kv_callback"


(Mon May 15 16:20:29 2023) [pam] [ldb] (0x4000): Destroying timer event 0x55b69627f090 "ldb_kv_timeout"


(Mon May 15 16:20:29 2023) [pam] [ldb] (0x4000): Destroying timer event 0x55b6962862d0 "ldb_kv_callback"


(Mon May 15 16:20:29 2023) [pam] [ldb] (0x4000): Added timed event "ldb_kv_callback": 0x55b696286b50


(Mon May 15 16:20:29 2023) [pam] [ldb] (0x4000): Added timed event "ldb_kv_timeout": 0x55b69627f090


(Mon May 15 16:20:29 2023) [pam] [ldb] (0x4000): Running timer event 0x55b696286b50 "ldb_kv_callback"


(Mon May 15 16:20:29 2023) [pam] [ldb] (0x4000): Destroying timer event 0x55b69627f090 "ldb_kv_timeout"


(Mon May 15 16:20:29 2023) [pam] [ldb] (0x4000): Destroying timer event 0x55b696286b50 "ldb_kv_callback"


(Mon May 15 16:20:29 2023) [pam] [filter_responses] (0x0100): [pam_response_filter] not available, not fatal.
(Mon May 15 16:20:29 2023) [pam] [pam_reply] (0x0200): blen: 21
(Mon May 15 16:20:29 2023) [pam] [pam_reply] (0x0200): Returning [9]: El servicio de autenticación no puede recuperar la información de autenticación to the client
(Mon May 15 16:20:31 2023) [pam] [client_recv] (0x0200): Client disconnected!
(Mon May 15 16:20:31 2023) [pam] [client_close_fn] (0x2000): Terminated client [0x55b696285820][19]
(Mon May 15 16:20:33 2023) [pam] [pam_initgr_cache_remove] (0x2000): [prova] removed from PAM initgroup cache

---

