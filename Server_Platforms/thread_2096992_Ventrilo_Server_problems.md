---
title: "Ventrilo Server problems"
date: 2012-12-21
forum: Server Platforms
---

### Post by insidus on 2012-12-21
Hey, im having some problems with ventrilo server. I have it set up, its running as a process, listening on a port but not accepting outside users.

heres the details.

service ventrilo start

 * Starting VOIP server ventrilo                                                19586: old priority 0, new priority -5

netstat

tcp        0      0 *:3784                  *:*                     LISTEN      19586/ventrilo_srv

udp        0      0 *:3784                  *:*                                 19586/ventrilo_srv

telnet localhost 3784

Trying ::1...
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.

telnet [www.insidus.co.uk](www.insidus.co.uk) 3784

Trying 176.9.244.151...
Connected to [www.insidus.co.uk](www.insidus.co.uk).
Escape character is '^]'.
Connection closed by foreign host.

log file

20121221 22:14:05 Version           = 3.0.3
20121221 22:14:05 Name              = Insidus.co.uk
20121221 22:14:05 Phonetic          = This is my vent server
20121221 22:14:05 Auth              = 1
20121221 22:14:05 Duplicates        = 1
20121221 22:14:05 SendBuffer        = 131072
20121221 22:14:05 RecvBuffer        = 131072
20121221 22:14:05 LogonTimeout      = 5
20121221 22:14:05 CloseStd          = 1
20121221 22:14:05 TimeStamp         = 0
20121221 22:14:05 PingRate          = 10
20121221 22:14:05 ExtraBuffer       = 131072
20121221 22:14:05 ChanWidth         = 0
20121221 22:14:05 ChanDepth         = 8
20121221 22:14:05 ChanClients       = 0
20121221 22:14:05 DisableQuit       = 0
20121221 22:14:05 VoiceCodec        = 0 (GSM 6.10)
20121221 22:14:05 VoiceFormat       = 1 (11 KHz, 16 bit) - Bytes/Sec 2210
20121221 22:14:05 SilentLobby       = 0
20121221 22:14:05 AutoKick          = 0
20121221 22:14:05 MaxClients        = 8
20121221 22:14:05
20121221 22:14:05
20121221 22:14:08 READY:
20121221 22:15:23 MSG_CONN: ID 1, IP 127.0.0.1, Accepted. (50748,262142) (87584,262142)
20121221 22:15:28 AUTO: ID 1, IP 127.0.0.1, Did not logon before timeout.
20121221 22:15:28 MSG_ABORT: ID 1, 127.0.0.1 aborted.
20121221 22:15:53 MSG_CONN: ID 2, IP 176.9.244.151, Accepted. (50748,262142) (87584,262142)
20121221 22:15:58 AUTO: ID 2, IP 176.9.244.151, Did not logon before timeout.
20121221 22:15:58 MSG_ABORT: ID 2, 176.9.244.151 aborted.



Results when using Ventrilo client
MSG: Contacting Server

The server is located on a different network, and all other web services work as they should, but it seems that ventrilo is not accepting requests from outside the network.

if you can offer any help, i'd be extreamly grateful!

edit: no firewall is being used, so its not a port issue

/insidus

---

