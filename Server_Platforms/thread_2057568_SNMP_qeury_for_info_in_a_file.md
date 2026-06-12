---
title: "SNMP qeury for info in a file"
date: 2012-09-13
forum: Server Platforms
---

### Post by jonobr on 2012-09-13
Hi All,

Has anyone tried, seen or any suggestions for this?

I have created an expect script on my Ubuntu server  to grab information from a non snmp capable target (a bunch of them!). The polling creates a file which contains a lot of data but has really useful specific stuff such as number of users , specific values etc.
Cron runs the script every hour and puts info into a file.
Works great...

The problem I was presented with was trying to get some of the information in the file to our SNMP capable NOC.
The NOC usually query our snmp capable devices via SNMP (V2 or V3) but I know I cannot go to the file directly.

I know I am going to have to write another script to extract and store the useful data ,
so is there any way I can get the data , pushed it into some middleware and have it pollable via SNMP or is there some other way around this I am not considering

Im guessing no, but you never know your luck in the big city:p

Cheers


Jonobr

---

### Post by sanderj on 2012-09-14
Wouldn't it be easier to send traps to the SNMP management system?

If not: what you want is called the "SNMP Agent", right? If so, does  [http://pysnmp.sourceforge.net/examples/4.x/v3arch/agent/cmdrsp.html](http://pysnmp.sourceforge.net/examples/4.x/v3arch/agent/cmdrsp.html) help? Or [http://snmpsim.sourceforge.net/simulating-agents.html](http://snmpsim.sourceforge.net/simulating-agents.html) ?

Disclaimer: I haven't tried it myself.

---

### Post by jonobr on 2012-10-03
Update on this,

I am working on extracting the file and importing into the NOC DB for presentation directly and not using SNMP.

---

