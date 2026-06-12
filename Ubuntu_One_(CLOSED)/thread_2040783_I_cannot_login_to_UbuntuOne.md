---
title: "I cannot login to UbuntuOne"
date: 2012-08-11
forum: Ubuntu One (CLOSED)
---

### Post by oscarivera9 on 2012-08-11
Help!!!
I can't login to UbuntuOne.  I have a new PC and in the process of setting it up, I decided to setup UbuntuOne.  Unfortunately, I used the wrong account by accident.  When I tried to change the account so that I could use the correct & current account, I ran into problems.  I could login but nothing was able to sync.  After trying a couple of things, I decided to just go ahead and uninstall UbuntuOne and reinstall it to start fresh.  I followed the guidelines that I found here: 
[https://one.ubuntu.com/help/faq/how-do-i-completely-remove-and-reinstall-ubuntu-one/](https://one.ubuntu.com/help/faq/how-do-i-completely-remove-and-reinstall-ubuntu-one/)

Part of the uninstall/reinstall process meant that I had to remove the UbuntuOne folder under "Passwords & Encryption" and I believe that this is causing my current problem.  Now I cannot login at all, in fact I can't even create a new account.  Just to check if my Ubuntu Single Sign On was working properly I tried to login to my account through the Ubuntu Software Center and I couldn't do that either.  I can sign in just fine through my other PC and my Android as well as through my new PC if I use Firefox.
I really need to be able to sign on to both of these places so any help would be highly appreciated.

Thanks

---

### Post by om_arino on 2012-08-12
I have the same problem.

---

### Post by masticate on 2012-08-15
I had a similar problem and it seems I was lacking in the proper SSL certificate. I was missing the file /usr/share/ca-certificates/mozilla/ValiCert_Class_2_VA.crt.

Please run the following in the terminal and post the response:
```
cd /tmp
wget http://people.canonical.com/~roman.yepishev/us/qtsslrequest.py
python qtsslrequest.py
```


Reinstall the certificates:
```
sudo apt-get install --reinstall ca-certificates
```

---

### Post by darraughbj on 2012-08-18
> **masticate said:**
> I had a similar problem and it seems I was lacking in the proper SSL certificate. I was missing the file /usr/share/ca-certificates/mozilla/ValiCert_Class_2_VA.crt.

Please run the following in the terminal and post the response:
```
cd /tmp
wget http://people.canonical.com/~roman.yepishev/us/qtsslrequest.py
python qtsslrequest.py
```


Reinstall the certificates:
```
sudo apt-get install --reinstall ca-certificates
```

Absolutely excellent, this problem had been nagging me all day and this was the solution, thank you so much.

---

### Post by Dy1anW on 2012-08-19
> **masticate said:**
> I had a similar problem and it seems I was lacking in the proper SSL certificate. I was missing the file /usr/share/ca-certificates/mozilla/ValiCert_Class_2_VA.crt.

<snip...>

Many thanks!

I had this problem too. I just wanted to download all my docs on my new laptop, but couldn't as U1 would just sit there trying to log in. Downloading files now  :guitar:

---

### Post by oscarivera9 on 2012-08-24
masticate,
thanks for your help.
It seems like lots of us had the same problem and it has been fixed

---

### Post by JonPaul on 2013-05-12
Excellent - thanks for this!

---

### Post by Vhumbani on 2013-08-25
> **masticate said:**
> I had a similar problem and it seems I was lacking in the proper SSL certificate. I was missing the file /usr/share/ca-certificates/mozilla/ValiCert_Class_2_VA.crt.

Please run the following in the terminal and post the response:
```
cd /tmp
wget http://people.canonical.com/~roman.yepishev/us/qtsslrequest.py
python qtsslrequest.py
```


Reinstall the certificates:
```
sudo apt-get install --reinstall ca-certificates
```

had the same problem thanks

---

### Post by miromarchi on 2014-03-09
Hi, thanks for the advice.
In my case I had also to remove the saved password for ubuntu one in password app.

---

### Post by Dragonbite on 2014-03-12
I'm going to try this tonight.

---

