---
title: "Comprimised maybe??"
date: 2011-05-07
forum: Security
---

### Post by AIG_234 on 2011-05-07
To: The Cog >>>

```

The Cog, heres the reszults for ps -ef | grep tty: 
yo mama@blah:~$ ps -ef | grep tty
root      1447     1  0 01:14 tty4     00:00:00 /bin/login -f       
root      1452     1  0 01:14 tty5     00:00:00 /bin/login -f       
root      1472     1  0 01:15 tty2     00:00:00 /bin/login -f       
root      1473     1  0 01:15 tty3     00:00:00 /bin/login -f       
root      1475     1  0 01:15 tty6     00:00:00 /bin/login -f       
ubuntu    2029  1473  0 01:15 tty3     00:00:00 -bash
ubuntu    2030  1447  0 01:15 tty4     00:00:00 -bash
ubuntu    2031  1452  0 01:15 tty5     00:00:00 -bash
ubuntu    2034  1472  0 01:15 tty2     00:00:00 -bash
ubuntu    2035  1475  0 01:15 tty6     00:00:00 -bash
root      2154     1  0 01:15 tty1     00:00:00 /bin/login -f       
ubuntu    2253  2154  0 01:15 tty1     00:00:00 -bash
root      3867  3864  2 01:49 tty7     00:00:04 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-vLKfVE/database -nolisten tcp vt7
ubuntu    4446  4107  0 01:52 pts/0    00:00:00 grep --color=auto tty

Also The Cog, i ran sudo netstat -plntu, i got this:
root@ubuntu:/home/ubuntu# sudo netstat -plntu
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           1301/avahi-daemon: 
udp        0      0 0.0.0.0:41242           0.0.0.0:*                           1301/avahi-daemon: 
udp        0      0 0.0.0.0:68              0.0.0.0:*                           4509/dhclient   
udp6       0      0 :::5353                 :::*                                1301/avahi-daemon: 
udp6       0      0 :::56270                :::*                                1301/avahi-daemon: 

********If you look at the UDP6 protocol  I am a little weary about that high local port address. 56270....

```i have been using ubuntu for years, 5 or more. And i have never had these issues before.

To: matt_symes >>>
```

@m[att_symes]("http://ubuntuforums.org/member.php?u=1067998"), i do not know if there are scripts running on the processes or not. How do i check??

```

---

### Post by doas777 on 2011-05-07
when in doubt, rebuild, and be very careful what you restore. as you reconfigure, be sure to question everything you did last time, and determine whether its really agood idea.

---

### Post by matt_symes on 2011-05-07
Hi

> **AIG_234 said:**
> So I think my system might be comprimised. It's acting all funny. First off I have 6 uninteruptable bash processes using tty1-6. I kill the processes and they just respawn.


This is not a problem. They are your consoles. To see them press ctrl + atl + f1 to f6. Press ctrl + alt + f7 to get back to X.

> 
I had a script called mozilla.sh running. And yesterday I was trying to use my terminal and was having problems. Like I tried apt-get install some programs and it would give an error and my terminal would say core dump and crash. I couldnt use it all night because of this.


What was the script and what was it meant to do ? What was the apt-get error ? Need more specifics here.

>  I have weird certificates in some foriegn german languages. And when i was trying to login into yahoo it site site was untrusted cannot verify CA. Come to find out firefox wasnt the broswer i was using. Once I switched over to firefox i stopped getting the yahoo warnings. 


What browser were you using before Firefox ?

> 
I dont want to seem paranoid but i was chatting with someone from a hacking site and he had me email him. i did and he never responded back. But it makes me cautious because of those pen testing cd's out. Blackbuntu and backtrack. Does any of this sound suspicious or am i being paranoid?

Are you behind a router firewall ? What ports do you have open ?

Are you being paranoid ? Maybe.

Kind regards

---

### Post by Irihapeti on 2011-05-08
The "other browser" probably doesn't have the specific security certificates installed that Yahoo needs, and Firefox does. Doesn't sound very suspicious to me.

I think that the certificates in all sorts of different languages are also standard. I've seen them in all the installations I've done.

---

### Post by AIG_234 on 2011-05-11
So I netstat -ant on my terminal and i have ports 80 and 443 used by foriegn addresses. Normal right? well i grep 80 /etc/services and came up with a canna server, a transparent proxy, zope ftp server, omniorb, socks proxy server, omirr, http-alt, and amanda. I would look further into it but my computer says it cannot locate nmap package for install. To my knowledge cannaserver is used for japenese key config. Why do I need that? And whats up with the transparent proxy?? Im sure that doesnt come standard on install. Is there a way to get rid of all this crap? Also my universe repository is missing and I cannot install many packages because of this. So how do I clean up all of this with my system all wacky? 

@matt_symes, i pressed the keys you told me to press and it froze my system. Not behind a firewall either. But I cannot find specifics because nmap wont install. But I do see all of these servers and crazy services running. theyre open on high ports on my comp. Ports in the 4 thousands and 5 thousands. above 1024.

---

### Post by matt_symes on 2011-05-11
Hi

> **AIG_234 said:**
> So I netstat -ant on my terminal and i have ports 80 and 443 used by foriegn addresses. Normal right? well i grep 80 /etc/services and came up with a canna server, a transparent proxy, zope ftp server, omniorb, socks proxy server, omirr, http-alt, and amanda. I would look further into it but my computer says it cannot locate nmap package for install. To my knowledge cannaserver is used for japenese key config. Why do I need that? And whats up with the transparent proxy?? Im sure that doesnt come standard on install. Is there a way to get rid of all this crap? Also my universe repository is missing and I cannot install many packages because of this. So how do I clean up all of this with my system all wacky? 

The /etc/services allows Linux to convert service names to port numbers. It is not necessarily the service currently running on that port.

To install nmap make sure you have all the repositories enabled as it is in one of the standard repositories. (quite possibly universe).

What transparent proxy ?

If you need help with your repositories then please post the output of

```
cat /etc/apt/sources.list
```> 
@matt_symes, i pressed the keys you told me to press and it froze my system.For a small tutorial about your virtual terminals

[http://lgjsheron.wordpress.com/2010/03/16/virtual-console-terminals-in-ubuntu/](http://lgjsheron.wordpress.com/2010/03/16/virtual-console-terminals-in-ubuntu/)

It should not have froze your system. Did it just freeze X ?

> 
Not behind a firewall either..Get yourself behind a firewall if you have a direct connection to the  internet. Read up on netfilter, iptables and use a GUI like gufw.

>  But I cannot find specifics because nmap  wont install. But I do see all of these servers and crazy services  running. theyre open on high ports on my comp. Ports in the 4 thousands  and 5 thousands. above 1024.If the local and foreign addresses are your loopback addresses (127.0.0.1) then this is not a problem. It is one of the ways the operating system and applications can talk to each other. On my machine
> 
<snip>
tcp        1      0 127.0.0.1:46582         127.0.0.1:55728         CLOSE_WAIT 
tcp        1      0 127.0.0.1:50822         127.0.0.1:55728         CLOSE_WAIT 
tcp        0      0 127.0.0.1:9050          127.0.0.1:34734         ESTABLISHED
<snip>The tools you are using are very powerful but you have to know how to read and understand them.

Kind regards

---

### Post by The Cog on 2011-05-12
> **AIG_234 said:**
> So I netstat -ant on my terminal and i have ports 80 and 443 used by foriegn addresses. Normal right?That lists all the inter-process communication that is going on inside your box too. Lots of stuff that is of no interest. More useful is just to list the listening tcp/udp ports like this:
```
sudo netstat -plntu
```

>  well i grep 80 /etc/services and came up with a canna server, a transparent proxy, zope ftp server, omniorb, socks proxy server, omirr, http-alt, and amanda. 
That is be cause "grep 80" looks for lines containing "80" and will also match strings like 1080, 8021, pQz803TF etc. 
Either of these two would do better in this case:
```
grep [^0-9]80[^0-9] /etc/services
grep ' 80/' /etc/services
```


You say there are bash processes running on your tty terminals. That's not normal - unless someone is logged in on the tty terminals. Can you say why you think there are bash processes on them, or post the output of the command
```
ps -ef | grep tty
```

---

### Post by matt_symes on 2011-05-13
Hi

> You say there are bash processes running on your tty terminals. That's  not normal - unless someone is logged in on the tty terminals.This is an interesting point actually and maybe i misunderstood you.

Do you have 6 tty consoles running bash as a shell or do you have scripts running on the tty consoles that you cannot kill.

If you try to kill the tty consoles themselves they will respawn. This is their behaviour.

If you have scripts running that you cannot kill on those ttys then that is a potential issue.

I just have normal tty consoles running. Take a look at this.

```
matthew@matthew-laptop:~$ ps aux | grep tty
root      1238  4.5  8.5 356308 242904 tty7    Ss+  11:21  16:25 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-cuhgpw/database -nolisten tcp vt7
root      1249  0.0  0.0   6080   620 tty4     Ss+  11:21   0:00 /sbin/getty -8 38400 tty4
root      1254  0.0  0.0   6080   620 tty5     Ss+  11:21   0:00 /sbin/getty -8 38400 tty5
root      1266  0.0  0.0   6080   620 tty2     Ss+  11:21   0:00 /sbin/getty -8 38400 tty2
root      1267  0.0  0.0   6080   620 tty3     Ss+  11:21   0:00 /sbin/getty -8 38400 tty3
root      1271  0.0  0.0   6080   616 tty6     Ss+  11:21   0:00 /sbin/getty -8 38400 tty6
root      1499  0.0  0.0   6080   616 tty1     Ss+  11:21   0:00 /sbin/getty -8 38400 tty1
matthew   4546  0.0  0.0   7632   976 pts/3    S+   17:19   0:00 grep --color=auto tty
matthew@matthew-laptop:~$ sudo kill -TERM 1249
[sudo] password for matthew: 
matthew@matthew-laptop:~$ ps aux | grep tty
root      1238  4.5  8.5 356308 242904 tty7    Ss+  11:21  16:26 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-cuhgpw/database -nolisten tcp vt7
root      1254  0.0  0.0   6080   620 tty5     Ss+  11:21   0:00 /sbin/getty -8 38400 tty5
root      1266  0.0  0.0   6080   620 tty2     Ss+  11:21   0:00 /sbin/getty -8 38400 tty2
root      1267  0.0  0.0   6080   620 tty3     Ss+  11:21   0:00 /sbin/getty -8 38400 tty3
root      1271  0.0  0.0   6080   616 tty6     Ss+  11:21   0:00 /sbin/getty -8 38400 tty6
root      1499  0.0  0.0   6080   616 tty1     Ss+  11:21   0:00 /sbin/getty -8 38400 tty1
root      4549  0.1  0.0   6080   628 tty4     Ss+  17:20   0:00 /sbin/getty -8 38400 tty4
matthew   4552  0.0  0.0   7632   976 pts/3    S+   17:20   0:00 grep --color=auto tty
matthew@matthew-laptop:~$ 
```tty4 that i killed is respawned with new process ID of 4522.

Kind regards

---

### Post by AIG_234 on 2011-06-02
After just forgetting about the issue for awhile, I was sitting in bed reading and I heard my computer working. It was clicking and humming like the old computers do when they are in use or the hard drive is in use. I check it out and see the crash notifier in the top right. The little pointed bubble thing with the exclamation point in it. And I pulled up the system monitor, as I suspected.... an sh process was running. The standard shell process is bash and if you are spawning a shell when smashing the stack it spawns an sh process not bash. And I ran an ifconfig command in my terminal and my static up has changed. And my windows manager crashed. So I could not exit out of anything. I have to go to file and then quit. There is no x or minimize for anything. And I cannot hit the desktop icon. The one that closes out all windows and brings me to the desktop.

To: The Cog >>>

```

The Cog, heres the reszults for ps -ef | grep tty: 
yo mama@blah:~$ ps -ef | grep tty
root      1447     1  0 01:14 tty4     00:00:00 /bin/login -f       
root      1452     1  0 01:14 tty5     00:00:00 /bin/login -f       
root      1472     1  0 01:15 tty2     00:00:00 /bin/login -f       
root      1473     1  0 01:15 tty3     00:00:00 /bin/login -f       
root      1475     1  0 01:15 tty6     00:00:00 /bin/login -f       
ubuntu    2029  1473  0 01:15 tty3     00:00:00 -bash
ubuntu    2030  1447  0 01:15 tty4     00:00:00 -bash
ubuntu    2031  1452  0 01:15 tty5     00:00:00 -bash
ubuntu    2034  1472  0 01:15 tty2     00:00:00 -bash
ubuntu    2035  1475  0 01:15 tty6     00:00:00 -bash
root      2154     1  0 01:15 tty1     00:00:00 /bin/login -f       
ubuntu    2253  2154  0 01:15 tty1     00:00:00 -bash
root      3867  3864  2 01:49 tty7     00:00:04 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-vLKfVE/database -nolisten tcp vt7
ubuntu    4446  4107  0 01:52 pts/0    00:00:00 grep --color=auto tty

Also The Cog, i ran sudo netstat -plntu, i got this:
root@ubuntu:/home/ubuntu# sudo netstat -plntu
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           1301/avahi-daemon: 
udp        0      0 0.0.0.0:41242           0.0.0.0:*                           1301/avahi-daemon: 
udp        0      0 0.0.0.0:68              0.0.0.0:*                           4509/dhclient   
udp6       0      0 :::5353                 :::*                                1301/avahi-daemon: 
udp6       0      0 :::56270                :::*                                1301/avahi-daemon: 

********If you look at the UDP6 protocol  I am a little weary about that high local port address. 56270....

```i have been using Linux for years, 5 or more. And i have never had these issues before.

To: matt_symes >>>
```

@m[att_symes]("http://ubuntuforums.org/member.php?u=1067998"), i do not know if there are scripts running on the processes or not. How do i check??

```

And I accidently replaced the original post, sorry.

---

### Post by The Cog on 2011-06-03
I don't think avahi is a problem: see below - I have a similar thing.

What I don't understand is the bash processes on the tty ports. In a normal install, they are running /bin/getty - see below from my machine. I looked up **man logi**n and it it says for the -f option:
> Do not perform authentication, user is preauthenticated. and it notes that a username following the -f is mandatory, but I don't see on one in your case. As an experiment, I logged in on tty3 before running the following commands, so you can see what a normal user logged in on a tty looks like. 

```
steve@StevesPC:~$ sudo netstat -plntu
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      811/sshd        
tcp        0      0 0.0.0.0:631             0.0.0.0:*               LISTEN      858/cupsd       
tcp6       0      0 :::22                   :::*                    LISTEN      811/sshd        
tcp6       0      0 :::631                  :::*                    LISTEN      858/cupsd       
udp        0      0 0.0.0.0:58917           0.0.0.0:*                           864/avahi-daemon: r
udp        0      0 0.0.0.0:68              0.0.0.0:*                           994/dhclient    
udp    66752      0 0.0.0.0:631             0.0.0.0:*                           858/cupsd       
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           864/avahi-daemon: r
udp6       0      0 :::5353                 :::*                                864/avahi-daemon: r
udp6       0      0 :::51479                :::*                                864/avahi-daemon: r
steve@StevesPC:~$ ps -ef | grep tty
root       982     1  0 18:57 tty4     00:00:00 /sbin/getty -8 38400 tty4
root       986     1  0 18:57 tty5     00:00:00 /sbin/getty -8 38400 tty5
root      1004   979  2 18:57 tty7     00:02:00 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-SETTp1/database -nolisten tcp vt7
root      1017     1  0 18:57 tty2     00:00:00 /sbin/getty -8 38400 tty2
root      1018     1  0 18:57 tty3     00:00:00 /bin/login --      
root      1020     1  0 18:57 tty6     00:00:00 /sbin/getty -8 38400 tty6
root      1340     1  0 18:58 tty1     00:00:00 /sbin/getty -8 38400 tty1
steve     3225  1018  3 20:37 tty3     00:00:00 -bash
steve     3276  3111  0 20:38 pts/0    00:00:00 grep tty

```

It would be interesting to use the command **w** to see who is logged in and what they're doing.

I really don't understand what's happening on your system, but I'm not actually convinced it's been compromised. The disk activity might have been the daily update of the file index (used by the locate command to find files quickly). If it were me, I would probably reinstall and look again at what a fresh install looks like, and see if/when things change again.

---

### Post by AIG_234 on 2011-06-03
The Cogs, I run a live cd. It crashes 2 and 3 times a day. So I am constantly redoing it. This problem occurs everyrtime. I go into update setting in preferences >admin and make it so there are no updates without me doing so. I tried installing onto my hard drive but it says the bootstrap is messed up on the cd. Idk then, its been acting all funky man fvck it.

---

