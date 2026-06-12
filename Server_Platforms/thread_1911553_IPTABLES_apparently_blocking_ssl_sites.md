---
title: "IPTABLES apparently blocking ssl sites"
date: 2012-01-19
forum: Server Platforms
---

### Post by williamwd on 2012-01-19
Hello everyone,

i have a PC that manages my home network(share internet with neighbors), with a little firewall script that i found a long ago on the internet(do not remember where), anyway, it seems like some https sites just does not work! My firefox says connecting to server ...... and nothing happens. I will post the internet script that i use.

```

# carrega modulos
/sbin/modprobe iptable_nat
/sbin/modprobe ip_conntrack
/sbin/modprobe ip_conntrack_ftp
/sbin/modprobe ip_nat_ftp
/sbin/modprobe ipt_LOG
/sbin/modprobe ipt_REJECT
/sbin/modprobe ipt_MASQUERADE
/sbin/modprobe ip_queue

# protecao contra spoofing
echo 1 > /proc/sys/net/ipv4/conf/all/rp_filter

# protecao contra spoofing 2
echo 0 > /proc/sys/net/ipv4/conf/all/accept_source_route
echo 1 > /proc/sys/net/ipv4/tcp_syncookies
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts
echo 1 > /proc/sys/net/ipv4/icmp_ignore_bogus_error_responses

# limpa as tabelas existentes
iptables -F
iptables -t mangle -F
iptables -t nat -F
iptables -X

# politica padrao
iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -P FORWARD DROP

# conexoes preestabelecidas
iptables -A INPUT -m state --state ESTABLISHED,RELATED,NEW -j ACCEPT
iptables -A OUTPUT -m state --state ESTABLISHED,RELATED,NEW -j ACCEPT
iptables -A FORWARD -m state --state ESTABLISHED,RELATED,NEW -j ACCEPT

# libera interface loopback
iptables -A INPUT -i lo -j ACCEPT

# Registro de logs
iptables -A INPUT -p tcp --dport 333 --syn -j LOG --log-prefix="[TENTATIVA ACESSO FWLOGWATCH]"
iptables -A INPUT -p tcp --dport 23 --syn -j LOG --log-prefix="[TENTATIVA ACESSO TELNET]"
iptables -A INPUT -p tcp --dport 10000 --syn -j LOG --log-prefix="[TENTATIVA ACESSO WEBMIN]"
iptables -A FORWARD -m multiport -p tcp --dport 5800,5900,6000 -j LOG --log-prefix="[ACESSO VNC]"
#iptables -A INPUT -p tcp --dport 22 --syn -j LOG --log-prefix="[TENTATIVA ACESSO SSH]"
iptables -A INPUT -p tcp --dport 2222 --syn -j LOG --log-prefix="[TENTATIVA ACESSO SSH]"
iptables -A INPUT -p tcp --dport 21 --syn -j LOG --log-prefix="[TENTATIVA ACESSO FTP]"

############### Redireciona pro Squid #############################
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128

#################################### SCRIPT ####################################################
#Declarando algumas variaveis
arq_clientes="/home/william/PHP/cadastro/cadastro.txt"
for ip in `cat $arq_clientes|cut -d# -f 1` ; do
        # Identifica o MAC ADDRESS
        mac="`grep -w $ip $arq_clientes|cut -d# -f2`"
        # Identifica o nome do cliente
        cliente="`grep -w $ip $arq_clientes|cut -d# -f3`"
        bloq="`grep -w $ip $arq_clientes|cut -d# -f4`"
          echo -e "Cadastrou o IP: $ip\nMAC: $mac\nCLIENTE: $cliente"
          iptables -t filter -A FORWARD -d 0/0 -s $ip -m mac --mac-source $mac -j ACCEPT
          iptables -t filter -A FORWARD -d $ip -s 0/0 -m mac --mac-source $mac -j ACCEPT
          iptables -t filter -A INPUT -s $ip -d 0/0 -m mac --mac-source $mac -j ACCEPT
          iptables -t filter -A INPUT -s 0/0 -d $ip -m mac --mac-source $mac -j ACCEPT
          iptables -t nat -A POSTROUTING -s $ip -o ppp0 -j MASQUERADE
done
################################################################################################


############# Sem o filtro de MAC ################################

#iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 22 -j DNAT --to-dest 192.168.20.1
#iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

# habilita roteamento no kernel
echo 1 > /proc/sys/net/ipv4/ip_forward

```as you can see, i have a file with MACs and IPs. If anyone have a suggestion for a change or a new script i accept, i just need it to accept incoming connections (remote access) and MAC filtering(so I can control how many PCs there are using my connection).

GOOGLE MAIL works, but ITUNES, FACEBOOK and other sites load very slowly(if i press ESC while it's loading, i can navigate on FACEBOOK)


Thank you and sorry if I misspelled something :p

---

### Post by a2j on 2012-01-20
you said you found this script on the internet. but let me ask you, do you actually know what each command does in this script? understanding this script is first step toward troubleshooting it.

---

### Post by williamwd on 2012-01-20
I have read the man page of IPTABLES and put the comments...I also made some changes to the original script, so I can access my server from the internet... Is there any chance that squid is messing with the 443 port? I did not consider it before

---

### Post by CharlesA on 2012-01-20
I cannot read most of the language since it's not English, but Squid shouldn't have anything to do with HTTPS, so it would be unaffected by that.

Have you tried allowing port 443 out?

---

### Post by Dangertux on 2012-01-20
You'll probably also notice you're not logging much either.

Those ESTABLISHED,RELATED,NEW rules at the beginning are going to eliminate pretty much any other rules in the INPUT chain right off the bat.

It doesn't matter what you allow outbound since everything to and from that machine is allowed by your rules so you don't need to add a rule for HTTPS outbound. Squid can and may be affecting your performance on ssl sites.

Hope this helps.

---

### Post by williamwd on 2012-02-15
Sorry for the delay, vacations :)

but yes, i allow everything and that is why i don't understand this problem.
Here is my squid.conf

```


http_port 3128 transparent
cache_mem 300 MB 
cache_swap_low 90
cache_swap_high 95

maximum_object_size 700 MB
maximum_object_size_in_memory 500 KB

access_log /var/log/squid3/access.log squid
cache_log /var/log/squid3/cache.log
cache_store_log /var/log/squid3/store.log
pid_filename /var/log/squid3/squid3.pid
mime_table /usr/share/squid3/mime.conf

cache_mgr admin@domain
memory_pools off

diskd_program /usr/lib/squid3/diskd
unlinkd_program /usr/lib/squid3/unlinkd

acl manager proto cache_object
acl localhost src 127.0.0.1/32
acl casa src 192.168.20.1-192.168.20.30
acl william src 192.168.30.1-192.168.30.10
acl vizinhos src 192.168.100.20-192.168.100.35
acl SSL_ports port 443 563
acl Safe_ports port 21 80 443 563 70 210 280 488 59 777 901 1025-65535
acl purge method PURGE
acl CONNECT method CONNECT

http_access allow manager localhost
http_access allow manager casa
http_access allow manager vizinhos
http_access allow manager william
http_access deny manager
http_access allow purge localhost
http_access allow purge casa
http_access allow purge vizinhos
http_access allow purge william
http_access deny purge
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports

http_access allow localhost
http_access allow casa
http_access allow vizinhos
http_access allow william
http_access deny all


```

---

