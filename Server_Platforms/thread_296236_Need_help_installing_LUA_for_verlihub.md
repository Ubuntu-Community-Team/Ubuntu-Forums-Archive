---
title: "Need help installing LUA for verlihub"
date: 2006-11-09
forum: Server Platforms
---

### Post by k0rv3n on 2006-11-09
Hi.

I just started my own DC-hub using verlihub.
I've tried to install the LUA-plugin but with bad results.

I downloaded lua-040914.tar.gz that I found somewhere, (think it was from a link on verlihubs homepage) and then i type ./configure wich gives no errors. But when I typ make I get some errors I can't solve.

This is the output I get

/usr/local/include/verlihub/ccommand.h:125: error: expected ';' before '*' token
cconsole.h: In member function 'cpiLua* nScripts::cConsole::cfBase::GetPI()':
cconsole.h:48: error: 'class nCmdr::cCommand' has no member named 'mCmdr'
/usr/local/include/verlihub/tlistconsole.h: In member function 'nConfig::tListConsole<DATA_TYPE, LIST_TYPE, OWNER_TYPE>* nCon
fig::tListConsole<DATA_TYPE, LIST_TYPE, OWNER_TYPE>::cfBase::GetConsole()':
/usr/local/include/verlihub/tlistconsole.h:142: error: 'class nCmdr::cCommand' has no member named 'mCmdr'
make[2]: *** [cpilua.lo] Error 1
make[2]: Leaving directory `/home/korven/lua/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/korven/lua'
make: *** [all] Error 2


Does anyone have a clue on how to solve this?
I have lua50 installed on the server if that is any help.

---

### Post by Intruder on 2006-12-23
Bump i have same  problem as this with iplog seems all plugins i try end up with same sort of error

g++ -DHAVE_CONFIG_H -I. -I. -I.. -g -O2 -I/usr/local/include -I/usr/local/include/verlihub -I/usr/include/mysql -I/usr/include -MT cpiiplog.lo -MD -MP -MF .deps/cpiiplog.Tpo -c cpiiplog.cpp -fPIC -DPIC -o .libs/cpiiplog.o
/usr/local/include/verlihub/ccommand.h:125: error: expected ';' before '*' token
cconsole.h: In member function 'cpiIPLog* nIPLog::cConsole::cfBase::GetPI()':
cconsole.h:55: error: 'class nCmdr::cCommand' has no member named 'mCmdr'
/usr/local/include/verlihub/tlistconsole.h: In member function 'nConfig::tListConsole<DATA_TYPE, LIST_TYPE, OWNER_TYPE>* nConfig::tListConsole<DATA_TYPE, LIST_TYPE, OWNER_TYPE>::cfBase::GetConsole()':
/usr/local/include/verlihub/tlistconsole.h:142: error: 'class nCmdr::cCommand' has no member named 'mCmdr'
make[2]: *** [cpiiplog.lo] Error 1
make[2]: Leaving directory `/home/intruder/iplog/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/intruder/iplog'
make: *** [all] Error 2


Anyone help me please

Int

---

### Post by Intruder on 2006-12-29
Bump!!

Come on guys im really stuck here

Cheers 

Int

---

### Post by Meserias on 2007-11-23
Same here....
I need help how to compile at least LUA plugin then I can install successfully Ezechiele BOT for VerliHUB.
:confused:

**Intruder**
Do you successfully install LUA plugin ?
Can you please help me ? or anyone ... :(

---

### Post by Meserias on 2007-11-23
[SIZE="3"]Same here....
I need help how to compile at least LUA plugin then I can install successfully Ezechiele BOT for VerliHUB.
:confused:[/SIZE]

---

