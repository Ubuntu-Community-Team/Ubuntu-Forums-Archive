---
title: "Freeradius dissociating users"
date: 2013-05-02
forum: Server Platforms
---

### Post by sdmike6 on 2013-05-02
I've done so much troubleshooting on this issue that I've hit a wall and I'm not sure how to resolve this.

I have two cisco aironet APs that authenticate with Freeradius/OpenLDAP on a server running Ubuntu 12.04 LTS.

Users are able to get onto the Wifi using their LDAP credentials but a lot of users are getting dissociated and they have to re-authenticate which is getting really annoying.

[B]Here is my /etc/freeradius/eap.conf
[/B]
```
# -*- text -*-
##
##  eap.conf -- Configuration for EAP types (PEAP, TTLS, etc.)
##
##    $Id$


#######################################################################
#
#  Whatever you do, do NOT set 'Auth-Type := EAP'.  The server
#  is smart enough to figure this out on its own.  The most
#  common side effect of setting 'Auth-Type := EAP' is that the
#  users then cannot use ANY other authentication method.
#
#  EAP types NOT listed here may be supported via the "eap2" module.
#  See experimental.conf for documentation.
#
    eap {
        #  Invoke the default supported EAP type when
        #  EAP-Identity response is received.
        #
        #  The incoming EAP messages DO NOT specify which EAP
        #  type they will be using, so it MUST be set here.
        #
        #  For now, only one default EAP type may be used at a time.
        #
        #  If the EAP-Type attribute is set by another module,
        #  then that EAP type takes precedence over the
        #  default type configured here.
        #
        default_eap_type = peap


        #  A list is maintained to correlate EAP-Response
        #  packets with EAP-Request packets.  After a
        #  configurable length of time, entries in the list
        #  expire, and are deleted.
        #
        timer_expire     = 60


        #  There are many EAP types, but the server has support
        #  for only a limited subset.  If the server receives
        #  a request for an EAP type it does not support, then
        #  it normally rejects the request.  By setting this
        #  configuration to "yes", you can tell the server to
        #  instead keep processing the request.  Another module
        #  MUST then be configured to proxy the request to
        #  another RADIUS server which supports that EAP type.
        #
        #  If another module is NOT configured to handle the
        #  request, then the request will still end up being
        #  rejected.
        ignore_unknown_eap_types = no


        # Cisco AP1230B firmware 12.2(13)JA1 has a bug.  When given
        # a User-Name attribute in an Access-Accept, it copies one
        # more byte than it should.
        #
        # We can work around it by configurably adding an extra
        # zero byte.
        cisco_accounting_username_bug = no


        #
        #  Help prevent DoS attacks by limiting the number of
        #  sessions that the server is tracking.  Most systems
        #  can handle ~30 EAP sessions/s, so the default limit
        #  of 4096 should be OK.
        max_sessions = 4096


        # Supported EAP-types


        #
        #  We do NOT recommend using EAP-MD5 authentication
        #  for wireless connections.  It is insecure, and does
        #  not provide for dynamic WEP keys.
        #
        md5 {
        }


        # Cisco LEAP
        #
        #  We do not recommend using LEAP in new deployments.  See:
        #  http://www.securiteam.com/tools/5TP012ACKE.html
        #
        #  Cisco LEAP uses the MS-CHAP algorithm (but not
        #  the MS-CHAP attributes) to perform it's authentication.
        #
        #  As a result, LEAP *requires* access to the plain-text
        #  User-Password, or the NT-Password attributes.
        #  'System' authentication is impossible with LEAP.
        #
        leap {
        }


        #  Generic Token Card.
        #
        #  Currently, this is only permitted inside of EAP-TTLS,
        #  or EAP-PEAP.  The module "challenges" the user with
        #  text, and the response from the user is taken to be
        #  the User-Password.
        #
        #  Proxying the tunneled EAP-GTC session is a bad idea,
        #  the users password will go over the wire in plain-text,
        #  for anyone to see.
        #
        gtc {
            #  The default challenge, which many clients
            #  ignore..
            #challenge = "Password: "


            #  The plain-text response which comes back
            #  is put into a User-Password attribute,
            #  and passed to another module for
            #  authentication.  This allows the EAP-GTC
            #  response to be checked against plain-text,
            #  or crypt'd passwords.
            #
            #  If you say "Local" instead of "PAP", then
            #  the module will look for a User-Password
            #  configured for the request, and do the
            #  authentication itself.
            #
            auth_type = PAP
        }


        ## EAP-TLS
        #
        #  See raddb/certs/README for additional comments
        #  on certificates.
        #
        #  If OpenSSL was not found at the time the server was
        #  built, the "tls", "ttls", and "peap" sections will
        #  be ignored.
        #
        #  Otherwise, when the server first starts in debugging
        #  mode, test certificates will be created.  See the
        #  "make_cert_command" below for details, and the README
        #  file in raddb/certs
        #
        #  These test certificates SHOULD NOT be used in a normal
        #  deployment.  They are created only to make it easier
        #  to install the server, and to perform some simple
        #  tests with EAP-TLS, TTLS, or PEAP.
        #
        #  See also:
        #
        #  http://www.dslreports.com/forum/remark,9286052~mode=flat
        #
        #  Note that you should NOT use a globally known CA here!
        #  e.g. using a Verisign cert as a "known CA" means that
        #  ANYONE who has a certificate signed by them can
        #  authenticate via EAP-TLS!  This is likey not what you want.
        tls {
            #
            #  These is used to simplify later configurations.
            #
            certdir = ${confdir}/certs
            cadir = ${confdir}/certs


            private_key_password = PASSWORD
            private_key_file = ${certdir}/server.key


            #  If Private key & Certificate are located in
            #  the same file, then private_key_file &
            #  certificate_file must contain the same file
            #  name.
            #
            #  If CA_file (below) is not used, then the
            #  certificate_file below MUST include not
            #  only the server certificate, but ALSO all
            #  of the CA certificates used to sign the
            #  server certificate.
            certificate_file = ${certdir}/server.pem


            #  Trusted Root CA list
            #
            #  ALL of the CA's in this list will be trusted
            #  to issue client certificates for authentication.
            #
            #  In general, you should use self-signed
            #  certificates for 802.1x (EAP) authentication.
            #  In that case, this CA file should contain
            #  *one* CA certificate.
            #
            #  This parameter is used only for EAP-TLS,
            #  when you issue client certificates.  If you do
            #  not use client certificates, and you do not want
            #  to permit EAP-TLS authentication, then delete
            #  this configuration item.
            #CA_file = ${cadir}/ca.pem


            #
            #  For DH cipher suites to work, you have to
            #  run OpenSSL to create the DH file first:
            #
            #      openssl dhparam -out certs/dh 1024
            #
            dh_file = ${certdir}/dh
            random_file = /dev/urandom


            #
            #  This can never exceed the size of a RADIUS
            #  packet (4096 bytes), and is preferably half
            #  that, to accomodate other attributes in
            #  RADIUS packet.  On most APs the MAX packet
            #  length is configured between 1500 - 1600
            #  In these cases, fragment size should be
            #  1024 or less.
            #
        #    fragment_size = 1024


            #  include_length is a flag which is
            #  by default set to yes If set to
            #  yes, Total Length of the message is
            #  included in EVERY packet we send.
            #  If set to no, Total Length of the
            #  message is included ONLY in the
            #  First packet of a fragment series.
            #
        #    include_length = yes


            #  Check the Certificate Revocation List
            #
            #  1) Copy CA certificates and CRLs to same directory.
            #  2) Execute 'c_rehash <CA certs&CRLs Directory>'.
            #    'c_rehash' is OpenSSL's command.
            #  3) uncomment the line below.
            #  5) Restart radiusd
        #    check_crl = yes
            CA_path = ${cadir}


               #
               #  If check_cert_issuer is set, the value will
               #  be checked against the DN of the issuer in
               #  the client certificate.  If the values do not
               #  match, the cerficate verification will fail,
               #  rejecting the user.
               #
               #  In 2.1.10 and later, this check can be done
               #  more generally by checking the value of the
               #  TLS-Client-Cert-Issuer attribute.  This check
               #  can be done via any mechanism you choose.
               #
        #       check_cert_issuer = "/C=GB/ST=Berkshire/L=Newbury/O=My Company Ltd"


               #
               #  If check_cert_cn is set, the value will
               #  be xlat'ed and checked against the CN
               #  in the client certificate.  If the values
               #  do not match, the certificate verification
               #  will fail rejecting the user.
               #
               #  This check is done only if the previous
               #  "check_cert_issuer" is not set, or if
               #  the check succeeds.
               #
               #  In 2.1.10 and later, this check can be done
               #  more generally by checking the value of the
               #  TLS-Client-Cert-CN attribute.  This check
               #  can be done via any mechanism you choose.
               #
        #    check_cert_cn = %{User-Name}
        #
            # Set this option to specify the allowed
            # TLS cipher suites.  The format is listed
            # in "man 1 ciphers".
            cipher_list = "DEFAULT"


            #


            #  This configuration entry should be deleted
            #  once the server is running in a normal
            #  configuration.  It is here ONLY to make
            #  initial deployments easier.
            #
            make_cert_command = "${certdir}/bootstrap"


            #
            #  Session resumption / fast reauthentication
            #  cache.
            #
            #  The cache contains the following information:
            #
            #  session Id - unique identifier, managed by SSL
            #  User-Name  - from the Access-Accept
            #  Stripped-User-Name - from the Access-Request
            #  Cached-Session-Policy - from the Access-Accept
            #
            #  The "Cached-Session-Policy" is the name of a
            #  policy which should be applied to the cached
            #  session.  This policy can be used to assign
            #  VLANs, IP addresses, etc.  It serves as a useful
            #  way to re-apply the policy from the original
            #  Access-Accept to the subsequent Access-Accept
            #  for the cached session.
            #
            #  On session resumption, these attributes are
            #  copied from the cache, and placed into the
            #  reply list.
            #
            #  You probably also want "use_tunneled_reply = yes"
            #  when using fast session resumption.
            #
            cache {
                  #
                  #  Enable it.  The default is "no".
                  #  Deleting the entire "cache" subsection
                  #  Also disables caching.
                  #
                  #  You can disallow resumption for a
                  #  particular user by adding the following
                  #  attribute to the control item list:
                  #
                  #        Allow-Session-Resumption = No
                  #
                  #  If "enable = no" below, you CANNOT
                  #  enable resumption for just one user
                  #  by setting the above attribute to "yes".
                  #
                  enable = no


                  #
                  #  Lifetime of the cached entries, in hours.
                  #  The sessions will be deleted after this
                  #  time.
                  #
                  lifetime = 24 # hours


                  #
                  #  The maximum number of entries in the
                  #  cache.  Set to "0" for "infinite".
                  #
                  #  This could be set to the number of users
                  #  who are logged in... which can be a LOT.
                  #
                  max_entries = 255
            }


            #
            #  As of version 2.1.10, client certificates can be
            #  validated via an external command.  This allows
            #  dynamic CRLs or OCSP to be used.
            #
            #  This configuration is commented out in the
            #  default configuration.  Uncomment it, and configure
            #  the correct paths below to enable it.
            #
            verify {
                #  A temporary directory where the client
                #  certificates are stored.  This directory
                #  MUST be owned by the UID of the server,
                #  and MUST not be accessible by any other
                #  users.  When the server starts, it will do
                #  "chmod go-rwx" on the directory, for
                #  security reasons.  The directory MUST
                #  exist when the server starts.
                #
                #  You should also delete all of the files
                #  in the directory when the server starts.
        #             tmpdir = /tmp/radiusd


                #  The command used to verify the client cert.
                #  We recommend using the OpenSSL command-line
                #  tool.
                #
                #  The ${..CA_path} text is a reference to
                #  the CA_path variable defined above.
                #
                #  The %{TLS-Client-Cert-Filename} is the name
                #  of the temporary file containing the cert
                #  in PEM format.  This file is automatically
                #  deleted by the server when the command
                #  returns.
        #            client = "/path/to/openssl verify -CApath ${..CA_path} %{TLS-Client-Cert-Filename}"
            }
        }


        #  The TTLS module implements the EAP-TTLS protocol,
        #  which can be described as EAP inside of Diameter,
        #  inside of TLS, inside of EAP, inside of RADIUS...
        #
        #  Surprisingly, it works quite well.
        #
        #  The TTLS module needs the TLS module to be installed
        #  and configured, in order to use the TLS tunnel
        #  inside of the EAP packet.  You will still need to
        #  configure the TLS module, even if you do not want
        #  to deploy EAP-TLS in your network.  Users will not
        #  be able to request EAP-TLS, as it requires them to
        #  have a client certificate.  EAP-TTLS does not
        #  require a client certificate.
        #
        #  You can make TTLS require a client cert by setting
        #
        #    EAP-TLS-Require-Client-Cert = Yes
        #
        #  in the control items for a request.
        #
        ttls {
            #  The tunneled EAP session needs a default
            #  EAP type which is separate from the one for
            #  the non-tunneled EAP module.  Inside of the
            #  TTLS tunnel, we recommend using EAP-MD5.
            #  If the request does not contain an EAP
            #  conversation, then this configuration entry
            #  is ignored.
            default_eap_type = md5


            #  The tunneled authentication request does
            #  not usually contain useful attributes
            #  like 'Calling-Station-Id', etc.  These
            #  attributes are outside of the tunnel,
            #  and normally unavailable to the tunneled
            #  authentication request.
            #
            #  By setting this configuration entry to
            #  'yes', any attribute which NOT in the
            #  tunneled authentication request, but
            #  which IS available outside of the tunnel,
            #  is copied to the tunneled request.
            #
            # allowed values: {no, yes}
            copy_request_to_tunnel = no


            #  The reply attributes sent to the NAS are
            #  usually based on the name of the user
            #  'outside' of the tunnel (usually
            #  'anonymous').  If you want to send the
            #  reply attributes based on the user name
            #  inside of the tunnel, then set this
            #  configuration entry to 'yes', and the reply
            #  to the NAS will be taken from the reply to
            #  the tunneled request.
            #
            # allowed values: {no, yes}
            use_tunneled_reply = yes


            #
            #  The inner tunneled request can be sent
            #  through a virtual server constructed
            #  specifically for this purpose.
            #
            #  If this entry is commented out, the inner
            #  tunneled request will be sent through
            #  the virtual server that processed the
            #  outer requests.
            #
            virtual_server = "inner-tunnel"


            #  This has the same meaning as the
            #  same field in the "tls" module, above.
            #  The default value here is "yes".
        #    include_length = yes
        }


        ##################################################
        #
        #  !!!!! WARNINGS for Windows compatibility  !!!!!
        #
        ##################################################
        #
        #  If you see the server send an Access-Challenge,
        #  and the client never sends another Access-Request,
        #  then
        #
        #        STOP!
        #
        #  The server certificate has to have special OID's
        #  in it, or else the Microsoft clients will silently
        #  fail.  See the "scripts/xpextensions" file for
        #  details, and the following page:
        #
        #    http://support.microsoft.com/kb/814394/en-us
        #
        #  For additional Windows XP SP2 issues, see:
        #
        #    http://support.microsoft.com/kb/885453/en-us
        #
        #
        #  If is still doesn't work, and you're using Samba,
        #  you may be encountering a Samba bug.  See:
        #
        #    https://bugzilla.samba.org/show_bug.cgi?id=6563
        #
        #  Note that we do not necessarily agree with their
        #  explanation... but the fix does appear to work.
        #
        ##################################################


        #
        #  The tunneled EAP session needs a default EAP type
        #  which is separate from the one for the non-tunneled
        #  EAP module.  Inside of the TLS/PEAP tunnel, we
        #  recommend using EAP-MS-CHAPv2.
        #
        #  The PEAP module needs the TLS module to be installed
        #  and configured, in order to use the TLS tunnel
        #  inside of the EAP packet.  You will still need to
        #  configure the TLS module, even if you do not want
        #  to deploy EAP-TLS in your network.  Users will not
        #  be able to request EAP-TLS, as it requires them to
        #  have a client certificate.  EAP-PEAP does not
        #  require a client certificate.
        #
        #
        #  You can make PEAP require a client cert by setting
        #
        #    EAP-TLS-Require-Client-Cert = Yes
        #
        #  in the control items for a request.
        #
        peap {
            #  The tunneled EAP session needs a default
            #  EAP type which is separate from the one for
            #  the non-tunneled EAP module.  Inside of the
            #  PEAP tunnel, we recommend using MS-CHAPv2,
            #  as that is the default type supported by
            #  Windows clients.
            default_eap_type = mschapv2


            #  the PEAP module also has these configuration
            #  items, which are the same as for TTLS.
            copy_request_to_tunnel = no
            use_tunneled_reply = yes


            #  When the tunneled session is proxied, the
            #  home server may not understand EAP-MSCHAP-V2.
            #  Set this entry to "no" to proxy the tunneled
            #  EAP-MSCHAP-V2 as normal MSCHAPv2.
        #    proxy_tunneled_request_as_eap = yes


            #
            #  The inner tunneled request can be sent
            #  through a virtual server constructed
            #  specifically for this purpose.
            #
            #  If this entry is commented out, the inner
            #  tunneled request will be sent through
            #  the virtual server that processed the
            #  outer requests.
            #
            virtual_server = "inner-tunnel"
        }


        #
        #  This takes no configuration.
        #
        #  Note that it is the EAP MS-CHAPv2 sub-module, not
        #  the main 'mschap' module.
        #
        #  Note also that in order for this sub-module to work,
        #  the main 'mschap' module MUST ALSO be configured.
        #
        #  This module is the *Microsoft* implementation of MS-CHAPv2
        #  in EAP.  There is another (incompatible) implementation
        #  of MS-CHAPv2 in EAP by Cisco, which FreeRADIUS does not
        #  currently support.
        #
        mschapv2 {
        }
    }

```
[B]When tailing the AP I'm getting dissociated from this is the output:
[/B]

```
Wed May  1 18:51:30 2013
    Packet-Type = Access-Request
    User-Name = "mroth"
    Framed-MTU = 1400
    Called-Station-Id = "ccef.484c.e42b"
    Calling-Station-Id = "68a8.6d4c.131a"
    Service-Type = Login-User
    Message-Authenticator = 0x022e3763e9556151708580f20d8638b2
    EAP-Message = 0x0201000a016d726f7468
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 8796
    NAS-Port-Id = "8796"
    NAS-IP-Address = 10.12.0.10
    NAS-Identifier = "010.012.000.010"


Wed May  1 18:51:30 2013
    Packet-Type = Access-Request
    User-Name = "mroth"
    Framed-MTU = 1400
    Called-Station-Id = "ccef.484c.e42b"
    Calling-Station-Id = "68a8.6d4c.131a"
    Service-Type = Login-User
    Message-Authenticator = 0xdac511c1a714dc2d72017118eb0f07c7
    EAP-Message = 0x0202008019800000007616030100710100006d0301518164330ea9d6093fc0a437bed2ab9bd8c2157bdc802409d97490dd3e94fd6000003200ffc00ac009c007c008c014c013c011c012c004c005c002c003c00ec00fc00cc00d002f000500040035000a00330039001601000012000a00080006001700180019000b00020100
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 8796
    NAS-Port-Id = "8796"
    State = 0xd4762861d474318a8f85b00c7bed4b33
    NAS-IP-Address = 10.12.0.10
    NAS-Identifier = "010.012.000.010"


Wed May  1 18:51:30 2013
    Packet-Type = Access-Request
    User-Name = "mroth"
    Framed-MTU = 1400
    Called-Station-Id = "ccef.484c.e42b"
    Calling-Station-Id = "68a8.6d4c.131a"
    Service-Type = Login-User
    Message-Authenticator = 0xb6bee89186f775c4c534bc0fc0810b8b
    EAP-Message = 0x020300061900
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 8796
    NAS-Port-Id = "8796"
    State = 0xd4762861d575318a8f85b00c7bed4b33
    NAS-IP-Address = 10.12.0.10
    NAS-Identifier = "010.012.000.010"


Wed May  1 18:51:30 2013
    Packet-Type = Access-Request
    User-Name = "mroth"
    Framed-MTU = 1400
    Called-Station-Id = "ccef.484c.e42b"
    Calling-Station-Id = "68a8.6d4c.131a"
    Service-Type = Login-User
    Message-Authenticator = 0x8c22d874039d4f9a78ab6aeceed9f788
    EAP-Message = 0x020400061900
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 8796
    NAS-Port-Id = "8796"
    State = 0xd4762861d672318a8f85b00c7bed4b33
    NAS-IP-Address = 10.12.0.10
    NAS-Identifier = "010.012.000.010"


Wed May  1 18:51:30 2013
    Packet-Type = Access-Request
    User-Name = "mroth"
    Framed-MTU = 1400
    Called-Station-Id = "ccef.484c.e42b"
    Calling-Station-Id = "68a8.6d4c.131a"
    Service-Type = Login-User
    Message-Authenticator = 0x2a13355337b6af61e948879d9824a432
    EAP-Message = 0x020500061900
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 8796
    NAS-Port-Id = "8796"
    State = 0xd4762861d773318a8f85b00c7bed4b33
    NAS-IP-Address = 10.12.0.10
    NAS-Identifier = "010.012.000.010"


Wed May  1 18:51:47 2013
    Packet-Type = Access-Request
    User-Name = "mroth"
    Framed-MTU = 1400
    Called-Station-Id = "64a0.e7f8.95f0"
    Calling-Station-Id = "68a8.6d4c.131a"
    Service-Type = Login-User
    Message-Authenticator = 0x92820f3417d6a84946e10fce303523e1
    EAP-Message = 0x0201000a016d726f7468
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 22371
    NAS-Port-Id = "22371"
    NAS-IP-Address = 10.12.0.10
    NAS-Identifier = "010.012.000.010"


Wed May  1 18:51:47 2013
    Packet-Type = Access-Request
    User-Name = "mroth"
    Framed-MTU = 1400
    Called-Station-Id = "64a0.e7f8.95f0"
    Calling-Station-Id = "68a8.6d4c.131a"
    Service-Type = Login-User
    Message-Authenticator = 0x4a100fc658045dc031bdc5cbc0982002
    EAP-Message = 0x0202008019800000007616030100710100006d030151816445ff4acacc0532b93dcf01a69b6f0579af072abd3bd8e9d56ccdfb56ec00003200ffc00ac009c007c008c014c013c011c012c004c005c002c003c00ec00fc00cc00d002f000500040035000a00330039001601000012000a00080006001700180019000b00020100
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 22371
    NAS-Port-Id = "22371"
    State = 0x224e1378224c0abf8b20b6e9dc78e6e7
    NAS-IP-Address = 10.12.0.10
    NAS-Identifier = "010.012.000.010"


Wed May  1 18:51:47 2013
    Packet-Type = Access-Request
    User-Name = "mroth"
    Framed-MTU = 1400
    Called-Station-Id = "64a0.e7f8.95f0"
    Calling-Station-Id = "68a8.6d4c.131a"
    Service-Type = Login-User
    Message-Authenticator = 0x0860ca781064d3d5cb471d79106e69d1
    EAP-Message = 0x020300061900
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 22371
    NAS-Port-Id = "22371"
    State = 0x224e1378234d0abf8b20b6e9dc78e6e7
    NAS-IP-Address = 10.12.0.10
    NAS-Identifier = "010.012.000.010"


Wed May  1 18:51:47 2013
    Packet-Type = Access-Request
    User-Name = "mroth"
    Framed-MTU = 1400
    Called-Station-Id = "64a0.e7f8.95f0"
    Calling-Station-Id = "68a8.6d4c.131a"
    Service-Type = Login-User
    Message-Authenticator = 0x96ce4444322072ba2fae5fee08866714
    EAP-Message = 0x020400061900
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 22371
    NAS-Port-Id = "22371"
    State = 0x224e1378204a0abf8b20b6e9dc78e6e7
    NAS-IP-Address = 10.12.0.10
    NAS-Identifier = "010.012.000.010"


Wed May  1 18:51:47 2013
    Packet-Type = Access-Request
    User-Name = "mroth"
    Framed-MTU = 1400
    Called-Station-Id = "64a0.e7f8.95f0"
    Calling-Station-Id = "68a8.6d4c.131a"
    Service-Type = Login-User
    Message-Authenticator = 0xc54794203a42a39e554e373869b0462d
    EAP-Message = 0x020500061900
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 22371
    NAS-Port-Id = "22371"
    State = 0x224e1378214b0abf8b20b6e9dc78e6e7
    NAS-IP-Address = 10.12.0.10
    NAS-Identifier = "010.012.000.010"


Wed May  1 18:51:47 2013
    Packet-Type = Access-Request
    User-Name = "mroth"
    Framed-MTU = 1400
    Called-Station-Id = "64a0.e7f8.95f0"
    Calling-Station-Id = "68a8.6d4c.131a"
    Service-Type = Login-User
    Message-Authenticator = 0xfcfdfcf1425f175d986d1b29d75368d5
    EAP-Message = 0x0206025019800000024616030102061000020202009f972265ae80df445e480cb61c3e581b908bef8ff4fd4a97ac288f8f9fe45adf1e28d0f771630258692fd209f0f763f847bfa5d8d70e395f55564c0a35165e60b3383ad5ccf8b0cb7fee0cdfb5d043ddd68a02c69245325759b085c5faabf0d6b8243622f8d123569d649af33a4947dc03262e190d8399ff94ef7689d794b51630f80d760a09b9a678be36fc0a470f94b20dd3a9ef3e833612dfe1fc7144c0871bccfa5c5dcba5c8a3479b24004dd39b7483764d13bb14d4169c6777e2e4487f7a4ca2e0cd454f84e59e56960fc9a6496cc2d0e6b22ab0d1bfc9b9f812a062ad92d9147f66e7a543
    EAP-Message = 0x7731c11d48ba58bf7db9188b6d6892382cc7c66f66b1029d7a1682618f6ff77859ef66ea2011cc84beac9d177724d43ac03477d8fd5ed1bab6c29eb0c9c7b9db7ae5565ba32de9084d6d755a0b4564992cb6bfdad48bd13faa6275ae8f04de07345dd78790a1a3f65ae8a8edb1cb50a1d92b87a1160a17e53b0fc553b122fe87dd3e03dc39aa5ebfcb05bfde37ae970259069838a0b3e6845bc607c8d3f1d5ae06b0a3ca9bcc032962f3799039af73794d02f420d21b8be56a1cc9a2bf5824c5dae5889a8a7a602d3c5422f70490e1f1a6a1b0531f8391e6782c6ce95b343d1751f1fbda12138934dbf0cb221afe8af78f732566dcc0d8eb4f87e26fe7
    EAP-Message = 0xc3d4fcd4af7fa16d99084c58c1bf5a4ddda0650366231341cc1f6e14030100010116030100306dc25b42c678b9eaf63c7fc2fd19dba7158106537d06886843db73d4ccd9474059a4c0c40f68a763884e6b6283e0935b
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 22371
    NAS-Port-Id = "22371"
    State = 0x224e137826480abf8b20b6e9dc78e6e7
    NAS-IP-Address = 10.12.0.10
    NAS-Identifier = "010.012.000.010"


Wed May  1 18:51:47 2013
    Packet-Type = Access-Request
    User-Name = "mroth"
    Framed-MTU = 1400
    Called-Station-Id = "64a0.e7f8.95f0"
    Calling-Station-Id = "68a8.6d4c.131a"
    Service-Type = Login-User
    Message-Authenticator = 0x679cff7b16741664160da5fa4829f375
    EAP-Message = 0x020700061900
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 22371
    NAS-Port-Id = "22371"
    State = 0x224e137827490abf8b20b6e9dc78e6e7
    NAS-IP-Address = 10.12.0.10
    NAS-Identifier = "010.012.000.010"


Wed May  1 18:51:47 2013
    Packet-Type = Access-Request
    User-Name = "mroth"
    Framed-MTU = 1400
    Called-Station-Id = "64a0.e7f8.95f0"
    Calling-Station-Id = "68a8.6d4c.131a"
    Service-Type = Login-User
    Message-Authenticator = 0x2e29e18df3fb094e0fdc5b15fc79cf57
    EAP-Message = 0x0208002b19001703010020e830fc43a806bf17e6e6161b8b79689d86c6cecc15d03903a574afa4cca71d71
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 22371
    NAS-Port-Id = "22371"
    State = 0x224e137824460abf8b20b6e9dc78e6e7
    NAS-IP-Address = 10.12.0.10
    NAS-Identifier = "010.012.000.010"


Wed May  1 18:51:47 2013
    Packet-Type = Access-Request
    User-Name = "mroth"
    Framed-MTU = 1400
    Called-Station-Id = "64a0.e7f8.95f0"
    Calling-Station-Id = "68a8.6d4c.131a"
    Service-Type = Login-User
    Message-Authenticator = 0x2c8ed86cb8ba1e3aa113dc0f8f5ba3b1
    EAP-Message = 0x0209006b19001703010060667ee82c8962f6d5ba60014d0c6cae7ba199b2aeea4d2915827665f3fd61555db4bda3819ec2aef2f00c4111f3da74b571e87e57f909c6b58fee38e30590ef0a1f113edfc542b7ef38ac9a81fb9d25ceb29757c4ecb740ce582bd5855bcbb830
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 22371
    NAS-Port-Id = "22371"
    State = 0x224e137825470abf8b20b6e9dc78e6e7
    NAS-IP-Address = 10.12.0.10
    NAS-Identifier = "010.012.000.010"


Wed May  1 18:51:47 2013
    Packet-Type = Access-Request
    User-Name = "mroth"
    Framed-MTU = 1400
    Called-Station-Id = "64a0.e7f8.95f0"
    Calling-Station-Id = "68a8.6d4c.131a"
    Service-Type = Login-User
    Message-Authenticator = 0x297821cb3e1e2dd14e2ad41c9031ef16
    EAP-Message = 0x020a002b19001703010020c3d5f93d65370bd0aca02440f3e4c05e6b527c2f57292373adb6f4d92983d535
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 22371
    NAS-Port-Id = "22371"
    State = 0x224e13782a440abf8b20b6e9dc78e6e7
    NAS-IP-Address = 10.12.0.10
    NAS-Identifier = "010.012.000.010"


Wed May  1 18:51:47 2013
    Packet-Type = Access-Request
    User-Name = "mroth"
    Framed-MTU = 1400
    Called-Station-Id = "64a0.e7f8.95f0"
    Calling-Station-Id = "68a8.6d4c.131a"
    Service-Type = Login-User
    Message-Authenticator = 0x5c597545a63a7671d3afb8280d68180c
    EAP-Message = 0x020b002b1900170301002099ebcd40f71a1d39af883cd7e8e88c39990a51f4b1e1f87db4590a1a221aa0af
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 22371
    NAS-Port-Id = "22371"
    State = 0x224e13782b450abf8b20b6e9dc78e6e7
    NAS-IP-Address = 10.12.0.10
    NAS-Identifier = "010.012.000.010"

```

---

