---
title: "strange snmpd problem"
date: 2007-11-11
forum: Server Platforms
---

### Post by FiFtHeLeMeNt on 2007-11-11
Hi,
I have installed snmpd on feitsy , seems it is working fine but the bandwidth graph I get is not continues , when I look at the data I see snmpd sends 0 then data and then 0 and .....
I have attached the bandwidth graph I get , what could the problem be ?
Regards

---

### Post by jlintz on 2007-11-11
How often are you querying the server?  Is it under a high load?  You may need to renice your snmpd daemon

---

### Post by FiFtHeLeMeNt on 2007-11-11
I am querying every 10 seconds , server is not under any load. I dont think it is a load issue , because the response pattern is regular like 1 0 1 0 1 0 1 0 1 , 1 is responding

---

