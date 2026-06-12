---
title: "ircd-hybrid with openssl .9.8c"
date: 2007-06-15
forum: Server Platforms
---

### Post by anxean on 2007-06-15
Hey, I'm trying to make this ssl work for irc, but I receive these messages:

asdf@asdf-desktop:~$ sudo openssl s_server -accept 6666 -nocert -bugs -chain -timeout
Using default temp DH parameters
Using default temp ECDH parameters
ACCEPT
ERROR
6472:error:140760FC:SSL routines:SSL23_GET_CLIENT_HELLO:unknown protocol:s23_srvr.c:562:
shutting down SSL
CONNECTION CLOSED
ACCEPT
**^SSL output**

01:20 -!- Irssi: Connection to ip.goes.here.169 established
01:20 -!- Irssi: Connection lost to ip.goes.here.169
**^IRC output**

Any ideas?

-anxean

---

### Post by anxean on 2007-06-15
* Looking up *4.146.80.169
* Connecting to *4.146.80.169 (*4.146.80.169) port 9999...
* * Certification info:
*  Subject:
*    C=UN
*    ST=Milky Way
*    L=Earth
*    O=IRCD-Hybrid services
*    OU=IRCD-Hybrid services
*    CN=Debian
*    emailAddress=root@localhost
*  Issuer:
*    C=UN
*    ST=Milky Way
*    L=Earth
*    O=IRCD-Hybrid services
*    OU=IRCD-Hybrid services
*    CN=Debian
*    emailAddress=root@localhost
*  Public key algorithm: rsaEncryption (2048 bits)
*  Public key algorithm uses ephemeral key with 2699 bits
*  Sign algorithm sha1WithRSAEncryption (0 bits)
*  Valid since Jun 15 08:43:16 2007 GMT to Jun 14 08:43:16 2008 GMT
* * Cipher info:
*  Version: TLSv1/SSLv3, cipher AES256-SHA (256 bits)
* * Verify E: self signed certificate.? (18) -- Ignored
* Connected. Now logging in...
* *** Spoofing your IP. congrats.
* *** You are exempt from K/D/G lines. congrats.
* *** You are exempt from user limits. congrats.
* Welcome to the focus Internet Relay Chat Network asdf
* Your host is focus[*4.146.80.169/9999], running version hybrid-7.0.3
* This server was created Thu Apr 21 2005 at 01:14:37 IST
* focus hybrid-7.0.3 oiwszcerkfydnxbaugl biklmnopstveIha bkloveIh
* WALLCHOPS KNOCK EXCEPTS INVEX MODES=4 MAXCHANNELS=15 MAXBANS=25 MAXTARGETS=4 NICKLEN=15 TOPICLEN=350 KICKLEN=350 :are supported by this server
* CHANTYPES=#& PREFIX=(ohv)@%+ CHANMODES=eIb,k,l,imnpst NETWORK=focus CASEMAPPING=rfc1459 CALLERID :are supported by this server
* There are 0 users and 1 invisible on 1 servers
* I have 1 clients and 0 servers
* Current local  users: 1  Max: 1
* Current global users: 1  Max: 1
* Highest connection count: 1 (1 clients) (1 connections received)
* - focus Message of the Day -
* -     
* - ___.  .__                              _____                         
* - \_ |__ |__| ____ _____ _______ ___.__._/ ____\____  ____  __ __  ______
* -  | __ \|  |/    \\__  \\_  __ <  |  |\  __\/  _ \_/ ___\|  |  \/  ___/
* -  | \_\ \  |  |  \/ __ \|  | \/\___  | |  | (  <_> )  \___|  |  /\___ \
* -  |___  /__|___|  (____  /__|  / ____| |__|  \____/ \___  >____//____  >
* -      \/        \/    \/      \/                      \/          \/
* -    OBEY THE RULES
* -                  .88888888:.  No Listing
* -                88888888.88888.  No Botting
* -              .8888888888888888.  Have Fun!!
* -              888888888888888888
* -              88' _`88'_  `88888
* -              88 () 88 ()  88888
* -              88_88_::_88_:88888
* -              88:::,::,:::::8888
* -              88`:::::::::'`8888
* -              .88  `::::'    8:88.
* -            8888            `8:888.
* -          .8888'            `888888.
* -          .8888:..  .::.  ...:'8888888:.
* -        .8888.'    :'    `'::`88:88888
* -        .8888        '        `.888:8888.
* -      888:8        .          888:88888
* -    .888:88        .:          888:88888:
* -    8888888.      ::          88:888888
* -    `.::.888.      ::          .88888888
* -    .::::::.888.    ::        :::`8888'.:.
* -  ::::::::::.888  '        .::::::::::::
* -  ::::::::::::.8    '      .:8::::::::::::.
* -  .::::::::::::::.        .:888:::::::::::::
* -  :::::::::::::::88:.__..:88888:::::::::::'
* -  `'.:::::::::::88888888888.88:::::::::'
* -        `':::_:' -- '' -'-' `':_::::'`
* End of /MOTD command.
* asdf sets mode +i asdf
* Found your IP: [*4.146.80.169]
* asdf sets mode +s asdf

if anyone needs help with this they can pm me

---

