---
title: "Someone's been trying to crack my NAS"
date: 2009-08-21
forum: Security
---

### Post by Paqman on 2009-08-21
I've got a Qnap NAS on my home network. I happened to look in the access logs tonight and it looks like some chancer has been trying to bruteforce it over SSH.

The chink in my armour seems to be the NAS's FTP service, which i'd switched on recently to give me access while I was overseas on holiday. Since disabling the FTP service the attacks have stopped.

So i'm pretty happy that i'm no longer at risk, and I don't believe any of the attacks actually cracked the password. I've just installed GUFW and set it to deny all SSH connections to my desktop and set ufw logging just in case.

Any other sensible precautions I should be taking? I'm not particularly gripped up on security. For what it's worth I did trace the IP back to the source and send an email to the ISP involved, but i'm assuming only a complete novice would be that easily caught.

---

### Post by flux_user on 2009-08-21
*Any other sensible precautions I should be taking?*

Just a few thoughts here:
[LIST=1]
[*]Log in name and password (check password strength) also change the password for good measure in case it was  compromised.  Numbers, UPPER and lower case  letters with Special characters: $@#%%^ as part of your password.  Increase  the length of the password.  Use a Pass Phrase not just one word.  The word and phrase should not be in the dictionary.  Here  is an example take a phrase: 

"I like different types of cheeses" 
and turn that into a phrase or  world like: "%#%I55LkeDiffCheZes66#%"

[*]Make sure that you created and set a public and private key and have them installed for SSH/SFTP.  That way not only does the attacker need a login , password they also need your keys to gain access.  Need I say that you need to  keep your PRIVATE KEY SAFE?  If I do; keep your Private Key SAFE.
[*]Can you restrict access on your firewall/nat based on IP Address?  That way only a handful of IP address can get access or bounced.  The trick here is that you need to the static IP's.  
[*]Don't use FTP; use SFTP which comes with SSH.
[/LIST]

That's off the top of my head... Hope that helps...

---

### Post by Paqman on 2009-08-22
> **flux_user said:**
> *Any other sensible precautions I should be taking?*

Just a few thoughts here:
[LIST=1]
[*]Log in name and password (check password strength) also change the password for good measure in case it was  compromised.  Numbers, UPPER and lower case  letters with Special characters: $@#%%^ as part of your password.  Increase  the length of the password.  Use a Pass Phrase not just one word.  The word and phrase should not be in the dictionary.  Here  is an example take a phrase: 

"I like different types of cheeses" 
and turn that into a phrase or  world like: "%#%I55LkeDiffCheZes66#%"


My password was always pretty strong, and the access logs show  nobody connected except me, so i'm confident it's still good. Like you say though, it wouldn't hurt to change it.


> 
[*]Make sure that you created and set a public and private key and have them installed for SSH/SFTP.  That way not only does the attacker need a login , password they also need your keys to gain access.  Need I say that you need to  keep your PRIVATE KEY SAFE?  If I do; keep your Private Key SAFE.

Good call, i'll get onto this.

> 
[*]Can you restrict access on your firewall/nat based on IP Address?  That way only a handful of IP address can get access or bounced.  The trick here is that you need to the static IP's.  


*Technicially* my router will do this. In reality it was the first thing I enabled, and didn't seem to make any difference, the NAS was still logging the intrusion attempts. It's a crummy old router, but I still wasn't impressed.

> 
[*]Don't use FTP; use SFTP which comes with SSH.
[/LIST]

That's off the top of my head... Hope that helps...

I actually don't need the FTP on the NAS right now, so i've disabled it completely.

Cheers for the tips though!

---

### Post by Copernicus1234 on 2009-08-22
I would block the ssh port in the firewall and open it up manually for only the networks where your friends are. Why should the entire internet have access to it?

You can set it up so it allows their entire ip range if they have dynamic ip's. It still takes down the chance of getting hacked by at least 99%. People who cant connect cant hack. :)

---

### Post by dk06 on 2009-08-22
> **Paqman said:**
> I've got a Qnap NAS on my home network. I happened to look in the access logs tonight and it looks like some chancer has been trying to bruteforce it over SSH.

The chink in my armour seems to be the NAS's FTP service, which i'd switched on recently to give me access while I was overseas on holiday. Since disabling the FTP service the attacks have stopped.

So i'm pretty happy that i'm no longer at risk, and I don't believe any of the attacks actually cracked the password. I've just installed GUFW and set it to deny all SSH connections to my desktop and set ufw logging just in case.

Any other sensible precautions I should be taking? I'm not particularly gripped up on security. For what it's worth I did trace the IP back to the source and send an email to the ISP involved, but i'm assuming only a complete novice would be that easily caught.


Check out Snort (IDS & IPS) just make sure you configure it properly.  [http://www.snort.org/](http://www.snort.org/)

you may find some other tools useful at [http://sectools.org/](http://sectools.org/)

---

### Post by HermanAB on 2009-08-23
Howdy,

Usually it is quite effective to change your SSH Daemon port to something non standard in /etc/ssh/sshd_config (then restart sshd).  That simple trick seems to throw all the script kiddies off.  It won't throw off a real hacker though, since he can do a full port scan to see where SSH is.

Also note that password complexity can be traded off for length.  For example an 8 character password with complexity is equivalent to a 10 character password without complexity.  I usually use 12 to 16 character words with little or no complexity, since I find it easier to type a longer password than to shift in the right spots.

---

### Post by Paqman on 2009-08-24
> **HermanAB said:**
> Howdy,

Usually it is quite effective to change your SSH Daemon port to something non standard in /etc/ssh/sshd_config (then restart sshd).  That simple trick seems to throw all the script kiddies off.  It won't throw off a real hacker though, since he can do a full port scan to see where SSH is.


That's a good call, i've done that. The Qnap boxes actually have really good web admin facilities. Besides coming with SSH/Telnet access by default the web admin tools let you tweak these system settings from your browser.

I'm tempted to turn the FTP gateway back on to see if it was just script kiddies...

---

### Post by trundlenut on 2009-08-24
you don't change the SSH port on the NAS, do it on the router, because that is what the attack comes through, if you change the port on the NAS you'll have to change the router anyway.

---

### Post by HermanAB on 2009-08-24
Sure, but garden variety El'Cheapo routers cannot forward one port to another.

---

### Post by Paqman on 2009-08-24
> **trundlenut said:**
> if you change the port on the NAS you'll have to change the router anyway.

No you don't. Just specify what remote port you want SSH to use when you connect. Works fine.

Doing it on the router would be more comprehensive though, yes.

---

### Post by dmizer on 2009-08-25
Don't trust the security of your network to a password. Use rsa encrypted key pairs: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

