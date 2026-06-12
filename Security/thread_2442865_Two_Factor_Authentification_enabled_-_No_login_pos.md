---
title: "Two Factor Authentification enabled - No login possible"
date: 2020-05-08
forum: Security
---

### Post by drdemo on 2020-05-08
Hi,

I followed [this tutorial]("https://ubuntu.com/tutorials/configure-ssh-2fa#1-overview") to enable 2FA on my server. I followed the tutorial on the root user, as I wanted the root user only to get secures via 2FA. As I wanted to relogin and try out if everything worked, it said Access Denied after entering my password. I have tried it now many times, everytime it gives me an Access Denied. I saved the emergency scratch codes. How do I gain access again?

Thanks.

---

### Post by EuclideanCoffee on 2020-05-08
Did you add the secret key to the authentication application? You should be prompted for a challenge. Be sure you have Internet connection.

---

### Post by drdemo on 2020-05-08
Yes it's added, I see new codes generated every few seconds.

---

### Post by EuclideanCoffee on 2020-05-08
You're logging into SSH or local (TTY/GMD)?

---

### Post by drdemo on 2020-05-08
Ssh

---

### Post by EuclideanCoffee on 2020-05-08
Can you log in locally without ssh? I'm afraid you aren't receiving the prompt.

Edit: Have you tried a reboot?

---

### Post by drdemo on 2020-05-08
I can reboot the server tonight, however I was hoping to find a solution without a reboot.
The server is being rent from an dedicated server company, which has remove login only. Unfortunatelly, don't have the option to login locally.

---

### Post by EuclideanCoffee on 2020-05-08
I'm hoping that the reboot would restart openssh-server and enable the challenge prompt. If not, you may need to login locally. Wishing you the best.

---

### Post by jmginer on 2020-06-05
Maybe you can ask your provider for a KVM-IP connection.

---

### Post by kevdog on 2020-06-06
Just restart the openssh service and see what happens and possibly the PAM daemon.  And just a "dad" type I hope you learned your lesson warning - "When enabling security measures on live systems that have the potential of locking you out completely, its probably best to try this approach on a test system first rather than initially on the production system".  I hope you get the system working and good luck to you.

---

