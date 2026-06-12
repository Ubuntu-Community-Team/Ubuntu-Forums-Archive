---
title: "Firestarter configuration"
date: 2006-07-18
forum: Server Platforms
---

### Post by airjunman on 2006-07-18
I just installed firestarter on my Dapper Drake. 

Now firestarter is supposed to be just a front-end to iptables, but when i go to the rules, there aren't any. So i go try "iptables -L", but none of the chains contain any rules.

I know that the system is decently secure, at least in the sense of open ports, since I'd tested it at one of those sites that check for open ports, and it seemed to pass all that. Now if the system has most of its ports in stealth mode who does it if its not firestarter?

And  is the firewall tghe outermost layer of security or is the tcp wrappers? n how do tcp wrappers come into play when an inbound connection is attempted?

Any document that makes these clearer are more than welcome.

---

### Post by wieman01 on 2006-07-19
According to what I've experienced Firestarter is more than "just a GUI". I am saying this because Firestarter is loaded during the boot process and simple GUIs aren't - unless they do more than just acting as a facilitator.

My conclusion is that Firestarter actually controls IP Tables and brings them up during startup. As along as Firestarter runs as a daemon your firewall should be up & running as well (that's what you've just figured out yourself). If you shut down Firestarter, your firewall will  be gone.

Sadly I cannot dig out any kind of documentation confirming this.

---

### Post by airjunman on 2006-07-19
I didn't mean firestarter was just a GUI. Its a firewall that does its work by controlling the iptables based firewall that the Linux box comes equipped with anyways. It makes it easier to write rules for iptables rather than learn abou the various chains(INPUT/OUTPUT/FORWARD). and i guess it makes the rules "stick" by starting off at boot. Atleast thats the way i understand it :neutral: ....

But the question remains that if my Firestarter doesn't have any rules on it and iptables doesnt list any rules either, whats protecting my system? Also, my ports are all in stealth mode, who takes care of that? :confused:

---

### Post by scxtt on 2006-07-19
it's essentially in a locked down mode until you start allowing services per port / connections from specific hosts ...

---

### Post by airjunman on 2006-07-19
But anything I want to access works.. i mean messenger/mail/browser/ftp- the works ...does it work by creating a baseline based on connections when its installed? or does it let pretty much any outgoing and no incoming unless i specifically allow them.

The only service that dint work was webhttrack, n that was installed after i installed firestarter, but i added a rule allowing access to 8080 from localhost and now that works for starters...

also when theres an inbound connection for, say a hotsmtp service(port 2500) on my machine(from my locally installed mail client), does it first go through the firewall, which allows it through to xinetd, which in turn starts the hotsmtp daemon? is that how it works?

---

### Post by scxtt on 2006-07-19
yeah - it shouldn't stop outbound connections originating from the box it's running on ...

---

### Post by wifiabc on 2006-07-20
If you start firestarter and then do "iptables -vnL" you would be able to see the rules.

---

### Post by airjunman on 2006-07-20
i tried it, but still got nothing:

> me@myhostname:~$ sudo iptables -vnL
Password:
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 

any help getting me to understand this is welcome...

---

### Post by wifiabc on 2006-07-21
Can you start firestarter and post the following?

a)output of:
```
ps aux |grep -i firestarter 
```

b) output of:
```
iptables -vnL 
```

c) /etc/firestarter/configuration 

d) output of:
```
route
```

---

### Post by sarum on 2006-07-21
Hello, I'm supprised that we cannot find precise details for configuering Firestarter. There seems to be a wealth of info on every other Ubuntu subject. I'm a newby and want to configuer my Firestarter. Typing 'IPTables -L shows Input/Output/Forward to be open.
However I have a book 'Fedora for Dummies' and page 106 onwards gives very clear directions on how to do it all down to saving rules to a script and how to turn on and off.
Being a newby (and old) I'm no longer bold. But if someone could tell me that Firestarter is non-distro-specific I think I might just do it. Perhaps after learning what to backup.
Cheers Sarum.

---

### Post by wieman01 on 2006-07-21
Firestarter should not be distro-specific at all. Have you tried the manual from this web-site?

[http://www.fs-security.com/]("http://www.fs-security.com/")

I think everything should be in there. I figured that Firestarter is fairly easy to use, much simpler at least than configuring IP Tables manually.

---

### Post by scxtt on 2006-07-21
i'm not one to advocate the non-understanding of anything, but if the question here happens to be "is firestarter working", i can most assuredly tell you that if it's running (and unless you've done otherwise, it ALWAYS is on boot --> ps -ef | grep firestarter) it's doing it's job - and if you don't believe me, make sure there's nothing in the "Policy" tab and try to make a connection to your box - i can guarantee you it won't connect ... VM's running on my host can't even connect via ssh to the host unless i allow their IPs (and we're talking 192.168.1.100 <-> 192.168.1.101 here) ...

now is there a literal translation b/t what's listed in firestarter vs. the output of iptables -vnL? - i don't know - but honestly, it doesn't matter ... it's not the 'goal' of firestarter to get you to understand IP tables, it's the 'goal' of firestarter to block/allow access to ports - and if it's doing that (and i assure you it does) - then any beef w/ iptables has nothing to do w/ firestarter ...

and i scoff at the losers who try to connect to the 2 ports i actually forward from my router - firestarter frys their attempts just as it should - and even tells me about it :D ...

---

### Post by wieman01 on 2006-07-21
> **scxtt said:**
> i'm not one to advocate the non-understanding of anything, but if the question here happens to be "is firestarter working", i can most assuredly tell you that if it's running (and unless you've done otherwise, it ALWAYS is on boot --> ps -ef | grep firestarter) it's doing it's job - and if you don't believe me, make sure there's nothing in the "Policy" tab and try to make a connection to your box - i can guarantee you it won't connect ... VM's running on my host can't even connect via ssh to the host unless i allow their IPs (and we're talking 192.168.1.100 <-> 192.168.1.101 here) ...

now is there a literal translation b/t what's listed in firestarter vs. the output of iptables -vnL? - i don't know - but honestly, it doesn't matter ... it's not the 'goal' of firestarter to get you to understand IP tables, it's the 'goal' of firestarter to block/allow access to ports - and if it's doing that (and i assure you it does) - then any beef w/ iptables has nothing to do w/ firestarter ...

I agree. It's doing its job well. It's up & running and protecting my computer. Just go to the Sygate web-site and have it tested. :-)

---

### Post by Malac on 2006-07-21
[COLOR=Black][SIZE=2]Go to [http://www.fs-security.com/](http://www.fs-security.com/) what firestarter does and how to configure it is explained pretty well there.

Hope this helps.
[/SIZE][/COLOR]

---

### Post by frodon on 2006-07-21
If you want a good firewall which you know what it is doing, write your iptables script yourself. It's far better than using firestarter :
[http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)

---

### Post by wieman01 on 2006-07-21
> **frodon said:**
> If you want a good firewall which you know what it is doing, write your iptables script yourself. It's far better than using firestarter :
[http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)

Well... it's a good option for advanced users but a bit over the top for normal users like me. But each of us has to make the decision whether or not it's worth it. Thanks for the guide anyway. I may use it at a later stage.

---

### Post by airjunman on 2006-07-21
> **frodon said:**
> If you want a good firewall which you know what it is doing, write your iptables script yourself. It's far better than using firestarter :
[http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)

Thanks frodon, that is a pretty awesome resource...

---

### Post by wifiabc on 2006-07-21
> **wieman01 said:**
> I agree. It's doing its job well. It's up & running and protecting my computer. Just go to the Sygate web-site and have it tested. :-)

I agree too. Firestarter works on my system. It is definitely easier than doing iptables manually.

---

### Post by goodfren on 2006-07-21
> **frodon said:**
> If you want a good firewall which you know what it is doing, write your iptables script yourself. It's far better than using firestarter :
[http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)
I think there is init.d script error, after i install it and run script executable, the terminal cannot detect the document.

Anyadvice for this? The rest work fine and i feel more easy to use than firestarter.

---

### Post by frodon on 2006-07-22
BTW, i have a thread for this guide, if you wish support :
[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

Did you run the "sudo update-rc.d firewall defaults" command ? i use the same script without any problem.

---

### Post by goodfren on 2006-07-22
> **frodon said:**
> BTW, i have a thread for this guide, if you wish support :
[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

Did you run the "sudo update-rc.d firewall defaults" command ? i use the same script without any problem.
This is what i get

> chmod: cannot access `etc/init.d/firewall': No such file or directory

But the rest all ok. I got a feeling that when i install / remove firestarter and guarddog that make my program now quite unstable and unable to keep my login into internet using Adsl connection. I even reinstall the pppoe program but still exist the problem.

Your advice is needed, thks

---

### Post by frodon on 2006-07-22
Hehe, you found a typo i forgot the "/" before etc/init.d/firewall,
so the command is "sudo chmod +x /etc/init.d/firewall", i made the correction in the guide too.
I don't know firestarter and guarddog really well but they should only mofify your iptables setting.
Once the init.d script installed, i advice you to run a "sudo /etc/init.d/firewall stop", it will erase all the iptables rules even those set by other programs like firestarter or guarddog.

If you have other problems or question please use the thread related to the guide because i wouldn't highjack this thread.

---

### Post by jrjr on 2006-07-22
sorry

---

