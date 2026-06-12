---
title: "Is VNC secure?"
date: 2010-02-13
forum: Security
---

### Post by ubudog on 2010-02-13
Hello, I am using firestarter as my firewall.  I setup a remote desktop connection in System>Preferences>Remote Desktop, got a domain at dyndns.org and configured my router properly.  Now all is ready except for the firewall.  In my configuration of the remote desktop, I set it up so that it would ask the user to enter a password before allowing them to access my machine.  If I enable VNC for everyone in firestarter, would it be easy for someone to get around the password?

---

### Post by lovinglinux on 2010-02-13
> **ubudog said:**
> Hello, I am using firestarter as my firewall.  I setup a remote desktop connection in System>Preferences>Remote Desktop, got a domain at dyndns.org and configured my router properly.  Now all is ready except for the firewall.  In my configuration of the remote desktop, I set it up so that it would ask the user to enter a password before allowing them to access my machine.  If I enable VNC for everyone in firestarter, would it be easy for someone to get around the password?

No, is not secure. I read some comments from bodhi.zazen somewhere saying that lots of machines cracked are from VNC users that don't take additional measures to lock it down. If you really need to use VNC, you should for example tunnel it through ssh and use encrypted key authentication instead of password authentication.

See these:

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

BTW, Firestarter is also not recommended. Use UFW instead, which is installed by default. You can install gufw, if you need a graphical interface.

---

### Post by bodhi.zazen on 2010-02-14
VNC is by far the most commonly cracked server on these forms. There are two problems with VNC :

1. Passwords are not encrypted, thus they can potentially be intercepted.

2. Weak passwords. Weak passwords are easily cracked.

I agree, it is best to either use ssh (ssh -X forwards X applications, you can run XMing with is a protable X server for Windows) or tunnel your VNC over SSH or use FreeNX.

I also suggest you use ufw or GUFW over firestarter.

---

### Post by lovinglinux on 2010-02-14
I wonder why VNC is included with Ubuntu by default?

---

### Post by LOLbuntu on 2010-02-14
Vnc is not secure, if you are going to use it make sure the client and server is encrypted and uses ssh.

---

### Post by bodhi.zazen on 2010-02-14
> **lovinglinux said:**
> I wonder why VNC is included with Ubuntu by default?

My only guess is that VNC is very popular with Windows users.

Although VNC is included, it is not enabled, nor is port forwarding, so it still requires users to enable.

Perhaps a warning about security would be in order.

---

### Post by ubudog on 2010-02-14
OK, I will just stick to ssh.  I have keys set up with ssh and I disabled password authentication. Is that enough?

---

### Post by bodhi.zazen on 2010-02-14
> **ubudog said:**
> OK, I will just stick to ssh.  I have keys set up with ssh and I disabled password authentication. Is that enough?

Probably. I always add a few rules to iptables or install denyhosts / fail2ban .

---

### Post by CharlesA on 2010-02-14
Second that. ^

You could always tunnel vnc over ssh, but if you don't need a gui, ssh is fine.

---

### Post by 2hot6ft2 on 2010-02-14
If you want a secure remote desktop you may want to checkout the how to in my sig. I like it and it's secured in several ways.

---

### Post by ubudog on 2010-02-14
> **bodhi.zazen said:**
> Probably. I always add a few rules to iptables or install denyhosts / fail2ban .

I installed fail2ban.  I can also use ssh -X right?

---

### Post by HermanAB on 2010-02-14
VNC is probably OK on a LAN, but it is really a Windows thing.  SSH is secure and more powerful than VNC.  However, you should always use passwords of length 9 characters or longer.  The minimum password length and complexity can be enforced by PAM and if the Ubuntu developers are guilty of negligence, then this is one.

---

