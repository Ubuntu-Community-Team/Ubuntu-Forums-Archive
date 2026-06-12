---
title: "help to explain this rule to detect hydra attack"
date: 2009-09-03
forum: Security
---

### Post by TUDORS on 2009-09-03
web-attacks.rules:alert tcp $EXTERNAL_NET any -> $HTTP_SERVERS $HTTP_PORTS (msg:"WEB-ATTACKS Hydra attempt"; flow:to_server,established; content:"User-Agent\: Mozilla/4.0 (Hydra)"; nocase;
classtype:web-application-activity;)


User-Agent...Hydra is hardcoded on hydra-http.c
 dear all any one can explain above rule 
or help me with another rule to detect hydra attack

---

### Post by unspawn on 2009-09-03
Translated this rule logs (alert) any IP-suite TCP traffic (tcp) that comes in from the configured external IP range ($EXTERNAL_NET) on no matter what port (any) to (->) the configured IP address(es) running webserver(s) ($HTTP_SERVERS) on default designated port ($HTTP_PORTS) with log message "WEB-ATTACKS Hydra attempt" (msg:"WEB-ATTACKS Hydra attempt") where in the established connection to the server (flow:to_server,established;) traffic contains the ASCII string "User-Agent: Mozilla/4.0 (Hydra)" (content:"User-Agent\: Mozilla/4.0 (Hydra)") and search for this string regardless of case (nocase) and classify the trigger as "web-application-activity" (classtype:web-application-activity;)


If you need to write a rule to detect a Hydra attack you need to simulate a Hydra attack, capture network packets, isolate traffic to the target and look for uniquely distinctive marks. Without you posting that data it will be real hard to provide help.

---

### Post by TUDORS on 2009-09-04
dear sir 
very thanks for your help 
plz help with this another rule 
rules:alert tcp $EXTERNAL_NET any -> $SMTP_SERVERS 25 (msg:"SMTP Hydra attempt";
flow:to_server,established; [COLOR="Red"][FONT="Comic Sans MS"]pcre:"/^(EHLO|HELO)\s+hydra/smi[/FONT][/COLOR]"; classtype:misc-attack

i dont understand what it is mean with [COLOR="red"]pcre:"/^(EHLO|HELO)\s+hydra/smi[/COLOR]
another question how can capture the traffic of hydra with any program

---

### Post by Kinstonian on 2009-09-04
PCRE means Perl Compatible Regular Expression.  It's a way of searching text for patterns.

^ means beginning of the line
(EHLO|HELO) means either EHLO or HELO
\s+ means one or more white space characters such as " "
hydra means match the word "hydra"
and the rest are called option modifiers, which you can google for.

---

### Post by TUDORS on 2009-09-05
thanks alot 
but what is the program that can i used to capture network packets,so can i analyze the packet to write rule

---

### Post by Kinstonian on 2009-09-05
The most user friendly one that I'm aware of would be WireShark.

---

