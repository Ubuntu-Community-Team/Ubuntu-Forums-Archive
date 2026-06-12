---
title: "SSH access denied"
date: 2007-06-19
forum: Server Platforms
---

### Post by ozpak on 2007-06-19
Bear with me I have only basic Linux / SSH understanding

I have Ubuntu Edgy server up on a public IP address
I have the SSH server up and running - I can SSH to 127.0.0.1 fine within the server
I have opened up the right port at the firewall
I can telnet to the SSH port and see that OpenSSH is waiting for connections

Then using putty to SSH connect remotely I am getting:

"Access denied"

Any ideas?

---

### Post by Mr. C. on 2007-06-19
Check your sshd_config for :

```
ListenAddress 0.0.0.0

```
If you have only 127.0.0.1, ssh is only listening on the loopback interface.  Change it to above and restart sshd.

MrC

---

### Post by ozpak on 2007-06-20
Thanks for response.

I enabled this line in sshd_config and restarted sshd however still same thing

I can telnet to the port and it gives a message about OpenSSH so it looks to be listening ok.

It seems to be something to do with the authentication mechanism - I just want to be able to enter a local username / password.

I have also enabled the line:
> PasswordAuthentication yes

---

### Post by Mr. C. on 2007-06-20
Enable Putty's session logging, and see where things are failing from the client end.

From the server end, you'll have to enable a higher level of logging to see what is failing.  See the LogLevel variable in the sshd_config man page.  Set and restart; then retry your connection.  Check your /var/log/auth.log.

Oh, and you're not trying to connect as root are you ?  If so, you need to allow root.

MrC

---

### Post by ozpak on 2007-06-20
Thanks think I am getting closer.

Looking in the auth.log the SSH server is getting dictionary attacked from different IP addresses! I can see why certificate authentication is a much better solution to un/pw.

sshd looks to be running find and accepting connections, there is just and authentication problem going on. 

Might switch it off for a while until these hackers move on and try again later.

Thanks heaps for your help Mr C.

---

### Post by MJN on 2007-06-20
> **ozpak said:**
> Might switch it off for a while until these hackers move on and try again later.
 
You'll be waiting a long time! As soon as the current set move on there'll be more!
 
Keep on with the debugging of your present problem - the bruteforce logins are a seperate issue to address.
 
Mathew

---

### Post by Mr. C. on 2007-06-20
Do you log-reading eyes a favor; move SSH to another port (eg. 221).  This will avoid the standard scripts probing for access, reducing the noise to essentially nil.

Looking foward to seeing what you uncover in your debugging.

MrC

---

