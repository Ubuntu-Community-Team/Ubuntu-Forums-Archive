---
title: "About halt and turning on problems"
date: 2011-03-14
forum: Server Platforms
---

### Post by acastrolorenzo on 2011-03-14
Hi everyone,

I have an 10.10 ubuntu server, wich is controlled by ssh from internet (not local).

Last day I decided to turn it off, as usual, did by remote ssh console:

*sudo halt*

But this time the server kept on (ssh connection disconnected, but could turn off). So turned it off by button, pressing it for a while.

Im not sure if its a bad decission, what to do in that case?

Well, I've tried now to turn on, it does (someone did it, not me, im not physically there), but cant connect to it from internet (I dont know if I could connect locally, but I am far away from the server right now).

Any idea?
Thanks in advance

---

### Post by BkkBonanza on 2011-03-14
Sounds like something has happened that requires seeing the console for messages or logging in. If it didn't shutdown cleanly due to some problem that may also affect how it boots after. 

Sometimes if it needs to do an **fsck** (file system check) (can be forced if power cut while active) then it may be waiting for a user response to an error. You'll need someone to view the console while booting or arrange for a KVM unit so you can remotely view the vga screen and interact with it. Some hosting services can provide this (a KVM) but they are a bit pricey to buy if you end up needing one.

I believe there are some changes you can make to force it to boot without waiting for prompts - maybe in the boot init options, but I don't recall right now.

---

### Post by acastrolorenzo on 2011-03-14
Thanks BkkBonanza,

I´ve someone there who turn on, and make some reboots tests with no problems. But couldnt connect like before. Did some test, restart apache and so.

Finally did: sudo fsck

Then appears like fixing some problems, but when reboot did 4 beeps instead of 2 as usual, and cant connect by ssh nor local.

I think it will better to reinstall all. 
Ideas?

Thanks in advance

---

### Post by BkkBonanza on 2011-03-14
While a reinstall will likely work I don't think it's really the right way. There should be a few more steps taken to figure out the problem. 

eg.
Can you ping the server to check any connectivity at all. or if not ping then try nmap to check some ports that should be open. verify that you can even get to the server.

If it appears to boot fine then have someone log in at the console and do a few info commands to check status. **sudo netstat -lntp** will show what programs are listening (obviously apache (httpd) should be listed there).

Run the **ps afx** command to see what processes are running .

Check if you can connect out from the server and if possible then maybe have the helper send you a copy of some log files to check for suspect lines.

There are more checks possible to narrow down why it isn't responding. Reinstalling is a radical solution that doesn't help undertand what happened or what is wrong.

---

### Post by acastrolorenzo on 2011-03-15
Thanks BkkBonanza,

Im sorry but in my case, I live far away from where server is, and have to go now there just to fix it, in one day, and have to be sure on what to do, think reinstall will be better in my case.

Last configurations I did before the bad turn off was:

1. Hide Apache version by modifing /etc/apache2/confid/securiy:

ServerSignature TO Off
ServerTokens TO Prod

2. Hide PHP version by modifing /etc/php5/apache2/php.ini:

expose_php TO Off

Maybe the consecuence?.

Another question, when text "sudo halt", but hardware stills on, what to do to avoid a boot problem?.

Thanks again, and sorry about the reinstall, I know is better try to learn more about errors.

---

