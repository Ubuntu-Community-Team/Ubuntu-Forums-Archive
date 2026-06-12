---
title: "Ssh execution of remote commands are not working"
date: 2012-02-08
forum: Security
---

### Post by mertoz on 2012-02-08
System: ubuntu 10.10
Openssh 5.5p1

I have few computer where I want to restart some services in bash script. When trying to execute a remote command of type:

ssh -t -vvv $host 'sudo /usr/sbin/program'

it happens that the program is successfully executed just at random times. From the debug info I can find that if the execution was succesfull the sequence of the flow begins with code1 and proceed with code2 (look bellow). In all attempts where execution failed the sequence was the opposite. First code2, then code1. 

```
code1:
debug2: channel 0: rcvd eof
debug2: channel 0: output open -> drain
debug2: channel 0: obuf empty
debug2: channel 0: close_write
debug2: channel 0: output drain -> closed

``````
code2:
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: client_input_channel_req: channel 0 rtype eow@openssh.com reply 0
debug2: channel 0: rcvd eow
debug2: channel 0: close_read
debug2: channel 0: input open -> closed

```I tried to install version openssh-client 5.9 from deb, but I nearly crashed my ubuntu box because of some dependencies.. Any help appreciated..

Thanks.

---

### Post by mertoz on 2012-02-12
I solved the problem with a service command witch better handle the execution of processes: 

ssh -t $host 'sudo service program'

---

