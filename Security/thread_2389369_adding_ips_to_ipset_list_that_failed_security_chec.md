---
title: "adding ips to ipset list that failed security check with iptables"
date: 2018-04-16
forum: Security
---

### Post by delfiler on 2018-04-16
i don't know if this is possible but iptables, ipset and ubuntu surprised me several times with things i thought impossible but back to the point
what i am trying to do is set a line of code in my 'script' i set up that uses iptables. the line of code needs to detect dropped packet/connections 
and add it to the black list i set up using ipset, so if the same IP tries to attack again they get dropped at the very start of the 'script' instead of somewhere in the middle.

this is the 'script' i am talking about: [https://1drv.ms/w/s!AmHBwtLKfRJ_hLUJbwQ5Hl5LLBySIQ](https://1drv.ms/w/s!AmHBwtLKfRJ_hLUJbwQ5Hl5LLBySIQ) 
i know it is not the most advanced script in the world but it gets the job done it needs to do currently and i know there are a few # lines of code and a few that needs checking but i am on to that currently and making progress 
the # ones are still needed but not at the current time

i hope the community can help me wit this cause it is a real pain to constantly keep adding them manually and if there isn't a solution, well better get used to it
edit: forgot to mention what was what the banned list is a hash:net, whitelist is a hash:net,port and whitelist2 is a hash:net

---

