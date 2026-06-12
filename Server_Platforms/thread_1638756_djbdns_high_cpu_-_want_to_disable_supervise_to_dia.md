---
title: "djbdns high cpu - want to disable supervise to diagnose."
date: 2010-12-06
forum: Server Platforms
---

### Post by mrmark on 2010-12-06
I have a server running ubuntu 8.04 configured with virtualmin.

I have recently moved some sites off this server but they continue to access a database running on the server.
Since then I have noticed high cpu usage from djbdns. It is possible it was high before but I have only just noticed.

Does MySQL use djbdns?

Also I have noticed that supervise seems to monitoring qmail.
This was strange since I thought I had removed qmail and "apt-get remove qmail" confirms that it is not on the system.

Supervise is also monitoring tinydns which appears to be related to djbdns and I am unsure if this is needed or not.


Searching online I am unable to find any details on how to configure supervise or how to set the default programs to watch.
I definately want to remove the qmail services from supervise and would also like to remove tinydns to test what is relying on it and causing high cpu.

My other server (10.04) with very similar setup doesn't seem to have djbdns running, which makes me think it may be redundant unless it is working with the incoming mysql connections. Or is it dkim related?


Here are running processes


ID   	Owner   	CPU   	Command   
25509	root	33.3 %	tcpserver -vDRHl0 -x /usr/local/djbdns/var/axfr.access.cdb -- 0 53 /usr/local/bin/axfrdns
24592	dkim-filter	21.4 %	/usr/sbin/dkim-filter -x /etc/dkim-filter.conf -u dkim-filter -P /var/run/dkim-filter/dkim-filter.pid -p inet:8891@localhost -b sv
4293	dnslog	14.7 %	multilog t s1000000 /var/log/axfrdns
31085	root	11.0 %	/usr/share/webmin/proc/index_cpu.cgi
4	root	0.3 %	[ksoftirqd/0]
7	root	0.3 %	[ksoftirqd/1]
5127	root	0.1 %	/usr/bin/perl /usr/share/webmin/virtual-server/backup.pl --id 127625524416362
9787	root	0.1 %	/usr/sbin/named -c /etc/bind/named.conf
11264	mysql	0.1 %	/usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file ...
1	root	0.0 %	/sbin/init
2	root	0.0 %	[kthreadd]
3	root	0.0 %	[migration/0]
5	root	0.0 %	[watchdog/0]
6	root	0.0 %	[migration/1]
8	root	0.0 %	[watchdog/1]
9	root	0.0 %	[events/0]
10	root	0.0 %	[events/1]
11	root	0.0 %	[khelper]
44	root	0.0 %	[kblockd/0]
45	root	0.0 %	[kblockd/1]
48	root	0.0 %	[kacpid]
49	root	0.0 %	[kacpi_notify]
124	root	0.0 %	[kseriod]
173	root	0.0 %	[kswapd0]
216	root	0.0 %	[aio/0]
217	root	0.0 %	[aio/1]
1175	root	0.0 %	/usr/sbin/saslauthd -a pam -m /var/spool/postfix/var/run/saslauthd -r -n 5
1384	root	0.0 %	[ksuspend_usbd]
1387	root	0.0 %	[khubd]
1401	root	0.0 %	[ata/0]
1402	root	0.0 %	[ata/1]
1403	root	0.0 %	[ata_aux]
1574	www-data	0.0 %	/usr/sbin/apache2 -k start
1633	www-data	0.0 %	/usr/sbin/apache2 -k start
1657	www-data	0.0 %	/usr/sbin/apache2 -k start
2030	postfix	0.0 %	local -t unix
2140	root	0.0 %	[scsi_eh_0]
2141	root	0.0 %	[scsi_eh_1]
2324	root	0.0 %	[kjournald]
2329	root	0.0 %	/usr/sbin/saslauthd -a pam -m /var/spool/postfix/var/run/saslauthd -r -n 5
2330	root	0.0 %	/usr/sbin/saslauthd -a pam -m /var/spool/postfix/var/run/saslauthd -r -n 5
2331	root	0.0 %	/usr/sbin/saslauthd -a pam -m /var/spool/postfix/var/run/saslauthd -r -n 5
2332	root	0.0 %	/usr/sbin/saslauthd -a pam -m /var/spool/postfix/var/run/saslauthd -r -n 5
2497	root	0.0 %	/sbin/udevd --daemon
2853	root	0.0 %	[supervise] <defunct>
2919	root	0.0 %	[kpsmoused]
3033	root	0.0 %	[supervise] <defunct>
3965	root	0.0 %	/usr/sbin/ntpd
3966	ntpd	0.0 %	/usr/sbin/ntpd
4199	root	0.0 %	/sbin/getty 38400 tty4
4200	root	0.0 %	/sbin/getty 38400 tty5
4202	root	0.0 %	/sbin/getty 38400 tty2
4204	root	0.0 %	/sbin/getty 38400 tty3
4206	root	0.0 %	/bin/sh /usr/bin/svscanboot
4207	root	0.0 %	/sbin/getty 38400 tty6
4266	root	0.0 %	svscan /etc/service
4267	root	0.0 %	readproctitle service errors: ... fatal: unable to start log/run: file does not ...
4268	root	0.0 %	supervise axfrdns
4269	root	0.0 %	supervise log
4271	root	0.0 %	supervise log
4273	root	0.0 %	supervise log
4282	root	0.0 %	supervise log
4294	dnslog	0.0 %	multilog t s1000000 /var/log/tinydns
4391	root	0.0 %	/usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
4443	root	0.0 %	/bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
4445	klog	0.0 %	/sbin/klogd -P /var/run/klogd/kmsg
4498	root	0.0 %	[supervise] <defunct>
4959	root	0.0 %	/usr/sbin/dovecot
4960	root	0.0 %	dovecot-auth
5122	root	0.0 %	/USR/SBIN/CRON
5123	root	0.0 %	/bin/sh -c /etc/webmin/virtual-server/backup.pl --id 127625524416362
5412	root	0.0 %	[supervise] <defunct>
5888	root	0.0 %	sh -c ps --cols 2048 -eo user:80,ruser:80,group:80,rgroup:80,pid,ppid,pgid,pcpu, ...
5890	root	0.0 %	ps --cols 2048 -eo user:80,ruser:80,group:80,rgroup:80,pid,ppid,pgid,pcpu,vsz,ni ...
6258	root	0.0 %	python /usr/sbin/denyhosts --daemon --config=/etc/denyhosts.conf --config=/etc/d ...
6555	www-data	0.0 %	/usr/sbin/apache2 -k start
7167	root	0.0 %	sshd: root@pts/0
7436	root	0.0 %	/usr/bin/perl /usr/share/usermin/miniserv.pl /etc/usermin/miniserv.conf
8801	root	0.0 %	/usr/sbin/cron
8872	dovecot	0.0 %	imap-login
8887	root	0.0 %	/usr/sbin/sshd
9032	root	0.0 %	/usr/bin/perl /usr/share/usermin/miniserv.pl /etc/usermin/miniserv.conf
9119	list	0.0 %	/usr/bin/python /usr/lib/mailman/bin/mailmanctl -s -q start
9510	postgres	0.0 %	/usr/lib/postgresql/8.3/bin/postgres -D /var/lib/postgresql/8.3/main -c config_f ...
9774	list	0.0 %	/usr/bin/python /var/lib/mailman/bin/qrunner --runner=ArchRunner:0:1 -s
9919	list	0.0 %	/usr/bin/python /var/lib/mailman/bin/qrunner --runner=BounceRunner:0:1 -s
9939	list	0.0 %	/usr/bin/python /var/lib/mailman/bin/qrunner --runner=CommandRunner:0:1 -s
9942	list	0.0 %	/usr/bin/python /var/lib/mailman/bin/qrunner --runner=IncomingRunner:0:1 -s
9943	list	0.0 %	/usr/bin/python /var/lib/mailman/bin/qrunner --runner=NewsRunner:0:1 -s
9944	root	0.0 %	/bin/sh /usr/bin/mysqld_safe
9945	list	0.0 %	/usr/bin/python /var/lib/mailman/bin/qrunner --runner=OutgoingRunner:0:1 -s
9947	list	0.0 %	/usr/bin/python /var/lib/mailman/bin/qrunner --runner=VirginRunner:0:1 -s
9950	list	0.0 %	/usr/bin/python /var/lib/mailman/bin/qrunner --runner=RetryRunner:0:1 -s
10342	root	0.0 %	supervise qmail-qmqpd
11289	root	0.0 %	logger -p daemon.err -t mysqld_safe -i -t mysqld
11677	dovecot	0.0 %	pop3-login
12128	www-data	0.0 %	/usr/sbin/apache2 -k start
12314	root	0.0 %	[pdflush]
12589	dovecot	0.0 %	imap-login
12966	clamav	0.0 %	/usr/bin/freshclam -d --quiet
14906	postfix	0.0 %	smtp -t unix -u -c
15014	postfix	0.0 %	smtp -t unix -u -c
15027	postfix	0.0 %	smtp -t unix -u -c
15082	postfix	0.0 %	smtp -t unix -u -c
15094	postfix	0.0 %	bounce -z -n defer -t unix -u -c
15096	postfix	0.0 %	smtp -t unix -u -c
15120	postfix	0.0 %	smtp -t unix -u -c
15293	postfix	0.0 %	smtp -t unix -u -c
15310	postfix	0.0 %	smtp -t unix -u -c
15329	postfix	0.0 %	smtp -t unix -u -c
15361	postfix	0.0 %	smtp -t unix -u -c
15403	postfix	0.0 %	bounce -z -n defer -t unix -u -c
15430	postfix	0.0 %	smtp -t unix -u -c
15448	postfix	0.0 %	bounce -z -n defer -t unix -u -c
15498	postfix	0.0 %	smtp -t unix -u -c
15499	postfix	0.0 %	smtp -t unix -u -c
15500	postfix	0.0 %	smtp -t unix -u -c
15502	postfix	0.0 %	smtp -t unix -u -c
15505	postfix	0.0 %	bounce -z -n defer -t unix -u -c
15507	postfix	0.0 %	bounce -z -n defer -t unix -u -c
15508	postfix	0.0 %	smtp -t unix -u -c
15509	postfix	0.0 %	smtp -t unix -u -c
15510	postfix	0.0 %	smtp -t unix -u -c
15604	syslog	0.0 %	/sbin/syslogd -u syslog
15896	postfix	0.0 %	smtp -t unix -u -c
16069	postfix	0.0 %	smtp -t unix -u -c
16097	postfix	0.0 %	smtp -t unix -u -c
16143	postfix	0.0 %	anvil -l -t unix -u -c
16271	postfix	0.0 %	smtp -t unix -u -c
16292	postfix	0.0 %	smtp -t unix -u -c
16294	postfix	0.0 %	smtp -t unix -u -c
16312	postfix	0.0 %	smtp -t unix -u -c
16385	postfix	0.0 %	smtp -t unix -u -c
16449	root	0.0 %	/usr/sbin/xinetd -pidfile /var/run/xinetd.pid -stayalive -inetd_compat
16460	postfix	0.0 %	smtp -t unix -u -c
16483	postfix	0.0 %	smtp -t unix -u -c
16748	postfix	0.0 %	smtp -t unix -u -c
16828	postfix	0.0 %	smtp -t unix -u -c
16910	postfix	0.0 %	smtp -t unix -u -c
16971	postfix	0.0 %	smtp -t unix -u -c
17212	postfix	0.0 %	smtp -t unix -u -c
17272	postfix	0.0 %	smtp -t unix -u -c
17296	postfix	0.0 %	smtp -t unix -u -c
17319	postfix	0.0 %	smtp -t unix -u -c
17343	postfix	0.0 %	smtp -t unix -u -c
17367	postfix	0.0 %	smtp -t unix -u -c
17462	postfix	0.0 %	bounce -z -n defer -t unix -u -c
17474	postfix	0.0 %	bounce -z -n defer -t unix -u -c
17506	postfix	0.0 %	smtp -t unix -u -c
17521	postfix	0.0 %	smtp -t unix -u -c
17627	postfix	0.0 %	smtp -t unix -u -c
17750	postfix	0.0 %	smtp -t unix -u -c
17797	postfix	0.0 %	smtp -t unix -u -c
17820	postfix	0.0 %	smtp -t unix -u -c
17848	postfix	0.0 %	smtp -t unix -u -c
17919	root	0.0 %	[pdflush]
17936	root	0.0 %	-bash
18003	postfix	0.0 %	smtp -t unix -u -c
18029	postfix	0.0 %	smtp -t unix -u -c
18032	postfix	0.0 %	smtp -t unix -u -c
18076	postfix	0.0 %	smtp -t unix -u -c
18129	postfix	0.0 %	tlsmgr -l -t unix -u -c
18222	postfix	0.0 %	smtp -t unix -u -c
18248	postfix	0.0 %	smtp -t unix -u -c
18263	postfix	0.0 %	smtp -t unix -u -c
18278	postfix	0.0 %	smtp -t unix -u -c
18313	postfix	0.0 %	smtp -t unix -u -c
18388	postfix	0.0 %	smtp -t unix -u -c
18434	postfix	0.0 %	bounce -z -n defer -t unix -u -c
18441	postfix	0.0 %	smtp -t unix -u -c
18489	postfix	0.0 %	smtp -t unix -u -c
18509	postfix	0.0 %	bounce -z -n defer -t unix -u -c
18523	www-data	0.0 %	/usr/sbin/apache2 -k start
18535	postfix	0.0 %	smtp -t unix -u -c
18644	postfix	0.0 %	smtp -t unix -u -c
18741	postfix	0.0 %	bounce -z -n defer -t unix -u -c
18786	postfix	0.0 %	pickup -l -t fifo -u -c
18847	postfix	0.0 %	smtp -t unix -u -c
18866	postfix	0.0 %	bounce -z -n defer -t unix -u -c
18892	postfix	0.0 %	smtp -t unix -u -c
18893	postfix	0.0 %	smtp -t unix -u -c
18894	postfix	0.0 %	bounce -z -n defer -t unix -u -c
18898	postfix	0.0 %	bounce -z -n defer -t unix -u -c
18899	postfix	0.0 %	smtp -t unix -u -c
18900	postfix	0.0 %	smtp -t unix -u -c
18901	postfix	0.0 %	smtp -t unix -u -c
18902	postfix	0.0 %	smtp -t unix -u -c
18903	postfix	0.0 %	bounce -z -n defer -t unix -u -c
18904	postfix	0.0 %	bounce -z -n defer -t unix -u -c
18906	postfix	0.0 %	bounce -z -n defer -t unix -u -c
18907	postfix	0.0 %	smtp -t unix -u -c
18908	postfix	0.0 %	smtp -t unix -u -c
18909	postfix	0.0 %	bounce -z -n defer -t unix -u -c
18910	postfix	0.0 %	bounce -z -n defer -t unix -u -c
19181	postfix	0.0 %	scache -l -t unix -u -c
21159	postfix	0.0 %	bounce -z -n defer -t unix -u -c
21165	www-data	0.0 %	/usr/sbin/apache2 -k start
21171	www-data	0.0 %	/usr/sbin/apache2 -k start
21283	daemon	0.0 %	/usr/sbin/atd
21547	dovecot	0.0 %	pop3-login
21777	postfix	0.0 %	bounce -z -n defer -t unix -u -c
21970	1066	0.0 %	/usr/bin/php5-cgi
22058	postfix	0.0 %	bounce -z -n defer -t unix -u -c
22831	root	0.0 %	/usr/sbin/apache2 -k start
23237	root	0.0 %	/usr/bin/perl /usr/share/webmin/miniserv.pl /etc/webmin/miniserv.conf
23480	postfix	0.0 %	smtpd -n smtp -t inet -u -c -o stress -o smtpd_sasl_auth_enable yes
24576	www-data	0.0 %	/usr/sbin/apache2 -k start
24601	www-data	0.0 %	/usr/sbin/apache2 -k start
26026	root	0.0 %	/usr/bin/perl /usr/share/usermin/miniserv.pl /etc/usermin/miniserv.conf
26034	dovecot	0.0 %	imap-login
26397	1066	0.0 %	/usr/bin/php5-cgi
26651	root	0.0 %	/sbin/getty 38400 tty1
26988	root	0.0 %	/bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
27016	syslog	0.0 %	/sbin/syslogd -u syslog
29482	dkim-filter	0.0 %	/usr/sbin/dkim-filter -x /etc/dkim-filter.conf -u dkim-filter -P /var/run/dkim-f ...
29999	dovecot	0.0 %	pop3-login
30077	root	0.0 %	supervise qmail-smtpd-2500
30601	root	0.0 %	supervise tinydns
30702	djbdns	0.0 %	/usr/local/bin/tinydns
30932	postfix	0.0 %	qmgr -l -t fifo -u
31043	root	0.0 %	/usr/lib/postfix/master
31526	www-data	0.0 %	/usr/sbin/apache2 -k start
31768	postgres	0.0 %	postgres: writer process
31770	postgres	0.0 %	postgres: wal writer process
31774	postgres	0.0 %	postgres: autovacuum launcher process
31777	postgres	0.0 %	postgres: stats collector process

---

