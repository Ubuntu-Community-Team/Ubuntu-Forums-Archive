---
title: "OpenLDAP and Ldap2radius Compile problem"
date: 2013-09-28
forum: Server Platforms
---

### Post by mehrdad4 on 2013-09-28
[COLOR=#000000][FONT=Arial]As this Instructions of ldap2radius for openldap from this url: [LDAp2Radius]("http://ftp.espci.fr/pub/ldap2radius/")[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]with this instructions:[/FONT][/COLOR]
 [COLOR=#800000]1[/COLOR] [COLOR=#2B91AF]Building[/COLOR] and installing
=========================

[COLOR=#2B91AF]Build[/COLOR] dependencies:
- [COLOR=#2B91AF]Flex[/COLOR]        http:[COLOR=gray]//www.gnu.org/software/flex/[/COLOR]
- [COLOR=#2B91AF]Bison[/COLOR]       http:[COLOR=gray]//www.gnu.org/software/bison/bison.html[/COLOR]
- libradius   http:[COLOR=gray]//portal-to-web.de/tacacs[/COLOR]
- [COLOR=#2B91AF]OpenLDAP[/COLOR]    http:[COLOR=gray]//www.openldap.org[/COLOR]

[COLOR=#2B91AF]To[/COLOR] build and install, just run
./configure && make && make install[COLOR=#000000][FONT=Arial]I get this error in last step exactly when make:[/FONT][/COLOR]
cc -g -O2 -DCF_FILE=\"/usr/local/etc/ldap2radius.conf\"   -c -o ldap2radius.o      ldap2radius.c
ldap2radius.c: [COLOR=#2B91AF]In[/COLOR] function main:
ldap2radius.c:[COLOR=#800000]94[/COLOR]: warning: assignment makes pointer from integer without a cast
ldap2radius.c: [COLOR=#2B91AF]In[/COLOR] function ldif_parse:
ldap2radius.c:[COLOR=#800000]259[/COLOR]: warning: assignment makes pointer from integer without a cast
ldap2radius.c: [COLOR=#2B91AF]In[/COLOR] function parse_line:
ldap2radius.c:[COLOR=#800000]324[/COLOR]: warning: [COLOR=#00008B]return[/COLOR] makes integer from pointer without a cast
ldap2radius.c:[COLOR=#800000]334[/COLOR]: warning: [COLOR=#00008B]return[/COLOR] makes integer from pointer without a cast
cc -g -O2 -DCF_FILE=\"/usr/local/etc/ldap2radius.conf\"   -c -o cf.o cf.c
bison -y cfparser.y
mv y.tab.c cfparser.c
flex -ocflexer.c cflexer.l
cc -g -O2 -DCF_FILE=\"/usr/local/etc/ldap2radius.conf\"   -c -o cfparser.o cfparser.c
cc -o ldap2radius   -lradius
/usr/lib/gcc/i686-redhat-linux/[COLOR=#800000]4.4[/COLOR].[COLOR=#800000]7[/COLOR]/../../../crt1.o: [COLOR=#2B91AF]In[/COLOR] function `_start[COLOR=#800000]':[/COLOR]
(.text+[COLOR=#800000]0x18[/COLOR]): undefined reference to `main[COLOR=#800000]'[/COLOR]
collect2: ld returned [COLOR=#800000]1[/COLOR] exit status
make: *** [ldap2radius] [COLOR=#2B91AF]Error[/COLOR] [COLOR=#800000]1
[/COLOR][COLOR=#000000][FONT=Arial]

please help
how can I make this?[/FONT][/COLOR]

---

