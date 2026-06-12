---
title: "Ubuntu Hylafax Recive fax"
date: 2010-05-18
forum: Server Platforms
---

### Post by pkombala on 2010-05-18
I am using Hylafax server since two year for sending faxes, now My self Install new Ubuntu server ver10  with Hylafax for sending fax OK
but receiving fax making trouble some particular Sender fax to my hylafax Hang 2 housr or more no dial-tone  Tel- line also not  responding
very critical stage please help me to solve this problem
I try with two external modem one Us robotics 56k other Rockwell 56 k
I need to initialize my telphone line with in 2 or 3 min please give me some command to solve this .. 


May 18 14:38:48.71: [20281]: SESSION BEGIN 000000073 96614023856
May 18 14:38:48.71: [20281]: HylaFAX (tm) Version 6.0.3
May 18 14:38:48.71: [20281]: <-- [4:ATA\r]
May 18 14:38:54.74: [20281]: --> [7:CONNECT]
May 18 14:38:54.74: [20281]: ANSWER: FAX CONNECTION  DEVICE '/dev/ttyS0'
May 18 14:38:54.74: [20281]: RECV FAX: begin
May 18 14:38:54.74: [20281]: <-- data [32]
May 18 14:38:54.74: [20281]: <-- data [2]
May 18 14:38:56.77: [20281]: --> [7:CONNECT]
May 18 14:38:56.77: [20281]: <-- data [23]
May 18 14:38:56.77: [20281]: <-- data [2]
May 18 14:38:57.59: [20281]: --> [7:CONNECT]
May 18 14:38:57.59: [20281]: <-- data [13]
May 18 14:38:57.59: [20281]: <-- data [2]
May 18 14:38:58.24: [20281]: --> [2:OK]
May 18 14:38:58.24: [20281]: <-- [9:AT+FRH=3\r]
May 18 14:39:05.24: [20281]: --> [0:]
May 18 14:39:05.24: [20281]: MODEM <Empty line>
May 18 14:39:05.24: [20281]: <-- data [1]
May 18 14:39:05.29: [20281]: --> [2:OK]
May 18 14:39:05.29: [20281]: <-- [9:AT+FRS=7\r]
May 18 14:39:05.42: [20281]: --> [2:OK]
May 18 14:39:05.42: [20281]: <-- [9:AT+FTH=3\r]
May 18 14:39:05.47: [20281]: --> [7:CONNECT]
May 18 14:39:05.47: [20281]: <-- data [32]
May 18 14:39:05.47: [20281]: <-- data [2]
May 18 14:39:07.49: [20281]: --> [7:CONNECT]
May 18 14:39:07.49: [20281]: <-- data [23]
May 18 14:39:07.49: [20281]: <-- data [2]
May 18 14:39:08.32: [20281]: --> [7:CONNECT]
May 18 14:39:08.38: [20281]: <-- data [13]
May 18 14:39:08.38: [20281]: <-- data [2]
May 18 14:39:08.97: [20281]: --> [2:OK]
May 18 14:39:08.97: [20281]: <-- [9:AT+FRH=3\r]
May 18 14:39:11.79: [20281]: --> [7:CONNECT]
May 18 14:39:12.96: [20281]: --> [2:OK]
May 18 14:39:12.96: [20281]: RECV recv DCS (command signal)
May 18 14:39:12.96: [20281]: REMOTE wants 4800 bit/s       This Faxes  came from very low speed
May 18 14:39:12.96: [20281]: REMOTE wants A4 page width (215 mm)
May 18 14:39:12.96: [20281]: REMOTE wants unlimited page length
May 18 14:39:12.96: [20281]: REMOTE wants 3.85 line/mm
May 18 14:39:12.96: [20281]: REMOTE wants 1-D MH
May 18 14:39:12.96: [20281]: RECV training at v.27ter 4800 bit/s
May 18 14:39:12.96: [20281]: <-- [10:AT+FRM=48\r]
May 18 14:39:14.13: [20281]: --> [7:CONNECT]
May 18 14:39:15.72: [20281]: RECV: TCF 943 bytes, 0% non-zero, 928 zero-run
May 18 14:39:15.73: [20281]: --> [10:NO CARRIER]
May 18 14:39:15.73: [20281]: <-- [9:AT+FRS=7\r]
May 18 14:39:15.85: [20281]: --> [2:OK]
May 18 14:39:15.85: [20281]: TRAINING succeeded
May 18 14:39:15.85: [20281]: <-- [9:AT+FTH=3\r]
May 18 14:39:15.90: [20281]: --> [7:CONNECT]
May 18 14:39:15.90: [20281]: <-- data [3]
May 18 14:39:15.90: [20281]: <-- data [2]
May 18 14:39:17.22: [20281]: --> [2:OK]
May 18 14:39:17.22: [20281]: <-- [10:AT+FRM=48\r]
May 18 14:39:19.44: [20281]: --> [7:CONNECT]
May 18 14:39:19.44: [20281]: RECV: begin page


after here modem hang (line also no dial tone )if i restart hylafax service its /etc /ini.... or switch off modem and on again the line ok  



I need to ideal my telephone line after 1 min or two I dont want receive that particular  fax .please give me idea

---

