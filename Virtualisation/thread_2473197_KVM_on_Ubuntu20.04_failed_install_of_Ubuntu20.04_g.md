---
title: "KVM on Ubuntu20.04 failed install of Ubuntu20.04 guest via virt-install"
date: 2022-03-27
forum: Virtualisation
---

### Post by jhunt89 on 2022-03-27
On both Ubuntu Server 20.04 and Ubuntu hirsute 21.04, I am running into the exact same error installing ubuntu 20.04 as a KVM guest using the virt-install utility.

I issue:

```
sudo virt-install --name=opeplsguest0 --description='Ubuntu 20.04' --os-variant ubuntu20.04 --vcpus 2 --ram 2048 --location http://ftp.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/  --network bridge=virbr0,model=virtio --network bridge=virbr0,model=virtio --graphics none --extra-args='console=ttyS0,115200n8 serial'

```

The installation program seems to run successfully.  I use the full disk guided install and allow it to install grub to the virtual disk MBR.  When it reboots, however, it simply hangs.  If I issue the above command without the 'graphics none' option on my workstation so that it displays in the virt-viewer, it will return:

```
/dev/vda5: recovering journal
/dev/vda5: clean, x/y files, x/y blocks

```

Otherwise, it is just a dead hang.  I can shutdown from virsh, start, same issue.  I finally got somewhere when I check libvirtd's status from systemctl and it returns:

```
Mar 27 14:30:53 workstation libvirtd[10451]: 2022-03-27 18:30:53.052+0000: 10451: info : libvirt version: 7.0.0, package: 2ubuntu2.2 (Christian Ehrhardt <christian.ehrhardt@canonical.com> Thu, 18 Nov 2021 10:22:28 +0100)
Mar 27 14:30:53 workstation libvirtd[10451]: 2022-03-27 18:30:53.052+0000: 10451: info : hostname: workstation
Mar 27 14:30:53 workstation libvirtd[10451]: 2022-03-27 18:30:53.052+0000: 10451: warning : virSecurityDACTransactionRun:289 : Ignoring failed restore attempt on /var/lib/libvirt/images/opeplsguest0.qcow2
Mar 27 14:30:53 workstation libvirtd[1167]: internal error: child reported (status=125): unable to stat: /var/lib/libvirt/boot/virtinst-e7yxjidg-linux: No such file or directory
Mar 27 14:30:53 workstation libvirtd[1167]: unable to stat: /var/lib/libvirt/boot/virtinst-e7yxjidg-linux: No such file or directory
Mar 27 14:30:53 workstation libvirtd[1167]: Unable to run security manager transaction
Mar 27 14:31:01 workstation dnsmasq-dhcp[1596]: DHCPDISCOVER(virbr0) 52:54:00:b3:21:de
Mar 27 14:31:01 workstation dnsmasq-dhcp[1596]: DHCPOFFER(virbr0) 192.168.122.201 52:54:00:b3:21:de
Mar 27 14:31:01 workstation dnsmasq-dhcp[1596]: DHCPREQUEST(virbr0) 192.168.122.201 52:54:00:b3:21:de
Mar 27 14:31:01 workstation dnsmasq-dhcp[1596]: DHCPACK(virbr0) 192.168.122.201 52:54:00:b3:21:de ubuntuguest

```

Here are the permissions on /var/lib/libvirt/boot

```
userh@workstation:/var/lib/libvirt$ sudo ls -la boot
total 8
drwx--x--x 2 root root 4096 Mar 27 14:16 .
drwxr-xr-x 7 root root 4096 Feb 12 11:13 ..

```

Nearly identical returns on attempts from my server and my workstation.  I did find this article from a Redhat user.
[https://bugzilla.redhat.com/show_bug.cgi?id=566425](https://bugzilla.redhat.com/show_bug.cgi?id=566425)  

It seems the most relevant to me, but I'm in over my head at this point.  I very much appreciate any feedback.

Thank you!

edit:  One more terminal snippet that doesn't look relevant to me, but may provide a hint to the enlightened.

```

Starting install...
Retrieving file linux...                                                                                                      |  11 MB  00:00:05     
Retrieving file initrd.gz...                                                                                                  |  49 MB  00:00:17     
Allocating 'opeplsguest0.qcow2'                                                                                               |  25 GB  00:00:00     
Running graphical console command: virt-viewer --connect qemu:///system --wait opeplsguest0
error: XDG_RUNTIME_DIR not set in the environment.
Domain creation completed.
Restarting guest.
Running graphical console command: virt-viewer --connect qemu:///system --wait opeplsguest0

```

---

### Post by #&amp;thj^% on 2022-03-27
> **jhunt89 said:**
> On both Ubuntu Server 20.04 and Ubuntu hirsute 21.04, I am running into the exact same error installing ubuntu 20.04 as a KVM guest using the virt-install utility.

I issue:

```
sudo virt-install --name=opeplsguest0 --description='Ubuntu 20.04' --os-variant ubuntu20.04 --vcpus 2 --ram 2048 --location http://ftp.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/  --network bridge=virbr0,model=virtio --network bridge=virbr0,model=virtio --graphics none --extra-args='console=ttyS0,115200n8 serial'

```


[S]How come sudo?? eg: "sudo virt-install -" permission problems I'll bet[/S]
Scratch that I do get prompted for sudo passwd
I set all mine up with something like:
```
virt-install --location http://us.archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/ --extra-args "ks=http://pastebin.com/raw/WxQygWpm"
```
My permissions:
```
ls -la
total 8
drwxr-xr-x  2 root root 4096 Jan 27 18:09 .
drwxr-xr-x 11 root root 4096 Feb 26 22:05 ..


```
Memory jog around a year ago I had modify "/etc/libvirt/libvirtd.conf"
and I un-commented this: <log_outputs="3:syslog:libvirtd">
```
# Master libvirt daemon configuration file
#

#################################################################
#
# Network connectivity controls
#

# Flag listening for secure TLS connections on the public TCP/IP port.
# NB, must pass the --listen flag to the libvirtd process for this to
# have any effect.
#
# This setting is not required or honoured if using systemd socket
# activation.
#
# It is necessary to setup a CA and issue server certificates before
# using this capability.
#
# This is enabled by default, uncomment this to disable it
#listen_tls = 0

# Listen for unencrypted TCP connections on the public TCP/IP port.
# NB, must pass the --listen flag to the libvirtd process for this to
# have any effect.
#
# This setting is not required or honoured if using systemd socket
# activation.
#
# Using the TCP socket requires SASL authentication by default. Only
# SASL mechanisms which support data encryption are allowed. This is
# DIGEST_MD5 and GSSAPI (Kerberos5)
#
# This is disabled by default, uncomment this to enable it.
#listen_tcp = 1



# Override the port for accepting secure TLS connections
# This can be a port number, or service name
#
# This setting is not required or honoured if using systemd socket
# activation.
#
#tls_port = "16514"

# Override the port for accepting insecure TCP connections
# This can be a port number, or service name
#
# This setting is not required or honoured if using systemd socket
# activation.
#
#tcp_port = "16509"


# Override the default configuration which binds to all network
# interfaces. This can be a numeric IPv4/6 address, or hostname
#
# This setting is not required or honoured if using systemd socket
# activation.
#
# If the libvirtd service is started in parallel with network
# startup (e.g. with systemd), binding to addresses other than
# the wildcards (0.0.0.0/::) might not be available yet.
#
#listen_addr = "192.168.0.1"


#################################################################
#
# UNIX socket access controls
#

# Set the UNIX domain socket group ownership. This can be used to
# allow a 'trusted' set of users access to management capabilities
# without becoming root.
#
# This setting is not required or honoured if using systemd socket
# activation.
#
# This is restricted to 'root' by default.
#unix_sock_group = "libvirt"

# Set the UNIX socket permissions for the R/O socket. This is used
# for monitoring VM status only
#
# This setting is not required or honoured if using systemd socket
# activation.
#
# Default allows any user. If setting group ownership, you may want to
# restrict this too.
#unix_sock_ro_perms = "0777"

# Set the UNIX socket permissions for the R/W socket. This is used
# for full management of VMs
#
# This setting is not required or honoured if using systemd socket
# activation.
#
# Default allows only root. If PolicyKit is enabled on the socket,
# the default will change to allow everyone (eg, 0777)
#
# If not using PolicyKit and setting group ownership for access
# control, then you may want to relax this too.
#unix_sock_rw_perms = "0770"

# Set the UNIX socket permissions for the admin interface socket.
#
# This setting is not required or honoured if using systemd socket
# activation.
#
# Default allows only owner (root), do not change it unless you are
# sure to whom you are exposing the access to.
#unix_sock_admin_perms = "0700"

# Set the name of the directory in which sockets will be found/created.
#
# This setting is not required or honoured if using systemd socket
# activation.
#
#unix_sock_dir = "/run/libvirt"



#################################################################
#
# Authentication.
#
# There are the following choices available:
#
#  - none: do not perform auth checks. If you can connect to the
#          socket you are allowed. This is suitable if there are
#          restrictions on connecting to the socket (eg, UNIX
#          socket permissions), or if there is a lower layer in
#          the network providing auth (eg, TLS/x509 certificates)
#
#  - sasl: use SASL infrastructure. The actual auth scheme is then
#          controlled from /etc/sasl2/libvirt.conf. For the TCP
#          socket only GSSAPI & DIGEST-MD5 mechanisms will be used.
#          For non-TCP or TLS sockets, any scheme is allowed.
#
#  - polkit: use PolicyKit to authenticate. This is only suitable
#            for use on the UNIX sockets. The default policy will
#            require a user to supply their own password to gain
#            full read/write access (aka sudo like), while anyone
#            is allowed read/only access.
#

# Set an authentication scheme for UNIX read-only sockets
#
# By default socket permissions allow anyone to connect
#
# If libvirt was compiled without support for 'polkit', then
# no access control checks are done, but libvirt still only
# allows execution of APIs which don't change state.
#
# If libvirt was compiled with support for 'polkit', then
# the libvirt socket will perform a check with polkit after
# connections. The default policy still allows any local
# user access.
#
# To restrict monitoring of domains you may wish to either
# enable 'sasl' here, or change the polkit policy definition.
#auth_unix_ro = "polkit"

# Set an authentication scheme for UNIX read-write sockets.
#
# If libvirt was compiled without support for 'polkit', then
# the systemd .socket files will use SocketMode=0600 by default
# thus only allowing root user to connect, and 'auth_unix_rw'
# will default to 'none'.
#
# If libvirt was compiled with support for 'polkit', then
# the systemd .socket files will use SocketMode=0666 which
# allows any user to connect and 'auth_unix_rw' will default
# to 'polkit'. If you disable use of 'polkit' here, then it
# is essential to change the systemd SocketMode parameter
# back to 0600, to avoid an insecure configuration.
#
#auth_unix_rw = "polkit"

# Change the authentication scheme for TCP sockets.
#
# If you don't enable SASL, then all TCP traffic is cleartext.
# Don't do this outside of a dev/test scenario. For real world
# use, always enable SASL and use the GSSAPI or DIGEST-MD5
# mechanism in /etc/sasl2/libvirt.conf
#auth_tcp = "sasl"

# Change the authentication scheme for TLS sockets.
#
# TLS sockets already have encryption provided by the TLS
# layer, and limited authentication is done by certificates
#
# It is possible to make use of any SASL authentication
# mechanism as well, by using 'sasl' for this option
#auth_tls = "none"

# Enforce a minimum SSF value for TCP sockets
#
# The default minimum is currently 56 (single-DES) which will
# be raised to 112 in the future.
#
# This option can be used to set values higher than 112
#tcp_min_ssf = 112


# Change the API access control scheme
#
# By default an authenticated user is allowed access
# to all APIs. Access drivers can place restrictions
# on this. By default the 'nop' driver is enabled,
# meaning no access control checks are done once a
# client has authenticated with libvirtd
#
#access_drivers = [ "polkit" ]

#################################################################
#
# TLS x509 certificate configuration
#

# Use of TLS requires that x509 certificates be issued. The default locations
# for the certificate files is as follows:
#
#   /etc/pki/CA/cacert.pem - The CA master certificate
#   /etc/pki/libvirt/servercert.pem - The server certificate signed by cacert.pem
#   /etc/pki/libvirt/private/serverkey.pem - The server private key
#
# It is possible to override the default locations by altering the 'key_file',
# 'cert_file', and 'ca_file' values and uncommenting them below.
#
# NB, overriding the default of one location requires uncommenting and
# possibly additionally overriding the other settings.
#

# Override the default server key file path
#
#key_file = "/etc/pki/libvirt/private/serverkey.pem"

# Override the default server certificate file path
#
#cert_file = "/etc/pki/libvirt/servercert.pem"

# Override the default CA certificate path
#
#ca_file = "/etc/pki/CA/cacert.pem"

# Specify a certificate revocation list.
#
# Defaults to not using a CRL, uncomment to enable it
#crl_file = "/etc/pki/CA/crl.pem"



#################################################################
#
# Authorization controls
#


# Flag to disable verification of our own server certificates
#
# When libvirtd starts it performs some sanity checks against
# its own certificates.
#
# Default is to always run sanity checks. Uncommenting this
# will disable sanity checks which is not a good idea
#tls_no_sanity_certificate = 1

# Flag to disable verification of client certificates
#
# Client certificate verification is the primary authentication mechanism.
# Any client which does not present a certificate signed by the CA
# will be rejected.
#
# Default is to always verify. Uncommenting this will disable
# verification.
#tls_no_verify_certificate = 1


# An access control list of allowed x509 Distinguished Names
# This list may contain wildcards such as
#
#    "C=GB,ST=London,L=London,O=Red Hat,CN=*"
#
# Any * matches any number of consecutive spaces, like a simplified glob(7).
#
# The format of the DN for a particular certificate can be queried
# using:
#
#    virt-pki-query-dn clientcert.pem
#
# NB If this is an empty list, no client can connect, so comment out
# entirely rather than using empty list to disable these checks
#
# By default, no DN's are checked
#tls_allowed_dn_list = ["DN1", "DN2"]


# Override the compile time default TLS priority string. The
# default is usually "NORMAL" unless overridden at build time.
# Only set this is it is desired for libvirt to deviate from
# the global default settings.
#
#tls_priority="NORMAL"


# An access control list of allowed SASL usernames. The format for username
# depends on the SASL authentication mechanism. Kerberos usernames
# look like username@REALM
#
# This list may contain wildcards such as
#
#    "*@EXAMPLE.COM"
#
# See the g_pattern_match function for the format of the wildcards.
#
# https://developer.gnome.org/glib/stable/glib-Glob-style-pattern-matching.html
#
# NB If this is an empty list, no client can connect, so comment out
# entirely rather than using empty list to disable these checks
#
# By default, no Username's are checked
#sasl_allowed_username_list = ["joe@EXAMPLE.COM", "fred@EXAMPLE.COM" ]


#################################################################
#
# Processing controls
#

# The maximum number of concurrent client connections to allow
# over all sockets combined.
#max_clients = 5000

# The maximum length of queue of connections waiting to be
# accepted by the daemon. Note, that some protocols supporting
# retransmission may obey this so that a later reattempt at
# connection succeeds.
#max_queued_clients = 1000

# The maximum length of queue of accepted but not yet
# authenticated clients. The default value is 20. Set this to
# zero to turn this feature off.
#max_anonymous_clients = 20

# The minimum limit sets the number of workers to start up
# initially. If the number of active clients exceeds this,
# then more threads are spawned, up to max_workers limit.
# Typically you'd want max_workers to equal maximum number
# of clients allowed
#min_workers = 5
#max_workers = 20


# The number of priority workers. If all workers from above
# pool are stuck, some calls marked as high priority
# (notably domainDestroy) can be executed in this pool.
#prio_workers = 5

# Limit on concurrent requests from a single client
# connection. To avoid one client monopolizing the server
# this should be a small fraction of the global max_workers
# parameter.
#max_client_requests = 5

# Same processing controls, but this time for the admin interface.
# For description of each option, be so kind to scroll few lines
# upwards.

#admin_min_workers = 1
#admin_max_workers = 5
#admin_max_clients = 5
#admin_max_queued_clients = 5
#admin_max_client_requests = 5

#################################################################
#
# Logging controls
#

# Logging level: 4 errors, 3 warnings, 2 information, 1 debug
# basically 1 will log everything possible
#
# WARNING: USE OF THIS IS STRONGLY DISCOURAGED.
#
# WARNING: It outputs too much information to practically read.
# WARNING: The "log_filters" setting is recommended instead.
#
# WARNING: Journald applies rate limiting of messages and so libvirt
# WARNING: will limit "log_level" to only allow values 3 or 4 if
# WARNING: journald is the current output.
#
# WARNING: USE OF THIS IS STRONGLY DISCOURAGED.
#log_level = 3

# Logging filters:
# A filter allows to select a different logging level for a given category
# of logs. The format for a filter is:
#
#    level:match
#
# where 'match' is a string which is matched against the category
# given in the VIR_LOG_INIT() at the top of each libvirt source
# file, e.g., "remote", "qemu", or "util.json". The 'match' in the
# filter matches using shell wildcard syntax (see 'man glob(7)').
# The 'match' is always treated as a substring match. IOW a match
# string 'foo' is equivalent to '*foo*'.
#
# 'level' is the minimal level where matching messages should
#  be logged:
#
#    1: DEBUG
#    2: INFO
#    3: WARNING
#    4: ERROR
#
# Multiple filters can be defined in a single @log_filters, they just need
# to be separated by spaces. Note that libvirt performs "first" match, i.e.
# if there are concurrent filters, the first one that matches will be applied,
# given the order in @log_filters.
#
# A typical need is to capture information from a hypervisor driver,
# public API entrypoints and some of the utility code. Some utility
# code is very verbose and is generally not desired. Taking the QEMU
# hypervisor as an example, a suitable filter string for debugging
# might be to turn off object, json & event logging, but enable the
# rest of the util code:
#
#log_filters="1:qemu 1:libvirt 4:object 4:json 4:event 1:util"

# Logging outputs:
# An output is one of the places to save logging information
# The format for an output can be:
#    level:stderr
#      output goes to stderr
#    level:syslog:name
#      use syslog for the output and use the given name as the ident
#    level:file:file_path
#      output to a file, with the given filepath
#    level:journald
#      output to journald logging system
# In all cases 'level' is the minimal priority, acting as a filter
#    1: DEBUG
#    2: INFO
#    3: WARNING
#    4: ERROR
#
# Multiple outputs can be defined, they just need to be separated by spaces.
# e.g. to log all warnings and errors to syslog under the libvirtd ident:
[B][COLOR="#FF0000"]log_outputs="3:syslog:libvirtd"

[/COLOR][/B]
##################################################################
#
# Auditing
#
# This setting allows usage of the auditing subsystem to be altered:
#
#   audit_level == 0  -> disable all auditing
#   audit_level == 1  -> enable auditing, only if enabled on host (default)
#   audit_level == 2  -> enable auditing, and exit if disabled on host
#
#audit_level = 2
#
# If set to 1, then audit messages will also be sent
# via libvirt logging infrastructure. Defaults to 0
#
#audit_logging = 1

###################################################################
# UUID of the host:
# Host UUID is read from one of the sources specified in host_uuid_source.
#
# - 'smbios': fetch the UUID from 'dmidecode -s system-uuid'
# - 'machine-id': fetch the UUID from /etc/machine-id
#
# The host_uuid_source default is 'smbios'. If 'dmidecode' does not provide
# a valid UUID a temporary UUID will be generated.
#
# Another option is to specify host UUID in host_uuid.
#
# Keep the format of the example UUID below. UUID must not have all digits
# be the same.

# NB This default all-zeros UUID will not work. Replace
# it with the output of the 'uuidgen' command and then
# uncomment this entry
#host_uuid = "00000000-0000-0000-0000-000000000000"
#host_uuid_source = "smbios"

###################################################################
# Keepalive protocol:
# This allows libvirtd to detect broken client connections or even
# dead clients.  A keepalive message is sent to a client after
# keepalive_interval seconds of inactivity to check if the client is
# still responding; keepalive_count is a maximum number of keepalive
# messages that are allowed to be sent to the client without getting
# any response before the connection is considered broken.  In other
# words, the connection is automatically closed approximately after
# keepalive_interval * (keepalive_count + 1) seconds since the last
# message received from the client.  If keepalive_interval is set to
# -1, libvirtd will never send keepalive requests; however clients
# can still send them and the daemon will send responses.  When
# keepalive_count is set to 0, connections will be automatically
# closed after keepalive_interval seconds of inactivity without
# sending any keepalive messages.
#
#keepalive_interval = 5
#keepalive_count = 5

#
# These configuration options are no longer used.  There is no way to
# restrict such clients from connecting since they first need to
# connect in order to ask for keepalive.
#
#keepalive_required = 1
#admin_keepalive_required = 1

# Keepalive settings for the admin interface
#admin_keepalive_interval = 5
#admin_keepalive_count = 5

###################################################################
# Open vSwitch:
# This allows to specify a timeout for openvswitch calls made by
# libvirt. The ovs-vsctl utility is used for the configuration and
# its timeout option is set by default to 5 seconds to avoid
# potential infinite waits blocking libvirt.
#
#ovs_timeout = 5



```
Then restart libvirt:
```
sudo systemctl start libvirtd
```
Then a log showed this:
```
    Feb  6 17:22:09 me libvirtd: 17576: info : libvirt version: 0.9.9
    Feb  6 17:22:09 me libvirtd: 17576: error : virNetTLSContextCheckCertFile:92: Cannot read CA certificate '/etc/pki/CA/cacert.pem': No such file or directory
    Feb  6 17:22:09 me /etc/init.d/libvirtd[17573]: start-stop-daemon: failed to start `/usr/sbin/libvirtd'
    Feb  6 17:22:09 me /etc/init.d/libvirtd[17565]: ERROR: libvirtd failed to start
```
I'm now quoting RedHat Manual
    The libvirtd man page shows that the missing cacert.pem file is used as TLS authority when libvirt is run in Listen for TCP/IP connections mode. This means the --listen parameter is being passed. 
Solution
    Configure the libvirt daemon's settings with one of the following methods:

        Install a CA certificate.

        Note
        For more information on CA certificates and configuring system authentication, refer to the Configuring Authentication chapter in the Red Hat Enterprise Linux 6 Deployment Guide. Found Here:[https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/virtualization_host_configuration_and_guest_installation_guide/chap-virtualization_host_configuration_and_guest_installation_guide-guest_installation](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/virtualization_host_configuration_and_guest_installation_guide/chap-virtualization_host_configuration_and_guest_installation_guide-guest_installation)
        Do not use TLS; use bare TCP instead. In /etc/libvirt/libvirtd.conf set listen_tls = 0 and listen_tcp = 1. The default values are listen_tls = 1 and listen_tcp = 0.
        Do not pass the --listen parameter. In /etc/sysconfig/libvirtd.conf change the LIBVIRTD_ARGS variable. 

    Appendix A. NetKVM Driver Parameters B.2. The URI Failed to Connect to the Hypervisor

---

### Post by TheFu on 2022-03-27
If virt-install isn't mandatory, perhaps virt-manager can be used? It is very much like Virtualbox or VMware Player or VMware Workstation or VMware vSphere, but without the limitation those other options have.  Virt-manager can be used from any workstation to control a libvirt/kvm server provided ssh connectivity exists. No root needed. The ssh userids on the client and remote kvm server just need to be in the libvirtd group. That is sufficient to manage all the VMs.  

virt-manager is much easier to use for creating occasional VMs. If you need to make more than 1/week, then I'd hunt down how to use virt-install.

For end users, GUI access to VMs is available using virt-viewer from most platforms.

---

### Post by #&amp;thj^% on 2022-03-28
> **TheFu said:**
> If virt-install isn't mandatory, perhaps virt-manager can be used? It is very much like Virtualbox or VMware Player or VMware Workstation or VMware vSphere, but without the limitation those other options have.  Virt-manager can be used from any workstation to control a libvirt/kvm server provided ssh connectivity exists. No root needed. The ssh userids on the client and remote kvm server just need to be in the libvirtd group. That is sufficient to manage all the VMs.  

virt-manager is much easier to use for creating occasional VMs. If you need to make more than 1/week, then I'd hunt down how to use virt-install.

For end users, GUI access to VMs is available using virt-viewer from most platforms.

+1 I was just going to suggest the very same.
OP's errors are related with:
```
Ignoring failed restore attempt on /var/lib/libvirt/images/opeplsguest0.qcow2
Mar 27 14:30:53 workstation libvirtd[1167]: internal error: child reported (status=125): unable to stat: /var/lib/libvirt/boot/virtinst-e7yxjidg-linux: No such file or directory
Mar 27 14:30:53 workstation libvirtd[1167]: unable to stat: /var/lib/libvirt/boot/virtinst-e7yxjidg-linux: No such file or directory
Mar 27 14:30:53 workstation libvirtd[1167]: Unable to run security manager transaction
```
Till they get a firm grasp on "virt-install" I don't think it would be the end of world with using a GUI virt-manager.

---

### Post by #&amp;thj^% on 2022-03-31
We haven't heard back from the OP
Just for fun I had to check again, with:
you'll have to change my code to fit your devices.
and i'll assume you have already set a bridged network.
```
sudo bridge link
[sudo] password for me: 
29: vnet17: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 master bro1 state forwarding priority 32 cost 100 
30: vnet18: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 master bro1 state forwarding priority 32 cost
 100 

```
and check with:
```
sudo -i brctl show
bridge name	bridge id		STP enabled	interfaces
bro1		8000.xno		vnet17
						vnet18
virbr0		8000.xno    	yes		

```

```
sudo virt-install --name=unknown --description='Ubuntu 20.04' --os-variant ubuntu20.04 --vcpus 4 
--ram 2048 --location http://us.archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/  --netwo
rk bridge=bro1,model=virtio --network bridge=bro1,model=virtio --graphics none --extra-args='console
=ttyS0,115200n8 serial'

```
Which brought me to this part:
```
      &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; [!] Ubuntu installer main menu &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
      &#9474;                                                                  &#9474;
      &#9474; Choose the next step in the install process:                     &#9474;
      &#9474;                                                                  &#9474;
      &#9474;  Choose language                                                 &#9474;
      &#9474;  Access software for a blind person using a braille display      &#9474;
      &#9474;  Configure the keyboard                                          &#9474;
      &#9474;  Detect network hardware                                         &#9474;
      &#9474;  Configure the network                                           &#9474;
      &#9474;  Choose a mirror of the Ubuntu archive                           &#9474;
      &#9474;  Download installer components                                   &#9474;
      &#9474;  Change debconf priority                                         &#9474;
      &#9474;  Save debug logs                                                 &#9474;
      &#9474;  Execute a shell                                                 &#9474;
      &#9474;  Abort the installation                                          &#9474;
      &#9474;                                                                  &#9474;
      &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;



<Tab> moves; <Space> selects; <Enter> activates buttons

```
I then aborted, I just didn't need to have another Focal install.

---

### Post by TheFu on 2022-03-31
I thought bridgeutils was deprecated in 20.04.  I don't have any 20.04 VM hosts. Still on 18.04 here ... mainly over netplan concerns which were corrected (to my knowledge) about a year ago.
I haven't used virt-install since around 2010-ish.  We don't churn through lots of VMs, so the GUI in virt-manager is much easier. Plus, we don't use image files and need to specify the LV for each VM during the VM-setup process.

---

### Post by #&amp;thj^% on 2022-03-31
> **TheFu said:**
> I thought bridgeutils was deprecated in 20.04.  I don't have any 20.04 VM hosts. Still on 18.04 here ... mainly over netplan concerns which were corrected (to my knowledge) about a year ago.

Yep it was, I was just making sure it still worked, and I forced the bridge connection.
> **TheFu said:**
> 
I haven't used virt-install since around 2010-ish.  We don't churn through lots of VMs, so the GUI in virt-manager is much easier. Plus, we don't use image files and need to specify the LV for each VM during the VM-setup process.
Guilty here as well (spoiled with virt-manager).  wait what, TheFu using a GUI??? that's a rarity. ;)

---

### Post by TheFu on 2022-03-31
> **1fallen said:**
> Yep it was, I was just making sure it still worked, and I forced the bridge connection.

Guilty here as well.  wait what, TheFu using a GUI??? that's a rarity. ;)

I use GUIs all the time!  Dillo, Firefox, chromium, xterm, xterm, xterm, xterm, xterm, xterm, xterm, xterm, xterm, xterm, ... alarm-clock-applet, oopps, was just looking at my window list in fvmw.

Never fear.  Music playback is using a TUI - ncmpc. Sometimes I'll use a little script that presents playlists to be played instead. Much easier.

Last month, I used a file manager for about 15 minutes too! The world didn't end. <rbg>

---

### Post by #&amp;thj^% on 2022-03-31
> **TheFu said:**
> I use GUIs all the time!  Dillo, Firefox, chromium, xterm, xterm, xterm, xterm, xterm, xterm, xterm, xterm, xterm, xterm, ... alarm-clock-applet, oopps, was just looking at my window list in fvmw.

Never fear.  Music playback is using a TUI - ncmpc. Sometimes I'll use a little script that presents playlists to be played instead. Much easier.

Last month, I used a file manager for about 15 minutes too! The world didn't end. <rbg>

:lolflag::lolflag::lolflag:
your a Good Sport.

---

### Post by TheFu on 2022-03-31
> **1fallen said:**
> your a Good Sport.
This is supposed to be fun, right?  I give enough grief that taking some is perfectly fair too.

---

### Post by #&amp;thj^% on 2022-03-31
> **TheFu said:**
> This is supposed to be fun, right?  I give enough grief that taking some is perfectly fair too.

Viewed in fun yes, and my words also may come across as sharp, I'm still working on that.

---

### Post by #&amp;thj^% on 2022-04-02
@ TheFu good news, bridged nics can be had in 22.04(beta as of now)
the OP was asking as well just on 20.04 though, which I had no intrest in as a sever.
```
sudo virsh net-list
 Name              State    Autostart   Persistent
----------------------------------------------------
 bridged-network   active   yes         yes

```
```

 ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: enp0s25: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 54:ee:75:54:59:df brd ff:ff:ff:ff:ff:ff
    inet 192.168<sniped>ope global dynamic noprefixroute enp0s25
       valid_lft 6604sec preferred_lft 6604sec
    inet6 fe80::<snipedlink noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp4s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 10:<sniped
    inet 192.168.<,sniped>68.1.255 scope global dynamic noprefixroute wlp4s0
       valid_lft 6743sec preferred_lft 6743sec
    inet6 fe80:<sniped>pe link noprefixroute 
       valid_lft forever preferred_lft forever
16: br0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 9e:
    inet 192.168.1.xxx scope global br0
       valid_lft forever preferred_lft forever
19: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1350 qdisc fq_codel state UNKNOWN group default qlen 500
    link/none 
    inet 10.133.0.6 peer 10.133.0.5/32 scope global tun0
       valid_lft forever preferred_lft forever
me@me-ThinkPad-T540p:~$ sudo ip link show type bridge
16: br0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/ether 9e:<sniped>
```
This system:
```
inxi -Fz
System:
  Kernel: 5.15.0-23-generic x86_64 bits: 64 Desktop: Xfce 4.16.0
    Distro: Ubuntu 22.04 (Jammy Jellyfish)
Machine:
  Type: Laptop System: LENOVO product: 20BFS3NJ00 v: ThinkPad T540p
    serial: <superuser required>
  Mobo: LENOVO model: 20BFS3NJ00 v: 0B98401 WIN
    serial: <superuser required> UEFI: LENOVO v: GMET91WW (2.39 )
    date: 06/03/2021
Battery:
  ID-1: BAT0 charge: 84.1 Wh (97.5%) condition: 86.3/99.5 Wh (86.8%)
CPU:
  Info: dual core model: Intel Core i7-4600M bits: 64 type: MT MCP cache:
    L2: 512 KiB
  Speed (MHz): avg: 2002 min/max: 800/3600 cores: 1: 2702 2: 804 3: 2380
    4: 2125
Graphics:
  Device-1: Intel 4th Gen Core Processor Integrated Graphics driver: i915
    v: kernel
  Device-2: NVIDIA GK208M [GeForce GT 730M] driver: nvidia v: 470.103.01
  Device-3: Lite-On Integrated Camera type: USB driver: uvcvideo
  Display: x11 server: X.Org v: 1.21.1.3 driver: X:
    loaded: modesetting,nvidia unloaded: fbdev,nouveau,vesa gpu: i915
    resolution: 1: 1920x1080~60Hz 2: 1920x1080~60Hz
  OpenGL: renderer: NVIDIA GeForce GT 730M/PCIe/SSE2
    v: 4.6.0 NVIDIA 470.103.01
Audio:
  Device-1: Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio
    driver: snd_hda_intel
  Device-2: Intel 8 Series/C220 Series High Definition Audio
    driver: snd_hda_intel
  Sound Server-1: ALSA v: k5.15.0-23-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Intel Ethernet I217-LM driver: e1000e
  IF: enp0s25 state: up speed: 100 Mbps duplex: full mac: <filter>
  Device-2: Intel Wireless 7260 driver: iwlwifi
  IF: wlp4s0 state: up mac: <filter>
  IF-ID-1: br0 state: down mac: <filter>
  IF-ID-2: tun0 state: unknown speed: 10 Mbps duplex: full mac: N/A
Bluetooth:
  Device-1: Intel Bluetooth wireless interface type: USB driver: btusb
  Report: hciconfig ID: hci0 state: up address: <filter> bt-v: 2.1
Drives:
  Local Storage: total: 5.46 TiB used: 4.42 TiB (81.0%)
  ID-1: /dev/sda vendor: PNY model: CS2311 1TB SSD size: 931.51 GiB
  ID-2: /dev/sdb type: USB vendor: Western Digital
    model: WD My Passport 2627 size: 4.55 TiB
Partition:
  ID-1: / size: 507.71 GiB used: 19.61 GiB (3.9%) fs: ext4 dev: /dev/sda2
  ID-2: /boot/efi size: 511 MiB used: 5.4 MiB (1.1%) fs: vfat
    dev: /dev/sda1
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 2 MiB (0.1%) file: /swapfile
Sensors:
  System Temperatures: cpu: 51.0 C mobo: N/A gpu: nvidia temp: 46 C
  Fan Speeds (RPM): fan-1: 2053
Info:
  Processes: 214 Uptime: 3h 2m Memory: 11.57 GiB used: 2.7 GiB (23.3%)
  Shell: Bash inxi: 3.3.13
me@me-ThinkPad-T540p:~$ 


```

---

### Post by TheFu on 2022-04-02
The bridges created by libvirt had terrible performance, at least around 2010.  I got into the habit of creating any bridges, sometimes using PCI passthru for security, manually.  For GigE connections, the bridges controlled by bridgeutils were excellent, but for 10Gbps connections, openvswitch really makes a huge performance difference when the bits go outside the VM host.

Of course, that may have all changed. Also, I use bridges not just for libvirt, but for some containers too, so I don't want libvirt controlling the bridge.

---

