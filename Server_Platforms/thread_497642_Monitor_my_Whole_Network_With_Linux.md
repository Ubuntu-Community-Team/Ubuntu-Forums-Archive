---
title: "Monitor my Whole Network With Linux"
date: 2007-07-10
forum: Server Platforms
---

### Post by ricky2567 on 2007-07-10
I want to know if there is something i can use to be able to monitor my whole network with Linux. I have Ubuntu running on a server and i have about 40 more servers and about 300 clients all running either windows or win xp. I don't want t o use any windows software, I want to run something on Linux. Any suggestions as to what i can run on Linux that will give me network monitoring such as bandwidth, server information and maybe some kind of intrusion detection?

---

### Post by rickyjones on 2007-07-10
> **ricky2567 said:**
> I want to know if there is something i can use to be able to monitor my whole network with Linux. I have Ubuntu running on a server and i have about 40 more servers and about 300 clients all running either windows or win xp. I don't want t o use any windows software, I want to run something on Linux. Any suggestions as to what i can run on Linux that will give me network monitoring such as bandwidth, server information and maybe some kind of intrusion detection?

I've been using Nagios to monitor my client networks. Seems to work pretty well! A little more difficult to configure at the start but it is well worth it in my opinion.

-Richard

---

### Post by blissend on 2007-07-10
I've never found one tool that does it all but that would be cool if there was. You could try Rootkit Hunter ([http://www.rootkit.nl/projects/rootkit_hunter.html](http://www.rootkit.nl/projects/rootkit_hunter.html)) for intrusion detection.

---

### Post by ricky2567 on 2007-07-10
Does that program detect only Linux OS's on a network or can i make it sniff out on my Windows machines also?

---

### Post by rickyjones on 2007-07-10
> **ricky2567 said:**
> Does that program detect only Linux OS's on a network or can i make it sniff out on my Windows machines also?

I believe that it can be configured to monitor aspects of Windows (disk, memory, etc...) - it might require installation of SNMP and/or some type of agent on the Windows side. Check out the Nagios documentation - it has a lot of information in there.

-Richard

---

### Post by ricky2567 on 2007-07-10
1

---

### Post by ricky2567 on 2007-07-10
> **blissend said:**
> I've never found one tool that does it all but that would be cool if there was. You could try Rootkit Hunter ([http://www.rootkit.nl/projects/rootkit_hunter.html](http://www.rootkit.nl/projects/rootkit_hunter.html)) for intrusion detection.

Can this tool be used with windows clients to?

---

### Post by eentonig on 2007-07-10
depends on what you want to monitor on your client. By default, windows doesn't provide much 'standard' monitoring tools. But if you load a snmp stack on them, Nagios can monitor them just fine.

But then, what do you want to monitor on your clients?

---

### Post by darkog on 2007-07-10
i like [ntop]("https://help.ubuntu.com/community/Ntop?highlight=%28ntop%29") for network/bandwidth monitoring. easier to use and setup than nagios. though nagios is much more flexible if you have the time to spare to set it up.

ntop does not have an IDS on it. you can use snort for that.

---

