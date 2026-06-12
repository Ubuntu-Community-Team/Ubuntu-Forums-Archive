---
title: "online banking on an ubuntu spare machine"
date: 2010-03-25
forum: Security
---

### Post by insecureboy on 2010-03-25
situation:

I have dedicated an old PC to do online banking and nothing else on it.
I did a boot and nuke w/ DBAN, and then got ubuntu 9.10 on it with all the updates
 
It's connected to internet using a belkin router and the only thing i do on it is: 
- turn the PC on
- log in to ubuntu 
- (update, if any, and restart)
- fire up firefox and start private browsing (though it shouldn't matter much in this case)
- go to the bank website and login
- sign out and close firefox once done
- turn off the computer

I have changed the default pass on my router, becuz of some stuff I read about router attack and getting my router's dns settings changed by some malware or scripts in a webpage I shouldn't visit.... 

I also can type in "198.96.179.190" in my browser instead of BMO.com if that helps any. But it wasn't recommended by my bank or any other source. I just got that ip by typing bmo.com in this website:   [http://www.mob.net/~ted/tools/dns.php3]("http://www.mob.net/%7Eted/tools/dns.php3")  
( If you have a better way of checking the dns health plz let me know )

Qustion: Is there any MAJOR threat that i am missing and therefore still vulnerable to??? if so plz let me know about it.


Qustion2: Is there any MINOR threat that i am vulnerable to???

:D thanks

---

### Post by HermanAB on 2010-03-25
Yeah, you'll be fine.  I don't do banking on Windows machines.  Well, I don't do *anything* important on Windows machines.

However, don't be too complacent.  Always use strong passwords for everything.  By strong I mean more than 9 characters.

---

### Post by captain_171 on 2010-03-25
If I could recommend some thing on online banking and passwords.
Use a password program that keeps track of STRONG passwords and use that program to make your password so its random and secure. Make sure to use a strong password to protect the password database program. and then also backup that database so you never lose that database.

Programs I would use
Ubuntu with all the security updates installed
Encrypted home folder that holds my Firefox program and my firefox data.
ROOT DNS look-up so your DNS could not be hacked because your DNS look-up is being done from the root servers
Firefox with private browsing mode on with noscript installed and a separate profile just for banking.
Keepass password database with a 20 digit password with a keyfile that I keep on a USB flash drive Keepass encrypted that database using AES 256 encryption
Keep the Keepass database in my Dropbox that backs it up online when ever I save it so I never lose it.



All these programs are free. 

Truecrypt I would recommended for the end user to encrypt there data using AES 256 encryption its easyer to use and it can mount the encrypted data anywhere. and also cross platform
[http://www.truecrypt.org/](http://www.truecrypt.org/)

Noscript provides extra protection for firefox and other browsers that controls insecure add-ons such as JavaScript, java, flash and other plugins. 
[noscript]("http://noscript.net/")

Dropbox gives you 2GBs for free and cross platform online backup solution
[http://www.dropbox.com]("http://www.dropbox.com/")

Keepass is a open source password database and cross platform
[http://keepass.info/](http://keepass.info/)


If you need any help setting this up just reply.

---

### Post by rookcifer on 2010-03-25
You are more likely to be compromised by a spoofed SSL cert than by malware on a Linux machine.  The government, for instance, is using [router applicances]("http://www.wired.com/threatlevel/2010/03/packet-forensics/") which allow them to spoof SSL certs and perform MITM attacks on traffic.  The problem is the certificate authorities (there are over 100 CA's out there).  In some cases, these CA's are not trustworthy and will provide criminals or Feds forged certificates.  So, basically, SSL is only as good as the CA is trustworthy.

I realize most people aren't worried about Feds, but there is no doubt criminal gangs use these appliances and forged certs too.

---

### Post by OpSecShellshock on 2010-03-25
It might also be a good idea to see if the bank's website has a feature that allows you to prohibit wire transfers being initiated during online banking sessions. If possible, it would be good to ensure that the only way a wire transfer can be initiated is for you to physically walk into a branch office and speak to a human teller. That way if some sort of account compromise does happen, you've eliminated the most commonly used means of theft.

Oh, and you may want to edit your post to remove the real name of your bank and its IP address. There's no info that could identify you or enable you to be contacted outside of this forum, which is good (breaks the possibility of associating the name of your bank with you as a specific individual), but it's never a bad idea to develop habits of online communication whereby you withhold non-essential information.

---

### Post by insecureboy on 2010-03-25
> **captain_171 said:**
> If I could recommend some thing on online banking and passwords.
Use a password program that keeps track of STRONG passwords and use that program to make your password so its random and secure. Make sure to use a strong password to protect the password database program. and then also backup that database so you never lose that database.

Programs I would use
Ubuntu with all the security updates installed
Encrypted home folder that holds my Firefox program and my firefox data.
ROOT DNS look-up so your DNS could not be hacked because your DNS look-up is being done from the root servers
Firefox with private browsing mode on with noscript installed and a separate profile just for banking.
Keepass password database with a 20 digit password with a keyfile that I keep on a USB flash drive Keepass encrypted that database using AES 256 encryption
Keep the Keepass database in my Dropbox that backs it up online when ever I save it so I never lose it.



All these programs are free. 

Truecrypt I would recommended for the end user to encrypt there data using AES 256 encryption its easyer to use and it can mount the encrypted data anywhere. and also cross platform
[http://www.truecrypt.org/](http://www.truecrypt.org/)

Noscript provides extra protection for firefox and other browsers that controls insecure add-ons such as JavaScript, java, flash and other plugins. 
[noscript]("http://noscript.net/")

Dropbox gives you 2GBs for free and cross platform online backup solution
[http://www.dropbox.com]("http://www.dropbox.com/")

Keepass is a open source password database and cross platform
[http://keepass.info/](http://keepass.info/)


If you need any help setting this up just reply.



thanks for the reply 
- in the case of Strong passwords -----<< I actually do use very long as* random set of characters so they are strong  ---- and i think i have a better solution than to keep them encrypted in my computer >> I just write them on paper and put the papers in a safe box :D that cost me 140 dollors :D -- but thanks for the point rechecking always helps...

- and about noscript i am actually using it right now on this machine that is not for banking but on the banking-PC I dont feel the need for it since i only and only visit my bank website and as a matter of fact i feel uncomfortable installing noscript on that becuz of the bad history noscript developer has of misusing public trust ( remember he designed his addon to cause incompatibilities with adblock and sort of tried to keep them secret until somebody figured it out)


- in the case of ROOT DNS i am not sure if i know how to do it so if u have some tutorial or some more info i'd be happy to read.

---

### Post by insecureboy on 2010-03-25
> **rookcifer said:**
> You are more likely to be compromised by a spoofed SSL cert than by malware on a Linux machine.  The government, for instance, is using [router applicances]("http://www.wired.com/threatlevel/2010/03/packet-forensics/") which allow them to spoof SSL certs and perform MITM attacks on traffic.  The problem is the certificate authorities (there are over 100 CA's out there).  In some cases, these CA's are not trustworthy and will provide criminals or Feds forged certificates.  So, basically, SSL is only as good as the CA is trustworthy.

I realize most people aren't worried about Feds, but there is no doubt criminal gangs use these appliances and forged certs too.

thanks for the reply 
you pointed me to some interesting new topic i will do a whole research on spoofed certificate attacks and on Man in the middle thing]]]]

also can u tell me if i am in danger of this,,,, assuming that i am typing my banks website in the address bar and i know that for example the website for bank of montreal is bmo.com

---

### Post by insecureboy on 2010-03-25
> **OpSecShellshock said:**
> 
Oh, and you may want to edit your post to remove the real name of your bank and its IP address. There's no info that could identify you or enable you to be contacted outside of this forum, which is good (breaks the possibility of associating the name of your bank with you as a specific individual), but it's never a bad idea to develop habits of online communication whereby you withhold non-essential information.

Hmmm good point i'll try to askk my question in more abstract ways next time but in this case i am actually not with bank of montreal anymore(since two years ago) as a matter of fact i am not any where close to the borders of BMO :D hehehehehhe

---

