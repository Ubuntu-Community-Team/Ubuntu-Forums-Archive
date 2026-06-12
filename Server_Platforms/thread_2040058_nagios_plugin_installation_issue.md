---
title: "nagios plugin installation issue"
date: 2012-08-10
forum: Server Platforms
---

### Post by mascir on 2012-08-10
hi All,

i tried to install the check_snmp plugin (vers 1.4) on my Ubuntu 12.04 32 bit server. I have installed NET-SNMP and snmpd.

So the ./configure command works, but when i tried to send make...

> depbase=`echo src/check_snmp.o | sed 's|[^/]*$|.deps/&|;s|\.o$||'`; \
if gcc -DHAVE_CONFIG_H -I. -I. -I./inc -I./inc -fno-strict-aliasing -g -O2 -Ulinux -Dlinux=linux -D_REENTRANT -D_GNU_SOURCE -DDEBIAN -fno-strict-aliasing -pipe -fstack-protector -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/lib/perl/5.14/CORE -I/usr/local/include -g -O2 -MT src/check_snmp.o -MD -MP -MF "$depbase.Tpo" -c -o src/check_snmp.o src/check_snmp.c; \
then mv -f "$depbase.Tpo" "$depbase.Po"; else rm -f "$depbase.Tpo"; exit 1; fi
In file included from src/check_snmp.c:24:0:
./inc/check_snmp.h:107:32: warning: âstruct variable_listâ declared inside parameter list [enabled by default]
./inc/check_snmp.h:107:32: warning: its scope is only this definition or declaration, which is probably not what you want [enabled by default]
./inc/check_snmp.h:108:62: warning: âstruct variable_listâ declared inside parameter list [enabled by default]
./inc/check_snmp.h:109:60: warning: âstruct variable_listâ declared inside parameter list [enabled by default]
./inc/check_snmp.h:110:60: warning: âstruct variable_listâ declared inside parameter list [enabled by default]
./inc/check_snmp.h:111:59: warning: âstruct variable_listâ declared inside parameter list [enabled by default]
src/check_snmp.c:28:68: warning: âstruct snmp_pduâ declared inside parameter list [enabled by default]
src/check_snmp.c: In function âcheck_snmpâ:
src/check_snmp.c:61:25: error: storage size of âinitâ isnât known
src/check_snmp.c:63:5: error: unknown type name âoidâ
src/check_snmp.c:63:19: error: âMAX_OID_LENâ undeclared (first use in this function)
src/check_snmp.c:63:19: note: each undeclared identifier is reported only once for each function it appears in
src/check_snmp.c:73:20: error: âSNMP_VERSION_2câ undeclared (first use in this function)
src/check_snmp.c:89:42: error: âSNMP_MSG_GETNEXTâ undeclared (first use in this function)
src/check_snmp.c:89:61: error: âSNMP_MSG_GETâ undeclared (first use in this function)
src/check_snmp.c:95:60: error: âsnmp_errnoâ undeclared (first use in this function)
src/check_snmp.c:104:14: error: âSTAT_SUCCESSâ undeclared (first use in this function)
src/check_snmp.c:105:29: error: dereferencing pointer to incomplete type
src/check_snmp.c:106:22: error: âSNMP_ERR_NOERRORâ undeclared (first use in this function)
src/check_snmp.c:107:21: warning: passing argument 2 of âcheck_snmp_responseâ from incompatible pointer type [enabled by default]
src/check_snmp.c:28:12: note: expected âstruct snmp_pdu *â but argument is of type âstruct snmp_pdu *â
src/check_snmp.c:112:56: error: dereferencing pointer to incomplete type
src/check_snmp.c:117:14: error: âSTAT_ERRORâ undeclared (first use in this function)
src/check_snmp.c:122:14: error: âSTAT_TIMEOUTâ undeclared (first use in this function)
src/check_snmp.c: At top level:
src/check_snmp.c:164:61: warning: âstruct snmp_pduâ declared inside parameter list [enabled by default]
src/check_snmp.c:164:1: error: conflicting types for âcheck_snmp_responseâ
src/check_snmp.c:28:12: note: previous declaration of âcheck_snmp_responseâ was here
src/check_snmp.c: In function âcheck_snmp_responseâ:
src/check_snmp.c:167:42: error: dereferencing pointer to incomplete type
src/check_snmp.c:170:13: warning: passing argument 2 of âcheck_snmp_intervalsâ from incompatible pointer type [enabled by default]
./inc/check_snmp.h:108:5: note: expected âstruct variable_list *â but argument is of type âstruct variable_list *â
src/check_snmp.c:173:13: warning: passing argument 2 of âcheck_snmp_stringsâ from incompatible pointer type [enabled by default]
./inc/check_snmp.h:109:5: note: expected âstruct variable_list *â but argument is of type âstruct variable_list *â
src/check_snmp.c:176:13: warning: passing argument 2 of âcheck_snmp_regexesâ from incompatible pointer type [enabled by default]
./inc/check_snmp.h:110:5: note: expected âstruct variable_list *â but argument is of type âstruct variable_list *â
src/check_snmp.c:179:13: warning: passing argument 2 of âcheck_snmp_simpleâ from incompatible pointer type [enabled by default]
./inc/check_snmp.h:111:5: note: expected âstruct variable_list *â but argument is of type âstruct variable_list *â
src/check_snmp.c: At top level:
src/check_snmp.c:186:28: warning: âstruct variable_listâ declared inside parameter list [enabled by default]
src/check_snmp.c:186:1: error: conflicting types for âcheck_snmp_var_typeâ
./inc/check_snmp.h:107:5: note: previous declaration of âcheck_snmp_var_typeâ was here
src/check_snmp.c: In function âcheck_snmp_var_typeâ:
src/check_snmp.c:188:14: error: dereferencing pointer to incomplete type
src/check_snmp.c:189:14: error: âSNMP_NOSUCHOBJECTâ undeclared (first use in this function)
src/check_snmp.c:190:14: error: âSNMP_NOSUCHINSTANCEâ undeclared (first use in this function)
src/check_snmp.c: In function âcheck_snmp_get_valueâ:
src/check_snmp.c:203:16: error: âASN_APPLICATIONâ undeclared (first use in this function)
src/check_snmp.c: At top level:
src/check_snmp.c:28:12: warning: âcheck_snmp_responseâ used but never defined [enabled by default]
make: *** [src/check_snmp.o] Errore 1
mascir@nagios:~/check_snmp-1.4$
mascir@nagios:~/check_snmp-1.4$
mascir@nagios:~/check_snmp-1.4$
mascir@nagios:~/check_snmp-1.4$ make
depbase=`echo src/check_snmp.o | sed 's|[^/]*$|.deps/&|;s|\.o$||'`; \
if gcc -DHAVE_CONFIG_H -I. -I. -I./inc -I./inc -fno-strict-aliasing -g -O2 -Ulinux -Dlinux=linux -D_REENTRANT -D_GNU_SOURCE -DDEBIAN -fno-strict-aliasing -pipe -fstack-protector -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/lib/perl/5.14/CORE -I/usr/local/include -g -O2 -MT src/check_snmp.o -MD -MP -MF "$depbase.Tpo" -c -o src/check_snmp.o src/check_snmp.c; \
then mv -f "$depbase.Tpo" "$depbase.Po"; else rm -f "$depbase.Tpo"; exit 1; fi
In file included from src/check_snmp.c:24:0:
./inc/check_snmp.h:107:32: warning: âstruct variable_listâ declared inside parameter list [enabled by default]
./inc/check_snmp.h:107:32: warning: its scope is only this definition or declaration, which is probably not what you want [enabled by default]
./inc/check_snmp.h:108:62: warning: âstruct variable_listâ declared inside parameter list [enabled by default]
./inc/check_snmp.h:109:60: warning: âstruct variable_listâ declared inside parameter list [enabled by default]
./inc/check_snmp.h:110:60: warning: âstruct variable_listâ declared inside parameter list [enabled by default]
./inc/check_snmp.h:111:59: warning: âstruct variable_listâ declared inside parameter list [enabled by default]
src/check_snmp.c:28:68: warning: âstruct snmp_pduâ declared inside parameter list [enabled by default]
src/check_snmp.c: In function âcheck_snmpâ:
src/check_snmp.c:61:25: error: storage size of âinitâ isnât known
src/check_snmp.c:63:5: error: unknown type name âoidâ
src/check_snmp.c:63:19: error: âMAX_OID_LENâ undeclared (first use in this function)
src/check_snmp.c:63:19: note: each undeclared identifier is reported only once for each function it appears in
src/check_snmp.c:73:20: error: âSNMP_VERSION_2câ undeclared (first use in this function)
src/check_snmp.c:89:42: error: âSNMP_MSG_GETNEXTâ undeclared (first use in this function)
src/check_snmp.c:89:61: error: âSNMP_MSG_GETâ undeclared (first use in this function)
src/check_snmp.c:95:60: error: âsnmp_errnoâ undeclared (first use in this function)
src/check_snmp.c:104:14: error: âSTAT_SUCCESSâ undeclared (first use in this function)
src/check_snmp.c:105:29: error: dereferencing pointer to incomplete type
src/check_snmp.c:106:22: error: âSNMP_ERR_NOERRORâ undeclared (first use in this function)
src/check_snmp.c:107:21: warning: passing argument 2 of âcheck_snmp_responseâ from incompatible pointer type [enabled by default]
src/check_snmp.c:28:12: note: expected âstruct snmp_pdu *â but argument is of type âstruct snmp_pdu *â
src/check_snmp.c:112:56: error: dereferencing pointer to incomplete type
src/check_snmp.c:117:14: error: âSTAT_ERRORâ undeclared (first use in this function)
src/check_snmp.c:122:14: error: âSTAT_TIMEOUTâ undeclared (first use in this function)
src/check_snmp.c: At top level:
src/check_snmp.c:164:61: warning: âstruct snmp_pduâ declared inside parameter list [enabled by default]
src/check_snmp.c:164:1: error: conflicting types for âcheck_snmp_responseâ
src/check_snmp.c:28:12: note: previous declaration of âcheck_snmp_responseâ was here
src/check_snmp.c: In function âcheck_snmp_responseâ:
src/check_snmp.c:167:42: error: dereferencing pointer to incomplete type
src/check_snmp.c:170:13: warning: passing argument 2 of âcheck_snmp_intervalsâ from incompatible pointer type [enabled by default]
./inc/check_snmp.h:108:5: note: expected âstruct variable_list *â but argument is of type âstruct variable_list *â
src/check_snmp.c:173:13: warning: passing argument 2 of âcheck_snmp_stringsâ from incompatible pointer type [enabled by default]
./inc/check_snmp.h:109:5: note: expected âstruct variable_list *â but argument is of type âstruct variable_list *â
src/check_snmp.c:176:13: warning: passing argument 2 of âcheck_snmp_regexesâ from incompatible pointer type [enabled by default]
./inc/check_snmp.h:110:5: note: expected âstruct variable_list *â but argument is of type âstruct variable_list *â
src/check_snmp.c:179:13: warning: passing argument 2 of âcheck_snmp_simpleâ from incompatible pointer type [enabled by default]
./inc/check_snmp.h:111:5: note: expected âstruct variable_list *â but argument is of type âstruct variable_list *â
src/check_snmp.c: At top level:
src/check_snmp.c:186:28: warning: âstruct variable_listâ declared inside parameter list [enabled by default]
src/check_snmp.c:186:1: error: conflicting types for âcheck_snmp_var_typeâ
./inc/check_snmp.h:107:5: note: previous declaration of âcheck_snmp_var_typeâ was here
src/check_snmp.c: In function âcheck_snmp_var_typeâ:
src/check_snmp.c:188:14: error: dereferencing pointer to incomplete type
src/check_snmp.c:189:14: error: âSNMP_NOSUCHOBJECTâ undeclared (first use in this function)
src/check_snmp.c:190:14: error: âSNMP_NOSUCHINSTANCEâ undeclared (first use in this function)
src/check_snmp.c: In function âcheck_snmp_get_valueâ:
src/check_snmp.c:203:16: error: âASN_APPLICATIONâ undeclared (first use in this function)
src/check_snmp.c: At top level:
src/check_snmp.c:28:12: warning: âcheck_snmp_responseâ used but never defined [enabled by default]
make: *** [src/check_snmp.o] Errore 1


i have installed also MRTG on this server, it works fine. A little bit strange is the Nagios alert "check_mrtgtraf: Unable to open MRTG log file". It's all connected?

Thanx in advance :)

---

### Post by LHammonds on 2012-08-10
Check my sig for how I have my Nagios server built.

---

### Post by mascir on 2012-08-10
> **LHammonds said:**
> Check my sig for how I have my Nagios server built.

Thanx! i solved with your guide :)

---

### Post by LHammonds on 2012-08-10
=d>

---

### Post by mascir on 2012-08-11
> **LHammonds said:**
> =d>

here again :(

strange issue with nagios....

"External command error: MIB search path: $HOME/.snmp/mibs:/usr/share/mibs/site:/usr/share/snmp/mibs:/usr/share/mibs/iana:/usr/share/mibs/ietf:/usr/share/mibs/netsnmp"

it seems a problem on a mib path...i tried to googling in order to find a fix...nothing.

Could you help me?

cheers

---

### Post by LHammonds on 2012-08-11
What are you doing to see that error?  Is it in the web application, the command line, what?

---

### Post by mascir on 2012-08-12
> **LHammonds said:**
> What are you doing to see that error?  Is it in the web application, the command line, what?

After i started Nagios i tried to configure some services in order to check my router.


i use this following config in "router.cfg"



# Monitor Port 1 status via SNMP

define service{
	use			generic-service	; Inherit values from a template
	host_name		P-660HN-F1Z
	service_description	Port 1 Link Status
	check_command		check_snmp!-C public -o ifOperStatus.1 -r 1 -m RFC1213-MIB
	}

and the following config in "commands.cfg":


# 'check_snmp' command definition
define command{
        command_name    check_snmp
        command_line    $USER1$/check_snmp -H $HOSTADDRESS$ $ARG1$
        }

After i restarted nagios (check config OK!) in the web interface i found the error. The other SNMP command (check_local_mrtgtraf) works fine.

cheers,

---

### Post by koenn on 2012-08-12
I'm guessing the plugin is looking for the  RFC1213-MIB and can't find it on the "MIB path". maybe it's not event present on your system at all.

---

### Post by mascir on 2012-08-12
> **koenn said:**
> I'm guessing the plugin is looking for the  RFC1213-MIB and can't find it on the "MIB path". maybe it's not event present on your system at all.

thank u for the reply...

i was pretty sure that the "apt-get install snmp" and "perl -MCPAN -e 'install Net::SNMP' " would also install the mib's

I can verify their presence with a few commands?
if not, how can I install it?
 may i download and copy in a directory and then change the path of the command?

cheers

---

### Post by mascir on 2012-08-12
> **mascir said:**
> thank u for the reply...

i was pretty sure that the "apt-get install snmp" and "perl -MCPAN -e 'install Net::SNMP' " would also install the mib's

I can verify their presence with a few commands?
if not, how can I install it?
 may i download and copy in a directory and then change the path of the command?

cheers

i downloaded the file (rfc1213.mib), I copied in /usr/share/mibs/netsnmp the same in /home/USER/.snmp/mibs/ renamed the file in  RFC1213-MIB as it invokes from command config, 
# Monitor Port 1 status via SNMP

define service{
	use			generic-service	; Inherit values from a template
	host_name		P-660HN-F1Z
	service_description	Port 1 Link Status
	check_command		check_snmp!-C public -o ifOperStatus.1 -r 1 -m RFC1213-MIB
	}

same issue! :(

suggestions?

---

### Post by mascir on 2012-08-12
> **mascir said:**
> i downloaded the file (rfc1213.mib), I copied in /usr/share/mibs/netsnmp the same in /home/USER/.snmp/mibs/ renamed the file in  RFC1213-MIB as it invokes from command config, 
# Monitor Port 1 status via SNMP

define service{
	use			generic-service	; Inherit values from a template
	host_name		P-660HN-F1Z
	service_description	Port 1 Link Status
	check_command		check_snmp!-C public -o ifOperStatus.1 -r 1 -m RFC1213-MIB
	}

same issue! :(

suggestions?

FIXED!

sudo sudo apt-get install  snmp-mibs-downloader

it works! :))))

---

### Post by koenn on 2012-08-13
> **mascir said:**
> FIXED!

sudo sudo apt-get install  snmp-mibs-downloader

it works! :)

good to hear that.

thanks for the feedback; I might need that some day. :-)

---

