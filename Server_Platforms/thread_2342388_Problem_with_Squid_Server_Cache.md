---
title: "Problem with Squid Server Cache"
date: 2016-11-06
forum: Server Platforms
---

### Post by amsar on 2016-11-06
after i do everything and i try and try with squid+mikrotik to work together and  fail so i hope any one can tell me where the problem because i try and try but i can't find the problem
[IMG]http://s.pictub.club/2016/11/06/9EUxk.jpg[/IMG]

```
acl localnet src 10.0.0.0/8 # RFC1918 possible internal network
acl localnet src 172.16.0.0/12 # RFC1918 possible internal network
acl localnet src 192.168.0.0/16 # RFC1918 possible internal network
acl localnet src fc00::/7 # RFC 4193 local private network range
acl localnet src fe80::/10 # RFC 4291 link-local (directly plugged) machines
 
acl SSL_ports port 443
acl Safe_ports port 80 # http
acl Safe_ports port 21 # ftp
acl Safe_ports port 443 # https
acl Safe_ports port 70 # gopher
acl Safe_ports port 210 # wais
acl Safe_ports port 1025-65535 # unregistered ports
acl Safe_ports port 280 # http-mgmt
acl Safe_ports port 488 # gss-http
acl Safe_ports port 591 # filemaker
acl Safe_ports port 777 # multiling http
acl CONNECT method CONNECT
 
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localhost manager
http_access deny manager
http_access allow localnet
http_access allow localhost
http_access deny all
https_port 3127 tproxy ssl-bump generate-host-certificates=on dynamic_cert_mem_cache_size=4MB cert=/etc/squid/ssl_cert/myCA.pem
http_port 3128
http_port 3129 tproxy
acl step1 at_step SslBump1
acl step2 at_step SslBump2
acl step3 at_step SslBump3
ssl_bump peek step1 all
ssl_bump bump all
 
# BAGIAN YANG PERLU DI SESUAIKAN
# DISINI SAYA MENGGUNAKAN PARTISI /cache untuk cache_dir, jika nama partisi anda berbeda silahkan sesuaikan
# UNTUK UKURAN cache_dir sesuaikan juga, disini yang mencontohkan 100gb,
cache_dir aufs /cache 100000 100 256

acl youtube url_regex -i ^https?:\/\/.*\.googlevideo\.com\/videoplayback\?
acl youtube url_regex -i ^https?:\/\/.*\.ytimg\.com.*\.(webp|jpg|gif)
store_id_program /etc/squid/store-id.pl
store_id_extras "%{Referer}>h"
store_id_children 10 startup=5 idle=2 concurrency=100
store_id_access allow youtube
store_id_access deny all
qos_flows tos local-hit=0x30
 
refresh_pattern -i ^http.*\.dokter\-squid\.com 432000 100% 432000 override-expire override-lastmod reload-into-ims ignore-reload ignore-no-store ignore-private ignore-auth ignore-must-revalidate
 
refresh_pattern ^ftp: 1440 20% 10080
refresh_pattern ^gopher: 1440 0% 1440
refresh_pattern -i (/cgi-bin/|\?) 0 0% 0
refresh_pattern . 0 20% 4320
# END
```

```
#!/usr/bin/perl
# =====================================================
# = DSI store-id sample youtube 2016
# = https://www.facebook.com/R.dhani.dhanu
# = http://www.dokter-squid.com/
# =====================================================
 
$|=1;
while (<>) {
chomp;
 
my $dsi = "";
if (s/^(\d+\s+)//o) { $dsi = $1; }
 
@X = split;
if (@X[0] =~ m/^(exit|quit|x|q)/) {
print STDERR "quiting helper quietly\n";
exit 0;
}
$url = $X[0];
$referer = $X[1];
 
# youtube.com
if ($url =~ m/^https?:\/\/.*\.googlevideo\.com\/videoplayback\?.*/) {
        @id = m/[\&?|\%?|\s?]id=([^\&\%\s]+)/;
        @range = m/[\&?|\%?|\s?]range=([^\&\%\s]+)/;
        @itag = m/[\&?|\%?|\s?]itag=([^\&\%\s]+)/;
        @mime = m/[\&?|\%?|\s?]mime=([^\&\%\s]+)/;
        @clen = m/[\&?|\%?|\s?]clen=([^\&\%\s]+)/;
        if ($referer =~ m/^https?\:\/\/www\.youtube\.com\/(watch\?v\=|embed\/|v\/)(.*)/) {
            $v = $2;
        } else { $v = $id[0] }
        $out = "http://youtube.dokter-squid.com/" . $v . "@range@itag@mime@clen";
 
 
# ytimg.com
} elsif ($url =~ m/^https?:\/\/.*\.ytimg\.com(.*\.(webp|jpg|gif))/) {
    $out = "http://ytimg.dokter-squid.com/$1";
 
} else  {
    $out = "ERR";
}
if ($out =~ m/^http:\/\/.*/) {
    print $dsi, "OK store-id=$out\n";
} else {
    print $dsi, "ERR\n";
}
}
```

```
iptables -t mangle -F
iptables -t mangle -X
 
echo 0 > /proc/sys/net/ipv4/conf/lo/rp_filter
echo 1 > /proc/sys/net/ipv4/ip_forward
 
ip rule add fwmark 1 lookup 100
ip route add local 0.0.0.0/0 dev lo table 100
 
iptables -t mangle -N DIVERT
iptables -t mangle -A PREROUTING -p tcp -m socket -j DIVERT
 
iptables -t mangle -A DIVERT -j MARK --set-mark 1
iptables -t mangle -A DIVERT -j ACCEPT
 
iptables -t mangle -A PREROUTING -p tcp --dport 80 -j TPROXY --tproxy-mark 0x1/0x1 --on-port 3129
iptables -t mangle -A PREROUTING -p tcp --dport 8080 -j TPROXY --tproxy-mark 0x1/0x1 --on-port 3129

    iptables -t mangle -A PREROUTING -p tcp --dport 443 -j TPROXY --tproxy-mark 0x1/0x1 --on-port 3127

exit 0
```
```

/ip firewall mangle
add action=mark-connection chain=prerouting comment="HTTP + HTTPS TO PROXY" dst-port=80,8080,443 new-connection-mark=to_proxy protocol=tcp src-address=192.168.2.0/24
add chain=prerouting src-mac-address=08:00:27:F7:75:7D[SIZE=2] [COLOR=#ff0000][FONT=comic sans ms]what mac i put in here from [/FONT][/COLOR][COLOR=#0000ff][FONT=comic sans ms]ROUTER[/FONT][/COLOR][COLOR=#ff0000][FONT=comic sans ms] or The [/FONT][/COLOR][COLOR=#0000ff][FONT=comic sans ms]SQUID[/FONT][/COLOR][/SIZE]

add action=mark-routing chain=prerouting connection-mark=to_proxy new-routing-mark=tproxy_route passthrough=no
/ip route
add distance=1 gateway=192.168.100.2 routing-mark=tproxy_route
/ip firewall mangle
add action=mark-packet chain=forward comment="HIT PROXY" dscp=12 new-packet-mark=HIT passthrough=no

```

---

