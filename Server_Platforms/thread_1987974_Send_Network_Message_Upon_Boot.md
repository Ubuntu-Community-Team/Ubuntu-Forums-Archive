---
title: "Send Network Message Upon Boot"
date: 2012-05-26
forum: Server Platforms
---

### Post by ads2996 on 2012-05-26
Hi,

I am trying to find a way of being able to tell if my server is turned on after it has been turned on via Magic Packets over the LAN. I would be grateful of any suggestions.

Thanks in advance

---

### Post by Ed_Ziffel on 2012-05-27
Don't know what type of server you are talking about, but why not just try to login to it after you think it should be up?  If it was up and running and you could not login to it what good would it be?  

Also you might not be, maybe you are, familiar with scripting.  You can do some reading and learn bash scripting. Linux Command Line and Shell Scritping Bible, Second Edition Richard Blum/Christine Bresnahan is a very good, but not great, book, to learn from. It has minor editing errors.  They talk about back tics but the example shows apostrophes (Not single quotes as some programming morons say, ie a quote mark is ", -end of discussion. Maybe everyone should start making up new names for everything because they can't spell or don't know any better).  The book also does not clearly explain absolutely every thing as it is presented (almost everything, but a great book makes no mistakes).  Could be a great book with not a lot of changes.

---

### Post by wojox on 2012-05-27
ping a port.

---

### Post by ads2996 on 2012-05-27
At the moment i ping the servers ip, to see if it is up.My main reason for this question is for remote access when im away from the house. So i can acces my music and videos anywhere or set it download a file, so its ready when I get back.

---

### Post by SeijiSensei on 2012-05-27
Add these lines to /etc/rc.local:

```

MYMASTER=you@example.com
echo 'Ready to serve you, master!' | mail -s "$(hostname) is up and running!" $MYMASTER

```

Install the [heirloom-mailx]("http://packages.ubuntu.com/precise/amd64/mail/heirloom-mailx") package and replace "you@example.com" with your email address.

---

### Post by ads2996 on 2012-05-27
Thank you, for your help with this. I really like the wording in the script.):P

---

