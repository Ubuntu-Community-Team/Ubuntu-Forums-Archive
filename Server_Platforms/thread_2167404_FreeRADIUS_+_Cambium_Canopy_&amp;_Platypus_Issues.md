---
title: "FreeRADIUS + Cambium Canopy &amp; Platypus Issues"
date: 2013-08-13
forum: Server Platforms
---

### Post by Crashedata on 2013-08-13
First, I apologize if I am not posting this in the correct place. I have been trying for a week now to get FreeRADIUS integrated with the Platypus billing system (which is made by Tucows) and a Cambium Canopy (formerly Motorola Canopy) Point-to-Multipoint system for authentication and quality of service. I followed the instructions in a pdf provided by the Platypus group at Tucows to the t, including which version of Ubuntu to use (the same one I all ready use frequently at home anyways, which is 10.04), and to install FreeRADIUS using their Python script rather than the Ubuntu repositories (as it has to communicate with a separate billing server's Microsoft (yuck!) SQL database for dictionaries and user authentication). However, when I change the eap.conf file to point to the AAA Certificates provided by Cambium for the Canopy platform, it stops working.

FreeRADIUS works fine until I set up the AAA certificates, but once that has been completed nothing works any more. I have tried getting support from Tucows, to no avail. They just keep telling me to try the same stuff I all ready have. I would try to get support from Cambium, however, through email that can take weeks, and over the phone I unfortunately cannot understand most of their support reps. Any help would be appreciated.


Here is what happens when I type sudo radiusd -X into the terminal (errors are near the bottom):

> radius@radius-server:~$ sudo radiusd -X
[sudo] password for radius: 
FreeRADIUS Version 2.2.0, for host i686-pc-linux-gnu, built on Aug 12 2013 at 16:14:17
Copyright (C) 1999-2012 The FreeRADIUS server project and contributors. 
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A 
PARTICULAR PURPOSE. 
You may redistribute copies of FreeRADIUS under the terms of the 
GNU General Public License v2. 
Starting - reading configuration files ...
including configuration file /usr/local/etc/raddb/radiusd.conf
including configuration file /usr/local/etc/raddb/proxy.conf
including configuration file /usr/local/etc/raddb/clients.conf
including files in directory /usr/local/etc/raddb/modules/
including configuration file /usr/local/etc/raddb/modules/krb5
including configuration file /usr/local/etc/raddb/modules/redis
including configuration file /usr/local/etc/raddb/modules/cui
including configuration file /usr/local/etc/raddb/modules/ippool
including configuration file /usr/local/etc/raddb/modules/otp
including configuration file /usr/local/etc/raddb/modules/opendirectory
including configuration file /usr/local/etc/raddb/modules/ntlm_auth
including configuration file /usr/local/etc/raddb/modules/replicate
including configuration file /usr/local/etc/raddb/modules/sql_log
including configuration file /usr/local/etc/raddb/modules/linelog
including configuration file /usr/local/etc/raddb/modules/echo
including configuration file /usr/local/etc/raddb/modules/soh
including configuration file /usr/local/etc/raddb/modules/detail.log
including configuration file /usr/local/etc/raddb/modules/policy
including configuration file /usr/local/etc/raddb/modules/smsotp
including configuration file /usr/local/etc/raddb/modules/radutmp
including configuration file /usr/local/etc/raddb/modules/pap
including configuration file /usr/local/etc/raddb/modules/dhcp_sqlippool
including configuration file /usr/local/etc/raddb/sql/mysql/ippool-dhcp.conf
including configuration file /usr/local/etc/raddb/modules/attr_rewrite
including configuration file /usr/local/etc/raddb/modules/etc_group
including configuration file /usr/local/etc/raddb/modules/exec
including configuration file /usr/local/etc/raddb/modules/rediswho
including configuration file /usr/local/etc/raddb/modules/mschap
including configuration file /usr/local/etc/raddb/modules/perl
including configuration file /usr/local/etc/raddb/modules/unix
including configuration file /usr/local/etc/raddb/modules/digest
including configuration file /usr/local/etc/raddb/modules/sradutmp
including configuration file /usr/local/etc/raddb/modules/preprocess
including configuration file /usr/local/etc/raddb/modules/files
including configuration file /usr/local/etc/raddb/modules/mac2ip
including configuration file /usr/local/etc/raddb/modules/dynamic_clients
including configuration file /usr/local/etc/raddb/modules/always
including configuration file /usr/local/etc/raddb/modules/expiration
including configuration file /usr/local/etc/raddb/modules/mac2vlan
including configuration file /usr/local/etc/raddb/modules/pam
including configuration file /usr/local/etc/raddb/modules/sqlcounter_expire_on_login
including configuration file /usr/local/etc/raddb/modules/wimax
including configuration file /usr/local/etc/raddb/modules/inner-eap
including configuration file /usr/local/etc/raddb/modules/chap
including configuration file /usr/local/etc/raddb/modules/passwd
including configuration file /usr/local/etc/raddb/modules/acct_unique
including configuration file /usr/local/etc/raddb/modules/realm
including configuration file /usr/local/etc/raddb/modules/detail.example.com
including configuration file /usr/local/etc/raddb/modules/detail
including configuration file /usr/local/etc/raddb/modules/checkval
including configuration file /usr/local/etc/raddb/modules/cache
including configuration file /usr/local/etc/raddb/modules/logintime
including configuration file /usr/local/etc/raddb/modules/expr
including configuration file /usr/local/etc/raddb/modules/counter
including configuration file /usr/local/etc/raddb/modules/attr_filter
including configuration file /usr/local/etc/raddb/modules/smbpasswd
including configuration file /usr/local/etc/raddb/modules/ldap
including configuration file /usr/local/etc/raddb/modules/radrelay
including configuration file /usr/local/etc/raddb/eap.conf
including configuration file /usr/local/etc/raddb/sql.conf
including configuration file /usr/local/etc/raddb/sql/mssql/dialup.conf
including configuration file /usr/local/etc/raddb/policy.conf
including files in directory /usr/local/etc/raddb/sites-enabled/
including configuration file /usr/local/etc/raddb/sites-enabled/default
including configuration file /usr/local/etc/raddb/sites-enabled/control-socket
including configuration file /usr/local/etc/raddb/sites-enabled/inner-tunnel
main {
    allow_core_dumps = no
}
including dictionary file /usr/local/etc/raddb/dictionary
main {
    name = "radiusd"
    prefix = "/usr/local"
    localstatedir = "/usr/local/var"
    sbindir = "/usr/local/sbin"
    logdir = "/usr/local/var/log/radius"
    run_dir = "/usr/local/var/run/radiusd"
    libdir = "/usr/local/lib"
    radacctdir = "/usr/local/var/log/radius/radacct"
    hostname_lookups = no
    max_request_time = 30
    cleanup_delay = 5
    max_requests = 1024
    pidfile = "/usr/local/var/run/radiusd/radiusd.pid"
    checkrad = "/usr/local/sbin/checkrad"
    debug_level = 0
    proxy_requests = yes
 log {
    stripped_names = no
    auth = no
    auth_badpass = no
    auth_goodpass = no
 }
 security {
    max_attributes = 200
    reject_delay = 1
    status_server = yes
 }
}
radiusd: #### Loading Realms and Home Servers ####
 proxy server {
    retry_delay = 5
    retry_count = 3
    default_fallback = no
    dead_time = 120
    wake_all_if_all_dead = no
 }
 home_server localhost {
    ipaddr = 127.0.0.1
    port = 1812
    type = "auth"
    secret = "testing123"
    response_window = 20
    max_outstanding = 65536
    require_message_authenticator = yes
    zombie_period = 40
    status_check = "status-server"
    ping_interval = 30
    check_interval = 30
    num_answers_to_alive = 3
    num_pings_to_alive = 3
    revive_interval = 120
    status_check_timeout = 4
  coa {
    irt = 2
    mrt = 16
    mrc = 5
    mrd = 30
  }
 }
 home_server_pool my_auth_failover {
    type = fail-over
    home_server = localhost
 }
 realm example.com {
    auth_pool = my_auth_failover
 }
 realm LOCAL {
 }
radiusd: #### Loading Clients ####
 client localhost {
    ipaddr = 127.0.0.1
    require_message_authenticator = no
    secret = "testing123"
    nastype = "other"
 }
 client 10.240.1.0/24 {
    require_message_authenticator = no
    secret = "password"
    nastype = "other"
 }
radiusd: #### Instantiating modules ####
 instantiate {
 Module: Linked to module rlm_exec
 Module: Instantiating module "exec" from file /usr/local/etc/raddb/modules/exec
  exec {
    wait = no
    input_pairs = "request"
    shell_escape = yes
  }
 Module: Linked to module rlm_expr
 Module: Instantiating module "expr" from file /usr/local/etc/raddb/modules/expr
 Module: Linked to module rlm_expiration
 Module: Instantiating module "expiration" from file /usr/local/etc/raddb/modules/expiration
  expiration {
    reply-message = "Password Has Expired  "
  }
 Module: Linked to module rlm_logintime
 Module: Instantiating module "logintime" from file /usr/local/etc/raddb/modules/logintime
  logintime {
    reply-message = "You are calling outside your allowed timespan  "
    minimum-timeout = 60
  }
 }
radiusd: #### Loading Virtual Servers ####
server { # from file /usr/local/etc/raddb/radiusd.conf
 modules {
  Module: Creating Auth-Type = digest
  Module: Creating Post-Auth-Type = REJECT
 Module: Checking authenticate {...} for more modules to load
 Module: Linked to module rlm_pap
 Module: Instantiating module "pap" from file /usr/local/etc/raddb/modules/pap
  pap {
    encryption_scheme = "auto"
    auto_header = no
  }
 Module: Linked to module rlm_chap
 Module: Instantiating module "chap" from file /usr/local/etc/raddb/modules/chap
 Module: Linked to module rlm_mschap
 Module: Instantiating module "mschap" from file /usr/local/etc/raddb/modules/mschap
  mschap {
    use_mppe = yes
    require_encryption = no
    require_strong = no
    with_ntdomain_hack = no
    allow_retry = yes
  }
 Module: Linked to module rlm_digest
 Module: Instantiating module "digest" from file /usr/local/etc/raddb/modules/digest
 Module: Linked to module rlm_unix
 Module: Instantiating module "unix" from file /usr/local/etc/raddb/modules/unix
  unix {
    radwtmp = "/usr/local/var/log/radius/radwtmp"
  }
 Module: Linked to module rlm_eap
 Module: Instantiating module "eap" from file /usr/local/etc/raddb/eap.conf
  eap {
    default_eap_type = "md5"
    timer_expire = 60
    ignore_unknown_eap_types = no
    cisco_accounting_username_bug = no
    max_sessions = 4096
  }
 Module: Linked to sub-module rlm_eap_md5
 Module: Instantiating eap-md5
 Module: Linked to sub-module rlm_eap_leap
 Module: Instantiating eap-leap
 Module: Linked to sub-module rlm_eap_gtc
 Module: Instantiating eap-gtc
   gtc {
    challenge = "Password: "
    auth_type = "PAP"
   }
 Module: Linked to sub-module rlm_eap_tls
 Module: Instantiating eap-tls
   tls {
    rsa_key_exchange = no
    dh_key_exchange = yes
    rsa_key_length = 512
    dh_key_length = 512
    verify_depth = 0
    CA_path = "/usr/local/etc/raddb/certs"
    pem_file_type = yes
    private_key_file = "/usr/local/etc/raddb/certs/aaasvr_key.pem"
    certificate_file = "/usr/local/etc/raddb/certs/aaasvr_cert.pem"
    private_key_password = "password"
    dh_file = "/usr/local/etc/raddb/certs/dh"
    random_file = "/usr/local/etc/raddb/certs/random"
    fragment_size = 1024
    include_length = yes
    check_crl = no
    cipher_list = "DEFAULT"
    make_cert_command = "/usr/local/etc/raddb/certs/bootstrap"
    ecdh_curve = "prime256v1"
    cache {
    enable = no
    lifetime = 24
    max_entries = 255
    }
    verify {
    }
    ocsp {
    enable = no
    override_cert_url = yes
    url = "http://127.0.0.1/ocsp/"
    use_nonce = yes
    timeout = 0
    softfail = no
    }
   }
rlm_eap: SSL error error:00000000:lib(0):func(0):reason(0)
rlm_eap_tls: Error loading randomness
rlm_eap: Failed to initialize type tls
/usr/local/etc/raddb/eap.conf[17]: Instantiation failed for module "eap"
/usr/local/etc/raddb/sites-enabled/default[310]: Failed to find "eap" in the "modules" section.
/usr/local/etc/raddb/sites-enabled/default[252]: Errors parsing authenticate section. 
radius@radius-server:~$ 


---

