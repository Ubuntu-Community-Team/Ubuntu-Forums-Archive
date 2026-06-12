---
title: "ircd-hybrid with SSL"
date: 2010-05-17
forum: Server Platforms
---

### Post by m3w2 on 2010-05-17
Hi,

I'm trying to setup a ircd-hybrid server with SSL encryption client-to-server on a Ubuntu 10.04 server and I've run in to some problems.

At first I tried to use the one from the repo. After a little configuration of the [ircd.conf]("http://trash.ytterbyhala.com/ircd-error/ircd.conf") my IRC-client was able to connect to the normal ports without SSL. Then I followed the instructions in the conf-file how to [generate the SSL-keys/cers]("http://trash.ytterbyhala.com/ircd-error/certs.txt") and configured the SSL port, but it didn't work. It didn't even listen on that port when I run **netstat -l**.

I asked around an was recommended to install the ircd-hybrid from source, since SSL might not be enabled in the repo-version. When I run **./configure** it finds OpenSSL (0.9.8k and libssl-dev from repo). But when I ran **make** I got this [error]("http://trash.ytterbyhala.com/ircd-error/make-error.txt"):

```
...
In file included from /usr/include/sys/stat.h:107,
                 from ../include/stdinc.h:123,
                 from ircd_lexer.l:31:
/usr/include/bits/stat.h:103: error: expected identifier or &#8216;(&#8217; before &#8216;[&#8217; token
make[1]: *** [lex.yy.o] Error 1
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/src'
make: *** [build] Error 2
```After some time on google I found a way to get past the error. Simply by changing "__unused[3]" to "__att_unused[3]" on line 103 and then I can run [**make** and **make install**]("http://trash.ytterbyhala.com/ircd-error/confmakeinstall.txt"). However, I don't know if it's a good/right solution to the error. Once again I configured the [ircd.conf]("http://trash.ytterbyhala.com/ircd-error/ircd.conf") and started ircd. Now it listen on both the non-SSL and the SSL port. Connecting on the normal ports work fine, but when I connect to the SSL-port I get this (used xchat 2.8.6):

```
Connection failed. Error: (336151568) error:14094410:SSL routines:SSL3_READ_BYTES:sslv3 alert handshake failure
```I also tried irssi, but all I got there was "*Irssi: warning SSL handshake failed: server closed connection unexpectedly*". So I spent some more time on google (like 12 hours). There are many different theorys of this error since it seams to be related to OpenSSL more than ircd-hybrid. I tested to connect to the server with

**openssl s_client -connect 10.0.1.16:6697**

and then I get this error:

```
CONNECTED(00000003)
7577:error:14077410:SSL routines:SSL23_GET_SERVER_HELLO:sslv3 alert handshake failure:s23_clnt.c:578:
```I've probably been trying to solve this for 30 hours. I'm testing on a VirtualBox, so I've started all over from a clean install a couple of times to. I get the same problem if I compile OpenSSL from source to (1.0.0).

**So, is someone familiar to this error or got any suggestions what to try next?**

This is the output from **make** when the stat.h gave me an error:
```
m3w2@ubuntu:~/ircd-hybrid/ircd-hybrid-7.2.3$ make
depend ==> lib
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib'
depend ==> pcre
make[2]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib/pcre'
gcc -MM -I.  pcre_chartables.c pcre_compile.c pcre_exec.c pcre_globals.c pcre_study.c pcre_tables.c pcre_fullinfo.c pcre_try_flipped.c > .depend
make[2]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib/pcre'
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib'
depend ==> modules
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/modules'
gcc -MM -I../include -I../lib/pcre   core/m_die.c core/m_join.c core/m_kick.c core/m_kill.c core/m_message.c core/m_mode.c core/m_nick.c core/m_part.c core/m_quit.c core/m_server.c core/m_sjoin.c core/m_squit.c m_accept.c m_admin.c m_away.c m_cap.c m_capab.c m_cburst.c m_close.c m_challenge.c m_cryptlink.c m_connect.c m_drop.c m_encap.c m_eob.c m_etrace.c m_hash.c m_help.c m_gline.c m_info.c m_invite.c m_ison.c m_kline.c m_knock.c m_links.c m_list.c m_lljoin.c m_llnick.c m_locops.c m_lusers.c m_map.c m_motd.c m_names.c m_nburst.c m_omotd.c m_oper.c m_operwall.c m_pass.c m_ping.c m_pong.c m_post.c m_rehash.c m_restart.c m_resv.c m_rkline.c m_rxline.c m_set.c m_stats.c m_svinfo.c m_tburst.c m_testmask.c m_testline.c m_time.c m_topic.c m_trace.c m_user.c m_userhost.c m_users.c m_version.c m_wallops.c m_who.c m_whois.c m_whowas.c m_xline.c m_challenge.c m_cryptlink.c > .depend
/bin/sed -e 's/\.o/.so/g' < .depend > .depend.tmp-1
/bin/sed -e 's/^m_\(server\|squit\|die\|join\|kick\|kill\|message\|mode\|nick\|part\|quit\|sjoin\)/core\/m_\1/' .depend.tmp-1 > .depend.tmp
/bin/mv -f .depend.tmp .depend
/bin/rm -f .depend.tmp-1
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/modules'
depend ==> src
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/src'
gcc -MM -I../include -I../lib/pcre   balloc.c channel.c channel_mode.c client.c csvlib.c dbuf.c dynlink.c event.c fdlist.c fileio.c getopt.c hash.c hook.c hostmask.c irc_getaddrinfo.c irc_getnameinfo.c irc_res.c irc_reslib.c irc_string.c ircd.c ircd_signal.c lex.yy.c list.c listener.c m_error.c match.c memory.c modules.c motd.c numeric.c packet.c parse.c restart.c resv.c rsa.c s_auth.c s_bsd.c s_conf.c s_gline.c s_log.c s_misc.c s_serv.c s_stats.c s_user.c send.c sprintf_irc.c tools.c version.c whowas.c y.tab.c s_bsd_epoll.c > .depend
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/src'
depend ==> servlink
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/servlink'
gcc -MM -I. -I../include   servlink.c io.c control.c > .depend
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/servlink'
build ==> lib
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib'
depend ==> pcre
make[2]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib/pcre'
make[2]: `.depend' is up to date.
make[2]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib/pcre'
build ==> pcre
make[2]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib/pcre'
gcc -I.  -Wall -O2 -g -c pcre_chartables.c -o pcre_chartables.o
gcc -I.  -Wall -O2 -g -c pcre_compile.c -o pcre_compile.o
gcc -I.  -Wall -O2 -g -c pcre_exec.c -o pcre_exec.o
gcc -I.  -Wall -O2 -g -c pcre_globals.c -o pcre_globals.o
gcc -I.  -Wall -O2 -g -c pcre_study.c -o pcre_study.o
gcc -I.  -Wall -O2 -g -c pcre_tables.c -o pcre_tables.o
gcc -I.  -Wall -O2 -g -c pcre_fullinfo.c -o pcre_fullinfo.o
gcc -I.  -Wall -O2 -g -c pcre_try_flipped.c -o pcre_try_flipped.o
/bin/rm -f libpcre.a
/usr/bin/ar csrv libpcre.a pcre_chartables.o pcre_compile.o pcre_exec.o pcre_globals.o pcre_study.o pcre_tables.o pcre_fullinfo.o pcre_try_flipped.o 
a - pcre_chartables.o
a - pcre_compile.o
a - pcre_exec.o
a - pcre_globals.o
a - pcre_study.o
a - pcre_tables.o
a - pcre_fullinfo.o
a - pcre_try_flipped.o
make[2]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib/pcre'
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib'
build ==> modules
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/modules'
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g core/m_die.c -o core/m_die.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g core/m_join.c -o core/m_join.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g core/m_kick.c -o core/m_kick.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g core/m_kill.c -o core/m_kill.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g core/m_message.c -o core/m_message.so
core/m_message.c: In function &#8216;build_target_list&#8217;:
core/m_message.c:269: warning: &#8216;p&#8217; may be used uninitialized in this function
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g core/m_mode.c -o core/m_mode.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g core/m_nick.c -o core/m_nick.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g core/m_part.c -o core/m_part.so
core/m_part.c: In function &#8216;m_part&#8217;:
core/m_part.c:144: warning: &#8216;p&#8217; may be used uninitialized in this function
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g core/m_quit.c -o core/m_quit.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g core/m_server.c -o core/m_server.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g core/m_sjoin.c -o core/m_sjoin.so
core/m_sjoin.c: In function &#8216;introduce_lazy_link_clients&#8217;:
core/m_sjoin.c:884: warning: suggest parentheses around operand of &#8216;!&#8217; or change &#8216;&&#8217; to &#8216;&&&#8217; or &#8216;!&#8217; to &#8216;~&#8217;
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g core/m_squit.c -o core/m_squit.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_accept.c -o m_accept.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_admin.c -o m_admin.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_away.c -o m_away.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_cap.c -o m_cap.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_capab.c -o m_capab.so
m_capab.c: In function &#8216;mr_capab&#8217;:
m_capab.c:70: warning: &#8216;p&#8217; may be used uninitialized in this function
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_cburst.c -o m_cburst.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_close.c -o m_close.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_challenge.c -o m_challenge.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_cryptlink.c -o m_cryptlink.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_connect.c -o m_connect.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_drop.c -o m_drop.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_encap.c -o m_encap.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_eob.c -o m_eob.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_etrace.c -o m_etrace.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_hash.c -o m_hash.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_help.c -o m_help.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_gline.c -o m_gline.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_info.c -o m_info.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_invite.c -o m_invite.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_ison.c -o m_ison.so
m_ison.c: In function &#8216;do_ison&#8217;:
m_ison.c:108: warning: &#8216;p&#8217; may be used uninitialized in this function
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_kline.c -o m_kline.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_knock.c -o m_knock.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_links.c -o m_links.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_list.c -o m_list.so
m_list.c: In function &#8216;do_list&#8217;:
m_list.c:111: warning: &#8216;save&#8217; may be used uninitialized in this function
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_lljoin.c -o m_lljoin.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_llnick.c -o m_llnick.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_locops.c -o m_locops.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_lusers.c -o m_lusers.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_map.c -o m_map.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_motd.c -o m_motd.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_names.c -o m_names.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_nburst.c -o m_nburst.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_omotd.c -o m_omotd.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_oper.c -o m_oper.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_operwall.c -o m_operwall.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_pass.c -o m_pass.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_ping.c -o m_ping.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_pong.c -o m_pong.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_post.c -o m_post.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_rehash.c -o m_rehash.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_restart.c -o m_restart.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_resv.c -o m_resv.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_rkline.c -o m_rkline.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_rxline.c -o m_rxline.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_set.c -o m_set.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_stats.c -o m_stats.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_svinfo.c -o m_svinfo.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_tburst.c -o m_tburst.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_testmask.c -o m_testmask.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_testline.c -o m_testline.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_time.c -o m_time.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_topic.c -o m_topic.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_trace.c -o m_trace.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_user.c -o m_user.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_userhost.c -o m_userhost.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_users.c -o m_users.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_version.c -o m_version.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_wallops.c -o m_wallops.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_who.c -o m_who.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_whois.c -o m_whois.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_whowas.c -o m_whowas.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_xline.c -o m_xline.so
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/modules'
build ==> src
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/src'
cd ../lib/pcre && make -w
make[2]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib/pcre'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib/pcre'
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c balloc.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c channel.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c channel_mode.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c client.c
client.c: In function &#8216;exit_client&#8217;:
client.c:1063: warning: format &#8216;%llu&#8217; expects type &#8216;long long unsigned int&#8217;, but argument 5 has type &#8216;uint64_t&#8217;
client.c:1063: warning: format &#8216;%llu&#8217; expects type &#8216;long long unsigned int&#8217;, but argument 6 has type &#8216;uint64_t&#8217;
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c csvlib.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c dbuf.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c dynlink.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c event.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c fdlist.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c fileio.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c getopt.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c hash.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c hook.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c hostmask.c
hostmask.c: In function &#8216;delete_one_address_conf&#8217;:
hostmask.c:382: warning: dereferencing pointer &#8216;v6&#8217; does break strict-aliasing rules
hostmask.c:377: warning: dereferencing pointer &#8216;v6&#8217; does break strict-aliasing rules
hostmask.c:371: note: initialized from here
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c irc_getaddrinfo.c
irc_getaddrinfo.c: In function &#8216;str_isnumber&#8217;:
irc_getaddrinfo.c:197: warning: ignoring return value of &#8216;strtoul&#8217;, declared with attribute warn_unused_result
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c irc_getnameinfo.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c irc_res.c
irc_res.c: In function &#8216;res_readreply&#8217;:
irc_res.c:156: warning: dereferencing pointer &#8216;v6in&#8217; does break strict-aliasing rules
irc_res.c:133: note: initialized from here
irc_res.c:166: warning: dereferencing pointer &#8216;v4in&#8217; does break strict-aliasing rules
irc_res.c:168: warning: dereferencing pointer &#8216;v4in&#8217; does break strict-aliasing rules
irc_res.c:136: note: initialized from here
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c irc_reslib.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c irc_string.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c ircd.c
ircd.c: In function &#8216;main&#8217;:
ircd.c:695: warning: ignoring return value of &#8216;chdir&#8217;, declared with attribute warn_unused_result
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c ircd_signal.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -I. -c lex.yy.c
In file included from /usr/include/sys/stat.h:107,
                 from ../include/stdinc.h:123,
                 from ircd_lexer.l:31:
/usr/include/bits/stat.h:103: error: expected identifier or &#8216;(&#8217; before &#8216;[&#8217; token
make[1]: *** [lex.yy.o] Error 1
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/src'
make: *** [build] Error 2

```This is the output from **./configure**, **make** and **make install** after modifying stat.h:
```
m3w2@ubuntu:~/ircd-hybrid/ircd-hybrid-7.2.3$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking uname -s for Cygwin, Solaris or HPUX... no
checking if gcc is Apple GCC... no
checking if gcc supports the SVR4 SGS interfaces... no
checking for mkdep... no
checking for makedepend... no
checking how to generate dependency info... gcc -MM
checking for /dev/null... yes
checking for library containing strerror... none required
checking for inline... inline
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking whether gcc needs -traditional... no
checking whether make sets $(MAKE)... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for rm... /bin/rm
checking for cp... /bin/cp
checking for mv... /bin/mv
checking for ln... /bin/ln
checking for sed... /bin/sed
checking for ar... /usr/bin/ar
checking for ld... /usr/bin/ld
checking for test... /usr/bin/test
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking crypt.h usability... yes
checking crypt.h presence... yes
checking for crypt.h... yes
checking for inttypes.h... (cached) yes
checking for stdint.h... (cached) yes
checking sys/resource.h usability... yes
checking sys/resource.h presence... yes
checking for sys/resource.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking sys/syslog.h usability... yes
checking sys/syslog.h presence... yes
checking for sys/syslog.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking libgen.h usability... yes
checking libgen.h presence... yes
checking for libgen.h... yes
checking sys/wait.h usability... yes
checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking wait.h usability... yes
checking wait.h presence... yes
checking for wait.h... yes
checking link.h usability... yes
checking link.h presence... yes
checking for link.h... yes
checking for library containing socket... none required
checking for library containing inet_aton... none required
checking for library containing inet_pton... none required
checking for library containing inet_ntop... none required
checking for struct sockaddr_storage... yes
checking for struct addrinfo... yes
checking for socklen_t... yes
checking for broken glibc with __ss_family... no
checking for core IPv6 support... yes
checking for struct in6addr_any... yes
checking for library containing crypt... -lcrypt
checking whether string.h and strings.h may both be included... yes
checking whether byte ordering is bigendian... no
checking stdarg.h usability... yes
checking stdarg.h presence... yes
checking for stdarg.h... yes
checking for strlcpy... no
checking for strlcat... no
checking for int64_t... yes
checking size of int64_t... 8
checking for long long... yes
checking size of long long... 8
checking for uint64_t... yes
checking for int64_t... (cached) yes
checking for u_int32_t... yes
checking for u_int16_t... yes
checking for in_port_t... yes
checking for sa_family_t... yes
checking for socketpair... yes
checking for basename... yes
checking for mmap... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for lrand48... yes
checking for srand48... yes
checking for strtok_r... yes
checking for usleep... yes
checking for OpenSSL... /usr
checking for OpenSSL 0.9.6 or above... found
checking for RSA_free in -lcrypto... yes
checking for EVP_bf_cfb... yes
checking for EVP_cast5_cfb... yes
checking for EVP_idea_cfb... no
checking for EVP_rc5_32_12_16_cfb... no
checking for EVP_des_ede3_cfb... yes
checking for EVP_des_cfb... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for zlibVersion in -lz... yes
checking for kevent... no
checking sys/epoll.h usability... yes
checking sys/epoll.h presence... yes
checking for sys/epoll.h... yes
checking for epoll support in kernel... yes
Using epoll for select loop.
checking if you want to do a profile build... no
checking if you want ElectricFence... no
checking if you want the block allocator... yes
Building ircd with G-Line voting support
checking for syslog options... none
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for library containing shl_load... no
checking for library containing dlopen... -ldl
checking for dlsym... yes
checking for dlfunc... no
checking for dlinfo... yes
checking for the ld -export-dynamic flag... yes
checking for compiler option to produce PIC... gcc: -fPIC -DPIC -shared
configure: creating ./config.status
config.status: creating Makefile
config.status: creating etc/Makefile
config.status: creating servlink/Makefile
config.status: creating contrib/Makefile
config.status: creating contrib/help/Makefile
config.status: creating src/Makefile
config.status: creating messages/Makefile
config.status: creating modules/Makefile
config.status: creating tools/Makefile
config.status: creating doc/Makefile
config.status: creating help/Makefile
config.status: creating lib/Makefile
config.status: creating lib/pcre/Makefile
config.status: creating include/setup.h
config.status: include/setup.h is unchanged

Compiling ircd-hybrid 7.2.2

Installing into: /usr/local/ircd
Ziplinks ................ yes
OpenSSL ................. yes - BF/168 BF/128 CAST/128 3DES/168 DES/56 
Modules ................. shared
IPv6 support ............ yes
Net I/O implementation .. epoll
EFnet server ............ no (use example.conf)
Halfops support ......... no
Small network ........... no
G-Line voting ........... yes

Configured limits:
NICKLEN ................. 9
TOPICLEN ................ 160

m3w2@ubuntu:~/ircd-hybrid/ircd-hybrid-7.2.3$ make
depend ==> lib
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib'
depend ==> pcre
make[2]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib/pcre'
gcc -MM -I.  pcre_chartables.c pcre_compile.c pcre_exec.c pcre_globals.c pcre_study.c pcre_tables.c pcre_fullinfo.c pcre_try_flipped.c > .depend
make[2]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib/pcre'
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib'
depend ==> modules
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/modules'
gcc -MM -I../include -I../lib/pcre   core/m_die.c core/m_join.c core/m_kick.c core/m_kill.c core/m_message.c core/m_mode.c core/m_nick.c core/m_part.c core/m_quit.c core/m_server.c core/m_sjoin.c core/m_squit.c m_accept.c m_admin.c m_away.c m_cap.c m_capab.c m_cburst.c m_close.c m_challenge.c m_cryptlink.c m_connect.c m_drop.c m_encap.c m_eob.c m_etrace.c m_hash.c m_help.c m_gline.c m_info.c m_invite.c m_ison.c m_kline.c m_knock.c m_links.c m_list.c m_lljoin.c m_llnick.c m_locops.c m_lusers.c m_map.c m_motd.c m_names.c m_nburst.c m_omotd.c m_oper.c m_operwall.c m_pass.c m_ping.c m_pong.c m_post.c m_rehash.c m_restart.c m_resv.c m_rkline.c m_rxline.c m_set.c m_stats.c m_svinfo.c m_tburst.c m_testmask.c m_testline.c m_time.c m_topic.c m_trace.c m_user.c m_userhost.c m_users.c m_version.c m_wallops.c m_who.c m_whois.c m_whowas.c m_xline.c m_challenge.c m_cryptlink.c > .depend
/bin/sed -e 's/\.o/.so/g' < .depend > .depend.tmp-1
/bin/sed -e 's/^m_\(server\|squit\|die\|join\|kick\|kill\|message\|mode\|nick\|part\|quit\|sjoin\)/core\/m_\1/' .depend.tmp-1 > .depend.tmp
/bin/mv -f .depend.tmp .depend
/bin/rm -f .depend.tmp-1
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/modules'
depend ==> src
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/src'
gcc -MM -I../include -I../lib/pcre   balloc.c channel.c channel_mode.c client.c csvlib.c dbuf.c dynlink.c event.c fdlist.c fileio.c getopt.c hash.c hook.c hostmask.c irc_getaddrinfo.c irc_getnameinfo.c irc_res.c irc_reslib.c irc_string.c ircd.c ircd_signal.c lex.yy.c list.c listener.c m_error.c match.c memory.c modules.c motd.c numeric.c packet.c parse.c restart.c resv.c rsa.c s_auth.c s_bsd.c s_conf.c s_gline.c s_log.c s_misc.c s_serv.c s_stats.c s_user.c send.c sprintf_irc.c tools.c version.c whowas.c y.tab.c s_bsd_epoll.c > .depend
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/src'
depend ==> servlink
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/servlink'
gcc -MM -I. -I../include   servlink.c io.c control.c > .depend
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/servlink'
build ==> lib
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib'
depend ==> pcre
make[2]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib/pcre'
make[2]: `.depend' is up to date.
make[2]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib/pcre'
build ==> pcre
make[2]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib/pcre'
gcc -I.  -Wall -O2 -g -c pcre_chartables.c -o pcre_chartables.o
gcc -I.  -Wall -O2 -g -c pcre_compile.c -o pcre_compile.o
gcc -I.  -Wall -O2 -g -c pcre_exec.c -o pcre_exec.o
gcc -I.  -Wall -O2 -g -c pcre_globals.c -o pcre_globals.o
gcc -I.  -Wall -O2 -g -c pcre_study.c -o pcre_study.o
gcc -I.  -Wall -O2 -g -c pcre_tables.c -o pcre_tables.o
gcc -I.  -Wall -O2 -g -c pcre_fullinfo.c -o pcre_fullinfo.o
gcc -I.  -Wall -O2 -g -c pcre_try_flipped.c -o pcre_try_flipped.o
/bin/rm -f libpcre.a
/usr/bin/ar csrv libpcre.a pcre_chartables.o pcre_compile.o pcre_exec.o pcre_globals.o pcre_study.o pcre_tables.o pcre_fullinfo.o pcre_try_flipped.o 
a - pcre_chartables.o
a - pcre_compile.o
a - pcre_exec.o
a - pcre_globals.o
a - pcre_study.o
a - pcre_tables.o
a - pcre_fullinfo.o
a - pcre_try_flipped.o
make[2]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib/pcre'
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib'
build ==> modules
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/modules'
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g core/m_die.c -o core/m_die.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g core/m_join.c -o core/m_join.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g core/m_kick.c -o core/m_kick.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g core/m_kill.c -o core/m_kill.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g core/m_message.c -o core/m_message.so
core/m_message.c: In function &#8216;build_target_list&#8217;:
core/m_message.c:269: warning: &#8216;p&#8217; may be used uninitialized in this function
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g core/m_mode.c -o core/m_mode.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g core/m_nick.c -o core/m_nick.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g core/m_part.c -o core/m_part.so
core/m_part.c: In function &#8216;m_part&#8217;:
core/m_part.c:144: warning: &#8216;p&#8217; may be used uninitialized in this function
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g core/m_quit.c -o core/m_quit.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g core/m_server.c -o core/m_server.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g core/m_sjoin.c -o core/m_sjoin.so
core/m_sjoin.c: In function &#8216;introduce_lazy_link_clients&#8217;:
core/m_sjoin.c:884: warning: suggest parentheses around operand of &#8216;!&#8217; or change &#8216;&&#8217; to &#8216;&&&#8217; or &#8216;!&#8217; to &#8216;~&#8217;
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g core/m_squit.c -o core/m_squit.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_accept.c -o m_accept.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_admin.c -o m_admin.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_away.c -o m_away.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_cap.c -o m_cap.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_capab.c -o m_capab.so
m_capab.c: In function &#8216;mr_capab&#8217;:
m_capab.c:70: warning: &#8216;p&#8217; may be used uninitialized in this function
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_cburst.c -o m_cburst.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_close.c -o m_close.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_challenge.c -o m_challenge.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_cryptlink.c -o m_cryptlink.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_connect.c -o m_connect.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_drop.c -o m_drop.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_encap.c -o m_encap.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_eob.c -o m_eob.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_etrace.c -o m_etrace.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_hash.c -o m_hash.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_help.c -o m_help.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_gline.c -o m_gline.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_info.c -o m_info.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_invite.c -o m_invite.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_ison.c -o m_ison.so
m_ison.c: In function &#8216;do_ison&#8217;:
m_ison.c:108: warning: &#8216;p&#8217; may be used uninitialized in this function
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_kline.c -o m_kline.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_knock.c -o m_knock.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_links.c -o m_links.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_list.c -o m_list.so
m_list.c: In function &#8216;do_list&#8217;:
m_list.c:111: warning: &#8216;save&#8217; may be used uninitialized in this function
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_lljoin.c -o m_lljoin.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_llnick.c -o m_llnick.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_locops.c -o m_locops.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_lusers.c -o m_lusers.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_map.c -o m_map.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_motd.c -o m_motd.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_names.c -o m_names.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_nburst.c -o m_nburst.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_omotd.c -o m_omotd.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_oper.c -o m_oper.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_operwall.c -o m_operwall.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_pass.c -o m_pass.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_ping.c -o m_ping.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_pong.c -o m_pong.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_post.c -o m_post.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_rehash.c -o m_rehash.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_restart.c -o m_restart.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_resv.c -o m_resv.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_rkline.c -o m_rkline.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_rxline.c -o m_rxline.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_set.c -o m_set.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_stats.c -o m_stats.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_svinfo.c -o m_svinfo.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_tburst.c -o m_tburst.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_testmask.c -o m_testmask.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_testline.c -o m_testline.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_time.c -o m_time.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_topic.c -o m_topic.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_trace.c -o m_trace.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_user.c -o m_user.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_userhost.c -o m_userhost.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_users.c -o m_users.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_version.c -o m_version.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_wallops.c -o m_wallops.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_who.c -o m_who.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_whois.c -o m_whois.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_whowas.c -o m_whowas.so
gcc -fPIC -DPIC -shared -I../include -I../lib/pcre   -Wall -O2 -g m_xline.c -o m_xline.so
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/modules'
build ==> src
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/src'
cd ../lib/pcre && make -w
make[2]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib/pcre'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib/pcre'
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c balloc.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c channel.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c channel_mode.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c client.c
client.c: In function &#8216;exit_client&#8217;:
client.c:1063: warning: format &#8216;%llu&#8217; expects type &#8216;long long unsigned int&#8217;, but argument 5 has type &#8216;uint64_t&#8217;
client.c:1063: warning: format &#8216;%llu&#8217; expects type &#8216;long long unsigned int&#8217;, but argument 6 has type &#8216;uint64_t&#8217;
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c csvlib.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c dbuf.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c dynlink.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c event.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c fdlist.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c fileio.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c getopt.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c hash.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c hook.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c hostmask.c
hostmask.c: In function &#8216;delete_one_address_conf&#8217;:
hostmask.c:382: warning: dereferencing pointer &#8216;v6&#8217; does break strict-aliasing rules
hostmask.c:377: warning: dereferencing pointer &#8216;v6&#8217; does break strict-aliasing rules
hostmask.c:371: note: initialized from here
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c irc_getaddrinfo.c
irc_getaddrinfo.c: In function &#8216;str_isnumber&#8217;:
irc_getaddrinfo.c:197: warning: ignoring return value of &#8216;strtoul&#8217;, declared with attribute warn_unused_result
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c irc_getnameinfo.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c irc_res.c
irc_res.c: In function &#8216;res_readreply&#8217;:
irc_res.c:156: warning: dereferencing pointer &#8216;v6in&#8217; does break strict-aliasing rules
irc_res.c:133: note: initialized from here
irc_res.c:166: warning: dereferencing pointer &#8216;v4in&#8217; does break strict-aliasing rules
irc_res.c:168: warning: dereferencing pointer &#8216;v4in&#8217; does break strict-aliasing rules
irc_res.c:136: note: initialized from here
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c irc_reslib.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c irc_string.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c ircd.c
ircd.c: In function &#8216;main&#8217;:
ircd.c:695: warning: ignoring return value of &#8216;chdir&#8217;, declared with attribute warn_unused_result
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c ircd_signal.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -I. -c lex.yy.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c list.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c listener.c
listener.c: In function &#8216;add_listener&#8217;:
listener.c:292: warning: dereferencing pointer &#8216;v4&#8217; does break strict-aliasing rules
listener.c:295: warning: dereferencing pointer &#8216;v4&#8217; does break strict-aliasing rules
listener.c:291: note: initialized from here
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c m_error.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c match.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c memory.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c modules.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c motd.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c numeric.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c packet.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c parse.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c restart.c
restart.c: In function &#8216;server_die&#8217;:
restart.c:82: warning: format not a string literal and no format arguments
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c resv.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c rsa.c
rsa.c: In function &#8216;verify_private_key&#8217;:
rsa.c:123: warning: value computed is not used
rsa.c:145: warning: format &#8216;%i&#8217; expects type &#8216;int&#8217;, but argument 3 has type &#8216;long int&#8217;
rsa.c:145: warning: format &#8216;%i&#8217; expects type &#8216;int&#8217;, but argument 4 has type &#8216;long int&#8217;
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c s_auth.c
s_auth.c: In function &#8216;start_auth&#8217;:
s_auth.c:294: warning: dereferencing pointer &#8216;v6&#8217; does break strict-aliasing rules
s_auth.c:293: note: initialized from here
s_auth.c: In function &#8216;auth_connect_callback&#8217;:
s_auth.c:510: warning: dereferencing pointer &#8216;v6&#8217; does break strict-aliasing rules
s_auth.c:509: note: initialized from here
s_auth.c:512: warning: dereferencing pointer &#8216;v6&#8217; does break strict-aliasing rules
s_auth.c:511: note: initialized from here
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c s_bsd.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c s_conf.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c s_gline.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c s_log.c
s_log.c: In function &#8216;log_user_exit&#8217;:
s_log.c:248: warning: format &#8216;%llu&#8217; expects type &#8216;long long unsigned int&#8217;, but argument 10 has type &#8216;uint64_t&#8217;
s_log.c:248: warning: format &#8216;%llu&#8217; expects type &#8216;long long unsigned int&#8217;, but argument 11 has type &#8216;uint64_t&#8217;
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c s_misc.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c s_serv.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c s_stats.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c s_user.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c send.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c sprintf_irc.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c tools.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c version.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c whowas.c
gcc -I../include -I../lib/pcre   -Wall -O2 -g -I. -c y.tab.c
ircd_parser.y: In function &#8216;yyparse&#8217;:
ircd_parser.y:573: warning: value computed is not used
ircd_parser.y:1013: warning: value computed is not used
ircd_parser.y:1171: warning: value computed is not used
ircd_parser.y:2779: warning: value computed is not used
gcc -I../include -I../lib/pcre   -Wall -O2 -g -c s_bsd_epoll.c
gcc -Wall -O2 -g -Wl,-export-dynamic -o ircd balloc.o channel.o channel_mode.o client.o csvlib.o dbuf.o dynlink.o event.o fdlist.o fileio.o getopt.o hash.o hook.o hostmask.o irc_getaddrinfo.o irc_getnameinfo.o irc_res.o irc_reslib.o irc_string.o ircd.o ircd_signal.o lex.yy.o list.o listener.o m_error.o match.o memory.o modules.o motd.o numeric.o packet.o parse.o restart.o resv.o rsa.o s_auth.o s_bsd.o s_conf.o s_gline.o s_log.o s_misc.o s_serv.o s_stats.o s_user.o send.o sprintf_irc.o tools.o version.o whowas.o y.tab.o s_bsd_epoll.o -ldl -lcrypt  ../lib/pcre/libpcre.a -lssl -lcrypto
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/src'
build ==> servlink
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/servlink'
gcc -I. -I../include   -Wall -O2 -g -c servlink.c
gcc -I. -I../include   -Wall -O2 -g -c io.c
gcc -I. -I../include   -Wall -O2 -g -c control.c
gcc -Wall -O2 -g -Wl,-export-dynamic -o servlink servlink.o io.o control.o -ldl -lcrypt  -lssl -lcrypto -lz
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/servlink'
build ==> tools
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/tools'
gcc -Wall -O2 -g -I../include  -Wl,-export-dynamic mkpasswd.c -o mkpasswd -lcrypt
gcc -Wall -O2 -g -I../include  -Wl,-export-dynamic encspeed.c -o encspeed -lssl -lcrypto
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/tools'

m3w2@ubuntu:~/ircd-hybrid/ircd-hybrid-7.2.3$ sudo make install
depend ==> lib
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib'
depend ==> pcre
make[2]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib/pcre'
make[2]: `.depend' is up to date.
make[2]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib/pcre'
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib'
depend ==> modules
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/modules'
make[1]: `.depend' is up to date.
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/modules'
depend ==> src
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/src'
make[1]: `.depend' is up to date.
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/src'
depend ==> servlink
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/servlink'
make[1]: `.depend' is up to date.
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/servlink'
build ==> lib
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib'
depend ==> pcre
make[2]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib/pcre'
make[2]: `.depend' is up to date.
make[2]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib/pcre'
build ==> pcre
make[2]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib/pcre'
make[2]: Nothing to be done for `build'.
make[2]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib/pcre'
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib'
build ==> modules
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/modules'
make[1]: Nothing to be done for `build'.
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/modules'
build ==> src
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/src'
cd ../lib/pcre && make -w
make[2]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib/pcre'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib/pcre'
gcc -Wall -O2 -g -Wl,-export-dynamic -o ircd balloc.o channel.o channel_mode.o client.o csvlib.o dbuf.o dynlink.o event.o fdlist.o fileio.o getopt.o hash.o hook.o hostmask.o irc_getaddrinfo.o irc_getnameinfo.o irc_res.o irc_reslib.o irc_string.o ircd.o ircd_signal.o lex.yy.o list.o listener.o m_error.o match.o memory.o modules.o motd.o numeric.o packet.o parse.o restart.o resv.o rsa.o s_auth.o s_bsd.o s_conf.o s_gline.o s_log.o s_misc.o s_serv.o s_stats.o s_user.o send.o sprintf_irc.o tools.o version.o whowas.o y.tab.o s_bsd_epoll.o -ldl -lcrypt  ../lib/pcre/libpcre.a -lssl -lcrypto
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/src'
build ==> servlink
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/servlink'
make[1]: Nothing to be done for `build'.
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/servlink'
build ==> tools
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/tools'
make[1]: Nothing to be done for `build'.
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/tools'
install ==> lib
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib'
install ==> pcre
make[2]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib/pcre'
make[2]: Nothing to be done for `install'.
make[2]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib/pcre'
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib'
install ==> modules
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/modules'
mkdir -p /usr/local/ircd
mkdir -p /usr/local/ircd/modules /usr/local/ircd/modules/autoload
Installing core modules into /usr/local/ircd/modules ..
Installing modules into /usr/local/ircd/modules/autoload ..
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/modules'
install ==> src
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/src'
mkdir -p /usr/local/ircd /usr/local/ircd /usr/local/ircd/bin /usr/local/ircd/etc \
        /usr/local/ircd/logs
cd ../lib/pcre && make -w
make[2]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib/pcre'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/lib/pcre'
gcc -Wall -O2 -g -Wl,-export-dynamic -o ircd balloc.o channel.o channel_mode.o client.o csvlib.o dbuf.o dynlink.o event.o fdlist.o fileio.o getopt.o hash.o hook.o hostmask.o irc_getaddrinfo.o irc_getnameinfo.o irc_res.o irc_reslib.o irc_string.o ircd.o ircd_signal.o lex.yy.o list.o listener.o m_error.o match.o memory.o modules.o motd.o numeric.o packet.o parse.o restart.o resv.o rsa.o s_auth.o s_bsd.o s_conf.o s_gline.o s_log.o s_misc.o s_serv.o s_stats.o s_user.o send.o sprintf_irc.o tools.o version.o whowas.o y.tab.o s_bsd_epoll.o -ldl -lcrypt  ../lib/pcre/libpcre.a -lssl -lcrypto
/usr/bin/install -c ircd /usr/local/ircd/bin
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/src'
install ==> servlink
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/servlink'
mkdir -p /usr/local/ircd/bin
/usr/bin/install -c servlink /usr/local/ircd/bin
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/servlink'
install ==> tools
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/tools'
mkdir -p /usr/local/ircd/bin
/usr/bin/install -c mkpasswd /usr/local/ircd/bin
/usr/bin/install -c encspeed /usr/local/ircd/bin
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/tools'
install ==> etc
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/etc'
/usr/bin/install -c -m 644 example.conf /usr/local/ircd/etc
Note: more example configuration files can be found in this directory (etc/).
Creating generic /usr/local/ircd/etc/ircd.motd
touch /usr/local/ircd/etc/dline.conf
touch /usr/local/ircd/etc/kline.conf
touch /usr/local/ircd/etc/xline.conf
touch /usr/local/ircd/etc/rxline.conf
touch /usr/local/ircd/etc/rkline.conf
touch /usr/local/ircd/etc/nresv.conf
touch /usr/local/ircd/etc/cresv.conf
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/etc'
install ==> doc
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/doc'
mkdir -p /usr/local/ircd/share/man/man8
/usr/bin/install -c -m 644 ircd.8 /usr/local/ircd/share/man/man8/
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/doc'
install ==> help
make[1]: Entering directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/help'
installing help files...
mkdir /usr/local/ircd/help
mkdir /usr/local/ircd/help/users
mkdir /usr/local/ircd/help/opers
make[1]: Leaving directory `/home/m3w2/ircd-hybrid/ircd-hybrid-7.2.3/help'

```**ircd.conf**:
```
 /* serverinfo {}:  Contains information about the server. (OLD M:) */
serverinfo {
    /* name: the name of our server */
    name = "m3w2-test-server";

    /* description: the description of our server.  '[' and ']' may not
     * be used here for compatibility with older servers.
     */
    description = "hybrid-7 test server";

    /* network info: the name and description of the network this server
     * is on.  Shown in the 005 reply and used with serverhiding.
     */
    network_name = "MyNet";
    network_desc = "This is My Network";

    /* hub: allow this server to act as a hub and have multiple servers
     * connected to it.  This may not be changed if there are active
     * LazyLink servers.
     */
    hub = no;

    /* vhost: the IP to bind to when we connect outward to ipv4 servers.
     * This should be an ipv4 IP only.
     */
    #vhost = "10.0.1.16";

    /* vhost6: the IP to bind to when we connect outward to ipv6 servers.
     * This should be an ipv6 IP only.
     */
    #vhost6 = "3ffe:80e8:546::2";

    /* max clients: the maximum number of clients allowed to connect */
    max_clients = 512;

    /*
     * rsa key: the path to the file containing our rsa key for cryptlink.
     *
     * Example command to store a 2048 bit RSA keypair in
     * rsa.key, and the public key in rsa.pub:
     * 
     *     openssl genrsa -out rsa.key 2048
     *    openssl rsa -in rsa.key -pubout -out rsa.pub
     *    chown <ircd-user>.<ircd.group> rsa.key rsa.pub
     *    chmod 0600 rsa.key
     *    chmod 0644 rsa.pub
     */
     rsa_private_key_file = "/usr/local/ircd/etc/rsa.key";

    /*
     * ssl certificate: the path to the file containing our ssl certificate
     * for encrypted client connection.
     *
     * This assumes your private RSA key is stored in rsa.key. You
     * MUST have an RSA key in order to generate the certificate
     *exi
     *    openssl req -new -days 365 -x509 -key rsa.key -out cert.pem
     *
     * See http://www.openssl.org/docs/HOWTO/certificates.txt
     *
     * Please use the following values when generating the cert
     *
     *    Organization Name: Network Name
     *    Organization Unit Name: changme.someirc.net
     *    Common Name: irc.someirc.net
     *    E-mail: you@domain.com
     */
    ssl_certificate_file = "/usr/local/ircd/etc/cert.pem";

};

/* admin {}: contains admin information about the server. (OLD A:) */
admin {
    name = "m3w2";
    description = "Main Server Administrator";
    email = "<root@localhost>";
};

/*
 * log {}:  contains information about logfiles.
 */
log {
    /* Do you want to enable logging to ircd.log? */
    use_logging = yes;

    /*
     * logfiles: the logfiles to use for user connects, /oper uses,
     * and failed /oper.  These files must exist for logging to be used.
     */
    fname_userlog = "logs/userlog";
    fname_operlog = "logs/operlog";
    fname_killlog = "logs/kill";
    fname_klinelog = "logs/kline";
    fname_glinelog = "logs/gline";

    /*
     * log_level: the amount of detail to log in ircd.log.  The
     * higher, the more information is logged.  May be changed
     * once the server is running via /quote SET LOG.  Either:
     * L_CRIT, L_ERROR, L_WARN, L_NOTICE, L_TRACE, L_INFO or L_DEBUG
     */
    log_level = L_DEBUG;
};

/* class {}: contain information about classes for users (OLD Y:) */
class {
    /* name: the name of the class.  classes are text now */
    name = "users";

    /* ping time: how often a client must reply to a PING from the
     * server before they are dropped.
     */
    ping_time = 2 minutes;

    /* number per ip: the number of users per host allowed to connect */
    number_per_ip = 2;

    /* max number: the maximum number of users allowed in this class */
    max_number = 100;

    /* sendq: the amount of data allowed in a clients queue before
     * they are dropped.
     */
    sendq = 100 kbytes;
};

class {
    name = "restricted";
    ping_time = 1 minute 30 seconds;
    number_per_ip = 1;
    max_number = 100;
    sendq = 60kb;
};

class {
    name = "opers";
    ping_time = 5 minutes;
    number_per_ip = 10;
    max_number = 100;
    sendq = 100kbytes;
};

class {
    name = "server";
    ping_time = 5 minutes;

    /* connectfreq: only used in server classes.  specifies the delay
     * between autoconnecting to servers.
     */
    connectfreq = 5 minutes;

    /* max number: the amount of servers to autoconnect to */
    max_number = 1;

    /* sendq: servers need a higher sendq as they send more data */
    sendq=2 megabytes;
};

/* listen {}: contain information about the ports ircd listens on (OLD P:) */
listen {
    /*
     * port: the specific port to listen on.  If no host is specified
     * before, it will listen on all available IPs.
     *
     * Ports are separated via a comma, a range may be specified using ".."
     */
    
    /* port: listen on all available IPs, ports 6665 to 6669 */
    host = "10.0.1.16";
    port = 6665 .. 6669;

    /*
     * Listen on 192.168.0.1/6697 with ssl enabled and hidden from STATS P
     * unless you are an administrator.
     *
     * NOTE: The "flags" directive has to come before "port".  Always!
     */
    //flags = hidden, ssl;
    flags = ssl;
    port = 6697;
};

/* auth {}: allow users to connect to the ircd (OLD I:) */
auth {
    /* user: the user@host allowed to connect.  multiple IPv4/IPv6 user 
     * lines are permitted per auth block.
     */
    user = "*@127.0.0.1";

    /* password: an optional password that is required to use this block */
    
    /* spoof: fake the users host to be be this.  This is free-form,
     * just do everyone a favour and dont abuse it. (OLD I: = flag)
     */
    spoof = "i.love.debian.org";

    /* spoof notice: enable spoofing notification to admins (default yes) */
    spoof_notice = yes;

    /* exceed limit: allow a user to exceed class limits (OLD I: > flag) */
    exceed_limit = yes;

    /* kline exempt: exempt this user from k/glines (OLD I: ^ flag) */
    kline_exempt = yes;

    /* gline exempt: exempt this user from glines (OLD I: _ flag) */
    gline_exempt = yes;

    /* no tilde: remove ~ from a user with no ident (OLD I: - flag) */
    no_tilde = yes;
    
    /* class: the class the user is placed in */
    class = "opers";
};

#auth {
#    # redirect: the server and port to redirect a user to.  A user does
#    # not have to obey the redirection, the ircd just suggests to them
#    # an alternative server.
#    redirserv = "irc.at.the.edge.of.earth";
#    redirport = 6667;
    
#    /* hostmask user has to match to receive redirection */
#    user = "*.on.mars";
#
#    /* class: a class is required even though it is not used */
#    class = "users";
#};

auth {
    user = "*@*";
    class = "users";
    
    /* restricted: stop the client sending mode changes */
    #restricted = yes;

    /* have ident: require the user has identd to connect (OLD I: + flag) */
    have_ident = no;
};

/* operator {}: defines ircd operators. (OLD O:)
 * ircd-hybrid no longer supports local operators, privileges are
 * controlled via flags.
 */
operator {
    /* name: the name of the oper */
    name = "root";

    /* user: the user@host required for this operator.  CIDR is not
     * supported.  multiple user="" lines are supported.
     */
    user = "*@*";

    /* password: the password required to oper.  By default this will
     * need to be encrypted using '/usr/bin/mkpasswd'.
     * WARNING: Please do not mix up the 'mkpasswd' program from 
         * /usr/sbin with this one. If you are root, typing 'mkpasswd' 
     * will run that one instead and you will receive a strange error.
     *
     * MD5 is supported. If you want to use it, use mkpasswd -Hmd5.
     */
    password = "ToJx.IEPqjiVg";
    #password = "$1$9PTzrFkW$yh3ablZ5DnHeU9yjhj..U/";

    /* rsa key: the public key for this oper when using Challenge.
     * A password should not be defined when this is used, see 
     * doc/challenge.txt for more information.
     */
    #rsa_public_key_file = "/usr/local/ircd/etc/oper.pub";

    /* class: the class the oper joins when they successfully /oper */
    class = "opers";

    /* privileges: controls the activities and commands an oper are 
     * allowed to do on the server.  All options default to no.
     * Available options:
     *
     * global_kill:  allows remote users to be /KILL'd (OLD 'O' flag)
     * remote:       allows remote SQUIT and CONNECT   (OLD 'R' flag)
     * kline:        allows KILL, KLINE and DLINE      (OLD 'K' flag)
     * unkline:      allows UNKLINE and UNDLINE        (OLD 'U' flag)
     * gline:        allows GLINE                      (OLD 'G' flag)
     * nick_changes: allows oper to see nickchanges    (OLD 'N' flag)
     *               via usermode +n
     * rehash:       allows oper to REHASH config      (OLD 'H' flag)
     * die:          allows DIE and RESTART            (OLD 'D' flag)
     * admin:        gives admin privileges.  admins
     *               may (un)load modules and see the
     *               real IPs of servers.
     */
    global_kill = yes;
    remote = yes;
    kline = yes;
    unkline = yes;
    gline = yes;
    die = yes;
    rehash = yes;
    nick_changes = yes;
    admin = yes;
};

/* connect {}: controls servers we connect to (OLD C:, N:, H:, L:) */

#connect {
#    /* name: the name of the server */
#    name = "irc.example.net";
#
#    /* host: the host or IP to connect to.  If a hostname is used it
#     * must match the reverse dns of the server.
#     */
#    host = "192.168.0.1";
#
#    /* passwords: the passwords we send (OLD C:) and accept (OLD N:).
#     * The remote server will have these passwords reversed.
#     */
#    send_password = "password";
#    accept_password = "anotherpassword";
#
#    /* encrypted: controls whether the accept_password above has been
#     * encrypted.  (OLD CRYPT_LINK_PASSWORD now optional per connect)
#     */
#    encrypted = no;
#
#    /* port: the port to connect to this server on */
#    port = 6666;
#
#    /* hub mask: the mask of servers that this server may hub. Multiple
#     * entries are permitted
#     */
#    hub_mask = "*";
#
#    /* leaf mask: the mask of servers this server may not hub.  Multiple
#     * entries are permitted.  Useful for forbidding EU -> US -> EU routes.
#     */
#    #leaf_mask = "*.uk";
#
#    /* class: the class this server is in */
#    class = "server";
#
#    /* autoconnect: controls whether we autoconnect to this server or not,
#     * dependent on class limits.
#     */
#    autoconn = no;
#    
#    /* compressed: controls whether traffic is compressed via ziplinks.
#     * By default this is disabled
#     */
#    #compressed = yes;
#
#    /* lazylink: controls whether this server is a LazyLink.  LazyLink 
#     * servers may NOT hub.  see doc/LazyLinks.as.implemented.txt
#     */
#    #lazylink = yes;
#
#    /* masking: the servername we pretend to be when we connect */
#    #fakename = "*.arpa";
#};

#connect {
#    name = "ipv6.some.server";
#    host = "3ffd:dead:beef::1";
#    send_password = "password";
#    accept_password = "password";
#    port = 6666;
#
#    /* aftype: controls whether the connection uses "ipv4" or "ipv6".
#     * Default is ipv4. */
#    aftype = ipv6;
#    class = "server";
#};

/* shared {}: users that are allowed to remote kline (OLD U:) */
shared {
    /* name: the server the user must be on to set klines.  If this is not
     * specified, the user will be allowed to kline from all servers.
     */
    name = "hybrid7.debian.local";

    /* user: the user@host mask that is allowed to set klines.  If this is
     * not specified, all users on the server above will be allowed to set
     * a remote kline.
     */
    user = "m3w2@localhost";
};

/* kill {}: users that are not allowed to connect (OLD K:)
 * Oper issued klines will be added to the specified kline config
 */
#kill {
#    user = "bad@*.hacked.edu";
#    reason = "Obviously hacked account";
#};

/* deny {}: IPs that are not allowed to connect (before DNS/ident lookup)
 * Oper issued dlines will be added to the specified dline config
 */
#deny {
#    ip = "10.0.1.0/24";
#    reason = "Reconnecting vhosted bots";
#};

/* exempt {}: IPs that are exempt from deny {} and Dlines. (OLD d:) */
exempt {
    ip = "192.168.0.0/16";
};

/* resv {}: nicks and channels users may not use/join (OLD Q:) */
resv {
    /* reason: the reason for the proceeding resv's */
    reason = "There are no services on this network";

    /* resv: the nicks and channels users may not join/use */
    nick = "nickserv";
    nick = "chanserv";
    channel = "#services";

    /* resv: wildcard masks are also supported in nicks only */
    reason = "Clone bots";
    nick = "clone*";
};

/* gecos {}:  The X: replacement, used for banning users based on their
 * "realname".  The action may be either:
 *      warn:   allow client to connect, but send message to opers
 *      reject: drop clients but also send message to opers.
 *      silent: silently drop clients who match.
 */
#gecos {
#    name = "*sex*";
#    reason = "Possible spambot";
#    action = warn;
#};

#gecos {
#    name = "sub7server";
#    reason = "Trojan drone";
#    action = reject;
#};

#gecos {
#    name = "*http*";
#    reason = "Spambot";
#    action = silent;
#};

/* The channel block contains options pertaining to channels */
channel {
    /* invex: Enable/disable channel mode +I, a n!u@h list of masks
     * that can join a +i channel without an invite.
     */
    use_invex = yes;

    /* except: Enable/disable channel mode +e, a n!u@h list of masks
     * that can join a channel through a ban (+b).
     */
    use_except = yes;

    /* knock: Allows users to request an invite to a channel that
     * is locked somehow (+ikl).  If the channel is +p or you are banned
     * the knock will not be sent.
     */
    use_knock = yes;

    /* knock delay: The amount of time a user must wait between issuing
     * the knock command.
     */
    knock_delay = 5 minutes;

    /* knock channel delay: How often a knock to any specific channel
     * is permitted, regardless of the user sending the knock.
     */
    knock_delay_channel = 1 minute;

    /* max chans: The maximum number of channels a user can join/be on. */
    max_chans_per_user = 15;
    
    /* quiet on ban: stop banned people talking in channels. */
    quiet_on_ban = yes;

    /* max bans: maximum number of +b/e/I modes in a channel */
    max_bans = 25;

    /* splitcode: the ircd will check every 60s as to whether splitmode
     * should be disabled or not, so there may be a delay between a
     * netsplit ending and splitmode ending.
     *
     * both split users and split servers must be true to enter splitmode
     * 
     * you may force splitmode to be permanent by /quote set splitmode on
     */

    /* split users: when the usercount is lower than this level, consider
     * ourselves split.  this must be set for automatic splitmode
     */
    default_split_user_count = 0;

    /* split servers: when the servercount is lower than this, consider
     * ourselves split.  this must be set for automatic splitmode
     */
    default_split_server_count = 0;

    /* split no create: disallow users creating channels on split. */
    no_create_on_split = no;

    /* split: no join: disallow users joining channels at all on a split */
    no_join_on_split = no;

    /* disable local channels: prevent users from joining &channels.
     * This is extreme, but it is still a flaw in serverhide.  It will
     * however remove far more from users than it will give back in
     * security.
     */
    disable_local_channels = no;
};


/* The serverhide block contains the options regarding serverhiding */
serverhide {
    /* flatten links: this option will show all servers in /links appear
     * that they are linked to this current server
     */
    flatten_links = no;

    /* links delay: how often to update the links file when it is
     * flattened.
     */
    links_delay = 5 minutes;

    /* hidden: hide this server from a /links output on servers that
     * support it.  this allows hub servers to be hidden etc.
     */
    hidden = no;

    /* disable hidden: prevent servers hiding themselves from a
     * /links ouput.
     */
    disable_hidden = no;

    /* hide servers: hide remote servernames everywhere and instead use
     * network_name and network_desc.
     */
    hide_servers = no;
};

/* The general block contains many of the options that were once compiled
 * in options in config.h.  The general block is read at start time.
 */
general {
    /* oper pass resv: allow opers to over-ride RESVs on nicks/channels */
    oper_pass_resv = yes;

    /* disable remote: disable users doing commands on remote servers */
    disable_remote_commands = no;

    /* floodcount: the default value of floodcount that is configurable
     * via /quote set floodcount.  This is the amount of lines a user
     * may send to any other user/channel in one second.
     */
        default_floodcount = 10;

    /* failed oper notice: send a notice to all opers on the server when 
     * someone tries to OPER and uses the wrong password, host or ident.
     */
    failed_oper_notice = yes;

    /* dots in ident: the amount of '.' characters permitted in an ident
     * reply before the user is rejected.
     */
    dots_in_ident=2;

    /* dot in ipv6: ircd-hybrid-6.0 and earlier will disallow hosts 
     * without a '.' in them.  this will add one to the end.  only needed
     * for older servers.
     */
        dot_in_ip6_addr = yes;
        
    /* min nonwildcard: the minimum non wildcard characters in k/d/g lines
     * placed via the server.  klines hand placed are exempt from limits.
     * wildcard chars: '.' '*' '?' '@'
     */
    min_nonwildcard = 4;

    /* max accept: maximum allowed /accept's for +g usermode */
    max_accept = 20;

    /* nick flood: enable the nickflood control code */
    anti_nick_flood = yes;

    /* nick flood: the nick changes allowed in the specified period */
    max_nick_time = 20 seconds;
    max_nick_changes = 5;

    /* anti spam time: the minimum time a user must be connected before
     * custom quit messages are allowed.
     *
     * The upstream default is 2 minutes.
     */
        anti_spam_exit_message_time = 0 minutes;

    /* ts delta: the time delta allowed between server clocks before
     * a warning is given, or before the link is dropped.  all servers
     * should run ntpdate/rdate to keep clocks in sync
     */
    ts_warn_delta = 30 seconds;
    ts_max_delta = 5 minutes;

    /* kline reason: show the user the reason why they are k/d/glined 
     * on exit.  may give away who set k/dline when set via tcm.
     */
    kline_with_reason = yes;

    /* kline connection closed: make the users quit message on channels
     * to be "Connection closed", instead of the kline reason.
     */
#    kline_with_connection_closed = no;

    /* warn no nline: warn opers about servers that try to connect but
     * we dont have a connect {} block for.  Twits with misconfigured 
     * servers can get really annoying with this enabled.
     */
    warn_no_nline = yes;

    /* stats o oper only: make stats o (opers) oper only */
    stats_o_oper_only=yes;

    /* stats P oper only: make stats P (ports) oper only */
    stats_P_oper_only=no;

    /* stats i oper only: make stats i (auth {}) oper only. set to:
     *     yes:    show users no auth blocks, made oper only.
     *     masked: show users first matching auth block
     *     no:     show users all auth blocks.
     */
    stats_i_oper_only=masked;

    /* stats k/K oper only: make stats k/K (klines) oper only.  set to:
     *     yes:    show users no auth blocks, made oper only
     *     masked: show users first matching auth block
     *     no:     show users all auth blocks.
     */
    stats_k_oper_only=masked;
                                    
    /* caller id wait: time between notifying a +g user that somebody
     * is messaging them.
     */
    caller_id_wait = 1 minute;

    /* pace wait simple: time between use of less intensive commands
     * (HELP, remote WHOIS, WHOWAS)
     */
    pace_wait_simple = 1 second;

    /* pace wait: time between more intensive commands
     * (ADMIN, INFO, LIST, LUSERS, MOTD, STATS, VERSION)
     */
    pace_wait = 10 seconds;

    /* short motd: send clients a notice telling them to read the motd
     * instead of forcing a motd to clients who may simply ignore it.
     */
    short_motd = no;

    /* ping cookies: require clients to respond exactly to a ping command,
     * can help block certain types of drones and FTP PASV mode spoofing.
     */
    ping_cookie = no;

    /* no oper flood: increase flood limits for opers. */
    no_oper_flood = yes;

    /* true no oper flood: completely eliminate flood limits for opers
         * and for clients with can_flood = yes in their auth {} blocks
     */
    true_no_oper_flood = yes;

    /* idletime: the maximum amount of time a user may idle before
     * they are disconnected
     */
        idletime = 0;

    /* REMOVE ME.  The following line checks you've been reading. */
    # havent_read_conf = 1;
    
    /* max targets: the maximum amount of targets in a single 
     * PRIVMSG/NOTICE.  set to 999 NOT 0 for unlimited.
     */
    max_targets = 4;

    /* client flood: maximum number of lines in a clients queue before
     * they are dropped for flooding.
     */
    client_flood = 20;

    /* message locale: the default message locale if gettext() is enabled
     * and working.
     * Use "custom" for the (in)famous Hybrid custom messages.
     * Use "standard" for the compiled in defaults.
     */
    message_locale = "standard";

    /* usermodes configurable: a list of usermodes for the options below
     *
     * +b - bots       - See bot and drone flooding notices
     * +c - cconn      - Client connection/quit notices
     * +d - debug      - See debugging notices
     * +f - full       - See I: line full notices
     * +g - callerid   - Server Side Ignore
     * +i - invisible  - Not shown in NAMES or WHO unless you share a 
     *                   a channel
     * +k - skill      - See server generated KILL messages
     * +l - locops     - See LOCOPS messages
     * +n - nchange    - See client nick changes
     * +r - rej        - See rejected client notices
     * +s - servnotice - See general server notices
     * +u - unauth     - See unauthorized client notices
     * +w - wallop     - See server generated WALLOPS
     * +x - external   - See remote server connection and split notices
     * +y - spy        - See LINKS, STATS, TRACE notices etc.
     * +z - operwall   - See oper generated WALLOPS
     */
     
    /* oper only umodes: usermodes only opers may set */
    oper_only_umodes = bots, cconn, debug, full, skill, nchange, 
                     rej, spy, external, operwall, locops, unauth;

    /* oper umodes: default usermodes opers get when they /oper */
    oper_umodes = locops, servnotice, operwall, wallop;

    /* servlink path: path to 'servlink' program used by ircd to handle
     * encrypted/compressed server <-> server links.
     *
     * unless you move servlink around (???), you shouldn't define this.
     */
    #servlink_path = "/usr/lib/ircd-hybrid/servlink";

    /* default cipher: default cipher to use for cryptlink when none is
     * specified in connect block.
     */
    default_cipher_preference = "BF/128";

    /* use egd: if your system does not have *random devices yet you
     * want to use OpenSSL and encrypted links, enable this.  Beware -
     * EGD is *very* CPU intensive when gathering data for its pool
     */
    #use_egd = yes;

    /* egdpool path: path to EGD pool. Not necessary for OpenSSL >= 0.9.7
     * which automatically finds the path.
     */
    #egdpool_path = "/var/run/egd-pool";


    /* compression level: level of compression for compressed links between
     * servers.  
     *
     * values are between: 1 (least compression, fastest)
     *                and: 9 (most compression, slowest).
     */
    #compression_level = 6;

    /* throttle time: the minimum amount of time between connections from
     * the same ip.  exempt {} blocks are excluded from this throttling.
     * Offers protection against flooders who reconnect quickly.  
     * Set to 0 to disable.
     */
    throttle_time = 10;
};

glines {
    /* enable: enable glines, network wide temp klines */
    enable = yes;

    /*
     * duration: the amount of time a gline will remain on your
     * server before expiring
     */
    duration = 1 day;

    /*
     * logging: which types of rules you want to log when triggered
     * (choose reject or block)
     */
    logging = reject, block;

    /*
     * NOTE: gline ACLs can cause a desync of glines throughout the
     * network, meaning some servers may have a gline triggered, and
     * others may not. Also, you only need insert rules for glines
     * that you want to block and/or reject. If you want to accept and
     * propagate the gline, do NOT put a rule for it.
     */

    /* user@host for rule to apply to */
    user = "god@I.still.hate.packets";
    /* server for rule to apply to */
    name = "hades.arpa";

    /*
     * action: action to take when a matching gline is found. options are:
     *  reject    - do not apply the gline locally
     *  block    - do not propagate the gline
     */
    action = reject, block;

    user = "god@*";
    name = "*";
    action = block;
};

modules {
    /* module path: paths to search for modules specified below and 
     * in /modload.
     */
    path = "/usr/lib/ircd-hybrid/modules";
    path = "/usr/lib/ircd-hybrid/modules/autoload";

    /* module: the name of a module to load on startup/rehash */
    module = "m_tburst.so";
};
```How i generated the cert:
```
m3w2@ubuntu:~$ sudo su
root@ubuntu:/home/m3w2# cd /usr/local/ircd/etc/
root@ubuntu:/usr/local/ircd/etc# openssl genrsa -out rsa.key 2048
Generating RSA private key, 2048 bit long modulus
................................................................+++
................................................................+++
e is 65537 (0x10001)
root@ubuntu:/usr/local/ircd/etc# openssl rsa -in rsa.key -pubout -out rsa.pub
writing RSA key
root@ubuntu:/usr/local/ircd/etc# chown irc.irc rsa.key rsa.pub 
root@ubuntu:/usr/local/ircd/etc# chmod 0600 rsa.key 
root@ubuntu:/usr/local/ircd/etc# chmod 0644 rsa.pub 
root@ubuntu:/usr/local/ircd/etc# openssl req -new -days 365 -x509 -key rsa.key -out cert.pem
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
Country Name (2 letter code) [AU]:TE
State or Province Name (full name) [Some-State]:Test
Locality Name (eg, city) []:Test
Organization Name (eg, company) [Internet Widgits Pty Ltd]:Test
Organizational Unit Name (eg, section) []:Test
Common Name (eg, YOUR name) []:Test
Email Address []:test@test.test
root@ubuntu:/usr/local/ircd/etc# 

```

---

### Post by m3w2 on 2010-05-18
I found the solutions to my problems. So I guess it's best to post it here if someone else need help in the future.

1. The repo version doesn't have SSL-encryption enabled.

2. The building error on the source verison from [ircd-hybrid.org]("http://prdownloads.sourceforge.net/ircd-hybrid/ircd-hybrid-7.2.3.tgz") only appears on 64-bits systems, so use a 32-bits instead.

3. I chown'ed the wrong user for the files rsa.key rsa.pub (pretty stupid of me).

---

### Post by davantalus on 2011-04-01
Looks like the compile error is addressed in the latest "current" found here: [http://www.ircd-hybrid.org/snapshot/](http://www.ircd-hybrid.org/snapshot/)  It's named: ircd-hybrid-7.3-STABLE-20110227_1130.tgz

I tried 7.2.x first and had the same bracket error... couldn't find the 32-bit release you spoke of but ended up finding the 7.3 release on accident.

Here's some notes from my install process for anyone attempting this.

I ended up installing from from dist first. I removed it... but it left a bunch of config stuff lying around... So I'm using that for start on boot and such.

Download the newest ircd-hybrid to your home folder and cd into it.
./configure --prefix="/usr/local/ircd" --enable-syslog --enable-openssl="/your/ssldirectory"
sudo su
make
make install
cd /usr/local/ircd/etc
openssl genrsa -out rsa.key 2048
openssl rsa -in rsa.key -pubout -out rsa.pub
openssl req -new -days 365 -x509 -key rsa.key -out cert.pem 
	...and fill in the blanks with something reasonable.
ln -s /usr/local/ircd/sbin/ircd /usr/sbin/ircd-hybrid

You may or may not need to add the startup stuff... The dist default seems to be 20/20 so: 
update-rc.d ircd-hybrid defaults 20 20

---

### Post by m3w2 on 2011-10-10
Hello! I'm back!

I had to re-install ircd-hybrid again. This time I used Debian and thanks to [**this bug report**]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=497960") found a very simple solution. I think it should work on Ubuntu as well:


First of all, install all dependencies and get the source:
```
m3w2@box:~/$ uname -a
Linux box 2.6.32-bpo.5-amd64 #1 SMP Fri Jun 11 08:42:31 UTC 2010 x86_64 GNU/Linux
m3w2@box:~/$ sudo apt-get build-dep ircd-hybrid
m3w2@box:~/$ sudo apt-get install openssl libssl-dev
m3w2@box:~/$ sudo apt-get source ircd-hybrid
```

Next we need to edit some files:

Enable SSL by adding a line to:
./ircd-hybrid-7.2.2.dfsg.2/debian/rules:

```

...

# Some useful stuff to edit here.
# Beware: TOPICLEN may not exceed 390.
NICKLEN = 15
TOPICLEN = 350
MAXCLIENTS = 200
**USE_OPENSSL = 1**

...
```


Fix a bug by modifying line 74 in:
./ircd-hybrid-7.2.2.dfsg.2/debian/patches/19_sslonly.dpatch:
```

...

**+        if (F && !F->ssl && strcmp(source_p->sockhost, "127.0.0.1"))**

...
```

Rebuild the deb-file and install it:

```
m3w2@box:~/ircd-hybrid-7.2.2.dfsg.2$ dpkg-buildpackage -rfakeroot -uc -b
m3w2@box:~/$ dpkg -i ircd-hybrid_7.2.2.dfsg.24+lenny1.ssl1_amd64.deb
```

Customize your /etc/ircd-hybrid/ircd.conf and you're done!

---

### Post by sandman887 on 2012-01-28
what is the absolute path of

```
./ircd-hybrid-7.2.2.dfsg.2/debian/rules:
```

?

---

### Post by danstinebaugh on 2012-02-22
This is a great help and worked flawlessly! Thanks alot M3w2!
Now I just need to figure out why hybserv isn't connecting. Thanks for the post, it really made getting the source files and compiling really easy!

(might have said cd .. before the dpkg -i option but I figured it out eventually lol)

---

### Post by hradek on 2013-01-02
Trying to build it today. The instructions posted above are excellent. However, OpenSSL is never included. It appears the current version has removed a few popular and necessary requirements such as RC5 or MD5 support which makes this not work. 

I am trying to see about downgrading to a previous version of OpenSSL. What a crock.

---

### Post by hradek on 2013-01-02
So I have been trying to build and just to clarify, here is the ./configure output:

```
Compiling ircd-hybrid 7.2.2

Installing into: /usr
Ziplinks ................ yes
OpenSSL ................. no
Modules ................. shared
IPv6 support ............ yes
Net I/O implementation .. sigio
EFnet server ............ no (use example.conf)
Halfops support ......... yes
Small network ........... no
G-Line voting ........... yes
```

I followed the code path and it is finding the libraries but seems to be failing here:

```
checking for OpenSSL... /usr
checking for OpenSSL 0.9.6 or above... found
checking for RSA_free in -lcrypto... yes
checking for EVP_bf_cfb... no
checking for EVP_cast5_cfb... no
checking for EVP_idea_cfb... no
checking for EVP_rc5_32_12_16_cfb... no
checking for EVP_des_ede3_cfb... no
checking for EVP_des_cfb... no
```

Which if you look into the configure script you'll see that at least one of the encryption libraries need to be enabled. 

I've rebuilt and installed OpenSSL with the enable-rc5 and other flags but no dice.

This is on Ubuntu 12.04. Help? Anyone? I'd like to enable SSL on IRC on my personal server. Apparently I can't create a new post so here I go.

---

### Post by m3w2 on 2013-01-14
> **hradek said:**
> Trying to build it today. The instructions posted above are excellent. However, OpenSSL is never included. It appears the current version has removed a few popular and necessary requirements such as RC5 or MD5 support which makes this not work. 

I am trying to see about downgrading to a previous version of OpenSSL. What a crock.

I just happened to drop by here, so I ran a test install on a fresh 12.04 32-bits.

I followed my own instruction, but I did not really understand what I had modified in *19_sslonly.dpatch*, since the lines looked the same to me. However, I followed the rest of the guide, fired up xchat, connected to "*localhost/6670*", checked "*Use SSL for all the servers on this network*" and "*Accept invalid SSL certificate*" and it just worked.

```
$ openssl version
OpenSSL 1.0.1 14 Mar 2012

```

---

### Post by hradek on 2013-01-22
Thanks for the reply. My problem is that I can't get OpenSSL to have any of the required ciphers. Check your configure output. This is what you posted above:

[INDENT]checking for OpenSSL... /usr
checking for OpenSSL 0.9.6 or above... found
checking for RSA_free in -lcrypto... yes
checking for EVP_bf_cfb... yes
checking for EVP_cast5_cfb... yes
checking for EVP_idea_cfb... no
checking for EVP_rc5_32_12_16_cfb... no
checking for EVP_des_ede3_cfb... yes
checking for EVP_des_cfb... yes[/INDENT]

All the lines with EVP... have NO. Some of yours have yes. I have no idea how to fix this!

---

### Post by blindenvy on 2013-02-17
I am having the same issue. I followed the same instructions but whenever I try and connect I get "Irssi: warning SSL handshake failed: Connection refused"

My outputs when building:

Compiling ircd-hybrid 7.2.2

Installing into: /usr
Ziplinks ................ yes
OpenSSL ................. no
Modules ................. shared
IPv6 support ............ yes
Net I/O implementation .. sigio
EFnet server ............ no (use example.conf)
Halfops support ......... yes
Small network ........... no
G-Line voting ........... yes

Configured limits:
NICKLEN ................. 15
TOPICLEN ................ 350

and

checking for usleep... yes
checking for OpenSSL... /usr
checking for OpenSSL 0.9.6 or above... found
checking for RSA_free in -lcrypto... yes
checking for EVP_bf_cfb... no
checking for EVP_cast5_cfb... no
checking for EVP_idea_cfb... no
checking for EVP_rc5_32_12_16_cfb... no
checking for EVP_des_ede3_cfb... no
checking for EVP_des_cfb... no
checking zlib.h usability... yes
checking zlib.h presence... yes

Further information:

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise

$ uname -a
Linux d6-1 3.2.0-37-generic #58-Ubuntu SMP Thu Jan 24 15:28:10 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

I can connect no problem when not trying to use SSL. Any Ideas?

---

### Post by blindenvy on 2013-02-17
It turns out it wasn't a problem with ircd but was a problem with the client I was trying to use. When using irssi I had to supply it the port along with the -ssl option. i.e. /connect -ssl server.com 6670

---

### Post by MadEgg on 2013-07-17
Dunno if it helps anyone, but I had the same issue with no ciphers being available, and therefore, no SSL support being compiled. I fixed this by editing the configure file in the ircd-hybrid dir and look for lines l

```

for ac_func in EVP_bf_cfb

```

Basically, the term you're looking for is EVP. If you add 64 after each of these strings and then try creating the package again, it will find the available ciphers and will enable SSL support.

For example, the line above would become

```

for ac_func in EVP_bf_cfb64

```

---

### Post by craiger2 on 2014-03-27
It took me a while to get it working, here's my notes:

ircd-hybrid is a mess on debian's openssl.  Also it refuses to run as root, which is a challenge if you're required to use a port lower than 1024, which is typically a requirement for ssl/authentication/encryption things.

build from source and put "USE_OPENSSL = 1" in debian/rules
edit configure and configure.ac, append "64" to ssl protocols:


configure:
  for ac_func in EVP_bf_cfb64   #append 64


configure.ac:
   AC_CHECK_FUNCS(EVP_bf_cfb64,   #append 64


edit /etc/init.d/ircd-hybrid
   -u irc -c irc     # change to root and root (on start and restart)


edit src/ircd.c
  if (geteuid() == 0)
  {
  /*    fprintf(stderr, "Don't run ircd as root!!!\n");
    return(-1);
  */
    fprintf(stderr, "Running as root.\n");
  }




I hope this saves four hours for other people.

---

