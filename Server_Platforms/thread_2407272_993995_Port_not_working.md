---
title: "993/995 Port not working"
date: 2018-12-01
forum: Server Platforms
---

### Post by programercek on 2018-12-01
Hi,

I have problem.

I installed postfix: port 25 and 587 are opened.

I want to install dovecot and port 993 and 995 are not opened.

I configured with these instructions: [https://www.digitalocean.com/community/tutorials/how-to-configure-a-mail-server-using-postfix-dovecot-mysql-and-spamassassin](https://www.digitalocean.com/community/tutorials/how-to-configure-a-mail-server-using-postfix-dovecot-mysql-and-spamassassin)

but not working. 

How can I check what is problem and where can be problem?

Thanks!

Best regards,

---

### Post by QIII on 2018-12-01
Hello!

Can you give us the specs of your machine?

Which release of Ubuntu are you using?

Is this on your residential ISP?

---

### Post by LHammonds on 2018-12-02
> **programercek said:**
> 
port 993 and 995 are not opened.

Not 'open' as in how?  Is your provider blocking those ports or do you simply need to add a rule in your software firewall to allow traffic on those ports?  Or do you have a hardware firewall / router that needs those ports opened?

If you are using UFW and need to add a rule, you can type the following to add the rule to your OS's firewall:
```

ufw allow proto tcp to any port 993 comment 'IMAPS'
ufw allow proto tcp to any port 995 comment 'POP3S'

```

**EDIT:** I took a quick look at that tutorial page.  Those steps were written for Ubuntu 12.04 (April 2014) so if you are running Ubuntu 18.04 (hopefully) then those instructions might be a bit different since the OS has changed a bit in its configuration and even though I do not use Dovecot, that software might have changed how it installs or its configuration options might be slightly different.

Maybe these links will be helpful:

[https://help.ubuntu.com/lts/serverguide/dovecot-server.html.en](https://help.ubuntu.com/lts/serverguide/dovecot-server.html.en)
[https://help.ubuntu.com/community/Dovecot](https://help.ubuntu.com/community/Dovecot)
[https://wiki2.dovecot.org/](https://wiki2.dovecot.org/)

LHammonds

---

### Post by programercek on 2018-12-02
Hello,

thanks for your reply.

I tried to use this conf but not working.

All ports on my ISP are opened.

I also use telnet localhost and the answer is the same: telnet: Unable to connect to remote host: Connection refused


I used Ubuntu version.

Maybe exists any logs to check what is problem?

---

### Post by programercek on 2018-12-02
I'm checked also with: netstat -tunlp | grep :993 port not exists..

---

### Post by The Cog on 2018-12-02
> **programercek said:**
> I'm checked also with: netstat -tunlp | grep :993 port not exists..

The the problem is not specifically with the port - it's that either dovecot is not running or it is not configured to open those ports. First I would try to see if the dovecot service is running. Try these commands:
```
ps -ef | grep dovecot
service dovecot status
systemctl status dovecot
```Service and systemctl may complain they haven't heard of dovecot but I expect ps to show the process if it's running. I think it probably isn't. So then you are probably going to have to go hunting for logs (/var/log/messages might be  agood start). Sorry I can't help there, I've never used dovecot.

---

### Post by programercek on 2018-12-02
Hello,


the problem is because certificat was not created and was is not exists on machine.

---

### Post by The Cog on 2018-12-02
Great. Thanks for posting the solution. You can Use the Thread tools pull-down at the top right to mark the thread solved.

---

