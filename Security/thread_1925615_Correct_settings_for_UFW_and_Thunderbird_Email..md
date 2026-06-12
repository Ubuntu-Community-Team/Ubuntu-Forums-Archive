---
title: "Correct settings for UFW and Thunderbird Email."
date: 2012-02-14
forum: Security
---

### Post by BlinkinCat on 2012-02-14
Hi all,

I thought that my UFW was correctly set up however when I read this thread - 
[http://ubuntuforums.org/showthread.php?p=11428970](http://ubuntuforums.org/showthread.php?p=11428970) I realized it wasn't.

I then reset UFW according to Method 2 in the description and when I checked the status all seemed to be in order. However I now find I am not receiving any incoming emails. I haven't checked out going at this stage.

This is the status of ufw as far as I know -

geoff@ABC:~$ sudo ufw status
[sudo] password for geoff: 
Status: active

To                         Action      From
--                         ------      ----
25,53,80,110,443/tcp       ALLOW OUT   Anywhere
53,67,68/udp               ALLOW OUT   Anywhere
51413/tcp                  ALLOW OUT   Anywhere
51413/udp                  ALLOW OUT   Anywhere
6969/tcp                   ALLOW OUT   Anywhere
25,53,80,110,443/tcp       ALLOW OUT   Anywhere (v6)
53,67,68/udp               ALLOW OUT   Anywhere (v6)
51413/tcp                  ALLOW OUT   Anywhere (v6)
51413/udp                  ALLOW OUT   Anywhere (v6)
6969/tcp                   ALLOW OUT   Anywhere (v6)

geoff@ABC:~$

Could somebody kindly explain what I have to do to get the email & ufw working.

Many thanks in advance - :)

---

### Post by BlinkinCat on 2012-02-14
Hi again,

I have just discovered that messages can be sent out, but these are not copied to the sent folder. Perhaps my post should be posted in General Help forum regarding Email settings as I feel that ufw settings are probably O.K.

Thanks again - :)

---

### Post by Dangertux on 2012-02-14
> **BlinkinCat said:**
> Hi all,

I thought that my UFW was correctly set up however when I read this thread - 
[http://ubuntuforums.org/showthread.php?p=11428970](http://ubuntuforums.org/showthread.php?p=11428970) I realized it wasn't.

I then reset UFW according to Method 2 in the description and when I checked the status all seemed to be in order. However I now find I am not receiving any incoming emails. I haven't checked out going at this stage.

This is the status of ufw as far as I know -

geoff@ABC:~$ sudo ufw status
[sudo] password for geoff: 
Status: active

To                         Action      From
--                         ------      ----
25,53,80,110,443/tcp       ALLOW OUT   Anywhere
53,67,68/udp               ALLOW OUT   Anywhere
51413/tcp                  ALLOW OUT   Anywhere
51413/udp                  ALLOW OUT   Anywhere
6969/tcp                   ALLOW OUT   Anywhere
25,53,80,110,443/tcp       ALLOW OUT   Anywhere (v6)
53,67,68/udp               ALLOW OUT   Anywhere (v6)
51413/tcp                  ALLOW OUT   Anywhere (v6)
51413/udp                  ALLOW OUT   Anywhere (v6)
6969/tcp                   ALLOW OUT   Anywhere (v6)

geoff@ABC:~$

Could somebody kindly explain what I have to do to get the email & ufw working.

Many thanks in advance - :)

It depends on the ports your mail server uses. If you're using gmail they would be 993, 995 and 587. Though it could be different for every mail service.

If you can give us your mail service and the method by which you retrieve mail (pop , imap , mapi etc) we could probably help you better.

---

### Post by BlinkinCat on 2012-02-14
Thanks Dangertux,

Do you mean my email provider? that is mail.optusnet.com.au
I believe method is imap
Does port 143 mean anything?

Is that what you mean? I can look further if it helps -

---

### Post by kevdog on 2012-02-14
Do you have any rules for the INPUT chain -- all I see is output?

---

### Post by BlinkinCat on 2012-02-14
> **kevdog said:**
> Do you have any rules for the INPUT chain -- all I see is output?

That's what I thought was a bit strange too. All I know is that I entered code exactly as described in method 2, and when I checked the status that was the result.

It is beyond my understanding - thanks for your interest.

Edit: I have been in touch with Optus whose rep told me that the ports used are 110 and 25
I hope that helps.
Dangertux I would appreciate if you could tell me the numbers I will need to remove and which ones I should replace them with. Also why rules only seem to cover output?

---

### Post by ztux on 2012-02-15
> **Dangertux said:**
> It depends on the ports your mail server uses. If you're using gmail they would be 993, 995 and 587. Though it could be different for every mail service.

Definitely give that a try, I didn't see any of the encrypted ports in your firewall rules. Thunderbird does use them by default!

Your ISP may be blocking the unencrypted ones, especially port 25.

Not all mail services have all of these features. I know hotmail does not offer IMAP, Yahoo doesn't offer anything.

---

### Post by BlinkinCat on 2012-02-15
> **BlinkinCat said:**
> That's what I thought was a bit strange too. All I know is that I entered code exactly as described in method 2, and when I checked the status that was the result.

It is beyond my understanding - thanks for your interest.

Edit: I have been in touch with Optus whose rep told me that the ports used are 110 and 25
I hope that helps.
Dangertux I would appreciate if you could tell me the numbers I will need to remove and which ones I should replace them with. Also why rules only seem to cover output?

All I understand is that ports are 110 and 25 (Could this be wrong?)
Dangertux, if you could instruct me on how to reset ufw according to method 2 it would be appreciated. Thank you for your time and patience. - :)

---

### Post by Dangertux on 2012-02-15
You might try the following and see if that works.

```

sudo ufw allow 143,993/tcp

```

That should help you out.

---

### Post by BlinkinCat on 2012-02-15
> **Dangertux said:**
> You might try the following and see if that works.

```

sudo ufw allow 143,993/tcp

```That should help you out.

Thanks very much Dangertux - One thing - Do I leave the rest of the installation as/is?

Thanks - :)

---

### Post by Dangertux on 2012-02-15
You can -- but you could probably also get rid of port 110.

You would be fine to leave it as is though.

---

### Post by BlinkinCat on 2012-02-15
> **Dangertux said:**
> You can -- but you could probably also get rid of port 110.

You would be fine to leave it as is though.

O.K. then Dangertux, I will give it a go.

Thanks very much for your time - :)

---

### Post by BlinkinCat on 2012-02-15
Hi again Dangertux - an update - I added your recommended code.

Result - Messages can be sent out without leaving copy in out file - this worked before but maybe there is an Thunderbird adjustment?

Incoming mail is delivered to server but does not come through. Did you see my remarks about ports 110 and 25 in #6 ?

Sorry to be a pain but I hope you can help me.

Edit - 1.  I just noticed 110 & 25 are mentioned in the Method 2 input - I really don't understand.
         2. In my ignorance, I can't understand why there is no mention of "Allow in" in ufw status.

Kind regards.

---

### Post by kevdog on 2012-02-16
Another way to look at your firewall rules are:
sudo iptables -L

This should print out all your chains.

---

### Post by BlinkinCat on 2012-02-16
> **kevdog said:**
> Another way to look at your firewall rules are:
sudo iptables -L

This should print out all your chains.

Thanks a lot kevdog - I'll have a look over the weekend - I'm a bit tied up right now.

But thank you very much - :)

I have had a bit of a look through the iptables, which to this old boy are a little difficult to grasp. I think I will mark this thread as solved for now although I intend to ask Dangertux a question about installing ufw about which I don't understand, in his other main thread. 

Cheers,

---

