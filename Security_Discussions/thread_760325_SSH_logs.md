---
title: "SSH logs"
date: 2008-04-20
forum: Security Discussions
---

### Post by DBQ on 2008-04-20
Does anybody know to view the ssh logs?

---

### Post by ibutho on 2008-04-20
I don't know of a specific ssh log file, but you can use the command "last" to see who logged in remotely" as well as check /var/log/messages.

---

### Post by hyperair on 2008-04-20
/var/log/auth.log is probably what you're looking for. When someone logs in through SSH it's shown there. If you're just looking for last commands executed then go check ~/.bash_history.

---

### Post by Dr Small on 2008-04-20
Try:
```
cat /var/log/auth.log | grep sshd
```

---

### Post by shane2peru on 2008-04-20
> **Dr Small said:**
> Try:
```
cat /var/log/auth.log | grep sshd
```

So if there is nothing there, even for ssh then that means there have been no attempts?  Or logins?  I had a bunch of hits on ssh, then installed denyhosts and set it to paranoid only internal LAN has access, and all attempts have disappeared!  

Shane

---

### Post by hyperair on 2008-04-21
If ssh doesn't appear there then it isn't even starting up. Also, this command would work as well:
```
grep sshd /var/log/auth.log
```

---

### Post by shane2peru on 2008-04-21
> **hyperair said:**
> If ssh doesn't appear there then it isn't even starting up. Also, this command would work as well:
```
grep sshd /var/log/auth.log
```

You mean the dameon?  That is starting because I ssh into the other computers in my LAN.   Just that no one is able to get in, or brut force attacks have ceased, at least I think.  

Shane

**EDIT:**  You are right, how odd, how would that have gotten shut off?  I logged into the other machine, and noticed that it did have logs on ssh, but, just the starting of it.  odd.  Thanks.

---

### Post by hyperair on 2008-04-21
SSH is a client-server thing. When you connect to a remote computer, the local computer is the client and the remote computer is the server. The daemon I am talking about is the server. It is **not** running on your system. sshd posts start up messages in the auth log. The fact that nobody can connect to your computer also shows that the daemon is stopped completely.

---

### Post by shane2peru on 2008-04-21
> **hyperair said:**
> SSH is a client-server thing. When you connect to a remote computer, the local computer is the client and the remote computer is the server. The daemon I am talking about is the server. It is **not** running on your system. sshd posts start up messages in the auth log. The fact that nobody can connect to your computer also shows that the daemon is stopped completely.

Yes, you are right, I edited my post above probably while you were typing this up.  I logged onto another machine and found that out.  Thanks. :)  How is it that my ssh would have been shutoff?  I figured it was automatic to have it on, if it is installed?  Perhaps I should keep it shut off?

Shane

---

