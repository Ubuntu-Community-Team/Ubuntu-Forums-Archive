---
title: "Server keeps sending spam!"
date: 2014-07-18
forum: Server Platforms
---

### Post by chaemil on 2014-07-18
Hi. My virtual Ubuntu server keeps sending spam for some time... Nothing shows up in the mail.log, relay server is disabled and etc... is there a way to determine which script or whathever is sending those emails? Thank you!

---

### Post by TheFu on 2014-07-19
lsof
netstat
and enable the outbound firewall, but at this point, I'd wipe the server since it has clearly been compromised.  It has been hacked and before bringing it up, I'd want to know how.  

What services does it provide? web, ftp, dns, email, something else?
Are passwords used for authentication? Key-based auth is better.

I've posted links to what crackers do with Linux systems here a few times. Makes for interesting reading.

---

### Post by chaemil on 2014-07-19
Ok i will look for that... but i really dont want to wipe my server... 

The server offers webhosting, ftp, email. We are using apssword protection not key based.

---

### Post by TheFu on 2014-07-19
You are in denial.  Sleep on it, but the company really should tell all the clients it has been compromised and wipe it. It may be legally required.

---

### Post by SeijiSensei on 2014-07-20
I'd run over to [mxtoolbox]("http://mxtoolbox.com/blacklists.aspx") and see if your server has been blacklisted.

Have any machines that connect to the Internet using the server as a gateway?  One of them could be compromised.

---

### Post by chaemil on 2014-07-21
No server using it as a gateway.... I'm blacklisted at Lashback... nowhere else... Is the senderbase.org log reliable? bcs that's how i suppose the server is sending spam...

---

### Post by TheFu on 2014-07-21
What happened with **lsof**?  If the email is being sent directly, the program sending it should jump out with lsof.

---

### Post by chaemil on 2014-07-22
lsof output is very long here's example...

didnt understand it a lot :/

```
php5-cgi  22580               moskalykova  mem       REG              251,0     92752     391918 /lib/libz.so.1.2.3.3php5-cgi  22580               moskalykova  mem       REG              251,0     43296     411302 /lib/libcrypt-2.11.1.so
php5-cgi  22580               moskalykova  mem       REG              251,0    136936     411291 /lib/ld-2.11.1.so
php5-cgi  22580               moskalykova    0u     unix 0xffff88007cf0b500       0t0    3823357 /var/lib/apache2/fcgid/sock/14208.5
php5-cgi  22580               moskalykova    1w      REG              251,0     34048     657249 /var/log/apache2/error.log
php5-cgi  22580               moskalykova    2w      REG              251,0     34048     657249 /var/log/apache2/error.log
php5-cgi  22580               moskalykova   42r     FIFO                0,8       0t0    3790765 pipe
php5-cgi  22580               moskalykova   45w     FIFO                0,8       0t0    3790766 pipe
php5-cgi  25518    beautystudiosalamounka  cwd       DIR              251,0      4096     400208 /home/beautystudiosalamounka/fcgi-bin
php5-cgi  25518    beautystudiosalamounka  rtd       DIR              251,0      4096          2 /
php5-cgi  25518    beautystudiosalamounka  txt       REG              251,0   7836616     134735 /usr/bin/php5-cgi
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0     92552     401124 /lib/libgcc_s.so.1
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0     51712     411283 /lib/libnss_files-2.11.1.so
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0     31120     134742 /usr/lib/php5/20090626/pdo_mysql.so
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0    100776     173053 /usr/lib/php5/20090626/pdo.so
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0    123576     134740 /usr/lib/php5/20090626/mysqli.so
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0   2164720     138577 /usr/lib/libmysqlclient_r.so.16.0.0
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0     51328     135630 /usr/lib/php5/20090626/mysql.so
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0    187752     154004 /usr/lib/libmcrypt.so.4.4.8
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0     43752     154024 /usr/lib/php5/20090626/mcrypt.so
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0     22560     144274 /usr/lib/libXdmcp.so.6.0.0
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0     14488     144272 /usr/lib/libXau.so.6.0.0
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0    165984     402822 /lib/libexpat.so.1.5.2
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0    113072     133439 /usr/lib/libxcb.so.1.1.0
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0    216832     149504 /usr/lib/libfontconfig.so.1.4.4
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0    146032     131231 /usr/lib/libjpeg.so.62.0.0
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0    158736     401035 /lib/libpng12.so.0.42.0
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0     68432     149508 /usr/lib/libXpm.so.4.11.0
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0   1269216     133867 /usr/lib/libX11.so.6.3.0
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0    547112     134257 /usr/lib/libfreetype.so.6.3.22
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0    295568     154039 /usr/lib/libt1.so.5.1.2
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0    270304     149510 /usr/lib/libgd.so.2.0.0
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0    116856     173050 /usr/lib/php5/20090626/gd.so
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0     10224     391937 /lib/libkeyutils-1.2.so
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0     31168     133416 /usr/lib/libkrb5support.so.0.1
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0    135745     411279 /lib/libpthread-2.11.1.so
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0     93000     411270 /lib/libresolv-2.11.1.so
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0   1626400     397338 /lib/libcrypto.so.0.9.8
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0   1588616     411299 /lib/libc-2.11.1.so
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0   1372344     130612 /usr/lib/libxml2.so.2.7.6
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0     14584     399113 /lib/libcom_err.so.2.1
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0    154048     131977 /usr/lib/libk5crypto.so.3.1
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0    803192     134284 /usr/lib/libkrb5.so.3.3
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0    213784     131997 /usr/lib/libgssapi_krb5.so.2.2
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0     97256     411305 /lib/libnsl-2.11.1.so
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0     14696     411284 /lib/libdl-2.11.1.so
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0    534832     411315 /lib/libm-2.11.1.so
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0     31744     411271 /lib/librt-2.11.1.so
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0    186440     391764 /lib/libpcre.so.3.12.1
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0     70912     420868 /lib/libbz2.so.1.0.4
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0   1494424     130749 /usr/lib/libdb-4.8.so
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0    342192     397755 /lib/libssl.so.0.9.8
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0     92752     391918 /lib/libz.so.1.2.3.3
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0     43296     411302 /lib/libcrypt-2.11.1.so
php5-cgi  25518    beautystudiosalamounka  mem       REG              251,0    136936     411291 /lib/ld-2.11.1.so
php5-cgi  25518    beautystudiosalamounka    0u     unix 0xffff8800643cec00       0t0    3832438 /var/lib/apache2/fcgid/sock/14208.6
php5-cgi  25518    beautystudiosalamounka    1w      REG              251,0     34048     657249 /var/log/apache2/error.log
php5-cgi  25518    beautystudiosalamounka    2w      REG              251,0     34048     657249 /var/log/apache2/error.log
php5-cgi  25518    beautystudiosalamounka   42r     FIFO                0,8       0t0    3790765 pipe
php5-cgi  25518    beautystudiosalamounka   45w     FIFO                0,8       0t0    3790766 pipe
master    29169                      root  cwd       DIR              251,0      4096     530730 /var/spool/postfix
master    29169                      root  rtd       DIR              251,0      4096          2 /
master    29169                      root  txt       REG              251,0     39016     132957 /usr/lib/postfix/master
master    29169                      root  mem       REG              251,0     51712     411283 /lib/libnss_files-2.11.1.so
master    29169                      root  mem       REG              251,0     43552     411304 /lib/libnss_nis-2.11.1.so
master    29169                      root  mem       REG              251,0     35712     411309 /lib/libnss_compat-2.11.1.so
master    29169                      root  mem       REG              251,0    135745     411279 /lib/libpthread-2.11.1.so
master    29169                      root  mem       REG              251,0     92752     391918 /lib/libz.so.1.2.3.3
master    29169                      root  mem       REG              251,0     14696     411284 /lib/libdl-2.11.1.so
master    29169                      root  mem       REG              251,0   1588616     411299 /lib/libc-2.11.1.so
master    29169                      root  mem       REG              251,0     93000     411270 /lib/libresolv-2.11.1.so
master    29169                      root  mem       REG              251,0     97256     411305 /lib/libnsl-2.11.1.so
master    29169                      root  mem       REG              251,0   1494424     130749 /usr/lib/libdb-4.8.so
master    29169                      root  mem       REG              251,0    105232     137634 /usr/lib/libsasl2.so.2.0.23
master    29169                      root  mem       REG              251,0   1626400     397338 /lib/libcrypto.so.0.9.8
master    29169                      root  mem       REG              251,0    342192     397755 /lib/libssl.so.0.9.8
master    29169                      root  mem       REG              251,0    216536     132983 /usr/lib/libpostfix-util.so.1.0.1
master    29169                      root  mem       REG              251,0    232120     132980 /usr/lib/libpostfix-global.so.1.0.1
master    29169                      root  mem       REG              251,0    136936     411291 /lib/ld-2.11.1.so
master    29169                      root    0u      CHR                1,3       0t0        791 /dev/null
master    29169                      root    1u      CHR                1,3       0t0        791 /dev/null
master    29169                      root    2u      CHR                1,3       0t0        791 /dev/null
master    29169                      root    3u     unix 0xffff88007c83c900       0t0    2195199 socket
master    29169                      root    4u      CHR                1,3       0t0        791 /dev/null
master    29169                      root    5u      CHR                1,3       0t0        791 /dev/null
master    29169                      root    6u      CHR                1,3       0t0        791 /dev/null
master    29169                      root    7u      CHR                1,3       0t0        791 /dev/null
master    29169                      root    8u      CHR                1,3       0t0        791 /dev/null
master    29169                      root    9uW     REG              251,0        33     522354 /var/spool/postfix/pid/master.pid
master    29169                      root   10uW     REG              251,0        33     659041 /var/lib/postfix/master.lock
master    29169                      root   11r     FIFO                0,8       0t0    2195333 pipe
master    29169                      root   12u     IPv4            2195211       0t0        TCP *:smtp (LISTEN)
master    29169                      root   13u     0000                0,9         0        781 anon_inode
master    29169                      root   14u     unix 0xffff88007c83c300       0t0    2195212 socket
master    29169                      root   15u     unix 0xffff88007c83c600       0t0    2195213 socket
master    29169                      root   16u     FIFO              251,0       0t0     522339 /var/spool/postfix/public/pickup
master    29169                      root   17u     unix 0xffff88007c83d800       0t0    2195215 socket
master    29169                      root   18u     unix 0xffff88007c83d200       0t0    2195216 socket
master    29169                      root   19u     unix 0xffff88007c83d500       0t0    2195217 public/cleanup
master    29169                      root   20u     unix 0xffff88007c83c000       0t0    2195219 socket
master    29169                      root   21u     unix 0xffff88007c83cf00       0t0    2195220 socket
master    29169                      root   22u     FIFO              251,0       0t0     522341 /var/spool/postfix/public/qmgr
master    29169                      root   23u     unix 0xffff88007c83cc00       0t0    2195222 socket
master    29169                      root   24u     unix 0xffff88006384ec00       0t0    2195223 socket
master    29169                      root   25u     unix 0xffff88006384f800       0t0    2195224 private/tlsmgr
master    29169                      root   26u     unix 0xffff88006384ef00       0t0    2195226 socket
master    29169                      root   27u     unix 0xffff88006384e900       0t0    2195227 socket
master    29169                      root   28u     unix 0xffff88006384f200       0t0    2195228 private/rewrite
master    29169                      root   29u     unix 0xffff8800640fc300       0t0    2195230 socket
master    29169                      root   30u     unix 0xffff8800640fdb00       0t0    2195231 socket
master    29169                      root   31u     unix 0xffff8800640fc000       0t0    2195232 private/bounce
master    29169                      root   32u     unix 0xffff8800640fcc00       0t0    2195234 socket
master    29169                      root   33u     unix 0xffff8800640fc900       0t0    2195235 socket
master    29169                      root   34u     unix 0xffff8800640fcf00       0t0    2195236 private/defer
master    29169                      root   35u     unix 0xffff8800640fd200       0t0    2195238 socket
master    29169                      root   36u     unix 0xffff88006380a300       0t0    2195239 socket
master    29169                      root   37u     unix 0xffff88006380b200       0t0    2195240 private/trace
master    29169                      root   38u     unix 0xffff88006380af00       0t0    2195242 socket
master    29169                      root   39u     unix 0xffff88006380bb00       0t0    2195243 socket
master    29169                      root   40u     unix 0xffff88006380b800       0t0    2195244 private/verify
master    29169                      root   41u     unix 0xffff88006380b500       0t0    2195246 socket
master    29169                      root   42u     unix 0xffff88007b535800       0t0    2195247 socket
master    29169                      root   43u     unix 0xffff88007b534000       0t0    2195248 public/flush
master    29169                      root   44u     unix 0xffff88007b535b00       0t0    2195250 socket
master    29169                      root   45u     unix 0xffff88007b534600       0t0    2195251 socket
master    29169                      root   46u     unix 0xffff880064429200       0t0    2195252 private/proxymap
master    29169                      root   47u     unix 0xffff880064429800       0t0    2195254 socket
master    29169                      root   48u     unix 0xffff880064428c00       0t0    2195255 socket
master    29169                      root   49u     unix 0xffff880064429500       0t0    2195256 private/proxywrite
master    29169                      root   50u     unix 0xffff880064428600       0t0    2195258 socket
master    29169                      root   51u     unix 0xffff880064428900       0t0    2195259 socket
master    29169                      root   52u     unix 0xffff880064429b00       0t0    2195260 private/smtp
master    29169                      root   53u     unix 0xffff880064428000       0t0    2195262 socket
master    29169                      root   54u     unix 0xffff88007cf0b200       0t0    2195263 socket
master    29169                      root   55u     unix 0xffff88007cf0a600       0t0    2195264 private/relay
master    29169                      root   56u     unix 0xffff88007cf0a300       0t0    2195266 socket
master    29169                      root   57u     unix 0xffff88007cf0ac00       0t0    2195267 socket
master    29169                      root   58u     unix 0xffff88007cf0a000       0t0    2195268 public/showq
master    29169                      root   59u     unix 0xffff88007cf0af00       0t0    2195270 socket
master    29169                      root   60u     unix 0xffff88007cf0b800       0t0    2195271 socket
master    29169                      root   61u     unix 0xffff8800642f2900       0t0    2195272 private/error
master    29169                      root   62u     unix 0xffff8800642f3800       0t0    2195274 socket
master    29169                      root   63u     unix 0xffff8800642f2c00       0t0    2195275 socket
master    29169                      root   64u     unix 0xffff8800642f2f00       0t0    2195276 private/retry
master    29169                      root   65u     unix 0xffff8800642f3500       0t0    2195278 socket
master    29169                      root   66u     unix 0xffff8800642f3b00       0t0    2195279 socket
master    29169                      root   67u     unix 0xffff8800642f2600       0t0    2195280 private/discard
master    29169                      root   68u     unix 0xffff8800642f2000       0t0    2195282 socket
master    29169                      root   69u     unix 0xffff8800642f2300       0t0    2195283 socket
master    29169                      root   70u     unix 0xffff88007c512000       0t0    2195284 private/local
master    29169                      root   71u     unix 0xffff88007c513800       0t0    2195286 socket
master    29169                      root   72u     unix 0xffff88007c513200       0t0    2195287 socket
master    29169                      root   73u     unix 0xffff88007c512c00       0t0    2195288 private/virtual
master    29169                      root   74u     unix 0xffff88007c513500       0t0    2195290 socket
master    29169                      root   75u     unix 0xffff88007c512900       0t0    2195291 socket
master    29169                      root   76u     unix 0xffff88007c513b00       0t0    2195292 private/lmtp
master    29169                      root   77u     unix 0xffff880037d6a300       0t0    2195294 socket
master    29169                      root   78u     unix 0xffff880037d6a600       0t0    2195295 socket
master    29169                      root   79u     unix 0xffff88007b982000       0t0    2195296 private/anvil
master    29169                      root   80u     unix 0xffff88007b982600       0t0    2195298 socket
master    29169                      root   81u     unix 0xffff88007b982f00       0t0    2195299 socket
master    29169                      root   82u     unix 0xffff88007b983800       0t0    2195300 private/scache
master    29169                      root   83u     unix 0xffff88007b982c00       0t0    2195302 socket
master    29169                      root   84u     unix 0xffff88007b982300       0t0    2195303 socket
master    29169                      root   85u     unix 0xffff88007b983500       0t0    2195304 private/maildrop
master    29169                      root   86u     unix 0xffff88007b983200       0t0    2195306 socket
master    29169                      root   87u     unix 0xffff88007a6e1b00       0t0    2195307 socket
master    29169                      root   88u     unix 0xffff88007a6e0600       0t0    2195308 private/uucp
master    29169                      root   89u     unix 0xffff88007a6e0c00       0t0    2195310 socket
master    29169                      root   90u     unix 0xffff88007a6e0300       0t0    2195311 socket
master    29169                      root   91u     unix 0xffff88007a6e1200       0t0    2195312 private/ifmail
master    29169                      root   92u     unix 0xffff88007a6e0f00       0t0    2195314 socket
master    29169                      root   93u     unix 0xffff88007a6e1500       0t0    2195315 socket
master    29169                      root   94u     unix 0xffff88007a6e0000       0t0    2195316 private/bsmtp
master    29169                      root   95u     unix 0xffff880078f0ec00       0t0    2195318 socket
master    29169                      root   96u     unix 0xffff880078f0e900       0t0    2195319 socket
master    29169                      root   97u     unix 0xffff880078f0e300       0t0    2195320 private/scalemail-backend
master    29169                      root   98u     unix 0xffff88005f55bb00       0t0    2195322 socket
master    29169                      root   99u     unix 0xffff88005f55b200       0t0    2195323 socket
master    29169                      root  100u     unix 0xffff88005f55b500       0t0    2195324 private/mailman
master    29169                      root  101u     unix 0xffff88005f55a600       0t0    2195326 socket
master    29169                      root  102u     unix 0xffff88005f55a900       0t0    2195327 socket
master    29169                      root  103u     IPv4            2195330       0t0        TCP *:submission (LISTEN)
master    29169                      root  104u     unix 0xffff88007d170600       0t0    2195331 socket
master    29169                      root  105u     unix 0xffff88007d170900       0t0    2195332 socket
master    29169                      root  106w     FIFO                0,8       0t0    2195333 pipe
master    29169                      root  107r     FIFO                0,8       0t0    2195334 pipe
master    29169                      root  108w     FIFO                0,8       0t0    2195334 pipe
qmgr      29171                   postfix  cwd       DIR              251,0      4096     530730 /var/spool/postfix
qmgr      29171                   postfix  rtd       DIR              251,0      4096          2 /
qmgr      29171                   postfix  txt       REG              251,0     67672     132968 /usr/lib/postfix/qmgr
qmgr      29171                   postfix  mem       REG              251,0     51712     411283 /lib/libnss_files-2.11.1.so
qmgr      29171                   postfix  mem       REG              251,0     43552     411304 /lib/libnss_nis-2.11.1.so
qmgr      29171                   postfix  mem       REG              251,0     35712     411309 /lib/libnss_compat-2.11.1.so
qmgr      29171                   postfix  mem       REG              251,0    135745     411279 /lib/libpthread-2.11.1.so
qmgr      29171                   postfix  mem       REG              251,0     92752     391918 /lib/libz.so.1.2.3.3
qmgr      29171                   postfix  mem       REG              251,0     14696     411284 /lib/libdl-2.11.1.so
qmgr      29171                   postfix  mem       REG              251,0   1588616     411299 /lib/libc-2.11.1.so
qmgr      29171                   postfix  mem       REG              251,0     93000     411270 /lib/libresolv-2.11.1.so
qmgr      29171                   postfix  mem       REG              251,0     97256     411305 /lib/libnsl-2.11.1.so
qmgr      29171                   postfix  mem       REG              251,0   1494424     130749 /usr/lib/libdb-4.8.so
qmgr      29171                   postfix  mem       REG              251,0    105232     137634 /usr/lib/libsasl2.so.2.0.23
qmgr      29171                   postfix  mem       REG              251,0   1626400     397338 /lib/libcrypto.so.0.9.8
qmgr      29171                   postfix  mem       REG              251,0    342192     397755 /lib/libssl.so.0.9.8
qmgr      29171                   postfix  mem       REG              251,0    216536     132983 /usr/lib/libpostfix-util.so.1.0.1
qmgr      29171                   postfix  mem       REG              251,0    232120     132980 /usr/lib/libpostfix-global.so.1.0.1
qmgr      29171                   postfix  mem       REG              251,0     38800     132981 /usr/lib/libpostfix-master.so.1.0.1
qmgr      29171                   postfix  mem       REG              251,0    136936     411291 /lib/ld-2.11.1.so
qmgr      29171                   postfix    0u      CHR                1,3       0t0        791 /dev/null
qmgr      29171                   postfix    1u      CHR                1,3       0t0        791 /dev/null
qmgr      29171                   postfix    2u      CHR                1,3       0t0        791 /dev/null
qmgr      29171                   postfix    3r     FIFO                0,8       0t0    2195334 pipe
qmgr      29171                   postfix    4w     FIFO                0,8       0t0    2195334 pipe
qmgr      29171                   postfix    5u     unix 0xffff88006384ec00       0t0    2195223 socket
qmgr      29171                   postfix    6u     FIFO              251,0       0t0     522341 /var/spool/postfix/public/qmgr
qmgr      29171                   postfix    7u     unix 0xffff88007c512f00       0t0    3892114 socket
qmgr      29171                   postfix    8u     0000                0,9         0        781 anon_inode
tlsmgr    29285                   postfix  cwd       DIR              251,0      4096     530730 /var/spool/postfix
tlsmgr    29285                   postfix  rtd       DIR              251,0      4096     530730 /var/spool/postfix
tlsmgr    29285                   postfix  txt       REG              251,0     22824     132975 /usr/lib/postfix/tlsmgr
tlsmgr    29285                   postfix  mem       REG              251,0     51712     411283 /lib/libnss_files-2.11.1.so
tlsmgr    29285                   postfix  mem       REG              251,0     43552     411304 /lib/libnss_nis-2.11.1.so
tlsmgr    29285                   postfix  mem       REG              251,0     35712     411309 /lib/libnss_compat-2.11.1.so
tlsmgr    29285                   postfix  mem       REG              251,0    135745     411279 /lib/libpthread-2.11.1.so
tlsmgr    29285                   postfix  mem       REG              251,0     92752     391918 /lib/libz.so.1.2.3.3
tlsmgr    29285                   postfix  mem       REG              251,0     14696     411284 /lib/libdl-2.11.1.so
tlsmgr    29285                   postfix  mem       REG              251,0   1588616     411299 /lib/libc-2.11.1.so
tlsmgr    29285                   postfix  mem       REG              251,0     93000     411270 /lib/libresolv-2.11.1.so
tlsmgr    29285                   postfix  mem       REG              251,0     97256     411305 /lib/libnsl-2.11.1.so
tlsmgr    29285                   postfix  mem       REG              251,0   1494424     130749 /usr/lib/libdb-4.8.so
tlsmgr    29285                   postfix  mem       REG              251,0    105232     137634 /usr/lib/libsasl2.so.2.0.23
tlsmgr    29285                   postfix  mem       REG              251,0   1626400     397338 /lib/libcrypto.so.0.9.8
tlsmgr    29285                   postfix  mem       REG              251,0    342192     397755 /lib/libssl.so.0.9.8
tlsmgr    29285                   postfix  mem       REG              251,0    216536     132983 /usr/lib/libpostfix-util.so.1.0.1
tlsmgr    29285                   postfix  mem       REG              251,0    232120     132980 /usr/lib/libpostfix-global.so.1.0.1
tlsmgr    29285                   postfix  mem       REG              251,0     63656     132982 /usr/lib/libpostfix-tls.so.1.0.1
tlsmgr    29285                   postfix  mem       REG              251,0     38800     132981 /usr/lib/libpostfix-master.so.1.0.1
tlsmgr    29285                   postfix  mem       REG              251,0    136936     411291 /lib/ld-2.11.1.so
tlsmgr    29285                   postfix    0u      CHR                1,3       0t0        791 /dev/null
tlsmgr    29285                   postfix    1u      CHR                1,3       0t0        791 /dev/null
tlsmgr    29285                   postfix    2u      CHR                1,3       0t0        791 /dev/null
tlsmgr    29285                   postfix    3r     FIFO                0,8       0t0    2195334 pipe
tlsmgr    29285                   postfix    4w     FIFO                0,8       0t0    2195334 pipe
tlsmgr    29285                   postfix    5u     unix 0xffff88006384e900       0t0    2195227 socket
tlsmgr    29285                   postfix    6u     unix 0xffff88006384f800       0t0    2195224 private/tlsmgr
tlsmgr    29285                   postfix    7u     unix 0xffff880078f0f200       0t0    2195515 socket
tlsmgr    29285                   postfix    8r      CHR                1,9       0t0        796 /dev/urandom
tlsmgr    29285                   postfix    9u      REG              251,0      1024     662339 /var/lib/postfix/prng_exch
tlsmgr    29285                   postfix   10u     0000                0,9         0        781 anon_inode
tlsmgr    29285                   postfix   11u      REG              251,0     24576     674033 /var/lib/postfix/smtpd_scache.db
tlsmgr    29285                   postfix   12u      REG              251,0     24576     674033 /var/lib/postfix/smtpd_scache.db
tlsmgr    29285                   postfix   13u      REG              251,0      8192     674042 /var/lib/postfix/smtp_scache.db
tlsmgr    29285                   postfix   14u      REG              251,0      8192     674042 /var/lib/postfix/smtp_scache.db
```

---

### Post by TheFu on 2014-07-22
Time to filter with **egrep** on what is important.
* ip traffic
* sent to port 25 on the remote system
* **anything** with smtp that you don't expect.

That should be just a few programs.  Seldom is the complete output from a command like this useful, as you know.  If the system isn't usually busy, then what is making it busy?  What are the top 20 processes - do any of those NOT make sense?

Of course, if there is a good rootkit in control, lsof can't see any of that stuff and only a memory image and/or file system image taken to a different box will find it.

And if php is involved, I'd check all the known bugs in that program and in the specific version running.  Our CSO won't let php programs be used on the internet - only through a strong VPN. He's been burned multiple times.

And just for fun, I'd re-validate that your system isn't an open relay and I'd block all automatic forwarding of email to external domains - once an employee decided that he preferred gmail over the interface we offered and forwarded all the email he received there.  Of course, this violated corporate policy - sending company sensitive information outside corporate systems is bad (giving google our corporate secrets is bad too), but it also made google thing that our email server was the spamming server.

---

### Post by SeijiSensei on 2014-07-22
Is there some good reason why you chose to run PHP5 as a cgi-bin application rather than the usual method of adding the PHP module to Apache?  Perhaps you have a security problem with /cgi-bin/.

---

### Post by chaemil on 2014-07-22
```

# lsof | egrep "smtp"
master    29169                   root   12u     IPv4            2195211       0t0        TCP *:smtp (LISTEN)
master    29169                   root   52u     unix 0xffff880064429b00       0t0    2195260 private/smtp
master    29169                   root   94u     unix 0xffff88007a6e0000       0t0    2195316 private/bsmtp
tlsmgr    29285                postfix   11u      REG              251,0     24576     674033 /var/lib/postfix/smtpd_scache.db
tlsmgr    29285                postfix   12u      REG              251,0     24576     674033 /var/lib/postfix/smtpd_scache.db
tlsmgr    29285                postfix   13u      REG              251,0      8192     674042 /var/lib/postfix/smtp_scache.db
tlsmgr    29285                postfix   14u      REG              251,0      8192     674042 /var/lib/postfix/smtp_scache.db

```

i gues nothing.... 

what about the senderbase.org i think that it just calculates somehow the ratio of email comunication. so for example if one day nobody sends any mail it will be 0 and when someone send 10 emails next days it will be something like 2.5? or how does this works? bcs in logs files there's nothing...

---

