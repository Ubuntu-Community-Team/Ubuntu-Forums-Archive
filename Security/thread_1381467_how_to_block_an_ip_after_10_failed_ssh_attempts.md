---
title: "how to block an ip after 10 failed ssh attempts?"
date: 2010-01-14
forum: Security
---

### Post by markp1989 on 2010-01-14
just looking in my logs of my 2 day old ubuntu server install 


i have had alot of failed log in attempts, 1 ip has failed over 1000 times.

```
mark@torrentslave:~$ cat /var/log/auth.log | grep failed | wc -l
13313

```

i have heard of ip tables, how do i make it block brute force attacks.


and is there any way to see if they successfuly got in?

thanks Markp1989

---

### Post by d3v1150m471c on 2010-01-14
[http://ubuntuforums.org/showthread.php?t=1375324](http://ubuntuforums.org/showthread.php?t=1375324)

Firestarter is your friend. It's not a firewall but it configures iptables (firewall) with an easy to use graphical user interface.

---

### Post by d3v1150m471c on 2010-01-14
I also recommend PSAD, and it will inform you in the event anyone tries to compromise your system. 

[http://www.linuxsecurity.com/content/view/134248/171/](http://www.linuxsecurity.com/content/view/134248/171/)
[http://www.cyberciti.biz/faq/linux-detect-port-scan-attacks/](http://www.cyberciti.biz/faq/linux-detect-port-scan-attacks/)

you can use those two links to help set it up. You can get them both with synaptic or apt-get

---

### Post by FuturePilot on 2010-01-14
Fail2ban or denyhosts will do what you want.

---

### Post by markp1989 on 2010-01-14
thanks for all the fast replies 
im having problems with psad starting , i have set the email address to my google mail account

mark@torrentslave:~$ sudo /etc/init.d/psad start
Starting Port Scan Attack Detector: psad [*] Could not find mail, edit /etc/psad/psad.conf at /usr/sbin/psad line 9566.
 * Unable to start the daemon.
mark@torrentslave:~$ 

thanks mark

---

### Post by d3v1150m471c on 2010-01-14
sudo gedit /etc/psad/psad.conf

go in and change the email address to your email. It should say something like:

EMAILADDRESS                           home@localhost;

Change it to:

EMAILADDRESS                           youremail@emailserver;

Save it. IE mine looks something like this:

EMAILADDRESS                           [email]d3v1150m471c@blah.com[/email];

---

### Post by d3v1150m471c on 2010-01-14
If you still can't get it working there is another similar program called "snort". I have no experience with it but it supposedly does the same thing. If you open firestarter and click on the events tab (you may have to click the reload button) it will tell you the ip's it blocked and it will also say adjacent to it what it was blocking. Like subseven, doomjuice, tcp, udp, ect. I just like psad because it's a little more intuitive and detailed.

---

### Post by markp1989 on 2010-01-14
> **d3v1150m471c said:**
> sudo gedit /etc/psad/psad.conf

go in and change the email address to your email. It should say something like:

EMAILADDRESS                           home@localhost;

Change it to:

EMAILADDRESS                           youremail@emailserver;

Save it. IE mine looks something like this:

EMAILADDRESS                           [email]d3v1150m471c@blah.com[/email];

i have set it to send to my [email]blah@googlemail.com[/email] address. but it hasnt 


i thought it wanted me to edit /usr/sbin/psad line 9566. but i havnt changedit beccause i know im not sposed to .

---

### Post by d3v1150m471c on 2010-01-14
From what the blogs were telling me on psad i had to change it with gedit, or vi, whichever you use, and mine works just fine. It doesn't need an email to run as far as i know and you can check its logs by typing:

sudo psad -S

Hell, you might want to avoid the whole email thing anyways and just use the terminal to check it because it can send a buttload of emails to you depending on how many idiots like to invade your computer. I run them both because firestarter is a wicked port stealther and firewall configurer.

---

### Post by absolutezero1287 on 2010-01-14
On a related note, you can always report the IP to the user's ISP. ISPs take matters like this really seriously.

---

### Post by markp1989 on 2010-01-14
> **absolutezero1287 said:**
> On a related note, you can always report the IP to the user's ISP. ISPs take matters like this really seriously.


i did whois on a a couple of the ip addresses , who ever it was is from  china i dont know what there laws a like for this kin of thinkg .

---

### Post by absolutezero1287 on 2010-01-14
> **markp1989 said:**
> i did whois on a a couple of the ip addresses , who ever it was is from  china i dont know what there laws a like for this kin of thinkg .

They'd probably get shot or something crazy. Its odd. China seems to be full of script kiddies.

You might be able to write a shell script that monitors incoming connections and automatically blacklists someone when they fail to authenticate properly. Unfortunately I don't know enough about IPtables to add any useful logic to the loop but the basic idea is to have a bash script parse iptables and add an entry that blocks the IP. If anyone that has more expertise would like to add their 2 cents that'd be great.

Something like this...
```

#!/usr/bin/env bash
NUM = "5"
#
if [$Log_Attempts > $NUM]
  then #ADD ACTION HERE
fi

```

---

### Post by nerdy_kid on 2010-01-15
> **absolutezero1287 said:**
> On a related note, you can always report the IP to the user's ISP. ISPs take matters like this really seriously.

sorry to sound like an idiot, but how do i do this?
i have this:
```
41.223.30.22 - - [14/Jan/2010:04:17:48 -0500] "GET HTTP/1.1 HTTP/1.1" 400 243 "-" "Toata dragostea mea pentru diavola"
```
a bunch of times in my apache logs and would like to get the jerk in trouble.

[http://www.whatismyip.com/tools/ip-address-lookup.asp](http://www.whatismyip.com/tools/ip-address-lookup.asp) says that the ISP is AFRINIC and the domain is CREOLINK.COM.  I kinda dont know what to do with that info....how do i report an IP?

---

### Post by cariboo on 2010-01-15
> **nerdy_kid said:**
> sorry to sound like an idiot, but how do i do this?
i have this:
```
41.223.30.22 - - [14/Jan/2010:04:17:48 -0500] "GET HTTP/1.1 HTTP/1.1" 400 243 "-" "Toata dragostea mea pentru diavola"
```
a bunch of times in my apache logs and would like to get the jerk in trouble.

[http://www.whatismyip.com/tools/ip-address-lookup.asp](http://www.whatismyip.com/tools/ip-address-lookup.asp) says that the ISP is AFRINIC and the domain is CREOLINK.COM.  I kinda dont know what to do with that info....how do i report an IP?

If you use whois, in a terminal, it will usually show a couple of email contacts. You can try emailing them, but I've never had any success, and I've finally just given up. As far as I'm concerned, the bad guys can bang on my firewall all day long, it doesn't affect me in any way.

---

### Post by dnvikram on 2010-01-15
> **FuturePilot said:**
> Fail2ban or denyhosts will do what you want.

I couldnt agree more!Denyhosts is a wonderful utility and it does the job perfectly.I have been using this since a long time and it never let me down.Configured it to block any IP from which any person tries to login with a valid/invalid/root user and enters the password wrong >2 times.So,at the 3rd attempt denyhosts basically refuses the connection and adds the ip to the /etc/hosts.deny file.

Denyhosts + Iptables + strong secure router firewall - unwanted services + strong passwords + SSH Allow Users list.

---

### Post by d3v1150m471c on 2010-01-15
psad logs all this stuff.

sudo psad -S

copy and paste or take a screenshot. report it.

---

### Post by markp1989 on 2010-01-15
> **d3v1150m471c said:**
> psad logs all this stuff.

sudo psad -S

copy and paste or take a screenshot. report it.

I have got deny hosts working, i tried loging in with the wrong password and it successfully blocked me.  i dont know how to get it to email using my googlemail account thou.

I dont have the gui installed on my server, im doin everything over ssh, so i done copy and paste rather then scrot.

```
mark@torrentslave:~$ 
sudo psad -S
[*] Could not find mail, edit /etc/psad/psad.conf at /usr/sbin/psad line 9566.
mark@torrentslave:~$ 

```

---

### Post by markp1989 on 2010-01-15
one more question, is there any way to tell if they did get in?

---

### Post by dnvikram on 2010-01-15
> **markp1989 said:**
> one more question, is there any way to tell if they did get in?

This is how my setup is.As mentioned before,I configured my denyhosts to block any IP (user who enters more than twice wrong password) from even initiating connection to my server.And in parallel,I have logwatch(with a bit higher logging level,default should also be good.But I am a little bit paranoid.So increased it) running as a service in the background.

Logwatch basically,will create a report in a nice format which will display all the details of the users who logged in,authentication failures,IPs which were blocked allowed,the login method(ssh/telnet),list of PIDs which made some suspicious modifications to the files,etc.Then I configured the server to send me those reports twice a week.

I have also configured AIDE to safeguard the integrity of the installed files on the system.It creates a fingerprint of it,which you store somewhere safe and once a while either manually/via cron I run a quick compare to see what files were changed by whom and when.

There is no one single utility to do everything.You have to use a collection of small utilities like this along with your own scripts(if any) to keep a server secure.

Bodhi Zazen has a nice sticky to get you started which discusses all this.

Hope this helped.If it did,please feel free to rate the answer.

Have a nice day! 

Cheers!!! Happy Ubuntuing!!!

---

### Post by spynappels on 2010-01-15
> **markp1989 said:**
> one more question, is there any way to tell if they did get in?

This depends on a number of things. you could look at the auth logs in /var/log/auth.log and grep for sshd and Accepted, this should get you a list of successful logins through SSH. If you do not recognise a login attempt or the IP it came from, someone likely got in.

Very clumsy hackers who get in may delete all logs, this is a certain giveaway that someone has been in and up to no good.

---

### Post by spynappels on 2010-01-15
OK ndvikram got there before me and put it much better!
I must have a look at logwatch myself, thanks.

---

### Post by FuturePilot on 2010-01-15
> **dnvikram said:**
> This is how my setup is.As mentioned before,I configured my denyhosts to block any IP (user who enters more than twice wrong password) from even initiating connection to my server

Actually denyhosts uses the tcpwrapper (hosts.deny, hosts.allow) which means that a connection is actually established. Then it checks hosts.deny and finds a match and closes the connection. Fail2ban uses iptables instead which will actually prevent a connection from even being established.

---

### Post by dnvikram on 2010-01-15
> **FuturePilot said:**
> Actually denyhosts uses the tcpwrapper (hosts.deny, hosts.allow) which means that a connection is actually established. Then it checks hosts.deny and finds a match and closes the connection. Fail2ban uses iptables instead which will actually prevent a connection from even being established.

Thanks for the correction.My bad!You are right.It will basically let the person initiate a connection,but then will go ahead and reject/refuse it.

---

### Post by nerdy_kid on 2010-01-16
> **cariboo907 said:**
> If you use whois, in a terminal, it will usually show a couple of email contacts. You can try emailing them, but I've never had any success, and I've finally just given up. As far as I'm concerned, the bad guys can bang on my firewall all day long, it doesn't affect me in any way.

thanks :D

---

### Post by markp1989 on 2010-01-16
i got psad running now, i changed to server kernel, rather then the generic one ( i dont remember why i had the generic server on my server ) and it started fine.

is there a way to test psad to see if it successfuly emails me?

thanks Markp1989

---

### Post by MarkC502 on 2010-01-16
From this IP you can see that this scumbag is in[FONT=monospace] [/FONT]Yaounde[FONT=Verdana], [/FONT]Camaroon ( how nice ). As previously mentioned his ISP is Creolink Communications, you can reach them via Email at this address [EMAIL="support@creolink.com"]support@creolink.com[/EMAIL]
I would Email them with the offending IP and a rundown of how many attempts they are making at bruteforcing your system and how you do not appreciate this, they may do something they may not.

Also relax as long as you have a strong password set for SSH you should be fine as a script kiddie can bruteforce all day and just waste his time.

---

### Post by markp1989 on 2010-01-17
i have set up ssh to use public keys with a strong password, and i have disabled password login. should help me sleep easier at night now :)

---

### Post by Lars Noodén on 2010-01-18
> **cariboo907 said:**
> If you use whois, in a terminal, it will usually show a couple of email contacts. You can try emailing them, but I've never had any success, and I've finally just given up. As far as I'm concerned, the bad guys can bang on my firewall all day long, it doesn't affect me in any way.

Your network administrator is supposed to do that for you, or at least help.  That would be your ISP if at home.  The e-mail addresses are less likely to be of use than the phone numbers.  But if they are out of your country then it may be an issue for some business associations or even the consulate.  

A coordinated clean up effort could save the various countries a lot of money.

---

### Post by bodhi.zazen on 2010-01-18
Personally I suggest you use either denyhosts or fail2ban.

I used these services until I learned iptables, and now I just have a few rules for iptables, limiting rates and numbers of log in attempts.

Note: With the majority of these programs and "attempt" is a series of 3 guesses at a password, do banning after 3 attempts = 9 opportunities to guess a password.

Also, if you use scp, you may need to allow more then 3 new connections.

---

### Post by Lars Noodén on 2010-01-18
> **bodhi.zazen said:**
> Personally I suggest you use either denyhosts or fail2ban.

I used these services until I learned iptables, and now I just have a few rules for iptables, limiting rates and numbers of log in attempts.

Note: With the majority of these programs and "attempt" is a series of 3 guesses at a password, do banning after 3 attempts = 9 opportunities to guess a password.

Also, if you use scp, you may need to allow more then 3 new connections.

@  bodhi.zazen   :

There are some nice tricks with advanced rulesets for IP Tables to limit the clumsy attacks.  Here are two interesting examples using **recent**:

[http://la-samhna.de/library/brutessh.html#3](http://la-samhna.de/library/brutessh.html#3)

[http://www.e18.physik.tu-muenchen.de/~tnagel/ipt_recent/](http://www.e18.physik.tu-muenchen.de/~tnagel/ipt_recent/)

Unfortunately we're seeing botnets trying once or twice each in what Peter Hansteen decided to compare the attack to a Hail Mary Pass (is that the same as an Alley Oop?) and slow brute forces:
[http://bsdly.blogspot.com/2009/11/rickrolled-get-ready-for-hail-mary.html](http://bsdly.blogspot.com/2009/11/rickrolled-get-ready-for-hail-mary.html)

If you are using scp or, better yet sftp, then there is no need to adjust the rate limiting that much.  I suppose the IP Table rules could be set to exempt machines that have successfully connected, but it's also possible to multiplex sessions so that multiple SSH/SFTP sessions are run over a single TCP/IP connection.  It's not hard, just a bit foreign at first because most are not used to changing the default ssh client options either as runtime arguments or in ssh_config.   

Here is an example that automatically tries to multiplex sessions if ssh connects using the shortcut host 'Version' 

```

# from ssh_config
Host Version
  HostName 192.168.0.122
  ControlPath ~/.ssh/controlmasters/%r@%h:%p
  ControlMaster autoask

```

YMMV

---

### Post by bodhi.zazen on 2010-01-18
> **Lars Noodén said:**
> @  bodhi.zazen   :

There are some nice tricks with advanced rulesets for IP Tables to limit the clumsy attacks.  Here are two interesting examples using **recent**:

[http://la-samhna.de/library/brutessh.html#3](http://la-samhna.de/library/brutessh.html#3)

[http://www.e18.physik.tu-muenchen.de/~tnagel/ipt_recent/](http://www.e18.physik.tu-muenchen.de/~tnagel/ipt_recent/)

Unfortunately we're seeing botnets trying once or twice each in what Peter Hansteen decided to compare the attack to a Hail Mary Pass (is that the same as an Alley Oop?) and slow brute forces:
[http://bsdly.blogspot.com/2009/11/rickrolled-get-ready-for-hail-mary.html](http://bsdly.blogspot.com/2009/11/rickrolled-get-ready-for-hail-mary.html)

If you are using scp or, better yet sftp, then there is no need to adjust the rate limiting that much.  I suppose the IP Table rules could be set to exempt machines that have successfully connected, but it's also possible to multiplex sessions so that multiple SSH/SFTP sessions are run over a single TCP/IP connection.  It's not hard, just a bit foreign at first because most are not used to changing the default ssh client options either as runtime arguments or in ssh_config.   

Here is an example that automatically tries to multiplex sessions if ssh connects using the shortcut host 'Version' 

```

# from ssh_config
Host Version
  HostName 192.168.0.122
  ControlPath ~/.ssh/controlmasters/%r@%h:%p
  ControlMaster autoask

```

YMMV

I agree with everything you are saying, but the old adage applies, security is built in layers.

iptables is but one layer , denyhosts would be another (as it uses tcpwrappers).

Basically these will eliminate the casual script kiddy , and there are tons of those.

The distributed attacks and botnets, and they can certainly can and do bring down servers.

In terms of ssh , I use keys and disable password logins, I know yet another layer, but this second layer is very successful against the bot nets.

If you are against a skilled and determined opponent you will need additional tools.

---

