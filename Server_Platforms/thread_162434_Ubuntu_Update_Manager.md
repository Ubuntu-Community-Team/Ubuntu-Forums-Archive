---
title: "Ubuntu Update Manager"
date: 2006-04-19
forum: Server Platforms
---

### Post by xrmuser on 2006-04-19
I am using ubuntu 2.6.12-9-386 (Breezy Badger). When I try to update it using Update Manager it says 'your system is up to date.'. 

I read there is a security issue regarding my Firefox browser version 1.0.7. I want to update it to 1.5 version. What should I do to automatically update it? 


CERT sent a security advisory. It says (portion of the advisory),

National Cyber Alert System

                 Technical Cyber Security Alert TA06-107A


Mozilla Products Contain Multiple Vulnerabilities

    Original release date: April 17, 2006
    Last revised: --
    Source: US-CERT


Systems Affected

      * Mozilla web browser, email and newsgroup client
      * Mozilla SeaMonkey
      * Firefox web browser
      * Thunderbird email client
      * Mozilla Suite

    Any products based on Mozilla components, particularly Gecko may also
    be affected.

III. Solution

Upgrade

    Upgrade to Mozilla Firefox 1.5.0.2, Mozilla Thunderbird 1.5.0.2, or
    SeaMonkey 1.0.1. According to Mozilla.org, Thunderbird 1.5.0.2 is
    to be released on April 18, 2006.

    Users are strongly encourages to apply the workarounds described in
    the individual vulnerability notes until updates can be applied.

---

### Post by aysiu on 2006-04-19
[QUOTE=xrmuser]
I read there is a security issue regarding my Firefox browser version 1.0.7. I want to update it to 1.5 version. What should I do to automatically update it?[/QUOTE] [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by mdsmedia on 2006-04-19
That's nice for Firefox. Did I read correctly. Are there any instructions for updating Thunderbird?

Additionally, I upgraded Firefox using sudo and the firefox upgrade feature. I don't have any Firefox extensions so I wasn't risking their ownership. What happens if I add extensions now?

---

### Post by aysiu on 2006-04-20
[QUOTE=mdsmedia]That's nice for Firefox. Did I read correctly. Are there any instructions for updating Thunderbird?[/quote] Sure. The instructions are here:

[https://wiki.ubuntu.com/ThunderbirdNewVersion](https://wiki.ubuntu.com/ThunderbirdNewVersion)

Someone also wrote [a Thunderbird install script](http://www.ubuntuforums.org/showpost.php?p=903590&postcount=4).

> 
Additionally, I upgraded Firefox using sudo and the firefox upgrade feature. I don't have any Firefox extensions so I wasn't risking their ownership. What happens if I add extensions now? Nothing, I hope, except that they get added. Extensions live in your /home/mdsmedia/.mozilla folder, not in the Firefox program folders.

If somehow *sudo* changed ownership of your profile, you can try ```
sudo chown -R mdsmedia:mdsmedia ~/.mozilla
```

---

### Post by mdsmedia on 2006-04-20
thanks aysiu. Do you have a life outside?

---

### Post by xrmuser on 2006-04-20
[QUOTE=aysiu][http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)[/QUOTE]
THANK YOU.  I was able to install it.:) It is now version 1.5.0.2.

---

### Post by aysiu on 2006-04-20
[QUOTE=mdsmedia]thanks aysiu. Do you have a life outside?[/QUOTE] Yeah, I check the forums during breaks at work and while watching TV with my wife and cat. Don't worry.

---

