---
title: "Iptable rule confusion."
date: 2008-06-22
forum: Security
---

### Post by madu on 2008-06-22
Hello,

I used the iptable guide given here ([http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)) and it works fine. 

Then I allowed http and ssh in the following way:
> 
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 80 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22  -j ACCEPT


Now this worked fine too.
Then I wanted to restrict ssh access to only my work computer domain so I did this:

> 
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22  --source  ! 131.0.0.0/8 -j DROP


So I expected iptable to drop all the tcp/22 packets 'except' from 131/8.
And it didnt work.

Then I did:
> iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22  --source 131.0.0.0/8 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22  --source ! 131.0.0.0/8 -j DROP

ANd now it works.
I'm a little confused as to why the first rule didnt allow 131/8 and the second did. All I did was to first allow 131/8 tcp/22 to come in. But doesnt > iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22  --source  ! 131.0.0.0/8 -j DROP do the same?

Also would appreciate if someone clarify the different between '-s' and '--source'.

Thanks guys.

---

### Post by kevdog on 2008-06-22
Did you have both rules in the ruleset?  Again once a rule is matched, it does not scan the remainder of the rules in that particular chain (ie TRUSTED in your case).  I noted that TRUSTED is your personal chain name.  Is this being called from the input chain?

---

### Post by madu on 2008-06-22
yes.. I have both these.. in the order given.

> iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22 --source 131.0.0.0/8 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22 --source ! 131.0.0.0/8 -j DROP 


I dont understand why only the second rule wouldnt work. I'm sorry my understanding on the chains are minimal. I just followed the guide I mentioned. 

Thanks for the reply mate.

---

### Post by The Cog on 2008-06-22
I think kevdog is probably right and that you haven't appreciated that hte rules are scanned in order, and that a particular chain ends whan a match is found. Here are some examples:

```
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22 --source ! 131.0.0.0/8 -j DROP
```
accepts ALL SSH connections. Why? because the first rule says for any ssh connection, jump to the ACCEPT target - the second rule never even gets looked at. These two though:
```
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22 --source 131.0.0.0/8 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22 -j DROP

```
does what you want. SSH from 131 sees the first rule and jumps off to ACCEPT. SSH from anywhere else doesn't match the first rule and then looks at the second rule, which does match and sends it off to DENY.

The thing is that the rules are looked at one at a time, in order. They are not considered as an all-in-one thing. This allows you to say to allow this specific thing, that specific thing, another specific thing, and at the end just have an all-encompassing "drop everything" to sweep up what hasn't already been allowed.

And in fact if you set a default policy to drop packest where no rule is found, you may be able to get away without the second (drop) rule and allow the default drop to handle it.

---

### Post by madu on 2008-06-22
> **The Cog said:**
> I think kevdog is probably right and that you haven't appreciated that hte rules are scanned in order, and that a particular chain ends whan a match is found. Here are some examples:

```
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22 --source ! 131.0.0.0/8 -j DROP
```
accepts ALL SSH connections. Why? because the first rule says for any ssh connection, jump to the ACCEPT target - the second rule never even gets looked at. These two though:
```
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22 --source 131.0.0.0/8 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22 -j DROP

```
does what you want. SSH from 131 sees the first rule and jumps off to ACCEPT. SSH from anywhere else doesn't match the first rule and then looks at the second rule, which does match and sends it off to DENY.

The thing is that the rules are looked at one at a time, in order. They are not considered as an all-in-one thing. This allows you to say to allow this specific thing, that specific thing, another specific thing, and at the end just have an all-encompassing "drop everything" to sweep up what hasn't already been allowed.

And in fact if you set a default policy to drop packest where no rule is found, you may be able to get away without the second (drop) rule and allow the default drop to handle it.

Thanks a lot Cog.
But got one confusion still.
In this case:
> iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22 --source ! 131.0.0.0/8 -j DROP

why doesnt the incoming SSH from 131/8 match and go through?why do I need an explicit ACCEPT for the 131/8 ? Doesnt the above rule implicitly mean to ACCEPT 131/8?

---

### Post by The Cog on 2008-06-22
Well that depends on what other rules exist afterwards. 
When you say it "didn't work", you don't say whether that was because it dropped things you wanted passed or whether it passed things you wanted to drop. But anyway, without seeing the exact ruleset it's difficult to comment on that.

You could indeed go:
```
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22 --source ! 131.0.0.0/8 -j DROP
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22 --source 131.0.0.0/8 -j ACCEPT
```
but then you have your 131 sepcification in two lines. With more complicated requirements that gets very messy and makes your head hurt. It is better to make use of the fact that rules are evaluated in order to keep things simple. Perhaps like this:
```
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22 --source ! 131.0.0.0/8 -j DROP
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22 -j ACCEPT
``` but even this gets messy. Suppose you now decide there is a second network where you want to allow access. Writing a rule that drops packets unless they are from network A **or** network B is probably only possible by reversing the logic and listing all the exceptions one-by-one. Which means listing separately every source you do want to accept and finally saying drop everything else.

---

### Post by kevdog on 2008-06-22
Id agree that it would probably be better to have a default drop policy or at least start a drop stance on port 22, and then specify exceptions.

madu
Are you using the script from your first link to set your iptables policy?

---

### Post by madu on 2008-06-22
Dear Cog and Kevdog,
Thank you very much for the replies. I guess the DROP everything except 131/8 doesnt really mean to ACCEPT 131/8.> # first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow loopback traffic
iptables -A FIREWALL -i lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
iptables -A FIREWALL -j DROP

# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL
# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP

iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 80 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22  --source 131.0.0.0/8 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22  --source ! 131.0.0.0/8 -j DROP


This is the iptable I'm using. This works fine. Was just wondering why I cant omit the 131/8 ACCEPT and use only 131/8 DROP statement.

Thanks heaps for the replies guys. Appreciate it.

---

### Post by madu on 2008-06-22
I would also like to know something else.
I just checked in my work machine, them machine I'm using to ssh connect to my home server, and there is no sshd_config file in /etc/ssh/. 
In my home server there are both ssh_config and sshd_config.

I'm curious as to why one machine has sshd_config and one doesnt and also the difference between the two. 

Also, if I want to make my machine look for the RSA private key somewhere other than the ~/.ssh/ida_rsa, how would I change it? In the ssh_config file, 

> #   IdentityFile ~/.ssh/id_rsa


is commented out and there is no sshd_config file.

Appreciate the help guys. Thanks a lot.

Madu.

---

### Post by kevdog on 2008-06-22
Couple of things. 

The sshd_config file is only for the ssh server.  I'm inferring you do not have the openssh-server installed at your work machine.

In order to have the client use a different file name instead of the default id_rsa file, you can do a few things:
1. Connect via the command line specifying the name of the identity file explicity:
ssh -i another_rsa_file .... [email]user@server.com[/email]

2. Copy the system wide ssh_config file from /etc/ssh/ssh_config to ~/.ssh/config.  You are then free to alter this personal ssh_config file -- with duplicate settings the personal ssh_config file will take precedent, with different settings the system wide config file will be appended to the personal file.  You can then start building a profile for your home computer such as:

```

Host myhomeserver
   HostName myhomeserver.com
   User username
   ForwardX11 yes
   RSAAuthentication yes
   PasswordAuthentication no
   CheckHostIP yes
   StrictHostKeyChecking ask
   IdentityFile ~/.ssh/identity
   IdentityFile ~/.ssh/NEW_FILE_NAME
   IdentityFile ~/.ssh/id_dsa
   Port 22
   Protocol 2
   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes2
56-cbc
   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
   EscapeChar ~
   PermitLocalCommand yes


```

You could then connect to your home computer simply by type
ssh myhomeserver

See man ssh_config for more options and thorough explanations

Does this help at all?

As far as the firewall question, I got to look something up!

---

### Post by kevdog on 2008-06-22
My guess (only a hunch since I haven't tried this myself) is that you haven't set a default policy for the particular TRUSTED chain -- not the first thing you did in your script was to set default policies for the INPUT/OUTPUT/FORWARD chains of accept.

So why dont you try this (again if you want a default policy of drop you may need to change this logic):

```
# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED
**[SIZE="3"]iptables -P TRUSTED ACCEPT[/SIZE]**


.....(Skip to bottom -- Ive only included this one line)
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22 --source ! 131.0.0.0/8 -j DROP
```

Again the default policy is to accept everything, so I took out the port 80 rule (since this should be covered by the default) and only explicity added lines where you didnt want the default policy

---

### Post by madu on 2008-06-23
> **kevdog said:**
> Couple of things. 

The sshd_config file is only for the ssh server.  I'm inferring you do not have the openssh-server installed at your work machine.

In order to have the client use a different file name instead of the default id_rsa file, you can do a few things:
1. Connect via the command line specifying the name of the identity file explicity:
ssh -i another_rsa_file .... [email]user@server.com[/email]

2. Copy the system wide ssh_config file from /etc/ssh/ssh_config to ~/.ssh/config.  You are then free to alter this personal ssh_config file -- with duplicate settings the personal ssh_config file will take precedent, with different settings the system wide config file will be appended to the personal file.  You can then start building a profile for your home computer such as:

```

Host myhomeserver
   HostName myhomeserver.com
   User username
   ForwardX11 yes
   RSAAuthentication yes
   PasswordAuthentication no
   CheckHostIP yes
   StrictHostKeyChecking ask
   IdentityFile ~/.ssh/identity
   IdentityFile ~/.ssh/NEW_FILE_NAME
   IdentityFile ~/.ssh/id_dsa
   Port 22
   Protocol 2
   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes2
56-cbc
   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
   EscapeChar ~
   PermitLocalCommand yes


```

You could then connect to your home computer simply by type
ssh myhomeserver

See man ssh_config for more options and thorough explanations

Does this help at all?

As far as the firewall question, I got to look something up!

Thanks a lot Kevdog.. Exactly what I was looking for.. will try out the iptable rule soon as I get home..
Thanks a million mate!

---

### Post by The Cog on 2008-06-23
> iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 80 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22 --source 131.0.0.0/8 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22 --source ! 131.0.0.0/8 -j DROP 
I think you should be able to omit that middle line, since as no other statements will match and you should eventually reach the default ACCEPT for the INPUT chain. I wonder if you have been clearing the iptables settings between invocations of the script, or if you have been allowing the different lines to accumulate. The command > sudo iptables -nvL will show you what's currently active, and also give counters for how many matches each line has made.

I still don't like that way of doing things - it feels too error -prone to me, but I guess that's personal choice.

---

### Post by kevdog on 2008-06-23
I would put these lines at the top of your script so the IPtables are flushed in between each load:

IPTABLES=/sbin/iptables

$IPTABLES -F
$IPTABLES -F -t nat
$IPTABLES -X

---

### Post by madu on 2008-06-23
> **The Cog said:**
> I think you should be able to omit that middle line, since as no other statements will match and you should eventually reach the default ACCEPT for the INPUT chain. I wonder if you have been clearing the iptables settings between invocations of the script, or if you have been allowing the different lines to accumulate. The command  will show you what's currently active, and also give counters for how many matches each line has made.

I still don't like that way of doing things - it feels too error -prone to me, but I guess that's personal choice.

My problem is exactly that it doesnt work when the middle ine is taken off. I need the middle line to work. when I dont have the middle line nothing is accepeted, as far as I can tell. I tried through 131/8 and another IP and both failed. 
I'm guessing DROP everything except 131/8 doesnt necessarily mean ACCEPT 131/8. 
But then again,if I have ACCEPT 131/8, I dont want the third line, do I?
Even if I dont have the DROP rule, anyother ssh request wouldnt match any rule and just get dropped? 

@Kevdog: I do have those lines. I am flushing the iptable before restarting it with new rules. 

Thanks a million for the help guys.

---

### Post by brian_p on 2008-06-23
> **madu said:**
> My problem is exactly that it doesnt work when the middle ine is taken off. I need the middle line to work. when I dont have the middle line nothing is accepeted, as far as I can tell. I tried through 131/8 and another IP and both failed. 
I'm guessing DROP everything except 131/8 doesnt necessarily mean ACCEPT 131/8. 
But then again,if I have ACCEPT 131/8, I dont want the third line, do I?
Even if I dont have the DROP rule, anyother ssh request wouldnt match any rule and just get dropped? 

I appreciate it is iptables you are sorting out but using tcp wrappers you could have

```
sshd: 131.0.0.: ALLOW
ALL: ALL: DENY
```

in /etc/hosts.allow. This would allow connections for ssh from 131.0.0.0/8 only.

---

### Post by madu on 2008-06-23
> **brian_p said:**
> I appreciate it is iptables you are sorting out but using tcp wrappers you could have

```
sshd: 131.0.0.: ALLOW
ALL: ALL: DENY
```

in /etc/hosts.allow. This would allow connections for ssh from 131.0.0.0/8 only.

Hello Brian, thanks for that.
that seems like a neat way to do that too.. didn't know that one.. will try it out.. thanks mate.

---

### Post by kevdog on 2008-06-23
It took me a long time to figure this out, but I think I got it.

Here is your relevant ruleset:
```
# DROP all other packets
iptables -A FIREWALL -j DROP

# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL
# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP

iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 80 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22 --source 131.0.0.0/8 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22 --source ! 131.0.0.0/8 -j DROP
```

If you follow the course of your chains, it goes from
INPUT --> FIREWALL --> TRUSTED ---BACK TO---> FIREWALL --BACK TO-->INPUT

Again in your script you created two custom chains FIREWALL AND TRUSTED.  IPTABLES is set up to follow each chain, but then once the chain has ended, it ends up back at the calling chain. So INPUT calls FIREWALL which calls TRUSTED.  When the TRUSTED chain is completed, it automatically goes back to the FIREWALL chain, which then completes and ends back in the INPUT chain.

Following this logic I'm going to rearrange your script (just so you can see what is happening (leaving out the rule 131.0.0.0/8 ACCEPT rule)

```



#Start at input chain

# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL

#Perform some checking in the FIREWALL chain

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow loopback traffic
iptables -A FIREWALL -i lo -j ACCEPT


# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED

#Perform some actions in the TRUSTED chain

iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 80 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22 --source ! 131.0.0.0/8 -j DROP

#Return to the FIREWALL chain (please note that any source port=131.0.0.0/8 hasn't been matched yet)

# DROP all other packets (NOTICE THIS IS WHERE 131.0.0.0/8 is getting dropped do to this statement right here!!!)
iptables -A FIREWALL -j DROP

#RETURN TO INPUT CHAIN

# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP

```

So notice you have an explicit drop default stance on the FIREWALL CHAIN if no rules are matched prior to this statement

So they way things are set up with your setup, you only want to list exceptions that you want to be accepted.  So in order to accomplish this you could modify your TRUSTED chain to only mention rules you want to explicitly ACCEPT (everything non-matching will get dropped).  So you probably only want the following:

```
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 80 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22 --source 131.0.0.0/8 -j ACCEPT
```

I hope this works for you -- it was confusing me for a long time until I started manually drawing out the chain paths.  And note I would put the following at the top of your original script along with the changes mentioned for the TRUSTED chain:

IPTABLES=/sbin/iptables

$IPTABLES -F
$IPTABLES -F -t nat
$IPTABLES -X

---

### Post by madu on 2008-06-24
> **kevdog said:**
> It took me a long time to figure this out, but I think I got it.


Dear Kevdog,
cannot thank you enough for this man.. not only because you figured out the mystery, but also I understood what is actually happening in the iptable. I had no clear idea about the chains and how they are followed before. Think I got that too now mate.

With my iptable, when I dont have the ACCEPT 131/8 and ONLY DROP !131/8, the connection goes back to FIREWALL and gets dropped there.

Just one tiny question, does it matter where I put the FORWARD DROP rule? I can have it in the top of the iptable and wouldnt make a difference would it?

Thanks a million again buddy.

---

### Post by kevdog on 2008-06-24
I would write your script another way if I could, but no, it does not matter where you put the FORWARD statement (you are catching on).

What you could do, would be to change:
iptables -P FORWARD ACCEPT

to 

iptables -P FORWARD DROP

This line set the default policy of the chain to drop

As I have since learned is although you can create your own chains (FIREWALL and TRUSTED as in this example), the default policy statement can only be used with the 3 default chains of FORWARD, INPUT, OUTPUT.  

What is really redundant in your script is the following (as see if you get this)

#1 The default policy for the INPUT chain is ACCEPT
iptables -P INPUT ACCEPT

#2 The INPUT chain calls the FIREWALL chain

#3 In indirect way of setting the default policy on custom defined chains is similar to the following (notice however this rule needs to the last rule in the chain):
iptables -A FIREWALL -j DROP

So what you have here is a redundant mechanism, whereby the default policy on incoming connections is first accept and then later drop.  You could probably rewrite the script to actually set the default policy on the INPUT chain to be DROP, do away with the FIREWALL and TRUSTED chains, and then simply set exceptions to this rule below (something similar to):

iptables -P INPUT DROP
iptables -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -i eth0 -p tcp -m tcp --dport 80 -j ACCEPT
iptables -A INPUT -i eth0 -p tcp -m tcp --dport 22 --source 131.0.0.0/8 -j ACCEPT

That basically would be it for the entire INPUT chain without calling or creating the custom chains.  Default policies when defined are almost always drop or reject, however in this example it kind of took a convoluted route, but in the end, the default policy was in fact reset to reject.


Incorporating the changes above you could try (if you were brave, just the following to confirm everything I just stated -- notice how much smaller the script becomes):

```
#!/bin/sh
#

IPTABLES=/sbin/iptables

### flush existing rules and set chain policy setting to DROP
$IPTABLES -F
$IPTABLES -F -t nat
$IPTABLES -X

$IPTABLES -P INPUT DROP
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -P FORWARD DROP

### state tracking rules
$IPTABLES -A INPUT -m state --state INVALID -j DROP
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

### ACCEPT rules
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -i eth0 -p tcp -m tcp --dport 80 -j ACCEPT
iptables -A INPUT -i eth0 -p tcp -m tcp --dport 22 --source 131.0.0.0/8 -j ACCEPT

exit
### EOF ###
```

And if you wanted your computer to respond to ping requests (I usually do since this is the first way I test when the computer isn't responding or verifying that the computer at least responds to a basic command):
$IPTABLES -A INPUT -p icmp --icmp-type echo-request -j ACCEPT

And lastly although I wont include this here, if you are really interested in tracking who is going in and out or attempting to connect to your computer, its possible to set up some logging to log attempted connections, rejections, completed connections, etc.

And you could also probably drop the -i eth0 statements if you use multiple network adapters (if you switch between wired and wireless if you wanted).

And lastly -- know that you have a really basic grasp of working with firewalls, check out my Port Knocking Tutorial if you want to see a really novel concept about dynamically changing your firewall (Shameless plug but I had nothing to do with the program).  I found the whole concept of Port Knocking and IPtables really interesting.

---

### Post by madu on 2008-06-24
Dear Kevdog,

Thanks heaps for that mate. I think I got the hang of the basics. Just got a few confusions, if you dont mind.

1) The 'default' policy (-P) means that if an INPUT packet didn't match any of the custom rules, the default rule will be executed?

2) Probably not related to Iptables, but what is the difference of using '$IPTABLES' and 'iptables' ? for the custom rules you have used 'iptables' while for other '$IPTABLES' is used. Can we use them interchangeably or is there a distinction between the two?

Finally, I would be really glad if you can give me a guide for tracking ppl who connect to my computer. Also I have a brief look at 'port knocking'. Looks really interesting. I'd definitely have a look leisurely. 

Thank you again mate. Really appreciate the help and clarifications.

Madu.

---

### Post by The Cog on 2008-06-24
1) Yes, the default Policy applies when no match is made in any of the chain rules. This is why it is usual to simply set a default DROP policy and list the explicit things you want to accept, like a whitelist.

2) Using $IPTABLES, that variable will have been defined to be /usr/sbin/iptables near the top of the file. It means you can change the executable just by changing one line I suppose, but since you will never want to do that (that I can think of), it just seems like an added layer of confusion to me. If I ever ddi want to use a different executable, searcn-and-replace will fix it up in seconds.

---

### Post by kevdog on 2008-06-24
I like to use variables for parameters that might change that I call more than once in a script.  I suppose its a little overkill, so it might not be necessary, but at least I think you get the idea.

---

### Post by madu on 2008-06-24
Dear Cog & Kevdog,

Thanks again for the input guys.
Kevdog, I tried the ruleset you gave and it worked fine. Thanks for that mate. much easier to understand like that. I guess my iptable is really simple that I dont need other chains to be defined.

Thanks again guys. I would also like to know about how to track the incoming connections.. if wouldnt mind sharing it :-)

Appreciate all the help.

Cheers.

---

### Post by kevdog on 2008-06-24
Track the incoming connections -- Does this mean track the dropped packets, or track the accepted connections only or both?

Most logging is done for dropped packets however I don't know what you want to do.

If you only want to log the dropped packets (as a form of troubleshooting), I've rewritten your script to the following:

```

#!/bin/sh
#

IPTABLES=/sbin/iptables

### flush existing rules and set chain policy setting to DROP
$IPTABLES -F
$IPTABLES -F -t nat
$IPTABLES -X

$IPTABLES -P INPUT DROP
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -P FORWARD DROP

### state tracking rules
$IPTABLES -A INPUT -m state --state INVALID -j DROP
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

### ACCEPT rules
$IPTABLES -A INPUT -i lo -j ACCEPT
$IPTABLES -A INPUT -i eth0 -p tcp -m tcp --dport 80 -j ACCEPT
$IPTABLES -A INPUT -i eth0 -p tcp -m tcp --dport 22 --source 131.0.0.0/8 -j ACCEPT
$IPTABLES -A INPUT -p icmp --icmp-type echo-request -m limit --limit 10/second -j ACCEPT

### Create a LOGDROP chain to log dropped packets
$IPTABLES -N LOGDROP

### Drop Log Ruleset (Logs all packets not captured above, before dropping)

#Change the Following Parameters to Limit the amount of Logging
LOGLIMIT="2/s"
LOGLIMITBURST="10"

#Log level may be one of the following: debug, info, notice, warning, warn, err, error, crit, alert, emerg, panic
LOGLEVEL = debug

$IPTABLES -A LOGDROP -i ! lo -p tcp -m limit --limit $LOGLIMIT --limit-burst $LOGLIMITBURST -j LOG --log-level $LOGLEVEL --log-prefix "TCP DROP: "
$IPTABLES -A LOGDROP -i ! lo -p udp -m limit --limit $LOGLIMIT --limit-burst $LOGLIMITBURST -j LOG --log-level $LOGLEVEL --log-prefix "UDP DROP: "
$IPTABLES -A LOGDROP -i ! lo -p icmp -m limit --limit $LOGLIMIT --limit-burst $LOGLIMITBURST -j LOG --log-level $LOGLEVEL --log-prefix "ICMP DROP: "
$IPTABLES -A LOGDROP -i ! lo -m limit --limit $LOGLIMIT --limit-burst $LOGLIMITBURST -j LOG --log-level $LOGLEVEL --log-prefix "IPTABLES UNKNOWN-IN:  "

### Log All Dropped INPUT Network Traffic
$IPTABLES -A INPUT -j LOGDROP

exit
### EOF ###

```

Please note that all messages will be logged to the syslog which is viewable by dmesg.  If you want this logged somewhere else, then likely the ulogd package should be installed and then appropriately configured (doesn't look hard although I've never done it!)

If you want to log all packets then the above script can be slightly modified.

Please note that once a packet is ACCEPTED or DROPED -- its dead.  It doesnt traverse the chain further.  This is not the case with the LOG chain -- the packet would be logged and then return back to the calling chain and procede farther down the chain.  With this example I collected all the leftover packets (the ones not meeting any rules or about to be dropped) at the end, logged them, and then let the default policy take over and drop the packets.  If I wanted to log all packets (both dropped and accepted), I would collect all the packets in the beginning of the script, log them, and then allow them to pass back to the INPUT chain and eventually either be ACCEPTED or DROPPED (by default).

---

### Post by madu on 2008-06-24
> **kevdog said:**
> Track the incoming connections -- Does this mean track the dropped packets, or track the accepted connections only or both?

Most logging is done for dropped packets however I don't know what you want to do.


Dear Kevdog,
Again, thank you for the help and the effort mate. And for explaining. 
I want to log the dropped packets, but I want to try it out for accepted packets, as a practice. 

I have basic question if you could please help me.
I'm confused with the use of '-m'. The guide said 'm=match'.
But for example:
> $IPTABLES -A INPUT -i eth0 -p tcp -m tcp --dport 80 -j ACCEPT


We mention that we are interested in TCP protocol with '-p'. Then why do we need to say '-m tcp' again?
what is the difference to using:
> $IPTABLES -A INPUT -i eth0 -p tcp --dport 80 -j ACCEPT


I think this probably is a simple concept but I can't seem to grasp it.

Thank you again for all the help mate. Learned an awful lot.

Cheers.

---

### Post by kevdog on 2008-06-24
After looking at it again -- you don't need the -m tcp with the -p tcp match type.  The use of -m designates an explicit of extended match.  There is no tcp extended match type (Here is the reference I am using to confirm this:)
[http://iptables-tutorial.frozentux.net/iptables-tutorial.htm](http://iptables-tutorial.frozentux.net/iptables-tutorial.htm)

If you want to log everything do the following:

```

#!/bin/sh
#

IPTABLES=/sbin/iptables

### flush existing rules and set chain policy setting to DROP
$IPTABLES -F
$IPTABLES -F -t nat
$IPTABLES -X

$IPTABLES -P INPUT DROP
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -P FORWARD DROP

### state tracking rules
$IPTABLES -A INPUT -m state --state INVALID -j DROP
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

### Create a LOGDROP chain to log dropped packets
$IPTABLES -N LOGDROP

### Drop Log Ruleset (Logs all packets not captured above, before dropping)

#Change the Following Parameters to Limit the amount of Logging
LOGLIMIT="2/sex"
LOGLIMITBURST="10"

#Log level may be one of the following: debug, info, notice, warning, warn, err, error, crit, alert, emerg, panic
LOGLEVEL = debug

$IPTABLES -A LOGDROP -i ! lo -p tcp -m limit --limit $LOGLIMIT --limit-burst $LOGLIMITBURST -j LOG --log-level $LOGLEVEL --log-prefix "TCP DROP: "
$IPTABLES -A LOGDROP -i ! lo -p udp -m limit --limit $LOGLIMIT --limit-burst $LOGLIMITBURST -j LOG --log-level $LOGLEVEL --log-prefix "UDP DROP: "
$IPTABLES -A LOGDROP -i ! lo -p icmp -m limit --limit $LOGLIMIT --limit-burst $LOGLIMITBURST -j LOG --log-level $LOGLEVEL --log-prefix "ICMP DROP: "
$IPTABLES -A LOGDROP -i ! lo -m limit --limit $LOGLIMIT --limit-burst $LOGLIMITBURST -j LOG --log-level $LOGLEVEL --log-prefix "IPTABLES UNKNOWN-IN:  "

### Log All INPUT Network Traffic
$IPTABLES -A INPUT -j LOGDROP

### ACCEPT rules
$IPTABLES -A INPUT -i lo -j ACCEPT
$IPTABLES -A INPUT -p tcp --dport 80 -j ACCEPT
$IPTABLES -A INPUT -p tcp --dport 22 --source 131.0.0.0/8 -j ACCEPT
$IPTABLES -A INPUT -p icmp --icmp-type echo-request -m limit --limit 10/second -j ACCEPT



exit
### EOF ###

```

This will only log new connections, because the logging rule is below the ESTABLISHED, RELATED packet match.  I'm figuring you are wanting to log only new are attempted new connections and not packets from established connections (Notice there are only 4 states -> NEW, ESTABLISHED, RELATED, INVALID) Note that the INVALID packets are dropped (and hence no longer traverse the input chain) and the ESTABLISHED, RELATED connections are accepted and hence no longer traverse the remainder of the input chain either, leaving only NEW connections to be logged, and then later accepted if meeting certain criteria.

---

### Post by madu on 2008-06-25
> **kevdog said:**
> After looking at it again -- you don't need the -m tcp with the -p tcp match type.  The use of -m designates an explicit of extended match.  There is no tcp extended match type (Here is the reference I am using to confirm this:)
[http://iptables-tutorial.frozentux.net/iptables-tutorial.htm](http://iptables-tutorial.frozentux.net/iptables-tutorial.htm)



Thanks again for that Kevdog!
Will try remove '-m' when I get home and see.
Currently reading your Port Knocking thread.. Awesome!
Although I'm a little reluctunt because usually when I try something this complicated (for my level) I end up screwing up a perfectly working thing. :confused:

Just curious, if I keep the port open time to 30 seconds, that means I will be cut off after that? and need to reconnect again? also this wouldnt work if I have a server and needs to keep 80 open all the time right? or can I keep 80 open and make port knock only on 22?

I'd probably read a little more and see.

Thanks a million again buddy.

---

### Post by kevdog on 2008-06-25
Again, the port knocking implicitly works with your firewall script.

Once you have issued the knock, you have x sec/minutes (whatever you specify in the fwknop.conf file) to complete the connection. If you do not complete the connection within the time limit port 22 is effectively closed.  Because your firewall was set up to already ACCEPT all ESTABLISHED/RELATED packets, if you complete a connection within the time interval, this connection will not be broken -- meaning you will not need to reconnect.  With the port knocking daemon in place, if you take out the ESTABLISHED/RELATED state match within the firewall script above -- all connections will be closed x seconds after opening them. (This confused me at first for a long time).  

Think about it like this.  In the firewall you are developing above, port 22 is accessible from --source 131.0.0.0/8 24 hours 7 days a week.  You've somewhat limited your access to a specific  IP range, however imagine if you had this open to the world (did not specify a source range).  Specifically if you notice its open for new connections.  Imagine however a program that was running in the background that could automatically modify the iptables dynamically.  For example it could insert the ACCEPT rule for port 22 in the iptables, and later (after x seconds or minutes) remove the rule.  That is what basically the port knocker daemon is doing -- its silently listening for packets passing by with an associated upd port number (again this port number can be set manually), and once detecting the packet with the specific udp port number (upd packet), attempts to decrypt the packet, reads the packet, and then performs an action -- by default this is modify the iptables to open an incoming port -- however it could be other things such as execute this file, perform this command, or call this shell script (which then could execute a bunch of commands).  

The port knocker utility sniffs packets off the wire using the pcap program.  This is the same program used in wireshark, aircrack, etc or utilities that could be used to break WEP wirelessly.  It basically is able to examine all passing network traffic whether its destined for your machine or not!!! Its interesting to run a packet sniffer on a wireless card with many networks nearby.  You can see a bunch of passing packets destined for other people's machines.  In fact, its oftentimes easy to reconstruct the packets and cipher what is in the packets -- very easy for example to pick off names and passwords passed in plaintext (extremely easy -- almost a no brainer -- all you need is wireshark and a wireless networking card).  Pcap is interesting since it actually can packet sniff without specifically opening up a port on your computer -- I don't know of another process that can accomplish this but there are probably others.

You can set up the port knocking utility to do whatever you want.  So specifically you can port knock only on port 22, and leave port 80 open, or do the opposite, or do both (even though I know you probably only want port 22).

Its a fun utility to play around with.  I took me about a day and a half to "get it" and then write the tutorial so I and everybody else could refer back to it.  I tend now to write tutorials or HOW-TO's for about everything new I do.  If they don't do anything at least they serve as a reference for me to refer back later for the instructions.  I tend to play around a lot with many different things and forget the nuances with certain projects.  The How-To tutorials really help me remember what I was thinking at the time.

---

### Post by madu on 2008-06-25
> **kevdog said:**
> Again, the port knocking implicitly works with your firewall script.


Thanks for that explanation mate. Didn't think about the ESTABLISHED. 
Probably read through it again and try it out in the weekend. Since my client machine and server machine(at home) are in different places makes this a bit hard to try it out and debug. Will get back with the port-knocking! :)

> At the conclusion of the examples and comments:
SOURCE: ANY;
OPEN_PORTS: tcp/22;
DATA_COLLECT_MODE: PCAP;
KEY: Ubuntu2008;
FW_ACCESS_TIMEOUT: 30;

For my case if I want to restrict the access, I'd just have to use; SOURCE: 131.0.0.0/8 ?

Appreciate all the help buddy.

---

### Post by kevdog on 2008-06-25
The ESTABLISHED rule will get you every time.  Just remember there are a bunch of packets flying by all the time.  You most likely just want to stop the first packet or NEW packet, since that stops the process.  Once the door is open and the NEW packet allowed, you most likely want to allow all ESTABLISHED/RELATED packets.  INVALID packets, or at least packets you can't figure out if they are NEW/ESTABLISHED/RELATED should probably be dropped.  Not sure how packets become invalid, but this must occur or there wouldn't be a need for this rule.

---

### Post by madu on 2008-06-25
Got it!
This is pretty interesting. 
So I guess FWKNOP is essentially altering the Iptable dynamically.
Thanks a lot mate. Definitely gonna try out.

Cheers.

---

### Post by kevdog on 2008-06-25
Now your cooking with gas!  But yes, its doing it without opening any open ports -- that is part of the magic!!  You will confuse your friends if you tell them you have a listening and reactive process without any requited open ports -- that will confuse them.  The port knocker is invisible to port scanners so its very hard to detect (if not impossible) that it is running on the server.  So its presence is essentially invisible to the outside world severely limiting its ability to become an attack target!

---

### Post by madu on 2008-06-25
> **kevdog said:**
> Now your cooking with gas!  But yes, its doing it without opening any open ports -- that is part of the magic!!  You will confuse your friends if you tell them you have a listening and reactive process without any requited open ports -- that will confuse them.  The port knocker is invisible to port scanners so its very hard to detect (if not impossible) that it is running on the server.  So its presence is essentially invisible to the outside world severely limiting its ability to become an attack target!

Neat!
Port knocking looked scary when I first read it, but once you understand it a bit, seems doable. It's better doing something knowing whats happening rather than just copy-pasting commands.:) Thanks mate!

---

### Post by madu on 2008-06-26
> **kevdog said:**
> Track the incoming connections -- Does this mean track the dropped packets, or track the accepted connections only or both?

Most logging is done for dropped packets however I don't know what you want to do.

If you only want to log the dropped packets (as a form of troubleshooting), I've rewritten your script to the following:

```

#!/bin/sh
#

IPTABLES=/sbin/iptables

### flush existing rules and set chain policy setting to DROP
$IPTABLES -F
$IPTABLES -F -t nat
$IPTABLES -X

$IPTABLES -P INPUT DROP
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -P FORWARD DROP

### state tracking rules
$IPTABLES -A INPUT -m state --state INVALID -j DROP
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

### ACCEPT rules
$IPTABLES -A INPUT -i lo -j ACCEPT
$IPTABLES -A INPUT -i eth0 -p tcp -m tcp --dport 80 -j ACCEPT
$IPTABLES -A INPUT -i eth0 -p tcp -m tcp --dport 22 --source 131.0.0.0/8 -j ACCEPT
$IPTABLES -A INPUT -p icmp --icmp-type echo-request -m limit --limit 10/second -j ACCEPT

### Create a LOGDROP chain to log dropped packets
$IPTABLES -N LOGDROP

### Drop Log Ruleset (Logs all packets not captured above, before dropping)

#Change the Following Parameters to Limit the amount of Logging
LOGLIMIT="2/s"
LOGLIMITBURST="10"

#Log level may be one of the following: debug, info, notice, warning, warn, err, error, crit, alert, emerg, panic
LOGLEVEL = debug

$IPTABLES -A LOGDROP -i ! lo -p tcp -m limit --limit $LOGLIMIT --limit-burst $LOGLIMITBURST -j LOG --log-level $LOGLEVEL --log-prefix "TCP DROP: "
$IPTABLES -A LOGDROP -i ! lo -p udp -m limit --limit $LOGLIMIT --limit-burst $LOGLIMITBURST -j LOG --log-level $LOGLEVEL --log-prefix "UDP DROP: "
$IPTABLES -A LOGDROP -i ! lo -p icmp -m limit --limit $LOGLIMIT --limit-burst $LOGLIMITBURST -j LOG --log-level $LOGLEVEL --log-prefix "ICMP DROP: "
$IPTABLES -A LOGDROP -i ! lo -m limit --limit $LOGLIMIT --limit-burst $LOGLIMITBURST -j LOG --log-level $LOGLEVEL --log-prefix "IPTABLES UNKNOWN-IN:  "

### Log All Dropped INPUT Network Traffic
$IPTABLES -A INPUT -j LOGDROP

exit
### EOF ###

```

Please note that all messages will be logged to the syslog which is viewable by dmesg.  If you want this logged somewhere else, then likely the ulogd package should be installed and then appropriately configured (doesn't look hard although I've never done it!)

If you want to log all packets then the above script can be slightly modified.

Please note that once a packet is ACCEPTED or DROPED -- its dead.  It doesnt traverse the chain further.  This is not the case with the LOG chain -- the packet would be logged and then return back to the calling chain and procede farther down the chain.  With this example I collected all the leftover packets (the ones not meeting any rules or about to be dropped) at the end, logged them, and then let the default policy take over and drop the packets.  If I wanted to log all packets (both dropped and accepted), I would collect all the packets in the beginning of the script, log them, and then allow them to pass back to the INPUT chain and eventually either be ACCEPTED or DROPPED (by default).


Dear kevdog,

I tried this script for logging dropped packets, but I get the following errors:

> 
 /etc/firewall.bash: 41: LOGLEVEL: not found
iptables v1.3.8: log-level `--log-prefix' unknown
Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: log-level `--log-prefix' unknown
Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: log-level `--log-prefix' unknown
Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: log-level `--log-prefix' unknown
Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: Couldn't load target `LOGDROP':/lib/iptables/libipt_LOGDROP.so: cannot open shared object file: No such file or directory



what am I doing wrong?
do I need to load a module?

Thanks a lot buddy.

---

### Post by kevdog on 2008-06-26
I'm slightly confused -- possiby its a syntax combination -- like

LOGLEVEL="debug"

or you could try:

$IPTABLES -A LOGDROP -i ! lo -p tcp -m limit --limit $LOGLIMIT --limit-burst $LOGLIMITBURST -j LOG --log-level debug --log-prefix "TCP DROP: "

---

### Post by madu on 2008-06-26
> **kevdog said:**
> I'm slightly confused -- possiby its a syntax combination -- like

LOGLEVEL="debug"

or you could try:

$IPTABLES -A LOGDROP -i ! lo -p tcp -m limit --limit $LOGLIMIT --limit-burst $LOGLIMITBURST -j LOG --log-level debug --log-prefix "TCP DROP: "

Thanks mate.
still gives a LOGLEVEL not found error. I'll look around a bit more.
Cheers mate.

---

### Post by kevdog on 2008-06-26
Hmmm, that is really strange.  Just eliminate the --log-level debug portion for now.  Every piece of documentation lists this as an option.

---

### Post by kevdog on 2008-06-26
Can you post your /etc/syslog.conf file?

Thanks.

---

### Post by madu on 2008-06-27
> **kevdog said:**
> Hmmm, that is really strange.  Just eliminate the --log-level debug portion for now.  Every piece of documentation lists this as an option.

Hi kevdog,
Thanks for the reply mate.

I took off the --log-level part seems still no luck. However I got this error:
> iptables v1.3.8: Couldn't load target `LOGDROP':/lib/iptables/libipt_LOGDROP.so: cannot open shared object file: No such file or directory
 

Do I need to install anything?

Here is my /etc/syslog.conf

> #  /etc/syslog.conf	Configuration file for syslogd.
#
#			For more information see syslog.conf(5)
#			manpage.

#
# First some standard logfiles.  Log by facility.
#

auth,authpriv.*			/var/log/auth.log
*.*;auth,authpriv.none		-/var/log/syslog
#cron.*				/var/log/cron.log
daemon.*			-/var/log/daemon.log
kern.*				-/var/log/kern.log
lpr.*				-/var/log/lpr.log
mail.*				-/var/log/mail.log
user.*				-/var/log/user.log

#
# Logging for the mail system.  Split it up so that
# it is easy to write scripts to parse these files.
#
mail.info			-/var/log/mail.info
mail.warn			-/var/log/mail.warn
mail.err			/var/log/mail.err

# Logging for INN news system
#
news.crit			/var/log/news/news.crit
news.err			/var/log/news/news.err
news.notice			-/var/log/news/news.notice

#
# Some `catch-all' logfiles.
#
*.=debug;\
	auth,authpriv.none;\
	news.none;mail.none	-/var/log/debug
*.=info;*.=notice;*.=warn;\
	auth,authpriv.none;\
	cron,daemon.none;\
	mail,news.none		-/var/log/messages

#
# Emergencies are sent to everybody logged in.
#
*.emerg				*

#
# I like to have messages displayed on the console, but only on a virtual
# console I usually leave idle.
#
#daemon,mail.*;\
#	news.=crit;news.=err;news.=notice;\
#	*.=debug;*.=info;\
#	*.=notice;*.=warn	/dev/tty8

# The named pipe /dev/xconsole is for the `xconsole' utility.  To use it,
# you must invoke `xconsole' with the `-file' option:
# 
#    $ xconsole -file /dev/xconsole [...]
#
# NOTE: adjust the list below, or you'll go crazy if you have a reasonably
#      busy site..
#
daemon.*;mail.*;\
	news.err;\
	*.=debug;*.=info;\
	*.=notice;*.=warn	|/dev/xconsole


Appreciate the help buddy.
Thanks a lot.

---

### Post by kevdog on 2008-06-27
Please post the following:

lsmod | grep ip

---

### Post by madu on 2008-06-27
> **kevdog said:**
> Please post the following:

lsmod | grep ip


Dear kevdog,
here's what I get.

> 
iptable_nat             8324  0 
nf_nat                 20396  1 iptable_nat
nf_conntrack_ipv4      19080  4 iptable_nat
nf_conntrack           66752  4 xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
ipv6                  267780  14 
iptable_filter          3840  1 
ip_tables              14820  2 iptable_nat,iptable_filter
x_tables               16132  4 xt_tcpudp,xt_state,iptable_nat,ip_tables
blkcipher               8324  1 ecb


Thanks for all the help mate.

---

### Post by kevdog on 2008-06-28
Thanks for hanging with me on this one -- Ive tested on my own machine and am really confused why its not working on yours.

Here is my script first of all:

I've taken out some of the limits for right now -- build them back in later:

#!/bin/sh
#

IPTABLES=/sbin/iptables

### flush existing rules and set chain policy setting to DROP
$IPTABLES -F
$IPTABLES -F -t nat
$IPTABLES -X

$IPTABLES -P INPUT DROP
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -P FORWARD DROP

### state tracking rules
$IPTABLES -A INPUT -m state --state INVALID -j DROP
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

### Create a LOGDROP chain to log dropped packets
$IPTABLES -N LOGDROP

### Drop Log Ruleset (Logs all packets not captured above, before dropping)

#Change the Following Parameters to Limit the amount of Logging
LOGLIMIT="2/s"
LOGLIMITBURST="10"

#Log level may be one of the following: debug, info, notice, warning, warn, err, error, crit, alert, emerg, panic
LOGLEVEL=7

$IPTABLES -A LOGDROP -i ! lo -p tcp -j LOG --log-level $LOGLEVEL --log-prefix "TCP DROP: "
$IPTABLES -A LOGDROP -i ! lo -p udp -j LOG --log-level $LOGLEVEL --log-prefix "UDP DROP: "
$IPTABLES -A LOGDROP -i ! lo -p icmp -j LOG --log-level $LOGLEVEL --log-prefix "ICMP DROP: "
#$IPTABLES -A LOGDROP -i ! lo -m limit --limit $LOGLIMIT --limit-burst $LOGLIMITBURST -j LOG --log-level $LOGLEVEL --log-prefix "IPTABLES UNKNOWN-IN:  "

### Log All INPUT Network Traffic
$IPTABLES -A INPUT -j LOGDROP

### ACCEPT rules
$IPTABLES -A INPUT -i lo -j ACCEPT
$IPTABLES -A INPUT -p tcp --dport 80 -j ACCEPT
$IPTABLES -A INPUT -p tcp --dport 22 --source 131.0.0.0/8 -j ACCEPT
$IPTABLES -A INPUT -p icmp --icmp-type echo-request -m limit --limit 10/second -j ACCEPT


exit
### EOF ###


Next I save this to a file called: firewall.sh
chmod +x firewall.sh


I executed the file:
sudo ./firewall.sh

To see the continuous output (in a separate terminal):
tail -f /var/log/kern.log

That is about it!  Are you executing the script as sudo?

---

### Post by madu on 2008-06-28
Dear kevdog,
Thank you soo much.
Finally got it to work.
I commented out the LOGLEVEL="debug" and manually put *--log-level 7* in the rule.

The error I got before was:
> iptables v1.3.8: log-level `--log-prefix' unknown

for some reason, the script takes *log-level* as *"log-prefix"*. I don't why it doesn't see the *$LOGLEVEL* in between.

Now it works fine. Atlest no error.

One final thing kevdog, 
The warning will be logged in kern.log or syslog?


Thanks a lot for helping me out on this buddy!

P.S: These messages get logged very frequently:
> IPTABLES UNKNOWN-IN:  IN=eth0 OUT= MAC=01:00: DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=60344 PROTO=2
> IPTABLES UNKNOWN-IN:  IN=eth0 OUT= MAC= SRC=192.168.0.5 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
192.168.0.5 is the local machine I'm using. From Google I see that 241/24 has something to do with multicasts although I have no concrete idea.

So I added > $IPTABLES -A INPUT -i eth0 --source 192.168.0.1 -j ACCEPT rule to stop Iptable filling up my syslog.

Just wondering, will there be any risk in accepting 192.168.0.1? I'm thinking no but curious....

Thanks for all the help kevdog!

---

### Post by kevdog on 2008-06-28
A couple things you can do is limit the amount that you log -- that is what I was trying to do -- setup some limits initially, but gave them up just to get this example to work.

kern.log is where I everything for me at least is getting logged.  I know that this can be changed if you want, but if this is sufficient I would leave it.  It seems iptables by default is setup to log to the kern.log, however other things besides iptables get loggged to the kern process.  

It also possible to fine tune your logging process for example if you do not want the google analytics to be logged.  Notice for example I have commented out this line:
#$IPTABLES -A LOGDROP -i ! lo -m limit --limit $LOGLIMIT --limit-burst $LOGLIMITBURST -j LOG --log-level $LOGLEVEL --log-prefix "IPTABLES UNKNOWN-IN: "

I left the remaining 3 lines.  To not log 224.0.0.1/24 for example you could do the following:
$IPTABLES -A LOGDROP -i ! lo -p tcp --source ! 244.0.0.0/24 -j LOG --log-level $LOGLEVEL --log-prefix "TCP_LOGGED_PACKETS: "

This would not log packets from google analytics for example. Also the way may last example was set up -- it logs everything!!! Meaning every accepted and dropped packet.  If this is what you really want to do, your kern.log will get filled up quickly.  You either need to stop logging every packet, or set up some limits about how many packets will be logged per minute, per hour for example, or set up to log somewhere else other than kern.log and then frequently set up this new file to be rotated with the syslog rotate utility frequently and you either combine and compress the logs together or only keep like 5 log generations and delete older logs.

Hopefully this clarifies some things.  I don't know what you want to do.  Most logged packets are specifically packets that were rejected or dropped by the firewall.

---

### Post by madu on 2008-06-28
Thanks a lot kevdog!
I commented out the "UNKNOWN-IN" rule and it should do it.

Thanks a million for all your help buddy. Greatly appreciate everything!

Cheers!

---

