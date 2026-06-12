---
title: "Email server only semi working"
date: 2008-10-21
forum: Server Platforms
---

### Post by Yaspoon on 2008-10-21
Hey
im setting up a mail server postfix/dovecot they both seem configured properly i can login i can send email to users on my internal network and i can send email to some external users anyone on bigpond and gmail works sometimes problem is that i cant receive mail from anyone i have ports forwarded (well i think there hte right ones)i have a registered domain and i can ping mail.mydomain.com(not my real domain) anyone got any ideas thanks
Yaspoon

---

### Post by Titan8990 on 2008-10-21
Can you verify that the mail is hitting your server?

Usually this is logged (I don't use posfix so I can't say where). Also, you can send a email and watch it through wireshark to see if it hits your server.

---

### Post by MJN on 2008-10-21
If you tell us your domain we can check the DNS, port forwarding and opening SMTP dialogue is functioning before moving on to specific problems with the Postfix configuration itself.

If not, then we'll be doing nothing more than guessing what's wrong.

Mathew

---

### Post by Yaspoon on 2008-10-22
Hey matt and titan
if the mail is hitting the server which i think is the problem how do i go about using wireshark to trace mail thanks :)
Yaspoon

---

### Post by MJN on 2008-10-22
Hi Yaspoon,
 
I cannot connect to your mail server. Can you confirm you have forward TCP port 25 from your router to the server? And that your ISP does not block incoming port 25? The blocking of outbound port 25 is quite common, but incoming less so hence I'd be inclined to think it's either a port forwarding or local firewall issue.
 
Mathew

---

### Post by Yaspoon on 2008-10-22
Matt 
thanks for the reply hmm i have checked my router and it is forwarded correctly i will mail my isp there's a good cahnce its blocked :/ weird thing is that i can email from my server to my isp's email addresses anyway ill will post back when i hear from my isp
Many thanks
Yaspoon
<edit>
Hey i dont know why but all of a sudden i jsut got a tonnes of emails what ever i did worked and i can now receive emails
and i think i know what the problem was incorect reverse lookups on my dns server duh something i never new so simple massive problem it 
caused :/ only thing wrong now is i cant send mail to my hotmail or gmail address because i think microsoft / google think i am a spam agent
know how to fix that? and matt can you try to connect to my server now bro :)
thanks
</edit>

---

