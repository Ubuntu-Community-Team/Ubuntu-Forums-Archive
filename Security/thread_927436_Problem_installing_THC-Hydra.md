---
title: "Problem installing THC-Hydra"
date: 2008-09-23
forum: Security
---

### Post by chronos00 on 2008-09-23
Hi!
I am trying to compile and install THC-Hydra with no success.

I have already downloaded and installed libssh-0.11.
As you can see in the following output, libssh is correctly detected and used:
```
chronos@Core:~/Desktop/Downloads/hydra-5.4-src$ make
gcc -I. -Wall -O2 -o pw-inspector pw-inspector.c
gcc -I. -Wall -O2 -c hydra-vnc.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-pcnfs.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-rexec.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-nntp.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-socks5.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-telnet.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-cisco.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-http.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-ftp.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-imap.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-pop3.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-smb.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-icq.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-cisco-enable.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-ldap.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-mysql.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-http-proxy.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-smbnt.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-mssql.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-snmp.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-cvs.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-smtpauth.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-sapr3.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-ssh2.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
hydra-ssh2.c:10:2: warning: #warning "If compilation of hydra-ssh2 fails, you are not using v0.11. Download from http://www.0xbadc0de.be/"
gcc -I. -Wall -O2 -c hydra-teamspeak.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-postgres.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-rsh.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-rlogin.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-oracle-listener.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
hydra-oracle-listener.c:10:2: warning: #warning "The Oracle Listener module does not work yet"
gcc -I. -Wall -O2 -c hydra-svn.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-pcanywhere.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-sip.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-vmauthd.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-http-proxy-auth-ntlm.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-imap-ntlm.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-pop3-ntlm.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-smtpauth-ntlm.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-http-form.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
hydra-http-form.c: In function &#8216;start_http_form&#8217;:
hydra-http-form.c:119: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 9 has type &#8216;size_t&#8217;
hydra-http-form.c:131: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 8 has type &#8216;size_t&#8217;
hydra-http-form.c:142: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 6 has type &#8216;size_t&#8217;
gcc -I. -Wall -O2 -c crc32.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c d3des.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c md4.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-mod.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c ntlm.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
ntlm.c: In function &#8216;buildAuthResponse&#8217;:
ntlm.c:1278: warning: the address of &#8216;lmRespData&#8217; will always evaluate as &#8216;true&#8217;
ntlm.c:1279: warning: the address of &#8216;ntRespData&#8217; will always evaluate as &#8216;true&#8217;
gcc -I. -Wall -O2 -c hydra.c -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH -I/usr/local/include
hydra.c: In function &#8216;hydra_restore_write&#8217;:
hydra.c:328: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 4 has type &#8216;long int&#8217;
hydra.c:328: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 5 has type &#8216;long int&#8217;
gcc -I. -Wall -O2 -lm -o hydra hydra-vnc.o hydra-pcnfs.o hydra-rexec.o hydra-nntp.o hydra-socks5.o hydra-telnet.o hydra-cisco.o hydra-http.o hydra-ftp.o hydra-imap.o hydra-pop3.o hydra-smb.o hydra-icq.o hydra-cisco-enable.o hydra-ldap.o hydra-mysql.o hydra-http-proxy.o hydra-smbnt.o hydra-mssql.o hydra-snmp.o hydra-cvs.o hydra-smtpauth.o hydra-sapr3.o hydra-ssh2.o hydra-teamspeak.o hydra-postgres.o hydra-rsh.o hydra-rlogin.o hydra-oracle-listener.o hydra-svn.o hydra-pcanywhere.o hydra-sip.o hydra-vmauthd.o hydra-http-proxy-auth-ntlm.o hydra-imap-ntlm.o hydra-pop3-ntlm.o hydra-smtpauth-ntlm.o hydra-http-form.o crc32.o d3des.o md4.o hydra-mod.o ntlm.o hydra.o -lm -lssl -lpq -lssh -lcrypto -L/usr/lib -L/usr/local/lib -L/lib -L/usr/lib || echo -e "\nIF YOU RECEIVED THE ERROR MESSAGE \"cannot find -lpq\" DO THE FOLLOWING:\n  make clean; ./configure\n  vi Makefile    <- and remove the \"-lpq\" and \"-DLIBPOSTGRES\" statements\n  make\n"
/usr/bin/ld: cannot find -lpq
collect2: ld returned 1 exit status
-e 
IF YOU RECEIVED THE ERROR MESSAGE "cannot find -lpq" DO THE FOLLOWING:
  make clean; ./configure
  vi Makefile    <- and remove the "-lpq" and "-DLIBPOSTGRES" statements
  make

```

but it complains about not finding "-lpq".

To solve this, the developer suggests to "remove the "-lpq" and "-DLIBPOSTGRES" statements" from the Makefile obtained from the ./configure, which I did.
But this didn't solve the problem either:

```
chronos@Core:~/Desktop/Downloads/hydra-5.4-src$ make
gcc -I. -Wall -O2 -o pw-inspector pw-inspector.c
gcc -I. -Wall -O2 -c hydra-vnc.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-pcnfs.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-rexec.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-nntp.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-socks5.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-telnet.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-cisco.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-http.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-ftp.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-imap.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-pop3.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-smb.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-icq.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-cisco-enable.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-ldap.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-mysql.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-http-proxy.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-smbnt.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-mssql.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-snmp.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-cvs.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-smtpauth.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-sapr3.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-ssh2.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
hydra-ssh2.c:10:2: warning: #warning "If compilation of hydra-ssh2 fails, you are not using v0.11. Download from http://www.0xbadc0de.be/"
gcc -I. -Wall -O2 -c hydra-teamspeak.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-postgres.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-rsh.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-rlogin.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-oracle-listener.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
hydra-oracle-listener.c:10:2: warning: #warning "The Oracle Listener module does not work yet"
gcc -I. -Wall -O2 -c hydra-svn.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-pcanywhere.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-sip.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-vmauthd.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-http-proxy-auth-ntlm.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-imap-ntlm.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-pop3-ntlm.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-smtpauth-ntlm.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-http-form.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
hydra-http-form.c: In function &#8216;start_http_form&#8217;:
hydra-http-form.c:119: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 9 has type &#8216;size_t&#8217;
hydra-http-form.c:131: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 8 has type &#8216;size_t&#8217;
hydra-http-form.c:142: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 6 has type &#8216;size_t&#8217;
gcc -I. -Wall -O2 -c crc32.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c d3des.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c md4.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c hydra-mod.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
gcc -I. -Wall -O2 -c ntlm.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
ntlm.c: In function &#8216;buildAuthResponse&#8217;:
ntlm.c:1278: warning: the address of &#8216;lmRespData&#8217; will always evaluate as &#8216;true&#8217;
ntlm.c:1279: warning: the address of &#8216;ntRespData&#8217; will always evaluate as &#8216;true&#8217;
gcc -I. -Wall -O2 -c hydra.c -DLIBOPENSSL -DLIBSSH -I/usr/local/include
hydra.c: In function &#8216;hydra_restore_write&#8217;:
hydra.c:328: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 4 has type &#8216;long int&#8217;
hydra.c:328: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 5 has type &#8216;long int&#8217;
gcc -I. -Wall -O2 -lm -o hydra hydra-vnc.o hydra-pcnfs.o hydra-rexec.o hydra-nntp.o hydra-socks5.o hydra-telnet.o hydra-cisco.o hydra-http.o hydra-ftp.o hydra-imap.o hydra-pop3.o hydra-smb.o hydra-icq.o hydra-cisco-enable.o hydra-ldap.o hydra-mysql.o hydra-http-proxy.o hydra-smbnt.o hydra-mssql.o hydra-snmp.o hydra-cvs.o hydra-smtpauth.o hydra-sapr3.o hydra-ssh2.o hydra-teamspeak.o hydra-postgres.o hydra-rsh.o hydra-rlogin.o hydra-oracle-listener.o hydra-svn.o hydra-pcanywhere.o hydra-sip.o hydra-vmauthd.o hydra-http-proxy-auth-ntlm.o hydra-imap-ntlm.o hydra-pop3-ntlm.o hydra-smtpauth-ntlm.o hydra-http-form.o crc32.o d3des.o md4.o hydra-mod.o ntlm.o hydra.o -lm -lssl -lssh -lcrypto -L/usr/lib -L/usr/local/lib -L/lib -L/usr/lib || echo -e "\nIF YOU RECEIVED THE ERROR MESSAGE \"cannot find -lpq\" DO THE FOLLOWING:\n  make clean; ./configure\n  vi Makefile    <- and remove the \"-lpq\" and \"-DLIBPOSTGRES\" statements\n  make\n"
hydra-ssh2.o: In function `start_ssh2':
hydra-ssh2.c:(.text+0x57): undefined reference to `options_new'
hydra-ssh2.c:(.text+0xaf): undefined reference to `options_set_wanted_method'
hydra-ssh2.c:(.text+0xc1): undefined reference to `options_set_wanted_method'
hydra-ssh2.c:(.text+0xcc): undefined reference to `options_set_port'
hydra-ssh2.c:(.text+0xd7): undefined reference to `options_set_host'
hydra-ssh2.c:(.text+0xe2): undefined reference to `options_set_username'
hydra-ssh2.c:(.text+0x12e): undefined reference to `ssh_error_code'
collect2: ld returned 1 exit status
-e 
IF YOU RECEIVED THE ERROR MESSAGE "cannot find -lpq" DO THE FOLLOWING:
  make clean; ./configure
  vi Makefile    <- and remove the "-lpq" and "-DLIBPOSTGRES" statements
  make

```


I understood the developer wanted me to change the header of the Makefile from this:
```
CC=gcc
STRIP=strip
XDEFINES= -DLIBOPENSSL -DLIBPOSTGRES -DLIBSSH
XLIBS= -lssl -lpq -lssh -lcrypto
XLIBPATHS=-L/usr/lib -L/usr/local/lib -L/lib -L/usr/lib
XIPATHS= -I/usr/local/include
PREFIX=/usr/local
XHYDRA_SUPPORT=xhydra
STRIP=strip

```
to this:
```
CC=gcc
STRIP=strip
XDEFINES= -DLIBOPENSSL -DLIBSSH
XLIBS= -lssl -lssh -lcrypto
XLIBPATHS=-L/usr/lib -L/usr/local/lib -L/lib -L/usr/lib
XIPATHS= -I/usr/local/include
PREFIX=/usr/local
XHYDRA_SUPPORT=xhydra
STRIP=strip

```

Am I wrong?
What am I missing?

---

### Post by chronos00 on 2008-09-24
bump.
Anyone?

---

### Post by oneadvent on 2008-09-25
I also get:
```
cd hydra-gtk && ./make_xhydra.sh
Trying to compile xhydra now (hydra gtk gui) - dont worry if this fails, this is really optional ...
Error: configure wasnt happy. Analyse this:
configure: error: Library requirements (gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

```

---

### Post by oneadvent on 2008-09-25
I also followed the instructions above and i get this on the sudo make install: 

```
test -e hydra.exe && touch Makefile || strip hydra pw-inspector
test -e hydra.exe && strip hydra.exe pw-inspector.exe || touch hydra
test -e xhydra && strip xhydra || touch Makefile
test -e hydra.exe && touch Makefile || cp hydra pw-inspector /usr/local/bin && cd /usr/local/bin && chmod 755 hydra pw-inspector
test -e hydra.exe && cp hydra.exe pw-inspector.exe /usr/local/bin && cd /usr/local/bin && chmod 755 hydra.exe pw-inspector.exe || touch Makefile
test -e xhydra && cp xhydra /usr/local/bin && cd /usr/local/bin && chmod 755 xhydra
make: [install] Error 1 (ignored)
```

---

### Post by oneadvent on 2008-09-25
I solved my dependency with
sudo aptitude install libgtk2.0-dev

I am now getting this when i try and run the program:

hydra: error while loading shared libraries: libssh.so: cannot open shared object file: No such file or directory


Does anyone have any ideas on this one?

---

### Post by stmurray on 2008-09-25
It looks to me like it is not finding the ssh header files or libraries.  Do you have to perhaps install the libssh-dev package to get those?  (Just a guess)

---

### Post by oneadvent on 2008-09-25
Ah such a genius. That fixed that problem.

I am having one more and then I think I'll be gtg, I get 

Error: ssh2 protocol error

What does that mean from Hydra?

---

### Post by stmurray on 2008-09-26
You got me.  Are you perhaps trying to crack ssh passwords against a port that is not ssh2?

---

### Post by oneadvent on 2008-09-26
Well I get this from an nmap. 

I'm wondering if Hydra is configured wrong somehow.

Or maybe the ssh isn't the right version on the remote machine?

```
Starting Nmap 4.53 ( http://insecure.org ) at 2008-09-26 10:56 CDT
Initiating Ping Scan at 10:56
Scanning XXX.XXX.XXX.XXX [2 ports]
Completed Ping Scan at 10:56, 0.15s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 10:56
Completed Parallel DNS resolution of 1 host. at 10:56, 0.21s elapsed
Initiating SYN Stealth Scan at 10:56
Scanning host177-30.bishopwireless.net (XXX.XXX.XXX.XXX) [1714 ports]
Discovered open port 443/tcp on XXX.XXX.XXX.XXX
Discovered open port 22/tcp on XXX.XXX.XXX.XXX
Increasing send delay for XXX.XXX.XXX.XXX from 0 to 5 due to 46 out of 114 dropped probes since last increase.
Increasing send delay for XXX.XXX.XXX.XXX from 5 to 10 due to 97 out of 242 dropped probes since last increase.
Completed SYN Stealth Scan at 10:56, 28.05s elapsed (1714 total ports)
Initiating Service scan at 10:56
Scanning 2 services on host177-30.bishopwireless.net (XXX.XXX.XXX.XXX)
Completed Service scan at 10:56, 0.00s elapsed (2 services on 1 host)
Initiating OS detection (try #1) against host177-30.bishopwireless.net (XXX.XXX.XXX.XXX)
Retrying OS detection (try #2) against host177-30.bishopwireless.net (XXX.XXX.XXX.XXX)
Insufficient responses for TCP sequencing (2), OS detection may be less accurate
Initiating Traceroute at 10:56
XXX.XXX.XXX.XXX: guessing hop distance at 1
Completed Traceroute at 10:56, 0.01s elapsed
SCRIPT ENGINE: Initiating script scanning.
Host host177-30.bishopwireless.net (XXX.XXX.XXX.XXX) appears to be up ... good.
Interesting ports on host177-30.bishopwireless.net (XXX.XXX.XXX.XXX):
Not shown: 1712 closed ports
PORT    STATE SERVICE VERSION
22/tcp  open  ssh?
443/tcp open  https?
Device type: firewall
Running (JUST GUESSING) : ZyXEL ZyNOS (96%)
Aggressive OS guesses: ZyXEL ZyWALL 2 or Prestige 660HW-61 ADSL router (96%)
No exact OS matches for host (test conditions non-ideal).
Uptime: 159.649 days (since Sat Apr 19 19:22:57 2008)

TRACEROUTE (using port 22/tcp)
HOP RTT  ADDRESS
1   2.23 host177-30.bishopwireless.net (XXX.XXX.XXX.XXX)

Read data files from: /usr/share/nmap
OS and Service detection performed. Please report any incorrect results at http://insecure.org/nmap/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 33.837 seconds
           Raw packets sent: 2814 (128.836KB) | Rcvd: 1749 (70.052KB)

```

---

### Post by stmurray on 2008-09-26
What is running on the other machine?

---

### Post by oneadvent on 2008-09-26
I dunno.

---

