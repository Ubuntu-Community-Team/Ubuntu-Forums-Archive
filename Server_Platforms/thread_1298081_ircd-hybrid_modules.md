---
title: "ircd-hybrid modules"
date: 2009-10-22
forum: Server Platforms
---

### Post by mitsios on 2009-10-22
Hi,

I've recently installed ircd-hybrid. I have read that the module m_services.so is compiled with the service hub string in the source file. However, when I try to build my modified m_services.c using mbuild-hybrid, I get these errors:

Module source file: /home/stavros/m_services.c
Install path: /usr/lib/ircd-hybrid/modules
Additional compile flags: -O2 -g -Wall 
--> Compiling: gcc -I/usr/include/ircd-hybrid-7 -fPIC -DPIC -shared -O2 -g -Wall  /home/stavros/m_services.c -o /home/stavros/m_services.so
In file included from /home/stavros/m_services.c:55:
/usr/include/ircd-hybrid-7/irc_string.h:29:18: error: pcre.h: No such file or directory
In file included from /home/stavros/m_services.c:55:
/usr/include/ircd-hybrid-7/irc_string.h:31: warning: type defaults to ‘int’ in declaration of ‘pcre’
/usr/include/ircd-hybrid-7/irc_string.h:31: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/ircd-hybrid-7/irc_string.h:32: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
In file included from /home/stavros/m_services.c:58:
/usr/include/ircd-hybrid-7/s_conf.h:85: error: expected specifier-qualifier-list before ‘pcre’
/usr/include/ircd-hybrid-7/s_conf.h:133: error: expected specifier-qualifier-list before ‘pcre’
build FAILED, exiting!

What should I do to get mbuild-hybrid to compile my module?

---

