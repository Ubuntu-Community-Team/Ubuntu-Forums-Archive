---
title: "Possible security breech?"
date: 2011-05-20
forum: Security
---

### Post by airspoon on 2011-05-20
I just recently installed Ubuntu 11.04 and I'm relatively new to Linux. Anyway, this morning I ran a port scan on 'localhost' and noticed that the SMTP port was open. I then checked the /var/mail/ directory and noticed a file named 'root'. So there are two files in the /var/mail/ directory, with one being named 'mail' and the other being named 'root'.

I did just install Apache2, MySQL and PHP5 the other day, but not any kind of mail server. Is this something that is normal, or is it something that I should worry about? Is it normal for port 25 to be open by default and are both 'root' and 'mail' files in the /var/mail/ directory?

I guess I'm a little bit paranoid because last month a Windows machine on my network was found with a root kit.

Any help would be greatly appreciated. Thanks.

Other ports open are 631 (ipp), 34331, 42755, 53037 and 55536. I figure these are normal or various services.

---

### Post by spynappels on 2011-05-20
You do not need to worry. The root mail account is enabled by default as when you do certain actions a mail message is sent to the root mail account by default.

Doing an nmap on localhost is not really a good reflection of what is really happening unless you have a lot of experience interpreting results. You need to run nmap from another computer on the LAN to get an accurate picture of what your machine is doing. Some of those ports are probably only listening on the lo (loopback) interface rather than on the eth0 (LAN) interface.

Are you running a server or desktop machine?

---

### Post by Soul-Sing on 2011-05-20
like this?
> Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2011-05-09 14:39 CDT
Interesting ports on localhost (127.0.0.1):
Not shown: 1711 closed ports
PORT    STATE SERVICE
22/tcp  open  ssh
25/tcp  open  smtp
631/tcp open  ipp

---

### Post by airspoon on 2011-05-20
Thanks for the quick responses. It's nice to know that it shouldn't be a problem. I'm running the desktop version of Ubuntu, although I primarily intend to use this machine as a web server. I figured that I would use the desktop Ubuntu until I become a little more familiar with Linux.

---

### Post by The Cog on 2011-05-20
Port 25 isn't open by default. Something or someone installed a mail relay service. This command will tell you which program is running all the listening services:
```
sudo netstat -plntu
```
Services listening on the loopback addresses 127.0.0.1 or ::1 are safe because they cannot be connected to from outside the machine.

---

### Post by airspoon on 2011-05-20
Thanks. I ran 'sudo netstat -plntu' and it turned out a local address of 0.0.0.0:25 with a foreign address of 0.0.0.0:*, with the state being LISTEN. Is it safe to post the full results here?

Thanks.

---

### Post by The Cog on 2011-05-21
It's safe enough. If your public IP address is in the listing, you might want to edit that out first. If it's all 192.168 stuff then there's no point editing that out because that's not your public address anyway.

---

### Post by Rasa1111 on 2011-05-21
hey, I know an "airspoon" from ats! :lol:
weird seeing that name here... I was confused for a minute..  :)

Hopefully Bodhi Zazen pops in can let us know what is up here! (if anything)lol 

Yeah you can post the results. 
Just pull out your IP as Cog said, if you want, but not required, I see a lot of IP's posted in conkys and stuff. 

Good luck.

---

### Post by airspoon on 2011-05-21
Rasa, that's me from ATS!

--airspoon

---

### Post by airspoon on 2011-05-21
Thanks guys, here are the results from the netstat:

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      17345/mysqld    
tcp        0      0 127.0.0.1:53037         0.0.0.0:*               LISTEN      6536/ssl_esock  
tcp        0      0 127.0.0.1:55536         0.0.0.0:*               LISTEN      6254/beam.smp   
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      26762/apache2   
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1050/cupsd      
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      30866/master    
tcp6       0      0 ::1:631                 :::*                    LISTEN      1050/cupsd      
udp        0      0 0.0.0.0:68              0.0.0.0:*                           627/dhclient    
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           440/avahi-daemon: r
udp        0      0 0.0.0.0:34059           0.0.0.0:*                           440/avahi-daemon: r
udp6       0      0 :::5353                 :::*                                440/avahi-daemon: r
udp6       0      0 :::38861                :::*                                440/avahi-daemon: r

Does this mean that there is a mail relay installed and if so, how can I stop it? I see its all zeros for the ip, not the '::' or '127' before the SMTP port. Does this mean that it isn't on a loopback?

Again, thanks.

---

### Post by Rasa1111 on 2011-05-21
I personally don't see anything suspicious there, airspoon. 
and to double check my first thought when looking at it, I've compared with my own 
(which i know is not compromised)... and I don't see much difference..
(though there are many here far more versed in this area than myself)...
But Ill still share my thoughts...  whatever it's worth to ya.. lol
Anyway, Here's mine.. 


```
sudo netstat -plntu

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:48749         0.0.0.0:*               LISTEN      2106/ssl_esock  
tcp        0      0 127.0.0.1:52304         0.0.0.0:*               LISTEN      1731/beam.smp   
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      9455/sshd       
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1245/cupsd      
tcp6       0      0 :::22                   :::*                    LISTEN      9455/sshd       
tcp6       0      0 ::1:631                 :::*                    LISTEN      1245/cupsd      
udp        0      0 0.0.0.0:68              0.0.0.0:*                           28848/dhclient  
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           532/avahi-daemon: r
udp        0      0 0.0.0.0:39166           0.0.0.0:*                           532/avahi-daemon: r
udp6       0      0 :::5353                 :::*                                532/avahi-daemon: r
udp6       0      0 :::53730                :::*                                532/avahi-daemon: r


``` Nice to see you here airspoon! 
some places I am rasa, some places ahmose. :)  
(and for launchpad, both!) :lol:   lol

Good luck bro..
Hope you're liking Ubuntu so far. <3

---

### Post by Rasa1111 on 2011-05-21
Forgot..

 Even though on a default Ubuntu install..
you do not need to turn on your firewall.. I always like to anyway...
Always give me more peace of mind...
being the 'lunatic' I am..  lol

Do you have yours on? 

If not, you turn it on via the terminal,
or you can install "GUFW" from the software center/repositories. 
and that will give you a nice GUI window to turn on/off and configure your firewall easily.
Generally you should just need to click "enable" , and forget about it. 

 Firewall is built in already. 
To turn it on using terminal, just enter 
```
sudo ufw enable
```

(or install GUFW) which looks like this~ [ATTACH]192793[/ATTACH]

Just ask if you need help with anything. :)

---

### Post by airspoon on 2011-05-21
Thanks Rasa, I'll turn the firewall on now. We have had some serious security issues with at least one of the Windows (Vista) computers on our [home] network, so I was kind of halfway expecting to have my new Ubuntu instillation attacked as well.
 
I may be wrong, but I believe that I was told root kits are a result of someone actually hacking your computer, as opposed to picking it up through a virus or trojan. Of course, I could have misunderstood.
 
I know that Linux is more secure as far as virii go, but what about deliberate attacks? Is it stronger there too?
 
Anyway, thanks for the help.

---

### Post by Rasa1111 on 2011-05-21
No problem.

I have asked our resident security expert to come take a look at the thread and give his thoughts, 
He always brings the proper info to these type of threads. lol

Linux is certainly more secure against deliberate attacks, but it still basically comes down to the users own 'common sense'. Choosing good passwords, not downloading shady files,  not leaving your networks open, no 'auto login', etc. 
But yeah, its definitely more secure, in all areas really. 

 Do you have any use for the "remote desktop"?

If not, it's a good idea to disable it. 

If you do want to disable it, (assuming you're using "Unity" in 11.04)
is to open the 'Dash" [ Click ubuntu logo at top left, or press the "windows / aka "super" key on the keyboard]. Then type "startup app" , and when you see "**Startup applications**"  pop up, click on it to open it. 

Once open, scroll down the list until you see "**Remote Desktop",** and uncheck the box next to it. 

 Just to add..
I know 4 or 5 people who, before I switched them to Ubuntu..
were using Vista, and their computers were full of more viruses and key loggers and malware than ive ever seen. Absolutely insane amount of crap on these pc's. O_o

Though since theyve been using Ubuntu (many months now), 
their computers are still 'clean', (unaffected, even if they may have downloaded some bad stuff), which wouldnt be surprising knowing them. lol
and their computers are running just as quick and smooth as when i first installed it for them.
They don't even have "virus protection software", yet they had all this expensive AV software with the completely ravaged vista installs. :P

It's normal to worry about this stuff when just coming from windows..
but you'll see... 
it's amazing! lol

Good luck, have fun!

---

### Post by Irihapeti on 2011-05-22
If you've installed rkhunter, you will have installed a mailserver as one of the dependencies. I think that some other security tools do the same thing, the idea being, I assume, to email the sysadmin if anything nasty is found.

It's been a while since I ran rkhunter, but I seem to recall that I could disable the mail server in startup applications. Even if I didn't, running nmap from another computer on the LAN showed port 25 as closed.

---

### Post by bobbrock on 2011-05-22
Im glad to hear ubuntu is safer than windows .

---

### Post by crispy_420 on 2011-05-25
Who is your ISP? Comcast for example kills port 25 traffic for obvious reasons of malware spreading and spamming.

Or maybe you have a false positive?

---

### Post by airspoon on 2011-05-25
Crispy, I have Cox Comm for an ISP. As far as a false positive, can that really happen? Would it continue to make the same 'mistake' by showing up in every scan that I do?

---

### Post by crispy_420 on 2011-05-27
I think Cox has that port blocked so nothing could get out because it is essentially dead.

Did not catch this but did you scan from another box? Self scans and not always the best info. That is why I stated the possibility of a false positive.

Once you get another box you can perform another more comprehensive system scan looking for other issues.

---

### Post by airspoon on 2011-05-29
Thanks for the help, everyone. Just this morning, I ran a scan (nmap) from a different computer on the same network. The scan is showing 25/tcp open and nmap is saying that it is Postfix smtpd.

Postfix isn't installed on Ubuntu 11.04 Desktop by default, right? If not, then someone had to install it, right? Again, thanks for the help and I look forward to a response.


--airspoon

---

### Post by Irihapeti on 2011-05-29
Postfix isn't part of a default Ubuntu installation, but it can be installed as a dependency of another package.

You could do this:
Open synaptic package manager. Select postfix. Click on properties and then select the dependencies tab. Then choose dependent packages from the drop-down list at the top. It will show a long list of packages.

If any of those are something you have installed, then there's your answer. My guess is that it has to do with the server software you mentioned in your original post.

As I've mentioned previously, quite a few packages have a mailserver as a dependency, presumably because they were put together with server admins in mind.

---

### Post by airspoon on 2011-05-29
Thank you for the help. I followed your instructions and I can't see anything in Synaptic that connects Postfix to anything I have installed, unless of course I just can't recognize anything.

Out of curiosity, I used telnet to connect to my Ubuntu computer on port 25. I did the "HELO", "MAIL FROM:" and "RCPT TO" to compose a message in an effort to see if anyone could do the same. I used my hotmail email for both the "from" and "to" and when I got to the "to", it kicked back a message saying "Relay access denied." I then used "username@localhost" for the "to" and it went through.

Does this mean that Postfix is solely set up for mail on localhost and that my computer can't be used for spam? 

Just the fact that Postfix was on there is freaking me out a little, especially because I don't recognize any dependent packages in Synaptic, nor did I think that the *AMP software would install a mail server. Would it be okay to remove Postfix, or does it seem okay since it appears (at least to me) that relay access is denied?

Again, thanks.

---

### Post by Irihapeti on 2011-05-29
Another trick would be to attempt to remove postfix. If it's been installed as a dependency, you'll be warned about other packages that will be removed. Of course, you can cancel at that point.

There are history files in /var/log/apt which might be worth browsing through. There is also a history (might be the same stuff) accessible from synaptic - see "History" under the file menu.

---

### Post by Irihapeti on 2011-05-29
If postfix is a dependency of a needed application, you can just disable postfix in startup applications by unticking it. I once used a program that had exim4 (another mail server) as a dependency and I did that. It caused no problems.

---

### Post by airspoon on 2011-05-29
Thank you very much. I going to try and uninstall it first, then disable it if otherwise (great advice!). Again, thanks.


--airspoon

---

