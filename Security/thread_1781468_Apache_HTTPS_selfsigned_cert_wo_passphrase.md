---
title: "Apache HTTPS selfsigned cert w/o passphrase"
date: 2011-06-13
forum: Security
---

### Post by pcarlos853 on 2011-06-13
Hi!

I have been running a web server (Ubuntu 10.10/Apache) for the past few months. I now want to offer HTTPS. I don't mind if it being self signed because the people that use the server are very tech knowledgeable and I will tell them that the cert is self signed. I have set up HTTPS cert with a passphrase and everything works, but where the server is located there are some power outages. I need the server to start when the power is restored along with Apache. This will not happen when there is a passphrase on the cert. I was about to generate a new one with out a passphrase when I read this:

```
You can also run your secure service without a passphrase.         This is convenient because you will not need to enter the         passphrase every time you start your secure service. But it         is highly insecure and a compromise of the key means a         compromise of the server as well.         
```
([https://help.ubuntu.com/8.04/serverguide/C/certificates-and-security.html](https://help.ubuntu.com/8.04/serverguide/C/certificates-and-security.html))

If I decide to run the server with HTTPS with out a passphrase how is my server insecure? Would it be better to not use HTTPS or use HTTPS with out a passphrase?

Thanks!
Carlos

---

### Post by bodhi.zazen on 2011-06-13
Think of it this way, if you encrypt a file, but set a blank password, what good is the encryption ?

If someone has access to the server , either physical access or via leverage of a vulnerability, they can decrypt the https data without a password.

With that in mind, IMO it is a small vulnerability, and for your use I would not worry about it.

Now if you are doing financial transactions, then yes it is an issue.

---

### Post by BkkBonanza on 2011-06-13
I don't think this is much of a concern for you. People forget that if someone gets physical access or gets root access on your system they can just replace the certificate with their own anyway. The passphrase isn't going to stop that. 

However, make real sure that write access for the cert/keys is root only. And read access for the key is root only. I've always thought that it's more important the server restarts without intervention. 

Your server is still just as secure for website use and only vulnerable to root access - but as mentioned, when someone gets root access they can do anything they like and you have bigger problems.

---

### Post by pcarlos853 on 2011-06-13
I think I will continue to run HTTP and run a VPN for sensitive content. Anyway thanks for the quick replies! 

Thanks,
Carlos

---

