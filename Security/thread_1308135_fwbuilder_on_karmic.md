---
title: "fwbuilder on karmic"
date: 2009-10-31
forum: Security
---

### Post by swdinesh on 2009-10-31
I installed ubuntu karmic 32-bit and I want to use fwbuilder as in my intrepid ubuntu.

I converted the firewall rules (ver. 2.1.19) file to the new format (3.0.5 build 1076). The convertion is ok but I obtain a lot of compile errors. 
After that i started a new firewall based on template and i received error messages as well. 
The errors are:
XML Parser reported:
element PolicyRule: validity error : Value "Undefined" for attribute direction of PolicyRule is not among the enumerated set
Undefined" comment="SSH Access to the host; useful ICMP types; ping request"
^
element PolicyRule: validity error : Value "Undefined" for attribute direction of PolicyRule is not among the enumerated set
False" log="False" position="3" action="Accept" direction="Undefined" comment=""
^
element PolicyRule: validity error : Value "Undefined" for attribute direction of PolicyRule is not among the enumerated set
d="False" log="True" position="4" action="Deny" direction="Undefined" comment=""
^

can anyone help me to solve that?

thank you 
Alex

---

### Post by swdinesh on 2009-10-31
> **swdinesh said:**
> I installed ubuntu karmic 32-bit and I want to use fwbuilder as in my intrepid ubuntu.

I converted the firewall rules (ver. 2.1.19) file to the new format (3.0.5 build 1076). The convertion is ok but I obtain a lot of compile errors. 
After that i started a new firewall based on template and i received error messages as well. 
The errors are:
XML Parser reported:
element PolicyRule: validity error : Value "Undefined" for attribute direction of PolicyRule is not among the enumerated set
Undefined" comment="SSH Access to the host; useful ICMP types; ping request"
^
element PolicyRule: validity error : Value "Undefined" for attribute direction of PolicyRule is not among the enumerated set
False" log="False" position="3" action="Accept" direction="Undefined" comment=""
^
element PolicyRule: validity error : Value "Undefined" for attribute direction of PolicyRule is not among the enumerated set
d="False" log="True" position="4" action="Deny" direction="Undefined" comment=""
^

can anyone help me to solve that?

thank you 
Alex
I resolved this problem by myself.
This version of fwbuilder has a bug. There´s no configuration about the direction of the rule. For every error I found the corresponding rule line and i setthe direction before incoming then again both direction and this resolved the compiling issue.

Alex

---

