---
title: "postfix smtp error"
date: 2013-05-27
forum: Server Platforms
---

### Post by sipetron on 2013-05-27
This is the mail system at host test.knowledgeexchanger.com.  I'm sorry to have to inform you that your message could not be delivered to one or more recipients. It's attached below.  For further assistance, please send mail to postmaster.  If you do so, please include this problem report. You can delete your own text from the attached returned message.                     The mail system  <[EMAIL="hassan.h.jaber@gmail.com"]hassan.h.jaber@gmail.com[/EMAIL]>: host gmail-smtp-in.l.google.com[173.194.66.27]     said: 550-5.7.1 [92.253.101.235] The IP you're using to send mail is not     authorized to 550-5.7.1 send email directly to our servers. Please use the     SMTP relay at your 550-5.7.1 service provider instead. Learn more at 550     5.7.1 [http://support.google.com/mail/bin/answer.py?answer=10336](http://support.google.com/mail/bin/answer.py?answer=10336)     gs5si3789417wib.76 - gsmtp (in reply to end of DATA command)  
 
Reporting-MTA: dns; test.knowledgeexchanger.com X-Postfix-Queue-ID: B355A341A9E X-Postfix-Sender: rfc822; [EMAIL="hassan@test.knowledgeexchanger.com"]hassan@test.knowledgeexchanger.com[/EMAIL] Arrival-Date: Mon, 27 May 2013 11:24:15 +0300 (EEST)  Final-Recipient: rfc822; [EMAIL="hassan.h.jaber@gmail.com"]hassan.h.jaber@gmail.com[/EMAIL] Original-Recipient: rfc822;[EMAIL="hassan.h.jaber@gmail.com"]hassan.h.jaber@gmail.com[/EMAIL] Action: failed Status: 5.7.1 Remote-MTA: dns; gmail-smtp-in.l.google.com Diagnostic-Code: smtp; 550-5.7.1 [92.253.101.235] The IP you're using to send     mail is not authorized to 550-5.7.1 send email directly to our servers.     Please use the SMTP relay at your 550-5.7.1 service provider instead. Learn     more at 550 5.7.1 [http://support.google.com/mail/bin/answer.py?answer=10336](http://support.google.com/mail/bin/answer.py?answer=10336)     gs5si3789417wib.76 - gsmtp  
 
Return-Path: <[EMAIL="hassan@test.knowledgeexchanger.com"]hassan@test.knowledgeexchanger.com[/EMAIL]> Received: from localhost (test.knowledgeexchanger.com [127.0.0.1]) 	by test.knowledgeexchanger.com (Postfix) with ESMTP id B355A341A9E 	for <[EMAIL="hassan.h.jaber@gmail.com"]hassan.h.jaber@gmail.com[/EMAIL]>; Mon, 27 May 2013 11:24:15 +0300 (EEST) DKIM-Signature: v=1; a=rsa-sha256; c=relaxed/simple; d= 	test.knowledgeexchanger.com; h=user-agent:message-id:subject 	:subject:to:from:from:date:date:content-transfer-encoding 	:content-type:content-type:mime-version; s=dkim; t=1369643055; 	 x=1370507055; bh=whHeGD3qkf0QB8QPkeDWxz630dlxNxpJlYc1tDEytdQ=; b= 	LkD4/RvtsCvq5tJyZLWCN+x3s+ixCg6FOYsNN14ZSlUkyKZisMhgnc/TJ6j//vaP 	JskY034o0/WlisAzmD1Nb+rS5kZWwG15iblbYBPrwU8fm0okOj1Xyb+fXTQscJ85 	NTvar3jH0hoU7PPs2lGa/U3MgTOdVTTNeOvnP7lcVHw= X-Virus-Scanned: Debian amavisd-new at test.knowledgeexchanger.com Received: from test.knowledgeexchanger.com ([127.0.0.1]) 	by localhost (test.knowledgeexchanger.com [127.0.0.1]) (amavisd-new, port 10024) 	with ESMTP id ozBRaIX-iHTQ for <[EMAIL="hassan.h.jaber@gmail.com"]hassan.h.jaber@gmail.com[/EMAIL]>; 	Mon, 27 May 2013 11:24:15 +0300 (EEST) Received: from 192.168.1.16 (test.knowledgeexchanger.com [127.0.0.1]) 	by test.knowledgeexchanger.com (Postfix) with ESMTPA id D8585341A8D 	for <[EMAIL="hassan.h.jaber@gmail.com"]hassan.h.jaber@gmail.com[/EMAIL]>; Mon, 27 May 2013 11:24:13 +0300 (EEST) MIME-Version: 1.0 Content-Type: text/plain; charset=UTF-8;  format=flowed Content-Transfer-Encoding: 7bit Date: Mon, 27 May 2013 11:24:13 +0300 From: [EMAIL="hassan@test.knowledgeexchanger.com"]hassan@test.knowledgeexchanger.com[/EMAIL] To: <[EMAIL="hassan.h.jaber@gmail.com"]hassan.h.jaber@gmail.com[/EMAIL]> Subject: dd Message-ID: <[EMAIL="48cf91df6f0edd02122d7e96d5112fdc@test.knowledgeexchanger.com"]48cf91df6f0edd02122d7e96d5112fdc@test.knowledgeexchanger.com[/EMAIL]> X-Sender: [EMAIL="hassan@test.knowledgeexchanger.com"]hassan@test.knowledgeexchanger.com[/EMAIL] User-Agent: RoundCube WebMail  dd


is there something wrong with my server ?????

---

### Post by lisati on 2013-05-27
It's possible that Google is consulting spamhaus's "PBL" list or something similar.

Have a look here: [http://www.spamhaus.org/query/bl?ip=92.253.101.235](http://www.spamhaus.org/query/bl?ip=92.253.101.235)

---

### Post by sipetron on 2013-05-27
i remve it from black list 
now i must wait

---

### Post by sipetron on 2013-05-27
its removed from balclist 
and my yahoo email received an email from this domain 
but gmail and hotmail give me the same error

---

### Post by Cheesemill on 2013-05-27
Do you have a reverse DNS entry set up for you mail server?

A lot of mail servers won't accept mail if the reverse DNS lookup of your IP address doesn't match the FQDN of your mail server.

---

### Post by sipetron on 2013-05-28
its work 
thank you

---

