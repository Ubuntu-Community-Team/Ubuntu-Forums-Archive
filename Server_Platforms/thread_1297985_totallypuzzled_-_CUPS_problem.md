---
title: "totallypuzzled - CUPS problem"
date: 2009-10-22
forum: Server Platforms
---

### Post by jsast21 on 2009-10-22
I am running ubuntu 9.04 server on one pc and am ssh'd in via my laptop (also ubuntu, but 8.04). It is my sons laptop and I wanted to set him up to have access to the network printer. no joy.

I could not get it to print. it sees it, connects to it, sends & completes the job. But nothing prints.  I go to [http://192.168.1.100:631](http://192.168.1.100:631) (from the laptop - that is the IP of the server) and can see the jobs just completed. But nothing printed. I plug the (USB) printer locally into the laptop and it prints fine, but reconnect it to the server and nothing. 

so I ssh'd back into the server and ran 
```
lp joe.txt 
```
(the file does exist) - and received:
```
lp: No file!?!
```

I cannot even print from my wife's window's laptop any longer. I have no idea what I screwed up, but I would appreciate any help anyone could offer in getting this right again.

Thanks.

---

### Post by jsast21 on 2009-10-22
update: I wanted to see if the printer was available, so here is the output from lpstat:

```

jsast21@alex-svr:/media/store/jsast21$ lpstat -p -d
printer HP_Printer is idle.  enabled since Thu 22 Oct 2009 11:49:21 AM EDT
system default destination: HP_Printer

```

still no joy on printing though. I removed and then added the printer back into CUPS via the web interface.But it is still thinking jobs are completed and the do not actually print. But on a better note, sending lp joe.txt now reports 

```
request id is HP_Printer-50 (1 file(s))
```
But still nothing comes out of the printer

---

### Post by moe_syzlak on 2009-10-22
Questions to begin with:
- What are you using to print across the network, SAMBA / CUPS?
- Are you using Samba?
- Is the client (your son's computer) running Windows or Linux?

---

### Post by confusedstingray on 2009-10-22
just a thought if you are using ubuntu on the laptop if it is desktop cant you add a printer from system, admin

---

### Post by confusedstingray on 2009-10-22
also check to see the hold function in cups is set 
here is the command

lp -i job-id -H resume

where "job-id" is the job ID reported by the lpstat command.

---

