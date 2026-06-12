---
title: "[SOLVED] Setting up hardy server to email me logs"
date: 2008-05-02
forum: Server Platforms
---

### Post by Nxion on 2008-05-02
A while back I asked if there were a way to setup my server to email me the logs so I can review them ([http://ubuntuforums.org/showthread.php?t=484300](http://ubuntuforums.org/showthread.php?t=484300)). It has been awhile now and I don't believe that will work any more since it was originally meant for Snapfish

So how would I go about setting Ubuntu up to send the logs to my Gmail account?

Thank you in advance.

---

### Post by p_quarles on 2008-05-02
One package to look at is logwatch. It can be configured to output various levels of detail, as well as e-mail the results to an address you choose.

---

### Post by Nxion on 2008-05-02
> **p_quarles said:**
> One package to look at is logwatch. It can be configured to output various levels of detail, as well as e-mail the results to an address you choose.


Does logwatch require a mail server to be setup on the server before it will send anything out ?

---

### Post by p_quarles on 2008-05-02
> **Nxion said:**
> Does logwatch require a mail server to be setup on the server before it will send anything out ?
Well, yes, as anything would. I use Exim4, and have e-mails sent to an mbox on my local network, which avoids any need for fiddling. If you were to send it to gmail, though, it could get more complicated.

---

### Post by Nxion on 2008-05-02
That is where I want to send the logs too :(

---

### Post by p_quarles on 2008-05-02
> **Nxion said:**
> That is where I want to send the logs too :(
Well, the main problem with that is the tendency of Gmail (and other big spam targets) to blacklist e-mails coming from unknown SMTP servers. So, if you have a known domain name, it shouldn't be a problem. 

That said, I don't see any huge advantage to sending to Gmail. It's not so bad to set up your own POP/IMAP/webmail server, so that you can access your mbox securely from wherever you like.

---

### Post by Nxion on 2008-05-02
> **p_quarles said:**
> Well, the main problem with that is the tendency of Gmail (and other big spam targets) to blacklist e-mails coming from unknown SMTP servers. So, if you have a known domain name, it shouldn't be a problem. 

That said, I don't see any huge advantage to sending to Gmail. It's not so bad to set up your own POP/IMAP/webmail server, so that you can access your mbox securely from wherever you like.


I have seen guide after guide online and I can't choose between on or another. Can you recommend a guide for me to use ?

---

### Post by p_quarles on 2008-05-02
> **Nxion said:**
> I have seen guide after guide online and I can't choose between on or another. Can you recommend a guide for me to use ?
I didn't go that route myself, so I don't have a preference. What I did was, I think, a bit more flexible. Basically, I had my server running exim4 and openssh-server (listening on a non-standard port). My other machines could then mount the /var/mail directory (read-only) via sshfs. Then, I setup Kmail (Evolution and Sylpheed can do this easily as well, though I'm not sure about Thunderbird) to read a local mail directory, and choose the one on the mounted sshfs partition rather than on the local drive. Stable, secure (via SSH), and low on system resources.

---

### Post by Nxion on 2008-05-02
> **p_quarles said:**
> I didn't go that route myself, so I don't have a preference. What I did was, I think, a bit more flexible. Basically, I had my server running exim4 and openssh-server (listening on a non-standard port). My other machines could then mount the /var/mail directory (read-only) via sshfs. Then, I setup Kmail (Evolution and Sylpheed can do this easily as well, though I'm not sure about Thunderbird) to read a local mail directory, and choose the one on the mounted sshfs partition rather than on the local drive. Stable, secure (via SSH), and low on system resources.

I will give that a try. Thanks

Since it is sshfs. Could I access that remotely ? So when I am not at home I can loot at it ?

---

### Post by p_quarles on 2008-05-02
> **Nxion said:**
> I will give that a try. Thanks

Since it is sshfs. Could I access that remotely ? So when I am not at home I can loot at it ?
Yes, remote access is the only reason to use sshfs. Just make sure that you configure port forwarding so that requests from outside the LAN are sent to the correct machine.

---

### Post by lemming465 on 2008-05-02
Out of the box Ubuntu is probably running *postfix* as a local mail MTA.  Edit /etc/postfix/main.cf and put your ISP's SMTP server in as the *relayhost*, do *sudo postfix reload*, and I think you'll be OK.

---

### Post by ghostknife on 2008-05-03
> **Nxion said:**
> Does logwatch require a mail server to be setup on the server before it will send anything out ?

Just setup whatever log sending software you want and 
Just install the postfix for Ubuntu and edit /etc/postfix/main.cf and add the line
```

relayhost = smtp.yourisp.com
```

This will cause all mail sent from the local machine to be routed via your ISPs SMTP server (remember to change the smtp server value before you save and restart postfix.

---

### Post by Nxion on 2008-05-05
> **ghostknife said:**
> Just setup whatever log sending software you want and 
Just install the postfix for Ubuntu and edit /etc/postfix/main.cf and add the line
```

relayhost = smtp.yourisp.com
```This will cause all mail sent from the local machine to be routed via your ISPs SMTP server (remember to change the smtp server value before you save and restart postfix.

It worked perfect. Thanks ghostknife and thanks p_quarles for the info !!

---

### Post by Nxion on 2008-05-07
I setup Logwatch and it works wonders. I love it :) Can you make this thread as Solved?

Thats for all the suggestions!

---

