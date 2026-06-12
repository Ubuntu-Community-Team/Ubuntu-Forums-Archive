---
title: "Script to install DHCP, Proxy, Content Filter, Webmin for Ubuntu 10.04"
date: 2011-04-09
forum: Server Platforms
---

### Post by jaimerosario on 2011-04-09
Greetings.

This is a work-in-progress I've been for a long time setting up. Test it or use it.

IT IS VERY IMPORTANT TO SETUP THE eth0 as the outside/internet gateway, so eth1 through eth4 will do NAT. The script automatically sets up DHCP Server, Dansguardian and Squid3. Also, it uses OpenDNS as the default forward DNS servers in BIND9. BIND9 is configured as a DNS Caching server only.

The script does the following:
1. Installs the following packages:
- Webmin, DHCP Server, BIND9, Squid3, Dansguardian, Samba, LikewiseOpen, and other tools for troubleshooting.
2. Detects up to 5 Network Adapters (eth only). Configures DHCP Server from eth1 to eth4.
3. Configures Squid3 and organize the configuration file by sections. Also adds ACLs for Windows Update, Adobe, Java and antivirus and security sites to bypass the proxy when updating (great for user authentication setup).
4. Configures Dansguardian with multiple filtering groups (up to 6, but only 4 active). Uses URL Big Black List for domain and url filtering. Allows access of more than 2,000 words/expressions that are "safe" in the urls expressions. Both english and spanish words included.
5. Installs Webmin and the Dansguardian Webmin Module, configured automatically for Ubuntu. 

What this script DOES NOT (IMPORTANT TO READ BEFORE USING IT):
1. IT DOES NOT CONFIGURES network adapters. You must configure all network adapters correctly, otherwise the script will trash configuration files.
2. IT DOES NOT CONFIGURES DOMAINS. BIND9 is configured as DNS Caching using OpenDNS as the default forwards. If you already have an active account, it will work out of the box. If are using FamilyShield, just edit out the Basic DNS ips.
3. IT DOES NOT CONFIGURES PROXY AUTHENTICATION. But make it easy to do when checking the squid3 configuration file, because is more organized.
4. IT DOES NOT CONFIGURES NAT or FIREWALL RULES. I recommend to use Firewall Builder or your prefered firewall settings.

NOTES:
- Popular Social Networking sites are blocked by default. The can be unblocked in each Dansguardian filtergroups "bannedsitelist".
- Live Messenger, Yahoo! Messenger and Torrents are blocked by default. They can be unblocked in Dansguardian "bannedmimetypelist"
- Squid3 is configured to bypass proxy when accessing sites like microsoft, adobe, and known antivirus and antispyware.
- Dansguardian is configured automatically to use ipgroups. Each subnet will be configure in a filtergroup. Filter group 4 is unrestricted unless eth4 is present and configured.
- All the original package configuration files that are changed are copied with the ".original" extension.
- When access Webmin for the first time, you must click on "Refresh Modules" so Squid and SysLog and other modules updates their configuration files. Some by default are not available until all modules are refreshed.
- This script is made mostly for schools and libraries. Feel free to use it and if you want to change it, that's ok. The more it can be improved, the better for all.

```
#!/bin/bash
#
# Proxy Server Installation Scripts v4.5
# by Jaime Rosario Justicia
#
#=============================== Activity Log =================================#
#
# 4.5 April 9, 2011
#
#=============================================================================#
#
#=============================================================================#
echo -e "Exporting environment settings"
#-----------------------------------------------------------------------------#
#	Export Webmin configuration data
#-----------------------------------------------------------------------------#
export wget_webmin="http://prdownloads.sourceforge.net/webadmin/webmin_1.540_all.deb"
export wget_dgwbm="http://voxel.dl.sourceforge.net/project/dgwebminmodule/dgwebmin-stable/0.7/dgwebmin-0.7.1.wbm"
export bind_webmin=/etc/webmin/bind8/config
export dhcpd_pid=/var/run/dhcp3-server/dhcpd.pid
export dhcp3_webmin=/etc/webmin/dhcpd/config
export squid_webmin=/etc/webmin/squid/config
export dg_webmin=/etc/webmin/dansguardian/config
export smb_webmin=/etc/webmin/samba/config
export syslog_webmin=/etc/webmin/syslog/config
export dhcp_conf=/etc/dhcp3/dhcpd.conf
#-----------------------------------------------------------------------------#
#	Export Squid3 configuration files
#-----------------------------------------------------------------------------#
export squidconf="/etc/squid3/squid.conf"
export squiddir="/etc/squid3"
export squidspool="/var/spool/squid3"
export squidacls="/etc/squid3/acls"
export squid_lib="/usr/lib/squid3"
#-----------------------------------------------------------------------------#
#	Export Dansguardian configuration files
#-----------------------------------------------------------------------------#
export dgconf=/etc/dansguardian/dansguardian.conf
export dgf1=/etc/dansguardian/dansguardianf1.conf
export dgf2=/etc/dansguardian/dansguardianf2.conf
export dgf3=/etc/dansguardian/dansguardianf3.conf
export dgf4=/etc/dansguardian/dansguardianf4.conf
export dgf5=/etc/dansguardian/dansguardianf5.conf
export dgf6=/etc/dansguardian/dansguardianf6.conf
export bannedurllist=/etc/dansguardian/lists/bannedurllist
export exceptionurllist=/etc/dansguardian/lists/exceptionurllist
export greyurllist=/etc/dansguardian/lists/greyurllist
export bannedsitelist=/etc/dansguardian/lists/bannedsitelist
export exceptionsitelist=/etc/dansguardian/lists/exceptionsitelist
export greysitelist=/etc/dansguardian/lists/greysitelist
export weightedphraselist=/etc/dansguardian/lists/weightedphraselist
export blacklists_domains=/tmp/site-lists
export blacklists_urls=/tmp/url-lists
export ipgroups=/etc/dansguardian/lists/authplugins/ipgroups
export blacklists_dir=/etc/dansguardian/lists/blacklists
export bannedphraselist=/etc/dansguardian/lists/bannedphraselist
export bannedregexpurllist=/etc/dansguardian/lists/bannedregexpurllist
export exceptionregexpurllist=/etc/dansguardian/lists/exceptionregexpurllist
export exceptionphraselist=/etc/dansguardian/lists/exceptionphraselist
export urlregexplist=/etc/dansguardian/lists/urlregexplist
export bannedmimetypelist=/etc/dansguardian/lists/bannedmimetypelist
export exceptionmimetypelist=/etc/dansguardian/lists/exceptionmimetypelist
export bannedextensionlist=/etc/dansguardian/lists/bannedextensionlist
export dansguardianlist=/etc/dansguardian/lists
export exceptionfilesitelist=/etc/dansguardian/lists/exceptionfilesitelist
export defaultexceptionsitelist=/etc/dansguardian/lists/defaultexceptionsitelist
export defaultexceptionurllist=/etc/dansguardian/lists/defaultexceptionurllist
export BL_URL="http://urlblacklist.com/cgi-bin/commercialdownload.pl?type=download&file=bigblacklist"
#-----------------------------------------------------------------------------#
#	Export network adapters configuration
#-----------------------------------------------------------------------------#
export eth_all=`ifconfig | grep eth | awk '{print $1}'`
if [[ "$eth_all" =~ "eth0" ]]
then
	# eth0 Configuration
	export eth0_ip=`ifconfig eth0 | grep "inet " | cut -d ':' -f2 | awk '{print $1}'`
	export eth0_net=`ifconfig eth0 | grep "inet " | cut -d '.' -f1,2,3 | cut -d ':' -f2 | awk '{print $0".0"}'`
	export eth0_mask=`ifconfig eth0 | grep Mask | cut -d ':' -f4 | awk '{print $1}'`
	export eth0_bcast=`ifconfig eth0 | grep Bcast | cut -d ":" -f3 | cut -d " " -f1`
	export eth0_netmask=`echo $eth0_net/$eth0_mask`
	export eth0_cmask=`ipcalc $eth0_netmask | grep Network | cut -d " " -f4`
else
	echo "Primary network adapter has not been found. Check your networking settings."
fi
	# eth1 Configuration
if [[ "$eth_all" =~ "eth1" ]]
then
	export eth1_ip=`ifconfig eth1 | grep "inet " | cut -d ':' -f2 | awk '{print $1}'`
	export eth1_net=`ifconfig eth1 | grep "inet " | cut -d '.' -f1,2,3 | cut -d ':' -f2 | awk '{print $0".0"}'`
	export eth1_mask=`ifconfig eth1 | grep Mask | cut -d ':' -f4 | awk '{print $1}'`
	export eth1_bcast=`ifconfig eth1 | grep Bcast | cut -d ":" -f3 | cut -d " " -f1`
	export eth1_netmask=`echo $eth1_net/$eth1_mask`
	export eth1_hostmin=`ipcalc $eth1_netmask | grep HostMin | cut -d " " -f4 | cut -d "." -f1,2,3 | awk '{print $0".50"}'`
	export eth1_hostmax=`ipcalc $eth1_netmask | grep HostMax | cut -d " " -f4`
	export eth1_cmask=`ipcalc $eth1_netmask | grep Network | cut -d " " -f4`
else
 	echo "ETH1 network adapter or configuration not found. Check your networking settings."
fi
# eth2 Configuration
if [[ "$eth_all" =~ "eth2" ]]
then
	export eth2_ip=`ifconfig eth2 | grep "inet " | cut -d ':' -f2 | awk '{print $1}'`
	export eth2_net=`ifconfig eth2 | grep "inet " | cut -d '.' -f1,2,3 | cut -d ':' -f2 | awk '{print $0".0"}'`
	export eth2_mask=`ifconfig eth2 | grep Mask | cut -d ':' -f4 | awk '{print $1}'`
	export eth2_bcast=`ifconfig eth2 | grep Bcast | cut -d ":" -f3 | cut -d " " -f1`
	export eth2_netmask=`echo $eth2_net/$eth2_mask`
	export eth2_hostmin=`ipcalc $eth2_netmask | grep HostMin | cut -d " " -f4 | cut -d "." -f1,2,3 | awk '{print $0".50"}'`
	export eth2_hostmax=`ipcalc $eth2_netmask | grep HostMax | cut -d " " -f4`
	export eth2_cmask=`ipcalc $eth2_netmask | grep Network | cut -d " " -f4`
else
 	echo "ETH2 network adapter not found."
fi
# eth3 Configuration
if [[ "$eth_all" =~ "eth3" ]]
then
	export eth3_ip=`ifconfig eth3 | grep "inet " | cut -d ':' -f2 | awk '{print $1}'`
	export eth3_net=`ifconfig eth3 | grep "inet " | cut -d '.' -f1,2,3 | cut -d ':' -f2 | awk '{print $0".0"}'`
	export eth3_mask=`ifconfig eth3 | grep Mask | cut -d ':' -f4 | awk '{print $1}'`
	export eth3_bcast=`ifconfig eth3 | grep Bcast | cut -d ":" -f3 | cut -d " " -f1`
	export eth3_netmask=`echo $eth3_net/$eth3_mask`
	export eth3_hostmin=`ipcalc $eth3_netmask | grep HostMin | cut -d " " -f4 | cut -d "." -f1,2,3 | awk '{print $0".50"}'`
	export eth3_hostmax=`ipcalc $eth3_netmask | grep HostMax | cut -d " " -f4`
	export eth3_cmask=`ipcalc $eth3_netmask | grep Network | cut -d " " -f4`
else
 	echo "ETH3 network adapter not found."
fi
# eth4 Configuration
if [[ "$eth_all" =~ "eth4" ]]
then
	export eth4_ip=`ifconfig eth4 | grep "inet " | cut -d ':' -f2 | awk '{print $1}'`
	export eth4_net=`ifconfig eth4 | grep "inet " | cut -d '.' -f1,2,3 | cut -d ':' -f2 | awk '{print $0".0"}'`
	export eth4_mask=`ifconfig eth4 | grep Mask | cut -d ':' -f4 | awk '{print $1}'`
	export eth4_bcast=`ifconfig eth4 | grep Bcast | cut -d ":" -f3 | cut -d " " -f1`
	export eth4_netmask=`echo $eth4_net/$eth4_mask`
	export eth4_hostmin=`ipcalc $eth4_netmask | grep HostMin | cut -d " " -f4 | cut -d "." -f1,2,3 | awk '{print $0".50"}'`
	export eth4_hostmax=`ipcalc $eth4_netmask | grep HostMax | cut -d " " -f4`
	export eth4_cmask=`ipcalc $eth4_netmask | grep Network | cut -d " " -f4`
else
 	echo "ETH4 network adapter not found."
fi
#-----------------------------------------------------------------------------#
echo "Installing Packages..."
#-----------------------------------------------------------------------------#
apt-get update  &> /dev/null
apt-get -y dselect-upgrade &> /dev/null
apt-get -y autoremove &> /dev/null
apt-get -y install lamp-server^ &> /dev/null
apt-get -y install bridge-utils vlan &> /dev/null
apt-get -y install bind9 dnsutils &> /dev/null
apt-get -y install dhcp3-server &> /dev/null
apt-get -y install ssh openssh-server &> /dev/null
apt-get -y install openssl stunnel &> /dev/null
apt-get -y install ntp ntpdate &> /dev/null
apt-get -y install ^squid3 calamaris &> /dev/null
apt-get -y install dansguardian &> /dev/null
apt-get -y install iptraf minicom traceroute nmap netcat whois ethtool ipcalc curl lynx arp-scan ifstat &> /dev/null
apt-get -y install zlib1g zip unzip &> /dev/null
apt-get -y -d install samba samba-common smbclient smbfs winbind acl likewise-open &> /dev/null
#=============================================================================#
#	Webmin and Modules
#-----------------------------------------------------------------------------#
mkdir /tmp/webmin &> /dev/null
echo "Downloading and installing Webmin, modules and extras..."
wget -q -c -O /tmp/webmin/webmin.deb $wget_webmin &> /dev/null
wget -q -c -O /tmp/webmin/dgwebmin.wbm $wget_dgwbm &> /dev/null
#
dpkg -i /tmp/webmin/webmin.deb &> /dev/null
apt-get -y -f install &> /dev/null
/usr/share/webmin/install-module.pl /tmp/webmin/dgwebmin.wbm &> /dev/null
#-----------------------------------------------------------------------------#
echo "Configuring BIND module..."
sed -i 's|stop_cmd=|stop_cmd=/etc/init.d/bind9 stop|' $bind_webmin
sed -i 's|start_cmd=|start_cmd=/etc/init.d/bind9 start|' $bind_webmin
#
echo "Configuring SysLog module..."
sed -i 's|syslogd=/sbin/syslogd|syslogd=/usr/sbin/rsyslogd|' $syslog_webmin
sed -i 's|restart_cmd=/etc/init.d/sysklogd reload|restart_cmd=service rsyslog reload|' $syslog_webmin
sed -i 's|start_cmd=/etc/init.d/sysklogd start|start_cmd=service rsyslog start|' $syslog_webmin
sed -i 's|signal_cmd=/etc/init.d/sysklogd restart|signal_cmd=service rsyslog restart|' $syslog_webmin
sed -i 's|syslog_conf=/etc/syslog.conf|syslog_conf=/etc/rsyslog.conf|' $syslog_webmin
#
echo "Configuring Samba Server module..."
sed -i 's|stop_cmd|#stop_cmd|' $smb_webmin
sed -i 's|start_cmd|#start_cmd|' $smb_webmin
echo -e 'stop_cmd=pkill smbd && pkill nmbd' >> $smb_webmin
echo -e 'start_cmd=service smbd start && service nmbd start' >> $smb_webmin
#
echo "Configuring DHCP Server module..."
sed -i 's|pid_file=/var/run/dhcpd.pid|pid_file=$dhcpd_pid|' $dhcp3_webmin
#
echo "Configuring Dansguardian module..."
> $dg_webmin
echo -e "binary_file=/usr/sbin/dansguardian" >> $dg_webmin
echo -e "pid_file=/var/run/dansguardian.pid" >> $dg_webmin
echo -e "start_cmd=/etc/init.d/dansguardian start" >> $dg_webmin
echo -e "stop_cmd=/etc/init.d/dansguardian stop" >> $dg_webmin
echo -e "restart_cmd=/etc/init.d/dansguardian stop && /etc/init.d/dansguardian start" >> $dg_webmin
echo -e "autoreload=1" >> $dg_webmin
echo -e "autorestart=1" >> $dg_webmin
echo -e "restart_type=1" >> $dg_webmin
echo -e "log_path=/var/log/dansguardian" >> $dg_webmin
echo -e "show_fixedlists=0" >> $dg_webmin
echo -e "conf_dir=/etc/dansguardian" >> $dg_webmin
echo -e "log_format=followDansGuardian" >> $dg_webmin
echo -e "messages_path=followDansGuardian" >> $dg_webmin
# Squid module settings
echo -e "Configuring Squid/Squid3 module..."
> $squid_webmin
echo -e "sort_conf=0" >> $squid_webmin
echo -e "squidclient=squidclient" >> $squid_webmin
echo -e "cache_dir=/var/spool/squid3" >> $squid_webmin
echo -e "sync_create=0" >> $squid_webmin
echo -e "log_dir=/var/log/squid3" >> $squid_webmin
echo -e "pid_file=/var/run/squid3.pid" >> $squid_webmin
echo -e "cal_max=50000" >> $squid_webmin
echo -e "sync_modify=1" >> $squid_webmin
echo -e "cal_fmt=w" >> $squid_webmin
echo -e "cal_all=1" >> $squid_webmin
echo -e "squid_path=squid3" >> $squid_webmin
echo -e "calamaris=calamaris" >> $squid_webmin
echo -e "squidconf=/etc/squid3/squid.conf" >> $squid_webmin
echo -e "sync_delete=0" >> $squid_webmin
echo -e "cal_args=-aw" >> $squid_webmin
echo -e "cachemgr_path=/usr/lib/cgi-bin/cachemgr3.cgi" >> $squid_webmin
echo -e "crypt_conf=0" >> $squid_webmin
echo -e "restart_pos=0" >> $squid_webmin
echo -e "squid_restart=/etc/init.d/dansguardian stop && squid3 -k reconfigure && /etc/init.d/dansguardian start" >> $squid_webmin
echo -e "squid_start=service squid3 start" >> $squid_webmin
echo -e "cal_extra=" >> $squid_webmin
echo -e "squid_stop=/etc/init.d/dansguardian stop && service squid3 stop" >> $squid_webmin
#
echo -e "Completed Webmin modules configuration..."
#=============================================================================#
echo "Backup Configuration Files..."
#-----------------------------------------------------------------------------#
cp /etc/squid3/squid.conf{,.original}
cp /etc/dhcp3/dhcpd.conf{,.original}
cp /etc/dansguardian/dansguardian.conf{,.original}
cp /etc/dansguardian/dansguardianf1.conf{,.original}
cp /etc/dhcp3/dhcpd.conf{,.original}
cp /etc/resolv.conf{,.original}
#=============================================================================#
echo "Configuring BIND DNS Forwarders..."
#-----------------------------------------------------------------------------#
> /etc/resolv.conf
echo "nameserver 127.0.0.1" >> /etc/resolv.conf
sed -i '14d' /etc/bind/named.conf.options
sed -i 's|// }|}|' /etc/bind/named.conf.options
sed -i 's|// forwarders|forwarders|' /etc/bind/named.conf.options
#
sed -i '13 a\\t208.67.222.220; # OpenDNS' /etc/bind/named.conf.options
sed -i '13 a\\t208.67.220.222; # OpenDNS' /etc/bind/named.conf.options
#
sed -i '13 a\\t208.67.222.123; # OpenDNS Family Shield' /etc/bind/named.conf.options
sed -i '13 a\\t208.67.220.123; # OpenDNS Family Shield' /etc/bind/named.conf.options
#
/etc/init.d/bind9 restart &> /dev/null
#=============================================================================#
echo -e "Configuring DHCP3 Server settings..."
#-----------------------------------------------------------------------------#
echo -e "ddns-update-style none;" >> $dhcp_conf
echo -e "default-lease-time 600;" >> $dhcp_conf
echo -e "max-lease-time 7200;" >> $dhcp_conf
echo -e "log-facility local7;" >> $dhcp_conf
echo -e "authoritative;" >> $dhcp_conf
echo -e "\t#option domain-name "'"DOMAIN.LOCAL"'";" >> $dhcp_conf
#
echo -e "Configuring DHCP Server Subnets..."
#
if [[ "$eth_all" =~ "eth1" ]]
then
	echo -e "#Local Network $eth1_net" >> $dhcp_conf
	echo -e "subnet $eth1_net netmask $eth1_mask { " >> $dhcp_conf
	echo -e "\t#option netbios-node-type 8;" >> $dhcp_conf
	echo -e "\t#option netbios-name-servers $eth1_ip;" >> $dhcp_conf
	echo -e "\toption time-servers $eth1_ip;" >> $dhcp_conf
	echo -e "\toption subnet-mask $eth1_mask;" >> $dhcp_conf
	echo -e "\toption domain-name-servers $eth1_ip;" >> $dhcp_conf
	echo -e "\t#option domain-name "'"DOMAIN.LOCAL"'";" >> $dhcp_conf
	echo -e "\toption broadcast-address $eth1_bcast;" >> $dhcp_conf
	echo -e "\toption routers $eth1_ip;" >> $dhcp_conf
	echo -e "\trange $eth1_hostmin $eth1_hostmax;" >> $dhcp_conf
	echo -e "\t} " >> $dhcp_conf
else
	echo ;
fi
if [[ "$eth_all" =~ "eth2" ]]
then
	echo -e "#Local Network $eth2_net" >> $dhcp_conf
	echo -e "subnet $eth2_net netmask $eth2_mask { " >> $dhcp_conf
	echo -e "\t#option netbios-node-type 8;" >> $dhcp_conf
	echo -e "\t#option netbios-name-servers $eth2_ip;" >> $dhcp_conf
	echo -e "\toption time-servers $eth2_ip;" >> $dhcp_conf
	echo -e "\toption subnet-mask $eth2_mask;" >> $dhcp_conf
	echo -e "\toption domain-name-servers $eth2_ip;" >> $dhcp_conf
	echo -e "\t#option domain-name "'"DOMAIN.LOCAL"'";" >> $dhcp_conf
	echo -e "\toption broadcast-address $eth2_bcast;" >> $dhcp_conf
	echo -e "\toption routers $eth2_ip;" >> $dhcp_conf
	echo -e "\trange $eth2_hostmin $eth2_hostmax;" >> $dhcp_conf
	echo -e "\t} " >> $dhcp_conf
else
	echo ;
fi
if [[ "$eth_all" =~ "eth3" ]]
then
	echo -e "#Local Network $eth3_net" >> $dhcp_conf
	echo -e "subnet $eth3_net netmask $eth3_mask { " >> $dhcp_conf
	echo -e "\t#option netbios-node-type 8;" >> $dhcp_conf
	echo -e "\t#option netbios-name-servers $eth3_ip;" >> $dhcp_conf
	echo -e "\toption time-servers $eth3_ip;" >> $dhcp_conf
	echo -e "\toption subnet-mask $eth3_mask;" >> $dhcp_conf
	echo -e "\toption domain-name-servers $eth3_ip;" >> $dhcp_conf
	echo -e "\t#option domain-name "'"DOMAIN.LOCAL"'";" >> $dhcp_conf
	echo -e "\toption broadcast-address $eth3_bcast;" >> $dhcp_conf
	echo -e "\toption routers $eth3_ip;" >> $dhcp_conf
	echo -e "\trange $eth3_hostmin $eth3_hostmax;" >> $dhcp_conf
	echo -e "\t} " >> $dhcp_conf
else
	echo ;
fi
if [[ "$eth_all" =~ "eth4" ]]
then
	echo -e "#Local Network $eth4_net" >> $dhcp_conf
	echo -e "subnet $eth4_net netmask $eth4_mask { " >> $dhcp_conf
	echo -e "\t#option netbios-node-type 8;" >> $dhcp_conf
	echo -e "\t#option netbios-name-servers $eth4_ip;" >> $dhcp_conf
	echo -e "\toption time-servers $eth4_ip;" >> $dhcp_conf
	echo -e "\toption subnet-mask $eth4_mask;" >> $dhcp_conf
	echo -e "\toption domain-name-servers $eth4_ip;" >> $dhcp_conf
	echo -e "\t#option domain-name "'"DOMAIN.LOCAL"'";" >> $dhcp_conf
	echo -e "\toption broadcast-address $eth4_bcast;" >> $dhcp_conf
	echo -e "\toption routers $eth4_ip;" >> $dhcp_conf
	echo -e "\trange $eth4_hostmin $eth4_hostmax;" >> $dhcp_conf
	echo -e "\t} " >> $dhcp_conf
else
	echo ;
fi
#
/etc/init.d/dhcp3-server start &> /dev/null
#=============================================================================#
echo -e "Customizing Squid Proxy server configuration file..."
#-----------------------------------------------------------------------------#
# Creates ACL Folder
mkdir $squidacls &> /dev/null
# Creates extended ACLs and files
touch ${squidacls}/allowed_domains.acl
touch ${squidacls}/allowed_urls.acl
touch ${squidacls}/malware-block-list.acl
touch ${squidacls}/windowsupdate.acl
touch ${squidacls}/wuCONNECT.acl
# Cache and Memory settings
echo -e "#==============================================================================#" >> ${squidconf}
echo -e "#\tWindows Update Fix - DO NOT CHANGE" >> ${squidconf}
echo -e "#==============================================================================#" >> ${squidconf}
echo -e acl windowsupdate dstdomain '"'/etc/squid3/acls/windowsupdate.acl'"' >> ${squidconf}
echo -e acl wuCONNECT dstdomain '"'/etc/squid3/acls/wuCONNECT.acl'"' >> ${squidconf}
echo -e "" >> ${squidconf}
echo -e "#==============================================================================#" >> ${squidconf}
echo -e "#\tJava browser fix - DO NOT CHANGE" >> ${squidconf}
echo -e "#==============================================================================#" >> ${squidconf}
echo -e acl Java browser Java/1.4 Java/1.5 Java/1.6 >> ${squidconf}
echo -e "" >> ${squidconf}
echo -e "#==============================================================================#" >> ${squidconf}
echo -e "#\tAllowed Domains and URLS - DO NOT CHANGE" >> ${squidconf}
echo -e "#==============================================================================#" >> ${squidconf}
echo -e acl allowed_domains dstdomain '"'/etc/squid3/acls/allowed_domains.acl'"' >> ${squidconf}
echo -e acl allowed_urls dstdom_regex -i '"'/etc/squid3/acls/allowed_urls.acl'"' >> ${squidconf}
echo -e "" >> ${squidconf}
echo -e "#==============================================================================#" >> ${squidconf}
echo -e "#\tNTLM / BASIC Proxy Authentication" >> ${squidconf}
echo -e "#------------------------------------------------------------------------------#" >> ${squidconf}
echo -e "# Uncomment the required lines to enable NTLM Authentication with a" >> ${squidconf}
echo -e "# Windows 200x Active Directory Server." >> ${squidconf}
echo -e "#------------------------------------------------------------------------------#" >> ${squidconf}
echo -e "" >> ${squidconf}
echo -e "#auth_param ntlm program /usr/bin/ntlm_auth --helper-protocol=squid-2.5-ntlmssp" >> ${squidconf}
echo -e "#auth_param ntlm children 30" >> ${squidconf}
echo -e "#auth_param ntlm keep_alive on" >> ${squidconf}
echo -e "#auth_param ntlm max_challenge_reuses 100" >> ${squidconf}
echo -e "#auth_param ntlm max_challenge_lifetime 10 minutesl." >> ${squidconf}
echo -e "#" >> ${squidconf}
echo -e "#auth_param basic program /usr/bin/ntlm_auth --helper-protocol=squid-2.5-basic" >> ${squidconf}
echo -e "#auth_param basic children 10" >> ${squidconf}
echo -e "#auth_param basic realm DOMAIN" >> ${squidconf}
echo -e "#auth_param basic credentialsttl 2 hour" >> ${squidconf}
echo -e "#auth_param basic casesensitive off" >> ${squidconf}
echo -e "" >> ${squidconf}
echo -e "#==============================================================================#" >> ${squidconf}
echo -e "#\tBASIC Proxy Authentication" >> ${squidconf}
echo -e "#------------------------------------------------------------------------------#" >> ${squidconf}
echo -e "# Uncomment the required lines to enable Basic Proxy Authentication." >> ${squidconf}
echo -e "#------------------------------------------------------------------------------#" >> ${squidconf}
echo -e "" >> ${squidconf}
echo -e "#auth_param basic program /usr/lib/squid3/ncsa_auth /etc/squid3/login" >> ${squidconf}
echo -e "#auth_param basic children 5" >> ${squidconf}
echo -e "#auth_param basic realm Proxy Authentication" >> ${squidconf}
echo -e "#auth_param basic credentialsttl 2 hours" >> ${squidconf}
echo -e "" >> ${squidconf}
echo -e "#==============================================================================#" >> ${squidconf}
echo -e "#\tAuthentication ACL" >> ${squidconf}
echo -e "#------------------------------------------------------------------------------#" >> ${squidconf}
echo -e "# Uncomment 'acl AUTHENTICATION proxy_auth REQUIRED' to enable" >> ${squidconf}
echo -e "# Proxy Authentication. Remember to uncomment Basic or NTLM Authentication" >> ${squidconf}
echo -e "# settings." >> ${squidconf}
echo -e "#------------------------------------------------------------------------------#" >> ${squidconf}
echo -e "#acl AUTHENTICATION proxy_auth REQUIRED" >> ${squidconf}
echo -e "" >> ${squidconf}
echo -e "#==============================================================================#" >> ${squidconf}
echo -e "#\tAccess Control List - DO NOT CHANGE" >> ${squidconf}
echo -e "#==============================================================================#" >> ${squidconf}
echo -e acl manager proto cache_object >> ${squidconf}
echo -e acl localhost src 127.0.0.1/32 >> ${squidconf}
echo -e acl to_localhost dst 127.0.0.0/8 0.0.0.0/32 >> ${squidconf}
echo -e acl SSL_ports port 443 >> ${squidconf}
echo -e acl Safe_ports port 80 >> ${squidconf}
echo -e "acl Safe_ports port 21 # http" >> ${squidconf}
echo -e "acl Safe_ports port 443 # ftp" >> ${squidconf}
echo -e "acl Safe_ports port 70 # https" >> ${squidconf}
echo -e acl CONNECT method CONNECT >> ${squidconf}
echo -e "#" >> ${squidconf}
echo -e acl localnet src 10.0.0.0/8 >> ${squidconf}
echo -e acl localnet src 172.16.0.0/12 >> ${squidconf}
echo -e acl localnet src 192.168.0.0/16 >> ${squidconf}
echo -e "" >> ${squidconf}
echo -e "#==============================================================================#" >> ${squidconf}
echo -e "#\tProxy Restrictions - DO NOT CHANGE" >> ${squidconf}
echo -e "#==============================================================================#" >> ${squidconf}
echo -e http_access allow CONNECT wuCONNECT localnet >> ${squidconf}
echo -e http_access allow CONNECT wuCONNECT localhost >> ${squidconf}
echo -e http_access allow windowsupdate localnet >> ${squidconf}
echo -e http_access allow windowsupdate localhost >> ${squidconf}
echo -e "#" >> ${squidconf}
echo -e http_access allow CONNECT Java localnet >> ${squidconf}
echo -e http_access allow CONNECT Java localhost >> ${squidconf}
echo -e http_access allow Java localnet >> ${squidconf}
echo -e http_access allow Java localhost >> ${squidconf}
echo -e "#" >> ${squidconf}
echo -e http_access allow CONNECT allowed_domains localnet >> ${squidconf}
echo -e http_access allow CONNECT allowed_domains localhost >> ${squidconf}
echo -e http_access allow allowed_domains localnet >> ${squidconf}
echo -e http_access allow allowed_domains localhost >> ${squidconf}
echo -e "" >> ${squidconf}
echo -e "#==============================================================================#" >> ${squidconf}
echo -e "#\tSquid3 Default Proxy Manager Settings - DO NOT CHANGE" >> ${squidconf}
echo -e "#==============================================================================#" >> ${squidconf}
echo -e http_access allow manager localhost >> ${squidconf}
echo -e http_access deny manager >> ${squidconf}
echo -e "http_access deny !Safe_ports" >> ${squidconf}
echo -e "http_access deny CONNECT !SSL_ports" >> ${squidconf}
echo -e "" >> ${squidconf}
echo -e "#==============================================================================#" >> ${squidconf}
echo -e "# Uncomment 'http_access allow AUTHENTICATION' to enable proxy authentication." >> ${squidconf}
echo -e "#------------------------------------------------------------------------------#" >> ${squidconf}
echo -e "#http_access allow AUTHENTICATION" >> ${squidconf}
echo -e "" >> ${squidconf}
echo -e "#==============================================================================#" >> ${squidconf}
echo -e "#\tSquid3 Default Proxy Settings - DO NOT CHANGE" >> ${squidconf}
echo -e "#==============================================================================#" >> ${squidconf}
echo -e http_access allow localnet >> ${squidconf}
echo -e http_access allow localhost >> ${squidconf}
echo -e http_access deny all >> ${squidconf}
echo -e icp_access deny all >> ${squidconf}
echo -e htcp_access deny all >> ${squidconf}
echo -e "" >> ${squidconf}
echo -e "#==============================================================================#" >> ${squidconf}
echo -e "#\tPort Settings" >> ${squidconf}
echo -e "#==============================================================================#" >> ${squidconf}
echo -e "# Add '"'transparent'"' after http_port 3128 to enable Transparent Proxy" >> ${squidconf}
echo -e "#------------------------------------------------------------------------------#" >> ${squidconf}
echo -e http_port 3128 >> ${squidconf}
echo -e icp_port 3130 >> ${squidconf}
echo -e "" >> ${squidconf}
echo -e "#==============================================================================#" >> ${squidconf}
echo -e "#\tCache and Memory Settings - BE CAREFUL WHEN CHANGING SETTINGS" >> ${squidconf}
echo -e "#==============================================================================#" >> ${squidconf}
echo -e hierarchy_stoplist cgi-bin ? >> ${squidconf}
echo -e cache_dir ufs /var/spool/squid3 16384 16 256 >> ${squidconf}
echo -e maximum_object_size 1 GB >> ${squidconf}
echo -e cache_mem 256 MB >> ${squidconf}
echo -e "" >> ${squidconf}
echo -e "#------------------------------------------------------------------------------#" >> ${squidconf}
echo -e "# Comment the following settings if slow browsing is experienced." >> ${squidconf}
echo -e "# These are needed uncommented for Windows Update." >> ${squidconf}
echo -e "#------------------------------------------------------------------------------#"  >> ${squidconf}
echo -e "range_offset_limit -1" >> ${squidconf}
echo -e "quick_abort_min -1" >> ${squidconf}
echo -e "" >> ${squidconf}
echo -e "#==============================================================================#" >> ${squidconf}
echo -e "#\tRefresh Patterns - DO NOT CHANGE" >> ${squidconf}
echo -e "#==============================================================================#" >> ${squidconf}
echo -e "refresh_pattern ^ftp:\t1440\t20%\t10080" >> ${squidconf}
echo -e "refresh_pattern ^gopher:\t1440\t0%\t1440" >> ${squidconf}
echo -e "refresh_pattern (cgi-bin|\?)\t0\t0%\t0" >> ${squidconf}
echo -e "refresh_pattern .\t\t0\t20%\t4320" >> ${squidconf}
echo -e "" >> ${squidconf}
echo -e "#==============================================================================#" >> ${squidconf}
echo -e "#\tDNS Name Servers" >> ${squidconf}
echo -e "#------------------------------------------------------------------------------#" >> ${squidconf}
echo -e "# Uncomment only the desired DNS servers." >> ${squidconf}
echo -e "# If you are combining Dansguardian with OpenDNS and need to allow unrestricted" >> ${squidconf}
echo -e "# users or devices to bypass OpenDNS, use the default option." >> ${squidconf}
echo -e "#" >> ${squidconf}
echo -e "# 8.8.8.8, 8.8.4.4 - Google DNS (Not filtered)" >> ${squidconf}
echo -e "# 208.67.222.222, 208.67.220.220 - OpenDNS" >> ${squidconf}
echo -e "# 208.67.222.123, 208.67.220.123 - OpenDNS FamilyShield" >> ${squidconf}
echo -e "#------------------------------------------------------------------------------#" >> ${squidconf}
echo -e "#dns_nameservers 8.8.8.8 8.8.4.4" >> ${squidconf}
echo -e "#dns_nameservers 208.67.222.222 208.67.220.220" >> ${squidconf}
echo -e "#dns_nameservers 208.67.222.123 208.67.220.123" >> ${squidconf}
echo -e "" >> ${squidconf}
echo -e "#==============================================================================#" >> ${squidconf}
echo -e "#\tOther Settings - DO NOT CHANGE" >> ${squidconf}
echo -e "#==============================================================================#" >> ${squidconf}
echo -e coredump_dir /var/spool/squid3 >> ${squidconf}
echo -e visible_hostname localhost >> ${squidconf}
echo -e access_log /var/log/squid3/access.log squid >> ${squidconf}
echo -e error_directory /usr/share/squid3/errors/templates/ >> ${squidconf}
echo -e "" >> ${squidconf}
#-----------------------------------------------------------------------------#
# Adding entries to External ACLs
#-----------------------------------------------------------------------------#
echo -e ".adobe.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".akamai.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".alwil.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".antivirus.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".avast.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".avg.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".avira.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".bitdefender.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".ca.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".clic.xtec.cat" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".cloudantivirus.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".debian.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".edline.net" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".eset.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".free-av.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".freeavg.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".go-mono.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".grisoft.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".grisoft.cz" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".java.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".kaspersky.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".lavasoft.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".malwarebytes.org" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".mcafeeasap.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".mcafee.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".microsoft.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".mono-project.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".mozilla.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".nai.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".norman.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".norton.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".opera.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".oracle.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".pandasecurity.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".pctools.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".real.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".safer-networking.org" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".sun.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".superantispyware.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".symantec.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".symantecliveupdate.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".sysinternals.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".trendmicro.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".trendsecure.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".ubuntu.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".verisign.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".virusbtn.com" >> /etc/squid3/acls/allowed_domains.acl 
echo -e ".windowsupdate.com" >> /etc/squid3/acls/allowed_domains.acl
#
echo -e "windowsupdate.microsoft.com" >> /etc/squid3/acls/windowsupdate.acl
echo -e ".update.microsoft.com" >> /etc/squid3/acls/windowsupdate.acl
echo -e "download.windowsupdate.com" >> /etc/squid3/acls/windowsupdate.acl
echo -e "redir.metaservices.microsoft.com" >> /etc/squid3/acls/windowsupdate.acl
echo -e "images.metaservices.microsoft.com" >> /etc/squid3/acls/windowsupdate.acl
echo -e "c.microsoft.com" >> /etc/squid3/acls/windowsupdate.acl
echo -e "www.download.windowsupdate.com" >> /etc/squid3/acls/windowsupdate.acl
echo -e "wustat.windows.com" >> /etc/squid3/acls/windowsupdate.acl
echo -e "crl.microsoft.com" >> /etc/squid3/acls/windowsupdate.acl
echo -e "sls.microsoft.com" >> /etc/squid3/acls/windowsupdate.acl
echo -e "productactivation.one.microsoft.com" >> /etc/squid3/acls/windowsupdate.acl
echo -e "ntservicepack.microsoft.com" >> /etc/squid3/acls/windowsupdate.acl
#
echo -e "www.update.microsoft.com" >> /etc/squid3/acls/wuCONNECT.acl
echo -e "sls.microsoft.com" >> /etc/squid3/acls/wuCONNECT.acl
#=============================================================================#
echo	"Dansguardian Multiple Filter Groups Configuration..."
#-----------------------------------------------------------------------------#
#	Backup default Dansguardian configuration files
#-----------------------------------------------------------------------------#
cp $dgconf $dgconf.original
cp $dgf1 $dgf1.original
cp $bannedextensionlist $bannedextensionlist.original
cp $bannedmimetypelist $bannedmimetypelist.original
cp $bannedurllist $bannedurllist.original
cp $exceptionurllist $exceptionurllist.original
cp $greyurllist $greyurllist.original
cp $bannedsitelist $bannedsitelist.original
cp $exceptionsitelist $exceptionsitelist.original
cp $greysitelist $greysitelist.original

# Configuring dansguardian.conf
#-----------------------------------------------------------------------------#
sed -i "s|#authplugin = '/etc/dansguardian/authplugins/ip.conf'|authplugin = '/etc/dansguardian/authplugins/ip.conf'|" $dgconf
sed -i "s|UNCONFIGURED|# UNCONFIGURED|" $dgconf
sed -i "s|filtergroups = 1|filtergroups = 4|" $dgconf
sed -i "s|reverseaddresslookups = off|reverseaddresslookups = on|" $dgconf
sed -i "s|recheckreplacedurls = off|recheckreplacedurls = on|" $dgconf
# Configuring dansguardianf1.conf
#-----------------------------------------------------------------------------#
sed -i "s|enablepics = off|enablepics = on|" $dgf1
sed -i "s|deepurlanalysis = off|deepurlanalysis = on|" $dgf1
sed -i "s|naughtynesslimit = 50|naughtynesslimit = 300|" $dgf1
# Copies Dansguardian Filter Groups configuration files
#-----------------------------------------------------------------------------#
sed -i "s|/lists/|/lists/filter1/|" $dgf1
for s in `seq 2 6`
 do cp $dgf1 /etc/dansguardian/dansguardianf$s.conf
done
sed -i "s|filter1|filter2|" $dgf2
sed -i "s|filter1|filter3|" $dgf3
sed -i "s|filter1|filter4|" $dgf4
sed -i "s|filter1|filter5|" $dgf5
sed -i "s|filter1|filter6|" $dgf6
#
# Assing Server IP Address to Template
#-----------------------------------------------------------------------------#
#sed -i "s|localhost|'$eth0_ip'|" /etc/dansguardian/languages/ukenglish/template.html
#
#==============================================================================#
echo	"Setting up Dansguardian IP Filtering group settings..."
#------------------------------------------------------------------------------#
# Change default lists location to contents on each filter directory and group name identification
#-----------------------------------------------------------------------------#
if [[ "$eth_all" =~ "eth1" ]]
then
	sed -i "s|#groupname = ''|groupname = 'Network $eth1_cmask'|" $dgf1
else
	sed -i "s|#groupname = ''|groupname = 'Filter Group 1'|" $dgf1
fi
if [[ "$eth_all" =~ "eth2" ]]
then
	sed -i "s|#groupname = ''|groupname = 'Network $eth2_cmask'|" $dgf2
else
	sed -i "s|#groupname = ''|groupname = 'Filter Group 2'|" $dgf2
fi
if [[ "$eth_all" =~ "eth3" ]]
then
	sed -i "s|#groupname = ''|groupname = 'Network $eth3_cmask'|" $dgf3
else
	sed -i "s|#groupname = ''|groupname = 'Filter Group 3'|" $dgf3
fi
if [[ "$eth_all" =~ "eth4" ]]
then
	sed -i "s|#groupname = ''|groupname = 'Network $eth4_cmask'|" $dgf4
else
	sed -i "s|#groupname = ''|groupname = 'Filter Group 4 - Unrestricted'|" $dgf4
	sed -i "s|groupmode = 1|groupmode = 2|" $dgf4
fi
	sed -i "s|#groupname = ''|groupname = 'Filter Group 5'|" $dgf5
	sed -i "s|#groupname = ''|groupname = 'Filter Group 6'|" $dgf6
#==============================================================================#
echo -e "Customizing Dansguardian Phrase, Regular Expressions and Weighted Filtering settings..."
#------------------------------------------------------------------------------#
# Changing bannedphraselist
#-----------------------------------------------------------------------------#
sed -i 's|rta/banned_portuguese|rta/banned|' $bannedphraselist
sed -i 's|##.Include|#.Include|' $bannedphraselist
sed -i 's|#.Include|.Include|' $bannedphraselist
sed -i 's|#.Include|.Include|' $exceptionphraselist
#-----------------------------------------------------------------------------#
# Changing weightedphraselist
#-----------------------------------------------------------------------------#
sed -i 's|#.Include</etc/dansguardian/lists/phraselists/illegaldrugs|.Include</etc/dansguardian/lists/phraselists/illegaldrugs|' $weightedphraselist
sed -i 's|#.Include</etc/dansguardian/lists/phraselists/intolerance|.Include</etc/dansguardian/lists/phraselists/intolerance|' $weightedphraselist
sed -i 's|#.Include</etc/dansguardian/lists/phraselists/intolerance/weighted_portuguese>|.Include</etc/dansguardian/lists/phraselists/intolerance/weighted_portuguese>|' $weightedphraselist
sed -i 's|#.Include</etc/dansguardian/lists/phraselists/gore|.Include</etc/dansguardian/lists/phraselists/gore|' $weightedphraselist
sed -i 's|#.Include</etc/dansguardian/lists/phraselists/gore/weighted_portuguese>|.Include</etc/dansguardian/lists/phraselists/gore/weighted_portuguese>|' $weightedphraselist
sed -i 's|#.Include</etc/dansguardian/lists/phraselists/violence|.Include</etc/dansguardian/lists/phraselists/violence|' $weightedphraselist
sed -i 's|#.Include</etc/dansguardian/lists/phraselists/weapons|.Include</etc/dansguardian/lists/phraselists/weapons|' $weightedphraselist
sed -i 's|#.Include</etc/dansguardian/lists/phraselists/chat|.Include</etc/dansguardian/lists/phraselists/chat|' $weightedphraselist
sed -i 's|#.Include</etc/dansguardian/lists/phraselists/personals|.Include</etc/dansguardian/lists/phraselists/personals|' $weightedphraselist
sed -i 's|#.Include</etc/dansguardian/lists/phraselists/peer2peer|.Include</etc/dansguardian/lists/phraselists/peer2peer|' $weightedphraselist
sed -i 's|#.Include</etc/dansguardian/lists/phraselists/upstreamfilter|.Include</etc/dansguardian/lists/phraselists/upstreamfilter|' $weightedphraselist
sed -i 's|.Include</etc/dansguardian/lists/phraselists/goodphrases/weighted_general_malay>|#.Include</etc/dansguardian/lists/phraselists/goodphrases/weighted_general_malay>|' $weightedphraselist
sed -i 's|.Include</etc/dansguardian/lists/phraselists/pornography/weighted_japanese>|#.Include</etc/dansguardian/lists/phraselists/pornography/weighted_japanese>|' $weightedphraselist
sed -i 's|.Include</etc/dansguardian/lists/phraselists/pornography/weighted_malay>|#.Include</etc/dansguardian/lists/phraselists/pornography/weighted_malay>|' $weightedphraselist
#-----------------------------------------------------------------------------#
# Changing bannedextensionlist
#-----------------------------------------------------------------------------#
> $bannedextensionlist;
#-----------------------------------------------------------------------------#
# Changing urlregexplist
#-----------------------------------------------------------------------------#
sed -i 's|#"(|"(|' $urlregexplist
#-----------------------------------------------------------------------------#
# Changing bannedregexpurllist
#-----------------------------------------------------------------------------#
sed -i 's|#(naturism|(naturism|' $bannedregexpurllist
sed -i 's|#(^|(^|' $bannedregexpurllist
sed -i 's|#(free|(free|' $bannedregexpurllist
sed -i 's|#(meet|(meet|' $bannedregexpurllist
sed -i 's|#(marr|(marr|' $bannedregexpurllist
echo -e "" >> $bannedregexpurllist
echo -e "#------------------------------------------------------------------------#" >> $bannedregexpurllist
echo -e "# Paintball and Gotcha guns" >> $bannedregexpurllist
echo -e "#------------------------------------------------------------------------#" >> $bannedregexpurllist
echo -e "(paintball|gotcha)" >> $bannedregexpurllist
echo -e "" >> $bannedregexpurllist
#-----------------------------------------------------------------------------#
# Changing exceptionregexpurllist
#-----------------------------------------------------------------------------#
echo -e "#=============================================================================#" >> $exceptionregexpurllist
echo -e "#	Exception Regular Expresson URL List" >> $exceptionregexpurllist
echo -e "#=============================================================================#" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "# Words containing ANAL" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "(acanalad(a|o)|acanalador|acanaladura|acanalar|acanallad(a|o)|acanallar|aduanal|aguanal|amanal|analectas|anal(e|é)ptic(a|o)|analfabet(a|o)|analfabetismo|analgesia|analg(e|é)sica|analg(e|é)sico|analista|anal(i|í)stica|anal(i|í)stico|anal(i|í)tica|anal(i|í)ticamente|anal(i|í)tico|analitycs|analizable|analizador|analizadora|analizar|analog(i|í)a|anal(o|ó)gic(a|o)|anal(o|ó)gicamente|analyst|analytics|analyze|apanalad(a|o)|arrayanal|artesanal|atarazanal|avellanal|azafranal|bacanal|bacchanal|banal|banalidad|bananal|bisemanal|canal|canalad(a|o)|canalador|canaladura|canaleja|canalera|canalet(a|e|o)|canal(i|í)|canaliega|canaliz(a|o)|canalizable|canalizaci(o|ó)n|canalizar|canalla|canallada|canallesc(a|o)|canal(o|ó)n|caranganal|cientanal|contracanal|cuartanal|encanalar|encanalizar|encanallamiento|encanallar|entrecanal|epanalepsis|fanal|fontanal|google-analytics|granalla|granallar|hermanal|hontanal|humanal|inanalizable|leganal|manal|manzanal|marranalla|mundanal|mundanalidad|panal|pantanal|pichanal|platanal|psicoanalista|psicoanal(i|í)tic(a|o)|psicoanalizar|rabanal|ranal|remanal|sanalotodo|semanal|semanalmente|tarazanal|tempranal|trisemanal|varganal|ventanal)" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "# Words containing ***" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "(admass|admasses|amass|amassed|amasser|amassers|amasses|amassing|amassment|amassments|ambassador|ambassadorial|ambassadors|ambassadorship|ambassadorships|ambassadress|ambassadresses|antiassimilation|antiassimilations|anticlassical|antimacassar|antimacassars|assagai|assagaied|assagaiing|assagais|assai|assail|assailable|assailant|assailants|assailed|assailer|assailers|assailing|assails|assais|assassin|assassinate|assassinated|assassinates|assassinating|assassination|assassinations|assassinator|assassinators|assassins|assault|assaulted|assaulter|assaulters|assaulting|assaultive|assaultively|assaultiveness|assaultivenesses|assaults|assay|assayed|assayer|assayers|assaying|assays|assed|assegai|assegaied|assegaiing|assegais|assemblage|assemblages|assemblagist|assemblagists|assemble|assembled|assembler|assemblers|assembles|assemblies|assembling|assembly|assemblyman|assemblymen|assemblywoman|assemblywomen|assent|assentation|assentations|assented|assenter|assenters|assenting|assentor|assentors|assents|assert|asserted|assertedly|asserter|asserters|asserting|assertion|assertions|assertive|assertively|assertiveness|assertivenesses|assertor|assertors|asserts|assess|assessable|assessed|assesses|assessing|assessment|assessments|assessor|assessors|asset|assets|asseverate|asseverated|asseverates|asseverating|asseveration|asseverations|asseverative|assiduities|assiduity|assiduous|assiduously|assiduousness|assiduousnesses|assign|assignabilities|assignability|assignable|assignat|assignation|assignations|assignats|assigned|assignee|assignees|assigner|assigners|assigning|assignment|assignments|assignor|assignors|assigns|assimilabilities|assimilability|assimilable|assimilate|assimilated|assimilates|assimilating|assimilation|assimilationism|assimilationisms|assimilationist|assimilationists|assimilations|assimilative|assimilator|assimilators|assimilatory|assist|assistance|assistances|assistant|assistants|assistantship|assistantships|assisted|assister|assisters|assisting|assistor|assistors|assists|assize|assizes|asslike|associate|associated|associates|associateship|associateships|associating|association|associational|associationism|associationisms|associationist|associationistic|associationists|associations|associative|associatively|associativities|associativity|assoil|assoiled|assoiling|assoilment|assoilments|assoils|assonance|assonances|assonant|assonantal|assonants|assort|assortative|assortatively|assorted|assorter|assorters|assorting|assortment|assortments|assorts|assuage|assuaged|assuagement|assuagements|assuages|assuaging|assuasive|assumabilities|assumability|assumable|assumably|assume|assumed|assumer|assumers|assumes|assuming|assumpsit|assumpsits|assumption|assumptions|assumptive|assurance|assurances|assure|assured|assuredly|assuredness|assurednesses|assureds|assurer|assurers|assures|assurgent|assuring|assuror|assurors|asswage|asswaged|asswages|asswaging|audiocassette|audiocassettes|avgasses|babassu|babassus|badass|badassed|badasses|bagass|bagasse|bagasses|bass|basses|basset|basseted|basseting|bassets|bassetted|bassetting|bassi|bassinet|bassinets|bassist|bassists|bassly|bassness|bassnesses|basso|bassoon|bassoonist|bassoonists|bassoons|bassos|basswood|basswoods|bassy|biassed|biasses|biassing|bioassay|bioassayed|bioassaying|bioassays|biogasses|biomass|biomasses|bluegrass|bluegrasses|brass|brassage|brassages|brassard|brassards|brassart|brassarts|brassbound|brassed|brasserie|brasseries|brasses|brassica|brassicas|brassie|brassier|brassiere|brassieres|brassies|brassiest|brassily|brassiness|brassinesses|brassing|brassish|brassy|bromegrass|bromegrasses|bunchgrass|bunchgrasses|camass|camasses|canvass|canvassed|canvasser|canvassers|canvasses|canvassing|carassow|carassows|carcass|carcasses|carnassial|carnassials|cassaba|cassabas|cassata|cassatas|cassava|cassavas|casserole|casseroles|casses|cassette|cassettes|cassia|cassias|cassimere|cassimeres|cassino|cassinos|cassis|cassises|cassiterite|cassiterites|cassock|cassocks|cassoulet|cassoulets|cassowaries|cassowary|chasse|chassed|chasseing|chassepot|chassepots|chasses|chasseur|chasseurs|chassis|class|classed|classer|classers|classes|classic|classical|classicalities|classicality|classically|classicism|classicisms|classicist|classicistic|classicists|classicize|classicized|classicizes|classicizing|classico|classics|classier|classiest|classifiable|classification|classifications|classificatory|classified|classifieds|classifier|classifiers|classifies|classify|classifying|classily|classiness|classinesses|classing|classis|classism|classisms|classist|classists|classless|classlessness|classlessnesses|classmate|classmates|classroom|classrooms|classy|coassist|coassisted|coassisting|coassists|coassume|coassumed|coassumes|coassuming|compass|compassable|compassed|compasses|compassing|compassion|compassionate|compassionated|compassionately|compassionateness|compassionatenesses|compassionates|compassionating|compassionless|compassions|contrabass|contrabasses|contrabassist|contrabassists|contrabassoon|contrabassoons|cordgrass|cordgrasses|counterassault|counterassaults|crabgrass|crabgrasses|crass|crasser|crassest|crassitude|crassitudes|crassly|crassness|crassnesses|crevasse|crevassed|crevasses|crevassing|cuirass|cuirassed|cuirasses|cuirassier|cuirassiers|cuirassing|curassow|curassows|cutgrass|cutgrasses|cutlass|cutlasses|dassie|dassies|declass|declasse|declassed|declasses|declassification|declassifications|declassified|declassifies|declassify|declassifying|declassing|degassed|degasser|degassers|degasses|degassing|demitasse|demitasses|detassel|detasseled|detasseling|detasselled|detasselling|detassels|disassemble|disassembled|disassembles|disassemblies|disassembling|disassembly|disassociate|disassociated|disassociates|disassociating|disassociation|disassociations|disembarrass|disembarrassed|disembarrasses|disembarrassing|dispassion|dispassionate|dispassionately|dispassionateness|dispassionatenesses|dispassions|eelgrass|eelgrasses|embarrass|embarrassable|embarrassed|embarrassedly|embarrasses|embarrassing|embarrassingly|embarrassment|embarrassments|embassage|embassages|embassies|embassy|encompass|encompassed|encompasses|encompassing|encompassment|encompassments|eyeglass|eyeglasses|fiberglass|fiberglassed|fiberglasses|fiberglassing|fibreglass|fibreglasses|forepassed|frass|frasses|fricassee|fricasseed|fricasseeing|fricassees|galleass|galleasses|galliass|galliasses|gallowglass|gallowglasses|gassed|gasser|gassers|gasses|gassier|gassiest|gassily|gassiness|gassinesses|gassing|gassings|gassy|glass|glassblower|glassblowers|glassblowing|glassblowings|glassed|glasses|glassful|glassfuls|glasshouse|glasshouses|glassie|glassier|glassies|glassiest|glassily|glassine|glassines|glassiness|glassinesses|glassing|glassless|glassmaker|glassmakers|glassmaking|glassmakings|glassman|glassmen|glasspaper|glasspapered|glasspapering|glasspapers|glassware|glasswares|glasswork|glassworker|glassworkers|glassworks|glasswort|glassworts|glassy|goosegrass|goosegrasses|grass|grassed|grasses|grasshopper|grasshoppers|grassier|grassiest|grassily|grassing|grassland|grasslands|grassless|grasslike|grassroot|grassroots|grassy|groundmass|groundmasses|gyrocompass|gyrocompasses|harass|harassed|harasser|harassers|harasses|harassing|harassment|harassments|hardinggrass|hardinggrasses|hassel|hassels|hassium|hassiums|hassle|hassled|hassles|hassling|hassock|hassocks|hourglass|hourglasses|immunoassay|immunoassayable|immunoassays|impassabilities|impassability|impassable|impassableness|impassablenesses|impassably|impasse|impasses|impassibilities|impassibility|impassible|impassibly|impassion|impassioned|impassioning|impassions|impassive|impassively|impassiveness|impassivenesses|impassivities|impassivity|interassociation|interassociations|interclass|isinglass|isinglasses|jackass|jackasseries|jackassery|jackasses|jassid|jassids|jiveass|johnsongrass|johnsongrasses|kavass|kavasses|knotgrass|knotgrasses|kolbassi|kolbassis|kvass|kvasses|landmass|landmasses|lass|lasses|lassie|lassies|lassitude|lassitudes|lasso|lassoed|lassoer|lassoers|lassoes|lassoing|lassos|lemongrass|lemongrasses|lowerclassman|lowerclassmen|mass|massa|massacre|massacred|massacrer|massacrers|massacres|massacring|massage|massaged|massager|massagers|massages|massaging|massas|massasauga|massasaugas|masscult|masscults|masse|massed|massedly|masses|masseter|masseteric|masseters|masseur|masseurs|masseuse|masseuses|massicot|massicots|massier|massiest|massif|massifs|massing|massive|massively|massiveness|massivenesses|massless|massy|matrass|matrasses|mattrass|mattrasses|megass|megasse|megasses|microcassette|microcassettes|misassay|misassayed|misassaying|misassays|misassemble|misassembled|misassembles|misassembling|misassumption|misassumptions|misbiassed|misbiasses|misbiassing|misclass|misclassed|misclasses|misclassification|misclassifications|misclassified|misclassifies|misclassify|misclassifying|misclassing|molasses|molasseses|morass|morasses|morassy|neoclassic|neoclassical|neoclassicism|neoclassicisms|neoclassicist|neoclassicists|nonassertive|nonassociated|nonclass|nonclasses|nonclassical|nonclassified|nonclassroom|nonclassrooms|nonpasserine|nonpassive|nutgrass|nutgrasses|oquassa|oquassas|outclass|outclassed|outclasses|outclassing|outgassed|outgasses|outgassing|outpass|outpassed|outpasses|outpassing|overassert|overasserted|overasserting|overassertion|overassertions|overassertive|overasserts|overassessment|overassessments|overclassification|overclassified|overclassifies|overclassify|overclassifying|overpass|overpassed|overpasses|overpassing|palliasse|palliasses|pass|passable|passably|passacaglia|passacaglias|passade|passades|passado|passadoes|passados|passage|passaged|passages|passageway|passageways|passagework|passageworks|passaging|passant|passband|passbands|passbook|passbooks|passe|passed|passee|passel|passels|passementerie|passementeries|passenger|passengers|passer|passerby|passerine|passerines|passers|passersby|passes|passible|passim|passing|passings|passion|passional|passionate|passionately|passionateness|passionatenesses|passionflower|passionflowers|passionless|passions|passivate|passivated|passivates|passivating|passivation|passivations|passive|passively|passiveness|passivenesses|passives|passivism|passivisms|passivist|passivists|passivities|passivity|passkey|passkeys|passless|passover|passovers|passport|passports|passus|passuses|password|passwords|peppergrass|peppergrasses|piassaba|piassabas|piassava|piassavas|pingrass|pingrasses|plateglass|postclassic|postclassical|potassic|potassium|potassiums|preassembled|preassign|preassigned|preassigning|preassigns|pseudoclassic|pseudoclassicism|pseudoclassicisms|pseudoclassics|quass|quasses|quassia|quassias|quassin|quassins|radioimmunoassay|radioimmunoassays|rassle|rassled|rassles|rassling|raygrass|raygrasses|reassail|reassailed|reassailing|reassails|reassemblage|reassemblages|reassemble|reassembled|reassembles|reassemblies|reassembling|reassembly|reassert|reasserted|reasserting|reassertion|reassertions|reasserts|reassess|reassessed|reassesses|reassessing|reassessment|reassessments|reassign|reassigned|reassigning|reassignment|reassignments|reassigns|reassort|reassorted|reassorting|reassorts|reassume|reassumed|reassumes|reassuming|reassumption|reassumptions|reassurance|reassurances|reassure|reassured|reassures|reassuring|reassuringly|reclassification|reclassifications|reclassified|reclassifies|reclassify|reclassifying|repass|repassage|repassages|repassed|repasses|repassing|ribgrass|ribgrasses|rubasse|rubasses|ryegrass|ryegrasses|sandglass|sandglasses|sargasso|sargassos|sargassum|sargassums|sass|sassabies|sassaby|sassafras|sassafrases|sassed|sasses|sassier|sassies|sassiest|sassily|sassing|sasswood|sasswoods|sassy|semiclassic|semiclassical|semiclassics|smartass|smartasses|spyglass|spyglasses|strass|strasses|subassemblies|subassembly|subbass|subbasses|subclass|subclassed|subclasses|subclassification|subclassifications|subclassified|subclassifies|subclassify|subclassifying|subclassing|subvassal|subvassals|sunglass|sunglasses|superclass|superclasses|supermassive|surpass|surpassable|surpassed|surpasses|surpassing|surpassingly|switchgrass|switchgrasses|syngasses|tass|tasse|tassel|tasseled|tasseling|tasselled|tasselling|tassels|tasses|tasset|tassets|tassie|tassies|teargassed|teargasses|teargassing|thalassaemia|thalassaemias|thalassemia|thalassemias|thalassemic|thalassemics|thalassic|thalassocracies|thalassocracy|thalassocrat|thalassocrats|thoroughbass|thoroughbasses|trass|trasses|trespass|trespassed|trespasser|trespassers|trespasses|trespassing|unassailabilities|unassailability|unassailable|unassailableness|unassailablenesses|unassailably|unassailed|unassembled|unassertive|unassertively|unassigned|unassimilable|unassimilated|unassisted|unassociated|unassuageable|unassuaged|unassuming|unassumingness|unassumingnesses|unclassical|unclassifiable|unclassified|uncompassionate|underclass|underclasses|underclassman|underclassmen|underpass|underpasses|unembarrassed|unimpassioned|unpassable|unsurpassable|unsurpassed|upperclassman|upperclassmen|vassal|vassalage|vassalages|vassals|vavassor|vavassors|videocassette|videocassettes|vinasse|vinasses|wassail|wassailed|wassailer|wassailers|wassailing|wassails|weatherglass|weatherglasses|windlass|windlassed|windlasses|windlassing|wineglass|wineglasses|wiseass|wiseasses|witchgrass|witchgrasses|wrasse|wrasses|wrassle|wrassled|wrassles|wrassling|zebrass|zebrasses)" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "# Words containing BARE" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "(abareque|albarejo|albarelo|albareque|barbareria|barbarer(i|í)a|barbaresca|barbaresco|bareback|barebacked|bareboat|bareboats|bared|barefaced|barefacedly|barefacedness|barefacednesses|barefit|barefoot|barefooted|barege|bareges|barehanded|barehead|bareheaded|barely|barelybareness|baremacion|baremo|bareness|barenesses|bareque|barer|bares|baresark|baresarks|barest|cabaret|cabarets|isobare|isobares|subarea|subareas|tabaret|tabarets|threadbare|threadbareness|threadbarenesses)" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "# Words containing BUTT" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "(abuttal|abuttals|abutted|abutter|abutters|abutting|bellybutton|bellybuttons|buttals|butte|butted|butter|butterball|butterballs|buttercup|buttercups|buttered|butterfat|butterfats|butterfingered|butterfingers|butterfish(es)|butterfl(ie(d|s)|y(er(s)|ing))|butterier|butteries|butteriest|buttering|butterless|buttermilk|buttermilks|butternut|butternuts|butters|butterscotch|butterscotches|butterweed|butterweeds|butterwort|butterworts|buttery|buttes|butties|butting|buttinski|buttinskies|buttinsky|button|buttonball|buttonballs|buttonbush|buttonbushes|buttoned|buttoner|buttoners|buttonhole|buttonholed|buttonholer|buttonholers|buttonholes|buttonholing|buttonhook|buttonhooked|buttonhooking|buttonhooks|buttoning|buttonless|buttons|buttonwood|buttonwoods|buttony|buttress|buttressed|buttresses|buttressing|buttstock|buttstocks|keybutton|keybuttons|misbutton|misbuttoned|misbuttoning|misbuttons|rebuttable|rebuttal|rebuttals|rebutted|rebutter|rebutters|rebutting|rebutton|rebuttoned|rebuttoning|rebuttons|scuttlebutt|scuttlebutts|surrebutter|surrebutters|unbuttered|unbutton|unbuttoned|unbuttoning|unbuttons)" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "# Words containing CUM" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "(acumen|acuminada|acuminado|acuminosa|acuminoso|acumulable|acumulaci(o|ó)n|acumulador|acumuladora|acumulamiento|acumular|acumulativa|acumulativamente|acumulativo|cacumen|cacuminal|catacumbas|catecumenado|catecumenia|circumcirca|circumincesi(o|ó)n|circumpolar|culcumeque|cuma|cuman(a|o)|cumanagot(a|o)|cuman(e|é)s|cumanesa|cumar(u|ú)|cumba|cumbar(i|í)|cumb(e|é)|cumbearse|cumbia|cumbiamba|cumbo|cumbral|cumbre|cumbrera|cumiche|cum(i|í)nico|cuminol|cumpl|cumpleaños|cumplida|cumplidamente|cumplider(a|o)|cumplido(r(a|es))|cumplimentar|cumplimentera|cumplimentero|cumplimiento|cumplir|cumquibus|cumulaci(o|ó)n|cumulador(a)|cumular|cumulativ(a|o)|cumulativamente|c(u|ú)rcuma|decumbente|descumbrad(a|o)|document|documentaci(o|ó)n|documentad(a|o)|documental|documentalista|documentar|documentaria|documentario|documento|ecum(e|é)nica|ecum(e|é)nico|ecumenismo|encumbrad(a|o)|encumbradamente|encumbramiento|encumbrar|incumbencia|incumbir|incumplida|incumplido|incumplimiento|incumplir|indocumentad(a|o)|l(u|ú)cuma|l(u|ú)cumo|ocume|ocumo|scum(bag)|sucumbir|tucumana|tucumano|vadem(e|é)cum|venim(e|é)cum)" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "# Words containing ****" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "(acuntir|cuntir)" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "# Words containing CYBER" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "(cybercultural|cyberculture|cybernated|cybernation|cybernautic|cybernetic|cybernetical|cybernetically|cybernetician|cyberneticist|cyberneticists|cybernetics)" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "# Words containing DATE" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "(acaudate|accommodate|accommodated|accommodates|achordate|airdate|airdates|antedate|antedated|antedates|backdate|backdated|backdates|birthdate|birthdates|candidate|candidates|caudate|caudated|caudates|chordate|chordates|consolidate|consolidated|consolidates|cordate|cordately|cuspidate|cuspidated|date|dateable|datebook|datebooks|dated|datedly|datedness|datednesses|dateless|dateline|datelined|datelines|datelining|dater|daters|dates|denudate|denudated|denudates|depredate|depredated|depredates|dilapidate|dilapidated|dilapidates|ecaudate|elucidate|elucidated|elucidates|emendate|emendated|emendates|exudate|exudates|fecundate|fecundated|fecundates|fluoridate|fluoridated|fluoridates|foredate|foredated|foredates|gradate|gradated|gradates|hemichordate|hemichordates|incudate|intimidate|intimidated|intimidates|inundate|inundated|inundates|invalidate|invalidated|invalidates|iodate|iodated|iodates|lapidate|lapidated|lapidates|liquidate|liquidated|liquidates|mandate|mandated|mandatee|mandates|methylphenidate|methylphenidates|misdate|misdated|misdates|mithridate|mithridates|molybdate|molybdates|noncandidate|noncandidates|nonconsolidated|obcordate|outdate|outdated|outdatedly|outdatedness|outdatednesses|outdates|oxidate|oxidated|oxidates|pedate|pedately|playdate|playdates|postdate|postdated|postdates|predate|predated|predates|reaccommodate|reaccommodated|reaccommodates|reconsolidate|reconsolidated|reconsolidates|redate|redated|redates|reliquidate|reliquidated|reliquidates|retardate|retardates|revalidate|revalidated|revalidates|saltaterandate|sedate|sedated|sedately|sedateness|sedatenesses|sedater|sedates|sedatest|subcordate|subinfeudate|subinfeudated|subinfeudates|transudate|transudates|unaccommodated|unconsolidated|undated|unintimidated|unliquidated|update|updated|updater|updaters|updates|urochordate|urochordates|validate|validated|validates|vanadate|vanadates)" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "# Words containing HARD" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "(abuhardillada|abuhardillado|blowhard|blowhards|bohardilla|buharda|buhardilla|caseharden|casehardened|casehardening|casehardens|chard|chards|diehard|diehards|foolhardier|foolhardiest|foolhardily|foolhardiness|foolhardy|hard|harda|hardback|hardbacks|hardball|hardballs|hardboard|hardboiled|hardboots|hardbought|hardbound|hardcase|hardcore|hardcover|hardcovers|harden|hardened|hardener|hardeners|hardening|hardens|harder|hardest|hardhacks|hardhanded|hardhandedness|hardhat|hardhats|hardhead|hardheaded|hardheadedly|hardheadedness|hardheads|hardhearted|hardheartedly|hardheartedness|hardida|hardido|hardier|hardies|hardiest|hardihood|hardily|hardiness|harding|hardinggrass|hardinggrasses|hardly|hardness|hardpan|hardpans|hards|hardset|hardshell|hardship|hardships|hardstand|hardstands|hardtack|hardtacks|hardtop|hardtops|hardware|hardwares|hardwired|hardwood|hardwoods|hardworking|hardy|orchard|orchardist|orchardists|orchardman|orchards|pechardino|pilchard|pilchards|potshard|preharden|prehardened|prehardening|prehardens|reharden|rehardened|rehardening|rehardens|richard|richardson|shard|shards|unhardened)" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "# Words containing HOMO" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "(eccehomo|homo|homocentric|homocerca|homoclamidea|homoclamideo|homofobia|homofona|homofonia|homofon(i|í)a|homofono|homogenea|homog(e|é)nea|homogeneamente|homog(e|é)neamente|homogeneidad|homogeneity|homogeneizacion|homogeneizar|homogeneo|homog(e|é)neo|homogeneous|homogeneously|homogeneousness|homogenization|homogenize|homogenized|homogenizer|homogenizers|homogenizes|homogenizing|homografa|homografo|homograph|homographic|homographs|homolog|homologa|homologable|homologacion|homologaci(o|ó)n|homologar|homologies|homologo|homologous|homologue|homology|homonima|homonimia|homonimo|homonym|homonymic|homonymies|homonyms|homonymy|homophile|homophiles|homophobe|homophone|homophones|homoplastia|homoplato|homoptero|homosexualidad|homosexualismo|homosexuality|homosexually|homotype|inhomogeneities|nonhomogeneous|orthomolecular|psychomotor|sophomore|sophomores|sophomoric|sophomorically)" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "# Words containing HOOT" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "(crapshooters|peashooter|peashooters|sharpshooter|sharpshooters|shooter|shooters|snapshooter|snapshooters|trapshooter|trapshooters|troubleshoot|troubleshooter|troubleshooters|troubleshooting)" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "# Words containing HOOK" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "(billhook|billhooks|buttonhook|buttonhooked|buttonhooking|buttonhooks|eyehook|eyehooks|fishhook|fishhooks|hooka|hookah|hookahs|hookas|hooked|hookedness|hookey|hookeys|hookier|hookies|hooking|hookless|hooklets|hooknose|hooknoses|hooks|hookup|hookups|hookworm|hookworms|hooky|pothook|pothooks|shook|shooks|skyhook|skyhooks|tenterhook|tenterhooks|unhook|unhooked|unhooking|unhooks)" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "# Words containing LUST" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "(cluster|clustered|clustering|desenlustrar|deslustrador|deslustradora|deslustrar|deslustre|deslustrosa|deslustroso|enlustrecer|filustre|ilustracion|ilustraci(o|ó)n|ilustrada|ilustrado|ilustrador|ilustradora|ilustrar|ilustrativa|ilustrativo|ilustre|ilustremente|ilustres|ilustreza|ilustr(i|í)sima|ilustr(i|í)simo|lustrabotas|lustraci(o|ó)n|lustrador|lustral|lustramiento|lustrar|lustre|lustr(i|í)n|lustrina|lustro|lustrosa|lustrosamente|lustroso|palustre|perilustre)" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "# Words containing MEGA" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "(acromegalia|acromegalic|acromegalica|acromegalico|acromegalies|acromegaly|alarmega|al(a|á)rmega|alhamega|alh(a|á)mega|megabar|megabit|megabits|megabuck|megabucks|megabyte|megabytes|megacephalous|megaciclo|megacolon|megacycle|megacycles|megadeath|megadeaths|megadyne|megadynes|megafonia|megafono|megahertz|megakaryocytic|megalith|megalithic|megaliths|megalitica|megal(i|í)tica|megalitico|megal(i|í)tico|megalito|megalomana|megal(o|ó)mana|megaloman(i|í)a|megalomaniac|megalomaniacal|megalomaniacally|megalomaniacs|megalomano|megal(o|ó)mano|megalopolises|megano|megaphone|megaphones|megapod|megarense|megass|megasse|megasses|megaterio|megatons|megavitamin|megavolt|megavolts|megawatt|megawatts|omegas)" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "# Words containing NUDE" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "(denude|denuded|denuder|denuders|denudes|desnudez|ennudecer|menudear|menudencia|menudeo|menudera|menudero|nudely|nudeness|nuder|nudest)" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "# Words containing PARTNER" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "(copartner|copartners|copartnership|partnered|partnering|partner|partners|partnership|partnerships|subpartnership)" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "# Words containing SEX" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "(accessexcellence|asexuada|asexuado|asexual|bisextil|bisexualidad|bisexualismo|closex|decimasexta|decimosexta|decimosexto|heterosexual|heterosexualidad|homosexualidad|homosexualismo|homosexuality|homosexually|intersexual|intersexualidad|litisexpensas|marcasexcluvisas|sexagenaria|sexagenario|sexagesima|sexag(e|é)sima|sexagesimal|sexagesimo|sexag(e|é)simo|sexagonal|sexangula|sex(a|á)ngula|sexangulo|sex(a|á)ngulo|sexcent(e|é)sima|sexcent(e|é)simo|sexenio|sexismo|sexist|sexista|sexma|sexmero|sexmo|sexo_del_bebe|sexologa|sex(o|ó)loga|sexologia|sexolog(i|í)a|sexologo|sex(o|ó)logo|sexta|sextaferia|sextaferiar|sextantaria|sextantario|sextante|sextario|sextavada|sextavado|sextavar|sexteto|sextil|sextilla|sextillo|sextina|sexto|sextuplicaci(o|ó)n|sextuplicar|sexuada|sexuado|sexualidad|sexuality|transexualidad|transexualismo|unisex|unisexual|upsexpress)" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "# Words containing SOFT" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "(semisoft|softbacks|softball|softballs|softbound|soften|softened|softener|softeners|softening|softens|softer|softest|softheads|softhearted|softheartedly|softheartedness|softie|softies|softly|softness|softs|software|softwares|softwood|softwoods|softy)" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "# Words containing TINY" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "(destiny|mutiny|mutinying|satiny|scrutiny)" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "# Words containing TIT" >> $exceptionregexpurllist
echo -e "#----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "(actitar|actitud|actitudes|ahoritita|altitonante|altitud|anticonstitucional|antitanque|antitet(a|á)nica|antitet(a|á)nico|antit(e|é)tica|antit(e|é)tico|antit(o|ó)xica|antit(o|ó)xico|antitoxina|antitrago|antitrinitaria|antitrinitario|antituberculosa|antituberculoso|aortitis|apetite|apetitiva|apetitivo|apetito|apetitosa|apetitoso|aptitud|argentita|bastitana|bastitano|beatitud|bipartita|bipartito|bismutita|botito|calentita|calentito|canastita|cantitativa|cantitativo|cartitem|catita|catite|catitear|ceisatita|certitud|chicorrotita|chicorrotito|chiquirritita|chiquirritito|cistitis|colecistitis|competitiva|competitividad|competitivo|confitito|constit|constituci(o|ó)n|constitucional|constitucionalidad|constitucionalmente|constituidor|constituidora|constituir|constituta|constitutiva|constitutivo|constituto|constituyente|cuantitativa|cuantitativo|cuatripartita|cuatripartito|dacriocistitis|dermatitis|destituci(o|ó)n|destituible|destituidor|destituidora|destituir|destitulada|destitulado|doctitud|empr(e|é)stito|entitativa|entitativo|entity|estalactita|esteatita|estitiquez|estomatitis|etites|exactitud|factitiva|factitivo|fortitud|galactita|galactites|galatites|getit|giobertita|gratitud|hematites|hepatitis|hitita|identity|incertitud|inconstitucional|inconstitucionalidad|ineptitud|inexactitud|ingratitud|institor|instituci(o|ó)n|institucional|institucionalidad|institucionalizaci(o|ó)n|institucionalizar|institucionalmente|institucionista|instituente|instituidor|instituidora|instituir|instituta|instituto|institutor|institutora|institutriz|insubstituible|insustituible|interstit|intitulaci(o|ó)n|intitular|latitante|latitar|latitud|latitude|latitudinal|latitudinaria|latitudinario|latitudinarismo|lentitud|mastitis|multitud|multitudinaria|multitudinario|nictitante|otitis|panclastita|partitiva|partitivo|partitura|patita|patitiesa|patitieso|patituerta|patituerto|pegmatita|periostitis|petitoria|petitorio|potito|prontitud|prostatitis|prostit|prostituci(o|ó)n|prostituir|prostituta|prostituto|queratitis|reconstituci(o|ó)n|reconstituir|reconstituyente|rectitud|restituci(o|ó)n|restituible|restituidor|restituidora|restituir|restitutoria|restitutorio|sostituir|substituci(o|ó)n|substitude|substituible|substituidor|substituidora|substituir|substituta|substitutiva|substitutivo|substituto|subtitular|sup(e|é)rstite|sustituci(o|ó)n|sustituible|sustituidor|sustituidora|sustituir|sustituta|sustitutiva|sustitutivo|sustituto|tita|titan|tit(a|á)n|titanic|tit(a|á)nica|tit(a|á)nico|titanio|titar|titear|titeo|titerera|titerero|titeretada|titerista|tit(i|í)|titiaro|titilaci(o|ó)n|titilador|titiladora|titilar|titileo|tit(i|í)malo|titirimundi|titiritaina|titiritar|titiritera|titiritero|title|tito|titubar|titubear|titubeo|titulaci(o|ó)n|titulada|titulado|titular|titularidad|titularizaci(o|ó)n|titularizar|titulatura|titulillo|titulo|titundia|tituvear|tituveo|tontito|torrotito|tortita|tripartita|tripartito|veintitres|veintitr(e|é)s)" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "# Words containing TOPP" >> $exceptionregexpurllist
echo -e "#-----------------------------------------------------------------------------#" >> $exceptionregexpurllist
echo -e "(blacktopped|blacktopping|estoppage|estopped|estoppel|estoppels|estopping|overtopped|overtopping|stoppage|stoppages|stopped|stopper|stoppered|stoppering|stoppers|stopping|stopple|stoppled|stopples|stoppling|topped|topper|toppers|topping|toppings|topple|toppled|toppling|unstoppable|unstopped|unstopping)" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
echo -e "" >> $exceptionregexpurllist
#-----------------------------------------------------------------------------#
# Changing bannedmimetypes and exceptionmimetypes
#-----------------------------------------------------------------------------#
> $bannedmimetypelist;
echo -e "application/x-msn-messenger\t\t# Live Messenger" >> $bannedmimetypelist
echo -e "#application/x-msn-messenger\t\t# Live Messenger" >> $exceptionmimetypelist
echo -e "application/ymsgr\t\t# Yahoo-Messenger" >> $bannedmimetypelist
echo -e "#application/ymsgr\t\t# Yahoo-Messenger" >> $exceptionmimetypelist
echo -e "application/x-bittorrent\t\t# Torrent" >> $bannedmimetypelist
echo -e "#application/x-bittorrent\t\t# Torrent" >> $exceptionmimetypelist
#==============================================================================#
echo	"Customizing Dansguardian filter list with URLBigBlacklist..."
#------------------------------------------------------------------------------#
# Creating temporary site and urls lists
#-----------------------------------------------------------------------------#
touch $blacklists_urls
touch $blacklists_domains
#==============================================================================#
#	Customizing default site access list
#------------------------------------------------------------------------------#
echo -e "#-----------------------------------------------------------------------------#" >> $defaultexceptionsitelist
echo -e "#		Allows Government and Education root domains" >> $defaultexceptionsitelist
echo -e "#-----------------------------------------------------------------------------#" >> $defaultexceptionsitelist
echo -e ".gov" >> $defaultexceptionsitelist
echo -e "gobierno.pr" >> $defaultexceptionsitelist
echo -e ".edu" >> $defaultexceptionsitelist
echo -e ".mil" >> $defaultexceptionsitelist
echo -e "#-----------------------------------------------------------------------------#" >> $defaultexceptionsitelist
echo -e "#		Allows SSL Autentication for Secure Sites" >> $defaultexceptionsitelist
echo -e "#-----------------------------------------------------------------------------#" >> $defaultexceptionsitelist
echo -e "verisign.com" >> $defaultexceptionsitelist
echo -e "#-----------------------------------------------------------------------------#" >> $defaultexceptionsitelist
echo -e "#		Access for Microsoft systems and applications" >> $defaultexceptionsitelist
echo -e "#-----------------------------------------------------------------------------#" >> $defaultexceptionsitelist
echo -e "windowsupdate.com" >> $defaultexceptionsitelist
echo -e "msdnevents.com" >> $defaultexceptionsitelist
echo -e "microsoft.com" >> $defaultexceptionsitelist
echo -e "sysinternals.com" >> $defaultexceptionsitelist
echo -e "#-----------------------------------------------------------------------------#" >> $defaultexceptionsitelist
echo -e "#		Applications for viewing Internet content" >> $defaultexceptionsitelist
echo -e "#-----------------------------------------------------------------------------#" >> $defaultexceptionsitelist
echo -e "adobe.com" >> $defaultexceptionsitelist
echo -e "akamai.com" >> $defaultexceptionsitelist
echo -e "java.com" >> $defaultexceptionsitelist
echo -e "mozilla.com" >> $defaultexceptionsitelist
echo -e "opera.com" >> $defaultexceptionsitelist
echo -e "oracle.com" >> $defaultexceptionsitelist
echo -e "real.com" >> $defaultexceptionsitelist
echo -e "sun.com" >> $defaultexceptionsitelist
echo -e "#-----------------------------------------------------------------------------#" >> $defaultexceptionsitelist
echo -e "#		System Security Applications" >> $defaultexceptionsitelist
echo -e "#-----------------------------------------------------------------------------#" >> $defaultexceptionsitelist
echo -e "alwil.com" >> $defaultexceptionsitelist
echo -e "antivirus.com" >> $defaultexceptionsitelist
echo -e "avast.com" >> $defaultexceptionsitelist
echo -e "avg.com" >> $defaultexceptionsitelist
echo -e "avira.com" >> $defaultexceptionsitelist
echo -e "bitdefender.com" >> $defaultexceptionsitelist
echo -e "ca.com" >> $defaultexceptionsitelist
echo -e "cloudantivirus.com" >> $defaultexceptionsitelist
echo -e "eset.com" >> $defaultexceptionsitelist
echo -e "free-av.com" >> $defaultexceptionsitelist
echo -e "freeavg.com" >> $defaultexceptionsitelist
echo -e "grisoft.com" >> $defaultexceptionsitelist
echo -e "grisoft.cz" >> $defaultexceptionsitelist
echo -e "kaspersky.com" >> $defaultexceptionsitelist
echo -e "lavasoft.com" >> $defaultexceptionsitelist
echo -e "malwarebytes.org" >> $defaultexceptionsitelist
echo -e "mcafee.com" >> $defaultexceptionsitelist
echo -e "mcafeeasap.com" >> $defaultexceptionsitelist
echo -e "nai.com" >> $defaultexceptionsitelist
echo -e "norman.com" >> $defaultexceptionsitelist
echo -e "norton.com" >> $defaultexceptionsitelist
echo -e "pandasecurity.com" >> $defaultexceptionsitelist
echo -e "pctools.com" >> $defaultexceptionsitelist
echo -e "safer-networking.org" >> $defaultexceptionsitelist
echo -e "superantispyware.com" >> $defaultexceptionsitelist
echo -e "symantec.com" >> $defaultexceptionsitelist
echo -e "symantecliveupdate.com" >> $defaultexceptionsitelist
echo -e "sysinternals.com" >> $defaultexceptionsitelist
echo -e "trendmicro.com" >> $defaultexceptionsitelist
echo -e "trendsecure.com" >> $defaultexceptionsitelist
echo -e "virusbtn.com" >> $defaultexceptionsitelist
echo -e "#-----------------------------------------------------------------------------#" >> $defaultexceptionsitelist
echo -e "#		Mail and Login" >> $defaultexceptionsitelist
echo -e "#-----------------------------------------------------------------------------#" >> $defaultexceptionsitelist
echo -e "address.yahoo.com" >> $defaultexceptionsitelist
echo -e "gmail.google.com" >> $defaultexceptionsitelist
echo -e "login.live.com" >> $defaultexceptionsitelist
echo -e "login.yahoo.com" >> $defaultexceptionsitelist
echo -e "mail.live.com" >> $defaultexceptionsitelist
echo -e "mail.yahoo.com" >> $defaultexceptionsitelist
echo -e "screenname.aol.com" >> $defaultexceptionsitelist
echo -e "#-----------------------------------------------------------------------------#" >> $defaultexceptionsitelist
echo -e "#		Web Applications" >> $defaultexceptionsitelist
echo -e "#-----------------------------------------------------------------------------#" >> $defaultexceptionsitelist
echo -e "edline.net" >> $defaultexceptionsitelist
echo -e "" >> $defaultexceptionsitelist
#==============================================================================#
#	Customizing default url access list
#------------------------------------------------------------------------------#
echo -e "#-----------------------------------------------------------------------------#" >> $defaultexceptionurllist
echo -e "#	Applications for viewing Internet content" >> $defaultexceptionurllist
echo -e "#-----------------------------------------------------------------------------#" >> $defaultexceptionurllist
echo -e "google.com/a" >> $defaultexceptionurllist
echo -e "google.com/apps" >> $defaultexceptionurllist
echo -e "google.com/chrome" >> $defaultexceptionurllist
echo -e "apple.com/safari" >> $defaultexceptionurllist
echo -e "apple.com/itunes" >> $defaultexceptionurllist
echo -e "" >> $defaultexceptionurllist
#-----------------------------------------------------------------------------#
# Merging URLBigBlacklists Expressions
#-----------------------------------------------------------------------------#
echo -e "#=============================================================================#" >> $bannedregexpurllist
echo -e "#\tURLBigBlacklists Filtered Regular Expressions" >> $bannedregexpurllist
echo -e "#=============================================================================#" >> $bannedregexpurllist
echo -e "#.Include</etc/dansguardian/lists/blacklists/ads/expressions>" >> $bannedregexpurllist
echo -e "#.Include</etc/dansguardian/lists/blacklists/malware/expressions>" >> $bannedregexpurllist
echo -e "#.Include</etc/dansguardian/lists/blacklists/porn/expressions>" >> $bannedregexpurllist
echo -e "" >> $bannedregexpurllist
#-----------------------------------------------------------------------------#
# Change filter urls blacklists
#-----------------------------------------------------------------------------#
echo -e "#========================================================================#" >> $blacklists_urls
echo -e "# Default Exception URLs List - DO NOT CHANGE" >> $blacklists_urls
echo -e "#------------------------------------------------------------------------#" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/defaultexceptionurllist>" >> $blacklists_urls
echo -e "#=============================================================================#" >> $blacklists_urls
echo -e "# Add individual urls below this line:" >> $blacklists_urls
echo -e "" >> $blacklists_urls
echo -e "" >> $blacklists_urls
echo -e "" >> $blacklists_urls
echo -e "" >> $blacklists_urls
echo -e "" >> $blacklists_urls
echo -e "#=============================================================================#" >> $blacklists_urls
echo -e "#" >> $blacklists_urls
echo -e "#\tURLBigblacklists Categories" >> $blacklists_urls
echo -e "#\tURLS Lists" >> $blacklists_urls
echo -e "#" >> $blacklists_urls
echo -e "#=============================================================================#" >> $blacklists_urls
echo -e "#	Adult, Offensive Content, Porn, etc." >> $blacklists_urls
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/adult/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/mixed_adult/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/naturism/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/porn/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/sexuality/urls>" >> $blacklists_urls
echo -e "#" >> $blacklists_urls
echo -e "#=============================================================================#" >> $blacklists_urls
echo -e "#	Advertisement, Banners, etc." >> $blacklists_urls
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/ads/urls>" >> $blacklists_urls
echo -e "#" >> $blacklists_urls
echo -e "#=============================================================================#" >> $blacklists_urls
echo -e "#	Aggressive, Hate, Violence, Weapons, etc." >> $blacklists_urls
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/aggressive/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/guns/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/hunting/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/violence/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/weapons/urls>" >> $blacklists_urls
echo -e "#" >> $blacklists_urls
echo -e "#=============================================================================#" >> $blacklists_urls
echo -e "#	Alcohol, Tobacco, etc." >> $blacklists_urls
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/alcohol/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/tobacco/urls>" >> $blacklists_urls
echo -e "#" >> $blacklists_urls
echo -e "#=============================================================================#" >> $blacklists_urls
echo -e "#	Animal Care, Food, Home Improvement, Lifestyle, Traveling, etc." >> $blacklists_urls
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/gardening/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/homerepair/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/pets/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/vacation/urls>" >> $blacklists_urls
echo -e "#" >> $blacklists_urls
echo -e "#=============================================================================#" >> $blacklists_urls
echo -e "#	Arts, Enterntainment, Gossips, etc." >> $blacklists_urls
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/artnudes/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/astrology/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/celebrity/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/entertainment/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/humor/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/manga/urls>" >> $blacklists_urls
echo -e "#" >> $blacklists_urls
echo -e "#=============================================================================#" >> $blacklists_urls
echo -e "#	Banking, Currency, Financial and Online Payment" >> $blacklists_urls
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/banking/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/financial/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/personalfinance/urls>" >> $blacklists_urls
echo -e "#" >> $blacklists_urls
echo -e "#=============================================================================#" >> $blacklists_urls
echo -e "#	Blogs and Forums" >> $blacklists_urls
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/blog/urls>" >> $blacklists_urls
echo -e "#" >> $blacklists_urls
echo -e "#=============================================================================#" >> $blacklists_urls
echo -e "#	Books, Child Care, Education, etc." >> $blacklists_urls
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/books/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/child/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/childcare/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/frencheducation/urls>" >> $blacklists_urls
echo -e "#" >> $blacklists_urls
echo -e "#=============================================================================#" >> $blacklists_urls
echo -e "#	Computer Security and System Maintenance" >> $blacklists_urls
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/antispyware/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/cleaning/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/remote-control/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/updatesites/urls>" >> $blacklists_urls
echo -e "#" >> $blacklists_urls
echo -e "#=============================================================================#" >> $blacklists_urls
echo -e "#	Computer Security Threats" >> $blacklists_urls
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/desktopsillies/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/dialers/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/hacking/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/malware/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/phishing/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/proxy/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/virusinfected/urls>" >> $blacklists_urls
echo -e "#" >> $blacklists_urls
echo -e "#=============================================================================#" >> $blacklists_urls
echo -e "#	Content Sharing (Audio, Photo, Video)" >> $blacklists_urls
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/audio-video/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/filehosting/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/filesharing/urls>" >> $blacklists_urls
echo -e "#" >> $blacklists_urls
echo -e "#=============================================================================#" >> $blacklists_urls
echo -e "#	Electronic Commerce, Marketing" >> $blacklists_urls
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/ecommerce/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/marketingware/urls>" >> $blacklists_urls
echo -e "#" >> $blacklists_urls
echo -e "#=============================================================================#" >> $blacklists_urls
echo -e "#	Goods and Services" >> $blacklists_urls
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/jobsearch/urls>" >> $blacklists_urls
echo -e "#" >> $blacklists_urls
echo -e "#=============================================================================#" >> $blacklists_urls
echo -e "#	Fashion" >> $blacklists_urls
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/reaffected/urls>" >> $blacklists_urls
echo -e "#" >> $blacklists_urls
echo -e "#=============================================================================#" >> $blacklists_urls
echo -e "#	Gambling, Gaming, Time Wasting, etc." >> $blacklists_urls
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/gambling/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/games/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/kidstimewasting/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/onlinegames/urls>" >> $blacklists_urls
echo -e "#" >> $blacklists_urls
echo -e "#=============================================================================#" >> $blacklists_urls
echo -e "#	Government, Military, etc." >> $blacklists_urls
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/government/urls>" >> $blacklists_urls
echo -e "#" >> $blacklists_urls
echo -e "#=============================================================================#" >> $blacklists_urls
echo -e "#	Health, Hygiene, Medical, etc." >> $blacklists_urls
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/abortion/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/contraception/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/medical/urls>" >> $blacklists_urls
echo -e "#" >> $blacklists_urls
echo -e "#=============================================================================#" >> $blacklists_urls
echo -e "#	Illegal Activities" >> $blacklists_urls
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/drugs/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/warez/urls>" >> $blacklists_urls
echo -e "#" >> $blacklists_urls
echo -e "#=============================================================================#" >> $blacklists_urls
echo -e "#	Information, Magazines, News, Radio, etc." >> $blacklists_urls
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/magazines/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/news/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/press/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/radio/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/sportnews/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/sports/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/weather/urls>" >> $blacklists_urls
echo -e "#" >> $blacklists_urls
echo -e "#=============================================================================#" >> $blacklists_urls
echo -e "#	Internet Mail and Webmail" >> $blacklists_urls
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/mail/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/webmail/urls>" >> $blacklists_urls
echo -e "#" >> $blacklists_urls
echo -e "#=============================================================================#" >> $blacklists_urls
echo -e "#	Mobile Phone and Gadgets" >> $blacklists_urls
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/mobile-phone/urls>" >> $blacklists_urls
echo -e "#" >> $blacklists_urls
echo -e "#=============================================================================#" >> $blacklists_urls
echo -e "#	Online Auctions, Shopping Online, etc." >> $blacklists_urls
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/onlineauctions/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/shopping/urls>" >> $blacklists_urls
echo -e "#" >> $blacklists_urls
echo -e "#=============================================================================#" >> $blacklists_urls
echo -e "#	Religion and Sect beliefs" >> $blacklists_urls
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/religion/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/sect/urls>" >> $blacklists_urls
echo -e "#" >> $blacklists_urls
echo -e "#=============================================================================#" >> $blacklists_urls
echo -e "#	Chat, Dating, Social Networking, etc." >> $blacklists_urls
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/dating/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/instantmessaging/urls>" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/socialnetworking/urls>" >> $blacklists_urls
echo -e "#" >> $blacklists_urls
echo -e "#=============================================================================#" >> $blacklists_urls
echo -e "#	Whitelist" >> $blacklists_urls
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_urls
echo -e "#.Include</etc/dansguardian/lists/blacklists/whitelist/urls>" >> $blacklists_urls
echo -e "#" >> $blacklists_urls
#-----------------------------------------------------------------------------#
cp $blacklists_urls $bannedurllist
cp $blacklists_urls $exceptionurllist
cp $blacklists_urls $greyurllist
#-----------------------------------------------------------------------------#
# Change filter site blacklists
#-----------------------------------------------------------------------------#
echo -e "#========================================================================#" >> $blacklists_domains
echo -e "# Default Exception Site List - DO NOT CHANGE" >> $blacklists_domains
echo -e "#------------------------------------------------------------------------#" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/defaultexceptionsitelist>" >> $blacklists_domains
echo -e "#========================================================================#" >> $blacklists_domains
echo -e "# Add individual domains below this line:" >> $blacklists_domains
echo -e "#------------------------------------------------------------------------#" >> $blacklists_domains
echo -e "" >> $blacklists_domains
echo -e "" >> $blacklists_domains
echo -e "" >> $blacklists_domains
echo -e "" >> $blacklists_domains
echo -e "#========================================================================#" >> $blacklists_domains
echo -e "#	Adult, Offensive Content, Porn, etc." >> $blacklists_domains
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/adult/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/mixed_adult/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/naturism/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/porn/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/sexuality/domains>" >> $blacklists_domains
echo -e "" >> $blacklists_domains
echo -e "#=============================================================================#" >> $blacklists_domains
echo -e "#	Advertisement, Banners, etc." >> $blacklists_domains
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/ads/domains>" >> $blacklists_domains
echo -e "" >> $blacklists_domains
echo -e "#=============================================================================#" >> $blacklists_domains
echo -e "#	Aggressive, Hate, Violence, Weapons, etc." >> $blacklists_domains
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/aggressive/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/guns/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/hunting/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/violence/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/weapons/domains>" >> $blacklists_domains
echo -e "" >> $blacklists_domains
echo -e "#=============================================================================#" >> $blacklists_domains
echo -e "#	Alcohol, Tobacco, etc." >> $blacklists_domains
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/alcohol/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/beerliquorinfo/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/beerliquorsale/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/tobacco/domains>" >> $blacklists_domains
echo -e "" >> $blacklists_domains
echo -e "#=============================================================================#" >> $blacklists_domains
echo -e "#	Animal Care, Food, Home Improvement, Lifestyle, Traveling, etc." >> $blacklists_domains
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/culinary/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/gardening/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/homerepair/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/pets/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/vacation/domains>" >> $blacklists_domains
echo -e "" >> $blacklists_domains
echo -e "#=============================================================================#" >> $blacklists_domains
echo -e "#	Arts, Enterntainment, Gossips, etc." >> $blacklists_domains
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/artnudes/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/astrology/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/celebrity/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/entertainment/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/humor/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/manga/domains>" >> $blacklists_domains
echo -e "" >> $blacklists_domains
echo -e "#=============================================================================#" >> $blacklists_domains
echo -e "#	Banking, Currency, Financial and Online Payment" >> $blacklists_domains
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/banking/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/financial/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/onlinepayment/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/personalfinance/domains>" >> $blacklists_domains
echo -e "" >> $blacklists_domains
echo -e "#=============================================================================#" >> $blacklists_domains
echo -e "#	Blogs and Forums" >> $blacklists_domains
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/blog/domains>" >> $blacklists_domains
echo -e "" >> $blacklists_domains
echo -e "#=============================================================================#" >> $blacklists_domains
echo -e "#	Books, Child Care, Education, etc." >> $blacklists_domains
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/books/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/child/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/childcare/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/frencheducation/domains>" >> $blacklists_domains
echo -e "" >> $blacklists_domains
echo -e "#=============================================================================#" >> $blacklists_domains
echo -e "#	Computer Security and System Maintenance" >> $blacklists_domains
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/antispyware/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/cleaning/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/remote-control/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/updatesites/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/verisign/domains>" >> $blacklists_domains
echo -e "" >> $blacklists_domains
echo -e "#=============================================================================#" >> $blacklists_domains
echo -e "#	Computer Security Threats" >> $blacklists_domains
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/desktopsillies/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/dialers/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/hacking/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/malware/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/phishing/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/proxy/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/spyware/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/virusinfected/domains>" >> $blacklists_domains
echo -e "" >> $blacklists_domains
echo -e "#=============================================================================#" >> $blacklists_domains
echo -e "#	Content Sharing (Audio, Photo, Video)" >> $blacklists_domains
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/audio-video/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/filehosting/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/filesharing/domains>" >> $blacklists_domains
echo -e "" >> $blacklists_domains
echo -e "#=============================================================================#" >> $blacklists_domains
echo -e "#	Electronic Commerce, Marketing" >> $blacklists_domains
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/ecommerce/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/marketingware/domains>" >> $blacklists_domains
echo -e "" >> $blacklists_domains
echo -e "#=============================================================================#" >> $blacklists_domains
echo -e "#	Fashion" >> $blacklists_domains
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/clothing/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/jewelry/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/reaffected/domains>" >> $blacklists_domains
echo -e "" >> $blacklists_domains
echo -e "#=============================================================================#" >> $blacklists_domains
echo -e "#	Gambling, Gaming, Time Wasting, etc." >> $blacklists_domains
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/gambling/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/games/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/kidstimewasting/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/onlinegames/domains>" >> $blacklists_domains
echo -e "" >> $blacklists_domains
echo -e "#=============================================================================#" >> $blacklists_domains
echo -e "#	Goods and Services." >> $blacklists_domains
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/jobsearch/domains>" >> $blacklists_domains
echo -e "" >> $blacklists_domains
echo -e "#=============================================================================#" >> $blacklists_domains
echo -e "#	Government, Military, etc." >> $blacklists_domains
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/government/domains>" >> $blacklists_domains
echo -e "" >> $blacklists_domains
echo -e "#=============================================================================#" >> $blacklists_domains
echo -e "#	Health, Hygiene, Medical, etc." >> $blacklists_domains
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/abortion/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/contraception/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/hygiene/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/medical/domains>" >> $blacklists_domains
echo -e "" >> $blacklists_domains
echo -e "#=============================================================================#" >> $blacklists_domains
echo -e "#	Illegal Activities" >> $blacklists_domains
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/drugs/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/warez/domains>" >> $blacklists_domains
echo -e "" >> $blacklists_domains
echo -e "#=============================================================================#" >> $blacklists_domains
echo -e "#	Internet Search Engines" >> $blacklists_domains
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/searchengines/domains>" >> $blacklists_domains
echo -e "" >> $blacklists_domains
echo -e "#=============================================================================#" >> $blacklists_domains
echo -e "#	Internet Mail and Webmail" >> $blacklists_domains
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/mail/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/webmail/domains>" >> $blacklists_domains
echo -e "" >> $blacklists_domains
echo -e "#=============================================================================#" >> $blacklists_domains
echo -e "#	Mobile Phone and Gadgets" >> $blacklists_domains
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/cellphones/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/mobile-phone/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/ringtones/domains>" >> $blacklists_domains
echo -e "" >> $blacklists_domains
echo -e "#=============================================================================#" >> $blacklists_domains
echo -e "#	Information, Magazines, News, Radio, etc." >> $blacklists_domains
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/magazines/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/news/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/press/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/radio/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/sportnews/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/sports/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/weather/domains>" >> $blacklists_domains
echo -e "" >> $blacklists_domains
echo -e "#=============================================================================#" >> $blacklists_domains
echo -e "#	Online Auctions, Shopping Online, etc." >> $blacklists_domains
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/onlineauctions/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/shopping/domains>" >> $blacklists_domains
echo -e "" >> $blacklists_domains
echo -e "#=============================================================================#" >> $blacklists_domains
echo -e "#	Religion and Sect beliefs" >> $blacklists_domains
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/religion/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/sect/domains>" >> $blacklists_domains
echo -e "" >> $blacklists_domains
echo -e "#=============================================================================#" >> $blacklists_domains
echo -e "#	Chat, Dating, Social Networking, etc." >> $blacklists_domains
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/chat/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/dating/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/instantmessaging/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/social_networks/domains>" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/socialnetworking/domains>" >> $blacklists_domains
echo -e "" >> $blacklists_domains
echo -e "#=============================================================================#" >> $blacklists_domains
echo -e "#	Whitelist" >> $blacklists_domains
echo -e "#-----------------------------------------------------------------------------#" >> $blacklists_domains
echo -e "#.Include</etc/dansguardian/lists/blacklists/whitelist/domains>" >> $blacklists_domains
echo -e "" >> $blacklists_domains
#-----------------------------------------------------------------------------#
cp $blacklists_domains $bannedsitelist
cp $blacklists_domains $exceptionsitelist
cp $blacklists_domains $greysitelist
#-----------------------------------------------------------------------------#
sed -i '9 a\\weebo.com' $bannedsitelist
sed -i '9 a\\#twitter.com' $bannedsitelist
sed -i '9 a\\orkut.com' $bannedsitelist
sed -i '9 a\\myspace.com' $bannedsitelist
sed -i '9 a\\myprofile.com' $bannedsitelist
sed -i '9 a\\#facebook.com' $bannedsitelist
sed -i 's|#facebook.com|facebook.com|' $bannedsitelist
sed -i 's|#twitter.com|twitter.com|' $bannedsitelist
#-----------------------------------------------------------------------------#
# Enable list of blocked domains
#-----------------------------------------------------------------------------#
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/ads|.Include</etc/dansguardian/lists/blacklists/ads|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/adult|.Include</etc/dansguardian/lists/blacklists/adult|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/aggressive|.Include</etc/dansguardian/lists/blacklists/aggressive|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/alcohol|.Include</etc/dansguardian/lists/blacklists/alcohol|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/beerliquorinfo|.Include</etc/dansguardian/lists/blacklists/beerliquorinfo|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/beerliquorsale|.Include</etc/dansguardian/lists/blacklists/beerliquorsale|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/chat|.Include</etc/dansguardian/lists/blacklists/chat|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/dating|.Include</etc/dansguardian/lists/blacklists/dating|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/desktopsillies|.Include</etc/dansguardian/lists/blacklists/desktopsillies|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/dialers|.Include</etc/dansguardian/lists/blacklists/dialers|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/drugs|.Include</etc/dansguardian/lists/blacklists/drugs|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/filehosting|.Include</etc/dansguardian/lists/blacklists/filehosting|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/filesharing|.Include</etc/dansguardian/lists/blacklists/filesharing|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/gambling|.Include</etc/dansguardian/lists/blacklists/gambling|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/games|.Include</etc/dansguardian/lists/blacklists/games|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/guns|.Include</etc/dansguardian/lists/blacklists/guns|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/hacking|.Include</etc/dansguardian/lists/blacklists/hacking|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/hunting|.Include</etc/dansguardian/lists/blacklists/hunting|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/instantmessaging|.Include</etc/dansguardian/lists/blacklists/instantmessaging|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/kidstimewasting|.Include</etc/dansguardian/lists/blacklists/kidstimewasting|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/malware|.Include</etc/dansguardian/lists/blacklists/malware|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/manga|.Include</etc/dansguardian/lists/blacklists/manga|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/mixed_adult|.Include</etc/dansguardian/lists/blacklists/mixed_adult|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/naturism|.Include</etc/dansguardian/lists/blacklists/naturism|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/onlinegames|.Include</etc/dansguardian/lists/blacklists/onlinegames|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/phishing|.Include</etc/dansguardian/lists/blacklists/phishing|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/porn|.Include</etc/dansguardian/lists/blacklists/porn|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/proxy|.Include</etc/dansguardian/lists/blacklists/proxy|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/sexuality|.Include</etc/dansguardian/lists/blacklists/sexuality|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/socialnetworking|.Include</etc/dansguardian/lists/blacklists/socialnetworking|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/social_networks|.Include</etc/dansguardian/lists/blacklists/social_networks|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/spyware|.Include</etc/dansguardian/lists/blacklists/spyware|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/tobacco|.Include</etc/dansguardian/lists/blacklists/tobacco|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/violence|.Include</etc/dansguardian/lists/blacklists/violence|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/virusinfected|.Include</etc/dansguardian/lists/blacklists/virusinfected|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/warez|.Include</etc/dansguardian/lists/blacklists/warez|' $bannedsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/weapons|.Include</etc/dansguardian/lists/blacklists/weapons|' $bannedsitelist
#-----------------------------------------------------------------------------#
# Enable list of allowed domains
#-----------------------------------------------------------------------------#
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/antispyware|.Include</etc/dansguardian/lists/blacklists/antispyware|' $exceptionsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/abortion|.Include</etc/dansguardian/lists/blacklists/abortion|' $exceptionsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/banking|.Include</etc/dansguardian/lists/blacklists/banking|' $exceptionsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/books|.Include</etc/dansguardian/lists/blacklists/books|' $exceptionsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/childcare|.Include</etc/dansguardian/lists/blacklists/childcare|' $exceptionsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/child|.Include</etc/dansguardian/lists/blacklists/child|' $exceptionsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/cleaning|.Include</etc/dansguardian/lists/blacklists/cleaning|' $exceptionsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/contraception|.Include</etc/dansguardian/lists/blacklists/contraception|' $exceptionsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/culinary|.Include</etc/dansguardian/lists/blacklists/culinary|' $exceptionsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/financial|.Include</etc/dansguardian/lists/blacklists/financial|' $exceptionsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/gardening|.Include</etc/dansguardian/lists/blacklists/gardening|' $exceptionsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/government|.Include</etc/dansguardian/lists/blacklists/government|' $exceptionsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/homerepair|.Include</etc/dansguardian/lists/blacklists/homerepair|' $exceptionsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/hygiene|.Include</etc/dansguardian/lists/blacklists/hygiene|' $exceptionsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/jobsearch|.Include</etc/dansguardian/lists/blacklists/jobsearch|' $exceptionsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/magazines|.Include</etc/dansguardian/lists/blacklists/magazines|' $exceptionsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/mail|.Include</etc/dansguardian/lists/blacklists/mail|' $exceptionsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/medical|.Include</etc/dansguardian/lists/blacklists/medical|' $exceptionsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/news|.Include</etc/dansguardian/lists/blacklists/news|' $exceptionsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/onlinepayment|.Include</etc/dansguardian/lists/blacklists/onlinepayment|' $exceptionsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/personalfinance|.Include</etc/dansguardian/lists/blacklists/personalfinance|' $exceptionsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/pets|.Include</etc/dansguardian/lists/blacklists/pets|' $exceptionsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/press|.Include</etc/dansguardian/lists/blacklists/press|' $exceptionsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/religion|.Include</etc/dansguardian/lists/blacklists/religion|' $exceptionsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/remote-control|.Include</etc/dansguardian/lists/blacklists/remote-control|' $exceptionsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/sect|.Include</etc/dansguardian/lists/blacklists/sect|' $exceptionsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/sportnews|.Include</etc/dansguardian/lists/blacklists/sportnews|' $exceptionsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/sports|.Include</etc/dansguardian/lists/blacklists/sports|' $exceptionsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/updatesites|.Include</etc/dansguardian/lists/blacklists/updatesites|' $exceptionsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/vacation|.Include</etc/dansguardian/lists/blacklists/vacation|' $exceptionsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/verisign|.Include</etc/dansguardian/lists/blacklists/verisign|' $exceptionsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/weather|.Include</etc/dansguardian/lists/blacklists/weather|' $exceptionsitelist
sed -i 's|#.Include</etc/dansguardian/lists/blacklists/webmail|.Include</etc/dansguardian/lists/blacklists/webmail|' $exceptionsitelist
#-----------------------------------------------------------------------------#
# Creates Filter Groups directories
#-----------------------------------------------------------------------------#
for s in `seq 1 6`
do
	mkdir $dansguardianlist/filter$s
	cp $dansguardianlist/*list $dansguardianlist/filter$s
	cp $dansguardianlist/pics $dansguardianlist/filter$s
	rm $dansguardianlist/filter$s/bannediplist
	rm $dansguardianlist/filter$s/exceptioniplist
	rm $dansguardianlist/filter$s/filtergroupslist
done
#==============================================================================#
echo	"Installing URLBigBlacklist..."
#------------------------------------------------------------------------------#
cd $dansguardianlist
wget -c -O blacklists.tgz -q -Y on ${BL_URL}
tar xfvz blacklists.tgz &> /dev/null
find $blacklists_dir -name "domains" -execdir cp {} {}.processed \;
find $blacklists_dir -name "urls" -execdir cp {} {}.processed \;
chown -R root:root $blacklists_dir
#
/etc/init.d/dansguardian stop && /etc/init.d/dansguardian start &> /dev/null
#=============================================================================#
echo	"Rebooting system..."
#-----------------------------------------------------------------------------#
reboot &> /dev/null

```

---

### Post by elico on 2011-04-09
This is one hell of a script dude!!!

i like it !!!

if you do have any changes i will be happy to hear about it.

---

### Post by krishanthan on 2012-01-08
Dear Friend,

i am new to Ubuntu, so please help me how to use above script in Ubuntu, please tell and above noted all package really i want it.

thanks

---

### Post by elico on 2012-01-08
it depends on what you need to do.
this script is long and i'm not sure it will fit you.
what you need to do is copy the script from the code tag into a file named "script.sh" or whatever name you want.
then us "chmod +x" on the file to make it executable and run the scripts.
if you didnt understood i will try to make it more simple but per your needs.

---

### Post by krishanthan on 2012-01-08
Dear Friend,

Thank for reply to me. i was make it script.sh, and can you tell me the next step, otherwise easy then this any way. my requirement, i have a internet cafe, so i want to use Squid as a transparent and i like to use Squid 3 and Webmin also and in feature some time i will use the PHP also because for  video PHP script. So i think above one is good but your idea also wel come please reply.

---

### Post by elico on 2012-01-08
what do you want to achieve?
that is my question.
do you want content filtering?
if you want to use this script you must understand the basics of how to use squid and webmin.
to install webmin you can look at:
[http://www.webmin.com/deb.html](http://www.webmin.com/deb.html)

it's very simple and should get you started.
the main for this script is to configure on the machine dhcp server and squid for content filtering and caching.
this scripts do not involves the things you need to do in order to make squid as intercept proxy.
what is this php video thing?

---

### Post by krishanthan on 2012-01-08
Dear Friend,

i target is >> i want to release the internet through Ubuntu DHCP server when is delivery to clients internet connection + Squid proxy (transparent) + filtering. already ready i was try but i have problem with IP table those think & Webmin will good for me because easy to control. (If don't mind can i have any Contact mail ID because if you free i can chat with you.)

Thanks

---

### Post by jaimerosario on 2012-01-10
Soon will update the script... Any question or request, send a PM.

---

### Post by krishanthan on 2012-01-18
Dear Friends,

Thanks for all reply and updated scripts also,i am attach a image with this massage, that image contain my Internet cafe network plan, so i want can any one change script for my network plan and IP ranges. That mean my Internet connection IP range 192.168.2.1 this IP range connect with Proxy server after proxy server will release the Internet to clients 192.168.3.x range with squid transparent proxy. Because i don't know Ubuntu IP routing or network interfaces and apply NAT rules, or you can use Firewall Builder to active NAT with iptables. this script contain every think also i want it and  So please this time also help me.

---

### Post by elico on 2012-01-19
do you need more then just squid as proxy? cause the main reason of this script is for content filtering.
if it's only for proxy it will be very simple to fix you a small script for everything.

---

### Post by a2j on 2012-01-20
> **krishanthan said:**
> Dear Friends,

Thanks for all reply and updated scripts also,i am attach a image with this massage, that image contain my Internet cafe network plan, so i want can any one change script for my network plan and IP ranges. That mean my Internet connection IP range 192.168.2.1 this IP range connect with Proxy server after proxy server will release the Internet to clients 192.168.3.x range with squid transparent proxy. Because i don't know Ubuntu IP routing or network interfaces and apply NAT rules, or you can use Firewall Builder to active NAT with iptables. this script contain every think also i want it and  So please this time also help me.

"router" could be eliminated and "proxy" box could take "router" tasks.

---

### Post by krishanthan on 2012-01-21
Dear Friend,

i was did successful above script but i have a problem, https(443) sites (gmail.com, paypla.com) are not working by transparent proxy. can can enable those site to clients. please give easy step for this issue.

Thanks

---

### Post by elico on 2012-01-21
well this script is ment for http sites only not for https.
you can't yet and not suppose to have intercept https traffic as for it being http over ssl (secure).

---

### Post by Rakeshvijayan on 2012-05-18
> **krishanthan said:**
> Dear Friend,

i was did successful above script but i have a problem, https(443) sites (gmail.com, paypla.com) are not working by transparent proxy. can can enable those site to clients. please give easy step for this issue.

Thanks

Hi 

you need to edit /etc/dansguardian/list/exceptionsitelist 

and add those site url .in my case I install dansguardian by step by step ...
only one problem that i meet was client cant loging to yahooo I resolved it by adding 
mail.yahoo.com
mail.yimg.com


to exceptionsitelist

  If it not working , I will help you to resolve this issue

---

