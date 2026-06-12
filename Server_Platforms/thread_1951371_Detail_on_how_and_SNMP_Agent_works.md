---
title: "Detail on how and SNMP Agent works"
date: 2012-04-02
forum: Server Platforms
---

### Post by spynappels on 2012-04-02
Hi All,

I've been looking for some specific details on where a SNMP Agent get some specific counters when it is queried by a snmpwalk or snmpget. Specifically counters like CPU usage and free RAM.

I've been googling but not found any references how the agent gets this information.

Any pointers would be eagerly read.

Stefan

---

### Post by Habitual on 2012-04-02
[Net-SNMP]("http://en.wikipedia.org/wiki/Net-SNMP")
and
[MIBS]("http://en.wikipedia.org/wiki/Management_information_base")

would be a good place to start.
What 'agent' are you referring to exactly?

---

### Post by spynappels on 2012-04-03
Hi and thanks for the reply.

I am pretty happy that I know how SNMP works and I've imported MIBs into MIB Browsers and into Wireshark to decode traps etc, what I'm looking for is a more technical description of how the agent handles a request.

The agent is based ion Net-SNMP as far as I can tell, so I'll ask about that one specifically.

What I'd like to know is when the agent receives a GET request for CPU Usage, where does it get the info from to return to the NMS/MIB Browser?

---

