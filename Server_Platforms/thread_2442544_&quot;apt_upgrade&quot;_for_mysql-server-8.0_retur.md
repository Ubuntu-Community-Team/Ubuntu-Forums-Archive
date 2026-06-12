---
title: "&quot;apt upgrade&quot; for mysql-server-8.0 returns an error on Ubuntu Server 20.04 LTS"
date: 2020-05-04
forum: Server Platforms
---

### Post by Emmanuel_Chanel on 2020-05-04
(I'm Japanese. So some parts are in Japanese.) 
```
$ sudo apt update && sudo apt upgrade -y
[sudo] emmanuel &#12398;&#12497;&#12473;&#12527;&#12540;&#12489;: 
&#12377;&#12415;&#12414;&#12379;&#12435;&#12289;&#12418;&#12358;&#19968;&#24230;&#35430;&#12375;&#12390;&#12367;&#12384;&#12373;&#12356;&#12290;
[sudo] emmanuel &#12398;&#12497;&#12473;&#12527;&#12540;&#12489;: 
&#12377;&#12415;&#12414;&#12379;&#12435;&#12289;&#12418;&#12358;&#19968;&#24230;&#35430;&#12375;&#12390;&#12367;&#12384;&#12373;&#12356;&#12290;
[sudo] emmanuel &#12398;&#12497;&#12473;&#12527;&#12540;&#12489;: 
&#21462;&#24471;:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease [107 kB]     
&#12498;&#12483;&#12488;:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal InRelease                      
&#21462;&#24471;:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates InRelease [107 kB]
&#21462;&#24471;:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main i386 Packages [14.2 kB]
&#21462;&#24471;:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 Packages [31.0 kB]
&#21462;&#24471;:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main Translation-en [12.8 kB]
&#21462;&#24471;:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-backports InRelease [98.3 kB]
&#21462;&#24471;:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 c-n-f Metadata [1,156 B]
&#21462;&#24471;:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe i386 Packages [3,904 B]
&#21462;&#24471;:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe amd64 Packages [4,352 B]
&#21462;&#24471;:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe Translation-en [4,040 B]
&#21462;&#24471;:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe amd64 c-n-f Metadata [540 B]
&#21462;&#24471;:13 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/main amd64 Packages [37.8 kB]
&#21462;&#24471;:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/main i386 Packages [15.7 kB]
&#21462;&#24471;:15 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/main Translation-en [15.8 kB]
&#21462;&#24471;:16 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/main amd64 c-n-f Metadata [1,500 B]
&#21462;&#24471;:17 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/universe amd64 Packages [13.0 kB]
&#21462;&#24471;:18 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/universe i386 Packages [11.3 kB]
&#21462;&#24471;:19 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/universe Translation-en [6,364 B]
&#21462;&#24471;:20 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/universe amd64 c-n-f Metadata [836 B]
&#21462;&#24471;:21 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-backports/universe i386 Packages [1,956 B]
&#21462;&#24471;:22 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-backports/universe amd64 Packages [2,792 B]
&#21462;&#24471;:23 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-backports/universe Translation-en [1,280 B]
&#21462;&#24471;:24 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-backports/universe amd64 c-n-f Metadata [188 B]
493 kB &#12434; 3&#31186; &#12391;&#21462;&#24471;&#12375;&#12414;&#12375;&#12383; (163 kB/s)  
&#12497;&#12483;&#12465;&#12540;&#12472;&#12522;&#12473;&#12488;&#12434;&#35501;&#12415;&#36796;&#12435;&#12391;&#12356;&#12414;&#12377;... &#23436;&#20102;
&#20381;&#23384;&#38306;&#20418;&#12484;&#12522;&#12540;&#12434;&#20316;&#25104;&#12375;&#12390;&#12356;&#12414;&#12377;       
&#29366;&#24907;&#24773;&#22577;&#12434;&#35501;&#12415;&#21462;&#12387;&#12390;&#12356;&#12414;&#12377;... &#23436;&#20102;
&#12450;&#12483;&#12503;&#12464;&#12524;&#12540;&#12489;&#12391;&#12365;&#12427;&#12497;&#12483;&#12465;&#12540;&#12472;&#12364; 8 &#20491;&#12354;&#12426;&#12414;&#12377;&#12290;&#34920;&#31034;&#12377;&#12427;&#12395;&#12399; 'apt list --upgradable' &#12434;&#23455;&#34892;&#12375;&#12390;&#12367;&#12384;&#12373;&#12356;&#12290;
&#12497;&#12483;&#12465;&#12540;&#12472;&#12522;&#12473;&#12488;&#12434;&#35501;&#12415;&#36796;&#12435;&#12391;&#12356;&#12414;&#12377;... &#23436;&#20102;
&#20381;&#23384;&#38306;&#20418;&#12484;&#12522;&#12540;&#12434;&#20316;&#25104;&#12375;&#12390;&#12356;&#12414;&#12377;                
&#29366;&#24907;&#24773;&#22577;&#12434;&#35501;&#12415;&#21462;&#12387;&#12390;&#12356;&#12414;&#12377;... &#23436;&#20102;
&#12450;&#12483;&#12503;&#12464;&#12524;&#12540;&#12489;&#12497;&#12483;&#12465;&#12540;&#12472;&#12434;&#26908;&#20986;&#12375;&#12390;&#12356;&#12414;&#12377;... &#23436;&#20102;
&#20197;&#19979;&#12398;&#12497;&#12483;&#12465;&#12540;&#12472;&#12399;&#12450;&#12483;&#12503;&#12464;&#12524;&#12540;&#12489;&#12373;&#12428;&#12414;&#12377;:
  libmysqlclient21 mysql-client-8.0 mysql-client-core-8.0 mysql-server
  mysql-server-8.0 mysql-server-core-8.0 python3-update-manager
  update-manager-core
&#12450;&#12483;&#12503;&#12464;&#12524;&#12540;&#12489;: 8 &#20491;&#12289;&#26032;&#35215;&#12452;&#12531;&#12473;&#12488;&#12540;&#12523;: 0 &#20491;&#12289;&#21066;&#38500;: 0 &#20491;&#12289;&#20445;&#30041;: 0 &#20491;&#12290;
23.9 MB &#12398;&#12450;&#12540;&#12459;&#12452;&#12502;&#12434;&#21462;&#24471;&#12377;&#12427;&#24517;&#35201;&#12364;&#12354;&#12426;&#12414;&#12377;&#12290;
&#12371;&#12398;&#25805;&#20316;&#24460;&#12395;&#36861;&#21152;&#12391; 698 kB &#12398;&#12487;&#12451;&#12473;&#12463;&#23481;&#37327;&#12364;&#28040;&#36027;&#12373;&#12428;&#12414;&#12377;&#12290;
&#21462;&#24471;:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/main amd64 mysql-client-core-8.0 amd64 8.0.20-0ubuntu0.20.04.1 [4,196 kB]
&#21462;&#24471;:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/main amd64 mysql-client-8.0 amd64 8.0.20-0ubuntu0.20.04.1 [22.0 kB]
&#21462;&#24471;:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/main amd64 mysql-server-8.0 amd64 8.0.20-0ubuntu0.20.04.1 [1,228 kB]
&#21462;&#24471;:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/main amd64 mysql-server-core-8.0 amd64 8.0.20-0ubuntu0.20.04.1 [17.2 MB]
&#21462;&#24471;:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/main amd64 python3-update-manager all 1:20.04.10 [36.5 kB]
&#21462;&#24471;:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/main amd64 update-manager-core all 1:20.04.10 [11.3 kB]
&#21462;&#24471;:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/main amd64 libmysqlclient21 amd64 8.0.20-0ubuntu0.20.04.1 [1,221 kB]
&#21462;&#24471;:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/main amd64 mysql-server all 8.0.20-0ubuntu0.20.04.1 [9,540 B]
23.9 MB &#12434; 7&#31186; &#12391;&#21462;&#24471;&#12375;&#12414;&#12375;&#12383; (3,616 kB/s)                                     
&#12497;&#12483;&#12465;&#12540;&#12472;&#12434;&#20107;&#21069;&#35373;&#23450;&#12375;&#12390;&#12356;&#12414;&#12377; ...
(&#12487;&#12540;&#12479;&#12505;&#12540;&#12473;&#12434;&#35501;&#12415;&#36796;&#12435;&#12391;&#12356;&#12414;&#12377; ... &#29694;&#22312; 139576 &#20491;&#12398;&#12501;&#12449;&#12452;&#12523;&#12392;&#12487;&#12451;&#12524;&#12463;&#12488;&#12522;&#12364;&#12452;&#12531;&#12473;&#12488;&#12540;&#12523;&#12373;&#12428;&#12390;&#12356;&#12414;&#12377;&#12290;)
.../0-mysql-client-core-8.0_8.0.20-0ubuntu0.20.04.1_amd64.deb &#12434;&#23637;&#38283;&#12377;&#12427;&#28310;&#20633;&#12434;&#12375;&#12390;&#12356;&#12414;&#12377; ...
mysql-client-core-8.0 (8.0.20-0ubuntu0.20.04.1) &#12391; (8.0.19-0ubuntu5 &#12395;) &#19978;&#26360;&#12365;&#23637;&#38283;&#12375;&#12390;&#12356;&#12414;&#12377; ...
.../1-mysql-client-8.0_8.0.20-0ubuntu0.20.04.1_amd64.deb &#12434;&#23637;&#38283;&#12377;&#12427;&#28310;&#20633;&#12434;&#12375;&#12390;&#12356;&#12414;&#12377; ...
mysql-client-8.0 (8.0.20-0ubuntu0.20.04.1) &#12391; (8.0.19-0ubuntu5 &#12395;) &#19978;&#26360;&#12365;&#23637;&#38283;&#12375;&#12390;&#12356;&#12414;&#12377; ...
.../2-mysql-server-8.0_8.0.20-0ubuntu0.20.04.1_amd64.deb &#12434;&#23637;&#38283;&#12377;&#12427;&#28310;&#20633;&#12434;&#12375;&#12390;&#12356;&#12414;&#12377; ...
mysql-server-8.0 (8.0.20-0ubuntu0.20.04.1) &#12391; (8.0.19-0ubuntu5 &#12395;) &#19978;&#26360;&#12365;&#23637;&#38283;&#12375;&#12390;&#12356;&#12414;&#12377; ...
.../3-mysql-server-core-8.0_8.0.20-0ubuntu0.20.04.1_amd64.deb &#12434;&#23637;&#38283;&#12377;&#12427;&#28310;&#20633;&#12434;&#12375;&#12390;&#12356;&#12414;&#12377; ...
mysql-server-core-8.0 (8.0.20-0ubuntu0.20.04.1) &#12391; (8.0.19-0ubuntu5 &#12395;) &#19978;&#26360;&#12365;&#23637;&#38283;&#12375;&#12390;&#12356;&#12414;&#12377; ...
.../4-python3-update-manager_1%3a20.04.10_all.deb &#12434;&#23637;&#38283;&#12377;&#12427;&#28310;&#20633;&#12434;&#12375;&#12390;&#12356;&#12414;&#12377; ...
python3-update-manager (1:20.04.10) &#12391; (1:20.04.9 &#12395;) &#19978;&#26360;&#12365;&#23637;&#38283;&#12375;&#12390;&#12356;&#12414;&#12377; ...
.../5-update-manager-core_1%3a20.04.10_all.deb &#12434;&#23637;&#38283;&#12377;&#12427;&#28310;&#20633;&#12434;&#12375;&#12390;&#12356;&#12414;&#12377; ...
update-manager-core (1:20.04.10) &#12391; (1:20.04.9 &#12395;) &#19978;&#26360;&#12365;&#23637;&#38283;&#12375;&#12390;&#12356;&#12414;&#12377; ...
.../6-libmysqlclient21_8.0.20-0ubuntu0.20.04.1_amd64.deb &#12434;&#23637;&#38283;&#12377;&#12427;&#28310;&#20633;&#12434;&#12375;&#12390;&#12356;&#12414;&#12377; ...
libmysqlclient21:amd64 (8.0.20-0ubuntu0.20.04.1) &#12391; (8.0.19-0ubuntu5 &#12395;) &#19978;&#26360;&#12365;&#23637;&#38283;&#12375;&#12390;&#12356;&#12414;&#12377; ...
.../7-mysql-server_8.0.20-0ubuntu0.20.04.1_all.deb &#12434;&#23637;&#38283;&#12377;&#12427;&#28310;&#20633;&#12434;&#12375;&#12390;&#12356;&#12414;&#12377; ...
mysql-server (8.0.20-0ubuntu0.20.04.1) &#12391; (8.0.19-0ubuntu5 &#12395;) &#19978;&#26360;&#12365;&#23637;&#38283;&#12375;&#12390;&#12356;&#12414;&#12377; ...
mysql-client-core-8.0 (8.0.20-0ubuntu0.20.04.1) &#12434;&#35373;&#23450;&#12375;&#12390;&#12356;&#12414;&#12377; ...
libmysqlclient21:amd64 (8.0.20-0ubuntu0.20.04.1) &#12434;&#35373;&#23450;&#12375;&#12390;&#12356;&#12414;&#12377; ...
mysql-server-core-8.0 (8.0.20-0ubuntu0.20.04.1) &#12434;&#35373;&#23450;&#12375;&#12390;&#12356;&#12414;&#12377; ...
python3-update-manager (1:20.04.10) &#12434;&#35373;&#23450;&#12375;&#12390;&#12356;&#12414;&#12377; ...
mysql-client-8.0 (8.0.20-0ubuntu0.20.04.1) &#12434;&#35373;&#23450;&#12375;&#12390;&#12356;&#12414;&#12377; ...
mysql-server-8.0 (8.0.20-0ubuntu0.20.04.1) &#12434;&#35373;&#23450;&#12375;&#12390;&#12356;&#12414;&#12377; ...
Specified filename /var/lib/mysql/ibdata1 does not exist.
mysqld will log errors to /var/log/mysql/error.log
mysqld is running as pid 1609960
Error: Unable to shut down server with process id 1609960
^[[1;5Fdpkg: &#12497;&#12483;&#12465;&#12540;&#12472; mysql-server-8.0 &#12398;&#20966;&#29702;&#20013;&#12395;&#12456;&#12521;&#12540;&#12364;&#30330;&#29983;&#12375;&#12414;&#12375;&#12383; (--configure):
 installed mysql-server-8.0 package post-installation script subprocess returned error exit status 1
update-manager-core (1:20.04.10) &#12434;&#35373;&#23450;&#12375;&#12390;&#12356;&#12414;&#12377; ...
dpkg: &#20381;&#23384;&#38306;&#20418;&#12398;&#21839;&#38988;&#12395;&#12424;&#12426; mysql-server &#12398;&#35373;&#23450;&#12364;&#12391;&#12365;&#12414;&#12379;&#12435;:
 mysql-server &#12399;&#20197;&#19979;&#12395;&#20381;&#23384; (depends) &#12375;&#12414;&#12377;: mysql-server-8.0 ...&#12375;&#12363;&#12375;:
  &#12497;&#12483;&#12465;&#12540;&#12472; mysql-server-8.0 &#12399;&#12414;&#12384;&#35373;&#23450;&#12373;&#12428;&#12390;&#12356;&#12414;&#12379;&#12435;&#12290;

dpkg: &#12497;&#12483;&#12465;&#12540;&#12472; mysql-server &#12398;&#20966;&#29702;&#20013;&#12395;&#12456;&#12521;&#12540;&#12364;&#30330;&#29983;&#12375;&#12414;&#12375;&#12383; (--configure):
 &#20381;&#23384;&#38306;&#20418;&#12398;&#21839;&#38988; - &#35373;&#23450;&#12434;&#35211;&#36865;&#12426;&#12414;&#12377;
&#12456;&#12521;&#12540;&#12513;&#12483;&#12475;&#12540;&#12472;&#12399;&#21069;&#12398;&#22833;&#25943;&#12363;&#12425;&#32154;&#12367;&#12456;&#12521;&#12540;&#12391;&#12354;&#12427;&#12371;&#12392;&#12434;&#31034;&#12375;&#12390;&#12356;&#12427;&#12398;&#12391;&#12289;&#12524;&#12509;&#12540;&#12488;&#12399;&#26360;&#12365;&#36796;&#12414;&#12428;&#12414;&#12379;&#12435;&#12290;
                systemd (245.4-4ubuntu3) &#12398;&#12488;&#12522;&#12460;&#12434;&#20966;&#29702;&#12375;&#12390;&#12356;&#12414;&#12377; ...
man-db (2.9.1-1) &#12398;&#12488;&#12522;&#12460;&#12434;&#20966;&#29702;&#12375;&#12390;&#12356;&#12414;&#12377; ...
ureadahead (0.100.0-21) &#12398;&#12488;&#12522;&#12460;&#12434;&#20966;&#29702;&#12375;&#12390;&#12356;&#12414;&#12377; ...
ureadahead will be reprofiled on next reboot
libc-bin (2.31-0ubuntu9) &#12398;&#12488;&#12522;&#12460;&#12434;&#20966;&#29702;&#12375;&#12390;&#12356;&#12414;&#12377; ...
&#20966;&#29702;&#20013;&#12395;&#12456;&#12521;&#12540;&#12364;&#30330;&#29983;&#12375;&#12414;&#12375;&#12383;:
 mysql-server-8.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
W: &#25805;&#20316;&#12399;&#12381;&#12428;&#12364;&#23436;&#20102;&#12377;&#12427;&#21069;&#12395;&#20013;&#26029;&#12373;&#12428;&#12414;&#12375;&#12383;
(Omitted)
$ sudo apt install -f
&#12497;&#12483;&#12465;&#12540;&#12472;&#12522;&#12473;&#12488;&#12434;&#35501;&#12415;&#36796;&#12435;&#12391;&#12356;&#12414;&#12377;... &#23436;&#20102;
&#20381;&#23384;&#38306;&#20418;&#12484;&#12522;&#12540;&#12434;&#20316;&#25104;&#12375;&#12390;&#12356;&#12414;&#12377;
&#29366;&#24907;&#24773;&#22577;&#12434;&#35501;&#12415;&#21462;&#12387;&#12390;&#12356;&#12414;&#12377;... &#23436;&#20102;
&#12450;&#12483;&#12503;&#12464;&#12524;&#12540;&#12489;: 0 &#20491;&#12289;&#26032;&#35215;&#12452;&#12531;&#12473;&#12488;&#12540;&#12523;: 0 &#20491;&#12289;&#21066;&#38500;: 0 &#20491;&#12289;&#20445;&#30041;: 0 &#20491;&#12290;
2 &#20491;&#12398;&#12497;&#12483;&#12465;&#12540;&#12472;&#12364;&#23436;&#20840;&#12395;&#12452;&#12531;&#12473;&#12488;&#12540;&#12523;&#12414;&#12383;&#12399;&#21066;&#38500;&#12373;&#12428;&#12390;&#12356;&#12414;&#12379;&#12435;&#12290;
&#12371;&#12398;&#25805;&#20316;&#24460;&#12395;&#36861;&#21152;&#12391; 0 B &#12398;&#12487;&#12451;&#12473;&#12463;&#23481;&#37327;&#12364;&#28040;&#36027;&#12373;&#12428;&#12414;&#12377;&#12290;
mysql-server-8.0 (8.0.20-0ubuntu0.20.04.1) &#12434;&#35373;&#23450;&#12375;&#12390;&#12356;&#12414;&#12377; ...
mysqld will log errors to /var/log/mysql/error.log
mysqld is running as pid 1621778
Job for mysql.service failed because a timeout was exceeded.
See "systemctl status mysql.service" and "journalctl -xe" for details.
invoke-rc.d: initscript mysql, action "start" failed.
&#9679; mysql.service - MySQL Community Server
     Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: enabled)
     Active: activating (auto-restart) (Result: timeout) since Tue 2020-05-05 02:10:29 JST; 5ms ago
    Process: 1621935 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=exited, status=0/SUCCESS)
    Process: 1621963 ExecStart=/usr/sbin/mysqld (code=exited, status=0/SUCCESS)
   Main PID: 1621963 (code=exited, status=0/SUCCESS)

 5&#26376; 05 02:10:29 gateway systemd[1]: mysql.service: Failed with result 'timeout'.
 5&#26376; 05 02:10:29 gateway systemd[1]: Failed to start MySQL Community Server.
dpkg: &#12497;&#12483;&#12465;&#12540;&#12472; mysql-server-8.0 &#12398;&#20966;&#29702;&#20013;&#12395;&#12456;&#12521;&#12540;&#12364;&#30330;&#29983;&#12375;&#12414;&#12375;&#12383; (--configure):
 installed mysql-server-8.0 package post-installation script subprocess returned error exit status 1
dpkg: &#20381;&#23384;&#38306;&#20418;&#12398;&#21839;&#38988;&#12395;&#12424;&#12426; mysql-server &#12398;&#35373;&#23450;&#12364;&#12391;&#12365;&#12414;&#12379;&#12435;:
 mysql-server &#12399;&#20197;&#19979;&#12395;&#20381;&#23384; (depends) &#12375;&#12414;&#12377;: mysql-server-8.0 ...&#12375;&#12363;&#12375;:
  &#12497;&#12483;&#12465;&#12540;&#12472; mysql-server-8.0 &#12399;&#12414;&#12384;&#35373;&#23450;&#12373;&#12428;&#12390;&#12356;&#12414;&#12379;&#12435;&#12290;

dpkg: &#12497;&#12483;&#12465;&#12540;&#12472; mysql-server &#12398;&#20966;&#29702;&#20013;&#12395;&#12456;&#12521;&#12540;&#12364;&#30330;&#29983;&#12375;&#12414;&#12375;&#12383; (--configure):
 &#20381;&#23384;&#38306;&#20418;&#12398;&#21839;&#38988; - &#35373;&#23450;&#12434;&#35211;&#36865;&#12426;&#12414;&#12377;
&#12456;&#12521;&#12540;&#12513;&#12483;&#12475;&#12540;&#12472;&#12399;&#21069;&#12398;&#22833;&#25943;&#12363;&#12425;&#32154;&#12367;&#12456;&#12521;&#12540;&#12391;&#12354;&#12427;&#12371;&#12392;&#12434;&#31034;&#12375;&#12390;&#12356;&#12427;&#12398;&#12391;&#12289;&#12524;&#12509;&#12540;&#12488;&#12399;&#26360;&#12365;&#36796;&#12414;&#12428;&#12414;&#12379;&#12435;&#12290;
                &#20966;&#29702;&#20013;&#12395;&#12456;&#12521;&#12540;&#12364;&#30330;&#29983;&#12375;&#12414;&#12375;&#12383;:
 mysql-server-8.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by slickymaster on 2020-05-04
Thread moved to **Server Platforms** for a better fit

---

### Post by darkod on 2020-05-04
I can't know the exact messages because it's in japanese, but have you tried to configure the package? It seems to suggest that. Sometimes it can remain inconsistant.
```
sudo dpkg --configure mysql-server-8.0
```

You can also try to confirm there are no dependencies missing (but I think you already did that):
```
sudo apt-get install -f
```

---

### Post by Emmanuel_Chanel on 2020-05-04
I tried by your ask. This is the result.
```
$ sudo dpkg --configure mysql-server-8.0
mysql-server-8.0 (8.0.20-0ubuntu0.20.04.1) &#12434;&#35373;&#23450;&#12375;&#12390;&#12356;&#12414;&#12377; ...
Specified filename /var/lib/mysql/ibdata1 does not exist.
mysqld will log errors to /var/log/mysql/error.log
mysqld is running as pid 1654471
Job for mysql.service failed because a timeout was exceeded.
See "systemctl status mysql.service" and "journalctl -xe" for details.
invoke-rc.d: initscript mysql, action "start" failed.
&#9679; mysql.service - MySQL Community Server
     Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: enabled)
     Active: activating (auto-restart) (Result: timeout) since Tue 2020-05-05 04:18:57 JST; 4ms ago
    Process: 1654598 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=exited, status=0/SUCCESS)
    Process: 1654622 ExecStart=/usr/sbin/mysqld (code=exited, status=0/SUCCESS)
   Main PID: 1654622 (code=exited, status=0/SUCCESS)
dpkg: &#12497;&#12483;&#12465;&#12540;&#12472; mysql-server-8.0 &#12398;&#20966;&#29702;&#20013;&#12395;&#12456;&#12521;&#12540;&#12364;&#30330;&#29983;&#12375;&#12414;&#12375;&#12383; (--configure):
 installed mysql-server-8.0 package post-installation script subprocess returned error exit status 1
&#20966;&#29702;&#20013;&#12395;&#12456;&#12521;&#12540;&#12364;&#30330;&#29983;&#12375;&#12414;&#12375;&#12383;:
 mysql-server-8.0
```

---

### Post by darkod on 2020-05-04
Well, it says there you have a missing file. Not sure if it's some config file or data file.

What if you try to reinstall mysql-server:
```
sudo apt-get install --reinstall mysql-server-8.0
```

---

### Post by Emmanuel_Chanel on 2020-05-04
```
$ export LANG=C
$ sudo apt-get install --reinstall mysql-server-8.0
[sudo] password for emmanuel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for mysql-server-8.0:amd64
```

---

### Post by Emmanuel_Chanel on 2020-05-04
"systemctl start mysql" doesn't finish properly after starting MySQL... I think it's related to this issue... How do you like it?

---

### Post by darkod on 2020-05-04
I saw it mentioned in your output but the package name seems not to include 8.0 in the name. How about trying:
```
sudo apt-get install --reinstall mysql-server
```

You should be able to reinstall it without errors. If there are errors then something is missing, either files or services, and not starting the service makes sense.

The reinstall should not give you errors like above. Just use the package name that you used to install mysql, which ever that might be.

PS. Did you check the logs as per the output in your post number #4 - "mysqld will log errors to /var/log/mysql/error.log"? The error log should have more details why it is failing.

---

### Post by Emmanuel_Chanel on 2020-05-04
```
$ sudo apt-get install --reinstall mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-5.4.0-26 linux-headers-5.4.0-26-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for mysql-server:amd64
```
I tried also this:
```
$ tail 200 /tail 200 /var/log/mysql/error.log
tail: cannot open '200' for reading: No such file or directory
==> /var/log/mysql/error.log <==
2020-05-04T21:58:07.408278Z 0 [Warning] [MY-010909] [Server] /usr/sbin/mysqld: Forcing close of thread 22  user: 'paperfortune'.
2020-05-04T21:58:13.853609Z 0 [System] [MY-010910] [Server] /usr/sbin/mysqld: Shutdown complete (mysqld 8.0.20-0ubuntu0.20.04.1)  (Ubuntu).
2020-05-04T21:58:14.267837Z 0 [Warning] [MY-011807] [Server] Failed to connect to systemd notification socket named /run/systemd/notify. Error: 'Permission denied'
2020-05-04T21:58:14.510811Z 0 [System] [MY-010116] [Server] /usr/sbin/mysqld (mysqld 8.0.20-0ubuntu0.20.04.1) starting as process 5117
2020-05-04T21:58:14.518687Z 1 [System] [MY-013576] [InnoDB] InnoDB initialization has started.
2020-05-04T21:58:17.209044Z 1 [System] [MY-013577] [InnoDB] InnoDB initialization has ended.
2020-05-04T21:58:17.434591Z 0 [ERROR] [MY-011300] [Server] Plugin mysqlx reported: 'Setup of socket: '/var/run/mysqld/mysqlx.sock' failed, can't create lock file /var/run/mysqld/mysqlx.sock.lock'
2020-05-04T21:58:17.435141Z 0 [System] [MY-011323] [Server] X Plugin ready for connections. Bind-address: '::' port: 33060
2020-05-04T21:58:17.803500Z 0 [Warning] [MY-010068] [Server] CA certificate ca.pem is self signed.
2020-05-04T21:58:17.827506Z 0 [System] [MY-010931] [Server] /usr/sbin/mysqld: ready for connections. Version: '8.0.20-0ubuntu0.20.04.1'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu).
```

---

### Post by Emmanuel_Chanel on 2020-05-04
I set aa-compain /usr/sbin/mysqld and the upgrade is completed. After that, I tried setting it back to enforce mode.
The log about apparmor.d is this:
```
$tail /var/log/syslog
May  5 10:51:10 gateway systemd[1]: Starting MySQL Community Server...
May  5 10:51:10 gateway kernel: [14792.671522] audit: type=1400 audit(1588643470.388:474): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/sys/devices/system/node/" pid=58299 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
May  5 10:51:10 gateway kernel: [14792.672712] audit: type=1400 audit(1588643470.388:475): apparmor="DENIED" operation="capable" profile="/usr/sbin/mysqld" pid=58299 comm="mysqld" capability=2  capname="dac_read_search"
May  5 10:51:10 gateway kernel: [14792.675776] audit: type=1400 audit(1588643470.392:476): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/proc/sys/kernel/random/boot_id" pid=58299 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
May  5 10:51:10 gateway kernel: [14792.675854] audit: type=1400 audit(1588643470.392:477): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/proc/sys/kernel/random/boot_id" pid=58299 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
May  5 10:51:10 gateway kernel: [14792.675892] audit: type=1400 audit(1588643470.392:478): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/proc/sys/kernel/random/boot_id" pid=58299 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
May  5 10:51:10 gateway kernel: [14792.675909] audit: type=1400 audit(1588643470.392:479): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/proc/sys/kernel/random/boot_id" pid=58299 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
May  5 10:51:10 gateway kernel: [14792.678378] audit: type=1400 audit(1588643470.392:480): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/etc/ssl/openssl.cnf" pid=58299 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=107 ouid=0
May  5 10:51:10 gateway kernel: [14792.694068] audit: type=1400 audit(1588643470.408:481): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/sys/devices/system/node/" pid=58303 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=107 ouid=0
May  5 10:51:10 gateway kernel: [14792.695835] audit: type=1400 audit(1588643470.412:482): apparmor="DENIED" operation="sendmsg" profile="/usr/sbin/mysqld" name="/run/systemd/notify" pid=58303 comm="mysqld" requested_mask="w" denied_mask="w" fsuid=107 ouid=0
May  5 10:51:10 gateway kernel: [14792.948896] audit: type=1400 audit(1588643470.664:483): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/etc/ssl/openssl.cnf" pid=58303 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=107 ouid=0
```
How can I edit the /etc/apparmor.d/usr.sbin.mysql ?

---

### Post by Emmanuel_Chanel on 2020-05-04
I edited /etc/apparmor.d/usr.sbin.mysqld and looks that the problem is solved. How do you like it?
```
# vim:syntax=apparmor
# Last Modified: Tue Feb 09 15:28:30 2016
#include <tunables/global>

/usr/sbin/mysqld {
  #include <abstractions/base>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>
  #include <abstractions/mysql>
  #include <abstractions/winbind>

  **[color=red]capability dac_read_search[/color]**
# Allow system resource access
  /sys/devices/system/cpu/ r,
  capability sys_resource,
  capability dac_override,
  capability setuid,
  capability setgid,

# Allow network access
  network tcp,

  /etc/hosts.allow r,
  /etc/hosts.deny r,

# Allow config access
  /etc/mysql/** r,

# Allow pid, socket, socket lock file access
  /var/run/mysqld/mysqld.pid rw,
  /var/run/mysqld/mysqld.sock rw,
  /var/run/mysqld/mysqld.sock.lock rw,
  /run/mysqld/mysqld.pid rw,
  /run/mysqld/mysqld.sock rw,
  /run/mysqld/mysqld.sock.lock rw,

[color=red]# Additional: Allow system files
  [b]/run/mysqld/mysqlx.sock rw,
  /run/mysqld/mysqlx.sock.lock rw,
  /etc/ssl/openssl.cnf r,
  /sys/devices/system/node/ rw,
  /sys/devices/system/node/** rw,
  /run/systemd/notify rw,
  /proc/sys/kernel/random/boot_id r,
  /run/systemd/notify rw,[/b][/color]
# Allow execution of server binary
  /usr/sbin/mysqld mr,
  /usr/sbin/mysqld-debug mr,

# Allow plugin access
  /usr/lib/mysql/plugin/ r,
  /usr/lib/mysql/plugin/*.so* mr,

# Allow error msg and charset access
  /usr/share/mysql/ r,
  /usr/share/mysql/** r,

# Allow data dir access
  /var/lib/mysql/ r,
  /var/lib/mysql/** rwk,
# Allow data files dir access
  /var/lib/mysql-files/ r,
  /var/lib/mysql-files/** rwk,

# Allow keyring dir access
  /var/lib/mysql-keyring/ r,
  /var/lib/mysql-keyring/** rwk,

# Allow log file access
  /var/log/mysql.err rw,
  /var/log/mysql.log rw,
  /var/log/mysql/ r,
  /var/log/mysql/** rw,

  # Site-specific additions and overrides. See local/README for details.
  #include <local/usr.sbin.mysqld>
}
```

---

### Post by Emmanuel_Chanel on 2020-05-04
I used to set /home/mysql as the datadir. So apparmor setting was edited. And when I commanded
```
$ sudo mv -iv /etc/apparmor.d/usr.sbin.mysqld{.dpkg-dist,}
```
The problem didn't occur. So I should have explained that situation and it was not the newly installed.

---

