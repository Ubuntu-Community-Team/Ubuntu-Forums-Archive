---
title: "Problem with getmail"
date: 2012-10-19
forum: Server Platforms
---

### Post by DJ_Cyberdance on 2012-10-19
Years ago I've configured getmail to fetch messages from 2 different accounts and put them in the local Maildir. This has been working flawlessly - until yesterday.

No matter which getmail retriever module I use, I receive an error message like this:

```

getmail version 4.24.0
Copyright (C) 1998-2009 Charles Cazabon.  Licensed under the GNU GPL version 2.
BrokenUIDLPOP3Retriever:xxxxx@xxxxxx.com:110:
getmailrc: protocol error (-ERR EOF)
  1 messages (1104 bytes) retrieved, 0 skipped

```

I've also manually logged into the POP3 server via telnet, there are 50+ messges on the server. I've deleted some of them, especially the first and the last one, the error message still was there.

However, connecting to the mail server using Thunderbird works fine. I did not change anything in my getmail configuration. The server operator does not care, they claim that connecting via Outlook/Thunderbird/... just works fine.

As I said, I have been using SimplePOP3Retriever as well as SimplePOP3SSLRetriever, BrokenUIDLPOP3Retriever and BrokenUIDLPOP3SSLRetriever.

I have executed getmail with the --trace option but that does not reveal any hints to me - maybe someone of you can help out. I'm open for any suggestions. Also, as I said, logging in via telnet and reading mail using USER, PASS, UIDL, RETR and DELE commands works just fine. Just getmail fails.

getmail --trace:
```

mail/', 'override_read_all': None, 'override_verbose': None, 'dump_config': False, 'rcfile': ['getmailrc']}>>",getmaildir="'~/.getmail/'",override_delete="None",override_read_all="None",override_verbose="None",rcfile="['getmailrc']",read_file="<bound method Values.read_file of <Values at 0x8ea366c: {'trace': True, 'override_delete': None, 'getmaildir': '~/.getmail/', 'override_read_all': None, 'override_verbose': None, 'dump_config': False, 'rcfile': ['getmailrc']}>>",read_module="<bound method Values.read_module of <Values at 0x8ea366c: {'trace': True, 'override_delete': None, 'getmaildir': '~/.getmail/', 'override_read_all': None, 'override_verbose': None, 'dump_config': False, 'rcfile': ['getmailrc']}>>",trace="True"
processing rcfile /home/xxxxx/.getmail/getmailrc
  looking for option read_all ...
got "0"
-> False

  looking for option delete ...
got "1"
-> True

  looking for option delivered_to ...
got "True"
-> True

  looking for option received ...
got "True"
-> True

  looking for option message_log_verbose ...
got "False"
-> False

  looking for option message_log_syslog ...
got "False"
-> False

  looking for option delete_after ...
got "0"
-> 0

  looking for option max_message_size ...
got "0"
-> 0

  looking for option max_messages_per_session ...
got "0"
-> 0

  looking for option max_bytes_per_session ...
got "0"
-> 0

  looking for option verbose ...
got "1"
-> 1

  looking for option message_log ...
got "~/.getmail/getmail.log"
-> ~/.getmail/getmail.log

  getting retriever
    type="BrokenUIDLPOP3Retriever"
    parameter username="xxxxx@xxxxx.com"
    parameter password=*
    parameter server="mail.xxxxx.com"
    instantiating retriever BrokenUIDLPOP3Retriever with args configparser="<ConfigParser.RawConfigParser instance at 0x8ea376c>",getmaildir="~/.getmail/",password=*,server="mail.xxxxx.com",username="xxxxx@xxxxx.com"
__init__() [baseclasses.py:249] trace
__init__() [baseclasses.py:261] setting username to "xxxxx@xxxxx.com" (<type 'str'>)
__init__() [baseclasses.py:261] setting configparser to "<ConfigParser.RawConfigParser instance at 0x8ea376c>" (<type 'instance'>)
__init__() [baseclasses.py:258] setting password to * (<type 'str'>)
__init__() [baseclasses.py:261] setting getmaildir to "~/.getmail/" (<type 'str'>)
__init__() [baseclasses.py:261] setting server to "mail.xxxxx.com" (<type 'str'>)
checkconf() [baseclasses.py:267] trace
checkconf() [baseclasses.py:272] checking configparser
checkconf() [baseclasses.py:272] checking getmaildir
checkconf() [baseclasses.py:272] checking timeout
checkconf() [baseclasses.py:272] checking server
checkconf() [baseclasses.py:272] checking port
checkconf() [baseclasses.py:272] checking username
checkconf() [baseclasses.py:272] checking password
checkconf() [baseclasses.py:272] checking use_apop
checkconf() [baseclasses.py:281] done
__init__() [_retrieverbases.py:558] trace
__str__() [retrievers.py:174] trace
    checking retriever configuration for BrokenUIDLPOP3Retriever:xxxxx@xxxxx.com@mail.xxxxx.com:110
checkconf() [baseclasses.py:267] trace
  getting destination
    type="MDA_external"
    parameter path="/usr/bin/procmail"
    instantiating destination MDA_external with args configparser="<ConfigParser.RawConfigParser instance at 0x8ea376c>",path="/usr/bin/procmail"
__init__() [baseclasses.py:249] trace
__init__() [baseclasses.py:261] setting path to "/usr/bin/procmail" (<type 'str'>)
__init__() [baseclasses.py:261] setting configparser to "<ConfigParser.RawConfigParser instance at 0x8ea376c>" (<type 'instance'>)
checkconf() [baseclasses.py:267] trace
checkconf() [baseclasses.py:272] checking configparser
checkconf() [baseclasses.py:272] checking path
checkconf() [baseclasses.py:272] checking arguments
checkconf() [baseclasses.py:272] checking user
checkconf() [baseclasses.py:272] checking group
checkconf() [baseclasses.py:272] checking allow_root_commands
checkconf() [baseclasses.py:272] checking unixfrom
checkconf() [baseclasses.py:272] checking ignore_stderr
checkconf() [baseclasses.py:281] done
initialize() [destinations.py:649] trace
__init__() [destinations.py:83] done
  getting filters
getmail version 4.24.0
Copyright (C) 1998-2009 Charles Cazabon.  Licensed under the GNU GPL version 2.
__str__() [retrievers.py:174] trace
BrokenUIDLPOP3Retriever:xxxxx@xxxxx.com@mail.xxxxx.com:110:
__str__() [retrievers.py:174] trace
initialize() [_retrieverbases.py:654] trace
initialize() [_retrieverbases.py:500] trace
checkconf() [baseclasses.py:267] trace
_read_oldmailfile() [retrievers.py:134] trace
_connect() [_retrieverbases.py:117] trace
_connect() [_retrieverbases.py:132] POP3 connection <poplib.POP3 instance at 0x8ea5fac> established
_getmsglist() [retrievers.py:142] trace
msgids: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49]
msgsizes: {1: 1104, 2: 4363, 3: 3240570, 4: 35177, 5: 7816652, 6: 553086, 7: 2288, 8: 82798, 9: 1702, 10: 1695, 11: 1979, 12: 181923, 13: 1994, 14: 3086209, 15: 107516, 16: 3178, 17: 3154, 18: 1743, 19: 38831, 20: 1401, 21: 5640, 22: 1640, 23: 3943, 24: 1126, 25: 2665, 26: 5388905, 27: 4589, 28: 14060, 29: 18736, 30: 14636, 31: 4231, 32: 6119, 33: 70898, 34: 6733, 35: 56161, 36: 5906, 37: 2578, 38: 1437, 39: 8285, 40: 9667, 41: 4837, 42: 3060, 43: 1100352, 44: 41936, 45: 1318385, 46: 27134, 47: 35438, 48: 9650182, 49: 4347}
retriever_info() [destinations.py:86] trace
__len__() [_retrieverbases.py:386] trace
__getitem__() [_retrieverbases.py:390] i == 0
  message 1 ...
msgid 1
_getmsgnumbyid() [_retrieverbases.py:564] trace
msgnum 1
RETR response "+OK 1104 octets", 1104 octets
deliver_message() [destinations.py:92] trace
_deliver_message() [destinations.py:710] trace
_prepare_child() [baseclasses.py:323]
msginfo "{'sender': 'ionalaurena@freetips.com'}"
spawned child 477
_wait_for_child() [baseclasses.py:332] waiting for child 477_wait_for_child() [baseclasses.py:332] waiting for child 477_wait_for_child() [baseclasses.py:332] waiting for child 477_wait_for_child() [baseclasses.py:332] waiting for child 477_wait_for_child() [baseclasses.py:332] waiting for child 477_wait_for_child() [baseclasses.py:332] waiting for child 477_wait_for_child() [baseclasses.py:332] waiting for child 477_wait_for_child() [baseclasses.py:332] waiting for child 477_wait_for_child() [baseclasses.py:332] waiting for child 477_wait_for_child() [baseclasses.py:332] waiting for child 477_wait_for_child() [baseclasses.py:332] waiting for child 477_wait_for_child() [baseclasses.py:332] waiting for child 477_wait_for_child() [baseclasses.py:332] waiting for child 477_child_handler() [baseclasses.py:309] handler called for signal 17_child_handler() [baseclasses.py:319] handler reaped child 477 with status 0
command procmail 477 exited 0
    delivered to MDA_external command procmail (about to execl() with args ['/usr/bin/procmail', '/usr/bin/procmail'])
_delmsgbyid() [_retrieverbases.py:626] trace
_getmsgnumbyid() [_retrieverbases.py:564] trace
write_oldmailfile() [retrievers.py:138] trace
getmailrc: protocol error (-ERR EOF)
  1 messages (1104 bytes) retrieved, 0 skipped
__str__() [retrievers.py:174] trace
retriever BrokenUIDLPOP3Retriever:xxxxx@xxxxx.com@mail.xxxxx.com:110 finished
quit() [_retrieverbases.py:691] trace
write_oldmailfile() [retrievers.py:138] trace
__del__() [_retrieverbases.py:378] trace
write_oldmailfile() [retrievers.py:138] trace

```

---

