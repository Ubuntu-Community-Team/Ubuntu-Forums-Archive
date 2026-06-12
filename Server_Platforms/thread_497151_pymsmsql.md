---
title: "pymsmsql"
date: 2007-07-09
forum: Server Platforms
---

### Post by fmtech on 2007-07-09
I want to install an extension for python that will allow python to talk to a SQL database. The extension is called “pymssql” (see their web site at: [http://pymssql.sourceforge.net/](http://pymssql.sourceforge.net/) “.

In the readme file it tells you to run this command “python setup.py install” to install the extension. After running the command I get a ton of error messages and I don’t understand what exactly it needs (see below).

I know this might not be an specific Ubuntu question but if you could give me some suggestions how to get this extension installed I would truly appreciate it.

Thank you,
FM 


vulopy@vulopy:~/pymssql-0.8.0$ python setup.py install
running install
running build
running build_py
running build_ext
building '_mssql' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O2 -Wall -Wstrict-prototypes -fPI                                                                             C -I/usr/include -I/usr/local/include -I/usr/include/freetds -I/usr/local/includ                                                                             e/freetds -I/usr/pkg/freetds/include -I/usr/include/python2.5 -c mssqldbmodule.c                                                                              -o build/temp.linux-i686-2.5/mssqldbmodule.o
mssqldbmodule.c:31:20: error: Python.h: No such file or directory
mssqldbmodule.c:32:26: error: structmember.h: No such file or directory
mssqldbmodule.c:33:22: error: datetime.h: No such file or directory
mssqldbmodule.c:45:24: error: sqlfront.h: No such file or directory
mssqldbmodule.c:46:21: error: sqldb.h: No such file or directory
mssqldbmodule.c:108: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â bef                                                                             ore â*â token
mssqldbmodule.c:109: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â bef                                                                             ore â*â token
mssqldbmodule.c:110: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â bef                                                                             ore â*â token
mssqldbmodule.c:114: error: expected specifier-qualifier-list before âPyObject_H                                                                             EADâ
mssqldbmodule.c:125: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â bef                                                                             ore â*â token
mssqldbmodule.c:126: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â bef                                                                             ore â*â token
mssqldbmodule.c:131: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â bef                                                                             ore â_mssql_ConnectionObj_Typeâ
mssqldbmodule.c:159: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â bef                                                                             ore â*â token
mssqldbmodule.c:280: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â bef                                                                             ore â*â token
mssqldbmodule.c:312: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â bef                                                                             ore â*â token
mssqldbmodule.c:343: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â bef                                                                             ore â*â token
mssqldbmodule.c:414: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â bef                                                                             ore â*â token
mssqldbmodule.c:436: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â bef                                                                             ore â*â token
mssqldbmodule.c:451: error: expected â)â before â*â token
mssqldbmodule.c:547: error: expected â)â before â*â token
mssqldbmodule.c:608: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â bef                                                                             ore â*â token
mssqldbmodule.c:722: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â bef                                                                             ore â*â token
mssqldbmodule.c:742: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â bef                                                                             ore â*â token
mssqldbmodule.c: In function â_mssql_ConnectionObj_deallocâ:
mssqldbmodule.c:760: error: â_mssql_ConnectionObjâ has no member named âconnecte                                                                             dâ
mssqldbmodule.c:761: error: âPyObjectâ undeclared (first use in this function)
mssqldbmodule.c:761: error: (Each undeclared identifier is reported only once
mssqldbmodule.c:761: error: for each function it appears in.)
mssqldbmodule.c:761: error: âoâ undeclared (first use in this function)
mssqldbmodule.c:761: warning: implicit declaration of function â_mssql_closeâ
mssqldbmodule.c:762: warning: implicit declaration of function âPy_XDECREFâ
mssqldbmodule.c:765: warning: implicit declaration of function âPyObject_Freeâ
mssqldbmodule.c: At top level:
mssqldbmodule.c:769: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â bef                                                                             ore â*â token
mssqldbmodule.c:780: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â bef                                                                             ore â_mssql_ConnectionObj_methodsâ
mssqldbmodule.c:793: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â bef                                                                             ore â_mssql_ConnectionObj_membersâ
mssqldbmodule.c:805: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â bef                                                                             ore â_mssql_ConnectionObj_Typeâ
mssqldbmodule.c:852: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â bef                                                                             ore â_mssql_methodsâ
mssqldbmodule.c:863: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â bef                                                                             ore âinit_mssqlâ
mssqldbmodule.c:930: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â bef                                                                             ore â*â token
mssqldbmodule.c:996: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â bef                                                                             ore â*â token
mssqldbmodule.c: In function âclr_errâ:
mssqldbmodule.c:1160: error: â_mssql_ConnectionObjâ has no member named âmssql_e                                                                             rror_strâ
mssqldbmodule.c:1162: error: â_mssql_ConnectionObjâ has no member named âmssql_s                                                                             everityâ
mssqldbmodule.c: In function âmaybe_raiseâ:
mssqldbmodule.c:1173: error: âPyObjectâ undeclared (first use in this function)
mssqldbmodule.c:1173: error: âoâ undeclared (first use in this function)
mssqldbmodule.c:1177: warning: implicit declaration of function âPyObject_GetAtt                                                                             râ
mssqldbmodule.c:1177: error: â_mssql_moduleâ undeclared (first use in this funct                                                                             ion)
mssqldbmodule.c:1177: warning: implicit declaration of function âPyString_FromSt                                                                             ringâ
mssqldbmodule.c:1178: warning: implicit declaration of function âPyInt_AS_LONGâ
mssqldbmodule.c:1179: warning: implicit declaration of function âPy_DECREFâ
mssqldbmodule.c:1181: error: â_mssql_ConnectionObjâ has no member named âmssql_s                                                                             everityâ
mssqldbmodule.c:1185: error: â_mssql_ConnectionObjâ has no member named âmssql_e                                                                             rror_strâ
mssqldbmodule.c:1187: warning: implicit declaration of function âPyErr_SetString                                                                             â
mssqldbmodule.c:1187: error: â_mssql_errorâ undeclared (first use in this functi                                                                             on)
mssqldbmodule.c:1190: error: âPy_BEGIN_ALLOW_THREADSâ undeclared (first use in t                                                                             his function)
mssqldbmodule.c:1191: error: expected â;â before âdbcancelâ
mssqldbmodule.c:1192: error: âPy_END_ALLOW_THREADSâ undeclared (first use in thi                                                                             s function)
mssqldbmodule.c:1194: error: expected â;â before âreturnâ
error: command 'gcc' failed with exit status 1

---

### Post by hawzor on 2007-07-12
Can you manually find these files: Python.h, structmember.h, datetime.h, sqlfront.h, sqldb.h ?

Are they in the same dir as you rant the python command?

If they are all right there in the same dir, it may be possible you need to run: 

python **[COLOR="Red"]./[/COLOR]**setup.py install

Good luck.

---

### Post by nrjCL on 2007-07-17
I'm having this exact same problem...
Anyone come up with a solution?
It appears to me that the package has missing files.

---

### Post by Kyle L. Huff on 2007-07-27
You need FreeTDS in order to use pymssql on *NIX;

The following command will install the necessary files:

```
sudo apt-get install freetds-dev
```

After that completes successfully you should be able to run ```
python ./setup.py install
``` from the source directory of pymssql.

Kyle

---

### Post by dmatamor on 2007-11-14
I also had to install python2.5-dev

---

