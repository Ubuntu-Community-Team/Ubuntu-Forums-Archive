---
title: "OpneSSL server drops connection after a while"
date: 2010-07-21
forum: Security
---

### Post by mangali on 2010-07-21
Here is weird one. I'm having a web server running with ssl version 0.9.8 on Ubuntu 8.0.4. Server is having a valid certificate issued by authorized CA. In the begining client and server able to communicate (beyond handshake) successfully.  However, after a couple of days all of the active connections go haywire. Any idea what could be going wrong? Thanks in anticipation.

---

### Post by cariboo on 2010-07-22
Is there anything weird in the logs?

---

### Post by mangali on 2010-07-30
Error observed on the server side is: "Connection reset by peer" for the already established sessions(which are active since hours). There onwards, ssl_accept starts failing for all new connections.

---

### Post by mangali on 2010-07-30
Here are some more details. Once the server shows the "Connection reset by peer" and SSL_ERROR_SYSCALL  for SSL_Accept. Following is socket level messaging observed i.e. server keeps on resending SYN, ACK and not entertaining cleint hello

                                                                  [FONT=Arial][SIZE=2]
Client--------------------------------------------------------Server

[/SIZE][/FONT]  [FONT=Arial][SIZE=2]1-------------------------------------------------------------->SYN[/SIZE][/FONT]
  
 [FONT=Arial][SIZE=2]2<--------------------------------------------------------------SYN,  ACK[/SIZE][/FONT]
  
 [FONT=Arial][SIZE=2]3------------------------------------------------------------------>  ACK[/SIZE][/FONT]
  
 [FONT=Arial][SIZE=2]4------------------------------------------------------------------->  client hello[/SIZE][/FONT]
  
 [FONT=Arial][SIZE=2]5------------------------------------------------------------------->  client hello (Retransmit  4 times)[/SIZE][/FONT]
  
 [FONT=Arial][SIZE=2]6<--------------------------------------------------------------SYN,  ACK (Same as #2)[/SIZE][/FONT]
  
 [FONT=Arial][SIZE=2]7------------------------------------------------------------------>  ACK(Duplicate)[/SIZE][/FONT]
  
 [FONT=Arial][SIZE=2]8------------------------------------------------------------------->  cleint hello (Transmitted  2 times)[/SIZE][/FONT]
  
 [FONT=Arial][SIZE=2]9<--------------------------------------------------------------SYN,  ACK (Same as #2 and  #6)[/SIZE][/FONT]
  
 [FONT=Arial][SIZE=2] [FONT=Arial][SIZE=2]10------------------------------------------------------------------>  ACK(Duplicate)[/SIZE][/FONT]
  
 [FONT=Arial][SIZE=2]11------------------------------------------------------------------->  cleint hello (Retransmit)[/SIZE][/FONT]
  
 [FONT=Arial][SIZE=2]12--------------------------------------------------------------------->(RST,  ACK)[/SIZE][/FONT]
[/SIZE][/FONT]

---

