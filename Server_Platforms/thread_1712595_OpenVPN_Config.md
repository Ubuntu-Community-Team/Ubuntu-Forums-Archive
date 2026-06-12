---
title: "OpenVPN Config"
date: 2011-03-22
forum: Server Platforms
---

### Post by pcarlos853 on 2011-03-22
Hello, I am running Ubuntu Server 10.10. I have installed OpenVPN using [this guide]("https://help.ubuntu.com/10.10/serverguide/C/openvpn.html") I have set up everything correctly as this guide says, but I am having problems with the config file. I want to securely route all traffic on the client to the server, how ever the server will not start. My config is below:
> #################################################
# Sample OpenVPN 2.0 config file for            #
# multi-client server.                          #
#                                               #
# This file is for the server side              #
# of a many-clients <-> one-server              #
# OpenVPN configuration.                        #
#                                               #
# OpenVPN also supports                         #
# single-machine <-> single-machine             #
# configurations (See the Examples page         #
# on the web site for more info).               #
#                                               #
# This config should work on Windows            #
# or Linux/BSD systems.  Remember on            #
# Windows to quote pathnames and use            #
# double backslashes, e.g.:                     #
# "C:\\Program Files\\OpenVPN\\config\\foo.key" #
#                                               #
# Comments are preceded with '#' or ';'         #
#################################################

# Which local IP address should OpenVPN
# listen on? (optional)
;local a.b.c.d

# Which TCP/UDP port should OpenVPN listen on?
# If you want to run multiple OpenVPN instances
# on the same machine, use a different port
# number for each one.  You will need to
# open up this port on your firewall.
port 1194

# TCP or UDP server?
;proto tcp
proto udp

# "dev tun" will create a routed IP tunnel,
# "dev tap" will create an ethernet tunnel.
# Use "dev tap0" if you are ethernet bridging
# and have precreated a tap0 virtual interface
# and bridged it with your ethernet interface.
# If you want to control access policies
# over the VPN, you must create firewall
# rules for the the TUN/TAP interface.
# On non-Windows systems, you can give
# an explicit unit number, such as tun0.
# On Windows, use "dev-node" for this.
# On most systems, the VPN will not function
# unless you partially or fully disable
# the firewall for the TUN/TAP interface.
;dev tap
dev tun

# Windows needs the TAP-Win32 adapter name
# from the Network Connections panel if you
# have more than one.  On XP SP2 or higher,
# you may need to selectively disable the
# Windows firewall for the TAP adapter.
# Non-Windows systems usually don't need this.
;dev-node MyTap

# SSL/TLS root certificate (ca), certificate
# (cert), and private key (key).  Each client
# and the server must have their own cert and
# key file.  The server and all clients will
# use the same ca file.
#
# See the "easy-rsa" directory for a series
# of scripts for generating RSA certificates
# and private keys.  Remember to use
# a unique Common Name for the server
# and each of the client certificates.
#
# Any X509 key management system can be used.
# OpenVPN can also use a PKCS #12 formatted key file
# (see "pkcs12" directive in man page).
ca ca.crt
cert server.crt
key server.key  # This file should be kept secret

# Diffie hellman parameters.
# Generate your own with:
#   openssl dhparam -out dh1024.pem 1024
# Substitute 2048 for 1024 if you are using
# 2048 bit keys. 
dh dh1024.pem

# Configure server mode and supply a VPN subnet
# for OpenVPN to draw client addresses from.
# The server will take 10.0.0.1 for itself,
# the rest will be made available to clients.
# Each client will be able to reach the server
# on 10.0.0.1. Comment this line out if you are
# ethernet bridging. See the man page for more info.
server 10.0.0.0 255.255.255.0

# Maintain a record of client <-> virtual IP address
# associations in this file.  If OpenVPN goes down or
# is restarted, reconnecting clients can be assigned
# the same virtual IP address from the pool that was
# previously assigned.
ifconfig-pool-persist ipp.txt

# Configure server mode for ethernet bridging.
# You must first use your OS's bridging capability
# to bridge the TAP interface with the ethernet
# NIC interface.  Then you must manually set the
# IP/netmask on the bridge interface, here we
# assume 10.0.0.4/255.255.255.0.  Finally we
# must set aside an IP range in this subnet
# (start=10.0.0.50 end=10.0.0.100) to allocate
# to connecting clients.  Leave this line commented
# out unless you are ethernet bridging.
server-bridge 10.0.0.4 255.255.255.0 10.0.0.200 10.0.0.215

# Push routes to the client to allow it
# to reach other private subnets behind
# the server.  Remember that these
# private subnets will also need
# to know to route the OpenVPN client
# address pool (10.0.0.0/255.255.255.0)
# back to the OpenVPN server.
;push "route 192.168.10.0 255.255.255.0"
;push "route 192.168.20.0 255.255.255.0"

# To assign specific IP addresses to specific
# clients or if a connecting client has a private
# subnet behind it that should also have VPN access,
# use the subdirectory "ccd" for client-specific
# configuration files (see man page for more info).

# EXAMPLE: Suppose the client
# having the certificate common name "Thelonious"
# also has a small subnet behind his connecting
# machine, such as 192.168.40.128/255.255.255.248.
# First, uncomment out these lines:
;client-config-dir ccd
;route 192.168.40.128 255.255.255.248
# Then create a file ccd/Thelonious with this line:
#   iroute 192.168.40.128 255.255.255.248
# This will allow Thelonious' private subnet to
# access the VPN.  This example will only work
# if you are routing, not bridging, i.e. you are
# using "dev tun" and "server" directives.

# EXAMPLE: Suppose you want to give
# Thelonious a fixed VPN IP address of 10.9.0.1.
# First uncomment out these lines:
;client-config-dir ccd
;route 10.9.0.0 255.255.255.252
# Then add this line to ccd/Thelonious:
#   ifconfig-push 10.9.0.1 10.9.0.2

# Suppose that you want to enable different
# firewall access policies for different groups
# of clients.  There are two methods:
# (1) Run multiple OpenVPN daemons, one for each
#     group, and firewall the TUN/TAP interface
#     for each group/daemon appropriately.
# (2) (Advanced) Create a script to dynamically
#     modify the firewall in response to access
#     from different clients.  See man
#     page for more info on learn-address script.
;learn-address ./script

# If enabled, this directive will configure
# all clients to redirect their default
# network gateway through the VPN, causing
# all IP traffic such as web browsing and
# and DNS lookups to go through the VPN
# (The OpenVPN server machine may need to NAT
# the TUN/TAP interface to the internet in
# order for this to work properly).
# CAVEAT: May break client's network config if
# client's local DHCP server packets get routed
# through the tunnel.  Solution: make sure
# client's local DHCP server is reachable via
# a more specific route than the default route
# of 0.0.0.0/0.0.0.0.
;push "redirect-gateway"

# Certain Windows-specific network settings
# can be pushed to clients, such as DNS
# or WINS server addresses.  CAVEAT:
# [http://openvpn.net/faq.html#dhcpcaveats](http://openvpn.net/faq.html#dhcpcaveats)
;push "dhcp-option DNS 10.0.0.1"
;push "dhcp-option WINS 10.0.0.1"

# Uncomment this directive to allow different
# clients to be able to "see" each other.
# By default, clients will only see the server.
# To force clients to only see the server, you
# will also need to appropriately firewall the
# server's TUN/TAP interface.
;client-to-client

# Uncomment this directive if multiple clients
# might connect with the same certificate/key
# files or common names.  This is recommended
# only for testing purposes.  For production use,
# each client should have its own certificate/key
# pair.
#
# IF YOU HAVE NOT GENERATED INDIVIDUAL
# CERTIFICATE/KEY PAIRS FOR EACH CLIENT,
# EACH HAVING ITS OWN UNIQUE "COMMON NAME",
# UNCOMMENT THIS LINE OUT.
;duplicate-cn

# The keepalive directive causes ping-like
# messages to be sent back and forth over
# the link so that each side knows when
# the other side has gone down.
# Ping every 10 seconds, assume that remote
# peer is down if no ping received during
# a 120 second time period.
keepalive 10 120

# For extra security beyond that provided
# by SSL/TLS, create an "HMAC firewall"
# to help block DoS attacks and UDP port flooding.
#
# Generate with:
#   openvpn --genkey --secret ta.key
#
# The server and each client must have
# a copy of this key.
# The second parameter should be '0'
# on the server and '1' on the clients.
;tls-auth ta.key 0 # This file is secret

# Select a cryptographic cipher.
# This config item must be copied to
# the client config file as well.
;cipher BF-CBC        # Blowfish (default)
;cipher AES-128-CBC   # AES
;cipher DES-EDE3-CBC  # Triple-DES

# Enable compression on the VPN link.
# If you enable it here, you must also
# enable it in the client config file.
comp-lzo

# The maximum number of concurrently connected
# clients we want to allow.
;max-clients 100

# It's a good idea to reduce the OpenVPN
# daemon's privileges after initialization.
#
# You can uncomment this out on
# non-Windows systems.
;user nobody
;group nobody

# The persist options will try to avoid
# accessing certain resources on restart
# that may no longer be accessible because
# of the privilege downgrade.
persist-key
persist-tun

# Output a short status file showing
# current connections, truncated
# and rewritten every minute.
status openvpn-status.log

# By default, log messages will go to the syslog (or
# on Windows, if running as a service, they will go to
# the "\Program Files\OpenVPN\log" directory).
# Use log or log-append to override this default.
# "log" will truncate the log file on OpenVPN startup,
# while "log-append" will append to it.  Use one
# or the other (but not both).
;log         openvpn.log
;log-append  openvpn.log

# Set the appropriate level of log
# file verbosity.
#
# 0 is silent, except for fatal errors
# 4 is reasonable for general usage
# 5 and 6 can help to debug connection problems
# 9 is extremely verbose
verb 3

# Silence repeating messages.  At most 20
# sequential messages of the same message
# category will be output to the log.
;mute 20The servers ip is 10.0.0.65 and I want to assign the clients the ip range of 10.0.0.200 to 10.0.0.20 When I try to start the server I get the message Fail.

Your help is much appreciated! 
Thanks

---

### Post by SeijiSensei on 2011-03-23
What does /var/log/messages show?  Running at "verb 3" like you specified should give you enough detail to diagnose what's wrong.

Are the clients also in the same 10.0.0.0/24 network (seems unlikely)?  If not, can they actually see the server?  Firewalling or routing problems?

---

### Post by pcarlos853 on 2011-03-23
My /var/log/messages:

> Mar 20 06:25:03 UbuntuSvr rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="621" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Mar 21 06:25:03 UbuntuSvr rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="621" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Mar 21 21:33:39 UbuntuSvr kernel: imklog 4.2.0, log source = /proc/kmsg started.
Mar 21 21:33:39 UbuntuSvr rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="634" x-info="http://www.rsyslog.com"] (re)start
Mar 21 21:33:39 UbuntuSvr rsyslogd: rsyslogd's groupid changed to 103
Mar 21 21:33:39 UbuntuSvr rsyslogd: rsyslogd's userid changed to 101
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] Initializing cgroup subsys cpuset
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] Initializing cgroup subsys cpu
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] Linux version 2.6.35-22-generic-pae (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu4) ) #33-Ubuntu SMP Sun Sep 19 22:14:14 UTC 2010 (Ubuntu 2.6.35-22.33-generic-pae 2.6.35.4)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] BIOS-provided physical RAM map:
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fc00000 (usable)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]  BIOS-e820: 00000000fc000000 - 0000000100000000 (reserved)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] DMI 2.4 present.
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] Hypervisor detected: Microsoft HyperV
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] HyperV: features 0x70, hints 0x0
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] last_pfn = 0x1fc00 max_arch_pfn = 0x1000000
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] Scanning 1 areas for low memory corruption
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] modified physical RAM map:
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]  modified: 0000000000010000 - 000000000009e000 (usable)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]  modified: 000000000009e000 - 00000000000a0000 (reserved)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]  modified: 0000000000100000 - 000000001fc00000 (usable)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]  modified: 00000000fc000000 - 0000000100000000 (reserved)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] found SMP MP-table at [c00fccd0] fccd0
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000001fc00000
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] RAMDISK: 17045000 - 17d40000
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] ACPI: RSDP 000ea020 00024 (v02    Xen)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] ACPI: XSDT fc006050 0003C (v01    Xen      HVM 00000000 HVML 00000000)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] ACPI: FACP fc005ea0 000F4 (v04    Xen      HVM 00000000 HVML 00000000)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] ACPI: DSDT fc002c40 031D7 (v02    Xen      HVM 00000000 INTL 20081204)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] ACPI: FACS fc002c00 00040
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] ACPI: APIC fc005fa0 00068 (v02    Xen      HVM 00000000 HVML 00000000)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] ACPI: HPET fc006010 00038 (v01    Xen      HVM 00000000 HVML 00000000)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] 0MB HIGHMEM available.
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] 508MB LOWMEM available.
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   mapped low ram: 0 - 1fc00000
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   low ram: 0 - 1fc00000
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] Zone PFN ranges:
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   DMA      0x00000001 -> 0x00001000
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   Normal   0x00001000 -> 0x0001fc00
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   HighMem  empty
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] Movable zone start PFN for each node
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] early_node_map[3] active PFN ranges
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]     0: 0x00000001 -> 0x00000002
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]     0: 0x00000010 -> 0x0000009e
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]     0: 0x00000100 -> 0x0001fc00
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] Using APIC driver default
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1f48
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-47
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 5 global_irq 5 low level)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 10 global_irq 10 low level)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 11 global_irq 11 low level)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] Allocating PCI resources starting at 1fc00000 (gap: 1fc00000:dc400000)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] PERCPU: Embedded 15 pages/cpu @c1400000 s39872 r0 d21568 u2097152
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] pcpu-alloc: s39872 r0 d21568 u2097152 alloc=1*2097152
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] pcpu-alloc: [0] 0 
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 128919
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.35-22-generic-pae root=/dev/mapper/UbuntuSvr-root ro quiet
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] Enabling fast FPU save and restore... done.
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] Initializing CPU#0
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] allocated 2600940 bytes of page_cgroup
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] Subtract (41 early reservations)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #2 [0000100000 - 00009f965c]   TEXT DATA BSS
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #3 [0017045000 - 0017d40000]         RAMDISK
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #4 [00009fa000 - 0000a010fc]             BRK
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #5 [00000fcce0 - 0000100000]   BIOS reserved
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #6 [00000fccd0 - 00000fcce0]    MP-table mpf
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #7 [000009e000 - 00000fcc00]   BIOS reserved
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #8 [00000fccc8 - 00000fccd0]   BIOS reserved
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #9 [00000fcc00 - 00000fccc8]    MP-table mpc
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #10 [0000010000 - 0000011000]      TRAMPOLINE
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #11 [0000011000 - 0000015000]     ACPI WAKEUP
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #12 [0001000000 - 0001001000]         BOOTMEM
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #13 [0001001000 - 00013f9000]         BOOTMEM
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #14 [00013f9000 - 00013f9004]         BOOTMEM
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #15 [00013f9040 - 00013f9100]         BOOTMEM
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #16 [00013f9100 - 00013f9160]         BOOTMEM
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #17 [00013f9180 - 00013fa980]         BOOTMEM
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #18 [00013fa980 - 00013fa9ad]         BOOTMEM
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #19 [00013fa9c0 - 00013fa9ef]         BOOTMEM
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #20 [00013faa00 - 00013fab20]         BOOTMEM
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #21 [00013fab40 - 00013fab80]         BOOTMEM
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #22 [00013fab80 - 00013fabc0]         BOOTMEM
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #23 [00013fabc0 - 00013fac00]         BOOTMEM
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #24 [00013fac00 - 00013fac40]         BOOTMEM
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #25 [00013fac40 - 00013fac80]         BOOTMEM
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #26 [00013fac80 - 00013fac90]         BOOTMEM
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #27 [00013facc0 - 00013facd0]         BOOTMEM
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #28 [00013fad00 - 00013fad53]         BOOTMEM
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #29 [00013fad80 - 00013fadd3]         BOOTMEM
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #30 [0001400000 - 000140f000]         BOOTMEM
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #31 [00013fce00 - 00013fce04]         BOOTMEM
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #32 [00013fce40 - 00013fce44]         BOOTMEM
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #33 [00013fce80 - 00013fce84]         BOOTMEM
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #34 [00013fcec0 - 00013fcec4]         BOOTMEM
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #35 [00013fcf00 - 00013fcfa8]         BOOTMEM
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #36 [00013fcfc0 - 00013fd028]         BOOTMEM
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #37 [00013fae00 - 00013fce00]         BOOTMEM
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #38 [000140f000 - 000144f000]         BOOTMEM
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #39 [000144f000 - 000146f000]         BOOTMEM
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]   #40 [000146f000 - 00016e9fec]         BOOTMEM
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] Initializing HighMem for node 0 (00000000:00000000)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] Memory: 490128k/520192k available (5085k kernel code, 29612k reserved, 2432k data, 704k init, 0k highmem)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] virtual kernel memory layout:
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]     vmalloc : 0xe0400000 - 0xffbfe000   ( 503 MB)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xdfc00000   ( 508 MB)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]       .init : 0xc0858000 - 0xc0908000   ( 704 kB)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]       .data : 0xc05f748a - 0xc0857768   (2432 kB)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]       .text : 0xc0100000 - 0xc05f748a   (5085 kB)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] Hierarchical RCU implementation.
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]     RCU-based detection of stalled CPUs is disabled.
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000]     Verbose stalled-CPUs detection is disabled.
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] NR_IRQS:2304 nr_irqs:256
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] Console: colour VGA+ 80x25
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] console [tty0] enabled
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] Fast TSC calibration using PIT
Mar 21 21:33:39 UbuntuSvr kernel: [    0.000000] Detected 1867.234 MHz processor.
Mar 21 21:33:39 UbuntuSvr kernel: [    0.024014] Calibrating delay loop (skipped), value calculated using timer frequency.. 3734.46 BogoMIPS (lpj=7468936)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.024040] pid_max: default: 32768 minimum: 301
Mar 21 21:33:39 UbuntuSvr kernel: [    0.024067] Security Framework initialized
Mar 21 21:33:39 UbuntuSvr kernel: [    0.024102] AppArmor: AppArmor initialized
Mar 21 21:33:39 UbuntuSvr kernel: [    0.024104] Yama: becoming mindful.
Mar 21 21:33:39 UbuntuSvr kernel: [    0.024176] Mount-cache hash table entries: 512
Mar 21 21:33:39 UbuntuSvr kernel: [    0.024374] Initializing cgroup subsys ns
Mar 21 21:33:39 UbuntuSvr kernel: [    0.024382] Initializing cgroup subsys cpuacct
Mar 21 21:33:39 UbuntuSvr kernel: [    0.024388] Initializing cgroup subsys memory
Mar 21 21:33:39 UbuntuSvr kernel: [    0.024401] Initializing cgroup subsys devices
Mar 21 21:33:39 UbuntuSvr kernel: [    0.024404] Initializing cgroup subsys freezer
Mar 21 21:33:39 UbuntuSvr kernel: [    0.024410] Initializing cgroup subsys net_cls
Mar 21 21:33:39 UbuntuSvr kernel: [    0.024513] mce: CPU supports 0 MCE banks
Mar 21 21:33:39 UbuntuSvr kernel: [    0.024541] Performance Events: unsupported p6 CPU model 15 no PMU driver, software events only.
Mar 21 21:33:39 UbuntuSvr kernel: [    0.034536] SMP alternatives: switching to UP code
Mar 21 21:33:39 UbuntuSvr kernel: [    0.194683] Freeing SMP alternatives: 24k freed
Mar 21 21:33:39 UbuntuSvr kernel: [    0.194698] ACPI: Core revision 20100428
Mar 21 21:33:39 UbuntuSvr kernel: [    0.196471] ftrace: converting mcount calls to 0f 1f 44 00 00
Mar 21 21:33:39 UbuntuSvr kernel: [    0.196477] ftrace: allocating 22394 entries in 44 pages
Mar 21 21:33:39 UbuntuSvr kernel: [    0.252098] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Mar 21 21:33:39 UbuntuSvr kernel: [    0.258249] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Mar 21 21:33:39 UbuntuSvr kernel: [    0.298107] CPU0: Intel(R) Core(TM)2 CPU          6320  @ 1.86GHz stepping 06
Mar 21 21:33:39 UbuntuSvr kernel: [    0.300147] Brought up 1 CPUs
Mar 21 21:33:39 UbuntuSvr kernel: [    0.300151] Total of 1 processors activated (3734.46 BogoMIPS).
Mar 21 21:33:39 UbuntuSvr kernel: [    0.300572] devtmpfs: initialized
Mar 21 21:33:39 UbuntuSvr kernel: [    0.302146] regulator: core version 0.5
Mar 21 21:33:39 UbuntuSvr kernel: [    0.302200] Time:  1:33:10  Date: 03/22/11
Mar 21 21:33:39 UbuntuSvr kernel: [    0.302242] NET: Registered protocol family 16
Mar 21 21:33:39 UbuntuSvr kernel: [    0.302369] EISA bus registered
Mar 21 21:33:39 UbuntuSvr kernel: [    0.302378] ACPI: bus type pci registered
Mar 21 21:33:39 UbuntuSvr kernel: [    0.302909] PCI: PCI BIOS revision 2.10 entry at 0xfb550, last bus=0
Mar 21 21:33:39 UbuntuSvr kernel: [    0.302912] PCI: Using configuration type 1 for base access
Mar 21 21:33:39 UbuntuSvr kernel: [    0.303905] bio: create slab <bio-0> at 0
Mar 21 21:33:39 UbuntuSvr kernel: [    0.306360] ACPI: Interpreter enabled
Mar 21 21:33:39 UbuntuSvr kernel: [    0.306363] ACPI: (supports S0 S5)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.306376] ACPI: Using IOAPIC for interrupt routing
Mar 21 21:33:39 UbuntuSvr kernel: [    0.317125] ACPI: No dock devices found.
Mar 21 21:33:39 UbuntuSvr kernel: [    0.317131] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Mar 21 21:33:39 UbuntuSvr kernel: [    0.317243] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Mar 21 21:33:39 UbuntuSvr kernel: [    0.317416] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
Mar 21 21:33:39 UbuntuSvr kernel: [    0.317419] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
Mar 21 21:33:39 UbuntuSvr kernel: [    0.317423] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
Mar 21 21:33:39 UbuntuSvr kernel: [    0.317426] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfbffffff]
Mar 21 21:33:39 UbuntuSvr kernel: [    0.322946] * Found PM-Timer Bug on the chipset. Due to workarounds for a bug,
Mar 21 21:33:39 UbuntuSvr kernel: [    0.322948] * this clock source is slow. Consider trying other clock sources
Mar 21 21:33:39 UbuntuSvr kernel: [    0.324071] pci 0000:00:01.3: quirk: [io  0x1f40-0x1f7f] claimed by PIIX4 ACPI
Mar 21 21:33:39 UbuntuSvr kernel: [    0.362044] ACPI: PCI Interrupt Link [LNKA] (IRQs *5 10 11)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.362276] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 *10 11)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.362468] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 10 *11)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.362660] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 10 11)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.362803] HEST: Table is not found!
Mar 21 21:33:39 UbuntuSvr kernel: [    0.362917] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Mar 21 21:33:39 UbuntuSvr kernel: [    0.362921] vgaarb: loaded
Mar 21 21:33:39 UbuntuSvr kernel: [    0.363104] SCSI subsystem initialized
Mar 21 21:33:39 UbuntuSvr kernel: [    0.363241] usbcore: registered new interface driver usbfs
Mar 21 21:33:39 UbuntuSvr kernel: [    0.363254] usbcore: registered new interface driver hub
Mar 21 21:33:39 UbuntuSvr kernel: [    0.363283] usbcore: registered new device driver usb
Mar 21 21:33:39 UbuntuSvr kernel: [    0.363402] ACPI: WMI: Mapper loaded
Mar 21 21:33:39 UbuntuSvr kernel: [    0.363404] PCI: Using ACPI for IRQ routing
Mar 21 21:33:39 UbuntuSvr kernel: [    0.364107] NetLabel: Initializing
Mar 21 21:33:39 UbuntuSvr kernel: [    0.364109] NetLabel:  domain hash size = 128
Mar 21 21:33:39 UbuntuSvr kernel: [    0.364111] NetLabel:  protocols = UNLABELED CIPSOv4
Mar 21 21:33:39 UbuntuSvr kernel: [    0.364122] NetLabel:  unlabeled traffic allowed by default
Mar 21 21:33:39 UbuntuSvr kernel: [    0.364172] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Mar 21 21:33:39 UbuntuSvr kernel: [    0.364200] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Mar 21 21:33:39 UbuntuSvr kernel: [    0.364206] hpet0: 3 comparators, 64-bit 62.500000 MHz counter
Mar 21 21:33:39 UbuntuSvr kernel: [    0.368018] Switching to clocksource tsc
Mar 21 21:33:39 UbuntuSvr kernel: [    0.379193] AppArmor: AppArmor Filesystem Enabled
Mar 21 21:33:39 UbuntuSvr kernel: [    0.379208] pnp: PnP ACPI init
Mar 21 21:33:39 UbuntuSvr kernel: [    0.379225] ACPI: bus type pnp registered
Mar 21 21:33:39 UbuntuSvr kernel: [    0.383746] pnp: PnP ACPI: found 13 devices
Mar 21 21:33:39 UbuntuSvr kernel: [    0.383749] ACPI: ACPI bus type pnp unregistered
Mar 21 21:33:39 UbuntuSvr kernel: [    0.383753] PnPBIOS: Disabled by ACPI PNP
Mar 21 21:33:39 UbuntuSvr kernel: [    0.383766] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
Mar 21 21:33:39 UbuntuSvr kernel: [    0.383773] system 00:02: [io  0x10c0-0x10e1] has been reserved
Mar 21 21:33:39 UbuntuSvr kernel: [    0.383776] system 00:02: [io  0xb044-0xb047] has been reserved
Mar 21 21:33:39 UbuntuSvr kernel: [    0.383783] system 00:04: [io  0x08a0-0x08a3] has been reserved
Mar 21 21:33:39 UbuntuSvr kernel: [    0.383786] system 00:04: [io  0x0cc0-0x0ccf] has been reserved
Mar 21 21:33:39 UbuntuSvr kernel: [    0.383789] system 00:04: [io  0x04d0-0x04d1] has been reserved
Mar 21 21:33:39 UbuntuSvr kernel: [    0.420212] NET: Registered protocol family 2
Mar 21 21:33:39 UbuntuSvr kernel: [    0.420274] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.420456] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.420549] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.420646] TCP: Hash tables configured (established 16384 bind 16384)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.420649] TCP reno registered
Mar 21 21:33:39 UbuntuSvr kernel: [    0.420652] UDP hash table entries: 256 (order: 1, 8192 bytes)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.420661] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.420727] NET: Registered protocol family 1
Mar 21 21:33:39 UbuntuSvr kernel: [    0.420738] pci 0000:00:00.0: Limiting direct PCI/PCI transfers
Mar 21 21:33:39 UbuntuSvr kernel: [    0.420839] pci 0000:00:01.0: PIIX3: Enabling Passive Release
Mar 21 21:33:39 UbuntuSvr kernel: [    0.420995] pci 0000:00:01.0: Activating ISA DMA hang workarounds
Mar 21 21:33:39 UbuntuSvr kernel: [    0.422192] cpufreq-nforce2: No nForce2 chipset.
Mar 21 21:33:39 UbuntuSvr kernel: [    0.422225] Scanning for low memory corruption every 60 seconds
Mar 21 21:33:39 UbuntuSvr kernel: [    0.422413] audit: initializing netlink socket (disabled)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.422423] type=2000 audit(1300757589.416:1): initialized
Mar 21 21:33:39 UbuntuSvr kernel: [    0.434937] Trying to unpack rootfs image as initramfs...
Mar 21 21:33:39 UbuntuSvr kernel: [    0.448090] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Mar 21 21:33:39 UbuntuSvr kernel: [    0.460099] VFS: Disk quotas dquot_6.5.2
Mar 21 21:33:39 UbuntuSvr kernel: [    0.460169] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.460807] fuse init (API version 7.14)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.460901] msgmni has been set to 957
Mar 21 21:33:39 UbuntuSvr kernel: [    0.468246] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.468250] io scheduler noop registered
Mar 21 21:33:39 UbuntuSvr kernel: [    0.468252] io scheduler deadline registered
Mar 21 21:33:39 UbuntuSvr kernel: [    0.468267] io scheduler cfq registered (default)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.468363] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar 21 21:33:39 UbuntuSvr kernel: [    0.468386] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Mar 21 21:33:39 UbuntuSvr kernel: [    0.468565] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Mar 21 21:33:39 UbuntuSvr kernel: [    0.468571] ACPI: Power Button [PWRF]
Mar 21 21:33:39 UbuntuSvr kernel: [    0.468675] input: Sleep Button as /devices/LNXSYSTM:00/LNXSLPBN:00/input/input1
Mar 21 21:33:39 UbuntuSvr kernel: [    0.468679] ACPI: Sleep Button [SLPF]
Mar 21 21:33:39 UbuntuSvr kernel: [    0.473689] ERST: Table is not found!
Mar 21 21:33:39 UbuntuSvr kernel: [    0.473865] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Mar 21 21:33:39 UbuntuSvr kernel: [    0.474783] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Mar 21 21:33:39 UbuntuSvr kernel: [    0.476445] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Mar 21 21:33:39 UbuntuSvr kernel: [    0.480162] isapnp: Scanning for PnP cards...
Mar 21 21:33:39 UbuntuSvr kernel: [    0.488493] brd: module loaded
Mar 21 21:33:39 UbuntuSvr kernel: [    0.489059] loop: module loaded
Mar 21 21:33:39 UbuntuSvr kernel: [    0.495944] scsi0 : ata_piix
Mar 21 21:33:39 UbuntuSvr kernel: [    0.496059] scsi1 : ata_piix
Mar 21 21:33:39 UbuntuSvr kernel: [    0.496097] ata1: PATA max MWDMA2 cmd 0x1f0 ctl 0x3f6 bmdma 0xc220 irq 14
Mar 21 21:33:39 UbuntuSvr kernel: [    0.496101] ata2: PATA max MWDMA2 cmd 0x170 ctl 0x376 bmdma 0xc228 irq 15
Mar 21 21:33:39 UbuntuSvr kernel: [    0.496442] Fixed MDIO Bus: probed
Mar 21 21:33:39 UbuntuSvr kernel: [    0.496478] PPP generic driver version 2.4.2
Mar 21 21:33:39 UbuntuSvr kernel: [    0.496527] tun: Universal TUN/TAP device driver, 1.6
Mar 21 21:33:39 UbuntuSvr kernel: [    0.496530] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Mar 21 21:33:39 UbuntuSvr kernel: [    0.496614] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Mar 21 21:33:39 UbuntuSvr kernel: [    0.496629] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Mar 21 21:33:39 UbuntuSvr kernel: [    0.496641] uhci_hcd: USB Universal Host Controller Interface driver
Mar 21 21:33:39 UbuntuSvr kernel: [    0.496758] uhci_hcd 0000:00:01.2: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Mar 21 21:33:39 UbuntuSvr kernel: [    0.496871] uhci_hcd 0000:00:01.2: UHCI Host Controller
Mar 21 21:33:39 UbuntuSvr kernel: [    0.496910] uhci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1
Mar 21 21:33:39 UbuntuSvr kernel: [    0.497250] uhci_hcd 0000:00:01.2: irq 23, io base 0x0000c200
Mar 21 21:33:39 UbuntuSvr kernel: [    0.497573] hub 1-0:1.0: USB hub found
Mar 21 21:33:39 UbuntuSvr kernel: [    0.497579] hub 1-0:1.0: 2 ports detected
Mar 21 21:33:39 UbuntuSvr kernel: [    0.497984] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Mar 21 21:33:39 UbuntuSvr kernel: [    0.548713] serio: i8042 KBD port at 0x60,0x64 irq 1
Mar 21 21:33:39 UbuntuSvr kernel: [    0.548722] serio: i8042 AUX port at 0x60,0x64 irq 12
Mar 21 21:33:39 UbuntuSvr kernel: [    0.548844] mice: PS/2 mouse device common for all mice
Mar 21 21:33:39 UbuntuSvr kernel: [    0.549708] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
Mar 21 21:33:39 UbuntuSvr kernel: [    0.550244] rtc_cmos 00:06: RTC can wake from S4
Mar 21 21:33:39 UbuntuSvr kernel: [    0.550287] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
Mar 21 21:33:39 UbuntuSvr kernel: [    0.550390] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
Mar 21 21:33:39 UbuntuSvr kernel: [    0.550504] device-mapper: uevent: version 1.0.3
Mar 21 21:33:39 UbuntuSvr kernel: [    0.556016] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
Mar 21 21:33:39 UbuntuSvr kernel: [    0.559856] device-mapper: multipath: version 1.1.1 loaded
Mar 21 21:33:39 UbuntuSvr kernel: [    0.559860] device-mapper: multipath round-robin: version 1.0.0 loaded
Mar 21 21:33:39 UbuntuSvr kernel: [    0.559994] EISA: Probing bus 0 at eisa.0
Mar 21 21:33:39 UbuntuSvr kernel: [    0.559997] EISA: Cannot allocate resource for mainboard
Mar 21 21:33:39 UbuntuSvr kernel: [    0.560000] Cannot allocate resource for EISA slot 1
Mar 21 21:33:39 UbuntuSvr kernel: [    0.560002] Cannot allocate resource for EISA slot 2
Mar 21 21:33:39 UbuntuSvr kernel: [    0.560004] Cannot allocate resource for EISA slot 3
Mar 21 21:33:39 UbuntuSvr kernel: [    0.560006] Cannot allocate resource for EISA slot 4
Mar 21 21:33:39 UbuntuSvr kernel: [    0.560009] Cannot allocate resource for EISA slot 5
Mar 21 21:33:39 UbuntuSvr kernel: [    0.560011] Cannot allocate resource for EISA slot 6
Mar 21 21:33:39 UbuntuSvr kernel: [    0.560013] Cannot allocate resource for EISA slot 7
Mar 21 21:33:39 UbuntuSvr kernel: [    0.560015] Cannot allocate resource for EISA slot 8
Mar 21 21:33:39 UbuntuSvr kernel: [    0.560017] EISA: Detected 0 cards.
Mar 21 21:33:39 UbuntuSvr kernel: [    0.568066] cpuidle: using governor ladder
Mar 21 21:33:39 UbuntuSvr kernel: [    0.568069] cpuidle: using governor menu
Mar 21 21:33:39 UbuntuSvr kernel: [    0.568336] TCP cubic registered
Mar 21 21:33:39 UbuntuSvr kernel: [    0.568479] NET: Registered protocol family 10
Mar 21 21:33:39 UbuntuSvr kernel: [    0.568813] lo: Disabled Privacy Extensions
Mar 21 21:33:39 UbuntuSvr kernel: [    0.569001] NET: Registered protocol family 17
Mar 21 21:33:39 UbuntuSvr kernel: [    0.569048] Using IPI No-Shortcut mode
Mar 21 21:33:39 UbuntuSvr kernel: [    0.569148] registered taskstats version 1
Mar 21 21:33:39 UbuntuSvr kernel: [    0.569595]   Magic number: 3:765:559
Mar 21 21:33:39 UbuntuSvr kernel: [    0.569686] rtc_cmos 00:06: setting system clock to 2011-03-22 01:33:10 UTC (1300757590)
Mar 21 21:33:39 UbuntuSvr kernel: [    0.569689] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Mar 21 21:33:39 UbuntuSvr kernel: [    0.569691] EDD information not available.
Mar 21 21:33:39 UbuntuSvr kernel: [    0.752241] ata1.01: ATA-7: QEMU HARDDISK, 0.10.2, max UDMA/100
Mar 21 21:33:39 UbuntuSvr kernel: [    0.752246] ata1.01: 251658240 sectors, multi 16: LBA48 
Mar 21 21:33:39 UbuntuSvr kernel: [    0.752997] ata2.01: ATAPI: QEMU DVD-ROM, 0.10.2, max UDMA/100
Mar 21 21:33:39 UbuntuSvr kernel: [    0.754948] ata2.01: configured for MWDMA2
Mar 21 21:33:39 UbuntuSvr kernel: [    0.755264] ata1.01: configured for MWDMA2
Mar 21 21:33:39 UbuntuSvr kernel: [    0.807871] usb 1-2: new full speed USB device using uhci_hcd and address 2
Mar 21 21:33:39 UbuntuSvr kernel: [    1.199356] Freeing initrd memory: 13292k freed
Mar 21 21:33:39 UbuntuSvr kernel: [    1.255633] isapnp: No Plug & Play device found
Mar 21 21:33:39 UbuntuSvr kernel: [    1.255822] scsi 0:0:1:0: Direct-Access     ATA      QEMU HARDDISK    0.10 PQ: 0 ANSI: 5
Mar 21 21:33:39 UbuntuSvr kernel: [    1.256035] sd 0:0:1:0: Attached scsi generic sg0 type 0
Mar 21 21:33:39 UbuntuSvr kernel: [    1.256925] scsi 1:0:1:0: CD-ROM            QEMU     QEMU DVD-ROM     0.10 PQ: 0 ANSI: 5
Mar 21 21:33:39 UbuntuSvr kernel: [    1.257392] sd 0:0:1:0: [sda] 251658240 512-byte logical blocks: (128 GB/120 GiB)
Mar 21 21:33:39 UbuntuSvr kernel: [    1.257447] sd 0:0:1:0: [sda] Write Protect is off
Mar 21 21:33:39 UbuntuSvr kernel: [    1.257474] sd 0:0:1:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Mar 21 21:33:39 UbuntuSvr kernel: [    1.258315]  sda:sr0: scsi3-mmc drive: 4x/4x xa/form2 tray
Mar 21 21:33:39 UbuntuSvr kernel: [    1.355614] Uniform CD-ROM driver Revision: 3.20
Mar 21 21:33:39 UbuntuSvr kernel: [    1.355809] sr 1:0:1:0: Attached scsi generic sg1 type 5
Mar 21 21:33:39 UbuntuSvr kernel: [    1.355863]  sda1 sda2 < sda5 >
Mar 21 21:33:39 UbuntuSvr kernel: [    1.356812] sd 0:0:1:0: [sda] Attached SCSI disk
Mar 21 21:33:39 UbuntuSvr kernel: [    1.356826] Freeing unused kernel memory: 704k freed
Mar 21 21:33:39 UbuntuSvr kernel: [    1.357313] Write protecting the kernel text: 5088k
Mar 21 21:33:39 UbuntuSvr kernel: [    1.357484] Write protecting the kernel read-only data: 2012k
Mar 21 21:33:39 UbuntuSvr kernel: [    2.296727] udev[69]: starting version 163
Mar 21 21:33:39 UbuntuSvr kernel: [    4.226162] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Mar 21 21:33:39 UbuntuSvr kernel: [    4.226282] 8139cp 0000:00:04.0: PCI INT A -> GSI 32 (level, low) -> IRQ 32
Mar 21 21:33:39 UbuntuSvr kernel: [    4.466793] 8139cp 0000:00:04.0: eth0: RTL-8139C+ at 0xe0438000, 0e:f3:e4:d8:71:f6, IRQ 32
Mar 21 21:33:39 UbuntuSvr kernel: [    4.620222] 8139too: 8139too Fast Ethernet driver 0.9.28
Mar 21 21:33:39 UbuntuSvr kernel: [    5.291636] usbcore: registered new interface driver hiddev
Mar 21 21:33:39 UbuntuSvr kernel: [    5.563037] FDC 0 is a S82078B
Mar 21 21:33:39 UbuntuSvr kernel: [    5.903580] input: QEMU 0.10.2 QEMU USB Tablet as /devices/pci0000:00/0000:00:01.2/usb1/1-2/1-2:1.0/input/input3
Mar 21 21:33:39 UbuntuSvr kernel: [    5.913554] generic-usb 0003:0627:0001.0001: input,hidraw0: USB HID v0.01 Pointer [QEMU 0.10.2 QEMU USB Tablet] on usb-0000:00:01.2-2/input0
Mar 21 21:33:39 UbuntuSvr kernel: [    5.913765] usbcore: registered new interface driver usbhid
Mar 21 21:33:39 UbuntuSvr kernel: [    5.913768] usbhid: USB HID core driver
Mar 21 21:33:39 UbuntuSvr kernel: [   14.253020] EXT4-fs (dm-0): INFO: recovery required on readonly filesystem
Mar 21 21:33:39 UbuntuSvr kernel: [   14.253031] EXT4-fs (dm-0): write access will be enabled during recovery
Mar 21 21:33:39 UbuntuSvr kernel: [   15.336955] EXT4-fs (dm-0): orphan cleanup on readonly fs
Mar 21 21:33:39 UbuntuSvr kernel: [   15.343030] EXT4-fs (dm-0): 1 orphan inode deleted
Mar 21 21:33:39 UbuntuSvr kernel: [   15.343034] EXT4-fs (dm-0): recovery complete
Mar 21 21:33:39 UbuntuSvr kernel: [   15.353641] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
Mar 21 21:33:39 UbuntuSvr kernel: [   20.513715] udev[312]: starting version 163
Mar 21 21:33:39 UbuntuSvr kernel: [   20.958002] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
Mar 21 21:33:39 UbuntuSvr kernel: [   21.385897] lp: driver loaded but no devices found
Mar 21 21:33:39 UbuntuSvr kernel: [   23.119796] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input4
Mar 21 21:33:39 UbuntuSvr kernel: [   23.721994] type=1400 audit(1300757613.649:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=441 comm="apparmor_parser"
Mar 21 21:33:39 UbuntuSvr kernel: [   23.722790] type=1400 audit(1300757613.649:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=441 comm="apparmor_parser"
Mar 21 21:33:39 UbuntuSvr kernel: [   23.723218] type=1400 audit(1300757613.649:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=441 comm="apparmor_parser"
Mar 21 21:33:39 UbuntuSvr kernel: [   24.647070] parport_pc 00:0c: reported by Plug and Play ACPI
Mar 21 21:33:39 UbuntuSvr kernel: [   24.647707] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Mar 21 21:33:39 UbuntuSvr kernel: [   24.853496] lp0: using parport0 (interrupt-driven).
Mar 21 21:33:39 UbuntuSvr kernel: [   25.106519] ppdev: user-space parallel port driver
Mar 21 21:33:39 UbuntuSvr kernel: [   26.007000] eth0: link up, 100Mbps, full-duplex, lpa 0x05E1
Mar 21 21:33:40 UbuntuSvr kernel: [   30.591015] type=1400 audit(1300757620.957:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=676 comm="apparmor_parser"
Mar 21 21:33:40 UbuntuSvr kernel: [   30.591991] type=1400 audit(1300757620.957:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=676 comm="apparmor_parser"
Mar 21 21:33:40 UbuntuSvr kernel: [   30.602104] type=1400 audit(1300757620.969:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=676 comm="apparmor_parser"
Mar 21 21:33:41 UbuntuSvr kernel: [   30.673693] type=1400 audit(1300757621.041:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=680 comm="apparmor_parser"
Mar 21 21:33:41 UbuntuSvr kernel: [   30.683762] padlock: VIA PadLock not detected.
Mar 21 21:33:41 UbuntuSvr kernel: [   31.187822] padlock: VIA PadLock Hash Engine not detected.
Mar 21 21:33:44 UbuntuSvr kernel: [   34.026913] Adding 1523708k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:1523708k 
Mar 21 22:49:29 UbuntuSvr sudo: pam_sm_authenticate: Called
Mar 21 22:49:29 UbuntuSvr sudo: pam_sm_authenticate: username = [carlos]
Mar 21 22:49:29 UbuntuSvr sudo: Passphrase file wrapped
Mar 21 23:50:35 UbuntuSvr sudo: pam_sm_authenticate: Called
Mar 21 23:50:35 UbuntuSvr sudo: pam_sm_authenticate: username = [carlos]
Mar 21 23:50:35 UbuntuSvr sudo: pam_sm_authenticate: /home/carlos is already mounted
Mar 22 00:00:46 UbuntuSvr kernel: [ 8855.903424] eth0: link up, 100Mbps, full-duplex, lpa 0x05E1
Mar 22 00:06:40 UbuntuSvr kernel: [ 9210.266024] tun0: Disabled Privacy Extensions
Mar 22 06:25:06 UbuntuSvr rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="634" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Mar 22 12:36:53 UbuntuSvr sudo: pam_sm_authenticate: Called
Mar 22 12:36:53 UbuntuSvr sudo: pam_sm_authenticate: username = [carlos]
Mar 22 12:36:53 UbuntuSvr sudo: pam_sm_authenticate: /home/carlos is already mounted
Mar 22 15:44:27 UbuntuSvr sudo: pam_sm_authenticate: Called
Mar 22 15:44:27 UbuntuSvr sudo: pam_sm_authenticate: username = [carlos]
Mar 22 15:44:27 UbuntuSvr sudo: pam_sm_authenticate: /home/carlos is already mounted
Mar 22 15:45:00 UbuntuSvr kernel: [65509.721224] tun0: Disabled Privacy Extensions
Mar 22 16:18:01 UbuntuSvr sudo: pam_sm_authenticate: Called
Mar 22 16:18:01 UbuntuSvr sudo: pam_sm_authenticate: username = [carlos]
Mar 22 16:18:01 UbuntuSvr sudo: pam_sm_authenticate: /home/carlos is already mounted
Mar 22 16:21:28 UbuntuSvr kernel: [67698.416191] tun0: Disabled Privacy Extensions
Mar 22 20:51:05 UbuntuSvr sudo: pam_sm_authenticate: Called
Mar 22 20:51:05 UbuntuSvr sudo: pam_sm_authenticate: username = [carlos]
Mar 22 20:51:05 UbuntuSvr sudo: pam_sm_authenticate: /home/carlos is already mounted
Mar 22 23:04:35 UbuntuSvr sudo: pam_sm_authenticate: Called
Mar 22 23:04:35 UbuntuSvr sudo: pam_sm_authenticate: username = [carlos]
Mar 22 23:04:35 UbuntuSvr sudo: pam_sm_authenticate: /home/carlos is already mounted
Mar 22 23:21:49 UbuntuSvr sudo: pam_sm_authenticate: Called
Mar 22 23:21:49 UbuntuSvr sudo: pam_sm_authenticate: username = [carlos]
Mar 22 23:21:49 UbuntuSvr sudo: pam_sm_authenticate: /home/carlos is already mounted
Mar 22 23:50:22 UbuntuSvr sudo: pam_sm_authenticate: Called
Mar 22 23:50:22 UbuntuSvr sudo: pam_sm_authenticate: username = [carlos]
Mar 22 23:50:22 UbuntuSvr sudo: pam_sm_authenticate: /home/carlos is already mounted
Mar 22 23:50:36 UbuntuSvr kernel: [94645.888609] ip_tables: (C) 2000-2006 Netfilter Core Team
Mar 23 00:00:52 UbuntuSvr sudo: pam_sm_authenticate: Called
Mar 23 00:00:52 UbuntuSvr sudo: pam_sm_authenticate: username = [carlos]
Mar 23 00:00:52 UbuntuSvr sudo: pam_sm_authenticate: /home/carlos is already mounted
Mar 23 00:15:20 UbuntuSvr sudo: pam_sm_authenticate: Called
Mar 23 00:15:20 UbuntuSvr sudo: pam_sm_authenticate: username = [carlos]
Mar 23 00:15:20 UbuntuSvr sudo: pam_sm_authenticate: /home/carlos is already mounted
Mar 23 06:25:06 UbuntuSvr rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="634" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Mar 23 06:25:06 UbuntuSvr rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="634" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Mar 23 15:47:52 UbuntuSvr sudo: pam_sm_authenticate: Called
Mar 23 15:47:52 UbuntuSvr sudo: pam_sm_authenticate: username = [carlos]
Mar 23 15:47:52 UbuntuSvr sudo: pam_sm_authenticate: /home/carlos is already mounted 

The client (my netbook) is on the same 10.0.0.x network right now. When I didn't change anything in the default config the OpenVPN server could start, but when I connected I was unable to access the Internet or my LAN from the client. So I tried changing the config, but now the server wont even start.

Thanks for the help!

---

### Post by SeijiSensei on 2011-03-23
I suggest you start with a [static-key configuration]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html") using the server and just one client.  

The IP's you use for the tunnels should not be in the same address range as the server's interface.  Use another block like 10.1.0.0/24.  My guess is you're having routing problems because there are overlapping addresses.  You may need to use the "up" directive to run a routing script when the VPN service starts, too.

Static-key configurations are the easiest ones to set up.  Once you've gotten a working configuration you can start to look into supporting multiple clients.

If you need to post another log, grep for the OpenVPN entries like this:

```
grep -i openvpn /var/log/message
```

It'll help us separate the wheat from the chaff, as the proverb says.

---

### Post by pcarlos853 on 2011-03-24
I followed the instructions for the static key how to and now the server starts with the [ok] message! But I am now having client side problems (I think). I am able to connect to the server, but then I don't have access to the Internet or the LAN. When I run ip config on the client I get this: 
> tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.0.0.200  P-t-P:10.0.0.201  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:1980 (1.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:2c:5c:bf:d1  
          inet addr:10.111.1.121  Bcast:10.111.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2cff:fe5c:bfd1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8014 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5737158 (5.7 MB)  TX bytes:1647530 (1.6 MB)
My Servers config is
> 
dev tun
ifconfig 10.8.0.1 10.8.0.2
secret static.key
Thanks for the help! Also is static key any less secure then the normal mode?
Cheers

---

### Post by SeijiSensei on 2011-03-24
Here's a sample server-side configuration that I use:

```

dev tun
ifconfig 192.168.1.1 192.168.1.2
secret /etc/openvpn/keys/mykey.key
port 6574
user nobody
group nogroup
comp-lzo
ping 15
ping-restart 45
ping-timer-rem
persist-tun
persist-key
verb 3

```

The ping and persist directives keep the connection up during idle periods.  comp-lzo applies compression to the bitstream.  "verb 3" makes OpenVPN write informative messages to syslog.  I also use non-standard ports since I'm actually running half-a-dozen tunnels on this box, each on a separate port.

My client-side configuration is largely identical except the order of addresses in ifconfig is reversed, and the "remote" directive is added to tell the client where the server is located.  Clients often also have an "up" directive to tell OpenVPN to run a routing script when started.

The connectivity problems you're having arise from not adding an entry to the client's routing table telling it how to get to the remote network.  On the client, you'll need an "up" directive like this:

```
up ./route.sh
```

Create the file /etc/openvpn/route.sh like this:

```
ip route add 10.111.1.0/24 via 10.0.0.201
```

Mark the script executable with 'sudo chmod a+x /etc/openvpn/route.sh'.

This tells the client that traffic intended for the 10.111.1.0/24 network should be sent over the tunnel rather than via the host's default route.  The server's tunnel address is used as gateway address for that network.

Static-key configurations are not any less secure assuming you generated the key with "openvpn --genkey".  However they are more work if you want to support lots of clients, since each needs it own port and IP configuration.

---

### Post by pcarlos853 on 2011-03-29
Sorry for the long delay, it was finals week at school. Anyway I have tried out your server.conf but I still could not connect. I decided to reinstall Ubuntu 10.10 so that I can have a clean environment. I followed the instructions from openvpn's how to and I think I am getting closer to getting a working openvpn environment. The new error that I am getting is:

> carlos@ps3:/etc/openvpn$ openvpn client.conf
Tue Mar 29 23:01:11 2011 OpenVPN 2.1.0 i686-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [MH] [PF_INET6] [eurephia] built on Jul 12 2010
Tue Mar 29 23:01:11 2011 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Tue Mar 29 23:01:11 2011 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Tue Mar 29 23:01:11 2011 LZO compression initialized
Tue Mar 29 23:01:11 2011 Control Channel MTU parms [ L:1542 D:138 EF:38 EB:0 ET:0 EL:0 ]
Tue Mar 29 23:01:11 2011 Data Channel MTU parms [ L:1542 D:1450 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
Tue Mar 29 23:01:11 2011 Local Options hash (VER=V4): '41690919'
Tue Mar 29 23:01:11 2011 Expected Remote Options hash (VER=V4): '530fdded'
Tue Mar 29 23:01:11 2011 Socket Buffers: R=[114688->131072] S=[114688->131072]
Tue Mar 29 23:01:11 2011 UDPv4 link local: [undef]
Tue Mar 29 23:01:11 2011 UDPv4 link remote: [AF_INET]173.66.59.230:1194
Tue Mar 29 23:01:11 2011 TLS: Initial packet from [AF_INET]173.66.59.230:1194, sid=0fecdd26 77b5196f
Tue Mar 29 23:01:11 2011 VERIFY ERROR: depth=1, error=self signed certificate in certificate chain: /C=US/ST=MD/L=Bethesda/O=SecureSolutions/CN=SecureSolutions_CA/emailAddress=blogofcarlos@gmail.com
Tue Mar 29 23:01:11 2011 TLS_ERROR: BIO read tls_read_plaintext error: error:14090086:SSL routines:SSL3_GET_SERVER_CERTIFICATE:certificate verify failed
Tue Mar 29 23:01:11 2011 TLS Error: TLS object -> incoming plaintext read error
Tue Mar 29 23:01:11 2011 TLS Error: TLS handshake failed
Tue Mar 29 23:01:11 2011 TCP/UDP: Closing socket
Tue Mar 29 23:01:11 2011 SIGUSR1[soft,tls-error] received, process restarting
Tue Mar 29 23:01:11 2011 Restart pause, 2 second(s)
^CTue Mar 29 23:01:12 2011 SIGINT[hard,init_instance] received, process exiting
carlos@ps3:/etc/openvpn$ My new client.conf:
> ##############################################
# Sample client-side OpenVPN 2.0 config file #
# for connecting to multi-client server.     #
#                                            #
# This configuration can be used by multiple #
# clients, however each client should have   #
# its own cert and key files.                #
#                                            #
# On Windows, you might want to rename this  #
# file so it has a .ovpn extension           #
##############################################

# Specify that we are a client and that we
# will be pulling certain config file directives
# from the server.
client

# Use the same setting as you are using on
# the server.
# On most systems, the VPN will not function
# unless you partially or fully disable
# the firewall for the TUN/TAP interface.
;dev tap
dev tun

# Windows needs the TAP-Win32 adapter name
# from the Network Connections panel
# if you have more than one.  On XP SP2,
# you may need to disable the firewall
# for the TAP adapter.
;dev-node MyTap

# Are we connecting to a TCP or
# UDP server?  Use the same setting as
# on the server.
;proto tcp
proto udp

# The hostname/IP and port of the server.
# You can have multiple remote entries
# to load balance between the servers.
remote myhostip.com 1194
# remote my-server-2 1194

# Choose a random host from the remote
# list for load-balancing.  Otherwise
# try hosts in the order specified.
;remote-random

# Keep trying indefinitely to resolve the
# host name of the OpenVPN server.  Very useful
# on machines which are not permanently connected
# to the internet such as laptops.
resolv-retry infinite

# Most clients don't need to bind to
# a specific local port number.
nobind

# Downgrade privileges after initialization (non-Windows only)
;user nobody
;group nobody

# Try to preserve some state across restarts.
persist-key
persist-tun

# If you are connecting through an
# HTTP proxy to reach the actual OpenVPN
# server, put the proxy server/IP and
# port number here.  See the man page
# if your proxy server requires
# authentication.
;http-proxy-retry # retry on connection failures
;http-proxy [proxy server] [proxy port #]

# Wireless networks often produce a lot
# of duplicate packets.  Set this flag
# to silence duplicate packet warnings.
;mute-replay-warnings

# SSL/TLS parms.
# See the server config file for more
# description.  It's best to use
# a separate .crt/.key file pair
# for each client.  A single ca
# file can be used for all clients.
ca ca.crt
cert client1.crt
key client1.key

# Verify server certificate by checking
# that the certicate has the nsCertType
# field set to "server".  This is an
# important precaution to protect against
# a potential attack discussed here:
#  [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm)
#
# To use this feature, you will need to generate
# your server certificates with the nsCertType
# field set to "server".  The build-key-server
# script in the easy-rsa folder will do this.
ns-cert-type server

# If a tls-auth key is used on the server
# then every client must also have the key.
;tls-auth ta.key 1

# Select a cryptographic cipher.
# If the cipher option is used on the server
# then you must also specify it here.
;cipher x

# Enable compression on the VPN link.
# Don't enable this unless it is also
# enabled in the server config file.
comp-lzo

# Set log file verbosity.
verb 3

# Silence repeating messages
;mute 20My server.conf
> #################################################
# Sample OpenVPN 2.0 config file for            #
# multi-client server.                          #
#                                               #
# This file is for the server side              #
# of a many-clients <-> one-server              #
# OpenVPN configuration.                        #
#                                               #
# OpenVPN also supports                         #
# single-machine <-> single-machine             #
# configurations (See the Examples page         #
# on the web site for more info).               #
#                                               #
# This config should work on Windows            #
# or Linux/BSD systems.  Remember on            #
# Windows to quote pathnames and use            #
# double backslashes, e.g.:                     #
# "C:\\Program Files\\OpenVPN\\config\\foo.key" #
#                                               #
# Comments are preceded with '#' or ';'         #
#################################################

# Which local IP address should OpenVPN
# listen on? (optional)
;local a.b.c.d

# Which TCP/UDP port should OpenVPN listen on?
# If you want to run multiple OpenVPN instances
# on the same machine, use a different port
# number for each one.  You will need to
# open up this port on your firewall.
port 1194

# TCP or UDP server?
;proto tcp
proto udp

# "dev tun" will create a routed IP tunnel,
# "dev tap" will create an ethernet tunnel.
# Use "dev tap0" if you are ethernet bridging
# and have precreated a tap0 virtual interface
# and bridged it with your ethernet interface.
# If you want to control access policies
# over the VPN, you must create firewall
# rules for the the TUN/TAP interface.
# On non-Windows systems, you can give
# an explicit unit number, such as tun0.
# On Windows, use "dev-node" for this.
# On most systems, the VPN will not function
# unless you partially or fully disable
# the firewall for the TUN/TAP interface.
;dev tap
dev tun

# Windows needs the TAP-Win32 adapter name
# from the Network Connections panel if you
# have more than one.  On XP SP2 or higher,
# you may need to selectively disable the
# Windows firewall for the TAP adapter.
# Non-Windows systems usually don't need this.
;dev-node MyTap

# SSL/TLS root certificate (ca), certificate
# (cert), and private key (key).  Each client
# and the server must have their own cert and
# key file.  The server and all clients will
# use the same ca file.
#
# See the "easy-rsa" directory for a series
# of scripts for generating RSA certificates
# and private keys.  Remember to use
# a unique Common Name for the server
# and each of the client certificates.
#
# Any X509 key management system can be used.
# OpenVPN can also use a PKCS #12 formatted key file
# (see "pkcs12" directive in man page).
ca ca.crt
cert server.crt
key server.key  # This file should be kept secret

# Diffie hellman parameters.
# Generate your own with:
#   openssl dhparam -out dh1024.pem 1024
# Substitute 2048 for 1024 if you are using
# 2048 bit keys. 
dh dh1024.pem

# Configure server mode and supply a VPN subnet
# for OpenVPN to draw client addresses from.
# The server will take 10.8.0.1 for itself,
# the rest will be made available to clients.
# Each client will be able to reach the server
# on 10.8.0.1. Comment this line out if you are
# ethernet bridging. See the man page for more info.
server 10.8.0.0 255.255.255.0

# Maintain a record of client <-> virtual IP address
# associations in this file.  If OpenVPN goes down or
# is restarted, reconnecting clients can be assigned
# the same virtual IP address from the pool that was
# previously assigned.
ifconfig-pool-persist ipp.txt
Thanks for your help! I truly appreciate it!

---

### Post by spynappels on 2011-03-30
Your original server conf had an issue in that you were telling it to run in both Routed and Bridged mode, you have to select one or the other, this section is not shown in your last post, so I'm not sure if you have the same in your current conf.

```
server 10.0.0.0 255.255.255.0
```

```
server-bridge 10.0.0.4 255.255.255.0 10.0.0.200 10.0.0.215
```

Does your current conf have both those lines in it?

---

### Post by pcarlos853 on 2011-03-30
I only have this line in my server conf > server 10.8.0.0 255.255.255.0 I do not have > server-bridge 10.0.0.4 255.255.255.0 10.0.0.200 10.0.0.215I think my problem is: > Tue Mar 29 23:01:11 2011 VERIFY ERROR: depth=1, error=self signed  certificate in certificate chain:  /C=US/ST=MD/L=Bethesda/O=SecureSolutions/CN=SecureSolutions_CA/emailAddress=carlos894@gmail.com
Tue Mar 29 23:01:11 2011 TLS_ERROR: BIO read tls_read_plaintext error:  error:14090086:SSL routines:SSL3_GET_SERVER_CERTIFICATE:certificate  verify failed
Tue Mar 29 23:01:11 2011 TLS Error: TLS object -> incoming plaintext read error
Tue Mar 29 23:01:11 2011 TLS Error: TLS handshake failed
Tue Mar 29 23:01:11 2011 TCP/UDP: Closing socketI still can't get this to work. Does anyone have any suggestions? 

Thanks!

---

