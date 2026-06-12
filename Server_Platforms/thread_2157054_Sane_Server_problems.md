---
title: "Sane Server problems"
date: 2013-06-24
forum: Server Platforms
---

### Post by Z.K. on 2013-06-24
I am trying to get my scanner to work with my Ubuntu 12.04 server, no desktop.  Now I have managed to get it to work locally and I can even see it from my client machine, but when I try to access it using simple scan, I get a Access to resource has been denied.  I was wondering if anyone else has experience setting up saned on a local network and can give me some pointers on how to solve my problem.  It looks to be some kind of permission problem, but I am not exactly sure what.

I ran saned -d255 on the server and then on the on the client I opened up Simple Scan.  I only get the error when I click the scan button and not when I open the application.

This is what I recieved after opening the Simple Scan application:
> 
server@Server:~$ saned -d255
[saned] main: starting debug mode (level 255)
[saned] read_config: searching for config file
[saned] read_config: data port range: 11000 - 11100
[saned] read_config: done reading config
[saned] saned (AF-indep+IPv6) from sane-backends 1.0.22 starting up
[saned] do_bindings: trying to get port for service "sane-port" (getaddrinfo)
[saned] do_bindings: [1] socket () using IPv6
[saned] do_bindings: [1] setsockopt ()
[saned] do_bindings: [1] bind () to port 6566
[saned] do_bindings: [1] listen ()
[saned] do_bindings: [0] socket () using IPv4
[saned] do_bindings: [0] setsockopt ()
[saned] do_bindings: [0] bind () to port 6566
[saned] do_bindings: [0] bind failed: Address already in use
[saned] run_standalone: spawning Avahi process
[saned] run_standalone: waiting for control connection
[saned] saned_avahi_callback: AVAHI_CLIENT_S_RUNNING
[saned] saned_create_avahi_services: adding service 'saned'
[saned] saned_avahi_group_callback: service 'saned' successfully established
[saned] handle_connection: processing client connection
[saned] check_host: detected an IPv4-mapped address
[saned] check_host: access by remote host: ::ffff:192.168.0.199
[saned] check_host: remote host is not IN_LOOPBACK nor IN6_LOOPBACK
[saned] check_host: local hostname: Print-Server.merlin.home
[saned] check_host: local hostname(s) (from DNS): Print-Server.merlin.home
[saned] check_host: local hostname(s) (from DNS): (null)
[saned] check_host: local hostname(s) (from DNS): (null)
[saned] check_host: remote host doesn't have same addr as local
[saned] check_host: opening config file: /etc/hosts.equiv
[saned] check_host: can't open config file: /etc/hosts.equiv (No such file or directory)
[saned] check_host: opening config file: saned.conf
[saned] check_host: config file line: `# saned.conf'
[saned] check_host: config file line: `# Configuration for the saned daemon'
[saned] check_host: config file line: `'
[saned] check_host: config file line: `## Daemon options'
[saned] check_host: config file line: `# Port range for the data connection. Choose a range inside [1024 - 65535].'
[saned] check_host: config file line: `# Avoid specifying too large a range, for performance reasons.'
[saned] check_host: config file line: `#'
[saned] check_host: config file line: `# ONLY use this if your saned server is sitting behind a firewall. If your'
[saned] check_host: config file line: `# firewall is a Linux machine, we strongly recommend using the'
[saned] check_host: config file line: `# Netfilter nf_conntrack_sane connection tracking module instead.'
[saned] check_host: config file line: `#'
[saned] check_host: config file line: `data_portrange = 11000 - 11100'
[saned] check_host: config file line: `'
[saned] check_host: config file line: `'
[saned] check_host: config file line: `## Access list'
[saned] check_host: config file line: `# A list of host names, IP addresses or IP subnets (CIDR notation) that'
[saned] check_host: config file line: `# are permitted to use local SANE devices. IPv6 addresses must be enclosed'
[saned] check_host: config file line: `# in brackets, and should always be specified in their compressed form.'
[saned] check_host: config file line: `#'
[saned] check_host: config file line: `# The hostname matching is not case-sensitive.'
[saned] check_host: config file line: `'
[saned] check_host: config file line: `#scan-client.somedomain.firm'
[saned] check_host: config file line: `#192.168.0.1'
[saned] check_host: config file line: `#192.168.0.1/29'
[saned] check_host: config file line: `#localhost'
[saned] check_host: config file line: `#127.0.0.1'
[saned] check_host: config file line: `192.168.0.0/24'
[saned] check_host: subnet with base IP = 192.168.0.0, CIDR netmask = 24
[saned] check_host: access granted from IP address 192.168.0.199 (in subnet 192.168.0.0/24)
[saned] init: access granted
[saned] init: access granted to saned-user@::ffff:192.168.0.199
[saned] process_request: waiting for request
[saned] process_request: got request 1
[saned] process_request: waiting for request



And this is what happened when clicking on the scan button:
> 
[saned] process_request: got request 2
[saned] process_request: access to resource `epkowa' granted
[saned] process_request: sane_open returned: Access to resource has been denied
[saned] process_request: waiting for request



:confused:

---

### Post by Z.K. on 2013-06-24
Okay, it works now after adding saned user to the saned group.

---

