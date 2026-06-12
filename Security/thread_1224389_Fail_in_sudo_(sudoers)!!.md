---
title: "Fail in sudo (sudoers)!?!"
date: 2009-07-27
forum: Security
---

### Post by argos3016 on 2009-07-27
Well, the problem is when I go to change the configuration of firewall or any system configuration, ubuntu says:
"sudo: /etc/sudoers is mode 0777, should be 0440."
I supose that was a permission configuration and I reboot to recovery mode and change with chmod.
After this, the system says that I'm not in sudoers file, while and can't change ANY system configuration.
Help ubunters!:(

---

### Post by uzdawi on 2009-07-27
Same problem

---

### Post by cosine352 on 2009-07-27
follow this tutorial and you can login as root. Now you can add yourself back to sudoers.
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by damis648 on 2009-07-27
What command did you use exactly? It should be
```
chmod 440 /etc/sudoers
```

---

### Post by argos3016 on 2009-07-27
(for damis648) It was that command, yes.
(for cosine352 or an ubunter ) I'm some novice , tell me what  I should write on sudoers for config the system , please.
Thanks

---

### Post by damis648 on 2009-07-27
> **argos3016 said:**
> (for damis648) It was that command, yes.
(for cosine352 or an ubunter ) I'm some novice , tell me what  I should write on sudoers for config the system , please.
Thanks

Just making sure, it sounds as if you may have accidentally used 0440

---

### Post by argos3016 on 2009-07-27
Yeah I changed the sudoers file permissions with chmod to 777 going to recovery mode and the problem doesn't it's the first now.
Now the terminal says some about I'm not in sudoers file. "This error will be reported" or similar.

---

### Post by damis648 on 2009-07-27
> **argos3016 said:**
> Yeah I changed the sudoers file permissions with chmod to 777 going to recovery mode and the problem doesn't it's the first now.
Now the terminal says some about I'm not in sudoers file. "This error will be reported" or similar.

No, the permissions of /etc/sudoers **MUST** be 440.
```
chmod 440 /etc/sudoers
```
Boot into recovery mode and run that now.

---

### Post by argos3016 on 2009-07-27
Thanks , I can change the configuration.

---

### Post by cosine352 on 2009-07-27
remember to disable the root account after you are done (if you have enabled it ofcourse) from a sudoers account. 

> sudo passwd -l root

this is a good practice in terms of security.

---

