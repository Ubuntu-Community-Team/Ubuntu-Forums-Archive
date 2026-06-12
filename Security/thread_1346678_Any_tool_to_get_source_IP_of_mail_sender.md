---
title: "Any tool to get source IP of mail sender?"
date: 2009-12-05
forum: Security
---

### Post by vksingh on 2009-12-05
Hi,

Is there any way to find the source ip of the sender of a mail. I want to extract the location of the person sending the mails.

Thanks,

vivek

---

### Post by Bachstelze on 2009-12-05
Any decent mail client will let you see the message headers, which contain this information. Which client are you using?

---

### Post by lisati on 2009-12-05
Usually it's contained in the email headers in the last "received from" entry.
[http://simple.wikipedia.org/wiki/Email_headers](http://simple.wikipedia.org/wiki/Email_headers)
[http://8help.osu.edu/3771.html](http://8help.osu.edu/3771.html)

---

### Post by wojox on 2009-12-05
Each email you receive comes with headers. The headers contain information about the routing of the email and the originating IP of the email. Not all emails you receive can be traced back to the originating point and depending on how you send emails determines whether or not they can trace the email back to you. 

The headers don't contain any personal information. At most, you can get the originating IP and the computer name that sent the email. The originating IP can be looked up to determine from where the email was sent. IP address location information DOES NOT contain your street address or phone number. It will most likely determine the city and the ISP the sender used.

---

### Post by lisati on 2009-12-05
Nice explanation, wojox.
A further thought. If you do get hold of a source IP address, there are websites such as [www.whatismyipaddress.com](www.whatismyipaddress.com) that have options to look up ip addresses that you provide yourself and identify the general location.

---

### Post by wojox on 2009-12-05
> **lisati said:**
> Nice explanation, wojox.
A further thought. If you do get hold of a source IP address, there are websites such as [www.whatismyipaddress.com](www.whatismyipaddress.com) that have options to look up ip addresses that you provide yourself and identify the general location.

Hey I can see my house from there :p

---

### Post by lisati on 2009-12-05
> **wojox said:**
> Hey I can see my house from there :p

:lolflag: I must have put in the URL for Google's "Street View" by mistake!

---

### Post by wojox on 2009-12-05
> **lisati said:**
> :lolflag: I must have put in the URL for Google's "Street View" by mistake!

No I just clicked on satellite and clicked till I could see my street ;)

---

### Post by Cheesemill on 2009-12-06
You must bear in mind that this isn't foolproof for the following reasons:
 
If the sender uses a webmail account (which is most people nowadays) you will only get the IP of the webmail machine, ie a googlemail server, not the machine they logged into their webmail from.
 
Also email headers can be easily spoofed.

---

### Post by bodhi.zazen on 2009-12-06
> **Cheesemill said:**
> You must bear in mind that this isn't foolproof for the following reasons:
 
If the sender uses a webmail account (which is most people nowadays) you will only get the IP of the webmail machine, ie a googlemail server, not the machine they logged into their webmail from.
 
Also email headers can be easily spoofed.

I was about to add this information =)

---

