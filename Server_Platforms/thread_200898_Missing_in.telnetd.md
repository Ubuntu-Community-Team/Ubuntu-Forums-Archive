---
title: "Missing in.telnetd?"
date: 2006-06-20
forum: Server Platforms
---

### Post by wildbillnj1975 on 2006-06-20
I'm trying to get a telnet server running (YEAH, I KNOW ABOUT THE RISKS, AND ABOUT SSH!  I WILL USE TELNET AT MY OWN RISK!).

Just did a clean install of dapper drake, and there is no in.telnetd in /sbin or /usr/sbin - so, my telnetd line in /etc/inetd.conf doesn't work.

I don't see any package in Synaptic Package Manager that contains in.telnetd

What am I missing?  ](*,)

---

### Post by tonyr on 2006-06-20
Normally, by default there is no **telnet** client or server installed ( I think; maybe
there is a client).  Which **telnetd** package did you install, if any?  I see several in my
package list.  The one named simply **telnetd** contains an **in.telnetd**.

---

