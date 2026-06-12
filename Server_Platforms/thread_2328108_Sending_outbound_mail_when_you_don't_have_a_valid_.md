---
title: "Sending outbound mail when you don't have a valid URL /  real Internet hostname"
date: 2016-06-17
forum: Server Platforms
---

### Post by Jonathan_Nowacki on 2016-06-17
How do I send outbound emails when I don't have a valid URL /  real Internet hostname

I'm on a private subnet.  10.22.xxx.xxx 

I'm running jobs on this server and would like to send outbound emails to my gmail when jobs complete.  I have full root priveledges just no legit server name for this computer.  None that's tied to a DNS server.   It's a nonstandard Ubuntu server inside a corporate network.  It can reach the outside world (google via firefox), I just can't receive anything from the outside world (which is fine).

So how do I send outbound email only?

---

### Post by slickymaster on 2016-06-17
*Thread moved to **Server Platforms**.*

---

### Post by SeijiSensei on 2016-06-18
First, it's pretty likely that the outbound traffic will be masqueraded and appear to be originating from the primary router's IP address.  So if the router has a valid domain name, you could try sending from user@router-name.  However gmail is pretty particular about what places it accepts mail from, so this may not work. Otherwise you'd need to contact your IP folks and ask if you can relay mail through the corporate mail server.  

A more complex solution would be to use OpenVPN and set up a tunnel between this computer and your home.  Then you could send mail to a server at home.

---

