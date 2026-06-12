---
title: "Advice after an attempted SSH attack"
date: 2009-03-06
forum: Server Platforms
---

### Post by mconway on 2009-03-06
Tonight I received a message from [FONT=Courier New]denyhosts[FONT=Arial] [FONT=Verdana]that it detected suspicious activity from a Shanghai, China IP (the location I discovered on my own). After sifting through my logs I discovered many brute-force attempts on my OpenSSH server.

My question is, should I report this type of attack? Maybe their ISP would be interested in knowing about it, maybe they don't care. [-( [/FONT][/FONT][/FONT]For now, they're in /etc/hosts.deny

Thanks in advance

---

### Post by brian_p on 2009-03-06
> **mconway said:**
> 

My question is, should I report this type of attack? Maybe their ISP would be interested in knowing about it, maybe they don't care. [-( [/FONT][/FONT][/FONT]For now, they're in /etc/hosts.deny 

It wouldn't do any harm but do not be too surprised if it leads nowhere. I never bother unless the ISP is geographically close and known to have a good AUP.

---

### Post by albandy on 2009-03-06
I've received this kind of attacks too, usually is a trojan running in a computer that scans the net searching for open ssh ports.
I solved this changing the ssh port to another, no more attacks received.

---

### Post by matey3 on 2009-03-06
There is a whole website related to DenyHost.
They even have a program you can download and install. but I wrote a little script that would read the /var/log/auth.log file take the intruders IPs and then copy them into my /etc/hosts.deny file;

google denyhost...
sorry I am not on my linux machine right now.

---

### Post by williane on 2009-03-06
yeah just change your port to something crazy like 19387 and make sure youre not using root or another really common name to log in. if they dont know your port or a valid name to begin with, they cant bruteforce the pass.

you can also set ssh to deny an IP after so many failed attempts in a certain time.

---

### Post by matey3 on 2009-03-06
got on PUtty....
use either this line;
```
grep 'Failed password' /var/log/auth.log|cut -d ']' --fields=2|cut -d ' ' --fields=9|uniq -c|sort -nr > ct-result.txt
```

or this one to put the results in a file called ct-result.txt

```
grep 'from' /var/log/auth.log|cut -d ' ' --field=13|uniq -c|sort -nr > ct-result.txt
```

I can never get the right column I use 13 here but I get diff. results? most of the IP addresses show up tho.
here's a link I used a long ago. 

[http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts](http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts)


BTW I used to report them , some times I get feedback some times nothing. In a case that the attackers were coming from a college in china, I reported it to their net admin and told him to watch it there...
he agreed. but most dont bother writing back so I quit reporting them.

I learned that I cant be too worried about these things, I mean its one of me against china southamerica here and there.. so let the system take care of itself by providing tough to break passwords and beefing up the sec. (notice they try as 'nobody' and cron jobs? heh.. no one been able to break in any way)!

---

### Post by mconway on 2009-03-10
Hey everyone, thank you for your responses. I'm already using the program denyhosts, which alerted me to the attempt. Of course, by now many more have occurred and then I decided to just use a non-standard port.
 
I sort of enjoyed reading my logs when they still occurred though--the invalid usernames were sometimes ridiculous! Like I'm really going to log in as falco. Or marine. lol
 
Aside from changing the port, I've enabled some other more secure settings from the start so I don't have much to worry about. It's just not often that I run a box that faces the net like that and I wanted to know how most of you react to a simple attempt like the one I described.
 
I realized eventually that no one in China will be interested in hearing (or capable of hearing) about all the attention I kept getting from their network. Shortly after my first post, I did a few scans on the first host and saw that it was likely a slave. Oh well.
 
In any case, thanks for the tips! :)

---

