---
title: "Sending of a GPG key to keyserver.ubuntu.com Failed"
date: 2009-05-09
forum: Security
---

### Post by delphiexile on 2009-05-09
Hi everybody;

I have generated a GPG key, but when I tried to send to keyserver.ubuntu.com using this command:

```

gpg --send-keys --keyserver keyserver.ubuntu.com <My Key ID>

[COLOR="Red"]**(I have replaced <My Key ID> with the ID I've generated)**[/COLOR]

```

... Terminal shows me this error:

```

gpg: keyserver timed out
gpg: keyserver send failed: keyserver error

```

Firstly I thought that the server is being repaired, so I asked if it is like that , they told me no , and it is accessible via http and ldap and that I've have a with my network. But i don't how to check my connection if we know that I've a PPPoE connection.

Thanks for helping me.

---

### Post by cariboo on 2009-05-09
I seem to have a problem accessing the key server from where I am, I would suggest trying it a little later today.

---

### Post by delphiexile on 2009-05-09
OK , thanks sir, I'll see it tomorrow!!

---

### Post by delphiexile on 2009-05-11
I'm trying now at other server , but the same problem , when I send the key , the same error happens , I think there is something to do with the internet connection.

---

### Post by cariboo on 2009-05-11
I just check the Ubuntu key server, and connected right away. Maybe this [howto]("http://help.ubuntu.com/community/GnuPrivacyGuardHowto") will help.

---

### Post by delphiexile on 2009-05-12
I read it , but it doesn't solve my problem ....

---

### Post by cariboo on 2009-05-12
Are you having the problem when you're running from the command line as well as from firefox?

---

### Post by delphiexile on 2009-05-12
> **cariboo907 said:**
> Are you having the problem when you're running from the command line as well as from firefox?

Yes , and Epiphany too.

---

### Post by cariboo on 2009-05-12
I'm wondering if you are suffering from an ipv6 problem. Have a look at this [thread=1137127]thread[/thread] to see if any thing here solves the problem.

---

### Post by delphiexile on 2009-05-13
Unfortunately I think I'm not suffering from that , because I tried all the methods cited in the subject but without any effect so I've reset everything to its original state. Someone advised me to use the GUI "Password and Encryption Keys" but it doesn't work too.

---

### Post by delphiexile on 2009-05-14
What can you say to help me !! Please.

---

### Post by delphiexile on 2009-05-14
For more information about this problem , I opened a discussion here and I answered many questions about my issue , you may have some info .

[https://answers.launchpad.net/launchpad/+question/70532](https://answers.launchpad.net/launchpad/+question/70532)

---

### Post by Daeluin on 2009-08-15
for me it wasn't timing out but said "couldn't resolve keyserver.ubuntu.com"

so I used host keyserver.ubuntu.com to check if I could resolve at all, and it worked... so then I just replaced the domain with the ip and it worked fine. (if anyone is having a resolution problem try that)

---

### Post by cariboo on 2009-08-15
There are instructions [here]("https://help.launchpad.net/YourAccount/ImportingYourPGPKey") for creating a gpg key and registering it.

---

### Post by delphiexile on 2009-10-16
Accessing to keyserver.ubuntu.com is denied from my connection operator , i discovered this by an experience. thanks to all people who has posted in this thread.

---

