---
title: "Snmp"
date: 2010-07-23
forum: Security
---

### Post by Xlar on 2010-07-23
I am using Ubuntu 10.04 and wen I boot it seems to do an SNMP scan because a UPS on the same subnet configured to report SNMP requests sends out a report. The report says: Informational - System: Detected an unauthorized user attempting to access the SNMP interface from 152.15.194.17. (My IP address).

I am concerned about this as the SNMP scan may be something that isn't apart of Ubuntu. From my Googling I think that it is Ubuntu scanning for printers but I want to be certain because if my Ubuntu is infected with something I want to fix it.

Any help would be greatly appreciated,
Xlar

---

### Post by The Cog on 2010-07-23
I can confirm that 9.04 would broadcast an SNMP request asking for device type as it booted - an SNMP GET with the password "public". Apart from triggering authentication failure traps, I confirm this packet was actually harmless - I am familiar with SNMP. I gather from other people that it was the print spooler looking for printers that was sending it.

I thought this had been stopped in 10.04, but judging by your post, maybe not.

To really confirm that's what is happening, you need to run wireshark on another PC to catch the packets on the wire.

---

### Post by Xlar on 2010-07-23
ok, thank you :)

I'll run wireshark at my next opportunity. Will it be obvious what the packets are for when I run wireshark?

Thanks again, I appreciate your response.
Xlar

---

### Post by The Cog on 2010-07-24
> **Xlar said:**
> Will it be obvious what the packets are for when I run wireshark?

Not necessarily. Depends how much you understand the way network protocols work. You can set the capture filter for "udp port 161" which will cut down how much rubbish you pick up. I guess you will see an SNMP GET request. The source IP address will be the address of the offending PC of course.

It's kind of hard to work out what info it's asking for though.

---

### Post by Xlar on 2010-07-25
OK, I'll run woreshark and see what results I get.
 
It may take me a while to set everything up as I'll need to wire my laptop into my home network rather than the work one and install wireshark on my home PC.
 
Thanks :)
Xlar

---

### Post by Ford Falcon on 2010-09-17
Hi all,

I'm also getting this error message. I just installed the beta version, 10.10 Maverick. My Network admin stopped by my desk the other day to say "what the heck?" ... lol. Anyway, I'm not sure what to do with this one. Is it a bug, or is it a service that I can disable, and if so, how can I go about doing that?

Thanks in advance

Dave

---

### Post by adrianpounder on 2012-05-09
Hi, 

I also have this problem can someone please tell me which service is scanning the network so I can stop it. I don't want to have to add this one computer to every snmp device on my network to stop getting SNMP alerts for every device on my network.

Cheers,

AP

---

### Post by oldos2er on 2012-05-09
adrianpounder, please start a new thread for your question.

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

