---
title: "help interpreting netstat output"
date: 2007-01-31
forum: Server Platforms
---

### Post by neill on 2007-01-31
hi

this is the output from netstat -l -t on my LAN server

Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 *:swat                  *:*                     LISTEN
tcp        0      0 localhost:57289         *:*                     LISTEN
tcp        0      0 *:mysql                 *:*                     LISTEN
tcp        0      0 *:netbios-ssn           *:*                     LISTEN
tcp        0      0 localhost:50379         *:*                     LISTEN
tcp        0      0 *:hylafax               *:*                     LISTEN
tcp        0      0 *:ipp                   *:*                     LISTEN
tcp        0      0 *:smtp                  *:*                     LISTEN
tcp        0      0 *:microsoft-ds          *:*                     LISTEN
tcp6       0      0 *:www                   *:*                     LISTEN
tcp6       0      0 *:ipp                   *:*                     LISTEN
tcp6       0      0 *:https                 *:*                     LISTEN


i understand most of it but can anyone help me with *.ipp and the 2 high ports on localhost?

thanks

neill

---

### Post by jtc on 2007-01-31
IPP stands for Internet Printing Protocol. I'd guess it's CUPS running.

---

### Post by neill on 2007-02-01
> **jtc said:**
> IPP stands for Internet Printing Protocol. I'd guess it's CUPS running.
yes that makes perfect sense - thanks

i've googled for the high port numbers but no joy

they're not exposed to the outside anyway as nmap from the LAN doesn't show them (but then they're localhost anyway !!)

---

