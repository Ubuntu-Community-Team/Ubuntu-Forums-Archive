---
title: "I've definitely been hacked..."
date: 2006-08-21
forum: Server Platforms
---

### Post by chouta on 2006-08-21
OK guys, so I've definitely been hacked... I just can't figure out whether it was remotely or locally, so I need your help to bounce ideas/feedback:(  

Here's the rundown.  I left my machine running over the weekend with the user logged in (gnome was running).  I came back and to my horror deduced someone had been browsing porn in firefox. Traces were all over the history file and 2 porn avi files were left in my home folder (likely the default d/l folder in firefox).  

So I got nervous, started looking up the logs to see if it was a local attack (I live with housemates) or remote (I run SSH and Apache for web dev stuff) 

I traced down some suspicious messages in the messages.log: 

Aug 20 14:23:52 localhost kernel: [17270476.072000] atkbd.c: Unknown key release
d (translated set 2, code 0x81 on isa0060/serio0).
Aug 20 14:23:52 localhost kernel: [17270476.072000] atkbd.c: Use 'setkeycodes e0
01 <keycode>' to make it known.

This snippet tells me that somebody tried to hit an as-yet unprogrammed internet key on my internet/multimedia keyboard when I was not home.  So I was pretty convinced at this point one of my housemates used my box without my permission. No biggie.   

Now here's the shocker that confused me.  I had to check whether somebody was hacking me remotely.  So for the first time ever since I set up my Ubuntu box (I know, bad me), I started looking up the auth.log, and discovered hundreds of lines of these: 

Aug 15 10:05:22 localhost sshd[11412]: Invalid user admin from xxx.xx.xx.xxx
Aug 15 10:05:22 localhost sshd[11412]: (pam_unix) check pass; user unknown

with the same rhost checking for user names such as admin, test, mysql, apache, etc etc.  for days.  

Then another attacker with this: 

Aug 20 13:01:41 localhost sshd[7677]: (pam_unix) authentication failure; 
logname= uid=0 euid=0 tty=ssh ruser= rhost=xxx.xx.xxx.xxx  user=root

with hundreds of tries, one overy 5 seconds or so.

(I'm hiding the rhost part cuz don't want to arouse "his" suspicion) 

So now I'm totally confused.  Was I remotely hacked or locally hacked.  Who left all that porn and traces in my history file?  And what should my next move be?!! 

Please help out a desperate and confused fellow Ubuntu user! 

Thanks in advance guys!

---

### Post by encompass on 2006-08-21
This form of attack is not uncommon.  There are computers that have been hijacked or are used to attack people with small programs looking ofr common passwords and information.
I get them all the time... but change my password enough and keep it complicated enough that people can't get in.
Another way to avoid atacks is to change your port number for all of your services.  Some you can't change like port 80 but others like you ssh can change.
I like to switch common ports around. Like, my ssh is not 5901 and my vnc is not 21.  It helps... and an even bigger thing... if you don't use it don't run it.  Many users have ftp installed when they really only need ssh.
Don't leave your computer open/on when you don't need it.
And don't activate your root acount or give everyone your account rights.
you can look at the files creation time... it will give you a time frame when they were on.
Then check every flipping log to find stuff from that time.  Lets hope they didn't have total rights to your computer.  And a local attack likes to look at porn.  Why would someone look at stuff with ssh.
Oh baby you look so good.  those D's and G's are amazing!
JK
Hope this helps you or someone else.

---

### Post by Sam on 2006-08-21
Reading your story I don't think you have been remotely cracked. The entries in your logs files refers to script kiddies around the world how try to access your box (unsuccessfuly: "Invalid user xxx", "(pam_unix) authentication failure"). I own two servers and my daily reports shows me hundreds of attack attempts like this.

I'm pretty sure that this his one of your housemate which uses your computer (a cracker won't browse porn from a remote computer, except for illegal porn).


Next time remember to lock your session, or create separates accounts for your housemates.

---

### Post by chouta on 2006-08-21
Thanks encompass, sam... Sane words of advice.  

So what I did now: I changed all my passwords, installed Firestarter and  allowed ssh connections from only the external IPs I connect from,  and stopped ssh from allowing root access. Oh, I log off my local sessions too.  

This should hold the fort down for awhile :)

Thanks again!

---

### Post by Sam on 2006-08-21
> **chouta said:**
> Thanks encompass, sam... Sane words of advice.  

So what I did now: I changed all my passwords, installed Firestarter and  allowed ssh connections from only the external IPs I connect from,  and stopped ssh from allowing root access. Oh, I log off my local sessions too.  

This should hold the fort down for awhile :)

Thanks again!

If you want to secure ssh more, disable password logins and use authentication with certificate.

---

### Post by Lord Illidan on 2006-08-21
It could be a local attack (ie someone looking at porn from your machine) occuring at the same time as a remote one.

Lock it up is my advice.

---

### Post by jreid08 on 2006-08-22
> **Sam said:**
> If you want to secure ssh more, disable password logins and use authentication with certificate.

Where can you find information on how to use this?  I'm assuming that this is something you'd use pagent for?  Problem is the documentation for pagent sucks so if you can explain - we'd all appreciate it!

---

### Post by Sam on 2006-08-23
> **jreid08 said:**
> Where can you find information on how to use this?  I'm assuming that this is something you'd use pagent for?  Problem is the documentation for pagent sucks so if you can explain - we'd all appreciate it!

Sorry I used the wrong term. This is "public key" not "certificate".

I don't know what pagent is, but basicaly that's how public keys work with ssh:

You create your own key. You upload it on your ssh server, then next time, instead of being asked for your ssh password, you'll be asked for your key password. You can also use ssh-agent to authenticate just once then you'll be logged to a remote ssh without any password. This is very convenient.

If you disable ssh passwords to use only public keys, people without their key within the ssh server will be immediatly rejected.

Read [this](https://help.ubuntu.com/community/SSHHowto).

---

### Post by jreid08 on 2006-08-24
> **Sam said:**
> Sorry I used the wrong term. This is "public key" not "certificate".

I don't know what pagent is, but basicaly that's how public keys work with ssh:

You create your own key. You upload it on your ssh server, then next time, instead of being asked for your ssh password, you'll be asked for your key password. You can also use ssh-agent to authenticate just once then you'll be logged to a remote ssh without any password. This is very convenient.

If you disable ssh passwords to use only public keys, people without their key within the ssh server will be immediatly rejected.

Read [this](https://help.ubuntu.com/community/SSHHowto).

I'm sorry too!](*,) I didn't spell it correctly but I'm talking about Pageant (an SSH authentication agent for PuTTY, PSCP and Plink) located at [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) if anyone knows how to use this I'm sure many would appreciate a brief tutorial.:D

Perhaps the point I'm missing is that you don't have to use a tool like this?  I can't find a thread in the forums that seems to be what I'm looking for.

---

### Post by Sam on 2006-08-24
> **jreid08 said:**
> I'm sorry too!](*,) I didn't spell it correctly but I'm talking about Pageant (an SSH authentication agent for PuTTY, PSCP and Plink) located at [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) if anyone knows how to use this I'm sure many would appreciate a brief tutorial.:D

Perhaps the point I'm missing is that you don't have to use a tool like this?  I can't find a thread in the forums that seems to be what I'm looking for.

These tools are for Windows, in Linux they're already in the system. They are ssh, ssh-agent, scp, ...). But you can also use nautilus to browse a remote ssh (using the address ssh://example.org/).

In Windows there is a good ssh browser called [WinSCP](http://winscp.net/eng/index.php).

I don't know if I answered your problem, if not please explain more what you need.

---

### Post by helmet on 2006-08-25
umm....lock your desktop?? lol

don't worry about the auth.log stuff...i work at the university of alberta, and as such we have a real world Class B subnet. once a few people figure this out, every time a new server comes up, the auth log fills up with a whack of invalid user stuff because people just run their little bots and try to find a way (they never do).

---

### Post by skymt on 2006-08-28
> **Sam said:**
> These tools are for Windows, in Linux they're already in the system. They are ssh, ssh-agent, scp, ...). But you can also use nautilus to browse a remote ssh (using the address ssh://example.org/).

In Windows there is a good ssh browser called [WinSCP](http://winscp.net/eng/index.php).

I don't know if I answered your problem, if not please explain more what you need.

I definately second WinSCP. That app is *beautiful*!

gFTP works pretty well as a SFTP (SSH2 only, better than SCP or FISH) client.

---

### Post by chrisfay on 2006-08-30
> Where can you find information on how to use this? I'm assuming that this is something you'd use pagent for? Problem is the documentation for pagent sucks so if you can explain - we'd all appreciate it!

Pageant is really easy. If you already have your keys setup and can use them with Putty then 90% is already done. All you need to do is download the pageant.exe, start it and load your key into it. Instead of haveing to locate your key in putty every time, pageant stores it until you either shut down the pageant software or reboot; then you have to reload it again. 

I just keep my key on my usb keychain so when I need to ssh I just pop it into pageant, start Putty and that's it. 

Here's a description on using your SSH keys with putty in more detail:
[http://the.earth.li/~sgtatham/putty/0.53b/htmldoc/Chapter8.html](http://the.earth.li/~sgtatham/putty/0.53b/htmldoc/Chapter8.html)

If you don't have keys setup yet, your first step is to generate a private and public key pair. You can do this either from a terminal or within the PuttyGen software itself. If you do it from the terminal, you will have to take the generated private key and convert it into a compatible putty file as described in the link above if you plan on using it with Putty. If you generate the pair using the PuttyGen software, you will have to copy the contents of the public key into your /home/user/.ssh/authorized_keys file. (you could put it any file but make sure SSH is configured to use whatever file you choose)

After the keys are generated and Putty can use them to connect, you should then turnoff the password option in SSH so only your key works for authentication. 

Here's a link on generating keys using the terminal:
[http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/s1-openssh-client-config.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/s1-openssh-client-config.html)

---

