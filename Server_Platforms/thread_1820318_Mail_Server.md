---
title: "Mail Server"
date: 2011-08-07
forum: Server Platforms
---

### Post by dr1134 on 2011-08-07
First off I am sorry if some thing like this has been posted. I am have troubles putting what I want it terms for Google. Also I am new to the Ubuntu forums so sorry if this is in the wrong section.

So I have two computers that I want to use for e-mail. What I would like is to have computer one send all incoming e-mail to computer two. Also if computer one lose connection with computer two(this would mean the computer is off or it lost connection with the Internet) it should stop sending the e-mail and hold it on its hard drive. Then when connection with computer two is reestablished it should send all e-mail on its hard drive to computer two. Also if computer one was to be down or lose connection with the Internet I would then have computer two would need to be able to receive e-mail.

The reason I am doing this is so that a computer can be down for a long maintenance period. So if my method is too complected for what I am trying then please tell me of a better way of doing this.

The only mail software that I know how to use is postfix but I do not know if it can do something like this.

Both computers use Ubuntu 11.04.

---

### Post by howefield on 2011-08-07
Thread moved to "*Server Platforms*"

---

### Post by Vishal Agarwal on 2011-08-08
The computer one can receive all the mails and forward to computer two.
If the computer one will be down/ or switched off /  or not connected to internet; how come it can store all the mails at it's hard disk. in such case all the mails  can be stored at the ISP's server in it's MX.
The second computer also can be configured to receive the emails but if it is required directly to download the emails; it should be defined in the MX record.

---

### Post by dr1134 on 2011-08-08
The reason why I do not want computer one to hold all the email for long  periods of time is it has a very small hard disk space and this will be  a large volume email server with loots of emails and attachments(large). Also  the MX records only point to public IP address. I can forward all  incoming request on port x to the computer I want using the router. So using that method all email would be sent computer two if computer one is down. Again the reason I am doing this is to have multiple ways that mail can be delivered, sent, and read by clients. This is so that if something bad happens to either computer that is going to take some time to fix, email will still be flowing. Also my ISP's email server is not very good so that is not a good option but I had fought about that option and will think about it.

---

