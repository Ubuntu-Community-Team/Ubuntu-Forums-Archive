---
title: "Freeradius-mysql segfault on fresh install 14.04 LTS"
date: 2015-01-22
forum: Server Platforms
---

### Post by Prem029 on 2015-01-22
I have a freeradius configuration running on multiple ubuntu 12.04 LTS servers without any issues but when they were upgraded to 14.04 I am now getting segfaults. I did a fresh install of 14.04 LTS and setup freeradius-mysql and am still getting the segfault.

Here is the syslog for the error:
```
Jan 22 10:35:56 something kernel: [88778.487430] freeradius[26592]: segfault at 8 ip 00007f6d3637e67a sp 00007fff0686e378 error 4 in libc-2.19.so[7f6d362f5000+1bb000]
```

Here is the freeradius -X debug output:

```
FreeRADIUS Version 2.1.12, for host x86_64-pc-linux-gnu, built on Feb 24 2014 at 14:57:57Copyright (C) 1999-2009 The FreeRADIUS server project and contributors. 
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A 
PARTICULAR PURPOSE. 
You may redistribute copies of FreeRADIUS under the terms of the 
GNU General Public License v2. 
Starting - reading configuration files ...
including configuration file /etc/freeradius/radiusd.conf
including configuration file /etc/freeradius/clients.conf
including configuration file /etc/freeradius/canopy/dynamic-ap-list-nas-table-sql0.conf
including files in directory /etc/freeradius/modules/
including configuration file /etc/freeradius/modules/sqlcounter_expire_on_login
including configuration file /etc/freeradius/modules/realm
including configuration file /etc/freeradius/modules/chap
including configuration file /etc/freeradius/modules/policy
including configuration file /etc/freeradius/modules/krb5
including configuration file /etc/freeradius/modules/attr_rewrite
including configuration file /etc/freeradius/modules/detail.example.com
including configuration file /etc/freeradius/modules/logintime
including configuration file /etc/freeradius/modules/echo
including configuration file /etc/freeradius/modules/sradutmp
including configuration file /etc/freeradius/modules/pam
including configuration file /etc/freeradius/modules/files
including configuration file /etc/freeradius/modules/inner-eap
including configuration file /etc/freeradius/modules/radutmp
including configuration file /etc/freeradius/modules/etc_group
including configuration file /etc/freeradius/modules/ntlm_auth
including configuration file /etc/freeradius/modules/wimax
including configuration file /etc/freeradius/modules/attr_filter
including configuration file /etc/freeradius/modules/detail
including configuration file /etc/freeradius/modules/preprocess
including configuration file /etc/freeradius/modules/acct_unique
including configuration file /etc/freeradius/modules/passwd
including configuration file /etc/freeradius/modules/otp
including configuration file /etc/freeradius/modules/opendirectory
including configuration file /etc/freeradius/modules/perl
including configuration file /etc/freeradius/modules/mac2vlan
including configuration file /etc/freeradius/modules/sql_log
including configuration file /etc/freeradius/modules/checkval
including configuration file /etc/freeradius/modules/smsotp
including configuration file /etc/freeradius/modules/unix
including configuration file /etc/freeradius/modules/digest
including configuration file /etc/freeradius/modules/ippool
including configuration file /etc/freeradius/modules/expiration
including configuration file /etc/freeradius/modules/smbpasswd
including configuration file /etc/freeradius/modules/mschap
including configuration file /etc/freeradius/modules/expr
including configuration file /etc/freeradius/modules/ldap
including configuration file /etc/freeradius/modules/dynamic_clients
including configuration file /etc/freeradius/modules/detail.log
including configuration file /etc/freeradius/modules/cui
including configuration file /etc/freeradius/modules/exec
including configuration file /etc/freeradius/modules/linelog
including configuration file /etc/freeradius/modules/counter
including configuration file /etc/freeradius/modules/mac2ip
including configuration file /etc/freeradius/modules/always
including configuration file /etc/freeradius/modules/pap
including configuration file /etc/freeradius/canopy/eap-canopy.conf
including configuration file /etc/freeradius/canopy/eap-canopy-trace-inner.conf
including configuration file /etc/freeradius/sql0.conf
including configuration file /etc/freeradius/sql/mysql/dialup.conf
including configuration file /etc/freeradius/policy.conf
including files in directory /etc/freeradius/sites-enabled/
including configuration file /etc/freeradius/sites-enabled/default
including configuration file /etc/freeradius/sites-enabled/canopy-outer
including configuration file /etc/freeradius/sites-enabled/canopy-sm-tunnel
including configuration file /etc/freeradius/sites-enabled/canopy-outer-trace-both
including configuration file /etc/freeradius/sites-enabled/canopy-sm-tunnel-trace
including configuration file /etc/freeradius/sites-enabled/canopy-outer-trace-inner
including configuration file /etc/freeradius/sites-enabled/canopy-outer-trace
main {
    user = "freerad"
    group = "freerad"
    allow_core_dumps = no
}
including dictionary file /etc/freeradius/dictionary
main {
    name = "freeradius"
    prefix = "/usr"
    localstatedir = "/var"
    sbindir = "/usr/sbin"
    logdir = "/var/log/freeradius"
    run_dir = "/var/run/freeradius"
    libdir = "/usr/lib/freeradius"
    radacctdir = "/var/log/freeradius/radacct"
    hostname_lookups = no
    max_request_time = 30
    cleanup_delay = 5
    max_requests = 262144
    pidfile = "/var/run/freeradius/freeradius.pid"
    checkrad = "/usr/sbin/checkrad"
    debug_level = 0
    proxy_requests = no
 log {
    stripped_names = no
    auth = yes
    auth_badpass = yes
    auth_goodpass = no
 }
 security {
    max_attributes = 200
    reject_delay = 1
    status_server = yes
 }
}
radiusd: #### Loading Realms and Home Servers ####
radiusd: #### Loading Clients ####
 client localhost {
    ipaddr = 127.0.0.1
    require_message_authenticator = no
    secret = "testyrad"
    nastype = "other"
 }
 client dynamic-canopy-aps {
    ipaddr = 10.0.0.0
    netmask = 8
    require_message_authenticator = no
    dynamic_clients = "dynamic_canopy_ap_server"
    lifetime = 86400
 }
radiusd: #### Instantiating modules ####
 instantiate {
 Module: Linked to module rlm_exec
 Module: Instantiating module "exec" from file /etc/freeradius/modules/exec
  exec {
    wait = no
    input_pairs = "request"
    shell_escape = yes
  }
 Module: Linked to module rlm_expr
 Module: Instantiating module "expr" from file /etc/freeradius/modules/expr
 Module: Linked to module rlm_expiration
 Module: Instantiating module "expiration" from file /etc/freeradius/modules/expiration
  expiration {
    reply-message = "Password Has Expired  "
  }
 Module: Linked to module rlm_logintime
 Module: Instantiating module "logintime" from file /etc/freeradius/modules/logintime
  logintime {
    reply-message = "You are calling outside your allowed timespan  "
    minimum-timeout = 60
  }
 }
radiusd: #### Loading Virtual Servers ####
server { # from file /etc/freeradius/radiusd.conf
 modules {
  Module: Creating Post-Auth-Type = REJECT
 Module: Checking authenticate {...} for more modules to load
 Module: Linked to module rlm_pap
 Module: Instantiating module "pap" from file /etc/freeradius/modules/pap
  pap {
    encryption_scheme = "auto"
    auto_header = no
  }
 Module: Linked to module rlm_chap
 Module: Instantiating module "chap" from file /etc/freeradius/modules/chap
 Module: Linked to module rlm_mschap
 Module: Instantiating module "mschap" from file /etc/freeradius/modules/mschap
  mschap {
    use_mppe = yes
    require_encryption = no
    require_strong = no
    with_ntdomain_hack = no
    allow_retry = yes
  }
 Module: Linked to module rlm_unix
 Module: Instantiating module "unix" from file /etc/freeradius/modules/unix
  unix {
    radwtmp = "/var/log/freeradius/radwtmp"
  }
 Module: Checking authorize {...} for more modules to load
 Module: Linked to module rlm_preprocess
 Module: Instantiating module "preprocess" from file /etc/freeradius/modules/preprocess
  preprocess {
    huntgroups = "/etc/freeradius/huntgroups"
    hints = "/etc/freeradius/hints"
    with_ascend_hack = no
    ascend_channels_per_line = 23
    with_ntdomain_hack = no
    with_specialix_jetstream_hack = no
    with_cisco_vsa_hack = no
    with_alvarion_vsa_hack = no
  }
 Module: Linked to module rlm_realm
 Module: Instantiating module "suffix" from file /etc/freeradius/modules/realm
  realm suffix {
    format = "suffix"
    delimiter = "@"
    ignore_default = no
    ignore_null = no
  }
 Module: Linked to module rlm_files
 Module: Instantiating module "files" from file /etc/freeradius/modules/files
  files {
    usersfile = "/etc/freeradius/users"
    acctusersfile = "/etc/freeradius/acct_users"
    preproxy_usersfile = "/etc/freeradius/preproxy_users"
    compat = "no"
  }
 Module: Linked to module rlm_sql
 Module: Instantiating module "sql0" from file /etc/freeradius/sql0.conf
  sql sql0 {
    driver = "rlm_sql_mysql"
    server = "127.0.0.1"
    port = ""
    login = "itsalogin"
    password = "itsapass"
    radius_db = "radius"
    read_groups = yes
    sqltrace = no
    sqltracefile = "/var/log/freeradius/sqltrace.sql"
    readclients = no
    deletestalesessions = yes
    num_sql_socks = 15
    lifetime = 1200
    max_queries = 0
    sql_user_name = "%{User-Name}"
    default_user_profile = ""
    nas_query = "SELECT id, nasname, shortname, type, secret, server FROM nas"
    authorize_check_query = "SELECT id, username, attribute, value, op           FROM radcheck           WHERE username = '%{SQL-User-Name}'           ORDER BY id"
    authorize_reply_query = "SELECT id, username, attribute, value, op           FROM radreply           WHERE username = '%{SQL-User-Name}'           ORDER BY id"
    authorize_group_check_query = "SELECT id, groupname, attribute,           Value, op           FROM radgroupcheck           WHERE groupname = '%{Sql-Group}'           ORDER BY id"
    authorize_group_reply_query = "SELECT id, groupname, attribute,           value, op           FROM radgroupreply           WHERE groupname = '%{Sql-Group}'           ORDER BY id"
    accounting_onoff_query = "          UPDATE radacct           SET              acctstoptime       =  '%S',              acctsessiontime    =  unix_timestamp('%S') -                                    unix_timestamp(acctstarttime),              acctterminatecause =  '%{Acct-Terminate-Cause}',              acctstopdelay      =  %{%{Acct-Delay-Time}:-0}           WHERE acctstoptime IS NULL           AND nasipaddress      =  '%{NAS-IP-Address}'           AND acctstarttime     <= '%S'"
    accounting_update_query = "           UPDATE radacct           SET              framedipaddress = '%{Framed-IP-Address}',              acctsessiontime     = '%{Acct-Session-Time}',              acctinputoctets     = '%{%{Acct-Input-Gigawords}:-0}'  << 32 |                                    '%{%{Acct-Input-Octets}:-0}',              acctoutputoctets    = '%{%{Acct-Output-Gigawords}:-0}' << 32 |                                    '%{%{Acct-Output-Octets}:-0}'           WHERE acctsessionid = '%{Acct-Session-Id}'           AND username        = '%{SQL-User-Name}'           AND nasipaddress    = '%{NAS-IP-Address}'"
    accounting_update_query_alt = "           INSERT INTO radacct             (acctsessionid,    acctuniqueid,      username,              realm,            nasipaddress,      nasportid,              nasporttype,      acctstarttime,     acctsessiontime,              acctauthentic,    connectinfo_start, acctinputoctets,              acctoutputoctets, calledstationid,   callingstationid,              servicetype,      framedprotocol,    framedipaddress,              acctstartdelay,   xascendsessionsvrkey)           VALUES             ('%{Acct-Session-Id}', '%{Acct-Unique-Session-Id}',              '%{SQL-User-Name}',              '%{Realm}', '%{NAS-IP-Address}', '%{NAS-Port}',              '%{NAS-Port-Type}',              DATE_SUB('%S',                       INTERVAL (%{%{Acct-Session-Time}:-0} +                                 %{%{Acct-Delay-Time}:-0}) SECOND),                       '%{Acct-Session-Time}',              '%{Acct-Authentic}', '',              '%{%{Acct-Input-Gigawords}:-0}' << 32 |              '%{%{Acct-Input-Octets}:-0}',              '%{%{Acct-Output-Gigawords}:-0}' << 32 |              '%{%{Acct-Output-Octets}:-0}',              '%{Called-Station-Id}', '%{Calling-Station-Id}',              '%{Service-Type}', '%{Framed-Protocol}',              '%{Framed-IP-Address}',              '0', '%{X-Ascend-Session-Svr-Key}')"
    accounting_start_query = "           INSERT INTO radacct             (acctsessionid,    acctuniqueid,     username,              realm,            nasipaddress,     nasportid,              nasporttype,      acctstarttime,    acctstoptime,              acctsessiontime,  acctauthentic,    connectinfo_start,              connectinfo_stop, acctinputoctets,  acctoutputoctets,              calledstationid,  callingstationid, acctterminatecause,              servicetype,      framedprotocol,   framedipaddress,              acctstartdelay,   acctstopdelay,    xascendsessionsvrkey)           VALUES             ('%{Acct-Session-Id}', '%{Acct-Unique-Session-Id}',              '%{SQL-User-Name}',              '%{Realm}', '%{NAS-IP-Address}', '%{NAS-Port}',              '%{NAS-Port-Type}', '%S', NULL,              '0', '%{Acct-Authentic}', '%{Connect-Info}',              '', '0', '0',              '%{Called-Station-Id}', '%{Calling-Station-Id}', '',              '%{Service-Type}', '%{Framed-Protocol}', '%{Framed-IP-Address}',              '%{%{Acct-Delay-Time}:-0}', '0', '%{X-Ascend-Session-Svr-Key}')"
    accounting_start_query_alt = "           UPDATE radacct SET              acctstarttime     = '%S',              acctstartdelay    = '%{%{Acct-Delay-Time}:-0}',              connectinfo_start = '%{Connect-Info}'           WHERE acctsessionid  = '%{Acct-Session-Id}'           AND username         = '%{SQL-User-Name}'           AND nasipaddress     = '%{NAS-IP-Address}'"
    accounting_stop_query = "           UPDATE radacct SET              acctstoptime       = '%S',              acctsessiontime    = '%{Acct-Session-Time}',              acctinputoctets    = '%{%{Acct-Input-Gigawords}:-0}' << 32 |                                   '%{%{Acct-Input-Octets}:-0}',              acctoutputoctets   = '%{%{Acct-Output-Gigawords}:-0}' << 32 |                                   '%{%{Acct-Output-Octets}:-0}',              acctterminatecause = '%{Acct-Terminate-Cause}',              acctstopdelay      = '%{%{Acct-Delay-Time}:-0}',              connectinfo_stop   = '%{Connect-Info}'           WHERE acctsessionid   = '%{Acct-Session-Id}'           AND username          = '%{SQL-User-Name}'           AND nasipaddress      = '%{NAS-IP-Address}'"
    accounting_stop_query_alt = "           INSERT INTO radacct             (acctsessionid, acctuniqueid, username,              realm, nasipaddress, nasportid,              nasporttype, acctstarttime, acctstoptime,              acctsessiontime, acctauthentic, connectinfo_start,              connectinfo_stop, acctinputoctets, acctoutputoctets,              calledstationid, callingstationid, acctterminatecause,              servicetype, framedprotocol, framedipaddress,              acctstartdelay, acctstopdelay)           VALUES             ('%{Acct-Session-Id}', '%{Acct-Unique-Session-Id}',              '%{SQL-User-Name}',              '%{Realm}', '%{NAS-IP-Address}', '%{NAS-Port}',              '%{NAS-Port-Type}',              DATE_SUB('%S',                  INTERVAL (%{%{Acct-Session-Time}:-0} +                  %{%{Acct-Delay-Time}:-0}) SECOND),              '%S', '%{Acct-Session-Time}', '%{Acct-Authentic}', '',              '%{Connect-Info}',              '%{%{Acct-Input-Gigawords}:-0}' << 32 |              '%{%{Acct-Input-Octets}:-0}',              '%{%{Acct-Output-Gigawords}:-0}' << 32 |              '%{%{Acct-Output-Octets}:-0}',              '%{Called-Station-Id}', '%{Calling-Station-Id}',              '%{Acct-Terminate-Cause}',              '%{Service-Type}', '%{Framed-Protocol}', '%{Framed-IP-Address}',              '0', '%{%{Acct-Delay-Time}:-0}')"
    group_membership_query = "SELECT groupname           FROM radusergroup           WHERE username = '%{SQL-User-Name}'           ORDER BY priority"
    connect_failure_retry_delay = 60
    simul_count_query = ""
    simul_verify_query = "SELECT radacctid, acctsessionid, username,                                nasipaddress, nasportid, framedipaddress,                                callingstationid, framedprotocol                                FROM radacct                                WHERE username = '%{SQL-User-Name}'                                AND acctstoptime IS NULL"
    postauth_query = "INSERT INTO radpostauth                           (username, pass, reply, authdate)                           VALUES (                           '%{User-Name}',                           '%{%{User-Password}:-%{Chap-Password}}',                           '%{reply:Packet-Type}', '%S')"
    safe-characters = "@abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789.-_: /"
  }
rlm_sql Creating new attribute sql0-SQL-Group
rlm_sql: Registering sql_groupcmp for sql0-SQL-Group
rlm_sql (sql0): Driver rlm_sql_mysql (module rlm_sql_mysql) loaded and linked
rlm_sql (sql0): Attempting to connect to ispdone@127.0.0.1:/radius
rlm_sql (sql0): starting 0
rlm_sql (sql0): Attempting to connect rlm_sql_mysql #0
rlm_sql_mysql: Starting connect to MySQL server for #0
rlm_sql (sql0): Connected new DB handle, #0
rlm_sql (sql0): starting 1
rlm_sql (sql0): Attempting to connect rlm_sql_mysql #1
rlm_sql_mysql: Starting connect to MySQL server for #1
rlm_sql (sql0): Connected new DB handle, #1
rlm_sql (sql0): starting 2
rlm_sql (sql0): Attempting to connect rlm_sql_mysql #2
rlm_sql_mysql: Starting connect to MySQL server for #2
rlm_sql (sql0): Connected new DB handle, #2
rlm_sql (sql0): starting 3
rlm_sql (sql0): Attempting to connect rlm_sql_mysql #3
rlm_sql_mysql: Starting connect to MySQL server for #3
rlm_sql (sql0): Connected new DB handle, #3
rlm_sql (sql0): starting 4
rlm_sql (sql0): Attempting to connect rlm_sql_mysql #4
rlm_sql_mysql: Starting connect to MySQL server for #4
rlm_sql (sql0): Connected new DB handle, #4
rlm_sql (sql0): starting 5
rlm_sql (sql0): Attempting to connect rlm_sql_mysql #5
rlm_sql_mysql: Starting connect to MySQL server for #5
rlm_sql (sql0): Connected new DB handle, #5
rlm_sql (sql0): starting 6
rlm_sql (sql0): Attempting to connect rlm_sql_mysql #6
rlm_sql_mysql: Starting connect to MySQL server for #6
rlm_sql (sql0): Connected new DB handle, #6
rlm_sql (sql0): starting 7
rlm_sql (sql0): Attempting to connect rlm_sql_mysql #7
rlm_sql_mysql: Starting connect to MySQL server for #7
rlm_sql (sql0): Connected new DB handle, #7
rlm_sql (sql0): starting 8
rlm_sql (sql0): Attempting to connect rlm_sql_mysql #8
rlm_sql_mysql: Starting connect to MySQL server for #8
rlm_sql (sql0): Connected new DB handle, #8
rlm_sql (sql0): starting 9
rlm_sql (sql0): Attempting to connect rlm_sql_mysql #9
rlm_sql_mysql: Starting connect to MySQL server for #9
rlm_sql (sql0): Connected new DB handle, #9
rlm_sql (sql0): starting 10
rlm_sql (sql0): Attempting to connect rlm_sql_mysql #10
rlm_sql_mysql: Starting connect to MySQL server for #10
rlm_sql (sql0): Connected new DB handle, #10
rlm_sql (sql0): starting 11
rlm_sql (sql0): Attempting to connect rlm_sql_mysql #11
rlm_sql_mysql: Starting connect to MySQL server for #11
rlm_sql (sql0): Connected new DB handle, #11
rlm_sql (sql0): starting 12
rlm_sql (sql0): Attempting to connect rlm_sql_mysql #12
rlm_sql_mysql: Starting connect to MySQL server for #12
rlm_sql (sql0): Connected new DB handle, #12
rlm_sql (sql0): starting 13
rlm_sql (sql0): Attempting to connect rlm_sql_mysql #13
rlm_sql_mysql: Starting connect to MySQL server for #13
rlm_sql (sql0): Connected new DB handle, #13
rlm_sql (sql0): starting 14
rlm_sql (sql0): Attempting to connect rlm_sql_mysql #14
rlm_sql_mysql: Starting connect to MySQL server for #14
rlm_sql (sql0): Connected new DB handle, #14
 Module: Checking preacct {...} for more modules to load
 Module: Linked to module rlm_acct_unique
 Module: Instantiating module "acct_unique" from file /etc/freeradius/modules/acct_unique
  acct_unique {
    key = "User-Name, Acct-Session-Id, NAS-IP-Address, Client-IP-Address, NAS-Port"
  }
 Module: Checking accounting {...} for more modules to load
 Module: Linked to module rlm_attr_filter
 Module: Instantiating module "attr_filter.accounting_response" from file /etc/freeradius/modules/attr_filter
  attr_filter attr_filter.accounting_response {
    attrsfile = "/etc/freeradius/attrs.accounting_response"
    key = "%{User-Name}"
    relaxed = no
  }
 Module: Checking session {...} for more modules to load
 Module: Checking post-auth {...} for more modules to load
 Module: Instantiating module "attr_filter.access_reject" from file /etc/freeradius/modules/attr_filter
  attr_filter attr_filter.access_reject {
    attrsfile = "/etc/freeradius/attrs.access_reject"
    key = "%{User-Name}"
    relaxed = no
  }
 } # modules
} # server
server dynamic_canopy_ap_server { # from file /etc/freeradius/canopy/dynamic-ap-list-nas-table-sql0.conf
 modules {
 Module: Checking authorize {...} for more modules to load
 Module: Linked to module rlm_always
 Module: Instantiating module "ok" from file /etc/freeradius/modules/always
  always ok {
    rcode = "ok"
    simulcount = 0
    mpp = no
  }
 } # modules
} # server
server canopy-outer { # from file /etc/freeradius/sites-enabled/canopy-outer
 modules {
  Module: Creating Auth-Type = canopy-eap
 Module: Checking authenticate {...} for more modules to load
 Module: Linked to module rlm_eap
 Module: Instantiating module "canopy-eap" from file /etc/freeradius/canopy/eap-canopy.conf
  eap canopy-eap {
    default_eap_type = "tls"
    timer_expire = 60
    ignore_unknown_eap_types = no
    cisco_accounting_username_bug = no
    max_sessions = 4096
  }
 Module: Linked to sub-module rlm_eap_tls
 Module: Instantiating eap-tls
   tls {
    rsa_key_exchange = no
    dh_key_exchange = yes
    rsa_key_length = 512
    dh_key_length = 512
    verify_depth = 0
    pem_file_type = yes
    private_key_file = "/etc/freeradius/canopy/certs/abi/serverkey.key"
    certificate_file = "/etc/freeradius/canopy/certs/abi/server.crt"
    CA_file = "/etc/freeradius/canopy/certs/abi/abicrt.pem"
    private_key_password = "somepass"
    dh_file = "/etc/freeradius/canopy/certs/abi/dh"
    random_file = "/dev/urandom"
    fragment_size = 1024
    include_length = yes
    check_crl = no
    cipher_list = "DEFAULT"
    make_cert_command = "/etc/freeradius/canopy/certs/abi/bootstrap"
    ecdh_curve = "prime256v1"
    cache {
    enable = no
    lifetime = 24
    max_entries = 255
    }
   }
 Module: Linked to sub-module rlm_eap_ttls
 Module: Instantiating eap-ttls
   ttls {
    default_eap_type = "md5"
    copy_request_to_tunnel = no
    use_tunneled_reply = yes
    virtual_server = "canopy-sm-tunnel"
    include_length = yes
   }
 Module: Linked to sub-module rlm_eap_peap
 Module: Instantiating eap-peap
   peap {
    default_eap_type = "mschapv2"
    copy_request_to_tunnel = no
    use_tunneled_reply = no
    proxy_tunneled_request_as_eap = yes
    virtual_server = "canopy-sm-tunnel"
    soh = no
   }
 Module: Linked to sub-module rlm_eap_mschapv2
 Module: Instantiating eap-mschapv2
   mschapv2 {
    with_ntdomain_hack = no
    send_error = no
   }
 Module: Checking authorize {...} for more modules to load
 Module: Checking preacct {...} for more modules to load
 Module: Checking accounting {...} for more modules to load
 Module: Linked to module rlm_detail
 Module: Instantiating module "detail" from file /etc/freeradius/modules/detail
  detail {
    detailfile = "/var/log/freeradius/radacct/%{Client-IP-Address}/detail-%Y%m%d"
    header = "%t"
    detailperm = 384
    dirperm = 493
    locking = no
    log_packet_header = no
  }
 Module: Linked to module rlm_radutmp
 Module: Instantiating module "radutmp" from file /etc/freeradius/modules/radutmp
  radutmp {
    filename = "/var/log/freeradius/radutmp"
    username = "%{User-Name}"
    case_sensitive = yes
    check_with_nas = yes
    perm = 384
    callerid = yes
  }
 Module: Checking session {...} for more modules to load
 Module: Checking post-proxy {...} for more modules to load
 Module: Checking post-auth {...} for more modules to load
 } # modules
} # server
server canopy-sm-tunnel { # from file /etc/freeradius/sites-enabled/canopy-sm-tunnel
 modules {
 Module: Checking authenticate {...} for more modules to load
 Module: Checking authorize {...} for more modules to load
 Module: Checking session {...} for more modules to load
 Module: Checking post-proxy {...} for more modules to load
 Module: Checking post-auth {...} for more modules to load
 } # modules
} # server
server canopy-outer-trace-both { # from file /etc/freeradius/sites-enabled/canopy-outer-trace-both
 modules {
  Module: Creating Auth-Type = canopy-eap-trace-tunnel
 Module: Checking authenticate {...} for more modules to load
 Module: Instantiating module "canopy-eap-trace-tunnel" from file /etc/freeradius/canopy/eap-canopy-trace-inner.conf
  eap canopy-eap-trace-tunnel {
    default_eap_type = "tls"
    timer_expire = 60
    ignore_unknown_eap_types = no
    cisco_accounting_username_bug = no
    max_sessions = 4096
  }
 Module: Linked to sub-module rlm_eap_tls
 Module: Instantiating eap-tls
   tls {
    rsa_key_exchange = no
    dh_key_exchange = yes
    rsa_key_length = 512
    dh_key_length = 512
    verify_depth = 0
    pem_file_type = yes
    private_key_file = "/etc/freeradius/canopy/certs/abi/serverkey.key"
    certificate_file = "/etc/freeradius/canopy/certs/abi/server.crt"
    CA_file = "/etc/freeradius/canopy/certs/abi/abicrt.pem"
    private_key_password = "somepass"
    dh_file = "/etc/freeradius/canopy/certs/abi/dh"
    random_file = "/dev/urandom"
    fragment_size = 1024
    include_length = yes
    check_crl = no
    cipher_list = "DEFAULT"
    make_cert_command = "/etc/freeradius/canopy/certs/abi/bootstrap"
    ecdh_curve = "prime256v1"
    cache {
    enable = no
    lifetime = 24
    max_entries = 255
    }
   }
 Module: Linked to sub-module rlm_eap_ttls
 Module: Instantiating eap-ttls
   ttls {
    default_eap_type = "md5"
    copy_request_to_tunnel = no
    use_tunneled_reply = yes
    virtual_server = "canopy-sm-tunnel-trace"
    include_length = yes
   }
 Module: Linked to sub-module rlm_eap_peap
 Module: Instantiating eap-peap
   peap {
    default_eap_type = "mschapv2"
    copy_request_to_tunnel = no
    use_tunneled_reply = no
    proxy_tunneled_request_as_eap = yes
    virtual_server = "canopy-sm-tunnel-trace"
    soh = no
   }
 Module: Linked to sub-module rlm_eap_mschapv2
 Module: Instantiating eap-mschapv2
   mschapv2 {
    with_ntdomain_hack = no
    send_error = no
   }
 Module: Checking authorize {...} for more modules to load
 Module: Checking preacct {...} for more modules to load
 Module: Checking accounting {...} for more modules to load
 Module: Checking session {...} for more modules to load
 Module: Checking post-proxy {...} for more modules to load
 Module: Checking post-auth {...} for more modules to load
 } # modules
} # server
server canopy-sm-tunnel-trace { # from file /etc/freeradius/sites-enabled/canopy-sm-tunnel-trace
 modules {
 Module: Checking authenticate {...} for more modules to load
 Module: Checking authorize {...} for more modules to load
 Module: Checking session {...} for more modules to load
 Module: Checking post-proxy {...} for more modules to load
 Module: Checking post-auth {...} for more modules to load
 } # modules
} # server
server canopy-outer-trace-inner { # from file /etc/freeradius/sites-enabled/canopy-outer-trace-inner
 modules {
 Module: Checking authenticate {...} for more modules to load
 Module: Checking authorize {...} for more modules to load
 Module: Checking preacct {...} for more modules to load
 Module: Checking accounting {...} for more modules to load
 Module: Checking session {...} for more modules to load
 Module: Checking post-proxy {...} for more modules to load
 Module: Checking post-auth {...} for more modules to load
 } # modules
} # server
server canopy-outer-trace { # from file /etc/freeradius/sites-enabled/canopy-outer-trace
 modules {
 Module: Checking authenticate {...} for more modules to load
 Module: Checking authorize {...} for more modules to load
 Module: Checking preacct {...} for more modules to load
 Module: Checking accounting {...} for more modules to load
 Module: Checking session {...} for more modules to load
 Module: Checking post-proxy {...} for more modules to load
 Module: Checking post-auth {...} for more modules to load
 } # modules
} # server
radiusd: #### Opening IP addresses and Ports ####
listen {
    type = "auth"
    ipaddr = *
    port = 0
}
listen {
    type = "acct"
    ipaddr = *
    port = 0
}
Listening on authentication address * port 1812
Listening on accounting address * port 1813
Ready to process requests.
rad_recv: Access-Request packet from host 10.23.34.3 port 1227, id=0, length=90
server dynamic_canopy_ap_server {
rlm_sql (sql0): Reserving sql socket id: 14
rlm_sql (sql0): Released sql socket id: 14
rlm_sql (sql0): Reserving sql socket id: 13
rlm_sql (sql0): Released sql socket id: 13
rlm_sql (sql0): Reserving sql socket id: 12
rlm_sql (sql0): Released sql socket id: 12
rlm_sql (sql0): Reserving sql socket id: 11
rlm_sql (sql0): Released sql socket id: 11
} # server dynamic_canopy_ap_server
Segmentation fault (core dumped)



```

---

