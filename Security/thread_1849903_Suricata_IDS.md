---
title: "Suricata IDS"
date: 2011-09-25
forum: Security
---

### Post by DanR01 on 2011-09-25
Does anyone have any experience of using Suricata as a Network IDS/IPS? Would they recommend this tool?

Snort from the repos is too old to receive rules updates and I ran into problems compiling it from source. 

I am a little concerned about installing this program as it seems to be funded primarily by the US Military Space and Naval Command, Department of Homeland Security and other anonymous backers. It describes itself as 'open source based'. 

Or am I just being a little paranoid!?

Thanks

Dan

---

### Post by Dangertux on 2011-09-25
> **DanR01 said:**
> Does anyone have any experience of using Suricata as a Network IDS/IPS? Would they recommend this tool?

Snort from the repos is too old to receive rules updates and I ran into problems compiling it from source. 

I am a little concerned about installing this program as it seems to be funded primarily by the US Military Space and Naval Command, Department of Homeland Security and other anonymous backers. It describes itself as 'open source based'. 

Or am I just being a little paranoid!?

Thanks

Dan

I think you're just being paranoid, we ran this when I was in the military. It's a decent tool.

Any IDS/IPS will likely need custom rules to be successful at catching anything other than automated scanners/tools. This one is no different.

---

### Post by bodhi.zazen on 2011-09-26
> **DanR01 said:**
> Does anyone have any experience of using Suricata as a Network IDS/IPS? Would they recommend this tool?

Snort from the repos is too old to receive rules updates and I ran into problems compiling it from source. 

You get snort rules from , well, snort

[http://www.snort.org/snort-rules/](http://www.snort.org/snort-rules/)

Although you have to register, the rules are free.

If you need help compiling from source, post the error, however the snort mailing list may be a better option.

---

### Post by Dangertux on 2011-09-26
The only difference between the free and the subscriber rules is that the free rules are 30 days older than the subscriber rules.

---

