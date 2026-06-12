---
title: "Force password?"
date: 2012-03-14
forum: Security
---

### Post by ryuguns on 2012-03-14
Hai guise.

I've been having a problem that I think is ridiculous. I wanted to change my password, but my password choice was "too weak" according to Ubuntu, so, Ubuntu was discouraging me from using the password I wanted too, there's nothing wrong with that. However, when I wanted to change it, I just got a window requesting that I choose another password, I don't think my password choice is too weak, and I think that anything trying to force me not to use my preferred password is annoying. 

So, is there anyway to force it even if Ubuntu thinks it is too weak?

---

### Post by youngunix on 2012-03-14
Is this during the installation of ubuntu? If so, you should get a pop up window asking you to change or keep the password and continue.
[IMG]http://www.ubuntugeek.com/images/u9/10.png?iact=hc&vpx=542&vpy=149&dur=92&hovh=194&hovw=259&tx=140&ty=121&sig=108996081179537820530&ei=R-5gT4HdObPJsQLu362WCA&page=1&tbnh=133&tbnw=177&start=0&ndsp=18&ved=1t:429,r:2,s:0[/IMG]

---

### Post by Thewhistlingwind on 2012-03-14
```
man chpasswd
```

Good luck.

---

### Post by lovbuntu on 2012-03-14
I'm not sure if I follow what you are saying. If you click continued it should let you use the "weak password".

If you want to change the password after the installation, then login and do the following:

1. Open up a terminal and type ```
passwd
```
2. Press Enter
3. Type your new password
4. Press Enter again
5. Retype the same password
6. Press Enter again

Your password is now changed.

---

### Post by ryuguns on 2012-03-19
Late response, sorry. 
No, it's not from installation, it's from the settings.

---

### Post by SeijiSensei on 2012-03-19
1)  Open a Terminal
2)  Enter "man passwd" and read the documentation.
3)  Run "sudo passwd yourusername".  Enter your password when prompted to run the passwd program as the root user, then enter your new password twice when prompted.

---

### Post by snowpine on 2012-03-19
Try:

```
sudo passwd ryuguns
```

(substitute your actual username for 'ryuguns')

---

