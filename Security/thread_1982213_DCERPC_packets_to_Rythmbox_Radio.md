---
title: "DCERPC packets to Rythmbox Radio"
date: 2012-05-18
forum: Security
---

### Post by SparTacux on 2012-05-18
I was listening to an online radio station last night using Rhythmbox. I had wireshark running analysing all packets on eth0.  I was messing around with the expert info feature in wireshark and noticed 5 warnings ( alerts ) to do with DCERPC packets taking place. 

I'm not sure if this is normal or not. The packets came from the radio staion IP address directed to my computer IP address. There were also a handfull of malformed packets  coming from the same radio station IP. 

The vast majority of the  other traffic from the radio station was normal but the DCERPC packets got me worried. Anyone got any enlightenment on this?

---

### Post by Ms. Daisy on 2012-05-18
No enlightenment coming from me, but I'm intrigued.  What did Wireshark say- were they TCP packets?  The wireshark wiki says those packets can use TCP, UDP, SMB, and SMB2, another source says it can use even more protocols.

---

### Post by SparTacux on 2012-05-18
I was listening to Absolute Classic Rock which is one of Ubuntu's default radio stations that is already set up. IP address 85.159.184.226 using TCP port 80. I let the computer play by itself for about 2 hours and then analised the packets captured by wireshark. Wireshark reported that the DCERPC protocol had been used on some of the packets. 

Unfortunately, I was unable to save the capture as my computer started thrashing big style when I prompted wireshark to rearrange the packets by protocol. I had a few other applications running at the same time and did an internet search on DCERPC and the whole system went t*ts up.

What I do remember is that the packet sizes were in order of around 1400 to 1700 bytes. CTX was displayed on wiresharks info window.

---

### Post by SparTacux on 2012-05-18
I've not had much in the way of a response to this question.

 I did a bit of homework and it appears wireshark has had vulnerability issues with DCERPC packets. It looks like an exploit could use wiresharks sudo access level to compromise your system if running wireshark in sudo. 

This is an interesting scenario. Anyone? Man in the middle attack injecting code into data stream or genuine error or something else?

---

### Post by Hungry Man on 2012-05-18
If you're worried... profile wireshark and rythmbox with apparmor.

I honestly have no idea why you would be seeing those packets but, then again, I really wouldn't know.

Always best to be safe. A rythmbox profile will not take long to setup, wireshark may be longer.

---

### Post by bodhi.zazen on 2012-05-18
> **SparTacux said:**
> I've not had much in the way of a response to this question.

 I did a bit of homework and it appears wireshark has had vulnerability issues with DCERPC packets. It looks like an exploit could use wiresharks sudo access level to compromise your system if running wireshark in sudo. 

This is an interesting scenario. Anyone? Man in the middle attack injecting code into data stream or genuine error or something else?

post or pastebin an example packet.

---

### Post by Ms. Daisy on 2012-05-18
Did you find these?

[http://www.wireshark.org/security/wnpa-sec-2009-07.html](http://www.wireshark.org/security/wnpa-sec-2009-07.html)
[FONT=Arial, Helvetica][SIZE=-1]http://www.wireshark.org/security/wnpa-sec-2009-08.html

Look at your version of wireshark, those are both pretty old vulnerabilities. But it sounds similar to what happened with the little info you posted.

This lists those same 2 vulnerabilities plus one that is a bit newer:
[http://www.exploitsearch.net/index.php?q=XFDB%2054017]("http://www.exploitsearch.net/index.php?q=XFDB%2054017")
[/SIZE][/FONT]

---

### Post by SparTacux on 2012-05-19
> **bodhi.zazen said:**
> post or pastebin an example packet.

I'd love to. 

Unfortunately, as I mentioned in my third post on this thread, I was unable to save the capture. Wireshark stopped responding when I tried to rearrange the packets by protocol type and group the packets together. Unless wireshark has some sort of temp storage somewhere then I'm not going to be able to retrieve that data. I wish I'd taken a screen shot just to confirm what I saw.

Those DCERPC packets were all located towards the end of the rhythmbox session.  The other malformed packets that were identified were scattered throughout the 2 hour period I was listening to Rhythmbox. I did go through the data looking for recognizable text and did see the word OGG in the packet data on those suspect packets. 

I'm not sure if it's  possible the packets got corrupted and wireshark misread them as DCERPC packets. 

Assuming ( rightly or wrongly ) packets can be intercepted and modified on the fly in transit - who's capable of doing this sort of thing?

---

### Post by SparTacux on 2012-05-19
> **Ms. Daisy said:**
> Did you find these?

[http://www.wireshark.org/security/wnpa-sec-2009-07.html](http://www.wireshark.org/security/wnpa-sec-2009-07.html)
[FONT=Arial, Helvetica][SIZE=-1]http://www.wireshark.org/security/wnpa-sec-2009-08.html

Look at your version of wireshark, those are both pretty old vulnerabilities. But it sounds similar to what happened with the little info you posted.

This lists those same 2 vulnerabilities plus one that is a bit newer:
[http://www.exploitsearch.net/index.php?q=XFDB%2054017](http://www.exploitsearch.net/index.php?q=XFDB%2054017)
[/SIZE][/FONT]

I saw similar notes. 

It seems like many an application can be compromised by malformed packets or corrupted data being supplied as input to those apps. Looks like I'd better use apparmor for wireshark too ;-)

Wireshark version 1.2.7 being used with libcap version 1.0.0 for those who are interested.

---

### Post by OpSecShellshock on 2012-05-19
It might be easier to get a handle on things if you can try to reproduce the issue by accessing the station again while running Wireshark, but over a shorter period of time. My general feeling is that this is most likely perfectly normal, but it's hard to say without the captures.

---

### Post by SparTacux on 2012-05-20
> **OpSecShellshock said:**
> It might be easier to get a handle on things if you can try to reproduce the issue by accessing the station again while running Wireshark, but over a shorter period of time. My general feeling is that this is most likely perfectly normal, but it's hard to say without the captures.

That sounds like a good idea to me. :-)

I did another 2 hour 15 minutes listening to the same radio station on Sunday afternoon. ( when America is in bed ;-) ). I checked the expert info after 1 hour 45 mins of capture and had NO malformed packets and NO packets listed as DCERPC packets.  

Total captured packets from the same radio station during this time was 644,000 packets. 

Stats on this data were:

Previous segment lost >  3414 counts
Out of order segments > 206 counts
Fast retransmissions > 1965 counts

Wireshark was seriously struggling at 2 hour 15 minutes of capture. The live capture display window was 17 minutes behind the actual time. It took another 17 minutes or so to stop the capture after I hit the stop capture command. I aborted the save command since my computer was struggling doing the save. The file created was over 226MB in size. 

Looks like my computer needs more memory :-)

My conclusions are that the original DCERPC packets are to be treated as suspect but I doubt if they were the actual cause of Wireshark crashing. I reckon that was down to the original capture file being too large.

---

### Post by Dry Lips on 2012-05-22
> **SparTacux said:**
> 

Looks like my computer needs more memory :-)


Just out of curiosity,... how much RAM have you got?

---

### Post by SparTacux on 2012-05-23
> **Dry Lips said:**
> Just out of curiosity,... how much RAM have you got?

This computer is an old Dinosaur - 400MB RAM.
I Reckon I can get the latest version of Windows to run on it  ;-)

Come to think of it I probably need a new computer !
And a IDS intrusion system, and a more advanced router Firewall and employ a pro IT security expert.

---

