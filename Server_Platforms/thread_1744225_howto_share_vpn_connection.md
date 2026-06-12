---
title: "howto share vpn connection?"
date: 2011-04-30
forum: Server Platforms
---

### Post by Face_Man on 2011-04-30
hello all,

I am trying to share vpn connection between my network without any luck. 
here is how my network is setup.


**Main DNS server with 2 NIC's:**

/etc/network/interfaces
```

auto lo eth0 eth1
iface lo inet loopback

#internet 
iface eth0 inet static
	address 10.0.0.2
	netmask 255.255.255.192
	gateway 10.0.0.1		
#local
iface eth1 inet static
	address 10.0.1.1
	netmask 255.255.255.240

```

/etc/resolv.conf
```

nameserver 127.0.0.1

```

/etc/bind/options.conf
```

options {
    directory "/var/cache/bind";
    forwarders {208.67.222.222; 208.67.220.220;};
    auth-nxdomain no;
    allow-query { any; };
    recursion no;	
    version "0";        
    listen-on-v6 { any; };
};

```

My iptables 
```

EXTIF="eth0"
EXTIP="`/sbin/ifconfig eth0 | grep 'inet addr' | awk '{print $2}' | sed -e 's/.*://'`" #whick is 10.0.0.2
INTIF="eth1" # Enter the designation for the Internal Interface's
INTNET="10.0.1.0/28" # Enter the NETWORK address the Internal Interface is on
INTIP="10.0.1.1" # Enter the IP address of the Internal Interface
UNIVERSE="0.0.0.0/0"

    /sbin/depmod -a
    /sbin/modprobe ip_tables
    /sbin/modprobe ip_conntrack
    /sbin/modprobe ip_conntrack_ftp
    /sbin/modprobe ip_conntrack_irc
    /sbin/modprobe iptable_nat
    /sbin/modprobe ip_nat_ftp
    /sbin/modprobe ip_nat_irc

    echo "1" > /proc/sys/net/ipv4/ip_forward
    echo "1" > /proc/sys/net/ipv4/ip_dynaddr

    iptables -P INPUT DROP
    iptables -F INPUT 
    iptables -P OUTPUT DROP
    iptables -F OUTPUT 
    iptables -P FORWARD DROP
    iptables -F FORWARD 
    iptables -F -t nat

    if [ "`iptables -L | grep drop-and-log-it`" ]; then
       iptables -F drop-and-log-it
    fi
    iptables -X
    iptables -Z
    iptables -N drop-and-log-it
    iptables -A drop-and-log-it -j LOG --log-level info 
    iptables -A drop-and-log-it -j REJECT

    iptables -A INPUT -i lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT
    iptables -A INPUT -i $INTIF -s $INTNET -d $UNIVERSE -j ACCEPT
    iptables -A INPUT -i $EXTIF -s $INTNET -d $UNIVERSE -j drop-and-log-it
    iptables -A INPUT -i $EXTIF -s $UNIVERSE -d $EXTIP -j ACCEPT
    iptables -A INPUT -i $EXTIF -s $UNIVERSE -d $EXTIP -m state --state ESTABLISHED,RELATED -j ACCEPT
    iptables -A INPUT -s $UNIVERSE -d $UNIVERSE -j drop-and-log-it

    iptables -A OUTPUT -o lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT
    iptables -A OUTPUT -o $INTIF -s $EXTIP -d $INTNET -j ACCEPT
    iptables -A OUTPUT -o $INTIF -s $INTIP -d $INTNET -j ACCEPT
    iptables -A OUTPUT -o $EXTIF -s $UNIVERSE -d $INTNET -j drop-and-log-it
    iptables -A OUTPUT -o $EXTIF -s $EXTIP -d $UNIVERSE -j ACCEPT
    iptables -A OUTPUT -s $UNIVERSE -d $UNIVERSE -j drop-and-log-it


    Cloud=10.0.1.4
    Port=8080
    iptables -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT
    iptables -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT

    iptables -A FORWARD -i $EXTIF -o $INTIF -d $Cloud -p tcp --dport $Port -j ACCEPT
    iptables -t nat -A PREROUTING -i $EXTIF -d $EXTIP -p tcp --dport $Port -j DNAT --to $Cloud

    iptables -A FORWARD -j drop-and-log-it
    iptables -t nat -A POSTROUTING -o $EXTIF -j SNAT --to $EXTIP

```


With those setting i am able to share my internet connection, however, when i try to connect to vpn server using openvpn it seem i am connect to the vpn server but i dont have any internet internet connectivity even on the dns server.

here my openvpn log
```

Sat Apr 30 04:59:50 2011 us=705962 Current Parameter Settings:
Sat Apr 30 04:59:50 2011 us=706310   config = '/etc/openvpn/Overplay.conf'
Sat Apr 30 04:59:50 2011 us=706370   mode = 0
Sat Apr 30 04:59:50 2011 us=706405   persist_config = DISABLED
Sat Apr 30 04:59:50 2011 us=706438   persist_mode = 1
Sat Apr 30 04:59:50 2011 us=706470   show_ciphers = DISABLED
Sat Apr 30 04:59:50 2011 us=706502   show_digests = DISABLED
Sat Apr 30 04:59:50 2011 us=706533   show_engines = DISABLED
Sat Apr 30 04:59:50 2011 us=706564   genkey = DISABLED
Sat Apr 30 04:59:50 2011 us=706596   key_pass_file = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=706628   show_tls_ciphers = DISABLED
Sat Apr 30 04:59:50 2011 us=706659 Connection profiles [default]:
Sat Apr 30 04:59:50 2011 us=707220   proto = tcp-client
Sat Apr 30 04:59:50 2011 us=707304   local = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=707339   local_port = 0
Sat Apr 30 04:59:50 2011 us=707372   remote = '208.43.135.137'
Sat Apr 30 04:59:50 2011 us=707405   remote_port = 442
Sat Apr 30 04:59:50 2011 us=707436   remote_float = DISABLED
Sat Apr 30 04:59:50 2011 us=707596   bind_defined = DISABLED
Sat Apr 30 04:59:50 2011 us=707632   bind_local = DISABLED
Sat Apr 30 04:59:50 2011 us=707665   connect_retry_seconds = 5
Sat Apr 30 04:59:50 2011 us=707697   connect_timeout = 10
Sat Apr 30 04:59:50 2011 us=707730   connect_retry_max = 0
Sat Apr 30 04:59:50 2011 us=707762   socks_proxy_server = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=707794   socks_proxy_port = 0
Sat Apr 30 04:59:50 2011 us=707825   socks_proxy_retry = DISABLED
Sat Apr 30 04:59:50 2011 us=707879 Connection profiles END
Sat Apr 30 04:59:50 2011 us=707912   remote_random = ENABLED
Sat Apr 30 04:59:50 2011 us=707943   ipchange = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=707974   dev = 'tun'
Sat Apr 30 04:59:50 2011 us=708005   dev_type = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=708036   dev_node = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=708068   lladdr = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=708099   topology = 1
Sat Apr 30 04:59:50 2011 us=708129   tun_ipv6 = DISABLED
Sat Apr 30 04:59:50 2011 us=708161   ifconfig_local = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=708193   ifconfig_remote_netmask = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=708224   ifconfig_noexec = DISABLED
Sat Apr 30 04:59:50 2011 us=708255   ifconfig_nowarn = DISABLED
Sat Apr 30 04:59:50 2011 us=708287   shaper = 0
Sat Apr 30 04:59:50 2011 us=708317   tun_mtu = 1500
Sat Apr 30 04:59:50 2011 us=708348   tun_mtu_defined = ENABLED
Sat Apr 30 04:59:50 2011 us=708380   link_mtu = 1500
Sat Apr 30 04:59:50 2011 us=708411   link_mtu_defined = DISABLED
Sat Apr 30 04:59:50 2011 us=708442   tun_mtu_extra = 0
Sat Apr 30 04:59:50 2011 us=708472   tun_mtu_extra_defined = DISABLED
Sat Apr 30 04:59:50 2011 us=708504   fragment = 0
Sat Apr 30 04:59:50 2011 us=708535   mtu_discover_type = -1
Sat Apr 30 04:59:50 2011 us=708566   mtu_test = 0
Sat Apr 30 04:59:50 2011 us=708596   mlock = DISABLED
Sat Apr 30 04:59:50 2011 us=708627   keepalive_ping = 0
Sat Apr 30 04:59:50 2011 us=708659   keepalive_timeout = 0
Sat Apr 30 04:59:50 2011 us=708690   inactivity_timeout = 0
Sat Apr 30 04:59:50 2011 us=708722   ping_send_timeout = 0
Sat Apr 30 04:59:50 2011 us=708754   ping_rec_timeout = 0
Sat Apr 30 04:59:50 2011 us=708787   ping_rec_timeout_action = 0
Sat Apr 30 04:59:50 2011 us=708819   ping_timer_remote = DISABLED
Sat Apr 30 04:59:50 2011 us=708850   remap_sigusr1 = 0
Sat Apr 30 04:59:50 2011 us=708881   explicit_exit_notification = 0
Sat Apr 30 04:59:50 2011 us=708912   persist_tun = ENABLED
Sat Apr 30 04:59:50 2011 us=708944   persist_local_ip = DISABLED
Sat Apr 30 04:59:50 2011 us=708976   persist_remote_ip = DISABLED
Sat Apr 30 04:59:50 2011 us=709008   persist_key = ENABLED
Sat Apr 30 04:59:50 2011 us=709040   mssfix = 1450
Sat Apr 30 04:59:50 2011 us=709071   passtos = DISABLED
Sat Apr 30 04:59:50 2011 us=709102   resolve_retry_seconds = 1000000000
Sat Apr 30 04:59:50 2011 us=709133   username = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=709165   groupname = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=709197   chroot_dir = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=709228   cd_dir = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=709259   writepid = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=709289   up_script = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=709320   down_script = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=709350   down_pre = DISABLED
Sat Apr 30 04:59:50 2011 us=709381   up_restart = DISABLED
Sat Apr 30 04:59:50 2011 us=709412   up_delay = DISABLED
Sat Apr 30 04:59:50 2011 us=709444   daemon = DISABLED
Sat Apr 30 04:59:50 2011 us=709475   inetd = 0
Sat Apr 30 04:59:50 2011 us=709506   log = DISABLED
Sat Apr 30 04:59:50 2011 us=709536   suppress_timestamps = DISABLED
Sat Apr 30 04:59:50 2011 us=709567   nice = 0
Sat Apr 30 04:59:50 2011 us=709598   verbosity = 5
Sat Apr 30 04:59:50 2011 us=709629   mute = 0
Sat Apr 30 04:59:50 2011 us=709659   gremlin = 0
Sat Apr 30 04:59:50 2011 us=709688   status_file = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=709720   status_file_version = 1
Sat Apr 30 04:59:50 2011 us=709753   status_file_update_freq = 60
Sat Apr 30 04:59:50 2011 us=709783   occ = ENABLED
Sat Apr 30 04:59:50 2011 us=709814   rcvbuf = 65536
Sat Apr 30 04:59:50 2011 us=709844   sndbuf = 65536
Sat Apr 30 04:59:50 2011 us=709874   sockflags = 0
Sat Apr 30 04:59:50 2011 us=709904   fast_io = DISABLED
Sat Apr 30 04:59:50 2011 us=709962   lzo = 7
Sat Apr 30 04:59:50 2011 us=710000   route_script = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=710032   route_default_gateway = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=710064   route_default_metric = 0
Sat Apr 30 04:59:50 2011 us=710095   route_noexec = DISABLED
Sat Apr 30 04:59:50 2011 us=710126   route_delay = 2
Sat Apr 30 04:59:50 2011 us=710157   route_delay_window = 30
Sat Apr 30 04:59:50 2011 us=710187   route_delay_defined = ENABLED
Sat Apr 30 04:59:50 2011 us=710219   route_nopull = DISABLED
Sat Apr 30 04:59:50 2011 us=710250   route_gateway_via_dhcp = DISABLED
Sat Apr 30 04:59:50 2011 us=710282   max_routes = 100
Sat Apr 30 04:59:50 2011 us=710313   allow_pull_fqdn = DISABLED
Sat Apr 30 04:59:50 2011 us=710346   management_addr = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=710379   management_port = 0
Sat Apr 30 04:59:50 2011 us=710413   management_user_pass = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=710446   management_log_history_cache = 250
Sat Apr 30 04:59:50 2011 us=710479   management_echo_buffer_size = 100
Sat Apr 30 04:59:50 2011 us=710512   management_write_peer_info_file = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=710546   management_client_user = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=710579   management_client_group = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=710611   management_flags = 0
Sat Apr 30 04:59:50 2011 us=710643   shared_secret_file = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=710676   key_direction = 0
Sat Apr 30 04:59:50 2011 us=712036   ciphername_defined = ENABLED
Sat Apr 30 04:59:50 2011 us=712152   ciphername = 'BF-CBC'
Sat Apr 30 04:59:50 2011 us=712240   authname_defined = ENABLED
Sat Apr 30 04:59:50 2011 us=712279   authname = 'SHA1'
Sat Apr 30 04:59:50 2011 us=712311   prng_hash = 'SHA1'
Sat Apr 30 04:59:50 2011 us=712343   prng_nonce_secret_len = 16
Sat Apr 30 04:59:50 2011 us=712375   keysize = 0
Sat Apr 30 04:59:50 2011 us=712406   engine = DISABLED
Sat Apr 30 04:59:50 2011 us=712438   replay = ENABLED
Sat Apr 30 04:59:50 2011 us=712470   mute_replay_warnings = DISABLED
Sat Apr 30 04:59:50 2011 us=712502   replay_window = 64
Sat Apr 30 04:59:50 2011 us=712534   replay_time = 15
Sat Apr 30 04:59:50 2011 us=712566   packet_id_file = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=712598   use_iv = ENABLED
Sat Apr 30 04:59:50 2011 us=712630   test_crypto = DISABLED
Sat Apr 30 04:59:50 2011 us=712662   tls_server = DISABLED
Sat Apr 30 04:59:50 2011 us=712693   tls_client = ENABLED
Sat Apr 30 04:59:50 2011 us=712724   key_method = 2
Sat Apr 30 04:59:50 2011 us=712757   ca_file = '/etc/openvpn/OverplayCert.crt'
Sat Apr 30 04:59:50 2011 us=712791   ca_path = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=712823   dh_file = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=712855   cert_file = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=712888   priv_key_file = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=712921   pkcs12_file = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=712954   cipher_list = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=712986   tls_verify = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=713018   tls_remote = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=713050   crl_file = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=713083   ns_cert_type = 0
Sat Apr 30 04:59:50 2011 us=713116   remote_cert_ku[i] = 0
Sat Apr 30 04:59:50 2011 us=713149   remote_cert_ku[i] = 0
Sat Apr 30 04:59:50 2011 us=713181   remote_cert_ku[i] = 0
Sat Apr 30 04:59:50 2011 us=713213   remote_cert_ku[i] = 0
Sat Apr 30 04:59:50 2011 us=713245   remote_cert_ku[i] = 0
Sat Apr 30 04:59:50 2011 us=713279   remote_cert_ku[i] = 0
Sat Apr 30 04:59:50 2011 us=713310   remote_cert_ku[i] = 0
Sat Apr 30 04:59:50 2011 us=713342   remote_cert_ku[i] = 0
Sat Apr 30 04:59:50 2011 us=713373   remote_cert_ku[i] = 0
Sat Apr 30 04:59:50 2011 us=713404   remote_cert_ku[i] = 0
Sat Apr 30 04:59:50 2011 us=713434   remote_cert_ku[i] = 0
Sat Apr 30 04:59:50 2011 us=713465   remote_cert_ku[i] = 0
Sat Apr 30 04:59:50 2011 us=713496   remote_cert_ku[i] = 0
Sat Apr 30 04:59:50 2011 us=713528   remote_cert_ku[i] = 0
Sat Apr 30 04:59:50 2011 us=713559   remote_cert_ku[i] = 0
Sat Apr 30 04:59:50 2011 us=713591   remote_cert_ku[i] = 0
Sat Apr 30 04:59:50 2011 us=713622   remote_cert_eku = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=713655   tls_timeout = 2
Sat Apr 30 04:59:50 2011 us=713687   renegotiate_bytes = 0
Sat Apr 30 04:59:50 2011 us=713718   renegotiate_packets = 0
Sat Apr 30 04:59:50 2011 us=713750   renegotiate_seconds = 3600
Sat Apr 30 04:59:50 2011 us=713783   handshake_window = 60
Sat Apr 30 04:59:50 2011 us=713815   transition_window = 3600
Sat Apr 30 04:59:50 2011 us=713846   single_session = DISABLED
Sat Apr 30 04:59:50 2011 us=713876   tls_exit = DISABLED
Sat Apr 30 04:59:50 2011 us=713907   tls_auth_file = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=713940   pkcs11_protected_authentication = DISABLED
Sat Apr 30 04:59:50 2011 us=713973   pkcs11_protected_authentication = DISABLED
Sat Apr 30 04:59:50 2011 us=714005   pkcs11_protected_authentication = DISABLED
Sat Apr 30 04:59:50 2011 us=714037   pkcs11_protected_authentication = DISABLED
Sat Apr 30 04:59:50 2011 us=714068   pkcs11_protected_authentication = DISABLED
Sat Apr 30 04:59:50 2011 us=714100   pkcs11_protected_authentication = DISABLED
Sat Apr 30 04:59:50 2011 us=714132   pkcs11_protected_authentication = DISABLED
Sat Apr 30 04:59:50 2011 us=714164   pkcs11_protected_authentication = DISABLED
Sat Apr 30 04:59:50 2011 us=714196   pkcs11_protected_authentication = DISABLED
Sat Apr 30 04:59:50 2011 us=714228   pkcs11_protected_authentication = DISABLED
Sat Apr 30 04:59:50 2011 us=714260   pkcs11_protected_authentication = DISABLED
Sat Apr 30 04:59:50 2011 us=714292   pkcs11_protected_authentication = DISABLED
Sat Apr 30 04:59:50 2011 us=714323   pkcs11_protected_authentication = DISABLED
Sat Apr 30 04:59:50 2011 us=714355   pkcs11_protected_authentication = DISABLED
Sat Apr 30 04:59:50 2011 us=714386   pkcs11_protected_authentication = DISABLED
Sat Apr 30 04:59:50 2011 us=714418   pkcs11_protected_authentication = DISABLED
Sat Apr 30 04:59:50 2011 us=714452   pkcs11_private_mode = 00000000
Sat Apr 30 04:59:50 2011 us=714484   pkcs11_private_mode = 00000000
Sat Apr 30 04:59:50 2011 us=714517   pkcs11_private_mode = 00000000
Sat Apr 30 04:59:50 2011 us=714550   pkcs11_private_mode = 00000000
Sat Apr 30 04:59:50 2011 us=714582   pkcs11_private_mode = 00000000
Sat Apr 30 04:59:50 2011 us=714613   pkcs11_private_mode = 00000000
Sat Apr 30 04:59:50 2011 us=714644   pkcs11_private_mode = 00000000
Sat Apr 30 04:59:50 2011 us=714675   pkcs11_private_mode = 00000000
Sat Apr 30 04:59:50 2011 us=715703   pkcs11_private_mode = 00000000
Sat Apr 30 04:59:50 2011 us=715746   pkcs11_private_mode = 00000000
Sat Apr 30 04:59:50 2011 us=715922   pkcs11_private_mode = 00000000
Sat Apr 30 04:59:50 2011 us=716059   pkcs11_private_mode = 00000000
Sat Apr 30 04:59:50 2011 us=716104   pkcs11_private_mode = 00000000
Sat Apr 30 04:59:50 2011 us=716137   pkcs11_private_mode = 00000000
Sat Apr 30 04:59:50 2011 us=716169   pkcs11_private_mode = 00000000
Sat Apr 30 04:59:50 2011 us=716200   pkcs11_private_mode = 00000000
Sat Apr 30 04:59:50 2011 us=716232   pkcs11_cert_private = DISABLED
Sat Apr 30 04:59:50 2011 us=716265   pkcs11_cert_private = DISABLED
Sat Apr 30 04:59:50 2011 us=716298   pkcs11_cert_private = DISABLED
Sat Apr 30 04:59:50 2011 us=716330   pkcs11_cert_private = DISABLED
Sat Apr 30 04:59:50 2011 us=716362   pkcs11_cert_private = DISABLED
Sat Apr 30 04:59:50 2011 us=716394   pkcs11_cert_private = DISABLED
Sat Apr 30 04:59:50 2011 us=716425   pkcs11_cert_private = DISABLED
Sat Apr 30 04:59:50 2011 us=716456   pkcs11_cert_private = DISABLED
Sat Apr 30 04:59:50 2011 us=716488   pkcs11_cert_private = DISABLED
Sat Apr 30 04:59:50 2011 us=716521   pkcs11_cert_private = DISABLED
Sat Apr 30 04:59:50 2011 us=716553   pkcs11_cert_private = DISABLED
Sat Apr 30 04:59:50 2011 us=716584   pkcs11_cert_private = DISABLED
Sat Apr 30 04:59:50 2011 us=716616   pkcs11_cert_private = DISABLED
Sat Apr 30 04:59:50 2011 us=716647   pkcs11_cert_private = DISABLED
Sat Apr 30 04:59:50 2011 us=716677   pkcs11_cert_private = DISABLED
Sat Apr 30 04:59:50 2011 us=716708   pkcs11_cert_private = DISABLED
Sat Apr 30 04:59:50 2011 us=716741   pkcs11_pin_cache_period = -1
Sat Apr 30 04:59:50 2011 us=716773   pkcs11_id = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=716805   pkcs11_id_management = DISABLED
Sat Apr 30 04:59:50 2011 us=716916   server_network = 0.0.0.0
Sat Apr 30 04:59:50 2011 us=716956   server_netmask = 0.0.0.0
Sat Apr 30 04:59:50 2011 us=716992   server_bridge_ip = 0.0.0.0
Sat Apr 30 04:59:50 2011 us=717027   server_bridge_netmask = 0.0.0.0
Sat Apr 30 04:59:50 2011 us=717062   server_bridge_pool_start = 0.0.0.0
Sat Apr 30 04:59:50 2011 us=717097   server_bridge_pool_end = 0.0.0.0
Sat Apr 30 04:59:50 2011 us=717130   ifconfig_pool_defined = DISABLED
Sat Apr 30 04:59:50 2011 us=717165   ifconfig_pool_start = 0.0.0.0
Sat Apr 30 04:59:50 2011 us=717200   ifconfig_pool_end = 0.0.0.0
Sat Apr 30 04:59:50 2011 us=717234   ifconfig_pool_netmask = 0.0.0.0
Sat Apr 30 04:59:50 2011 us=717268   ifconfig_pool_persist_filename = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=717303   ifconfig_pool_persist_refresh_freq = 600
Sat Apr 30 04:59:50 2011 us=717335   n_bcast_buf = 256
Sat Apr 30 04:59:50 2011 us=717368   tcp_queue_limit = 64
Sat Apr 30 04:59:50 2011 us=717400   real_hash_size = 256
Sat Apr 30 04:59:50 2011 us=717431   virtual_hash_size = 256
Sat Apr 30 04:59:50 2011 us=717463   client_connect_script = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=717496   learn_address_script = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=717529   client_disconnect_script = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=717562   client_config_dir = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=717593   ccd_exclusive = DISABLED
Sat Apr 30 04:59:50 2011 us=717624   tmp_dir = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=717656   push_ifconfig_defined = DISABLED
Sat Apr 30 04:59:50 2011 us=717691   push_ifconfig_local = 0.0.0.0
Sat Apr 30 04:59:50 2011 us=717725   push_ifconfig_remote_netmask = 0.0.0.0
Sat Apr 30 04:59:50 2011 us=717758   enable_c2c = DISABLED
Sat Apr 30 04:59:50 2011 us=717789   duplicate_cn = DISABLED
Sat Apr 30 04:59:50 2011 us=717819   cf_max = 0
Sat Apr 30 04:59:50 2011 us=717851   cf_per = 0
Sat Apr 30 04:59:50 2011 us=717883   max_clients = 1024
Sat Apr 30 04:59:50 2011 us=717915   max_routes_per_client = 256
Sat Apr 30 04:59:50 2011 us=717949   auth_user_pass_verify_script = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=717981   auth_user_pass_verify_script_via_file = DISABLED
Sat Apr 30 04:59:50 2011 us=718015   ssl_flags = 0
Sat Apr 30 04:59:50 2011 us=718047   port_share_host = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=718080   port_share_port = 0
Sat Apr 30 04:59:50 2011 us=718111   client = ENABLED
Sat Apr 30 04:59:50 2011 us=718142   pull = ENABLED
Sat Apr 30 04:59:50 2011 us=718176   auth_user_pass_file = 'stdin'
Sat Apr 30 04:59:50 2011 us=718222 OpenVPN 2.1.0 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [MH] [PF_INET6] [eurephia] built on Jul 20 2010
Enter Auth Username:MyUserName
Enter Auth Password:
Sat Apr 30 04:59:58 2011 us=267193 WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Sat Apr 30 04:59:58 2011 us=267321 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Sat Apr 30 04:59:58 2011 us=269517 LZO compression initialized
Sat Apr 30 04:59:58 2011 us=269928 Control Channel MTU parms [ L:1544 D:140 EF:40 EB:0 ET:0 EL:0 ]
Sat Apr 30 04:59:58 2011 us=270284 Data Channel MTU parms [ L:1544 D:1450 EF:44 EB:135 ET:0 EL:0 AF:3/1 ]
Sat Apr 30 04:59:58 2011 us=270448 Local Options String: 'V4,dev-type tun,link-mtu 1544,tun-mtu 1500,proto TCPv4_CLIENT,comp-lzo,cipher BF-CBC,auth SHA1,keysize 128,key-method 2,tls-client'
Sat Apr 30 04:59:58 2011 us=270492 Expected Remote Options String: 'V4,dev-type tun,link-mtu 1544,tun-mtu 1500,proto TCPv4_SERVER,comp-lzo,cipher BF-CBC,auth SHA1,keysize 128,key-method 2,tls-server'
Sat Apr 30 04:59:58 2011 us=270588 Local Options hash (VER=V4): '69109d17'
Sat Apr 30 04:59:58 2011 us=270640 Expected Remote Options hash (VER=V4): 'c0103fa8'
Sat Apr 30 04:59:58 2011 us=271310 Attempting to establish TCP connection with [AF_INET]208.43.135.137:442 [nonblock]
Sat Apr 30 04:59:59 2011 us=271963 TCP connection established with [AF_INET]208.43.135.137:442
Sat Apr 30 04:59:59 2011 us=272128 Socket Buffers: R=[87380->131072] S=[16384->131072]
Sat Apr 30 04:59:59 2011 us=272182 TCPv4_CLIENT link local: [undef]
Sat Apr 30 04:59:59 2011 us=272221 TCPv4_CLIENT link remote: [AF_INET]208.43.135.137:442
WRSat Apr 30 04:59:59 2011 us=784959 TLS: Initial packet from [AF_INET]208.43.135.137:442, sid=a0878115 17f6db74
WSat Apr 30 04:59:59 2011 us=785581 WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
WRWRRRWWRWRWRRWWRWRWRRWWRWRRWWRRWWRWRWRRWWRSat Apr 30 05:00:08 2011 us=118169 VERIFY OK: depth=1, /C=UK/ST=LANCS/L=MANCHESTER/O=OVERPLAY.NET_LLP/OU=CA/CN=OVERPLAY_CA/emailAddress=ca@overplay.net
Sat Apr 30 05:00:08 2011 us=119861 VERIFY OK: depth=0, /C=US/ST=IL/L=Chicago/O=OVERPLAY.NET_LLP/OU=SERVERS/CN=vpn1-us/emailAddress=ca@overplay.net
WRWRRWWRWWRRWWWWRRRRRRSat Apr 30 05:00:13 2011 us=263146 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Sat Apr 30 05:00:13 2011 us=263415 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Sat Apr 30 05:00:13 2011 us=263570 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Sat Apr 30 05:00:13 2011 us=263613 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
WWSat Apr 30 05:00:13 2011 us=264012 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Sat Apr 30 05:00:13 2011 us=264132 [vpn1-us] Peer Connection Initiated with [AF_INET]208.43.135.137:442
Sat Apr 30 05:00:15 2011 us=691030 SENT CONTROL [vpn1-us]: 'PUSH_REQUEST' (status=1)
WRRRRSat Apr 30 05:00:16 2011 us=759237 PUSH: Received control message: 'PUSH_REPLY,redirect-gateway def1,dhcp-option DNS 8.8.8.8,route 10.11.0.1,topology net30,ping 10,ping-restart 120,ifconfig 10.11.19.18 10.11.19.17'
Sat Apr 30 05:00:16 2011 us=759539 OPTIONS IMPORT: timers and/or timeouts modified
Sat Apr 30 05:00:16 2011 us=759595 OPTIONS IMPORT: --ifconfig/up options modified
Sat Apr 30 05:00:16 2011 us=759626 OPTIONS IMPORT: route options modified
Sat Apr 30 05:00:16 2011 us=759656 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Sat Apr 30 05:00:16 2011 us=760372 ROUTE default_gateway=10.0.0.1
Sat Apr 30 05:00:16 2011 us=771897 TUN/TAP device tun0 opened
Sat Apr 30 05:00:16 2011 us=772131 TUN/TAP TX queue length set to 100
Sat Apr 30 05:00:16 2011 us=772320 /sbin/ifconfig tun0 10.11.19.18 pointopoint 10.11.19.17 mtu 1500
WWSat Apr 30 05:00:19 2011 us=2895 /sbin/route add -net 208.43.135.137 netmask 255.255.255.255 gw 10.0.0.1
Sat Apr 30 05:00:19 2011 us=6971 /sbin/route add -net 0.0.0.0 netmask 128.0.0.0 gw 10.11.19.17
Sat Apr 30 05:00:19 2011 us=11768 /sbin/route add -net 128.0.0.0 netmask 128.0.0.0 gw 10.11.19.17
Sat Apr 30 05:00:19 2011 us=17427 /sbin/route add -net 10.11.0.1 netmask 255.255.255.255 gw 10.11.19.17
Sat Apr 30 05:00:19 2011 us=22593 Initialization Sequence Completed

``` 


I really have no idea what should i be doing or if there is something wrong i should change, therefore if anyone could help me or point me to the right direction that would be grate.


Any help would be much appreciated.
thx

---

### Post by elico on 2011-04-30
what machine is the client of OPENVPN?
this or other?
and on the one that you have the problem give an output of
> route -n
before the VPN established and after.

---

### Post by Face_Man on 2011-04-30
> **elico said:**
> what machine is the client of OPENVPN?
this or other?



the client of OPENVPN is the dns server 

> **elico said:**
> 
and on the one that you have the problem give an output of

before the VPN established and after.

**On dns server **
Before
```

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.1.0        0.0.0.0         255.255.255.240 U     0      0        0 eth1
10.0.0.0        0.0.0.0         255.255.255.192 U     0      0        0 eth0
0.0.0.0         10.0.0.1        0.0.0.0         UG    100    0        0 eth0

```

after
```

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.11.0.1       10.11.19.17     255.255.255.255 UGH   0      0        0 tun0
208.43.135.137  10.0.0.1        255.255.255.255 UGH   0      0        0 eth0
10.11.19.17     0.0.0.0         255.255.255.255 UH    0      0        0 tun0
10.0.1.0        0.0.0.0         255.255.255.240 U     0      0        0 eth1
10.0.0.0        0.0.0.0         255.255.255.192 U     0      0        0 eth0
0.0.0.0         10.11.19.17     128.0.0.0       UG    0      0        0 tun0
128.0.0.0       10.11.19.17     128.0.0.0       UG    0      0        0 tun0
0.0.0.0         10.0.0.1        0.0.0.0         UG    100    0        0 eth0

```

**on other client on my network **
Before
```

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.1.0        0.0.0.0         255.255.255.240 U     0      0        0 eth0
0.0.0.0         10.0.1.1        0.0.0.0         UG    0      0        0 eth0

```

after
```

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.1.0        0.0.0.0         255.255.255.240 U     0      0        0 eth0
0.0.0.0         10.0.1.1        0.0.0.0         UG    0      0        0 eth0

```

---

### Post by elico on 2011-04-30
the problem solved!! (just remember to mark the problem as solved after.)
(at the bottom are the fault stuff from the VPN)

the basic route to "all" is using the eth0
> 0.0.0.0         10.0.0.1        0.0.0.0         UG    100    0        0 eth0after you connect the openvpn tunnel, the connection is changing the default aka "all" routes to be used using the vpn and not the eth0.
as in :
after> 
route -n 
Kernel IP routing table Destination Gateway Genmask Flags Metric Ref Use Iface 
10.11.0.1 10.11.19.17 255.255.255.255 UGH 0 0 0 tun0 
208.43.135.137 10.0.0.1 255.255.255.255 UGH 0 0 0 eth0 
10.11.19.17 0.0.0.0 255.255.255.255 UH 0 0 0 tun0 
10.0.1.0 0.0.0.0 255.255.255.240 U 0 0 0 eth1 
10.0.0.0 0.0.0.0 255.255.255.192 U 0 0 0 eth0 
0.0.0.0 10.11.19.17 128.0.0.0 UG 0 0 0 tun0 
128.0.0.0 10.11.19.17 128.0.0.0 UG 0 0 0 tun0 
0.0.0.0 10.0.0.1 0.0.0.0 UG 100 0 0 eth0as you can see the basic default gateway metric is 100 and goes to interface eth0
means that if i will set another default (0.0.0.0) using metric less then 100 let say 99 the system will try to use the 99 metric route\router.


in your case when the vpn connection established it sets the default (0.0.0.0) with metric 0 that is less then 100 to use tun0 means it will not try to get to the internet using the eth0 10.0.0.1 router but
10.11.19.17 on tun0

so change the openvpn settings to not set default on connection.
and change the default to metric 0 and not 100.

and if you dont know then use the following
you have two 0.0.0.0 so del both of them:
```

route del 0.0.0.0
route del 0.0.0.0

```then add to use the eth0 using:
```
route add default gw 10.0.0.1 metric 1 eth0
```after that run the 
```
route -n
```to get the result that should be something like:(the order will might not be the same)

> route -n 
Kernel IP routing table Destination Gateway Genmask Flags Metric Ref Use Iface 
10.11.0.1 10.11.19.17 255.255.255.255 UGH 0 0 0 tun0 
208.43.135.137 10.0.0.1 255.255.255.255 UGH 0 0 0 eth0 
10.11.19.17 0.0.0.0 255.255.255.255 UH 0 0 0 tun0 
10.0.1.0 0.0.0.0 255.255.255.240 U 0 0 0 eth1 
10.0.0.0 0.0.0.0 255.255.255.192 U 0 0 0 eth0 
128.0.0.0 10.11.19.17 128.0.0.0 UG 0 0 0 tun0 
0.0.0.0 10.0.0.1 0.0.0.0 UG 1 0 0 eth0 and now you can make sure that you can ping the internet.

the next step is to build the routes for the network that you want to get the connection using the VPN.
so add a route like this:
```
route add -net 192.168.0.0/24 metric 0 tun0
```with the subnet of the network or networks that you want to access using the tun0 vpn connection.
if you want specific host only you can use
```
route add 192.168.0.1 metric 0 tun0
```after this you should have something like this:> 
route -n 
Kernel IP routing table Destination Gateway Genmask Flags Metric Ref Use Iface 
10.11.0.1 10.11.19.17 255.255.255.255 UGH 0 0 0 tun0 
208.43.135.137 10.0.0.1 255.255.255.255 UGH 0 0 0 eth0
10.11.19.17 0.0.0.0 255.255.255.255 UH 0 0 0 tun0 
10.0.1.0 0.0.0.0 255.255.255.240 U 0 0 0 eth1
10.0.0.0 0.0.0.0 255.255.255.192 U 0 0 0 eth0
128.0.0.0 10.11.19.17 128.0.0.0 UG 0 0 0 tun0
0.0.0.0 10.0.0.1 0.0.0.0 UG 1 0 0 eth0
192.168.0.0 10.11.19.17 255.255.255.0 UG 0 0 0 tun0 
192.168.0.1 10.11.19.17 255.255.255.0 UG 0 0 0 tun0


wrong stuff on vpn config from log output(with notes)

#some route settings found 
Sat Apr 30 04:59:50 2011 us=710000   route_script = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=710032   route_default_gateway = '[UNDEF]'
#change it to metric 110 as route_default_metric = 110 in the config file and it might solve everything 
Sat Apr 30 04:59:50 2011 us=710064   route_default_metric = 0

#setting up ip for tun0
Sat Apr 30 05:00:16 2011 us=772320 /sbin/ifconfig tun0 10.11.19.18 pointopoint 10.11.19.17 mtu 1500
#adding route for the tun to use the eth0 gateway
WWSat Apr 30 05:00:19 2011 us=2895 /sbin/route add -net 208.43.135.137 netmask 255.255.255.255 gw 10.0.0.1
# adding GW for alllllmost the networking using the the tun0
Sat Apr 30 05:00:19 2011 us=6971 /sbin/route add -net 0.0.0.0 netmask 128.0.0.0 gw 10.11.19.17
#adding route for specific network using the tun0
Sat Apr 30 05:00:19 2011 us=11768 /sbin/route add -net 128.0.0.0 netmask 128.0.0.0 gw 10.11.19.17
#adding route to specific host using the tun0
Sat Apr 30 05:00:19 2011 us=17427 /sbin/route add -net 10.11.0.1 netmask 255.255.255.255 gw 10.11.19.17

---

### Post by Face_Man on 2011-05-01
> **elico said:**
> the problem solved!! (just remember to mark the problem as solved after.)
(at the bottom are the fault stuff from the VPN)

the basic route to "all" is using the eth0
after you connect the openvpn tunnel, the connection is changing the default aka "all" routes to be used using the vpn and not the eth0.
as in :
afteras you can see the basic default gateway metric is 100 and goes to interface eth0
means that if i will set another default (0.0.0.0) using metric less then 100 let say 99 the system will try to use the 99 metric route\router.


in your case when the vpn connection established it sets the default (0.0.0.0) with metric 0 that is less then 100 to use tun0 means it will not try to get to the internet using the eth0 10.0.0.1 router but
10.11.19.17 on tun0

so change the openvpn settings to not set default on connection.
and change the default to metric 0 and not 100.

and if you dont know then use the following
you have two 0.0.0.0 so del both of them:
```

route del 0.0.0.0
route del 0.0.0.0

```then add to use the eth0 using:
```
route add default gw 10.0.0.1 metric 1 eth0
```after that run the 
```
route -n
```to get the result that should be something like:(the order will might not be the same)

and now you can make sure that you can ping the internet.

the next step is to build the routes for the network that you want to get the connection using the VPN.
so add a route like this:
```
route add -net 192.168.0.0/24 metric 0 tun0
```with the subnet of the network or networks that you want to access using the tun0 vpn connection.
if you want specific host only you can use
```
route add 192.168.0.1 metric 0 tun0
```after this you should have something like this:


wrong stuff on vpn config from log output(with notes)

#some route settings found 
Sat Apr 30 04:59:50 2011 us=710000   route_script = '[UNDEF]'
Sat Apr 30 04:59:50 2011 us=710032   route_default_gateway = '[UNDEF]'
#change it to metric 110 as route_default_metric = 110 in the config file and it might solve everything 
Sat Apr 30 04:59:50 2011 us=710064   route_default_metric = 0

#setting up ip for tun0
Sat Apr 30 05:00:16 2011 us=772320 /sbin/ifconfig tun0 10.11.19.18 pointopoint 10.11.19.17 mtu 1500
#adding route for the tun to use the eth0 gateway
WWSat Apr 30 05:00:19 2011 us=2895 /sbin/route add -net 208.43.135.137 netmask 255.255.255.255 gw 10.0.0.1
# adding GW for alllllmost the networking using the the tun0
Sat Apr 30 05:00:19 2011 us=6971 /sbin/route add -net 0.0.0.0 netmask 128.0.0.0 gw 10.11.19.17
#adding route for specific network using the tun0
Sat Apr 30 05:00:19 2011 us=11768 /sbin/route add -net 128.0.0.0 netmask 128.0.0.0 gw 10.11.19.17
#adding route to specific host using the tun0
Sat Apr 30 05:00:19 2011 us=17427 /sbin/route add -net 10.11.0.1 netmask 255.255.255.255 gw 10.11.19.17

elico,

thx for taking the time to look into my problem. However, I seem i am not able to follow your steps and here what iam getting:

```

$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.11.0.1       10.11.19.17     255.255.255.255 UGH   0      0        0 tun0
208.43.135.137  10.0.0.1        255.255.255.255 UGH   0      0        0 eth0
10.11.19.17     0.0.0.0         255.255.255.255 UH    0      0        0 tun0
10.0.1.0        0.0.0.0         255.255.255.240 U     0      0        0 eth1
10.0.0.0        0.0.0.0         255.255.255.192 U     0      0        0 eth0
0.0.0.0         10.11.19.17     128.0.0.0       UG    0      0        0 tun0
128.0.0.0       10.11.19.17     128.0.0.0       UG    0      0        0 tun0
0.0.0.0         10.0.0.1        0.0.0.0         UG    100    0        0 eth0

$ sudo route  del 0.0.0.0
SIOCDELRT: No such process

$ sudo route  del 0.0.0.0
SIOCDELRT: No such process

```

---

### Post by elico on 2011-05-01
you should add the interface as in:
> route del 0.0.0.0  eth0
or in your case try first only:
> route del 0.0.0.0  tun0

should solve the internet connectivity  issue.

---

### Post by Face_Man on 2011-05-01
> **elico said:**
> you should add the interface as in:

or in your case try first only:


should solve the internet connectivity  issue.

still i cannot get any  internet connectivity here what i did 

**before VPN established**
```

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.1.0        0.0.0.0         255.255.255.240 U     0      0        0 eth1
10.0.0.0        0.0.0.0         255.255.255.192 U     0      0        0 eth0
0.0.0.0         10.0.0.1        0.0.0.0         UG    1      0        0 eth0

```

**after VPN established**
```

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.11.0.1       10.11.19.17     255.255.255.255 UGH   0      0        0 tun0
208.43.135.137  10.0.0.1        255.255.255.255 UGH   0      0        0 eth0
10.11.19.17     0.0.0.0         255.255.255.255 UH    0      0        0 tun0
10.0.1.0        0.0.0.0         255.255.255.240 U     0      0        0 eth1
10.0.0.0        0.0.0.0         255.255.255.192 U     0      0        0 eth0
0.0.0.0         10.11.19.17     128.0.0.0       UG    0      0        0 tun0
128.0.0.0       10.11.19.17     128.0.0.0       UG    0      0        0 tun0
0.0.0.0         10.0.0.1        0.0.0.0         UG    1      0        0 eth0

```

**then**
```

sudo route del -net 0.0.0.0 netmask 128.0.0.0 dev tun0
sudo route del -net 0.0.0.0 netmask 0.0.0.0 dev eth0
sudo route add default gw 10.0.0.1 metric 1 eth0
sudo route add -net 10.0.0.0/24 metric 0 tun0

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.11.0.1       10.11.19.17     255.255.255.255 UGH   0      0        0 tun0
208.43.135.137  10.0.0.1        255.255.255.255 UGH   0      0        0 eth0
10.11.19.17     0.0.0.0         255.255.255.255 UH    0      0        0 tun0
10.0.1.0        0.0.0.0         255.255.255.240 U     0      0        0 eth1
10.0.0.0        0.0.0.0         255.255.255.192 U     0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 tun0
128.0.0.0       10.11.19.17     128.0.0.0       UG    0      0        0 tun0
0.0.0.0         10.0.0.1        0.0.0.0         UG    1      0        0 eth0

```

```

sudo ping yahoo.com
ping: unknown host yahoo.com

```


**am i missing something ?**

---

### Post by elico on 2011-05-01
try 
> 
ping 87.248.112.181
ping 8.8.8.8
ping 208.67.222.222



and remove also the line
128.0.0.0       10.11.19.17     128.0.0.0       UG    0      0        0 tun0

using:
> route del 128.0.0.0 tun0
then try to ping again to the ips
then
> ping [www.yahoo.com](www.yahoo.com)
and check your /etc/resolv.conf file using:
> cat /etc/resolv.conf

if you do have ping to 8.8.8.8 and the others you can try
> 
nslookup - 8.8.8.8 [www.yahoo.com](www.yahoo.com)
dig @8.8.8.8 [www.yahoo.com](www.yahoo.com)

if you get results using dig or nslookup 
make usre you have the content of /etc/resolv.conf like this:
> nameserver 127.0.0.1
nameserver 208.67.222.222
nameserver 8.8.8.8

and then try 
> nslookup [www.yahoo.com](www.yahoo.com)
dig [www.yahoo.com](www.yahoo.com)

if it works:
add 
> route add -net 128.0.0.0 netmask 128.0.0.0 gw 10.11.19.17 metric 20 tun0
and make sure that you still have anything in place and works.
if internet is working after the command make sure you can get to the remote network and see later.

---

### Post by Face_Man on 2011-05-01
> **elico said:**
> try 



and remove also the line
128.0.0.0       10.11.19.17     128.0.0.0       UG    0      0        0 tun0

using:

then try to ping again to the ips
then

and check your /etc/resolv.conf file using:


if you do have ping to 8.8.8.8 and the others you can try

if you get results using dig or nslookup 
make usre you have the content of /etc/resolv.conf like this:


and then try 


if it works:
add 

and make sure that you still have anything in place and works.
if internet is working after the command make sure you can get to the remote network and see later.


well i do have  internet connectivity however its not the vpn ip address 

```

sudo route del -net 0.0.0.0 netmask 128.0.0.0 dev tun0
sudo route del -net 0.0.0.0 netmask 0.0.0.0 dev eth0
sudo route del -net 128.0.0.0 netmask 128.0.0.0 dev tun0
sudo route add default gw 10.0.0.1 metric 1 eth0
sudo route add -net 10.0.0.0/24 metric 0 tun0

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.11.0.1       10.11.19.17     255.255.255.255 UGH   0      0        0 tun0
208.43.135.137  10.0.0.1        255.255.255.255 UGH   0      0        0 eth0
10.11.19.17     0.0.0.0         255.255.255.255 UH    0      0        0 tun0
10.0.1.0        0.0.0.0         255.255.255.240 U     0      0        0 eth1
10.0.0.0        0.0.0.0         255.255.255.192 U     0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 tun0
0.0.0.0         10.0.0.1        0.0.0.0         UG    1      0        0 eth0

```

when i add try this 
```

sudo route add -net 128.0.0.0 netmask 128.0.0.0 gw 10.11.19.17 metric 20 tun0
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.11.0.1       10.11.19.17     255.255.255.255 UGH   0      0        0 tun0
208.43.135.137  10.0.0.1        255.255.255.255 UGH   0      0        0 eth0
10.11.19.17     0.0.0.0         255.255.255.255 UH    0      0        0 tun0
10.0.1.0        0.0.0.0         255.255.255.240 U     0      0        0 eth1
10.0.0.0        0.0.0.0         255.255.255.192 U     0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 tun0
128.0.0.0       10.11.19.17     128.0.0.0       UG    20     0        0 tun0
0.0.0.0         10.0.0.1        0.0.0.0         UG    1      0        0 eth0

```

**i start to lose the internet connectivity, and when i check it seem i am using my ISP ip address not the vpn (208.43.135.137) ip address ?**

---

### Post by elico on 2011-05-01
one big mistake:
> sudo route add -net 10.0.0.0/24 metric 0 tun0ok so you have internet and it's good!
i tried to get it work while not shutting down the VPN.

do you want to use the internet connection via the VPN?
del the 128 route and the 10.0.0.0/24
> route del 128.0.0.0 tun0
route del -net 10.0.0.0/24 metric 0 tun0
try to ping the VPN GW
> ping 10.11.19.17then 
> route add -net 10.11.0.1 netmask 255.255.255.255 gw 10.11.19.17 metric 0 tun0
ping 10.11.0.1
if you can ping the 10.11.0.1
make sure what is the remote GW and if it's 
10.11.19.17
or 
10.11.0.1

add the route to the internet using and ping 8.8.8.8
> 
route add default metric 0 tun0
ping 8.8.8.8
and then 
> traceroute 8.8.8.8to make sure that you are getting to the internet using the VPN and not using the eth0.

now i want to understan..
by your iptables script  it seems like you need nat.
so you must do NAT for the VPN also.

what do you want? that all the internet traffic will go using your ISP or VPN?
it seems like you want specific host\s to be accessed using the vpn.
am i right?
if so you will need to change you iptables rules.
and...
you better learn about 
iptables-restore cause scripts are most of the time too dumb.

if you can give me some more solid info on the network infrastructure it will be very helpful.(PM to me)

---

