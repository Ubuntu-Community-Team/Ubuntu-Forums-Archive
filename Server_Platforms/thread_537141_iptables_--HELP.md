---
title: "iptables --HELP"
date: 2007-08-28
forum: Server Platforms
---

### Post by tekkenlord on 2007-08-28
Hi, I want to do something very simple but have no idea how. I would like to use the iptables commands to :

1. Allow my computer to surf the internet, download, etc.
2. Block all incoming connections.

Now, I have found a command:

iptables -A INPUT -j DROP

which blocks all incoming traffic, however after this I cannot surf the internet. Can someone tell me what am I doing wrong?

Thanks in advance.

---

### Post by WinterWeaver on 2007-08-28
sudo apt-get install firestarter

^_^ -- That should take care of all that for you :)

EDIT: oops... forgot the 'install'

---

### Post by tekkenlord on 2007-08-28
Thanks for the quick response. However, I have already tried that and it won't let me add any rules (do not know why). I need to do it with commands...

---

### Post by WinterWeaver on 2007-08-28
Firestarter will also warn you of any hits etc. it's basically a nice front-end to your IP-Tables

---

### Post by WinterWeaver on 2007-08-28
?? Thats odd... I use Firestarter all the time.. and I add and remove rules every week.

Does firestarter prompt you for a password when you first start it?

did you go through the wizard and/or check the preferences?

---

### Post by tekkenlord on 2007-08-28
Yes, it asks for a password and I used the wizard and checked the preferences. In any case, I think that the default firestarter policies block incoming connections. However, I used a shh to my self (from my computer) and it does not block it. So I removed it.

---

### Post by WinterWeaver on 2007-08-28
well... in that case I cant help you. Personally I've never touched the IPTables. i've just used firestarter and its been working for me.

sorry... :( ... I hope someone with a bit more knowledge can assist.

WW

---

### Post by tekkenlord on 2007-08-28
That's allright, thanks! 

Come on guys, there must be someone who knows these simple commands.!?

---

### Post by tekkenlord on 2007-08-28
Ok I managed to get firestarter to work properly. However, when I still ssh to myself I do not get rejected. Is this normal?

---

### Post by p_quarles on 2007-08-28
What do you mean "ssh to myself"? Do you mean you're tunneling to the same computer you're calling from? If so, which of the following commands are you using:
```
ssh localhost
ssh *lan-IP-address*
ssh *public-IP-address*
```
It makes a difference. In most situations you only want your firewall to prevent the latter. 

The firestarter wizard does allow you to set policy, but the options are more limited than they are using CLI. I'm very much a beginner with iptables myself (see [this recent thread]("http://ubuntuforums.org/showthread.php?t=533425")), but I'll offer whatever help I can. 

One question, though: are you trying to disable SSH access completely? Because, if so, that's relatively simple.

---

### Post by tekkenlord on 2007-08-28
Yes, I am tunneling to the same computer I am calling from using the third command (I think). Actually, I want to block all incoming connections but also be able to ssh to others (e.g. office computer). Anyway, I found a minute ago that the commands 

iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

and subsequently

iptables -A INPUT -j DROP

will do exactly what I want. Btw, do you know what an established session is? Also, when I was trying to block the incoming traffic using only the second command I was not able to surf the internet or connect to other computers. However, the second command affects only the inbound traffic (INPUT), so why wasn't I able to have outgoing connections? (I hope that was not too confusing... ;-) ) What am I missing here?

Thanks for replying and know that beginner or not, your help is greatly appreciated!

---

### Post by p_quarles on 2007-08-28
> **tekkenlord said:**
> Yes, I am tunneling to the same computer I am calling from using the third command (I think). Actually, I want to block all incoming connections but also be able to ssh to others (e.g. office computer).

The only way someone else can ssh into your machine is if you have the ssh server software running. Try this:
```
sudo apt-get remove openssh-server
```You'll still have the ssh client, which is what allows you to tunnel into other servers, but your computer will no longer be listening for ssh requests. 

> Anyway, I found a minute ago that the commands 

iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

and subsequently

iptables -A INPUT -j DROP

will do exactly what I want. Btw, do you know what an established session is?Established=session you started. The server you're connecting to needs to be able to send information back to your machine in order for you to get it. (i.e., blocking *all *incoming traffic is the same as unplugging the network connection). 

> Also, when I was trying to block the incoming traffic using only the second command I was not able to surf the internet or connect to other computers. However, the second command affects only the inbound traffic (INPUT), so why wasn't I able to have outgoing connections? (I hope that was not too confusing... ;-) ) What am I missing here?You can set rules for outbound traffic by replacing the INPUT option with OUTPUT. I recommend reading the thread I linked to in my last message. Koenn's replies to my question explained it very well. 

One other thing to add: the default installation of Ubuntu/Debian is fairly secure. You don't actually need to add iptables rules until you start installing server software. Essentially, these systems won't respond to any external request until you instruct them to. So, if you're not running an ssh server, Apache, MySQL, ftp, etc., you're already invisible to the scriptkiddies. And the serious hackers don't really care about you, unless you're running a bank or a country.

---

### Post by tekkenlord on 2007-08-28
Cool! Understood. Thanks again. 

> unless you're running a bank or a country.

Well, not yet anyway... ;-)

---

### Post by HermanAB on 2007-08-28
Note that '-A' adds a command to the end of the list, while '-I' inserts a command at the start of the list.  

When you are hacking away and playing with new rules to see what they do, a new command usually needs to go in the beginning, not at the end.  The reason being that the last command is usually a DROP everything still left over and not explicitly ACCEPTed on the floor command, so adding rules at the end after that one will usually do abschlootly diddly squat...

Hope that helps!

Herman

---

### Post by p_quarles on 2007-08-28
> **HermanAB said:**
> Note that '-A' adds a command to the end of the list, while '-I' inserts a command at the start of the list.  

When you are hacking away and playing with new rules to see what they do, a new command usually needs to go in the beginning, not at the end.  The reason being that the last command is usually a DROP everything still left over and not explicitly ACCEPTed on the floor command, so adding rules at the end after that one will usually do abschlootly diddly squat...

Hope that helps!

Herman
You can also use the -I option to specify a rule number. For instance:
```
sudo -I OUTPUT 2 -m state --state RELATED,ESTABLISHED -j ACCEPT 
```
will insert that rule into line 2 of the OUTPUT chain, and push the current rule 2 to rule 3.

---

