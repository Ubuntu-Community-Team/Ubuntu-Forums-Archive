---
title: "Firewall"
date: 2013-02-16
forum: Security
---

### Post by ChrisInNevada on 2013-02-16
I am a newbie to Ubuntu.  I've been reading information on how to turn on the default firewall and it might as well be written in Greek. 

I have located Network Settings options for iPv4 and iPv6  and have turned them on.  Is this the correct way to activate the Ubuntu firewall?

Also, I have noticed that since enabling these settings I can no longer access Options in Network settings.  How can I access the Options settings again?  Thanks!

---

### Post by leclerc65 on 2013-02-16
I would install Gufw, Enable it, choose DENY IN, ALLOW OUT - for the moment - until I understand more Greek.:p

---

### Post by PIE09gbLmgG6 on 2013-02-16
Sorry for being such a newb...I was under the assumption that firewall and virus etc came turned on and runnning and all that with ubuntu?

Very new here...

ego-

---

### Post by ChrisInNevada on 2013-02-16
New to Ubuntu and lost.  If someone could point me in the right direction of where I can find, access and manage UFW settings, please?

---

### Post by deadflowr on 2013-02-16
ufw a command line program.

 Open a terminal and use:

```
man ufw
```

to enable it simply:

```
sudo ufw enable
```

beyond that is simply tweaking rules to fit your needs.

---

### Post by coffeecat on 2013-02-16
Community documentation, UFW:

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

And the gufw GUI frontend:

[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

---

### Post by Ms. Daisy on 2013-02-16
> **ChrisInNevada said:**
> I have located Network Settings options for iPv4 and iPv6  and have turned them on.  Is this the correct way to activate the Ubuntu firewall? No, that's got nothing to do with the firewall. 

To enable the firewall:

Open a terminal by pressing ctrl + alt + t.
type in ```
sudo ufw enable
```and you're done.  It will allow all out and deny all incoming by default, which will be fine for you until you learn more.  

It will also stay enabled from now on even after you reboot until you specifically disable the firewall by typing ```
sudo ufw disable
```

---

### Post by coffeecat on 2013-02-16
Threads merged. One thread per topic, please.

---

### Post by ChrisInNevada on 2013-02-16
ctrl alt t is what I was looking for.  Thank you, Ms Daisy!

---

### Post by Ms. Daisy on 2013-02-16
> **egosophist said:**
> Sorry for being such a newb...I was under the assumption that firewall and virus etc came turned on and runnning and all that with ubuntu? Read the basic security wiki, it's designed specifically to answer your questions.

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

TL;DR version: the firewall is installed but not enabled by default.  

There is no anti-virus software in the world that will scan for linux viruses, they all scan for Windows and maybe Mac viruses.  So for a new Linux user there is no point in running anti-virus.  However, there are OTHER security controls that you might want to implement that would actually be effective.  Again, read the basic security wiki for details.

---

